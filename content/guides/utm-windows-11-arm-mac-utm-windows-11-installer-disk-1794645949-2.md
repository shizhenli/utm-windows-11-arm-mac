---
title: "UTM Windows 11 Installer Disk Boot Loop: Stop the Restart Cycle"
description: "Windows 11 ARM setup keeps restarting at the same screen in UTM? Learn how to check the installer disk, break the boot loop, and verify a clean install."
seo_title: "Fix UTM Windows 11 Installer Disk Boot Loop on Apple Silicon"
seo_description: "Windows 11 ARM setup keeps restarting at the same screen in UTM? Learn how to check the installer disk, break the boot loop, and verify a clean install."
keywords:
  - "utm windows 11 installer disk"
date: 2026-11-14T19:53:00+08:00
publishDate: 2026-11-14T19:53:00+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are running a Windows 11 ARM VM in UTM on your Apple Silicon Mac, and Windows Setup restarts at the same screen instead of continuing the install.

## Confirm the boot order and installer disk

Shut down the VM, open its settings, and check the drive order. The **utm windows 11 installer disk** should be first, with the target virtual drive second. If the installer ISO is listed after an empty or partially written disk, UTM may boot from the wrong device and loop.

Next, inspect the target drive in the VM settings. If it is smaller than 64 GB or marked read-only, Windows Setup cannot stage files and will restart. Resize it to at least 64 GB and confirm the format is not set to a locked state.

## Break the loop with a clean setup pass

Start the VM and press a key when prompted to boot from the installer. At the first setup screen, choose your language and click Next, then select Install now. When you reach the disk selection step, delete any existing partitions on the target virtual disk, then select the unallocated space and click Next. This removes partial install data that can trigger the restart cycle.

If setup restarts again before the disk screen, detach the installer ISO, boot once into the VM firmware, then reattach the ISO and retry.

## Verification test

After setup copies files, it should reboot into the "Getting devices ready" phase without returning to the language screen. If you see that progress screen, the loop is resolved. If the language screen returns, stop and capture the exact step where it restarts.

## Rollback note

Before deleting partitions, snapshot the VM so you can revert if the target disk contained data you need. If the loop persists after these checks,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with your UTM version and the step where setup restarts.
