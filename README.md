# autonomous-drone

A UAV platform focused on stable autonomous flight and navigation.

![Domain](https://img.shields.io/badge/domain-UAV%20%2F%20flight%20control-1E90FF)
![Embedded](https://img.shields.io/badge/embedded-yes-success)
![Status](https://img.shields.io/badge/status-in%20development-orange)

## Overview

`autonomous-drone` is an unmanned aerial vehicle (UAV) platform aimed at stable autonomous flight and navigation — from reliable attitude stabilization up to waypoint-based autonomous missions. This repository is the home for the flight firmware, control logic, and hardware/design documentation.

> Early-stage project — this repository currently holds the structure, design docs, and roadmap. Implementation details are marked `TODO:` and filled in as the platform develops.

## Features (planned)

- Attitude stabilization and reliable manual-assisted flight
- Sensor fusion for state estimation (IMU + barometer + GPS)
- Waypoint navigation and autonomous flight modes
- Fail-safes (low battery, signal loss)

## Tech stack

- **Domain:** UAV / flight control
- **Compute:** embedded flight controller (TODO: confirm board, e.g. STM32-based / Pixhawk-class)
- **Firmware/Language:** TODO: confirm (C/C++ firmware, or a flight stack such as PX4/ArduPilot)
- **Sensors:** IMU, barometer, GPS (TODO: confirm)

## Architecture (intended)

1. **Sense** — read IMU/baro/GPS for orientation, altitude, and position.
2. **Estimate** — fuse sensors into a stable state estimate.
3. **Control** — run stabilization + position control loops.
4. **Navigate** — execute autonomous waypoint missions with fail-safes.

## Getting started

TODO: add hardware bring-up and firmware flashing instructions once the platform is defined.

## Repository layout

```
src/     # flight firmware / control source
docs/    # wiring, frame design, tuning notes
```

## Status

In development — scaffolding and design phase.

## Roadmap

- TODO: finalize frame + flight controller + ESC/motor selection
- TODO: bring up stabilization loop and manual-assisted flight
- TODO: add state estimation (sensor fusion)
- TODO: add GPS waypoint navigation
- TODO: flight test + demo video

## Contact

Bhavya Dosi — [LinkedIn](https://www.linkedin.com/in/bhavya-dosi)
