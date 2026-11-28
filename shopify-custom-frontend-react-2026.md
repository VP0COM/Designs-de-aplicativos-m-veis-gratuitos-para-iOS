# Shopify Custom Frontend React: Beispiele, Architektur & Code 2026

Von Lawrence Dauchy, Gründer von VP0.com

Veröffentlicht am 28. November 2026

Ein Shopify Custom Frontend mit React ermöglicht es Entwicklern, individuelle Onlineshops zu erstellen, ohne an die Gestaltungsmöglichkeiten klassischer Shopify Themes gebunden zu sein. Shopify übernimmt dabei die Verwaltung von Produkten, Bestellungen und Checkout, während React die Benutzeroberfläche steuert.

Für moderne E-Commerce-Projekte eignen sich insbesondere Shopify Hydrogen, Next.js und die Shopify Storefront API. Welche Architektur sinnvoll ist, hängt von den technischen Anforderungen, dem Budget und der gewünschten Flexibilität ab.

## Was ist ein Shopify Custom Frontend mit React?

Ein Shopify Custom Frontend ist eine individuelle Shop-Oberfläche, die unabhängig vom klassischen Shopify Theme entwickelt wird. Diese Architektur wird als Headless Commerce bezeichnet.

Bei einem traditionellen Shopify-Shop werden Seiten mit Liquid, CSS und JavaScript innerhalb des Theme-Systems erstellt. Bei einem Headless-Shop übernimmt React die Darstellung und Shopify stellt die Commerce-Daten über Schnittstellen bereit.

Die Aufgaben verteilen sich entsprechend:

- React: Benutzeroberfläche und Interaktionen.
- Shopify: Produkte, Lagerbestände und Bestellungen.
- Storefront API: Verbindung zwischen Frontend und Shopsystem.
- Shopify Checkout: Bestellabschluss und Zahlungsabwicklung.
- Hosting: Bereitstellung des individuellen Frontends.

Du kannst dadurch Produktseiten, Navigation, Filter, Warenkörbe und interaktive Einkaufserlebnisse unabhängig vom Theme gestalten.

