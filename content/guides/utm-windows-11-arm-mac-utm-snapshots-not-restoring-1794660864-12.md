---
title: "UTM Snapshots Not Restoring: Fix a Sluggish or Unbootable Windows 11 ARM VM"
description: "Troubleshoot UTM snapshots not restoring on Windows 11 ARM when the VM becomes slow or won't shut down. Step-by-step checks, verification, and recovery."
seo_title: "UTM Snapshots Not Restoring: Fix a Sluggish or Unbootable Windows 11 ARM VM"
seo_description: "Troubleshoot UTM snapshots not restoring on Windows 11 ARM when the VM becomes slow or won't shut down. Step-by-step checks, verification, and recovery."
keywords:
  - "utm snapshots not restoring"
date: 2026-11-17T11:09:53+08:00
publishDate: 2026-11-17T11:09:53+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You tried to restore a snapshot, but now your Windows 11 ARM VM is sluggish or refuses to shut down, leaving you stuck before you can diagnose anything.

## Check the Snapshot State Before Anything Else

Open UTM and select your VM. In the sidebar, click Snapshots. Look at the timestamp and status of the snapshot you restored. If it shows an error or is marked incomplete, the restore did not finish cleanly. Delete that snapshot and try an older one. If the older snapshot restores and the VM boots normally, the problem is the newer snapshot file, not your VM configuration.

## Verify VM Settings and Disk Health

With the VM shut down, open Settings > Drives. Confirm the main disk is still attached and its size matches what you expect. A missing or resized disk after a restore often explains why **utm snapshots not restoring** leaves the VM unbootable. Next, check Settings > System and confirm the memory and CPU values are reasonable for your Mac. If they were changed by the snapshot, reset them to your previous values.

## Test a Controlled Shutdown

Start the VM and wait for Windows to reach the desktop. Open Task Manager and watch CPU and disk usage for one minute. If usage stays near 100% with no obvious process, the restored state may include a stuck service. Try a graceful shutdown from the Start menu. If it hangs, force quit UTM, then start the VM again and repeat the shutdown test. A clean shutdown confirms the restore is usable.

## Rollback and Recovery

If the VM still will not shut down or remains slow, revert to the snapshot you took before the problematic restore. Keep that known-good snapshot untouched. If no good snapshot exists, create a new VM with the same Windows 11 ARM installer and attach your existing disk image to recover files.

If these steps do not resolve it,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with your UTM version and snapshot details.
