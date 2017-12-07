---
id: 88
title: Constant != Frozen
date: 2005-06-02T16:45:00+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=88
permalink: /2005/06/02/constant-frozen/
categories:
  - Ruby
---
I almost always learn something new when hanging out in the #ruby-lang IRC channel at [freenode](http://freenode.net/). Or at least I&#8217;m reminded of something that I used to know but have since forgotten.

There was some discussion today of how constants work in [Ruby](http://www.ruby-lang.org/) and I realized that I didn&#8217;t quite understand the difference between a constant and a &#8220;frozen&#8221; object. In Ruby, a constant is variable whose name begins with a capital letter, e.g. 

> `irb(main):001:0> ANSWER = "Forty-Two"
=> "Forty-Two"` Now, as Aredridel noted, constants are just constant _references_ to objects. In other words, attempting to change the object to which `ANSWER` refers (i.e. by assigning some new value to `ANSWER`) will result in a warning: 

> `irb(main):002:0> ANSWER = "Forty-Three"
(irb):2: warning: already initialized constant ANSWER
=> "Forty-Three"` Note that Ruby doesn&#8217;t enforce the &#8220;constant reference&#8221; rule &#8212; it did go ahead and bind `ANSWER` to a different String &#8212; but it does at least warn you about what you&#8217;re doing.

So the basic purpose of using constants is to be aware of when those variables are bound to different objects. That doesn&#8217;t mean, however, that we can&#8217;t change things about the objects to which those constants are bound. Continuing with the previous example, we can make a quick check of the object&#8217;s identity: 

> `irb(main):003:0> ANSWER.object<em>id
=> 22455208` And then call some method (of the _mutator_ persuasion) on the object that will change its properties: 

> `irb(main):004:0> ANSWER.upcase!
=> "FORTY-THREE"` And a subsequent check will confirm that `ANSWER` still refers to the same String that it did before we called `upcase!`: 

> `irb(main):005:0> ANSWER.object</em>id
=> 22455208` Now, if we want to actually lock down the object itself, so that it can&#8217;t be changed anymore, the method we need to call is `freeze`: 

> `irb(main):006:0> ANSWER.freeze
=> "FORTY-THREE"` Trying to modify a frozen object results in a `TypeError`: 

> ``irb(main):011:0> ANSWER.downcase!
TypeError: can't modify frozen string
from (irb):11:in `downcase!'
from (irb):11`` Hopefully the process of writing this long-winded explanation will help me to remember the distinction between constants and frozen objects in the future. Hope it helped you, too.