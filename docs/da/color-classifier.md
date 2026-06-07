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
|---

## Farveindeks

Blokken `Identificere` returnerer et tal fra **1 til 8**. Tildelingen er fast:

| Indeks | Farve  | Standard R | Standard G | Standard B |
|--------|--------|------------|------------|------------|
| **1**  | Rød    | 255 | 0   | 0   |
| **2**  | Grøn   | 0   | 255 | 0   |
| **3**  | Blå    | 0   | 0   | 255 |
| **4**  | Gul    | 255 | 255 | 0   |
| **5**  | Hvid   | 255 | 255 | 255 |
| **6**  | Sort   | 0   | 0   | 0   |
| **7**  | Brun   | 128 | 64  | 0   |
| **8**  | Pink   | 200 | 50  | 150 |

> **Vigtigt:** Standardværdierne er idealværdier. Rigtige EV3-sensorer producerer meget lavere værdier. Mål hver farve med din sensor og indtast disse værdier i Setup-blokkene.
-------|----------|-------------|
| `Normalize` | — | Hver kanal / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | Opsætning | Gem referencefarve i slot n |
| `Distance` | — | Kvadreret afstand fra input-RGB til hver af 8 slots |
| `Identify` | — | Returnerer indeks og afstand for nærmeste farve |

## Tips

- Maks 8 slots.
- BestDistance er kvadreret. Tag kvadratrod for faktisk euklidisk afstand.
- Identify returnerer altid 1–8. Tjek `BestDistance > tærskel` for "intet match".
