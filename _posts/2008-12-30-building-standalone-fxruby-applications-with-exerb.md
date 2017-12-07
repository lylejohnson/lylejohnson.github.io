---
id: 308
title: Building Standalone FXRuby Applications with Exerb
date: 2008-12-30T12:49:59+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=308
permalink: /2008/12/30/building-standalone-fxruby-applications-with-exerb/
categories:
  - FXRuby
---
Distributing FXRuby-based applications to end-users who don&#8217;t have Ruby (or FXRuby) installed on their computers can be a challenge. Fortunately, there are a number of freely available tools for building &#8220;standalone&#8221; versions of Ruby applications. In this post, we&#8217;re going to focus on how to use [Exerb](http://exerb.sourceforge.jp/index.en.html), developed by Yuya Kato, to build standalone FXRuby applications on Windows.

The first step is to [download](http://exerb.sourceforge.jp/index.en.html#download) and install the latest Exerb distribution (version 4.2.0, as of this writing). It&#8217;s packaged as a ZIP file, which you&#8217;ll need to extract into some convenient place on your hard drive. Once that&#8217;s done, change directories into the <tt>exerb-4.2.0</tt> directory and run the <tt>setup.rb</tt> script.

Now, to actually go through the process of building a standalone FXRuby application, let&#8217;s start with a simple example. We&#8217;ll use the [hello.rb](http://www.fxruby.org/examples/hello.rb) example program from the FXRuby source code distribution. The first step is to generate a &#8220;recipe&#8221; file for your Ruby application, which is basically a listing of all the files that Exerb should use to build the executable. You&#8217;ll use the <tt>mkexy</tt> tool to do this.


<code lang="bash">
ruby -r exerb/mkexy hello.rb
</code>

The <tt>mkexy</tt> tool runs your application in a custom version of Ruby to analyze which libraries it requires while it&#8217;s running. Once you exit the application, <tt>mkexy</tt> spits out a recipe file (for this example, <tt>hello.exy</tt>) in the current working directory.

Now that you have a recipe, you&#8217;re ready to run Exerb to generate the executable.


<code lang="bash">
exerb hello.exy
</code>

Note that the executable that Exerb creates is quite large, as it bundles both a copy of the Ruby interpreter as well as the FXRuby library code. When I did this experiment, the executable weighed in at close to 9 Mb. You can distribute this executable to other people who don&#8217;t have Ruby or FXRuby installed on their computers.

Now let&#8217;s look at a slightly more complicated example, the [hello2.rb](http://www.fxruby.org/examples/hello2.rb) program. The complication is that this example uses an external file, a PNG icon that it loads from disk at runtime, as shown in this excerpt:

This is unfortunately something that Exerb doesn&#8217;t handle very well, but there is a workaround. What we must first do is dump the contents of the PNG icon to a Ruby string, and store the contents in a regular <tt>.rb</tt> file. Here&#8217;s some code to do that:

Now we need to modify the bit in <tt>hello2.rb</tt> that loads the icon data, so that it instead loads this Ruby code instead:

Now, run the <tt>mkexy</tt> tool as before to generate a recipe file (<tt>hello2.exy</tt>) and then <tt>exerb</tt> to generate the executable.


<code lang="bash">
ruby -r exerb/mkexy hello2.rb
exerb hello2.exy
</code>

There are at least a couple of other tools out there for building standalone Ruby applications, including Erik Veenstra&#8217;s [RubyScript2Exe](http://www.erikveen.dds.nl/rubyscript2exe/) and Jeremy Hinegardner&#8217;s [Crate](http://copiousfreetime.rubyforge.org/crate/). I&#8217;m not at all familiar with how those tools work, but if you&#8217;ve had luck building standalone FXRuby applications with either of these tools, I&#8217;d love to hear about your experience.