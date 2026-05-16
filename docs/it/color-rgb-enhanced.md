# Sensore di colore RGB avanzato — Guida

Blocco esteso del sensore di colore EV3: canali RGB e HSVL grezzi e un modo di confronto RGB. Nella scheda **Sensore**.

## Concetto

Il blocco standard fornisce solo 7 colori e luce riflessa/ambiente. Internamente il sensore restituisce R, G, B. Questo blocco li espone.

- **Misurare – RGB** — leggere R, G, B grezzi (0–255).
- **Misurare – HSVL** — convertire in Tonalità (0–360°), Saturazione, Valore, Chiarezza.
- **Confrontare – RGB** — confrontare con R/G/B di riferimento con tolleranza, restituisce booleano.

## Modi

| Modo | Ingressi | Uscite |
|------|----------|--------|
| `ReadRGB` | Porta | Rosso, Verde, Blu |
| `ReadHSV` | Porta | Tonalità, Saturazione, Valore, Chiarezza |
| `DectRGB` | Porta, R/G/B riferimento, Tolleranza | Rosso, Verde, Blu, Corrisponde |

## Suggerimenti

- Calibrare con l'illuminazione reale.
- Con illuminazione variabile, usare il modo **Normalizzare** del Classificatore di colore.

Blocco RGB originale: David Gilday. HSVL e Compare-RGB: OFDL.
