---
title: "UTM Windows 11 ARM Drivers Missing: Fix the x86 App Compatibility Error"
description: "Troubleshoot the arm app compatibility error in a Windows 11 ARM VM on UTM when an x86 app or driver refuses to install. Step-by-step checks and a verification test."
seo_title: "UTM Windows 11 ARM Drivers Missing: Fix x86 App Compatibility Error"
seo_description: "Troubleshoot the arm app compatibility error in a Windows 11 ARM VM on UTM when an x86 app or driver refuses to install. Step-by-step checks and a verification test."
keywords:
  - "utm windows arm drivers missing"
date: 2026-11-15T19:12:17+08:00
publishDate: 2026-11-15T19:12:17+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are running Windows 11 ARM in UTM on an Apple Silicon Mac, and an x86 app or driver installer stops with an arm app compatibility error before you can diagnose it. This usually means the installer is trying to load an x86 driver that Windows on ARM cannot translate, or the VM is missing the ARM64 driver package it expects.

## Check the Installer Architecture

First, confirm what you are installing. Right-click the installer, choose Properties, and look at the Details tab. If the file is marked x86 or x64 and it includes a driver component, Windows 11 ARM will often refuse it. A pure user-mode x86 app should run under emulation; a driver cannot. If the installer is x86-only and driver-based, stop here—it will not work natively.

## Verify the Driver Store

Open Device Manager and look for devices with a yellow warning icon. Expand System devices and check for unknown entries. Then open an elevated Command Prompt and run `pnputil /enum-drivers`. Look for ARM64 driver packages. If you see only x86 or x64 packages, the **utm windows arm drivers missing** condition is confirmed: the VM lacks the ARM64 driver the installer needs.

## Verification Test

Install a known ARM64 app from the Microsoft Store, such as an ARM-native utility, and launch it. If it opens normally, Windows on ARM is healthy and the problem is specific to the x86 driver installer. If it also fails, the VM image may be incomplete.

## Rollback and Recovery

Before changing anything, create a UTM snapshot. If a driver installation leaves the VM unstable, restore that snapshot. Do not force-install an x86 driver; it can break boot. If the ARM64 driver package is genuinely absent, you may need to rebuild the VM from a fresh Windows 11 ARM ISO. For guided diagnosis,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
