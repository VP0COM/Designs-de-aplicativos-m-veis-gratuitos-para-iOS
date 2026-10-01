# Apple Website Scroll Effekt CSS: Code & Beispiele für den Apple-Look 2026

Von Lawrence Dauchy, Gründer von VP0  
Veröffentlicht am 1. Oktober 2026

Apple gehört zu den bekanntesten Beispielen für Websites, bei denen Scrollen nicht nur der Navigation dient, sondern Teil des eigentlichen Designs ist. Inhalte erscheinen kontrolliert, Bilder bewegen sich langsamer als der restliche Inhalt, Produkte bleiben für einige Sekunden im Fokus und einzelne Elemente verändern ihre Größe oder Position abhängig vom Scrollfortschritt.

Die gute Nachricht: Für einen überzeugenden Apple-Look brauchst du weder ein riesiges JavaScript-Framework noch komplizierte WebGL-Szenen.

Viele typische Effekte lassen sich 2026 mit modernem CSS, wenigen Zeilen JavaScript und sauber aufgebauten HTML-Sektionen nachbauen.

In diesem Guide zeigen wir praktische CSS-Beispiele für:

- Sticky Product Sections
- Scroll Reveal Animationen
- Parallax-Effekte
- Scale-on-Scroll
- Text-Fades
- Scroll Progress Animationen
- Fullscreen Product Sections
- Bildsequenzen
- Performance-Optimierung
- Reduced-Motion-Unterstützung

## Was macht den Apple-Look beim Scrollen aus?

Der typische Apple-Stil entsteht nicht durch einen einzelnen Effekt.

Es ist die Kombination aus mehreren Prinzipien.

### Große visuelle Flächen

Apple-ähnliche Seiten verwenden häufig sehr große Sections. Statt zehn Informationen gleichzeitig zu zeigen, bekommt eine einzelne Aussage ausreichend Platz.

### Kontrollierte Bewegung

Animationen bewegen sich meistens langsam und vorhersehbar.

Ein Element springt nicht plötzlich ins Bild. Es:

- wird langsam sichtbar
- vergrößert sich leicht
- bewegt sich wenige Pixel
- bleibt kurz fixiert
- verschwindet anschließend wieder

### Sticky Elemente

Besonders wichtig sind Elemente mit:

```css
position: sticky;
```

Damit kann beispielsweise ein Produktbild auf dem Bildschirm bleiben, während Textinhalte daran vorbeiscrollen.

### Viel negativer Raum

Der Premium-Eindruck entsteht nicht nur durch Animation.

Whitespace ist mindestens genauso wichtig.

Eine gute Apple-inspirierte Section benötigt oft deutlich mehr vertikalen Abstand als eine klassische Landingpage.

## Die einfachste Apple-Style Scroll Section

Beginnen wir mit einem simplen Aufbau.

```html
<section class="apple-section">
  <div class="apple-content">
    <p class="eyebrow">Neues Produkt</p>
    <h2>Ein Design, das sich leicht anfühlt.</h2>
    <p>
      Große Typografie, viel Raum und eine kontrollierte Scroll-Animation.
    </p>
  </div>
</section>
```

Das CSS:

```css
.apple-section {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 8rem 2rem;
  background: #f5f5f7;
}

.apple-content {
  width: min(900px, 100%);
  text-align: center;
}

.eyebrow {
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

.apple-content h2 {
  font-size: clamp(3rem, 8vw, 7rem);
  line-height: 0.95;
  letter-spacing: -0.05em;
  margin: 0;
}

.apple-content p {
  max-width: 620px;
  margin: 2rem auto 0;
  font-size: 1.25rem;
  line-height: 1.6;
}
```

Bereits dieser Aufbau erzeugt einen ähnlichen visuellen Rhythmus.

Der eigentliche Apple-Look entsteht anschließend durch Bewegung.

## Apple Scroll Reveal mit CSS und JavaScript

Ein sehr verbreiteter Effekt ist das langsame Einblenden eines Inhalts.

Das Element startet leicht transparent und etwas weiter unten.

```css
.reveal {
  opacity: 0;
  transform: translateY(60px);
  transition:
    opacity 900ms ease,
    transform 900ms cubic-bezier(0.22, 1, 0.36, 1);
}

.reveal.is-visible {
  opacity: 1;
  transform: translateY(0);
}
```

