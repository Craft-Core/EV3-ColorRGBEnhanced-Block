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
|---

## Kleurindex

Het blok `Identificeren` geeft een getal van **1 tot 8** terug. De toewijzing is vast:

| Index | Kleur  | Standaard R | Standaard G | Standaard B |
|-------|--------|-------------|-------------|-------------|
| **1** | Rood   | 255 | 0   | 0   |
| **2** | Groen  | 0   | 255 | 0   |
| **3** | Blauw  | 0   | 0   | 255 |
| **4** | Geel   | 255 | 255 | 0   |
| **5** | Wit    | 255 | 255 | 255 |
| **6** | Zwart  | 0   | 0   | 0   |
| **7** | Bruin  | 128 | 64  | 0   |
| **8** | Roze   | 200 | 50  | 150 |

> **Belangrijk:** De standaardwaarden zijn ideale waarden. Echte EV3-sensoren produceren veel lagere waarden. Meet elke kleur met uw sensor en voer die waarden in de Setup-blokken in.
----|-----------|--------------|
| `Normalize` | — | Elk kanaal / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | Instellen | Sla referentiekleur op in slot n |
| `Distance` | — | Kwadratische afstand van invoer-RGB tot elk van 8 slots |
| `Identify` | — | Geeft index en afstand van dichtstbijzijnde kleur |

## Tips

- 8 slots is het maximum.
- BestDistance is kwadratisch. Neem wortel voor werkelijke Euclidische afstand.
- Identify retourneert altijd 1–8. Check `BestDistance > drempel` voor "geen match".
