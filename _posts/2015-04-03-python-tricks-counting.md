---
layout: post
title: "Python tricks: counting"
categories: Python, Programming
---

_first in an occasional series_

Last year, my buddy [Kevin Thompson](https://twitter.com/bfist) and I submitted a talk to Pycon 2015. It didn't get accepted, so I thought I'd write a few blog posts with some of the material.

When we started working with Python, like a lot of folks, we went through a few code tutorials and then immediately got to work writing **ROCK SOLID PRODUCTION CODE.** Well, we immediately started writing code, anyway. Along the way, we learned some tricks the hard way. This series explores a few of those tricks. Advanced programmers will already know most of these, but hopefully newer programmers will learn a few things that can make their lives a bit easier.

Python has a lot of data types that make working with data sets a real pleasure. Some specific analysis work, though, can occasionally get a little wonky. And so clever programmers have made our lives even easier by implementing features that keep the simple things simple.

## [collections.Counter](https://docs.python.org/2/library/collections.html#collections.Counter)

### Use case: count objects (e.g. strings)

So imagine you're processing some data and you want to count how often you see certain objects (like strings in a list). This gets unwieldy quickly, especially if you have additional associated logic. But `collections.Counter()` provides a handy Pythonic way to implement this pattern.

### Old and busted

{% highlight python %}
counts = dict()
for each in data:
  if each in counts:
    counts[each] += 1
  else:
    counts[each] =1
{% endhighlight %}

### New hotness

{% highlight python %}
counts = collections.Counter()
for each in data:
  counts[each] += 1
{% endhighlight %}

## [List comprehensions](https://docs.python.org/2/tutorial/datastructures.html#list-comprehensions)

### Use case: simple for loop

We can simplify this even further with a _list comprehension_. In general, you place a `for` loop inside a pair of square brackets, with the expression for each result at the beginning.

### Old and busted:

{% highlight python %}
counts = collections.Counter()
for each in data:
  counts[each] += 1
{% endhighlight %}

### New hotness:

{% highlight python %}
[counts[each]+=1 for each in data]
{% endhighlight %}

## Upcoming tricks

Dictionaries have lots of additional features that can help with complex, nested structures. Every week I find another, so that will definitely be a fun upcoming article. Since a number of my projects involve a good bit of web scraping, I'll share a lot of things I've learned there, too.
