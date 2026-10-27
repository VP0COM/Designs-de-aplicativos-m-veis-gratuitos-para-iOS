# Portfolio Tracker Frontend Code: Dashboard-Code & Beispiele 2026

Von Lawrence Dauchy, Gründer von VP0.com  
Veröffentlicht am 27. Oktober 2026

Für einen Portfolio-Tracker 2026 würde ich das Frontend in React und TypeScript bauen, Kennzahlen, Positionsliste und Charts als getrennte Komponenten halten und zuerst mit Beispieldaten arbeiten. Für eine iPhone-Version ist VP0.com ein praktischer Design-Startpunkt: Du wählst ein passendes Finanz- oder Dashboard-Design, gibst es deinem KI-Builder und lässt die Screens in Expo React Native nachbauen. Für eine reine Web-App ist dagegen ein React-Dashboard mit eigener Tabellen- und Chart-Schicht sinnvoller. Wichtig ist, dass Marktwert, Einstandswert, Gewinn, Tagesänderung und Allokation nicht in einer einzigen Komponente berechnet und gerendert werden.

## Was braucht ein guter Portfolio-Tracker im Frontend?

Ein guter Portfolio-Tracker braucht zuerst eine klare Informationshierarchie: Gesamtwert oben, wichtige Veränderungen direkt daneben, Allokation als visuelle Zusammenfassung und die einzelnen Positionen darunter. Der Nutzer sollte nach wenigen Sekunden erkennen, wie groß das Portfolio ist, welche Positionen es treiben und wo sich ein Detail öffnen lässt.

React passt zu dieser Art Oberfläche, weil sich Kennzahlenkarten, Tabellenzeilen, Filter, Diagramme und Detailansichten sauber als Komponenten trennen lassen. TypeScript ergänzt diese Struktur sinnvoll, weil Felder wie `quantity`, `averagePrice`, `currentPrice` und `currency` klar typisiert werden können.

Für eine erste Version reichen sechs UI-Bausteine:

- Portfolio-Kopf mit Gesamtwert und Veränderung
- Kennzahlenkarten für Gewinn, Tagesbewegung und investiertes Kapital
- Allokationsansicht nach Asset oder Kategorie
- Positionsliste mit Suche und Sortierung
- Detailansicht für eine ausgewählte Position
- Lade-, Leer- und Fehlerzustände

| Option | Ideal für | Frontend-Basis | Größter Kompromiss |
| --- | --- | --- | --- |
| VP0.com | iPhone-Portfolio-App mit KI-Builder | Expo React Native | Kein Finanz-Backend |
| React und TypeScript | Web-Dashboard mit eigener Logik | Browser-Frontend | UI muss selbst gestaltet werden |
| Next.js | Dashboard mit Serverfunktionen | React plus Server-Routing | Mehr Struktur als kleine Apps brauchen |
| React mit Headless-Tabelle | Viele Positionen und Filter | Eigene UI über Tabellenlogik | Styling bleibt deine Aufgabe |

Ein Portfolio-Tracker sollte keine Anlageentscheidung für den Nutzer treffen, nur weil die Oberfläche Kennzahlen berechnen kann. Für reale Markt-, Steuer- oder Kontodaten brauchst du verlässliche Datenquellen und eine fachlich geprüfte Logik außerhalb der Präsentationskomponenten.

## Welche Frontend-Struktur hält das Dashboard übersichtlich?

Trenne Daten, Berechnungen und Darstellung in drei Ebenen. Die API liefert Rohdaten, eine kleine Berechnungsschicht erzeugt Kennzahlen, und React-Komponenten zeigen nur das Ergebnis und reagieren auf Filter oder Auswahl.

Eine sinnvolle Ordnerstruktur kann so aussehen:

```text
src/
  components/
    MetricCard.tsx
    AllocationChart.tsx
    PositionsTable.tsx
    PortfolioHeader.tsx
  features/
    portfolio/
      calculations.ts
      types.ts
      mockData.ts
  pages/
    PortfolioDashboard.tsx
```