Für die visuelle Planung mobiler Einkaufserlebnisse bietet [VP0.com](https://vp0.com) kostenlose Designreferenzen auf Basis von Expo React Native. Diese kannst du als Ausgangspunkt für eigene React-Webkomponenten verwenden.

## Welche React-Architektur eignet sich für Shopify 2026?

Für einen vollständigen Headless-Shop würde ich mit Hydrogen oder Next.js beginnen. Eine einfache React-Anwendung eignet sich eher für Prototypen und einzelne Shopping-Funktionen.

| Architektur | Geeignet für | Aufwand |
| --- | --- | --- |
| Hydrogen | Individuelle Shopify-Shops | Mittel |
| Next.js mit Hydrogen | Content und Commerce | Mittel bis hoch |
| React mit Storefront API | Individuelle Anwendungen | Hoch |
| Shopify Liquid | Klassische Onlineshops | Niedrig bis mittel |
| Expo React Native | Mobile Shopping-Apps | Mittel bis hoch |

### Shopify Hydrogen

Hydrogen ist das offizielle Headless-Toolkit von Shopify.

Es unterstützt die Integration von Produktdaten, Warenkörben, Kundenkonten und weiteren Commerce-Funktionen. Seit der Version 2026-10 lässt sich das Toolkit auch stärker unabhängig von einem bestimmten JavaScript-Framework einsetzen.

Für bestehende Hydrogen-Projekte solltest du deshalb darauf achten, welche Version verwendet wird. Ältere Tutorials können andere Schnittstellen und Projektstrukturen voraussetzen.

### Next.js und Shopify

Next.js eignet sich besonders für Shops, die redaktionelle Inhalte und E-Commerce miteinander verbinden.

Typische Einsatzbereiche sind:

- Umfangreiche Produktkataloge.
- Internationale Markenwebsites.
- Individuelle Landingpages.
- Content-Commerce-Plattformen.
- Shops mit externem CMS.

Mit serverseitig gerenderten Produktseiten kannst du außerdem dafür sorgen, dass wichtige Produktinformationen bereits im ausgelieferten HTML enthalten sind.

### React Native für mobile Shopping-Apps

Wenn du neben deinem Webshop eine native Shopping-App entwickeln möchtest, ist Expo React Native eine interessante Ergänzung.

Shopify bleibt das zentrale Commerce-System, während du eine separate Oberfläche für iOS und Android erstellst.

Dabei solltest du allerdings berücksichtigen, dass React-Webkomponenten und React-Native-Komponenten nicht ohne Anpassungen austauschbar sind.

## Wie sieht die Architektur eines Shopify React Frontends aus?

Eine sinnvolle Headless-Architektur trennt die Darstellung, die Geschäftslogik und die Datenverwaltung voneinander.

Eine vereinfachte Struktur sieht so aus:

```text
Kunde
  |
React / Next.js Frontend
  |
Serverseitige API-Schicht
  |
Shopify Storefront API
  |
Shopify Commerce Backend
  |
Shopify Checkout
```

Auf diese Weise bleibt die Benutzeroberfläche unabhängig vom Backend. Dein Produktkatalog wird weiterhin in Shopify verwaltet.

Die [offizielle Shopify-Dokumentation](https://shopify.dev/docs/storefronts/headless/overview) beschreibt, welche Schnittstellen für Produkte, Warenkörbe und Kundenkonten zur Verfügung stehen und wie sich alternative Verkaufskanäle anbinden lassen.

### Empfohlene Projektstruktur

Für einen individuellen Next.js-Shop kannst du beispielsweise folgende Ordnerstruktur verwenden:

```text
shopify-frontend/
  app/
    page.tsx
    products/
      [handle]/
        page.tsx
    collections/
      [handle]/
        page.tsx
    cart/
      page.tsx
    api/
      cart/
        route.ts
  components/
    Header.tsx
    ProductCard.tsx
    ProductGrid.tsx
    ProductGallery.tsx
    CartDrawer.tsx
    Footer.tsx
  lib/
    shopify.ts
    queries.ts
    mutations.ts
  types/
    shopify.ts
  styles/
    globals.css
  .env.local
```

Die React-Komponenten enthalten hauptsächlich die Darstellung. API-Abfragen und Commerce-Logik bleiben in separaten Dateien.

Das erleichtert es, später das Design zu ändern, ohne gleichzeitig die gesamte Shopify-Anbindung neu entwickeln zu müssen.

## Wie baust du ein Shopify Custom Frontend mit React?

Beginne mit einer funktionierenden Produktübersicht und einem vollständigen Kaufprozess. Animationen, Personalisierung und zusätzliche Funktionen kannst du danach ergänzen.

### 1. Next.js-Projekt erstellen

Erstelle zunächst ein neues Projekt:

```bash
npx create-next-app@latest shopify-frontend
```

Wechsle anschließend in das Projektverzeichnis:

```bash
cd shopify-frontend
npm run dev
```

Für dieses Beispiel verwendest du TypeScript und den Next.js App Router.

### 2. Shopify Storefront API konfigurieren

Richte in Shopify einen passenden Headless-Vertriebskanal ein und erstelle die Zugangsdaten für deine Storefront.

Speichere die Konfiguration in deiner `.env.local`:

```env
SHOPIFY_STORE_DOMAIN=your-store.myshopify.com
SHOPIFY_STOREFRONT_PRIVATE_TOKEN=your-private-token
SHOPIFY_API_VERSION=2026-10
```

Der private Token darf nicht in öffentlich ausgeliefertem JavaScript erscheinen. Verwende ihn ausschließlich in serverseitigem Code.

### 3. Shopify API Client erstellen

Erstelle die Datei `lib/shopify.ts`:

```typescript
import "server-only";

export async function shopifyFetch<T>(
  query: string,
  variables: Record<string, unknown> = {}
): Promise<T> {
  const domain = process.env.SHOPIFY_STORE_DOMAIN;
  const token =
    process.env.SHOPIFY_STOREFRONT_PRIVATE_TOKEN;
  const version = process.env.SHOPIFY_API_VERSION;

  const response = await fetch(
    `https://${domain}/api/${version}/graphql.json`,
    {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        "Shopify-Storefront-Private-Token": token!,
      },
      body: JSON.stringify({
        query,
        variables,
      }),
      cache: "no-store",
    }
  );

  if (!response.ok) {
    throw new Error("Shopify request failed");
  }

  const result = await response.json();

  if (result.errors?.length) {
    throw new Error("GraphQL request failed");
  }

  return result.data;
}
```

Diese Funktion dient als vereinfachte serverseitige Verbindung zwischen deinem Next.js-Projekt und Shopify.

Für einen produktiven Shop solltest du zusätzlich Zeitlimits, eine differenzierte Fehlerbehandlung und eine geeignete Cache-Strategie ergänzen.

### 4. Produkte über GraphQL abrufen

Mit einer GraphQL-Abfrage kannst du festlegen, welche Produktinformationen dein Frontend benötigt.

```graphql
query GetProducts {
  products(first: 12) {
    nodes {
      id
      title
      handle
      featuredImage {
        url
        altText
      }
      priceRange {
        minVariantPrice {
          amount
          currencyCode
        }
      }
    }
  }
}
```

Die Abfrage liefert die grundlegenden Informationen für ein Produktgrid.

Für eine vollständige Produktdetailseite benötigst du zusätzlich Varianten, Beschreibungen, Verfügbarkeiten und weitere Produktbilder.

### 5. React Product Card erstellen

Eine wiederverwendbare Produktkarte erleichtert die einheitliche Darstellung im gesamten Shop.

```tsx
type Product = {
  handle: string;
  title: string;
  featuredImage: {
    url: string;
    altText: string | null;
  } | null;
  priceRange: {
    minVariantPrice: {
      amount: string;
      currencyCode: string;
    };
  };
};

