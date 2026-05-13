---
title: Tube and hose
description: 
---

## Interactive Hose / Tube Diameter Calculator
This calculator helps you size a hydraulic hose or tube by converting flow rate and target fluid velocity into the minimum required internal diameter, then selecting the next suitable nominal size (DN). It also estimates line pressure drop using the Darcy-Weisbach equation with temperature-dependent viscosity for common hydraulic oil grades (default ISO VG 46), so you can quickly compare design choices and avoid excessive velocity and energy loss.

<iframe src="../../media/hose-calculator.html" style="width: 100%; height: 660px; border: 0"></iframe>

## Tubing

### Tube Sizing Standards: DIN 2391 S/L and EN 10305-4

Hydraulic tubing is specified using two related European standards that define seamless steel tubes for hydraulic systems.

#### DIN 2391 S/L System

The **DIN 2391** standard uses a code-based sizing format: **Size Code + S/L designation**

- **S** = "Schwer" (German for Heavy) — heavier wall thickness, higher pressure rating
- **L** = "Leicht" (German for Light) — lighter wall thickness, lower pressure rating

Examples: 6S, 6L, 10S, 10L, 16S, 16L

For each nominal size code, the S and L variants have different outside diameters and wall thicknesses, allowing selection based on system pressure requirements while maintaining compatibility with standard hydraulic component ports.

#### EN 10305-4 System

**EN 10305-4** is the current European standard for seamless precision steel tubes for hydraulic applications. It replaced DIN 2391 but maintains compatibility. Sizing uses an explicit notation: **OD × WT** (Outside Diameter × Wall Thickness in mm)

- **Example:** 16 × 2 means 16 mm OD with 2 mm wall thickness
- **Internal Diameter** is calculated as: ID = OD − (2 × WT)
  - For 16 × 2: ID = 16 − 4 = 12 mm
- **Common sizes:** 4×1, 6×1, 8×1, 10×1, 10×1.5, 12×1.5, 14×2, 16×2, 18×2, 20×2, 22×2, 25×2.5, 28×2.5, 32×3, 36×3, 40×3, 45×3, 50×3.5

#### DIN 2391 to EN 10305-4 Relationship

EN 10305-4 evolved from DIN 2391 and maintains dimensional compatibility. The main difference is notation:
- DIN 2391 uses the S/L code system for quick pressure-class identification
- EN 10305-4 specifies exact dimensions, providing clearer transparency on material properties and pressure ratings

Modern specifications typically reference EN 10305-4, though DIN 2391 designations are still encountered in legacy documents and some European industries.
