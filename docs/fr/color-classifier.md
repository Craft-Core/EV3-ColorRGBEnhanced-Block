# Classificateur de couleurs — Guide

Classification de couleurs par distance pour l'onglet **Opérations sur les données**. Apprenez jusqu'à 8 couleurs de référence et identifiez celle dont une lecture RGB est la plus proche.

## Concept

```
Normaliser : Rn = R / (R+G+B) × 100   (invariant à l'éclairage)
Setup ×8 :   Stocker une couleur de référence par emplacement
Distance :   Pour chaque emplacement n : D{n} = (R-Rn)² + (G-Gn)² + (B-Bn)²
Identifier : BestColor = argmin(D1..D8); BestDistance = min(D1..D8)
```

## Utilisation

1. Au démarrage, appeler `Setup_C{n}` pour n=1..8 avec les R, G, B de référence.
2. Boucle principale : lire RGB → Normaliser (optionnel) → Distance → Identifier.

## Modes

| Mode | Catégorie | Description |
|------|-----------|-------------|
| `Normalize` | — | Chaque canal / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | Configuration | Stocker la couleur de référence à l'emplacement n |
| `Distance` | — | Distance au carré du RGB d'entrée à chacun des 8 emplacements |
| `Identify` | — | Renvoie l'indice et la distance de la couleur la plus proche |

## Conseils

- 8 emplacements maximum.
- BestDistance est au carré. Prenez la racine pour la distance euclidienne réelle.
- Identify renvoie toujours 1–8. Vérifiez `BestDistance > seuil` pour "pas de match".
