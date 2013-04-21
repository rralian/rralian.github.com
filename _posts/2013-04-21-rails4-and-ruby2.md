---
layout: post
title: "Rails4 and Ruby2"
description: "Install Problems and the Fix"
category: 
tags: [rails4, rvm, ruby2, libyaml]
---
{% include JB/setup %}

> **tl;dr** If you find yourself in a möbius strip of installing libyaml
> and reinstalling ruby with rvm, instead try deleting libyaml and letting 
> rvm handle installing libyaml itself.

## Before It Went All Wrong

I had decided to spend some time with Rails4. And if I'm going to play on the edge, I might as well install Ruby 2.0.0. RVM makes it pretty easy. No sweat.

Well, if you've ever set up ruby or rails on a new machine, you may have found a no-sweat situation turn into a surprisingly sweaty time. That's what happened to me.

My journey included upgrading my version of xcode, reinstalling the xcode command-line tools, removing MacPorts (which I had used once, but switched to Homebrew), blowing away all MacPorts diretories, installing ssl and libyaml packages, installing psych, reinstalling my rubies (either with reinstall or uninstall and then separate install) time and time again. I even at one point blew away rvm entirely and reinstalled it. I tried all different variations of solutions to the common gcc problem all OSX rails developers are familiar with. I'd say I tried about a dozen different suggestions from [forum posts like this one](http://stackoverflow.com/questions/9434002/how-to-solve-ruby-installation-is-missing-psych-error).

But no matter what I did, I was in a loop of installing libyaml, then reinstalling rubies, and then having rvm complain that I was missing libyaml libraries (psych). At one point I got through the ruby installation without an error, but when I created a rails4 project and did a bundle install, the first thing it complained about was a lack of the psych libyaml libraries.

The eventual solution was to disregard what the error messages were saying (that you need to install libyaml) and instead I *uninstalled* libyaml. I set up rvm to [enable autolibs](https://rvm.io/rvm/autolibs/), which is a feature that allows rvm to more directly manage dependencies on OSX. And then when I installed ruby *without* having libyaml installed, rvm was finally able to install libyaml where it wanted it.

I hope this can save you a little time.