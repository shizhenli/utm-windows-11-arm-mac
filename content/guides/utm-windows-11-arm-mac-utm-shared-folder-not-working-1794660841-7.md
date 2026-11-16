---
title: "UTM Shared Folder Not Working: Make the Share Appear in Windows 11 ARM"
description: "A focused fix for when a UTM share is configured but no drive or network path appears in Windows 11 ARM. Check the share mode, mount it manually, and verify access."
seo_title: "UTM Shared Folder Not Working in Windows 11 ARM: Fix the Missing Drive"
seo_description: "A focused fix for when a UTM share is configured but no drive or network path appears in Windows 11 ARM. Check the share mode, mount it manually, and verify access."
keywords:
  - "utm shared folder not working"
date: 2026-11-16T12:33:23+08:00
publishDate: 2026-11-16T12:33:23+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You configured a share in UTM, but Windows 11 ARM shows no drive or network path, so you are stuck before any diagnosis can begin. Here is a controlled way to make the share visible.

## Confirm the share mode in UTM

Shut down the VM, open its settings, and select the shared folder entry. Check that the directory path is correct and that the share is enabled. Note the share name exactly. If the mode is set to a read-only or restricted option, switch to the standard sharing mode, save, and start the VM again. A wrong mode or a typo in the path is the most common reason the guest never sees the share.

## Mount the share manually in Windows

In Windows 11 ARM, open File Explorer and look under Network. If nothing appears, open Command Prompt and run `net use Z: \\Mac\ShareName`, replacing ShareName with the exact name from UTM. Interpret the result: a success message means the share exists and only discovery failed; an error such as system error 53 means the name or path is wrong; error 67 means the share is not reachable. Correct the name in UTM and retry.

## Verification test

Create a small text file on the Mac inside the shared folder. In Windows, open the mounted drive and confirm the file appears. Then create a file in Windows and check it on the Mac. If both directions work, the share is restored. If only one direction works, the share mode is still restricted.

## Rollback note

If manual mounting fails repeatedly, remove the shared folder entry in UTM, save, and add it again with a simple path and name. This resets the configuration without touching the VM disk. If the share still does not appear,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with the exact error text. For any **utm shared folder not working** case, record the error code before changing settings again.
