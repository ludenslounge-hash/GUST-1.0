# GUST Game Testing Plan

Stand: 2026-08-28  
Testfokus: PC-Prototyp mit Tastatur-Mapping fuer vier Controller

## 1. Projektanalyse

### Vorhandene Dateien

- `gust-og-mockup.html`
  - Spielbarer 2D-HTML-Prototyp.
  - Vier virtuelle Controller sind auf Tastaturtasten gemappt:
    - Controller A: `A`
    - Controller D: `S`
    - Controller B: `K`
    - Controller C: `L`
  - Eingabeprinzip:
    - Taste halten = Farbanteil / Signalstaerke laden.
    - Taste loslassen = Signalimpuls abschicken.
    - Signal braucht 1,1 Sekunden bis zur zentralen Kugel.
    - Alle vier Signale muessen innerhalb eines Zeitfensters ankommen.
    - Die Farbanteile muessen aehnlich stark sein.
  - Aktuelle Spielwerte:
    - Signallaufzeit: `1100 ms`
    - Ladezeit bis voll: `900 ms`
    - Start-Zeitfenster: `400 ms`
    - Zeitfenster wird nach Treffern enger, Minimum `150 ms`
    - Maximal erlaubte Abweichung der Farbanteile: `0.34`
  - Feedbacksysteme:
    - Score / Trefferanzeige
    - Anzeige der letzten Abweichung in Millisekunden
    - Anzeige des aktuellen Zeitfensters
    - Visuelles Signal entlang der Kabel
    - Zentraler Kugel-Effekt bei Erfolg
    - Audio-Beep bei Senden, Ankunft und Erfolg
  - Aktuelle Risiken:
    - Mehrere deutsche Sonderzeichen sind falsch codiert, z. B. Gedankenstrich und Umlaute.
    - Es gibt noch kein Logging fuer Playtest-Daten.
    - Es gibt noch keinen Reset-Button.
    - Es gibt noch keinen klaren Testmodus mit konstantem Schwierigkeitsgrad.
    - Keine Session-Auswertung nach einem Testlauf.

- `GDD mock up.md`
  - Datei ist aktuell leer.
  - Sollte spaeter Zielgruppe, Spielidee, Kernmechanik, Hardware-Idee und Testannahmen dokumentieren.

- `02324e6e-c5bc-46a6-9a3a-1d2a10502b9e.png`
  - Hero-Visual des Raumkonzepts.
  - Zeigt vier Spieler:innen an Stationen, Lichtsignale und zentrale Kugel.
  - Nuetzlich fuer Pitch, Testbriefing und Erwartungsabgleich.

- `db5b1da4-0299-4f2d-9e1f-7ba66642349e.png`
  - Composite mit Hero-Visual, Top-Down-Gameplay, Erfolgsmoment, Controller-Close-up und Animationssequenz.
  - Besonders relevant als Referenz fuer den PC-Prototyp.

- `photo_2026-08-28_14-34-04.jpg`
  - Physischer Mockup-Koffer mit vier Controllern und zentraler Kugel.
  - Zeigt, dass der digitale Tastatur-Prototyp eine reduzierte Version eines physischen Vier-Controller-Setups ist.

## 2. Ziel des Game Testings

Der Test soll pruefen, ob die Kernidee von GUST am PC verstaendlich und spielerisch tragfaehig ist, bevor ein physischer oder technisch aufwendiger Prototyp weitergebaut wird.

### Hauptfragen

1. Verstehen Spieler:innen die Controller-Mechanik ueber Tastatur?
2. Fuehlt sich das gleichzeitige Loslassen der vier Signale spannend und fair an?
3. Verstehen Spieler:innen den Zusammenhang zwischen Haltezeit, Signalstaerke und Erfolg?
4. Funktioniert das PC-Setup als Ersatz fuer vier physische Controller?
5. Welche Werte fuer Laufzeit, Ladezeit und Trefferfenster fuehlen sich gut an?
6. Eignet sich das Spiel eher fuer eine Person mit vier Fingern oder fuer mehrere Personen an einer Tastatur?

