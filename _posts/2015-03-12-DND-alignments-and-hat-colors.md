---
layout: post
title: "D&D alignments and hat colors"
categories: Security
---

So [@da_667](https://twitter.com/da_667) started a thread [on Twitter](https://twitter.com/da_667/status/576127675355541504) today with a "hypothetical" scenario:

> Let's have a discussion. But before we do that - Disclaimer: Parentel discretion is advised. Any resemblance of the following scenario to any actual real-life scenario is purely coincidental. Scenario: You manage IDS/IPS systems, honeypots, FPC devices, whatever. You caught some bad shit coming over your pipes: attackers trying to exploit some of your webservers. Some of these exploits are just php system() calls to curl to download files over FTP. These FTP calls contained creds. Would you then, proceed to go on a download spree on the payload server with said creds? Addendum: fuck ethics. This is a scenario where you only get a single shot. Would you or would you not use the creds and download everything?


## Alignment talk

In the ensuing discussion, [@stauken](https://twitter.com/stauken) made a [D&D alignment reference](https://twitter.com/stauken/status/576132190813057024):
> so what you're saying is, lawful evil exists for a reason

As often happens among geeks, this led to a wild and fast-moving discussion about D&D alignments. One of my favorite sites for this sort of discussion is [EasyDamus](http://www.easydamus.com/alignment.html). For those of you not familiar with this system, imagine your "ethical" alignment along two axes: **Good vs Evil** and **Law vs Chaos**. For "law", you can mentally substitute "order", since it has more to do with with honor and adherence to rules than what we think of as "law" in our society.

Conversely, in hacking tradition, we often refer to the color of "hats" along a simpler one-dimensional axis, "white" to "grey" to "black". "White hat hackers" are envisioned as Lawful Good [LG], "black hat hackers" as some form of evil (usually Neutral Evil [NE]), and "grey hats" as something else like "chaotic good" [CG]. The referenced material here comes from old Western movies where you could tell if a gunslinger or sheriff or bandit or whomever was a "good guy" or "bad guy" based on the color of their hats.

In the latter case, then, that depends very much on the perspective of the viewer. For the simplest example, think about how, say, your average US and PRC citizens might think about the [NSA TAO](http://en.wikipedia.org/wiki/Tailored_Access_Operations) versus [PLA Unit 61398](http://en.wikipedia.org/wiki/PLA_Unit_61398). "Our guys are good, theirs are bad" sums up the sentiments of most people.

So returning to the original scenario, let's look at how different alignments might react.

### Lawful Good

LG would not use the credentials and log into the server because that would appear _prima facie_ illegal in most jurisdictions. However, they might contact law enforcement or share that information (threat intelligence) with appropriate network security teams in other organizations so that they can check for possible indicators of compromise.

### Neutral Good

NG **might** log in to see if the server contains additional exfiltrated data. Likely, however, they'd consult with their legal counsel and otherwise follow the same course as LG in this particular scenario.

### Chaotic Good

CG would not care much about the law in this situation. They would log into the server, exfiltrate the data, and use it to notify other victims. However, they would not use those data for their own selfish benefit. They might even go a step further and take some action to shut down the server or expose the attacker.

### Lawful Neutral

LN generally follows LG in this scenario. They might be slightly less likely to notify other groups, however, as they'd focus their concern on their own defensive responsibilities.

### True Neutral

TN (or just N) would possibly not do anything. However, it depends on which type of N they identify as. "Undecided" would simply secure their systems and move onto the next incident. The type of neutral who tries to maintain balance between law & order and good & evil might log into the server and try to determine where the balance of power lies (e.g. is the information from inexpert regular people or powerful organizations?) before making a decision.

### Chaotic Neutral

CN doesn't care. They log in and replace all the exfiltrated data with copies of _Paradise Lost_ or just `/dev/random`. Like their "Good" counterparts, they might expose the attacker to others - but for fun rather than to stop them.

### Lawful Evil

LE would generally do the same as LG here. If anything, they'd contact Law Enforcement (also LE!) with the intention of bringing the law's hammer down upon their adversaries. They might even use the situation to advance within their organization at the expense of existing management.

### Neutral Evil

NE would log into the server and destroy it, or at least their own information. They might expose the attacker or, just as likely, use the information for their own benefit.

### Chaotic Evil

CE realizes that the server contains valuable data that they could use for their own benefit. They might subtly corrupt the information on the server after copying it themselves, then use it for financial gain or even to compromise the other victims themselves for additional gain.
