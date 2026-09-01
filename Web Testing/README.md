# GUST Web Testing

Diese Webversion ist eine eigenstaendige PC-Testfassung des GUST-Prototyps.

## Start

`index.html` im Browser oeffnen.

## Steuerung

- `A` = Controller A
- `S` = Controller D
- `K` = Controller B
- `L` = Controller C
- Taste halten = Signal laden
- Taste loslassen = Signal senden
- `R` = Reset

## Testfunktionen

- auswählbare Spielmodi:
  - OG GUST: Synchronisation und Signalstaerke
  - Tug of War: Team links gegen Team rechts
  - Looping Louie: aktive Station im Kreis treffen
  - Ping Pong: Signal im Kreis weiterleiten
- Solo-, Duo- und Vier-Personen-Testmodus
- fixe und variable Schwierigkeitsfenster
- Treffer, Versuche, Abweichung und Zeitfenster sichtbar
- Session Log im rechten Panel
- CSV Export in die Zwischenablage

## Testziel

## Spielmodi

- **OG GUST:** Alle vier Signale muessen gleichzeitig und mit aehnlicher Staerke ankommen.
- **Tug of War:** A/S (links) und K/L (rechts) senden Kraftimpulse und ziehen die Balance zu ihrer Seite.
- **Looping Louie:** Das leuchtende Ziel wandert im Kreis; nur die aktive Station darf gedrueckt werden.
- **Ping Pong:** Das Signal wird in der angezeigten Reihenfolge innerhalb des Countdowns weitergegeben.

Pruefen, ob Spieler:innen die Kernmechanik verstehen:

1. Halten laedt ein Signal.
2. Loslassen sendet das Signal.
3. Alle vier Signale muessen synchron und mit aehnlicher Staerke ankommen.
