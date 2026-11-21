---
title: "UTM Network Not Working: Restore the Missing Adapter in Windows 11 ARM"
description: "Step-by-step fix for UTM network not working in Windows 11 ARM on Apple Silicon Mac. Diagnose missing adapter, verify connectivity, and recover safely."
seo_title: "UTM Network Not Working? Fix the Missing Adapter in Windows 11 ARM"
seo_description: "Step-by-step fix for UTM network not working in Windows 11 ARM on Apple Silicon Mac. Diagnose missing adapter, verify connectivity, and recover safely."
keywords:
  - "utm network not working"
date: 2026-11-21T16:29:42+08:00
publishDate: 2026-11-21T16:29:42+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're running Windows 11 ARM in UTM on your Apple Silicon Mac, but the VM has no network adapter or can't reach the host, and you're stuck before any controlled diagnosis.

## Check the VM's network adapter in UTM

Shut down the VM completely. In UTM, open the VM settings and go to Network. Ensure at least one adapter is enabled. For most setups, choose Shared Network (NAT) and confirm the checkbox is ticked. If you see Emulated VLAN, switch to Shared Network. Save and start the VM.

## Inspect Windows Device Manager

In Windows, right-click Start and open Device Manager. Expand Network adapters. If you see an unknown device or a yellow warning icon, the driver isn't loaded. Right-click the adapter and select Update driver, then Search automatically. If no adapter appears at all, return to UTM settings and verify the network device is present. A missing adapter in both places means the VM configuration lost the network device.

## Verify connectivity

Open Command Prompt in the VM and run ipconfig. You should see an IPv4 address like 192.168.64.x. Then ping the host by running ping 192.168.64.1. A reply confirms the link works. If ping fails, temporarily disable Windows Firewall for testing and retry.

## Rollback and recovery

If changes break networking further, revert to a UTM snapshot taken before editing settings. If no snapshot exists, remove the network adapter in UTM, save, then re-add a Shared Network adapter and restart. This resets the virtual NIC without reinstalling Windows.

If the **utm network not working** issue persists after these checks,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with your UTM version and ipconfig output.
