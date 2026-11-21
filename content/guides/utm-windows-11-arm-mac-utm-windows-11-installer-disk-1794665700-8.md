---
title: "UTM Windows 11 Installer Disk: Break the Boot Loop Before Setup Restarts Again"
description: "Windows 11 ARM setup keeps restarting at the same screen in UTM? Check the installer disk, boot order, and virtual disk state to break the loop and finish installation."
seo_title: "UTM Windows 11 Installer Disk Boot Loop: Stop Setup Restarting"
seo_description: "Windows 11 ARM setup keeps restarting at the same screen in UTM? Check the installer disk, boot order, and virtual disk state to break the loop and finish installation."
keywords:
  - "utm windows 11 installer disk"
date: 2026-11-21T16:32:48+08:00
publishDate: 2026-11-21T16:32:48+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are installing Windows 11 ARM in UTM on your Apple Silicon Mac, and setup restarts at the same screen instead of continuing—so you are stuck in a boot loop before you can diagnose it properly.

## Confirm the installer disk is still attached

Open UTM and select your Windows 11 VM, then click Edit. Under Drives, verify the installer ISO is listed and its checkbox is enabled. If it is missing or unchecked, re-add it and save. Next, open the VM settings and check Boot Order. The installer disk should appear before the virtual hard disk. If the hard disk is first, setup will keep returning to the same screen.

## Check the virtual disk state

In the same Drives panel, confirm the main virtual disk is present and not marked read-only. A missing or read-only disk can make setup restart instead of writing files. If you recently changed the **utm windows 11 installer disk** configuration, revert that change and save before booting again.

## Verification test

Start the VM and watch the first setup screen. Press a key when prompted to boot from the installer. If setup proceeds past the language screen and begins copying files, the loop is broken. If it restarts at the same point, note the exact screen and stop—do not repeat blindly.

## Rollback and recovery

If the loop persists, shut down the VM, remove the installer ISO, and re-add it from a freshly downloaded Windows 11 ARM image. Keep a backup of the VM bundle before further changes so you can restore the previous state.

If these checks do not resolve it,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with the exact screen where setup restarts.
