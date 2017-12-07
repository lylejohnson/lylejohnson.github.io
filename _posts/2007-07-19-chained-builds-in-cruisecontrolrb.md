---
id: 215
title: Chained Builds in CruiseControl.rb
date: 2007-07-19T17:17:21+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=215
permalink: /2007/07/19/chained-builds-in-cruisecontrolrb/
categories:
  - Ruby
---
The good news is that there is some code in the trunk for [CruiseControl.rb](http://cruisecontrolrb.rubyforge.org/ "CruiseControl.rb Home Page") that addresses the need for chained builds. If you&#8217;re using that version, you can for example specify that a successful build of ProjectA should trigger a build of ProjectB. 

> <pre># cruise<em>config.rb for ProjectB
Project.configure do |project|
  project.triggered</em>by 'ProjectA'
end</pre> The bad news &#8212; which I didn&#8217;t realize until I had modified several (OK, 

_all_) of my `cruise_config.rb` files &#8212; is that: 

  1. A project can only be triggered by one other project. If ProjectB depends on both ProjectA and ProjectC, too bad.
  2. Specifying that ProjectB depends on ProjectA disables the default build trigger, which checks for changes to ProjectB&#8217;s Subversion repository. Looks like I&#8217;m going to need to look into the source code and see if there&#8217;s some way to hack in dependencies on multiple triggers. At a minimum, I&#8217;d want to be able to specify that a project depends on both a 

`ChangeInSourceControlTrigger` and one or more `SuccessfulBuildTrigger`s.