HTML:

```html
<section class="feature reveal">
  <h2>Mehr sehen. Weniger Ablenkung.</h2>
</section>
```

JavaScript:

```javascript
const observer = new IntersectionObserver(
  entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add("is-visible");
      }
    });
  },
  {
    threshold: 0.2
  }
);

document.querySelectorAll(".reveal").forEach(element => {
  observer.observe(element);
});
```

Dieser Ansatz eignet sich besonders für:

- Headlines
- Feature-Blöcke
- Screenshots
- Produktbilder
- Testimonials
- Call-to-Action-Sections

Wichtig ist, dass die Bewegung subtil bleibt.

`translateY(200px)` würde beispielsweise schnell wie eine klassische Marketing-Animation wirken.

Für einen ruhigeren Premium-Look sind Werte zwischen ungefähr 20 und 80 Pixeln meist überzeugender.

## Sticky Scroll Effekt wie auf Produktseiten

Sticky Sections sind eine der wichtigsten Grundlagen für immersive Produktseiten.

HTML:

```html
<section class="story">
  <div class="sticky-product">
    <div class="product-visual">
      PRODUCT
    </div>
  </div>

  <div class="story-content">
    <article>
      <h2>Leichter.</h2>
      <p>Ein reduziertes Design mit klarer visueller Hierarchie.</p>
    </article>

    <article>
      <h2>Schneller.</h2>
      <p>Informationen erscheinen genau dann, wenn sie gebraucht werden.</p>
    </article>

    <article>
      <h2>Einfacher.</h2>
      <p>Die Bewegung unterstützt die Story statt von ihr abzulenken.</p>
    </article>
  </div>
</section>
```

CSS:

```css
.story {
  position: relative;
  display: grid;
  grid-template-columns: 1fr 1fr;
  max-width: 1400px;
  margin: 0 auto;
}

.sticky-product {
  position: relative;
}

.product-visual {
  position: sticky;
  top: 0;
  height: 100vh;
  display: grid;
  place-items: center;
  font-size: 4rem;
  font-weight: 700;
}

.story-content article {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 4rem;
}
```

Das Produkt bleibt links stehen, während die Inhalte rechts scrollen.

Dieses Pattern funktioniert besonders gut für:

- SaaS-Produkte
- Hardware
- Apps
- Portfolio-Projekte
- Design-Systeme
- Produkt-Launches

## Fullscreen Sticky Section

Eine dramatischere Variante verwendet eine gesamte Bildschirmfläche als Sticky Canvas.

```html
<section class="scroll-stage">
  <div class="scroll-stage__sticky">
    <h2>Gebaut für den Moment.</h2>
  </div>
</section>
```

```css
.scroll-stage {
  height: 300vh;
}

.scroll-stage__sticky {
  position: sticky;
  top: 0;
  height: 100vh;
  display: grid;
  place-items: center;
  overflow: hidden;
  background: #000;
  color: #fff;
}

.scroll-stage__sticky h2 {
  font-size: clamp(3rem, 8vw, 8rem);
  text-align: center;
}
```

Die äußere Section ist `300vh` hoch.

Das eigentliche Visual bleibt jedoch für die Dauer des Abschnitts mit `position: sticky` auf dem Bildschirm.

Damit entsteht ein Zeitraum, in dem du andere Animationen an den Scrollfortschritt koppeln kannst.

## Scale-on-Scroll Effekt

Ein häufiger Produktseiten-Effekt ist ein Visual, das sich beim Scrollen langsam vergrößert.

HTML:

```html
<section class="scale-section">
  <div class="scale-sticky">
    <div class="scale-object" id="scaleObject">
      VP0
    </div>
  </div>
</section>
```

CSS:

```css
.scale-section {
  height: 250vh;
}

.scale-sticky {
  position: sticky;
  top: 0;
  height: 100vh;
  display: grid;
  place-items: center;
  overflow: hidden;
}

.scale-object {
  width: 320px;
  aspect-ratio: 1;
  display: grid;
  place-items: center;
  border-radius: 3rem;
  background: #111;
  color: #fff;
  font-size: 3rem;
  will-change: transform;
}
```

