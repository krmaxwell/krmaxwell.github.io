---
layout: post
title: "The Breach Dodecahedron"
categories: Security, Guest Blog
---

_This post was written by guest blogger and broham extraordinaire [Kevin "@bfist" Thompson](https://twitter.com/bfist). For more ramblings on risk management and pro wrestling, go follow him!_

I spend a lot of my time reading breach reports for publicly disclosed incidents
or reading reports from forensic organizations about security breaches. A while
back I noticed that our industry seems to have a fascination with geometry.  For
example, we have the CIA triad which later gave rise to the Parkerian hexad, and
as I was going over an old [Trustwave Global Security
Report](http://www2.trustwave.com/rs/trustwave/images/2013-Global-Security-Report.pdf)
I saw that they decided to change their breach triangle into a breach
quadrilateral so that their model would better reflect the data they were
seeing.  But in the security field, more is better; why have four sides or six
sides when you can have 12?  Why have a two dimensional shape when you can have
a three dimensional shape?  And so it is with tongue firmly in cheek that I
present the Breach Dodecahedron.

<img src="/assets/images/dodecahedron.png" alt="Dodecadedron - 12-sided 3-dimensional shape", height="100", width="100" />

A dodecahedron is a three-dimensional, 12 sided shape as seen in this picture.
Each side of the dodecahedron could be given a label to describe one phase of a
security breach.  One of the advantages of using a 3 dimensional shape is that
it makes it easy to turn the Breach Dodecahedron into vendor swag or booth toys
for next year’s RSA conference.  The shape also helps to illustrate the fact
that an attacker might move to any of a number of phases during an attack and
may not take a serial path from one step to the next.  Just like with the
Kübler-Ross model of grieving, a person might move backwards or skip a step
before reaching the end. The primary weakness of using the dodecahedron is that
you can’t easily put it on a t-shirt or print it in a brochure.

The 12 phases of the Breach Dodecahedron are as follows:
1.	Target Selection
2.	Reconnaissance
3.	Scanning
4.	Gaining access
5.	Maintaining Access
6.	Lateral Expansion
7.	Searching for data
8.	Aggregation
9.	Exfiltration
10.	Monetizing
11.	Covering tracks
12.	High Five.

It’s easy to see how an attacker might move through these phases multiple times
or skip some of them.  Some attackers never cover their tracks, and others
surely high five many times during an attack.  A three dimensional shape really
illustrates these possibilities because there are more directions to turn rather
than ahead and backwards.

Scanning and recon sound similar to each other and they are.  The primary
difference is that scanning is considered an active probe to find potential
weaknesses while reconnaissance is a more passive effort to gain information
without making contact.  Google hacking and looking up network information in
ARIN might be considered recon, while an nmap scan would constitute scanning.

You may be wondering how this is different from the [The Five Phase Approach of
Malicious
Hackers](http://blog.phpkemist.com/2008/07/20/the-five-phase-approach-of-malicious-hackers/)
or the [Lockheed Martin Cyber Kill
Chain](http://www.lockheedmartin.com/us/what-we-do/information-technology/cyber-security/cyber-kill-chain.html).
Haven’t I just taken some of the steps from that list and expanded them?  Why is
this list better than that list?  If you're wondering that then you haven't
worked in security for very long. This model is better because 12 is bigger than
5 or 7. Seriously I have added a few phases that were not in that article, but I
also expanded some of the phases so that I could get to 12.  When you’re
building a model like this it isn’t just about being complete; you also have to
have a cool word like dodecahedron which I couldn’t get with only 9 phases.

Organizations should put preventative, detective, and corrective controls in
place to disrupt an attacker at every phase of the Breach Dodecahedron.
However, some of these phases are very difficult to disrupt.  For example,
organizations may try to reduce their visibility as a target, but successful
businesses draw attention to themselves and make good targets for espionage or
activism.  It is also difficult to prevent an attacker from monetizing data that
has been exfiltrated.  And if an attacker successfully exploits a weakness and
gains access it is nearly impossible to prevent the high five from happening. However,
I understand that the good people over at [Threatvertica](http://threatverti.ca) are
working on high-five prevention appliances that they will showcase at a tech show
in the near future.
