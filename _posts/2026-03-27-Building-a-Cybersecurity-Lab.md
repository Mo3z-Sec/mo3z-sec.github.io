---
title: "Red & Blue Lab at Home"
date: 2026-03-27 10:00:00 +0300
categories: [Blog, homelab]
tags: [proxmox, homelab, cybersecurity]
author: abdul rahman
description: "Homelab - to attack, detect, and. defend sytems safely"
---

# Building My Red & Blue Team Cybersecurity Lab

I’ve been building a personal cybersecurity lab to practice both **attacking systems (red team)** and **defending them (blue team)**. It’s still a work in progress, but it’s already been one of the most valuable parts of my learning.

---

## Why I Built This

I didn’t just want to learn tools — I wanted to understand how attacks actually happen and how they’re detected in real time.

So I built a setup where I can:
- Launch attacks from my Kali laptop  
- Monitor activity using tools like Splunk  
- Analyze real attack behavior  

---

## My Approach

The key decision I made early on was **network separation**.

- One network card handles **internet-facing services**  
- The other is **fully isolated**, used for vulnerable machines and testing  

This allows me to safely experiment without risking my main network, while still keeping some services accessible.

---

## Tools I’m Using

- **OPNsense (planned)** – will act as my central firewall and monitoring point inside Proxmox  
- **Suricata (via OPNsense)** – for detecting and eventually blocking malicious traffic  
- **Splunk** – for log analysis and visibility  
- **Cowrie (planned)** – to capture and study real attacker behavior  
- **Vulnerable machines** – for hands-on exploitation practice  

---

## What I’m Working Towards

The next step is integrating **OPNsense into Proxmox** so it can sit between both networks and monitor:

- Traffic coming from the internet  
- Traffic inside my isolated lab  

This will give me full visibility and let me simulate real-world scenarios like:
- Attack detection  
- Lateral movement  
- Defensive response  

---

## Why This Matters

This lab isn’t about having a lot of tools — it’s about understanding **how they work together**.

It’s helping me think like:
- An attacker (how to get in)  
- A defender (how to detect and stop it)  

---

If you’re learning cybersecurity, building something like this is worth it. Even a simple setup can teach you more than hours of theory.

For full configs and updates, check my GitHub: https://github.com/mo3z-sec