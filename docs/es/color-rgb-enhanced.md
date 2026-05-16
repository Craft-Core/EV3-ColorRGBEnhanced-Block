# Sensor de color RGB mejorado — Guía

Bloque extendido del sensor de color EV3: canales RGB y HSVL en bruto, más un modo de comparación RGB. En la pestaña **Sensor**.

## Concepto

El bloque estándar solo da 7 colores y luz reflejada/ambiente. Internamente el sensor reporta R, G, B. Este bloque los expone.

- **Medir – RGB** — leer R, G, B brutos (0–255).
- **Medir – HSVL** — convertir a Tono (0–360°), Saturación, Valor, Luminosidad.
- **Comparar – RGB** — comparar con R/G/B de referencia con tolerancia, devuelve booleano.

## Modos

| Modo | Entradas | Salidas |
|------|----------|---------|
| `ReadRGB` | Puerto | Rojo, Verde, Azul |
| `ReadHSV` | Puerto | Tono, Saturación, Valor, Luminosidad |
| `DectRGB` | Puerto, R/G/B referencia, Tolerancia | Rojo, Verde, Azul, Coincide |

## Consejos

- Calibre bajo la iluminación real.
- Bajo iluminación cambiante, use el modo **Normalizar** del Clasificador de color.

Bloque RGB original: David Gilday. HSVL y Compare-RGB: OFDL.
