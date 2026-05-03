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

In the HW4 design the handles were treated as rigid. Now I model each handle as a **beam that bends** under the combined transverse loads from the nut at B and from the actuator at C.

This analysis is done on the **linear-actuator version** of the design, since the assignment text specifies *"forces from the nut and from the actuator."*

### Idealization

I model one half-handle as a **cantilever fixed at the pivot A**, of length L = L<sub>1</sub> = 222 mm, with two point loads applied transverse to the beam axis:

- The nut reaction at point B, distance *a<sub>1</sub>* = L<sub>2</sub> = 27 mm from A.
- The actuator force at point C, distance *a<sub>2</sub>* = L<sub>1</sub> = 222 mm from A.

**Why a cantilever?** The pivot at A is a pin — it allows rotation of either arm about A but provides no moment reaction. However, by mirror symmetry, when both arms are loaded identically each arm's slope at A is zero relative to the centerline. The pivot is therefore *equivalent to a fixed (cantilever) support* for the analysis of one arm in symmetric loading.

### Forces and Their Transverse Components

| Symbol | Value | Direction | Where applied |
|---|---|---|---|
| F<sub>act</sub> | 56 lbf ≈ 249 N | inward (toward centerline) | C, at x = L<sub>1</sub> |
| F<sub>nut</sub> = (L<sub>1</sub>/L<sub>2</sub>) · F<sub>act</sub> = 8.23 · F<sub>act</sub> | ≈ 2050 N | outward (away from centerline) | B, at x = L<sub>2</sub> |

The handle sits at angle θ = 30° from the centerline. The applied forces are perpendicular to the centerline, so projecting onto the direction transverse to the beam:

- F<sub>1</sub> = F<sub>nut</sub> · cos θ = 2050 · cos 30° ≈ **+1775 N** at *x = a<sub>1</sub>* (outward)
- F<sub>2</sub> = F<sub>act</sub> · cos θ = 249 · cos 30° ≈ **−216 N** at *x = a<sub>2</sub>* (inward)

The two transverse loads point in opposite directions: the nut pushes outward, the actuator inward.

### Part (a) — Location of Maximum Deflection

Using Beer Ch15 cantilever deflection formulas + superposition. For a cantilever with a point load P at distance *a* from the wall:

- For *x ≤ a*:  *δ(x) = P x²(3a − x) / (6EI)*
- For *x > a*:  *δ(x) = P a²(3x − a) / (6EI)*

Superposing F<sub>1</sub> at *a<sub>1</sub>* and F<sub>2</sub> at *a<sub>2</sub>*, the slope dδ/dx in the region a<sub>1</sub> ≤ x ≤ a<sub>2</sub> is:

dδ/dx = (1 / (2EI)) · [F<sub>1</sub> · a<sub>1</sub>² + F<sub>2</sub> · x · (2a<sub>2</sub> − x)]

Plugging in: F<sub>1</sub>·a<sub>1</sub>² = 1775 × (0.027)² ≈ 1.29; F<sub>2</sub>·x·(2a<sub>2</sub>−x) = −216 · x · (0.444 − x). Setting dδ/dx = 0 gives x ≈ 0.014 m, **outside** the region a<sub>1</sub> ≤ x ≤ a<sub>2</sub>. Inside that region dδ/dx is therefore single-signed (negative — checked at x = a<sub>1</sub> and x = a<sub>2</sub>), and a similar argument shows dδ/dx is single-signed on 0 ≤ x ≤ a<sub>1</sub>.

**Conclusion:** δ(x) is monotonic over the whole beam — there is no internal extremum — so the deflection has its maximum magnitude at the **tip, x = L<sub>1</sub> = 222 mm (point C, where the actuator pushes)**.

The magnitude is found by evaluating the superposition at x = L<sub>1</sub>:

δ<sub>max</sub> = (1 / (6EI)) · [F<sub>1</sub> · a<sub>1</sub>² · (3 L<sub>1</sub> − a<sub>1</sub>) + 2 F<sub>2</sub> L<sub>1</sub>³]

Plugging in numbers:

δ<sub>max</sub> · EI ≈ (1 / 6) · [1775 · (0.027)² · (3·0.222 − 0.027) + 2·(−216)·(0.222)³]
                   ≈ (1 / 6) · [0.827 − 4.726]
                   ≈ **−0.650 N · m³**

So |δ<sub>max</sub>| ≈ **0.650 / (EI)**, in the **inward** direction (the actuator dominates the bending).

### Part (b) — Cross-Section + Material Selection

**Constraint:** vertical elastic deflection below 2% of beam length.

> δ<sub>max</sub> < 0.02 × L<sub>1</sub> = 0.02 × 0.222 m = **4.44 mm**

