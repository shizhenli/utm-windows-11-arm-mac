---
title: "UTM Windows 11 Installer Disk: Break the Setup Restart Loop"
description: "Windows 11 ARM setup keeps restarting at the same screen in UTM? Diagnose the installer disk boot loop with targeted checks and a verification test."
seo_title: "UTM Windows 11 Installer Disk Boot Loop: Fix Setup Restarting"
seo_description: "Windows 11 ARM setup keeps restarting at the same screen in UTM? Diagnose the installer disk boot loop with targeted checks and a verification test."
keywords:
  - "utm windows 11 installer disk"
date: 2026-11-18T11:22:38+08:00
publishDate: 2026-11-18T11:22:38+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are installing Windows 11 ARM in UTM on an Apple Silicon Mac, and Windows Setup restarts at the same screen instead of continuing.

## Confirm the restart is a loop, not a normal reboot

Watch the VM window through one full cycle. A normal setup reboot shows progress text, then continues to the next configuration screen. A loop returns to the same language or install screen with no progress. Note the exact screen title each time; if it is identical, treat it as a loop.

## Check the installer disk attachment

Open the VM settings and inspect the drive list. The **utm windows 11 installer disk** should appear as a removable or CD/DVD device, and the main virtual drive should be listed separately. If the ISO is attached as a fixed hard disk, or if two drives point to the same image, setup can restart itself. Detach the ISO, reattach it as a CD/DVD drive, and confirm the main disk is first in boot order.

## Rule out the ISO and firmware

Verify the ISO checksum against the official Microsoft download page. A truncated image often causes repeated restarts. In the VM settings, confirm UEFI boot is enabled and that no stale saved state is loaded; delete any saved state before booting.

## Verification test

Start the VM and press a key when prompted to boot from the installer. If setup reaches the disk selection screen and stays there, the loop is resolved. If it restarts again at the same screen, the ISO or drive configuration is still wrong.

## Rollback note

Before changing attachments, duplicate the VM in UTM so you can restore the previous configuration. If the loop persists,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with the exact screen title and your drive list.
