---
title: "UTM Windows 11 Installer Disk Restart Loop: Break the Cycle Before You Reinstall"
description: "Fix the UTM Windows 11 ARM installer disk boot loop where setup restarts at the same screen. Step-by-step checks, verification, and rollback for Apple Silicon Macs."
seo_title: "UTM Windows 11 Installer Disk Boot Loop: Stop the Restart Cycle"
seo_description: "Fix the UTM Windows 11 ARM installer disk boot loop where setup restarts at the same screen. Step-by-step checks, verification, and rollback for Apple Silicon Macs."
keywords:
  - "utm windows 11 installer disk"
date: 2026-11-22T09:10:08+08:00
publishDate: 2026-11-22T09:10:08+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are running a Windows 11 ARM VM in UTM on your Apple Silicon Mac, and the installer keeps restarting at the same screen instead of continuing—this is the classic boot loop tied to the installer disk.

## First, confirm the loop pattern

Watch one full cycle. If the VM shows the Windows logo, spins, then returns to the same setup screen without a new progress message, the installer disk is being re-read as if boot media. That is your baseline. If instead you see a specific error code, stop here—this is a different failure.

## Check the boot order and disk attachment

Open the VM settings in UTM. Under Drives, verify the installer ISO is attached as a CD/DVD drive, not as a hard disk. Then check the boot order: the virtual hard disk should be first after the first reboot. If the ISO remains first, setup will loop. Also confirm the target disk is attached and shows a capacity; if it is missing, the **utm windows 11 installer disk** cannot hand off to the installed system.

## Verification test

Detach the ISO, save, and start the VM. If Windows Setup no longer appears and the VM either boots the installed system or shows a clear “no bootable device” message, the loop is broken and the installer disk was the cause. Reattach the ISO only when you need to repair.

## Rollback note

If detaching the ISO leaves you with no bootable system, reattach it, boot to setup, and use Repair your computer to run startup repair. Keep a snapshot before changes so you can revert.

If the cycle persists after these checks,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with your VM settings and the exact screen sequence.
