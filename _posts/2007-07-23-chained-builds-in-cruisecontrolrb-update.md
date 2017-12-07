---
id: 216
title: Chained Builds in CruiseControl.rb (Update)
date: 2007-07-23T17:37:47+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=216
permalink: /2007/07/23/chained-builds-in-cruisecontrolrb-update/
categories:
  - Ruby
---
Last Thursday I [wrote](http://lylejohnson.name/blog/?p=215) about the kind of chained builds functionality that I want from [CruiseControl.rb](http://cruisecontrolrb.rubyforge.org/). I think I&#8217;ve got it hacked in, at least to the &#8220;good enough&#8221; stage.

The first big change was to change the `@trigger` instance variable for the `Project` class from a single trigger to an array of triggers. I modified its name to `@triggers` to reflect this change. So in the `initialize` method for the `Project` class, instead of saying: 

> <pre>@trigger = ChangeInSourceControlTrigger.new</pre> We now say this: 

> <pre>@triggers = [ChangeInSourceControlTrigger.new]</pre> Next, I modified the 

`build<em>if</em>necessary` method to collect information from all of the triggers about which revisions need to be built. 

> <pre>revisions = []
@triggers.each { |trigger| revisions += trigger.get<em>revisions</em>to<em>build(self) }
revisions = revisions.uniq.sort
if revisions.empty?
  ...</pre>
</blockquote>
I also made a change to the <code>triggered&lt;/em>by</code> method for the <code>Project</code> class so that it accepts multiple triggers, and so that it always adds triggers to the existing set (instead of replacing them). Here&#8217;s what my modified version of <code>triggered&lt;em>by</code> looks like.


<blockquote>
  <pre>def triggered&lt;/em>by(*things)
  things.each do |thing|
    if thing.is_a?(String) || thing.is_a?(Symbol)
      @triggers &lt;&lt; SuccessfulBuildTrigger.new(thing)
    else
      @triggers &lt;&lt; thing
  end
end</pre>
  
</blockquote>
This allows me to declare dependencies in my 

<code>cruise_config.rb</code> file like so:


<blockquote>
  <pre>project.triggered_by 'projectA', 'projectB', 'projectC'</pre>
  
</blockquote>
I had to modify the logic 

<code>get_revisions_to_build</code> method for the <code>SuccessfulBuildTrigger</code> class a little bit, so that it wouldn&#8217;t return any build numbers from triggering projects that were older than the latest build of the &#8220;triggered&#8221; project. Here&#8217;s what that block looks like now.


<blockquote>
  <pre>if last_successful_build.nil? || project.find_build(last_successful_build.label)
  []
elsif project.last_build && project.last_build.label.to_i &gt;= last_successful_build.label.to_i
  []
else
  [Revision.new[last_successful_build.label]
end</pre>
  
</blockquote>
The last step was to add the 

<a href="http://www.catb.org/jargon/html/S/spaceship-operator.html">spaceship operator</a> to the <code>Revision</code> class, so that I can sort arrays of them.


<blockquote>
  <pre>def &lt;=&gt;(other)
  number.to_i &lt;=&gt; other.number.to_i
end</pre>
  
</blockquote>
Note that the 

<code>number</code> attribute for the <code>Revision</code> class sometimes refer to an integer, and other times to a string. I suspect that this is a bug, but calling <code>to_i</code> on it does the trick for this purpose.</p>



<p>
  It took a bit of experimenting to get it right, but this <em>seems</em> to be working properly now. It took maybe a couple of hours to get it working, and the code was easy to read and understand.
</p>