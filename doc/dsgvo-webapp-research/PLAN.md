# DSGVO Interaktiv — Gesamtplan

> Interaktive Lern-Webseite zu DSGVO-Grundlagen
> React + TypeScript | GitHub Pages | "Erleben vor Lesen"

---

## 1. Konzept & Pädagogischer Ansatz

### Grundidee

Die Webseite ersetzt Aufgabe 1 des Datenschutz-Arbeitsblatts. Schüler erarbeiten sich DSGVO-Grundlagen **interaktiv**, bevor sie in Aufgabe 2+3 den Transfer auf NHPlus selbst leisten.

### Leitprinzip: "Frage → Do → Show → Tell"

Jedes Kapitel folgt einer vierstufigen Sequenz:

1. **Frage**: Eine konkrete Orientierungsfrage gibt dem Kapitel Richtung — der Schüler weiß, worauf er achten soll
2. **Do**: Der Schüler interagiert mit einem Widget — ohne vorherige Erklärung
3. **Show**: Visuelles Feedback zeigt, was richtig/falsch war und warum
4. **Tell**: Erst jetzt erscheint der erklärende Text inkl. Gesetzestext-Auszug

Dieses Pattern stammt aus dem "Explorable Explanations"-Ansatz (Nicky Case) und nutzt den kognitiven Effekt, dass selbst entdeckte Erkenntnisse besser haften als gelesene. Die vorangestellte Frage verhindert ungerichtetes Ausprobieren und gibt dem "Do"-Schritt ein klares Ziel (vgl. Cognitive Load Theory — Sweller).

### Kapitelstruktur: maximal 2 Kern-Widgets

Jedes Kapitel enthält maximal **zwei Kern-Widgets** mit unterschiedlichen Interaktionsmodi. Weitere Widgets stehen als optionale **Vertiefung** bereit, die visuell abgesetzt ist ("Wenn du tiefer einsteigen willst..."). So wird kognitive Überlastung vermieden — jedes Widget erfordert Einarbeitung in eine neue Interaktionsform *und* neuen Inhalt gleichzeitig.

### Dreistufiges Feedback bei Grenzfällen

Die DSGVO hat Graubereiche (z.B. IP-Adresse, berechtigtes Interesse). Statt binärem Richtig/Falsch gibt es in allen Widgets drei Feedback-Stufen:

- **Richtig** — grüner Glow + Bestätigung
- **Diskutabel** — Amber-Highlight + Erklärung, warum die Zuordnung strittig ist (z.B. EuGH-Urteil zur IP-Adresse)
- **Falsch** — sanftes Schütteln + Korrektur-Erklärung

### Adaptiver Schwierigkeitsgrad

Widgets mit progressivem Schwierigkeitsgrad (Sortier-Spiel, Szenario-Player) passen sich dem Leistungsniveau an: Wer die ersten Aufgaben sicher löst, bekommt schneller Grenzfälle. Wer Fehler macht, bekommt zusätzliche einfachere Aufgaben zur Festigung. Der vorhandene Zustand-Store trackt die Fehlerrate und steuert die Kartenauswahl.

### Kein NHPlus-Bezug

Die Webseite ist **bewusst domain-unabhängig**. Beispiele kommen aus Fitness-Apps, Online-Shops, Schulen, Arztpraxen und Social Media. Der Transfer auf NHPlus ist die eigentliche Denkleistung der Schüler (Aufgabe 2+3).

---

## 2. Kapitelstruktur (6 Kapitel)

### Kapitel 0: "Was weiß die App über dich?"
**Typ**: Emotionaler Einstieg / Hook
**DSGVO-Bezug**: Motivation für alles Folgende
**Dauer**: ~5 Minuten

**Orientierungsfrage**: *"Was kann ein Unternehmen allein aus deinem Profil über dich herausfinden?"*

**Widget — Selbst-Experiment:**
- Schüler füllt ein fiktives Profil aus (Name, Alter, Interessen, Wohnort — alles erfunden)
- Die App zeigt schrittweise, was ein Unternehmen daraus ableiten könnte: Kaufkraft, politische Tendenz, Gesundheitsrisiko
- Dramatische Reveal-Animationen: Karten drehen um, Zahlen zählen hoch
- **Transparenz-Einschub** nach dem Reveal: *"Diese Ableitungen sind vereinfacht — aber echte Unternehmen nutzen tausende Datenpunkte und liegen deutlich genauer."* — bewahrt den Effekt und bleibt intellektuell ehrlich
- Abschluss: **"Deshalb gibt es die DSGVO."** → Überleitung zu Kapitel 1

