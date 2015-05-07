---
layout: post
title: To Pr0n Or Notpr0n, That Is The Answer
date: '2005-12-20T22:23:00.000-06:00'
tags:
- bare-with-me
excerpt: In telling the story I present this evening, I'm afraid that I must spoil a few of the puzzles on notpron.
modified_time: '2008-04-22T21:50:22.999-05:00'
blogger_id: tag:blogger.com,1999:blog-7551548.post-113514929991169079
slug: to-pr0n-or-notpr0n-that-is-answer
redirect_from: 
- /2005/12/to-pr0n-or-notpr0n-that-is-answer.html
- /redirect/http://fuwjax.blogspot.com/2005/12/to-pr0n-or-notpr0n-that-is-answer.html
blogger_orig_url: http://fuwjax.blogspot.com/2005/12/to-pr0n-or-notpr0n-that-is-answer.html
---
I found myself a new addiction, a little webpuzzle called [notpron](http://deathball.net/notpron).  In telling the story I present this evening, I'm afraid that I must spoil a few of the puzzles, level 40 in particular.  For this I am deeply sorry, and beg of you to first, before reading this post, go directly to notpron and solve the first 40 levels.  You will be the better for having done so.  So to not inadvertently give away any of the fun before you are able to click the link above, the rest of this story will be written in lemon oil.

{::options parse_block_html="true" /}
<div class="lemonink">Level 40 is, as you now certainly know, the third most simple and straightforward puzzle on the site, the first being the first and the second, level 22.  It is with no small amount of embarrassment and shame then that I admit to taking over 3 days to solve this puzzle.  This post is not an attempt to convince you that I am any less of a loser, in fact, I'm probably just validating the hypothesis.  But it will make me feel better, and in the end, isn't that what this time of year is all about?

To my credit I did not just stare at the image for 3 straight days.  I started this level the way I do every level, right click to view source.  After perusing the html, I note any odd tags, comments, filenames, and text, and then proceed to systematically save the source and all related files to my notpron archive.  Yes, in addition to my notes on the site, I have a full archive of every file I have seen starting with the notpron homepage.  DavidM, the puzzle's creator, has very generously used relative links almost everywhere, making the archive quite easy to build.

I consider solving these puzzles much like detective work.  Careful diligence and near-obsessive organization will often be rewarded.  And in the end, any logical jumps made on the basis of intuition should be completely substantiated by a logical connection of the evidence.  And so I approach the levels very systematically, acquiring all the evidence, processing it slowly, iteratively, continually.  

This particular level had an image, an mp3, and the title was in Spanish.  The image looked incredibly similar to the one from level 12, so I went back to the archive to see if there was some connection.  A quick once over showed me that there was a halo to the number 40, but not one on the 12.  I tried halo.htm and a few variants, then switched to trying those variants in Spanish, to no avail.  I decided that the entire puzzle must be on the level 40 and that the reference to 12 was just a red herring.

I opened up the image in the Gimp and started mucking about with the colors.  You see, I'm color blind, so very often things that stand out to you are completely invisible to me.  Take for instance, level 25.  I found one of the words in a matter of minutes, I found the other a few hours later.  I knew it was there, I just didn't know how to find it.

This brings up a very interesting point.  I spent a few hours looking for it because I knew it was there.  I knew it was there because I trust DavidM.  He said the username and password will show up in similar ways, and I believe him.  He has made every puzzle obvious once you solve it.  I know that when I find the answer, I'll know it's the answer.  Trust is very important in these types of puzzles; if you can't trust the creator, you'll lose interest pretty quick.

But I also know that since I'm color blind, I'll occasionally have to make leaps where the path is obvious to everyone else.  And I know I'll have to work harder to see that those obvious things weren't leaps at all.  Honestly, that just makes it more fun for me, even when I got to level 23.  Sure, the first time I read "Yes, I'm small and red, zoom for me" my reaction was something along the lines of "Why don't you just pack me in a train and send me to Auschwitz, you Nazi bastard!?!" but I quickly felt quite guilty for that reaction, and horribly sorry for screaming it as loud as I did.

So there I am in Gimp mucking about with the colors when I realize I'm getting nowhere fast.  I can't find any words embedded in the raster data.  I opened the file in notepad and checked the exif... nothing.  I opened the mp3, and played around with it long enough to find that it's another second of audience noise from a live track.  I tried every elvis.htm variant I could come up with... a dead end.  I looked at the mp3 properties and came up empty again.

At this point I decided I needed a hint.  So off to the irc channel to !hint 40 and lo and behold "Which level are we in?  Go check it closely."  Of course... We're in the bedroom image of level 12.  I need to spend more time in level 12.

So back to level 12 I go, searching and scouring.  After pouring through both the jpg and the gif from that level, I find that the digital clock has had the numbers removed on the jpg, but they're still there on the gif.  But a stab at clock.htm gives "You are the most unoriginal, sorry being I know."  Yes... yes I know.

So I opted for a break and went back to trying to write a little irc bot that will act as a help proxy on the notpron channel.  You see, the channel is a wonderful resource for puzzlers, not only because the automated bots give you hints, but the other notpronners will help out if you still can't figure it out.  I really enjoy helping people, but I've found that people keep coming back to you for help.  It's somewhat difficult to work your own puzzle when you're too busy chatting with other people about theirs.  And perhaps a bigger problem are the people who in desperation bring up level details in the main channel instead of through private messages.  Often times these outbursts are met with a friendly reprimand and an offer of help, and usually much faster than help would otherwise be offered; an odd reward for spoiling.  This has the unfortunate side effect of giving spoilers in one of the places you'd hope to never have them.

So I thought to myself, wouldn't it be great to have a bot that worked like a call center.  You could ask for help, and someone could service your request, but you'd never know who it was.  If you want more help, you have to put in another help request, since you don't know who to message.  And if you just burst into the channel and ask for help, everyone could direct you to the help service.  So you won't be rewarded for spoiling puzzles for everyone else.

I thought this was a great idea, and worked up a good first draft by about 5am.  It had a pretty simple interface and a reasonably robust design.  I figured I'd give it a quick test and then head to bed.  So I had it join the channel and was almost immediately met with the following

> Hal9k1: what the heck
> Hal9k1: Fuwjax - what the hell?
> Fuwjax: hey man, if it bothers you, I'll yank it
> Fuwjax: didn't mean to bug you
> Fuwjax: I was just testing an idea during a low traffic time
> Hal9k1: a) what do we need a 3rd bot for, b) why are you three times in here, and c) pirc is an irc worm

