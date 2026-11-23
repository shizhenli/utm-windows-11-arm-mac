---
title: "UTM Snapshots Not Restoring: When a Slow VM Won't Shut Down"
description: "Troubleshoot UTM snapshots not restoring on Windows 11 ARM when the VM is slow or won't shut down. Step-by-step checks, verification, and recovery."
seo_title: "UTM Snapshots Not Restoring: Fix a Slow VM That Won't Shut Down"
seo_description: "Troubleshoot UTM snapshots not restoring on Windows 11 ARM when the VM is slow or won't shut down. Step-by-step checks, verification, and recovery."
keywords:
  - "utm snapshots not restoring"
date: 2026-11-23T10:10:15+08:00
publishDate: 2026-11-23T10:10:15+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You tried to restore a snapshot, and now your Windows 11 ARM VM is either crawling or stuck refusing to shut down.

## Check the Snapshot State First

Open UTM and select your VM. Go to the Snapshots tab. Look at the timestamp and size of the snapshot you tried to restore. If the size is 0 bytes or the timestamp is missing, that snapshot is incomplete and cannot be restored. Delete it and use an earlier one.

Next, check the VM's current state. If it shows Running, click Stop, then Force Stop. Wait 30 seconds. If it still shows Running, quit UTM entirely from the menu bar, reopen it, and check again. A stale lock file can make **UTM snapshots not restoring** appear to hang.

## Inspect the Disk and Config

In Finder, right-click the VM bundle and choose Show Package Contents. Confirm the .qcow2 disk file exists and its size matches the snapshot's expected size. A truncated disk means the restore failed partway. Also open the config.plist and verify the drive order has not changed; a reordered disk will make Windows boot slowly or hang at shutdown.

## Verification Test

Boot the VM and let it reach the desktop. Open Task Manager and watch CPU usage for two minutes. If it settles below 20 percent idle, the restore is healthy. Then shut down from the Start menu. If it powers off within 60 seconds, the fix is confirmed.

## Rollback Note

If the VM remains unbootable, do not overwrite the bundle. Duplicate it first, then restore the previous snapshot in the copy. Keep the original for recovery.

If these steps do not resolve it,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