**Technisch**: Multi-Step-Formular + Motion Page-Transitions + deterministische Ableitungsregeln (kein echtes ML)

---

### Kapitel 1: "Persönlich, sensibel, anonym"
**Typ**: Kategorisierung / Klassifikation
**DSGVO-Bezug**: Art. 4 (Definitionen), Art. 9 (Besondere Kategorien)
**Dauer**: ~10 Minuten

**Orientierungsfrage**: *"Warum ist eine IP-Adresse ein personenbezogenes Datum — und deine Lieblingspizza nicht?"*

**Widget A — Daten-Sortier-Spiel (Drag & Drop):**
- Karten mit Datenbeispielen erscheinen einzeln (Name, IP-Adresse, Blutgruppe, Lieblingspizza, Fingerabdruck, E-Mail, Parteimitgliedschaft...)
- 3 Drop-Zones: "Personenbezogen" | "Besondere Kategorie (Art. 9)" | "Kein Personenbezug"
- **Adaptiver Schwierigkeitsgrad**: Wer die ersten 5 Karten richtig sortiert, bekommt direkt Grenzfälle. Wer Fehler macht, bekommt zusätzliche eindeutige Karten zur Festigung
- **Dreistufiges Feedback**: Richtig → grüner Snap; Diskutabel (z.B. IP-Adresse) → Amber + Erklärung mit EuGH-Urteil; Falsch → sanftes Zurückgleiten + Korrektur
- **Touch-Fallback**: Auf Touch-Geräten Tap-to-Assign statt Drag & Drop (Karte antippen, dann Kategorie antippen)

**Widget B — Gesetzestext-Highlighter:**
- Art. 9 Abs. 1 wird als Originaltext angezeigt
- Aufgabe: "Markiere alle Kategorien besonders geschützter Daten"
- Text-Selektion über Web Selection API, Ziel-Bereiche vorher definiert
- Fortschrittsanzeige: "7 von 8 Kategorien gefunden"

**Tell-Phase**: Nach den Widgets: Zusammenfassung mit Erklärtexten + Tabelle der Datenkategorien

**Technisch**: @dnd-kit/react + Motion Stagger-Animationen + Custom Selection Handler + Touch-Sensor-Fallback

---

### Kapitel 2: "Darf ich das?"
**Typ**: Szenario-Entscheidungen
**DSGVO-Bezug**: Art. 5 (Grundsätze), Art. 6 (Rechtsgrundlagen)
**Dauer**: ~12 Minuten

**Orientierungsfrage**: *"Wann darf ein Unternehmen deine Daten verarbeiten — und wann auf keinen Fall?"*

**Widget A — Rechtsgrundlagen-Finder ("Place Your Bets"):**
- Szenarien werden präsentiert: "Ein Online-Shop schickt dir Werbung per Post"
- Schüler tippt erst: "Ist das erlaubt? Auf welcher Grundlage?"
- Dann Auflösung mit der richtigen Rechtsgrundlage aus Art. 6
- Bei "Berechtigtes Interesse" (Art. 6 Abs. 1 f): zusätzliche Interessenabwägung durchführen
- **Adaptiv**: Wer Einwilligung und Vertrag sicher zuordnet, bekommt schneller die schwierigen Fälle (öffentliches Interesse, berechtigtes Interesse)

**Widget B — Einwilligungs-Builder:**
- Split-Screen: Links Baukasten, rechts Live-Preview eines Cookie-Banners
- Bausteine: Zweckangabe, Widerrufshinweis, Verständlichkeit, Freiwilligkeit, Dark-Pattern-Erkennung
- Schüler baut eine DSGVO-konforme Einwilligung zusammen
- Validierung gegen Art. 7 Kriterien mit Grün/Rot/Amber-Indikatoren

**Vertiefung (optional) — Formular-Redesign (Datenminimierung):**
- Visuell abgesetzt: *"Wenn du tiefer einsteigen willst: Datenminimierung in der Praxis"*
- Überladenes Registrierungsformular für einen Newsletter (15 Felder)
- Schüler streicht überflüssige Felder (Familienstand, Geburtsdatum, Telefon...)
- Ziel: Minimales Formular, das den Grundsatz der Datenminimierung erfüllt
- Feedback: "Dieses Feld ist für einen Newsletter nicht erforderlich"

