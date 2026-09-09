# EPLAN Beginner Projects

Four control circuits designed in EPLAN Electric P8. The first three are exported as single-page circuit diagrams (PDF); the fourth is a more advanced circuit exported as its full multi-page schematic (title page, table of contents, and circuit page).

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

A single-pushbutton lamp sequencer built entirely from relays — a walking-ring counter with no PLC and no electronics. Noticeably more advanced than the three circuits above.

- **S1** pulses one of five "selector" relays (**K1, K3, K5, K7, K9**) on each press — but only the selector for the *next* state can actually pick up, because each one's coil runs through the normally-closed contacts of every other currently-active relay.
- Each selector hands off to a "latching" relay (**K2, K4, K6, K8**), which seals itself in through its own auxiliary contact and drives one lamp (**H1–H4**).
- Advancing to a new latching relay automatically breaks the *previous* one's seal-in, through a shared interlock contact — nothing has to actively switch the old lamp off.
- The 5th press energizes **K9**, which drives no lamp of its own — its only job is to open K8's latch, clearing the board and resetting the cycle.

This is the same principle behind pre-electronic telephone stepping switches, appliance program timers, and chaser lighting — and the direct hardware ancestor of every PLC step-sequencer instruction in use today.

---

Built with [EPLAN Electric P8](https://www.eplan.com/) as hands-on practice projects for learning relay logic and control-circuit fundamentals.
