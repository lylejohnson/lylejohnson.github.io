---
id: 245
title: Building FXRuby on Leopard with MacPorts (Update)
date: 2008-02-28T16:19:45+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/2008/02/28/building-fxruby-on-leopard-with-macports-update/
permalink: /2008/02/28/building-fxruby-on-leopard-with-macports-update/
categories:
  - FXRuby
---
I [previously](http://lylejohnson.name/blog/2008/01/24/building-fxruby-on-leopard-with-macports/) wrote about the difficulties some people (including myself) were having with building FXRuby on Mac OS X (Leopard). I am pleased to report that as of the most recent update to [MacPorts](http://www.macports.org/), the Ruby port has been upgraded to 1.8.6-p111 (previous version was 1.8.6-p110), and this seems to have fixed the problem.

If you&#8217;ve been having trouble building FXRuby &#8220;out of the box&#8221; on Mac OS X, first make sure you have the latest MacPorts and that you&#8217;ve upgraded to ruby-1.8.6-p111: 

> `$ sudo port -d sync
$ sudo port upgrade ruby` Once that&#8217;s done, you should be able to either install FXRuby from its port, e.g. 

> `$ sudo port install rb-fxruby` or from the source gem, e.g. 

> `$ sudo gem install fxruby` If you&#8217;re still having trouble after this update, please let me know!