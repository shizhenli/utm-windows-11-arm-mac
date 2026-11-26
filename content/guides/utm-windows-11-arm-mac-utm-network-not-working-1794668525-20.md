---
title: "UTM Network Not Working: Diagnose the Missing Adapter in Windows 11 ARM"
description: "Fix UTM network not working in Windows 11 ARM VM on Apple Silicon. Step-by-step checks for missing adapter, host reachability, and recovery."
seo_title: "UTM Network Not Working: Fix Windows 11 ARM VM No Network Adapter"
seo_description: "Fix UTM network not working in Windows 11 ARM VM on Apple Silicon. Step-by-step checks for missing adapter, host reachability, and recovery."
keywords:
  - "utm network not working"
date: 2026-11-26T09:08:26+08:00
publishDate: 2026-11-26T09:08:26+08:00
draft: false
categories:
  - "Virtualization"
category_slug: "virtualization"
---

## Troubleshooting

You are running a Windows 11 ARM VM in UTM on your Apple Silicon Mac, and at the network step, Windows shows no adapter or cannot reach the host. Start by checking the VM's network configuration in UTM. Open the VM settings, go to Network, and confirm the adapter is set to Shared Network or Bridged. If it is set to None, change it to Shared Network and save. Next, inside Windows, open Device Manager and expand Network adapters. If you see a yellow warning or no adapter at all, the driver may not be loading. Right-click the adapter and select Update driver, then choose Search automatically. If that fails, download the latest UTM network driver from the UTM website and install it manually. After the driver is installed, open Command Prompt as administrator and run ipconfig /all. Look for an IPv4 address. If it shows 169.254.x.x, the VM is not getting a DHCP lease. In UTM settings, switch from Shared Network to Bridged, select your Mac's active interface, and restart the VM. Then run ping 8.8.8.8. If that succeeds, run ping google.com. If the first works but the second fails, DNS is the issue; set DNS to 8.8.8.8 manually. If neither works, the **utm network not working** issue is likely a host firewall blocking the virtual interface. Temporarily disable the macOS firewall and test again. To verify, open Edge in the VM and load a simple page. If it loads, the network is restored. If you changed settings and need to roll back, revert the network mode to Shared Network and restart. For further diagnosis,

![UTM virtual machine settings showing a Windows ISO and virtio disk](/images/service-detail-960.webp "UTM Windows 11 ARM disk and driver check")

[Ask for help](/#consult).
