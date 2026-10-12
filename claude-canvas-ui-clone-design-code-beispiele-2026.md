# Claude Canvas UI Clone: Design, Code & Beispiele 2026

Von Lawrence Dauchy, Gründer von VP0  
Veröffentlicht am 11. Oktober 2026

Ein Claude Canvas UI Clone ist im Kern eine Arbeitsoberfläche, bei der Chat, Inhalt und direkte Bearbeitung nebeneinander funktionieren. Statt dass die KI nur Text in einem Chat ausgibt, entsteht rechts oder in einem separaten Arbeitsbereich ein Dokument, eine Vorschau, ein Codeblock oder eine interaktive Oberfläche, die weiterbearbeitet werden kann.

Wenn du dieses Prinzip 2026 für eine eigene App nachbauen möchtest, solltest du nicht versuchen, Claude Pixel für Pixel zu kopieren. Interessanter ist das Interaktionsmodell: links Kommunikation, rechts Arbeitsfläche, dazwischen ein klarer Übergang zwischen Anweisung und Ergebnis.

Genau daraus lässt sich eine erstaunlich einfache und gleichzeitig hochwertige App-Oberfläche bauen.

## Was ist mit einer Claude Canvas UI eigentlich gemeint?

Der Begriff "Canvas" wird häufig allgemein für die visuelle Arbeitsfläche neben einem KI-Chat verwendet. Bei Claude selbst ist das entsprechende Produktkonzept vor allem über Artifacts bekannt.

Ein Artifact kann beispielsweise ein Dokument, Code, eine Website, ein SVG, ein Diagramm oder eine interaktive React-Komponente sein. Entscheidend ist nicht das konkrete Format, sondern die Trennung zwischen Unterhaltung und Ergebnis.

Für einen Clone bedeutet das:

- Der Chat bleibt ein eigener Bereich.
- Das generierte Ergebnis bekommt eine eigene Fläche.
- Änderungen können direkt am Ergebnis sichtbar werden.
- Nutzer können zwischen verschiedenen Inhalten wechseln.
- Die Oberfläche zeigt deutlich, was Unterhaltung und was Arbeitsobjekt ist.

Diese Trennung macht das Konzept wesentlich nützlicher als einen klassischen Chatbot mit langen Codeblöcken.

## Die einfachste Struktur für einen Claude Canvas Clone

Für einen ersten Prototyp brauchst du keine komplizierte Architektur.

Eine Desktop-Oberfläche kann aus vier Bereichen bestehen:

1. Navigation
2. Chat
3. Canvas
4. Canvas-Toolbar

Die Navigation enthält Projekte oder vergangene Sessions. Der Chat enthält Nachrichten und das Eingabefeld. Der Canvas zeigt das aktuelle Arbeitsobjekt. Die Toolbar enthält kontextbezogene Aktionen wie Vorschau, Code, Kopieren oder Schließen.

Auf kleineren Displays sollte daraus keine zusammengestauchte Drei-Spalten-Oberfläche werden. Dort ist ein Wechsel zwischen Chat und Canvas meistens verständlicher.

## Beispiel für die visuelle Hierarchie

Eine typische Desktop-Struktur könnte so aussehen:

```text
┌──────────────┬────────────────────┬───────────────────────────┐
│              │                    │                           │
│ Navigation   │ Chat               │ Canvas                    │
│              │                    │                           │
│ Chats        │ User message       │ Document / Preview        │
│ Projects     │ AI response        │                           │
│ History      │                    │                           │
│              │                    │                           │
│              │ Prompt input       │ Canvas toolbar            │
└──────────────┴────────────────────┴───────────────────────────┘
```

Die Stärke liegt nicht in außergewöhnlichen visuellen Effekten. Sie entsteht durch klare Größenverhältnisse, ruhige Flächen und eine eindeutige Informationshierarchie.

## Welche Designprinzipien machen die Oberfläche hochwertig?

Viele Claude-Clones sehen sofort nach einem Hobbyprojekt aus, obwohl die einzelnen Komponenten technisch sauber umgesetzt wurden.

