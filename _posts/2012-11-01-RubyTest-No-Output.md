---
layout: post
title: RubyTest Displays No Output
time: '23:43:30'
day: 01
month: November
year: 2012
---

When using RubyTest in Sublime Text 2 to run my tests I initially received an error:
{% highlight bash %}
    /bin/sh: rspec: command not found
{% endhighlight %}
Further research suggested that due to the use of rvm I needed to cd into the rails project directory and then run
{% highlight bash %}
    subl .
{% endhighlight %}
Once I did that I no longer received an error but I also received no output at all. Using
{% highlight bash %}
    ctrl + `
{% endhighlight %}
I was able to determine a different error regarding UnicodeDecodeError. Turns out it is most likely linked to my used of bash-powerline and a fix was mentioned to the Sublime Core team. In the interim changing the code on line 45 of /Users/metafour/Library/Application Support/Sublime Text 2/Packages/Default/exec.py from
{% highlight python %}
    proc_env[k] = os.path.expandvars(v).encode(sys.getfilesystemencoding())
{% endhighlight %}
to
{% highlight python %}
    proc_env[k] = os.path.expandvars(v.decode(sys.getfilesystemencoding())).encode(sys.getfilesystemencoding())
{% endhighlight %}
seems to fix the problem.


    
