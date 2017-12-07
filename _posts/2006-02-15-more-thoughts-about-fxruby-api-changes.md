---
id: 133
title: More Thoughts About FXRuby API Changes
date: 2006-02-15T16:10:52+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=133
permalink: /2006/02/15/more-thoughts-about-fxruby-api-changes/
categories:
  - FXRuby
---
Per the last few posts, I&#8217;m thinking a lot about potential API changes for the upcoming release of &#8220;FXRuby&#8221;:http://www.fxruby.org/ 1.6.

When Jeroen began developing &#8220;FOX&#8221;:http://www.fox-toolkit.com/ way back when, most of the available C++ compilers didn&#8217;t have great support for C++ namespaces. As a result, FOX classes ended up with an &#8220;FX&#8221; prefix to avoid name clashes. That is of course of little concern to Rubyists, as the @Module@ construct provides (among other things) a way of maintaining separate namespaces for different code libraries. Despite this, the FXRuby classes followed the standard FOX naming conventions, and so we end up with the visually jarring situation that the fully-qualified name for FOX&#8217;s button class is @Fox::FXButton@.

So one of the major changes that I&#8217;m considering for FXRuby 1.6 is renaming the classes by removing the &#8220;FX&#8221; prefix from the existing class names and method names. @Fox::FXButton@ becomes @Fox::Button@, @Fox::FXLabel@ becomes @Fox::Label@, and so on. There&#8217;s no _technical_ reason to make such a change, but it would be more aesthetically pleasing. One disadvantage of this change would be that the FOX and FXRuby class names would no longer quite match up (although it wouldn&#8217;t be much of a brain twister to convert between the two). A more significant disadvantage is that it would break a lot of existing code. This problem could probably be alleviated by using @const_missing@, e.g.


    <code lang="ruby">
    module Fox
      def self.const&lt;em>missing(class&lt;/em>id)
        name = "FX" + class&lt;em>id.to&lt;/em>s
        if const&lt;em>defined? name
          const&lt;/em>get(name)
        else
          super
        end
      end
    end</code>

Another change that I&#8217;m considering is switching from CamelCase method names to method names with underscores, so that @beginWaitCursor@ becomes @begin_wait_cursor@. As with the proposed change for the class name, the potential for code breakage could be alleviated by the careful use of @method_missing@, with something along the lines of:


    <code lang="ruby">
    class FXObject
      def method&lt;em>missing(method&lt;/em>id, &lt;em>args)
        camel&lt;em>case = method&lt;/em>id.to&lt;em>s
        while camel&lt;/em>case =~ /([^_]&lt;/em>)&lt;em>(.)(.*)/ 
          camel&lt;/em>case = $1 + $2.upcase + $3
        end
        if respond&lt;em>to? camel&lt;/em>case
          self.send(camel&lt;em>case.to&lt;/em>sym, *args)
        else
          super
        end
      end
    end</code>

Note that this idea was &#8220;inspired&#8221; by Richard Dale&#8217;s work on Ruby/Qt.