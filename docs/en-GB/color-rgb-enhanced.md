# Colour Sensor RGB Enhanced — Usage Guide

An extended EV3 colour sensor block that exposes raw RGB and HSVL channels, plus an RGB-based comparison mode. Sits in the **Sensor** palette.

---

## Concept

The stock EV3-G colour sensor block only exposes a 7-colour slot and reflected/ambient light values. Internally the LEGO Colour Sensor reports per-channel R, G, B intensities. This block surfaces them.

- **Measure – RGB** — read the raw 0–255 Red, Green, Blue values.
- **Measure – HSVL** — convert the live RGB into Hue (0–360°), Saturation, Value, Lightness (0–100).
- **Compare – RGB** — given a reference R/G/B triple and a per-channel tolerance, return `true` when the live colour is within range.

---

## Modes

| Mode | Inputs | Outputs |
|------|--------|---------|
| `ReadRGB` | Port | Red, Green, Blue |
| `ReadHSV` | Port | Hue, Saturation, Value, Lightness |
| `DectRGB` | Port, Red/Green/Blue Reference, Tolerance | Red, Green, Blue, Match (Boolean) |

---

## Tips

- Calibrate by sampling each target colour under your actual lighting conditions before relying on absolute RGB thresholds.
- For lighting that changes during a run, prefer the **Normalise** mode of Colour Classifier rather than raw RGB.

Original RGB block by David Gilday. HSVL and Compare-RGB modes added by OFDL.
