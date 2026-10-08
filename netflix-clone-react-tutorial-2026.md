# Netflix Clone React Tutorial: Schritt-für-Schritt-Anleitung 2026

Von Lawrence Dauchy, Gründer von VP0  
Veröffentlicht am 8. Oktober 2026

Einen Netflix Clone mit React baust du am besten als überschaubare Streaming-Oberfläche: mit Filmkarten, einer Suche, einer persönlichen Merkliste und einer Detailansicht. Dieses Tutorial führt dich vom leeren Projekt zu einem funktionierenden Prototyp, den du anschließend erweitern kannst. Du verwendest eigene Beispieldaten und lokale Bilder, damit du zuerst die React-Grundlagen verstehst. Das Ziel ist eine eigenständige Anwendung mit vertrauten Bedienmustern. Verwende dafür einen eigenen Namen und eigene Inhalte, statt Netflix-Logos, Filmplakate oder Videos zu übernehmen. Eine spätere iOS-Version kannst du separat planen; VP0 bietet dafür kostenlose Design-Startpunkte auf Basis von Expo React Native.

## Was brauchst du für einen Netflix Clone mit React?

Du brauchst Node.js, npm, einen Codeeditor und grundlegende JavaScript-Kenntnisse. Besonders hilfreich sind Arrays, Funktionen, Objekte und die Methoden `map` und `filter`.

Für dieses Lernprojekt verwenden wir React mit Vite. React übernimmt die Oberfläche und ihre Zustände. Vite stellt die Entwicklungsumgebung und den Produktionsbuild bereit.

Installiere eine aktuelle, unterstützte Node.js-LTS-Version. Kontrolliere anschließend im Terminal mit `node -v` und `npm -v`, ob beide Programme verfügbar sind. Beachte beim Erstellen des Projekts mögliche Hinweise zur erforderlichen Node-Version.

### Welche Funktionen gehören in die erste Version?

Halte den Umfang bewusst klein:

- Eine Startseite mit einem hervorgehobenen Film.
- Filmreihen nach Genre.
- Eine Suche nach Filmtiteln.
- Eine Merkliste.
- Eine Detailansicht für ausgewählte Filme.
- Ein Layout für Smartphone und Desktop.

Konten, Abonnements und eine echte Streaming-Infrastruktur kommen später. Du lernst mehr, wenn zunächst jede sichtbare Funktion zuverlässig arbeitet.

Ein klickbarer Abspielen-Button braucht entweder einen funktionierenden Player oder eine klare Kennzeichnung als Vorschau. Eine Schaltfläche ohne Wirkung lässt die Anwendung unfertig erscheinen.

### React im Browser oder React Native?

Dieses Tutorial erstellt eine Webanwendung. Sie läuft im Browser und verwendet HTML-Elemente wie `button`, `section` und `img`.

React Native verwendet andere Oberflächenkomponenten. Deshalb kannst du eine Weboberfläche später nicht einfach unverändert in eine native iOS-App kopieren. Übertragbar sind jedoch Teile deiner Datenstruktur und Anwendungslogik.

## Schritt 1: Wie richtest du das React-Projekt ein?

Erstelle zuerst ein neues Vite-Projekt mit der React-Vorlage. Führe diese Befehle im Terminal nacheinander aus:

```bash
npm create vite@latest stream-demo -- --template react
cd stream-demo
npm install
npm run dev
```

Öffne danach die lokale Adresse, die das Terminal anzeigt. Du solltest die Startansicht des Projekts sehen.

Für die erste Version reichen drei Dateien:

- `src/App.jsx` für die Oberfläche und Zustände.
- `src/App.css` für das Layout.
- `src/movies.js` für deine Filmdaten.

Der vorhandene Einstiegspunkt `src/main.jsx` bleibt bestehen. Entferne später die mitgelieferten Beispielstile aus `src/index.css`, damit sie dein Layout nicht unbeabsichtigt verändern.

### Warum starten wir mit lokalen Daten?

Lokale Daten machen den ersten Aufbau leichter nachvollziehbar. Du kannst Suche, Merkliste und Darstellung entwickeln, ohne gleichzeitig Netzwerkfehler oder Zugangsdaten behandeln zu müssen.

