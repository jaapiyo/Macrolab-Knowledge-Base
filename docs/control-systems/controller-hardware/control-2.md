---
title: Control 2
description: Hydraulic servo controller, version 2
---

# Manifold I/O connector
The connector on the controller side is a *25-pin male D sub* with the following pinout (all other pins are not connected).

| Pin | Function        |
| --- | --------------- |
| 1   | VLV Out         |
| 2   | VLV Act         |
| 3   | Loop 4          |
| 4   | Loop 3          |
| 5   | Loop 2 (PS)     |
| 6   | Loop 1          |
| 7   | R1M (VK)        |
| 8   | R2M (HK)        |
| 9   | R3M             |
| 10  | + 24V           |
| 14  | GND             |
| 15  | GND             |
| 16  | + 24V           |
| 17  | + 24 V          |
| 18  | + 24 V          |
| 19  | + 24V           |
| 20  | GND             |
| 21  | GND             |
| 22  | R3NO            |
| 23  | GND             |

# F, S, $\upepsilon$ connector
The connector on the controller side is a *25-pin female D sub* with the following pinout (all other pins are not connected).

| Pin | Function        |
| --- | --------------- |
| 1   | AC ex +         |
| 14  | AC ex -         |
| 2   | AC in +         |
| 15  | AC in -         |
| 3   | GND             |
| 16  | GND             |
| 4   | AC direct       |
| 17  | AC signal       |
| 5   | DC1 ex +        |
| 18  | DC1 ex -        |
| 6   | DC1 in +        |
| 19  | DC1 in -        |
| 7   | GND             |
| 20  | GND             |
| 8   | DC1 direct      |
| 21  | DC1 sign        |
| 9   | DC2 ex +        |
| 22  | DC2 ex -        |
| 10  | DC2 in +        |
| 23  | DC2 in -        |
| 11  | GND             |
| 24  | GND             |
| 12  | DC2 direct      |
| 25  | - 15V           |
| 13  | + 15V           |


Direct (DCT) is switched internally to bypass input conditioner. Signal (SIGN) is directly connected to the output of the conditioner. Don't input any signal into SIGN because this can cause a short circuit with the output of the amplifier in the conditioner!