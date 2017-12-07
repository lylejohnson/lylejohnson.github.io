---
id: 16
title: Java Profiling Tools (Part Two)
date: 2004-06-08T14:06:03+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=16
permalink: /2004/06/08/java-profiling-tools-part-two/
categories:
  - Uncategorized
---
The next Java profiling tool I looked at, and which I think I&#8217;ve settled on, is aptly-named [Eclipse Profiler Plugin (EPP)](http://eclipsecolorer.sourceforge.net/index_profiler.html). Unlike the [Extensive Java Profiler (EJP)](http://ejp.sourceforge.net), this one&#8217;s truly an Eclipse plugin. Like EJP, the EPP lets you view the per-method CPU time (and other measurements). The difference is that it&#8217;s done dynamically; no more waiting for the job to finish, dumping a huge log file, and then using a separate postprocessing tool to analyze the results.

Something that both of these tools seem to be missing, and which I would like to see, is an API that gives me a lot tighter control over when profiling is turned on or off. The EPP does give some control over filtering out classes from certain packages, and turning profiling on and off when you enter or exit one specific method, but I&#8217;d like to see more done in this area. Another thing I&#8217;m looking for is better tutorial documentation about how best to use such a profiling tool. It&#8217;s imperative that the documentation tell you which button to press to trigger a certain action, but it&#8217;s more important in my mind to give guidelines about when certain profiling tools are useful and how to get the most benefit from them. A lot of times I find that I&#8217;ve run the test, am looking at the profiling results, and still am no closer to understanding where all the time&#8217;s going.

The last tool I looked at, and one which I&#8217;m still interested in, is [JFluid](http://research.sun.com/projects/jfluid) from the Sun Research Labs. This one&#8217;s a little more invasive in the sense that you&#8217;re actually replacing the stock Java 1.4.2 Hotspot VM with a modified version from the JFluid project. This modified JVM supports dynamic bytecode instrumentation, which means that you can actually change the parts of the program that are being profiled while the program&#8217;s still running. Furthermore, by selectively instrumenting certain parts of the code (while leaving others alone) you don&#8217;t suffer the performance hit that many other profiling tools impose when they effectively instrument every method call.

JFluid also has some nice tools built in to its GUI for visualizing the heap usage and &#8220;object liveness&#8221;, i.e. the numbers of objects which survive over successive generations of garbage collection. This is something I didn&#8217;t see in the other profiling tools, and it provides an especially useful way to detect memory leaks. If some object(s) survive for a large number of generations, it is quite possible that you&#8217;ve got a memory leak. JFluid can tell you where those objects were allocated to give you a head start on finding those potential leaks.