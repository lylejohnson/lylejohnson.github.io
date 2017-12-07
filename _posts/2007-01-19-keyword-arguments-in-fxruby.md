---
id: 164
title: Keyword Arguments in FXRuby
date: 2007-01-19T16:03:29+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=164
permalink: /2007/01/19/keyword-arguments-in-fxruby/
categories:
  - FXRuby
---
FXRuby 1.6.5 (coming real soon now) will introduce preliminary, experimental support for using keyword-style arguments in FXRuby method calls. The initial implementation of this feature will only work for class constructors (i.e. the &#8220;new&#8221; class methods), but the intent is to gradually extend this feature so that it covers all FXRuby methods.

What this means in practice is that for calls to methods that have one or more optional arguments, you can replace all of the optional arguments with a hash that sets only the values for which the default isn&#8217;t appropriate. So, for example, consider a typical call to `FXMainWindow.new`: 

> `main = FXMainWindow.new(app, "Title Goes Here", nil, nil,
                        DECOR_ALL, 0, 0, 800, 600)` In this case, the programmer wants to set the initial window width and height to 800 and 600. In order to do that (with the current release of FXRuby), however, she&#8217;s required to fill in all of the optional arguments in between the window title string and the width and height values. As anyone who&#8217;s worked with FXRuby for any amount of time will tell you, it&#8217;s easy to accidentally leave out one of those intermediate arguments and it can be difficult to figure out what&#8217;s wrong afterwards.

Now consider how this method call could be written using the new keyword arguments support. First, the programmer would need to require the keyword arguments library: 

> `require 'fox16/kwargs'` Then she would look up the API documentation for the `FXMainWindow#initialize` method (e.g. [here](http://www.fxruby.org/doc/api/classes/Fox/FXMainWindow.html)) and see that the names of the width and height arguments are, in fact, &#8220;width&#8221; and &#8220;height&#8221;. Armed with that information, she would be able to rewrite the previous code as: 

> `main = FXMainWindow.new(app,
                        "Title Goes Here",
                        :width => 800,
                        :height => 600)` Here, the programmer has omitted the intermediate optional arguments (thus accepting their default values) and specified only the width and height values. This code is obviously a lot more readable and maintainable.

It is important to observe the difference between required and optional arguments when using this feature. If the API documentation for a particular method doesn&#8217;t indicate that an argument has a default value, then it is by definition not an optional argument. So one could **not** write the previous example as, e.g. 

> `main = FXMainWindow.new(app,
                        :width => 800,
                        :title => "Title Goes Here",
                        :height => 600)` This example is incorrect because the title argument is required, and it must be the second argument in the call. Obviously, this means that the optional arguments in a method call (if they&#8217;re specified) will always follow all of the required arguments.

Finally, note that the keyword arguments feature has been implemented so that it&#8217;s backwards-compatible with the current positional arguments (or it&#8217;s intended to be, at any rate). What that means is that you can immediately start making use of this feature in your existing code, even if you don&#8217;t have time to update all of the method calls to use keyword arguments.

I expect to release FXRuby 1.6.5 with this feature very soon, possibly as soon as this weekend. As stated in the opening paragraph, the initial release of this feature will only work for class constructors (i.e. the &#8220;new&#8221; class methods), but the intent is to gradually extend this feature so that it covers all FXRuby methods. All feedback/questions/comments are welcome and appreciated.