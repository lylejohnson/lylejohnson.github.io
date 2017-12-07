---
id: 39
title: RDF-Redland
date: 2004-08-16T10:57:15+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=39
permalink: /2004/08/16/rdf-redland/
categories:
  - Ruby
  - Semantic Web
---
[RDF-Redland](http://rdf-redland.rubyforge.org/) is Dominic Sisneros&#8217; project to layer a more object-oriented, Ruby-friendly API on top of the flattened C API provided by the standard Redland installation. [Redland](http://www.redland.opensource.ac.uk) is Dave Beckett&#8217;s popular library that provides a framework for building RDF-based applications. It supports a variety of RDF parsers and serializers, persistent storage to a number of relational databases, RDQL-based queries and more.

The standard Redland package originally included only a thin wrapper over Redland&#8217;s C API as its Ruby interface. As of the latest release of the [Redland Language Bindings](http://www.redland.opensource.ac.uk/bindings/), a version of Dominic&#8217;s library is included, and this helps very much to bring the official Ruby bindings up to par with the existing Python and Perl bindings, which are very good.

This post is unfortunately light on content, but I hope to follow up with more information about how to actually use RDF-Redland in a future post. Of the existing options for processing RDF with Ruby, it is certainly the most mature and capable, as of this writing, and it&#8217;s one that I plan to feature in my presentation at the Ruby Conference in October.