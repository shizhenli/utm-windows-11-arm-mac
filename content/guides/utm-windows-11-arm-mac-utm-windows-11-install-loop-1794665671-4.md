---
title: "UTM Windows 11 Install Loop: Break the Restart Cycle"
description: "Stuck in a UTM Windows 11 install loop? Learn how to diagnose and break the restart cycle so Windows Setup continues normally."
seo_title: "Fix UTM Windows 11 Install Loop: Stop the Restart Cycle"
seo_description: "Stuck in a UTM Windows 11 install loop? Learn how to diagnose and break the restart cycle so Windows Setup continues normally."
keywords:
  - "utm windows 11 install loop"
date: 2026-11-21T16:29:42+08:00
publishDate: 2026-11-21T16:29:42+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are installing Windows 11 ARM in UTM on your Apple Silicon Mac, and Windows Setup keeps restarting at the same screen instead of continuing the installation.

## Check the Boot Order and ISO Attachment

First, shut down the VM completely. In UTM, open the VM settings and confirm the boot order. The installer ISO should be listed first, but after the first restart, the virtual disk must take priority. If the ISO remains first, Setup will loop back to the installer. Remove the ISO from the boot order after the initial file-copy phase, or set the virtual disk as the primary boot device. Also verify the ISO is attached as a CD/DVD drive, not as a removable USB, which can confuse the boot sequence.

## Verify the Virtual Disk Is Recognized

Start the VM and watch the UEFI boot screen. If the virtual disk does not appear, the **utm windows 11 install loop** will persist because Setup has nowhere to write the next stage. Check that the disk is formatted as GPT and has an EFI system partition. You can do this from the installer's command prompt using diskpart: list disk, select disk 0, list partition. A missing EFI partition means you must recreate the disk layout before Setup can proceed.

## Run a Verification Test

After adjusting the boot order, restart the VM. Setup should now load from the virtual disk and display the regional settings or account creation screen. If it returns to the initial language screen, the boot order is still wrong or the disk is not bootable.

## Rollback and Recovery

If the loop continues, revert to a snapshot taken before the install, or detach the ISO and boot from the virtual disk alone. For persistent issues,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with your UTM configuration details.
