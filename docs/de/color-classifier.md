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
|-------|-----------|--------------|
| `Normalize` | — | Jeder Kanal / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | Einrichten | Referenzfarbe in Slot n speichern |
| `Distance` | — | Quadrierte Distanz vom Eingang zu jedem der 8 Slots |
| `Identify` | — | Slot-Nummer und Distanz der nächsten Farbe zurückgeben |

## Tipps

- 8 Slots ist die Obergrenze.
- BestDistance ist quadriert. Wurzel ziehen für tatsächliche Euklid-Distanz.
- Identify gibt immer 1–8 zurück. Schwellwert für „kein Match" selbst prüfen.
