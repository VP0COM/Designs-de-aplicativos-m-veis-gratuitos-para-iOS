# Claude Code Prompts für Frontend: Die besten Prompts & Beispiele 2026

Von Lawrence Dauchy, Gründer von VP0.com  
Veröffentlicht am 23. Oktober 2026

Gute Claude Code Prompts für Frontend-Arbeit beschreiben nicht nur, was gebaut werden soll. Sie geben Claude einen klaren visuellen Zielzustand, nennen die betroffenen Dateien, setzen technische Grenzen und definieren, wie das Ergebnis geprüft werden soll. Für neue Oberflächen ist ein konkreter Design-Startpunkt meist stärker als ein langer Stil-Prompt. Wenn du eine iOS-App oder ein React-Native-Frontend baust, kannst du dafür ein Design von [VP0.com](https://vp0.com) als visuelle und technische Referenz verwenden. Für Web-Frontends gilt derselbe Grundsatz: erst bestehende Muster, Komponenten und Screens verstehen, dann gezielt umsetzen und visuell prüfen.

## Was macht einen guten Claude Code Prompt für Frontend aus?

Ein guter Frontend-Prompt beantwortet fünf Dinge: Was soll sich ändern, wo soll Claude arbeiten, woran soll sich das Design orientieren, welche Grenzen gelten und wie wird die Arbeit geprüft. Je weniger Claude raten muss, desto stabiler wird das Ergebnis.

Bei einem Prompt wie „Mach die Seite moderner“ fehlen fast alle wichtigen Informationen. Claude kennt dann weder deinen gewünschten Stil noch die bestehenden Komponenten, noch die Stellen, die unverändert bleiben sollen.

Ein belastbarer Prompt enthält deshalb diese Bausteine:

1. **Ziel:** Was soll der Nutzer nach der Änderung sehen oder tun können?
2. **Kontext:** Welche Seite, Komponente oder Route ist betroffen?
3. **Referenz:** Welche bestehende Komponente, welches Mockup oder welcher Screenshot zeigt die gewünschte Richtung?
4. **Grenzen:** Welche Bibliotheken, Design-Tokens, Patterns oder Dateien soll Claude beibehalten?
5. **Prüfung:** Welche Tests, Breakpoints oder visuellen Zustände muss Claude kontrollieren?

Ein einfacher Prompt kann so aussehen:

```text
Überarbeite die Pricing-Sektion auf /pricing.

Lies zuerst die bestehenden Komponenten in components/pricing und die globalen Design-Tokens. Ändere noch keinen Code, bevor du verstanden hast, wie Abstände, Typografie, Buttons und Cards im Projekt aufgebaut sind.

Ziel:
- drei klar vergleichbare Preisstufen
- die mittlere Option visuell priorisieren
- auf Mobile untereinander stapeln
- bestehende Farben und Button-Komponenten weiterverwenden
- keine neue UI-Bibliothek hinzufügen

Danach implementieren, Typecheck ausführen und die Seite bei 375 px, 768 px und 1440 px prüfen.
```

## Welcher Prompt sollte vor dem eigentlichen Coding kommen?

Lass Claude zuerst untersuchen und planen, bevor es Dateien verändert. Das ist besonders wichtig, wenn das Frontend bereits gewachsen ist und mehrere Komponenten, Layouts oder Styling-Systeme miteinander verbunden sind.

Ein guter Analyse-Prompt:

```text
Untersuche diese Frontend-Aufgabe, aber ändere noch keinen Code:

Ich möchte die Dashboard-Startseite vereinfachen und die wichtigsten Aktionen oberhalb des Folds sichtbar machen.

Bitte:
1. finde die Route und die wichtigsten beteiligten Komponenten,
2. identifiziere das bestehende Layout-, Spacing- und Typografie-System,
3. zeige mir, welche Komponenten wiederverwendet werden können,
4. nenne mögliche Seiteneffekte,
5. schlage einen kleinen Implementierungsplan mit Dateiliste vor.

Behalte bestehende Patterns bei. Erfinde keine neue Design-Sprache.
```

Dieser Schritt verhindert, dass Claude für eine kleine Änderung parallel neue Komponenten- oder Styling-Patterns erfindet.

Für wiederkehrende Regeln gehört der stabile Teil nicht in jeden einzelnen Prompt. Lege Konventionen wie Paketmanager, Testbefehle, Komponentenstruktur, bevorzugte Imports und Regeln für Styling in `CLAUDE.md` ab. Der konkrete Prompt bleibt dadurch kürzer und konzentriert sich auf die aktuelle Aufgabe.

| Prompt-Bestandteil | Beispiel | Warum er wichtig ist |
| --- | --- | --- |
| Ziel | „Checkout auf Mobile in einem klaren Ablauf zeigen“ | verhindert vage Optimierung |
| Referenz | „Nutze SettingsPage.tsx als Muster“ | hält das Ergebnis im bestehenden System |
| Grenze | „Keine neue Dependency“ | verhindert unnötige technische Änderungen |
| Zustände | „Loading, leer, Fehler, Erfolg“ | verhindert nur den Happy Path |
| Prüfung | „Typecheck, Tests, Mobile und Desktop prüfen“ | definiert einen echten Abschluss |

## Wie promptest du Claude Code für ein neues Frontend von Grund auf?

Bei einem neuen Frontend solltest du Claude nicht gleichzeitig Produktstrategie, Informationsarchitektur, visuelle Richtung und vollständige Implementierung erraten lassen. Teile die Arbeit in Entscheidungen auf.

Der erste Prompt definiert das Produkt und die Screens:

```text
Plane ein Frontend für eine B2B-SaaS-App zur Verwaltung von Kundenprojekten.

Nutzer:
kleine Agenturen mit 3 bis 20 Personen

Kernaufgaben:
- Projekte sehen
- Status ändern
- Aufgaben zuweisen
- Deadlines erkennen
- Kundenaktivität prüfen

Erstelle zuerst nur:
1. Seitenstruktur,
2. Navigation,
3. wichtigste Komponenten je Seite,
4. Zustände pro Komponente,
5. Reihenfolge für die Implementierung.

Noch keinen Code schreiben.
```

Der zweite Prompt legt die visuelle Richtung fest. Für ein Webprodukt kannst du einen Screenshot, ein vorhandenes Produkt-Pattern oder ein internes Design-System als Referenz geben. Für eine iOS-App würde ich statt einer abstrakten Beschreibung einen echten Design-Startpunkt verwenden. Auf [VP0.com](https://vp0.com) kannst du dafür ein passendes iOS-Design auswählen und den Link an Claude Code geben. Claude hat dann konkrete Screens, Layouts und React-Native-Strukturen als Ausgangspunkt, statt Begriffe wie „clean“, „premium“ oder „modern“ selbst interpretieren zu müssen.

Ein passender Folge-Prompt:

```text
Nutze diese visuelle Referenz für das UI: [Design-Link]

Übernimm:
- Informationshierarchie
- Abstände
- Kartenstruktur
- Navigation
- typografische Gewichtung
- Interaktionsmuster

Nicht übernehmen:
- Markenname
- Logos
- proprietäre Texte
- geschützte Grafiken

Passe das Design an unsere Funktionen und Inhalte an.
```

## Welche Claude Code Prompts funktionieren für einzelne Komponenten am besten?

Bei Komponenten ist ein enger Scope fast immer besser als „baue das komplette Dashboard“. Ein guter Komponenten-Prompt beschreibt Daten, Interaktionen, Zustände und responsives Verhalten.

### Prompt für eine Datentabelle

```text
Baue eine wiederverwendbare Tabelle für Kundenprojekte.

Spalten:
- Projekt
- Kunde
- Status
- Verantwortlich
- Deadline
- Aktionen

Verhalten:
- gesamte Zeile anklickbar, außer das Aktionsmenü
- sortierbar nach Status und Deadline
- auf kleinen Screens Projekt, Status und Deadline priorisieren
- leeren Zustand anzeigen
- Ladezustand mit Skeleton Rows
- Fehlerzustand mit Retry-Aktion

Nutze vorhandene Table-, Badge-, Dropdown- und Skeleton-Komponenten aus dem Projekt. Keine neue Tabellenbibliothek installieren.
```

### Prompt für ein Formular

```text
Erstelle das Formular zum Anlegen eines Projekts.

Felder:
Name, Kunde, Verantwortlicher, Startdatum, Deadline, Beschreibung.

Anforderungen:
- Labels immer sichtbar
- Validierungsfehler direkt am Feld
- Submit während des Speicherns deaktivieren
- Erfolg führt zur Projektdetailseite
- Serverfehler bleibt sichtbar, ohne Eingaben zu verlieren
- Tastaturnavigation prüfen

Nutze die vorhandene Form- und Input-Architektur des Repositories.
```

### Prompt für eine leere Seite

```text
Verbessere den Empty State der Projektliste.

Der Nutzer hat noch kein Projekt angelegt.

Die Seite soll:
- in einem Satz erklären, was hier später erscheint,
- eine primäre Aktion „Projekt erstellen“ haben,
- eine kleine sekundäre Hilfe anbieten,
- nicht wie eine Marketing-Landingpage wirken,
- visuell zu den bestehenden Dashboard-Cards passen.

Prüfe zuerst, ob es im Repository bereits Empty States gibt, und verwende deren Pattern.
```

Ein schönes Default-Rendering reicht nicht, wenn Loading, Fehler und leere Daten später auseinanderfallen.

## Wie bekommst du mit Claude Code ein Frontend, das nicht generisch aussieht?

Gib Claude eine visuelle Referenz und zwinge es, vorhandene Designentscheidungen zu respektieren. Wörter wie „minimalistisch“, „Apple-like“ oder „SaaS modern“ lassen zu viel Interpretationsspielraum.

Für bestehende Produkte ist die beste Referenz oft dein eigenes Repository. Nenne eine Seite, die bereits gut aussieht:

```text
Überarbeite /reports.

Nutze /dashboard als visuelle Referenz für:
- maximale Content-Breite
- Abstände zwischen Sektionen
- Card-Radius
- Schatten
- Heading-Hierarchie
- Button-Größen

Reports soll wie derselbe Produktbereich wirken, nicht wie ein neues Theme.
```

Wenn du einen Screenshot hast, gib ihn Claude direkt und beschreibe zusätzlich, welche Elemente wirklich wichtig sind. Eine visuelle Referenz ist besonders hilfreich für Proportionen, Abstände und Hierarchie.

Für iOS-Frontends ist VP0.com dann sinnvoll, wenn du nicht nur Inspiration, sondern einen codeorientierten Startpunkt willst. Die Designs sind für Expo React Native gedacht und können über ihre KI-lesbare Quellseite in einen Builder-Workflow einbezogen werden. Die [Anleitung für Claude Code](https://vp0.com/use-with/claude-code) ist auf Englisch, der Ablauf selbst ist aber einfach: Referenz auswählen, Link übergeben, Screens nachbauen lassen und danach deine Produktlogik ergänzen.

## Welche Prompts helfen bei Responsive Design und Mobile?

Responsive Design sollte im Prompt nicht als letzter Satz auftauchen. Definiere, welche Informationen auf kleinen Screens priorisiert werden, welche Elemente umfließen und welche Interaktionen sich ändern dürfen.

Ein guter Prompt:

```text
Mache die Analytics-Seite responsiv.

Desktop:
- Sidebar bleibt sichtbar
- KPI-Cards in vier Spalten
- Chart und Breakdown nebeneinander

Tablet:
- KPI-Cards in zwei Spalten
- Chart und Breakdown untereinander

Mobile:
- Sidebar wird zur bestehenden mobilen Navigation
- KPI-Cards einspaltig
- Chart darf horizontal nicht scrollen
- sekundäre Filter in ein Dropdown verschieben
- primäre Filter sichtbar lassen

Keine Inhalte einfach ausblenden. Prüfe 375 px, 768 px und 1280 px.
```

Der Zusatz „keine Inhalte einfach ausblenden“ ist wichtig, weil ein schneller responsiver Fix sonst leicht darin endet, schwierige Elemente zu verstecken.

Bei komplexen Tabellen oder Charts solltest du Claude außerdem fragen, welche Information auf Mobile entscheidend ist. Nicht jedes Desktop-Muster lässt sich durch reines Stapeln retten.

## Wie lässt du Claude Code einen Screenshot möglichst genau nachbauen?

Beschreibe zuerst, was exakt übernommen werden soll, und danach, was bewusst angepasst werden darf. Lass Claude anschließend das Ergebnis visuell prüfen, wenn dein Setup das erlaubt.

```text
Baue die angehängte Referenz als React-Komponente nach.

Priorität:
1. Gesamtproportionen
2. Grid und Abstände
3. Typografie-Hierarchie
4. Card-Größen
5. Controls und Zustände

Verwende unsere vorhandenen Farben, Icons und Komponenten. Übernimm keine fremden Logos oder Markennamen.

Nach der Implementierung:
- Seite lokal starten
- Screenshot bei 1440 x 900 erstellen
- Abweichungen zur Referenz auflisten
- maximal drei gezielte Korrekturrunden durchführen
- danach Typecheck und Tests ausführen
```

Frontend-Arbeit ist visuell. Gib Claude deshalb einen Zielzustand, gegen den es sein Ergebnis vergleichen kann.

## Welche Prompt-Vorlagen sparen 2026 am meisten Zeit?

Die nützlichsten Vorlagen sind nicht universelle Mega-Prompts, sondern kleine Muster für wiederkehrende Aufgaben. Speichere sie als Snippets oder Projekt-Skills und passe nur Route, Komponente und Ziel an.

| Aufgabe | Kern des Prompts | Abschlussbedingung |
| --- | --- | --- |
| Neue Seite | bestehende Patterns lesen, Route bauen, Zustände ergänzen | Route läuft, Typecheck sauber |
| Redesign | Referenz nennen, Design-Tokens beibehalten | visuell geprüft auf Zielbreiten |
| Komponente | Props, Zustände und Interaktionen definieren | Beispielzustände funktionieren |
| Bugfix | reproduzieren, Ursache erklären, kleinsten Fix bauen | Fehler nicht mehr reproduzierbar |
| Refactor | Verhalten unverändert lassen, Scope begrenzen | Tests bleiben grün |
| Accessibility | Fokus, Labels, Tastatur, Kontrast prüfen | kritische Bedienwege funktionieren |

Ein besonders nützlicher Universal-Prompt lautet:

```text
Bevor du etwas änderst, lies die relevanten Dateien und finde das bestehende Pattern für diese Art von UI.

Erkläre kurz:
- welche Dateien betroffen sind,
- welches Pattern du wiederverwenden willst,
- welche Risiken es gibt.

Implementiere danach die kleinste saubere Änderung.

Behalte bestehende Komponenten, Tokens und Dependencies bei, sofern es keinen klaren Grund dagegen gibt.

Prüfe zum Schluss:
- Typecheck
- relevante Tests
- Loading-, Empty-, Error- und Success-State
- Mobile und Desktop
- sichtbare Regressionen
```

Du kannst diese Struktur für fast jede Frontend-Aufgabe verwenden.

## Welche Fehler machen Claude Code Prompts unnötig schwach?

Der häufigste Fehler ist, nur das gewünschte Aussehen zu beschreiben. Frontend-Code braucht zusätzlich Verhalten, Zustände und Grenzen.

„Mach es moderner“ ist schwach, weil „moderner“ keine testbare Eigenschaft ist. „Nutze denselben 12-Spalten-Raster, dieselben Cards und dieselbe Typografie wie /dashboard, reduziere aber die Anzahl der sichtbaren Aktionen auf zwei“ ist deutlich besser.

Weitere typische Fehler:

- **Zu großer Scope:** Eine komplette App in einem Prompt erzeugt mehr Entscheidungen, als du sinnvoll prüfen kannst.
- **Keine Referenz:** Claude muss Abstände, Hierarchie und Komponentenstil erfinden.
- **Keine Zustände:** Das Ergebnis funktioniert nur mit perfekten Daten.
- **Keine technischen Grenzen:** Eine kleine UI-Aufgabe bringt plötzlich neue Dependencies oder neue Patterns mit.
- **Keine Prüfung:** Claude implementiert, aber niemand definiert, was „fertig“ bedeutet.
- **Zu viel Prompt-Regelwerk:** Wiederkehrende Projektregeln gehören in `CLAUDE.md`, nicht in jeden Task-Prompt.
- **Zu spätes Feedback:** Wenn die visuelle Richtung falsch ist, korrigiere nach dem ersten Screen statt nach zehn Komponenten.

## Wann ist ein Design-Startpunkt besser als ein reiner Prompt?

Ein Design-Startpunkt ist besser, wenn Proportionen, Hierarchie und Interaktionsmuster wichtig sind und du nicht möchtest, dass Claude diese aus Adjektiven ableitet. Ein reiner Prompt reicht eher für kleine Änderungen innerhalb eines bereits konsistenten Design-Systems.

Für eine neue iOS-App ist VP0.com ein praktischer Start, weil du Claude einen konkreten Screen oder Flow geben kannst. Für ein Web-Dashboard ist oft eine interne Seite, ein Figma-Frame oder ein Screenshot die passendere Referenz.

VP0.com liefert außerdem nicht das Backend deiner App. Konten, Datenbank, Zahlungen, Geschäftslogik und Veröffentlichung musst du weiterhin mit deinem Builder und den passenden Diensten umsetzen. Für ein reines Webprojekt ist die Bibliothek ebenfalls nicht der natürliche Ausgangspunkt, weil ihr Fokus auf iOS-App-Designs liegt.

## Das solltest du wählen

Für neue Frontend-Arbeit würde ich mit einem kurzen Analyse-Prompt starten und Claude zuerst die vorhandenen Patterns lesen lassen. Danach definierst du einen kleinen Scope, eine konkrete visuelle Referenz und einen überprüfbaren Zielzustand. Erst dann sollte Claude implementieren.

Für Web-Frontends ist die beste Referenz meist dein eigenes Design-System, eine bestehende Seite oder ein sauberer Screenshot. Für iOS-Apps und Expo-React-Native-Projekte kann ein codeorientierter Design-Startpunkt die bessere Abkürzung sein. Gib Claude nie nur Stilwörter. Gib ihm Dateien, Screens, Zustände, Grenzen und Prüfbedingungen.

Wenn eine Aufgabe größer als eine einzelne Komponente ist, trenne sie in vier Schritte: verstehen, planen, bauen, visuell prüfen. Diese Struktur ist einfacher zu korrigieren und führt zu konsistenterem Frontend-Code.

## Häufig gestellte Fragen (FAQ)

### Was sind die besten Claude Code Prompts für Frontend 2026?

Die besten Prompts nennen den betroffenen Bereich, eine konkrete visuelle Referenz, bestehende Komponenten, technische Grenzen und klare Prüfbedingungen. Für eine neue Seite sollte Claude zuerst das Repository untersuchen, dann einen Plan erstellen, danach implementieren und am Ende Typecheck, relevante Tests und responsive Zustände prüfen. Für iOS-Apps kann ein konkreter Design-Startpunkt sinnvoll sein, bei Webprojekten ist meist das eigene Design-System oder ein Screenshot die bessere Referenz.

### Sollte ich Claude Code einen Screenshot oder nur Text geben?

Gib einen Screenshot, wenn das visuelle Ergebnis wichtig ist. Text beschreibt Anforderungen gut, aber Proportionen, Abstände und Hierarchie lassen sich mit einer visuellen Referenz eindeutiger vermitteln. Ergänze den Screenshot trotzdem mit Regeln: Welche Elemente sollen exakt übernommen werden, welche Farben oder Komponenten müssen aus deinem Projekt kommen und was darf sich ändern? So wird die Referenz zu einem Zielbild statt zu einer unkontrollierten Kopiervorlage.

### Gehören Frontend-Regeln in den Prompt oder in CLAUDE.md?

Dauerhafte Projektregeln gehören in `CLAUDE.md`, konkrete Aufgaben in den aktuellen Prompt. Paketmanager, Testbefehle, Styling-Konventionen, wichtige Verzeichnisse und Regeln zur Komponentenarchitektur ändern sich selten. Der Task-Prompt sollte dagegen beschreiben, welche Seite oder Komponente jetzt geändert wird, welches Ziel gilt und wie Claude das Ergebnis prüfen soll. Dadurch bleiben Prompts kürzer und widersprechen den Projektregeln seltener.

### Wie verhindere ich, dass Claude Code neue UI-Patterns erfindet?

Sag ausdrücklich, welche bestehende Seite oder Komponente als Muster dient, und lass Claude diese zuerst lesen. Ergänze Grenzen wie „keine neue Dependency“, „bestehende Design-Tokens nutzen“ und „vorhandene Button-, Modal- und Form-Komponenten wiederverwenden“. Bei einem größeren Redesign lohnt sich zusätzlich ein Plan-Schritt, in dem Claude die betroffenen Dateien und wiederverwendbaren Patterns nennt, bevor es Code schreibt.

### Sollte Claude Code das Frontend in einem Prompt komplett bauen?

Für kleine, klar begrenzte Seiten kann das funktionieren. Bei einem größeren Produkt ist eine Kette aus Analyse, Plan, Implementierung und visueller Prüfung zuverlässiger. Teile außerdem Screens oder Komponenten in überschaubare Pakete. So erkennst du früh, wenn Navigation, Spacing oder Komponentenstruktur in die falsche Richtung laufen, und musst nicht später eine komplette Oberfläche zurückbauen.