JavaScript:

```javascript
const section = document.querySelector(".scale-section");
const object = document.querySelector("#scaleObject");

function updateScale() {
  const rect = section.getBoundingClientRect();

  const scrollable =
    section.offsetHeight - window.innerHeight;

  const progress = Math.min(
    Math.max(-rect.top / scrollable, 0),
    1
  );

  const scale = 1 + progress * 1.8;

  object.style.transform = `scale(${scale})`;
}

window.addEventListener("scroll", updateScale, {
  passive: true
});

updateScale();
```

`progress` bewegt sich dabei zwischen `0` und `1`.

Dadurch lassen sich praktisch beliebige CSS-Werte vom Scrollfortschritt abhängig machen.

## Eine wiederverwendbare Scroll-Progress-Funktion

Statt für jede Animation neue Logik zu schreiben, lohnt sich eine kleine Utility-Funktion.

```javascript
function getScrollProgress(section) {
  const rect = section.getBoundingClientRect();
  const distance = section.offsetHeight - window.innerHeight;

  if (distance <= 0) {
    return 0;
  }

  return Math.min(
    Math.max(-rect.top / distance, 0),
    1
  );
}
```

Danach:

```javascript
const section = document.querySelector(".scroll-section");

window.addEventListener(
  "scroll",
  () => {
    const progress = getScrollProgress(section);

    console.log(progress);
  },
  { passive: true }
);
```

Jetzt kann derselbe Wert für mehrere Animationen verwendet werden.

## Text mit Scrollfortschritt einblenden

Ein besonders eleganter Effekt besteht darin, Text abhängig vom Scrollfortschritt langsam sichtbar zu machen.

```javascript
const section = document.querySelector(".text-stage");
const text = document.querySelector(".scroll-text");

function animateText() {
  const progress = getScrollProgress(section);

  text.style.opacity = progress;
  text.style.transform =
    `translateY(${40 - progress * 40}px)`;
}

window.addEventListener(
  "scroll",
  animateText,
  { passive: true }
);
```

CSS:

```css
.scroll-text {
  opacity: 0;
  transform: translateY(40px);
  will-change: opacity, transform;
}
```

Bei einem Fortschritt von `0` befindet sich das Element 40 Pixel weiter unten.

Bei `1` erreicht es seine finale Position.

## Mehrere Texte nacheinander animieren

Produktseiten funktionieren besonders gut, wenn Informationen nicht gleichzeitig erscheinen.

Nehmen wir drei Textelemente:

```html
<div class="story-text">
  <p data-step="0">Extrem leicht.</p>
  <p data-step="1">Unglaublich schnell.</p>
  <p data-step="2">Für jeden Moment.</p>
</div>
```

JavaScript:

```javascript
const items = document.querySelectorAll("[data-step]");

function updateSteps(progress) {
  items.forEach((item, index) => {
    const start = index * 0.25;
    const end = start + 0.25;

    const localProgress = Math.min(
      Math.max((progress - start) / (end - start), 0),
      1
    );

    item.style.opacity = localProgress;
    item.style.transform =
      `translateY(${30 - localProgress * 30}px)`;
  });
}
```

Damit können Inhalte kontrolliert nacheinander eingeblendet werden.

## Parallax Effekt im Apple-Stil

Parallax sollte subtil eingesetzt werden.

Eine extrem starke Verschiebung erzeugt schnell einen künstlichen Effekt.

HTML:

```html
<section class="parallax-section">
  <div class="parallax-image"></div>
  <div class="parallax-copy">
    <h2>Eine neue Perspektive.</h2>
  </div>
</section>
```

CSS:

```css
.parallax-section {
  position: relative;
  min-height: 120vh;
  overflow: hidden;
}

.parallax-image {
  position: absolute;
  inset: -10%;
  background:
    radial-gradient(
      circle at center,
      #d7e5ff,
      #4e62ff 40%,
      #050505 75%
    );
  will-change: transform;
}

.parallax-copy {
  position: relative;
  min-height: 120vh;
  display: grid;
  place-items: center;
  color: white;
}

.parallax-copy h2 {
  font-size: clamp(3rem, 9vw, 8rem);
}
```

