# Kalender Komponente Tailwind CSS: Fertiger Code & Beispiele 2026

Von Lawrence Dauchy, Gründer von VP0  
Veröffentlicht am 7. Oktober 2026

Eine Kalender-Komponente mit Tailwind CSS besteht aus einem übersichtlichen Monatsraster, einer Navigation und einer klar erkennbaren Datumsauswahl. Tailwind gestaltet die Oberfläche; JavaScript berechnet die Tage und verarbeitet die Auswahl. Der folgende Code verbindet beides ohne zusätzliche Kalenderbibliothek: mit deutscher Beschriftung, Montag als Wochenbeginn und einem Formularwert für das gewählte Datum. Für eine spätere iOS-App kann VP0 als kostenlose Bibliothek für App-Designs einen visuellen Ausgangspunkt liefern. Die Web-Komponente hier kannst du dagegen direkt in ein bestehendes Tailwind-Projekt einbauen und für Terminbuchungen, Aufgaben oder eine einfache Tagesauswahl anpassen.

## Welche Kalender-Komponente brauchst du für dein Projekt?

Für die Auswahl eines einzelnen Datums genügt ein Monatskalender. Sobald Nutzer Uhrzeiten buchen, Termine verschieben oder mehrere Kalender vergleichen sollen, brauchst du zusätzliche Funktionen und ein passendes Datenmodell.

Drei Oberflächen werden häufig unter demselben Begriff gesucht:

- **Datumsauswahl:** Ein Nutzer wählt beispielsweise den gewünschten Liefertag.
- **Buchungskalender:** Ein Nutzer sieht verfügbare Tage und anschließend passende Uhrzeiten.
- **Terminkalender:** Ein Nutzer verwaltet bestehende Ereignisse in einer Monats-, Wochen- oder Tagesansicht.

Der fertige Code konzentriert sich auf die erste Variante. Er zeigt einen Monat, erlaubt den Wechsel zum vorherigen oder nächsten Monat und speichert einen ausgewählten Tag.

Das ist ein sinnvoller Einstieg für ein Kontaktformular, eine Aufgabenverwaltung oder eine Reservierungsanfrage. Eine Auswahl bedeutet dabei noch keine bestätigte Buchung. Dafür muss dein Server prüfen, ob der Termin tatsächlich verfügbar ist.

Wenn dein Formular nur ein Geburtsdatum benötigt, lohnt sich auch ein gewöhnliches Datumsfeld. Eine eigene Kalenderoberfläche ist vor allem dann hilfreich, wenn du zusätzliche Informationen direkt am Tag zeigen möchtest: freie Plätze, gesperrte Tage oder kleine Terminmarkierungen.

Entscheide deshalb zuerst, welche Information der Nutzer auswählen soll. Ein aufwendig gestalteter Monatskalender hilft wenig, wenn eigentlich eine Uhrzeit oder eine wiederkehrende Terminserie gefragt ist.

## Wie ist der Kalender mit Tailwind CSS aufgebaut?

Die Komponente besteht aus einem Kopfbereich, sieben Wochentagsüberschriften und einem Raster mit Tagesbuttons. Darunter stehen die aktuelle Auswahl und ein verstecktes Formularfeld.

Im Kopfbereich findest du den Monatsnamen und zwei Navigationsbuttons. Das Tagesraster verwendet sieben gleich breite Spalten. Tailwind stellt dafür die Klasse `grid-cols-7` bereit.

Die einzelnen Zustände müssen eindeutig bleiben:

- Der aktuelle Tag bekommt eine zusätzliche Umrandung.
- Der ausgewählte Tag erhält eine dunkle Hintergrundfarbe.
- Tage aus angrenzenden Monaten erscheinen heller.
- Tastaturfokus bekommt einen sichtbaren Rahmen.
- Die Auswahl wird unterhalb des Kalenders ausgeschrieben.

