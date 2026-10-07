# Maschinensteuerung Web Interface: Moderne UI-Beispiele & Vorlagen 2026

Von Lawrence Dauchy, Gründer von VP0  
Veröffentlicht am 7. Oktober 2026

Ein modernes Web Interface für Maschinensteuerung zeigt den aktuellen Anlagenzustand, erklärt Störungen und macht zulässige Bedienaktionen eindeutig erkennbar. Ein guter Ausgangspunkt ist eine Oberfläche mit dauerhaft sichtbarem Maschinenstatus, wenigen zentralen Aktionen und getrennten Ansichten für Produktion, Alarme und Wartung. Entscheidend ist, dass Bediener auch bei Verbindungsproblemen oder einer unterbrochenen Befehlsausführung verstehen, was tatsächlich passiert. Die folgenden UI-Beispiele und Vorlagen beschreiben konkrete Bildschirmaufteilungen für unterschiedliche Aufgaben. Du kannst sie als Grundlage für einen Prototyp verwenden und anschließend mit deiner Steuerung, deinem Berechtigungssystem und den tatsächlichen Betriebsabläufen verbinden.

## Was muss ein Web Interface für Maschinensteuerung leisten?

Die Oberfläche muss drei Fragen beantworten: Was macht die Maschine gerade, darf ich eingreifen und wie erkenne ich das Ergebnis meiner Aktion? Diese Informationen gehören auf jede Ansicht, von der aus eine Maschine bedient werden kann.

Ein Human Machine Interface, kurz HMI, verbindet Menschen mit den Zuständen und Bedienfunktionen einer Anlage. Industrielle HMI-Systeme werden beispielsweise zur Überwachung und Bedienung automatisierter Prozesse eingesetzt.

Für dein UI-Konzept solltest du zunächst drei Aufgaben unterscheiden:

- **Beobachten:** Zustände, Messwerte und Produktionsfortschritt anzeigen.
- **Bedienen:** Freigegebene Aktionen anfordern und deren Ergebnis verfolgen.
- **Konfigurieren:** Parameter, Rezepte und Einstellungen innerhalb definierter Grenzen ändern.

Diese Aufgaben brauchen unterschiedliche Berechtigungen. Ein Mitarbeiter, der Produktionszahlen ansehen darf, muss deshalb noch keine Parameter ändern können.

Auch die Begriffe sollten zum Betrieb passen. „Bereit“ kann bedeuten, dass die Maschine eingeschaltet ist, dass alle Voraussetzungen erfüllt sind oder dass ein Produktionsauftrag geladen wurde. Verwende einen solchen Status erst, wenn seine Bedeutung feststeht.

Ein hilfreicher Einstieg ist eine Liste echter Bedienaufgaben. Beschreibe beispielsweise: „Auftrag auswählen“, „Materialwechsel bestätigen“, „Störung lokalisieren“ und „Wartungsinformationen öffnen“. Daraus entstehen Navigation und Bildschirmaufteilung.

Plane zusätzlich die Zustände außerhalb des Normalbetriebs. Ein Interface, das ausschließlich „Produktion läuft“ darstellen kann, ist als Bedienoberfläche unvollständig.

## Wie sieht eine übersichtliche Maschinenoberfläche aus?

Eine übersichtliche Maschinenoberfläche besitzt einen festen Statusbereich, einen aufgabenbezogenen Hauptbereich und eine klar abgegrenzte Aktionszone. Diese Struktur bleibt über die wichtigsten Ansichten hinweg erhalten.

Im oberen Bereich stehen Maschinenname, Betriebsart, Verbindung und Benutzerrolle. Ein Bediener sollte sofort erkennen, ob er Maschine A oder Maschine B betrachtet und ob die angezeigten Daten aktuell sind.

Der Hauptbereich beantwortet die Frage der geöffneten Ansicht. Auf der Produktionsseite sind das beispielsweise Auftrag, Fortschritt und relevante Prozesswerte. Auf der Alarmseite stehen Ursache, betroffener Bereich und nächster zulässiger Schritt.

Die Aktionszone enthält nur Funktionen, die zur aktuellen Aufgabe passen. Verstecke selten benötigte Einstellungen auf eigenen Seiten, statt den Produktionsbildschirm mit sämtlichen verfügbaren Befehlen zu füllen.

### Eine sinnvolle Grundaufteilung

Für ein Bedienpanel im Querformat kannst du folgende Struktur verwenden:

- Oben: Maschinenname, Betriebszustand und Datenaktualität.
- Links: Navigation zu Produktion, Alarmen, Rezepten und Wartung.
- Mitte: Informationen zur aktuellen Aufgabe.
- Rechts oder unten: zulässige Aktionen und deren Rückmeldungen.
- Am unteren Rand: ergänzende Hinweise zum laufenden Vorgang.

