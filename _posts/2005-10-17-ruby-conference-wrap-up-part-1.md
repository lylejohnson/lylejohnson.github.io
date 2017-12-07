---
id: 99
title: Ruby Conference Wrap-Up (Part 1)
date: 2005-10-17T13:39:00+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=99
permalink: /2005/10/17/ruby-conference-wrap-up-part-1/
categories:
  - Ruby
---
Early this morning, I was in the middle of typing up a summary of my notes and reflections on this year&#8217;s [Ruby Conference](http://www.rubyconf.org/), when I innocently surfed over to [ruby-doc.org](http://www.ruby-doc.org/) to look up something. Imagine my horror as I watched Firefox crash before my eyes, wiping out the previous half-hour&#8217;s work in the process.

Note to self: Save early, save often. Or better yet, compose blog posts off-line from now on.

So instead of going into detail about the weekend&#8217;s talks, let me just hit the highlights:

Francis Hwang opened the first morning&#8217;s panel with a talk on &#8220;Top-to-bottom testing in Ruby&#8221;. I&#8217;ve only seen Francis speak once before, I guess at the Seattle conference when he introduced [Lafcadio](http://lafcadio.rubyforge.org/). I had forgotten how good he is at this, and it was a great way to kick things off. Favorite quote: &#8220;Sometimes a global variable is just a global variable.&#8221;

To be blunt, I had low expectations for Akira Tanaka&#8217;s talk, entitled &#8220;open-uri: easy to use & extensible virtual file system&#8221;. This is not to say that **open-uri** isn&#8217;t a wonderfully ingenious and useful module to have in the standard library, but come on: there&#8217;s just not _that_ much to say about it, is there? I was pleasantly surprised to find that after spending a relatively short time talking about **open-uri** itself, Akira turned to the more general subject of how to design &#8220;easy to use&#8221; APIs.

Akira covered a number of topics during this part of his talk, but perhaps the most interesting was his use of [Huffman encoding](http://en.wikipedia.org/wiki/Huffman_encoding) as an analogy for how one should think about names in APIs: use shorter names for frequently used methods, and longer names for less frequently used methods. As he correctly noted, Ruby&#8217;s &#8220;p&#8221; method has a lousy name by most any objective standard, but in practice it doesn&#8217;t present a problem because everyone uses it and thus everyone remembers what it does. He made a number of other good points about what makes for a good (or bad) API, and this turned out to be one of the most interesting talks at the conference for me. Favorite quote: &#8220;No configuration is good configuration&#8221;.

The final talk of the morning was Charles Nutter&#8217;s presentation on the state of JRuby, and especially the redesign work that is now underway. I didn&#8217;t take a lot of notes on Charles&#8217; talk because his slides were so detailed and captured most of what he had to say, but this was definitely a topic of interest to me.

More to come in a later installment&#8230;