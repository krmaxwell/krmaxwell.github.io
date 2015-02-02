---
layout: post
title: "Understanding honeypots on two axes"
categories: Security
---

With the release of [Modern Honey Network](https://github.com/threatstream/mhn), lots of folks have started to pay attention to honeypots as a data source again. I want to talk about ways to think about honeypots, particularly in terms of categorization.

Historically, we talked about honeypots on a spectrum of [interaction](http://www.honeyd.org/background.php). Low-interaction honeypots provide a relatively small surface to an attacker and they can't do much beyond the initial contact. In contrast, high-interaction honeypots simulate as much of a system as possible so that the attacker can take many different types of actions. This classification is primarily a function of the underlying platform (kippo, netcat, dionaea, etc.)

When deploying a honeypot or analyzing the data from it, however, another categorization also should be taken into account: the **targetedness**. That is, how targeted is your data collection? A collection of sensors scattered across a bunch of hosting providers around the world is fairly untargeted. Conversely, an internally-deployed honeypot with a simulated Active Directory environment and seeded with decoy data is highly targeted. That deployment will only provide data on attackers within your environment.
