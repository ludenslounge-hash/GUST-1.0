# GUST 1.0 - Testing GDD

Version: 0.2 - PC Prototype / Game Testing  
Stand: 2026-08-28  
Status: Testkonzept fuer spielbaren HTML-Prototyp  
Input-Modell: Vier Controller auf Tastatur gemappt

## 1. Zweck dieses GDD

Dieses GDD beschreibt GUST nicht als fertige Rauminstallation, sondern als testbaren PC-Prototyp. Ziel ist es, die Kernmechanik frueh zu pruefen, bevor Hardware, Raumaufbau, Sensorik oder Installation weiterentwickelt werden.

Die langfristige Vision bleibt:

> GUST verwandelt einen Raum in ein kooperatives Lichtspiel, bei dem mehrere Spieler:innen Signale zu einer zentralen Kugel senden.

Fuer das aktuelle Game Testing wird diese Vision reduziert auf:

> Ein PC-Prototyp simuliert vier Controller, vier Lichtverbindungen und eine zentrale Kugel. Die vier Controller werden ueber Tastaturtasten gesteuert.

## 2. Analyse des bisherigen GDD

Das bisherige GDD beschreibt GUST stark als modulares Spatial Multiplayer Game. Das ist fuer die langfristige Vision sinnvoll, aber fuer das naechste Testing zu breit.

### Gut geeignet fuer Testing

- Die Kernidee ist klar: mehrere Inputs aktivieren gemeinsam eine zentrale Kugel.
- Die radiale Struktur mit vier Stationen ist visuell und mechanisch stark.
- Die Kombination aus Timing und Farbverhaeltnis ist eine gute testbare Challenge.
- Der Fokus auf Licht als Feedback passt sehr gut zum bestehenden HTML-Prototyp.
- Die physische Vision laesst sich gut durch einen Bildschirm-Prototyp simulieren.

### Zu breit fuer den ersten Test

- Rauminstallation, Festivalversion, Gestensteuerung und Plattformgedanke sind fuer den ersten PC-Test nicht notwendig.
- Alternative Spielmodi wie Tug of War, Looping Louie und Ping Pong sollten im Test nicht vermischt werden.
- Das Ziel "moeglichst ohne Erklaerung" ist wertvoll, braucht aber kontrollierte Testvarianten.
- Das bisherige GDD definiert noch nicht konkret genug, was der PC-Prototyp koennen muss.

### Anpassung fuer Testing

GUST 1.0 wird fuer den naechsten Schritt als "Proof of Core Mechanic" verstanden:

- Nicht die Raumwirkung wird getestet.
- Nicht die Hardware wird getestet.
- Nicht die finale Show-Qualitaet wird getestet.
- Getestet wird, ob die spielerische Logik funktioniert:
  - Halten
  - Loslassen
  - Signalreise
  - Synchronisation
  - aehnliche Signalstaerke
  - gemeinsamer Erfolg

## 3. High Concept fuer den Test

GUST ist ein kooperatives Timing-Spiel fuer vier virtuelle Controller.

Jeder Controller sendet ein farbiges Signal zur zentralen Kugel. Ein Signal wird vorbereitet, indem die zugehoerige Taste gehalten wird. Beim Loslassen startet das Signal und reist sichtbar zur Kugel.

Die Kugel aktiviert sich nur, wenn alle vier Signale ungefaehr gleichzeitig ankommen und eine vergleichbare Staerke besitzen.

Der PC-Prototyp bildet damit das spaetere physische Spiel abstrahiert ab:

```text
Tastaturtaste -> virtueller Controller -> sichtbares Signal -> zentrale Kugel
```

## 4. Testbare Kernmechanik

### Controller-Mapping

Die vier Controller werden fuer das Testing auf folgende Tasten gemappt:

- `A` = Controller A / blau / links oben
- `K` = Controller B / rot / rechts oben
- `L` = Controller C / gruen / rechts unten
- `S` = Controller D / gelb / links unten

Diese Belegung entspricht dem aktuellen Prototyp. Sie erlaubt drei Testformen:

- Solo: eine Person steuert alle vier Tasten.
- Duo: zwei Personen steuern je zwei Tasten.
- Gruppe: vier Personen steuern je eine Taste.

### Player Action

Eine Aktion besteht aus zwei Phasen:

1. Taste halten
   - Der Controller laedt Signalstaerke auf.
   - Die Ladeanzeige steigt sichtbar.

2. Taste loslassen
   - Das Signal wird abgeschickt.
   - Der Lichtimpuls reist zur Kugel.

Wichtig fuer das Testing:

- Es wird nicht "Druecken im richtigen Moment" getestet.
- Es wird "Loslassen im richtigen gemeinsamen Moment" getestet.
- Die Haltezeit beeinflusst die Signalstaerke.

## 5. Ziel des Spiels

Die Spieler:innen sollen die zentrale Kugel aktivieren.

Ein Treffer entsteht, wenn:

