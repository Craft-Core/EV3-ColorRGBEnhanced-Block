# Classificador de cor — Guia

Classificação de cor baseada em distância para o separador **Operações de dados**. Ensine até 8 cores de referência e identifique qual está mais próxima de uma leitura RGB ao vivo.

## Conceito

```
Normalizar: Rn = R / (R+G+B) × 100   (invariante à iluminação)
Setup ×8:   Armazena uma cor de referência por ranhura
Distância:  Para cada ranhura n: D{n} = (R-Rn)² + (G-Gn)² + (B-Bn)²
Identify:   BestColor = argmin(D1..D8); BestDistance = min(D1..D8)
```

## Uso

1. No início, chame `Setup_C{n}` para n=1..8 com os R, G, B de referência.
2. Ciclo principal: ler RGB → Normalizar (opcional) → Distância → Identify.

## Modos

| Modo | Categoria | Descrição |
|------|-----------|-----------|
| `Normalize` | — | Cada canal / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | Configurar | Armazena cor de referência na ranhura n |
| `Distance` | — | Distância ao quadrado do RGB de entrada para cada uma das 8 ranhuras |
| `Identify` | — | Devolve índice e distância da cor mais próxima |

## Dicas

- Máximo 8 ranhuras.
- BestDistance é ao quadrado. Tire raiz para distância euclidiana real.
- Identify devolve sempre 1–8. Verifique `BestDistance > limite` para "sem correspondência".
