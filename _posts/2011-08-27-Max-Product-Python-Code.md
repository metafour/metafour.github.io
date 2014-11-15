---
layout: post
title: Max Product Python Code
time: '21:24:34'
day: 27
month: August
year: 2011
---

	#!/usr/bin/python

	n = raw_input('n = ')

	n = int(n)

	if n % 3 == 1:
		print "f(n) = %d" % (3**(n//3-1) * 2**2)
	elif n % 3 == 2:
		print "f(n) = %d" % (3**(n//3) * 2)
	else:
		print "f(n) = %d" % (3**(n//3))
