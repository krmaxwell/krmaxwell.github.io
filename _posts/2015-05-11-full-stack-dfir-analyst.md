---
layout: post
title: "Full Stack DFIR Analyst"
categories: Career
---

The other day, I tossed off a barely-thought-out [tweet](https://twitter.com/kylemaxwell/status/596106032939671552) that got way more attention than I would have ever expected:

> You call it "full stack" but we call it "actually knowing how stuff works".

[![Egg-stacktic](/assets/images/Stack_of_egg_cartons.jpg)](http://commons.wikimedia.org/wiki/File:Stack_of_egg_cartons.jpg)

## Developers

This came partly from seeing a semi-famous Etsy job requisition for an [intrisically-motivated full stack product hacker](https://www.etsy.com/careers/job/oEzuWfwn) that came across as _more than a little_ pretentious.

> Thales of Miletus was said to have been so intent on watching the stars that he fell into a well. Herein lies an invitation to join those of us, comfortable with this as an occupational hazard, happily contemplating from the bottom... You consider critical thinking to be among your core competencies. Rigor is important to you. You are prone to quixotic behavior. You dedicate time and effort communicating nuance to Manichaeans. Honesty, integrity, and a firm grip on reality are much more important to you than being right. You recognize the inherent limitations of your own wetware, and you do your best to work around them. You find argument exhilarating.

(In the interest of fairness, everyone I've met from Etsy has not been like that at all.)

So the idea basically means that a "full-stack developer" can handle everything from the OS-level work through the middleware, database, and application. Hopefully, this developer understand the environment in which her stack lives, including the host (whether that's a traditional datacenter or cloud or desktop PC). When the term "LAMP stack" had some currency, I would have thought of somebody who could write the [Perl|PHP|Python] code, manage Apache and MySQL, and admin the Linux box. These days, it implies a bit more about UI/UX design and devops, I suppose. But that's not the world where I really live - I just visit there sometimes.

## DFIR

So what does a "full-stack DFIR analyst" look like? Beyond never using that term in an actual organization, I'd suggest understanding the following:

- **Network environment:** That means that the analyst understands the fundamentals of routing, switching, and even modern load balancing. Just like everything else in our world, networks have evolved significantly over the last 15 years.
- **System environment:** This should include hypervisors and virtual machines, multicore processing, and datacenter management. It also means operating systems, including desktop, server, and mobile.
- **Cloud:** Don't give me a bunch of static about the word "cloud" here. In this case, I'm talking about technologies that make "the cloud is somebody else's computer" happen. That includes things like the hypervisor stuff above, how to work in large multitenant environments like AWS or DigitalOcean, etc.
- **Web:** Oh, there's so much here. Today we have to understand technical matters like HTTP, Javascript and DOM, REST APIs, and CDNs, just to get started. But we _also_ have to understand cultural issues, like memes, social media, the existence and basic background of various communities, and major social phenomena on the web (e.g. Black Twitter, Gamergate, etc.)
- **Code:** I firmly believe that everybody in DFIR, and in infosec, and even in tech, needs some familiarity with - and ability to - code. Not that everybody has to be a full-time developer, but we should be able to write basic scripts in some chosen language, as well as follow logic expressed in major languages, including C, JavaScript, and scripting languages. (Maybe even Java.)
- **Intelligence analysis:** Analysis is a discipline unto itself. Whether your job involves monitoring in a SOC or full-on system & network forensics, you need to understand it within the [larger context](http://xwell.org/2013/12/21/kent-doctrine-intel-analysis/).

## You left something out!

Yes, I'm sure I did. By our nature, we have to be [generalists rather than specialists](http://sroberts.github.io/2015/05/02/imposter-syndrome-in-dfir/#the-jack-of-all-trades-inferiority). Some other things we probably need to include might be cryptography, legal processes, and interviewing. But I think the above constitutes a minimum core set of things to know. If you'd like to discuss further, please feel free to [comment on GitHub](https://github.com/krmaxwell/krmaxwell.github.io/issues/71) or [ping me on Twitter](https://twitter.com/kylemaxwell).
