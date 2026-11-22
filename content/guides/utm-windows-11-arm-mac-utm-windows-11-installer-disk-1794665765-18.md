---
title: "UTM Windows 11 Installer Disk Not Detected: A Controlled Diagnosis"
description: "Windows 11 setup can't see the UTM virtual disk? Follow these checks to diagnose the missing disk before reinstalling."
seo_title: "Fix UTM Windows 11 Installer Disk Not Found"
seo_description: "Windows 11 setup can't see the UTM virtual disk? Follow these checks to diagnose the missing disk before reinstalling."
keywords:
  - "utm windows 11 installer disk"
date: 2026-11-22T08:10:13+08:00
publishDate: 2026-11-22T08:10:13+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're in the Windows 11 ARM installer on your Apple Silicon Mac, and setup stops because it cannot find a virtual disk.

## Check the VM's drive configuration

Shut down the VM completely. In UTM, open the VM settings and inspect the Drives section. Confirm a VirtIO disk exists and is attached to the correct interface. If the disk is missing, add a new VirtIO drive and save. If it exists but is detached, reattach it. Then start the VM and return to the disk selection screen. A listed drive with unallocated space means the disk is visible; an empty list means setup still cannot see it.

## Confirm the installer has the VirtIO storage driver

Windows 11 ARM setup needs the VirtIO block driver to detect the disk. If the disk list is empty, load the driver from a mounted ISO or folder containing the ARM64 VirtIO storage driver. After loading, click Refresh. The disk should appear. If it does not, the driver may be the wrong architecture or the ISO may not be attached.

## Verify with a quick test

Create a new minimal VM with a single VirtIO disk and boot the same installer. If the disk appears there, your original VM's configuration is the problem. If it does not, the installer media or driver source is the issue.

## Rollback note

Before changing disk settings, note the original configuration. If a new disk or driver causes boot failures, revert to the previous settings and reattach the original disk.

If these checks don't restore the expected result,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with your VM settings and driver source details. For the broader **utm windows 11 installer disk** workflow, keep the diagnosis controlled before reinstalling.
