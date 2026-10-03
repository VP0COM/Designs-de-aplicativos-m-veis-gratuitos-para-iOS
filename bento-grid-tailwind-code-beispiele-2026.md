# Bento Grid Tailwind: Fertiger Code & moderne Beispiele 2026

Von Lawrence Dauchy  
Veröffentlicht am 3. Oktober 2026

Ein Bento Grid mit Tailwind baust du mit CSS Grid, unterschiedlich großen Karten und einer responsiven Spaltenstruktur. Du beginnst mit einer Spalte auf kleinen Bildschirmen und ergänzt auf größeren Displays breite oder hohe Elemente. Entscheidend sind eine klare Reihenfolge, passende Abstände und Karten, deren Größe zum Inhalt passt. Das folgende Beispiel liefert dir eine vollständige React-Komponente für ein bereits eingerichtetes Tailwind-Projekt. Sie kommt ohne zusätzliche Komponentenbibliothek, externe Bilder oder JavaScript für das Layout aus. Anschließend kannst du das Raster für eine Produktseite, ein Portfolio oder ein Dashboard anpassen.

## Was ist ein Bento Grid und wann lohnt es sich?

Ein Bento Grid ist ein Kartenlayout, das unterschiedlich große Inhaltsbereiche in einem gemeinsamen Raster verbindet. Eine große Karte setzt den Schwerpunkt, kleinere Karten ergänzen Funktionen, Kennzahlen oder Beispiele.

Der Name erinnert an eine Bento-Box mit mehreren Fächern. Im Webdesign entsteht daraus eine Fläche, auf der jedes Element eine eigene Aufgabe bekommt. Die Karten teilen sich Abstände und Gestaltung, müssen aber nicht dieselbe Größe haben.

Das funktioniert besonders gut, wenn du mehrere Informationen gleichzeitig zeigen möchtest:

- Eine Produktseite stellt eine Hauptfunktion und ergänzende Vorteile vor.
- Ein Portfolio kombiniert ein großes Projekt mit kleineren Arbeiten.
- Ein Dashboard verbindet eine zentrale Auswertung mit Statusanzeigen.
- Eine persönliche Website zeigt Vorstellung, Fähigkeiten und aktuelle Projekte.
- Eine Funktionsübersicht gruppiert kurze Erklärungen mit visuellen Beispielen.

Die Kartengröße sollte dabei eine Bedeutung haben. Ein ausführlicher Produktüberblick darf mehr Platz bekommen als ein kurzer Status. Wenn jede Karte gleich laut wirkt, fehlt dem Raster eine erkennbare Hierarchie.

Ein Bento Grid unterscheidet sich außerdem von einem Masonry-Layout. Bei Masonry werden Elemente unterschiedlicher Höhe typischerweise möglichst lückenarm angeordnet. Ein Bento Grid arbeitet meist mit bewusst gesetzten Zeilen, Spalten und Flächen.

Für einen langen Text, eine lineare Anleitung oder ein umfangreiches Formular ist eine normale Seitenstruktur häufig angenehmer. Das Raster lohnt sich, wenn die Inhalte eigenständig verständlich bleiben und gemeinsam einen schnellen Überblick ermöglichen.

## Welche Tailwind-Klassen brauchst du für das Raster?

Für den Einstieg reichen `grid`, eine Spaltenanzahl, ein Abstand und responsive Klassen für die einzelnen Karten. Tailwind übersetzt diese Utilities in die entsprechenden CSS-Grid-Eigenschaften.

Die Grundstruktur sieht so aus:

```html
<div class="grid grid-cols-1 gap-4 md:grid-cols-2 lg:grid-cols-4">
  <!-- Karten -->
</div>
```

`grid-cols-1` legt eine Spalte fest. Mit `md:grid-cols-2` und `lg:grid-cols-4` erweitert sich das Raster an den jeweiligen Breakpoints. Die Karten bleiben dadurch auf schmalen Bildschirmen untereinander lesbar.

Die wichtigsten Klassen für unterschiedlich große Karten sind:

