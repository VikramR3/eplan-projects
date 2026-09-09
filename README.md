# EPLAN Beginner Projects

Three beginner-level control circuits designed in EPLAN Electric P8, each exported as a single-page circuit diagram (PDF).

## 1. Lamp Latch (`LampLatch.pdf`)

A start/stop push-button latch circuit for a single lamp.

- **S1 (Start)** energizes coil **K1**.
- **K1** seals itself in through its own auxiliary contact, so the button can be released and the lamp stays on.
- **S2 (Stop)** breaks the circuit and drops out K1.
- **K1** also drives lamp **H1** through a second contact.

Standard "start/stop/seal-in" latching logic — the building block behind almost every relay control circuit.

## 2. Door Motor (`DoorMotor.pdf`)

An interlocked forward/reverse circuit for a sliding door motor, using two contactors, **K1** (open) and **K2** (close).

- **S1 (Open)** energizes K1 through K2's interlock contact.
- **S2 (Close)** energizes K2 through K1's interlock contact.
- Each contactor's auxiliary contact blocks the other from energizing at the same time, preventing both directions from being driven simultaneously.

This is the classic cross-interlocked reversing-starter topology used for any bidirectional motor drive.

## 3. Fire Alarm (`FireAlarm.pdf`)

A latching alarm circuit triggered by a smoke switch.

- **SM1 (Smoke switch)** energizes coil **K1**.
- **K1** seals itself in through an auxiliary contact, so the alarm stays latched even after the smoke switch resets.
- **K1** drives horn **HORN1** through a second contact.
- **RESET** breaks the seal-in path to silence the alarm and clear the latch.

Same seal-in latching pattern as the Lamp Latch, applied to an alarm/annunciator use case.

---

Built with [EPLAN Electric P8](https://www.eplan.com/) as hands-on practice projects for learning relay logic and control-circuit fundamentals.