Now, don't get me wrong.  In hindsight that was a pretty stupid thing to do.  But at 5 in the morning, you don't always process the consequences of your actions.  And to think I had brought a worm on the channel... man, I was choking on my stomach.  Well, Hal and I talked for a while.  It turns out that the pirc I was using is not a worm and he did think the help bot wasn't a horrible idea, just not something the channel needs.  And hopefully he doesn't think I was trying to spam the channel (Hal, if you by some chance ever make it to this page, you should be able to find the code <a href ="http://ctp2nd.com/fuwjax/notpron/NotpronHelpBot.zip" title="Long long gone" class="lemonink">here</a>.)  But as I was leaving, he asked what puzzle I was on.  He then went on to ask me how long it took me to finish level 22, clearly a hint (in hindsight, the best hint I was given.)  

I went back to the puzzle and tried desperately to find the plain-as-the-nose-on-my-face answer Hal had hinted toward, but could not find it.  I went to bed with only the small joy that I had somehow narrowly avoided complete banishment from the channel for pissing off the op.  Hal, you're my hero.

The next day I went back to work looking now at the mp3.  I couldn't find anything hidden in the file, but then it dawned on me, level 10 had similar mp3 trickery.  So back to level 10 to peruse all the data yet finding nothing.  I tried all the files from 40 on the level 10 and 12 paths, and vice versa.  I tried every image trick I could on the images from 10 and 12.  I overlayed the level 40 image on the level 12 image to find if it lined up.  I tried everything I could think of.

While helping people out in the channel, I came across Harry who was willing to give me a little help.  I don't like asking for help, and so usually I'll just ask one yes or no question of my own choosing to try and prune one of the possible paths I'm considering.  So I asked Harry, "Does the title play into the puzzle at all?"  I wonder now what Harry must have thought when he saw that question.  In his graciousness he answered "It's trying to get you to look at sth."