- `lg:col-span-2` lässt eine Karte ab dem großen Breakpoint zwei Spalten belegen.
- `lg:row-span-2` lässt sie dort zwei Zeilen belegen.
- `gap-4` setzt einen gemeinsamen Abstand zwischen den Karten.
- `min-w-0` hilft, Inhalte innerhalb einer Karte schrumpfen zu lassen.
- `h-full` lässt eine innere Fläche die verfügbare Höhe ausfüllen.

Spalten- und Zeilenüberspannungen verändern die belegte Fläche einer Karte. Sie legen allerdings nicht automatisch eine sinnvolle Höhe für deren Inhalt fest.

Deshalb ist es hilfreich, zwei Entscheidungen zu trennen: Wie viele Rasterfelder bekommt die Karte, und wie viel Platz braucht ihr Inhalt?

Für eine Funktionsübersicht funktionieren natürliche Höhen oft gut. Für ein bewusst geometrisches Desktoplayout kannst du zusätzlich eine minimale Zeilenhöhe verwenden:

```html
<div
  class="grid grid-cols-1 gap-4 md:grid-cols-2
         lg:auto-rows-[minmax(180px,auto)] lg:grid-cols-4"
>
  <!-- Karten -->
</div>
```

Damit dürfen die Zeilen bei längeren Inhalten wachsen. Eine starre Höhe würde dagegen schneller zu abgeschnittenen Texten führen.

## Wie sieht ein fertiges Bento Grid mit React und Tailwind aus?

Die folgende Komponente erstellt fünf Karten: eine große Einführung, zwei kompakte Funktionskarten, eine hohe Ablaufkarte und eine breite Abschlusskarte. Auf kleinen Bildschirmen stehen sie untereinander.

Voraussetzung ist ein React-Projekt mit funktionierender Tailwind-Einbindung. Speichere die Komponente beispielsweise als `BentoGrid.jsx` und rendere sie auf deiner Seite.

