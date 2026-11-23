---
title: "UTM Windows 11 ARM Networking: Diagnose a Missing Adapter or Host Unreachable"
description: "Troubleshoot UTM Windows 11 ARM networking when the VM has no network adapter or cannot reach the host. Step-by-step checks, verification, and rollback."
seo_title: "UTM Windows 11 ARM Networking: Fix No Adapter or Host Unreachable"
seo_description: "Troubleshoot UTM Windows 11 ARM networking when the VM has no network adapter or cannot reach the host. Step-by-step checks, verification, and rollback."
keywords:
  - "utm windows arm networking"
date: 2026-11-23T12:10:21+08:00
publishDate: 2026-11-23T12:10:21+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

## Troubleshooting

You are running Windows 11 ARM in UTM on an Apple Silicon Mac, and the VM either shows no network adapter or cannot reach the host. Start by opening UTM and selecting your Windows VM, then click the settings gear and go to Network. Confirm that a network interface is enabled and set to Shared Network. If it is set to Host Only, change it to Shared Network, save, and restart the VM. Next, inside Windows, open Device Manager and expand Network adapters. If you see a yellow warning icon or no adapter at all, right-click and choose Scan for hardware changes. If the adapter appears but still fails, open Settings > Network & Internet and check that the adapter is not disabled. A quick interpretation: if the adapter is missing entirely, the virtual hardware is not being presented; if it is present but shows no IP, the issue is configuration or DHCP. For a verification test, open Command Prompt in the VM and run ipconfig. You should see an IPv4 address in the 192.168.64.x range for Shared Network. Then run ping 192.168.64.1 to test the host gateway. If ping succeeds, networking is restored. If it fails, switch the network mode to Bridged, restart, and test again. This isolates whether the problem is the shared network service. For rollback, note your original network mode before changing it; if Bridged causes issues, revert to Shared Network and restart. If the adapter still does not appear, remove the network device in UTM settings, save, then add it back and restart. For deeper **utm windows arm networking** diagnosis,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
