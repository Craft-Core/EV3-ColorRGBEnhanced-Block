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
|---

## Fargeindeks

Blokken `Identifisere` returnerer et tall fra **1 til 8**. Tildelingen er fast:

| Indeks | Farge  | Standard R | Standard G | Standard B |
|--------|--------|------------|------------|------------|
| **1**  | Rød    | 255 | 0   | 0   |
| **2**  | Grønn  | 0   | 255 | 0   |
| **3**  | Blå    | 0   | 0   | 255 |
| **4**  | Gul    | 255 | 255 | 0   |
| **5**  | Hvit   | 255 | 255 | 255 |
| **6**  | Sort   | 0   | 0   | 0   |
| **7**  | Brun   | 128 | 64  | 0   |
| **8**  | Rosa   | 200 | 50  | 150 |

> **Viktig:** Standardverdiene er idealverdier. Ekte EV3-sensorer produserer mye lavere verdier. Mål hver farge med sensoren din og skriv inn disse verdiene i Setup-blokkene.
----|----------|--------------|
| `Normalize` | — | Hver kanal / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | Oppsett | Lagre referansefarge i slot n |
| `Distance` | — | Kvadrert avstand fra input-RGB til hver av 8 slot |
| `Identify` | — | Returnerer indeks og avstand for nærmeste farge |

## Tips

- Maks 8 slot.
- BestDistance er kvadrert. Ta kvadratrot for faktisk euklidsk avstand.
- Identify returnerer alltid 1–8. Sjekk `BestDistance > terskel` for "ingen treff".
