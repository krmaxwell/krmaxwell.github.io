---
layout: post
title: "Handling URLs in Python with a wrapper function"
date: 2014-01-14 22:24:46 -0600
comments: true
categories: Programming, Python
---

Now for a break from Project Euler... In my projects, I find myself frequently retrieving URLs from various servers. Sometimes I need to call a REST API endpoint and other times I need to scrape a site. And like a lot of programmers, I don't like to rewrite code. So originally, in [Maltrieve](http://maltrieve.org), I wrote a function called `get_URL()` that wrapped calls to `urllib2.urlopen()` so I didn't have to repeat the error handling every time. It [sucked](https://github.com/krmaxwell/maltrieve/blob/b75dbe5d70aab97928648159d92ccdd2596b1d1c/malutil.py#L6).

Now in a work project, I have the same basic requirement and I brought over that function. But in daily usage, the terribad error handling kept biting me. Also, sometimes I need to set up the request with various parameters (like, say, an API key or a specific user agent string).

For the latter requirement, `isinstance()` does the trick. We compare the parameter to the Python type `basestring` because all sorts of subclasses could get used; this mostly matters around Unicode stuff. Otherwise, we make sure the parameter is the proper type of object.

Once we make the request, though, we need to handle possible errors. We should probably replace the calls to `sys.stderr.write()` with `logging.error()` or similar, but for my implementations to date this works fine. In the `urllib2` module, `HTTPError` is a subclass of `URLError` is a subclass of `IOError`. So we need to handle the more specific cases first, else we will never see the data for them. And while we could access specific attributes like `HTTPError.code`, since all we want to do is tell a human, we just need the base value.

I suppose this could be rewritten as a class but that seems like one level of abstraction too far. And procedural programming can never go out of style.

{% highlight python %}
def get_url(orig_request):
    # Utility function to get a URL with error handling
    # Accepts URL string or urllib2.Request object

    if isinstance(orig_request, basestring):
        url = orig_request.encode('utf8')
        request = urllib2.Request(url)
    elif isinstance(orig_request, urllib2.Request):
        request = orig_request
    else:
        return None

    try:
        response = urllib2.urlopen(request)
    except urllib2.HTTPError as e:
        sys.stderr.write("The server couldn't fulfill the request for URL %s: %s\n" % (request.get_full_url(), e))
        return None
    except urllib2.URLError as e:
        sys.stderr.write("We failed to reach a server for URL %s: %s\n" % (request.get_full_url(), e))
        return None
    else:
        return response
{% endhighlight %}

I need to backport this to Maltrieve soon, I think. So many projects... Although I have made this code snippet [available as a Gist](https://gist.github.com/krmaxwell/8430955) for canonical purposes.
