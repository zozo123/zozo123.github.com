---
layout: post
title: "Generating list's subsets - Python"
description: ""
category: ""
tags: []
---
{% include JB/setup %}

Once a month a <strong>"how to generate all subsets in python"</strong> question appers on <a href="http://www.stackoverflow.com">stackoverflow</a>.

The OP ("Original poster") of the question apparently found an itertools based implementation.

But what he really looked for is an algorithm to create all the subsets.

There are fewer solutions on <a href="http://www.stackoverflow.com">stackoverflow</a> that implements the naive alogrithm in python.

Unfortuntally I couldn't find the awesome and elegant original post, but I rewrote it somehow and post it here.

<strong>The naive implementation:</strong>

{% highlight python %}
def naiveSubsetGen(s):
	subsets = [[]]
	for i in s:
		subsets = subsets + [[i] + j for j in subsets]
	return subsets
{% endhighlight %}


<strong>The itertools solution:</strong>

{% highlight python %}
from itertools import combinations

def itertoolsSubsetGen(s):
	return [[]] + [list(j) for i in range(len(s)) for j in combinations(s, i+1)]
{% endhighlight %}

I benchmarked both of them:

{% highlight python %}
itertoolTestStr=\
"""
for i in xrange(5,25,5):
	itertoolsSubsetGen(range(i+1))
"""

naiveTestStr=\
"""
for i in xrange(5,25,5):
	naiveSubsetGen(range(i+1))
"""

setupItertool = """from __main__ import itertoolsSubsetGen"""
setupNaive = "from __main__ import naiveSubsetGen"
if __name__=='__main__':
	import timeit
	print "naive time:", timeit.timeit(naiveTestStr, setup=setupNaive, number=4)
	print "itertools time:",timeit.timeit(itertoolTestStr, setup=setupItertool, number=4)

{% endhighlight %}

<h4>Results:</h4>

{% highlight python %}
naive time: 8.25990605354
itertools time: 12.5649080276
{% endhighlight %}
