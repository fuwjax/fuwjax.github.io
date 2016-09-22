---
title: Fuwjin Suite v0.9.6
layout: single
tags: 
- de-machina
date: '2011-05-20T05:47:00.002-05:00'
slug: fuwjin-suite-v0-9-6
redirect_from: /2011/05/fuwjin-suite-v0-9-6/
---
The Fuwjin Suite v0.9.6 is released to Maven Central. Some fun new features in there.

* There's a first stab at a maven plugin that runs a Grin Script during the build. In fact chessur is using the maven plugin to compile itself.
* The full Grin Specification is supported 100% in the GrinParser, GrinSerializer, GrinFormatter, and GrinCodeGenerator.
* The performance is substantially improved. The system tests alone used to take around 2 minutes to run, now the whole project builds in 20 seconds.
* The API has been overhauled to allow more direct calls to the Scripts.

The suite really is ready for general use, and I'd be happy to help folks understand what it does and why it's different. I'm planning on taking a break from active development to get some posts up here and a few screencasts on the [googlecode][1] site. Let me know if there's anything in particular you'd like to see.

[1]: http://fuwjin.googlecode.com "development"