```jsx
export default function BentoGrid() {
  const card =
    "min-w-0 rounded-3xl border border-slate-200 " +
    "bg-white p-6 shadow-sm sm:p-8";

  return (
    <main className="min-h-screen bg-slate-50 px-4 py-16 sm:px-6">
      <section
        aria-labelledby="bento-heading"
        className="mx-auto max-w-6xl"
      >
        <header className="mb-8 max-w-2xl">
          <p className="text-sm font-semibold text-indigo-700">
            Dein Arbeitsbereich
          </p>

          <h1
            id="bento-heading"
            className="mt-3 text-4xl font-semibold tracking-tight
                       text-slate-950 sm:text-5xl"
          >
            Mehr Überblick für deine Projekte.
          </h1>

          <p className="mt-4 text-lg leading-8 text-slate-600">
            Aufgaben, Fortschritt und Zusammenarbeit
            an einem gemeinsamen Ort.
          </p>
        </header>

        <div
          className="grid grid-cols-1 gap-4 md:grid-cols-2
                     lg:auto-rows-[minmax(180px,auto)]
                     lg:grid-cols-4"
        >
          <article
            className={`${card} flex flex-col justify-between
                        md:col-span-2 lg:row-span-2`}
          >
            <div>
              <p className="text-sm font-medium text-indigo-700">
                Projekte
              </p>

              <h2
                className="mt-3 text-3xl font-semibold
                           tracking-tight text-slate-950"
              >
                Ein Plan, den dein Team versteht.
              </h2>

              <p className="mt-4 max-w-md leading-7 text-slate-600">
                Sammle Aufgaben, halte Entscheidungen fest
                und erkenne, was als Nächstes ansteht.
              </p>
            </div>

            <div className="mt-8 rounded-2xl bg-slate-100 p-4">
              <p className="text-sm font-semibold text-slate-800">
                Beispielprojekt: Website
              </p>

              <ul className="mt-4 space-y-3 text-sm text-slate-700">
                <li className="rounded-xl bg-white p-3">
                  Inhalte vorbereiten
                </li>
                <li className="rounded-xl bg-white p-3">
                  Layout abstimmen
                </li>
                <li className="rounded-xl bg-white p-3">
                  Veröffentlichung prüfen
                </li>
              </ul>
            </div>
          </article>

          <article className={card}>
            <p className="text-sm font-medium text-slate-500">
              Fokus
            </p>

            <h2 className="mt-3 text-xl font-semibold text-slate-950">
              Klare Prioritäten
            </h2>

            <p className="mt-3 leading-7 text-slate-600">
              Zeige zuerst die Aufgaben,
              die dein Projekt weiterbringen.
            </p>
          </article>

          <article
            className={`${card} bg-indigo-50 lg:row-span-2`}
          >
            <p className="text-sm font-medium text-indigo-700">
              Ablauf
            </p>

            <h2 className="mt-3 text-xl font-semibold text-slate-950">
              Vom Entwurf zur Freigabe
            </h2>

            <ol className="mt-6 space-y-5 text-sm text-slate-700">
              <li>
                <span className="font-semibold">1. Sammeln</span>
                <p className="mt-1 leading-6">
                  Ideen und Anforderungen festhalten.
                </p>
              </li>
              <li>
                <span className="font-semibold">2. Umsetzen</span>
                <p className="mt-1 leading-6">
                  Aufgaben verteilen und bearbeiten.
                </p>
              </li>
              <li>
                <span className="font-semibold">3. Prüfen</span>
                <p className="mt-1 leading-6">
                  Ergebnisse gemeinsam freigeben.
                </p>
              </li>
            </ol>
          </article>

          <article className={card}>
            <p className="text-sm font-medium text-slate-500">
              Zusammenarbeit
            </p>

            <h2 className="mt-3 text-xl font-semibold text-slate-950">
              Weniger Rückfragen
            </h2>

            <p className="mt-3 leading-7 text-slate-600">
              Halte Zuständigkeiten direkt
              bei der jeweiligen Aufgabe fest.
            </p>
          </article>

          <article
            className={`${card} md:col-span-2 lg:col-span-4`}
          >
            <div
              className="flex flex-col gap-4 sm:flex-row
                         sm:items-center sm:justify-between"
            >
              <div>
                <h2 className="text-xl font-semibold text-slate-950">
                  Starte mit einem überschaubaren Projekt.
                </h2>

                <p className="mt-2 leading-7 text-slate-600">
                  Ergänze weitere Abläufe,
                  sobald die Grundstruktur funktioniert.
                </p>
              </div>

              <span
                className="self-start rounded-full bg-slate-100
                           px-4 py-2 text-sm font-medium
                           text-slate-700"
              >
                Beispielansicht
              </span>
            </div>
          </article>
        </div>
      </section>
    </main>
  );
}
```

Die Inhalte beschreiben eine fiktive Projektoberfläche. Ersetze sie durch echte Funktionen deines Produkts. Das Beispiel enthält bewusst keine erfundenen Erfolgszahlen und keine Schaltflächen ohne Funktion.

Auf großen Bildschirmen nimmt die erste Karte die linke Hälfte über zwei Zeilen ein. Die Ablaufkarte liegt rechts und ist ebenfalls zwei Zeilen hoch. Die beiden kompakten Karten teilen sich die verbleibende Spalte.

Die Abschlusskarte belegt eine eigene Zeile über die gesamte Breite. Dadurch bleibt der nächste Schritt sichtbar vom Funktionsbereich getrennt.

## Wie machst du das Bento Grid wirklich responsiv?

Ein responsives Bento Grid beginnt mit einer sinnvollen mobilen Reihenfolge. Breite und hohe Karten entstehen erst dort, wo ausreichend Platz vorhanden ist.

Tailwind arbeitet bei seinen normalen Breakpoint-Varianten nach dem Mobile-first-Prinzip: Klassen ohne Präfix gelten grundsätzlich, Varianten wie `md:` greifen ab dem jeweiligen Breakpoint.

Im Beispiel bedeutet das:

- Mobil bekommt jede Karte eine eigene Zeile.
- Auf mittleren Bildschirmen entstehen zwei Spalten.
- Auf großen Bildschirmen entstehen vier Spalten.
- Die hohe Kartenform wird erst auf großen Bildschirmen aktiviert.

Ein häufiger Fehler ist eine unbedingte Spaltenüberspannung:

```html
<article class="col-span-2">
  Inhalt
</article>
```

