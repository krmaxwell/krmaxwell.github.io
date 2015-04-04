---
layout: post
title: "Python tricks: dictionary setdefault and addict"
categories: Python, Programming
---

_This post was written by guest blogger [Kevin "@bfist" Thompson](https://twitter.com/bfist)
who is too lazy to start his own blog and just camps out on others like a homeless
bass player crashing on friend's couches._

One of the cooler things I get to tell people is that I'm one of the people behind
the [VERIS Framework](https://github.com/vz-risk/veris) and the
[VERIS Community Database](https://github.com/vz-risk/vcdb). VERIS is a schema for
describing information security incidents that affect an organization and incidents
are represented as JSON objects. This means that I spent a lot of time in python
manipulating dictionaries and I've picked up a couple of methods that are pretty
helpful.

# dict.get()
This was my favorite method in all of python for quite a while. This is what you
use when you need to lookup a key from a dictionary but you're not positive that
the key is actually there. So if you find yourself checking to see if a key is
present and then using the key, you can replace a lot of that by using dict.get().

```
myDict = {'fname':'Kevin'}
if 'lname' in myDict:
  print("My last name is {}".format(myDict['lname']))
else:
  print("My last name is undefined")
```

Can be replaced with this code:

```
myDict = {'fname':'Kevin'}
print("My last name is {}".format(myDict.get('lname','undefined')))
```

# dict.setdefault()
We use `dict.get()` to gracefully access keys that don't exist. Another use case
that comes up a lot is adding a key if it isn't present. Setdefault
can really reduce the amount of code that you have to write if you need to add
keys on the fly. The `dict.setdefault` method will return a default value the same
way that `dict.get()` does but also adds the default value to the dictionary if
it was missing.

```
myDict = {'fname':'Kevin'}
print("My first name is {}".format(myDict.setdefault('fname','Kevin')))
print("My last name is {}".format(myDict.setdefault('lname','Thompson')))
print(myDict) # {'lname': 'Thompson', 'fname': 'Kevin'}
```

## What about defaultdict?
The `collections` library in python gives us `defaultdict` which does something
pretty similar to what we have done above. With `defaultdict` we create a dictionary
and define a default container that will apply to *every* missing key. So if you want
to create a dictionary that will hold other dictionaries you can do something like this:

```
from collections import defaultdict
myDict = defaultdict(dict())
myDict['home']['state'] = "MN"
# {'home': {'state': 'MN'}}
```

This can make your code more concise if you're only going to be adding the same
kind of container as subkeys in a dictionary. Where`dict.setdefault()` shines
is when you need to create *deeply-nested* dictionaries or dictionaries that
might not all have the same type. You see, you can't create a defaultdict of
defaultdicts.

```
>>> myDict = defaultdict(defaultdict(dict))
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: first argument must be callable
```

With `dict.setdefault()` I can do something like this to put a value deep into a
dictionary even if I haven't created all the keys yet.

```
incident = {}
incident.setdefault('action', {}).setdefault('hacking', {}).setdefault('variety', []).append("Brute force")
# {'action': {'hacking': {'variety': ['Brute force']}}}
```

This really changed my old way of doing it:
```
incident = {}
if 'action' not in incident:
  incident['action'] = {}
if 'hacking' not in incident['action']:
  incident['action']['hacking'] = {}
if 'variety' not in incident['action']['hacking']:
  incident['action']['hacking']['variety'] = []
incident['action']['hacking']['variety'].append("Brute force")
```

# Addict
If you get irritated from typing those brackets all the time and you really wish
you had a defaultdict of defaultdicts of yet more defaultdicts (defaultdicts all the way
down) then you should try out [addict](https://github.com/mewwts/addict).

`addict` lets you access keys in a dictionary by using the dot notation used in
javascript which is a whole lot faster to type.

When you define a `Dict` object (notice the capitalization) you get an object
that is defaultdict all the way down. So I can really tighten up the code for
deeply nested objects by combining `addict` with `setdefault`.

```
from addict import Dict
incident = Dict()
incident.action.hacking.setdefault('variety', []).append("Brute force")
```
