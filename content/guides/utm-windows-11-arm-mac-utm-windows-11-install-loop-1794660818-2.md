---
title: "UTM Windows 11 Install Loop: Break the Restart Cycle Before Setup Completes"
description: "Fix the UTM Windows 11 ARM install loop where Windows Setup restarts at the same screen. Check boot order, ISO integrity, and VM settings to resume installation."
seo_title: "UTM Windows 11 Install Loop: Stop Setup Restarting at the Same Screen"
seo_description: "Fix the UTM Windows 11 ARM install loop where Windows Setup restarts at the same screen. Check boot order, ISO integrity, and VM settings to resume installation."
keywords:
  - "utm windows 11 install loop"
date: 2026-11-15T19:12:17+08:00
publishDate: 2026-11-15T19:12:17+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are installing Windows 11 ARM in UTM on your Apple Silicon Mac, and Windows Setup keeps restarting at the same screen instead of continuing the install.

## Check the boot order first

In UTM, open the VM settings and confirm the virtual DVD/ISO is not first in the boot order after the first restart. Setup writes boot files to the virtual disk, then expects to boot from that disk. If the ISO remains first, the VM re-enters Setup repeatedly. Set the virtual disk as the primary boot device, save, and start the VM again. If Setup still returns to the same screen, the boot files may not have been written correctly.

## Verify the ISO and disk

Re-download the Windows 11 ARM ISO from Microsoft and compare its checksum with the published value. A truncated or corrupted ISO often causes Setup to restart before completing the file copy. Also confirm the virtual disk has at least 64 GB and is attached as the primary drive. If the disk is too small or detached, Setup cannot finish and may loop.

## Run a verification test

Start the VM and watch the first reboot. If it proceeds to the regional settings screen or the desktop, the **utm windows 11 install loop** is resolved. If it returns to the initial Setup language screen, stop the VM and recheck the boot order and ISO checksum before trying again.

## Rollback and recovery

If the loop persists, delete the failed virtual disk and create a new one, then reinstall. Keep the old disk image until the new install succeeds so you can recover any data. For guided diagnosis,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
