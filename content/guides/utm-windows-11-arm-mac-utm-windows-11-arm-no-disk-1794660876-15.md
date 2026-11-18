---
title: "UTM Windows 11 ARM No Disk: Fix the Missing Virtual Disk at Setup"
description: "Windows 11 ARM setup can't see your UTM virtual disk? Follow these checks to diagnose the missing disk and get the installer to detect it."
seo_title: "UTM Windows 11 ARM No Disk: Fix the Missing Virtual Disk at Setup"
seo_description: "Windows 11 ARM setup can't see your UTM virtual disk? Follow these checks to diagnose the missing disk and get the installer to detect it."
keywords:
  - "utm windows 11 arm no disk"
date: 2026-11-18T09:10:08+08:00
publishDate: 2026-11-18T09:10:08+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're installing Windows 11 ARM on your Apple Silicon Mac with UTM, and the setup stops at the disk selection screen because no virtual disk appears.

## Check the VM's drive configuration

Open UTM and select your Windows 11 ARM VM, then click Edit. Go to Drives and confirm a VirtIO or NVMe drive is listed. If it's missing, add a new drive, set the interface to VirtIO, and choose a size (at least 64 GB). Save and restart the VM. If the drive exists but the installer still shows nothing, the controller type may be wrong: try switching between VirtIO and NVMe, since Windows 11 ARM setup sometimes lacks drivers for one of them.

## Verify the disk is attached and boot order is correct

In the same Drives panel, ensure the virtual disk is not set to Removable and that its image file exists in the VM bundle. Check that the Windows ISO is attached to a separate CD/DVD drive and that the boot order starts with that drive. If the disk was created after the ISO was mounted, reorder the boot entries so setup runs again with the new disk present. This is a common cause of the **utm windows 11 arm no disk** symptom.

## Run a verification test

Start the VM and proceed to the disk selection screen. If the virtual disk now appears, select it and continue. If it still doesn't, shut down the VM, create a fresh disk image in UTM, and repeat the steps. Keep a backup of your VM bundle before making changes so you can roll back if needed.

If the disk remains invisible after these checks,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with your UTM version and VM settings.
