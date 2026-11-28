---
title: "UTM Snapshots Not Restoring: Recover a Sluggish or Unbootable Windows 11 ARM VM"
description: "Troubleshoot UTM snapshots not restoring when your Windows 11 ARM VM is slow or won't shut down. Step-by-step checks, verification, and rollback advice."
seo_title: "Fix UTM Snapshots Not Restoring on Windows 11 ARM"
seo_description: "Troubleshoot UTM snapshots not restoring when your Windows 11 ARM VM is slow or won't shut down. Step-by-step checks, verification, and rollback advice."
keywords:
  - "utm snapshots not restoring"
date: 2026-11-28T21:58:54+08:00
publishDate: 2026-11-28T21:58:54+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You were restoring a snapshot on your Windows 11 ARM VM in UTM, but now the VM is sluggish or won't shut down, and you're stuck before you can complete a controlled diagnosis.

## Check the VM state before restoring again

First, confirm the VM is fully stopped. In UTM, open the VM window and look at the status indicator. If it shows running or paused, click Stop, then Force Stop if needed. A restore attempted while the VM is still active often leaves it unbootable. Next, open the VM settings and verify the disk image path still exists and points to the correct .qcow2 file. If the path is missing or renamed, the restore will fail silently. Also check that you have at least 10 GB free on the Mac's disk; low space can cause a partial restore.

## Interpret the results

If the status never changes from running, the guest is hung and must be force-stopped before any snapshot action. If the disk path is wrong, reattach the correct image in settings. If free space is low, clear space and retry. When **utm snapshots not restoring** still occurs after these checks, the snapshot itself may be corrupt, so try an older snapshot from the same list.

## Verification test

After a successful restore, start the VM and wait for the Windows desktop. Open Task Manager and confirm CPU usage settles below 20 percent at idle. Then shut down normally from the Start menu; the VM should power off within two minutes.

## Rollback and recovery

If the VM remains unbootable, do not delete the disk. Duplicate the VM bundle first, then restore the most recent snapshot that booted. If none work,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) before reinstalling Windows.
