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
|------|----------|-------------|
| `Normalize` | — | Varje kanal / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | Konfigurera | Spara referensfärg i plats n |
| `Distance` | — | Kvadrerat avstånd från in-RGB till var och en av 8 platser |
| `Identify` | — | Returnerar index och avstånd för närmsta färg |

## Tips

- Max 8 platser.
- BestDistance är kvadrerat. Ta roten ur för faktiskt Euklidiskt avstånd.
- Identify returnerar alltid 1–8. Kontrollera `BestDistance > tröskel` för "ingen träff".
