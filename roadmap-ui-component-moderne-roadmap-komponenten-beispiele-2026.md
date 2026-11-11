# Roadmap UI Component: Moderne Roadmap-Komponenten & Beispiele 2026

Von Lawrence Dauchy, Gründer von VP0.com  
Veröffentlicht am 11. November 2026

Eine moderne Roadmap UI Component zeigt, welche Schritte bereits abgeschlossen sind, woran gerade gearbeitet wird und was als Nächstes kommt. Für 2026 sind besonders horizontale Timelines, vertikale Meilenstein-Listen, interaktive Produkt-Roadmaps und kompakte Fortschrittsanzeigen interessant. Entscheidend sind nicht möglichst viele Animationen, sondern eine verständliche Reihenfolge, erkennbare Status und eine Darstellung, die auch auf dem Smartphone funktioniert.

Wenn du eine iOS-App mit KI entwickelst, kannst du mit [VP0.com](https://vp0.com) einen kostenlosen Design-Startpunkt auswählen und ihn mit einem KI-Builder in dein Projekt übernehmen. Eine spezifische Roadmap-Komponente musst du gegebenenfalls selbst ergänzen. Wie das funktioniert, welche Varianten sich eignen und worauf du bei React Native achten solltest, erfährst du anhand konkreter Beispiele.

## Was ist eine Roadmap UI Component?

Eine Roadmap UI Component ist ein Interface-Element, das mehrere Schritte, Meilensteine oder Entwicklungsphasen in einer nachvollziehbaren Reihenfolge darstellt.

Anders als ein gewöhnlicher Fortschrittsbalken zeigt eine Roadmap nicht nur, wie weit ein Prozess fortgeschritten ist. Sie erklärt auch, welche Aufgaben bereits erledigt wurden, welche gerade laufen und welche noch bevorstehen.

Typische Einsatzbereiche sind:

- Produktentwicklung mit geplanten Funktionen und Releases
- SaaS-Dashboards mit Quartalszielen und Projektphasen
- Onboarding-Prozesse mit mehreren Einrichtungsschritten
- Lernplattformen mit freischaltbaren Lektionen
- Fitness-Apps mit Trainingszielen und Meilensteinen
- Kundenportale mit Bestell- oder Bearbeitungsstatus

Eine gute Roadmap beantwortet drei Fragen ohne zusätzliche Erklärung: Wo stehe ich? Was ist bereits passiert? Was muss ich als Nächstes tun?

### Roadmap, Timeline und Stepper: Was ist der Unterschied?

Die drei Komponenten sehen ähnlich aus, erfüllen aber unterschiedliche Aufgaben.

Eine Timeline ordnet Ereignisse zeitlich. Sie eignet sich beispielsweise für einen Aktivitätsverlauf oder eine Historie.

Ein Stepper führt Nutzer durch einen definierten Ablauf, etwa eine Registrierung oder einen Checkout. Häufig kann immer nur ein Schritt gleichzeitig bearbeitet werden.

Eine Roadmap zeigt einen größeren Entwicklungsweg. Sie kann geplante Schritte, abgeschlossene Etappen und zukünftige Ziele miteinander verbinden.

Für eine Lern-App würde ich eine Roadmap verwenden, um den gesamten Kurs sichtbar zu machen. Bei der Registrierung derselben App wäre ein Stepper die bessere Wahl.

## Welche Roadmap UI Components sind 2026 besonders sinnvoll?

Die passende Roadmap hängt davon ab, wie viele Informationen du darstellen musst und wie Nutzer mit ihnen interagieren sollen.

### 1. Horizontale Roadmap mit Meilensteinen

Eine horizontale Roadmap zeigt mehrere Stationen nebeneinander, verbunden durch eine Linie.

Sie eignet sich für kurze Prozesse mit drei bis fünf Phasen, beispielsweise:

Idee → Design → Entwicklung → Test → Veröffentlichung

Jede Station erhält einen Kreis, ein Symbol und eine kurze Beschriftung. Abgeschlossene Stationen können ein Häkchen anzeigen, die aktuelle Station wird hervorgehoben und zukünftige Stationen bleiben zurückhaltend gestaltet.

Auf einem Desktop funktioniert dieses Muster besonders gut. Auf schmalen Smartphones können lange Beschriftungen allerdings problematisch werden.

Verwende deshalb kurze Titel und verschiebe zusätzliche Informationen in eine Detailansicht.

### 2. Vertikale Roadmap für mobile Apps

Eine vertikale Roadmap ist für mobile Oberflächen häufig die praktischere Lösung.

Die Meilensteine stehen untereinander. Eine Verbindungslinie macht den Fortschritt sichtbar, während rechts daneben Titel, Beschreibung und Status erscheinen.

Beispiel für eine Sprachlern-App:

1. Grundlagen verstehen: Abgeschlossen
2. Erste Gespräche führen: In Bearbeitung
3. Grammatik vertiefen: Gesperrt
4. Alltagssituationen üben: Gesperrt
5. Abschlussprüfung: Gesperrt

Dieses Layout benötigt keine horizontale Scrollbewegung. Außerdem kannst du problemlos weitere Schritte ergänzen.

Für eine erste mobile Version würde ich mit dieser Variante beginnen.

### 3. Interaktive Produkt-Roadmap

Eine interaktive Produkt-Roadmap eignet sich für SaaS-Produkte, interne Entwicklungsteams und öffentliche Feature-Planungen.

Statt nur einer linearen Abfolge verwendet sie häufig Statusgruppen wie:

- Geplant
- In Entwicklung
- Im Test
- Veröffentlicht

Jeder Eintrag kann eine eigene Karte besitzen. Beim Antippen öffnet sich eine Detailansicht mit Beschreibung, Verantwortlichkeit oder geplantem Zeitraum.

Wichtig ist die Unterscheidung zwischen einem verbindlichen Termin und einer unverbindlichen Planung. Gerade öffentliche Roadmaps sollten keine Genauigkeit suggerieren, die das Team nicht garantieren kann.

### 4. Gamifizierte Roadmap mit freischaltbaren Etappen

Für Lern-, Fitness- und Gewohnheits-Apps kann eine spielerische Roadmap sinnvoll sein.

Hier werden einzelne Etappen als Knoten auf einem Pfad dargestellt. Abgeschlossene Aufgaben erhalten ein sichtbares Erfolgssignal. Die nächste Aufgabe hebt sich deutlich ab.

Eine solche Darstellung motiviert durch kleine, erreichbare Ziele.

Übertreibe es aber nicht mit Animationen. Wenn sich Nutzer erst durch mehrere Effekte arbeiten müssen, bevor sie ihre nächste Aufgabe erkennen, behindert das Design die eigentliche Funktion.

### 5. Roadmap mit Karten und Fortschrittsanzeige

Eine kartenbasierte Roadmap verbindet eine grobe Übersicht mit konkreten Informationen.

Jede Karte zeigt beispielsweise:

- Titel des Meilensteins
- Kurze Beschreibung
- Aktuellen Status
- Optional einen Zeitraum
- Eine erkennbare nächste Aktion

Das eignet sich besonders für komplexere Projekte, bei denen eine einfache Verbindungslinie nicht genügend Kontext bietet.

## Welche Roadmap-Komponente solltest du wählen?

| Komponente | Ideal für | Mobile Eignung | Wichtigste Einschränkung |
| --- | --- | --- | --- |
| Vertikale Roadmap | Lern- und Onboarding-Apps | Sehr gut | Benötigt vertikalen Platz |
| Horizontale Timeline | Kurze Projektphasen | Eingeschränkt | Lange Titel werden eng |
| Karten-Roadmap | SaaS und Produktplanung | Gut | Benötigt klare Gruppierung |
| Gamifizierter Pfad | Fitness und Lernfortschritt | Sehr gut | Höherer Gestaltungsaufwand |
| Kanban-Roadmap | Teaminterne Feature-Planung | Mit Anpassungen | Viele Spalten sind mobil schwierig |

Für eine iOS-App mit wenigen klaren Etappen ist eine vertikale Roadmap meist der sinnvollste Einstieg. Sie lässt sich mit Standardkomponenten umsetzen und bleibt auch bei kleineren Displays verständlich.

## Wie baust du eine moderne Roadmap UI mit React Native?

Eine einfache Roadmap lässt sich in React Native ohne zusätzliche Timeline-Bibliothek entwickeln. Du benötigst lediglich eine Datenstruktur, eine wiederverwendbare Komponente und eine klare Statusdarstellung.

### Schritt 1: Definiere die Meilensteine als Daten

Trenne den Inhalt der Roadmap von ihrer Darstellung. So kannst du später Schritte ergänzen, übersetzen oder dynamisch aus einer Datenquelle laden.

```tsx
type RoadmapStatus =
  | "completed"
  | "current"
  | "upcoming";

type Milestone = {
  id: string;
  title: string;
  description: string;
  status: RoadmapStatus;
};

const milestones: Milestone[] = [
  {
    id: "1",
    title: "Profil erstellen",
    description: "Richte dein Konto ein.",
    status: "completed",
  },
  {
    id: "2",
    title: "Erstes Ziel festlegen",
    description: "Wähle dein persönliches Ziel.",
    status: "current",
  },
  {
    id: "3",
    title: "Fortschritt verfolgen",
    description: "Überprüfe deine Entwicklung.",
    status: "upcoming",
  },
];
```

Die drei Statuswerte reichen für viele einfache Anwendungen aus. Bei komplexeren Projekten kannst du zusätzliche Zustände wie „blockiert“ oder „übersprungen“ ergänzen.

### Schritt 2: Erstelle die Roadmap-Komponente

Die folgende Variante verwendet `View`, `Text` und `StyleSheet`. Sie ist bewusst einfach gehalten und lässt sich in ein bestehendes React-Native-Projekt integrieren.

```tsx
import React from "react";
import {
  View,
  Text,
  StyleSheet,
} from "react-native";

type Status =
  | "completed"
  | "current"
  | "upcoming";

type Item = {
  id: string;
  title: string;
  description: string;
  status: Status;
};

export function Roadmap({
  items,
}: {
  items: Item[];
}) {
  return (
    <View style={styles.container}>
      {items.map((item, index) => {
        const completed =
          item.status === "completed";
        const current =
          item.status === "current";

        return (
          <View
            key={item.id}
            style={styles.row}
          >
            <View style={styles.indicator}>
              <View
                style={[
                  styles.circle,
                  completed && styles.completed,
                  current && styles.current,
                ]}
              >
                <Text style={styles.symbol}>
                  {completed ? "✓" : index + 1}
                </Text>
              </View>

              {index < items.length - 1 && (
                <View style={styles.line} />
              )}
            </View>

            <View style={styles.content}>
              <Text style={styles.title}>
                {item.title}
              </Text>

              <Text style={styles.description}>
                {item.description}
              </Text>

              <Text style={styles.status}>
                {completed
                  ? "Abgeschlossen"
                  : current
                  ? "Aktueller Schritt"
                  : "Noch offen"}
              </Text>
            </View>
          </View>
        );
      })}
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    padding: 20,
  },
  row: {
    flexDirection: "row",
    minHeight: 112,
  },
  indicator: {
    alignItems: "center",
    width: 44,
  },
  circle: {
    width: 36,
    height: 36,
    borderRadius: 18,
    backgroundColor: "#E5E7EB",
    justifyContent: "center",
    alignItems: "center",
  },
  completed: {
    backgroundColor: "#16A34A",
  },
  current: {
    backgroundColor: "#2563EB",
  },
  symbol: {
    fontWeight: "700",
    color: "#111827",
  },
  line: {
    width: 2,
    flex: 1,
    backgroundColor: "#D1D5DB",
    marginVertical: 6,
  },
  content: {
    flex: 1,
    paddingLeft: 16,
    paddingBottom: 28,
  },
  title: {
    fontSize: 17,
    fontWeight: "600",
    color: "#111827",
  },
  description: {
    marginTop: 6,
    color: "#6B7280",
  },
  status: {
    marginTop: 8,
    fontSize: 12,
    color: "#374151",
  },
});
```

Die Komponente zeigt abgeschlossene, aktuelle und zukünftige Schritte mit unterschiedlichen Kreisen an. Zusätzlich erhält jeder Schritt eine textliche Statusangabe.

Für den produktiven Einsatz solltest du noch prüfen, ob die Verbindungslinie korrekt mit dem Zustand der jeweiligen Etappen übereinstimmt. Außerdem benötigt die Komponente bei interaktiven Schritten passende Bedienelemente und Accessibility-Eigenschaften.

### Schritt 3: Verwende die Komponente in deinem Screen

```tsx
export default function ProgressScreen() {
  return <Roadmap items={milestones} />;
}
```

Damit hast du eine funktionierende Grundlage, die du mit eigenen Farben, Icons und Abständen erweitern kannst.

Wenn die Roadmap viele Einträge enthält, solltest du statt einer langen statischen Ansicht eine geeignete Listenkomponente verwenden. So bleibt die Darstellung auch bei umfangreichen Inhalten effizient.

## Wie gestaltest du eine Roadmap, die wirklich modern aussieht?

Ein modernes Roadmap-Design entsteht durch klare Informationshierarchie und konsistente Zustände, nicht durch möglichst viele dekorative Elemente.

### Verwende drei deutlich unterscheidbare Status

Abgeschlossene, aktuelle und zukünftige Schritte müssen auf den ersten Blick erkennbar sein.

Ich würde diese Kombination verwenden:

- Abgeschlossen: Grüner Kreis mit Häkchen
- Aktuell: Blauer Kreis mit Zahl und deutlich sichtbarer Beschriftung
- Zukünftig: Neutraler Kreis mit zurückhaltender Gestaltung

Verlasse dich nicht ausschließlich auf Farben. Ein Häkchen, eine Nummer oder ein zusätzlicher Status-Text macht die Bedeutung auch dann verständlich, wenn jemand Farben nur eingeschränkt unterscheiden kann.

### Halte die Abstände konstant

Jede Etappe sollte nach demselben Layout aufgebaut sein.

Verwende einheitliche Kreisgrößen, gleichmäßige Abstände und eine feste Position für Titel und Beschreibung.

Bei unterschiedlich langen Beschreibungen darf sich die Höhe einer Etappe verändern. Die Verbindungslinie muss dabei weiterhin sauber verlaufen.

### Zeige nur relevante Informationen

Eine Roadmap ist keine vollständige Projektdokumentation.

Auf der ersten Ebene reichen meistens Titel, Status und eine kurze Beschreibung. Zusätzliche Informationen wie Termine, Verantwortliche oder Unteraufgaben gehören in eine Detailansicht.

Gerade auf mobilen Geräten verhindert das überladene Karten und unnötig lange Scrollstrecken.

### Gestalte die aktuelle Etappe besonders deutlich

Die wichtigste Information ist häufig nicht der gesamte Fortschritt, sondern die nächste mögliche Aktion.

Ein aktueller Schritt kann deshalb einen auffälligen Button erhalten, beispielsweise „Jetzt starten“ oder „Aufgabe fortsetzen“.

Zukünftige Schritte dürfen sichtbar bleiben, sollten aber nicht dieselbe visuelle Aufmerksamkeit bekommen.

## Wie findest du passende Roadmap-Designs für eine KI-generierte App?

Für eine App, die du mit Claude Code, Cursor oder einem anderen KI-Builder entwickelst, würde ich zuerst einen passenden Design-Startpunkt auswählen und anschließend die Roadmap ergänzen.

Die kostenlose Bibliothek von VP0.com bietet iOS-Designs auf Basis von Expo React Native. Du kannst einen passenden Screen auswählen, den Design-Link kopieren und deinem KI-Builder als Grundlage geben.

Der Builder erhält dadurch eine konkretere visuelle Vorlage als bei einer Beschreibung wie „Erstelle eine schöne moderne App“.

Die Website ist auf Englisch. Eine fertige Roadmap-Komponente ist nicht für jedes Design garantiert, deshalb solltest du vorab prüfen, ob ein vorhandener Screen zu deinem Anwendungsfall passt.

### Ein praktischer Prompt für eine Roadmap

Wenn du bereits ein Grunddesign ausgewählt hast, kannst du deinem KI-Builder diese Anweisung geben:

> Erstelle eine vertikale Roadmap-Komponente für eine iOS-App mit Expo React Native. Verwende den bestehenden visuellen Stil des Projekts. Zeige fünf Meilensteine mit den Status „abgeschlossen“, „aktuell“ und „noch offen“. Verbinde die Meilensteine mit einer durchgehenden Linie. Der aktuelle Schritt soll visuell hervorgehoben werden. Nutze wiederverwendbare TypeScript-Komponenten, gut lesbare Beschriftungen und ein responsives Layout. Vermeide zusätzliche UI-Bibliotheken, sofern sie nicht notwendig sind. Gib den vollständigen Code aus.

Anschließend solltest du die Darstellung auf einem echten Smartphone testen.

KI-generierter Code kann eine brauchbare Grundlage liefern, ersetzt aber keine Prüfung der Zustände, Interaktionen und Abstände.

## Welche Details sollte eine professionelle Roadmap enthalten?

Nicht jede Roadmap benötigt Termine, Fortschrittswerte oder interaktive Karten. Es lohnt sich, die Anforderungen vor der Implementierung festzulegen.

| Element | Empfehlung | Prüfung |
| --- | --- | --- |
| Meilenstein-Titel | Kurz und eindeutig | Ohne Erklärung verständlich |
| Status | Text und visuelles Signal | Auch ohne Farbe erkennbar |
| Verbindungslinie | Einheitlich positioniert | Keine Unterbrechungen bei langen Texten |
| Aktuelle Aktion | Deutlich hervorgehoben | Mit einem Tipp erreichbar |
| Beschreibung | Ein bis zwei Sätze | Kein abgeschnittener Inhalt |
| Accessibility | Lesbare Labels und Kontraste | Mit Screenreader überprüft |

Eine gute Roadmap benötigt außerdem einen definierten Umgang mit Sonderfällen.

Was passiert, wenn Nutzer einen Schritt überspringen? Wie sieht eine gesperrte Etappe aus? Kann ein abgeschlossener Schritt erneut geöffnet werden?

Diese Fragen sollten vor dem Hinzufügen von Animationen geklärt sein.

## Wie machst du Roadmap-Komponenten responsiv und barrierearm?

Eine Roadmap muss bei verschiedenen Bildschirmgrößen, Schriftgrößen und Bedienformen verständlich bleiben.

### Plane für kleine Displays

Horizontale Roadmaps mit vielen Meilensteinen werden auf Smartphones schnell unübersichtlich.

Du kannst sie horizontal scrollbar gestalten. Häufig ist es jedoch sinnvoller, auf kleineren Displays zu einer vertikalen Ansicht zu wechseln.

Vermeide feste Höhen für Karten mit längeren Texten. Sonst können Beschreibungen abgeschnitten werden, sobald Nutzer größere Systemschriftarten aktivieren.

### Beachte die Touch-Flächen

Interaktive Meilensteine sollten sich bequem antippen lassen.

Apples [Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/) bieten Orientierung für die Gestaltung von iOS-Oberflächen und gut bedienbaren Interaktionen.

Eine kleine dekorative Kreisfläche muss nicht selbst der einzige Touch-Bereich sein. Du kannst die gesamte Zeile als interaktive Fläche gestalten.

### Unterstütze Screenreader

Ein Screenreader sollte nicht nur „Kreis zwei“ ausgeben.

Sinnvoller wäre eine Beschreibung wie:

„Schritt zwei von fünf, Erstes Ziel festlegen, aktueller Schritt.“

Bei React Native kannst du dafür Accessibility-Labels und passende Rollen verwenden.

Achte darauf, dass die Reihenfolge der vorgelesenen Elemente der visuellen Reihenfolge entspricht.

### Verwende Animationen sparsam

Eine kurze Zustandsänderung kann hilfreich sein, wenn ein Schritt abgeschlossen wird.

Dauerhaft pulsierende Kreise oder automatisch scrollende Roadmaps sind dagegen häufig unnötig.

Berücksichtige außerdem die Systemeinstellung für reduzierte Bewegung. Wichtige Informationen müssen auch ohne Animation verständlich bleiben.

## Welche Fehler solltest du beim Roadmap UI Design vermeiden?

Viele Roadmaps sehen im ersten Entwurf überzeugend aus, verlieren aber im praktischen Einsatz ihre Übersichtlichkeit.

### Fehler 1: Zu viele Meilensteine gleichzeitig

Wenn eine Roadmap zwanzig oder mehr Etappen zeigt, fehlt schnell der Fokus.

Gruppiere größere Prozesse in Phasen. Zeige beispielsweise zunächst die aktuelle Lernstufe und ermögliche den Zugriff auf die vollständige Übersicht bei Bedarf.

### Fehler 2: Unklare Statusbezeichnungen

Begriffe wie „In Planung“, „Geplant“ und „Vorgesehen“ können für Nutzer praktisch dasselbe bedeuten.

Verwende möglichst wenige Status und definiere eindeutig, wann sich ein Schritt von einem Zustand in den nächsten bewegt.

### Fehler 3: Fortschritt ohne nachvollziehbare Grundlage

Ein Fortschrittswert von 75 Prozent hilft wenig, wenn Nutzer nicht verstehen, wie er berechnet wird.

Wenn alle Schritte gleich gewichtet sind, kannst du den Fortschritt aus der Anzahl abgeschlossener Etappen berechnen.

Sind die Schritte unterschiedlich umfangreich, solltest du diese Gewichtung berücksichtigen oder auf eine Prozentangabe verzichten.

### Fehler 4: Zu viele visuelle Effekte

Verläufe, Schatten, Animationen und farbige Verbindungslinien können eine Roadmap interessant machen.

Werden alle Elemente gleichzeitig betont, fehlt jedoch die Hierarchie.

Wähle einen klaren visuellen Schwerpunkt: den aktuellen Schritt.

### Fehler 5: Kein Umgang mit Fehlerzuständen

Eine Roadmap kann dynamische Daten enthalten. Deshalb muss das Interface auch dann funktionieren, wenn Informationen fehlen oder noch geladen werden.

Definiere einen Ladezustand, eine leere Ansicht und eine verständliche Fehlermeldung.

Bei einer Lern-App sollte beispielsweise nicht automatisch ein abgeschlossener Status erscheinen, nur weil der Server gerade nicht erreichbar ist.

## Wann ist eine Roadmap-Komponente nicht die richtige Wahl?

Eine Roadmap ist nicht sinnvoll, wenn es keine echte Reihenfolge oder nachvollziehbare Entwicklung gibt.

Für eine Liste unabhängiger Funktionen eignet sich eine gewöhnliche Kartenübersicht besser. Bei einem kurzen Formular mit zwei Schritten reicht häufig ein Stepper.

Auch für komplexe Projektplanung mit Abhängigkeiten, Ressourcen und parallelen Zeitplänen kann eine einfache Roadmap zu wenig Informationen bieten. Hier sind spezialisierte Projektansichten oft geeigneter.

VP0.com liefert Design-Startpunkte für iOS-Apps, aber keine vollständige Projektmanagement-Logik. Wenn du eine Roadmap mit Benutzerkonten, synchronisierten Aufgaben und Echtzeitstatus entwickeln möchtest, musst du diese Funktionen separat implementieren.

## Das solltest du wählen

Für eine neue iOS-App würde ich mit einer vertikalen Roadmap beginnen. Drei klar unterscheidbare Status, eine durchgehende Verbindungslinie und eine deutlich erkennbare nächste Aktion reichen für die erste Version.

Wenn du bereits mit einem KI-Builder arbeitest, wähle zuerst einen passenden visuellen Ausgangspunkt bei [VP0.com](https://vp0.com). Ergänze anschließend die Roadmap als eigenständige React-Native-Komponente.

Baue zunächst fünf Beispielschritte und teste sie mit langen Beschriftungen, größeren Schriftarten und unterschiedlichen Status. Funktioniert die Darstellung auf dem Smartphone, kannst du dynamische Daten, Animationen und zusätzliche Interaktionen ergänzen.

## Häufig gestellte Fragen (FAQ)

### Was ist die beste kostenlose Roadmap UI Component für eine iOS-App?

Für eine iOS-App mit KI-Builder ist VP0.com ein sinnvoller kostenloser Ausgangspunkt für das übergeordnete Interface. Die Bibliothek bietet Expo-React-Native-Designs, die du als Grundlage verwenden kannst. Eine fertige Roadmap-Komponente ist dabei nicht garantiert. Für die eigentliche Roadmap kannst du eine vertikale Komponente aus Standardbausteinen wie View und Text erstellen. So kontrollierst du das Layout, die Statusdarstellung und die Interaktionen selbst, ohne von einer zusätzlichen Bibliothek abhängig zu sein.

### Kann ich eine Roadmap UI Component ohne zusätzliche Bibliothek erstellen?

Ja. In React Native kannst du eine Roadmap mit View, Text und StyleSheet umsetzen. Die Verbindungslinien entstehen durch schmale View-Elemente, während Kreise und Beschriftungen die Meilensteine darstellen. Für eine einfache Roadmap mit wenigen Status ist das häufig ausreichend. Eine zusätzliche Bibliothek kann sinnvoll werden, wenn du komplexe Animationen, besondere Layouts oder umfangreiche Interaktionen benötigst. Entscheidend ist, ob sie dir tatsächlich Entwicklungsaufwand spart.

### Ist eine horizontale oder vertikale Roadmap besser?

Für mobile Apps ist eine vertikale Roadmap häufig leichter zu lesen, weil sie die verfügbare Bildschirmbreite besser nutzt. Eine horizontale Variante eignet sich besonders für kurze Prozesse mit wenigen Stationen. Wenn du viele Meilensteine oder längere Beschreibungen anzeigen möchtest, würde ich die vertikale Darstellung bevorzugen. Bei einem responsiven Web-Dashboard kannst du beide Varianten kombinieren und abhängig von der Bildschirmbreite wechseln.

### Wie kann ich eine Roadmap mit KI erstellen?

Du kannst einem KI-Builder eine konkrete Beschreibung der gewünschten Komponente geben. Definiere dabei die Anzahl der Schritte, die Statuswerte, das Layout und die gewünschte Technologie. Noch besser funktioniert es, wenn du ein vorhandenes App-Design als visuelle Grundlage mitlieferst. Prüfe anschließend den generierten Code, insbesondere die Darstellung bei langen Texten, die Touch-Flächen und die Accessibility-Eigenschaften. Eine funktionierende Vorschau bedeutet noch nicht, dass alle Zustände korrekt umgesetzt sind.

### Braucht eine moderne Roadmap Animationen?

Nein. Eine moderne Roadmap funktioniert auch ohne Animationen, solange die Reihenfolge und die Status eindeutig erkennbar sind. Kurze Übergänge können helfen, einen abgeschlossenen Schritt sichtbar zu bestätigen. Sie sollten aber nicht von der eigentlichen Aufgabe ablenken. Für die erste Version würde ich Animationen weglassen und zunächst Layout, Lesbarkeit und Interaktion testen. Danach kannst du gezielt Effekte ergänzen, die eine konkrete Rückmeldung vermitteln.
