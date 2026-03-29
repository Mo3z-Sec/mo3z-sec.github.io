---
title: "What's Next for the Homelab"
date: 2026-03-29 10:00:00 +0300
categories: [Blog, homelab]
tags: [proxmox, homelab, cybersecurity]
author: abdul rahman
description: "Splunk was running but had nothing to watch. Here's what I'm adding to fix that."
---

After getting Splunk up and running I realised I had a problem — nothing
to actually look at. A SIEM with no logs is just a fancy empty dashboard.

That got me thinking about how to generate real traffic worth analyzing,
and I landed on two additions that I think will make the lab genuinely
useful rather than just impressive on paper.

## Cowrie SSH Honeypot

The idea is simple. Deploy a fake SSH server, expose it to the internet,
and let attackers find it. They're scanning for open ports constantly —
they'll find it. Cowrie records everything they do and ships it straight
to Splunk.

Real attackers, real commands, real behaviour. That's the kind of data
you can actually learn detection from. Way more interesting than anything
I could simulate myself.

## OPNsense

The other addition is OPNsense — a proper open source firewall to replace
the basic Proxmox firewall I have now. It gives me full visibility into
what's moving across my network and comes with Suricata built in for
intrusion detection.

Honestly the main reason I want to learn it is career-driven. Firewall
administration is a core skill for anyone working in security and
OPNsense is a solid way to get hands-on with it without needing
enterprise hardware.

## What's Blocking It

Both need a RAM upgrade before I can deploy them alongside everything
else already running. A second 8GB stick for the Dell is next on the
list — once that's in, these are the next two things going up.

Full technical details and config will be on the
[GitHub repo](https://github.com/Mo3z-Sec/homelab) as always.