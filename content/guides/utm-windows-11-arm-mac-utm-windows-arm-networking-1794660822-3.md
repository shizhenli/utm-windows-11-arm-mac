---
title: "UTM Windows 11 ARM Networking: Diagnose and Fix the Missing Adapter"
description: "Step-by-step diagnosis for UTM Windows 11 ARM networking when the VM has no network adapter or cannot reach the host. Check shared network, adapter presence, and IP configuration."
seo_title: "UTM Windows 11 ARM Networking: Fix No Network Adapter"
seo_description: "Step-by-step diagnosis for UTM Windows 11 ARM networking when the VM has no network adapter or cannot reach the host. Check shared network, adapter presence, and IP configuration."
keywords:
  - "utm windows arm networking"
date: 2026-11-16T08:09:49+08:00
publishDate: 2026-11-16T08:09:49+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are running Windows 11 ARM in UTM on an Apple Silicon Mac, and the VM shows no network adapter or cannot reach the host, so you need a controlled diagnosis before changing settings.

## Confirm the VM network mode

Open UTM, select the VM, and click Edit. Under Network, note the mode. Shared Network is the usual choice for internet access; Host Only is for host-only communication. If the mode is Emulated VLAN or Bridged, switch to Shared Network and save. Start the VM and check Device Manager under Network adapters. If no adapter appears, the virtual hardware is not being presented. If an adapter appears with a warning icon, the driver is the issue.

## Check adapter and IP inside Windows

In Windows, open Settings > Network & Internet > Status. If no adapter is listed, return to UTM settings and confirm the network device is enabled. If an adapter exists, run Command Prompt as administrator and type ipconfig /all. Look for a valid IPv4 address. An address starting with 169.254 means DHCP failed. In that case, set a static IP in the same subnet as the host-only network, or switch back to Shared Network and restart the VM.

## Verification test

From the VM, run ping 8.8.8.8. If replies arrive, networking works. If not, run ping followed by the host's IP address. Success there but not on the internet points to DNS or routing; set DNS to 8.8.8.8 and retry.

## Rollback and recovery

Before changing modes, note the original UTM network settings. If a change breaks host access, revert to Shared Network, shut down the VM completely, and restart. For persistent **utm windows arm networking** failures, collect the ipconfig output and UTM network mode, then

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
