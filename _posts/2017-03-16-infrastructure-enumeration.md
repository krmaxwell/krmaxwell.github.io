---
layout: post
title: "Infrastructure Enumeration"
categories: Security
---

During an investigation or analysis, we often want to start with one piece of information, such as a hash or URL, and list as much related infrastructure as possible. By "infrastructure", I mean IP and domain addresses, URLs, and similar host and network identifiers.

These notes provide guidance on some particularly basic methods. But many investigations don't need more than basic methods: 99% of cases involving low-level attacks need triage and remediation, whether dealing with commodity malware, phishing, or generic online fraud.

# Starting points

The methods used will generally depend on whatever data we have at the beginning. For simplicity, let's start with some atomic indicators, but keep in mind that the [Pyramid of Pain](http://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html) means that our ease of investigating them is matched by the adversary's ease of changing them.

## File

Most malware analysts already understand the basics when starting with a piece of malcode or other file. Extracting addresses may occur via static analysis (such as listing out strings or decrypting embedded data) or via dynamic analysis (such as observing C2 comms).  Additionally, searching for the file hash in open sources like Virustotal, Malwr.com, or even Google can occasionally yield URLs indicating locations where the file was observed. This is obviously context-dependent and low-probability, but searching for hashes is also low-effort and low-risk. 

Beware, though, of uploading any files: that can potentially expose a lot more sensitive data than you realize and should only be done if we are absolutely sure of what you have and just want to see how various AV engines will categorize the file. In most investigations, no files should ever be uploaded to a public tool. As an example, Virustotal makes all uploads available for a subscription fee, and lots of other investigators run searches against this corpus and download anything interesting. Additionally, adversaries can search for hashes of files they've run in particular campaigns. If the hash shows up, they know somebody has detected something and can adjust quickly. Uploading files gives away intelligence pointlessly.

## IP address

When given an IP address, we generally want to know the following things, often starting with the mentioned resources:

- Who has this IP address assignment? (IANA WHOIS)
- What names resolve to this address? (reverse DNS or passive DNS)
- What past activity has been associated with this address? (black lists and similar databases)

In some contexts, geolocation may also be useful. Analysts should think carefully about how applicable this information will be in a given situation and beware drawing strong conclusions based on this. 

## Domain name

When given a domain name, first determine whether this is a fully-qualified domain name (e.g. `example.com` or `example.co.uk`) or potentially just a subdomain or even a host name.

For domains, we generally want the following information, with useful resource types listed again:

- What is the registrant's name, location, and especially email address, and has that changed over time? (historical WHOIS)
- What was the date of initial registration (domain age)? (WHOIS)
- What IP addresses has it resolved to? (DNS and passive DNS)
- What registrar, NS records, and MX records have been associated with this domain? (WHOIS and passive DNS)

Registrant data is often fake and should never be assumed to reflect a true identity without corroborating data. However, these data (especially email addresses) can be used to correlate with other data points, as we will see in a moment.

## Email address

In the case of enumerating infrastructure, email addresses can be particularly valuable as registrants.

- What other domains have been associated with this registrant? (Reverse WHOIS)
- What online accounts, chat logs, and other information mention this address? (OSINT, not infrastructure enumeration _per se_)

# Pivoting

Obviously, finding a related indicator one hop away does not necessarily provide much analytic value. Indicators will almost always need to pivot multiple times. For example, if we're investigating a domain name, we can use WHOIS and then reverse WHOIS to determine what other domains may be associated with that same actor. We can then pivot using passive DNS to see what IP addresses are associated with these domains, whether they share infrastructure, and perhaps link to other incidents or campaigns.

As a note, IP addresses can present significant challenges when associated with large hosting providers. Some IP addresses may host hundreds or even thousands of domain names. In those cases, we need to try alternate methods to find related infrastructure.

# Data sources

We have a number of sources available to us for each of these.

- **Files:** VirusTotal, Malwr
- **WHOIS:** DomainTools (includes reverse and historical)
- **Passive DNS:** PassiveTotal, VirusTotal
- **Reverse DNS:** Spyonweb, Robtex, Hurricane Electric
- **Historical activity:** IPVoid/URLVoid, VirusTotal, other OSINT

# Tools

In some cases, these sources include programmatic access (APIs), but for small jobs analysts may wish to look things up manually. I also have a collection of small Python scripts to query data sources, organize the data, and output in a text template. For those comfortable working directly with code, [Jupyter (IPython) Notebook](http://jupyter.org/) has no equal for mixing code, data, and documentation (notes). 

## Maltego

I generally either use Maltego whenever possible, which is purpose-built for pivoting. 

In fact, I've made available a set of [Maltego transforms](https://github.com/krmaxwell/spyonweb) to query Spyonweb. You'll need your own [Spyonweb API key](https://api.spyonweb.com/) first. They have a free tier although the Basic level is really affordable. You can either set up your own remote transforms with my code or use [this seed](https://cetas.paterva.com/TDS/runner/showseed/Ej0UmwSl3GrA) in Maltego directly and use my server. 

Note: I don't have any association with Spyonweb or DevHQ (the company behind it). I'm just a paying customer who has made my own tool available to you. 

# Other comments

The above presents the most straightforward and obvious methods of enumeration. Other advanced methods may apply. For example, some landing pages will use Google Analytics. The script tag will include the Analytics user account ID (e.g. "UA-2309503-4") and that tag may be used on multiple sites. Mirroring and analyzing (exploiting) information from sites may yield additional indicators for further investigation. Another method involves pivoting off of different types of DNS records (not just `A` and `CNAME`).
