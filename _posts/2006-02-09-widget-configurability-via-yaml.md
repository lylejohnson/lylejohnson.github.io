---
id: 131
title: Widget Configurability via YAML?
date: 2006-02-09T16:20:30+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=131
permalink: /2006/02/09/widget-configurability-via-yaml/
categories:
  - FXRuby
---
Just to follow up on my &#8220;previous post&#8221;:http://lylejohnson.name/blog/?p=130: Most who responded on the ruby-talk list liked the proposed API change for FXRuby. &#8220;Dan Berger&#8221;:http://www.livejournal.com/users/djberg96/ noted that I should be sure to make it so that strings could be used in place of symbols, e.g.

<code lang="ruby">splitter.expand("top&lt;em>left", "top&lt;/em>right")</code>

should be equivalent to:

<code lang="ruby">splitter.expand(:top&lt;em>left, :top&lt;/em>right)</code>

Ara Howard added that accepting string values as inputs _could_ make it easier to configure a widget via &#8220;YAML&#8221;:http://yaml4r.sourceforge.net/. For example, suppose that all widgets had a @configure@ method that took a hash:


    <code lang="ruby">
    splitter.configure({
      "expand" => ["top&lt;em>left", "top&lt;/em>right"],
      "foo" => "bar" 
    })</code>

Now if you had a file @config.yml@ containing the YAML representation of that hash:


    <code lang="yaml">
    ---
    expand:
    - top&lt;em>left
    - top&lt;/em>right
    foo: bar</code>

You could then configure the widget in one line using:

<code lang="ruby">splitter.configure(YAML::load(IO::read('config.yml')))</code>

Now, I said that _most_ folks like the proposed changes. Simon Kr&#246;ger is (so far) the lone dissenter, and he didn&#8217;t see all that much that was wrong with the current approach. He did propose an alternative approach that involved treating the attribute (here, @FX4Splitter#expanded@) as a @Symbol@ but also delegating some of the work to a @Set@. It seemed a little convoluted for my taste but it&#8217;s good to see other ways to think about the problem.