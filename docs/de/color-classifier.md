# Farb-Klassifikator — Anleitung

Distanzbasierter Farbklassifikator für den Tab **Datenoperationen**. Bis zu 8 Referenzfarben anlernen und identifizieren, welcher davon ein Live-RGB-Wert am nächsten kommt.

## Konzept

```
Normieren: Rn = R / (R+G+B) × 100    (helligkeitsunabhängig)
Setup ×8:  Eine Referenzfarbe pro Slot speichern
Distanz:   Für jeden Slot n: D{n} = (R-Rn)² + (G-Gn)² + (B-Bn)²
Identif.:  BestColor = argmin(D1..D8); BestDistance = min(D1..D8)
```

## Anwendung

1. Bei Programmstart `Setup_C{n}` für n=1..8 mit den Referenzwerten aufrufen.
2. In der Hauptschleife: RGB lesen → optional Normieren → Distanz → Identifizieren.

## Modi

| Modus | Kategorie | Beschreibung |
|---

## Farbindex

Der Block `Identifizieren` gibt eine Zahl von **1 bis 8** zurück. Die Zuordnung ist fest:

| Index | Farbe  | Standard R | Standard G | Standard B |
|-------|--------|------------|------------|------------|
| **1** | Rot    | 255 | 0   | 0   |
| **2** | Grün   | 0   | 255 | 0   |
| **3** | Blau   | 0   | 0   | 255 |
| **4** | Gelb   | 255 | 255 | 0   |
| **5** | Weiß   | 255 | 255 | 255 |
| **6** | Schwarz | 0  | 0   | 0   |
| **7** | Braun  | 128 | 64  | 0   |
| **8** | Pink   | 200 | 50  | 150 |

> **Wichtig:** Die Standardwerte sind Idealwerte. Echte EV3-Sensoren liefern deutlich niedrigere Werte. Messen Sie jede Farbe mit Ihrem Sensor und tragen Sie die gemessenen Werte in die Setup-Blöcke ein.
----|-----------|--------------|
| `Normalize` | — | Jeder Kanal / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | Einrichten | Referenzfarbe in Slot n speichern |
| `Distance` | — | Quadrierte Distanz vom Eingang zu jedem der 8 Slots |
| `Identify` | — | Slot-Nummer und Distanz der nächsten Farbe zurückgeben |

## Tipps

- 8 Slots ist die Obergrenze.
- BestDistance ist quadriert. Wurzel ziehen für tatsächliche Euklid-Distanz.
- Identify gibt immer 1–8 zurück. Schwellwert für „kein Match" selbst prüfen.