**Tell-Phase**: Die 6 Grundsätze (Art. 5) als animierte Übersicht + Art. 6 Rechtsgrundlagen-Tabelle

**Technisch**: State Machine für Szenarien + Motion AnimatePresence + Controlled Components

---

### Kapitel 3: "Deine Daten, deine Rechte"
**Typ**: Rollenspiel-Simulation
**DSGVO-Bezug**: Art. 12–22 (Betroffenenrechte)
**Dauer**: ~12 Minuten

**Orientierungsfrage**: *"Was kannst du tun, wenn ein Unternehmen Daten über dich hat, die du löschen willst?"*

**Widget A — Rechte-Simulator (Rollenspiel):**
- Schüler schlüpft in die Rolle einer betroffenen Person
- Szenarien:
  - "Du bekommst Spam von einem Unternehmen, bei dem du nie eingekauft hast"
  - "Dein Kreditantrag wurde automatisch abgelehnt — ohne Begründung"
  - "Du willst deinen Social-Media-Account komplett löschen"
  - "Bei deiner Krankenkasse ist eine falsche Diagnose gespeichert"
- Zu jeder Situation: Auswahl aus den Betroffenenrechten
- Entscheidungsbaum mit animierten Verzweigungen

**Widget B — Löschungs-Dilemma:**
- Perspektivwechsel: Löschanfragen landen im "Posteingang" des Schülers (der jetzt die Unternehmens-Perspektive einnimmt)
- Entscheidung: Löschen / Nicht löschen (+ Begründung)
- **Dreistufiges Feedback**: Richtig gelöscht / Diskutabel (Grauzone bei Aufbewahrungspflichten) / Falsch entschieden
- Spannungsfeld: Löschrecht vs. Aufbewahrungspflichten (Steuerrecht, 10 Jahre Rechnungen)

**Vertiefung (optional) — Betroffenenrechte-Kompass:**
- Visuell abgesetzt: *"Wenn du tiefer einsteigen willst: Finde das passende Recht"*
- Interaktives Entscheidungstool: "Was ist dein Problem?"
- Fragen führen zum passenden Recht + Artikel
- Am Ende: Muster-Formulierung eines Auskunftsersuchens

**Tell-Phase**: Übersicht aller Rechte mit Art.-Nummern + Fristen (1 Monat)

**Technisch**: useReducer State Machine + Motion Szenen-Übergänge + Entscheidungsbaum-Visualisierung

---

### Kapitel 4: "Schutz eingebaut"
**Typ**: Sandbox / Baukasten
**DSGVO-Bezug**: Art. 25 (Privacy by Design/Default), Art. 32 (TOMs)
**Dauer**: ~12 Minuten

**Orientierungsfrage**: *"Wie baust du Datenschutz in ein System ein, statt ihn nachträglich draufzukleben?"*

**Widget A — Privacy-by-Design-Baukasten:**
- Links: Vereinfachte System-Architektur (Frontend → Backend → Datenbank → API → Drittanbieter)
- Rechts: Werkzeugkasten mit Schutzmaßnahmen (Verschlüsselung, Pseudonymisierung, Zugriffskontrollen, Logging, Datensparsamkeit, Backups)
- Schüler zieht Maßnahmen per Drag & Drop auf die passenden Architektur-Elemente
- Visuelles "Schutzschild" erscheint bei korrekter Platzierung
- **Dreistufiges Feedback**: Richtig platziert / Sinnvoll aber nicht optimal (z.B. Verschlüsselung am falschen Layer) / Falsch
- Score: "Wie gut ist das System geschützt?" — zu wenig = Lücke, zu viel = unverhältnismäßig
- **Touch-Fallback**: Tap-to-Select statt Drag auf Touch-Geräten

**Widget B — App-Einstellungs-Audit (Privacy by Default):**
- Screenshots fiktiver App-Einstellungsseiten (Social Media, Fitness-App, Messenger)
- Schüler bewertet: Welche Voreinstellungen sind DSGVO-konform?
- Toggle-Switches zum "Reparieren" der Einstellungen
- Feedback pro Einstellung mit Art. 25 Abs. 2 Bezug

