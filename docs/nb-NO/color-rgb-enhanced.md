# Fargesensor RGB Utvidet — Brukerveiledning

Utvidet EV3-fargesensorblokk: rå RGB- og HSVL-kanaler pluss en RGB-basert sammenligningsmodus. På fanen **Sensor**.

## Konsept

Standardblokken gir kun 7 fargeslot og reflektert/omgivelseslys. Internt rapporterer sensoren R, G, B. Denne blokken eksponerer dem.

- **Mål – RGB** — les rå 0–255 R, G, B.
- **Mål – HSVL** — konverter RGB til fargetone (0–360°), metning, verdi, lyshet (0–100).
- **Sammenlikne – RGB** — sammenlikne med referanse-R/G/B med toleranse, returnerer boolsk.

## Moduser

| Modus | Innganger | Utganger |
|-------|-----------|----------|
| `ReadRGB` | Port | Rød, Grønn, Blå |
| `ReadHSV` | Port | Fargetone, Metning, Verdi, Lyshet |
| `DectRGB` | Port, R/G/B referanse, Toleranse | Rød, Grønn, Blå, Treff |

## Tips

- Kalibrer under faktisk belysning.
- Ved varierende belysning bruk **Normaliser**-modus i Fargeklassifisereren.

Original RGB-blokk: David Gilday. HSVL og Compare-RGB: OFDL.
