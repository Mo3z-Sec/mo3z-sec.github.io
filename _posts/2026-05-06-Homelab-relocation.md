---
title: "Shutting Down the Homelab — For Now"
date: 2026-05-06 10:00:00 +0300
categories: [Blog, homelab]
tags: [proxmox, homelab, cybersecurity]
author: abdul rahman
description: "Temporarily shutting down the homelab due to relocation"
---

After months of building, breaking, fixing, and documenting — the
homelab is officially offline.

Not permanently. Just temporarily.

I'm relocating and the PC stays behind. The HDD comes with me.

---

## What's on That Drive

Everything. The entire lab — Proxmox, all the LXC containers, every
VM, the Active Directory environment, Metasploitable, DVWA, Splunk,
WireGuard, Nextcloud, all of it. Seven months of work sitting on a
single 931GB HDD.

The beauty of running everything on Proxmox is that it's completely
portable in theory. The hypervisor, the configs, the VMs — they all
live on the disk. Plug it into a compatible PC and it boots up exactly
where it left off.

---

## What I Did Before Pulling the Drive

I wasn't just going to yank the HDD and hope for the best. A few
things needed to happen first.

**Photos backup**
My Nextcloud had been quietly backing up my phone photos for months.
Before anything else I tarred the entire data directory and copied
it to a USB drive — about 8GB of photos compressed down to 4GB.
Lossless compression, everything intact. The USB goes in my bag.

**Proxmox backups**
Used Proxmox's built in backup tool to create `.vma.zst` snapshot
backups of every single container and VM. These live on the HDD
itself. If anything gets corrupted during the move or the new PC
has issues, I can restore any machine to exactly this state in
a few clicks.

**Clean shutdown**
Shut everything down in the right order — VMs first, then containers,
then Proxmox itself. Waited for the PC to fully power off before
touching the drive. Sounds obvious but pulling a drive mid-write
is how data gets corrupted.

---

## What Happens When I Plug It Into a New PC

Proxmox is tied to the hardware it was installed on — specifically
the network interface names. A new PC will almost certainly have
different NIC names which will break the network config on first boot.

The fix is straightforward:
- Boot Proxmox (might need `nomodeset` again for GPU issues)
- Find the new NIC name with `ip link show`
- Update `/etc/network/interfaces` with the new name
- Run `ifreload -a`

Everything else — the containers, the VMs, the configs, the data —
should come up exactly as it was. The static routes, IP forwarding,
all of it is saved in the config files on the drive.

---

## What's Next

The lab gets back online as soon as I'm settled. There's still a
lot left on the roadmap:

- OPNsense firewall replacing the current static route setup
- WS02 with intentional misconfigurations for lateral movement practice
- Cowrie SSH honeypot on a dedicated DMZ network
- Grafana dashboards once Splunk has real data flowing
- Sysmon and Splunk Universal Forwarder on the Windows VMs
- The full AD attack simulation I've been building toward

The documentation is all on GitHub. The knowledge isn't going anywhere.
The lab will be back.

---

*Thanks for following along. More updates once I'm back up and running.*