Auf einem kleineren Bildschirm sollte die Reihenfolge dieselbe Bedeutung behalten. Der Maschinenstatus darf nicht unter einer eingeklappten Navigation verschwinden.

Halte Positionen wichtiger Aktionen möglichst stabil. Wenn ein Button bei jedem Zustandswechsel an eine andere Stelle springt, wird die Bedienung schwerer vorhersehbar.

Eine moderne Gestaltung entsteht dabei durch klare Abstände, lesbare Beschriftungen und eindeutige Zustände. Transparente Karten, dekorative Animationen und komplexe Farbverläufe helfen nur dann, wenn sie diese Aufgaben unterstützen.

## Welche UI-Beispiele passen zu Produktion, Alarmen und Wartung?

Für Produktion, Alarme und Wartung brauchst du unterschiedliche Ansichten. Ein gemeinsames Gestaltungssystem verbindet sie, während jede Ansicht ihre eigene Aufgabe beantwortet.

### Beispiel 1: Produktionsübersicht

Die Produktionsübersicht zeigt, welcher Auftrag läuft und ob der Prozess wie erwartet fortschreitet.

Ein Beispielbildschirm enthält:

- Auftrag „Gehäuse Serie B“.
- Betriebszustand „Automatikbetrieb“.
- Fortschritt „320 von 500 Teilen“.
- Aktuelle Stückzahl und Ausschusszahl.
- Relevante Prozesswerte mit Einheiten.
- Eine Zusammenfassung aktiver Meldungen.
- Die aktuell zulässigen Bedienaktionen.

Die Zahlen sind Beispieldaten für den Entwurf. Welche Kennzahlen du tatsächlich benötigst, hängt vom Prozess ab.

Zeige wenige Werte, die eine Entscheidung ermöglichen. Zwölf gleich große Kennzahlen wirken zwar vollständig, lassen aber offen, welcher Wert Aufmerksamkeit braucht.

Bei einem Temperaturwert gehören Istwert, Sollwert und gegebenenfalls ein definierter Betriebsbereich zusammen. Eine große Zahl ohne Einheit oder Kontext ist für die Bedienung wenig hilfreich.

### Beispiel 2: Alarmansicht

Die Alarmansicht beantwortet: Was ist betroffen und was soll der Bediener als Nächstes tun?

Ein brauchbarer Alarm enthält eine verständliche Bezeichnung, Zeitpunkt, betroffenen Bereich und aktuellen Bearbeitungszustand. Ergänze eine konkrete Handlungsinformation, wenn sie fachlich freigegeben ist.

„Sensor S14 meldet kein Werkstück am Einlauf“ hilft mehr als „Fehler 104“. Die technische Kennung kann daneben stehen, damit die Instandhaltung gezielt suchen kann.

Unterscheide das Quittieren einer Meldung von der Beseitigung ihrer Ursache. Die Oberfläche sollte beide Vorgänge sprachlich und visuell auseinanderhalten.

### Beispiel 3: Wartungsansicht

Die Wartungsansicht zeigt Komponenten, Aufgaben und relevante Diagnosewerte.

Für jede Aufgabe kannst du Fälligkeit, erforderlichen Maschinenzustand und Dokumentationsstatus anzeigen. Eine Aktion wie „Wartung abgeschlossen“ sollte einen bewusst ausgeführten Schritt bestätigen.

Wenn du zusätzlich eine iOS-Begleit-App für Wartung oder Inspektionen entwickelst, kann VP0 als kostenlose Bibliothek für iOS-App-Designs einen visuellen Ausgangspunkt liefern. Die technische Maschinenanbindung und die fachlichen Wartungsabläufe musst du separat entwickeln.

## Welche Vorlagen kannst du für deinen Prototyp verwenden?

Beginne mit einer Vorlage, die zur häufigsten Bedienaufgabe passt. Definiere anschließend für jeden Bildschirm Normalzustand, Ladezustand, Fehlerzustand und fehlende Berechtigung.

Die folgenden Vorlagen sind konkrete Bildschirmkonzepte. Sie enthalten noch keine Verbindung zu einer Maschine und führen keine Steuerungsbefehle aus.

### Vorlage A: Kompakte Einzelmaschinensteuerung

Diese Vorlage eignet sich für eine Maschine mit überschaubarem Prozess und wenigen häufigen Aktionen.

Der Bildschirm besitzt eine Statuszeile, einen großen Prozessbereich und eine feste Aktionszone. Die Navigation führt zu Produktion, Meldungen und Einstellungen.