Das ist besonders hilfreich beim Debuggen. Wird eine Filmkarte nicht angezeigt, prüfst du zuerst dein Datenobjekt und die Komponente. Du musst noch nicht herausfinden, ob ein externer Dienst erreichbar ist.

Sobald die Oberfläche funktioniert, kannst du die Datenquelle austauschen. Die Komponenten sollten dabei weiterhin denselben Aufbau der Filmobjekte erwarten.

## Schritt 2: Wie strukturierst du die Filmdaten?

Jeder Film erhält eine stabile ID, einen Titel, ein Genre und eine Beschreibung. Bilder werden als lokale Dateien eingebunden.

Lege im Ordner `public` einen Unterordner `images` an. Speichere dort drei eigene oder passend lizenzierte Bilder mit den unten verwendeten Dateinamen.

Erstelle anschließend `src/movies.js`:

```javascript
export const movies = [
  {
    id: "nachtfahrt",
    title: "Nachtfahrt",
    genre: "Thriller",
    year: 2026,
    description:
      "Eine nächtliche Reise führt zwei Fremde durch eine verlassene Stadt.",
    image: "/images/nachtfahrt.jpg",
  },
  {
    id: "fernweh",
    title: "Fernweh",
    genre: "Drama",
    year: 2025,
    description:
      "Eine Fotografin beginnt an der Küste ein neues Leben.",
    image: "/images/fernweh.jpg",
  },
  {
    id: "morgenlicht",
    title: "Morgenlicht",
    genre: "Drama",
    year: 2026,
    description:
      "Drei Freunde versuchen, ein altes Kino wiederzueröffnen.",
    image: "/images/morgenlicht.jpg",
  },
];
```

Diese Titel und Beschreibungen sind fiktive Beispieldaten.

Verwende die ID später als React-Schlüssel und für die Merkliste. Der Titel ist dafür ungeeignet, weil verschiedene Filme denselben Namen haben können.

### Welche Daten solltest du zusätzlich vorbereiten?

Für eine größere Anwendung sind Laufzeit, Altersfreigabe, Untertitelsprachen und ein separates Hintergrundbild sinnvoll. Ergänze diese Felder erst, wenn deine Oberfläche sie tatsächlich verwendet.

Trenne außerdem Filmmetadaten von personenbezogenen Informationen. Ein Filmobjekt beschreibt den Inhalt. Welche Person ihn gespeichert oder angesehen hat, gehört in einen anderen Datenbereich.

So vermeidest du, dass dieselben Filmdaten für jedes Benutzerprofil vollständig kopiert werden müssen.

## Schritt 3: Wie baust du Filmkarten, Suche und Merkliste?

Baue zunächst eine gemeinsame Oberfläche, die alle Kernfunktionen enthält. Anschließend kannst du einzelne Teile in separate Komponenten verschieben.

Ersetze den Inhalt von `src/App.jsx` durch folgenden Code:

