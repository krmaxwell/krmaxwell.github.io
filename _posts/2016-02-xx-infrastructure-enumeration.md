---
layout: post
title: "Infrastructure Enumeration"
categories: Security
---
# Introduction

During an investigation or analysis, we often want to start with one piece of information, such as a hash or URL, and list as much related infrastructure as possible.

By "infrastructure" we mean IP and domain addresses, URLs, and similar host and network identifiers.

These notes provide guidance on some basic methods.

# Starting point: file

Most malware analysts already understand the basics when starting with a piece of malcode or other file. Extracting addresses may occur via static analysis (such as listing out strings or decrypting embedded data) or via dynamic analysis (such as observing C2 comms).

Additionally, searching open sources (e.g. Virustotal) for the file hash can occasionally yield URLs indicating locations where the file was observed. This is obviously context-dependent.

# Starting point: IP address

When given an IP address, we generally want to know the following things:

- Who has this IP address assignment? (IANA WHOIS)
- What names resolve to this address? (reverse DNS or passive DNS)
- What past activity has been associated with this address? (Black lists & similar DBs)

In some contexts, geolocation may also be useful. Analysts should think carefully about how applicable this information will be in a given situation and beware drawing strong conclusions based on this.

# Starting point: Domain name

When given a domain name, first determine whether this is a fully-qualified domain name (e.g. `example.com` or `example.co.uk`) or potentially just a subdomain or even a host name.

For domains, we generally want the following information:

- What is the registrant's name, location, and especially email address, and has that changed over time? (historical WHOIS)
- What was the date of initial registration (domain age)? (WHOIS)
- What IP addresses has it resolved to? (DNS and passive DNS)
- What registrar, NS records, and MX records have been associated with this domain? (WHOIS and passive DNS)

Registrant data is often fake and should never be assumed to reflect a true identity without corroborating data. However, these data (especially email addresses) can be used to correlate with other data points, as we will see in a moment.

# Starting point: Email address

In the case of enumerating infrastructure, email addresses can be particularly valuable as registrants.

- What other domains have been associated with this registrant? (Reverse WHOIS)
- What online accounts, chat logs, and other information mention this address? (OSINT, not infrastructure enumeration _per se_)

# Pivoting

Obviously, making one hop does not necessarily provide the needed analytic value. The key here is to pivot multiple times. For example, if we're investigating a domain name, we can use WHOIS and then reverse WHOIS to determine what other domains may be associated with that same actor. We can then pivot using passive DNS to see what IP addresses are associated with these domains, whether they share infrastructure, and perhaps link to other incidents or campaigns.

As a note, IP addresses can present significant challenges when associated with large hosting providers. Some IP addresses may host hundreds or even thousands of domain names. In those cases, we need to try alternate methods to find related infrastructure.

# Data sources

We have a number of sources available to us for each of these.

- **Files:** VirusTotal, Malwr
- **WHOIS:** DomainTools (includes reverse and historical)
- **Passive DNS:** PassiveTotal, VirusTotal
- **Historical activity:** IPVoid/URLVoid, VirusTotal, other OSINT

# Tools

In some cases, these sources include programmatic access (APIs), but for small jobs analysts may wish to look things up manually.

I generally either use Maltego whenever possible, which is purpose-built for this. However, occasionally some transforms are not working completely reliably.

The rest of the time, I have a collection of small Python scripts to query data sources and organize the data. When working more intensely and not using Maltego, I will work directly in a Python REPL (either the default shell or IPython).

# Other comments

The above presents the most straightforward and obvious methods of enumeration. Other advanced methods may apply. For example, some landing pages will use Google Analytics. The script tag will include the Analytics user account ID (e.g. "UA-2309503-4") and that tag may be used on multiple sites. Mirroring and analyzing (exploiting) information from sites may yield additional indicators for further investigation. Another method involves pivoting off of different types of DNS records (not just `A` and `CNAME`).
