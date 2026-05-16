# Kleursensor RGB Verbeterd — Handleiding

Uitgebreid EV3-kleursensorblok: ruwe RGB- en HSVL-kanalen plus een RGB-vergelijkingsmodus. In het tabblad **Sensor**.

## Concept

Het standaardblok geeft slechts 7 kleuren en gereflecteerd/omgevingslicht. Intern levert de sensor R, G, B. Dit blok stelt die beschikbaar.

- **Meten – RGB** — lees ruwe R, G, B (0–255).
- **Meten – HSVL** — converteer naar Tint (0–360°), Verzadiging, Waarde, Lichtheid.
- **Vergelijken – RGB** — vergelijk met R/G/B-referentie met tolerantie, retourneert boolean.

## Modi

| Modus | Ingangen | Uitgangen |
|-------|----------|-----------|
| `ReadRGB` | Poort | Rood, Groen, Blauw |
| `ReadHSV` | Poort | Tint, Verzadiging, Waarde, Lichtheid |
| `DectRGB` | Poort, R/G/B referentie, Tolerantie | Rood, Groen, Blauw, Komt overeen |

## Tips

- Kalibreer onder werkelijke verlichting.
- Bij wisselende verlichting: gebruik de **Normaliseren**-modus van de Kleurclassificator.

Origineel RGB-blok: David Gilday. HSVL en Compare-RGB: OFDL.
