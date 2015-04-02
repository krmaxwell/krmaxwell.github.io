---
layout: post
title: "Open Source Software Engineering"
categories: Programming
---

In the process of 'leveling up' as a programmer, I have started trying to implement some lightweight, basic software engineering concepts. This post serves as a way for me to organize my own thoughts as I learn. It focuses primarily on open-source methodologies, but of course the core lessons themselves apply in any environment.

## Community implementations

When implementing engineering guidelines in community-developed projects (such as open source software), we have to take a few steps. GitHub will show a link to a [contributor guide](https://github.com/blog/1184-contributing-guidelines) on all issue and pull request pages. The guidelines document should explain the process, as well as any other considerations (such as licensing and coding standards).

## Basic flow
I've used the [**Github Flow**](https://guides.github.com/introduction/flow/) for quite a while for lots of things (recently including even [this blog](https://github.com/krmaxwell/krmaxwell.github.io)). But this mostly applies to processes that use continuous deployment, like GitHub itself. It can also work pretty well for documentation and other similar projects that don't need the concept of "releases".

For projects with staged releases, we need a few more bits. The git branching model [documented](http://nvie.com/posts/a-successful-git-branching-model/) by [Vincent Driessen](https://twitter.com/nvie) has become quite popular lately. I think it really just shows how to use git for implementing a very common model we've used for a long time. (I recall using this basic approach twenty years ago when our source code collaboration just relied on using a whiteboard to document who had which file checked out. That sucked as hard as it sounds.)

This model uses two primary branches: `master`, which must always be deployable and represents the current release, and `development`, which contains the currently-accepted features and bug fixes for the next release. Hot fixes for production-affecting bugs can be merged directly into both of these, but otherwise everything goes through `development` before going to `master`.

## Code quality

The smart folks over at [Yelp](http://www.yelp.com) have a fun tool called [_pre-commit_](http://pre-commit.com). This tool uses [git hooks](http://githooks.com) to run a few scripts before committing code, even locally. This primarily should include code linters, although in some projects some level of testing may also run here.

For an example, take a look at the [pre-commit configuration file for Maltrieve](https://github.com/krmaxwell/maltrieve/blob/3f6fdcc3c8d139dbab3c5153efc95f65b8f30251/.pre-commit-config.yaml). This runs a few scripts to format my code according to [PEP8](https://www.python.org/dev/peps/pep-0008/), check any JSON and YAML files, etc. While slavish adherence to PEP8 can create problems, in general it will result in more readable and standard code when used judiciously. Other languages have similar tools and linters available, so _pre-commit_ should work even for projects coded in some other language like C.

Tools like [Landscape](https://landscape.io) can also run these sorts of linters and style checkers (among other things) to generate code quality metrics. For open-source projects, this can work well in conjunction with _pre-commit_ because it can look at code in PRs from outside contributors.

## Testing

I remember trying **test-driven development** a decade ago, and for whatever reason the lesson didn't take. (Probably because I wrote all my code in Perl at the time, carrying with it a whole slew of issues for me.) However, I've committed to improving code quality by writing tests, if not going to full [TDD](http://c2.com/cgi/wiki?TestDrivenDevelopment) just yet. Rather than use the standard [_unittest_](https://docs.python.org/2/library/unittest.html) in Python, going with [_pytest_](http://pytest.org) allows a developer to get started much more quickly. I just create an additional Python module with a set of functions that start with _test_ (e.g. "_test_data_load()_") and `assert` that results from functions in my production code meet certain expectations. It uses simple decorators for setup and teardown. While larger projects might need more complex testing environments, everything I currently write fits easily into this tool. Friends have told me that it has changed writing tests so that they have fun writing them now.

## Continuous Integration

Projects with tests can start implementing **continuous integration**. For my projects, this means I have automated testing running that gives me a result before merging it back to `master` (or even `development`). GitHub has great [support](https://developer.github.com/guides/building-a-ci-server/) for CI tools. Popular hosted choices include [Travis CI](https://travis-ci.com) and [CircleCI](https://circleci.com), while projects that want to run their own could look at [Jenkins](http://jenkins-ci.org). In both cases, developers can log into the tools with their GitHub accounts and specify which repositories to check. CircleCI has some basic support for getting started automatically, but taking proper advantage of either tool will require a small, straightforward configuration file written in YAML.

After testing both extensively, I chose to stick with CircleCI. Both offer free testing for open-source projects (by which they seem to mean "public repositories"), but CircleCI has a little lower pricing than Travis CI for private repositories or closed-source projects. I also liked how the UI integrates a little more with GitHub, making it easy to check on a pull request, branch, or commit right from its interface. Both provide solid options, though, and for many people Travis CI may actually be the right choice.

CI can do a lot more than run tests, of course, including providing some level of automation for continuous deployment. That has applications for projects that provide services or do other stuff with data, for example.

## Test Coverage

Getting those green check marks when all tests pass gives a great feeling. But if the tests only handle a small amount of code, then the probability increases that things have broken and nobody knows it. Code coverage tools measure how much code actually gets exercised by tests. (Note the distinction between that and how much code gets tested **well**.) For _py.test_, the [_pytest-cov_](https://pypi.python.org/pypi/pytest-cov) plugin outputs a data table after the tests run:

```
-------------------- coverage: platform linux2, python 2.6.4-final-0 ---------------------
Name                 Stmts   Miss  Cover
----------------------------------------
myproj/__init__          2      0   100%
myproj/myproj          257     13    94%
myproj/feature4286      94      7    92%
----------------------------------------
TOTAL                  353     20    94%
```

Percentages on my projects have not climbed to where I would like them, but they've increased from 0%.

For seeing automated results, [Coveralls](https://coveralls.io) integrates well with both of the CI tools listed above. In CircleCI, just add some environment variables so that API keys don't have to go into a public repository. (In this area, Travis CI probably integrates a little better with Coveralls.)

## Releases

Eventually, software has to be released. GitHub allows project maintainers to [create releases](https://help.github.com/articles/creating-releases/). This applies a [lightweight tag](http://git-scm.com/book/en/v2/Git-Basics-Tagging#Lightweight-Tags) and also allows a download of the code as a snapshot. GitHub also will serve binaries (e.g. compiled code). At one time, I used a nonstandard sequential system like "beta1" and "beta2". However, [semantic versioning](http://semver.org) allows for more granularity and works well with different sorts of tools like PyPI.

## Kanban

The Kanban approach, originally developed for manufacturing processes, can apply to task management too. I've used a version of it for personal productivity in past jobs, including offline versions (a white board with actual sticky notes). [Waffle](https://waffle.io) provides a very lightweight interface to GitHub issues, including synchronizing state and comments with issue and pull requests plus filters on milestones and such. [Trello](https://trello.com) is probably better-known for general Kanban usage, but by itself doesn't directly integrate with GitHub to my knowledge.  A number of other add-ons can help with this, such as connecting them with [IFTTT](https://ifttt.com) or [Zapier](https://zapier.com). For a similar tool that doesn't use the Kanban methodology, I've heard great things about [Asana](https://asana.com).

## Conclusion

For a long time, I have been a "hacker" and even "coder" but not a "software engineer". My code is a house of cards and I just try not to topple it with an errant breath. But software engineering can go much deeper. Projects such as code that needs to meet life safety requirements really do require much more. But applying extra polish and quality can benefit just about any project, and the tools & methodologies here represent huge improvements over what I have used for the last couple of decades.

## Further reading

- [Do Not Merge WIP for GitHub](https://chrome.google.com/webstore/detail/do-not-merge-wip-for-gith/nimelepbpejjlbmoobocpfnjhihnpked)
- [GitHub Flow](http://scottchacon.com/2011/08/31/github-flow.html)
- [git-flow](https://github.com/nvie/gitflow)
- [Git Flow vs GitHub Flow](http://lucamezzalira.com/2014/03/10/git-flow-vs-github-flow/)
- [How do we define code quality? (Stack Overflow thread)](http://stackoverflow.com/questions/405243/how-do-we-define-code-quality)
- [Python Guide: Testing Your Code](http://docs.python-guide.org/en/latest/writing/tests/)
- [The Art of Unit Testing](http://artofunittesting.com)
- [Continuous Delivery vs Continuous Deployment vs Continuous Integration - Wait huh?](http://blog.assembla.com/AssemblaBlog/tabid/12618/bid/92411/Continuous-Delivery-vs-Continuous-Deployment-vs-Continuous-Integration-Wait-huh.aspx)
- [Practical continuous deployment](http://blogs.atlassian.com/2014/04/practical-continuous-deployment/)
- [Test Coverage](http://martinfowler.com/bliki/TestCoverage.html)
- [About Releases](https://help.github.com/articles/about-releases/)
- [Kanban](http://kanbanblog.com/explained/)