Meistens liegt das an fünf Dingen.

### 1. Zu viele sichtbare Container

Nicht jede Komponente braucht einen Rahmen.

Wenn Navigation, Nachrichten, Eingabefeld, Canvas, Toolbar und Karten jeweils einen eigenen Border besitzen, zerfällt die Oberfläche optisch.

Nutze stattdessen Abstand, Hintergrundunterschiede und Typografie zur Gruppierung.

### 2. Zu viele Farben

Eine produktive KI-Oberfläche profitiert von Zurückhaltung.

Eine gute Ausgangsbasis ist:

```css
:root {
  --background: #f7f7f5;
  --surface: #ffffff;
  --text: #1f1f1d;
  --muted: #73736f;
  --border: #e7e7e2;
  --accent: #c96f4a;
}
```

Die konkreten Werte sind weniger wichtig als ihre Rollen.

Definiere ein System und verwende dieselben Tokens überall.

### 3. Schlechte Breiten

Ein Chat sollte nicht automatisch die gesamte verfügbare Fläche nutzen.

Lange Textzeilen werden schwer lesbar. Gleichzeitig braucht ein Canvas genug Raum für Code, Dokumente oder interaktive Vorschauen.

Deshalb funktioniert eine feste oder begrenzte Chatbreite häufig besser.

### 4. Unklare Zustände

Der Nutzer sollte jederzeit verstehen:

- Welches Dokument ist geöffnet?
- Wird gerade etwas generiert?
- Wurde eine Änderung gespeichert?
- Welche Ansicht ist aktiv?
- Kann der Canvas geschlossen werden?

Diese Zustände gehören zum Design und nicht nur zur technischen Logik.

### 5. Zu viele Aktionen

Ein häufiger Fehler bei Clones ist eine Toolbar mit zehn Icons.

Zeige nur Aktionen, die im aktuellen Zustand sinnvoll sind.

Bei einem Dokument könnten das beispielsweise sein:

```text
Edit
Copy
Versions
Close
```

Bei einer App-Vorschau:

```text
Preview
Code
Refresh
Open
```

Das Interface fühlt sich dadurch wesentlich ruhiger an.

## React-Struktur für einen Claude Canvas UI Clone

Du kannst das Layout zunächst sehr klein halten.

```jsx
export default function Workspace() {
  return (
    <div className="workspace">
      <Sidebar />
      <ChatPanel />
      <CanvasPanel />
    </div>
  );
}
```

Das Grid dazu:

```css
.workspace {
  display: grid;
  grid-template-columns: 240px 420px minmax(0, 1fr);
  height: 100vh;
  background: var(--background);
}
```

Damit steht bereits die grundlegende Desktop-Struktur.

Die einzelnen Bereiche sollten anschließend unabhängig scrollbar sein.

```css
.sidebar,
.chat-panel,
.canvas-panel {
  min-height: 0;
  overflow: hidden;
}

.chat-scroll,
.canvas-content {
  height: 100%;
  overflow-y: auto;
}
```

`min-height: 0` wird bei solchen Grid-Layouts leicht vergessen. Ohne diese Begrenzung können innere Scrollbereiche unerwartet über die Höhe ihres Containers hinauswachsen.

## Wie sollte der Chat aufgebaut sein?

Der Chat braucht überraschend wenig UI.

Eine gute Struktur ist:

```jsx
function ChatPanel() {
  return (
    <section className="chat-panel">
      <header className="chat-header">
        <span>New project</span>
      </header>

      <div className="chat-scroll">
        <Message role="user">
          Build a settings screen for my app.
        </Message>

        <Message role="assistant">
          I created the first version in the canvas.
        </Message>
      </div>

      <Composer />
    </section>
  );
}
```

Der wichtigste Teil ist das Eingabefeld.

Es sollte nicht wie ein normales einzeiliges Formularfeld aussehen. Ein größerer Composer mit automatischer Höhe, Upload-Aktion und Send-Button wirkt bei einer KI-Anwendung natürlicher.

