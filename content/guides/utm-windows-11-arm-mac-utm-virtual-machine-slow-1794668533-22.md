---
title: "UTM Virtual Machine Slow or Won't Shut Down: A Controlled Fix"
description: "Troubleshoot a slow or unresponsive Windows 11 ARM VM in UTM after a snapshot restore. Follow these checks to diagnose and recover without reinstalling."
seo_title: "UTM Virtual Machine Slow: Fix Shutdown and Snapshot Issues"
seo_description: "Troubleshoot a slow or unresponsive Windows 11 ARM VM in UTM after a snapshot restore. Follow these checks to diagnose and recover without reinstalling."
keywords:
  - "utm virtual machine slow"
date: 2026-11-28T21:58:54+08:00
publishDate: 2026-11-28T21:58:54+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You restored a snapshot and now your Windows 11 ARM VM is sluggish or refuses to shut down, leaving you stuck before a proper diagnosis.

## First, check the VM state and logs
Open UTM and select the VM. Look at the status indicator: if it shows "Running" but Windows is unresponsive, the guest OS may be hung. Click the VM's settings gear, then go to the Log tab. A repeating "disk I/O error" or "snapshot chain broken" message means the restore left inconsistent virtual disk state. If the log is clean, the issue is likely resource contention.

## Verify resource allocation
In UTM settings, confirm CPU cores are set to 4 or fewer and RAM is 4–8 GB. Over-allocating causes the host to swap, making the VM slow. Also check that the disk image is on a fast local SSD, not an external drive. After adjusting, force shutdown the VM by holding Option and clicking the power button in UTM, then start it normally.

## Run a verification test
Once Windows boots, open Task Manager and watch CPU and disk usage for two minutes. If disk usage stays at 100% with no process listed, the virtual disk needs repair. Shut down Windows from the Start menu. If it hangs, the snapshot is corrupt.

## Rollback and recovery
If shutdown still fails, delete the problematic snapshot in UTM's snapshot manager and revert to the previous one. If no snapshot works, create a new VM and attach the existing disk image as a second drive to recover files. This **utm virtual machine slow** condition often clears after reverting to a clean snapshot.

For guided recovery,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
