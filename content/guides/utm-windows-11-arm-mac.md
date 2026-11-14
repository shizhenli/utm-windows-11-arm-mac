---
title: UTM Windows 11 ARM Installer Cannot Find the Virtual Disk
description: 'A UTM storage sequence for Windows 11 ARM: correct ISO, virtio disk, driver loading, boot order, and shared-folder verification.'
seo_title: 'UTM Windows 11 ARM No Disk Found: Virtio Fix'
seo_description: 'A UTM storage sequence for Windows 11 ARM: correct ISO, virtio disk, driver loading, boot order, and shared-folder verification.'
keywords:
- utm windows 11 arm no disk
- windows 11 arm utm install
- utm virtio disk missing
date: '2026-11-13'
draft: false
categories:
- Virtualization
category_slug: virtualization
---

**utm windows 11 arm no disk**. 

<p>Windows Setup cannot see a UTM disk when the VM is using a storage controller without the matching driver. Add the virtio disk and load its driver before repartitioning.</p>
<h2>Before you start</h2><ul>
<li>Apple silicon Mac with UTM</li>
<li>ARM64 Windows 11 ISO</li>
<li>virtio-win ISO</li>
<li>Enough free disk space for the VM</li>
</ul>
<h2>Step-by-step checks</h2>
<h3>Step 1: Verify the ISO architecture</h3>
<p>Check that the Windows ISO is ARM64 and the UTM VM is configured for ARM. An x64 ISO is the wrong starting point for a native ARM VM.</p>
<p>Check: The VM and ISO are both ARM64.</p>
<h3>Step 2: Add the virtio disk</h3>
<p>In UTM settings, add a virtio drive for Windows and attach the virtio-win ISO as a second optical drive. Keep the Windows ISO available for setup.</p>
<p>Check: The VM lists a virtio disk and both ISO drives.</p>
<h3>Step 3: Load the storage driver</h3>
<p>At the disk screen, choose Load driver, browse the virtio-win ISO, and select the matching Windows 11 ARM storage driver. Rescan after loading.</p>
<p>Check: Windows Setup lists the virtio disk as available.</p>
<h3>Step 4: Finish and fix boot order</h3>
<p>Install Windows, then remove or demote the Windows ISO so the virtio disk boots first. Restart and confirm Windows starts without the installer.</p>
<p>Check: The VM boots to the Windows desktop from the installed disk.</p>
<h3>Step 5: Test one app and shared folder</h3>
<p>Install one lightweight app, configure a UTM shared folder, and open a file from it in Windows. Confirm the path and permissions.</p>
<p>Check: The app launches and the shared file opens.</p>
<h2>Verify the result</h2>
<p>Windows boots from the virtual disk, one app runs, and a file in the Mac shared folder opens in Windows after a VM restart.</p>
<h2>Rollback</h2>
<p>Keep the previous VM configuration or a snapshot before changing storage. Remove only the test VM if the install cannot be recovered.</p>
<p><a href="/#consult">Ask for help with this exact symptom</a> · All troubleshooting guides</p>
