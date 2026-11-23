---
title: "UTM Windows 11 Install Loop: Break the Restart Cycle Before Setup Begins"
description: "Stuck in a UTM Windows 11 install loop? Learn how to diagnose and fix the restart cycle at the Windows installer screen with practical steps."
seo_title: "UTM Windows 11 Install Loop: Stop Setup Restarting"
seo_description: "Stuck in a UTM Windows 11 install loop? Learn how to diagnose and fix the restart cycle at the Windows installer screen with practical steps."
keywords:
  - "utm windows 11 install loop"
date: 2026-11-23T11:10:19+08:00
publishDate: 2026-11-23T11:10:19+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're running a Windows 11 ARM VM on your Apple Silicon Mac with UTM, and the installer keeps restarting at the same screen instead of moving forward.

## Check the boot order and installer media

First, confirm the VM isn't booting from the ISO again after the first restart. In UTM, open the VM settings and go to the Drives tab. Ensure the ISO is listed but not set as the primary boot device after installation begins. If the ISO is first in the boot order, Windows setup will loop back to the installer. Change the boot order to prioritize the virtual hard disk, then save and restart the VM.

Next, verify the ISO integrity. A corrupted download can cause setup to restart prematurely. Compare the SHA-256 hash of your ISO with the official Microsoft value. If it mismatches, re-download the ISO and recreate the VM.

## Interpret the restart behavior

If the VM restarts immediately after the first setup phase, check the UTM console for a brief error message. A missing or misconfigured virtual disk often triggers this. In the Drives tab, confirm the virtual disk is present and set as the primary drive. If it's missing, add a new disk and reattach the ISO.

## Verification test

After adjusting the boot order and confirming the disk, start the VM. The installer should proceed past the initial screen and begin copying files. If it still loops, try creating a new VM from scratch with the same ISO to rule out a corrupted VM configuration.

## Rollback and recovery

If changes worsen the issue, revert to a previous VM snapshot or delete the VM and start fresh. Keep your ISO and any data backed up. For personalized diagnostics,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).

A persistent **utm windows 11 install loop** often points to boot order or media issues, so address those first.
