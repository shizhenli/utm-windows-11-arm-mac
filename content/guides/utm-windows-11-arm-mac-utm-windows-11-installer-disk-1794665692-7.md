---
title: "UTM Windows 11 Installer Cannot Find Virtual Disk: A Focused Fix"
description: "Windows 11 ARM setup can't see your UTM virtual disk? Follow these checks to restore disk detection before reinstalling."
seo_title: "UTM Windows 11 Installer Disk Not Detected: Step-by-Step Fix"
seo_description: "Windows 11 ARM setup can't see your UTM virtual disk? Follow these checks to restore disk detection before reinstalling."
keywords:
  - "utm windows 11 installer disk"
date: 2026-11-21T16:32:48+08:00
publishDate: 2026-11-21T16:32:48+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're in the Windows 11 ARM installer on your Apple Silicon Mac, and at the disk selection screen, no virtual disk appears. This article helps you diagnose that exact stop point without reinstalling yet.

## Check the UTM drive configuration

Shut down the VM. In UTM, open the VM settings and inspect the drive list. Confirm there is a VirtIO or NVMe drive attached and that its size is what you expect. If the drive is missing, add a new drive and set the interface to VirtIO. If it exists but shows 0 bytes, remove and recreate it; a zero-size drive will never appear in setup.

## Confirm the installer can see the controller

Boot back into setup. On the disk screen, press Shift+F10 to open Command Prompt. Run `diskpart`, then `list disk`. If your virtual disk appears here but not in the setup window, the issue is the installer's storage driver, not the disk. If it does not appear, return to UTM and verify the drive is attached to the correct controller.

## Verification test

After adjusting the drive, restart the VM and reach the disk screen again. A healthy result is the virtual disk listed with its full size and the Next button enabled. If it still fails, try a different drive interface (NVMe instead of VirtIO) as a controlled test.

## Rollback and recovery

Before changing anything, duplicate the VM in UTM so you can revert. If a new drive configuration makes things worse, delete the added drive and restore the duplicate. For guided diagnosis,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).

One common cause is a mismatched **utm windows 11 installer disk** configuration, so verify the drive is attached and sized correctly before reinstalling Windows.
