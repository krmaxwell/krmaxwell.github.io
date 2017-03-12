---
layout: post
title: "On learning new programming languages"
categories: Programming,Education,Python,Golang
---

I decided a couple of decades ago that I wanted to speak Spanish beyond the very basics we learned in junior high and high school (which didn't include much, even in Texas). That meant I wanted to achieve a conversational level, at a minimum. Circumstances at the time prevented me from moving to another country for _full_ immersion, but I could come close to that living in Dallas. Through intense self-directed study and spending large amounts of time in environments where I *had to* speak Spanish - or at least *could* speak Spanish - eventually I reached good professional proficiency.

This demonstrates a good model for learning programming languages.

# Do the work
[![talent](/assets/images/talent-development.png)](http://threepanelsoul.com/2015/05/11/talent/)

**There is no shortcut to success in learning. You have to do the work.** People love to talk about how much they "want" to learn something, or how they started and got distracted. Somehow they often give the impression that that's almost as good.

It's not.

Learning a new skill requires time and effort. While [Learn X in Y minutes](http://learnxinyminutes.com/) is a wonderful reference and high-level overview, it can't burn knowledge into your synaptic pathways to the degree needed for proficiency. Prepare yourself for mental exercise.

Note, I certainly understand that other people may learn in different ways. The whole issue of learning theory and pedagogy lies well outside my expertise. So the rest of this post will just discuss what has worked for me. Hopefully somebody else can get some good ideas they can use out of it.

# Build your knowledge
Personally, I prefer instruction oriented toward people who already understand code. Explanations of the concept of variables and basic logic constructs wastes my time. Instead, give me a good explanation of syntax (the grammar, as it were). For a programmer with an existing skill set, resources like [Learn Code the Hard Way](http://learncodethehardway.org/) work much better than [Codecademy](http://www.codecademy.com/learn).

NB: "X for Dummies"-styled instruction is a total non-starter for me. I'm not a dummy just because I don't know X yet, and neither are you. You are a smart, capable person who wants to learn something new. We should celebrate the desire to learn, not feed into a societal psychosis that rejects _knowing things_.

[A re-introduction to Javascript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript) does a great job of explaining that language with appropriate assumptions about how much I already know about the general topic. I dislike lessons that talk down to me, but at the same time I recognize the need to learn new material. The [Mozilla Developer Network](https://developer.mozilla.org) provides a wonderful example of content balanced for several different levels of development knowledge.

![face book and study](/assets/images/facebook-study.jpg)

This part of the process includes actual study. Learning the [spec](http://golang.org/ref/spec) for a given language will pay off tremendously in time saved over constantly looking up basic syntax stuff ("how do I write a `for` loop in this one again?"). That has cost me more in time wasted and buggy code than it ever should have.

# Exercise your knowledge

I remember my dad asking me how well I understood the language after finishing Spanish II. As an arrogant teenager with an acute case of [Dunning-Kruger syndrome](https://en.wikipedia.org/wiki/Dunning%E2%80%93Kruger_effect), I thought that I only lacked vocabulary.

![much to learn you still have](/assets/images/yoda-learn.jpg)

But it turns out that answering questions on a test doesn't work the same mental muscles as normal conversation. It also turns out that [idiomatic usage](https://blog.udemy.com/idioms-and-their-meanings/comment-page-1/) matters a lot in any language. So I learned way more through spending time chatting with people, reading newspapers, and watching TV: immersion, in other words.

**Learn through usage: projects and drills, not just reading. Work on this every day, or as close to it as feasible.**

My old buddy Mike Matonis tweeted some good [advice](https://twitter.com/matonis/status/597800103643086848) on this topic:

> I'm a fan of project-oriented learning. Design a task, Google your way out of it until it works.

This reminds me a bit of [How to Program (in four easy steps)](https://imgur.com/wOsEq7N) but using that "step 2" to learn rather than just fueling step 3 "copy and paste".

Reading other people's code helps a lot here, either when it's organized for that purpose (as in [Go by Example](https://gobyexample.com/)) or when done in an organized fashion. I'm in a small "Python Poetry Reading Club" where we do just this: select a project, then get in a Google Hangout and review the code and architecture together for an hour. Not only has it given me insight on better, more idiomatic Python, it has helped me understand _how_ I dissect code. (In my case, it turns out that I unconsciously follow the same process as when analyzing malware, which makes sense in its own way.)

Collaborating with others also helps. We each know different sorts of things, so you should not feel any shame when somebody who knows a language's ecosystem better than you [shows you the right way to set up a Python package](https://github.com/mlsecproject/combine/pull/138). Working on [free software](https://gnu.org/philosophy/free-sw.html) provides unparalleled opportunities to do this, although the scope of getting involved in those communities is something I should cover in a separate post.

# Wrapping up

This process never ends, by the way. I will never reach a point where I've learned all I need to know about programming, because that's the path to irrelevancy. (My knowledge of Spanish gets better all the time, too, because I apply it every day.) 

With that in mind, I've started learning Go lately. The adventure begins again...
