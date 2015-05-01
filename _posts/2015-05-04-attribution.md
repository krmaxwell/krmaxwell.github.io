---
layout: post
title: "Understanding attribution"
categories: Security
---

One of the most popular and enduring forms of mystery fiction is the [_whodunit_](http://en.wikipedia.org/wiki/Whodunit). Readers and audiences love following along and trying to determine the actual identity of the attacker based on the clues and observations provided. During and after incident investigations, many folks from the actual investigators on the case up to the public (armchair DFIR!) tries to figure out the same thing. Unlike "whodunit" fiction, though, we may not have all the information needed or indeed ever get confirmation of the right answer.

For various reasons, infosec people (_especially_ those who don't actually work in incident response) love to mock the idea of "attribution". Some of that is deserved because of the FUD that policymakers and vendors throw around. Some of it is not, and reflects lack of expertise on the part of the [commenters](http://blog.norsecorp.com/2015/03/11/pseudo-threat-intelligence-all-i-want-you-to-know/).

## What attribution means in DFIR

"Attribution" in the DFIR world means assigning some identity to the adversary in an incident. That identity may not necessarily drill all the way down to the "real life" name and address (though in some cases it will). But it can also include correlating a set of intrusions to the same entity, possibly providing some set of data like region or affiliation or operational aspects and observations.

So this can include everything from naming John Doe at 123 Main Street, Anytown as the threat actor thru saying "state-sponsored attackers from Arstotzka". It also includes determining that a given incident belongs to a specific intrusion set, whether you name that intrusion set "APT 1337" or "Pedantic Penguin" or "PURPLERAIN".

## When and how it matters

The importance of attribution varies across the _type_ of attribution under discussion as well as the _consumer_ of that intelligence. Law enforcement, intelligence community, and military organizations, for example, have an interest in the actual meatspace identity because they may have authority to apprehend or carry out some type of retribution - handcuffs and cruise missiles, as it were (h/t [Scott Roberts](http://sroberts.github.io). (Criminal actors have a similar interest from their perspective, whether for OPSEC validation or for their own illegal retribution.) For security and malware analysts in the private sector, however, attribution in that sense rarely matters too much. The exception to that is when the adversary is located in a jurisdiction where civil or criminal complaints can be brought.

However, **all** analysts care about understanding the TTPs and capabilities of a given adversary as well as strategic information (e.g. motives and targeting).

## Bases for proper attribution

Attribution based on geolocation of IP addresses is generally accepted to be facially invalid, on par with using dice or a magic 8-ball. (There are some exceptions when these methods turns out to produce valid conclusions, but they are just that: exceptions.) Proper attribution requires cross-validating information from across a number of disciplines. Artifacts from malware analysis and forensic examination can play a role, of course. So does intelligence gathered through open sources, search warrants, interviews, informants, infiltration, and network penetration.

None of these by themselves will necessarily provide sufficient evidence for a solid assessment. For this reason, attribution depends on [all-source intelligence analysis](http://www.globalsecurity.org/intell/library/policy/army/fm/2-0/chap5.htm). Even when the analysis doesn't produce an actual name, evaluation of **detailed** TTPs and methodologies can link an incident to a larger intrusion set. That then permits defenders and investigators to use information found in previous investigations to prevent and detect more activity.

## When attribution matters

FBI Director James Comey recently gave a [speech](http://www.fbi.gov/news/speeches/addressing-the-cyber-security-threat) that people mostly talked about because of his mention of Sony's intrusion in the fall of 2014. But he also talked a bit about why attribution matters in the context of changing the cost/benefit calculus for adversaries:

> I said we need to impose costs. What do I mean by that? I worry sometimes that whether the actor is a nation state or a criminal or a creep down the block, there's a sense that it's a freebie. That if I'm at a keyboard somehow it's free that I can break in and steal the lifeblood of an American business or steal the identity of an American citizen when it is in reality no different than kicking in your front door and walking out with your television, right? Or dragging something you love dearly out of your life. We have to treat it that way. We have to impose real costs on people who think they're alone - think they're far enough away that it's a freebie.

How those costs increase can vary. Maybe, if you're the FBI, you can go arrest some folks. Or maybe you can't because of jurisdiction, but you freeze their bank accounts and deny them the ability to travel to significant parts of the world. Outside of organizations of that type, we usually can't do that, but we can beef up our network defenses against the specific TTPs used by the attackers or implement some sort of deception operation to get them to expend resources pointlessly. (This can have the side benefit of gathering additional intelligence.) 

## Conclusion

Armchair investigation can actually be a useful thought exercise for training and understanding broader context if undertaken as a type of intelligence analysis. But it's just as important to understand what attribution means when carried out by people with the appropriate training and actual information at hand.

If you're interested in discussing this further, please feel free to ping me on [Twitter](https://twitter.com/kylemaxwell) or comment on [GitHub](https://github.com/krmaxwell/krmaxwell.github.io/issues/11).

## External reading

- http://www.simonganiere.ch/2014/12/28/attribution-of-cyber-attack/
- http://espionageware.blogspot.com/2014/04/apt-attributions-and-dns-profiling.html
- https://www.youtube.com/watch?v=kstOKWL_OEk
