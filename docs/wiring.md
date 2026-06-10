# Wiring Guide — Drone Tracker

![Wiring diagram](images/wiring-diagram.png)

## Connection Summary

| From | To | Interface | Notes |
|------|----|-----------|-------|
| LiPo Battery | 4-in-1 ESC, Flight Controller | Power (XT30) | 14.8V main bus |
| 4-in-1 ESC | Flight Controller | PWM In | Motor control signals |
| 4-in-1 ESC | Motors (×4) | Phase wires | 3 wires per motor |
| Flight Controller | GPS Module | UART2 (TX/RX) | UBLOX protocol |
| Flight Controller | Radio Receiver | UART3 (TX/RX) | CRSF (ELRS) |
| Flight Controller | VTX | UART4 | SmartAudio / Tramp |
| Flight Controller | Camera Module | I2C (SDA/SCL) | Control + telemetry |
| Flight Controller | Gimbal Servo | PWM5 | Tilt control |
| Camera Module | VTX | Analog video | FPV feed |
| All components | Common ground | GND | Shared ground plane |

## Flight Controller Ports

**SpeedyBee F7 Mini**

| Port | Assignment |
|------|------------|
| UART1 | — |
| UART2 | GPS (Serial RX + GPS UBLOX) |
| UART3 | ELRS Radio Receiver (CRSF) |
| UART4 | VTX (SmartAudio / Tramp) |
| I2C | Camera Module (SDA/SCL) |
| PWM1–4 | 4-in-1 ESC motor outputs |
| PWM5 | Gimbal tilt servo |
| VBAT | Battery voltage sense |

## Power Distribution

```
LiPo Battery (2S, 14.8V)
    ├── 4-in-1 ESC (VBAT) ──► Motors ×4
    └── Flight Controller (VBAT)
            ├── 5V ──► GPS, RX, VTX, Camera, Servo
            └── GND ──► Common ground bus
```

## Wiring Steps

1. **Main power** — Solder XT30 leads from LiPo to 4-in-1 ESC and Flight Controller.
2. **Motors** — Solder phase wires from ESC to each motor (FL, FR, RL, RR).
3. **ESC data** — Connect FC PWM outputs to ESC PWM In.
4. **GPS** — Solder TX/RX and 5V/GND to FC UART2.
5. **Radio** — Solder TX/RX and 5V/GND to FC UART3.
6. **VTX** — Solder data, 5V, and GND to FC UART4 and VBAT as needed.
7. **Camera** — Route analog video to VTX; connect I2C and power to FC.
8. **Gimbal servo** — Connect PWM and 5V/GND to FC PWM5.

## Safety

- Disconnect LiPo before soldering or continuity checks.
- Verify no shorts between VBAT and GND before first power-on.
- Confirm 5V/GND continuity to all peripherals without data-pin shorts.
