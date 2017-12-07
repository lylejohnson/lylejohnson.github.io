---
id: 389
title: First Steps with Clojure
date: 2010-08-18T14:55:28+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=389
permalink: /2010/08/18/first-steps-with-clojure/
categories:
  - Clojure
---
So I&#8217;m starting to learn [Clojure](http://clojure.org/), using Stuart Halloway&#8217;s book [<cite>Programming Clojure</cite>](http://pragprog.com/titles/shcloj/programming-clojure) as a guide. It&#8217;s a steep learning curve for me as I&#8217;ve only ever done procedural and object-oriented programming, save for a brief dalliance with Scheme in a programming course I took in graduate school.

I get the basic concepts of functional programming (immutable data, functions without side effects, etc.) but am nowhere near the point where this functional mindset comes naturally to me. I still want to break things down into objects, with methods that carry out actions step-by-step.

One of the the things about Clojure that seems to be tripping me up a lot is the syntax surrounding the `ns`, `use` and `require` special forms. For example, one of the first references to `use` occurs on p. 19 of <cite>Programming Clojure</cite>, and it looks like this:

A bit later, on p. 38, he reintroduces `use`, but this time the example looks like this:

Now, I get that in the first example, he&#8217;s saying &#8220;only use the `str-join` function from the `clojure.contrib.str-utils` library,&#8221; while in the second example he&#8217;s using everything. What I don&#8217;t get is the differing syntax, using a quoted vector in the first example, and a quoted list in the second. It sort-of makes me think that this should work too:

but of course it doesn&#8217;t, and I get a mostly useless error message in the REPL. Now, if you&#8217;re an experienced Lisp, Scheme or Clojure programmer, you probably understand why this last example is wrong and you really don&#8217;t understand how I could _possibly_ think that could be right, but I&#8217;m just not there yet. But I&#8217;m working on it!

Another thing that has hindered my progress a bit is the way that Clojure&#8217;s standard library and its API documentation are organized. Take the [`clojure.core` library](http://clojure.github.com/clojure/clojure.core-api.html) for example: it contains several hundred functions, and unless you already know the name of the function you&#8217;re looking for, tracking down just the right function for what you need is like looking for a needle in a haystack. For example, a little program I was playing with yesterday dealt with a list of maps, like so:

Now what I wanted was to convert this list of maps into a single map, where the names of the relation types were the keys and the values were the relation types themselves; i.e. a result like this:

After looking through the API documentation for `clojure.core` I decided there wasn&#8217;t any function that would perform this kind of transformation directly (or at least not that I could tell). I also determined (I think) that there&#8217;s only one function, `hash-map`, that will produce a `map` from its inputs; everything else seems to produce a list/sequence. So anyways, I ended up going with this approach:

and it works, but I&#8217;m looking at it and wondering, is this the best way to do this? Is there maybe a more efficient approach than first constructing a list of the type names, then interleaving those with the types to produce yet another list, and finally using `hash-map` to convert it into a map?

Having said all that, the challenge of learning this new (to me) approach to programming is fun, and I anticipate that it&#8217;s going to affect how I think about programs that I write in the languages that I already know well, like Ruby and Java. I&#8217;m also excited about finally having what feels like a more &#8220;practical&#8221; Lisp to play with, one that I can use with existing Java libraries that I work with every day.