„Heute“ und „ausgewählt“ bedeuten unterschiedliche Dinge. Öffnet jemand den Kalender am 7. Oktober und wählt den 12. Oktober, müssen beide Informationen erkennbar sein.

Das Beispiel zeigt immer sechs Wochen. Dadurch bleibt die Höhe beim Monatswechsel gleich. Einige sichtbare Tage gehören deshalb zum vorherigen oder folgenden Monat. Sie sind ebenfalls auswählbar; beim Anklicken wechselt die Ansicht zum betreffenden Monat.

Voraussetzung ist ein Projekt, in dem Tailwind CSS bereits eingebunden ist. Füge das HTML in deine Seite ein und platziere das Skript direkt dahinter. Bei mehreren Kalendern auf derselben Seite braucht jede Instanz eigene Elementkennungen oder eine gekapselte Initialisierung.

## Wie sieht der fertige Kalender-Code aus?

Der folgende Code erzeugt einen interaktiven Monatskalender mit deutschen Datumsangaben. Du benötigst dafür HTML, Tailwind CSS und gewöhnliches JavaScript.

Die Tagesberechnung berücksichtigt unterschiedliche Monatslängen und Schaltjahre. Die Oberfläche startet im aktuellen Monat, zunächst ohne ausgewähltes Datum.

