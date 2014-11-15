---
layout: post
title: "Chef: Application Cookbook"
time: '12:09:45'
day: 23
month: September
year: 2014
---

The opscode application cookbook doesn't like working with branches and this has been going on for a while now:  

http://lists.opscode.com/sympa/arc/chef/2013-07/msg00334.html

https://github.com/opscode/chef/issues/1563

Only solution still seems to be `shallow_clone false`
