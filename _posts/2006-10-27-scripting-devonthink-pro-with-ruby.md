---
id: 157
title: Scripting DEVONthink Pro with Ruby
date: 2006-10-27T16:46:53+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=157
permalink: /2006/10/27/scripting-devonthink-pro-with-ruby/
categories:
  - Ruby
---
For awhile now I&#8217;ve been wanting to learn more about scripting DEVONthink Pro, but I&#8217;ve just never gotten around to it. I think one of the reasons I&#8217;ve been putting it off has been that I&#8217;m not all that interested in learning AppleScript &#8212; it&#8217;s one of those special-purpose languages that I&#8217;d only use occasionally and would thus have to re-learn every time I needed to do something in that language.

A few days ago, Apple employee Laurent Sansonetti announced the first release of [RubyOSA](http://rubyosa.rubyforge.org/), a &#8220;bridge that connects Ruby to the Apple Event Manager infrastructure.&#8221; Well, whatever &#8212; it&#8217;s an extension that allows you to script Mac OS X applications in Ruby instead of AppleScript. It was interesting timing, because Hamish Sanderson had only recently announced his [rb-appscript](http://rb-appscript.rubyforge.org/) project, which seems to serve exactly the same purpose.

After installing RubyOSA, the first order of business was to generate some documentation and get an idea of what my options were for scripting DEVONthink. RubyOSA includes a command-line utility named `rdoc-osa`, which generates RDoc-like documentation for a given application:

> `$ rdoc-osa --name "DEVONthink Pro"`
The resulting documentation reveals a number of kinds of application objects that one can work with, but it was still a little unclear to me what was what. After some educated guesses, I came up with this preliminary test program:

> `require 'rbosa'

app = OSA.app('DEVONthink Pro')
app.open_database '/Users/lyle/Documents/Knowledge Engineering.dtBase'
app.current_database.records.each do |record|
&nbsp;&nbsp;puts "Record #{record.name} is of kind #{record.kind}"
end`
Which produces the output:

> `Record News Feeds is of kind Group
Record Software Development is of kind Group
Record Semantic Web is of kind Group
Record Apple Mail is of kind Group
Record Documents is of kind Group
Record @Inbox is of kind Group
...`
OK, so the database&#8217;s `records` accessor returns an array of `Record` objects, each of which is a reference to a top-level group in my DEVONthink Pro database. The next trick is to see how I can get at the items in a group (specifically, the items in the &#8220;@Inbox&#8221; group). According to the RDoc, `Record` has an accessor named `children`, which returns an array of `Child` objects, and `Child` is a subclass of `Record`. So I move on to the next iteration of my test:

> `require 'rbosa'

app = OSA.app('DEVONthink Pro')
app.open_database '/Users/lyle/Documents/Knowledge Engineering.dtBase'
app.current_database.records.each do |record|
&nbsp;&nbsp;if record.name == '@Inbox'
&nbsp;&nbsp;&nbsp;&nbsp;record.children.each do |child|
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;puts "Item with name '#{child.name}' is of kind #{child.kind}"
&nbsp;&nbsp;&nbsp;&nbsp;end
&nbsp;&nbsp;end
end`
Which produces the output:

> `Item with name 'Why do I need a Semantic Web?' is of kind RTF
Item with name 'The Power of the Marginal' is of kind RTF
Item with name 'Ready or not...' is of kind RTF
Item with name 'The Semantic Web Revisited' is of kind RTF
Item with name 'Panasonic Speaker Phone Manual' is of kind PDF+Text
Item with name 'RubyAndRdf.rdoc' is of kind rdoc
Item with name 'Proposal Stuff.doc' is of kind RTF
Item with name 'www.oreilly.com/oreilly/author' is of kind URL
...`
So with really just a small amount of work, I&#8217;ve got a framework for doing some more advanced scripting of DEVONthink Pro, using Ruby. One of the projects that I&#8217;d like to take on with this is to convert some of the old FOX mailing list archives (which I currently have as `mbox` files) into individual RTF documents and then import those into DEVONthink. I&#8217;m interested in seeing how DEVONthink&#8217;s classification and search capabilities do with this kind of content, and what kinds of patterns it can discover for me. Hopefully I&#8217;ll be able to follow up on this article soon with the results of that project.