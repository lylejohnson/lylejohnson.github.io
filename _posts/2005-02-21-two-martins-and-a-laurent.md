---
id: 71
title: Two Martins and a Laurent
date: 2005-02-21T09:23:00+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=71
permalink: /2005/02/21/two-martins-and-a-laurent/
categories:
  - FXRuby
---
Two guys named Martin announced a couple of nice little [FXRuby](http://www.fxruby.org/)-based applications over the weekend.

First, there was Martin DeMello&#8217;s announcement of the latest version of [FXIrb](http://rubyforge.org/projects/fxirb/), an irb session embedded in a [FOX](http://www.fox-toolkit.org/) window. As Martin noted in his announcement, this work builds on some code initially developed by Gilles Filippini (of [FXScintilla](http://savannah.nongnu.org/projects/fxscintilla) fame) and later picked up by Marco Frailis.

This was followed up by [Martin Ankerl](http://martinus.geekisp.com/rublog.cgi)&#8216;s announcement of [fxri](http://rubyforge.org/projects/fxri/), an FXRuby-based viewer for the ri-style documentation. There&#8217;s a nice [screenshot](http://martinus.geekisp.com/rublog.cgi/Projects/fxri/fxri.html) over at Martin&#8217;s web log. Of special interest is that fxri integrates FXIrb into one of its panes, so that you can try out things on the fly to make sure that they work the way you think they do. Note that fxri depends on the FXRuby gem install and you may find it a challenge to get it working if you&#8217;ve installed FXRuby via the source tarball.

Not to be outdone, Laurent Julliard [announced](http://rubyforge.org/pipermail/freeride-announce/2005-February/000008.html) the latest version of [FreeRIDE](http://freeride.rubyforge.org/), the Ruby IDE. This version includes an irb plugin based on the previously mentioned FXIrb and Laurent says he&#8217;s also working on integrating fxri into FreeRIDE for a future release.

**Update**: Here&#8217;s a [screenshot](http://freeride.rubyforge.org/fxri.png) from Laurent, of fxri integrated into a future version of FreeRIDE. This is some pretty cool stuff.