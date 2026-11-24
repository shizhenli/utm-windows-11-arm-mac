---
title: "UTM Windows 11 ARM No Disk: Fix the Installer's Missing Virtual Disk"
description: "Windows 11 ARM installer can't see your UTM virtual disk? Follow these checks to diagnose the missing disk and get back to installation."
seo_title: "UTM Windows 11 ARM No Disk: Fix Installer Disk Not Found"
seo_description: "Windows 11 ARM installer can't see your UTM virtual disk? Follow these checks to diagnose the missing disk and get back to installation."
keywords:
  - "utm windows 11 arm no disk"
date: 2026-11-24T08:10:11+08:00
publishDate: 2026-11-24T08:10:11+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're installing Windows 11 ARM in UTM on your Apple Silicon Mac, but at the disk selection screen, Windows Setup reports no disks and you're stuck.

## Check the VM's drive configuration

Open UTM, select your Windows VM, and click Edit. Go to Drives. Confirm there is a VirtIO or NVMe drive listed as the main disk. If it's missing, add a new drive: choose VirtIO (recommended) or NVMe, set the size, and save. If a drive exists but is set to IDE, switch it to VirtIO or NVMe, because Windows 11 ARM setup may not include IDE drivers. After any change, restart the VM and return to the disk selection screen.

## Verify the disk appears in setup

At the Windows Setup disk screen, click Refresh. If the disk still doesn't appear, press Shift+F10 to open Command Prompt. Type diskpart, then list disk. If your virtual disk is listed but setup doesn't show it, the issue is likely a missing driver or partition table. If it's not listed, the VM isn't exposing the drive correctly. This is a common **utm windows 11 arm no disk** symptom.

## Check for a conflicting ISO or attached drive

In UTM's Drives section, ensure the Windows ISO is attached only as a CD/DVD drive, not as a hard disk. An ISO mounted as a disk can confuse setup. Also remove any extra empty drives you don't need.

## Verification test

After adjusting the drive type, boot the VM and reach the disk screen again. If the disk now appears, proceed with installation. If not, create a new VM with a VirtIO disk from the start and test.

## Rollback note

If changes make the VM unbootable, revert to your previous UTM configuration or restore from a snapshot. Keep a backup of the VM bundle before editing.

Still stuck?

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