**Vertiefung (optional) — TOM-Konfigurator:**
- Visuell abgesetzt: *"Wenn du tiefer einsteigen willst: TOMs für eine Arztpraxis zusammenstellen"*
- Konkretes Szenario: "Arztpraxis mit 3 Ärzten und einer Sprechstundenhilfe"
- Baukasten mit technischen und organisatorischen Maßnahmen
- Schüler stellt passende TOMs zusammen und erhält Risikobewertung
- Feedback: Zu wenig = Datenschutzlücke, zu viel = unverhältnismäßiger Aufwand
- Verbindung zwischen physischen und digitalen Maßnahmen (Clean-Desk-Policy, Besucherregelungen neben Verschlüsselung, Zugriffskontrollen)

**Tell-Phase**: Art. 25 (Privacy by Design + Default) + Art. 32 (TOMs, 4 Schutzziele)

**Technisch**: @dnd-kit + SVG-Architektur-Diagramm + Motion Layout-Animationen + Touch-Sensor-Fallback

---

### Kapitel 5: "Von der Erhebung bis zur Löschung"
**Typ**: Zusammenfassung & Transfer-Vorbereitung
**DSGVO-Bezug**: Alle Artikel verknüpft
**Dauer**: ~12 Minuten

**Orientierungsfrage**: *"Welche DSGVO-Regeln greifen in jeder Phase eines Daten-Lebenszyklus?"*

**Widget A — Daten-Lebenszyklus-Timeline:**
- Horizontale, scroll-gesteuerte Timeline
- 5 Phasen: Erhebung → Verarbeitung → Speicherung → Weitergabe → Löschung
- Jede Phase: animierte Partikel stellen Datenfluss dar
- In jeder Phase: Mini-Quiz ("Welche Rechtsgrundlage brauche ich hier?" / "Welches Betroffenenrecht greift?")
- Verknüpft Wissen aus allen vorherigen Kapiteln
- **Artikel-Vernetzung**: Am Rand ein "Beziehungsdiagramm", das zeigt, wie die DSGVO-Artikel zusammenhängen (Art. 5 als Klammer → Art. 6 konkretisiert 5a → Art. 32 konkretisiert 5f)

**Widget B — Transfer-Check:**
- **Aktiver Transfer** statt passiver Text-Screen
- Kurzes Szenario: Eine vereinfachte "Schul-App" wird beschrieben (keine NHPlus-Details, aber ein ähnlicher Kontext)
- Der Schüler identifiziert 3-4 Datenschutzverstöße in der Beschreibung
- Zu jedem Verstoß: Zuordnung des passenden DSGVO-Artikels
- **Dreistufiges Feedback**: Richtig / Teilweise richtig (richtiger Artikel, aber falscher Absatz) / Falsch
- Abschluss: *"Du kannst jetzt Datenschutzverstöße erkennen und den passenden Artikeln zuordnen. Dein nächster Schritt: Analysiere NHPlus."*

**Abschluss-Zusammenfassung:**
- Personalisiertes Recap: "Du hast gelernt, dass..."
- Basierend auf den tatsächlichen Interaktionen/Fehlern des Schülers
- Kein Score — inhaltliches Feedback
- Checkliste der gelernten Konzepte als druckbares "Werkzeug" für AB02, Aufgabe 2

**Technisch**: Motion useScroll + react-scrollama + Partikel-Animation + Zustand für personalisiertes Recap

---

## 3. Tech-Stack

| Bereich | Technologie | Begründung |
|---|---|---|
| Build | **Vite 6 + React 19 + TypeScript** | De-facto-Standard, blitzschnell, triviales GH Pages Setup |
| Routing | **react-router-dom 7 (HashRouter)** | Zuverlässigste Lösung für GitHub Pages |
| Styling | **Tailwind CSS 4 + shadcn/ui (selektiv)** | Schnell, konsistent, accessible Basis-Komponenten |
| State | **Zustand 5 + persist-Middleware** | localStorage-Persistierung für Lernfortschritt, ~1.2 KB |
| Animation | **Motion 12 (framer-motion)** | Spring-Physik, Layout-Animationen, Gesture-Support |
| Drag & Drop | **@dnd-kit** | Accessibility, Keyboard-Support, modular |
| Visualisierung | **visx** (für Datenfluss-Diagramm) | Tree-shakable, maximale Kontrolle |
| Scroll | **Motion useScroll + react-scrollama** | Kapitel-Storytelling + scroll-verknüpfte Animationen |

### Bundle-Budget

