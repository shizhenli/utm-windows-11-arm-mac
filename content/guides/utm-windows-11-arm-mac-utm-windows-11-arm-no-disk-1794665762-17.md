---
title: "UTM Windows 11 ARM No Disk: Why Setup Can't See the Virtual Disk"
description: "Windows 11 ARM setup can't see your UTM virtual disk? Follow these checks to diagnose the missing disk before reinstalling."
seo_title: "UTM Windows 11 ARM No Disk: Fix Installer Can't Find Virtual Disk"
seo_description: "Windows 11 ARM setup can't see your UTM virtual disk? Follow these checks to diagnose the missing disk before reinstalling."
keywords:
  - "utm windows 11 arm no disk"
date: 2026-11-21T16:35:53+08:00
publishDate: 2026-11-21T16:35:53+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're installing Windows 11 ARM in UTM on your Apple Silicon Mac, and at the disk selection screen, no virtual disk appears—so setup can't continue.

## Check the VM's drive configuration

Shut down the VM and open its settings in UTM. Under Drives, confirm there is a VirtIO or NVMe drive attached and that it's not set to "None." If the drive exists but Windows Setup still shows nothing, the installer likely lacks the matching storage driver. For VirtIO disks, you must load the VirtIO storage driver during setup. Download the VirtIO drivers ISO, attach it as a second CD/DVD drive, then at the disk screen click "Load driver" and browse to the viostor folder for your architecture. After loading, the disk should appear. If you prefer to avoid driver loading, switch the drive interface to NVMe or SATA and restart the installer.

## Verify the disk is detected

After making changes, boot the installer again and reach the disk selection step. A working configuration lists at least one disk with its size. If it still doesn't appear, open a command prompt from the installer (Shift+F10) and run diskpart, then list disk. An empty list confirms the guest cannot see any block device—pointing to a VM configuration issue rather than a Windows problem.

## Rollback and recovery

If you changed the drive type and the installer now fails elsewhere, revert to the previous drive setting in UTM and reattach the original ISO. Your existing virtual disk file remains intact unless you manually deleted it; do not format or recreate it until you've confirmed the correct driver or interface.

This **utm windows 11 arm no disk** issue is usually resolved by loading the VirtIO driver or switching the disk interface. If the disk still won't appear,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with your VM settings and diskpart output.
