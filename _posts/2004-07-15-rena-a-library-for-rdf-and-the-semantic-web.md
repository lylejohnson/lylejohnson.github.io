---
id: 30
title: 'Rena: A Library for RDF and the Semantic Web'
date: 2004-07-15T15:25:06+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=30
permalink: /2004/07/15/rena-a-library-for-rdf-and-the-semantic-web/
categories:
  - Ruby
  - Semantic Web
---
[Rena](http://raa.ruby-lang.org/project/rena) is a new library for working with RDF that seems to be a Ruby port of the popular [Jena](http://jena.sourceforge.net/) semantic web framework for Java. As noted by the author, it&#8217;s still in the &#8220;experimental&#8221; stage but already shows some promise.

As with Jena, the basic object model parallels the RDF model. Rena has not yet adopted Jena 2.0&#8217;s factory-based approach to creating model instances, so you instead just instantiate the desired model class directly. For example, here&#8217;s how to create an in-memory model, add a resource and define some properties for it: 

> `require 'rena'
require 'rena/dc'`</p> 
> 
> docURI = &#8220;http://www.fxruby.org/doc&#8221; docTitle = &#8220;FXRuby User&#8217;s Guide&#8221; docDate = &#8220;2004-10-24&#8243;
> 
> # Create an empty Model
> 
> model = Rena::MemModel.new
> 
> # Create the resource
> 
> myDoc = model.create_resource(docURI)
> 
> # Add some properties
> 
> myDoc.add_property(Rena::DC::Title, Rena::PlainLiteral.new(docTitle)) myDoc.add_property(Rena::DC::Date, Rena::PlainLiteral.new(docDate))
> 
> # Dump
> 
> model.save(STDOUT, :content_type => &#8216;application/rdf+xml&#8217;)</blockquote> Here, we&#8217;re taking advantage of the built-in support for some of the [Dublin Core](http://dublincore.org) elements. The output of that final call to `MemModel#save` is the RDF/XML serialization of this model: 
> 
> > <pre><?xml version='1.0'?>
<rdf:RDF xmlns:ns0='http://purl.org/dc/elements/1.1/' xmlns:rdf='http://www.w3.org/1999/02/22-rdf-syntax-ns#'></p>



<p>
  <rdf:Description ns0:title='FXRuby User';s Guide' ns0:date='2004-10-24' rdf:about='http://www.fxruby.org/doc'/>
  </rdf:RDF></pre>
  </blockquote>
  I haven&#8217;t gotten around to trying out the parsing or querying support yet, but it looks like the author&#8217;s goal is to more or less emulate what&#8217;s being done with Jena. Hopefully this one will progess quickly.
</p>