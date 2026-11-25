---
title: "UTM Windows 11 ARM Installer Disk Boot Loop: Stop the Restart Cycle"
description: "Stuck in a Windows 11 ARM installer boot loop on UTM? Learn how to check the installer disk, verify boot order, and break the restart cycle safely."
seo_title: "Fix UTM Windows 11 Installer Disk Boot Loop on Apple Silicon"
seo_description: "Stuck in a Windows 11 ARM installer boot loop on UTM? Learn how to check the installer disk, verify boot order, and break the restart cycle safely."
keywords:
  - "utm windows 11 installer disk"
date: 2026-11-25T11:10:09+08:00
publishDate: 2026-11-25T11:10:09+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are running a Windows 11 ARM VM on an Apple Silicon Mac with UTM, and Windows Setup keeps restarting at the same screen instead of continuing the install. This is a common boot-loop symptom tied to how the installer disk is attached and prioritized.

## Check the installer disk attachment

Shut down the VM completely. In UTM, open the VM settings and inspect the drive list. Confirm the Windows 11 ARM ISO is attached as a CD/DVD drive, not as a hard disk. If it appears as a removable USB or hard disk, remove it and re-add it as a CD/DVD. Then check that the virtual hard disk you intend to install Windows onto is present and listed after the CD/DVD in boot order. Result interpretation: if the ISO is the only bootable device, Setup will restart into itself repeatedly. The virtual hard disk must be visible and bootable after installation.

## Verify boot order and firmware

Open the VM's boot order settings. Set the CD/DVD drive first for the initial install, and ensure the virtual hard disk is second. If UTM offers a one-time boot menu, use it to select the CD/DVD explicitly. Save changes and start the VM. If Setup still restarts at the same screen, detach the ISO after the first reboot phase, then let the VM boot from the virtual hard disk.

## Verification test

Start the VM and watch the first reboot. When the screen flashes, confirm the VM is now booting from the virtual hard disk rather than the installer disk. If Windows continues to the region selection or account setup, the loop is resolved.

## Rollback and recovery

If the VM becomes unbootable, shut it down, reattach the **utm windows 11 installer disk**, and boot from it to run Startup Repair. Keep a snapshot before changes so you can revert. For guided diagnostics,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
