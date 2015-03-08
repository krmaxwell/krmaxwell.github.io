---
layout: post
title: "Data sets in Python"
categories: Python, Programming
---

Last year, my buddy [Kevin Thompson](https://twitter.com/bfist) and I submitted a talk to Pycon 2015. It didn't get accepted, so I thought I'd write a few blog posts with some of the material.

Python has a lot of data types that make working with data sets a real pleasure.

- collections.Counter
- dict.get
- list comprehensions

Use case: count objects (e.g. strings)

Old and busted:

{% highlight python %}
counts = dict()
for each in data:
  if each in counts:
    counts[each] += 1
  else:
    counts[each] =1
{% endhighlight %}

New hotness:
{% highlight python %}
counts = collections.Counter()
for each in data:
  counts[each] += 1
{% endhighlight %}

Use case: nested data structures

Old and busted:
{% highlight python %}
if 'foo' in data and 'bar' in data['foo'] and 'baz' in data['foo']['bar']:
  stuff(data['foo']['bar']['baz'])
{% endhighlight %}

New hotness:
{% highlight python %}
if data.get('foo', '').get('bar', '').get('baz', ''):
  stuff(data['foo']['bar']['baz'])
{% endhighlight %}

Use case: simple for loop

Old and busted:
{% highlight python %}
counts = collections.Counter()
for each in data:
  counts[each] += 1

New hotness:
{% highlight python %}
[counts[each]+=1 for each in data]
{% endhighlight %}
