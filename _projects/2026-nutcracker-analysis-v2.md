---
layout: project
title: Macadamia Nutcracker Design
description: A simple lever nutcracker sized to crack a macadamia nut, with a linear-actuator modification to improve usability.
technologies: [Statics, FBD analysis]
image: /assets/images/nutcrackerp1.png
---

A hand-operated lever nutcracker designed to crack a macadamia nut, then modified to swap human grip strength for a linear actuator.

*ENGRD 2020 — Statics and Mechanics of Solids · Spring 2026*

## Find (Objective)

Design a simple lever-style nutcracker that can crack a macadamia nut. Specifically:

- Determine the lever-arm dimensions required so an average user can produce enough force at the nut to crack it.
- Discuss the usability of the resulting design.
- Modify the design to use a linear actuator instead of human grip strength.

## Given (Inputs and Constraints)

| Parameter | Value | Source |
|---|---|---|
| Load to crack a macadamia nut, F<sub>out</sub> | ≈ 222.18 kgf (≈ 2179 N) | Schrauf et al. (2008) |
| Typical grip strength, women, F<sub>in</sub> | 25–29 kgf (used 27 kgf) | Reference grip-strength data |
| Average macadamia nut diameter, *d* | ≈ 27 mm (radius *r* = 13.5 mm) | Typical reported value |

**Assumptions**

- Symmetric two-arm lever about a vertical line of symmetry.
- Pivot at A; nut clamped at B; input force applied at the handle C.
- Members are rigid (HW4 scope — handle deflection is treated in the HW12 follow-up).

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

## Acknowledgments and Sources

- Discussion with Laura at office hours, and with classmates Angelika and Eva.
- Schrauf, C., et al. *Do capuchin monkeys use weight to select hammer tools?* **Animal Cognition** 11, 413–422 (2008). [doi:10.1007/s10071-007-0131-2](https://doi.org/10.1007/s10071-007-0131-2)
- Linear actuator catalog: [Progressive Automations Linear Actuators](https://www.progressiveautomations.com/collections/linear-actuators).

