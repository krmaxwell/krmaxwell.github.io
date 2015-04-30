---
layout: post
title: "Understanding attribution"
categories: Security
---

One of the most popular and enduring forms of mystery fiction is the [_whodunit_](http://en.wikipedia.org/wiki/Whodunit). Readers and audiences love following along and trying to determine the actual identity of the attacker based on the clues and observations provided. During and after incident investigations, many folks from the actual investigators on the case up to the public (armchair DFIR!) tries to figure out the same thing. Unlike "whodunit" fiction, though, we may not have all the information needed or indeed ever get confirmation of the right answer.

For various reasons, infosec people (_especially_ those who don't actually work in incident response) love to mock the idea of "attribution". Some of that is deserved because of the FUD that policymakers and vendors throw around. Some of it is not, and reflects lack of expertise on the part of the commenters.

## What attribution means in DFIR

"Attribution" in the DFIR world means assigning some identity to the adversary in an incident. That identity may not necessarily drill all the way down to the "real life" name and address (though in some cases it will). But it can also include correlating a set of intrusions to the same entity, possibly providing some set of data like region or affiliation or operational aspects and observations.

So this can include everything from naming John Doe at 123 Main Street, Anytown as the threat actor thru saying "state-sponsored attackers from Arstotzka". It also includes determining that a given incident belongs to a specific intrusion set, whether you name that intrusion set "APT 1337" or "Pedantic Penguin" or "PURPLERAIN".

## When and how it matters

The importance of attribution varies across the _type_ of attribution under discussion as well as the _consumer_ of that intelligence. Law enforcement, intelligence community, and military organizations, for example, have an interest in the actual meatspace identity because they may have authority to apprehend or carry out some type of retribution. (Criminal actors have a similar interest from their perspective, whether for OPSEC validation or for their own illegal retribution.) For security and malware analysts in the private sector, however, attribution in that sense rarely matters too much. The exception to that is when the adversary is located in a jurisdiction where civil or criminal complaints can be brought.

However, **all** analysts care about understanding the TTPs and capabilities of a given adversary as well as strategic information (e.g. motives and targeting).

## Bases for proper attribution

Attribution based on geolocation of IP addresses is generally accepted to be facially invalid. (There are some exceptions when that method turns out to produce valid conclusions, but they are just that: exceptions.) Proper attribution requires cross-validating information from across a number of disciplines. Artifacts from malware analysis and forensic examination can play a role, of course. So does intelligence gathered thru interviews, informants, and infiltration. (The IC generally refers to these as HUMINT and SIGINT.)

## External reading

- http://www.simonganiere.ch/2014/12/28/attribution-of-cyber-attack/
- http://espionageware.blogspot.com/2014/04/apt-attributions-and-dns-profiling.html
- https://www.youtube.com/watch?v=kstOKWL_OEk

---

# Previously published at iDefense

_originally published 2015-01-21. included here temporarily for helping me organize and update my thoughts_

Threat intelligence covers a wide variety of information types. We can model these as a sort of spectrum ranging from strategic on one end to tactical on the other. Strategic threat intelligence tends to cover identity and motive, or "who" and "why." Tactical intelligence, on the other hand, tends toward focusing on methodology and specific asset targeting, or "how" and "what."

When we talk about attribution as part of threat intelligence, we mean one specific component: the "who." Generally speaking, determining the precise identity of an adversary matters most to those who can then create real-world consequences for that adversary. Scott Roberts, a senior incident responder and intelligence analyst with GitHub, is fond of noting that attribution is for people who can use handcuffs or cruise missiles. The additional work in terms of data collection and analysis for that level of attribution often does not yield commensurate benefits without the capacity to act on that information. This often requires "all-source" intelligence, not just analysis of open-source information or forensic artifacts. The investigation techniques that yield this data sometimes require governmental capabilities, such as legal warrants, human intelligence, or signals intelligence from exploitation of external networks.

Other aspects of attribution provide value in terms of correlation. If we can say that a given adversary acts in a particular way, we have identified relevant tactics, techniques, and procedures (TTPs). This applies even to adversaries we only know via code names or other labels. When analysis links a given incident to that adversary, then, the defending organization can then use the knowledge of that adversary's TTPs for prevention, detection, and response.

FBI Director James Comey recently gave a [speech](http://www.fbi.gov/news/speeches/addressing-the-cyber-security-threat) in which he described the Bureau's new strategy regarding cyber-security issues. His speech received a lot of attention because of the discussion of attribution in the recent public Sony hacking incident, but that just provided an example for the strategy the FBI has already begun to implement. One point in its plan illustrates this idea:

> I said we need to impose costs. What do I mean by that? I worry sometimes that whether the actor is a nation state or a criminal or a creep down the block, there's a sense that it's a freebie. That if I'm at a keyboard somehow it's free that I can break in and steal the lifeblood of an American business or steal the identity of an American citizen when it is in reality no different than kicking in your front door and walking out with your television, right? Or dragging something you love dearly out of your life. We have to treat it that way. We have to impose real costs on people who think they're alone - think they're far enough away that it's a freebie.

Those costs may include things like incarceration or international sanctions when we can determine real-world identities; however, even if not, we can change the risk/benefit calculus. We can target defenses against the specific TTPs an adversary used. Or perhaps we can create deceptions so that the adversary spends resources attacking the wrong assets (such as using decoy data). Over time, adversaries will need to change their own approach, potentially decreasing the expected profit or benefit from a given campaign. This also gives responders more time to detect an incident in progress and take corrective measures.

A better understanding of the costs and value associated with attribution enables analysts and leaders to make relevant decisions that best achieve an organization's specific information security goals.
