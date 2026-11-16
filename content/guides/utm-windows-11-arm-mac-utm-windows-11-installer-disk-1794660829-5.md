---
title: "UTM Windows 11 Installer Disk Not Detected: Fix the Missing Virtual Disk"
description: "Windows 11 setup can't see your UTM virtual disk? Follow these checks to restore disk detection and complete the installer."
seo_title: "UTM Windows 11 Installer Disk Not Detected: Fix Missing Virtual Disk"
seo_description: "Windows 11 setup can't see your UTM virtual disk? Follow these checks to restore disk detection and complete the installer."
keywords:
  - "utm windows 11 installer disk"
date: 2026-11-16T10:09:52+08:00
publishDate: 2026-11-16T10:09:52+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're in the Windows 11 ARM installer on your Apple Silicon Mac, but setup can't find a virtual disk and won't let you continue.

## Check the VM's drive configuration

Shut down the VM completely, then open its settings in UTM. Under Drives, confirm there is a VirtIO or NVMe drive attached and that it is not set to an empty or read-only image. If the drive is missing, add a new disk and save. If it exists, note its interface type; Windows 11 ARM setup needs a driver for VirtIO, so switching to NVMe often resolves detection issues.

## Verify the installer sees the controller

Boot back into setup and press Shift+F10 to open Command Prompt. Run `diskpart`, then `list disk`. If your virtual disk appears here but not in the GUI, the issue is a missing storage driver. Load the VirtIO driver from your installation media or switch the disk to NVMe and retry.

## Confirm the expected result

After adjusting the drive type or loading the driver, return to the disk selection screen. You should now see the virtual disk listed with its full capacity. Select it and continue. If it still doesn't appear, the **utm windows 11 installer disk** configuration likely needs a fresh disk image.

## Rollback and recovery

Before changing anything, duplicate your VM in UTM so you can revert. If the new disk still isn't detected, delete the added disk, restore your backup, and recreate the VM with an NVMe drive from the start. For hands-on help,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