```jsx
import { useState } from "react";
import { movies } from "./movies";
import "./App.css";

export default function App() {
  const [query, setQuery] = useState("");
  const [savedIds, setSavedIds] = useState([]);
  const [selectedMovie, setSelectedMovie] = useState(null);
  const [showSavedOnly, setShowSavedOnly] = useState(false);

  const featuredMovie = movies[0];

  const filteredMovies = movies.filter((movie) => {
    const matchesQuery = movie.title
      .toLocaleLowerCase("de-DE")
      .includes(query.trim().toLocaleLowerCase("de-DE"));

    const matchesSaved =
      !showSavedOnly || savedIds.includes(movie.id);

    return matchesQuery && matchesSaved;
  });

  const genres = [
    ...new Set(filteredMovies.map((movie) => movie.genre)),
  ];

  function toggleSaved(id) {
    setSavedIds((current) =>
      current.includes(id)
        ? current.filter((savedId) => savedId !== id)
        : [...current, id]
    );
  }

  return (
    <>
      <header className="header">
        <span className="brand">StreamDemo</span>

        <button
          type="button"
          aria-pressed={showSavedOnly}
          onClick={() => setShowSavedOnly((current) => !current)}
        >
          {showSavedOnly ? "Alle Filme anzeigen" : "Meine Liste"}
        </button>

        <label className="search">
          Film suchen
          <input
            type="search"
            value={query}
            onChange={(event) => setQuery(event.target.value)}
            placeholder="Titel eingeben"
          />
        </label>
      </header>

      <main>
        {!showSavedOnly && query.trim() === "" && (
          <section className="hero">
            <p>Heute entdecken</p>
            <h1>{featuredMovie.title}</h1>
            <p>{featuredMovie.description}</p>
            <button
              type="button"
              onClick={() => setSelectedMovie(featuredMovie)}
            >
              Details ansehen
            </button>
          </section>
        )}

        {filteredMovies.length === 0 && (
          <p role="status">
            {showSavedOnly
              ? "Keine passenden Filme in deiner Liste."
              : "Keine passenden Filme gefunden."}
          </p>
        )}

        {genres.map((genre) => (
          <section className="movie-section" key={genre}>
            <h2>{genre}</h2>

            <div className="movie-row">
              {filteredMovies
                .filter((movie) => movie.genre === genre)
                .map((movie) => (
                  <article className="movie-card" key={movie.id}>
                    <button
                      type="button"
                      className="poster-button"
                      onClick={() => setSelectedMovie(movie)}
                    >
                      <img
                        src={movie.image}
                        alt=""
                        loading="lazy"
                        width="320"
                        height="180"
                      />
                      <span>{movie.title}</span>
                    </button>

                    <p>{movie.year}</p>

                    <button
                      type="button"
                      aria-pressed={savedIds.includes(movie.id)}
                      onClick={() => toggleSaved(movie.id)}
                    >
                      {savedIds.includes(movie.id)
                        ? "Aus Liste entfernen"
                        : "Zur Liste hinzufügen"}
                    </button>
                  </article>
                ))}
            </div>
          </section>
        ))}

        {selectedMovie && (
          <section className="details" aria-label="Filmdetails">
            <h2>{selectedMovie.title}</h2>
            <p>
              {selectedMovie.genre}, {selectedMovie.year}
            </p>
            <p>{selectedMovie.description}</p>
            <button
              type="button"
              onClick={() => setSelectedMovie(null)}
            >
              Details schließen
            </button>
          </section>
        )}
      </main>
    </>
  );
}
```

Damit hast du bereits eine funktionierende Grundlage. Die Suche filtert Titel, der Listenbutton wechselt die Ansicht und jede Filmkarte öffnet einen Detailbereich.

### Warum werden Zustände getrennt?

Jeder Zustand beantwortet eine andere Frage. `query` enthält den Suchtext. `savedIds` speichert die ausgewählten Film-IDs. `selectedMovie` bestimmt den geöffneten Film.

Die gefilterte Filmliste wird daraus berechnet. Du brauchst dafür keinen zusätzlichen Zustand und keinen Effekt. Dadurch gibt es weniger Werte, die versehentlich auseinanderlaufen können.

Beim Speichern verwenden wir eine funktionale Zustandsänderung. React bekommt damit eine Funktion, die aus dem bisherigen Array ein neues erzeugt. Das bestehende Array wird nicht direkt verändert.

### Warum ist die Detailansicht zunächst kein Popup?

Ein normaler Detailbereich ist für die erste Version leichter umzusetzen. Ein modales Fenster benötigt zusätzliche Bedienlogik: Fokus setzen, den Fokus innerhalb des Fensters halten und ihn beim Schließen zurückgeben.

Baue diese Variante später bewusst ein. Eine dunkle Fläche über dem Hintergrund allein ergibt noch keinen gut bedienbaren Dialog.

## Schritt 4: Wie bekommt die Oberfläche den Streaming-Look?

Ein ruhiger Streaming-Look entsteht durch klare Abstände, große Bilder und eine zurückhaltende Farbpalette. Du brauchst dafür zunächst keine Komponentenbibliothek.

Ersetze `src/App.css` durch diese Grundlage:

