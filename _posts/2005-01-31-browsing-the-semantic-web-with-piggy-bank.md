---
id: 64
title: Browsing the Semantic Web with Piggy-Bank
date: 2005-01-31T10:01:36+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=64
permalink: /2005/01/31/browsing-the-semantic-web-with-piggy-bank/
categories:
  - Semantic Web
---
[Piggy-Bank](http://simile.mit.edu/piggy-bank/) is a new extension for the Mozilla Firefox browser that allows you to easily browse the semantic data linked to from regular web pages. I&#8217;ve seen some other projects along these lines, but they tend to be focused on a particular flavor of RDF data (such as Joel&#8217;s [FOAFer](http://peoplesdns.com/foafer/) extension, or Christopher Schmidt&#8217;s [DOAP Viewer extension](http://crschmidt.net/doap/doaper.html)).

I&#8217;m still not quite sure how Piggy-Bank works, but at the least it&#8217;s scraping web pages for any embedded links that have well-recognized types in the Semantic Web, such as &#8220;application/rss+xml&#8221; (for RSS feeds) and &#8220;application/xml+rdf&#8221;. It then follows those links and parses out the &#8220;information tidbits&#8221; from those sources, and presents that information to you in a sidebar. Piggy-Bank attempts to categorize the tidbits into high-level categories, such as &#8220;News&#8221; for RSS Channel and Item resources, or &#8220;Contacts&#8221; for FOAF&#8217;s &#8220;Person&#8221; resources. You can save the tidbits of interest in a local database (&#8220;My Piggy Bank&#8221;) and search through them later; Piggy-Bank remembers the original source of the data and allows you to annotate them with comments as you desire.

In response to the question, &#8220;Why was [Piggy-Bank] built?&#8221; the developers offer the simple answer: 

> _&#8220;Already many researchers and organizations have gotten excited about the promises by the Semantic Web. Through the deployment of this Piggy-Bank extension, we would like to get end-users excited about the Semantic Web, too.&#8221;_ I&#8217;m not sure that Piggy-Bank is the tipping point that&#8217;s going to get end-users &#8220;excited&#8221; about the Semantic Web, but it certainly was easy to install and use.

There are still a few kinks in the system. For example, I found that a lot of pages that _do_ in fact contain links to bunches of semantic data (such as Bob DuCharme&#8217;s [rdfdata.org](http://www.rdfdata.org/) site) aren&#8217;t properly &#8220;scraped,&#8221; presumably since they don&#8217;t annotate the links using the expected link types. The developers might reasonably argue that this is by design, and that it would be too costly to follow all possible outgoing hyperlinks to try to determine whether they point to any useful RDF data. Nevertheless, it might prove useful to find ways to relax whatever rules that Piggy-Bank is currently using so that it&#8217;s able harvest even more semantic data from pages that aren&#8217;t necessarily playing by the rules. Another kink is that (at present) it only seems to handle RSS 1.0 feeds. Again, the developers might reasonably argue that since RSS 1.0 is the only version of RSS that parses as &#8220;legitimate&#8221; RDF, it&#8217;s OK for Piggy-Bank to stumble over the RSS 0.9x and 2.0 flavors. That was little solace to me as I had to wade through a number of my friends&#8217; blogs&#8217; RSS feeds before finding one that was actually available in RSS 1.0 format.

I&#8217;m anxious to see where this project goes over the coming year.