| Chunk | Limit |
|---|---|
| Initial (Shell + Navigation) | < 150 KB gzipped |
| Pro Kapitel | < 80 KB gzipped |
| Gesamt (alles geladen) | < 300 KB gzipped |

---

## 4. Design

### Ästhetik
Modern, clean, dunkel — wie ein SaaS-Produkt, nicht wie ein Schulportal.
Referenzen: Linear.app, Vercel.com, Laws of UX.

### Farbschema (Dark-First)

```
Hintergrund:      #0A0A0B
Surface:          #141416
Surface-Elevated: #1E1E22
Border:           #2A2A30
Text-Primary:     #EDEDEF
Text-Secondary:   #8B8B96
Akzent-Primär:    #6C63FF (Indigo — seriös, modern)
Akzent-Sekundär:  #22D3EE (Cyan — für Datenfluss-Visuals)
Erfolg:           #34D399
Fehler:           #F87171
```

Light Mode als Alternative verfügbar (Toggle im Header).

### Typografie

- **Überschriften + Body**: Inter (Variable Font)
- **Gesetzestexte**: JetBrains Mono (Monospace — hebt sich visuell ab)
- Body: 16px/1.7, Semi-Bold (600) für Überschriften

### Gamification — was NICHT

- Keine Punkte, XP, Sterne, Badges, Leaderboards, Timer-Druck
- Zielgruppe ist 16-17 Jahre (11. Klasse) — das wirkt infantil

### Gamification — was stattdessen

- **Satisfying Animationen** als primärer Belohnungsmechanismus
- **Kapitel-Karte** (Metro-Map-Stil): Fortschritt als verbundene Knoten
- **Visueller Zustandswechsel** bei abgeschlossenen Kapiteln (Grau → Gefüllt + Spring-Animation)
- **Inhaltliches Feedback** statt Scores ("Du hast gelernt, dass...")
- **Unlock-Mechanik** für fortgeschrittene Widgets (aber kein künstliches Gating)

---

## 5. Projektstruktur

```
dsgvo-interaktiv/
├── .github/workflows/deploy.yml
├── public/
│   └── favicon.svg
├── src/
│   ├── app/
│   │   ├── App.tsx
│   │   └── routes.tsx              # Lazy imports pro Kapitel
│   ├── chapters/
│   │   ├── 0-hook/                 # "Was weiß die App über dich?"
│   │   ├── 1-kategorien/           # "Persönlich, sensibel, anonym"
│   │   ├── 2-rechtsgrundlagen/     # "Darf ich das?"
│   │   ├── 3-betroffenenrechte/    # "Deine Daten, deine Rechte"
│   │   ├── 4-schutz/              # "Schutz eingebaut"
│   │   ├── 5-lebenszyklus/        # "Von der Erhebung bis zur Löschung"
│   │   └── _shared/
│   │       └── chapter-layout.tsx
│   ├── components/
│   │   ├── ui/                     # shadcn/ui (Button, Dialog, Tooltip)
│   │   ├── widgets/                # Wiederverwendbare Lern-Widgets
│   │   │   ├── drag-sort-game.tsx   # Kap. 1 + 4 (mit Touch-Fallback)
│   │   │   ├── text-highlighter.tsx # Kap. 1
│   │   │   ├── scenario-player.tsx  # Kap. 2 + 3 (mit adaptivem Schwierigkeitsgrad)
│   │   │   ├── consent-builder.tsx  # Kap. 2
│   │   │   ├── form-redesigner.tsx  # Kap. 2 (Vertiefung)
│   │   │   ├── architecture-sandbox.tsx # Kap. 4 (mit Touch-Fallback)
│   │   │   ├── settings-audit.tsx   # Kap. 4
│   │   │   ├── tom-configurator.tsx # Kap. 4 (Vertiefung)
│   │   │   ├── timeline-scroll.tsx  # Kap. 5
│   │   │   └── transfer-check.tsx   # Kap. 5
│   │   ├── navigation/
│   │   └── layout/
│   ├── content/
│   │   ├── chapters.json           # Kapitel-Metadaten
│   │   ├── scenarios.json          # Szenarien für Rechte-Simulator etc.
│   │   ├── data-cards.json         # Datenkarten für Sortier-Spiel
│   │   └── legal-texts.json        # DSGVO-Auszüge mit Markierungszonen
│   ├── stores/
│   │   └── learning-store.ts       # Zustand + persist
│   ├── hooks/
│   ├── lib/
│   ├── styles/globals.css
│   └── main.tsx
├── vite.config.ts
├── package.json
└── tsconfig.json
```