```css
:root {
  font-family: system-ui, sans-serif;
  color: #f4f4f5;
  background: #111114;
  color-scheme: dark;
}

* {
  box-sizing: border-box;
}

body {
  margin: 0;
}

button,
input {
  font: inherit;
}

button {
  cursor: pointer;
  padding: 0.7rem 1rem;
  border: 1px solid #64646e;
  border-radius: 0.6rem;
  background: #25252c;
  color: inherit;
}

button:focus-visible,
input:focus-visible {
  outline: 3px solid #c4b5fd;
  outline-offset: 3px;
}

.header {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
  padding: 1.25rem clamp(1rem, 4vw, 4rem);
  border-bottom: 1px solid #303038;
}

.brand {
  font-size: 1.4rem;
  font-weight: 800;
}

.search {
  display: grid;
  gap: 0.35rem;
  margin-left: auto;
}

.search input {
  width: min(100%, 22rem);
  padding: 0.7rem;
  border: 1px solid #64646e;
  border-radius: 0.5rem;
  background: #1b1b21;
  color: inherit;
}

main {
  padding: 1.5rem clamp(1rem, 4vw, 4rem) 4rem;
}

.hero {
  padding: clamp(2rem, 6vw, 5rem);
  border-radius: 1rem;
  background: linear-gradient(135deg, #30234b, #18181f);
}

.hero h1 {
  margin: 0.5rem 0;
  font-size: clamp(2.5rem, 7vw, 5rem);
}

.hero p {
  max-width: 42rem;
  line-height: 1.6;
}

.movie-section {
  margin-top: 2.5rem;
}

.movie-row {
  display: grid;
  grid-auto-flow: column;
  grid-auto-columns: minmax(15rem, 19rem);
  gap: 1rem;
  overflow-x: auto;
  padding: 0.5rem 0.25rem 1rem;
}

.movie-card {
  min-width: 0;
}

.poster-button {
  display: block;
  width: 100%;
  padding: 0;
  overflow: hidden;
  text-align: left;
}

.poster-button img {
  display: block;
  width: 100%;
  height: auto;
  aspect-ratio: 16 / 9;
  object-fit: cover;
}

.poster-button span {
  display: block;
  padding: 0.8rem;
  font-weight: 700;
}

.details {
  margin-top: 2rem;
  padding: 1.5rem;
  border: 1px solid #64646e;
  border-radius: 1rem;
}

@media (max-width: 600px) {
  .search {
    width: 100%;
    margin-left: 0;
  }

  .search input {
    width: 100%;
  }
}
```

Entferne außerdem die ursprünglichen Regeln aus `src/index.css`. Sonst können beispielsweise eine voreingestellte Zentrierung oder Hintergrundfarbe den neuen Aufbau beeinflussen.

### Worauf solltest du beim Design achten?

Verwende möglichst einheitliche Bildformate. Unterschiedliche Seitenverhältnisse machen Filmreihen unruhig, selbst wenn Farben und Abstände stimmen.

Zeige wichtige Informationen dauerhaft. Titel und Listenbutton dürfen nicht ausschließlich beim Darüberfahren erscheinen, weil Touchgeräte keinen vergleichbaren Hover-Zustand haben.

Für eine spätere native iOS-Version ist VP0 ein möglicher kostenloser Design-Startpunkt. Die dortigen Expo-React-Native-Designs sind jedoch keine direkt einsetzbaren HTML- und CSS-Vorlagen für dieses Browserprojekt.

## Schritt 5: Wie bleibt die Merkliste nach einem Neustart erhalten?

Für einen lokalen Prototyp kannst du Film-IDs im Browser speichern. Dafür eignet sich `localStorage`, solange du keine geräteübergreifende Synchronisierung benötigst.

Erweitere zunächst den React-Import um `useEffect`:

```jsx
import { useEffect, useState } from "react";
```

Ersetze anschließend die bisherige Initialisierung von `savedIds`:

```jsx
const [savedIds, setSavedIds] = useState(() => {
  try {
    const parsed = JSON.parse(
      localStorage.getItem("stream-demo-saved") ?? "[]"
    );

    return Array.isArray(parsed)
      ? parsed.filter((id) => typeof id === "string")
      : [];
  } catch {
    return [];
  }
});
```

