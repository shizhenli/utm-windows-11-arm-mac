---
title: UTM Windows 11 ARM Help
seo_title: UTM Windows 11 ARM Help | Installer Cannot Find Disk
seo_description: Remote help with UTM Windows 11 ARM installs when the installer cannot find the virtual disk.
keywords:
- utm windows 11 arm no disk
- windows 11 arm utm install
- utm virtio disk missing
hero_kicker: UTM ON APPLE SILICON
hero_h1: Windows 11 ARM can't find the virtual disk?
hero_lead: Attach the Windows 11 ARM ISO and virtio drivers correctly, then verify one app and a shared folder in the VM.
hero_proof:
- One Mac, one VM, one Windows ISO
- Virtio storage and driver checks
- One app and shared folder verified
hero_alt: Laptop showing a Windows 11 virtual machine desktop
hero_title: Windows 11 ARM virtual machine on a Mac
body_alt: UTM virtual machine settings showing a Windows ISO and virtio disk
body_title: UTM Windows 11 ARM disk and driver check
body_caption: The installer must see the virtio disk before Windows setup can continue.
failures_kicker: THE THREE FAILURES WE SEE
failures_heading: What is going wrong?
test_kicker: HOW WE TEST
test_heading: Find the failing layer, then prove the fix.
scope_kicker: SERVICE SCOPE
scope_heading: What is included
scope_note: The session covers one agreed device and one verified path. Anything outside the written scope is quoted separately before work starts.
faq_kicker: FAQ
faq_heading: Before you book
consult_heading: Tell us what is happening.
consult_lead: Send the device, software, exact symptom, and what you have already tried. We will confirm scope and a fixed quote before booking.
form_placeholder: Device, software version, exact symptom, and what you have tried.
first_guide_url: /guides/utm-windows-11-arm-mac/
symptoms:
- title: No drives are listed
  text: Windows Setup opens, but the disk selection screen is empty or shows no available partition.
- title: The ISO boots but setup stops
  text: The installer starts, then fails when it looks for a storage driver or restarts into the ISO again.
- title: Shared folder is invisible
  text: Windows works, but the Mac shared folder does not appear in File Explorer.
checks:
- title: Confirm the VM architecture
  text: Use the ARM64 Windows ISO on Apple silicon, not an x64 ISO. Check the UTM VM type and the ISO's architecture.
- title: Attach a virtio disk and driver
  text: Add a virtio disk and mount the virtio-win ISO as a second drive. Load the storage driver from the installer's “Load driver” option.
- title: Fix boot order after install
  text: Remove or reorder the Windows ISO so the installed disk boots first; otherwise setup can loop back into the installer.
- title: Test one app and share
  text: Install one lightweight app and open the Mac shared folder from Windows before calling the VM complete.
included:
- One Apple silicon Mac and one UTM VM
- ARM ISO and virtio storage review
- Boot-order and driver assistance
- One app and shared-folder verification
excluded:
- Windows license activation
- Running x86-only software
- macOS repair or storage replacement
- Guaranteeing every peripheral
faqs:
- q: Can I use a normal Windows 11 ISO?
  a: The VM needs an ARM64 build on Apple silicon. An x64 ISO may boot into emulation but will not behave like the native ARM VM.
- q: Why does setup still show no disk?
  a: The virtio storage driver may not be loaded, or the disk is attached to a controller Windows Setup cannot see. Load the matching driver and recheck.
- q: Is this legal on my Mac?
  a: You are responsible for the Windows license and Apple's virtualization terms. The session configures the VM but does not supply licenses.
---