export default function ProductCard({
  product,
}: {
  product: Product;
}) {
  const price =
    product.priceRange.minVariantPrice;

  const formattedPrice =
    new Intl.NumberFormat("de-DE", {
      style: "currency",
      currency: price.currencyCode,
    }).format(Number(price.amount));

  return (
    <article className="group">
      <a href={`/products/${product.handle}`}>
        {product.featuredImage && (
          <img
            src={product.featuredImage.url}
            alt={
              product.featuredImage.altText
              || product.title
            }
            className="aspect-square w-full
              rounded-2xl object-cover"
          />
        )}

        <h2 className="mt-4 font-medium">
          {product.title}
        </h2>

        <p className="mt-1 text-neutral-600">
          Ab {formattedPrice}
        </p>
      </a>
    </article>
  );
}
```

Für größere Shops solltest du eine optimierte Bildkomponente mit responsiven Bildgrößen verwenden.

Die Produktkarte lässt sich anschließend auf Kategorieseiten, der Startseite und in Produktempfehlungen einsetzen.

### 6. Warenkorb und Checkout anbinden

Der Warenkorb sollte auf der Shopify Cart API basieren. Vermeide es, Preise ausschließlich lokal zu berechnen oder Produktbestände im Browser als verbindlich zu behandeln.

Eine vereinfachte GraphQL-Mutation zum Erstellen eines Warenkorbs sieht so aus:

```graphql
mutation CreateCart(
  $variantId: ID!
) {
  cartCreate(
    input: {
      lines: [
        {
          merchandiseId: $variantId
          quantity: 1
        }
      ]
    }
  ) {
    cart {
      id
      checkoutUrl
      totalQuantity
    }
    userErrors {
      field
      message
    }
  }
}
```

Die Mutation erwartet die ID einer konkreten Produktvariante, nicht die allgemeine Produkt-ID.

Speichere die vollständige Warenkorb-ID geschützt auf dem Server oder in einem geeigneten serverseitig verwalteten Session-System. Gib vertrauliche Bestandteile der ID nicht im Browser aus.

Für den Bestellabschluss leitest du den Kunden an die von Shopify bereitgestellte Checkout-URL weiter.

Die gezeigten Codeausschnitte sind bewusst auf einzelne Funktionen reduziert. Sie müssen vor dem produktiven Einsatz mit deinem Shopify-Shop und der verwendeten API-Version getestet werden.

## Welche Shopify Frontend Beispiele eignen sich als Designvorlage?

Gute Shopify-Frontends kombinieren eine klare Produktauswahl mit kurzen Entscheidungswegen. Das Design sollte sich an der Art des Produkts orientieren, nicht ausschließlich an aktuellen visuellen Trends.

### Minimalistischer Fashion-Shop

Ein moderner Fashion-Shop benötigt große Produktbilder, eine übersichtliche Navigation und gut erkennbare Varianten.

Eine geeignete Oberfläche besteht aus:

- Großformatiger Produktfotografie.
- Zurückhaltender Typografie.
- Farbauswahl über visuelle Farbmuster.
- Größenwahl mit eindeutigen Verfügbarkeiten.
- Mobilfreundlichem Warenkorb.
- Gut sichtbaren Lieferinformationen.

Bei Modeprodukten solltest du besonders darauf achten, dass nicht verfügbare Größen eindeutig erkennbar bleiben.

### Premium-Elektronik-Shop

Bei technischen Produkten stehen Spezifikationen und Vergleichsmöglichkeiten stärker im Vordergrund.

Ergänze die Produktseite durch eine strukturierte Darstellung technischer Daten, interaktive Produktgalerien, Zubehörangebote und verständliche Informationen zu Garantie und Kompatibilität.

Ein Produktvergleich kann sinnvoller sein als eine aufwendige Animation.

### Beauty- und Kosmetik-Shop

Für Kosmetikprodukte eignet sich ein Frontend, das Kunden nach Anwendungsbereich, Inhaltsstoffen oder Hautbedürfnissen durch das Sortiment führt.

Dazu gehören Produktfilter, Anwendungshinweise und verständliche Produktinformationen.

Achte darauf, dass Empfehlungen keine unbelegten medizinischen Versprechen enthalten.

### Mobile Shopping-App

Für eine Shopping-App kannst du bei VP0.com nach mobilen Designmustern suchen und passende Layouts auf deine eigene Markenidentität übertragen.

Besonders relevant sind Produktkarten, Suchoberflächen, Filter, Favoriten, Warenkörbe und Kundenprofile.

Für einen React-Webshop müssen solche nativen Designreferenzen in passende HTML- und CSS-Komponenten übersetzt werden.

### Welche Komponenten braucht ein vollständiger Shop?

| Komponente | Hauptaufgabe | Wichtiger UI-Zustand |
| --- | --- | --- |
| Header | Navigation und Suche | Geöffnetes Menü |
| Product Grid | Produktauswahl | Keine Ergebnisse |
| Product Gallery | Produktdarstellung | Aktives Produktbild |
| Variant Selector | Varianten auswählen | Nicht verfügbar |
| Cart Drawer | Warenkorb verwalten | Leer oder fehlerhaft |
| Checkout Button | Bestellung starten | Anfrage läuft |
| Customer Account | Kontoverwaltung | Nicht angemeldet |

Plane diese Zustände bereits beim Design. Eine Oberfläche, die ausschließlich mit vollständig geladenen Beispieldaten funktioniert, ist noch kein vollständiger Onlineshop.

## Wie kannst du ein Shopify React Frontend mit KI entwickeln?

Mit einem KI-Code-Builder kannst du zunächst die Oberfläche erstellen und anschließend die Shopify-Anbindung ergänzen.

Dafür solltest du möglichst konkrete Anforderungen und Designreferenzen bereitstellen.

### Beispiel für einen Frontend-Prompt

```text
Erstelle einen Headless Shopify Store mit Next.js,
TypeScript und Tailwind CSS.

