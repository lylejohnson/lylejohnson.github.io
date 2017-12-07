---
id: 361
title: Wait, what was that last bit?
date: 2009-10-26T16:29:00+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=361
permalink: /2009/10/26/wait-what-was-that-last-bit/
categories:
  - FXRuby
  - Ruby
---
So some of you may have seen the [news](http://update.gemcutter.org/2009/10/26/transition.html) about Gemcutter.org changing its name to RubyGems.org and becoming the new default gem repository for the Ruby community. I&#8217;m not completely clear yet on all the pros and cons of this move, but I do have to admit that the new site is pretty to look at. As a maintainer, I like the idea of being able to just type &#8220;gem push fxruby&#8221; (or whatever the command syntax is) and being done with it. So I think this will probably turn out to be a good thing.

Buried a few paragraphs down in the news, however, is this tidbit:

> So, what does this mean for RubyForge? The Ruby-specific functionality and data will be moved into RubyGems.org, and the parts that other hosting sites (GitHub, Google Code, SourceForge) can do better will be pruned away.

In the comments, I asked for clarification on exactly what RubyForge services will be going away, and Tom Copeland&#8217;s reply seems to indicate (to me) that the answer is &#8220;everything&#8221;:

> &#8230; We&#8217;re putting together a schedule for standing down (or making read-only) various bits of RubyForge. The thing is that now there are much better options for hosting code/forums/lists/files/etc, so that stuff is going to be retired. I think back in 2003 it made sense for the Ruby community to have a dedicated site for hosting that stuff. Now I don&#8217;t think it does&#8230; I think GitHub/Google Code/SourceForge can all do a better job at that, and Ruby Central doesn&#8217;t have to expend resources/time/money supporting functionality that others are doing better.

This is troubling to me since several FXRuby-related services (such as the web page hosting, bug tracker, and mailing lists) are handled by RubyForge, and have been for a long time now. For me, it&#8217;s not merely a question of, say, finding a new place to host the mailing lists. It&#8217;s also making a decision about what to do with the archives, and dealing with all of the [non-readers](http://www.codinghorror.com/blog/archives/001306.html) who will go out their way to try to subscribe to the old lists even when they&#8217;re clearly marked as inactive and then send e-mails to me to ask why that&#8217;s so. But I know that Tom and company are sensitive to these concerns, and we&#8217;ll figure out a way to make the transition work as painlessly as possible, so I&#8217;m going to try not to be a grumpy old man about it.

So in the meantime, I&#8217;m beginning to consider what my post-RubyForge options are. Setting up a dedicated [Redmine](http://www.redmine.org/) installation, as [Jim Weirich](http://onestepback.org/redmine/) has done for his projects, is an attractive option as it provides one-stop shopping (and I&#8217;ve had some experience with setting up Redmine for other projects already). Another option is to go with different sites targeted at the different services, like entp&#8217;s [Lighthouse](http://lighthouseapp.com/) for bug tracking, maybe [Google Groups](http://groups.google.com/) for the mailing list hosting, and maybe piggybacking the static web site content off of my personal web site somehow (ugh). What about you, dear reader? If you&#8217;re hosting one of the 8,500 projects at RubyForge, what plans are you contemplating for RubyForge&#8217;s looming retirement?