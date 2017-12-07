---
id: 53
title: Sneaking Ruby into a Java Shop
date: 2004-11-15T16:04:46+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=53
permalink: /2004/11/15/sneaking-ruby-into-a-java-shop/
categories:
  - Ruby
---
Like a lot of Rubyists, I&#8217;m working for a company that more or less uses Java exclusively for its software development. And like a lot of those Rubyists, I&#8217;d like to find opportunities to start using Ruby in addition to Java (if not in place of it) for some of those software projects.

Since we have a lot of legacy Java code that we can&#8217;t just rewrite from scratch in Ruby, I need to find a solution that lets me develop new code in Ruby while taking advantage of that Java legacy code. The obvious choice is [JRuby](http://jruby.sourceforge.net), a Java implementation of the Ruby interpreter. Some other less-promising-looking options include [RJava](http://www.spricom.com/rjava) and [RubyJavaBridge](http://arton.no-ip.info/collabo/backyard/?RubyJavaBridge).

I was a little concerned after my first glance at the JRuby home page because it appeared that there wasn&#8217;t much going on; there doesn&#8217;t seem to be much there in terms of documentation, and the last news dated from March 2004. Nevertheless, recent posts to the JRuby users&#8217; mailing list indicate that the project is alive and well. I also found a nice introductory [article](http://www-106.ibm.com/developerworks/java/library/j-alj09084/?ca=dgr-lnxw03JRubyIntro) at IBM&#8217;s developerWorks site.

Another option which technically isn&#8217;t Ruby, but is awfully darned close, is [Groovy](http://groovy.codehaus.org). I think I first heard about Groovy when Chad [blogged](http://chadfowler.com/index.cgi/Computing/Programming/Languages/GroovyJSR.rdoc,v) about it earlier this year, but since then there&#8217;s been a lot of buzz about it in the Ruby community (and elsewhere, I suppose).

One of my concerns about Groovy is the same thing that Chad noted: that Groovy&#8217;s designers have put perhaps a little _too_ much effort into making Groovy similar (syntactically) to Java. One of the enjoyable things about Ruby is that (as I believe Dave Thomas put it) it &#8220;stays out of your way&#8221;; it makes a point of avoiding the awkward constructs found in languages like Java. Another concern about Groovy is the lack of books (so far) about the language. This will no doubt change over the next year or so, as Groovy seems to be on track to becoming an officially blessed scripting language for Java. But in the short term, it means that my co-workers and I are forced to pull together knowledge about Groovy from various sources on the web. A big advantage of Groovy is, of course, that it can be compiled directly into Java bytecode. I&#8217;m not yet sure if that&#8217;s an option with JRuby.