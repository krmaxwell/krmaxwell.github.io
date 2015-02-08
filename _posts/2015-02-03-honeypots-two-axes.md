---
layout: post
title: "Understanding honeypots on two axes"
categories: Security
---

With the release of [Modern Honey Network](https://github.com/threatstream/mhn), lots of folks have started to pay attention to honeypots as a data source again. Historically, we have classified honeypots on a spectrum of [interaction](http://www.honeyd.org/background.php). Low-interaction honeypots provide a relatively small surface to an attacker and they can't do much beyond the initial contact. High-interaction honeypots, in contrast, simulate as much of a system as possible. This approach allows the attacker to take many different types of actions. Generally, the level of interaction available depends on the underlying platform (kippo, netcat, dionaea, etc.)

When deploying a honeypot or analyzing the data from it, we should also think about the **targetedness**. That is, how targeted is the scope of our data collection? A collection of sensors scattered across a bunch of hosting providers around the world will provide a broad view with little direct relevancy to a particular enterprise.  Conversely, an internally-deployed honeypot with a simulated Active Directory environment and seeded with decoy data targets a narrow scope of attackers. That deployment will only provide data on attackers within our environment.

One doesn't matter more than the other. These are orthogonal axes. And the choices we make on each spectrum depend almost entirely on your goals for the project and the resources you can allocate. Broadly-targeted, high-interaction honeypots require an entirely different approach than narrow-targeted (internal) low-interaction honeypots. They also provide wildly different sorts of data and you'll take different actions.


|                     | High Interaction | Low Interaction         |
|---------------------|------------------|-------------------------|
|**Broad targeting**  | Danger zone      | Many community projects |
|**Narrow targeting** | Active defense   | Internal monitoring     |

- How to decide
- Things to keep in mind
- Ideas to get started
