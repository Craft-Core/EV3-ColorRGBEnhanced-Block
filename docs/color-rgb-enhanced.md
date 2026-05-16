# Color Sensor RGB Enhanced — Usage Guide

An extended EV3 color sensor block that exposes raw RGB and HSVL channels, plus an RGB-based comparison mode. Sits in the **Sensor** palette.

---

## Concept

The stock EV3-G color sensor block only exposes a 7-color slot and reflected/ambient light values. Internally the LEGO Color Sensor reports per-channel R, G, B intensities that are much richer. This block surfaces them.

- **Measure – RGB** — read the raw 0–255 Red, Green, Blue values.
- **Measure – HSVL** — convert the live RGB into Hue (0–360°), Saturation, Value, Lightness (0–100).
- **Compare – RGB** — given a reference R/G/B triple and a per-channel tolerance, return `true` when the live color is within range.

---

## Setup

Plug the EV3 Color Sensor into any input port. Default is port 3. The block auto-detects the sensor in EV3-G.

---

## Modes

| Mode | Inputs | Outputs |
|------|--------|---------|
| `ReadRGB` | Port | Red, Green, Blue |
| `ReadHSV` | Port | Hue, Saturation, Value, Lightness |
| `DectRGB` | Port, Red Reference, Green Reference, Blue Reference, Tolerance | Red, Green, Blue, Match (Boolean) |

---

## Typical usage

```
Loop:
  [ColorSensorRGB: ReadRGB → R, G, B]
  [Display R, G, B on brick screen]
```

For line-following or color-detecting robots, combine the RGB output with the **Color Classifier** block (Data Operations tab) for distance-based identification.

---

## Tips

- Calibrate by sampling each target color under your actual lighting conditions before relying on absolute RGB thresholds.
- If lighting changes a lot during a run, prefer the **Normalize** mode of Color Classifier rather than raw RGB.
- HSVL mode is convenient for hue-based detection (e.g., "is it red-ish?") because hue is more illumination-invariant than RGB.

---

## Credits

Original RGB block by David Gilday ([mindcuber's RGB Block](https://mindcuber.com/mindcub3r/mindcub3r.html#ColorSensorRGBBlock)). HSVL and Compare-RGB modes added by [OFDL](https://ofdl.tw/).
