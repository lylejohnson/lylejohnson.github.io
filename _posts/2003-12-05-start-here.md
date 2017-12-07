---
id: 3
title: Start Here
date: 2003-12-05T09:45:36+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=3
permalink: /2003/12/05/start-here/
categories:
  - Uncategorized
---
At the beginning of the week, [Why the Lucky Stiff](http://whytheluckystiff.net) launched [What a Quiet Stiff](http://whytheluckystiff.net/quiet), a new wholly owned subsidiary of his popular web site. His request for people to take advantage of the [RSS feed](http://whytheluckystiff.net/quiet/quiet.xml) reminded me that I never got around to finding out what RSS is all about, and so I started doing some research about what it is and what kinds of RSS parsing libraries are available for Ruby.

The first stop was Chad Fowler&#8217;s [Ruby/RSS](http://raa.ruby-lang.org/list.rhtml?name=ruby-rss) module, which is probably very good but presented two immediate problems. First, it relies on yet another extension (xmlparser) for its XML parsing instead of the now-standard REXML. Second, it only works for RSS version 0.91, and Why&#8217;s RSS feed is in version 2.0 format. The next and last stop (for now) was [kou&#8217;s RSS parser](http://raa.ruby-lang.org/list.rhtml?name=rss), which does use REXML and supports RSS 2.0 as well.

After a flurry of hacking, I managed to put together a little [FXRuby](http://www.fxruby.org)-based GUI application for viewing the latest images from [WAQS](http://whytheluckystiff.net/quiet). After a few more touches I will probably publish it to [RubyForge](http://rubyforge.org); it is probably a little too big to include as an example amongst the shorter (and easier-to-digest) FXRuby example programs. Watch this space for the latest developments.