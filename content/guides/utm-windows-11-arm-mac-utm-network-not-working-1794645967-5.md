---
title: "UTM Network Not Working: Fix the Missing Adapter in Windows 11 ARM"
description: "Fix a missing network adapter in a Windows 11 ARM VM on UTM. Check the virtual adapter, switch modes, and verify connectivity with a simple test."
seo_title: "UTM Network Not Working: Restore the Windows 11 ARM Adapter"
seo_description: "Fix a missing network adapter in a Windows 11 ARM VM on UTM. Check the virtual adapter, switch modes, and verify connectivity with a simple test."
keywords:
  - "utm network not working"
date: 2026-11-15T19:12:17+08:00
publishDate: 2026-11-15T19:12:17+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You started your Windows 11 ARM VM in UTM, but Windows shows no network adapter, and you cannot reach the host or the internet.

## Check the virtual network adapter first

Open UTM, select the VM, and click Edit. Go to Network. Confirm that a network adapter is listed and enabled. If the list is empty, add one and choose Shared Network. Save, then start the VM. In Windows, open Device Manager and expand Network adapters. A working setup shows a virtual Ethernet adapter without a warning icon. If you see an unknown device, right-click it and choose Update driver, then search automatically.

## Interpret the result

If the adapter appears but Windows still cannot reach the host, the problem is likely the network mode. Shut down the VM, return to Edit, and switch from Shared Network to Bridged, or the reverse. Save and boot again. If the adapter is missing entirely, remove the network device, add a new one, and keep the default emulated model. This is the most common cause of **utm network not working** before any diagnosis is done.

## Verification test

In Windows, open Command Prompt and run ipconfig. You should see an IPv4 address such as 192.168.64.x for Shared Network. Then run ping 192.168.64.1 to test the host gateway. A reply confirms the link works. If ping fails, recheck the adapter mode.

## Rollback note

If the new settings make things worse, shut down the VM, return to Edit, and restore the previous network mode and adapter. Keep a note of the original values before changing them.

If these steps do not restore connectivity,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with your UTM version and the ipconfig output.
