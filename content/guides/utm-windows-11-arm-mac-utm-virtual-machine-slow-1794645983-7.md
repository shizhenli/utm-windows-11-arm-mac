---
title: "UTM Windows 11 ARM Slow or Won't Shut Down: A Controlled Diagnosis"
description: "Troubleshoot a slow or non-shutting-down Windows 11 ARM VM in UTM. Follow step-by-step checks to diagnose and restore expected performance."
seo_title: "UTM Virtual Machine Slow: Fix Windows 11 ARM Shutdown and Snapshot Issues"
seo_description: "Troubleshoot a slow or non-shutting-down Windows 11 ARM VM in UTM. Follow step-by-step checks to diagnose and restore expected performance."
keywords:
  - "utm virtual machine slow"
date: 2026-11-15T19:12:17+08:00
publishDate: 2026-11-15T19:12:17+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're running Windows 11 ARM in UTM on your Apple Silicon Mac, and the VM has become sluggish or won't shut down after a snapshot restore, leaving you stuck before a controlled diagnosis.

## First, Check UTM and macOS Resource Allocation

Open UTM and select your Windows 11 ARM VM. Click Edit, then go to the System tab. Verify CPU cores are set to 4 or fewer (more can cause contention on Apple Silicon). Check Memory: 4GB is minimum, 8GB recommended. If overallocated, reduce and save. Next, open macOS Activity Monitor and sort by CPU. If UTM is using over 80% consistently, the VM is likely thrashing. Quit other heavy apps and retry.

## Inspect Snapshot State and Disk Health

If the VM won't shut down, force quit UTM from the Apple menu, then reopen it. Go to the VM's Snapshots tab. Delete any incomplete or old snapshots. A corrupted snapshot often causes boot hangs. Then check the VM's disk image in Finder: right-click the .utm file, Show Package Contents, and verify the .qcow2 file size is stable (not growing wildly). If it's abnormally large, the disk may be fragmented.

## Verification Test

Start the VM. Open Task Manager in Windows and watch CPU and disk usage for two minutes. If idle usage stays under 20% and shutdown completes within 30 seconds, the issue is resolved. If not, proceed to recovery.

## Rollback and Recovery

If the VM remains unbootable, restore from a known-good snapshot or reinstall Windows 11 ARM using a fresh UTM VM. Before deleting anything, export your data via shared folders. For persistent **utm virtual machine slow** behavior, consider reinstalling UTM and recreating the VM with default settings. If you need guided assistance,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