Füge innerhalb der Komponente diesen Effekt hinzu:

```jsx
useEffect(() => {
  try {
    localStorage.setItem(
      "stream-demo-saved",
      JSON.stringify(savedIds)
    );
  } catch {
    // Die Merkliste funktioniert weiter im Arbeitsspeicher.
  }
}, [savedIds]);
```

Die Anwendung startet jetzt mit den gespeicherten IDs und aktualisiert den Browser-Speicher bei Änderungen. Ungültige gespeicherte Daten führen durch die Fehlerbehandlung nicht zum Absturz.

### Welche Grenze hat diese Lösung?

Die Merkliste gehört zum jeweiligen Browser-Speicher. Sie erscheint nicht automatisch auf einem anderen Gerät und kann durch das Löschen der Browserdaten verschwinden.

Für echte Benutzerkonten benötigst du eine serverseitige Speicherung. Dabei muss der Server prüfen, welche Person auf welche Liste zugreifen darf.

Speichere keine Passwörter oder vertraulichen Zugangsdaten in dieser lokalen Merkliste. Sie enthält ausschließlich Film-IDs.

## Schritt 6: Wie ergänzt du Videos und externe Filmdaten?

Ergänze Videos erst, wenn die Katalogoberfläche zuverlässig funktioniert. Für den Anfang reicht ein eigenes kurzes Testvideo.

Lege beispielsweise eine Datei `demo.mp4` im Ordner `public/videos` ab. Ein einfacher Player sieht so aus:

```jsx
<video controls preload="metadata" playsInline>
  <source src="/videos/demo.mp4" type="video/mp4" />
  Dein Browser unterstützt dieses Videoformat nicht.
</video>
```

Füge dem Player eine passende Breite per CSS hinzu. Verwende Untertitel, wenn dein Video gesprochene Inhalte enthält, und kontrolliere die Wiedergabe auf deinen Zielgeräten.

Automatische Wiedergabe ist für diesen Einstieg unnötig. Lass die Person selbst entscheiden, wann ein Video startet.

### Wie bindest du später eine Film-API ein?

Erstelle eine eigene Funktion, die externe Daten in dein Filmformat umwandelt. Deine Komponenten sollen weiterhin Felder wie `id`, `title`, `genre` und `image` erhalten.

Plane dabei drei sichtbare Zustände: Daten werden geladen, Daten wurden geladen und Daten konnten nicht geladen werden. Eine leere Seite beantwortet keine dieser Situationen verständlich.

Prüfe vor der Integration die Nutzungsbedingungen für Metadaten und Bilder. Ein Zugriff auf Filminformationen umfasst nicht automatisch das Recht, die zugehörigen Filme abzuspielen.

Vertrauliche API-Schlüssel gehören auf den Server. Variablen, die Vite in den Browsercode einbindet, sind für Besucher zugänglich und eignen sich deshalb nicht als Geheimnisspeicher.

## Schritt 7: Wie prüfst du den Clone vor der Veröffentlichung?

Prüfe vollständige Abläufe und anschließend den Produktionsbuild. Die Entwicklungsansicht allein reicht dafür nicht.

Gehe diese Schritte durch:

1. Suche nach einem vorhandenen Titel.
2. Suche nach einem unbekannten Titel.
3. Speichere einen Film und öffne „Meine Liste“.
4. Entferne den Film wieder.
5. Lade die Seite neu und kontrolliere gespeicherte Einträge.
6. Öffne und schließe die Filmdetails.
7. Bediene sämtliche Schaltflächen mit der Tastatur.
8. Prüfe die Oberfläche auf einem schmalen Bildschirm.

Kontrolliere außerdem, ob alle lokalen Bilder vorhanden sind. Bei einer Veröffentlichung auf einem System mit anderer Behandlung der Groß- und Kleinschreibung können abweichende Dateinamen auffallen.

### Wie erstellst du den Produktionsbuild?

