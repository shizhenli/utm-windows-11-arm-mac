---
title: "UTM Windows 11 ARM Install Loop: Break the Restart Cycle Before Setup Completes"
description: "Stuck in a UTM Windows 11 ARM install loop? Learn how to diagnose the restart cycle, verify the fix, and recover your VM without reinstalling from scratch."
seo_title: "UTM Windows 11 Install Loop: Fix the Restart Cycle"
seo_description: "Stuck in a UTM Windows 11 ARM install loop? Learn how to diagnose the restart cycle, verify the fix, and recover your VM without reinstalling from scratch."
keywords:
  - "utm windows 11 install loop"
date: 2026-11-28T22:26:33+08:00
publishDate: 2026-11-28T22:26:33+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are running Windows 11 ARM in UTM on an Apple Silicon Mac, and the installer keeps restarting at the same screen instead of finishing the setup. This is a frustrating **utm windows 11 install loop**, but it is usually caused by a boot order or ISO issue that you can check quickly.

## Check the Boot Order and ISO

First, shut down the VM completely. In UTM, open the VM settings and go to the Drives tab. Confirm the Windows 11 ARM ISO is attached to the virtual CD/DVD drive and that the virtual hard disk is listed as the primary boot device. If the ISO is still first in the boot order, Windows setup will restart into the installer instead of the installed system. Move the hard disk to the top of the boot order, save, and start the VM again.

Next, verify the ISO is the ARM64 version, not x64. An x64 ISO can cause setup to fail and restart. Check the file name and size; ARM64 images are typically labeled clearly. If you are unsure, re-download the ISO from Microsoft and reattach it.

## Verification Test

Start the VM and watch the first restart. If setup continues to the region and account screens without returning to the initial language prompt, the loop is broken. If it still restarts at the same screen, detach the ISO after the first reboot and boot from the hard disk only.

## Rollback and Recovery

If the loop persists, revert to a snapshot taken before the install, or create a new VM and attach the verified ARM64 ISO. Do not delete the existing virtual disk until you confirm the new VM boots. For hands-on help,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
