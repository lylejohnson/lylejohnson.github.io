---
id: 415
title: Literate Programming and Clojure
date: 2011-01-06T17:19:03+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=415
permalink: /2011/01/06/literate-programming-and-clojure/
categories:
  - Clojure
---
Michael Fogus just published a post about [Marginalia](http://blog.fogus.me/2011/01/05/the-marginalia-manifesto/), a new documentation system for Clojure based on Jeremy Ashkenas&#8217; [Docco](http://jashkenas.github.com/docco/) for [CoffeeScript](http://jashkenas.github.com/coffee-script/). It&#8217;s work that Fogus started on late last year, and which Zachary Kim (the creator of [ClojureDocs](http://clojuredocs.org/)) picked up and improved on. The goal for Marginalia is to build a [literate programming](http://www.literateprogramming.com/) system, or something close to it, around Clojure.

My first exposure to the concept of literate programming was about ten years ago, when I was still doing a lot of work with Python. Edward K. Ream&#8217;s [Leo](http://webpages.charter.net/edreamleo/front.html) was the tool that I used to experiment with LP, and to be honest, I didn&#8217;t get it. The idea of LP, as I thought I understood it then, was that you wanted your documentation and code to be intertwined, and readable: more like literature for humans, and less like a structured formula for computers. But the user interface for Leo required you to build up your system in a highly structured outline form. It was tedious. Writing code with Leo didn&#8217;t feel like any sort of programming I&#8217;d done before, and trying to write documentation with Leo sure didn&#8217;t feel like any sort of writing I&#8217;d done before. So after playing with it for awhile, and then getting frustrated with it, I moved on and haven&#8217;t thought any more literate programming until this morning.

Marginalia (in its current incarnation) takes a decidedly different, and for me more familiar tack, of embedding documentation comments directly in code. In that sense it&#8217;s no different from JavaDoc, or RDoc, or most other software documentation systems today. As you would hope, it picks up directly on the docstrings that you provide for namespaces, functions, etc.

It also parses out more general documentation text that you embed in comments that start with two semicolons.

Note that it supports [Markdown](http://daringfireball.net/projects/markdown/syntax)-style formatting in both your docstrings as well as these special documentation comments. There&#8217;s also support for some fancier stuff, like displaying mathematical formulas written in LaTeX, that uses the [MathJAX](http://www.mathjax.org/) engine under the hood, but I haven&#8217;t gotten around to trying that yet.

I must admit that the primary attraction of Marginalia for me at the moment is that it produces [pretty documentation](http://fogus.me/fun/marginalia/uberdoc.html). I&#8217;m a sucker for pretty documentation. But I am intrigued by Fogus&#8217; claim that &#8220;The very process of using Marginalia will help to crystalize your understanding of [the] problem and its solution(s).&#8221; Near the end of his blog post, he proposes a set of guidelines (based on a similar set by [Reg Braithwaite](https://github.com/raganwald/homoiconic/blob/master/2010/11/docco.md)) for incorporating Marginalia into your Clojure software development process to achieve that goal.

Now, if you&#8217;re _really_ into literate programming, Fogus&#8217; blog post also refers (in a footnote) to Tim Daly&#8217;s work on [&#8220;Clojure in Small Pieces&#8221;](http://groups.google.com/group/clojure/browse_thread/thread/460417fe45f314c3), a fork of the Clojure source code (re)written in LP style. This strikes me as a very ambitious effort, but one that I plan to keep tabs on as well. It will be interesting to see how studying this re-interpretation of the Clojure code influences one&#8217;s understanding of Clojure&#8217;s design and implementation.