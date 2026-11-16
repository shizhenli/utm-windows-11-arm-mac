---
title: "UTM Windows 11 Installer Disk Boot Loop: Break the Restart Cycle"
description: "Stuck in a Windows 11 installer boot loop on UTM? Learn how to diagnose the installer disk, verify boot order, and break the restart cycle safely."
seo_title: "UTM Windows 11 Installer Disk Boot Loop: Fix the Restart Cycle"
seo_description: "Stuck in a Windows 11 installer boot loop on UTM? Learn how to diagnose the installer disk, verify boot order, and break the restart cycle safely."
keywords:
  - "utm windows 11 installer disk"
date: 2026-11-16T11:09:54+08:00
publishDate: 2026-11-16T11:09:54+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're installing Windows 11 ARM on your Apple Silicon Mac with UTM, and the installer keeps restarting at the same screen instead of continuing. This usually points to the virtual machine booting from the wrong device or the installer disk not being recognized correctly.

## Check the Boot Order First

Open UTM and select your Windows 11 VM, then go to Settings > System. Under Boot Order, ensure the installer disk (the ISO or virtual drive) is listed first. If it's not, drag it to the top. Also confirm the drive is attached and not set to read-only. A read-only installer disk can cause setup to restart endlessly because it can't write temporary files.

## Verify the Installer Disk Attachment

In UTM, check that your **utm windows 11 installer disk** is properly attached to the VM. Go to Settings > Drives and confirm the ISO or VHDX is listed and marked as connected. If you see two installer entries, remove the duplicate. Then start the VM and watch the boot screen: if it briefly shows the UTM logo then returns to the same setup screen, the VM is likely booting from the installer again after the first restart instead of the virtual hard disk.

## Fix the Restart Loop

After the first phase of setup, Windows needs to boot from the virtual hard disk, not the installer. In UTM, shut down the VM, go to Settings > System, and change the boot order to put the virtual hard disk first. Save and restart. The installer should now continue from where it left off.

## Verification Test

Restart the VM and observe the boot sequence. If Windows setup proceeds past the initial screen without looping back, the fix worked. You should see the setup continue to the next stage.

## Rollback Note

If the loop persists, revert the boot order to its original state and reattach the installer disk. If you're still stuck,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) for a guided diagnosis.