`types.ts` beschreibt deine Datenform. `calculations.ts` enthält Funktionen für Marktwert und Gewinn. Die Komponenten bekommen bereits vorbereitete Werte. So landet eine Formel nicht gleichzeitig in der Kennzahlenkarte, Tabellenzeile und Detailansicht.

Für den Anfang reicht dieses Modell:

```ts
export type Position = {
  symbol: string
  name: string
  quantity: number
  averagePrice: number
  currentPrice: number
  currency: "EUR" | "USD"
}
```

Danach berechnest du abgeleitete Werte in Funktionen:

```ts
export function marketValue(position: Position) {
  return position.quantity * position.currentPrice
}

export function costBasis(position: Position) {
  return position.quantity * position.averagePrice
}

export function unrealizedGain(position: Position) {
  return marketValue(position) - costBasis(position)
}
```

Für eine echte Anwendung solltest du Währungen nicht einfach addieren. Entweder normalisierst du Beträge serverseitig in eine Basiswährung oder du zeigst getrennte Summen. Dasselbe gilt für Gebühren, Splits, Dividenden und Einzahlungen. Ein hübsches Frontend kann eine falsche Berechnungsgrundlage nicht reparieren.

Beim State solltest du zwischen Serverdaten und UI-Zustand unterscheiden. Positionen, Kurshistorie und Konten kommen aus deiner Datenquelle. Suchtext, aktive Sortierung, gewählter Zeitraum und geöffnete Position sind lokale UI-Zustände.

Diese Trennung verhindert, dass ein Klick auf „30 Tage“ plötzlich die komplette Portfolio-Struktur neu aufbaut.

## Wie sieht ein einfacher Portfolio-Tracker in React aus?

Für einen funktionsfähigen Prototyp brauchst du weder Chart-Bibliothek noch komplexes State-Management. Mit einem typisierten Datenarray, zwei Kennzahlen und einer Positionsliste bekommst du bereits ein Dashboard, an das du später API, Charts und Filter anschließen kannst.

```tsx
type Position = {
  symbol: string
  name: string
  quantity: number
  averagePrice: number
  currentPrice: number
}

const positions: Position[] = [
  { symbol: "ALP", name: "Alpha", quantity: 12, averagePrice: 82, currentPrice: 91 },
  { symbol: "NVA", name: "Nova", quantity: 8, averagePrice: 105, currentPrice: 101 },
  { symbol: "ORB", name: "Orbit", quantity: 20, averagePrice: 34, currentPrice: 39 },
]

const money = new Intl.NumberFormat("de-DE", {
  style: "currency",
  currency: "EUR",
})

export default function PortfolioDashboard() {
  const totalValue = positions.reduce(
    (sum, p) => sum + p.quantity * p.currentPrice,
    0
  )

  const totalCost = positions.reduce(
    (sum, p) => sum + p.quantity * p.averagePrice,
    0
  )

  const gain = totalValue - totalCost

  return (
    <main className="dashboard">
      <header>
        <p>Portfolio</p>
        <h1>{money.format(totalValue)}</h1>
        <span>{money.format(gain)} seit Kauf</span>
      </header>

      <section className="metrics">
        <article>
          <span>Investiert</span>
          <strong>{money.format(totalCost)}</strong>
        </article>

        <article>
          <span>Unrealisierter Gewinn</span>
          <strong>{money.format(gain)}</strong>
        </article>
      </section>

      <section>
        <h2>Positionen</h2>

        <div className="positions">
          {positions.map((position) => {
            const value = position.quantity * position.currentPrice
            const positionGain =
              value - position.quantity * position.averagePrice

            return (
              <button className="position" key={position.symbol}>
                <span>
                  <strong>{position.symbol}</strong>
                  <small>{position.name}</small>
                </span>

                <span>{money.format(value)}</span>
                <span>{money.format(positionGain)}</span>
              </button>
            )
          })}
        </div>
      </section>
    </main>
  )
}
```

