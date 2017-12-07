---
id: 163
title: Everybody Say Hoe
date: 2007-01-18T23:38:00+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=163
permalink: /2007/01/18/everybody-say-hoe/
categories:
  - Ruby
---
I&#8217;ve been meaning to check out [Hoe](http://seattlerb.rubyforge.org/hoe/) since it was first announced and I finally got around to it today. Hoe is, basically, a library of useful [Rake](http://rake.rubyforge.org/) tasks. It&#8217;s especially useful for projects hosted on [RubyForge](http://rubyforge.org/), as it provides tasks for uploading your project package and gem files to RubyForge, making announcements, and so forth.

There are at least a few gotchas that you need to be aware of, especially if you&#8217;re trying to integrate Hoe into an existing project (as I did). The first thing I discovered is that Hoe expects to find a file named 

`Manifest.txt` in the top-level directory. This file should (as you might expect) contain a listing of all the files to be included in the package or gem for a release.

Another gotcha is that Hoe tasks want to have complete control over the 

`doc` and `pkg` directories. For example, the `clean` task will remove these directories (in addition to any other files that you specify in the `clean_globs` parameter). This was a problem in my case since I already have a `doc` directory. There&#8217;s at least one change request on file to give developers more control over these directory names, and I hope that the Hoe powers-that-be will take that under consideration.

I haven&#8217;t had an opportunity to try out some of the more release-oriented features, like automatically posting announcement messages and uploading packages to RubyForge, so I&#8217;ll reserve comment on them for the moment. These are definitely tedious tasks to perform manually, and I&#8217;m anxious to see how well Hoe does at automating them when it&#8217;s time for a new 

[FXRuby](http://www.fxruby.org/) release.

To sum up, if you&#8217;re starting out a new project from scratch and haven&#8217;t yet committed yourself to a particular directory structure, I can strongly recommend that you take advantage of Hoe to simplify things. If on the other hand you have an existing project that could benefit from some extra automation, I think Hoe will be beneficial to you as well &#8212; just be aware that there are some sharp edges that you&#8217;ll want to look out for.