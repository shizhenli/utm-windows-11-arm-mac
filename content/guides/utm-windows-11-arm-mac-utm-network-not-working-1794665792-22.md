---
title: "UTM Network Not Working: A Controlled Diagnosis Before You Reinstall"
description: "Fix UTM network not working in Windows 11 ARM by checking the VM network mode, adapter presence, and host reachability before reinstalling or resetting the VM."
seo_title: "UTM Network Not Working: Diagnose the Missing Adapter in Windows 11 ARM"
seo_description: "Fix UTM network not working in Windows 11 ARM by checking the VM network mode, adapter presence, and host reachability before reinstalling or resetting the VM."
keywords:
  - "utm network not working"
date: 2026-11-22T12:10:36+08:00
publishDate: 2026-11-22T12:10:36+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are in a Windows 11 ARM VM on an Apple Silicon Mac, and the network does not work in the VM before you have completed a controlled diagnosis.

## Confirm the VM's network mode first

Open UTM, select the VM, and click Edit. Under Network, note the mode. Shared Network is the expected default and usually gives the guest an address from the host. If it is set to Host Only, the VM can reach the Mac but not the internet. If it is set to Bridged, the VM depends on the Mac's active interface. Switch to Shared Network, save, and boot the VM. This isolates whether the mode, not Windows, is the cause.

## Check for the adapter inside Windows

In the VM, open Device Manager and expand Network adapters. A healthy guest shows a virtual Ethernet adapter without a warning icon. If the list is empty, Windows has no driver bound to the virtual NIC. If the adapter shows a yellow warning, the driver is present but not started. In either case, the **utm network not working** symptom is at the virtual hardware layer, not your router.

## Run one verification test

In Windows, open Command Prompt and run ipconfig. Look for an IPv4 address. A 169.254.x.x address means the adapter exists but did not receive a lease. Then run ping 192.168.64.1, the usual Shared Network host address. A reply confirms the link to the Mac works and the fault is upstream. A timeout confirms the virtual link itself is down.

## Rollback and recovery

Before changing drivers or reinstalling, note the original network mode so you can restore it. If a mode change breaks connectivity further, revert to the previous setting and reboot the VM. If the adapter remains missing after reverting, stop and get a second opinion rather than resetting the VM:

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
