---
title: "UTM Windows 11 ARM No Disk: Make the Installer See Your Virtual Disk Again"
description: "Windows 11 ARM setup can't find the UTM virtual disk? Follow these checks to restore disk detection before reinstalling."
seo_title: "UTM Windows 11 ARM No Disk: Restore the Missing Virtual Disk"
seo_description: "Windows 11 ARM setup can't find the UTM virtual disk? Follow these checks to restore disk detection before reinstalling."
keywords:
  - "utm windows 11 arm no disk"
date: 2026-11-16T09:09:49+08:00
publishDate: 2026-11-16T09:09:49+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are installing Windows 11 ARM in UTM on an Apple Silicon Mac, and Setup stops at the disk selection screen because no virtual disk appears. This is a common **utm windows 11 arm no disk** symptom, and it usually means the VM's storage isn't attached or visible to the installer, not that Windows is broken.

## Check the VM's drive configuration

Shut down the VM completely, then open its settings in UTM. Under Drives, confirm there is a VirtIO or NVMe drive listed for the Windows installation. If the list is empty, add a new drive and set its size. If a drive exists, note its interface. Windows 11 ARM Setup includes VirtIO storage drivers in recent builds, but older images may not. If you see a drive in UTM but not in Setup, the interface or driver is the likely cause.

## Verify the installer is loading the right image

Make sure the Windows ISO is attached as a CD/DVD drive and that you booted from it. A common mistake is leaving only the installer ISO attached with no target disk. Setup will show no disk because there is nowhere to install. Add the target drive, save, and boot again.

## Run a verification test

Return to the disk selection screen. If the virtual disk now appears, select it and continue. If it still does not, switch the drive interface to NVMe or SATA in UTM settings and retry. A disk that appears after the interface change confirms a driver or interface mismatch.

## Rollback and recovery

If changes make the VM unbootable, revert to your last UTM snapshot or restore the previous drive settings. Do not delete the VM bundle until you have copied any existing data. For guided diagnosis,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
