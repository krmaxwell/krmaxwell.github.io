---
layout: post
title: "Kent Doctrine for security intel analysis"
date: 2013-12-20 23:02:17 -0600
comments: true
categories: Security, Intel
---

I’ve said before that log management matters, but **log analysis matters more**. Extracting and communicating useful information (analysis) requires collecting and storing your security data as well as processing the data quickly. But having all the data available won’t matter to anybody except auditors if you don’t use it in ways that inform good decisions. [Mike Rothman](https://twitter.com/securityincite) of Securosis expressed this exceptionally well in his [preview of the 2012 RSA Conference](https://securosis.com/blog/rsa-conference-2012-guide-key-themes):

>You will see a bunch of vendors talking about their new alerting engines taking advantage of these cool new data management tactics, but at the end of the day, it’s not how something gets done – it’s still what gets done.
>So a Hadoop-based backend is no more inherently helpful than that 10-year-old RDBMS-based SIEM you never got to work. You still have to know what to ask the data engine to get meaningful answers. Rather than being blinded by the shininess of the Big Data backend focus on how to use the tool in practice. On how to set up the queries to alert on stuff that maybe you don’t know about.

To paraphrase Socrates, **unexamined data are not worth collecting**. Analysis methodology and critical thinking skills matter. Rothman is spot on with this: the value of big data tech comes when you need to grow past the capabilities that traditional SIEM and RDBMS provide. By way of analogy: if you don’t understand algebra, then don’t take a course in calculus until you have the basic prerequisites down. You’ll just frustrate yourself and waste your tuition dollars.

![Sherman Kent](https://www.cia.gov/news-information/featured-story-archive/2010-featured-story-archive/Kent_Sherman_t.jpg/image.jpg)
*Provided by CIA*

In this vein, then, I appreciated the [CIA paper on the background and work](https://www.cia.gov/library/kent-center-occasional-papers/vol1no5.htm) of [Sherman Kent](http://en.wikipedia.org/wiki/Sherman_Kent), the “father of intelligence analysis”.

He promoted an analytic doctrine that boils down to nine key points, listed in the CIA paper above. That doctrine applies across domains, not just for the sorts military and geopolitical analysis we expect from government intelligence agencies. I highly recommend that everyone read at least that section of the paper, but here are some applications for those of us involved in security intelligence analysis, especially in the private sector.

1. **Focus on Policymaker Concerns:** What keeps your management up at night? Hopefully security isn’t the only thing, of course. So assuming that your CxOs understand the general threat landscape, analysts need to ensure that they track relevant areas that can lead to useful changes and decisions at strategic and tactical levels.
1. **Avoidance of a Personal Policy Agenda:** Many analysts focus on threats that concern them for reasons outside of their organization. Maybe they disagree with the politics of the Occupy movement and overemphasize threats to entirely unrelated organizations, or worry about APT China because of Sinophobia rather than a reasoned assessment of the situation. Or maybe they want to drive decision makers to a particular tech solution. Even worse, they may use their analyses as weapons for corporate political plays. Doing that represents a disservice to the organization and an unprofessional approach.
1. **Intellectual Rigor:** This area stands as-is: "Estimative judgments are based on evaluated and organized data, substantive expertise, and sound, open-minded postulation of assumptions. Uncertainties and gaps in in­formation are made explicit and accounted for in making predictions."
1. **Conscious Effort to Avoid Analytic Biases:** None of us can completely avoid cognitive bias, but we can make sure we understand it and try to correct for it where possible. That principally means application of the scientific method. Whether or not faith and dogma have a place in one’s personal life, they certainly do not in one’s professional analyses.
1. **Willingness to Consider Other Judgments:** Fight for your ideas, but playing "devil’s advocate" should rest on a better intellectual basis than simply spreading FUD. Recognize that others may in fact know more than you do or have insights that can help you.
1. **Systematic Use of Outside Experts:** In addition to seeking out and understanding the work of other analysts, don’t restrict yourself solely to your field or even industry. Work with a community and keep bringing in fresh concepts from other disciplines.
1. **Collective Responsibility for Judgment:** Eventually, your team will produce a report. You may not have agreed with everything that went into it, but that’s the way the sausage gets made. Once that report goes to its audience, support it. Throwing the rest of your analysis team under the bus by telling the audience "I told them so" doesn’t actually make you look smarter. It makes you look unprofessional. That doesn’t mean that you should ignore all criticism; rather, it means that you should be willing to take lumps with the rest of the group. If someone asks you for your opinion, give it – but clarify that it doesn’t represent the considered opinion of the rest of the team.
1. **Effective communication of policy-support information and judgments:** Analysts need three core skills: domain expertise, critical thinking skills, and communication ability. This includes targeting your analysis to the level appropriate to your audience. You must be able to summarize your findings in understandable and accurate ways. And you must be able to handle points of uncertainty properly.
1. **Candid Admission of Mistakes:** You won’t always be right. Admit it, and review past work to see what you can learn for improvement the next time. "Try again. Fail again. Fail better."

Security intelligence analysts should learn from previous work, instead of simply trusting in their own domain expertise and innate intelligence. Dr. Kent [led the way](http://www.au.af.mil/au/awc/awcgate/cia/strategic_warning_kent.htm), and even we non-spooks can still learn from his work.
