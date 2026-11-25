---
title: "UTM Windows 11 ARM No Disk: What to Check Before You Reinstall"
description: "Windows 11 ARM setup can't see the UTM virtual disk? Follow these checks to confirm the disk exists, is attached, and is recognized before reinstalling."
seo_title: "UTM Windows 11 ARM No Disk: Fix Missing Virtual Disk"
seo_description: "Windows 11 ARM setup can't see the UTM virtual disk? Follow these checks to confirm the disk exists, is attached, and is recognized before reinstalling."
keywords:
  - "utm windows 11 arm no disk"
date: 2026-11-25T09:10:13+08:00
publishDate: 2026-11-25T09:10:13+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're in the Windows 11 ARM installer on your Apple Silicon Mac, and the disk selection screen shows nothing—no drive to install to.

## Confirm the virtual disk exists in UTM
Shut down the VM and open its settings. Under Drives, check that a VirtIO disk is listed and has a non-zero size. If the list is empty, add a new disk and set the interface to VirtIO. If a disk is present, note its size; a 0 GB entry means the disk file is missing or corrupt.

## Check the drive order and interface
In the same Drives panel, make sure the Windows ISO is attached as a CD/DVD and the virtual disk is not. If the disk is set to IDE or SCSI, switch it to VirtIO and save. Then start the VM and return to the disk selection screen.

## Load the VirtIO storage driver
If the disk still doesn't appear, the installer likely lacks the VirtIO driver. At the disk screen, click Load driver, browse to the mounted VirtIO ISO, and select the viostor driver for Windows 11 ARM. After installation, the disk should be visible.

## Verification test
After any change, boot the installer and reach the disk selection step. A working setup lists the VirtIO disk with its expected size. If it appears, you've resolved the **utm windows 11 arm no disk** issue and can proceed.

## Rollback note
If a new disk or driver change makes the VM unbootable, revert to the previous UTM settings snapshot or remove the added disk and reattach the original. Keep a copy of the VM bundle before editing.

Still stuck?

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
