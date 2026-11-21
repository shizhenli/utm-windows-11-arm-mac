---
title: "UTM Virtual Machine Slow or Won't Shut Down: A Controlled Diagnosis"
description: "Troubleshoot a sluggish UTM Windows 11 ARM VM that won't shut down or becomes unbootable after a snapshot restore. Step-by-step checks and recovery."
seo_title: "UTM Virtual Machine Slow: Diagnose and Fix Shutdown Issues"
seo_description: "Troubleshoot a sluggish UTM Windows 11 ARM VM that won't shut down or becomes unbootable after a snapshot restore. Step-by-step checks and recovery."
keywords:
  - "utm virtual machine slow"
date: 2026-11-21T16:35:53+08:00
publishDate: 2026-11-21T16:35:53+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're running Windows 11 ARM in UTM on your Apple Silicon Mac, and the VM has become painfully slow or refuses to shut down, leaving you stuck before you can diagnose the problem.

## First, check UTM's resource allocation

Open UTM and select your Windows 11 VM, then click Edit. Under System, confirm CPU cores are set to 4 or fewer and RAM is at least 4 GB but not more than half your Mac's total memory. If you see 8 cores or 8 GB assigned on an 8 GB Mac, reduce them. Click Save, then start the VM. If it boots and feels responsive, the issue was over-allocation.

## Verify disk and snapshot health

In UTM's sidebar, right-click the VM and choose Show in Finder. Look for the .utm package and check its size. If it's unexpectedly large (over 60 GB for a basic install), snapshots may be bloating it. Open UTM's snapshot manager (the camera icon) and delete older snapshots you don't need. If the VM won't shut down, force quit UTM, then reopen it and try a normal shutdown from Windows. A forced quit can corrupt snapshots, so avoid it unless necessary.

## Run a controlled shutdown test

Start the VM and open Task Manager in Windows. Watch CPU and disk usage for one minute. If disk stays at 100%, Windows is likely updating or indexing. Let it finish. Then attempt a shutdown via Start > Power > Shut down. If it hangs, note the last screen. This tells you whether a driver or service is blocking shutdown.

## Recovery if the VM is unbootable

If a snapshot restore left the VM unbootable, revert to the previous snapshot in UTM's snapshot manager. If none exist, create a new VM and attach the existing disk image as a second drive to recover files. For persistent **utm virtual machine slow** behavior after these checks,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult) before reinstalling Windows.
