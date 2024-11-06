---
title: "How to Enable Bypass Charging on MediaTek Devices"
description: "Learn how to enable bypass charging on MediaTek devices to extend battery lifespan, reduce heat, and boost performance, especially during gaming."
date: 2024-10-26T14:55:20+07:00
tags: ["Android", "MediaTek", "Linux", "Kernel", "Bypass Charging", "Battery", "Smartphone"]
cover: '/posts/bypass-charging-on-mediatek/ogp.jpg'
author: Rem01Gaming
draft: false
---

![Bypass Charging for MediaTek Devices](/posts/bypass-charging-on-mediatek/ogp.jpg)

Smartphone batteries endure specific charge-discharge cycles. With increased usage, these cycles become more frequent, gradually wearing down the battery's chemical integrity and impacting its performance. This is especially concerning for high-performance and gaming smartphones, where overheating can accelerate this degradation. **Bypass charging** is a solution designed to mitigate battery wear, extend lifespan, and improve performance.

## What is Bypass Charging?

In standard charging, your smartphone uses the battery even when plugged in, while simultaneously charging it. **Bypass charging** differs by allowing the device to receive power directly from the charger, effectively bypassing the battery. This technique, used in some gaming devices and high-performance laptops, helps reduce wear and heat.

## Benefits of Bypass Charging

1. **Extended Battery Lifespan:** By avoiding constant charging and discharging, bypass charging reduces the stress on the battery, helping it retain capacity longer.
2. **Lower Heat Generation:** Bypass charging avoids the combined heat of charging and intense usage, reducing strain on the battery.
3. **Enhanced Performance:** With less heat, devices are less likely to throttle during resource-heavy activities, providing a smoother user experience, especially during gaming.

## How to Enable Bypass Charging on MediaTek Devices
Many **MediaTek devices** support bypass charging via the `mtk_battery_cmd` procfs interface. This allows control over current limits and bypass charging with a few simple commands. **Note:** Root access is required.

```shell
# Enable bypass charging
# Charging current will read 10mA or lower, indicating bypass charging is active.
echo "0 1" > /proc/mtk_battery_cmd/current_cmd

# Disable bypass charging
# Charging current returns to normal.
echo "0 0" > /proc/mtk_battery_cmd/current_cmd
```

Other tools, like [Advanced Charging Controller (ACC)](https://github.com/VR-25/acc) and [Origami Kernel Manager](https://github.com/Rem01Gaming/origami_kernel_manager), also support bypass charging on MediaTek and other devices.

## Important Considerations for Bypass Charging

1. **Use an Original or Equivalent Charger**
> Non-original chargers typically deliver less current. Low current may cause slight battery drain if the system compensates for current deficit from the charger.

2. **Not All Devices Are Compatible**
> Bypass charging requires both software and hardware support. Some devices may not fully support bypass charging, even if enabled.

## References
[Advanced Charging Controller (ACC)](https://github.com/VR-25/acc)

[Origami Kernel Manager](https://github.com/Rem01Gaming/origami_kernel_manager)

[How-To Geek on Bypass Charging](https://www.howtogeek.com/what-is-bypass-charging-and-why-you-want-it/)