```html
<section
  id="calendar"
  aria-labelledby="calendar-heading"
  class="mx-auto w-full max-w-md rounded-2xl border
         border-slate-200 bg-white p-4 shadow-sm sm:p-6"
>
  <h2
    id="calendar-heading"
    class="mb-4 text-lg font-semibold text-slate-900"
  >
    Datum auswählen
  </h2>

  <div class="mb-5 flex items-center justify-between gap-3">
    <button
      id="calendar-prev"
      type="button"
      aria-label="Vorherigen Monat anzeigen"
      class="min-h-11 rounded-lg border border-slate-200
             px-3 text-slate-700 hover:bg-slate-100
             focus-visible:outline-2
             focus-visible:outline-offset-2
             focus-visible:outline-indigo-600"
    >
      Zurück
    </button>

    <p
      id="calendar-month"
      aria-live="polite"
      aria-atomic="true"
      class="text-center font-semibold text-slate-900"
    ></p>

    <button
      id="calendar-next"
      type="button"
      aria-label="Nächsten Monat anzeigen"
      class="min-h-11 rounded-lg border border-slate-200
             px-3 text-slate-700 hover:bg-slate-100
             focus-visible:outline-2
             focus-visible:outline-offset-2
             focus-visible:outline-indigo-600"
    >
      Weiter
    </button>
  </div>

  <div
    aria-hidden="true"
    class="mb-2 grid grid-cols-7 text-center
           text-sm font-medium text-slate-500"
  >
    <span>Mo</span>
    <span>Di</span>
    <span>Mi</span>
    <span>Do</span>
    <span>Fr</span>
    <span>Sa</span>
    <span>So</span>
  </div>

  <div
    id="calendar-days"
    role="group"
    aria-label="Tage des angezeigten Monats"
    class="grid grid-cols-7 gap-1"
  ></div>

  <p
    id="calendar-selection"
    role="status"
    aria-atomic="true"
    class="mt-5 text-sm text-slate-600"
  >
    Noch kein Datum ausgewählt.
  </p>

  <input
    id="calendar-value"
    type="hidden"
    name="appointmentDate"
    value=""
  >
</section>

<script>
(() => {
  const root = document.getElementById("calendar");
  const monthLabel = root.querySelector("#calendar-month");
  const daysContainer = root.querySelector("#calendar-days");
  const selectionLabel = root.querySelector(
    "#calendar-selection"
  );
  const input = root.querySelector("#calendar-value");

  const today = new Date();
  let visibleMonth = new Date(
    today.getFullYear(),
    today.getMonth(),
    1
  );
  let selectedDate = "";

  const monthFormatter = new Intl.DateTimeFormat("de-DE", {
    month: "long",
    year: "numeric"
  });

  const dateFormatter = new Intl.DateTimeFormat("de-DE", {
    weekday: "long",
    day: "numeric",
    month: "long",
    year: "numeric"
  });

  function dateKey(date) {
    const year = date.getFullYear();
    const month = String(date.getMonth() + 1).padStart(2, "0");
    const day = String(date.getDate()).padStart(2, "0");

    return `${year}-${month}-${day}`;
  }

  function render(focusKey = null) {
    monthLabel.textContent = monthFormatter.format(
      visibleMonth
    );
    daysContainer.replaceChildren();

    const year = visibleMonth.getFullYear();
    const month = visibleMonth.getMonth();
    const firstDay = new Date(year, month, 1);
    const offset = (firstDay.getDay() + 6) % 7;

    for (let index = 0; index < 42; index++) {
      const date = new Date(
        year,
        month,
        index - offset + 1
      );
      const key = dateKey(date);
      const isSelected = key === selectedDate;
      const isToday = key === dateKey(today);
      const isCurrentMonth = date.getMonth() === month;

      const button = document.createElement("button");
      button.type = "button";
      button.dataset.date = key;
      button.textContent = String(date.getDate());

      button.setAttribute(
        "aria-label",
        dateFormatter.format(date)
      );
      button.setAttribute(
        "aria-pressed",
        String(isSelected)
      );

      if (isToday) {
        button.setAttribute("aria-current", "date");
      }

      button.className =
        "min-h-11 rounded-lg text-sm font-medium " +
        "focus-visible:outline-2 " +
        "focus-visible:outline-offset-2 " +
        "focus-visible:outline-indigo-600";

      if (isSelected) {
        button.className +=
          " bg-indigo-600 text-white hover:bg-indigo-700";
      } else if (isCurrentMonth) {
        button.className +=
          " text-slate-900 hover:bg-slate-100";
      } else {
        button.className +=
          " text-slate-400 hover:bg-slate-100";
      }

      if (isToday) {
        button.className += " ring-1 ring-indigo-400";
      }

      button.addEventListener("click", () => {
        selectedDate = key;
        input.value = key;

        visibleMonth = new Date(
          date.getFullYear(),
          date.getMonth(),
          1
        );

        selectionLabel.textContent =
          `Ausgewählt: ${dateFormatter.format(date)}`;

        render(key);

        input.dispatchEvent(
          new Event("change", { bubbles: true })
        );
      });

      daysContainer.append(button);
    }

    if (focusKey) {
      daysContainer
        .querySelector(`[data-date="${focusKey}"]`)
        ?.focus();
    }
  }

  function changeMonth(step) {
    visibleMonth = new Date(
      visibleMonth.getFullYear(),
      visibleMonth.getMonth() + step,
      1
    );

    render();
  }

  root.querySelector("#calendar-prev")
    .addEventListener("click", () => changeMonth(-1));

  root.querySelector("#calendar-next")
    .addEventListener("click", () => changeMonth(1));

  render();
})();
</script>
```

Das versteckte Feld wird nur dann mit einem Formular abgesendet, wenn es innerhalb dieses Formulars liegt oder ihm ausdrücklich zugeordnet ist. Setze die gesamte Kalendersektion daher beispielsweise zwischen deine öffnenden und schließenden Formular-Tags.

Die Komponente verwendet normale Buttons. Du kannst sie mit der Tabulatortaste erreichen und mit Enter oder der Leertaste auswählen. Eine Pfeiltastensteuerung zwischen den Tagen ist in diesem bewusst einfachen Beispiel noch nicht enthalten.

## Wie funktionieren Monatswechsel und Datumsauswahl?

Der Kalender speichert den angezeigten Monat getrennt vom ausgewählten Datum. Dadurch kannst du durch andere Monate navigieren, ohne deine bisherige Auswahl zu verlieren.

