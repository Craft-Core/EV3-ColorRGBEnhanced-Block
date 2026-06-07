# EV3-ColorRGBEnhanced-Block

> An extended, multi-language fork of [EV3-ColorRGBEnhanced-Block](https://github.com/a10036gt/EV3-ColorRGBEnhanced-Block) — adding a distance-based **Color Classifier** in the Data Operations tab so your EV3 robot can tell colors apart even under changing light.

![EV3 Color RGB Enhanced overview](https://ofdl.tw/wp-content/uploads/2019/04/EV3_RGBAdv_OFDL.jpg)

## What is this?

The stock EV3 color sensor only distinguishes 7 named colors and exposes reflected/ambient light. For competitive WRO / FLL robots you want **raw RGB**, **illumination-invariant ratios**, and a way to **classify against your own color palette**. This project bundles all of that:

- Original **Color Sensor RGB Enhanced** block (Sensor tab) — surfaces raw R/G/B, HSVL, and a tolerance-based comparator.
- New **Color Classifier** block (Data Operations tab) — normalize, define up to 8 reference colors, compute distances, pick the closest match.

All UI strings are localized into 15 languages.

---

## Blocks Included

### Original block (by [OFDL / a10036gt](https://github.com/a10036gt/EV3-ColorRGBEnhanced-Block))

| Block | Modes | Description |
| ----- | ----- | ----------- |
| **Color Sensor RGB Enhanced** | ReadRGB, ReadHSV, DectRGB | Raw RGB / HSVL output and RGB-tolerance comparator for the LEGO Color Sensor |

### Added in this fork

| Block | Modes | Description |
| ----- | ----- | ----------- |
| **Color Classifier** | Normalize, Setup_C1..C8, Distance, Identify | Distance-based color classification: teach 8 reference colors then identify which one is closest to a live RGB reading |

---

## Color Index (Identify block output)

The `Identify` block outputs a number **1–8** that maps to these colors:

| # | Color  | Default R | Default G | Default B |
|---|--------|-----------|-----------|-----------|
| 1 | Red    | 255 | 0   | 0   |
| 2 | Green  | 0   | 255 | 0   |
| 3 | Blue   | 0   | 0   | 255 |
| 4 | Yellow | 255 | 255 | 0   |
| 5 | White  | 255 | 255 | 255 |
| 6 | Black  | 0   | 0   | 0   |
| 7 | Brown  | 128 | 64  | 0   |
| 8 | Pink   | 200 | 50  | 150 |

> Default values are ideal — always calibrate with your actual sensor readings.

---

## Usage Guides

Detailed documentation for each block (primary language: English):

| Block | en-US | en-GB | ja | de | fr | es | it | nl | pt | ru | ko | zh-Hans | da | nb-NO | sv |
| ----- | ----- | ----- | -- | -- | -- | -- | -- | -- | -- | -- | -- | ------- | -- | ----- | -- |
| **Color Sensor RGB Enhanced** | [EN](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/color-rgb-enhanced.md) | [en-GB](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/en-GB/color-rgb-enhanced.md) | [ja](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/ja/color-rgb-enhanced.md) | [de](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/de/color-rgb-enhanced.md) | [fr](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/fr/color-rgb-enhanced.md) | [es](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/es/color-rgb-enhanced.md) | [it](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/it/color-rgb-enhanced.md) | [nl](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/nl/color-rgb-enhanced.md) | [pt](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/pt/color-rgb-enhanced.md) | [ru](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/ru/color-rgb-enhanced.md) | [ko](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/ko/color-rgb-enhanced.md) | [zh-Hans](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/zh-Hans/color-rgb-enhanced.md) | [da](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/da/color-rgb-enhanced.md) | [nb-NO](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/nb-NO/color-rgb-enhanced.md) | [sv](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/sv/color-rgb-enhanced.md) |
| **Color Classifier** | [EN](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/color-classifier.md) | [en-GB](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/en-GB/color-classifier.md) | [ja](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/ja/color-classifier.md) | [de](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/de/color-classifier.md) | [fr](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/fr/color-classifier.md) | [es](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/es/color-classifier.md) | [it](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/it/color-classifier.md) | [nl](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/nl/color-classifier.md) | [pt](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/pt/color-classifier.md) | [ru](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/ru/color-classifier.md) | [ko](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/ko/color-classifier.md) | [zh-Hans](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/zh-Hans/color-classifier.md) | [da](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/da/color-classifier.md) | [nb-NO](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/nb-NO/color-classifier.md) | [sv](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/blob/master/docs/sv/color-classifier.md) |

---

## Multi-Language Support

All blocks are fully localized for 15 languages:

| Language | Folder |
| -------- | ------ |
| English (US) | en-US |
| English (GB) | en-GB |
| Japanese (日本語) | ja |
| German (Deutsch) | de |
| French (Français) | fr |
| Spanish (Español) | es |
| Italian (Italiano) | it |
| Dutch (Nederlands) | nl |
| Portuguese (Português) | pt |
| Russian (Русский) | ru |
| Korean (한국어) | ko |
| Simplified Chinese (简体中文) | zh-Hans |
| Danish (Dansk) | da |
| Norwegian (Norsk) | nb-NO |
| Swedish (Svenska) | sv |

Translations are AI-assisted — PRs to refine wording in any locale are very welcome.

---

## Installation

1. Download the latest `.ev3b` file from the [Releases page](https://github.com/Craft-Core/EV3-ColorRGBEnhanced-Block/releases/).
2. In EV3-G: **Tools → Block Import** → select the `.ev3b` file → Import → restart EV3-G.

Or install manually by copying the entire repo folder into:

```
C:\Program Files (x86)\LEGO Software\LEGO MINDSTORMS Edu EV3\Resources\Blocks\
```

(needs Administrator rights).

---

## Credits

- Original block: **OFDL / a10036gt** — <https://github.com/a10036gt/EV3-ColorRGBEnhanced-Block>
- Original RGB block: **David Gilday** ([mindcuber's RGB Block](https://mindcuber.com/mindcub3r/mindcub3r.html#ColorSensorRGBBlock))
- Original user guide (繁體中文): <https://ofdl.tw/ev3-hack/ev3-color-sensor-enhanced-block/>
- Original user guide (English): <https://ofdl.tw/en/ev3-hacking/ev3-color-sensor-adv-block/>