## 3. Testannahmen

Diese Annahmen sollen durch Playtesting bestaetigt oder widerlegt werden:

- Die Spieler:innen erkennen nach kurzer Zeit, dass nicht schnelles Druecken, sondern synchrones Loslassen entscheidend ist.
- `A`, `S`, `K`, `L` sind fuer PC-Testing ausreichend gut, weil sie zwei Haende oder mehrere Personen an einer Tastatur erlauben.
- Ein Startfenster von `400 ms` ist fuer den Einstieg fair.
- Eine Signallaufzeit von `1100 ms` ist lang genug, damit Spieler:innen die Reise des Signals wahrnehmen.
- Das enger werdende Zeitfenster erzeugt Spannung, ohne zu frueh zu frustrieren.
- Die Anzeige der Abweichung hilft beim Lernen.
- Audio und visuelles Feedback sind wichtig, aber der Prototyp muss auch ohne Ton spielbar bleiben.

## 4. Anforderungen an den PC-Prototyp

### Muss-Anforderungen fuer den ersten Test

- Der Prototyp muss lokal auf einem PC im Browser laufen.
- Der Prototyp muss ohne Installation spielbar sein, idealerweise per HTML-Datei oder lokalem Server.
- Die vier Controller muessen eindeutig auf Tastaturtasten gemappt sein:
  - `A` = Controller A
  - `S` = Controller D
  - `K` = Controller B
  - `L` = Controller C
- Jede Taste muss zwei Zustaende haben:
  - gedrueckt / halten
  - losgelassen / Signal senden
- Der Ladezustand jedes Controllers muss sichtbar sein.
- Der Signalimpuls muss sichtbar vom Controller zur Kugel reisen.
- Die zentrale Kugel muss klar auf Erfolg und Misserfolg reagieren.
- Das Spiel muss Score, aktuelle Abweichung und erlaubtes Zeitfenster anzeigen.
- Der Prototyp muss nach einem Treffer weiterspielbar bleiben.
- Der Prototyp darf keine kaputten Sonderzeichen in sichtbaren deutschen Texten haben.

### Sollte-Anforderungen fuer bessere Tests

- Ein Reset-Button setzt Score, Zeitfenster, aktive Signale und Anzeige zurueck.
- Ein Testmodus friert die Schwierigkeit ein, z. B. dauerhaft `400 ms`, damit Tester:innen vergleichbar spielen.
- Ein Debug-Overlay zeigt:
  - letzter Spread in ms
  - Ladeanteile der vier Controller
  - Erfolg / Misserfolg-Grund
  - Anzahl Versuche
- Ein Session-Log speichert pro Versuch:
  - Timestamp
  - Release-Zeitpunkte der vier Tasten
  - Ankunfts-Spread
  - vier Ladeanteile
  - Treffer ja/nein
  - Misserfolgsgrund: Timing oder Farbanteil
- Eine einfache Exportfunktion kopiert die Session-Daten als JSON oder CSV.
- Es gibt eine Start-/Instruktionsansicht mit maximal drei Saetzen.
- Es gibt eine klare Erfolgsmeldung und eine klare Fehlermeldung.

### Kann-Anforderungen fuer spaetere Tests

- Alternative Tastaturbelegungen:
  - `Q`, `W`, `O`, `P`
  - `1`, `2`, `9`, `0`
  - frei konfigurierbare Keys
- Lokaler Multiplayer-Modus:
  - 1 Spieler:in steuert alle vier Tasten
  - 2 Spieler:innen steuern je zwei Tasten
  - 4 Spieler:innen steuern je eine Taste
- Schwierigkeitsauswahl:
  - Easy: `600 ms`
  - Normal: `400 ms`
  - Hard: `250 ms`
  - Expert: `150 ms`
- Stummschalten / Lautstaerke-Regler.
- Vollbildmodus.
- Countdown fuer strukturierte Testdurchlaeufe.

## 5. Test-Setup

### Hardware