In einem einspaltigen Raster kann das zusätzliche implizite Spalten erzeugen. Verwende deshalb ein passendes Präfix, wenn die Karte nur auf größeren Displays breiter sein soll:

```html
<article class="md:col-span-2">
  Inhalt
</article>
```

Prüfe außerdem die Zwischenbreiten. Ein Layout kann auf einem großen Monitor und einem kleinen Smartphone gut aussehen, aber auf einem schmalen Tablet unruhig werden.

Ziehe das Browserfenster langsam schmaler. Achte darauf, wann Überschriften ungünstig umbrechen und Karten zu wenig Platz bekommen. Der passende Breakpoint richtet sich nach deinem Inhalt.

Bei langen deutschen Begriffen helfen ausreichend breite Karten und ein flexibler Textbereich. Kürze wichtige Beschriftungen sinnvoll, statt die Schrift immer kleiner zu machen.

Wenn eine Karte auf Mobilgeräten unverhältnismäßig lang wird, prüfe ihre Aufgabe. Vielleicht gehört ein ausführlicher Ablauf in einen eigenen Abschnitt unterhalb des Rasters.

## Welche modernen Bento-Grid-Beispiele lassen sich daraus bauen?

Aus derselben Grundstruktur kannst du mehrere deutlich unterschiedliche Seiten entwickeln. Ändere zuerst die Inhalte und ihre Gewichtung, anschließend Farben und Dekoration.

### Eine Funktionsübersicht für ein digitales Produkt

Nutze die große Karte für das zentrale Problem, das dein Produkt löst. Die kleineren Karten erklären ergänzende Funktionen.

Eine Terminplanungssoftware könnte beispielsweise so aufgebaut sein:

- Große Karte: Wochenplanung mit einer vereinfachten Kalenderansicht.
- Kleine Karte: Verfügbarkeiten.
- Hohe Karte: Ablauf einer Buchung.
- Kleine Karte: Erinnerungen.
- Breite Karte: Einrichtung des ersten Kalenders.

Die Vorschau sollte einen nachvollziehbaren Vorgang zeigen. Eine Reihe zufälliger Balken wirkt dekorativ, erklärt aber keine Funktion.

Halte Produktversprechen und Darstellung zusammen. Wenn eine Karte „einfache Buchung“ behauptet, sollte ihre Vorschau einen kurzen Buchungsablauf erkennen lassen.

### Ein Portfolio mit klarer Projektgewichtung

Für ein Portfolio bekommt dein wichtigstes Projekt die größte Fläche. Ergänzende Arbeiten erscheinen kleiner, gefolgt von Fähigkeiten und einer kurzen Vorstellung.

Verwende für jedes Projekt dieselbe Informationsstruktur: Name, Aufgabe und dein konkreter Beitrag. So lassen sich die Arbeiten beim Überfliegen vergleichen.

Bei Bildern solltest du ein bewusstes Seitenverhältnis festlegen. Prüfe außerdem, ob `object-cover` wichtige Details abschneidet. Ein vollständiger Oberflächenentwurf braucht manchmal eine andere Darstellung als ein atmosphärisches Foto.

Verzichte darauf, jedes Projekt als gleich bedeutend zu präsentieren. Ein Portfolio wird verständlicher, wenn die Auswahl bereits eine Richtung vorgibt.

### Ein Dashboard mit nachvollziehbaren Zuständen

In einem Dashboard kann die Hauptkarte eine Auswertung enthalten. Kompakte Karten zeigen ergänzende Werte, eine hohe Karte aktuelle Aktivitäten.

Plane dabei auch Zustände ohne fertige Daten:

- Daten werden geladen.
- Es sind noch keine Daten vorhanden.
- Eine Anfrage ist fehlgeschlagen.
- Ein Filter liefert keine Ergebnisse.
- Ein Wert wurde zuletzt zu einem bestimmten Zeitpunkt aktualisiert.

Ein leeres Dashboard sollte erklären, was als Nächstes zu tun ist. Eine dekorative Null ohne Kontext kann dagegen wie ein Fehler aussehen.

