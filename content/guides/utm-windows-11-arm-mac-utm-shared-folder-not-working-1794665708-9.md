---
title: "UTM Shared Folder Not Working: Why Windows 11 ARM Sees No Drive"
description: "Troubleshoot a UTM shared folder that is configured but not visible in Windows 11 ARM. Check the share path, mount status, and network discovery, then verify with a simple test."
seo_title: "UTM Shared Folder Not Working: Fix Missing Drive in Windows 11 ARM"
seo_description: "Troubleshoot a UTM shared folder that is configured but not visible in Windows 11 ARM. Check the share path, mount status, and network discovery, then verify with a simple test."
keywords:
  - "utm shared folder not working"
date: 2026-11-21T16:32:48+08:00
publishDate: 2026-11-21T16:32:48+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You set up a shared folder in UTM for your Windows 11 ARM VM, but when you open File Explorer there is no drive or network path. This is a common **utm shared folder not working** situation, and it usually means the guest never received the share, not that the folder is gone.

## Check the share in UTM first

Shut down the VM, open its settings, and go to Sharing. Confirm the folder is listed and that the share name is short and has no spaces. Start the VM and watch the UTM window during boot. If you see a VirtFS or 9p mount message, the host side is working. If you see nothing, the share is not being passed to Windows.

## Confirm what Windows sees

Open Device Manager and look under System devices for a VirtIO or 9p device. If it is missing or has a warning, the guest tools are not loaded. Next, open PowerShell as administrator and run `net use`. An empty list means Windows has no mapped share. A mapped drive with a red X means the path exists but is disconnected.

## Verification test

In UTM, enable the share again and set it to mount at boot. Restart Windows. Open File Explorer and type `\\?\unc\` is not valid, so instead check This PC for a new drive letter or open Network and look for the host name. If the share appears, create a test file on the Mac side and confirm it shows in Windows within a few seconds.

## Rollback and recovery

If the share still does not appear, remove it in UTM settings, restart the VM, and add it back with a single simple folder such as your Downloads directory. If Windows stops booting after a share change, boot into safe mode and remove any mapped drive entries with `net use /delete`. For a guided review of your VM configuration,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
