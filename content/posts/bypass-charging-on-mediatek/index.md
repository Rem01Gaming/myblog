---
title: "How To Enable Bypass Charging On Any MediaTek Devices"
description: ""
date: 2024-10-26T14:55:20+07:00
tags: ["Android","MediaTek","Linux","kernel","Bypass Charging"]
cover: '/posts/bypass-charging-on-mediatek/ogp.jpg'
author: Rem01Gaming
draft: false
---

![Source: The Daily Messenger](/posts/bypass-charging-on-mediatek/ogp.jpg)

Batteries in smartphones are engineered to endure a specific number of charge-discharge cycles. As you use your phone more frequently, it drains faster, requiring more frequent charging. This continuous cycle gradually deteriorates the battery's chemical composition, impairing performance and significantly reducing its capacity to hold a charge.

This issue becomes more pronounced in gaming smartphones, which often run hot during extended use. Bypass charging is one of several strategies employed by manufacturers to mitigate battery wear in smartphones and laptops.

## What is bypass charging?

Typically, your phone draws power from the battery while charging it through an charger. However, bypass charging, utilized in high-performance laptops and some gaming phones like the Asus ROG, allows the device to receive power directly from the charger instead of the battery. This mode effectively bypasses the battery, hence the name.

## Benefits of bypass charging

1. **Reduced Battery Wear:** Since the battery isn't constantly charging and discharging, its lifespan can be extended.
2. **Reduced Heat:** Intense tasks generate heat, and this combined with charging can strain the battery. Bypass charging helps avoid this.
3. **Improved Performance:** Bypassing the battery reduces the likelihood of thermal throttling, especially during heavy tasks like gaming or prolonged use.

## How to enable bypass charging on MediaTek devices
**Most MediaTek devices support bypass charging**, as MediaTek provides a procfs interface, `mtk_battery_cmd`, which allows control over current limits and the bypass charging feature. You can easily toggle the bypass charging feature on and off with simple commands.

> **Note**: Root access is required to execute these commands.

```shell
# Enable bypass charging
# Charging current will show 10mA on reading or lower if bypass charging working
echo "0 1" >/proc/mtk_battery_cmd/current_cmd

# Disable bypass charging
# Charging current will back to normal
echo "0 0" >/proc/mtk_battery_cmd/current_cmd
```

There are some other software like [Advanced Charging Controller](https://github.com/VR-25/acc) and [Origami Kernel Manager](https://github.com/Rem01Gaming/origami_kernel_manager) that can do bypass charging in MediaTek devices as well as other devices.

## There's some consideration if you want to try bypass charging

1. **You must use original charger or equivalent**
	> Typically, non-original charger gives lower amount off current that original charger gives, **lower current can result slight battery drain because system tries to compensate current deficit from charger.**
2. **Not all devices support bypass charging**
	> Bypass charging not only requires support on software, but also hardware. expect bypass charging to not work on some devices.

## References
https://github.com/VR-25/acc
https://github.com/Rem01Gaming/origami_kernel_manager
https://www.howtogeek.com/what-is-bypass-charging-and-why-you-want-it/
