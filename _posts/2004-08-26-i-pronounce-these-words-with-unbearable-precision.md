---
id: 45
title: '&#8220;I Pronounce These Words With Unbearable Precision&#8230;&#8221;'
date: 2004-08-26T19:16:47+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=45
permalink: /2004/08/26/i-pronounce-these-words-with-unbearable-precision/
categories:
  - Uncategorized
---
Apologies for the title, I&#8217;m just sort of tapped out right now. Bonus points if you caught the reference.

So I&#8217;m down to about one month until the Ruby Conference and I really need to get to work on my presentation. I already know most of what I want to say in terms of background information, but I&#8217;d like to cook up some simple application in order to demonstrate the various Ruby libraries for RDF processing. By developing the same application in each of the available libraries I should get a pretty good feel for which one(s) are most mature and can be recommended for other people to check out.

One obvious choice is a &#8220;six degrees of Lyle&#8221; application, that would make use of the various &#8220;knows&#8221; entries in [my FOAF file](http://www.lylejohnson.name/foaf.rdf) to spider out and identify all of the people who are _n_ degrees away from me. I haven&#8217;t tried this yet, but I have the feeling that given the somewhat inbred nature of the fledgling [FOAF](http://www.foaf-project.org) community I might not have much luck for values of _n_ greater than one. Unless I make some farfetched claim, such as that I &#8220;know&#8221; Dan Brickley or some other well-connected soul. It also suggests that I have the time and bandwidth to run a [scutter](http://rdfweb.org/topic/Scutter).

A more straightforward but less glamorous application would be a little utility that reads a FOAF file containing **mbox** entries for various people and converts them into **mbox_sha1sum</b> entries. That is, I could maintain my FOAF using the unencrypted e-mail addresses for my friends by use this utility to encrypt them before publishing my FOAF to the web. It would certainly be a useful tool for me to have, since I&#8217;m currently just leaving little comments to myself in the FOAF to remind me of which e-mail address a particular **mbox</em>sha1sum** tag refers to, e.g. &#8220;This is Bob&#8217;s yahoo.com e-mail address&#8221;.</p> 

I&#8217;ve also got a nagging feeling that I could do some interesting things with the [Auburn Knights](http://www.auburnknights.com) Alumni Association&#8217;s database if I were to convert it to RDF. Charlie K. has already asked me to take the lead in organizing and writing up the history of the band in the 90&#8217;s and so I&#8217;m having to sift through all of this data anyways, to try to identify who was on the band when. In order to pound it with the RDF hammer I&#8217;d need to cook up an appropriate vocabulary, or even better a combination of existing vocabularies. FOAF could certainly be a part of that, and maybe Masahide Kanzaki&#8217;s [Music Vocabulary](http://www.kanzaki.com/ns/music.rdf) (although the latter seems more slanted toward classical music performances and musicians, and not Big Band Jazz).