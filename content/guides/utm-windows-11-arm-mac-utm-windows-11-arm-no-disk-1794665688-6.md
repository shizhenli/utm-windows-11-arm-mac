---
title: "UTM Windows 11 ARM No Disk: Make the Installer See the Virtual Disk Again"
description: "Windows 11 ARM setup cannot find the UTM virtual disk? Follow these checks to restore disk detection without reinstalling the VM."
seo_title: "UTM Windows 11 ARM No Disk: Restore the Missing Virtual Disk"
seo_description: "Windows 11 ARM setup cannot find the UTM virtual disk? Follow these checks to restore disk detection without reinstalling the VM."
keywords:
  - "utm windows 11 arm no disk"
date: 2026-11-21T16:32:48+08:00
publishDate: 2026-11-21T16:32:48+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are in the Windows 11 ARM installer on your Apple Silicon Mac, and the disk selection screen shows no virtual disk to install onto.

## Check the VM drive attachment first

Shut down the VM completely. In UTM, open the VM settings and inspect the drive list. Confirm a VirtIO or NVMe drive exists and is enabled. If the drive is missing, add a new drive and set the interface to VirtIO. If it is present but empty, note its size; a zero-byte or detached drive will not appear in setup. Save, then start the VM and return to the disk screen. If the drive now appears, the attachment was the cause.

## Load the storage driver during setup

If the drive is attached but still invisible, the installer likely lacks a VirtIO storage driver. On the disk screen, choose Load driver, browse to the mounted virtio-win ISO, and select the matching ARM64 storage driver folder. After loading, click Refresh. A disk entry should appear. If setup reports no compatible driver, the ISO is the wrong architecture; use the ARM64 build.

## Verification test

Create a fresh test VM with one small VirtIO disk and boot the same installer. If the disk appears there, your original VM configuration is at fault; compare drive settings side by side. If it does not appear in the test VM either, the installer media or driver ISO is the problem.

## Rollback and recovery

Before changing attachments, duplicate the VM so you can revert. If a new drive does not help, remove it and restore the previous settings. For persistent **utm windows 11 arm no disk** failures after these checks,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with your VM settings and driver ISO version.
