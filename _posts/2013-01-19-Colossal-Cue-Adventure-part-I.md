---
layout: post
title: Colossal Cue Adventure part I
time: '13:49:42'
day: 19
month: January
year: 2013
published: NO
---

Checking [Hacker News](http://news.ycombinator.com) yesterday I saw this programming text adventure called [Colossal Cue Adventure](http://adventure.cueup.com) linked on the front page and thought I'd check it out. Since I've been trying to learn Ruby and Ruby on Rails I figured I could use this as a way to get some practice coding. Let us begin by taking a look at the first puzzle.

The context of the puzzle has us looking at an implementation of VAX's MTH$RANDOM that is running a Roulette wheel. Since the outcome of the game is based on this pseudo-random number generator we should be able to determine where to place our bets given the information that the first three numbers in the sequence are 6, 19, and 16. (The output of MTH$RANDOM is % 36 so that we are limited to a set of numbers that roughly matches a roulette wheel.)

The basic implementation of VAX's MTH$RANDOM is as follows:

\\\[ x_{n+1} = ax_{n} + c % 2^{32} \\\]

where \\\( a = 69069\\\), \\\(x_{1} = 1\\\) and \\\(c = 1 \\\).



