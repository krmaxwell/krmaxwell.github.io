---
layout: post
title: "How I ended up submitting a tiny PR to swagger-codegen"
categories: Programming,Python,OpenSource
---

One of the nicer trends in API development has been the growth of the [OpenAPI specification](https://github.com/OAI/OpenAPI-Specification) (formerly known as [swagger](http://swagger.io/)). This allows API providers to document their interface easily and improve the developer experience (DX) for anyone using it. 

Because the specification comes as a machine-readable file (usually JSON or YAML), tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) can process the spec file and automatically generate a set of bindings for that particular API in a given language. That can really help navigating the ins and outs of particularly large or complex APIs, and thus reduce time to deployment.

Recently, I [needed proxy support](https://github.com/swagger-api/swagger-codegen/issues/4639) for a particular deployment of code that relied on a private API documented with OpenAPI. I already work fairly consistently with the generated Python module from swagger-codegen for that API, but all of my previous deployments have been able to connect directly to the endpoint (without a proxy in the middle).

I hacked in support overnight for a proxy connection into my existing module since I had a tight timeframe, but this seemed like something the upstream project needed too. After all, the template code for other languages (even PHP) already supported proxies. But contributing to a new open source project made me a bit nervous, and so I dawdled for a bit. Even after many years of working with OSS, the idea of accidentally violating some social norm or doing it the "wrong way" led me to wait longer than needed.

Happily, the project has a nice set of [guidelines for contributing](https://github.com/swagger-api/swagger-codegen/blob/master/CONTRIBUTING.md). They also use the [issue and PR template functionality](https://github.com/blog/2111-issue-and-pull-request-templates) Github provides so that contributors have a checklist. This not only helps the maintainers keep their sanity, it also provides a bit of a confidence boost to the contributor who has some guidance on doing things correctly. And of course the maintainers were friendly even when it turned out I'd missed committing some code that fulfilled one of the items in the checklist!

Some suggestions from reviewers came back very quickly on fixing some mistakes on my part, I addressed them, and then the PR suddenly made its way into the code base. I'm looking forward now to helping more with the Python client, since it provides a significant basis for tooling I use nearly every day professionally.

The moral here: don't be afraid of sending in a PR. Ask questions, pay attention, and be friendly. The project will likely welcome your effort and help you out!
