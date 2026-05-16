# Kleurclassificator — Handleiding

Op afstand gebaseerde kleurclassificatie voor het tabblad **Gegevensbewerkingen**. Leer maximaal 8 referentiekleuren en identificeer welke het dichtst bij een live RGB-lezing ligt.

## Concept

```
Normaliseren: Rn = R / (R+G+B) × 100  (verlichtingsinvariant)
Setup ×8:     Sla per slot één referentiekleur op
Afstand:      Voor elke slot n: D{n} = (R-Rn)² + (G-Gn)² + (B-Bn)²
Identify:     BestColor = argmin(D1..D8); BestDistance = min(D1..D8)
```

## Gebruik

1. Bij programmastart `Setup_C{n}` aanroepen voor n=1..8 met referentie R, G, B.
2. Hoofdlus: RGB lezen → Normaliseren (optioneel) → Afstand → Identify.

## Modi

| Modus | Categorie | Beschrijving |
|-------|-----------|--------------|
| `Normalize` | — | Elk kanaal / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | Instellen | Sla referentiekleur op in slot n |
| `Distance` | — | Kwadratische afstand van invoer-RGB tot elk van 8 slots |
| `Identify` | — | Geeft index en afstand van dichtstbijzijnde kleur |

## Tips

- 8 slots is het maximum.
- BestDistance is kwadratisch. Neem wortel voor werkelijke Euclidische afstand.
- Identify retourneert altijd 1–8. Check `BestDistance > drempel` voor "geen match".
