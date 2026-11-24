---
title: "UTM Windows 11 Installer Disk Not Visible: Restore Disk Detection"
description: "Windows 11 setup can't see your UTM virtual disk? Follow these checks to restore disk detection before reinstalling."
seo_title: "UTM Windows 11 Installer Disk Not Visible: Fix Disk Detection"
seo_description: "Windows 11 setup can't see your UTM virtual disk? Follow these checks to restore disk detection before reinstalling."
keywords:
  - "utm windows 11 installer disk"
date: 2026-11-24T09:10:11+08:00
publishDate: 2026-11-24T09:10:11+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're installing Windows 11 ARM in UTM on your Apple Silicon Mac, and setup stops at the disk selection screen because no virtual disk appears. Here's how to diagnose the **utm windows 11 installer disk** issue without reinstalling yet.

## Check the virtual disk attachment

Shut down the VM. In UTM, open the VM settings and go to Drives. Confirm a VirtIO or NVMe drive exists and is enabled. If it's missing, add a new drive and set the interface to VirtIO. If it's present, note the interface type; Windows 11 ARM setup often lacks drivers for VirtIO unless you load them. Switch the drive to NVMe or SATA, save, and boot the installer again.

## Interpret what setup shows

At the disk screen, if you see no disks, click Load driver and browse to the virtio-win ISO if attached. If the list stays empty, the controller isn't recognized. If a disk appears but is marked offline or unallocated, that's a different issue: select it and click Next after formatting. A missing disk means the controller or attachment is the problem, not the disk itself.

## Verification test

Create a new temporary VM with a 64 GB NVMe drive and attach the same Windows 11 ARM ISO. Boot it and reach the disk screen. If the disk appears there, your original VM's drive configuration is the cause. If it doesn't, the ISO or UTM version needs attention.

## Rollback note

Before changing interfaces, duplicate the VM or snapshot it. If switching to NVMe causes boot issues later, revert to the snapshot and try loading VirtIO drivers instead.

If these steps don't restore detection,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with your UTM version and drive settings.
