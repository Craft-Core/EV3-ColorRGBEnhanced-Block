# Fargeklassifiserer — Brukerveiledning

Avstandsbasert fargeklassifisering for fanen **Dataoperasjoner**. Lær opptil 8 referansefarger og identifiser hvilken en live RGB-avlesning er nærmest.

## Konsept

```
Normaliser: Rn = R / (R+G+B) × 100   (lysuavhengig)
Setup ×8:   Lagre én referansefarge per slot
Avstand:    For hver slot n: D{n} = (R-Rn)² + (G-Gn)² + (B-Bn)²
Identify:   BestColor = argmin(D1..D8); BestDistance = min(D1..D8)
```

## Bruk

1. Ved programstart kall `Setup_C{n}` for n=1..8 med referanse R, G, B.
2. Hovedløkke: les RGB → Normaliser (valgfritt) → Avstand → Identify.

## Moduser

| Modus | Kategori | Beskrivelse |
|-------|----------|--------------|
| `Normalize` | — | Hver kanal / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | Oppsett | Lagre referansefarge i slot n |
| `Distance` | — | Kvadrert avstand fra input-RGB til hver av 8 slot |
| `Identify` | — | Returnerer indeks og avstand for nærmeste farge |

## Tips

- Maks 8 slot.
- BestDistance er kvadrert. Ta kvadratrot for faktisk euklidsk avstand.
- Identify returnerer alltid 1–8. Sjekk `BestDistance > terskel` for "ingen treff".
