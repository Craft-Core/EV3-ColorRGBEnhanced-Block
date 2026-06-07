# Färgklassificerare — Användarguide

Avståndsbaserad färgklassificering för fliken **Dataåtgärder**. Lär in upp till 8 referensfärger och identifiera vilken en live RGB-avläsning ligger närmast.

## Koncept

```
Normalisera: Rn = R / (R+G+B) × 100   (ljusinvariant)
Setup ×8:    Spara en referensfärg per plats
Avstånd:     För varje plats n: D{n} = (R-Rn)² + (G-Gn)² + (B-Bn)²
Identify:    BestColor = argmin(D1..D8); BestDistance = min(D1..D8)
```

## Användning

1. Vid programstart anropa `Setup_C{n}` för n=1..8 med referens R, G, B.
2. Huvudloop: läs RGB → Normalisera (valfritt) → Avstånd → Identify.

## Lägen

| Läge | Kategori | Beskrivning |
|---

## Färgindex

Blocket `Identifiera` returnerar ett tal från **1 till 8**. Tilldelningen är fast:

| Index | Färg   | Standard R | Standard G | Standard B |
|-------|--------|------------|------------|------------|
| **1** | Röd    | 255 | 0   | 0   |
| **2** | Grön   | 0   | 255 | 0   |
| **3** | Blå    | 0   | 0   | 255 |
| **4** | Gul    | 255 | 255 | 0   |
| **5** | Vit    | 255 | 255 | 255 |
| **6** | Svart  | 0   | 0   | 0   |
| **7** | Brun   | 128 | 64  | 0   |
| **8** | Rosa   | 200 | 50  | 150 |

> **Viktigt:** Standardvärdena är idealvärden. Riktiga EV3-sensorer producerar mycket lägre värden. Mät varje färg med din sensor och ange dessa värden i Setup-blocken.
---|----------|-------------|
| `Normalize` | — | Varje kanal / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | Konfigurera | Spara referensfärg i plats n |
| `Distance` | — | Kvadrerat avstånd från in-RGB till var och en av 8 platser |
| `Identify` | — | Returnerar index och avstånd för närmsta färg |

## Tips

- Max 8 platser.
- BestDistance är kvadrerat. Ta roten ur för faktiskt Euklidiskt avstånd.
- Identify returnerar alltid 1–8. Kontrollera `BestDistance > tröskel` för "ingen träff".
