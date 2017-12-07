---
id: 146
title: 'On Ruby&#8217;s Performance'
date: 2006-05-22T20:37:16+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=146
permalink: /2006/05/22/on-rubys-performance/
categories:
  - Ruby
---
Comments in a recent [interview](http://www.oreillynet.com/ruby/blog/2006/05/post.html) of <span class="vcard"><a class="fn url" href="http://www.zedshaw.com/">Zed Shaw</a></span> have sparked a new round of discussion concerning Ruby&#8217;s performance (see the thread beginning [here](http://thread.gmane.org/gmane.comp.lang.ruby.general/151370/focus=151370)). Unlike, say, the recent ruby-talk thread on whether stealing is a bad or good thing, this thread actually has a lot of useful information tucked away inside.

Some people noted that for them and their applications, Ruby&#8217;s performance is more than adequate. <span class="vcard"><a class="fn url" href="http://www.jamesbritt.com/">James Britt</a></span> noted that if bottlenecks are identified, performance-critical code can be re-implemented as a C extension module. Ara Howard (among others) [seconded this point](http://article.gmane.org/gmane.comp.lang.ruby.general/151425), furthermore asserting that:

> the key to speed is c, not a vm and, if you ask me, that quest is the white elephant &#8211; not ruby&#8217;s speed. projects like ruby2c, ruby-inline, ruby/dl, swig &#8211; those are the way to speed. putting a vm on top of ruby and trying to make it fast is like chopping and dropping your mini-van and heading to the track : you are going to get killed.

Of course, you can write inefficient code in any programming language, are there are often small changes that can be made to improve the performance of &#8220;pure Ruby&#8221; code. Sam Roberts and Simon Kroger observed that for some of Sam&#8217;s code, the combined effects of making lots of method calls and creating large numbers of objects led to a serious performance problem. As my friend Jeroen likes to point out, the fastest thing that you can do is **nothing**, and &#8220;your slowest Celeron can do nothing as fast as your fastest Pentium D.&#8221; Although Jeroen&#8217;s usually saying this in reference to optimizing graphics performance, the same rule would apply for code that is (for example) creating lots and lots of objects.

Finally, although a lot of the talk in this thread touched on Rite and YARV (the new virtual machine for Ruby) and how that will impact Ruby&#8217;s performance, of special interest is an offshoot of this [thread](http://thread.gmane.org/gmane.comp.lang.ruby.general/151370/focus=151370), started by John Carter, that talks about things we could be doing now (while we&#8217;re waiting for Rite) to improve the out-of-box performance of Ruby, such as taking advantage of all possible compiler optimizations.