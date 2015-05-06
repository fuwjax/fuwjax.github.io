---
title: How slow are Java Exceptions?
layout: post
tags:
- de-machina
date: '2011-04-10T05:47:00.002-05:00'
excerpt: The real question is not "How slow are 'failures reported as exceptions' compared to 'code that never fails'?"
redirect_from: /2011/04/how-slow-are-java-exceptions/
---
This is a response to a [StackOverflow question][1], but it got a bit too long to leave as an answer on the site.

The real question here is not "How slow are 'failures reported as exceptions' compared to 'code that never fails'?" as the [accepted response][2] might have you believe. Instead the question should be "How slow are 'failures reported as exceptions' compared to failures reported other ways?"

It's commonly accepted that the paradigm for exceptions is "Never throw an exception you intend to catch." So, it's appropriate to throw an exception when someone else will catch it, such as platform/framework API's, or when writing some utility API such as logging or messaging that needs to communicate extra-VM failures such as file or network IO errors.

This is all well and good, and no one would debate throwing an exception in these cases. But let's look at what happens in a simple method that could fail sometimes. Let's say we have the following method signature:

~~~
  /**
   * Transforms SomeClass into SomeOtherClass.
   * @param input some class instance
   * @return the transformed instance,
   *         or null if the transformation was unsuccessful
   */
  public SomeOtherClass transform(SomeClass input)
~~~

Which means our callers all look something like this:

~~~
  SomeClass input = ... // get the input from somewhere
  SomeOtherClass result = transform(input);
  if(result == null) {
    // handle the failure
  } else {
    // use the result
  }
~~~

But now we want to start communicating what went wrong when transform returns null. The easy thing to do is the following:

~~~
  /**
   * Transforms SomeClass into SomeOtherClass.
   * @param input some class instance
   * @return the transformed instance, never null
   * @throws TransformationException on failure
   */
  public SomeOtherClass transform(SomeClass input) throws TransformationException
~~~

To pull this off inside the method implementation, you just turn all those "return null;"'s into "return new TransformationException("reason");"'s. And how would the callers change?

~~~
  SomeClass input = ... // get the input from somewhere
  try {
    SomeOtherClass result = transform(input);
    // use the result
  } catch(TransformationException e) {
    // handle the failure
  }
~~~

It's worth noting that absolutely no one read the previous code block. It's unsurprising. You see that kind of stuff every day in your code. It doesn't register as a smell, because in fact, it isn't. But let's say that one day you start reading about how bad it is to use exceptions on "expected" failures. Now, the very concept of catching an "unexpected" exception is ridiculous, as the act of writing the catch block and handling the exception clearly indicates an expectation. But that doesn't matter, we all start churning our code looking for a smell that's very hard to identify. When we find such a place, we fall back on the ancient C practice of returning a sentinel value.

~~~
  /**
   * Transforms SomeClass into SomeOtherClass.
   * @param input some class instance
   * @return the SomeOtherClass instance or, 
   *    if the transform fails, a TransformFailure instance 
   */
  public Object transform(SomeClass input)
~~~

Which means our callers now have to write some pretty psychic code.

~~~
  SomeClass input = ... // get the input from somewhere
  Object result = transform(input);
  if(result instanceof SomeOtherClass) {
    SomeOtherClass success = (SomeOtherClass)result;
    // use the result
  } else {
    TransformFailure failure = (TransformFailure)result;
    // handle the failure
  }
~~~

So, if you consider using exceptions to be a smell but were perfectly fine with breaking type-safety, you'd wind up with something that's difficult to maintain, impossible to use, and only about twice as fast as the exception-based solution. But you're not fine with breaking type-safety, because it's horribly reckless behavior unjustified by a simple 2x improvement. So instead of sentinel values you decide to use a result object.

~~~
  /**
   * Transforms SomeClass into SomeOtherClass.
   * @param input some class instance
   * @return the TransformResult instance
   */
  public TransformResult transform(SomeClass input)
~~~

And now the calling code looks something more like the following:

~~~
  SomeClass input = ... // get the input from somewhere
  TransformResult result = transform(input);
  if(result.isSuccess()) {
    SomeOtherClass success = result.getSuccess();
    // use the result
  } else {
    TransformFailure failure = result.getFailure();
    // handle the failure
  }
~~~

And now we have a solution that is cryptic, though manageable, but this time, it's twice as slow as using the exceptions in the first place, even if you merge the code between TransformResult and TransformFailure. Again, let me be clear: **Result objects are slower than exceptions even when failures happen half of the time**. You're creating a new result object every time, instead of exceptions only when you need them. It just doesn't make sense.

There's one more argument for exceptions I'd like to make. Let's say someone comes along and uses the transform method without checking the javadocs. In the exception case we see the following:

~~~
  SomeClass input = ... // get the input from somewhere
  SomeOtherClass result = transform(input);
  // use the result
~~~

In the exception case, they will know the return type, and if it's a checked exception, they'll either have a compile failure or have to declare it in the throws clause. Even if it's unchecked, the failure will still propagate. Now consider the sentinel case:

~~~
  SomeClass input = ... // get the input from somewhere
  SomeOtherClass result = (SomeOtherClass)transform(input);
  // use the result
~~~

Here the unaware user will write code that looks perfectly acceptable until it fails at runtime. At that point, all of that failure information you worked so hard to provide will be lost to a ClassCastException. And the result object is no better.

~~~
  SomeClass input = ... // get the input from somewhere
  SomeOtherClass result = transform(input).getSuccess();
  // use the result
~~~

Again, this looks like perfectly normal code. There's no reason to suspect at runtime there will be the same NullPointerException they would have seen if they blindly used the first method in this post that had no failure information.

The main point here is that in the event of a failure handling logic error, the exception case works exactly like it should, reporting the failure information. But the other solutions result in absolutely useless exceptions, which even if you correct and redeploy the software, will still result in the failure, just this time with the information you thought you were getting the first time.

So, the only logical conclusion is this. If you need to report failure information, then use an exception. It's faster than result objects, safer than sentinels, and is far and away the least surprising solution.

[1]: http://stackoverflow.com/q/299068/315943 "How slow are Java Exceptions?"
[2]: http://stackoverflow.com/questions/299068/how-slow-are-java-exceptions/299315#299315 "See some test code..."