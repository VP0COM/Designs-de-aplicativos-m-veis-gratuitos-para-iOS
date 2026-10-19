# Airbnb Clone Next.js: Template, Komponenten & Beispiele 2026

Von Lawrence Dauchy, Gründer von VP0.com  
Veröffentlicht am 19. Oktober 2026

Ein Airbnb Clone mit Next.js ist 2026 ein gutes Projekt, wenn du lernen willst, wie moderne Marktplätze aufgebaut sind. Statt Airbnb pixelgenau zu kopieren, solltest du die grundlegende Produktlogik nachbauen: Startseite mit Suche, Karten für Unterkünfte, Filter, Detailseiten, Bildergalerie, Datumswahl, Gästeauswahl und einen einfachen Buchungsablauf. Next.js eignet sich dafür besonders gut, weil du Oberfläche, Routing und serverseitige Logik in einem Projekt strukturieren kannst. Für das UI würde ich nicht bei einem leeren Prompt anfangen. Nutze ein klares Design als visuelle Referenz und zerlege es anschließend in wiederverwendbare Komponenten.

## Welche Architektur braucht ein Airbnb Clone mit Next.js?

Ein sinnvoller Clone besteht nicht aus einer riesigen Seite. Teile das Produkt in kleine Bereiche auf, die unabhängig voneinander weiterentwickelt werden können.

Eine mögliche Struktur sieht so aus:

```text
app/
  page.tsx
  search/
    page.tsx
  listings/
    [id]/
      page.tsx
  booking/
    page.tsx

components/
  Header.tsx
  SearchBar.tsx
  CategoryFilter.tsx
  ListingGrid.tsx
  ListingCard.tsx
  ImageGallery.tsx
  DatePicker.tsx
  GuestPicker.tsx
  BookingCard.tsx

lib/
  listings.ts
  search.ts
  booking.ts
```