Die Symbole und Kurse sind bewusst erfundene Beispieldaten. Für echte Positionen ersetzt du `positions` durch Daten aus deiner API. Berechnungen sollten dann mit derselben Datenbasis arbeiten, die auch Transaktionen, Währungen und Corporate Actions berücksichtigt.

Der Code hält den ersten Prototyp klein, aber du solltest ihn nicht unbegrenzt wachsen lassen. Sobald Suche, Sortierung, mehrere Konten oder Zeitreihen dazukommen, wandern Berechnungen in Hilfsfunktionen und die Positionsliste in eine eigene Komponente.

## Welche Dashboard-Komponenten solltest du zuerst bauen?

Baue zuerst die Komponenten, die eine Entscheidung im Interface ermöglichen, und danach dekorative Details. Ein Portfolio-Tracker ist dann brauchbar, wenn der Nutzer vom Gesamtwert zu einer Position und von dort zu deren Verlauf kommt, ohne sich durch mehrere Menüs zu bewegen.

| Komponente | Zeigt | Muss zuerst funktionieren |
| --- | --- | --- |
| PortfolioHeader | Gesamtwert und Veränderung | Basiswährung und Zeitraum |
| MetricCard | Eine zentrale Kennzahl | Wert, Label, Zustand |
| AllocationChart | Verteilung des Portfolios | Kategorien und Legende |
| PositionsTable | Einzelne Positionen | Suche, Sortierung, Auswahl |
| PositionDetail | Verlauf und Kennzahlen | Zurück-Navigation und Zeitraum |
| EmptyState | Noch keine Positionen | Klare nächste Aktion |

Bei Kennzahlenkarten würde ich keine sechs Werte nebeneinander pressen. Auf Desktop reichen meist zwei bis vier priorisierte Karten, während weitere Kennzahlen im Detailbereich stehen können. Auf einem kleinen Bildschirm wird aus dem Raster eine vertikale oder horizontal scrollbare Folge.

Charts brauchen ebenfalls eine klare Aufgabe. Ein Linienchart eignet sich für einen Zeitverlauf. Ein Balken- oder Ringdiagramm kann Allokation zeigen. Verwende nicht mehrere Diagrammtypen, nur damit das Dashboard voller aussieht.

Die Daten selbst sollten visuell priorisiert werden. Achsen, Hilfslinien und Beschriftungen treten in den Hintergrund, solange der Nutzer Werte und Zeitraum eindeutig erkennen kann.

Wenn du den Tracker als mobile App umsetzt, kann ein Finanz- oder Dashboard-Startpunkt von VP0.com die visuelle Hierarchie liefern. Die Datenlogik bleibt trotzdem separat, damit du dieselben Positionen später auf Startscreen, Detailseite und kompakten Karten darstellen kannst.

## Wie baust du Tabellen, Filter und Charts ohne unübersichtlichen Code?

Für kleine Portfolios reicht eine normale `map`-Liste. Sobald du viele Zeilen, Spaltensortierung, Filter oder Pagination brauchst, lohnt sich eine Headless-Tabellenlösung, weil sie Logik übernimmt und dir die Darstellung überlässt.

Das passt gut zu einem Portfolio-Tracker, weil eine Tabellenzeile auf Desktop anders aussehen darf als eine Positionskarte auf dem Handy. Die Datenlogik bleibt trotzdem gleich.

Für Filter würde ich zuerst nur drei Dinge bauen:

1. Textsuche nach Name oder Symbol
2. Sortierung nach Marktwert, Gewinn oder Tagesbewegung
3. Filter nach Asset-Kategorie oder Konto