Für umfangreiche Datensätze brauchst du zusätzlich geeignete Detailansichten. Das Bento Grid eignet sich als Einstieg in die Informationen, nicht als Ersatz für jede Arbeitsoberfläche.

## Wie bekommt das Layout einen ruhigen, hochwertigen Look?

Ein überzeugendes Bento Grid entsteht durch konsistente Abstände, verständliche Typografie und gezielte Akzente. Die unterschiedliche Kartengröße bringt bereits Bewegung in die Gestaltung.

Lege zunächst wenige Regeln fest:

- Alle Karten verwenden denselben Grundradius.
- Innenabstände folgen einer gemeinsamen Größenfolge.
- Überschriften haben wenige klar definierte Größen.
- Fließtext bleibt ausreichend kontrastreich.
- Eine Akzentfarbe markiert ausgewählte Inhalte.

Im Code erzeugen `rounded-3xl`, `p-6` und `sm:p-8` eine gemeinsame Form. Die farbige Ablaufkarte unterbricht das weiße Raster an einer Stelle.

Wenn du jede Karte mit einem anderen Verlauf, Schatten und Rahmen versiehst, konkurrieren die Flächen miteinander. Wähle einen Hauptakzent und lasse die übrigen Karten zurückhaltender wirken.

Achte außerdem auf den Abstand innerhalb einer Karte. Titel, Erklärung und Vorschau brauchen eine erkennbare Reihenfolge. Außen großzügige Karten wirken trotzdem eng, wenn innen alle Elemente zusammenrücken.

Bei dunklen Varianten reicht es nicht, den Hintergrund auszutauschen. Text, Rahmen, Vorschauen und Fokusmarkierungen brauchen passende Farben. Prüfe dabei die tatsächliche Lesbarkeit jeder Kombination.

Animation ist optional. Ein statisches Raster kann vollständig funktionieren. Ergänze Bewegung erst, wenn sie eine Interaktion erklärt oder eine Zustandsänderung verständlicher macht.

## Welche Fehler solltest du vor der Veröffentlichung prüfen?

Die wichtigsten Fehler betreffen Überlauf, fehlende Klassen, unpassende Höhen und eine widersprüchliche Lesereihenfolge. Prüfe diese Punkte mit echten Inhalten.

### Tailwind erkennt zusammengesetzte Klassennamen nicht zuverlässig

Baue Klassennamen nicht aus unvollständigen Fragmenten zusammen:

```jsx
const className = `lg:col-span-${span}`;
```

Verwende stattdessen vollständig ausgeschriebene Varianten:

```jsx
const layouts = {
  standard: "",
  wide: "md:col-span-2",
  tall: "lg:row-span-2",
};

const className = layouts[variant] ?? layouts.standard;
```

Tailwind durchsucht Quelldateien nach erkennbaren Klassen. Vollständige Klassenstrings sind deshalb der geeignete Weg für solche Varianten.

### Text wird durch feste Höhen abgeschnitten

Teste jede Karte mit längeren Überschriften und zusätzlichen Textzeilen. Vermeide feste Höhen für Flächen, deren Inhalt wachsen muss.

`overflow-hidden` kann dekorative Elemente begrenzen. Auf einer textreichen Karte kann es allerdings auch wichtige Inhalte verbergen. Prüfe seinen Einsatz deshalb gezielt.

### Visuelle Reihenfolge und Tastaturreihenfolge widersprechen sich

Lege die Karten im Quelltext in einer logisch lesbaren Reihenfolge an. Verwende visuelle Umordnung nicht als Ersatz dafür.

Die CSS-Grid-Spezifikation warnt ausdrücklich davor, Rasterplatzierung zur Korrektur einer falschen Quellreihenfolge zu verwenden. Die visuelle Anordnung kann sonst von der Reihenfolge beim linearen Lesen und Navigieren abweichen.

### Interaktive Karten haben keine erkennbare Funktion

Wenn eine Karte navigiert, verwende ein geeignetes Navigationselement. Wenn sie eine Aktion auslöst, verwende einen Button.

Eine anklickbare Fläche braucht außerdem einen sichtbaren Tastaturfokus und eine verständliche Beschriftung. Verlasse dich nicht allein auf eine Farbänderung beim Darüberfahren.

