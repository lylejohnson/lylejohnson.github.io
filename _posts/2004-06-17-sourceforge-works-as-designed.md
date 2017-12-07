---
id: 20
title: 'SourceForge: &#8220;Works as Designed&#8221;'
date: 2004-06-17T13:20:55+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=20
permalink: /2004/06/17/sourceforge-works-as-designed/
categories:
  - Uncategorized
---
I noticed a new problem after the most recent release of [FXRuby](http://www.fxruby.org). It turns out that due to a recent &#8220;fix&#8221;, text in the release notes for a given file release is no longer rendered as HTML; it is instead escaped, making any HTML in the release notes basically incomprehensible. This change of course applies &#8220;retroactively,&#8221; in the sense that if you were to now go back and look at the release notes for an older release, they&#8217;ll look like garbage too (see, for example, the borked [change notes](http://sourceforge.net/project/shownotes.php?release_id=211091) for FXRuby version 1.0.28).

There&#8217;s no way that I&#8217;m going to go back and sanitize all of the old releases&#8217; release notes to use plain text and not HTML. And, to be honest, I don&#8217;t know if anyone was actually reading those anyways, since I usually refer people directly to the [change notes](http://www.fxruby.org/doc/changes.html) at the home page. But it&#8217;s the principle of the thing.

When I went looking for some mention of this change, somewhere in the SourceForge site documentation, the only thing I could find was [this SourceForge support request](http://sourceforge.net/tracker/?group_id=1&atid=200001&func=detail&aid=955494) from Helge Schulz. In his support request, Helge politely described the problems associated with this change and suggested a way that SourceForge could alleviate the problem for projects whose release notes use HTML. Here is the terse response from David Burley, the SourceForge Support Tech who responded to the support request: 

> _&#8220;HTML was never intended to work in the release notes (the fact that it worked was a bug in and of itself).&#8221;_Perhaps so, but this &#8220;bug&#8221; went unnoticed by users for years because it was, in fact, a useful feature of the file release system. This is an excellent illustration of the dark side of &#8220;Works as Designed&#8221;.