- alle vier Controller ein Signal geschickt haben,
- alle vier Signale innerhalb des erlaubten Zeitfensters ankommen,
- die vier Signalstaerken aehnlich genug sind.

Der Erfolg ist kollektiv. Kein einzelner Controller kann alleine gewinnen.

## 6. Aktuelle Prototype-Werte

Diese Werte stammen aus dem vorhandenen HTML-Prototyp und sind Startwerte fuer Testing:

- Signallaufzeit: `1100 ms`
- Ladezeit bis volle Signalstaerke: `900 ms`
- Start-Zeitfenster: `400 ms`
- Mindest-Zeitfenster nach Erfolgen: `150 ms`
- Verringerung pro Treffer: `30 ms`
- erlaubte Differenz der Signalstaerken: `0.34`
- LED-Segmente pro Verbindung: `44`

Diese Werte sind nicht final. Sie sind Testparameter.

## 7. Design Pillars fuer den Test

### 7.1 Lesbare Ursache-Wirkung

Tester:innen muessen schnell verstehen:

```text
Ich halte eine Taste -> mein Controller laedt.
Ich lasse los -> mein Signal reist zur Kugel.
Mein Signal erreicht die Kugel -> die Kugel reagiert.
```

### 7.2 Koordination statt Reflex

Das Spiel soll nicht nur Reaktionsgeschwindigkeit testen. Der zentrale Spass soll aus Abstimmung entstehen:

- gemeinsam zaehlen,
- aufeinander warten,
- Haltezeit angleichen,
- aus Fehlern lernen.

### 7.3 Sichtbares Lernen

Spieler:innen sollen nach einem Fehler erkennen koennen, woran es lag:

- Timing war zu ungenau.
- Signalstaerken waren zu unterschiedlich.
- Ein Controller wurde vergessen.

### 7.4 Erfolg als gemeinsamer Moment

Ein Treffer muss sich deutlich vom normalen Signalfeedback unterscheiden. Die Kugel soll sichtbar heller werden, der Score steigen und alle Spieler:innen sollen merken: "Das war unser gemeinsamer Treffer."

## 8. Scope fuer den ersten Test

### Im Scope

- Vier Controller
- PC-Browser
- Tastatursteuerung
- Halten und Loslassen
- sichtbare Signalreise
- Timing-Auswertung
- Signalstaerken-Auswertung
- Treffer / Misserfolg
- Score
- Playtest mit 1, 2 oder 4 Personen

### Nicht im Scope

- echte physische Controller
- LED-Hardware
- Kamera- oder Gestensteuerung
- raumfuellende Installation
- Festival- oder Messe-Version
- alternative Spielmodi
- Online-Multiplayer
- finales Art Direction Polish

## 9. Prototyp-Anforderungen fuer Game Testing

### Muss

- Der Prototyp laeuft lokal im Browser.
- Die Tasten `A`, `S`, `K`, `L` sind eindeutig sichtbar.
- Jeder Controller zeigt den gedrueckten Zustand.
- Jeder Controller zeigt Ladefortschritt.
- Loslassen erzeugt unmittelbar einen sichtbaren Impuls.
- Signale reisen sichtbar zur Kugel.
- Die Kugel reagiert auf eintreffende Signale.
- Erfolg und Misserfolg sind unterscheidbar.
- Score, Zeitfenster und letzte Abweichung sind sichtbar.
- Deutsche Texte sind korrekt lesbar.
- Das Spiel kann mehrere Minuten ohne Neustart getestet werden.

### Sollte

- Reset-Funktion fuer neue Testperson.
- Testmodus mit fixem Zeitfenster.
- Anzeige des Misserfolgsgrunds:
  - Timing
  - Signalstaerke
  - fehlender Controller
- Versuchszahl sichtbar.
- Einfaches Logging fuer Testleitung.
- Export der Session-Daten als CSV oder JSON.

### Kann

- Auswahl fuer Solo-, Duo- und Vier-Personen-Test.
- Schwierigkeitsauswahl.
- alternative Keymaps.
- Ton an/aus.
- Vollbildmodus.

## 10. Testmodi

### Modus A: Solo

Eine Person steuert alle vier Controller.

Testfrage:

> Ist die Mechanik alleine verstaendlich und technisch sauber spielbar?

Risiko:

- Solo kann sich eher wie Fingerkoordination als wie kooperatives Spiel anfuehlen.

### Modus B: Duo

Zwei Personen teilen sich die Controller.

Vorschlag:

- Person 1: `A` und `S`
- Person 2: `K` und `L`

Testfrage:

> Entsteht bereits Kommunikation und Abstimmung?

### Modus C: Vier Personen

Jede Person steuert eine Taste.

Testfrage:

> Traegt die Kernmechanik als kooperativer Multiplayer-Moment?

Dieser Modus ist der wichtigste fuer die spaetere physische Installation.

## 11. Onboarding fuer Testing

Das urspruengliche GDD strebt moeglichst erklaerungsfreies Spielen an. Fuer Testing sollte das in zwei Varianten geprueft werden.

### Variante 1: Minimal erklaert

