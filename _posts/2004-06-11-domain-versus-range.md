---
id: 19
title: Domain versus Range
date: 2004-06-11T08:08:02+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=19
permalink: /2004/06/11/domain-versus-range/
categories:
  - Semantic Web
---
For this brief moment during which I think I get it: 

  * the _range_ of a property indicates the type(s) of values it can take on. For example, [foaf:homepage](http://xmlns.com/foaf/0.1/homepage) has the range [foaf:Document](http://xmlns.com/foaf/0.1/Document), because your homepage must be a Document resource. Another way to say this is that &#8220;[foaf:Document](http://xmlns.com/foaf/0.1/Document) is the range of [foaf:homepage](http://xmlns.com/foaf/0.1/homepage).&#8221;
  * the _domain_ of a property indicates the classes of resources that might have one of these properties. For example, the [foaf:mbox](http://xmlns.com/foaf/0.1/mbox) property has the domain [foaf:Agent](http://xmlns.com/foaf/0.1/Agent), because it is Agent resources that have this property. Another way to say this is that &#8220;[foaf:Agent](http://xmlns.com/foaf/0.1/Agent) is the domain of [foaf:mbox](http://xmlns.com/foaf/0.1/mbox).&#8221;