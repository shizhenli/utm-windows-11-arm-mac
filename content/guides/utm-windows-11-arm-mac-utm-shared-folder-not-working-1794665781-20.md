---
title: "UTM Shared Folder Not Working: Why Windows 11 ARM Shows No Drive and How to Diagnose It"
description: "UTM shared folder configured but no drive appears in Windows 11 ARM? Follow these checks to diagnose the missing share before reinstalling anything."
seo_title: "UTM Shared Folder Not Working: Fix Missing Drive in Windows 11 ARM"
seo_description: "UTM shared folder configured but no drive appears in Windows 11 ARM? Follow these checks to diagnose the missing share before reinstalling anything."
keywords:
  - "utm shared folder not working"
date: 2026-11-22T10:10:16+08:00
publishDate: 2026-11-22T10:10:16+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You set up a share in UTM, but Windows 11 ARM shows no drive letter or network path, so you are stuck at the shared folder is not available in Windows step.

## Check the share in UTM first

Open UTM, select your Windows 11 ARM VM, and go to Settings > Sharing. Confirm the shared folder is listed and enabled. If it is missing, add it again and save. Next, check that the share is not set to read-only if you need write access. A common cause of **utm shared folder not working** is that the share was added to the wrong VM or left disabled after an edit.

## Verify the Windows side

Start the VM and open File Explorer. Look under This PC for a mapped drive, or open \\utm\share in the address bar. If neither appears, open PowerShell as administrator and run `net use` to list connections. An empty list means Windows never received the share. Also check Device Manager for a yellow warning on the VirtIO Serial or Network device, since a missing driver can block the share channel.

## Run a verification test

In PowerShell, run `net view \\utm` and note the result. If it returns the share name, the connection works and only the drive mapping is missing. If it returns a system error, the share channel is not reaching Windows. Reboot the VM once and retest before changing anything else.

## Rollback and recovery

If a recent UTM update or share edit caused the problem, revert to your last VM snapshot or remove and re-add the share with the same path. Keep a snapshot before further changes so you can recover quickly.

If these checks do not restore the share,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with your UTM version and the PowerShell output.
