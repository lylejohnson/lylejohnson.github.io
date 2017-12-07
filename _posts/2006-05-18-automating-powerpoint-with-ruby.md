---
id: 145
title: Automating PowerPoint with Ruby
date: 2006-05-18T10:35:42+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=145
permalink: /2006/05/18/automating-powerpoint-with-ruby/
categories:
  - Ruby
---
I knew that Ruby had some support for Windows OLE Automation &#8212; I vaguely remembered skimming over that part in _Programming Ruby_, once upon a time &#8212; but I&#8217;d honestly just never had any need to use it.

Well, that changed today. A client needed some code, as part of a more complicated tool chain, to open a named PowerPoint presentation and then save it as HTML. Not a complicated request, to be sure, but something that suggested the use of PowerPoint&#8217;s Automation capabilities. After a little bit of futzing around, here&#8217;s the code that I came up with:

> <pre>require 'win32ole'</p>



<pre><code>class PowerPoint; end

ppt = WIN32OLE.new('powerpoint.application')
WIN32OLE.const_load(ppt, PowerPoint)
ppt.Activate
ppt.Presentations.Open('FileName' =&gt; ppt_filename)
ppt.ActivePresentation.SaveAs('FileName' =&gt; html_filename,
                              'FileFormat' =&gt; PowerPoint::PpSaveAsHTML)
ppt.ActivePresentation.Close
ppt.Quit
</code></pre>



<p>
  </pre></blockquote>I&#8217;m sure that it could be done in even fewer lines of code if I knew what I was doing. For example, I don&#8217;t know whether the call to <tt>Activate</tt> is even required, but it doesn&#8217;t seem to hurt. The issue of how to access an application&#8217;s constants (like the <strong>ppSaveAsHTML</strong> constant used in this code) threw me for a bit since that topic&#8217;s not covered in <em>Programming Ruby</em>, but a quick look at <a href="http://www.ruby-doc.org/stdlib/libdoc/win32ole/rdoc/classes/WIN32OLE.html">the RDoc</a> uncovered the solution.
</p>