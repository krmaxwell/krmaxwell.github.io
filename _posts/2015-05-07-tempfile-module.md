---
layout: post
title: "Python tricks: tempfile module"
categories: Security,Python,Programming
---

Imagine a program that needs to store a bunch of files in a directory (possibly already existing). How do you make sure that you can, in fact, save to that directory successfully? I can think of a few ways:

1. **Just try it: write your files to the directory.** If it doesn't work, hopefully you catch the exception or error. That can lead to problems, though, if you will be doing this over and over. If your process doesn't abort immediately, it could waste a lot of time before the process ends (as in downloading the files and attempting to save them).
1. **Check permissions on the directory before starting all the writes.** This is a little better because it checks for a potential problem in advance. However, other problems can exist (such as the volume having reached capacity).
1. **Try to write a temporary file. If it works, then proceed.** You still have a few complications, of course, like avoiding race conditions and dirty games other users might play to steal your data.

Fortunately for us, Python provides the [tempfile module](https://docs.python.org/2/library/tempfile.html) with some functions to help us: `mkstemp()` and `mkdtemp()`.

## [mkstemp()](https://docs.python.org/2/library/tempfile.html#tempfile.mkstemp)

From the documentation:

> Creates a temporary file in the most secure manner possible.

This means that flags and permissions and file descriptors are handled correctly to prevent the things I noted in #3 above.

The function returns a tuple with the file descriptor as well as the pathname to the temporary file. Since we're not using a context manager like `with`, we need to close that file and then remove the temporary file (the function does not do that for us). So an example implementation might look like:

```
try:
    fd, temp_path = tempfile.mkstemp(dir=my_dir)
    os.close(fd)
    os.remove(temp_path)
except OSError:
    logging.error('Could not write file to %s' % my_dir)
```

Let's walk through this:
- Wrapping everything in a `try/except` block lets us catch potential exceptions.
- We assign the variables `fd` and `temp_path` to the tuple returned by the `mkstemp()` call. The `dir` parameter to that call allows us to specify the directory in which we want to test file creation.
- Close the file descriptor for the open (temporary) file within our program so that the OS doesn't have stale handles hanging around. Then remove the file itself.
- Watch out for [`OSError`](https://docs.python.org/2/library/exceptions.html#exceptions.OSError). This indicates that we **failed writing the file** to `my_dir` and need to fail gracefully somehow.

At this point, your program can proceed to write securely to `my_dir`. Of course, it should still watch for the error condition in #1 above, but you've avoided the cost of that first batch before the program realizes it had a problem.

If you want to use the temporary file for something else (scratch space), you don't have to close the descriptor and remove the path right away. But you will still need to do all that before your program exits. In that case, consider [`NamedTempFile()`](https://docs.python.org/2.7/library/tempfile.html#tempfile.NamedTemporaryFile).

## [mkdtemp()](https://docs.python.org/2/library/tempfile.html#tempfile.mkdtemp)

This function is the sibling of `mkstemp()` but instead creates a temporary directory for whatever you need. Fortunately for us, it's a lot easier to use since we don't have to deal with file descriptors. This is great if your program just needs a temporary workspace to store some files before moving or removing them. The example might look like:

```
try:
    temp_path = tempfile.mkdtemp(dir=my_dir)
    os.rmdir(temp_path)
except OSError:
    logging.error('Could not create subdirectory in %s' % my_dir)
```

This works almost identically except for the lack of a file descriptor to track and close. Again, your program can use the temporary directory for a bit and move the `os.rmdir()` call outside the `try`.

## Conclusion

I use this sort of pattern in [Maltrieve](http://maltrieve.org) for checking the archive directory before saving off retrieved malware. If you have suggestions on other use cases, or better ways to do this, I'd love to chat with you on [GitHub](https://github.com/krmaxwell/krmaxwell.github.io/pull/68) or [Twitter](https://twitter.com/kylemaxwell).
