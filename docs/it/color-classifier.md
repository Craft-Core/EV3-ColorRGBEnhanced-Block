# Classificatore di colore — Guida

Classificazione di colore basata sulla distanza per la scheda **Operazioni sui dati**. Insegnate fino a 8 colori di riferimento e identificate quale è più vicino a una lettura RGB in tempo reale.

## Concetto

```
Normalizzare: Rn = R / (R+G+B) × 100  (invariante alla luminosità)
Setup ×8:     Memorizza un colore di riferimento per slot
Distanza:     Per ogni slot n: D{n} = (R-Rn)² + (G-Gn)² + (B-Bn)²
Identifica:   BestColor = argmin(D1..D8); BestDistance = min(D1..D8)
```

## Uso

1. All'avvio, chiamare `Setup_C{n}` per n=1..8 con i R, G, B di riferimento.
2. Ciclo principale: leggere RGB → Normalizzare (opzionale) → Distanza → Identifica.

## Modi

| Modo | Categoria | Descrizione |
|---

## Indice dei colori

Il blocco `Identificare` restituisce un numero da **1 a 8**. L'assegnazione è fissa:

| Indice | Colore  | R predefinito | G predefinito | B predefinito |
|--------|---------|---------------|---------------|---------------|
| **1**  | Rosso   | 255 | 0   | 0   |
| **2**  | Verde   | 0   | 255 | 0   |
| **3**  | Blu     | 0   | 0   | 255 |
| **4**  | Giallo  | 255 | 255 | 0   |
| **5**  | Bianco  | 255 | 255 | 255 |
| **6**  | Nero    | 0   | 0   | 0   |
| **7**  | Marrone | 128 | 64  | 0   |
| **8**  | Rosa    | 200 | 50  | 150 |

> **Importante:** I valori predefiniti sono valori ideali. I sensori EV3 reali producono valori molto più bassi. Misurare ogni colore con il proprio sensore e inserire quei valori nei blocchi Setup.
---|-----------|-------------|
| `Normalize` | — | Ogni canale / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | Impostazione | Memorizza colore di riferimento nello slot n |
| `Distance` | — | Distanza al quadrato dall'RGB di ingresso a ciascuno dei 8 slot |
| `Identify` | — | Restituisce indice e distanza del colore più vicino |

## Suggerimenti

- 8 slot al massimo.
- BestDistance è al quadrato. Estrarre la radice per la distanza euclidea reale.
- Identify restituisce sempre 1–8. Controllare `BestDistance > soglia` per "nessuna corrispondenza".
