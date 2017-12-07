---
id: 243
title: Second Beta Release for FXRuby Book
date: 2008-01-22T16:34:37+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/2008/01/22/second-beta-release-for-fxruby-book/
permalink: /2008/01/22/second-beta-release-for-fxruby-book/
categories:
  - FXRuby
---
An updated version of the [beta book](http://www.pragprog.com/titles/fxruby) has been released today. The most visible change for this release is the inclusion of the final three chapters of the book, which were still being edited and revised at the time of the initial release. The new chapters cover layout managers, menus and toolbars, and dialog boxes. Thanks to comments and suggestions from beta book readers and other reviewers, I&#8217;ve had the opportunity to make a number of fixes and improvements to the previously released chapters as well.

Many of the changes involved the extended &#8220;Picture Book&#8221; tutorial. For example, the layout algorithm that was described in section 4.4 didn&#8217;t work well in some circumstances (e.g. when the first photo in the album was taller than it was wide, or when the main window was resized so that it was narrower than the width of the first photo). As a result of these and other issues, that section has been revised a bit. Another significant problem that several readers noted had to do with the initialize() method for the AlbumView class, which mysteriously changed between chapters 4 and 5 without any explanation. This problem has also been corrected.

Some readers have been having trouble running the examples due to misconfigured RubyGems installations. The code in the book is written under the assumption that if you&#8217;ve installed FXRuby using RubyGems, that you&#8217;ve also configured Ruby to automatically load up the runtime support for RubyGems, so that **require** statements will search through your installed gems repository when it&#8217;s trying to find libraries like FXRuby. As a result of the confusion over this issue, I&#8217;ve added a new sidebar that discusses RubyGems configuration issues.

Finally, there were a handful of other little changes, in some cases fixing typos, in other cases clarifying and improving the original text. When you work on a project like this for months at a time, it&#8217;s difficult to be objective about it and see things as clearly as fresh sets of eyes can. Thanks to all of the readers who have taken the time to add a report to the official [errata](http://www.pragprog.com/titles/fxruby/errata "Errata for the FXRuby Book") list, or to make a post to the book&#8217;s [forums](http://forums.pragprog.com/forums/53), or to fire off an e-mail to me. Many of your suggestions have already been incorporated, and I&#8217;m keeping track of all of them as I evaluate which changes to make in subsequent releases.