JavaScript:

```javascript
const parallax = document.querySelector(".parallax-image");

window.addEventListener(
  "scroll",
  () => {
    const offset = window.scrollY * 0.08;

    parallax.style.transform =
      `translateY(${offset}px)`;
  },
  { passive: true }
);
```

Der Faktor `0.08` hält die Bewegung relativ ruhig.

## Apple-Style Zoom Transition

Eine weitere interessante Technik besteht darin, ein Visual so stark zu vergrößern, dass es anschließend zur nächsten Section wird.

Beispiel:

```html
<section class="zoom-story">
  <div class="zoom-sticky">
    <div class="zoom-card" id="zoomCard">
      <span>Explore</span>
    </div>
  </div>
</section>
```

```css
.zoom-story {
  height: 300vh;
}

.zoom-sticky {
  position: sticky;
  top: 0;
  height: 100vh;
  display: grid;
  place-items: center;
  overflow: hidden;
  background: #f5f5f7;
}

.zoom-card {
  width: min(70vw, 800px);
  aspect-ratio: 16 / 10;
  border-radius: 3rem;
  background: #050505;
  color: white;
  display: grid;
  place-items: center;
  transform-origin: center;
  will-change: transform, border-radius;
}
```

JavaScript:

```javascript
const zoomSection =
  document.querySelector(".zoom-story");

const zoomCard =
  document.querySelector("#zoomCard");

function updateZoom() {
  const progress =
    getScrollProgress(zoomSection);

  const scale =
    1 + progress * 2.2;

  const radius =
    48 - progress * 48;

  zoomCard.style.transform =
    `scale(${scale})`;

  zoomCard.style.borderRadius =
    `${Math.max(radius, 0)}px`;
}

window.addEventListener(
  "scroll",
  updateZoom,
  { passive: true }
);
```

Während sich die Karte vergrößert, wird gleichzeitig der Border-Radius reduziert.

Dadurch kann die Karte optisch in eine Fullscreen-Section übergehen.

## Text Mask Effekt

Große Headlines gehören stark zum Apple-inspirierten Webdesign.

Ein interessanter Effekt ist Text, der schrittweise sichtbar wird.

```css
.mask-title {
  font-size: clamp(4rem, 10vw, 10rem);
  line-height: 0.9;

  background:
    linear-gradient(
      90deg,
      #111 0%,
      #111 var(--progress),
      #d2d2d7 var(--progress),
      #d2d2d7 100%
    );

  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
}
```

JavaScript:

```javascript
const title =
  document.querySelector(".mask-title");

const titleSection =
  document.querySelector(".title-section");

function updateTitle() {
  const progress =
    getScrollProgress(titleSection);

  title.style.setProperty(
    "--progress",
    `${progress * 100}%`
  );
}

window.addEventListener(
  "scroll",
  updateTitle,
  { passive: true }
);
```

Der Text wird dadurch nicht einfach eingeblendet.

Stattdessen verändert sich seine Farbe entsprechend dem Scrollfortschritt.

## Bildsequenzen beim Scrollen

Einige der beeindruckendsten Produktseiten verwenden keine klassische CSS-Animation.

Stattdessen werden zahlreiche Einzelbilder nacheinander auf einem Canvas dargestellt.

Das Prinzip:

```javascript
const frameCount = 120;
const images = [];

for (let i = 0; i < frameCount; i++) {
  const img = new Image();

  img.src =
    `/frames/frame-${String(i).padStart(4, "0")}.webp`;

  images.push(img);
}
```

Aus dem Scrollfortschritt lässt sich anschließend der aktuelle Frame berechnen:

```javascript
const frame =
  Math.min(
    frameCount - 1,
    Math.floor(progress * frameCount)
  );
```

Danach wird das entsprechende Bild in ein `<canvas>` gezeichnet.

Diese Technik eignet sich für:

- Produktrotationen
- Exploded Views
- Geräteanimationen
- Materialtransformationen
- 3D-ähnliche Produktvisualisierungen

Allerdings ist sie deutlich anspruchsvoller als reine CSS-Effekte.

## CSS Scroll-Driven Animations

Moderne Browser ermöglichen zunehmend Animationen, die direkt an Scroll-Timelines gekoppelt werden können.

