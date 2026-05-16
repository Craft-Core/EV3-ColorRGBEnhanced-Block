# Colour Classifier — Usage Guide

A distance-based colour classification block for the **Data Operations** palette. Teach the robot up to 8 reference colours and identify which one a live RGB reading is closest to.

## Concept

```
Normalise:  Rn = R / (R+G+B) × 100         (illumination invariant)
Setup ×8:   store one reference colour per slot
Distance:   D{n} = (R-Rn)² + (G-Gn)² + (B-Bn)² for each slot n=1..8
Identify:   BestColour = argmin(D1..D8); BestDistance = min(D1..D8)
```

## Usage

1. Call `Setup_C{n}` for n=1..8 at program start with each reference R, G, B.
2. In the main loop: read RGB → optional Normalise → Distance → Identify.

## Modes

| Mode | Category | Description |
|------|----------|-------------|
| `Normalise` | — | Divide each channel by R+G+B and scale to 100 |
| `Setup_C1`..`Setup_C8` | Setup | Store reference colour in slot n |
| `Distance` | — | Squared distance from input RGB to each of 8 stored colours |
| `Identify` | — | Pick closest stored colour, report index + distance |

## Tips

- 8 slots is the hard cap.
- BestDistance is squared distance — take sqrt for actual Euclidean distance.
- Identify always returns 1–8; check `BestDistance > threshold` for a "no match" outcome.
