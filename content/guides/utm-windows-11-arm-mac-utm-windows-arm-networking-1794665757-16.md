---
title: "UTM Windows 11 ARM Networking: Diagnose the Missing Adapter Before Reinstalling"
description: "Fix UTM Windows 11 ARM networking when the VM has no network adapter or cannot reach the host. Step-by-step diagnosis and verification."
seo_title: "UTM Windows 11 ARM Networking: Fix No Network Adapter"
seo_description: "Fix UTM Windows 11 ARM networking when the VM has no network adapter or cannot reach the host. Step-by-step diagnosis and verification."
keywords:
  - "utm windows arm networking"
date: 2026-11-21T16:35:53+08:00
publishDate: 2026-11-21T16:35:53+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are running Windows 11 ARM in UTM on your Apple Silicon Mac, and the VM shows no network adapter or cannot reach the host, so you are stuck before you can complete a controlled diagnosis.

## Check the VM network device first

Open UTM, select the VM, and click Edit. Go to Network. Confirm a network device is present. If it says None, add a device. For most setups, choose Emulated VLAN or Shared Network. Save and start the VM. In Windows, open Device Manager and expand Network adapters. If you see an unknown device or no adapter, the guest driver is missing or the virtual hardware is not attached. If you see an adapter with a warning, note the error code. A healthy adapter appears without a warning.

## Confirm the guest sees a link

In Windows, open Settings, Network & Internet, and check the status. If it says no network, run Command Prompt as administrator and type ipconfig /all. A valid IPv4 address (for example, 192.168.x.x or 10.0.x.x) means the adapter is working. A 169.254.x.x address means DHCP failed. If ipconfig shows no adapter, return to UTM and recheck the network device.

## Test host reachability

From the VM, ping the host Mac's IP address. If ping fails, switch the UTM network mode to Shared Network and restart the VM. This is a common fix for **utm windows arm networking** issues. Then ping again.

## Verification test

Open a browser in the VM and load a simple site, or run ping 1.1.1.1. Success means replies return and the page loads. Failure means the adapter or DHCP is still misconfigured.

## Rollback and recovery

If changes make things worse, revert the UTM network setting to its previous mode and restart the VM. If the adapter disappears after a Windows update, use Device Manager to scan for hardware changes. For guided diagnosis,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
