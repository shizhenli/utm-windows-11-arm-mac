---
title: "UTM Windows 11 ARM Networking: Fix the Missing Adapter Before You Reinstall"
description: "Step-by-step fix for UTM Windows 11 ARM networking when the VM has no network adapter or cannot reach the host. Diagnose shared vs bridged mode and verify with ping."
seo_title: "UTM Windows 11 ARM Networking: Fix the Missing Adapter"
seo_description: "Step-by-step fix for UTM Windows 11 ARM networking when the VM has no network adapter or cannot reach the host. Diagnose shared vs bridged mode and verify with ping."
keywords:
  - "utm windows arm networking"
date: 2026-11-18T08:10:21+08:00
publishDate: 2026-11-18T08:10:21+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're running Windows 11 ARM in UTM on an Apple Silicon Mac, and the VM shows no network adapter or can't reach the host, so you're stuck before you can complete a controlled diagnosis. Let's fix the adapter first.

## Check the VM's network mode

Open UTM, select your Windows 11 ARM VM, and click Edit. Go to Network. If the mode is Emulated VLAN or Host Only, switch it to Shared Network. Shared Network uses the host's connection through NAT and is the most reliable default for **utm windows arm networking**. Save and start the VM.

## Confirm Windows sees an adapter

Inside Windows, open Settings > Network & Internet. If it says no adapter, open Device Manager and expand Network adapters. A missing or yellow-marked device means the virtual NIC isn't being presented. Shut down the VM fully, re-open Network settings in UTM, and confirm the adapter is enabled. If it still doesn't appear, remove the network device and add it again as Shared Network.

## Interpret the result

If the adapter appears but shows no internet, run `ipconfig` in Command Prompt. A 169.254.x.x address means DHCP didn't respond; switch to Bridged (Advanced) and pick your Mac's active interface. A valid 192.168.x.x address means the adapter works and the problem is upstream.

## Verification test

From Windows, run `ping 8.8.8.8`. Replies confirm outbound networking. Then run `ping <host-ip>` using your Mac's IP from System Settings > Network. If the first succeeds and the second fails, host-to-VM isolation is the remaining issue.

## Rollback note

If changes make things worse, return Network mode to Shared Network and restart the VM. That restores the default state without reinstalling Windows. For deeper diagnosis,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