```jsx
function Composer() {
  return (
    <div className="composer">
      <textarea placeholder="Ask anything..." />

      <div className="composer-actions">
        <button aria-label="Datei hinzufügen">+</button>
        <button>Send</button>
      </div>
    </div>
  );
}
```

## Wie baut man den Canvas?

Der Canvas sollte als eigenständiges Objekt gedacht werden.

Nicht:

```text
Chat
  └── Canvas
```

Sondern:

```text
Workspace
  ├── Chat
  └── Canvas
```

Diese kleine konzeptionelle Änderung macht spätere Funktionen wesentlich einfacher.

Ein einfacher Canvas könnte so aussehen:

```jsx
function CanvasPanel() {
  return (
    <section className="canvas-panel">
      <header className="canvas-header">
        <div>
          <strong>Settings Screen</strong>
          <span>React component</span>
        </div>

        <div className="canvas-actions">
          <button>Code</button>
          <button>Preview</button>
          <button aria-label="Canvas schließen">×</button>
        </div>
      </header>

      <main className="canvas-content">
        <Preview />
      </main>
    </section>
  );
}
```

Jetzt kann `Preview` praktisch alles enthalten:

- Markdown
- Rich Text
- Code
- React-Komponenten
- Formulare
- Diagramme
- App-Screens
- HTML-Vorschauen

Diese Flexibilität ist wichtiger als eine perfekte visuelle Kopie.

## Preview und Code als zwei Modi

Für Entwicklerprodukte ist ein Wechsel zwischen Ergebnis und Code besonders sinnvoll.

Der State kann extrem einfach sein:

```jsx
const [mode, setMode] = useState("preview");
```

Anschließend:

```jsx
{mode === "preview" ? (
  <ComponentPreview />
) : (
  <CodeEditor />
)}
```

Du solltest Preview und Code allerdings nicht als zwei völlig unterschiedliche Produkte behandeln.

Beide repräsentieren dasselbe Artifact.

Eine mögliche Datenstruktur:

```js
const artifact = {
  id: "settings-screen",
  title: "Settings Screen",
  type: "react",
  code: "...",
  version: 4,
  updatedAt: Date.now()
};
```

Dadurch lassen sich später Versionen, Autosave und mehrere offene Arbeitsobjekte hinzufügen.

## Der wichtigste State eines Canvas-Clones

Die technische Herausforderung ist nicht das Layout.

Es ist die Beziehung zwischen Chat und Artifact.

Du solltest beispielsweise unterscheiden können zwischen:

```js
const workspaceState = {
  activeConversationId: "chat_01",
  activeArtifactId: "artifact_04",
  artifacts: [],
  messages: []
};
```

Eine Nachricht kann anschließend auf ein Artifact verweisen:

```js
{
  id: "message_12",
  role: "assistant",
  content: "I updated the settings screen.",
  artifactId: "artifact_04",
  artifactVersion: 5
}
```

Damit weiß deine Anwendung später genau, welche Nachricht welche Version ausgelöst hat.

Das wird wichtig, sobald der Nutzer schreibt:

> Mach die Buttons kleiner.

Ohne Versionsbezug weiß dein System irgendwann nicht mehr zuverlässig, welches UI verändert werden soll.

## Versionierung von Anfang an einplanen

Du musst für einen MVP keine komplexe Git-artige Versionsverwaltung bauen.

Das Datenmodell sollte Versionen aber bereits erlauben.

Zum Beispiel:

```js
const artifactVersions = [
  {
    version: 1,
    code: "...",
    createdAt: 1720000000000
  },
  {
    version: 2,
    code: "...",
    createdAt: 1720000100000
  }
];
```

In der Oberfläche reicht zunächst:

```text
Version 4
‹  ›
```

Später kannst du Funktionen wie Restore oder Compare ergänzen.

## Wie nah sollte ein Clone optisch an Claude sein?

Nicht zu nah.

Du kannst das Interaktionsmuster untersuchen und daraus lernen:

- geteilte Arbeitsfläche
- zurückhaltende Farben
- großzügige Abstände
- fokussierte Navigation
- kontextbezogene Aktionen
- starke Typografie
- sichtbarer Canvas