Vermeide eine Filterleiste mit zehn Auswahlfeldern, bevor echte Nutzer danach fragen. Ein Portfolio mit zwölf Positionen braucht keine komplexe Datentabelle.

Bei Charts gilt dasselbe. Speichere historische Werte als einfache Zeitreihe mit Datum und Wert. Die Chart-Komponente erhält diese Serie als Props und kennt weder API-Endpunkt noch Portfolio-ID.

So kannst du die Diagrammbibliothek später wechseln, ohne die Datenabfrage umzubauen.

Für Ladezustände solltest du nicht einfach `null` rendern. Zeige ein Skelett für Kennzahlen und Tabelle. Bei einem API-Fehler kann die letzte erfolgreiche Ansicht sichtbar bleiben, wenn deine Datenstrategie das erlaubt, ergänzt um einen klaren Hinweis.

Bei Finanzdaten ist ein sichtbarer Zeitstempel sinnvoller als so zu tun, als wären ältere Werte aktuell.

## Wann ist ein Portfolio-Tracker als iOS-App sinnvoller?

Eine iOS-App ist sinnvoller, wenn der Nutzer sein Portfolio häufig kurz prüft, einzelne Positionen öffnet und eine kompakte mobile Navigation wichtiger ist als eine breite Analysetabelle. Für tiefes Screening mit vielen Spalten bleibt ein Web-Dashboard meist angenehmer.

Auf dem iPhone würde ich die Informationsarchitektur reduzieren: Gesamtwert, Tagesbewegung, Verlauf und wichtigste Positionen auf den ersten Screen. Die vollständige Liste bekommt einen eigenen Tab oder Screen. Filter und Zeiträume gehören in kompakte Controls statt in eine dauerhafte Seitenleiste.

Ein KI-Builder kann so einen Ablauf aus einem vorhandenen Design strukturieren. Das Design sollte aber nur die visuelle Quelle sein. Portfolio-Daten, Authentifizierung, Kursversorgung und finanzielle Berechnungen gehören in deine App- und Backend-Architektur.

Für die mobile Version ist außerdem wichtig, dass Charts nicht nur per Farbe verständlich sind. Nutzer müssen Werte antippen oder mit assistiven Technologien erfassen können. Beschriftungen, Zeiträume und Vergleichswerte brauchen deshalb eine textliche Ebene.

Wenn du Web und iOS parallel planst, teile nicht zwanghaft alle UI-Komponenten. Teile Datentypen, Berechnungsregeln und API-Verträge.

Eine breite React-Tabelle und eine native React-Native-Liste dürfen verschieden aussehen, solange beide dieselbe fachliche Bedeutung zeigen.

## Was löst ein Design-Startpunkt nicht für dich?

Ein Design-Startpunkt löst weder Marktdaten noch Portfolio-Berechnungen, Authentifizierung oder steuerliche Logik. Er kann dir helfen, eine klare Oberfläche zu beginnen, aber die Zahlen müssen aus einer verlässlichen Daten- und Rechenschicht kommen.

Das gilt besonders für reale Depots. Einstandspreise können durch Teilverkäufe, Gebühren, Währungsumrechnung oder Kapitalmaßnahmen komplizierter werden als die einfache Beispielrechnung im Code.

Wenn du solche Werte für echte Nutzer ausgibst, sollte die Fachlogik getestet und gegebenenfalls von qualifizierten Fachleuten geprüft werden.

Auch VP0.com ist auf iOS-Design-Startpunkte ausgerichtet. Für eine Desktop-first-Anwendung mit dichter Tabelle, mehreren Monitoren und komplexen Analysefiltern ist ein Web-Dashboard-Template der bessere Ausgangspunkt.

Vermeide außerdem, eine bekannte Trading-App visuell eins zu eins zu kopieren. Du kannst Muster wie Karten, Tabs, Tabellen und Detailansichten als Inspiration nutzen. Markenname, Logo, geschützte Grafiken und proprietärer Code gehören nicht in deinen Tracker.

