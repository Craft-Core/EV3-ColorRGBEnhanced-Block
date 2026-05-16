# Färgsensor RGB Utvidgad — Användarguide

Utvidgad EV3-färgsensorblock: råa RGB- och HSVL-kanaler plus ett RGB-baserat jämförelseläge. På fliken **Sensor**.

## Koncept

Standardblocket ger bara 7 färgplatser och reflekterat/omgivande ljus. Internt rapporterar sensorn R, G, B. Detta block exponerar dem.

- **Mät – RGB** — läs råa 0–255 R, G, B.
- **Mät – HSVL** — konvertera RGB till nyans (0–360°), mättnad, värde, ljushet (0–100).
- **Jämför – RGB** — jämför mot referens R/G/B med tolerans, returnerar booleskt.

## Lägen

| Läge | Ingångar | Utgångar |
|------|----------|----------|
| `ReadRGB` | Port | Röd, Grön, Blå |
| `ReadHSV` | Port | Nyans, Mättnad, Värde, Ljushet |
| `DectRGB` | Port, R/G/B referens, Tolerans | Röd, Grön, Blå, Träff |

## Tips

- Kalibrera under faktisk belysning.
- Vid varierande belysning använd **Normalisera**-läget i Färgklassificeraren.

Original RGB-block: David Gilday. HSVL och Compare-RGB: OFDL.
