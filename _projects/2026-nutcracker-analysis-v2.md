---
layout: project
title: Macadamia Nutcracker Design
description: A simple lever nutcracker sized to crack a macadamia nut, with a linear-actuator modification and a flexible-handle (beam) extension.
technologies: [Statics, FBD analysis, Beam deflection]
image: /assets/images/nutcrackerp1.png
---

A hand-operated lever nutcracker designed to crack a macadamia nut, then modified to swap human grip strength for a linear actuator, and finally re-analyzed with the handles treated as bending beams.

*ENGRD 2020 — Statics and Mechanics of Solids · Spring 2026*

## Find (Objective)

Design a simple lever-style nutcracker that can crack a macadamia nut. Specifically:

- Determine the lever-arm dimensions required so an average user can produce enough force at the nut to crack it.
- Discuss the usability of the resulting design.
- Modify the design to use a linear actuator instead of human grip strength.
- (HW12 extension) Re-analyze the handles as bendable beams; pick a cross-section and material that meets a deflection limit while minimizing mass.

## Given (Inputs and Constraints)

| Parameter | Value | Source |
|---|---|---|
| Load to crack a macadamia nut, F<sub>out</sub> | ≈ 222.18 kgf (≈ 2179 N) | Schrauf et al. (2008) |
| Typical grip strength, women, F<sub>in</sub> | 25–29 kgf (used 27 kgf) | Reference grip-strength data |
| Average macadamia nut diameter, *d* | ≈ 27 mm (radius *r* = 13.5 mm) | Typical reported value |

**Assumptions**

- Symmetric two-arm lever about a vertical line of symmetry.
- Pivot at A; nut clamped at B; input force applied at the handle C.
- Members are rigid in the HW4 scope — handle deflection is treated in the HW12 follow-up.

## Approach

**Free body diagram (half-symmetry).** Taking moments about the pivot A:

ΣM<sub>A</sub> = 0  →  F<sub>out</sub> · (L<sub>2</sub> sin θ) = F<sub>in</sub> · (L<sub>1</sub> sin θ)

The sin θ terms cancel, giving the mechanical-advantage relation:

**F<sub>out</sub> / F<sub>in</sub> = L<sub>1</sub> / L<sub>2</sub>**

**Required mechanical advantage:**

F<sub>out</sub> / F<sub>in</sub> = 222.18 kgf / 27 kgf ≈ **8.23**

So the handle arm L<sub>1</sub> must be at least 8.23 × the length of the nut arm L<sub>2</sub>.

**Sizing L<sub>2</sub> and L<sub>1</sub>.** The nut sits between the two arms at angle θ from the centerline. With nut radius *r* = 13.5 mm:

L<sub>2</sub> = *r* / sin θ

| θ | L<sub>2</sub> | L<sub>1</sub> = 8.23 · L<sub>2</sub> |
|---|---|---|
| 30° | 27 mm | 222 mm |
| 10° | 77.7 mm | 640 mm |

The 10° configuration produces an impractically long handle, so I selected:

> **θ = 30°,  L<sub>2</sub> = 27 mm,  L<sub>1</sub> = 222 mm.**

This gives a total grip-end span of roughly **22.2 cm (≈ 8.7 in)**.

## Diagram and Original Calculations

![Nutcracker free body diagram and dimension calculations]({{"/assets/images/nutcrackerp2.png"|relative_url}})

*Half-symmetry FBD with the moment equation about pivot A, plus the L<sub>1</sub>/L<sub>2</sub> sizing for θ = 30° and θ = 10°.*

## Usability Discussion

The mechanics work, but the resulting **22.2 cm grip span is too wide for much of the population**:

- My own hand (19-year-old female) can only grip an object ≈ 13 cm wide — so I personally cannot operate this design.
- Average adult female hand span: ≈ 16–18 cm — also too narrow.
- Average adult male hand span: 20–22.6 cm — at the upper edge of comfortable use.

The design is mechanically sufficient but fails the usability test for the broader audience it is meant to serve — women, children, and anyone with smaller hands. **Verdict: usability is poor.**

## Modification — Replacing Grip with a Linear Actuator

