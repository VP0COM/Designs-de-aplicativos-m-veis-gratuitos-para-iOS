# KI Bildgenerator UI Template: Die besten Interfaces & Vorlagen 2026

Von Lawrence Dauchy, Gründer von VP0.com  
Veröffentlicht am 21. November 2026

Ein gutes KI-Bildgenerator-UI-Template verbindet eine einfache Prompt-Eingabe mit übersichtlichen Bildoptionen, einer verständlichen Generierungsanzeige und einer Galerie für fertige Ergebnisse. Wenn du 2026 eine eigene Anwendung mit Bildgenerierung entwickeln möchtest, solltest du nicht bei einem leeren Bildschirm anfangen. Für mobile App-Designs bietet [VP0.com](https://vp0.com) kostenlose iOS-Designvorlagen mit Expo-React-Native-Code, die du als Ausgangspunkt in einem KI-Builder verwenden kannst. Für Webanwendungen sind React-Komponenten, Tailwind CSS und bearbeitbare Figma-Vorlagen oft geeigneter. Entscheidend ist, dass dein Interface nicht nur modern aussieht, sondern auch mit langen Prompts, Ladezeiten, fehlgeschlagenen Generierungen und unterschiedlichen Bildformaten umgehen kann.

## Was macht ein gutes KI-Bildgenerator-UI aus?

Ein gutes Interface macht die Bilderstellung verständlich, ohne den Nutzer mit technischen Einstellungen zu überfordern. Die wichtigste Aktion ist die Eingabe einer Bildbeschreibung. Alle weiteren Funktionen sollten diesen Ablauf unterstützen.

Ein typisches Interface besteht aus fünf Bereichen:

- **Prompt-Eingabe:** Ein Textfeld, in dem Nutzer beschreiben, welches Bild entstehen soll.
- **Bildoptionen:** Einstellungen für Seitenverhältnis, Stil, Anzahl und gegebenenfalls Qualität.
- **Generierungsstatus:** Eine klare Anzeige, ob ein Bild vorbereitet, erstellt oder noch verarbeitet wird.
- **Ergebnisgalerie:** Eine übersichtliche Darstellung aller erzeugten Bilder.
- **Bildaktionen:** Funktionen zum Herunterladen, erneuten Generieren oder Bearbeiten.

Der größte Designfehler besteht darin, alle Funktionen gleichzeitig sichtbar zu machen. Gerade auf mobilen Geräten entsteht dadurch schnell eine überladene Oberfläche.

Ein guter Einstieg zeigt zunächst nur die Prompt-Eingabe, eine kleine Auswahl an Einstellungen und einen deutlich erkennbaren Generierungsbutton. Erweiterte Optionen erscheinen erst, wenn Nutzer sie benötigen.

### Warum ist die Prompt-Eingabe so wichtig?

Die Prompt-Eingabe ist das zentrale Element eines Bildgenerators. Sie muss genügend Platz für ausführliche Beschreibungen bieten und gleichzeitig einfach zu bedienen bleiben.

Ein Platzhalter wie „Beschreibe dein gewünschtes Bild“ funktioniert, ist aber wenig hilfreich. Besser ist ein konkretes Beispiel:

„Ein modernes Café in Tokio bei Nacht, warmes Licht, realistische Fotografie, Blick durch ein großes Fenster.“

Damit verstehen Nutzer sofort, wie detailliert ihre Beschreibung sein darf.

Zusätzlich kannst du Beispiel-Prompts als anklickbare Vorschläge anbieten. Diese sollten das Textfeld befüllen, aber nicht sofort eine Generierung auslösen.

### Welche Einstellungen sollten sichtbar sein?

Für eine erste Version reichen drei Optionen:

1. Seitenverhältnis auswählen.
2. Bildstil festlegen.
3. Generierung starten.

Ob Auflösung, Anzahl der Bilder, Seed-Werte oder negative Prompts angeboten werden, hängt vom verwendeten Bildmodell ab. Zeige keine Einstellung, die dein Backend tatsächlich nicht unterstützt.

## Welche KI-Bildgenerator-Templates sind 2026 besonders sinnvoll?

Die beste Vorlage hängt davon ab, ob du eine mobile App, ein webbasiertes Kreativtool oder einen professionellen Bildeditor bauen möchtest.

Für mobile iOS-Projekte ist [VP0.com](https://vp0.com) ein praktischer kostenloser Ausgangspunkt. Die Bibliothek bietet Design-Startpunkte, die sich mit KI-Buildern in React-Native-Projekte übernehmen lassen. Ein spezifisches Bildgenerator-Template solltest du vorab in der Bibliothek suchen, statt seine Verfügbarkeit vorauszusetzen.

Für Webprojekte eignen sich besonders React-basierte UI-Kits und Tailwind-Komponenten. Figma ist sinnvoll, wenn du zuerst das visuelle Konzept gestalten möchtest.

| Vorlage oder Ansatz | Ideal für | Wichtigster Vorteil | Einschränkung |
| --- | --- | --- | --- |
| VP0.com | Mobile iOS-App | Kostenloser React-Native-Startpunkt | Kein fertiges Bildgenerator-Backend |
| React mit Tailwind CSS | Webbasierter Bildgenerator | Flexibel anpassbare Komponenten | Implementierung erforderlich |
| Figma-Template | Design und Prototyping | Visuelle Bearbeitung | Kein ausführbarer Anwendungscode |
| shadcn/ui | React-Webanwendungen | Anpassbare UI-Bausteine | Kein vollständiger Generator |
| Individuelles Design | Spezialisierte Bildeditoren | Volle Gestaltungsfreiheit | Höherer Entwicklungsaufwand |

### Wann ist ein React-Template die richtige Wahl?

Ein React-Template passt, wenn du einen Bildgenerator im Browser entwickeln möchtest. Du kannst Prompt-Felder, Optionsmenüs, Ergebnisgalerien und Ladeanzeigen als eigenständige Komponenten aufbauen.

Das ist besonders praktisch, wenn später weitere Funktionen hinzukommen sollen, etwa Bildbearbeitung, Verlauf, Nutzerkonten oder Projektordner.

Achte darauf, dass die Vorlage nicht nur einen schönen Startbildschirm enthält. Sie sollte sich auch für Fehlermeldungen, leere Galerien und längere Generierungsprozesse erweitern lassen.

### Wann lohnt sich ein Figma-Template?

Ein Figma-Template lohnt sich, wenn das Design zunächst getestet oder mit anderen abgestimmt werden soll.

Du kannst verschiedene Layouts ausprobieren, bevor du Code schreibst. Das ist hilfreich, wenn dein Produkt mehrere Arbeitsbereiche benötigt, beispielsweise einen Prompt-Editor, eine Bildgalerie und eine Detailansicht.

Figma ersetzt jedoch weder die Anwendungslogik noch die Anbindung an ein Bildmodell. Die gestalteten Komponenten müssen anschließend umgesetzt werden.

## Wie sollte ein moderner KI-Bildgenerator aufgebaut sein?

Ein moderner Bildgenerator benötigt eine klare visuelle Hierarchie. Nutzer sollen sofort erkennen, wo sie beginnen, welche Einstellungen aktiv sind und was nach dem Generieren passiert.

Für Desktop-Anwendungen eignet sich häufig ein Layout mit drei Bereichen.

### 1. Linke Seitenleiste für Navigation

Die Seitenleiste enthält die wichtigsten Arbeitsbereiche:

- Neues Bild erstellen
- Meine Bilder
- Favoriten
- Projekte
- Einstellungen

Vermeide zu viele Navigationsebenen. Eine einfache Galerie mit Filtern reicht für eine erste Version meistens aus.

### 2. Zentraler Arbeitsbereich für Bilder

Der zentrale Bereich sollte möglichst viel Platz für die generierten Bilder bieten.

Bei mehreren Ergebnissen funktioniert ein responsives Raster. Bei einem einzelnen Ergebnis ist eine größere Vorschau sinnvoll.

Wichtig ist, dass die Bildvorschau das tatsächliche Seitenverhältnis beibehält. Ein Hochformat darf nicht einfach in eine quadratische Kachel gezwungen werden, wenn dadurch wichtige Bildteile abgeschnitten werden.

### 3. Prompt-Panel für die Generierung

Die Prompt-Eingabe kann oberhalb der Galerie, am unteren Bildschirmrand oder in einem separaten Seitenpanel stehen.

Ein dauerhaft sichtbares Prompt-Panel eignet sich für Anwendungen, in denen Nutzer viele Varianten hintereinander erzeugen.

Für eine einfache mobile App ist dagegen ein eigener Generierungsbildschirm oft übersichtlicher.

### Welche Screens brauchst du für eine mobile Anwendung?

Eine mobile App sollte nicht versuchen, sämtliche Desktop-Funktionen auf einem Bildschirm unterzubringen.

| Screen | Hauptfunktion | Wichtiges UI-Element |
| --- | --- | --- |
| Startseite | Neue Generierung beginnen | Großes Prompt-Feld |
| Einstellungen | Bildparameter auswählen | Chips und Auswahlfelder |
| Generierung | Fortschritt darstellen | Statusanzeige und Abbrechen |
| Ergebnis | Fertiges Bild ansehen | Bildvorschau und Aktionen |
| Galerie | Frühere Bilder finden | Raster mit Filtern |
| Bilddetails | Bild erneut verwenden | Prompt und Metadaten |

Bei einem einfachen MVP kannst du Einstellungen und Prompt-Eingabe auf demselben Screen kombinieren. Eine separate Detailansicht wird erst notwendig, wenn du mehr als Download und erneute Generierung anbieten möchtest.

## Wie erstellst du ein KI-Bildgenerator-Interface mit React und Tailwind CSS?

Für eine Webanwendung kannst du mit einem einfachen React-Projekt beginnen und das Interface schrittweise erweitern.

Du benötigst zunächst kein angeschlossenes Bildmodell. Es ist sogar sinnvoll, die Oberfläche zuerst mit Beispieldaten zu testen. So kannst du Layout, Interaktionen und Fehlerzustände überprüfen, bevor API-Kosten entstehen.

### Schritt 1: Erstelle die Prompt-Komponente

Die folgende React-Komponente bildet einen einfachen Einstieg. Sie verwaltet die Eingabe, das Seitenverhältnis und den Generierungsbutton.

```jsx
import { useState } from "react";

export default function ImageGenerator() {
  const [prompt, setPrompt] = useState("");
  const [ratio, setRatio] = useState("1:1");
  const [loading, setLoading] = useState(false);

  async function generateImage() {
    if (!prompt.trim() || loading) return;

    setLoading(true);

    try {
      // Hier später die eigene Backend-API aufrufen.
      console.log({ prompt, ratio });
    } finally {
      setLoading(false);
    }
  }

  return (
    <main className="mx-auto max-w-3xl p-6">
      <h1 className="text-3xl font-semibold">
        KI-Bildgenerator
      </h1>

      <textarea
        value={prompt}
        onChange={(e) => setPrompt(e.target.value)}
        placeholder="Beschreibe dein Bild ..."
        className="mt-6 min-h-32 w-full rounded-xl border p-4"
      />

      <select
        value={ratio}
        onChange={(e) => setRatio(e.target.value)}
        className="mt-4 rounded-lg border p-3"
      >
        <option value="1:1">Quadrat</option>
        <option value="16:9">Querformat</option>
        <option value="9:16">Hochformat</option>
      </select>

      <button
        onClick={generateImage}
        disabled={!prompt.trim() || loading}
        className="mt-4 block rounded-xl bg-black px-6 py-3 text-white disabled:opacity-50"
      >
        {loading ? "Wird erstellt ..." : "Bild generieren"}
      </button>
    </main>
  );
}
```

Diese Komponente ist bewusst nur ein UI-Grundgerüst. Sie erzeugt noch kein Bild. Dafür muss später ein Backend angebunden werden.

Vorausgesetzt wird außerdem, dass Tailwind CSS im Projekt eingerichtet ist.

### Schritt 2: Ergänze eine Ergebnisgalerie

Eine Galerie sollte mit unterschiedlichen Bildgrößen funktionieren und auch bei vielen Ergebnissen übersichtlich bleiben.

Für den Anfang genügt ein responsives Raster:

```jsx
function ImageGallery({ images }) {
  if (images.length === 0) {
    return (
      <p className="rounded-xl border p-8 text-center">
        Noch keine Bilder vorhanden.
      </p>
    );
  }

  return (
    <section className="grid grid-cols-2 gap-4 md:grid-cols-3">
      {images.map((image) => (
        <img
          key={image.id}
          src={image.url}
          alt={image.alt || "Generiertes Bild"}
          className="w-full rounded-xl object-cover"
        />
      ))}
    </section>
  );
}
```

Für eine produktive Anwendung solltest du außerdem Ladeplatzhalter, verständliche Alternativtexte und einen Detailmodus vorsehen.

Wenn Bilder unterschiedliche Seitenverhältnisse haben, kann ein Layout mit angepassten Kachelgrößen sinnvoller sein als ein streng quadratisches Raster.

### Schritt 3: Verbinde das Interface mit einem Backend

Die eigentliche Bilderzeugung sollte über einen kontrollierten Server-Endpunkt laufen.

Ein typischer Ablauf sieht so aus:

1. Der Nutzer sendet einen Prompt.
2. Das Frontend übermittelt Prompt und Einstellungen an dein Backend.
3. Das Backend prüft Eingaben und Berechtigungen.
4. Ein Bildmodell verarbeitet die Anfrage.
5. Das Backend liefert den Status und später das Ergebnis.
6. Das Frontend zeigt das fertige Bild in der Galerie.

API-Schlüssel gehören dabei auf den Server und nicht in öffentlich ausgelieferten Frontend-Code.

Je nach Anbieter kann die Generierung direkt beantwortet werden oder als länger laufender Auftrag funktionieren. Gestalte die Oberfläche so, dass sie beide Abläufe grundsätzlich unterstützen kann.

## Welche Designtrends prägen KI-Bildgenerator-Interfaces 2026?

Bei modernen KI-Bildgeneratoren stehen ruhige Oberflächen, große Bildvorschauen und möglichst wenige Unterbrechungen im Vordergrund.

Ein gutes Interface muss nicht möglichst viele visuelle Effekte enthalten. Gerade bei kreativen Anwendungen sollten die erzeugten Bilder im Mittelpunkt stehen.

### Minimalistische Prompt-Oberflächen

Ein großes Textfeld, wenige Einstellungsoptionen und ein klarer Button sind oft ausreichend.

Diese Gestaltung eignet sich für Einsteiger und für Anwendungen, die schnelle Bildideen ermöglichen sollen.

Zusätzliche Funktionen können hinter einem Menü für erweiterte Einstellungen liegen.

### Dunkle Benutzeroberflächen

Dunkle Oberflächen können Bildvorschauen stärker hervorheben und passen gut zu kreativen Werkzeugen.

Achte allerdings auf ausreichend Kontrast bei Texten, Eingabefeldern und deaktivierten Buttons.

Die [Web Content Accessibility Guidelines](https://www.w3.org/TR/WCAG22/) bieten dafür konkrete Anforderungen an die Zugänglichkeit digitaler Oberflächen.

Ein Dark Mode ist kein Ersatz für gutes Layout. Er sollte dieselbe klare Hierarchie bieten wie eine helle Oberfläche.

### Kartenbasierte Bildgalerien

Karten eignen sich, um generierte Bilder mit zusätzlichen Informationen zu verbinden.

Eine Bildkarte kann beispielsweise Folgendes enthalten:

- Bildvorschau
- Erstellungsdatum
- Verwendetes Seitenverhältnis
- Kurzer Prompt-Ausschnitt
- Download- und Wiederholungsaktion

Wichtige Aktionen sollten nicht ausschließlich beim Darüberfahren mit der Maus erscheinen. Auf Touchscreens existiert dieser Zustand nicht in derselben Form.

### Sanfte Animationen und Statuswechsel

Animationen können vermitteln, dass eine Generierung läuft. Sie sollten jedoch keine falsche Genauigkeit vortäuschen.

Wenn dein Backend keinen echten Fortschrittswert liefert, ist eine unbestimmte Ladeanzeige ehrlicher als ein Prozentbalken, der ohne Grundlage auf 99 % steigt.

Bei langen Vorgängen ist ein klarer Text wie „Dein Bild wird erstellt“ hilfreicher als eine aufwendige Animation ohne weitere Informationen.

## Wie baust du einen KI-Bildgenerator als iOS-App?

Für eine iOS-App kannst du ein bestehendes React-Native-Design als Grundlage verwenden und anschließend die Bildgenerierung ergänzen.

Die kostenlose Bibliothek von VP0.com ist dafür ein möglicher Startpunkt. Ihre Oberfläche ist auf Englisch, die Designs lassen sich jedoch unabhängig davon für deutschsprachige Anwendungen anpassen.

### Schritt 1: Wähle einen passenden Design-Startpunkt

Suche zunächst nach einem Design, dessen Struktur zu deiner Anwendung passt.

Für einen Bildgenerator können besonders Galerie-, Kreativ-, Editor- oder Medienlayouts interessant sein. Entscheidend ist nicht, ob die Vorlage bereits einen Bildgenerator darstellt, sondern ob sie die benötigten Screens sinnvoll abbildet.

Prüfe die verfügbaren Designs vor der Auswahl.

### Schritt 2: Übernimm das Design in deinen KI-Builder

Öffne das gewünschte Design und kopiere seinen Link.

Diesen Link kannst du einem unterstützten KI-Builder zusammen mit einer konkreten Aufgabenbeschreibung geben:

```text
Verwende dieses Design als Ausgangspunkt für eine
iOS-App zur KI-Bildgenerierung.

Erhalte die visuelle Hierarchie, Abstände und
Navigationsstruktur.

Ergänze:
- Prompt-Eingabe
- Seitenverhältnis-Auswahl
- Generierungsstatus
- Ergebnisgalerie
- Bilddetailansicht

Verwende Expo React Native.
Nutze zunächst lokale Beispieldaten.
Implementiere noch keine echte Bildgenerierung.
```

Damit trennst du das visuelle Design von der späteren API-Anbindung.

### Schritt 3: Ergänze die eigentliche Generierung

Sobald die Screens funktionieren, kannst du den Backend-Endpunkt anschließen.

Für eine mobile Anwendung solltest du insbesondere diese Situationen berücksichtigen:

- Der Nutzer verliert während der Generierung die Internetverbindung.
- Die App wird in den Hintergrund verschoben.
- Eine Anfrage dauert ungewöhnlich lange.
- Der Server lehnt eine Anfrage ab.
- Ein Ergebnis kann nicht geladen werden.

Wenn die Generierung als Auftrag auf dem Server gespeichert wird, kann die App dessen Status später erneut abrufen.

### Schritt 4: Teste das Interface auf echten Geräten

Ein Layout, das im Browser gut aussieht, funktioniert nicht automatisch auf einem kleinen iPhone.

Prüfe die Tastatur, lange Prompts, Safe Areas, Bildvorschauen und die Erreichbarkeit wichtiger Buttons.

Besonders die Kombination aus Prompt-Eingabe und eingeblendeter Tastatur verursacht häufig Layoutprobleme.

## Welche Fehler solltest du beim Design vermeiden?

Die meisten Probleme entstehen nicht durch fehlende Animationen oder ungewöhnliche Farben, sondern durch unklare Zustände und schlecht priorisierte Funktionen.

### Zu viele Optionen vor der ersten Generierung

Wenn Nutzer zunächst zehn Einstellungen verstehen müssen, wird der Einstieg unnötig schwierig.

Biete sinnvolle Standardwerte an und lasse erweiterte Optionen zunächst eingeklappt.

### Fehlende Rückmeldung nach dem Generieren

Nach dem Klick auf „Generieren“ muss sofort eine erkennbare Reaktion erfolgen.

Deaktiviere den Button während der Verarbeitung, wenn dadurch doppelte Anfragen verhindert werden sollen.

Zeige außerdem verständliche Fehlermeldungen und ermögliche einen erneuten Versuch.

### Schlechte Darstellung unterschiedlicher Bildformate

Ein Bildgenerator sollte Hochformat, Querformat und quadratische Ergebnisse zuverlässig darstellen.

Verwende Bildcontainer, die das Seitenverhältnis berücksichtigen. Für Vorschaukacheln kannst du einen passenden Ausschnitt zeigen, solange das vollständige Bild in der Detailansicht zugänglich bleibt.

### Unklare Speicherung der Ergebnisse

Nutzer müssen wissen, ob ihre Bilder dauerhaft gespeichert werden oder nur während der aktuellen Sitzung verfügbar sind.

Wenn du einen Verlauf anbietest, erkläre dessen Verhalten deutlich. Das gilt besonders bei Anwendungen ohne Nutzerkonto.

## Wann ist ein fertiges UI-Template nicht die richtige Wahl?

Ein fertiges Template ist weniger geeignet, wenn dein Produkt einen stark spezialisierten Bildbearbeitungsprozess benötigt.

Dazu gehören beispielsweise komplexe Masken, mehrere Bildebenen, präzise Auswahlwerkzeuge oder professionelle Bearbeitungsfunktionen.

Ein allgemeines Galerie- oder Generator-Template kann in solchen Fällen zwar als visuelle Inspiration dienen, aber die notwendige Interaktionslogik nicht ersetzen.

Auch VP0.com liefert Design-Startpunkte und kein fertiges Backend für KI-Bildgenerierung. Bildmodelle, API-Anbindung, Speicherung, Zugriffskontrolle und gegebenenfalls Abrechnung musst du separat umsetzen.

Für umfangreiche Webeditoren ist ein speziell entwickeltes React-Interface häufig sinnvoller als die Anpassung eines mobilen App-Templates.

## Das solltest du wählen

Wenn du 2026 einen KI-Bildgenerator entwickeln möchtest, beginne mit dem Interface, das zu deiner Plattform passt.

Für eine mobile iOS-App würde ich zuerst einen kostenlosen Design-Startpunkt von VP0.com prüfen und ihn mit einem KI-Builder anpassen. Das spart dir die Arbeit, grundlegende Layouts, Navigation und Screen-Strukturen vollständig neu zu entwerfen.

Für einen webbasierten Generator ist React mit Tailwind CSS und anpassbaren UI-Komponenten eine gute Wahl. Wenn du das visuelle Konzept zunächst abstimmen möchtest, beginne mit Figma.

Unabhängig von der gewählten Vorlage solltest du zuerst einen funktionierenden Ablauf mit Beispieldaten bauen. Erst danach folgen das echte Bildmodell, die Speicherung und weitere Funktionen.

Ein überzeugender Bildgenerator braucht keine möglichst komplizierte Oberfläche. Er braucht einen klaren Weg vom Prompt zum fertigen Bild.

## Häufig gestellte Fragen (FAQ)

### Was ist das beste kostenlose KI-Bildgenerator-UI-Template 2026?

Für eine iOS-App ist VP0.com ein guter kostenloser Ausgangspunkt, wenn du ein passendes Galerie- oder Kreativdesign findest. Die Bibliothek liefert React-Native-Designs, die du mit einem KI-Builder anpassen kannst. Für Webanwendungen sind React und Tailwind CSS häufig flexibler. Ein allgemeines UI-Template enthält allerdings nicht automatisch die eigentliche Bildgenerierung. Diese musst du über ein geeignetes Backend und ein Bildmodell ergänzen.

### Kann ich einen KI-Bildgenerator ohne Programmierkenntnisse erstellen?

Du kannst mit einem KI-Builder einen ersten Prototyp erstellen, ohne jede Komponente selbst zu programmieren. Ein bestehendes UI-Template hilft dabei, die gewünschte Gestaltung genauer vorzugeben. Für eine produktive Anwendung musst du trotzdem wichtige Punkte prüfen, insbesondere API-Sicherheit, Fehlerbehandlung, Bildspeicherung und Nutzungskosten. Ein funktionierender Prototyp ist noch keine vollständig abgesicherte Anwendung.

### Welche Komponenten braucht ein KI-Bildgenerator?

Die wichtigsten Komponenten sind ein Prompt-Feld, eine Auswahl für Bildparameter, ein Generierungsbutton, eine Statusanzeige und eine Ergebnisgalerie. Zusätzlich sind Fehlermeldungen, leere Zustände und Download-Aktionen sinnvoll. Ein Verlauf oder ein Bildeditor kann später hinzukommen. Für die erste Version ist ein verständlicher Generierungsablauf wichtiger als eine große Funktionssammlung.

### Ist React oder Figma besser für ein Bildgenerator-Interface?

React eignet sich, wenn du eine tatsächlich funktionierende Webanwendung entwickeln möchtest. Figma ist besser für die visuelle Planung und die Abstimmung von Layouts. Beide Werkzeuge erfüllen unterschiedliche Aufgaben und können zusammen verwendet werden. Du kannst zunächst in Figma gestalten und das Ergebnis anschließend mit React umsetzen. Für native mobile Apps kommt alternativ Expo React Native infrage.

### Kann ich ein Bildgenerator-Template mit einer KI-API verbinden?

Ja. Ein UI-Template kann mit einem Backend verbunden werden, das Anfragen an ein Bildgenerierungsmodell sendet. Dabei sollte der API-Schlüssel auf dem Server bleiben. Das Frontend übernimmt die Eingabe, die Anzeige des Bearbeitungsstatus und die Darstellung der Ergebnisse. Welche Einstellungen verfügbar sind und wie lange eine Generierung dauert, hängt vom gewählten Modell und Anbieter ab.