Dadurch kann für bestimmte Effekte JavaScript vollständig entfallen.

Ein vereinfachtes Konzept sieht so aus:

```css
@keyframes reveal {
  from {
    opacity: 0;
    transform: translateY(60px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.scroll-reveal {
  animation: reveal linear both;
  animation-timeline: view();
  animation-range: entry 10% cover 40%;
}
```

Das Element reagiert damit direkt auf seine Position im Viewport.

Für moderne Projekte ist diese Technik besonders interessant, weil die Animationslogik näher am CSS bleibt.

Bei produktiven Websites sollte jedoch immer geprüft werden, welche Browser für die Zielgruppe unterstützt werden müssen.

## Apple-Look ohne zu viele Animationen

Ein häufiger Fehler besteht darin, eine Apple-ähnliche Website mit möglichst vielen Animationen gleichzusetzen.

Das Gegenteil funktioniert meistens besser.

Eine hochwertige Seite kann beispielsweise nur aus folgenden Elementen bestehen:

1. Große Hero-Headline
2. Langsame Fade-in-Animation
3. Sticky Produktvisual
4. Drei Story-Sections
5. Leichter Scale-Effekt
6. Große Abschluss-Section

Mehr braucht es häufig nicht.

## Die richtige Easing-Kurve

Animationen wirken stark unterschiedlich, obwohl Dauer und Bewegung identisch sind.

Ein klassisches:

```css
transition: transform 0.6s ease;
```

funktioniert.

Für weichere Premium-Bewegungen eignet sich häufig eine individuelle Cubic-Bezier-Kurve:

```css
transition:
  transform 900ms
  cubic-bezier(0.22, 1, 0.36, 1);
```

Oder:

```css
transition:
  all 1s
  cubic-bezier(0.16, 1, 0.3, 1);
```

Solche Kurven beschleunigen und bremsen weniger linear und fühlen sich dadurch natürlicher an.

## Performance: transform statt top verwenden

Scroll-Animationen laufen kontinuierlich.

Deshalb kann eine schlechte Implementierung schnell zu Ruckeln führen.

Wann immer möglich, sollten Animationen auf:

```css
transform
```

und:

```css
opacity
```

beschränkt bleiben.

Statt:

```javascript
element.style.top = `${value}px`;
```

ist meist besser:

```javascript
element.style.transform =
  `translateY(${value}px)`;
```

Transforms lassen sich vom Browser in vielen Fällen effizienter rendern.

## `will-change` gezielt verwenden

Für aktiv animierte Elemente kann Folgendes hilfreich sein:

```css
.animated-element {
  will-change: transform, opacity;
}
```

Allerdings sollte `will-change` nicht pauschal auf hundert Elemente angewendet werden.

Es ist eher ein Hinweis an den Browser für Elemente, bei denen tatsächlich häufige Veränderungen erwartet werden.

## Scroll-Events mit `requestAnimationFrame`

Bei komplexeren Animationen sollte die eigentliche Rendering-Logik nicht unkontrolliert bei jedem Scroll-Event ausgeführt werden.

Ein robusteres Pattern:

```javascript
let ticking = false;

function update() {
  const progress =
    getScrollProgress(section);

  object.style.transform =
    `scale(${1 + progress})`;

  ticking = false;
}

window.addEventListener(
  "scroll",
  () => {
    if (!ticking) {
      requestAnimationFrame(update);
      ticking = true;
    }
  },
  { passive: true }
);
```

Damit wird die Aktualisierung mit dem Render-Zyklus des Browsers koordiniert.

## Reduced Motion unterstützen

Nicht jeder Nutzer möchte starke Animationen sehen.