Führe `npm run build` aus. Wenn der Build erfolgreich ist, prüfst du ihn mit `npm run preview`.

Veröffentliche anschließend den erzeugten Ordner `dist` über einen passenden Hostingdienst. Der Vorschauprozess ist eine lokale Kontrolle und ersetzt keinen Produktionsserver.

Wenn du später mehrere Seiten mit clientseitigem Routing einführst, muss das Hosting direkte Aufrufe dieser Seiten unterstützen. Teste deshalb auch einen Seitenneustart innerhalb einer Detailansicht.

### Was fehlt für einen echten Streamingdienst?

Dieser Prototyp enthält keine Abrechnung, Rechteverwaltung oder belastbare Videoauslieferung. Ein echter Dienst benötigt außerdem Benutzerverwaltung, abgesicherte Schnittstellen und eine Infrastruktur für die Medienbereitstellung.

Auch VP0 liefert Design-Startpunkte und keine vollständige Streaming-Plattform. Für eine native Erweiterung hilft das beim UI; die Daten- und Videotechnik musst du separat entwickeln.

## Das solltest du wählen

Beginne mit React, Vite und lokalen Beispieldaten, wenn du Komponenten, Zustände und Benutzerinteraktionen lernen möchtest. Baue zuerst einen kleinen Katalog, dessen Suche und Merkliste sauber funktionieren.

Ergänze danach eine Datenquelle und einen einfachen Player. Benutzerkonten folgen erst, wenn du die Grenzen der lokalen Speicherung verstanden hast.

Für eine umfangreiche Anwendung mit zusätzlichen Anforderungen solltest du anschließend bewusst entscheiden, ob ein React-Framework und eine serverseitige Architektur besser passen.

Der nächste sinnvolle Schritt ist konkret: Erstelle das Projekt, füge drei eigene Bilder hinzu und arbeite das Tutorial bis zur gespeicherten Merkliste durch. Danach hast du eine Grundlage, deren Verhalten du selbst erklären und verändern kannst.

## Häufig gestellte Fragen (FAQ)

### Wie baue ich einen Netflix Clone mit React 2026?

Erstelle ein React-Projekt mit Vite und entwickle einen Filmkatalog mit lokalen Beispieldaten. Ergänze Filmkarten, Suche, Merkliste und Detailansicht. Danach kannst du einen eigenen Videoplayer und externe Daten anbinden. Verwende einen eigenen Projektnamen und Inhalte, die du nutzen darfst.

### Brauche ich für dieses Tutorial eine Film-API?

Nein, lokale Filmdaten reichen für die erste Version aus. Sie erleichtern das Lernen und die Fehlersuche. Eine API wird sinnvoll, wenn du einen größeren oder regelmäßig aktualisierten Katalog brauchst. Behandle dann auch Ladezustände, Fehler und die erlaubte Nutzung der gelieferten Bilder.

### Kann ich den Clone ohne Backend veröffentlichen?

Ja, den beschriebenen Browserprototyp kannst du als statische Webanwendung veröffentlichen. Die Merkliste bleibt dabei lokal im Browser. Für gemeinsame Benutzerkonten, geräteübergreifende Listen, Zahlungen oder geschützte Inhalte benötigst du zusätzlich eine geeignete serverseitige Lösung.

### Eignet sich VP0 für einen Netflix Clone?

VP0 eignet sich als kostenloser Design-Startpunkt, wenn du später eine native iOS-Oberfläche mit Expo React Native entwickeln möchtest. Für den hier beschriebenen React-Webclone baust du die HTML- und CSS-Komponenten selbst. Prüfe für eine native Erweiterung, ob ein vorhandenes Design zu deinem gewünschten Ablauf passt.

### Wie lange dauert die Umsetzung?

Das hängt von deinen JavaScript-Kenntnissen und dem gewünschten Funktionsumfang ab. Arbeite mit überprüfbaren Etappen: Projekt starten, Karten darstellen, Suche ergänzen, Merkliste speichern und Build prüfen. Eine funktionsfähige Lernoberfläche ist deutlich überschaubarer als ein Streamingdienst mit Konten, Medienrechten und eigener Videoauslieferung.