Im Prozessbereich stehen aktueller Schritt, Auftrag und die wichtigsten Messwerte. Bei einer Störung ersetzt eine verständliche Meldung die gewöhnliche Fortschrittsanzeige, ohne die Maschinenidentität zu verdecken.

Für den ersten Prototyp reichen diese Ansichten:

1. Maschine verbunden und bereit.
2. Produktion läuft.
3. Aktion wird verarbeitet.
4. Störung aktiv.
5. Verbindung unterbrochen.

Damit kannst du bereits prüfen, ob Nutzer Zustände unterscheiden und Rückmeldungen verstehen.

### Vorlage B: Übersicht mehrerer Maschinen

Diese Vorlage eignet sich für eine Leitstandsübersicht. Jede Maschine bekommt eine kompakte Karte mit Name, Zustand, Auftrag und Datenaktualität.

Sortiere die Karten nach einer sinnvollen Betriebslogik, beispielsweise Produktionslinie oder Standort. Eine zusätzliche Ansicht kann Maschinen mit aktiven Störungen hervorheben.

Die Übersicht dient vor allem dem Beobachten. Für Bedienaktionen öffnet der Nutzer eine Detailansicht, in der Maschinenidentität, Berechtigung und aktueller Zustand erneut klar sichtbar sind.

Eine fehlende Verbindung darf nicht wie eine stillstehende Maschine aussehen. „Keine aktuellen Daten“ ist ein eigener Zustand.

### Vorlage C: Rezept- und Parametereinstellungen

Diese Vorlage eignet sich für Maschinen, die mit unterschiedlichen Produktparametern arbeiten.

Zeige aktuelles Rezept, bearbeitete Werte und zulässige Eingabegrenzen. Trenne Entwurf, gespeicherte Konfiguration und tatsächlich übernommene Maschinenparameter.

Vor einer Übernahme bekommt der Nutzer eine nachvollziehbare Änderungsübersicht. Beispielsweise: „Fördergeschwindigkeit von 12 auf 10 Meter pro Minute ändern“.

Plane außerdem den Fall, dass ein Parameter während des laufenden Betriebs nicht geändert werden darf. Die Oberfläche erklärt dann die Voraussetzung, statt lediglich einen ausgegrauten Button zu zeigen.

### Vorlage D: Service- und Diagnoseoberfläche

Diese Vorlage eignet sich für autorisierte Techniker. Sie stellt Diagnoseinformationen und Komponentenstatus in den Vordergrund.

Ordne Informationen nach Baugruppen. Ein Techniker sollte vom betroffenen Bereich zu den passenden Signalen gelangen können, ohne sämtliche Datenpunkte durchsuchen zu müssen.

Falls du dazu eine mobile Service-App planst, kann ein passender VP0-Screen beim Aufbau von Navigation und Detailansichten helfen. Eine industrielle Web-HMI benötigt weiterhin ein eigenes, zum Prozess passendes Bedienkonzept.

## Wie verbindest du das Interface mit Maschinenzuständen und Befehlen?

Verbinde die Oberfläche über eine definierte Anwendungsschicht mit der Maschinenkommunikation. Diese Schicht prüft Berechtigungen, verarbeitet Zustände und liefert nachvollziehbare Rückmeldungen.

Für den Entwurf kannst du vier Bereiche unterscheiden:

- Die Web-Oberfläche zeigt Informationen und nimmt Eingaben entgegen.
- Der Anwendungsserver prüft Benutzer, Rollen und angeforderte Aktionen.
- Ein Gateway oder Kommunikationsdienst übersetzt die Maschinenanbindung.
- Die Steuerung verarbeitet die für sie zulässigen Anforderungen.

Die konkrete Umsetzung hängt von deiner vorhandenen Anlage ab. Ein Interface-Projekt sollte deshalb mit den verfügbaren Schnittstellen und Betriebszuständen beginnen.

OPC UA ist eine mögliche Technologie für industrielle Kommunikation. Sein Sicherheitsmodell umfasst unter anderem Authentifizierung, Signierung und Verschlüsselung. Welche Mechanismen tatsächlich aktiv sind, hängt von der gewählten Konfiguration ab.

### Befehle brauchen einen nachvollziehbaren Ablauf

Ein Klick auf „Auftrag starten“ bedeutet zunächst, dass der Nutzer eine Aktion angefordert hat. Die Maschine muss darauf nicht sofort im gewünschten Zustand sein.

Unterscheide deshalb:

1. Anforderung abgesendet.
2. Anforderung angenommen oder abgelehnt.
3. Ausführung läuft.
4. Ergebnis bestätigt oder fehlgeschlagen.

