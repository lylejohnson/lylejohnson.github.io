---
id: 248
title: One-step installation for FXRuby on Mac OS X
date: 2008-03-28T21:01:04+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/2008/03/28/one-step-installation-for-fxruby-on-mac-os-x/
permalink: /2008/03/28/one-step-installation-for-fxruby-on-mac-os-x/
categories:
  - FXRuby
---
In previous posts over the last few months I&#8217;ve written about the efforts to get the ports of [FOX](http://www.fox-toolkit.org/ "FOX Home Page") and [FXRuby](http://www.fxruby.org/ "FXRuby Home Page") working in [MacPorts](http://www.macports.org/) for OS X &#8220;Leopard.&#8221; Now that that issue is (mostly) settled, the next thing I wanted to do was work out the steps required to provide a binary gem of FXRuby for OS X that _didn&#8217;t_ depend on MacPorts. I&#8217;m pleased to report that as of today, with the release of version 1.6.14 of FXRuby, that binary gem is now available.

If you&#8217;re running OS X and using the built-in version of Ruby that comes with that operating system, you can install FXRuby by typing:

> `$ <strong>sudo gem install fxruby</strong>`
Once the installation is complete, you can verify that it&#8217;s working properly by firing up `irb` and trying to `require` the library:

> 
``In previous posts over the last few months I&#8217;ve written about the efforts to get the ports of [FOX](http://www.fox-toolkit.org/ "FOX Home Page") and [FXRuby](http://www.fxruby.org/ "FXRuby Home Page") working in [MacPorts](http://www.macports.org/) for OS X &#8220;Leopard.&#8221; Now that that issue is (mostly) settled, the next thing I wanted to do was work out the steps required to provide a binary gem of FXRuby for OS X that _didn&#8217;t_ depend on MacPorts. I&#8217;m pleased to report that as of today, with the release of version 1.6.14 of FXRuby, that binary gem is now available.

If you&#8217;re running OS X and using the built-in version of Ruby that comes with that operating system, you can install FXRuby by typing:

> `$ <strong>sudo gem install fxruby</strong>`
Once the installation is complete, you can verify that it&#8217;s working properly by firing up `irb` and trying to `require` the library:

> 
`` 
Hopefully, this will make it a lot easier for Mac users to get up and running with FXRuby. If you run into problems installing or using the gem, please report them on the [FXRuby mailing list](http://rubyforge.org/mailman/listinfo/fxruby-users "FXRuby Mailing List Information").