# Assembly Instructions — Drone Tracker

## Tools Required

- 3D printer (PETG, PLA, or TPU)
- Soldering iron with fine tip + small-gauge solder
- Wire strippers, heat gun, heat shrink
- Small Phillips screwdrivers (M1.2, M2)
- Tweezers, multimeter, hobby knife / flush cutters
- LiPo battery charger
- Zip ties / cable management straps

## Assumptions

- Basic soldering experience
- Familiarity with Betaflight Configurator (or similar FC software)
- Computer with USB port for FC configuration
- Understanding of LiPo battery safety
- Basic drone electrical wiring knowledge

---

## Phase 1 — Fabricate

Print all custom mechanical parts (12 unique mounts + canopy):

| Step | Task | Parts |
|------|------|-------|
| 1.1 | 3D print all mounts and canopy | 12 |
| 1.2 | Test fit Flight Controller in mount | 2 |
| 1.3 | Test fit 4-in-1 ESC in mount | 2 |
| 1.4 | Test fit GPS module in mount | 2 |
| 1.5 | Test fit Radio Receiver in mount | 2 |
| 1.6 | Test fit VTX in mount | 2 |
| 1.7 | Test fit motors in arm mounts | 8 |
| 1.8 | Assemble camera, gimbal, and servo in camera mount | 4 |

---

## Phase 2 — Wire

| Step | Task |
|------|------|
| 2.1 | Solder XT30 power leads from LiPo to ESC and FC |
| 2.2 | Solder motor phase wires from ESC to each motor |
| 2.3 | Solder FC data/telemetry wires to ESC |
| 2.4 | Solder GPS TX/RX and power to FC UART2 |
| 2.5 | Solder Radio RX TX/RX and power to FC UART3 |
| 2.6 | Solder VTX data and power to FC UART4 / VBAT |
| 2.7 | Solder camera video out to VTX; I2C/power to FC |
| 2.8 | Solder gimbal servo PWM and power to FC PWM5 |

See [wiring.md](wiring.md) for the full connection map.

---

## Phase 3 — Bring-up

### 3.1 Continuity checks

- Disconnect LiPo before testing.
- Check VBAT ↔ GND shorts on ESC and FC.
- Check 5V ↔ GND on GPS, RX, VTX, camera, and servo.
- Verify FC 5V/GND reach all peripherals.
- Confirm no shorts between power/ground and data pins.

### 3.2 Flash and configure FC

1. Connect SpeedyBee F7 Mini via USB.
2. Open Betaflight → Firmware Flasher → flash latest stable firmware (Full Erase).
3. Set drone type to **quadcopter**.
4. Calibrate accelerometer (and magnetometer if present).
5. Save and reboot.

### 3.3 ESC and motor direction

1. Remove all propellers.
2. Betaflight → Motors tab → enable motor testing.
3. Spin each motor individually; verify smooth operation and correct direction.
4. Reverse any two phase wires on a motor if direction is wrong.

### 3.4 GPS lock

1. Ports: enable Serial RX + GPS (UBLOX) on UART2.
2. Configuration: enable GPS feature.
3. Test outdoors with clear sky view.
4. Wait for 3D fix in Betaflight GPS tab.

### 3.5 Radio binding

1. Ports: enable Serial RX on UART3.
2. Configuration: Serial-based receiver, CRSF, telemetry on.
3. Bind ELRS receiver to transmitter.
4. Verify stick inputs in Receiver tab.

### 3.6 Video feed

1. Power on (no propellers).
2. Set VTX band/channel/power in Betaflight.
3. Tune FPV goggles to match.
4. Confirm clear camera image and OSD (if configured).

### 3.7 Gimbal servo

1. Servos tab: enable PWM5 output.
2. Set min/max/neutral pulse widths for SG90.
3. Map an aux channel to tilt control.
4. Verify full-range movement; reverse if needed.

---

## Phase 4 — Assemble

| Step | Task |
|------|------|
| 4.1 | Mount FC and ESC in frames on Main Frame |
| 4.2 | Secure four motors in mounts; attach mounts to frame |
| 4.3 | Mount GPS, RX, and VTX in their cradles |
| 4.4 | Attach camera & gimbal assembly to front of frame |
| 4.5 | Mount battery tray; secure LiPo |
| 4.6 | Route and zip-tie all wires for strain relief |
| 4.7 | Attach propellers (correct rotation per corner) |
| 4.8 | Install protective canopy |

---

## First Flight Checklist

- [ ] All continuity checks passed
- [ ] Motors spin correct direction (props off)
- [ ] GPS 3D fix acquired outdoors
- [ ] Radio bound and channels verified
- [ ] FPV feed clear
- [ ] Gimbal servo responds to aux channel
- [ ] LiPo charged and secured
- [ ] Canopy installed
- [ ] Open area, no bystanders nearby
