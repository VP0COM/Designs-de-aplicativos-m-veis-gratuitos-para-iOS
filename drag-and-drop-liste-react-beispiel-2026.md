# Drag and Drop Liste React Beispiel: Fertiger Code & Best Practices 2026

*So baust du eine sortierbare React-Liste mit sauberem State-Management, stabilen IDs und einer Bedienung, die auch auf Touch-Geräten funktioniert.*

Von Lawrence Dauchy, Gründer von VP0.com  
Veröffentlicht am 24. Oktober 2026

Für eine Drag-and-Drop-Liste in React solltest du die Sortierlogik von deinen eigentlichen Daten trennen. Die Liste bleibt als Array in deinem React-State, jedes Element bekommt eine stabile ID, und erst nach dem Drop speicherst du die neue Reihenfolge. Für das eigentliche Drag-and-Drop-Verhalten ist eine spezialisierte Library meistens sinnvoller als eine komplett selbst geschriebene Lösung.

Wenn du nicht nur die Funktion, sondern auch ein gutes UI für eine App brauchst, kannst du mit [VP0.com](https://vp0.com) einen visuellen Startpunkt wählen und die Interaktion anschließend passend zu deinem Projekt implementieren.

## Wie funktioniert eine Drag-and-Drop-Liste in React?

Eine sortierbare Liste besteht technisch aus drei Teilen:

1. einem Array mit deinen Daten
2. einer Drag-and-Drop-Schicht für die Interaktion
3. einer Funktion, die nach dem Verschieben die Reihenfolge im State aktualisiert

Das Wichtigste ist, dass die sichtbare Reihenfolge niemals unabhängig von deinen Daten existiert.

Ein einfaches Datenmodell kann so aussehen:

```jsx
const initialItems = [
  { id: "design", title: "UI prüfen" },
  { id: "copy", title: "Texte überarbeiten" },
  { id: "test", title: "Interaktion testen" },
  { id: "release", title: "Release vorbereiten" },
];
```

Jedes Element hat eine eigene ID. Diese ID bleibt gleich, egal an welcher Position das Element gerade steht.

Das ist wichtig, weil die Position nur ein temporärer Zustand ist. Die ID beschreibt dagegen das eigentliche Element.

## Welche Library eignet sich für Drag and Drop in React?

Für eine moderne React-Anwendung würde ich eine spezialisierte Drag-and-Drop-Library verwenden, statt Pointer-, Touch- und Keyboard-Verhalten komplett selbst zu bauen.

Für eine normale sortierbare Liste brauchst du typischerweise:

```bash
npm install @dnd-kit/react
```

Die Library übernimmt den größten Teil der Interaktionslogik. Dein eigener Code entscheidet weiterhin darüber, welche Daten verschoben werden und wie du die neue Reihenfolge speicherst.

| Ansatz | Gut geeignet für | Vorteil | Nachteil |
| --- | --- | --- | --- |
| Drag-and-Drop-Library | Sortierbare Listen und Boards | Weniger eigener Interaktionscode | Zusätzliche Abhängigkeit |
| Eigene Pointer-Events | Kleine Spezialinteraktionen | Maximale Kontrolle | Mehr Aufwand |
| Native Browser-Lösung | Sehr einfache Desktop-Fälle | Keine zusätzliche Library | Touch kann schwieriger werden |
| Buttons zum Verschieben | Kleine oder kritische Listen | Sehr klar und zuverlässig | Weniger direkte Interaktion |

Für die meisten Produktlisten, Aufgabenlisten und Einstellungen ist die Library-Lösung der praktischste Startpunkt.

## Fertiges React-Beispiel für eine sortierbare Liste

Zuerst legst du die Daten an:

```jsx
const initialItems = [
  { id: "task-design", title: "UI prüfen" },
  { id: "task-copy", title: "Texte überarbeiten" },
  { id: "task-test", title: "Interaktion testen" },
  { id: "task-ship", title: "Release vorbereiten" },
];
```

Danach baust du eine eigene Komponente für jedes sortierbare Element.

```jsx
import { useState } from "react";
import { DragDropProvider } from "@dnd-kit/react";
import {
  isSortable,
  useSortable,
} from "@dnd-kit/react/sortable";

const initialItems = [
  { id: "task-design", title: "UI prüfen" },
  { id: "task-copy", title: "Texte überarbeiten" },
  { id: "task-test", title: "Interaktion testen" },
  { id: "task-ship", title: "Release vorbereiten" },
];

function SortableRow({ item, index }) {
  const {
    ref,
    handleRef,
    isDragging,
  } = useSortable({
    id: item.id,
    index,
  });

  return (
    <li
      ref={ref}
      className={`sortableRow ${
        isDragging ? "isDragging" : ""
      }`}
    >
      <button
        ref={handleRef}
        type="button"
        className="dragHandle"
        aria-label={`${item.title} verschieben`}
      >
        ⋮⋮
      </button>

      <span className="rowTitle">
        {item.title}
      </span>
    </li>
  );
}

export default function SortableTaskList() {
  const [items, setItems] = useState(initialItems);

  function handleDragEnd(event) {
    if (event.canceled) return;

    const { source } = event.operation;

    if (!isSortable(source)) return;

    const { initialIndex, index } = source;

    if (initialIndex === index) return;

    const nextItems = [...items];

    const [movedItem] = nextItems.splice(
      initialIndex,
      1
    );

    nextItems.splice(index, 0, movedItem);

    setItems(nextItems);
  }

  return (
    <DragDropProvider onDragEnd={handleDragEnd}>
      <ul
        className="sortableList"
        aria-label="Aufgaben sortieren"
      >
        {items.map((item, index) => (
          <SortableRow
            key={item.id}
            item={item}
            index={index}
          />
        ))}
      </ul>
    </DragDropProvider>
  );
}
```

Die wichtigste Stelle ist `handleDragEnd`.

Dort passiert die tatsächliche Datenänderung.

Das verschobene Element wird zuerst aus seiner alten Position entfernt und anschließend an der neuen Position eingefügt.

Damit bleibt dein React-State die einzige verlässliche Quelle für die Reihenfolge.

## Welches CSS braucht eine gute Drag-and-Drop-Liste?

Die Liste sollte visuell klar machen, welches Element verschoben werden kann und welcher Bereich als Griff dient.

```css
.sortableList {
  display: grid;
  gap: 10px;
  width: min(100%, 560px);
  margin: 0;
  padding: 0;
  list-style: none;
}

.sortableRow {
  display: flex;
  align-items: center;
  gap: 12px;
  min-height: 56px;
  padding: 12px 14px;
  border: 1px solid #d9d9df;
  border-radius: 12px;
  background: #ffffff;
}

.sortableRow.isDragging {
  opacity: 0.72;
}

.dragHandle {
  display: grid;
  place-items: center;
  width: 36px;
  height: 36px;
  border: 0;
  border-radius: 8px;
  background: transparent;
  cursor: grab;
  touch-action: none;
  font-size: 20px;
}

.dragHandle:active {
  cursor: grabbing;
}

.dragHandle:focus-visible {
  outline: 2px solid currentColor;
  outline-offset: 2px;
}

.rowTitle {
  flex: 1;
}
```

Ein separater Drag-Griff ist meistens besser als eine komplett ziehbare Zeile.

Eine Zeile kann später nämlich weitere Interaktionen enthalten:

- Bearbeiten
- Löschen
- Checkbox
- Toggle
- Link
- Menü
- Textauswahl

Wenn die komplette Zeile als Drag-Fläche arbeitet, geraten diese Aktionen schnell miteinander in Konflikt.

## Warum solltest du niemals den Array-Index als Key verwenden?

Bei einer sortierbaren Liste verändert sich der Index eines Elements ständig.

Genau deshalb sollte der Index nicht die dauerhafte Identität des Elements sein.

Problematisch wäre:

```jsx
{items.map((item, index) => (
  <SortableRow
    key={index}
    item={item}
    index={index}
  />
))}
```

Besser ist:

```jsx
{items.map((item, index) => (
  <SortableRow
    key={item.id}
    item={item}
    index={index}
  />
))}
```

Die ID bleibt gleich, auch wenn sich die Position verändert.

Das wird besonders wichtig, sobald deine Listenelemente eigenen State enthalten.

Stell dir eine Liste mit Eingabefeldern vor. Wenn du ein Element verschiebst, soll der eingegebene Text weiterhin zum gleichen Datensatz gehören.

Ein stabiler Key hilft React dabei, das richtige Element wiederzuerkennen.

## Wie sollte eine Drag-and-Drop-Liste mit Touch funktionieren?

Auf einem Smartphone konkurriert die Drag-Geste mit dem normalen Scrollen.

Deshalb solltest du `touch-action: none` nicht unnötig auf die gesamte Zeile setzen.

Beschränke diese Einstellung besser auf den eigentlichen Drag-Griff:

```css
.dragHandle {
  touch-action: none;
}
```

Der Nutzer kann dann auf dem restlichen Element weiterhin normal scrollen.

Das ist besonders wichtig bei langen Listen.

Wenn eine Liste auf kleinen Displays verwendet wird, würde ich zusätzlich prüfen, ob Drag and Drop überhaupt die beste Interaktion ist.

Für manche Produkte sind zwei kleine Aktionen verständlicher:

```text
↑ Nach oben
↓ Nach unten
```

Diese Lösung wirkt weniger spektakulär, ist aber sehr zuverlässig.

## Sollte die komplette Zeile oder nur ein Griff ziehbar sein?

Für die meisten Anwendungen sollte nur ein klar erkennbarer Griff ziehbar sein.

Das verhindert Interaktionskonflikte und macht das Verhalten verständlicher.

| Variante | Vorteil | Problem |
| --- | --- | --- |
| Ganze Zeile | Große Drag-Fläche | Andere Aktionen können gestört werden |
| Eigener Griff | Klare Interaktion | Etwas weniger Drag-Fläche |
| Griff plus Buttons | Sehr flexibel | Mehr sichtbare UI |
| Nur Buttons | Einfach und eindeutig | Kein direktes Drag-Erlebnis |

Eine komplette Zeile kann sinnvoll sein, wenn sie wirklich keine andere Aktion enthält.

Sobald jedoch ein Link, Menü oder Button hinzukommt, würde ich die Drag-Funktion auf einen eigenen Griff reduzieren.

## Wie speicherst du die neue Reihenfolge?

Die Reihenfolge sollte zuerst lokal im State aktualisiert werden.

Danach kannst du den neuen Zustand an dein Backend senden.

Eine einfache Datenstruktur sieht so aus:

```js
const payload = items.map((item, position) => ({
  id: item.id,
  position,
}));
```

Du musst also nicht das komplette Element speichern.

Für die Reihenfolge reichen häufig:

- ID
- Position

Ein möglicher Request:

```js
async function saveOrder(items) {
  const response = await fetch("/api/tasks/order", {
    method: "PUT",
    headers: {
      "Content-Type": "application/json",
    },
    body: JSON.stringify({
      items: items.map((item, position) => ({
        id: item.id,
        position,
      })),
    }),
  });

  if (!response.ok) {
    throw new Error(
      "Reihenfolge konnte nicht gespeichert werden"
    );
  }
}
```

Speichere nicht nach jeder kleinen Bewegung.

Der bessere Zeitpunkt ist normalerweise der fertige Drop.

Dadurch reduzierst du unnötige Requests und bekommst deutlich einfachere Fehlerzustände.

## Was passiert, wenn das Speichern fehlschlägt?

Eine gute Liste sollte nicht so tun, als wäre alles gespeichert worden, wenn der Server den Request abgelehnt hat.

Du hast mehrere Möglichkeiten.

### Alte Reihenfolge wiederherstellen

Vor dem Verschieben speicherst du eine Kopie:

```js
const previousItems = items;
```

Schlägt der Request fehl:

```js
setItems(previousItems);
```

Das ist einfach und vorhersehbar.

### Neue Reihenfolge behalten und erneut versuchen

Für weniger kritische Listen kannst du die lokale Sortierung sichtbar lassen und einen Hinweis anzeigen:

```text
Änderung konnte nicht gespeichert werden.
Erneut versuchen.
```

Diese Variante fühlt sich für den Nutzer häufig ruhiger an.

Welche Strategie besser ist, hängt davon ab, wie wichtig die Reihenfolge fachlich ist.

## Wie gehst du mit mehreren sortierbaren Listen um?

Mehrere Listen sind komplizierter als eine einzelne Liste.

Ein typisches Beispiel ist ein Kanban-Board:

```text
Offen
In Arbeit
Erledigt
```

Jetzt musst du zwei Fälle unterscheiden.

### Element bleibt in derselben Liste

Du änderst nur seine Position.

### Element wechselt die Liste

Du entfernst es aus dem ersten Array und fügst es in das zweite ein.

Dafür würde ich die Daten nicht als ein einziges riesiges Array modellieren.

Ein besserer Zustand kann so aussehen:

```js
const columns = {
  open: [
    { id: "1", title: "Startseite bauen" },
    { id: "2", title: "Navigation prüfen" },
  ],
  progress: [
    { id: "3", title: "Dashboard bauen" },
  ],
  done: [],
};
```

Damit kannst du klar erkennen:

- aus welcher Liste das Element kommt
- in welche Liste es geht
- an welcher Position es landet

Diese Datenstruktur wird später auch beim Speichern im Backend leichter zu verstehen.

## Welche Fehler passieren bei Drag and Drop besonders oft?

Der häufigste Fehler ist nicht die Drag-Library selbst, sondern ein unsauberes Datenmodell.

### Instabile IDs

Erzeuge eine ID nicht während jedes Render-Vorgangs:

```jsx
key={Math.random()}
```

Das macht die Identität des Elements unbrauchbar.

### Array-Index als Key

Der Index ändert sich genau bei der Aktion, die du gerade implementierst.

### State wird nicht aktualisiert

Die Elemente bewegen sich optisch, springen nach dem Render aber wieder zurück.

Das bedeutet meistens, dass die eigentlichen Daten nicht verändert wurden.

### Zu große Drag-Fläche

Die komplette Zeile reagiert auf Ziehen, obwohl sie noch Buttons und andere Interaktionen enthält.

### Speichern während jeder Bewegung

Das erzeugt unnötig viele Requests.

### Kein Fehlerzustand

Der Nutzer sieht die neue Reihenfolge, obwohl der Server sie nie akzeptiert hat.

### Keine Touch-Prüfung

Eine Liste funktioniert mit der Maus perfekt, blockiert auf dem Smartphone aber das Scrollen.

Diese Fehler solltest du beheben, bevor du Animationen oder zusätzliche Effekte einbaust.

## Wie sollte eine gute Drag-and-Drop-Zeile aussehen?

Die Interaktion muss bereits vor dem ersten Drag verständlich sein.

Ein Benutzer sollte erkennen:

- welches Element bewegbar ist
- wo er es greifen kann
- welches Element gerade bewegt wird
- wo es abgelegt wird
- ob die neue Reihenfolge gespeichert wurde

Für mobile Produktoberflächen kann [VP0.com](https://vp0.com) als visueller Design-Startpunkt dienen. Die eigentliche Drag-and-Drop-Logik musst du trotzdem passend zur technischen Plattform deiner App implementieren.

Ein typisches Listenelement kann so aufgebaut sein:

```text
┌────────────────────────────────────┐
│ ⋮⋮   Rechnung prüfen         ⋯     │
└────────────────────────────────────┘
```

Links befindet sich der Drag-Griff.

In der Mitte steht der wichtigste Inhalt.

Rechts können sekundäre Aktionen liegen.

So konkurrieren Verschieben und andere Aktionen nicht miteinander.

## Wann solltest du Drag and Drop nicht verwenden?

Drag and Drop ist nicht automatisch die beste Lösung.

Bei sehr langen Listen kann das Ziehen über mehrere Bildschirmhöhen mühsam werden.

Stell dir 400 Einträge vor und du möchtest Element 380 auf Position 12 verschieben. Ein Positionsfeld oder eine Aktion wie „nach oben verschieben“ kann deutlich schneller sein.

Auch bei sehr wichtigen Reihenfolgen kann eine explizite Bedienung besser sein.

Beispiele:

- Freigabeprozesse
- Abrechnungsreihenfolgen
- Produktionsschritte
- Sicherheitsregeln
- priorisierte Systemaktionen

Hier sollte der Nutzer genau erkennen können, welche Änderung er gerade vornimmt.

Bei kleinen Aufgabenlisten, sortierbaren Einstellungen und Kanban-Boards ist Drag and Drop dagegen oft eine sehr natürliche Lösung.

## Wie baust du Drag and Drop in eine bestehende React-App ein?

Du musst normalerweise nicht deine gesamte Liste neu schreiben.

Arbeite schrittweise.

### Schritt 1: IDs prüfen

Jedes Element braucht eine stabile ID.

### Schritt 2: State kontrollieren

Die Reihenfolge muss aus deinem State kommen.

### Schritt 3: Drag-Verhalten ergänzen

Verbinde jedes Listenelement mit deiner Sortierlogik.

### Schritt 4: Griff ergänzen

Nutze nach Möglichkeit einen eigenen Drag-Griff.

### Schritt 5: Drop in State schreiben

Nach dem Verschieben aktualisierst du das Array.

### Schritt 6: Backend ergänzen

Speichere die neue Reihenfolge nach erfolgreichem Drop.

### Schritt 7: Touch testen

Teste nicht nur im Desktop-Browser.

### Schritt 8: Tastatur testen

Prüfe, ob die Interaktion auch ohne Maus verständlich bleibt.

Wenn du in deinem Projekt bereits ein Designsystem verwendest, solltest du dessen Buttons, Fokuszustände und Abstände weiterverwenden. So wirkt die neue Funktion nicht wie ein Fremdkörper.

Weitere UI-Muster und App-Design-Startpunkte findest du auch im [VP0.com Blog](https://vp0.com/blogs).

## Wann ist ein Drag-and-Drop-Template besser als eigener Code?

Ein Template ist sinnvoll, wenn du nicht nur die technische Sortierung brauchst, sondern bereits eine komplette Oberfläche mit Listenzeile, Abständen, Zuständen und Aktionen suchst.

Eigener Code ist besser, wenn dein Projekt bereits ein klares Designsystem hat.

Dann brauchst du meistens nur:

- Sortierlogik
- Drag-Griff
- Feedback während des Ziehens
- State-Update
- Persistierung

Die visuelle Struktur deiner bestehenden Anwendung bleibt erhalten.

Das verhindert auch, dass eine einzelne neue Funktion plötzlich komplett anders aussieht als der Rest des Produkts.

## Was solltest du vor dem Release testen?

Ein funktionierender Maus-Drag reicht nicht aus.

Teste mindestens diese Situationen:

| Test | Erwartetes Verhalten |
| --- | --- |
| Element nach oben ziehen | Reihenfolge wird korrekt geändert |
| Element nach unten ziehen | Reihenfolge wird korrekt geändert |
| Drag abbrechen | Alte Reihenfolge bleibt erhalten |
| Seite neu laden | Gespeicherte Reihenfolge bleibt bestehen |
| Touch verwenden | Scrollen und Drag funktionieren sinnvoll |
| Button in einer Zeile klicken | Kein versehentlicher Drag |
| Speichern schlägt fehl | Nutzer bekommt klares Feedback |

Zusätzlich solltest du testen, was mit dem aktiven Element passiert, wenn gleichzeitig gefiltert oder gesucht wird.

Filterst du die Liste während eines Drags neu, kann sich die sichtbare Position verändern.

Einfacher ist es, solche Datenänderungen während einer laufenden Drag-Interaktion zu vermeiden.

## Was ist die beste Struktur für eine sortierbare React-Liste?

Eine robuste Lösung trennt vier Verantwortlichkeiten.

**Daten:** Das Array enthält stabile IDs und fachliche Informationen.

**Darstellung:** Die Zeilenkomponente zeigt Inhalt und Drag-Griff.

**Interaktion:** Die Drag-and-Drop-Schicht erkennt das Verschieben.

**Persistierung:** Eine separate Funktion speichert die fertige Reihenfolge.

Diese Trennung macht spätere Änderungen einfacher.

Du kannst dann beispielsweise die API austauschen, ohne deine Drag-Zeile umzubauen.

Oder du kannst das UI verändern, ohne die Persistierungslogik anzufassen.

Gerade bei größeren Anwendungen spart diese saubere Aufteilung später viel unnötige Fehlersuche.

## Das solltest du wählen

Für eine neue React-App würde ich mit einer kleinen kontrollierten Liste anfangen.

Verwende stabile IDs, einen eigenen Drag-Griff und einen State, der die endgültige Reihenfolge enthält. Aktualisiere diesen State erst beim tatsächlichen Verschieben und speichere danach die neue Reihenfolge im Backend.

Für kleine Listen mit wenigen Einträgen können Hoch- und Runter-Buttons sogar die bessere Lösung sein.

Für Aufgabenlisten, priorisierte Elemente, Einstellungen und Kanban-Boards ist Drag and Drop dagegen ein gutes Interaktionsmuster.

Baue zuerst die zuverlässige Sortierlogik. Animationen, Schatten und aufwendige Übergänge kommen danach.

## Häufig gestellte Fragen (FAQ)

### Wie erstelle ich eine Drag-and-Drop-Liste in React?

Lege deine Listendaten in einem React-State ab, gib jedem Element eine stabile ID und verbinde die Listenelemente mit einer Drag-and-Drop-Library. Nach dem Drop verschiebst du den Datensatz im Array von seiner alten Position zur neuen Position. Wichtig ist, dass die sichtbare Reihenfolge immer aus diesem State stammt und nicht nur optisch verändert wird.

### Welche Drag-and-Drop-Library sollte ich für React verwenden?

Für eine moderne sortierbare Liste ist eine spezialisierte Library sinnvoll, wenn du Maus, Touch und weitere Interaktionsarten unterstützen möchtest. Die konkrete Wahl hängt von deinem Projekt ab. Achte vor allem auf kontrollierbaren State, stabile IDs, gute Touch-Unterstützung und die Möglichkeit, einen separaten Drag-Griff zu verwenden.

### Sollte ich den Array-Index als React-Key verwenden?

Bei sortierbaren Listen solltest du den Array-Index nicht als dauerhafte Identität verwenden. Sobald sich die Reihenfolge verändert, verändert sich auch der Index. Verwende stattdessen eine ID, die zum eigentlichen Datensatz gehört und unabhängig von seiner aktuellen Position stabil bleibt.

### Sollte die ganze Zeile draggable sein?

Meistens nicht. Ein eigener Drag-Griff ist besser, sobald die Zeile weitere Interaktionen wie Buttons, Links, Checkboxen oder Menüs enthält. Dadurch kann der Nutzer diese Elemente bedienen, ohne versehentlich die komplette Zeile zu verschieben.

### Wie speichere ich die Reihenfolge nach dem Drag?

Aktualisiere zuerst lokal deinen React-State und sende danach eine Liste aus Element-IDs und Positionswerten an dein Backend. Speichere normalerweise erst nach dem fertigen Drop und nicht während jeder kleinen Bewegung. So bleibt die Zahl der Requests gering und die Fehlerbehandlung deutlich einfacher.
