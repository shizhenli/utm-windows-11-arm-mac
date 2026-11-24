---
title: "UTM Windows 11 ARM Drivers Missing: Clear the x86 App Compatibility Error"
description: "Stuck at the arm app compatibility error in UTM? Learn how to check driver status, interpret results, and verify the fix for missing drivers on Windows 11 ARM."
seo_title: "Fix UTM Windows 11 ARM Drivers Missing: x86 App Compatibility Error"
seo_description: "Stuck at the arm app compatibility error in UTM? Learn how to check driver status, interpret results, and verify the fix for missing drivers on Windows 11 ARM."
keywords:
  - "utm windows arm drivers missing"
date: 2026-11-24T11:10:21+08:00
publishDate: 2026-11-24T11:10:21+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are running Windows 11 ARM in UTM on your Apple Silicon Mac, and an x86 app or driver refuses to install with an arm app compatibility error. This usually means Windows cannot find or load a required driver, often because the driver package is x86-only or not present in the ARM build. Here is a controlled way to diagnose and fix it.

## Check driver presence and architecture

Open Device Manager (right-click Start > Device Manager). Look for devices with a yellow warning icon. Right-click the problem device and choose Properties > Driver tab. Note the driver provider, date, and version. Then open a Command Prompt as administrator and run:

`pnputil /enum-drivers`

Scan the output for the driver's .inf name. If it is missing, the driver was never staged. If it appears but the device still fails, the driver may be x86-only. Check the driver's folder for a .sys file; right-click it > Properties > Details and look at the "Machine Type" or "Target Machine" field. If it says x86, it will not load on ARM.

## Interpret the result

If the driver is absent, install the ARM64 version from the vendor. If only x86 is available, the app or driver cannot work natively; you need an ARM64 equivalent or a different approach. This is the core of **utm windows arm drivers missing** scenarios: the driver simply is not staged for ARM.

## Verification test

After installing an ARM64 driver, return to Device Manager, right-click the device, and select Update driver > Browse my computer. Point to the driver folder. If the warning icon disappears and the device shows as working, the fix is confirmed. Then retry the x86 app installation.

## Rollback and recovery

If the new driver causes instability, open Device Manager, right-click the device, choose Properties > Driver > Roll Back Driver. If that is unavailable, use System Restore to return to a prior point. Keep a snapshot of your UTM VM before major driver changes so you can revert quickly. For further diagnosis,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
