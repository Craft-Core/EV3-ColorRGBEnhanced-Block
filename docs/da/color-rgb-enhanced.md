# Farvesensor RGB Udvidet — Vejledning

Udvidet EV3-farvesensorblok: rå RGB- og HSVL-kanaler plus RGB-baseret sammenligningstilstand. På fanen **Sensor**.

## Koncept

Standardblokken giver kun 7 farveslots og reflekteret/omgivende lys. Internt rapporterer sensoren R, G, B. Denne blok udstiller dem.

- **Mål – RGB** — læs rå 0–255 R, G, B.
- **Mål – HSVL** — konverter RGB til farvetone (0–360°), mætning, værdi, lyshed (0–100).
- **Sammenlign – RGB** — sammenlign med reference R/G/B med tolerance, returnerer boolsk.

## Tilstande

| Tilstand | Indgange | Udgange |
|----------|----------|---------|
| `ReadRGB` | Port | Rød, Grøn, Blå |
| `ReadHSV` | Port | Farvetone, Mætning, Værdi, Lyshed |
| `DectRGB` | Port, R/G/B reference, Tolerance | Rød, Grøn, Blå, Match |

## Tips

- Kalibrer under den faktiske belysning.
- Ved varierende belysning brug **Normaliser**-tilstanden i Farveklassificeringen.

Original RGB-blok: David Gilday. HSVL og Compare-RGB: OFDL.
