# Capteur de couleur RGB amélioré — Guide

Bloc capteur de couleur EV3 étendu : canaux RGB bruts, HSVL et un mode de comparaison RGB. Onglet **Capteur**.

## Concept

Le bloc standard ne donne que 7 couleurs et la lumière réfléchie/ambiante. En interne le capteur fournit R, G, B. Ce bloc les expose.

- **Mesurer – RGB** — lire les R, G, B bruts (0–255).
- **Mesurer – HSVL** — convertir en Teinte (0–360°), Saturation, Valeur, Luminosité.
- **Comparer – RGB** — comparer à R/G/B de référence avec tolérance, retourne booléen.

## Modes

| Mode | Entrées | Sorties |
|------|---------|---------|
| `ReadRGB` | Port | Rouge, Vert, Bleu |
| `ReadHSV` | Port | Teinte, Saturation, Valeur, Luminosité |
| `DectRGB` | Port, R/G/B référence, Tolérance | Rouge, Vert, Bleu, Correspondance |

## Conseils

- Calibrez sous l'éclairage réel.
- Sous éclairage variable, utilisez le mode **Normaliser** du Classificateur de couleurs.

Bloc RGB original : David Gilday. HSVL et Compare-RGB : OFDL.