`visibleMonth` enthält immer den ersten Tag des angezeigten Monats. Diese Entscheidung verhindert einen typischen Fehler: Wenn du vom 31. Januar aus lediglich die Monatszahl erhöhst, kann die Datumsberechnung über den kürzeren Februar hinauslaufen.

Beim Monatswechsel wird deshalb ein neues Datum mit dem Tageswert `1` erzeugt. JavaScript verarbeitet dabei auch Jahreswechsel. Auf Dezember folgt Januar des nächsten Jahres; vor Januar liegt Dezember des vorherigen Jahres.

Die Berechnung des Wochenbeginns erfolgt mit:

```js
const offset = (firstDay.getDay() + 6) % 7;
```

Damit wird Montag zur ersten Spalte. Der Offset sagt, wie viele Tage vor dem ersten Monatstag im Raster erscheinen müssen.

Die Datumsauswahl verwendet dagegen einen eindeutigen Textwert, beispielsweise `2026-10-12`. Der sichtbare Text kann „Montag, 12. Oktober 2026“ lauten, während dein Formular eine gleichbleibende technische Darstellung erhält.

Für reine Kalendertage baut das Beispiel diesen Wert aus lokalen Jahr-, Monats- und Tagesbestandteilen zusammen. Es verwendet dafür keine Umwandlung nach UTC. So wird ein lokal gewählter Tag nicht durch eine Zeitzonenumrechnung versehentlich zum Vortag.

Wenn du später Uhrzeiten ergänzt, brauchst du eine weitere Entscheidung: Gilt die Uhrzeit am Standort des Unternehmens oder am Standort des Nutzers? Speichere diese Information ausdrücklich. Ein Datum allein beantwortet diese Frage nicht.

## Wie passt du Farben, Größe und verfügbare Tage an?

Passe zuerst die Zustände an und danach die dekorativen Details. Auswahl, Fokus und gesperrte Tage müssen auch nach einem Farbwechsel verständlich bleiben.

Für eine andere Akzentfarbe ersetzt du die vollständigen Indigo-Klassen durch entsprechende Klassen deiner Farbpalette. Ändere dabei nicht nur den Hintergrund der Auswahl, sondern auch den Fokusrand und die Markierung des heutigen Tages.

Vermeide zusammengesetzte Klassennamen wie:

```js
const colorClass = `bg-${color}-600`;
```

Verwende stattdessen vollständige Klassen in einer festen Zuordnung. Tailwind erkennt Klassen als Text in deinen Quelldateien; dynamisch zusammengesetzte Namen werden dabei nicht zuverlässig erfasst.

Für einen kompakteren Kalender kannst du den äußeren Abstand verkleinern. Lass die Tagesbuttons trotzdem ausreichend groß. Ein Monatsraster muss auf dem Smartphone mit dem Finger bedienbar bleiben.

### Vergangene Tage sperren

Vergleiche jeden Tag mit dem heutigen Datum auf Tagesebene. Ergänze innerhalb der Schleife vor dem Klick-Handler:

```js
const startOfToday = new Date(
  today.getFullYear(),
  today.getMonth(),
  today.getDate()
);

if (date < startOfToday) {
  button.disabled = true;
  button.className +=
    " cursor-not-allowed opacity-40";
}
```

Ein deaktivierter Button lässt sich nicht auswählen. Für eine Buchungsoberfläche solltest du zusätzlich erklären, warum bestimmte Tage nicht verfügbar sind. Eine blasse Zahl allein verrät nicht, ob der Tag vergangen, ausgebucht oder grundsätzlich geschlossen ist.

### Wochenenden ausschließen

Wenn dein Betrieb nur werktags Termine anbietet, kannst du Samstag und Sonntag sperren:

```js
const weekday = date.getDay();

if (weekday === 0 || weekday === 6) {
  button.disabled = true;
  button.className +=
    " cursor-not-allowed opacity-40";
}
```

Diese Regel bildet noch keine Feiertage ab. Feiertage unterscheiden sich nach Land und Region. Halte solche Regeln in einer eigenen Datenquelle, statt sie zwischen Farbklassen und Klick-Handlern zu verstecken.

