---
title: "UTM Snapshots Not Restoring: Fix a Slow or Unbootable Windows 11 ARM VM"
description: "Troubleshoot UTM snapshots not restoring on Windows 11 ARM by checking disk space, snapshot integrity, and VM state, then verify with a test boot and recover safely."
seo_title: "UTM Snapshots Not Restoring: Fix Slow or Unbootable Windows 11 ARM VM"
seo_description: "Troubleshoot UTM snapshots not restoring on Windows 11 ARM by checking disk space, snapshot integrity, and VM state, then verify with a test boot and recover safely."
keywords:
  - "utm snapshots not restoring"
date: 2026-11-15T19:12:17+08:00
publishDate: 2026-11-15T19:12:17+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You restored a snapshot on your Windows 11 ARM VM in UTM, and now the VM is sluggish or won't shut down, leaving you stuck before you can diagnose it properly.

## Check Available Disk Space and Snapshot Integrity

First, confirm your Mac has enough free space. UTM snapshots can be large, and a nearly full disk causes slow I/O and failed restores. Open Finder > Go > Computer, select your drive, and check free space. You want at least 20 GB free. If it's lower, delete old snapshots or move files off the drive.

Next, in UTM, select your VM and open the Snapshots panel. Look for the snapshot you restored. If it shows a warning icon or a size of 0 bytes, it's corrupt. Delete that snapshot and try an older one. Also check that the VM is fully shut down, not suspended, before restoring; a suspended state can conflict with snapshot data.

## Verify the Restore

After restoring a valid snapshot, start the VM and watch the boot process. If Windows reaches the login screen within a few minutes and the VM responds to clicks without long pauses, the restore worked. Then test a controlled shutdown: Start > Power > Shut down. It should complete within 60 seconds. If it hangs, the snapshot may have captured a bad driver state.

## Rollback and Recovery

If the VM remains slow or unbootable, shut it down forcefully in UTM (stop button), then restore the previous snapshot. If none work, create a new VM and attach your existing virtual disk as a second drive to recover files. Keep a known-good snapshot before major changes.

If **utm snapshots not restoring** keeps happening,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with your UTM version and snapshot list.
