---
title: "UTM Windows 11 Installer Disk: Why Setup Can't See the Virtual Disk"
description: "Windows 11 setup can't see your UTM virtual disk? Check the drive interface, virtio drivers, and disk attachment order to restore the installer disk."
seo_title: "UTM Windows 11 Installer Disk Not Detected: Fix Disk Selection"
seo_description: "Windows 11 setup can't see your UTM virtual disk? Check the drive interface, virtio drivers, and disk attachment order to restore the installer disk."
keywords:
  - "utm windows 11 installer disk"
date: 2026-11-25T10:10:06+08:00
publishDate: 2026-11-25T10:10:06+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

You are running a Windows 11 ARM VM in UTM on an Apple Silicon Mac, and Windows Setup has stopped at the disk selection screen because no disk is listed.

## Check the drive interface first

Open the VM settings in UTM and select Drives. Confirm the main virtual disk is present and note its interface. If it is set to VirtIO, Windows Setup may lack the matching storage driver and will show an empty list. Switch the disk to NVMe or SATA, save, and boot the installer again. If the disk now appears, the interface was the cause.

## Confirm the disk is attached and ordered correctly

In the same Drives panel, verify the virtual disk is attached to the VM, not only created. Check that the installer ISO is listed before the target disk in boot order. A detached or misordered disk produces the same empty selection screen. Reattach the disk, keep the ISO first, and retry.

## Verification test

Boot the installer and reach the disk selection step. A working configuration lists the virtual disk with its size and shows it as unallocated or partitioned. If the list remains empty, the problem is the storage driver or attachment, not the ISO.

## Rollback note

If changing the interface does not help, revert the drive settings to their previous values before making further changes, so you can isolate which adjustment mattered. For a guided diagnosis of your **utm windows 11 installer disk** configuration,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).

Repeat the same check after a restart and confirm the result twice.
