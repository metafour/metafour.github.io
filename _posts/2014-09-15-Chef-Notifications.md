---
layout: post
title: Chef Notifications
time: '12:57:48'
day: 15
month: September
year: 2014
---

Chef notifications can use the `notifies` attribute to notify other resources about actions they may need to take either `:immediately` or at the end of the chef-client run by using the `:delayed` option. This seems to allow one to notify an existing resource on the current node but what about notifying another node that something needs to happen? Having another node call chef-client on an existing node would require that a user exists on the calling node that has SSH access to the called node.
