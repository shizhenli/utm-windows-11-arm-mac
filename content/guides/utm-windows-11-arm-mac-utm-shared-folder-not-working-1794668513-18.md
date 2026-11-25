---
title: "UTM Shared Folder Not Working: Why No Drive Appears in Windows 11 ARM"
description: "UTM share configured but no drive or network path appears in Windows 11 ARM? Follow these checks to diagnose and restore the shared folder."
seo_title: "UTM Shared Folder Not Working: Fix Missing Drive in Windows 11 ARM"
seo_description: "UTM share configured but no drive or network path appears in Windows 11 ARM? Follow these checks to diagnose and restore the shared folder."
keywords:
  - "utm shared folder not working"
date: 2026-11-25T12:10:11+08:00
publishDate: 2026-11-25T12:10:11+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You set up a shared folder in UTM for your Windows 11 ARM VM, but when you open File Explorer, there's no drive or network path to be found.

## Check the UTM Share Configuration

First, shut down the VM completely (not just suspend). In UTM, select the VM and open Settings > Sharing. Confirm the shared folder is listed and the path points to an existing folder on your Mac. If the path is wrong or the folder was moved, remove and re-add it. Also verify the share name has no spaces or special characters.

## Verify the SPICE WebDAV Service in Windows

Windows 11 ARM accesses UTM shares through a WebDAV service. Open Services (services.msc) and look for "SPICE WebDAV Service." If it's stopped, start it and set Startup type to Automatic. If it's missing, the guest tools aren't installed—reinstall UTM Guest Tools from the mounted ISO.

## Map the Share Manually

Open File Explorer and try \\localhost\DavWWWRoot. If that path opens but no drive letter appears, map it: right-click This PC > Map network drive, choose a letter, and enter http://localhost:9843/ as the folder. This confirms whether the **utm shared folder not working** issue is a mapping problem rather than a service failure.

## Verification Test

Create a test file on your Mac inside the shared folder. Then in Windows, open the mapped drive or \\localhost\DavWWWRoot and confirm the file appears. If it does, the share is restored.

## Rollback Note

If mapping fails or causes errors, disconnect the mapped drive in File Explorer and revert the SPICE WebDAV service to its previous startup setting. Then re-check the UTM sharing settings before trying again.

If these steps don't restore the share,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with your UTM version and Windows build.
