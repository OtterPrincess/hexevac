# hexevac

# HEXEVAC
### Open-Source Rescue Robotics Research Platform

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-nd/4.0/)
[![Status: Active Research](https://img.shields.io/badge/Status-Active%20Research-orange)]()
[![Version: 0.1.0-alpha](https://img.shields.io/badge/Version-0.1.0--alpha-blue)]()

---

A 6-legged autonomous rescue robot designed for emergency stair evacuation with a patient transport capsule — built on prior clinical research into neonatal vibration isolation (Project Nestara).

**[→ View the Research Dashboard](https://otterprincess.github.io/hexevac)** *(enable GitHub Pages to activate)*

---

## The Problem

No existing rescue robot addresses patient safety during transport. Current platforms move a patient — they don't protect one. Stair evacuation produces multi-axis acceleration profiles that can cause serious harm to critically ill patients, yet every legged robot in development treats the payload as cargo.

## The Research Origin

This project grows directly out of **Nestara** — an IDEP (Interdisciplinary Design Engineering Project) that investigated auxetic metamaterial lattice structures for neonatal vibration isolation during medical transport. That research was developed through field immersion with:

- **UCAN / Lurie Children's Hospital** — neonatal transport team observations
- **Boston MedFlight** — NICU air transport protocol review

**Honest research status:** Testing showed amplified vibration in some conditions using BCC lattice geometry at FDM consumer print resolution. The clinical need is validated. The right isolation material is still an open research question. This repo documents that openly.

## What's In This Repo

| File | Description |
|------|-------------|
| `index.html` | Full research dashboard — kinematics, architecture, AI stack, prior art, prototype photos |
| `LICENSE.md` | CC BY-NC-ND 4.0 — read and reference freely, no commercial use or derivatives |
| `README.md` | This file |

## Robot Specs

| Parameter | Value |
|-----------|-------|
| Legs | 6 |
| DOF per leg | 6 (R-R-R-P-R-R chain) |
| Patient tilt limit | ±5° |
| Stair descent speed | 1.2 m/s (target) |
| Control loop | 1kHz joint / 50Hz RL policy |
| Simulation | MuJoCo + Isaac Lab |
| Software stack | ROS2, Python, C++ |

## Kinematic Chain

```
HIP YAW → HIP PITCH → KNEE PITCH → [PRISMATIC] → ANKLE PITCH → ANKLE ROLL → FOOT
    R           R            R            P               R             R
```

The prismatic joint is the key addition over standard hexapod designs — it provides terrain compliance and maps directly to the spring layer in the Nestara isolation stack.

## Open Research Questions

- [ ] Is BCC lattice geometry viable at accessible manufacturing tolerances, or does FDM resolution introduce resonance amplification?
- [ ] Does open-cell foam (Confor, Evazote) outperform geometric metamaterial at neonatal WBV frequencies?
- [ ] Can the Nestara passive isolation stack be integrated into a robot-mounted capsule without adding prohibitive mass?
- [ ] What RL reward shaping best captures patient safety constraints during stair descent?

## Roadmap

- [x] v0.1 — Research platform, prior art documentation, kinematic spec
- [ ] v0.2 — MuJoCo MJCF model + IK solver validation
- [ ] v0.3 — Tripod gait + flat terrain RL policy
- [ ] v0.4 — Stair detection + descent policy
- [ ] v0.5 — First physical prototype

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) if you want to collaborate.
Areas most needed: simulation, RL training, materials science, mechanical design.

## License

This research is shared under **CC BY-NC-ND 4.0**.
You may read, reference, and cite this work with attribution.
You may not use it commercially or publish derivatives without permission.

The underlying inventive concepts (isolation geometries, capsule architecture) are retained by the author. Contact for licensing or collaboration inquiries.

---

*Built on prior art: Freenove Hexapod (CC BY-NC-SA 3.0) for locomotion reference.*
*Original patient safety research: Project Nestara, 2024.*
