# ISCIR

**Integrated Sensing, Communication and Intelligent Robotics**

> An open-source research framework for reproducible simulation and development of next-generation autonomous robotic perception systems based on integrated sensing and communication technologies.

[![Project Status](https://img.shields.io/badge/status-under%20development-orange)](#project-status)
[![Primary Language](https://img.shields.io/badge/python-primary-blue)](#technology-strategy)
[![Research Framework](https://img.shields.io/badge/type-research%20framework-informational)](#vision)

## Vision

ISCIR aims to provide a modular, extensible, and scientifically reproducible environment for research at the intersection of:

- integrated sensing and communication (ISAC),
- FMCW radar sensing,
- optical sensing and optical ISAC,
- autonomous robotics,
- statistical signal processing,
- target detection and tracking,
- machine learning and artificial intelligence,
- physics-informed simulation.

The long-term objective is to connect waveform generation, propagation-channel modelling, sensing, communication, perception, tracking, and robotic decision-making within a coherent research framework.

## Project Status

> **Under active development — pre-alpha**

ISCIR is currently in **Sprint 1: Foundation**. The repository is being established before algorithmic modules are introduced. Interfaces, architecture, tests, documentation, and reproducibility conventions may change substantially until the first stable release.

The initial development target is a minimal simulation workflow in which a user can define a scene, add targets, generate a synthetic signal, and visualize the result.

```python
from iscir.simulation import Scene

scene = Scene()
scene.add_target(distance=20.0, velocity=3.0)

signal = scene.generate()
signal.plot()
```

The example above represents the **planned public API** and is not yet available in the current release.

## Research Scope

ISCIR is designed around six interacting research domains:

| Domain | Intended capabilities |
|---|---|
| Simulation | Scene definition, targets, trajectories, environmental parameters, and reproducible experiments |
| Waveforms | FMCW, communication-aware, and future optical waveform generation |
| Channels | Propagation, attenuation, delay, Doppler, multipath, interference, and noise models |
| Sensing | Radar and optical signal processing, detection, estimation, and range–Doppler analysis |
| Tracking and Robotics | Multi-target state estimation, sensor integration, navigation, and robotic perception |
| AI | Learned signal processing, data-driven perception, fusion, and decision support |

## Conceptual Processing Pipeline

```text
Scene
  ↓
Targets and trajectories
  ↓
Waveform generator
  ↓
Propagation channel
  ↓
Noise and interference
  ↓
Received signal
  ↓
Receiver processing
  ↓
Detection and estimation
  ↓
Tracking and robotic perception
```

The first functional pipeline will focus on a reduced simulation chain:

```text
Scene → FMCW waveform → Channel → Receiver → FFT → Range profile
```

## Design Principles

ISCIR development is guided by the following principles:

1. **Scientific reproducibility** — experiments should be configurable, deterministic when seeded, and accompanied by explicit assumptions.
2. **Modularity** — scene generation, waveform synthesis, channel modelling, receiver processing, and tracking should remain independently testable.
3. **Physical interpretability** — model parameters, units, coordinate systems, and approximations should be documented clearly.
4. **Extensibility** — researchers should be able to add algorithms and models without modifying unrelated components.
5. **Verification** — numerical implementations should be validated through analytical checks, unit tests, reference cases, and MATLAB comparisons where appropriate.
6. **Interoperability** — the architecture should support future integration with ROS 2, PyTorch, scientific Python tooling, and external simulators.

## Technology Strategy

Python is the primary implementation language because it enables direct integration with the modern scientific-computing, robotics, and machine-learning ecosystems.

Planned core dependencies include tools from the Python scientific stack, selected incrementally as the framework develops. MATLAB examples may be maintained separately for algorithm verification, benchmark reproduction, and comparison with established research workflows.

ROS 2 and AI components are intentionally outside the first foundation release. The early focus is a clean, testable simulation core.

## Planned Repository Structure

```text
ISCIR/
├── README.md
├── LICENSE
├── .gitignore
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── docs/
│   ├── architecture.md
│   ├── roadmap.md
│   ├── theory.md
│   └── references.md
├── core/
├── simulation/
│   ├── scenarios/
│   ├── channel/
│   ├── generator/
│   └── visualization/
├── waveforms/
├── sensing/
├── tracking/
├── communication/
├── robotics/
├── ai/
├── examples/
├── tests/
└── assets/
```

The structure is provisional and may evolve as package boundaries and public interfaces are formalized.

## Roadmap

| Version | Primary milestone |
|---|---|
| v0.1 | Repository foundation and project infrastructure |
| v0.2 | Scenario generator |
| v0.3 | FMCW signal generator |
| v0.4 | Propagation and channel models |
| v0.5 | Radar receiver processing |
| v0.6 | Target tracking |
| v0.7 | Robotics integration |
| v0.8 | Artificial intelligence modules |
| v1.0 | Stable, documented, and validated release |

Detailed milestones and acceptance criteria will be maintained in `docs/roadmap.md`.

## Initial v0.1 Objective

Version 0.1 will establish the repository, documentation, contribution conventions, package architecture, testing infrastructure, and the minimal abstractions required for scene-based simulation.

The target user workflow is:

```python
scene = Scene()
scene.add_target(...)
signal = scene.generate()
plot(signal)
```

No AI, ROS 2, or advanced perception stack is required for this milestone.

## Contributing

ISCIR is intended to grow as an open research project. Contributions involving architecture, documentation, physical models, signal-processing algorithms, validation experiments, tests, and reproducible examples will be welcome once the contribution workflow is published.

Until `CONTRIBUTING.md` is finalized, proposed changes should be introduced through focused issues and pull requests with:

- a clear scientific or engineering motivation,
- explicit assumptions and units,
- tests or validation evidence where applicable,
- documentation for public interfaces,
- references for externally derived models or equations.

## Documentation

Planned documentation includes:

- `docs/architecture.md` — system boundaries, modules, interfaces, and data flow,
- `docs/roadmap.md` — releases, milestones, and acceptance criteria,
- `docs/theory.md` — mathematical models, notation, assumptions, and derivations,
- `docs/references.md` — scientific literature, standards, and supporting sources.

## Citation

A formal citation file will be added when the first research release is published. Until then, academic users should cite the repository URL and the specific commit used in their experiments.

## License

A project license will be selected and documented during Sprint 1. Until a license file is committed, no permissions should be assumed beyond those granted by applicable law.

## Maintainer

ISCIR is initiated and maintained by [panagiotagrosdouli](https://github.com/panagiotagrosdouli).

---

**ISCIR is research software under development. Results generated with early versions should be independently validated before scientific or operational use.**
