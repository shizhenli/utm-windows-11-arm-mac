---
title: "UTM Windows 11 Install Loop: Stop the Restart Cycle Before Diagnosis"
description: "Stuck in a UTM Windows 11 install loop? Learn how to break the restart cycle, verify the fix, and recover your VM without reinstalling from scratch."
seo_title: "Fix UTM Windows 11 Install Loop: Stop the Restart Cycle"
seo_description: "Stuck in a UTM Windows 11 install loop? Learn how to break the restart cycle, verify the fix, and recover your VM without reinstalling from scratch."
keywords:
  - "utm windows 11 install loop"
date: 2026-11-17T12:09:53+08:00
publishDate: 2026-11-17T12:09:53+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're installing Windows 11 ARM on your Apple Silicon Mac with UTM, and the installer keeps restarting at the same screen instead of continuing.

## Check the Boot Order First

Open your VM's settings in UTM and go to the Drives tab. The installer ISO should be listed, but after the first restart, the virtual hard disk must be first in the boot order. If the ISO remains first, the VM boots back into setup endlessly. Move the hard disk to the top, save, and start the VM again. If setup now proceeds past the initial screen, the loop was caused by boot order.

## Disconnect the Installer ISO

If the loop persists, shut down the VM. In the Drives tab, temporarily remove the installer ISO from the drive list, keeping only the virtual disk. Start the VM. If Windows continues to the desktop or the next setup phase, the ISO was being re-read. Reattach the ISO only when you need recovery tools.

## Verification Test

After making either change, start the VM and watch the first restart. The expected result is that setup moves to the next configuration screen or the Windows desktop, not the same installer page. If it still loops, note the exact screen title and any error code before changing anything else.

## Rollback and Recovery

If the VM becomes unbootable after these changes, reattach the ISO and boot from it to run startup repair. Keep a snapshot before editing drive settings so you can revert quickly. For a guided diagnosis of your **utm windows 11 install loop**,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
