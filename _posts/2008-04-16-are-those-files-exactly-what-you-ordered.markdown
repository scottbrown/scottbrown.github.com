---
layout: default
title: Are Those Files Exactly What You Ordered?
published: true
categories:
  - information technology
tags:
  - batch
  - security
---

…after all, how would you know?

Batch processing typically involves moving large data files (so called 
extracts) between systems. These data files include can include financial 
information, billing information, reports, blah blah blah. The thing I 
see very often is the verification and authentication of extracts…or 
rather, the lack of it. I believe in the 
[Bruce Schneier school of learning][ref-1], where one must be born with 
the security mindset, as it cannot be learned. As a result, I’m always 
seeing exploitable problems where others just see efficiency.

The problem I see currently with moving large data files around is that 
the files are never verified as being complete. Sure, the transfer 
protocol being used by the underlying operating system says that it does 
a completeness check, but what if the file was tampered before it was 
sent? Whether these files move into different directories or over the 
network, they must be checked each time for completeness and 
authenticity. A simple solution to all of this is to use 
[checksums][ref-2], which has been the solution for authenticating 
downloadable Internet files for many years.

So if checksums are such a simple concept and have been around forever, 
why don’t all companies use them? The first is money. It takes more 
development to put in extra checks around the transfer of files, which 
in turn means a higher cost to the company. Second is that there is a 
lack of security-mindedness in code development today. This isn’t just 
about checking that your code is safe from SQL injections, this is 
about making sure that no part of the system can be subjected to exploit.

Here’s a real-world example. Instead of thinking of transferring extracts 
between systems, let’s translate that to money between transferred 
between a bank’s branch offices to the central hub. Since digital money 
or sci-fi credit systems do not yet exist, the money must instead be 
transferred by armoured vehicles. So which is the best place for someone 
to exploit? The banks can have the most secure environment possible, but 
they must give up some of their security during transport. This is a 
reasonable risk because there are numerous verification protocols in 
place before the money leaves and after it has arrived at the central hub.

Bringing the example back into our problem at hand, there is an inherent 
risk to sending extracts to another directory or over the network. The 
target filesystem can fail, the network can be sniffed, the target 
machine can be a zombie. Secure communications can mitigate that (MITM 
attacks aside) but one can never be certain if the files sent are the 
exact match to the files received.

[ref-1]: http://www.schneier.com/crypto-gram-0804.html#2
[ref-2]: http://en.wikipedia.org/wiki/Checksum

