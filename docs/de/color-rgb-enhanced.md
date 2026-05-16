# Farbsensor RGB Erweitert — Anleitung

Ein erweiterter EV3-Farbsensor-Block, der rohe RGB- und HSVL-Kanäle sowie einen RGB-basierten Vergleichsmodus bereitstellt. In der Palette **Sensor**.

## Konzept

Der Standard-EV3-Farbsensor liefert nur 7 Farbslots und Licht-Reflexion/-Umgebung. Intern liefert er R, G, B-Intensitäten. Dieser Block macht sie zugänglich.

- **Messen – RGB** — rohe 0–255 Rot, Grün, Blau lesen.
- **Messen – HSVL** — RGB in Farbton (0–360°), Sättigung, Wert, Helligkeit (0–100) umwandeln.
- **Vergleichen – RGB** — gegen Referenz-R/G/B mit Toleranz vergleichen, `true` bei Treffer.

## Modi

| Modus | Eingänge | Ausgänge |
|-------|----------|----------|
| `ReadRGB` | Port | Rot, Grün, Blau |
| `ReadHSV` | Port | Farbton, Sättigung, Wert, Helligkeit |
| `DectRGB` | Port, R/G/B-Referenz, Toleranz | Rot, Grün, Blau, Treffer (Boolean) |

## Tipps

- Kalibrieren Sie unter realistischen Lichtbedingungen.
- Bei wechselndem Licht den **Normieren**-Modus des Farb-Klassifikators bevorzugen.

Original-RGB-Block: David Gilday. HSVL und Compare-RGB: OFDL.
