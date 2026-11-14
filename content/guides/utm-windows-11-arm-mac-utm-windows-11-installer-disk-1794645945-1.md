---
title: "UTM Windows 11 Installer Disk Not Found: A Step-by-Step Fix"
description: "Windows 11 ARM setup can't see your UTM virtual disk? Follow these practical checks to restore disk detection before reinstalling anything."
seo_title: "UTM Windows 11 Installer Disk Not Found? Fix It Step by Step"
seo_description: "Windows 11 ARM setup can't see your UTM virtual disk? Follow these practical checks to restore disk detection before reinstalling anything."
keywords:
  - "utm windows 11 installer disk"
date: 2026-11-14T19:53:00+08:00
publishDate: 2026-11-14T19:53:00+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're in the Windows 11 ARM installer on your Apple Silicon Mac, and setup stops at the disk selection screen with no virtual disk listed. Here's how to diagnose this without reinstalling yet.

## Check the VM's drive configuration first

Shut down the VM completely. In UTM, open the VM settings and inspect the Drives section. Confirm there is a VirtIO or NVMe drive attached and that its size is what you expect. If the drive is missing entirely, add a new drive and set the interface to VirtIO. If it exists but shows 0 bytes, the disk image may be corrupt. Note the exact interface type; Windows 11 ARM setup needs a driver for VirtIO. If you used VirtIO, switch temporarily to NVMe and retry the installer. If the disk appears with NVMe but not VirtIO, the missing driver is your cause.

## Load the storage driver during setup

If the disk still doesn't appear, download the VirtIO drivers ISO from the Fedora project. Attach it as a CD/DVD drive in UTM. In the installer, click Load driver, browse to the viostor folder for ARM64, and install it. The disk should then appear. If setup reports no compatible driver found, you likely selected the wrong architecture folder.

## Verification test

After loading the driver or switching to NVMe, refresh the disk list. A correctly detected disk shows its full size and is selectable. If it appears, proceed with installation. If it doesn't, create a fresh VM with a new disk and test the installer there to isolate whether the issue is the VM config or the disk image.

## Rollback note

If switching interfaces or adding drivers makes things worse, revert to your previous UTM settings snapshot before changing anything else. For hands-on help with your **utm windows 11 installer disk** configuration,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