- PC oder Laptop
- Externe Tastatur empfohlen
- Bildschirm mindestens 13 Zoll, besser 24 Zoll
- Browser: Chrome oder Edge als Hauptbrowser
- Optional: Firefox als Vergleich
- Optional: Lautsprecher oder Kopfhoerer

### Raum

- Ruhiger Platz
- Tester:in soll Tastatur und Bildschirm bequem sehen
- Beobachter:in sitzt seitlich und greift nicht ein

### Rollen

- Testleitung:
  - startet Prototyp
  - gibt minimale Einweisung
  - beobachtet Verhalten
  - stellt Nachfragen nach dem Test
- Tester:in:
  - spielt ohne lange Erklaerung
  - denkt laut, wenn moeglich
- Optional zweite Person:
  - notiert Zeiten, Aussagen und Auffaelligkeiten

## 6. Testablauf

### Vorbereitung

1. Browser oeffnen.
2. `gust-og-mockup.html` starten.
3. Ton pruefen.
4. Fenster maximieren.
5. Sicherstellen, dass `A`, `S`, `K`, `L` funktionieren.
6. Beobachtungsbogen bereitlegen.

### Kurze Einweisung

Empfohlener Text:

> Du steuerst vier Controller mit `A`, `S`, `K` und `L`. Taste halten laedt ein Signal auf, Loslassen schickt es zur Kugel. Versuche, alle vier Signale moeglichst gleichzeitig und mit aehnlicher Staerke ankommen zu lassen.

### Testdurchlauf

- Dauer pro Person: 5 bis 8 Minuten
- Ziel: mindestens 5 Treffer oder maximal 20 Versuche
- Testleitung sagt waehrend des Spiels moeglichst wenig
- Nach jedem Test kurze Befragung

### Varianten

- Solo-Test:
  - Eine Person bedient alle vier Tasten.
  - Prueft, ob der PC-Prototyp allein verstaendlich und spielbar ist.

- Zwei-Personen-Test:
  - Person 1 bedient `A` und `S`.
  - Person 2 bedient `K` und `L`.
  - Prueft Koordination und Kommunikation.

- Vier-Personen-Test:
  - Jede Person bedient eine Taste.
  - Naehert sich der physischen Installation am staerksten an.

## 7. Konkrete Testfaelle

### Eingabe

- `A` gedrueckt halten: Controller A laedt sichtbar.
- `S` gedrueckt halten: Controller D laedt sichtbar.
- `K` gedrueckt halten: Controller B laedt sichtbar.
- `L` gedrueckt halten: Controller C laedt sichtbar.
- Taste loslassen: Signal startet sofort sichtbar.
- Mehrere Tasten gleichzeitig halten: alle passenden Controller laden parallel.
- Mehrere Tasten gleichzeitig loslassen: mehrere Signale starten parallel.
- Wiederholtes Halten und Loslassen erzeugt keine haengenden Zustaende.

### Timing

- Vier Signale innerhalb `400 ms` Ankunftsfenster erzeugen Treffer.
- Vier Signale ausserhalb des Fensters erzeugen Misserfolg wegen Timing.
- Nach Treffer sinkt das erlaubte Zeitfenster.
- Zeitfenster sinkt nicht unter `150 ms`.
- Angezeigte Abweichung entspricht erkennbar dem Spielverhalten.

### Farbanteil / Ladeanteil

- Sehr unterschiedlich lange gehaltene Tasten erzeugen Misserfolg wegen ungleicher Farbanteile.
- Aehnlich lange gehaltene Tasten koennen Treffer erzeugen.
- Ladeanzeige ist waehrend des Haltens lesbar.
- Spieler:innen verstehen, dass zu kurze und zu lange Haltezeiten relevant sind.

### Feedback

- Erfolg ist visuell eindeutig.
- Misserfolg wegen Timing ist textlich eindeutig.
- Misserfolg wegen Farbanteil ist textlich eindeutig.
- Score steigt nur bei Erfolg.
- Audio unterstuetzt Feedback, ist aber nicht zwingend noetig.

