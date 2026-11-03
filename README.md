# Overload Elevator

An interactive simulator of a single elevator car with a load cell under the floor. It shows how real elevators protect themselves when they get too heavy.

**Live demo:** https://lazaridoue.github.io/elevator-overload-sim/

## What it does

The controller reads the car's total weight and switches between three modes:

| Load | Mode | Doors | Car |
|---|---|---|---|
| under 80% | Normal | Open at every call | Moves normally |
| 80–100% | Full-load bypass | Stay shut for hall calls; open only where riders get off | Passes floors where people are waiting |
| over 100% | Overload | Held open | Won't leave. Buzzer and OVERLOAD light until someone steps off |

The elevator can't weigh someone before they step in. So when the car goes over its rated load, the doors stay open instead of closing, and the car refuses to move until the last person steps back out.

## Try it

- Add riders with a starting floor, destination and weight
- Drop a crowd of 5 on a random floor
- Switch the rated load between 450, 630 and 1000 kg cars
- Move the full-load bypass threshold between 60% and 95%
- Read the controller log to see why the car made each decision

The demo starts with 7 people (650 kg) waiting for a 630 kg car, so the overload behavior shows up right away.

## Run locally

It's a single HTML file with no build step. Open `index.html` in a browser.

## Next steps

- Move the controller logic into a tested Python state machine
- Add load-cell noise filtering and hysteresis around the thresholds
- Simulate a busy building to compare bypass thresholds by wait time and throughput
- Build a desk-sized model with an ESP32, an HX711 load cell, a servo door and a buzzer
