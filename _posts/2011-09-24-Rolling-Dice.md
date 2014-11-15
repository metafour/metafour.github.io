---
layout: post
month: September
day: 24
year: 2011
published: NO
---

If I take a 20-sided die and roll it 6 times the probability that I will roll a single number exactly 4 times is given by the following expression.

$$ \binom{6}{4} \biggl(\frac{1}{20}\biggr)^{4} \biggl(\frac{19}{20}\biggr)^{2} = 0.000084609375 \approx \frac{84}{1,000,000} $$

While this is a small probability it is not impossible. Therefore I wrote some *ruby* code to simulate this exact situation.

### Code ###

{% highlight ruby %}
    def rolldie(sides)
        rand(sides) + 1
    end
    
    sides = 20
    success = 20
    successes = 0
    trials = 6
    roll = []
    counter = 0
    
    while successes != 4
    
      successes = 0
    
      1.upto(trials) { |i|
        roll[i] = rolldie(sides)
        successes += 1  if roll[i] == success
      }
    
      counter += 1
    
    end
    
    1.upto(trials) { |i| 
      puts roll[i]
    }
    
    puts counter
{% endhighlight %}

### Results ###

The first six digits in each grouping are the results of each roll. The final number in 
each grouping is the total number of trials completed to get the desired result.

    20
    20
    11
    19
    20
    20
    686
    
    20
    20
    20
    8
    20
    19
    2171
    
    20
    20
    11
    20
    6
    20
    65502
    
    20
    20
    20
    20
    18
    17
    14672

As you can see it is not impossible and actually isn't as rare as you might think.
