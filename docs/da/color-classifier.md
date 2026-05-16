# Farveklassificering — Vejledning

Afstandsbaseret farveklassificering til fanen **Datahandlinger**. Lær op til 8 referencefarver og identificer hvilken en live RGB-aflæsning er tættest på.

## Koncept

```
Normaliser:  Rn = R / (R+G+B) × 100   (belysningsuafhængig)
Setup ×8:    Gem én referencefarve per slot
Afstand:     For hver slot n: D{n} = (R-Rn)² + (G-Gn)² + (B-Bn)²
Identify:    BestColor = argmin(D1..D8); BestDistance = min(D1..D8)
```

## Brug

1. Ved programstart kald `Setup_C{n}` for n=1..8 med reference R, G, B.
2. Hovedløkke: læs RGB → Normaliser (valgfri) → Afstand → Identify.

## Tilstande

| Tilstand | Kategori | Beskrivelse |
|----------|----------|-------------|
| `Normalize` | — | Hver kanal / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | Opsætning | Gem referencefarve i slot n |
| `Distance` | — | Kvadreret afstand fra input-RGB til hver af 8 slots |
| `Identify` | — | Returnerer indeks og afstand for nærmeste farve |

## Tips

- Maks 8 slots.
- BestDistance er kvadreret. Tag kvadratrod for faktisk euklidisk afstand.
- Identify returnerer altid 1–8. Tjek `BestDistance > tærskel` for "intet match".