Der App Router ist dafür ein natürlicher Ausgangspunkt. Next.js beschreibt den App Router als den neueren Router, der unter anderem moderne React-Funktionen wie Server Components unterstützt. Die [offizielle Next.js-Dokumentation](https://nextjs.org/docs) ist deshalb die externe Referenz, die ich beim technischen Aufbau offenhalten würde.

Wichtig ist die Trennung zwischen Daten, Darstellung und Interaktion. Eine `ListingCard` sollte zum Beispiel nicht gleichzeitig Suchparameter verwalten, Buchungen speichern und Bilder laden.

| Bereich | Aufgabe | Typische Komponente |
| --- | --- | --- |
| Navigation | Logo, Suche, Benutzeraktionen | `Header` |
| Suche | Ort, Datum, Gäste | `SearchBar` |
| Ergebnisse | Unterkünfte darstellen | `ListingGrid` |
| Unterkunft | Bilder und Details | `ImageGallery` |
| Buchung | Datum, Gäste, Preisübersicht | `BookingCard` |
| Filter | Kategorien und Eigenschaften | `CategoryFilter` |

So bleibt dein Clone verständlich, auch wenn du später Authentifizierung, Favoriten oder echte Daten hinzufügst.

## Welche Komponenten solltest du zuerst bauen?

Beginne nicht mit dem Backend. Baue zuerst den sichtbaren Kern des Produkts.

Ich würde diese Reihenfolge wählen:

1. Header
2. Suchleiste
3. Kategorie- oder Filterleiste
4. Listing Card
5. Listing Grid
6. Detailseite
7. Bildergalerie
8. Buchungskarte
9. Datumswahl
10. Gästeauswahl

Der wichtigste Baustein ist die Listing Card. Sie taucht mehrfach auf und zwingt dich früh zu guten Entscheidungen bei Bildern, Abständen, Typografie und responsivem Verhalten.

Eine einfache Komponente könnte so aussehen:

```tsx
type ListingCardProps = {
  title: string
  location: string
  image: string
  price: number
  rating?: number
}

export function ListingCard({
  title,
  location,
  image,
  price,
  rating,
}: ListingCardProps) {
  return (
    <article>
      <div className="aspect-square overflow-hidden rounded-2xl">
        <img
          src={image}
          alt={title}
          className="h-full w-full object-cover"
        />
      </div>

      <div className="mt-3">
        <div className="flex items-start justify-between gap-3">
          <h3 className="font-medium">{location}</h3>
          {rating && <span>{rating}</span>}
        </div>

        <p className="text-sm text-neutral-500">{title}</p>

        <p className="mt-2">
          <strong>{price} €</strong> pro Nacht
        </p>
      </div>
    </article>
  )
}
```

Im echten Projekt würde ich für die Bilder die Bildfunktionen von Next.js prüfen und die Karte anschließend als wiederverwendbaren Baustein behandeln.

## Wie sollte die Startseite aufgebaut sein?

Die Startseite braucht weniger Elemente, als viele erste Clones enthalten.

Ein guter Aufbau ist:

```text
Header
↓
Search Bar
↓
Category Filters
↓
Listing Grid
↓
Pagination oder weitere Ergebnisse
```

Der häufigste Fehler ist, zu früh jede mögliche Airbnb-Funktion nachbauen zu wollen. Für einen überzeugenden Prototyp brauchst du zunächst einen einzigen funktionierenden Suchpfad.

Ein Nutzer sollte beispielsweise Folgendes tun können:

```text
Berlin auswählen
→
Datum festlegen
→
2 Gäste auswählen
→
Unterkünfte sehen
→
Unterkunft öffnen
→
Buchungsdetails prüfen
```

Wenn dieser Ablauf funktioniert und visuell zusammenhängend aussieht, hast du bereits einen wesentlich besseren Clone als ein Projekt mit 30 halbfertigen Funktionen.

## Wie baust du die Suchleiste?

Die Suchleiste ist nicht nur Dekoration. Sie verbindet mehrere Zustände miteinander.

Du brauchst mindestens:

```ts
const search = {
  location: "",
  checkIn: null,
  checkOut: null,
  adults: 1,
  children: 0,
}
```

Auf Desktop kannst du diese Werte nebeneinander darstellen:

```text
Wo?
Berlin

Check-in
24. Oktober

Check-out
27. Oktober

Gäste
2 Gäste
```

Auf kleinen Displays solltest du nicht versuchen, dieselbe breite Leiste zusammenzuquetschen. Eine kompakte Schaltfläche, die einen Suchdialog öffnet, ist meistens leichter zu bedienen.

Halte den Suchzustand an einer Stelle. Wenn Datum, Gästeauswahl und Ergebnisliste jeweils eigene Kopien derselben Daten verwalten, entstehen unnötig schnell Synchronisationsprobleme.

## Wie sollte die Listing Card aussehen?

Die Karte muss Informationen schnell lesbar machen. Dafür brauchst du keine komplizierte Gestaltung.

Konzentriere dich auf:

- ein großes Bild
- einen klaren Ortsnamen
- eine kurze Beschreibung
- den Preis
- optional eine Bewertung
- eine Favoritenaktion
- konsistente Abstände
- große klickbare Flächen

Vermeide zehn verschiedene Schriftgrößen oder mehrere konkurrierende Farben. Bei einem Unterkunfts-Marktplatz kommen bereits durch die Fotos sehr viele visuelle Informationen auf den Screen.

Für das Grid kannst du mit einem einfachen responsiven Raster starten:

```tsx
<div className="
  grid
  grid-cols-1
  gap-6
  sm:grid-cols-2
  lg:grid-cols-3
  xl:grid-cols-4
">
  {listings.map((listing) => (
    <ListingCard
      key={listing.id}
      {...listing}
    />
  ))}
</div>
```

Damit lässt sich die Grundidee schnell testen, bevor du Zeit in komplexe Filter oder Animationen steckst.

## Was gehört auf die Unterkunftsseite?

Die Detailseite ist der wichtigste zweite Screen nach der Startseite.

Sie sollte dem Nutzer drei Fragen beantworten:

1. Was ist das für eine Unterkunft?
2. Passt sie zu meiner Reise?
3. Wie kann ich den Aufenthalt auswählen?

Ein sinnvoller Aufbau:

| Abschnitt | Inhalt | Priorität |
| --- | --- | --- |
| Titelbereich | Name, Ort, Bewertung | Hoch |
| Galerie | Mehrere Bilder | Hoch |
| Informationen | Gäste, Zimmer, Betten | Hoch |
| Beschreibung | Eigenschaften der Unterkunft | Mittel |
| Ausstattung | WLAN, Küche, Parkplatz usw. | Mittel |
| Buchung | Datum, Gäste, Preisübersicht | Hoch |
| Karte | Lage oder Umgebung | Optional |

Die Buchungskarte sollte auf Desktop gut sichtbar bleiben. Auf Mobile kann daraus eine feste untere Aktionsleiste werden, die Preis und Buchungsaktion zeigt.

## Wie baust du die Bildergalerie?

Bei einem Airbnb Clone tragen Bilder einen großen Teil der Oberfläche. Eine Unterkunft ohne überzeugende Galerie fühlt sich sofort unfertig an.

Für die erste Version reicht:

- ein großes Hauptbild
- vier kleinere Bilder auf Desktop
- ein einzelnes großes Bild auf Mobile
- eine Schaltfläche für alle Fotos
- ein Modal oder Overlay für die vollständige Galerie

Du brauchst am Anfang keinen komplexen Slider.

Achte stattdessen auf feste Seitenverhältnisse. Unterschiedlich hohe Bilder erzeugen schnell Layoutsprünge und unruhige Karten.

Bei Next.js kannst du später die Bildoptimierung des Frameworks einsetzen, statt jedes Bild manuell für verschiedene Viewports vorzubereiten.

## Wie setzt du Filter sinnvoll um?

Baue Filter erst, wenn die grundlegende Ergebnisliste funktioniert.

Für einen Clone reichen beispielsweise:

```ts
type Filters = {
  minPrice?: number
  maxPrice?: number
  bedrooms?: number
  guests?: number
  propertyType?: string
}
```

Danach kannst du die Filter mit URL-Parametern verbinden:

```text
/search?location=berlin&guests=2&bedrooms=1
```

Das hat einen praktischen Vorteil: Der Zustand der Suche bleibt über die URL nachvollziehbar.

Ein Nutzer kann eine gefilterte Seite neu laden oder weitergeben, ohne dass die Auswahl vollständig verloren gehen muss.

## Welche Daten brauchst du für ein Listing?

Halte dein Datenmodell am Anfang bewusst klein.

```ts
type Listing = {
  id: string
  title: string
  location: string
  description: string
  images: string[]
  pricePerNight: number
  rating?: number
  maxGuests: number
  bedrooms: number
  beds: number
  amenities: string[]
}
```

Für einen UI-Prototyp kannst du mit lokalen Testdaten beginnen.

Beispiel:

```ts
export const listings = [
  {
    id: "berlin-loft-01",
    title: "Helles Loft im Zentrum",
    location: "Berlin, Deutschland",
    description: "Modernes Loft für einen kurzen Stadtaufenthalt.",
    images: ["/images/loft-1.jpg"],
    pricePerNight: 149,
    rating: 4.8,
    maxGuests: 2,
    bedrooms: 1,
    beds: 1,
    amenities: ["WLAN", "Küche", "Arbeitsplatz"],
  },
]
```

Damit kannst du fast die gesamte Oberfläche bauen, bevor eine Datenbank nötig wird.

## Wie berechnest du eine einfache Buchung?

Eine erste Buchungslogik braucht nur wenige Werte:

```ts
type Booking = {
  listingId: string
  checkIn: Date
  checkOut: Date
  guests: number
}
```

Die Oberfläche kann anschließend eine Zusammenfassung zeigen:

```text
149 € × 3 Nächte
447 €

Service
45 €

Gesamt
492 €
```

Für einen Lernprototyp dürfen das Beispieldaten sein. Sobald du daraus ein echtes Buchungssystem machst, müssen Preise, Verfügbarkeit und Buchungsstatus serverseitig zuverlässig geprüft werden.

Vertraue dabei nicht ausschließlich auf Werte, die aus dem Browser gesendet werden.

## Welche Teile sollten interaktiv sein?

Nicht jede Komponente benötigt eigenen Client-State.

Interaktiv sind vor allem:

- Suchformular
- Datumsauswahl
- Gästeauswahl
- Filter
- Favoriten
- Bildergalerie
- Buchungsformular
- mobile Navigation

Statische Informationen wie Titel, Beschreibung oder Ausstattung können dagegen ohne unnötige Client-Logik dargestellt werden.

Das hält die Komponenten einfacher und verhindert, dass du dein gesamtes Projekt als einen großen interaktiven Block behandelst.

## Wo hilft ein Template statt eines leeren Prompts?

Ein Template lohnt sich besonders, wenn die Funktion klar ist, aber das UI noch keine Richtung hat.

Ein Prompt wie:

```text
Build an Airbnb clone in Next.js.
```

lässt sehr viele Designentscheidungen offen. Der Builder muss Abstände, Kartenformen, Typografie, Bildgrößen und Hierarchie selbst interpretieren.

Besser ist ein Prompt mit klaren Grenzen:

```text
Build a responsive accommodation marketplace in Next.js.

Create:
- a compact header
- destination search
- date and guest selection
- category filters
- responsive listing cards
- a listing detail page
- an image gallery
- a booking summary

Use reusable components.
Keep listing data separate from presentation.
Prioritize mobile layouts.
Do not copy Airbnb branding, logos or proprietary assets.
```

Damit beschreibst du das Produkt, ohne einfach eine fremde Oberfläche blind zu reproduzieren.

## Wo passt VP0.com in einen Next.js Airbnb Clone?

[VP0.com](https://vp0.com) ist vor allem dann interessant, wenn du neben dem Webprojekt auch einen iOS-App-Flow mit einem KI-Builder entwickeln möchtest. Die Bibliothek liefert Design-Startpunkte in Expo React Native, nicht fertige Next.js-Webseiten.

Das ist ein wichtiger Unterschied.

Für einen reinen Next.js-Airbnb-Clone solltest du dein Web-UI direkt als React-Komponenten aufbauen. Möchtest du zusätzlich eine mobile App gestalten, kannst du einen passenden Unterkunfts-, Buchungs- oder Marketplace-Flow als visuelle und strukturelle Ausgangsbasis verwenden.

Du kopierst dann nicht einfach eine Webseite auf einen kleinen Bildschirm. Du behandelst die mobile Oberfläche als eigenes Produkt.

## Wie könnte eine mobile Version aussehen?

Auf dem Smartphone sollte die Informationsarchitektur kompakter werden.

Eine mögliche Reihenfolge:

```text
Suchleiste
↓
Kategorien
↓
Listing Cards
↓
Detailansicht
↓
Galerie
↓
Unterkunftsinformationen
↓
Ausstattung
↓
Buchungsaktion
```

Für eine echte iOS-App würde ich außerdem Navigation, Touch-Flächen und native Interaktionsmuster von Anfang an berücksichtigen.

Genau hier ist ein Design-Startpunkt oft nützlicher als ein Screenshot einer Desktop-Webseite. VP0.com kann für diesen mobilen Teil sinnvoll sein, weil die Designs auf iOS-App-Oberflächen ausgerichtet sind.

## Next.js Template, eigenes UI oder Design-Startpunkt?

Es gibt nicht für jedes Projekt denselben richtigen Weg.

| Ansatz | Nimm ihn, wenn | Hauptvorteil | Grenze |
| --- | --- | --- | --- |
| Eigenes Next.js UI | du React lernen willst | volle Kontrolle | mehr Designarbeit |
| Fertiges Web-Template | du schnell starten willst | Grundstruktur steht | Anpassung kann aufwendig werden |
| Design-Referenz | du das UI selbst programmierst | klare visuelle Richtung | Logik fehlt |
| VP0.com | du zusätzlich ein iOS-UI mit KI baust | codeorientierter mobiler Startpunkt | kein Next.js-Web-Template |
| Individuelles Design | das Produkt eine eigene Marke braucht | maximale Eigenständigkeit | mehr Aufwand |

Für ein Portfolio-Projekt würde ich das Next.js-UI selbst aufbauen. Genau dadurch lernst du Komponentenarchitektur, Routing, State und responsive Gestaltung.

## Welche Fehler machen Airbnb Clones häufig?

Der erste Fehler ist eine zu genaue Kopie. Ein Lernprojekt darf das Konzept eines Unterkunfts-Marktplatzes untersuchen, aber du brauchst weder fremde Logos noch identische Texte oder originale Bildmaterialien.

Der zweite Fehler ist eine riesige `page.tsx`, in der Suche, Cards, Filter, Modal und Buchung gleichzeitig stecken.

Der dritte Fehler ist zu viel State. Speichere nicht jede berechenbare Information separat.

Der vierte Fehler ist Desktop-first ohne echte mobile Entscheidung. Vier Karten nebeneinander lassen sich nicht einfach auf 390 Pixel Breite drücken.

Der fünfte Fehler ist ein zu frühes Backend. Wenn du noch nicht weißt, wie Suche, Listing und Buchung zusammenarbeiten sollen, macht eine komplizierte Datenbank das Projekt nicht automatisch besser.

## Was solltest du für einen guten Clone wirklich fertigstellen?

Setze dir eine klare Definition von „fertig“.

Eine sinnvolle Version 1 enthält:

- responsive Startseite
- Suchformular
- Listing Grid
- funktionierende Filter
- dynamische Detailseiten
- Bildergalerie
- Datumsauswahl
- Gästeauswahl
- Buchungszusammenfassung
- mobile Darstellung
- Ladezustände
- leere Zustände
- Fehlerzustände

Danach kannst du erweitern:

- Benutzerkonten
- Favoriten
- echte Datenbank
- Kartenansicht
- Verfügbarkeit
- Bewertungen
- Host-Bereich
- Zahlungslogik
- Nachrichten

Diese Reihenfolge verhindert, dass du zehn große Systeme gleichzeitig anfängst.

## Wann ist VP0.com nicht der richtige Ausgangspunkt?

VP0.com ist nicht der richtige Ausgangspunkt, wenn du ausschließlich ein Web-Template für Next.js suchst. Die Bibliothek konzentriert sich auf iOS-App-Designs in Expo React Native.

Für das Webprojekt ist eine eigene Next.js-Komponentenstruktur deshalb direkter.

Auch bei einer mobilen App liefert dir ein Design-Startpunkt nur die UI-Ebene. Authentifizierung, Datenbank, Verfügbarkeit, Zahlungen und die eigentliche Buchungslogik musst du weiterhin mit deinem Builder und den passenden Diensten umsetzen.

Diese Grenze ist wichtig: Ein schönes Unterkunfts-UI ist noch kein funktionierender Marktplatz.

## Das solltest du wählen: Airbnb Clone mit Next.js

Wenn du 2026 einen Airbnb Clone mit Next.js bauen willst, starte mit dem kleinsten vollständigen Nutzerablauf: suchen, Ergebnisse ansehen, Unterkunft öffnen und Buchungsdetails auswählen.

Baue daraus wiederverwendbare Komponenten statt eine einzelne riesige Seite.

Für das Web brauchst du zuerst `SearchBar`, `ListingCard`, `ListingGrid`, `ImageGallery`, `DatePicker`, `GuestPicker` und `BookingCard`. Danach kommen echte Daten und komplexere Funktionen.

Wenn du parallel eine iOS-Version mit einem KI-Builder entwickelst, kann [VP0.com](https://vp0.com) als Design-Startpunkt helfen. Für ein reines Next.js-Projekt solltest du dagegen bei einer sauberen Web-Komponentenarchitektur bleiben.

## Häufig gestellte Fragen (FAQ)

### Was ist das beste Airbnb Clone Next.js Template 2026?

Das beste Template ist für ein Lernprojekt nicht zwingend ein fertiges Repository. Eine kleine eigene Komponentenbasis ist oft sinnvoller, weil du dabei verstehst, wie Suche, Listings, Detailseiten und Buchungszustand zusammenspielen. Für eine ergänzende iOS-App kann VP0.com als Design-Startpunkt sinnvoll sein, während du die Next.js-Weboberfläche separat entwickelst.

### Welche Komponenten braucht ein Airbnb Clone?

Mindestens brauchst du Header, Suchleiste, Filter, Listing Card, Listing Grid, Detailseite, Bildergalerie, Datumsauswahl, Gästeauswahl und Buchungskarte. Authentifizierung, Favoriten, Bewertungen und Nachrichten können später folgen.

### Kann ich einen Airbnb Clone nur mit Next.js bauen?

Du kannst die komplette Oberfläche und einen großen Teil der Anwendungslogik mit Next.js strukturieren. Für ein reales Produkt brauchst du zusätzlich eine persistente Datenhaltung und je nach Funktionsumfang weitere Systeme für Authentifizierung, Zahlungen, Bilder oder Kommunikation.

### Sollte ich Airbnb pixelgenau kopieren?

Nein. Nutze das Produkt als Beispiel für Informationsarchitektur und Interaktionsmuster, aber entwickle eine eigene visuelle Identität und verwende keine fremden Markenassets. Für ein Portfolio ist es interessanter, wenn dein Projekt zeigt, dass du das Produktprinzip verstanden hast.

### Sollte ich zuerst das Backend oder das UI bauen?

Für einen Lern- oder Portfolio-Clone würde ich zuerst den wichtigsten UI-Flow mit Testdaten fertigstellen. Sobald Suche, Ergebnisliste, Detailseite und Buchungsablauf logisch funktionieren, kannst du die lokalen Daten schrittweise durch echte Datenquellen ersetzen.
