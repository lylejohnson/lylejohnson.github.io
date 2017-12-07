---
id: 244
title: Building FXRuby on Leopard with MacPorts
date: 2008-01-24T22:41:38+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/2008/01/24/building-fxruby-on-leopard-with-macports/
permalink: /2008/01/24/building-fxruby-on-leopard-with-macports/
categories:
  - FXRuby
---
A number of people are having interesting problems trying to build [FXRuby](http://www.fxruby.org/) on Leopard (Mac OS 10.5) and so I&#8217;m trying to pin down exactly where the problems are. [Last month](http://lylejohnson.name/blog/2007/12/01/building-fox-and-fxruby-on-mac-os-x-leopard/), I wrote about some of the fundamental problems that you might run into building FXRuby &#8220;from scratch&#8221;, without the help of [MacPorts](http://www.macports.org/). One problem has to do with an apparent bug in the latest release of the Xcode Developer Tools, and another has to do with the buggy X11 server that ships with Leopard. Putting those issues aside, I thought that the MacPorts build was working fine.

Turns out it wasn&#8217;t fine after all. Sorry about that.

In an attempt to get to the bottom of things, I began by completely wiping out the `/opt` directory on my iMac (which is running Mac OS 10.5.1). Next, I reinstalled the [MacPorts 1.6.0](http://svn.macports.org/repository/macports/downloads/MacPorts-1.6.0/MacPorts-1.6.0-10.5-Leopard.dmg) base package. Finally, I fired off an install of the `rb-fxruby` port: 

> `$ sudo port -v install rb-fxruby` Then I went to bed, because I knew that this fresh install of MacPorts was going to need to download and build a bunch of dependencies before it ever got anywhere near FXRuby.

When I checked on the progress the next morning, I saw that, sure enough, the build failed for FXRuby. Some of the last gasps of that attempted build included lines like: 

> ``A number of people are having interesting problems trying to build [FXRuby](http://www.fxruby.org/) on Leopard (Mac OS 10.5) and so I&#8217;m trying to pin down exactly where the problems are. [Last month](http://lylejohnson.name/blog/2007/12/01/building-fox-and-fxruby-on-mac-os-x-leopard/), I wrote about some of the fundamental problems that you might run into building FXRuby &#8220;from scratch&#8221;, without the help of [MacPorts](http://www.macports.org/). One problem has to do with an apparent bug in the latest release of the Xcode Developer Tools, and another has to do with the buggy X11 server that ships with Leopard. Putting those issues aside, I thought that the MacPorts build was working fine.

Turns out it wasn&#8217;t fine after all. Sorry about that.

In an attempt to get to the bottom of things, I began by completely wiping out the `/opt` directory on my iMac (which is running Mac OS 10.5.1). Next, I reinstalled the [MacPorts 1.6.0](http://svn.macports.org/repository/macports/downloads/MacPorts-1.6.0/MacPorts-1.6.0-10.5-Leopard.dmg) base package. Finally, I fired off an install of the `rb-fxruby` port: 

> `$ sudo port -v install rb-fxruby` Then I went to bed, because I knew that this fresh install of MacPorts was going to need to download and build a bunch of dependencies before it ever got anywhere near FXRuby.

When I checked on the progress the next morning, I saw that, sure enough, the build failed for FXRuby. Some of the last gasps of that attempted build included lines like: 

>``  which suggests that those object files were either _never_ compiled, or that they were compiled and subsequently blown away before the linker could get to them. Turns out it was the former case. When I scrolled a little further up in the build log, I could see lines like: 

> ```A number of people are having interesting problems trying to build [FXRuby](http://www.fxruby.org/) on Leopard (Mac OS 10.5) and so I&#8217;m trying to pin down exactly where the problems are. [Last month](http://lylejohnson.name/blog/2007/12/01/building-fox-and-fxruby-on-mac-os-x-leopard/), I wrote about some of the fundamental problems that you might run into building FXRuby &#8220;from scratch&#8221;, without the help of [MacPorts](http://www.macports.org/). One problem has to do with an apparent bug in the latest release of the Xcode Developer Tools, and another has to do with the buggy X11 server that ships with Leopard. Putting those issues aside, I thought that the MacPorts build was working fine.

Turns out it wasn&#8217;t fine after all. Sorry about that.

In an attempt to get to the bottom of things, I began by completely wiping out the `/opt` directory on my iMac (which is running Mac OS 10.5.1). Next, I reinstalled the [MacPorts 1.6.0](http://svn.macports.org/repository/macports/downloads/MacPorts-1.6.0/MacPorts-1.6.0-10.5-Leopard.dmg) base package. Finally, I fired off an install of the `rb-fxruby` port: 

> `$ sudo port -v install rb-fxruby` Then I went to bed, because I knew that this fresh install of MacPorts was going to need to download and build a bunch of dependencies before it ever got anywhere near FXRuby.

When I checked on the progress the next morning, I saw that, sure enough, the build failed for FXRuby. Some of the last gasps of that attempted build included lines like: 

> ``A number of people are having interesting problems trying to build [FXRuby](http://www.fxruby.org/) on Leopard (Mac OS 10.5) and so I&#8217;m trying to pin down exactly where the problems are. [Last month](http://lylejohnson.name/blog/2007/12/01/building-fox-and-fxruby-on-mac-os-x-leopard/), I wrote about some of the fundamental problems that you might run into building FXRuby &#8220;from scratch&#8221;, without the help of [MacPorts](http://www.macports.org/). One problem has to do with an apparent bug in the latest release of the Xcode Developer Tools, and another has to do with the buggy X11 server that ships with Leopard. Putting those issues aside, I thought that the MacPorts build was working fine.

Turns out it wasn&#8217;t fine after all. Sorry about that.

In an attempt to get to the bottom of things, I began by completely wiping out the `/opt` directory on my iMac (which is running Mac OS 10.5.1). Next, I reinstalled the [MacPorts 1.6.0](http://svn.macports.org/repository/macports/downloads/MacPorts-1.6.0/MacPorts-1.6.0-10.5-Leopard.dmg) base package. Finally, I fired off an install of the `rb-fxruby` port: 

> `$ sudo port -v install rb-fxruby` Then I went to bed, because I knew that this fresh install of MacPorts was going to need to download and build a bunch of dependencies before it ever got anywhere near FXRuby.

When I checked on the progress the next morning, I saw that, sure enough, the build failed for FXRuby. Some of the last gasps of that attempted build included lines like: 

>``  which suggests that those object files were either _never_ compiled, or that they were compiled and subsequently blown away before the linker could get to them. Turns out it was the former case. When I scrolled a little further up in the build log, I could see lines like: 

>```  If you&#8217;re not used to scouring build logs looking for strange errors, it may not be obvious what&#8217;s wrong: there _ought_ to be a compiler command (such as `gcc` or `g++`) at the beginning of the line that starts out &#8220;`I. -I. -I/opt/local/...`&#8220;.

What&#8217;s even more interesting to me is that when I typed (again): 

> `$ sudo port -v install rb-fxruby`_This_ time, the build went through fine. Those lines that previously didn&#8217;t show a compiler command were now invoking the C++ compiler (`g++`), and so those object files (like `core_wrap.o`) that were missing in action the last time around got created after all, and everyone lived happily ever after.

So the next part of the investigation is for me to figure out what was broken during the first pass, and why the C++ compiler wasn&#8217;t being picked up properly by FXRuby&#8217;s `extconf.rb` script. More to come&#8230;

**Update:** Problem seems to be [resolved](http://lylejohnson.name/blog/2008/02/28/building-fxruby-on-leopard-with-macports-update/) as of the latest update to Ruby in MacPorts.