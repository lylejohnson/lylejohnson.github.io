---
id: 258
title: Easy Charts in FXRuby with the Google Chart API
date: 2008-06-05T21:43:36+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=258
permalink: /2008/06/05/easy-charts-in-fxruby-with-the-google-chart-api/
categories:
  - FXRuby
  - Ruby
tags:
  - chart
  - FXRuby
  - google
  - graph
  - Ruby
---
[InfoQ](http://www.infoq.com/) has just published an [article](http://www.infoq.com/articles/bass-google-charts-gchartrb "Intro to Google Charts and gchartrb") written by Matthew Bass that introduces the [Google Chart API](http://code.google.com/apis/chart/ "Google Chart API Developer's Guide") and the [gchartrb](http://code.google.com/p/gchartrb/ "Ruby wrapper around the Google Chart API") library, which you can use to programmatically generate URLs for use with Google Chart. It&#8217;s very easy to use this library to generate charts in your [FXRuby](http://www.fxruby.org/) applications. First, install the [gchartrb](http://code.google.com/p/gchartrb/ "Ruby wrapper around the Google Chart API") gem: 

> <pre>$ <strong>sudo gem install gchartrb</strong></pre> You&#8217;ll need to poke around the 

[gchartrb](http://code.google.com/p/gchartrb/ "Ruby wrapper around the Google Chart API") documentation to decide just what kinds of charts are supported; for this example, we&#8217;ll just use a bar chart example from Matthew&#8217;s article:

<div class="wp_syntax">
  <table>
    <tr>
      <td class="code">
        <pre class="ruby" style="font-family:monospace;"><span style="color:#9966CC; font-weight:bold;">def</span> bar_chart
  <span style="color:#6666ff; font-weight:bold;">GoogleChart::BarChart</span>.<span style="color:#9900CC;">new</span><span style="color:#006600; font-weight:bold;">&#40;</span><span style="color:#996600;">'600x200'</span>, <span style="color:#996600;">'My Chart'</span>, <span style="color:#ff3333; font-weight:bold;">:vertical</span><span style="color:#006600; font-weight:bold;">&#41;</span> <span style="color:#9966CC; font-weight:bold;">do</span> <span style="color:#006600; font-weight:bold;">|</span>bc<span style="color:#006600; font-weight:bold;">|</span>
    bc.<span style="color:#9900CC;">data</span> <span style="color:#996600;">'Trend 1'</span>, <span style="color:#006600; font-weight:bold;">&#91;</span><span style="color:#006666;">5</span>,<span style="color:#006666;">4</span>,<span style="color:#006666;">3</span>,<span style="color:#006666;">1</span>,<span style="color:#006666;">3</span>,<span style="color:#006666;">5</span><span style="color:#006600; font-weight:bold;">&#93;</span>, <span style="color:#996600;">'0000ff'</span>
    bc.<span style="color:#9900CC;">data</span> <span style="color:#996600;">'Trend 2'</span>, <span style="color:#006600; font-weight:bold;">&#91;</span><span style="color:#006666;">1</span>,<span style="color:#006666;">2</span>,<span style="color:#006666;">3</span>,<span style="color:#006666;">4</span>,<span style="color:#006666;">5</span>,<span style="color:#006666;">6</span><span style="color:#006600; font-weight:bold;">&#93;</span>, <span style="color:#996600;">'ff0000'</span>
    bc.<span style="color:#9900CC;">data</span> <span style="color:#996600;">'Trend 3'</span>, <span style="color:#006600; font-weight:bold;">&#91;</span><span style="color:#006666;">6</span>,<span style="color:#006666;">5</span>,<span style="color:#006666;">4</span>,<span style="color:#006666;">4</span>,<span style="color:#006666;">5</span>,<span style="color:#006666;">6</span><span style="color:#006600; font-weight:bold;">&#93;</span>, <span style="color:#996600;">'00ff00'</span>
  <span style="color:#9966CC; font-weight:bold;">end</span>
<span style="color:#9966CC; font-weight:bold;">end</span></pre>
      </td>
    </tr>
  </table>
</div>

The `to<em>escaped</em>url` method for the `BarChart` object returns a URL from which we can retrieve the chart image data in PNG format. We can in turn use that data to construct an `FXPNGImage`, and place it inside an `FXImageFrame`:

<div class="wp_syntax">
  <table>
    <tr>
      <td class="code">
        <pre class="ruby" style="font-family:monospace;">FXImageFrame.<span style="color:#9900CC;">new</span><span style="color:#006600; font-weight:bold;">&#40;</span><span style="color:#0000FF; font-weight:bold;">self</span>, <span style="color:#0000FF; font-weight:bold;">nil</span>, <span style="color:#ff3333; font-weight:bold;">:opts</span> <span style="color:#006600; font-weight:bold;">=&gt;</span> LAYOUT_FILL<span style="color:#006600; font-weight:bold;">&#41;</span> <span style="color:#9966CC; font-weight:bold;">do</span> <span style="color:#006600; font-weight:bold;">|</span>f<span style="color:#006600; font-weight:bold;">|</span>
  f.<span style="color:#9900CC;">image</span> = FXPNGImage.<span style="color:#9900CC;">new</span><span style="color:#006600; font-weight:bold;">&#40;</span>app, <span style="color:#CC0066; font-weight:bold;">open</span><span style="color:#006600; font-weight:bold;">&#40;</span>bar_chart.<span style="color:#9900CC;">to_escaped_url</span>, <span style="color:#996600;">"rb"</span><span style="color:#006600; font-weight:bold;">&#41;</span>.<span style="color:#9900CC;">read</span><span style="color:#006600; font-weight:bold;">&#41;</span>
<span style="color:#9966CC; font-weight:bold;">end</span></pre>
      </td>
    </tr>
  </table>
</div>

The result is a nice little bar chart, as shown here: 

<p style="text-align:center;">
  <img src="http://lylejohnson.name/blog/wp-content/uploads/2008/06/google-charts-demo1.png" border="0" alt="google_charts_demo.png" width="320" height="129" />
</p> For reference, here&#8217;s the complete program: