---
id: 18
title: In Search of the Semantic Web
date: 2004-06-10T11:20:23+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=18
permalink: /2004/06/10/in-search-of-the-semantic-web/
categories:
  - Semantic Web
---
I&#8217;ve been doing a lot of reading over the last few weeks to try to get a better handle on where things stand with the [Semantic Web](http://www.w3.org/2001/sw/), especially in terms of the enabling technologies (like [RDF](http://www.w3.org/RDF/) and [OWL](http://www.w3.org/2001/sw/WebOnt/)) and existing applications. The [RDF Primer](http://www.w3.org/TR/rdf-primer/) provides a thorough (a very, _very_ thorough) introduction to RDF which I probably need to re-read soon. And from my limited reading it looks like OWL just builds on top of the RDF foundation by providing an even more precise way to specify the relationships between classes, constraints on properties, and so on. A majority of the software is written in Java, which is no surprise, but it looks as though there are at least a few RDF libraries for [Ruby](http://www.ruby-lang.org), such as Dan Brickley&#8217;s [RubyRDF](http://www.w3.org/2001/12/rubyrdf/intro.html) and Dominic Sisneros&#8217;s [rdf-redland](http://rubyforge.org/projects/ruby-rdf/).

In terms of applications, and especially those that are easily accessible to someone like me, I&#8217;ve only just started looking around. I spent a lot of time yesterday reading about the [Friend of a Friend (FOAF)](http://www.foaf-project.org/) project, which has the goal of &#8220;&#8230; creating a Web of machine-readable homepages describing people, the links between them and the things they create and do.&#8221; The idea is that you create a special RDF file (typically named **foaf.rdf**) and place it in some publically accessible place on the web. For example, I&#8217;ve now added a button to this blog which links to [my FOAF file](http://www.knology.net/~lyle/foaf.rdf). By placing a special tag in the metadata of your web page(s) to &#8220;advertise&#8221; this file, special web crawlers can collect FOAF information about anyone on the web who cares to publish a FOAF file in this fashion. Now I just need to find out how having done that is going to make my life better.