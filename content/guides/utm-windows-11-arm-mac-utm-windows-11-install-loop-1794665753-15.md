---
title: "UTM Windows 11 Install Loop: Break the Restart Cycle Before You Reinstall"
description: "Stuck in a UTM Windows 11 install loop where setup restarts at the same screen? Follow these checks to break the cycle and verify a clean install."
seo_title: "Fix UTM Windows 11 Install Loop: Stop Setup Restarting"
seo_description: "Stuck in a UTM Windows 11 install loop where setup restarts at the same screen? Follow these checks to break the cycle and verify a clean install."
keywords:
  - "utm windows 11 install loop"
date: 2026-11-21T16:35:53+08:00
publishDate: 2026-11-21T16:35:53+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're installing Windows 11 ARM in UTM on your Apple Silicon Mac, and setup keeps restarting at the same screen instead of continuing the install.

## Confirm the loop pattern

Watch the first restart carefully. If setup returns to the language screen or the Install now button, the VM is booting from the installer ISO again instead of the virtual disk. That is the **utm windows 11 install loop** pattern. If it instead shows a recovery error, stop here and treat it as a separate boot issue.

## Check boot order and the ISO

Open the VM settings in UTM and inspect the drive order. The installer ISO should be first only for the initial boot. After setup copies files, the virtual disk must be first. If the ISO remains first, remove it or move the disk above it, save, and start the VM again. Also confirm the ISO is the ARM64 Windows 11 build, not an x64 image.

## Check the virtual disk

In the VM's drive list, verify the main disk exists and is at least 64 GB. A missing or undersized disk can make setup restart without writing files. If the disk is missing, add a new VirtIO disk before retrying.

## Verification test

Start the VM and let setup run through the first restart. Success means you see the region and keyboard screens, then the account setup page, without returning to the installer. If the language screen reappears, the boot order is still wrong.

## Rollback and recovery

If changes make the VM unbootable, revert to the last UTM snapshot or restore the previous settings. Keep the ISO attached only until the first restart completes.

Still cycling?

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with your UTM version and drive order.
