---
layout: post
title: "Maximum likelihood decoding in Python"
date: 2015-01-27 08:30:00 -0600
categories: [Programming, Python, Math]
---

As [previously discussed]({% post_url 2015-01-14-tech-goals-for-2015 %}), I started reading [A Book of Abstract Algebra](http://www.amazon.com/gp/product/0486474178/) by [Charles Pinter](http://charlespinter.com) this year. [Reading a math book](http://math.stackexchange.com/questions/279079/how-to-read-a-book-in-mathematics) isn't the same as reading most prose. You have to engage with the text in a different way, **doing** at least as much as **reading**. Among other things, many books include much of their content in the exercises. *Pinter* definitely is one of those books.

The book surprised me by having more applications (and earlier in it) than I expected. Thus, I started a [repository](https://github.com/technoskald/abstract-algebra) for code I write for this book. Automata appears in the second chapter, for example. One of the problem sets in particular grabbed my attention: [maximum-likelihood decoding](http://nbviewer.ipython.org/github/technoskald/abstract-algebra/blob/master/Chapter%203%20Exercise%20G.ipynb). The rest of this post mostly explains to my future self why and how I did what I did.

> Note to self: get [MathJax](http://www.mathjax.org) working in Jekyll at some point.

## Theory

Understanding the theory here involves two key realizations.
1. Only certain codewords are valid, due to the use of specific bits within the word as parity checks (a form of error checking).
1. The distance between any two codewords (the weight their XOR) is the minimum number of bit flips to change one codeword into another.

Therefore, if we receive an invalid word, we check to see which valid codeword is "nearest" to it. In a code where the minimum distance is 2, that means that flipping a single bit in a word can **always** be detected. Flipping two bits, though, may mean that we get another "valid" codeword in error. Larger minimum distances help. If the minimum distance is *m*, then we can always detect errors of *m-1* bits (because those can never result in another valid codeword). Even better, we can **correct** errors of *(m-1)/2* bits or fewer. We do this by finding the minimum distance between the received word and the valid codewords (XORing and calculating the weight), then correcting to the nearest one.

## Code

This exposed some gaps in my knowledge of Python around bitwise operators. It didn't help that the problem labels the bits in an awkward fashion (at least to my programmer-mind), since it starts by labeling the most significant bit *a<sub>1</sub>*. I don't doubt that Python has easier ways to do all this, but I couldn't find them and wanted to focus on the math more than the code. So first I wrote a quick function to slice out a given bit from the codeword:

{% highlight python %}
  def bit(num, pos, width):
    # assume num is codeword in form a1a2..an where each a is bit
    return (num & (1 << width-pos)) >> width-pos
{% endhighlight %}

I also refreshed my memory on the [format string specifications](https://docs.python.org/2/library/string.html#formatspec). For outputting a number as a five-bit word, for example, `print format(num, '05b')` makes things nice and neat. So does LaTeX in IPython, enclosing the text in `$` for inline or `$$` for new lines!

Calculating the binary weight (number of 1s) is a little goofy to me. Literally I have to convert it to a string first, then count the instances of the substring `1`.

{% highlight python %}
  def weight(n):
    return bin(n).count("1")
{% endhighlight %}
