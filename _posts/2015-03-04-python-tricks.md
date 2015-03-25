---
layout: post
title: "Data sets in Python"
categories: Python, Programming
---

Last year, my buddy [Kevin Thompson](https://twitter.com/bfist) and I submitted a talk to Pycon 2015. It didn't get accepted, so I thought I'd write a few blog posts with some of the material.

Python has a lot of data types that make working with data sets a real pleasure.

- dict.get
- list comprehensions

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
