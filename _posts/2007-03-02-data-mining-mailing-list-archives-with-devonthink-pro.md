---
id: 183
title: Data Mining Mailing List Archives with DEVONthink Pro
date: 2007-03-02T17:21:47+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=183
permalink: /2007/03/02/data-mining-mailing-list-archives-with-devonthink-pro/
categories:
  - Uncategorized
---
I&#8217;ve [written](http://lylejohnson.name/blog/?p=153) a little in the past about [DEVONthink Pro](http://www.devon-technologies.com/products/devonthink/index.html), a research tool for Mac OS X that I bought last summer. I&#8217;ve also [written](http://lylejohnson.name/blog/?p=157) more recently about a little experiment that I&#8217;ve been meaning to perform in an attempt to make better use of the software: namely, to import the [FOX](http://www.fox-toolkit.org/) mailing list archives into DEVONthink to see what kinds of data mining I could do on those archives.

My friend Charlies provided me with his archive of about 9600 e-mail messages from the mailing list (in <tt>mbox</tt> format, if you&#8217;re familiar with it) and so the first challenge was to decide how best to import them into DEVONthink. I ended up writing a little Ruby script to chunk the file into separate HTML files (one per message) and then imported them into a new DEVONthink database. So far, so good.

Next, I wondered how well DEVONthink&#8217;s &#8220;Auto Group&#8221; feature would stand up to the challenge of grouping this volume of data. I tried a couple of small samples &#8212; say, selecting a hundred or so messages and auto-grouping them &#8212; and it finished the job in a few seconds time (and it did an admirable job of grouping them, I might add). But I did wonder what the &#8220;big-O&#8221; level of complexity was for this operation, and if would cause my MacBook to burst into flames if I ask it to auto-group all 9600 items. But I charged ahead and tried anyways.

I selected all of the message items and asked DEVONthink to auto-group them. The first pass, in which it &#8220;compared text&#8221; for the items, took approximately 20 minutes. The second pass, in which it actually grouped the items, took another 35 minutes. So, close to an hour&#8217;s worth of processing on my 2.0 GHz MacBook with 1Gb of RAM &#8212; but it did finish. Note that these are all relatively small files; I&#8217;m assuming the problem becomes progressively more difficult with larger documents.

I was a little surprised, and disappointed, by the results. It _did_ create 303 new groups, each of which contained a handful of messages &#8212; presumably with each group corresponding to all of the messages in a given thread &#8212; but it left the remaining 9000 or so messages ungrouped. I think I&#8217;ll try again to auto-group those remaining messages, but I assume that it will take another hour to do so and I&#8217;m not sure what to expect at the end of the run; will it attempt to construct groups for those items this time?