This requires **EI > 0.650 / 0.00444 ≈ 146 N · m²**.

**Mass-efficiency criterion.** For fixed length, mass is *m = ρAL*, and stiffness is *EI*. Mass-efficient sections have a high *I/A* (radius of gyration) — favoring **hollow circular tubes** and **I-beams** over solid rods. Mass-efficient materials have a high *E/ρ*. For common engineering materials:

| Material | E (GPa) | ρ (kg/m³) | E/ρ (MJ/kg) |
|---|---|---|---|
| Steel | 200 | 7800 | 25.6 |
| Aluminum 6061-T6 | 69 | 2700 | 25.6 |
| CFRP (carbon fiber) | 130 | 1600 | 81.3 |

Aluminum and steel have similar specific stiffness. CFRP is best on paper, but for a manufacturable, machinable, affordable nutcracker handle I select **aluminum 6061-T6** (low density, easy machining, common stock).

**Section sizing.** Trying a hollow circular aluminum tube of outer diameter D<sub>o</sub> and wall thickness t.

For **D<sub>o</sub> = 19 mm, t = 1 mm** (ID = 17 mm):

- I = π(D<sub>o</sub>⁴ − D<sub>i</sub>⁴) / 64 = π(19⁴ − 17⁴) / 64 ≈ **2298 mm⁴ = 2.30 × 10⁻⁹ m⁴**
- A = π(D<sub>o</sub>² − D<sub>i</sub>²) / 4 = π(361 − 289) / 4 ≈ **56.5 mm²**
- EI = 69 GPa × 2.30 × 10⁻⁹ m⁴ ≈ **159 N · m²** > 146 N · m² ✓
- Predicted δ<sub>max</sub> = 0.650 / 159 ≈ **4.10 mm** < 4.44 mm ✓
- Mass per handle = ρ · A · L = 2700 × 56.5 × 10⁻⁶ × 0.222 ≈ **0.034 kg ≈ 34 g**

A solid aluminum rod meeting the same constraint would need diameter ≈ 15 mm and weigh ≈ 106 g — about **3× heavier** for the same stiffness. The hollow tube is the mass-efficient choice.

### Part (c) — Final Design

**Selected handle:** aluminum 6061-T6 hollow circular tube, **19 mm OD × 1 mm wall × 222 mm long**.

**Predicted performance:** maximum deflection ≈ 4.10 mm at the tip (point C, where the actuator attaches), satisfying the 4.44 mm (2%) limit with ~7% margin.

**Mass per handle:** ≈ 34 g; total mass of both arms ≈ 68 g (excluding pivot, jaws, and actuator).

*A drawing of the final beam-handle design will be added here once sketched.*

### Assumptions and Limitations

- **Symmetry assumption** justifies the cantilever boundary at A. If real loading is asymmetric (e.g., off-axis grip), the slope at A is nonzero and the deflection grows.
- **Linear elastic, small deflection.** δ ≈ 4 mm out of 222 mm length (≈ 2%) is at the edge of where small-deflection beam theory holds.
- **Transverse force only** is considered, as instructed. Axial components (F · sin θ ≈ 0.5 F) cause column compression but are neglected here. For F<sub>nut</sub> = 2050 N axial × sin 30° ≈ 1025 N, Euler buckling of a 222 mm aluminum tube is well above this load, so this is a safe simplification.
- **Stress check.** The maximum bending moment at A is M<sub>max</sub> ≈ F<sub>1</sub>·a<sub>1</sub> + F<sub>2</sub>·a<sub>2</sub> ≈ 1775·0.027 + 216·0.222 ≈ 95.85 N·m. Bending stress σ = Mc/I = 95.85 × 0.0095 / (2.30 × 10⁻⁹) ≈ 396 MPa, which exceeds the yield strength of 6061-T6 (~276 MPa). **The deflection-optimal design fails on stress** — it would yield at the pivot under cracking load. A real design would need to thicken the wall near A (or use a higher-strength alloy / steel) to avoid yielding. *Flagging this as a limitation of the deflection-only criterion in the assignment.*

## Acknowledgments and Sources

- Discussion with Laura at office hours, and with classmates Angelika and Eva.
- Schrauf, C., et al. *Do capuchin monkeys use weight to select hammer tools?* **Animal Cognition** 11, 413–422 (2008). [doi:10.1007/s10071-007-0131-2](https://doi.org/10.1007/s10071-007-0131-2)
- Linear actuator catalog: [Progressive Automations Linear Actuators](https://www.progressiveautomations.com/collections/linear-actuators).
- Beer, Johnston, et al. *Mechanics of Materials*, Ch. 15 (beam deflection equations).
