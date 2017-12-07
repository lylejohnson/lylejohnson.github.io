---
id: 237
title: Building FOX and FXRuby on Mac OS X Leopard
date: 2007-12-01T17:59:50+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/2007/12/01/building-fox-and-fxruby-on-mac-os-x-leopard/
permalink: /2007/12/01/building-fox-and-fxruby-on-mac-os-x-leopard/
categories:
  - FXRuby
---
I&#8217;ve run into a few snags trying to build and run FOX and FXRuby on Mac OS X Leopard, and so I wanted to capture those problems (and the solutions) here.

The first problem occurs at build time. FOX compiles OK, but at link time you may see this error message: 

> `ld: cycle in dylib re-exports with /usr/X11/lib/libGL.dylib` This is due to an apparent bug in the Xcode Developer Tools version 3.0 (the latest release). The workaround is to modify the setting of the `LDFLAGS` environment variable to include an additional flag: 

> `LDFLAGS="-dylib_file/System/Library/Frameworks/OpenGL.framework/Versions/A/Libraries/libGL.dylib:/System/Library/Frameworks/OpenGL.framework/Versions/A/Libraries/libGL.dylib"` Note that you&#8217;ll need to do a `make clean` and re-configure the build for this change to take affect.

The next problem occurrs at runtime. When you run a sample FOX application, such as **adie**, you may see a flood of error messages in the console window, along the lines of: 

> `X Error: code 8 major 62 minor 0: BadMatch (invalid parameter attributes).
X Error: code 8 major 62 minor 0: BadMatch (invalid parameter attributes).
X Error: code 8 major 62 minor 0: BadMatch (invalid parameter attributes).
...` There are also several visual artifacts, such as disabled menu items being drawn incorrectly, that indicate something&#8217;s wrong. Fortunately, the [Xquartz](http://trac.macosforge.org/projects/xquartz "Xquartz Project Page") project is providing more up-to-date builds of the X server. Download their latest pre-built binary of the X server, and copy it over the installed version of `Xquartz`: 

> `bunzip ~/Downloads/Xquartz-1.3a1.bz2
sudo cp ~/Downloads/Xquartz-1.3a1 /usr/X11/bin/Xquartz` With these changes in place, FOX and FXRuby should work fine.

P.S. Apologies for the formatting glitches; this WordPress theme isn&#8217;t particularly conducive to posting code snippets.