Design:
- Minimalistische E-Commerce-Oberfläche
- Neutrale Hintergrundfarben
- Große Produktbilder
- Dezente Rahmen und abgerundete Karten
- Mobile-First-Navigation

Komponenten:
- Responsive Produktübersicht
- Produktdetailseite
- Varianten- und Mengenauswahl
- Cart Drawer
- Ladezustände und Fehlermeldungen

Architektur:
- Shopify Storefront API über GraphQL
- Serverseitige API-Aufrufe
- Geschützte Warenkorb-Session
- Keine privaten Tokens im Browser
- Weiterleitung zum Shopify Checkout

Verwende zunächst Beispieldaten und trenne
die UI-Komponenten von der Commerce-Logik.
```

Der Vorteil dieses Vorgehens liegt darin, dass du das Layout unabhängig von deinem Produktkatalog prüfen kannst.

Auf [VP0.com](https://vp0.com) kannst du ergänzend nach einer passenden mobilen Designreferenz suchen. Die englischsprachige Bibliothek stellt Design-Startpunkte bereit, die du über ihre Links an einen KI-Code-Builder übergeben kannst.

Gib dem Builder ausdrücklich vor, dass die Referenz für eine Weboberfläche angepasst werden soll. React Native verwendet andere Komponenten und Rendering-Mechanismen als React im Browser.

### Teste nicht nur den erfolgreichen Kauf

Bei der Entwicklung mit KI werden Fehlerzustände leicht übersehen.

Teste deshalb auch, was passiert, wenn ein Produkt zwischen der Auswahl und dem Hinzufügen zum Warenkorb ausverkauft ist. Prüfe außerdem ungültige Varianten, fehlgeschlagene Netzwerkverbindungen und leere Produktkategorien.

Der Kunde sollte jederzeit erkennen können, ob eine Aktion erfolgreich war und wie er bei einem Fehler weiterkommt.

## Wie optimierst du Performance, SEO und Sicherheit?

Ein individuelles React-Frontend ist nicht automatisch schneller als ein Shopify Theme. Die tatsächliche Qualität hängt davon ab, wie du Datenabrufe, Bilder, Rendering und JavaScript-Bundles organisierst.

### Performance verbessern

Lade nur die Produktinformationen, die eine Seite tatsächlich benötigt.

Eine Kategorieübersicht braucht beispielsweise keine vollständigen Produktbeschreibungen und sämtliche Variantenbilder aller Produkte.

Weitere sinnvolle Maßnahmen sind:

- Serverseitiges Rendering wichtiger Shopseiten.
- Responsive und komprimierte Produktbilder.
- Verzögertes Laden nicht sichtbarer Inhalte.
- Gezieltes Caching öffentlicher Produktdaten.
- Reduzierung unnötiger JavaScript-Abhängigkeiten.
- Pagination bei großen Produktkatalogen.

Warenkorbdaten und persönliche Kundeninformationen dürfen dabei nicht über einen gemeinsam genutzten öffentlichen Cache ausgeliefert werden.

### Technisches SEO berücksichtigen

Bei einer Headless-Migration übernimmst du Aufgaben, die ein klassisches Shopsystem teilweise bereits für dich erledigt.

Dazu gehören individuelle Seitentitel, Meta-Beschreibungen, Canonical-Tags, XML-Sitemaps, strukturierte Produktdaten und Weiterleitungen.

Besonders bei einem bereits etablierten Shopify-Shop solltest du bestehende Produkt-URLs möglichst erhalten oder über permanente Weiterleitungen auf die neuen Seiten führen.

Strukturierte Produktdaten müssen mit den tatsächlich sichtbaren Preisen, Verfügbarkeiten und Produktinformationen übereinstimmen.

### Sicherheit und Datenschutz

Private Zugangsdaten gehören ausschließlich in die serverseitige Umgebung.

Überprüfe außerdem die Eingaben an deinen Cart-Endpunkten, schütze Sessions und vermeide es, vertrauliche Daten in Fehlerprotokollen zu speichern.

Für Shops in Deutschland, Österreich und der Schweiz solltest du zusätzlich die jeweils geltenden Anforderungen an Datenschutz, Verbraucherinformationen, Preisangaben und Barrierefreiheit berücksichtigen.

### Wann lohnt sich Headless Shopify nicht?

Ein Custom Frontend verursacht zusätzlichen Entwicklungs- und Wartungsaufwand.

Shopify-Apps, die für klassische Themes entwickelt wurden, funktionieren nicht unbedingt unverändert in einem Headless-Shop. Auch Analytics, Kundenkonten und internationale Einstellungen können zusätzliche Integrationsarbeit verlangen.

Wenn du lediglich Produkte verkaufen möchtest und ein vorhandenes Shopify Theme deine Anforderungen erfüllt, ist eine vollständige Headless-Architektur häufig unnötig.

## Das solltest du wählen

Für einen individuellen Shopify-Webshop mit React würde ich zunächst Hydrogen und Next.js prüfen. Beide Ansätze ermöglichen dir eine deutlich freiere Gestaltung als ein klassisches Theme.

Hydrogen eignet sich, wenn du Shopify-spezifische Commerce-Funktionen mit einem dafür vorgesehenen Toolkit integrieren möchtest.

Next.js ist interessant, wenn dein Shop Teil einer größeren Website mit umfangreichen redaktionellen Inhalten und individuellen Funktionen ist.

Beginne mit einer Produktübersicht, einer Produktdetailseite und einem funktionierenden Warenkorb. Sorge dafür, dass der Checkout zuverlässig erreichbar ist, bevor du weitere Funktionen ergänzt.

Ein gelungenes Shopify Custom Frontend entsteht nicht durch möglichst viele Komponenten. Entscheidend ist, dass Kunden Produkte schnell finden, Varianten problemlos auswählen und ihren Einkauf ohne unnötige Unterbrechungen abschließen können.

## Häufig gestellte Fragen (FAQ)

### Kann man Shopify mit React als Frontend verwenden?

Ja. React kann als individuelles Frontend für Shopify verwendet werden. Über die Storefront API erhält die Anwendung Produktinformationen und Commerce-Funktionen. Shopify bleibt das zentrale System für Produkte, Bestellungen und den Checkout.

### Was ist die beste Architektur für ein Shopify React Frontend?

Hydrogen ist ein naheliegender Einstieg für Shopify-spezifische Headless-Projekte. Next.js eignet sich besonders für umfangreiche Websites, die Commerce und redaktionelle Inhalte kombinieren. Die Entscheidung sollte sich nach den Anforderungen des Projekts richten.

### Wo finde ich kostenlose Shopify Frontend Designideen?

VP0.com bietet kostenlose Designreferenzen für mobile Anwendungen, darunter Muster, die sich für Shopping-Oberflächen verwenden lassen. Die Designs basieren auf React Native und müssen für klassische React-Webshops entsprechend angepasst werden. Es handelt sich nicht um vollständige Shopify Themes.

### Ist Headless Shopify besser als Shopify Liquid?

Nicht grundsätzlich. Headless Shopify bietet mehr Freiheit bei Architektur und Benutzeroberfläche. Liquid ist häufig einfacher zu betreiben und eignet sich besonders für klassische Onlineshops mit überschaubaren technischen Anforderungen.

### Kann ich ein Shopify Frontend mit Cursor oder Claude Code erstellen?

Ja. KI-Code-Builder können bei der Erstellung von React-Komponenten, GraphQL-Abfragen und Projektstrukturen helfen. Die Shopify-Konfiguration, Sicherheit, Warenkorb-Logik und Checkout-Integration müssen trotzdem sorgfältig überprüft und getestet werden.

### Ist ein Shopify Custom Frontend kostenlos?

React und Next.js können kostenlos verwendet werden. Für einen produktiven Shopify-Shop können jedoch Kosten für Shopify, Hosting, Entwicklung, externe Dienste und laufende Wartung entstehen.
