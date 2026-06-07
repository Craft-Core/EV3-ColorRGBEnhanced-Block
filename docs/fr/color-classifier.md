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
|---

## Index des couleurs

Le bloc `Identifier` retourne un nombre de **1 à 8**. L'affectation est fixe :

| Index | Couleur | R par défaut | G par défaut | B par défaut |
|-------|---------|--------------|--------------|--------------|
| **1** | Rouge   | 255 | 0   | 0   |
| **2** | Vert    | 0   | 255 | 0   |
| **3** | Bleu    | 0   | 0   | 255 |
| **4** | Jaune   | 255 | 255 | 0   |
| **5** | Blanc   | 255 | 255 | 255 |
| **6** | Noir    | 0   | 0   | 0   |
| **7** | Marron  | 128 | 64  | 0   |
| **8** | Rose    | 200 | 50  | 150 |

> **Important :** Les valeurs par défaut sont des valeurs idéales. Les vrais capteurs EV3 produisent des valeurs beaucoup plus faibles. Mesurez chaque couleur avec votre capteur et entrez ces valeurs dans les blocs Setup.
---|-----------|-------------|
| `Normalize` | — | Chaque canal / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | Configuration | Stocker la couleur de référence à l'emplacement n |
| `Distance` | — | Distance au carré du RGB d'entrée à chacun des 8 emplacements |
| `Identify` | — | Renvoie l'indice et la distance de la couleur la plus proche |

## Conseils

- 8 emplacements maximum.
- BestDistance est au carré. Prenez la racine pour la distance euclidienne réelle.
- Identify renvoie toujours 1–8. Vérifiez `BestDistance > seuil` pour "pas de match".
