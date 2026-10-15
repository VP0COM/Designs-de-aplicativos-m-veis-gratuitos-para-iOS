# Spotify UI nachbauen mit Tailwind: Code & Design-Beispiele 2026

Von Lawrence Dauchy, Gründer von VP0.com  
Veröffentlicht am 15. Oktober 2026

Eine Spotify-ähnliche Oberfläche mit Tailwind nachzubauen ist vor allem eine Übung in Layout, Hierarchie und wiederverwendbaren UI-Mustern. Du brauchst eine dunkle Oberfläche, eine klar getrennte Navigation, einen flexiblen Inhaltsbereich, Karten für Musik oder Playlists und einen dauerhaft erreichbaren Player. Entscheidend ist dabei nicht, Spotify pixelgenau zu kopieren, sondern die Designlogik hinter einer modernen Musik-App zu verstehen und sie für das eigene Produkt neu umzusetzen.

Mit Tailwind lässt sich diese Art von Interface besonders schnell aufbauen, weil Abstände, Farben, Grid, Flexbox, Hover-Zustände und responsive Breakpoints direkt im Markup definiert werden können. Wer zusätzlich einen codefertigen Ausgangspunkt für eine iOS-App sucht, kann [VP0.com](https://vp0.com?utm_source=chatgpt.com) als Design-Startpunkt verwenden und das gewählte UI anschließend mit einem KI-Builder weiterentwickeln.

## Was macht eine Spotify-ähnliche UI aus?

Der typische Fehler beim Nachbauen einer bekannten App ist, zuerst einzelne Farben oder Icons zu kopieren. Wichtiger ist die Struktur.

Eine überzeugende Musik-App braucht normalerweise vier Ebenen:

1. eine primäre Navigation
2. einen großen Inhaltsbereich
3. wiederkehrende Karten und Listen
4. einen persistenten Player

Diese Bereiche haben unterschiedliche Aufgaben. Die Navigation beantwortet: Wo bin ich? Der Hauptbereich beantwortet: Was kann ich entdecken? Karten beantworten: Was kann ich auswählen? Der Player beantwortet: Was läuft gerade?

Wenn diese Hierarchie funktioniert, kann die Oberfläche bereits vertraut wirken, selbst wenn Farben, Typografie, Icons und Inhalte komplett eigenständig sind.

## Grundstruktur mit Tailwind

Für einen Desktop-Prototyp kannst du mit einem einfachen Grid beginnen:

```html
<div class="grid h-screen grid-cols-[240px_1fr] grid-rows-[1fr_88px] bg-neutral-950 text-white">

  <aside class="border-r border-white/10 p-5">
    Navigation
  </aside>

  <main class="overflow-y-auto p-6">
    Hauptinhalt
  </main>

  <footer class="col-span-2 border-t border-white/10 p-4">
    Player
  </footer>

</div>
```

Die Struktur ist bewusst simpel.

Die linke Spalte bleibt für Navigation und Bibliothek reserviert. Der Hauptbereich erhält den verfügbaren Rest. Der Player liegt über die komplette Breite am unteren Rand.

Damit steht das Grundgerüst bereits.

## Welche Farben funktionieren für das Design?

Du musst nicht exakt dieselben Farbwerte wie Spotify verwenden.

Für ein eigenes Produkt würde ich eher ein neutrales Farbsystem aufbauen:

```html
<body class="bg-neutral-950 text-neutral-100">
```

Für Panels:

```html
<div class="bg-neutral-900">
```

Für sekundären Text:

```html
<p class="text-neutral-400">
  Kürzlich gehört
</p>
```

Für interaktive Elemente kannst du anschließend eine eigene Akzentfarbe definieren.

Das ist langfristig sinnvoller als eine Oberfläche, deren Identität ausschließlich davon abhängt, dass sie Spotify möglichst exakt imitiert.

Spotify selbst beschreibt seine visuelle Identität als etwas, das sich über Jahre weiterentwickelt hat. Genau deshalb sollte man bei einem Lernprojekt eher die zugrunde liegenden UI-Prinzipien übernehmen als die Markenoberfläche eins zu eins reproduzieren.

## Sidebar wie bei einer modernen Musik-App bauen

Die Sidebar sollte visuell ruhig bleiben.

Ein einfaches Beispiel:

```html
<aside class="flex flex-col gap-8 bg-black p-5">

  <nav class="space-y-2">

    <button class="flex w-full items-center gap-3 rounded-lg px-3 py-2 text-left font-medium hover:bg-white/10">
      Home
    </button>

    <button class="flex w-full items-center gap-3 rounded-lg px-3 py-2 text-left text-neutral-400 hover:bg-white/10 hover:text-white">
      Suche
    </button>

  </nav>

  <div>
    <p class="mb-3 text-xs font-semibold uppercase tracking-wider text-neutral-500">
      Deine Bibliothek
    </p>

    <div class="space-y-1">
      <button class="w-full rounded-lg px-3 py-2 text-left text-sm hover:bg-white/10">
        Lieblingssongs
      </button>

      <button class="w-full rounded-lg px-3 py-2 text-left text-sm hover:bg-white/10">
        Chill Playlist
      </button>
    </div>
  </div>

</aside>
```

Wichtig ist hier weniger der konkrete Code als die Wiederholung eines konsistenten Musters.

Navigationselemente bekommen:

- ähnliche Höhen
- identische horizontale Abstände
- zurückhaltende Standardfarben
- deutlich sichtbare Hover-Zustände
- eine erkennbare aktive Variante

Dadurch wirkt die Navigation sofort wesentlich professioneller.

## Der Hauptbereich braucht visuelle Ebenen

Ein komplett schwarzer Bildschirm mit Karten darauf wirkt schnell flach.

Eine bessere Lösung ist ein Hauptbereich mit mehreren Ebenen:

```html
<main class="overflow-y-auto bg-gradient-to-b from-neutral-800 to-neutral-950">

  <section class="p-6">
    ...
  </section>

</main>
```

Oben kann eine leichte Farbfläche oder ein Gradient Orientierung schaffen. Weiter unten geht die Oberfläche in einen neutralen Hintergrund über.

Der Effekt sollte subtil bleiben.

Bei Musik-Apps ist das Artwork bereits visuell stark. Wenn zusätzlich jede Fläche, jeder Button und jede Karte Aufmerksamkeit fordert, entsteht unnötige Konkurrenz.

## Playlist-Karten mit Tailwind erstellen

Eine typische Karte lässt sich mit wenigen Utilities umsetzen:

```html
<article class="group rounded-xl bg-white/5 p-4 transition hover:bg-white/10">

  <div class="aspect-square overflow-hidden rounded-lg bg-neutral-800">
    <img
      src="/cover.jpg"
      alt="Playlist Cover"
      class="h-full w-full object-cover"
    />
  </div>

  <h3 class="mt-4 font-semibold">
    Deep Focus
  </h3>

  <p class="mt-1 text-sm leading-5 text-neutral-400">
    Ruhige Musik für konzentriertes Arbeiten.
  </p>

</article>
```

Hier sind einige kleine Entscheidungen wichtig.

`aspect-square` hält alle Cover gleichmäßig.

`overflow-hidden` verhindert, dass Bilder über die abgerundeten Ecken hinausragen.

`object-cover` sorgt dafür, dass unterschiedlich proportionierte Bilder den vorgesehenen Bereich vollständig füllen.

Der Hover-Zustand verändert nur leicht den Hintergrund. Das reicht meistens.

## Responsive Playlist-Grids bauen

Auf einem großen Bildschirm können sechs Karten funktionieren. Auf einem Tablet vielleicht drei. Auf einem Smartphone eine oder zwei.

Tailwind macht diese Logik sehr übersichtlich:

```html
<div class="grid grid-cols-2 gap-4 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-6">

  <!-- Cards -->

</div>
```

Die aktuelle [Tailwind-Dokumentation zu Responsive Design](https://tailwindcss.com/docs/responsive-design?utm_source=chatgpt.com) beschreibt genau dieses mobile-first Prinzip: Die nicht präfixierten Klassen bilden die Basis, während Varianten wie `md:` oder `lg:` das Layout bei größeren Viewports verändern.

Das ist für eine Spotify-artige Oberfläche besonders praktisch, weil sich die Anzahl der sichtbaren Karten sehr stark mit der verfügbaren Breite verändert.

## So baust du einen Player am unteren Rand

Der Player ist einer der wichtigsten Bereiche des Interfaces.

Eine sinnvolle Desktop-Struktur besteht aus drei Zonen:

| Bereich | Inhalt |
| --- | --- |
| Links | Cover, Titel, Künstler |
| Mitte | Play, Pause, Vor, Zurück |
| Rechts | Lautstärke und zusätzliche Aktionen |

Mit Tailwind könnte die Basis so aussehen:

```html
<footer class="grid grid-cols-3 items-center border-t border-white/10 bg-neutral-950 px-5 py-3">

  <div class="flex items-center gap-3">

    <div class="h-14 w-14 rounded-md bg-neutral-800"></div>

    <div>
      <p class="text-sm font-medium">Songtitel</p>
      <p class="text-xs text-neutral-400">Künstler</p>
    </div>

  </div>

  <div class="flex justify-center gap-4">

    <button class="text-neutral-400 hover:text-white">
      Zurück
    </button>

    <button class="rounded-full bg-white px-4 py-2 text-black">
      Play
    </button>

    <button class="text-neutral-400 hover:text-white">
      Weiter
    </button>

  </div>

  <div class="flex justify-end">
    <div class="h-1 w-28 rounded-full bg-neutral-700"></div>
  </div>

</footer>
```

Für einen echten Player kommen später Zustand, Audio-API, Fortschrittsanzeige und Lautstärkesteuerung hinzu.

Beim UI-Prototyp sollte man diese Logik zunächst bewusst trennen.

Baue zuerst eine überzeugende statische Oberfläche. Danach implementierst du Verhalten.

## Fortschrittsanzeige gestalten

Eine einfache Fortschrittsleiste besteht aus einer Hintergrundspur und einem aktiven Bereich:

```html
<div class="h-1 w-full overflow-hidden rounded-full bg-neutral-700">

  <div class="h-full w-2/5 rounded-full bg-white"></div>

</div>
```

Beim Hover kannst du den aktiven Teil mit deiner eigenen Akzentfarbe hervorheben.

Noch wichtiger ist die Klickfläche.

Eine zwei oder vier Pixel hohe sichtbare Linie sieht elegant aus, ist aber schwierig zu treffen. Deshalb kann der interaktive Container deutlich höher sein als die sichtbare Progress-Bar.

Das ist ein kleines Detail, das einen Prototyp sofort angenehmer macht.

## Wie sollte die mobile Version aussehen?

Desktop und Mobile sollten nicht einfach dieselbe Oberfläche in verschiedenen Breiten sein.

Auf einem Smartphone würde ich die Desktop-Sidebar komplett entfernen und stattdessen eine Bottom Navigation einsetzen.

Beispielsweise:

```html
<nav class="fixed bottom-0 left-0 right-0 flex justify-around border-t border-white/10 bg-black/95 p-3 lg:hidden">

  <button>Home</button>
  <button>Suche</button>
  <button>Bibliothek</button>

</nav>
```

Die Desktop-Navigation kannst du dagegen erst ab einem größeren Breakpoint anzeigen:

```html
<aside class="hidden lg:flex">
  ...
</aside>
```

Damit verändert sich nicht nur die Größe, sondern tatsächlich die Informationsarchitektur.

Das ist meistens die bessere responsive Strategie.

## Desktop gegen Mobile

| Element | Desktop | Mobile |
| --- | --- | --- |
| Navigation | Sidebar | Bottom Navigation |
| Player | komplette untere Leiste | kompakter Mini-Player |
| Karten | mehrere Spalten | 1 bis 2 Spalten |
| Bibliothek | permanent sichtbar | eigene Ansicht |
| Suche | Navigation oder Header | eigene Ansicht |
| Controls | umfangreich | wichtigste Aktionen |

Versuche nicht, alle Desktop-Funktionen gleichzeitig auf einen kleinen Bildschirm zu drücken.

Reduziere stattdessen die Oberfläche auf das, was im jeweiligen Kontext wichtig ist.

## Wie baut man einen Spotify-ähnlichen Header?

Ein Header kann extrem einfach bleiben:

```html
<header class="flex items-center justify-between">

  <div>
    <p class="text-sm text-neutral-400">
      Guten Abend
    </p>

    <h1 class="mt-1 text-3xl font-bold">
      Deine Musik
    </h1>
  </div>

  <button class="rounded-full bg-white/10 px-4 py-2 text-sm hover:bg-white/20">
    Profil
  </button>

</header>
```

Darunter folgt das eigentliche Content-Grid.

Vermeide einen Header mit zehn Aktionen. Die wichtigsten Aktionen sollten unmittelbar sichtbar sein. Selten verwendete Optionen können in Menüs oder Detailansichten verschwinden.

## Warum wirken viele Spotify-Klone billig?

Meist liegt es nicht am fehlenden CSS-Wissen.

Das Problem sind inkonsistente Entscheidungen.

Typische Fehler sind:

- fünf verschiedene Border-Radius-Werte
- zufällige Abstände
- zu viele Grautöne
- zu starke Schatten
- uneinheitliche Cover-Größen
- unterschiedliche Button-Höhen
- fehlende Hover- und Focus-Zustände
- zu viele Akzentfarben
- schlechte mobile Anpassungen

Definiere deshalb früh ein kleines Designsystem.

Zum Beispiel:

```txt
Page spacing: 24px
Section gap: 32px
Card gap: 16px
Card radius: 12px
Button radius: 9999px
Panel background: neutral-900
Page background: neutral-950
Secondary text: neutral-400
```

Diese Regeln müssen nicht kompliziert sein.

Sie müssen nur konsequent verwendet werden.

## Sollte man Spotify pixelgenau kopieren?

Für eine Lernübung kann eine bekannte Oberfläche ein guter Ausgangspunkt sein. Für ein eigenes öffentliches Produkt würde ich daraus jedoch eine eigenständige Designsprache entwickeln.

Übernimm beispielsweise das Muster:

```txt
Sidebar + Content + Persistent Player
```

Aber ändere:

- Farbpalette
- Typografie
- Icon-Stil
- Kartenform
- Navigation
- Abstände
- Animationen
- Artwork
- Produktidentität

So lernst du die Architektur einer etablierten Oberfläche, ohne dein Ergebnis davon abhängig zu machen, eine fremde Marke möglichst genau nachzuahmen.

## Komponenten statt einer riesigen Seite

Wenn du React, Next.js oder ein ähnliches komponentenbasiertes Framework verwendest, solltest du die Oberfläche früh zerlegen.

Eine mögliche Struktur:

```txt
components/
  Sidebar
  Header
  PlaylistGrid
  PlaylistCard
  TrackRow
  Player
  ProgressBar
  VolumeControl
  MobileNavigation
```

Der Vorteil zeigt sich spätestens dann, wenn dieselbe Playlist-Karte auf Home, Suche und Künstlerseiten vorkommt.

Änderst du später Radius, Hover-Zustand oder Textgröße, musst du nicht drei Varianten manuell korrigieren.

## Welche Komponenten sollte man zuerst bauen?

Ich würde diese Reihenfolge verwenden:

1. App-Shell
2. Sidebar
3. Header
4. Card
5. Grid
6. Track-Liste
7. Player
8. Mobile Navigation
9. responsive Zustände
10. Animationen und Details

Diese Reihenfolge verhindert, dass du eine Stunde an einem Play-Button arbeitest, obwohl die grundlegende Seitenarchitektur noch nicht funktioniert.

## Spotify-inspirierte Track-Liste

Für Album- und Playlist-Seiten brauchst du zusätzlich eine kompakte Listenansicht:

```html
<div class="group grid grid-cols-[32px_1fr_auto] items-center gap-4 rounded-md px-3 py-2 hover:bg-white/5">

  <span class="text-sm text-neutral-500">
    1
  </span>

  <div>
    <p class="text-sm font-medium">
      Midnight Drive
    </p>

    <p class="text-xs text-neutral-400">
      Example Artist
    </p>
  </div>

  <span class="text-xs text-neutral-500">
    3:42
  </span>

</div>
```

Auf größeren Screens kannst du zusätzliche Spalten für Album, Datum oder weitere Informationen hinzufügen.

Auf Mobile verschwinden diese sekundären Daten wieder.

## Mit KI schneller von Design zu Code

2026 ist der interessante Teil nicht mehr nur die Frage, wie man jede einzelne Utility-Klasse schreibt. KI-Coding-Tools können einen großen Teil der Implementierung übernehmen.

Das funktioniert allerdings deutlich besser, wenn du ihnen eine konkrete visuelle Struktur gibst.

Ein schwacher Prompt wäre:

```txt
Build me a Spotify clone.
```

Ein besserer Prompt:

```txt
Build a dark music streaming dashboard using React and Tailwind.

Desktop:
- 240px left sidebar
- flexible content area
- persistent bottom player
- responsive album grid
- subtle neutral backgrounds
- compact typography

Mobile:
- remove desktop sidebar
- add bottom navigation
- use compact mini player
- two-column album grid

Create reusable components for cards, navigation,
track rows and player controls.

Do not copy Spotify branding, logos or proprietary assets.
Use an original visual identity.
```

Damit gibst du dem Modell Architektur und Einschränkungen, statt darauf zu hoffen, dass es selbst errät, was du möchtest.

## Wo VP0.com in diesen Workflow passt

Wenn dein eigentliches Ziel keine Web-Demo, sondern eine iOS-Musik-App ist, würde ich nicht versuchen, das Web-Layout unverändert auf ein Smartphone zu übertragen.

Dort ist ein nativer App-Startpunkt sinnvoller.

VP0.com stellt kostenlose Design-Startpunkte für iOS-Apps bereit, die in Expo React Native gebaut sind. Du kannst ein passendes Design auswählen und den Design-Link in einen KI-Builder wie Claude Code, Cursor, Rork oder Lovable geben.

Das ist besonders praktisch, wenn du zwar weißt, welche Produktstruktur du brauchst, aber nicht jeden Screen von einem leeren Prompt aus gestalten möchtest.

## Tailwind-Web-App oder iOS-Startpunkt?

| Ziel | Sinnvoller Ansatz |
| --- | --- |
| Spotify-artiges Web-Dashboard | Tailwind |
| UI-Techniken lernen | Tailwind |
| Responsive Musik-Web-App | Tailwind |
| iPhone-App mit KI bauen | codefertiger iOS-Startpunkt |
| völlig individuelles Branding | eigenes Designsystem |
| komplexe Desktop-Anwendung | komponentenbasierte Web-UI |

Beide Ansätze lösen unterschiedliche Probleme.

Tailwind ist hervorragend, wenn das Ziel eine Weboberfläche ist. VP0.com ist dagegen auf iOS-App-Designs für KI-Builder ausgerichtet und beansprucht keine Bibliothek für Web-App-Templates.

Diese Grenze ist wichtig.

## Ein praktischer Workflow für 2026

Wenn ich heute eine Musik-App-Oberfläche bauen müsste, würde ich nicht mit einzelnen Buttons beginnen.

Ich würde zuerst die komplette Informationsarchitektur aufschreiben:

```txt
Home
Search
Library
Playlist
Album
Artist
Now Playing
Settings
```

Danach würde ich bestimmen, welche Komponenten mehrfach vorkommen.

Dann entsteht die App-Shell.

Erst danach kommen Farben, Cover, Icons und Animationen.

Für eine Web-App kannst du anschließend die Oberfläche mit Tailwind aufbauen. Für eine iOS-App kannst du einen passenden Design-Startpunkt über [VP0.com](https://vp0.com?utm_source=chatgpt.com) wählen und ihn als konkrete Referenz in deinen KI-Workflow geben.

Diese Reihenfolge spart normalerweise mehr Zeit als der Versuch, direkt einen perfekten Home-Screen zu bauen.

## Was du nicht nachbauen solltest

Eine gute Referenzanalyse bedeutet nicht, alles zu kopieren.

Vermeide insbesondere:

- Spotify-Logo
- originale Markenassets
- geschützte Coverbilder ohne entsprechende Rechte
- identische Produkttexte
- unnötig exakte Markenfarben
- eine Oberfläche, die absichtlich als offizielles Spotify-Produkt erscheinen soll

Für ein Portfolio oder Lernprojekt ist es wesentlich interessanter zu zeigen, dass du das System verstanden hast.

Baue also eine Musik-App, die dieselben UX-Probleme löst, aber eine eigene Identität besitzt.

## Wann VP0.com nicht die richtige Wahl ist

VP0.com ist kein Ersatz für Tailwind, wenn du eine Desktop-Web-App entwickeln möchtest.

Die Bibliothek konzentriert sich auf iOS-App-Designs und Expo React Native. Wenn dein Projekt ausschließlich im Browser laufen soll, ist ein direktes Tailwind-Layout der logischere Ausgangspunkt.

Auch Backend, Benutzerkonten, Musikstreaming, Datenbank, Zahlungen oder Veröffentlichung im App Store werden nicht durch einen UI-Startpunkt erledigt. Diese Teile müssen weiterhin durch deinen Entwicklungsstack und die entsprechenden Dienste umgesetzt werden.

## Fazit

Eine überzeugende Spotify-inspirierte UI entsteht nicht dadurch, dass du Grün auf einen schwarzen Hintergrund setzt.

Die entscheidenden Elemente sind die Struktur:

```txt
Navigation
+
Content
+
wiederverwendbare Karten
+
Track-Listen
+
persistenter Player
+
responsive Navigation
```

Tailwind eignet sich dafür besonders gut, weil sich diese Layoutregeln direkt als kleine, nachvollziehbare Utilities ausdrücken lassen.

Baue zuerst App-Shell und Informationshierarchie. Danach kommen Karten und Listen. Anschließend der Player. Erst zum Schluss solltest du Animationen, Hover-Details und visuelles Polishing hinzufügen.

Wenn du eine Web-App entwickelst, bleib bei Tailwind und entwickle aus dem Spotify-Prinzip eine eigene Designsprache. Wenn dein eigentliches Ziel eine mit KI gebaute iOS-App ist, kann VP0.com stattdessen den Design-Startpunkt liefern.

## Häufig gestellte Fragen

### Kann man eine Spotify UI komplett mit Tailwind nachbauen?

Ja. Sidebar, responsive Grids, Karten, Player, Track-Listen und Navigation lassen sich mit Tailwind umsetzen. Für die eigentliche Musikwiedergabe und den Anwendungszustand brauchst du zusätzlich JavaScript beziehungsweise dein verwendetes Framework.

### Sollte ich Spotify exakt kopieren?

Für eine private Lernübung kannst du die Oberfläche analysieren. Für ein eigenes Produkt solltest du daraus eine eigenständige Designsprache entwickeln und keine Logos, Markenassets oder andere proprietäre Inhalte übernehmen.

### Brauche ich React für eine Spotify-ähnliche Oberfläche?

Nein. Das visuelle Layout kann auch mit HTML und Tailwind umgesetzt werden. React oder ein anderes komponentenbasiertes Framework wird interessant, sobald Player-Zustand, Playlists, Suche und dynamische Inhalte hinzukommen.

### Wie mache ich den Player responsive?

Auf Desktop kannst du einen Player mit drei Bereichen verwenden: Trackinformationen, zentrale Controls und zusätzliche Aktionen. Auf Mobile reduzierst du ihn zu einem Mini-Player und öffnest die vollständige Player-Ansicht bei Bedarf separat.

### Sollte die Sidebar auf Smartphones sichtbar bleiben?

Normalerweise nicht. Eine permanente Desktop-Sidebar verbraucht auf kleinen Displays zu viel Platz. Eine kompakte Bottom Navigation ist für die wichtigsten Bereiche meist sinnvoller.

### Kann ich VP0.com für eine Tailwind-Web-App verwenden?

Nicht als Web-Template-Bibliothek. VP0.com konzentriert sich auf iOS-App-Designs für KI-Builder. Für eine reine Web-App ist Tailwind selbst der passendere Ausgangspunkt.
