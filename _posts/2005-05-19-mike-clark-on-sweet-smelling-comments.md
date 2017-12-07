---
id: 86
title: Mike Clark on Sweet-Smelling Comments
date: 2005-05-19T10:20:00+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=86
permalink: /2005/05/19/mike-clark-on-sweet-smelling-comments/
categories:
  - Software Development
---
A recent [article](http://www.stickyminds.com/s.asp?F=S9041_ART_3) from Mike Clark presents some good advice about comments: 

  1. **Keep It DRY.** The &#8220;Don&#8217;t Repeat Yourself&#8221; principle has wider application than the mere avoidance of code duplication. It&#8217;s also a mistake to duplicate knowledge about the intent or functionality of a method in the source code&#8217;s comments. As Mike notes, &#8220;If a comment already describes what the code does, then the comment is redundant and should be removed.&#8221; 
  2. **Make the Code Speak for Itself.** That is, choose meaningful names for classes, methods and variables. If the purpose of a method isn&#8217;t fairly obvious from its name, there&#8217;s a good chance that it needs a new name. Invest the time and energy that you would have used writing a comment to &#8220;deodorize&#8221; that code smell, and use it to come up with a more descriptive name instead.
  3. **Write a Sweet-Smelling Comment.** Use comments to tell _why_ something was done: what purpose a class serves in the system, assumptions made by the code, and so so.