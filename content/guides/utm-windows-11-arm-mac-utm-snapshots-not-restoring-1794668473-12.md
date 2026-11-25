---
title: "UTM Snapshots Not Restoring: Diagnose the Slow or Unresponsive Windows 11 ARM VM"
description: "Troubleshoot a Windows 11 ARM VM in UTM that becomes slow or won't shut down after a snapshot restore. Step-by-step checks, verification, and recovery."
seo_title: "Fix UTM Snapshots Not Restoring on Windows 11 ARM: Slow or Unbootable VM"
seo_description: "Troubleshoot a Windows 11 ARM VM in UTM that becomes slow or won't shut down after a snapshot restore. Step-by-step checks, verification, and recovery."
keywords:
  - "utm snapshots not restoring"
date: 2026-11-25T08:10:11+08:00
publishDate: 2026-11-25T08:10:11+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You restored a snapshot in UTM, and now your Windows 11 ARM VM is sluggish or refuses to shut down, leaving you stuck before you can diagnose it properly.

## First, confirm the VM state without forcing anything

Open UTM and select the affected VM. Check the VM status indicator: if it shows Running but the Windows desktop is frozen, the guest OS may be hung rather than the snapshot itself being corrupt. Do not repeatedly click Restore Snapshot; each attempt can overwrite the current state.

Next, inspect the snapshot list. A healthy snapshot shows a timestamp and a size. If the snapshot you need is missing or shows zero bytes, the restore cannot complete and you should stop here and recover from a backup.

## Check disk and memory pressure

In UTM's VM settings, verify the allocated RAM and disk size. Windows 11 ARM needs at least 4 GB RAM and 64 GB disk. If the snapshot was taken when the VM had less, restoring it can leave Windows swapping heavily, which looks like a slow or unresponsive VM. Increase RAM only after the VM is shut down cleanly.

## Perform a controlled shutdown test

From UTM's menu, choose Send Shutdown Signal rather than Force Stop. Wait up to two minutes. If Windows shuts down, the snapshot restored correctly and the slowness was resource-related. If it does not, force stop the VM, then start it again and watch for the Windows boot spinner. A boot loop confirms the snapshot is damaged.

## Rollback and recovery

If the VM remains unbootable, delete the failed snapshot and restore the previous one. Keep a copy of the VM bundle before any further restore. For persistent cases where **utm snapshots not restoring** blocks your work,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) before reinstalling Windows, since the virtual disk may still be recoverable.