## Wann ist ein Bento Grid die falsche Wahl?

Ein Bento Grid passt schlecht, wenn Informationen zwingend in einer festen Reihenfolge gelesen oder bearbeitet werden müssen. Auch stark unterschiedlich lange Inhalte lassen sich häufig einfacher linear darstellen.

Ein Anmeldeformular braucht eine eindeutige Abfolge. Ein ausführlicher Fachartikel braucht einen ruhigen Lesefluss. Eine große Ergebnisliste braucht Filter, Sortierung und ausreichend Platz für wiederkehrende Informationen.

Das Raster kann solche Bereiche ergänzen. Beispielsweise kann eine Produktseite zuerst Funktionen in Karten zeigen und darunter einen ausführlichen Ablauf erklären.

Prüfe vor dem Einsatz drei Fragen: Ist jede Karte allein verständlich? Hilft die Größe beim Priorisieren? Bleibt die mobile Darstellung angenehm?

Wenn du Inhalte nur deshalb kürzt, damit sie in eine bestimmte Form passen, ändere lieber das Layout. Die Form sollte die Information unterstützen.

## Das solltest du wählen

Starte mit dem fertigen Beispiel und ersetze zuerst die Texte. Prüfe anschließend die mobile Reihenfolge, bevor du die Desktopflächen anpasst.

Für eine Produktseite eignet sich eine große Hauptkarte mit wenigen ergänzenden Funktionen. Für ein Portfolio sollte dein wichtigstes Projekt den Schwerpunkt bilden. Bei einem Dashboard bestimmen Informationsbedarf und Zustände die Kartengröße.

Behalte zunächst natürliche Höhen bei. Ergänze Zeilenüberspannungen erst, wenn die Inhalte stabil sind und die größere Fläche eine erkennbare Aufgabe erfüllt.

Vor der Veröffentlichung teste lange Texte, schmale Zwischenbreiten und Tastaturbedienung. Entferne dekorative Elemente, die wichtige Informationen verdrängen. So erhältst du ein Bento Grid, das du mit echten Inhalten weiterentwickeln kannst.

## Häufig gestellte Fragen (FAQ)

### Wie baue ich ein Bento Grid mit Tailwind?

Du erstellst einen Grid-Container und legst Spalten, Abstände und responsive Kartenbreiten fest. Beginne mit `grid grid-cols-1 gap-4`. Ergänze anschließend größere Raster mit `md:grid-cols-2` oder `lg:grid-cols-4`. Einzelne Karten können dort mehrere Spalten oder Zeilen belegen.

### Brauche ich React für ein Bento Grid?

Nein. Das Layout funktioniert mit HTML und Tailwind, weil CSS Grid die Anordnung übernimmt. React hilft, wenn du Karten wiederverwenden, Inhalte aus Daten erzeugen oder interaktive Zustände verwalten möchtest. In normalem HTML verwendest du `class` anstelle von `className`.

### Funktioniert ein Bento Grid ohne JavaScript?

Ja. Spalten, Abstände und responsive Anpassungen benötigen kein JavaScript. Zusätzlicher Code wird erst für Funktionen wie Filter, dynamische Daten oder ausklappbare Inhalte nötig. Eine statische Funktionsübersicht kann vollständig mit HTML und CSS umgesetzt werden.

### Was ist der Unterschied zwischen Bento Grid und Masonry?

Ein Bento Grid verwendet bewusst unterschiedlich große Flächen in einem gemeinsamen Raster. Masonry ordnet unterschiedlich hohe Elemente möglichst lückenarm an. Bento eignet sich für eine gezielte Informationshierarchie, während Masonry häufig für Bildsammlungen und Inhalte mit variierenden Höhen verwendet wird.

### Warum läuft mein Bento Grid auf dem Smartphone über?

Prüfe zuerst unbedingte `col-span`-Klassen, feste Breiten und lange Inhalte. Eine Karte mit `col-span-2` kann in einem einspaltigen Raster zusätzliche Spalten erzeugen. Aktiviere die Überspannung erst am passenden Breakpoint und lasse innere Textbereiche bei Bedarf mit `min-w-0` schrumpfen.
