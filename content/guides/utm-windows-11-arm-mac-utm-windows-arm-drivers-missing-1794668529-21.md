---
title: "UTM Windows 11 ARM: Resolve the x86 App Compatibility Error When Drivers Are Missing"
description: "Stuck at the arm app compatibility error in your UTM Windows 11 ARM VM? Learn how to diagnose missing drivers and restore x86 app installation."
seo_title: "UTM Windows 11 ARM Drivers Missing: Fix x86 App Compatibility Error"
seo_description: "Stuck at the arm app compatibility error in your UTM Windows 11 ARM VM? Learn how to diagnose missing drivers and restore x86 app installation."
keywords:
  - "utm windows arm drivers missing"
date: 2026-11-26T10:08:28+08:00
publishDate: 2026-11-26T10:08:28+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You're running Windows 11 ARM in UTM on your Apple Silicon Mac, and an x86 app or driver refuses to install, leaving you at the arm app compatibility error before you can complete a controlled diagnosis.

## Check the Driver Signature and Architecture

First, confirm whether the driver is x86 or ARM64. Right-click the installer, choose Properties, and check the Digital Signatures tab. If the signature is missing or invalid, Windows 11 ARM will block it. Next, open Device Manager and look for devices with a yellow warning icon. If the device is listed under Other devices, the driver is likely missing or incompatible. Note the hardware ID (right-click > Properties > Details > Hardware Ids) and search for an ARM64 equivalent. If none exists, the driver cannot be installed natively.

## Interpret the Error

If the installer throws "This app can't run on your PC" or "Driver is not compatible," it means the driver is x86 and Windows 11 ARM lacks the translation layer for kernel-mode drivers. This is expected behavior, not a bug. The **utm windows arm drivers missing** issue often stems from this architecture mismatch. If the error mentions a missing .sys file, the driver package is incomplete.

## Verification Test

After obtaining an ARM64 driver, disable driver signature enforcement temporarily: hold Shift while restarting, choose Troubleshoot > Advanced options > Startup Settings > Restart, then press 7. Install the driver. If it succeeds, the problem was signature enforcement. Re-enable enforcement afterward by restarting normally.

## Rollback and Recovery

If the new driver causes instability, boot into Safe Mode (same Startup Settings, press 4) and use Device Manager to roll back the driver or uninstall it. System Restore can also revert changes. Always create a restore point before installing unsigned drivers.

If you need personalized guidance,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