### Einzelne Tage blockieren

Für eine kleine Demo genügt eine Menge gesperrter Datumswerte:

```js
const blockedDates = new Set([
  "2026-10-15",
  "2026-10-16",
  "2026-10-23"
]);
```

Prüfe anschließend innerhalb der Schleife, ob `blockedDates.has(key)` zutrifft. Für echte Reservierungen kommen diese Informationen vom Server. Auch beim Absenden muss die Verfügbarkeit erneut geprüft werden, weil zwischen Anzeige und Buchung ein anderer Nutzer denselben Termin wählen kann.

## Welche Beispiele lassen sich daraus entwickeln?

Die Komponente eignet sich als Ausgangspunkt für Liefertermine, Terminwünsche und Tagesansichten. Jede Erweiterung sollte eine konkrete Aufgabe unterstützen.

### Beispiel 1: Lieferdatum auswählen

Zeige nur Tage, an denen dein Versand tatsächlich zustellt. Wenn eine Bestellung eine Vorlaufzeit benötigt, sperrst du zusätzlich die unmittelbar bevorstehenden Tage.

Unter dem Kalender sollte eine verständliche Bestätigung stehen: „Gewünschtes Lieferdatum: 12. Oktober 2026“. Ist das Datum unverbindlich, benenne es ausdrücklich als Wunschdatum.

### Beispiel 2: Beratungstermin anfragen

Nach der Datumsauswahl öffnest du eine Liste verfügbarer Uhrzeiten. Verwende dafür eigene Buttons wie „09:00“, „10:30“ und „14:00“.

Speichere Datum und Uhrzeit getrennt oder über eine eindeutige Terminkennung. Ein Tag mit verfügbaren Terminen darf auswählbar sein; die eigentliche Reservierung erfolgt erst nach Auswahl eines freien Zeitfensters.

### Beispiel 3: Aufgaben nach Tag anzeigen

Ein Klick auf einen Tag filtert die Aufgabenliste darunter. Kleine Markierungen können anzeigen, dass an diesem Tag Aufgaben vorhanden sind.

Ergänze die Information auch im zugänglichen Namen des Tagesbuttons, beispielsweise „12. Oktober 2026, drei Aufgaben“. So bleibt die Bedeutung unabhängig von einem farbigen Punkt verständlich.

Wenn du denselben Ablauf später als iOS-App gestaltest, kann VP0 helfen, eine passende visuelle Richtung für Screens und Navigation zu finden. Das Datenmodell und die Kalenderlogik musst du weiterhin auf deine Anwendung abstimmen.

## Was solltest du vor dem Einsatz überprüfen?

Prüfe Datumsberechnung, Bedienung und Formularverhalten getrennt. Ein optisch überzeugender Kalender kann trotzdem den falschen Wert absenden oder beim Monatswechsel den Fokus verlieren.

Für die Datumsberechnung solltest du mindestens diese Fälle durchgehen:

- Einen Monat, der an einem Montag beginnt.
- Einen Monat, der an einem Sonntag beginnt.
- Februar mit 28 Tagen.
- Februar in einem Schaltjahr.
- Den Wechsel von Dezember zu Januar.
- Die Auswahl eines Tages aus dem angrenzenden Monat.

Prüfe anschließend die Tastaturbedienung. Bleibt der Fokus sichtbar? Kannst du jeden aktiven Button erreichen? Bleibt die Auswahl nach einem Monatswechsel erhalten? Landet der Fokus nach dem Anklicken wieder auf dem ausgewählten Tag?

Das Beispiel verwendet eine einfache Gruppe von Buttons. Für einen umfangreicheren Datepicker kannst du eine Navigation mit Pfeiltasten, einem einzigen Tabulatorstopp im Tagesraster und passenden Tastenkürzeln entwickeln. Das WAI-ARIA-Datepicker-Beispiel beschreibt ein solches Interaktionsmuster und weist auf die notwendige Prüfung mit assistiven Technologien hin.

