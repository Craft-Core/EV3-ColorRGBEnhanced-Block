# Color Classifier — Usage Guide

A distance-based color classification block for the **Data Operations** palette. Lets you teach the robot up to 8 reference colors and then identify which one a live RGB reading is closest to.

---

## Concept

---

## Color Index

`Identify` returns a number **1–8**. The fixed assignment is:

| Index | Color  | Default R | Default G | Default B |
|-------|--------|-----------|-----------|-----------|
| **1** | Red    | 255 | 0   | 0   |
| **2** | Green  | 0   | 255 | 0   |
| **3** | Blue   | 0   | 0   | 255 |
| **4** | Yellow | 255 | 255 | 0   |
| **5** | White  | 255 | 255 | 255 |
| **6** | Black  | 0   | 0   | 0   |
| **7** | Brown  | 128 | 64  | 0   |
| **8** | Pink   | 200 | 50  | 150 |

> **Important:** The default values above are ideal values. Real EV3 sensors produce much lower numbers. Always measure each color with your sensor and enter those values in the Setup blocks.


```
Normalize:  Rn = R / (R+G+B) × 100         (illumination invariant)
            Gn = G / (R+G+B) × 100
            Bn = B / (R+G+B) × 100

Setup (×8): store one reference color per slot
            OFDLCC_C{n}_R = Ref_R     (n = 1..8)
            OFDLCC_C{n}_G = Ref_G
            OFDLCC_C{n}_B = Ref_B

Distance:   for each slot n,
            D{n} = (R - OFDLCC_C{n}_R)² + (G - OFDLCC_C{n}_G)² + (B - OFDLCC_C{n}_B)²

Identify:   BestColor    = argmin(D1..D8)         (returns 1..8)
            BestDistance = min(D1..D8)            (the squared distance value)
```

`Distance` outputs **squared** Euclidean distance — order-preserving, faster, and exactly what `Identify` needs to pick the closest color.

---

## Setup

### Step 1 — call `Setup_Cn` once per slot at program start

For each color you want to recognize, drop a `Setup_C{n}` block (n = 1..8) into the initialization phase of your program and wire in its reference R, G, B values.

| Parameter | Description |
|-----------|-------------|
| **Reference R** | Red value (0–255) of this preset color |
| **Reference G** | Green value (0–255) of this preset color |
| **Reference B** | Blue value (0–255) of this preset color |

Use the **Measure – RGB color** block from the Color Sensor RGB Enhanced block to *capture* the reference RGB for each color while pointing the sensor at a printed swatch — then hard-code those numbers into the Setup blocks.

### Step 2 — in the main loop, chain Normalize → Distance → Identify

| Block | Wires in | Wires out |
|-------|----------|-----------|
| **Normalize** (optional) | R, G, B from sensor | Rn, Gn, Bn |
| **Distance** | R, G, B (raw or normalized) | D1..D8 |
| **Identify** | D1..D8 from Distance | BestColor, BestDistance |

---

## Modes

| Mode | Category | Description |
|------|----------|-------------|
| `Normalize` | — | Divide each channel by R+G+B and scale to 100. Strips brightness, keeps hue. |
| `Setup_C1` | Setup | Store reference color in slot 1 |
| `Setup_C2` | Setup | Store reference color in slot 2 |
| `Setup_C3` | Setup | Store reference color in slot 3 |
| `Setup_C4` | Setup | Store reference color in slot 4 |
| `Setup_C5` | Setup | Store reference color in slot 5 |
| `Setup_C6` | Setup | Store reference color in slot 6 |
| `Setup_C7` | Setup | Store reference color in slot 7 |
| `Setup_C8` | Setup | Store reference color in slot 8 |
| `Distance` | — | Compute squared distance from input RGB to each of the 8 stored colors |
| `Identify` | — | Pick the closest stored color and report its index + distance |

---

## Typical program structure

```
[Setup_C1: 255, 0,   0  ]   ← red
[Setup_C2: 0,   255, 0  ]   ← green
[Setup_C3: 0,   0,   255]   ← blue
[Setup_C4: 255, 255, 0  ]   ← yellow
[Setup_C5: 255, 255, 255]   ← white
[Setup_C6: 0,   0,   0  ]   ← black
[Setup_C7: 128, 64,  0  ]   ← brown
[Setup_C8: 200, 50,  150]   ← pink

Loop:
  [ColorSensorRGB ReadRGB → R, G, B]
  [Normalize: R, G, B → Rn, Gn, Bn]      (optional)
  [Distance:  Rn,Gn,Bn → D1..D8]
  [Identify:  D1..D8 → BestColor, BestDistance]
  [Switch on BestColor: 1=red, 2=green, ...]
```

If you don't need illumination invariance, skip Normalize and wire raw RGB straight into Distance — but make sure your Setup values were captured under the same lighting.

---

## Tips

- **8 slots is the hard cap.** The block stores 8 × 3 = 24 named globals (`OFDLCC_C1_R` ... `OFDLCC_C8_B`). If you need more colors, you'll need to fork the block.
- **Capture reference colors with the same sensor that will read them at run time.** Different EV3 color sensors have noticeable per-unit variation.
- **BestDistance is squared distance.** Take its square root in a Math block if you want the actual Euclidean distance (e.g., for a confidence threshold).
- **Use Normalize when lighting changes during a run.** It removes the brightness component but loses absolute intensity — so dark gray and dark blue may collide. Test both modes for your specific palette.
- **Identify always returns a value from 1 to 8** — it doesn't refuse to classify. Add a `BestDistance > threshold` check downstream if you need a "no match" outcome.

---

## Internal storage

| Slot | Globals |
|------|---------|
| 1 | `OFDLCC_C1_R`, `OFDLCC_C1_G`, `OFDLCC_C1_B` |
| 2 | `OFDLCC_C2_R`, `OFDLCC_C2_G`, `OFDLCC_C2_B` |
| ... | ... |
| 8 | `OFDLCC_C8_R`, `OFDLCC_C8_G`, `OFDLCC_C8_B` |

These persist across the entire program run but are wiped at brick reboot, so re-run Setup on every program start.
