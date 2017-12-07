---
id: 49
title: Martin Fowler on Closures
date: 2004-09-10T13:35:44+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=49
permalink: /2004/09/10/martin-fowler-on-closures/
categories:
  - Uncategorized
---
I love days like today when other people provide the content and I just link to it.

Gavri Savio Fernandez alerted readers of the ruby-talk mailing list about a recent [article](http://martinfowler.com/bliki/Closures.html) by Martin Fowler on the use of closures in languages like Smalltalk, Lisp and Ruby. As you might expect, Martin does a great job of explaining the utility of closures to users of less dynamic programming languages like C/C++, C# or Java.

In explaining the differences between closures and seemingly similar programming language features (like function pointers in C) Martin makes an especially insightful observation that I hadn&#8217;t ever considered: 

> _&#8220;Languages that support closures allow you to define them with very little syntax. While this might not seem an important point, I believe it&#8217;s crucial &#8211; it&#8217;s the key to make it natural to use them frequently. Look at Lisp, Smalltalk, or Ruby code and you&#8217;ll see closures all over the place &#8211; much more frequently used than the similar structures in other languages. The ability to bind to local variables is part of that, but I think the biggest reason is that the notation to use them is simple and clear.&#8221;_I&#8217;m not a Smalltalk or Lisp programmer, but this certainly jibes with some of the most frequently cited advantages of Ruby, namely, its expressiveness and readability.

Anyways, go read the article now. Even if you think you know the whole story on closures, I think you&#8217;ll appreciate the conciseness of Martin&#8217;s description. I wonder if we can get him to write something on continuations next?