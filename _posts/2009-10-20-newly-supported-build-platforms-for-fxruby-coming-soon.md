---
id: 359
title: Newly Supported Build Platforms for FXRuby (Coming Soon)
date: 2009-10-20T16:57:29+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=359
permalink: /2009/10/20/newly-supported-build-platforms-for-fxruby-coming-soon/
categories:
  - FXRuby
---
A long while has passed since the last release of FXRuby (in March 2009) and a couple of new platforms have appeared on the Ruby scene in the meantime. This post provides a brief status update on how support for those platforms is coming along.

One of those platforms is the new MinGW-based [Ruby installer for Windows](http://rubyinstaller.org/), which is quickly approaching its first release candidate. This is a really exciting development and while it&#8217;s not quite yet the official Ruby distribution on Windows, I don&#8217;t think that day is far off.

I actually quietly released a MinGW-compatible gem for FXRuby 1.6.19 a month or so ago, but there&#8217;s a little problem with it, which is that it&#8217;s only compatible with Ruby 1.8.6. If you&#8217;re running the MinGW build of Ruby 1.9.1, this gem isn&#8217;t going to work for you. That&#8217;s not a problem in and of itself, but it _is_ a problem because the RubyGems installation process has no built-in smarts to distinguish between gems that only work with one Ruby version or another. Before someone jumps on that: Yes, I&#8217;m aware of the **required_ruby_version** attribute for the gem specification. What I mean is, there&#8217;s no way to say, &#8220;I want to install the **FXRuby** gem for my platform, but make sure you get the one that was compiled for Ruby 1.9.1 and not the one compiled for Ruby 1.8.6.&#8221; The **required_ruby_version** attribute seems to only be used to prevent you from installing an incompatible gem&#8211;it&#8217;s not something that the gems are indexed on.

The recommendation from Luis Lavena of the RubyInstaller project is to build what he calls a &#8220;fat&#8221; gem (as described [here](http://github.com/luislavena/rake-compiler) and [here](http://tenderlovemaking.com/2009/05/07/fat-binary-gems-make-the-rockin-world-go-round/)), one that includes multiple builds of FXRuby and that selects the &#8220;right&#8221; one at load time. This will naturally increase the gem&#8217;s size, but hey, disk space is cheap and it&#8217;s a proven solution to the problem. So I&#8217;m looking into this approach now and hope to incorporate it into my build process soon.

Another new platform is Mac OS 10.6 (aka Snow Leopard). For an operating system that&#8217;s just a little over a month old, you&#8217;d be surprised at how many people are already looking for an FXRuby gem for Snow Leopard. (Well, maybe I _shouldn&#8217;t_ be surprised, given the Mac love in the Ruby community). This has been a little tricky because some of the tricks that I&#8217;d used in the past to build universal binaries on OS 10.5 (Leopard) didn&#8217;t work quite the same way under 10.6, but I think I&#8217;ve just solved that. If you&#8217;d like to help me test this, you can download a pre-release version of that gem [here](http://dl.getdropbox.com/u/60906/FXRuby-1.6.20-universal-darwin-10.gem). Note that this is intended for use that the Ruby 1.8.7 that comes pre-installed with Snow Leopard. If you&#8217;ve built your own Ruby (as many folks do), this _might_ work for you too, but if it does that&#8217;s just a nice bonus.

Once I&#8217;ve resolved the problems involved in supporting these two platforms, I&#8217;m planning to release FXRuby version 1.6.20. There won&#8217;t be that many functional improvements for those of you already using FXRuby 1.6.19, but it will help to prove out the new build process and re-stabilize things for future releases. I&#8217;ve also been doing a lot of work behind the scenes recently (since the move to [GitHub](http://github.com/lylejohnson/fxruby)) to make it easier for people to hack on FXRuby and contribute code back to the project, but that&#8217;s a subject for another post.