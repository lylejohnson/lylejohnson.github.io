---
id: 177
title: 'How to pass the current binding&#8217;s block to some other method?'
date: 2007-02-08T18:03:22+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=177
permalink: /2007/02/08/how-to-pass-the-current-bindings-block-to-some-other-method/
categories:
  - Ruby
---
I&#8217;ve posted this question to the mailing list but I might as well ask it here too, in case any of my three or four readers know the answer. Suppose I have a method that will yield to a block if one is given:

> `I&#8217;ve posted this question to the mailing list but I might as well ask it here too, in case any of my three or four readers know the answer. Suppose I have a method that will yield to a block if one is given:

>` 
Such that you can call it like so:

> `obj.try(1, 2, 3) { |recv| ... do something with recv ... }`
Now suppose that I create an alias to this method, for the purpose of overriding how it&#8217;s called, e.g.

> ``I&#8217;ve posted this question to the mailing list but I might as well ask it here too, in case any of my three or four readers know the answer. Suppose I have a method that will yield to a block if one is given:

> `I&#8217;ve posted this question to the mailing list but I might as well ask it here too, in case any of my three or four readers know the answer. Suppose I have a method that will yield to a block if one is given:

>` 
Such that you can call it like so:

> `obj.try(1, 2, 3) { |recv| ... do something with recv ... }`
Now suppose that I create an alias to this method, for the purpose of overriding how it&#8217;s called, e.g.

>`` 
If someone calls this new and improved version of `try` and provides a block, is there any way for me to somehow pass that block down into `old<em>try` without actually modifying the method signature for `old</em>try`? I had thought maybe there was some trickery I could do with the binding for the &#8220;outer&#8221; method call (i.e. the one to the new version of `try`) but that doesn&#8217;t appear to be the case.