# Clasificador de color — Guía

Clasificación de color basada en distancia para la pestaña **Operaciones de datos**. Enseñe hasta 8 colores de referencia e identifique cuál es el más cercano a una lectura RGB en vivo.

## Concepto

```
Normalizar: Rn = R / (R+G+B) × 100   (invariante a iluminación)
Setup ×8:   Almacenar un color de referencia por ranura
Distancia:  Para cada ranura n: D{n} = (R-Rn)² + (G-Gn)² + (B-Bn)²
Identificar: BestColor = argmin(D1..D8); BestDistance = min(D1..D8)
```

## Uso

1. Al iniciar, llame `Setup_C{n}` para n=1..8 con los R, G, B de referencia.
2. Bucle principal: leer RGB → Normalizar (opcional) → Distancia → Identificar.

## Modos

| Modo | Categoría | Descripción |
|------|-----------|-------------|
| `Normalize` | — | Cada canal / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | Configurar | Almacena color de referencia en ranura n |
| `Distance` | — | Distancia al cuadrado desde RGB de entrada a cada una de 8 ranuras |
| `Identify` | — | Devuelve índice y distancia del color más cercano |

## Consejos

- Máximo 8 ranuras.
- BestDistance es al cuadrado. Tome raíz para distancia euclidiana real.
- Identify siempre devuelve 1–8. Compruebe `BestDistance > umbral` para "sin coincidencia".
