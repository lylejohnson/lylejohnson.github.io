---
id: 14
title: Java Profiling Tools (Part One)
date: 2004-05-21T16:30:29+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=14
permalink: /2004/05/21/java-profiling-tools-part-one/
categories:
  - Uncategorized
---
I&#8217;ve been looking around for a free, open source Java profiling tool today. I&#8217;m especially interested in finding something that integrates well with [Eclipse](http://www.eclipse.org). You&#8217;d think there&#8217;d be a lot of choices for something as widely useful as this, but I&#8217;m still trying to find something I like. The first stop today is the [Extensible Java Profiler (EJP)](http://ejp.sourceforge.net), which, if it lives up to its hype, should ultimately be a good choice. I&#8217;ve had a lot of trouble getting it to work, though.

EJP uses a native DLL (named **tracer.dll** for the Windows version) and that DLL needs to be installed in just the right spot. The EJP installation instructions suggest that as long as the directory containing **tracer.dll** is in your path, all will be well. Nevertheless, I couldn&#8217;t get it working until I copied **tracer.dll** into my <tt>C:\j2sdk1.4.1_02\jre\bin</tt> directory. The next snag I ran into was that the profiler was expecting to find a **tracer.cfg** file in my current working directory. This file doesn&#8217;t seem to be documented anywhere, but I did find a sample one in the EJP distribution and so I&#8217;m using that for now.

The current problem is that the log files that EJP produces while it&#8217;s running are just [ginormous](http://www.langmaker.com/db/eng_ginormous.htm). I suspect that if there some hints about what to put in that **filter.cfg** file I might be able to slim those down. As it is, I think I&#8217;m going to have to read up on EJP&#8217;s tracer API, which I think will give more control over the profiling process (and hopefully reduce the size of those log files as a result).

Stay tuned&#8230;