Well I did prune out a major wrong path.  I had been completely convinced that the title was just a red herring; something to name the level that didn't really have anything to do with anything.  So that means somewhere in all the hunting around on level 10 and 12, I must have missed something in Spanish.  More hours of searching brought nothing.

But then it dawned on me.  The page right before this was a 404 error much like level 18.  And the response to clock.htm was the same tone as some of the Easter egg level 18 images.  Of course... it must be one of the images from 18.  But there are quite a few images on 18.  I figured it then had to be something like the red herring messages left in level 23.  So that let me rule out processing the... um... more colorful images of level 18.  Processing 18e gave me a very unusual pattern when I played with the red saturation, much like 23 did.  So I spent a long time trying to find a Spanish word from the highlighted letters.  Then I tried to include the individually referenced letters from the 18_ images.  Then I focused on the capital letters.

And then I realized that I had to make a decision right away.  I either had to keep going, looking for an answer that required too many leaps, or I had to trust DavidM.  I could keep searching for an answer that would not be certain even if I found it, or go back to 40 and work it from the start.

I went back to 40.  I'd rather never find the answer than find out I can't trust the puzzle creator.  But still, I found nothing.  I was desperate, I would have to ask for a hint on the channel.

> Fuwjax: in the last three days, I have found the only springerle mold carver in Texas, successfully found Christmas gifts for the two pickiest women on the planet, found a way to almost painlessly make java code i18n-able, and even found a way to not get banned after pissing Hal off.
> Fuwjax: I have not however, in those same three days, found the answer to level 40
> Fuwjax: so.. um... anyone have a little free time to help a brother out?
> Grog: Are you black?
> steve: yes

Am I black?  What self respecting black man drives all over Texas looking for a springerle mold carver?  But it doesn't matter, I know that no matter what I say, I'm about to be sorry I even said anything.  Grog and steve are ruthless, even more so when they're together.  Might as well try to keep them confused and duck out as gracefully as possible; the ol' smoke and mirrors trick.

> Fuwjax: not any more
> Fuwjax: went to high school in the projects, went to college in central Texas
> Fuwjax: but if saying yes means I can get help on 40, I don't mind lying
> Grog: Not any more?
> Grog: You were black but, now you're not?
> Fuwjax: right
> Grog: MICHAEL JACKSON
> Grog: * Added *!*Fuwjax@* to ignore list
> steve: michael jackson
> Fuwjax: damn... I knew it was a test
> Fuwjax: you clearly have never been to central Texas
> Fuwjax: it'll suck the black right out of you
> Grog: Heh
> Fuwjax: I swore I'd never buy boots, never buy a hat, and I'd sure as hell never two step
> Fuwjax: now I only wear boots, I love country dance halls, and I'm sad to say... I bought a hat last April

Alright... out of that one.  Still no help on 40, but tomorrow is another day.

So the next day in #notpron, MrCube comes asking for help on an unrelated issue, and we get to talking about level 40.  

> Fuwjax: well, I can tell you what I've done, if you'd like
> Fuwjax: it's clearly the pic from puzzle 12
> Fuwjax: with a bunch of the items removed
> Fuwjax: and the remote turned to face the bed
> MrCube: Yeah
> MrCube: But you need not know any of that
> MrCube: The answer is literally on the screen
> Fuwjax: haha, I figured as much
> MrCube: Anything look odd?
> Fuwjax: the 40 has a halo
> MrCube: A halo eh
> MrCube: Wonder what it is

So I pull out the Gimp, zoom in on the 40, play with the colors for a bit, and viola, the answer appears.  I could have cried.

So here's the moral of the story.  If you play notpron, trust DavidM.  Yes, he's evil.  Yes, he's devious.  Yes, he has 666 tattooed on his forehead.  But when you find the answer to a notpron riddle, you'll know it's the answer. Especially when it's been sitting on the screen in front of you for 3 straight days.</div>

If for some reason your reply has anything to do with a notpron level, please write it in lemon oil.