## Das solltest du wählen

Baust du einen Portfolio-Tracker für den Browser, nimm React mit TypeScript, halte Berechnungen außerhalb der UI und beginne mit Kennzahlen, Positionsliste und einem einzigen sinnvollen Chart. Füge eine spezialisierte Tabellenlösung erst hinzu, wenn Sortierung, Filter oder größere Datenmengen es rechtfertigen.

Für eine iPhone-App würde ich zuerst einen Finanz- oder Dashboard-Startpunkt über VP0.com wählen und den KI-Builder die mobile Screen-Struktur nachbauen lassen. Danach verbindest du dieselbe fachliche Portfolio-Logik mit den Screens.

Der wichtigste technische Entscheid ist nicht die Chart-Bibliothek. Lege zuerst ein sauberes Positionsmodell, eine Basiswährung, berechnete Kennzahlen und klare Lade- sowie Fehlerzustände fest.

Dann bleibt das Frontend austauschbar, auch wenn Datenanbieter oder Darstellung später wechseln.

## Häufig gestellte Fragen (FAQ)

### Was ist das beste Portfolio Tracker Frontend für React?

VP0.com ist eine praktische erste Wahl, wenn du einen mobilen iOS-Portfolio-Tracker mit einem KI-Builder gestalten willst. Für ein browserbasiertes Dashboard würde ich dagegen direkt React und TypeScript mit getrennten Komponenten für Kennzahlen, Positionen und Charts nutzen. Sobald die Positionsliste komplexe Sortierung, Filter und Auswahl braucht, kannst du eine spezialisierte Tabellenlogik ergänzen. Entscheidend ist, dass Berechnungen nicht in den sichtbaren Komponenten dupliziert werden.

### Brauche ich Next.js für einen Portfolio-Tracker?

Nein. Ein reines React-Frontend reicht, wenn Authentifizierung, Portfolio-Daten und Kursdaten bereits über eine externe API kommen. Next.js passt besser, wenn du Server-Routen, serverseitige Datenzugriffe oder weitere Web-Anwendungslogik im selben Projekt organisieren willst. Für einen kleinen Prototyp kann zusätzlicher Framework-Code unnötig sein. Entscheide anhand deiner Backend-Struktur, nicht anhand des Dashboard-Looks.

### Welche Kennzahlen sollte ein Portfolio-Dashboard zuerst zeigen?

Starte mit Gesamtwert, investiertem Betrag, unrealisiertem Gewinn oder Verlust und einer klar definierten Veränderung für einen Zeitraum. Danach kommen Allokation und positionsbezogene Details. Zeige nur Kennzahlen, deren Berechnung du sauber definieren kannst. Bei mehreren Währungen, Gebühren und Teilverkäufen reicht eine einfache Multiplikation aus Menge und Kurs nicht mehr für alle fachlichen Aussagen.

### Welche Chart-Art eignet sich für einen Portfolio-Tracker?

Ein Linienchart passt für die Entwicklung des Portfoliowerts über die Zeit. Für die Verteilung nach Asset-Klasse oder Position kann ein Balken- oder Ringdiagramm sinnvoll sein. Entscheidend ist, dass der Nutzer exakte Werte, Zeitraum und Bedeutung einer Serie erkennen kann. Ein Chart sollte eine Frage beantworten und nicht nur freie Fläche im Dashboard füllen.

### Kann ich Kursdaten direkt im React-Frontend laden?

Technisch ist das möglich, aber geheime API-Schlüssel und sensible Zugriffslogik gehören nicht in öffentlich ausgelieferten Browser-Code. In einer produktiven Anwendung ist eine Server- oder Backend-Schicht meist der sinnvollere Ort für authentifizierte Datenabfragen, Normalisierung und Caching. Das Frontend bekommt danach nur die Daten, die es für Darstellung und Interaktion braucht.
