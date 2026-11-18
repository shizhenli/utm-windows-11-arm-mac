---
title: "UTM Shared Folder Not Working: Why Windows 11 ARM Shows No Drive or Path"
description: "UTM share is configured but no drive or network path appears in Windows 11 ARM. Follow these checks to restore the shared folder without reinstalling."
seo_title: "UTM Shared Folder Not Working on Windows 11 ARM: Fix Missing Drive"
seo_description: "UTM share is configured but no drive or network path appears in Windows 11 ARM. Follow these checks to restore the shared folder without reinstalling."
keywords:
  - "utm shared folder not working"
date: 2026-11-18T12:13:18+08:00
publishDate: 2026-11-18T12:13:18+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You set up a shared folder in UTM for your Windows 11 ARM VM, but inside Windows no drive letter or network path appears, so you cannot reach your Mac files. This is a common configuration mismatch, not a broken VM.

## Check the UTM share mode and path
Shut down the VM, open its settings, and go to Sharing. Confirm the folder is enabled and note whether it uses VirtioFS or a network share. If VirtioFS is selected, Windows needs the matching driver. If the path contains spaces or special characters, move the folder to a simple path like /Users/Shared/VMShare and re-add it. Start the VM and open File Explorer. A working VirtioFS share usually appears under This PC as a drive or under Network; if nothing appears, continue below.

## Verify the Windows side
Open Device Manager and look under System devices for a Virtio FS device. A yellow warning icon means the driver is missing or failed to load. Open Services and confirm the UTM guest tools or VirtioFS service is running. Then open PowerShell as administrator and run `net use` to list mapped connections; an empty list confirms Windows has not mounted the share. If the service is stopped, start it and recheck This PC.

## Verification test
Create a small text file on the Mac inside the shared folder. In Windows, open Command Prompt and run `dir \\?\C:\` or check This PC again. If the file appears, the share is working. If not, the mount layer is still failing.

## Rollback and recovery
Before changing drivers, create a UTM snapshot. If a driver update breaks boot, restore the snapshot and switch the share mode from VirtioFS to a network share as a fallback. If the **utm shared folder not working** symptom persists after these checks, stop reinstalling Windows and

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) so the share configuration can be reviewed directly.