---

## 6. GitHub Pages Deployment

- GitHub Actions Workflow: Build bei Push auf `main`, Deploy via `actions/deploy-pages@v4`
- SPA-Routing: `index.html` wird nach `404.html` kopiert
- Base-Path: `base: '/REPO-NAME/'` in `vite.config.ts`
- Repo: Eigenes Repository (nicht im NHPlus-Repo)

---

## 7. Accessibility

- **Reduced Motion**: `useReducedMotion()` Hook — alle Animationen respektieren `prefers-reduced-motion`
- **Keyboard-DnD**: @dnd-kit liefert Enter/Space/Pfeiltasten/Escape out of the box
- **Screen-Reader**: ARIA-Labels, `aria-live="polite"` für dynamische Ergebnisse, deutsche Announcements
- **Fokus-Management**: Nach Kapitelwechsel Fokus auf `<main>`
- **Kontrast**: WCAG AA für alle Text/Hintergrund-Kombinationen

---

## 8. Implementierungsreihenfolge

### Phase 1: Grundgerüst
- [ ] Vite + React + TypeScript Projekt aufsetzen
- [ ] Tailwind + shadcn/ui konfigurieren
- [ ] Routing (HashRouter) + Kapitel-Navigation
- [ ] Zustand Store mit persist
- [ ] GitHub Actions Deploy-Workflow
- [ ] Dark/Light Mode Toggle
- [ ] Kapitel-Karte (Metro-Map Navigation)

### Phase 2: Kern-Widgets
- [ ] **Drag-Sort-Game** (wiederverwendbar) — Kap. 1+4, inkl. Touch-Fallback + adaptiver Schwierigkeit
- [ ] **Scenario-Player** (wiederverwendbar) — Kap. 2+3, inkl. adaptiver Schwierigkeit
- [ ] **Text-Highlighter** — Kap. 1
- [ ] **Dreistufiges Feedback-System** — Richtig/Diskutabel/Falsch als wiederverwendbare Komponente

### Phase 3: Kapitel implementieren (in Reihenfolge)
- [ ] Kapitel 0: Hook ("Was weiß die App?") — Selbst-Experiment + Transparenz-Einschub
- [ ] Kapitel 1: Daten-Kategorien — Sortier-Spiel + Highlighter
- [ ] Kapitel 2: Rechtsgrundlagen — Szenarien + Einwilligungs-Builder | Vertiefung: Formular-Redesign
- [ ] Kapitel 3: Betroffenenrechte — Rechte-Simulator + Löschungs-Dilemma | Vertiefung: Kompass
- [ ] Kapitel 4: Schutz — Privacy-Baukasten + Einstellungs-Audit | Vertiefung: TOM-Konfigurator
- [ ] Kapitel 5: Lebenszyklus — Timeline + Transfer-Check + Artikel-Vernetzungsdiagramm

### Phase 4: Polish
- [ ] Animationen feintunen (Spring-Parameter, Stagger-Timing)
- [ ] Personalisiertes Recap am Ende
- [ ] Touch-Fallback für alle DnD-Widgets testen (Tablet + Smartphone)
- [ ] Accessibility-Audit
- [ ] Performance-Check (Bundle-Size, Lighthouse)
- [ ] Responsive Design (Tablet + Mobile)
- [ ] Offline-Fähigkeit via `vite-plugin-pwa` (Service Worker für Schulen mit instabilem WLAN)

---

## 9. Content-Quellen (verifiziert)

| Artikel | Quelle |
|---|---|
| Art. 5 (Grundsätze) | dsgvo-gesetz.de, dejure.org |
| Art. 6 (Rechtsgrundlagen) | dsgvo-gesetz.de |
| Art. 9 (Besondere Kategorien) | dsgvo-gesetz.de, BfDI |
| Art. 12-22 (Betroffenenrechte) | dsgvo-gesetz.de, IHK Frankfurt |
| Art. 25 (Privacy by Design) | dsgvo-gesetz.de, EU Kommission |
| Art. 32 (TOMs) | dsgvo-gesetz.de |

Alle Gesetzestext-Auszüge liegen bereits aufbereitet in `01-dsgvo-inhalte.md`.
