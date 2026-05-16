# Sensor de cor RGB melhorado — Guia

Bloco estendido do sensor de cor EV3: canais RGB e HSVL brutos e modo de comparação RGB. No separador **Sensor**.

## Conceito

O bloco padrão só dá 7 cores e luz refletida/ambiente. Internamente o sensor reporta R, G, B. Este bloco expõe-os.

- **Medir – RGB** — ler R, G, B brutos (0–255).
- **Medir – HSVL** — converter para Matiz (0–360°), Saturação, Valor, Luminosidade.
- **Comparar – RGB** — comparar com R/G/B de referência com tolerância, devolve booleano.

## Modos

| Modo | Entradas | Saídas |
|------|----------|--------|
| `ReadRGB` | Porta | Vermelho, Verde, Azul |
| `ReadHSV` | Porta | Matiz, Saturação, Valor, Luminosidade |
| `DectRGB` | Porta, R/G/B referência, Tolerância | Vermelho, Verde, Azul, Corresponde |

## Dicas

- Calibre sob a iluminação real.
- Com iluminação variável, use o modo **Normalizar** do Classificador de cor.

Bloco RGB original: David Gilday. HSVL e Compare-RGB: OFDL.