### Bedienbarkeit

- Das Spiel ist im maximierten Browser gut lesbar.
- Die vier Controller sind eindeutig unterscheidbar.
- Tastaturmapping im Footer ist sichtbar.
- Text und UI ueberlappen nicht.
- Prototyp bleibt auch nach vielen Versuchen stabil.

## 8. Beobachtungsbogen

### Messwerte

- Tester:in ID:
- Testdatum:
- Browser:
- Eingabemodus:
  - Solo
  - 2 Personen
  - 4 Personen
- Zeit bis erstes korrektes Signalverhalten:
- Zeit bis erster Treffer:
- Treffer nach 5 Minuten:
- Anzahl sichtbarer Frustmomente:
- Anzahl Nachfragen zur Regel:

### Beobachtungen

- Was probiert die Person zuerst?
- Werden die Tasten verstanden?
- Wird Halten / Loslassen verstanden?
- Wird die Signallaufzeit verstanden?
- Wird der Ladeanteil verstanden?
- Wird die Abweichungsanzeige genutzt?
- Kommunizieren mehrere Spieler:innen miteinander?
- Welche Rueckmeldung fehlt?

### Nachbefragung

1. Was war deiner Meinung nach das Ziel des Spiels?
2. Wann hast du verstanden, was du tun musst?
3. Was war unklar?
4. War das Timing fair?
5. Waren die Tasten angenehm?
6. Hat sich ein Treffer gut angefuehlt?
7. Was wuerdest du als erstes verbessern?
8. Wuerdest du es nochmal spielen?

## 9. Erfolgskriterien

Der PC-Prototyp ist testbereit, wenn:

- Mindestens 4 von 5 Tester:innen die Grundregel innerhalb von 2 Minuten verstehen.
- Mindestens 4 von 5 Tester:innen schaffen innerhalb von 5 Minuten mindestens einen Treffer.
- Mindestens 3 von 5 Tester:innen koennen nach dem Test erklaeren, dass Timing und Ladeanteil wichtig sind.
- Es gibt keine haengenden Eingabezustaende.
- Keine sichtbaren deutschen Texte sind falsch codiert.
- Das Spiel laeuft 10 Minuten ohne Absturz oder starke Performance-Probleme.

Der Prototyp braucht Anpassung, wenn:

- Tester:innen nur schnell tippen und das Halten nicht verstehen.
- Tester:innen die Signallaufzeit nicht wahrnehmen.
- Mehrere Personen nicht erkennen, wer welchen Controller steuert.
- Misserfolg nicht klar erklaerbar ist.
- Treffer sich zufaellig statt verdient anfuehlen.

## 10. Empfohlene naechste Entwicklungsaufgaben

Prioritaet 1:

- Encoding-Probleme in `gust-og-mockup.html` beheben.
- Reset-Button einbauen.
- Kurze Startanweisung einbauen.
- Testmodus mit fixem Zeitfenster einbauen.

Prioritaet 2:

- Session-Logging fuer Playtests einbauen.
- Export als CSV oder JSON einbauen.
- Schwierigkeitsauswahl einbauen.
- Solo-, Duo- und Vier-Personen-Modus sichtbar machen.

Prioritaet 3:

- GDD in `GDD mock up.md` ausfuellen.
- Erkenntnisse aus Playtests in Balancing-Werte uebertragen.
- Tastatur-Prototyp spaeter mit physischem Controller-Layout vergleichen.

## 11. Minimale Version fuer den ersten echten Test

Vor dem ersten externen Test sollte der Prototyp mindestens diese Punkte erfuellen:

1. Sichtbare Texte korrekt codiert.
2. Tastaturmapping `A`, `S`, `K`, `L` funktioniert stabil.
3. Reset-Funktion vorhanden.
4. Treffer und Misserfolg sind klar unterscheidbar.
5. Testleitung kann Score, Abweichung und Zeitfenster notieren.
6. Testdauer und Testziel sind vorab definiert.
