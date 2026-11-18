---
title: "Windows 11 Installer Cannot Find a Virtual Disk in UTM: A Controlled Diagnosis"
description: "Stuck at the disk selection screen because Windows 11 setup cannot see your UTM virtual disk? Follow these checks to confirm the cause and restore the installer disk."
seo_title: "UTM Windows 11 Installer Disk Not Found: Fix Before Reinstalling"
seo_description: "Stuck at the disk selection screen because Windows 11 setup cannot see your UTM virtual disk? Follow these checks to confirm the cause and restore the installer disk."
keywords:
  - "utm windows 11 installer disk"
date: 2026-11-18T10:38:35+08:00
publishDate: 2026-11-18T10:38:35+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are running a Windows 11 ARM VM in UTM on an Apple Silicon Mac, and Windows Setup stops at the disk selection screen because it cannot see the virtual disk. Before reinstalling, work through these checks to confirm the cause.

## Check the VM's drive configuration

Shut down the VM and open its settings. Under Drives, confirm a VirtIO or NVMe drive is attached and that its size is not zero. If the drive is missing, add a new drive and set the interface to VirtIO. Save, then boot the installer again. If the drive appears but is uninitialized, Setup may still list it after you load the driver.

## Load the storage driver during setup

At the disk screen, click Load driver and browse to the mounted VirtIO driver ISO. Select the ARM64 folder, then the viostor or vioscsi driver, and install it. If the disk appears immediately afterward, the missing driver was the cause. If Setup reports no compatible driver, your ISO may be x64 rather than ARM64; replace it with an ARM64 build.

## Verify the expected result

After loading the driver, the disk list should show one unallocated drive matching the size you configured. If it does, the **utm windows 11 installer disk** is now visible and you can proceed. If the list stays empty, detach and reattach the drive, then repeat the driver load.

## Rollback and recovery

If changes make things worse, revert the VM to its previous settings snapshot or remove the newly added drive. Keep your existing disk image untouched until Setup sees it, so no data is lost.

For a guided review of your VM configuration,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
