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

Pruefen, ob Spieler:innen die Kernmechanik verstehen:

1. Halten laedt ein Signal.
2. Loslassen sendet das Signal.
3. Alle vier Signale muessen synchron und mit aehnlicher Staerke ankommen.