To eliminate the grip-strength constraint, I replaced the manual squeeze with a mini linear actuator from [Progressive Automations](https://www.progressiveautomations.com/collections/linear-actuators):

> **IPGS Mini Linear Actuator** — stroke ≈ 9 in (22.86 cm), max force ≈ 56 lbf (≈ 25.4 kgf).

**Why it matches:**

- **Stroke** ≈ 9 in ≈ 22.2 cm → matches the existing grip-span travel needed to open and close the lever, so no geometric redesign is required.
- **Force output** ≈ 25.4 kgf — essentially the same F<sub>in</sub> used in the manual design, so the same 8.23 × mechanical advantage carries the actuator's output up to the nut-cracking load.

**Effect on usability.** With the actuator supplying input force via a switch, the user no longer needs 27 kgf of grip strength. The design becomes operable by anyone regardless of hand size or strength — a substantial improvement.

![Modified nutcracker design with IPGS mini linear actuator]({{"/assets/images/nutcrackerp1.png"|relative_url}})

*Final design with the IPGS mini linear actuator (9 in stroke, 56 lbf) replacing the hand grip.*

## HW12 Extension — Flexible Handles

In the HW4 design I treated the handles as rigid. For this part, I'm modeling each handle as a beam that bends from the transverse loads coming from the nut at B and the actuator at C.

I did this analysis on the linear-actuator version since the assignment says "forces from the nut and from the actuator."

### Idealization

I treated one half-handle as a cantilever fixed at the pivot A, length L = L<sub>1</sub> = 222 mm, with two transverse point loads:

- the nut reaction at B, a<sub>1</sub> = L<sub>2</sub> = 27 mm from A
- the actuator force at C, a<sub>2</sub> = L<sub>1</sub> = 222 mm from A

Why a cantilever? The pin at A is just a pin so technically it can rotate freely and provides no moment reaction. But because the loading is symmetric on both arms, by symmetry the slope at A on each arm is zero, so it acts like a fixed support for this analysis.

### Forces and Their Transverse Components

| Symbol | Value | Direction | Where applied |
|---|---|---|---|
| F<sub>act</sub> | 56 lbf ≈ 249 N | inward | C, at x = L<sub>1</sub> |
| F<sub>nut</sub> = (L<sub>1</sub>/L<sub>2</sub>) · F<sub>act</sub> = 8.23 · F<sub>act</sub> | ≈ 2050 N | outward | B, at x = L<sub>2</sub> |

The handle is at θ = 30° from the centerline and the forces are perpendicular to the centerline, so the transverse components on the beam come out to each force times cos θ:

- F<sub>1</sub> = 2050 · cos 30° ≈ +1775 N at x = a<sub>1</sub> (outward)
- F<sub>2</sub> = 249 · cos 30° ≈ −216 N at x = a<sub>2</sub> (inward)

So the two transverse loads point in opposite directions: nut outward, actuator inward.

### Part (a) — Location of Maximum Deflection

Using Beer Ch15 cantilever deflection equations with superposition. For a cantilever with a point load P at distance a:

- for x ≤ a:  δ(x) = P x²(3a − x) / (6EI)
- for x > a:  δ(x) = P a²(3x − a) / (6EI)

After superposing both loads, I checked the slope dδ/dx in the region a<sub>1</sub> ≤ x ≤ a<sub>2</sub>. Setting it to zero gives x ≈ 0.014 m which is outside that region, so inside the region the slope doesn't change sign and theres no internal extremum. Same is true on 0 ≤ x ≤ a<sub>1</sub>.

So the deflection is monotonic across the whole beam, and max deflection happens at the tip, x = L<sub>1</sub> = 222 mm (point C, where the actuator pushes).

The magnitude at the tip works out to:

δ<sub>max</sub> · EI ≈ (1/6) · [1775 · (0.027)² · (3·0.222 − 0.027) + 2·(−216)·(0.222)³]
                   ≈ (1/6) · [0.827 − 4.726]
                   ≈ −0.650 N · m³

So |δ<sub>max</sub>| ≈ 0.650 / (EI), in the inward direction (the actuator dominates).

### Part (b) — Cross-Section + Material Selection

The constraint is δ<sub>max</sub> < 2% of length:

> δ<sub>max</sub> < 0.02 × 0.222 m = 4.44 mm

That requires EI > 0.650 / 0.00444 ≈ 146 N · m².

For the mass-efficient part, mass is m = ρAL and stiffness is EI, so for a fixed length you want a high I/A (so hollow tubes or I-beams beat solid rods) and a high E/ρ.

| Material | E (GPa) | ρ (kg/m³) | E/ρ (MJ/kg) |
|---|---|---|---|
| Steel | 200 | 7800 | 25.6 |
| Aluminum 6061-T6 | 69 | 2700 | 25.6 |
| CFRP (carbon fiber) | 130 | 1600 | 81.3 |

Aluminum and steel come out about even on specific stiffness. CFRP is best on paper but harder to manufacture and more expensive, so I picked aluminum 6061-T6 since its low density, easy to machine, and common stock material.

Trying a hollow circular aluminum tube with outer diameter D<sub>o</sub> = 19 mm and wall thickness t = 1 mm (so the inner diameter is 17 mm):

- I = π(D<sub>o</sub>⁴ − D<sub>i</sub>⁴) / 64 = π(19⁴ − 17⁴) / 64 ≈ 2298 mm⁴ = 2.30 × 10⁻⁹ m⁴
- A = π(D<sub>o</sub>² − D<sub>i</sub>²) / 4 ≈ 56.5 mm²
- EI = 69 GPa × 2.30 × 10⁻⁹ m⁴ ≈ 159 N · m² (more than the 146 needed) ✓
- δ<sub>max</sub> = 0.650 / 159 ≈ 4.10 mm, less than 4.44 mm ✓
- mass per handle = ρ · A · L = 2700 × 56.5 × 10⁻⁶ × 0.222 ≈ 0.034 kg ≈ 34 g

For comparison, a solid aluminum rod meeting the same stiffness would be about 15 mm in diameter and weigh around 106 g, which is about 3× more, so the hollow tube is a lot more mass-efficient.

### Part (c) — Final Design

Selected handle: aluminum 6061-T6 hollow circular tube, 19 mm OD × 1 mm wall × 222 mm long.

Predicted max deflection is around 4.10 mm at the tip (point C, where the actuator attaches), so it stays under the 4.44 mm (2%) limit with about a 7% margin.

Mass per handle is about 34 g, so the total for both arms comes out to around 68 g (not counting the pivot, jaws, or the actuator itself).

### Assumptions and Limitations

- Symmetry assumption is what justifies the cantilever boundary at A. If the loading is asymmetric (off-axis grip etc.) the slope at A wouldn't be zero and the deflection grows.
- Linear elastic, small deflection. δ ≈ 4 mm on a 222 mm length (about 2%) is right at the edge of where small-deflection beam theory holds.
- Only transverse force is considered, as instructed. Axial components (F · sin θ ≈ 0.5 F) cause column compression but I neglected them. With F<sub>nut</sub> · sin 30° ≈ 1025 N axial, Euler buckling of the aluminum tube is way above this load so its safe to ignore.
- Stress check: max bending moment at A is M<sub>max</sub> ≈ F<sub>1</sub>·a<sub>1</sub> + F<sub>2</sub>·a<sub>2</sub> ≈ 95.85 N·m. Bending stress σ = Mc/I = 95.85 × 0.0095 / (2.30 × 10⁻⁹) ≈ 396 MPa, which is more than the yield strength of 6061-T6 (~276 MPa). So the deflection-optimal design would actually yield at the pivot under cracking load, which is a real problem. A real design would probably need a thicker wall near A (or use steel or a higher-strength alloy) to avoid yielding.

## Acknowledgments and Sources

- Discussion with Laura at office hours, and with classmates Angelika and Eva.
- Schrauf, C., et al. *Do capuchin monkeys use weight to select hammer tools?* **Animal Cognition** 11, 413–422 (2008). [doi:10.1007/s10071-007-0131-2](https://doi.org/10.1007/s10071-007-0131-2)
- Linear actuator catalog: [Progressive Automations Linear Actuators](https://www.progressiveautomations.com/collections/linear-actuators).
- Beer, Johnston, et al. *Mechanics of Materials*, Ch. 15 (beam deflection equations).
