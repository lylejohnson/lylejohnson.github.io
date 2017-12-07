---
id: 130
title: FXRuby continues to search for the Ruby Way
date: 2006-02-09T14:03:49+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=130
permalink: /2006/02/09/fxruby-continues-to-search-for-the-ruby-way/
categories:
  - FXRuby
---
There are some things that I&#8217;m thinking of doing in &#8220;FXRuby&#8221;:http://www.fxruby.org/ 1.6 to make the API more Ruby-like. Something that I&#8217;ve been wanting to clean up for a while now is the widespread use of bit-flags for various widget attributes. This pattern shows up in a number of places in the code. For example, in &#8220;FOX&#8221;:http://www.fox-toolkit.com/ 1.6 the FX4Splitter window can be configured to expand only its top-left pane:

<code lang="cpp">splitter->setExpanded(FX4Splitter::ExpandTopLeft);</code>

or to expand both the top left and top right panes:

<code lang="cpp">splitter->setExpanded(FX4Splitter::ExpandTopLeft | FX4Splitter::ExpandTopRight);</code>

Likewise, if you want to check to see whether the bottom left pane is expanded or not, you&#8217;d write something like:


    <code lang="cpp">
    if (splitter->getExpanded() & FX4Splitter::ExpandBottomLeft) {
        // Bottom left pane is expanded
    }</code>

Now, what I&#8217;m thinking of doing is replacing the symbolic constants like `ExpandTopLeft` and `ExpandBottomRight` with Ruby symbols, and doing something like this instead:


    <code lang="ruby">
    splitter.expand :top&lt;em>left             # expand top left pane
    splitter.expand :top&lt;/em>left, :top_right # expand both top left and top right panes&lt;/p>

&lt;pre>&lt;code>if splitter.expanded? :bottom_left
  # Bottom left pane is expanded
end&lt;/code&gt;
</code></pre> 

Now, in order to "turn off" one of those bits, I'm probably going to need to add something like:

<code lang="ruby">splitter4.unexpand :bottom_right</code>

What I'm wondering is, is there some existing pattern in Ruby that I should be modeling this after? In other words, is this the "Ruby Way" to handle this kind of setting?