Zeige diese Schritte so, dass der Nutzer keine zweite Aktion auslösen muss, um herauszufinden, was passiert.

Für zusammengehörige Meldungen ist eine eindeutige Vorgangskennung hilfreich. So kann dein System Rückmeldungen der richtigen Anforderung zuordnen.

Bei einem Timeout ist das Ergebnis möglicherweise unbekannt. „Keine Bestätigung erhalten“ beschreibt diesen Fall genauer als „Befehl fehlgeschlagen“. Vor einer Wiederholung muss das System prüfen, ob die erste Anforderung bereits verarbeitet wurde.

### Datenalter gehört zum Zustand

Ein Messwert kann korrekt übertragen worden sein und trotzdem inzwischen veraltet sein. Zeige deshalb, wann Daten zuletzt aktualisiert wurden.

Für den Prototyp kannst du eine projektspezifische Grenze definieren, ab der Werte als veraltet gelten. Der passende Zeitraum hängt davon ab, wie schnell sich der Prozess verändert.

Behalte alte Werte gegebenenfalls sichtbar, kennzeichne sie aber ausdrücklich. So bleibt Orientierung möglich, ohne Aktualität vorzutäuschen.

## Wie gestaltest du Bedienaktionen verständlich und kontrollierbar?

Jede Bedienaktion braucht einen klaren Namen, erkennbare Voraussetzungen und eine verständliche Rückmeldung. Der Nutzer muss wissen, welche Maschine und welcher Vorgang betroffen sind.

„Übernehmen“ ist ohne Kontext zu ungenau. „Rezept für Maschine 2 übernehmen“ beschreibt die Aktion besser. Bei einer Parameteränderung sollte zusätzlich erkennbar sein, welche Werte geändert werden.

Bestätigungen sind dort sinnvoll, wo sie eine relevante Entscheidung absichern. Wenn jede kleine Navigation eine Rückfrage auslöst, werden Dialoge schnell routinemäßig weggeklickt.

Für einen Bestätigungsdialog kannst du festlegen:

- Welche Aktion wird angefordert?
- Welche Maschine ist betroffen?
- Welche Voraussetzungen gelten?
- Was passiert nach der Bestätigung?
- Welche Möglichkeit zum Abbrechen besteht?

Deaktivierte Aktionen brauchen eine Erklärung. „Start nicht verfügbar: Kein Auftrag ausgewählt“ hilft dem Bediener, den fehlenden Schritt zu erkennen.

### Betriebsarten getrennt darstellen

Automatik, Einrichten und Wartung sollten deutlich unterscheidbar sein. Passe verfügbare Aktionen an die tatsächlich gemeldete Betriebsart an.

Ein Wechsel der Ansicht darf keine Betriebsart ändern. Ebenso darf eine Benutzerrolle keine vorhandene Maschinenfreigabe ersetzen.

Ein gewöhnliches Web Interface ist keine nachgewiesene Sicherheitsfunktion. Funktionen wie Not-Halt und Schutzverriegelungen müssen im dafür vorgesehenen Maschinenkonzept umgesetzt werden. Plane eine Browser-Schaltfläche nicht als Ersatz für diese Einrichtungen.

### Berechtigungen auf dem Server prüfen

Das Ausblenden eines Buttons verbessert die Übersicht, verhindert aber keine unzulässige Anfrage. Prüfe Berechtigungen deshalb bei jeder relevanten Aktion erneut auf dem Server.

Dokumentiere Parameteränderungen mit Benutzer, Zeitpunkt, altem Wert, neuem Wert und Ergebnis. Dadurch lassen sich Änderungen später nachvollziehen, ohne sich auf den sichtbaren Zustand eines Browserfensters verlassen zu müssen.

## Wie prüfst du den Prototyp unter realistischen Bedingungen?

Prüfe den Prototyp anhand echter Aufgaben und absichtlich gestörter Abläufe. Eine Oberfläche muss auch dann verständlich bleiben, wenn Daten fehlen oder Rückmeldungen verspätet eintreffen.

Bitte einen Bediener zunächst, den Maschinenzustand zu erklären. Kann er ohne zusätzliche Hinweise sagen, welcher Auftrag läuft und ob die Daten aktuell sind?

Lass ihn anschließend einen typischen Ablauf durchführen: Auftrag auswählen, Voraussetzungen prüfen, Aktion anfordern und Ergebnis kontrollieren.

Beobachte dabei, wo er sucht, zögert oder denselben Button mehrfach drückt. Solche Stellen zeigen, welche Rückmeldung oder Beschriftung fehlt.

