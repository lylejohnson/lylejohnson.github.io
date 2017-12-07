---
id: 148
title: A Longish Post about Package Names and Versioning
date: 2006-05-31T15:15:35+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=148
permalink: /2006/05/31/a-longish-post-about-package-names-and-versioning/
categories:
  - FXRuby
---
So, I&#8217;ve created a bit of a mess with regards to the naming of different versions of [FXRuby](http://www.fxruby.org/) and am trying to decide how best to solve that problem.

When [FOX](http://www.fox-toolkit.com/) 1.2 was released, Jeroen made a number of API changes in order to promote more consistent naming conventions. For example, classes with names like <tt>FXScrollbar</tt> and <tt>FXStatusline</tt> were renamed to <tt>FXScrollBar</tt> and <tt>FXStatusLine</tt>, and everything was moved into a C++ namespace. FXRuby 1.2 inherited these changes and, as a result, threatened to break a lot of code in the process. Your compiler will loudly tell you that you&#8217;ve misspelled a class or member function name in your C++ code, but such errors won&#8217;t be discovered until runtime in an interpreted language like Ruby.

In a perhaps poorly thought-out workaround to this problem, I renamed the Ruby extension from &#8220;fox&#8221; to &#8220;fox12&#8243; when FXRuby 1.2 was released (see the [discussion](http://rubyforge.org/pipermail/fxruby-users/2004-July/000028.html) in the mailing list archives). Code that was written against the FXRuby 1.0 API would continue to <tt>require 'fox'</tt> and would continue to work as before, using the installed version of FXRuby 1.0. Code written against the FXRuby 1.2 API would instead <tt>require 'fox12'</tt>. And this approach more or less worked, and wasn&#8217;t all that confusing, considering that there were only two choices of FXRuby to pick from.

Fast-forward a few years, and we&#8217;ve now seen both FXRuby 1.4 and 1.6 releases. Neither of these releases made significant API changes as compared to FXRuby 1.2, and greater care was taken to promote backwards-compatibility. The confusing extension-naming convention was followed, however, which means that application programmers have to do some trickery in their code to ensure that a working version of FXRuby is <tt>require</tt>&#8216;d into their application. _Ideally_, code that was written in the FXRuby 1.4 era should continue to work unmodified if FXRuby 1.6 is the only version that&#8217;s available, but that&#8217;s not the case &#8212; at a minimum, you&#8217;re going to have to go in and modify the <tt>require 'fox14'</tt> statement to read <tt>require 'fox16'</tt>.

[RubyGems](http://docs.rubygems.org/) provides a mechanism (via the <tt>require_gem</tt> method) to deal with these versioning issues, but at the time we made this decision for the FXRuby project (back in the summer of 2004), that feature had not yet been implemented in RubyGems. And even if it had been available at that time, RubyGems wasn&#8217;t the de facto standard for Ruby library distribution that it is now, and it wouldn&#8217;t have made sense to depend on the user having installed FXRuby from a gem.

One of the happy side effects (well, happy for some) of the explosion of [Rails](http://www.rubyonrails.org/) over the last year and a half is that the acceptance and use of RubyGems has become much more widespread. I don&#8217;t believe RubyGems is part of the Ruby core (and probably doesn&#8217;t belong there yet), but it _is_ part of the [One-Click Ruby Installer for Windows](http://rubyinstaller.rubyforge.org/wiki/wiki.pl), and anyone who uses Rails is likely to have installed RubyGems as well. So it&#8217;s reasonably safe, at this point in time, for me to assume that RubyGems is going to be available on any platform where Ruby and FXRuby are running.

So the question is, what&#8217;s the best choice going forward? Discussion on the RubyGems developers&#8217; mailing list seems to indicate that the <tt>require<em>gem</tt> method is going away, and that it will be replaced (sort of) with a new <tt>gem</tt> method that &#8220;activates&#8221; a particular version of a Gem by placing its directory in Ruby&#8217;s <tt>$LOAD</em>PATH</tt> (but that doesn&#8217;t actually <tt>require</tt> anything.) On the other hand, that particular <a href="http://rubyforge.org/pipermail/rubygems-developers/2005-May/001521.html">discussion</a> has been going on since at least since May of last year and doesn&#8217;t seem to be quite resolved yet.</p> 

<p>
  As O&#8217;Reilly might ask, &#8220;What say you?&#8221;
</p>