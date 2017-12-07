---
id: 102
title: Ruby Conference Wrap-Up (Part 2)
date: 2005-10-21T15:10:00+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=102
permalink: /2005/10/21/ruby-conference-wrap-up-part-2/
categories:
  - Ruby
---
Hmm, based on the previous installment you might be led to believe that Charles Nutter&#8217;s talk was the last one of the Friday morning panel, when in fact it was the first talk of that afternoon&#8217;s panel. Oh well.

The _second_ talk on Friday afternoon was Koichi Sasada&#8217;s &#8220;YARV Progress Report&#8221;. The goal, as Koichi explained, is for YARV to become the virtual machine for Ruby 2.0 (a.k.a. &#8220;Rite&#8221;). I didn&#8217;t understand a lot of the technical details, but one thing that I do believe I heard was that Koichi doesn&#8217;t expect this work to be completed until at least sometime in 2007. Does that mean that Ruby 2.0, and all that comes with it, is still at least a year or so away? If so, that&#8217;s disappointing news.

The final speaker of the afternoon was Eric Hodel, who spoke about reimplementing Ruby in Ruby itself. The basic problem is that a lot of Ruby&#8217;s core classes and modules are implemented in C (unlike, for example, Smalltalk, where most of Smalltalk is implemented in Smalltalk itself). Since switching back and forth between C and Ruby programming requires such a huge mental &#8220;context switch&#8221;, there&#8217;s a real entry barrier for developers who&#8217;d like to contribute more to the Ruby core. By reimplementing certain core classes primarily in Ruby, with the judicious use of C code via Ryan Davis&#8217; [Ruby::Inline](http://rubyforge.org/projects/rubyinline/) module, the dynamic duo is doing a lot to chip away at that barrier.

After a break for dinner, we reconvened for a &#8220;roundtable&#8221; discussion at 7:30 Friday evening. It was basically an open-ended Q&A session with Matz, but it went really well. There were a lot of good questions. A few things that I took note of: 

  * Francis Hwang asked whether Matz intends to write a language &#8220;spec&#8221; for Ruby. Matz agreed to cooperate with anyone who wants to take the lead on such a project, but he doesn&#8217;t want to write it himself.
  * Austin Ziegler tried to pin Matz down about whether (and when) RubyGems could be integrated into the Ruby core; and more to the point, if Matz was going to take a position on the recent controversy on the ruby-talk mailing list concerning RubyGems. As I recall, Matz gave a suitably non-committal answer.
  * Jamis Buck asked if Matz started to work on Ruby to scratch any particular &#8220;itch&#8221;. Matz replied that no, he was just bored.
  * Derek Sivers (from [CD Baby](http://cdbaby.com/)) asked if Matz still thinks of Ruby as his &#8220;toy&#8221; when making decisions about its direction, or if he takes into account the larger Ruby community&#8217;s needs. Matz replied that because he travels around the world meeting Rubyists, he sees a lot of the different ways that people are using Ruby, things that a lot of us aren&#8217;t aware of. He also made it clear that whenever he makes decisions about Ruby, he wants to be sure that people understand the reasoning behind those decisions.
  * Nathaniel Talbott asked about moving the source code repository to [Subversion](http://subversion.tigris.org/). I didn&#8217;t hear any firm commitment from Matz on this subject, but it sounds like Subversion is already in use by his group and so it seems likely that this will happen eventually.
  * Someone asked if Matz had any regrets about Ruby&#8217;s design, in hindsight. He cited the ambiguity of how multiple assignments work in Ruby as one of his main regrets. Note that it wasn&#8217;t until this conference that I finally &#8220;got&#8221; what he feels is wrong with multiple assignments, and it demonstrated to me all the more how sensitive Matz is to making Ruby simple to understand.
  * Someone asked if Matz had ever been recruited by a large corporation like Microsoft. At first, he said no; but then he recalled that about three years ago, [ThoughtWorks](http://www.thoughtworks.com/) told him that they wanted him, but he thinks they were just kidding. Several ThoughtWorks employees there (including the [boss man](http://www.martinfowler.com/)) assured him that it wasn&#8217;t a joke!
  * I don&#8217;t remember how the question was phrased (i.e. whether the questioner was asking about which languages have influenced Ruby, or simply which languages Matz is interested in), but in his answer Matz mentioned Haskell, Lisp/Common Lisp/Scheme, CLU, Smalltalk and [Io](http://www.iolanguage.com/about/).
  * Finally, somewhere in there, it was noted that at this year&#8217;s conference we had attendees from fourteen different countries, spread over four continents (North America, Europe, Asia and Australia). Stay tuned for the third installment, coming real soon&#8230;