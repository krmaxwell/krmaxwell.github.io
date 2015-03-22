---
layout: post
title: "Release Engineering"
categories: Programming
---

In the process of 'leveling up' as a programmer, I have started trying to implement some basic software engineering concepts. This post serves as a way for me to organize my own thoughts as I learn.

## Basic flow
I've used the [Github Flow](https://guides.github.com/introduction/flow/) for quite a while for lots of things (recently including [this blog](https://github.com/krmaxwell/krmaxwell.github.io)). But this mostly applies to processes that use continuous deployment, like Github itself. It can also work pretty well for documentation and other similar projects that don't need the concept of "releases".

For projects with staged releases, we need a few more bits. The git branching model [documented](http://nvie.com/posts/a-successful-git-branching-model/) by [Vincent Driessen](https://twitter.com/nvie) has become quite popular lately. I think it really just shows how to use git for implementing a very common model we've used for a long time. (I recall using this basic approach twenty years ago when our source code collaboration just relied on using a whiteboard to document who had which file checked out. That sucked as hard as it sounds.)

This model uses two primary branches: `master`, which must always be deployable and represents the current release, and `development`, which contains the currently-accepted features and bug fixes for the next release. Hot fixes for production-affecting bugs can be merged directly into both of these, but otherwise everything goes through `development` before going to `master`.

## Community implementations

When implementing this flow in community-development projects (such as open source software), we have to take a few steps. Github will show a link to a [contributor guide](https://github.com/blog/1184-contributing-guidelines) on all issue and pull request pages. The guidelines document should explain this flow, as well as any other considerations (such as licensing and coding standards). Contributors should generally issue pull requests against the `development` branch, for example.
