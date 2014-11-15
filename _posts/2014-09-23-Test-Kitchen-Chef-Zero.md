---
layout: post
title: Using search() with test-kitchen and chef-zero
time: '10:16:41'
day: 23
month: September
year: 2014
---

When using [test-kitchen](http://kitchen.ci) for testing [Chef](http://getchef.com) cookbooks you may run into the following error:  
`I cannot read /tmp/kitchen/client.pem, which you told me to use to sign requests!`  
This results from using the `chef-solo` provisioner and having a `search()` function call in your recipe. `test-kitchen` is trying to reach the Chef server but it can't since it doesn't exist. Switch over to using `chef-zero` and put node JSON data in `test/integration/nodes` that can be searched against.

However, if your recipe is searching for a node based on a recipe, test-kitchen doesn't properly return the nodes so you may need to detect if you're running in a different environment within your cookbook and react accordingly.
