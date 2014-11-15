---
layout: post
title: Rails Tutorial
time: '20:54:30'
day: 01
month: November
year: 2012
---

Looking towards the future I've decided to learn Ruby on Rails. I started out by doing the [Rails for Zombies](http://railsforzombies.org) course and consequently the [Try Ruby](http://tryruby.org) course. While they both incorporate an interesting set of exercises they don't really develop any understanding of the material. I then moved onto the [Ruby on Rails Tutorial](http://ruby.railstutorial.org). This pushed me to look back into using [vagrant](http://vagrantup.com) for virtual environments as well as expanding the use of tools such as vim, tmux, bash scripting, python, and the list goes on.

#### vagrant, iterm2, vim, and tmux

I decided to look into vagrant for running some linux VM's so that I could leave my mac environment pristine. This led to using tmux and vim on the command line as a development environment. As much as I like vim this was taking a step back to when I was using linux exclusively. Setting up panes in tmux, configuring this and that, and then not being comfortable with the results. Therefore, I decided to switch to the tutorial's recommended setup of [Sublime Text 2](http://sublimetext.com).

#### Sublime Text 2 and Transmit

In order to gain access to the files in the development environment on the VM I decided to use Tranmit's disk feature. Mounting the home directory of the vagrant user and then loading the rails folder into sublime. I installed the RubyTests package and then tried to run a test only to have it fail due to not actually being in the ruby environment on the VM.

#### RVM and pow.cx

I'm now going to move to using RVM and pow.cx on the local Mac installation to see how it goes.