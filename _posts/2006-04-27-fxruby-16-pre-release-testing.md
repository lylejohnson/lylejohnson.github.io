---
id: 142
title: FXRuby 1.6 pre-release testing
date: 2006-04-27T12:32:23+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=142
permalink: /2006/04/27/fxruby-16-pre-release-testing/
categories:
  - FXRuby
---
All of the &#8220;first wave&#8221; of development is complete, and the code&#8217;s currently undergoing some pre-release testing, but I should be able to release [FXRuby](http://www.fxruby.org/) 1.6 some time next week. This release will provide support for all of the new features in [FOX](http://www.fox-toolkit.com/) 1.6, and includes all of the bug fixes from the 1.4 line of development up to and including those fixes made in version 1.4.6.

When I say that I&#8217;ve finished the first wave of development, what I mean is that I&#8217;ve made all of the necessary updates to make FXRuby compatible with FOX 1.6. I have not yet begun work on any of the new features that I&#8217;d like to introduce in the FXRuby 1.6 line, but some of those features include:

  * As previously [discussed](http://lylejohnson.name/blog/?p=133), there are some global API changes that I&#8217;d like to make to the naming of classes and methods in FXRuby.
  * Per a couple of different [feature](http://rubyforge.org/tracker/index.php?func=detail&aid=3425&group_id=300&atid=1226) [requests](http://rubyforge.org/tracker/index.php?func=detail&aid=4043&group_id=300&atid=1226), I&#8217;d like to do something to address the problems that occur when a programmer fails to call `create()` on a newly-constructed resource such as a new icon, or a new child window.
  * Not a code feature per se, but I&#8217;d like to organize some effort to produce more tutorial-style documentation for FXRuby. </ul>Another thing that I&#8217;m investigating is how to open up FXRuby a bit more. FXRuby development has for the most part been a one-man operation for the 5+ years that it&#8217;s been around. As my life gets more and more complicated, I&#8217;m finding less and less time to put into the development, support and maintenance of the code &#8212; so something needs to change for the project to stay relevant.</p> 
    I&#8217;m currently reading through Karl Fogel&#8217;s book, [_Producing Open Source Software_](http://www.producingoss.com/), and there&#8217;s a lot of good information in there, even for people who&#8217;ve been immersed in the open source software world for a long time. One of the big take-away points for me is that in order to attract new developers to help share the load (especially in terms of handling support requests and debugging users&#8217; problems), I&#8217;m going to have to write some developer documentation. And by developer documentation, I&#8217;m talking about documentation of the FXRuby internals and how things are actually implemented. FXRuby is somewhat of an ugly beast on the inside, and I can imagine that it would be daunting for a new developer to wrap their mind around the code base so that they could begin contributing.