Deshalb sollte eine hochwertige Implementierung `prefers-reduced-motion` berücksichtigen.

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    scroll-behavior: auto !important;
    transition-duration: 0.01ms !important;
  }
}
```

Alternativ können einzelne immersive Animationen vollständig deaktiviert werden.

```css
@media (prefers-reduced-motion: reduce) {
  .scale-object,
  .parallax-image,
  .zoom-card {
    transform: none !important;
  }
}
```

## Responsives Verhalten nicht vergessen

Desktop-Scroll-Storytelling lässt sich nicht immer direkt auf Smartphones übertragen.

Auf kleineren Displays ist häufig eine reduzierte Version sinnvoll.

```css
@media (max-width: 768px) {
  .story {
    display: block;
  }

  .product-visual {
    height: 55vh;
    top: 0;
  }

  .story-content article {
    min-height: auto;
    padding: 5rem 1.5rem;
  }
}
```

Bei mobilen Geräten sollte besonders darauf geachtet werden, dass:

- Sticky Sections nicht unnötig lang werden
- Text jederzeit lesbar bleibt
- Animationen den Inhalt nicht blockieren
- Bilder nicht zu viel Speicher verbrauchen
- Touch-Scrolling flüssig bleibt

## Ein komplettes Apple-Style Scroll Pattern

Ein guter Aufbau für eine moderne Landingpage könnte so aussehen:

### Section 1: Hero

Große Headline und kurze Subline.

```text
Das nächste Kapitel.
Gebaut für Geschwindigkeit.
```

### Section 2: Reveal

Produktvisual erscheint beim Scrollen langsam.

### Section 3: Sticky Story

Produkt bleibt fixiert.

Daneben erscheinen drei Kernfunktionen.

### Section 4: Zoom

Das Produktvisual vergrößert sich und geht in die nächste Section über.

### Section 5: Detail Story

Nahaufnahmen oder Feature-Blöcke erscheinen nacheinander.

### Section 6: Abschluss

Große Abschlussbotschaft mit ruhiger Typografie.

Dieses Storytelling fühlt sich häufig hochwertiger an als eine Landingpage mit zwanzig kleinen Animationen.

## Wann eine Animationsbibliothek sinnvoll ist

Für viele Apple-inspirierte Seiten reichen CSS und wenige Zeilen JavaScript vollständig aus.

Eine zusätzliche Animationslösung wird interessant, wenn du:

- komplexe Timelines benötigst
- mehrere Animationen exakt synchronisieren willst
- Pinning intensiv verwendest
- horizontale Scroll-Sequenzen baust
- SVG-Pfade animierst
- sehr komplexe Scroll-Choreografien entwickelst

Für kleinere Produktseiten bedeutet eine zusätzliche Library jedoch auch:

- mehr Abhängigkeiten
- mehr JavaScript
- zusätzliche Wartung
- potenziell größere Bundles

Beginne deshalb am besten mit den Browser-Funktionen selbst.

## Apple-inspirierte UI-Komponenten schneller aufbauen

Wer nicht jedes Interface und jede Animation von Grund auf neu entwickeln möchte, kann wiederverwendbare Komponenten als Ausgangspunkt nutzen.

Bei VP0 liegt der Fokus auf Design- und Code-Komponenten, die Entwicklern dabei helfen können, moderne Interfaces schneller aufzubauen und anschließend an das eigene Produkt anzupassen.

Gerade für scrollbasierte Landingpages ist ein Komponentenansatz sinnvoll.

Statt die gesamte Seite als eine riesige Animation zu programmieren, kannst du sie in unabhängige Bausteine zerlegen:

- Hero
- Sticky Product Stage
- Feature Reveal
- Scroll Text
- Image Stage
- Zoom Transition
- CTA Section

Dadurch bleibt der Code wesentlich leichter wartbar.

## Häufige Fehler beim Apple Website Scroll Effekt

### Zu viel Bewegung

Wenn jedes Element rotiert, skaliert und gleichzeitig einfliegt, verliert die Animation ihren Premium-Eindruck.

### Zu schnelle Animationen

Kurze Animationen wirken häufig wie klassische UI-Microinteractions.

Große Storytelling-Elemente dürfen deutlich langsamer sein.

### Zu große Bewegungsdistanzen

Eine Headline muss nicht 500 Pixel durch den Bildschirm fliegen.

20 bis 80 Pixel reichen häufig vollkommen aus.

### Scrollen wird blockiert

Scroll-Jacking sollte vermieden werden.

Der Nutzer sollte weiterhin das Gefühl haben, die Seite selbst zu kontrollieren.

### Mobile wird ignoriert

Eine Animation, die auf einem großen Desktop beeindruckend wirkt, kann auf einem Smartphone störend sein.

### Inhalt wird der Animation untergeordnet

Die Animation soll den Inhalt unterstützen.

Wenn Besucher den Text nicht mehr verstehen, weil sie auf den richtigen Scrollpunkt achten müssen, ist das Design zu kompliziert.

## Apple-Look Checkliste für 2026

Für einen überzeugenden Apple-inspirierten Scroll-Look kannst du diese Punkte prüfen:

- Große Headlines
- Klare Typografie
- Viel Whitespace
- Ruhige Farbpalette
- Große Produktvisuals
- Sticky Sections
- Langsame Reveal-Animationen
- Dezentes Scaling
- Wenige Parallax-Effekte
- Gut kontrollierte Scroll-Distanzen
- Animation hauptsächlich über `transform` und `opacity`
- Mobile Anpassungen
- Reduced-Motion-Unterstützung
- Saubere Performance
- Storytelling vor Animation

## Fazit

Der typische Apple Website Scroll Effekt entsteht nicht durch eine einzelne geheime CSS-Technik.

Der Look basiert auf einer Kombination aus gutem Layout, großzügigem Whitespace, Sticky Sections, kontrollierten Transformationen und präzise getimten Scroll-Animationen.

Für die meisten Websites reichen bereits:

```css
position: sticky;
transform: translateY();
transform: scale();
opacity: 0;
```

kombiniert mit:

```javascript
IntersectionObserver
```

oder einem normalisierten Scrollfortschritt zwischen `0` und `1`.

Komplexere Animationen können anschließend schrittweise ergänzt werden.

Der wichtigste Grundsatz bleibt jedoch derselbe: Die Bewegung sollte die Geschichte des Produkts verstärken und nicht versuchen, selbst zum eigentlichen Produkt zu werden.

## Häufig gestellte Fragen

### Wie kann ich den Apple Scroll Effekt mit CSS nachbauen?

Für die Grundstruktur eignen sich `position: sticky`, `transform`, `opacity` und große Scroll-Sections. Einfache Reveal-Effekte können zusätzlich mit Intersection Observer ausgelöst werden.

### Kann man Apple-ähnliche Scroll Animationen ohne JavaScript erstellen?

Ja. Einfache Sticky Layouts und bestimmte moderne Scroll-Animationen können vollständig mit CSS umgesetzt werden. Für komplexere Animationen, die exakt vom Scrollfortschritt abhängen, ist JavaScript weiterhin häufig praktisch.

### Wie funktioniert ein Sticky Scroll Effekt?

Ein Element erhält `position: sticky` und beispielsweise `top: 0`. Es bleibt dadurch innerhalb seines übergeordneten Containers an einer festen Position im Viewport, während der restliche Inhalt weiter scrollt.

### Wie erstellt man einen Scale-on-Scroll Effekt?

Zuerst wird der Scrollfortschritt einer Section auf einen Wert zwischen `0` und `1` normalisiert. Dieser Wert wird anschließend verwendet, um `transform: scale()` dynamisch anzupassen.

### Welche CSS-Eigenschaften eignen sich am besten für Scroll Animationen?

Für flüssige Animationen sind insbesondere `transform` und `opacity` geeignet. Layout-verändernde Eigenschaften sollten bei kontinuierlichen Scroll-Animationen möglichst sparsam eingesetzt werden.

### Brauche ich GSAP für einen Apple-ähnlichen Website-Look?

Nein. Viele typische Effekte lassen sich mit CSS, Intersection Observer und wenigen Zeilen JavaScript umsetzen. Animationsbibliotheken sind vor allem bei komplexen Timelines und aufwendigen Scroll-Choreografien hilfreich.

### Wie lang sollte eine Sticky Scroll Section sein?

Das hängt von der gewünschten Story ab. Für einfache Effekte sind häufig etwa `200vh` bis `300vh` ausreichend. Entscheidend ist, dass sich die Section nicht künstlich lang anfühlt.

### Funktionieren solche Scroll Effekte auch auf Smartphones?

Ja, allerdings sollten sie für kleinere Displays angepasst werden. Kürzere Sections, weniger Bewegung und kleinere Bilddateien sorgen auf Mobilgeräten häufig für ein besseres Erlebnis.
