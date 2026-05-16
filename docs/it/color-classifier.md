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
|------|-----------|-------------|
| `Normalize` | — | Ogni canale / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | Impostazione | Memorizza colore di riferimento nello slot n |
| `Distance` | — | Distanza al quadrato dall'RGB di ingresso a ciascuno dei 8 slot |
| `Identify` | — | Restituisce indice e distanza del colore più vicino |

## Suggerimenti

- 8 slot al massimo.
- BestDistance è al quadrato. Estrarre la radice per la distanza euclidea reale.
- Identify restituisce sempre 1–8. Controllare `BestDistance > soglia` per "nessuna corrispondenza".