Prüfe außerdem die mobile Darstellung mit langen Monatsnamen und vergrößerter Schrift. Die Navigation darf den Monatsnamen nicht verdecken. Farbige Zustände müssen lesbar bleiben, auch wenn dein Gerät einen anderen Kontrast zeigt als dein Entwicklungsmonitor.

Die Grenze des Beispiels ist klar: Es enthält keine Terminverwaltung, keine Bereichsauswahl und keinen modalen Dialog. Bei einem geöffneten Kalenderdialog kämen zusätzlich Fokusführung, Schließen mit Escape und die Rückkehr zum auslösenden Button hinzu.

## Das solltest du wählen

Verwende die gezeigte Komponente, wenn du einen einzelnen Tag auswählen und die Oberfläche selbst gestalten möchtest. Sie ist überschaubar genug, um Datumsberechnung, Darstellung und Formularwert nachvollziehen zu können.

Für ein schlichtes Formularfeld würde ich zuerst ein natives Datumsfeld prüfen. Für Reservierungen ergänzt du Verfügbarkeiten, Uhrzeiten und eine serverseitige Bestätigung. Für einen vollständigen Terminkalender mit wiederkehrenden Ereignissen und verschiebbaren Terminen lohnt sich eine spezialisierte Kalenderlösung.

Arbeite in dieser Reihenfolge: erst korrekte Tage, dann eindeutige Auswahl, anschließend Tastaturbedienung und zuletzt die optischen Details. So merkst du früh, ob die Komponente deinen tatsächlichen Ablauf unterstützt.

## Häufig gestellte Fragen (FAQ)

### Wie erstelle ich eine Kalender-Komponente mit Tailwind CSS?

Du baust die Oberfläche mit HTML und Tailwind-Klassen und ergänzt JavaScript für Monatsberechnung, Navigation und Auswahl. Der Code oben liefert dafür einen vollständigen Ausgangspunkt innerhalb eines bereits eingerichteten Tailwind-Projekts. Eine zusätzliche Kalenderbibliothek ist für diese einfache Tagesauswahl nicht erforderlich.

### Funktioniert ein interaktiver Kalender nur mit Tailwind CSS?

Tailwind CSS gestaltet den Kalender, berechnet aber keine Tage und speichert keine Auswahl. Für Monatswechsel und individuelle Interaktionen brauchst du JavaScript oder die Zustandslogik deines Frameworks. Alternativ kannst du ein natives HTML-Datumsfeld verwenden, dessen Auswahloberfläche der Browser bereitstellt.

### Kann ich die Komponente in React oder Vue verwenden?

Ja, du kannst Darstellung und Datumsberechnung übernehmen. Ersetze dabei die direkten DOM-Zugriffe durch den Zustand und die Ereignisbehandlung deines Frameworks. In React verwaltest du beispielsweise Monat und Auswahl über State; in Vue über reaktive Werte. Die Tagesbuttons werden dann aus einer berechneten Liste gerendert.

### Was ist die beste Lösung für eine einfache Datumsauswahl?

Für ein gewöhnliches Formular ist ein natives Datumsfeld häufig der praktischste Einstieg. Ein eigener Monatskalender lohnt sich, wenn du Verfügbarkeiten oder Zusatzinformationen pro Tag anzeigen möchtest. Entscheide anhand der benötigten Interaktion und des Aufwands für Entwicklung und Prüfung.

### Eignet sich VP0 für einen Tailwind-Webkalender?

VP0 liefert kostenlose Design-Startpunkte für iOS-Apps, hauptsächlich auf Basis von Expo React Native. Für einen Tailwind-Webkalender ist die hier gezeigte Web-Komponente der direkte technische Ausgangspunkt. Bei einer späteren iOS-Version kann ein passendes App-Design helfen, den Kalender in den gesamten Bildschirmablauf einzuordnen.
