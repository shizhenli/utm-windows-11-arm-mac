---
title: "UTM Snapshot Restore Leaves Windows 11 ARM VM Slow or Unbootable"
description: "Troubleshoot UTM snapshots not restoring on Windows 11 ARM. Learn to check disk health, verify snapshot integrity, and recover a sluggish or unbootable VM."
seo_title: "UTM Snapshots Not Restoring: Fix a Slow or Unbootable Windows 11 ARM VM"
seo_description: "Troubleshoot UTM snapshots not restoring on Windows 11 ARM. Learn to check disk health, verify snapshot integrity, and recover a sluggish or unbootable VM."
keywords:
  - "utm snapshots not restoring"
date: 2026-11-21T16:35:53+08:00
publishDate: 2026-11-21T16:35:53+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You restored a snapshot in UTM, and now your Windows 11 ARM VM is either crawling or won't boot at all.

## Check the VM state before you touch anything

Open UTM and select the affected VM. Look at the status indicator. If it says Running but the guest is unresponsive, click Stop, then Force Stop. Wait ten seconds. If the VM refuses to stop, that points to a hung virtual disk rather than a Windows problem.

Next, open the VM settings and inspect the drive under Drives. Confirm the disk image path still exists in Finder. A missing or renamed .qcow2 file is a common reason **utm snapshots not restoring** correctly. If the path is broken, reattach the correct disk image.

## Verify snapshot integrity

In UTM, open the Snapshots panel. Select the snapshot you tried to restore and check its timestamp and size. A snapshot that is 0 KB or has an old timestamp did not save properly. Delete it and restore the previous snapshot instead. If no snapshot is valid, you will need to boot from the base disk and repair Windows.

## Run a verification test

Start the VM in safe mode by holding Shift during boot. If Windows reaches the recovery screen, the disk is intact and the snapshot was the problem. If it still hangs, the virtual disk itself is damaged.

## Rollback and recovery

Before retrying, duplicate the VM bundle in Finder as a backup. Then restore the oldest known-good snapshot. If the VM remains slow, create a new VM and attach the existing disk image to preserve your data.

If these steps do not resolve it,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) with your UTM version and snapshot details.