Testleitung sagt:

> Ihr steuert vier Controller mit `A`, `S`, `K` und `L`. Haltet eure Taste, um ein Signal zu laden. Lasst los, um es zur Kugel zu schicken. Aktiviert gemeinsam die Kugel.

Ziel:

- Pruefen, ob die Kernmechanik nach kurzer Einweisung funktioniert.

### Variante 2: Beobachtend

Testleitung sagt nur:

> Findet heraus, wie ihr die Kugel aktivieren koennt.

Ziel:

- Pruefen, ob Lichtfeedback und UI allein genug erklaeren.

Empfehlung:

Fuer den ersten ernsthaften Test zuerst Variante 1 nutzen. Variante 2 erst testen, wenn Feedback und UI stabiler sind.

## 12. Balancing-Fragen

Die folgenden Parameter muessen durch Playtesting validiert werden:

- Ist `1100 ms` Signallaufzeit zu lang, zu kurz oder gut lesbar?
- Ist `900 ms` Ladezeit intuitiv?
- Ist `400 ms` Startfenster fuer neue Spieler:innen fair?
- Wird das enger werdende Zeitfenster als motivierend oder bestrafend erlebt?
- Ist der erlaubte Signalstaerken-Unterschied von `0.34` nachvollziehbar?
- Brauchen Spieler:innen mehr Feedback, wenn nur die Signalstaerke falsch war?
- Funktioniert dieselbe Balance fuer Solo, Duo und vier Personen?

## 13. Success Metrics

Der Prototyp gilt als erfolgreich getestet, wenn:

- 80 Prozent der Tester:innen das Halten/Laden innerhalb von 60 Sekunden verstehen.
- 80 Prozent verstehen, dass Loslassen das eigentliche Senden ausloest.
- 70 Prozent koennen nach dem Test erklaeren, dass Timing und Signalstaerke gemeinsam zaehlen.
- Die meisten Gruppen schaffen innerhalb von 5 Minuten mindestens einen Treffer.
- Treffer fuehlen sich fuer Tester:innen nicht zufaellig an.
- Misserfolge sind grob nachvollziehbar.
- Die Tastaturbelegung behindert das Spiel nicht wesentlich.

## 14. Risiken fuer den PC-Prototyp

### Tastatur ist kein echter Controller

Die PC-Version testet Mechanik und Timing, aber nicht Haptik, Raumgefuehl oder physische Praesenz.

Konsequenz:

- Testergebnisse zur Bedienlogik sind relevant.
- Testergebnisse zur finalen Experience sind nur eingeschraenkt uebertragbar.

### Solo-Test kann falsche Signale geben

Wenn eine Person alle vier Tasten steuert, wird Kooperation kaum getestet.

Konsequenz:

- Solo eignet sich fuer technische Funktion und Regelverstaendnis.
- Duo und vier Personen sind wichtiger fuer die eigentliche GUST-Erfahrung.

### UI erklaert mehr als spaeter die Installation

Der HTML-Prototyp nutzt Textanzeigen wie Score, Zeitfenster und Abweichung.

Konsequenz:

- Diese Anzeigen sind fuer Testing erlaubt.
- Spaeter muss entschieden werden, welche Informationen durch Licht statt Text vermittelt werden.

## 15. Testing-Backlog

Vor dem naechsten Playtest:

1. Encoding-Probleme im HTML beheben.
2. Reset-Funktion einbauen.
3. Testmodus mit fixem Zeitfenster einbauen.
4. Versuchszahl anzeigen.
5. Misserfolgsgrund klarer anzeigen.

Nach dem ersten Playtest:

1. Timing-Werte anhand der Ergebnisse anpassen.
2. Signalstaerken-Regel pruefen und gegebenenfalls vereinfachen.
3. Tastaturmapping bewerten.
4. Entscheiden, ob Solo, Duo oder Vier-Personen-Modus der Haupttestmodus wird.
5. Feedbacksprache Richtung physische Installation reduzieren.

## 16. Angepasstes Konzept fuer den aktuellen Prototyp

GUST 1.0 wird fuer die naechste Phase als PC-basierter Core-Mechanic-Test definiert.

Vier virtuelle Controller sind radial um eine zentrale Kugel angeordnet. Jeder Controller ist einer Tastaturtaste zugeordnet. Spieler:innen halten ihre Taste, um ein Signal aufzuladen, und lassen sie los, um den Impuls zur Kugel zu senden. Die Signale reisen sichtbar durch die Verbindungen. Die Kugel aktiviert sich, wenn alle vier Signale synchron genug und mit aehnlicher Staerke eintreffen.

Das Testing konzentriert sich auf drei Fragen:

1. Ist die Mechanik sofort genug lesbar?
2. Entsteht echte Abstimmung zwischen Spieler:innen?
3. Fuehlt sich ein gemeinsamer Treffer verdient und befriedigend an?

Alles, was nicht hilft, diese drei Fragen zu beantworten, bleibt vorerst ausserhalb des Prototyp-Scopes.

