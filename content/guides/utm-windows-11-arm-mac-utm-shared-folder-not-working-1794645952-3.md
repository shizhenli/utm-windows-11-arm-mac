---
title: "UTM Shared Folder Not Working: Fix the Missing Drive in Windows 11 ARM"
description: "UTM shared folder not working in Windows 11 ARM? Follow these steps to diagnose why no drive appears and restore access without reinstalling."
seo_title: "UTM Shared Folder Not Working on Windows 11 ARM? Fix It Now"
seo_description: "UTM shared folder not working in Windows 11 ARM? Follow these steps to diagnose why no drive appears and restore access without reinstalling."
keywords:
  - "utm shared folder not working"
date: 2026-11-14T19:53:00+08:00
publishDate: 2026-11-14T19:53:00+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You configured a shared folder in UTM, but Windows 11 ARM shows no drive or network path—so you are stuck before you can even begin troubleshooting. Let’s walk through this together.

## Check the UTM Share Configuration

First, confirm the share is actually enabled. In UTM, open your Windows 11 ARM VM settings, go to Sharing, and verify the folder is listed and enabled. If it is missing, add it again. Next, check that the share mode is set to VirtioFS or SPICE (depending on your UTM version). A common cause of **utm shared folder not working** is selecting a mode that Windows 11 ARM does not support without extra drivers.

## Verify Windows Sees the Share

Start the VM and open File Explorer. Look under This PC for a drive letter or under Network for a host path. If nothing appears, open Device Manager and check for unknown devices under System devices—missing VirtioFS or SPICE drivers will prevent the share from mounting. Also, run `net use` in Command Prompt; an empty list confirms Windows has no mapped share.

## Verification Test

Create a small text file on your Mac inside the shared folder. In Windows, open PowerShell and run `dir \\?\VirtioFS\` or check the expected drive letter. If the file appears, the share works. If not, the driver or service is not active.

## Rollback and Recovery

If changes make things worse, revert the UTM share settings to their previous state and restart the VM. You can also remove and re-add the share without affecting your Windows installation.

Still stuck?

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) and we’ll diagnose your exact setup.