### Diese Situationen gehören in die Prüfung

- Die Verbindung bricht während einer Anforderung ab.
- Ein Benutzer verliert seine Berechtigung.
- Ein anderer Bediener ändert einen Parameter.
- Die Maschine wechselt unerwartet ihre Betriebsart.
- Eine Anforderung wird abgelehnt.
- Die Seite wird während eines laufenden Vorgangs neu geladen.

Prüfe zusätzlich das tatsächliche Bediengerät. Ein Entwurf auf dem Laptop sagt wenig über einen Touchscreen neben der Anlage aus.

Teste Lesbarkeit, Fingerbedienung, Tastaturfokus und längere Meldungstexte. Wenn Handschuhe vorgesehen sind, gehören sie in den Bedienversuch.

Ein heller und ein dunkler Entwurf sollten unter den realen Lichtverhältnissen verglichen werden. Wähle die Variante, in der Zustände und Texte zuverlässig erkannt werden.

Auch eine sorgfältig gestaltete Vorlage bleibt zunächst ein Prototyp. Sie enthält noch keine validierte Maschinenintegration. VP0 kann für eine ergänzende iOS-App eine Designquelle sein; industrielle Bedienlogik, Kommunikationsverhalten und Freigaben müssen aus deinem konkreten Projekt kommen.

## Das solltest du wählen

Wähle für eine einzelne Maschine eine kompakte Oberfläche mit festem Statusbereich, aufgabenbezogenen Ansichten und wenigen eindeutigen Aktionen. Für mehrere Anlagen ergänzt du eine beobachtende Übersicht mit klaren Detailansichten.

Wenn bereits ein industrielles HMI-System vorhanden ist, prüfe zuerst dessen Schnittstellen und Erweiterungsmöglichkeiten. Eine individuelle Web-Oberfläche lohnt sich besonders dann, wenn du zusätzliche Abläufe oder eine geräteübergreifende Darstellung benötigst.

Beginne mit Produktionsübersicht, Alarmansicht und einem einzigen vollständig beschriebenen Bedienablauf. Ergänze Parameterverwaltung und Diagnose erst, wenn Maschinenzustände, Berechtigungen und Befehlsrückmeldungen eindeutig definiert sind.

Ein hilfreicher Entwurf zeigt bei jeder Aktion denselben Zusammenhang: Was wurde angefordert, was wurde bestätigt und was macht die Maschine jetzt?

## Häufig gestellte Fragen (FAQ)

### Was ist ein Maschinensteuerung Web Interface?

Ein Maschinensteuerung Web Interface ist eine browserbasierte Oberfläche zur Anzeige von Maschinenzuständen und zur Anforderung freigegebener Bedienaktionen. Es verbindet Darstellung, Benutzerrechte und Maschinenkommunikation. Welche Funktionen verfügbar sind, hängt von Steuerung, Schnittstellen und Betriebskonzept ab.

### Was ist die beste Vorlage für eine Maschinensteuerung?

Für eine einzelne Maschine ist eine Vorlage mit dauerhaft sichtbarem Status, klarer Aufgabenansicht und fester Aktionszone ein guter Einstieg. Für mehrere Maschinen eignet sich eine zusätzliche Übersichtsseite. Entscheidend sind die tatsächlichen Bedienaufgaben und die Darstellung von Fehler- und Verbindungszuständen.

### Kann ich eine Maschinenoberfläche mit Tailwind CSS gestalten?

Ja, Tailwind CSS eignet sich für die Gestaltung von Navigation, Statusanzeigen, Formularen und Aktionsbereichen. Maschinenkommunikation, Berechtigungen und Befehlsverarbeitung benötigen zusätzliche Anwendungskomponenten. Ein fertig gestalteter Bildschirm enthält diese Funktionen noch nicht automatisch.

### Kann ein Web Interface einen Not-Halt ersetzen?

Ein gewöhnliches Web Interface darf nicht als Ersatz für die vorgesehenen Not-Halt-Einrichtungen eingeplant werden. Die erforderlichen Sicherheitsfunktionen gehören in das dafür ausgelegte Maschinenkonzept. Die Web-Oberfläche kann Zustände anzeigen und freigegebene Betriebsaktionen unterstützen.

### Eignet sich VP0 für industrielle Bedienoberflächen?

VP0 liefert kostenlose Design-Startpunkte für iOS-Apps, hauptsächlich mit Expo React Native. Für eine mobile Wartungs- oder Service-App kann das eine passende visuelle Grundlage sein. Für eine industrielle Web-HMI brauchst du ein eigenes Bedienkonzept und eine fachlich geprüfte Maschinenintegration.