Aber deine eigene Anwendung braucht eine eigene visuelle Identität.

Ein Clone ist als Lernprojekt sinnvoll. Für ein echtes Produkt ist ein eigenes Designsystem langfristig wesentlich wertvoller.

## Ein eigener Design-Startpunkt ist oft besser als Screenshot-Nachbau

Wenn dein Ziel nicht die Claude-Weboberfläche selbst, sondern eine hochwertige KI-App für iOS ist, würde ich nicht mit einem Screenshot anfangen.

Ein Screenshot zeigt dir Pixel, aber nicht unbedingt Komponentenstruktur, Zustände oder sinnvolle mobile Interaktionen.

Für iOS-Projekte kannst du stattdessen einen vorhandenen Design-Startpunkt aus [VP0.com](https://vp0.com) nehmen und ihn in deinem KI-Builder weiterentwickeln. VP0.com stellt dafür kostenlose iOS-Design-Startpunkte in Expo React Native bereit.

Der praktische Workflow ist:

1. Passendes Design auswählen.
2. Design-Link kopieren.
3. Link in Claude Code, Cursor, Rork oder einen anderen unterstützten Builder geben.
4. Den Builder die vorhandene Struktur integrieren lassen.
5. Anschließend die Canvas-Interaktion ergänzen.

VP0.com ersetzt dabei nicht deine Anwendungslogik. Es liefert die UI-Ausgangsbasis. Chat-State, Daten, Authentifizierung, Modellaufrufe und Speicherung bleiben Teil deiner Anwendung.

Das ist besonders nützlich, wenn du zwar programmieren kannst, aber nicht jede Oberfläche von einem leeren Frame aus gestalten möchtest.

## Beispiel: Mobile Claude-Canvas-Interpretation

Auf einem iPhone würde ich das Desktop-Modell nicht direkt übernehmen.

Statt drei Bereichen:

```text
Navigation | Chat | Canvas
```

würde ich zwei Hauptzustände verwenden:

```text
Chat
 ↓
Open Canvas
 ↓
Canvas
```

Der Canvas nimmt dann den gesamten Bildschirm ein.

Eine Header-Struktur könnte so aussehen:

```text
‹ Chat       Settings Screen       •••
──────────────────────────────────────
Preview      Code
──────────────────────────────────────

           Canvas Content
```

Unten können kontextbezogene Aktionen erscheinen.

Das ist auf kleinen Displays wesentlich natürlicher als mehrere schmale Spalten.

## Beispiel: Dokument-Canvas

Nicht jeder Canvas braucht Code.

Für einen Schreibassistenten könnte das Modell so aussehen:

```text
Chat                         Document
────────────────────────────────────────

Rewrite the second          Product Launch
paragraph and make
it shorter.                 Introduction

                            Our new product...
Claude
I shortened the             Market
paragraph.                  The market...
```

Der rechte Bereich könnte einen Rich-Text-Editor enthalten.

Wenn der Nutzer eine Änderung verlangt, sollte nicht das komplette Dokument sichtbar neu aufgebaut werden. Besser ist eine gezielte Aktualisierung des betroffenen Bereichs.

Das vermittelt Kontinuität.

## Beispiel: UI-Generator

Noch interessanter wird das Konzept bei einem UI-Builder.

Links:

```text
Make the cards more compact
and add a monthly spending chart.
```

Rechts erscheint sofort die aktualisierte App.

Der Canvas könnte drei Modi besitzen:

```text
Preview | Code | Files
```

Unter `Files`:

```text
src/
  components/
    SpendingCard.tsx
    SpendingChart.tsx
  screens/
    Dashboard.tsx
  theme/
    tokens.ts
```

Damit wird aus einem Chatbot eine Entwicklungsumgebung.

## Streaming richtig darstellen

Wenn dein Modell eine Antwort streamt, solltest du nicht automatisch jede kleine Änderung im gesamten Canvas neu rendern.

Trenne mindestens:

```js
chatStreaming
artifactGenerating
artifactReady
artifactError
```

Das erlaubt unterschiedliche visuelle Zustände.

Im Chat kann Text bereits erscheinen, während der Canvas beispielsweise noch zeigt:

```text
Building preview...
```

Nach erfolgreicher Generierung wechselst du zu:

```text
Preview ready
```

Das fühlt sich wesentlich kontrollierter an als ein ständig flackernder Arbeitsbereich.

## Loading States ohne unnötige Animation

KI-Produkte werden schnell mit Animationen überladen.

Du brauchst meistens keine leuchtenden Orb-Effekte.

Ein kleiner Status reicht:

```text
Generating...
```

oder:

```text
Updating SettingsScreen.tsx...
```

Noch besser ist ein konkreter Status, weil der Nutzer versteht, was gerade passiert.

Vermeide erfundene technische Fortschrittsanzeigen wie:

```text
87% complete
```

wenn dein Backend diesen Fortschritt überhaupt nicht messen kann.

## Accessibility gehört in den Clone

Ein optisch minimalistisches Interface ist nicht automatisch zugänglich.

Buttons, Tabs, Dialoge und dynamische Bereiche brauchen semantische Rollen und verständliche Beschriftungen.

Bei React Native solltest du unter anderem Accessibility Labels, Rollen, States und sinnvolle Fokusstrukturen berücksichtigen. Die [React-Native-Dokumentation zur Barrierefreiheit](https://reactnative.dev/docs/accessibility) beschreibt die dafür verfügbaren APIs.

Ein Icon-Button sollte beispielsweise nicht nur so aussehen:

```jsx
<Pressable onPress={closeCanvas}>
  <CloseIcon />
</Pressable>
```

sondern eher:

```jsx
<Pressable
  accessibilityRole="button"
  accessibilityLabel="Canvas schließen"
  onPress={closeCanvas}
>
  <CloseIcon />
</Pressable>
```

Das kostet kaum zusätzliche Entwicklungszeit, wenn es von Anfang an Teil des Komponentenmodells ist.

## Responsive Verhalten planen

Ein brauchbarer Clone sollte mindestens drei Layoutzustände besitzen.

### Große Desktop-Breite

```text
Sidebar | Chat | Canvas
```

### Kleine Desktop-Breite

```text
Chat | Canvas
```

Die Sidebar wird zu einem Drawer.

### Mobile

```text
Chat
```

oder:

```text
Canvas
```

Zwischen beiden Ansichten wird navigiert.

Du kannst diese Zustände mit CSS Media Queries oder innerhalb eines App-Frameworks über Breakpoints steuern.

Wichtig ist, nicht einfach Elemente auszublenden, ohne einen alternativen Zugang zu schaffen.

## Welche Komponenten solltest du zuerst bauen?

Eine sinnvolle Reihenfolge ist:

1. AppShell
2. Sidebar
3. ChatPanel
4. Message
5. Composer
6. CanvasPanel
7. CanvasHeader
8. Preview
9. CodeView
10. VersionSwitcher
11. MobileNavigation

Baue zuerst statische Komponenten.

Danach kommen:

- State
- Persistenz
- Streaming
- Modellintegration
- Versionsverwaltung
- Fehlerzustände

So kannst du die Benutzeroberfläche testen, bevor Backend-Probleme die Arbeit verlangsamen.

## Ein sinnvoller Komponentenbaum

Eine größere Version könnte so aussehen:

```text
App
└── Workspace
    ├── Sidebar
    │   ├── NewChatButton
    │   ├── ProjectList
    │   └── ConversationList
    │
    ├── ChatPanel
    │   ├── ChatHeader
    │   ├── MessageList
    │   │   └── Message
    │   └── Composer
    │
    └── CanvasPanel
        ├── CanvasHeader
        │   ├── ArtifactTitle
        │   ├── ModeTabs
        │   └── CanvasActions
        │
        └── CanvasBody
            ├── Preview
            ├── CodeEditor
            └── FileTree
```

Das ist für einen ersten MVP bereits mehr als ausreichend.

## Was solltest du nicht kopieren?

Vermeide es, dein Projekt dadurch zu definieren, dass jede Ecke exakt wie Claude aussehen muss.

Nicht notwendig sind:

- identische Icons
- identische Farben
- identische Schrift
- identische Abstände
- identische Navigation
- identische Animationen

Kopiere lieber die guten Produktideen:

- Chat und Arbeit trennen
- Ergebnisse dauerhaft sichtbar machen
- direkte Iteration ermöglichen
- Versionen nachvollziehbar halten
- Kontext erhalten
- UI ruhig halten

Das sind die Prinzipien, die das Konzept interessant machen.

## Wo ein Designsystem hilft

Sobald mehr als zehn oder zwanzig Komponenten entstehen, solltest du Design Tokens definieren.

Zum Beispiel:

```js
export const tokens = {
  radius: {
    sm: 8,
    md: 12,
    lg: 18
  },
  spacing: {
    xs: 4,
    sm: 8,
    md: 16,
    lg: 24,
    xl: 32
  }
};
```

Dazu kommen Typografie, Oberflächen und Interaktionszustände.

Das verhindert, dass jeder neue Screen ein leicht anderes Padding oder einen anderen Radius bekommt.

Gerade bei KI-generiertem Code ist das wichtig. Wenn dein Builder klare Tokens bekommt, produziert er konsistentere neue Komponenten.

## Prompt für einen ersten Clone

Ein brauchbarer Startprompt könnte so aussehen:

```text
Build a desktop AI workspace with three areas:

1. A compact project sidebar.
2. A conversational chat panel.
3. A large editable canvas.

The canvas should support Preview and Code modes.

Use a restrained neutral design system with generous spacing,
subtle borders and clear typography.

Do not copy Claude branding, logos or exact visual assets.

Keep components modular.

Create:
- Sidebar
- ChatPanel
- MessageList
- Composer
- CanvasPanel
- CanvasHeader
- Preview
- CodeView

The layout must collapse cleanly for tablet and mobile.
```

Dieser Prompt beschreibt Struktur und Verhalten statt nur das Aussehen.

Das erhöht die Chance, dass der Builder eine brauchbare Grundlage erzeugt.

## Danach iterativ verbessern

Versuche nicht, die komplette Anwendung in einem einzigen Prompt zu erzeugen.

Arbeite in kleinen Schritten.

Zum Beispiel:

```text
Make the chat panel narrower and give the canvas more space.
```

Danach:

```text
Replace heavy borders with subtle background separation.
```

Dann:

```text
Add Preview and Code tabs to the canvas header.
```

Und anschließend:

```text
Create a mobile state where the canvas opens as a full-screen view.
```

Kleine Änderungen sind leichter zu beurteilen und leichter zurückzunehmen.

## Was macht einen guten Clone am Ende aus?

Ein guter Claude Canvas UI Clone ist nicht derjenige, bei dem ein Screenshot kaum vom Original zu unterscheiden ist.

Ein guter Clone übernimmt das richtige Produktmodell.

Der Nutzer sollte:

- mit der KI sprechen können
- ein dauerhaft sichtbares Ergebnis erhalten
- dieses Ergebnis verändern können
- zwischen Vorschau und Struktur wechseln können
- frühere Versionen verstehen können
- jederzeit wissen, woran er gerade arbeitet

Wenn diese Punkte funktionieren, kann das visuelle Design vollkommen eigenständig sein.

## Die wichtigste technische Entscheidung

Behandle den Canvas nicht als besonders große Chatnachricht.

Behandle ihn als eigenes Objekt.

Das bedeutet:

```text
Conversation
    ↓
Instruction
    ↓
Artifact
    ↓
Version
```

statt:

```text
Conversation
    ↓
Very large AI response
```

Diese Architektur macht spätere Funktionen wie Versionierung, Sharing, direkte Bearbeitung, Vorschau und mehrere Artifacts wesentlich einfacher.

## Wann VP0.com für so ein Projekt sinnvoll ist

VP0.com ist vor allem dann interessant, wenn dein Claude-inspiriertes Produkt als iOS-App umgesetzt werden soll und du einen fertigen visuellen Startpunkt möchtest.

Du kannst ein Design als Grundlage nehmen und anschließend die eigentliche Canvas-Logik darüber bauen.

Die Einschränkung ist wichtig: VP0.com liefert das UI und nicht dein vollständiges Produkt. Backend, KI-Aufrufe, Persistenz, Benutzerkonten und Geschäftslogik musst du weiterhin selbst umsetzen.

Für eine reine Desktop-Web-App brauchst du dagegen nicht zwangsläufig einen iOS-Design-Startpunkt. Dort ist ein eigenes Web-Designsystem häufig der direktere Weg.

## Fazit

Die beste Methode, eine Claude Canvas ähnliche Oberfläche 2026 zu bauen, besteht nicht darin, Claude visuell vollständig nachzuzeichnen.

Übernimm stattdessen das Arbeitsmodell:

```text
Chat + Artifact + direkte Iteration
```

Beginne mit einem einfachen Drei-Bereich-Layout auf dem Desktop, mache Chat und Canvas zu unabhängigen Objekten und plane Versionierung bereits im Datenmodell ein. Auf mobilen Geräten sollte der Canvas zu einer eigenen Vollbildansicht werden.

Für iOS kannst du mit einem bestehenden Design-Startpunkt beginnen. Für Web-Anwendungen reichen React, ein kleines Token-System und eine klare Komponentenarchitektur bereits für einen überzeugenden ersten Prototyp.

Der entscheidende Unterschied zwischen einem gewöhnlichen KI-Chat und einer echten Arbeitsoberfläche ist nicht die Farbe des Hintergrunds.

Es ist die Tatsache, dass das Ergebnis einen eigenen Platz bekommt.

## FAQ

### Was ist ein Claude Canvas UI Clone?

Damit ist meist eine Oberfläche gemeint, die einen KI-Chat mit einer separaten Arbeitsfläche kombiniert. Dort können beispielsweise Dokumente, Code oder interaktive Vorschauen dauerhaft angezeigt und weiterbearbeitet werden.

### Muss ich Claude exakt kopieren?

Nein. Für ein echtes Produkt ist es sinnvoller, das Interaktionsprinzip zu übernehmen und eine eigene visuelle Identität zu entwickeln.

### Welche Technologie eignet sich für einen Web-Clone?

React ist eine naheliegende Wahl, weil Chat, Canvas, Editor und Vorschau gut als getrennte Komponenten modelliert werden können. Andere moderne Frontend-Frameworks können dieselbe Architektur ebenfalls umsetzen.

### Wie sollte der Canvas auf dem Smartphone funktionieren?

Statt Chat und Canvas nebeneinander zu quetschen, sollte der Canvas normalerweise als eigene Vollbildansicht geöffnet werden. Der Nutzer kann anschließend zurück zum Chat wechseln.

### Brauche ich sofort einen Code-Editor?

Nein. Für einen MVP kann eine einfache Codeansicht reichen. Einen vollständigen Editor solltest du erst hinzufügen, wenn direkte Codebearbeitung tatsächlich zum Kern des Produkts gehört.

### Wie speichere ich verschiedene Canvas-Versionen?

Speichere das Artifact unabhängig vom Chat und lege Änderungen als einzelne Versionen ab. Nachrichten können anschließend auf eine bestimmte Artifact-ID und Versionsnummer verweisen.

### Kann ich VP0.com für einen Claude Clone verwenden?

Für eine iOS-App kann VP0.com als kostenloser Design-Startpunkt dienen. Die eigentliche Chat-, Canvas-, Daten- und KI-Logik bleibt Teil deiner Anwendung.

### Was sollte ich zuerst bauen?

Beginne mit AppShell, ChatPanel und CanvasPanel. Wenn diese drei Bereiche auf Desktop und Mobile sauber funktionieren, kannst du Versionierung, Streaming, Persistenz und weitere Editorfunktionen ergänzen.
