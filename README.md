# EPLAN Beginner Projects

Five control circuits designed in EPLAN Electric P8. The first three are exported as single-page circuit diagrams (PDF); the fourth and fifth are more advanced circuits exported as their full multi-page schematics.

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

## 4. Lamp Sequence (`LampSequence.pdf`)

A single-pushbutton lamp sequencer built from nine relays, with no PLC involved.

- **S1** pulses one of five selector relays (**K1, K3, K5, K7, K9**), advancing the sequence by one step per press.
- Each selector relay hands off to a latching relay (**K2, K4, K6, K8**), which seals itself in through its own auxiliary contact and drives one lamp (**H1–H4**).
- Advancing to the next latching relay breaks the previous one's seal-in through a shared interlock contact, turning its lamp off automatically.
- The 5th press energizes **K9**, which drives no lamp — it only opens K8's latch, clearing the board and resetting the cycle.

A walking-ring counter — the same relay-only sequencing logic used in old telephone stepping switches and appliance program timers.

## 5. Elevator (`Elevator.pdf`)

A two-direction reversing-contactor hoist drive with PLC digital I/O, exported as its full multi-page schematic (title page, table of contents, single-line overview, power/control circuit, PLC inputs, PLC outputs).

- **S1 (Up)** and **S2 (Down)** each energize their contactor, **K1** or **K2**, through the *other* contactor's normally-closed interlock contact, plus **F1**'s thermal-overload aux contact.
- The interlock is electrical, not just logical: K1 and K2 physically cannot both be energized at once, so a reversal can never be forced by a stuck relay or a software fault.
- **S3 (Stop)** breaks the shared control bus feeding both directions.
- A second pole of S1/S2/S3 is wired into a dedicated PLC input page (**I0.0–I0.2**); two interposing relays, **K3**/**K4**, represent the PLC's digital outputs (**Q0.0/Q0.1**) that would drive the real contactors.

The cross-interlocked reversing-starter pattern from Door Motor, scaled up with the PLC I/O layer a real elevator controller adds on top of (never instead of) the hard-wired safety interlock.

---

Built with [EPLAN Electric P8](https://www.eplan.com/) as hands-on practice projects for learning relay logic and control-circuit fundamentals.
