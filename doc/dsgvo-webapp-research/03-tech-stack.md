# Tech-Stack: React-basierte DSGVO-Lern-Webseite auf GitHub Pages

> Recherche-Ergebnis vom 2026-03-17

---

## 1. Build-Tool

### Vergleich

| Kriterium | Vite + React | Create React App (CRA) | Next.js (static export) |
|---|---|---|---|
| **Status** | Aktiv, Standard fuer neue React-Projekte | Offiziell deprecated seit 2023 | Aktiv, aber primaer fuer SSR/SSG |
| **Dev-Server** | Blitzschnell (ESBuild + HMR) | Webpack-basiert, langsam | Turbopack (schnell, aber Overhead) |
| **Build-Output** | Rein statisch (`dist/`) | Rein statisch (`build/`) | Statisch moeglich via `output: 'export'` |
| **Konfiguration** | Minimal (`vite.config.ts`) | Eject noetig fuer Anpassungen | `next.config.js` + viele Konventionen |
| **GitHub Pages** | Nativer Support, triviales Setup | Funktioniert, aber veraltet | Moeglich, aber Einschraenkungen (kein Image Optimization, kein ISR, kein Middleware) |
| **Bundle-Size** | Klein, tree-shaking via Rollup | Groesser, Webpack-Overhead | Groesser durch Framework-Runtime |
| **Lernkurve** | Gering | Gering (aber veraltet) | Mittel (viele Konzepte wie App Router, Server Components nicht nutzbar) |

### Empfehlung: **Vite + React + TypeScript**

**Begruendung:**
- Vite ist der de-facto-Standard fuer neue React-SPAs in 2025/2026
- Blitzschneller Dev-Server mit Hot Module Replacement
- Minimaler Konfigurationsaufwand fuer statische Builds
- Nativer GitHub Pages Support (einfache `base`-Konfiguration)
- Kein unnuetiger Server-Side-Overhead fuer eine rein clientseitige Lern-App
- Next.js waere Overkill: Kein Backend, kein SSR, kein ISG noetig
- CRA ist deprecated und wird nicht mehr maintained

**Setup:**
```bash
npm create vite@latest dsgvo-webapp -- --template react-ts
```

**vite.config.ts:**
```typescript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  base: '/REPO-NAME/',  // Anpassen an den tatsaechlichen Repo-Namen
})
```

---

## 2. GitHub Pages Deployment

### 2.1 GitHub Actions Workflow

Offizieller Workflow aus der Vite-Dokumentation, angepasst:

**.github/workflows/deploy.yml:**
```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: ['main']
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: 'pages'
  cancel-in-progress: true

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v6

      - name: Setup Node
        uses: actions/setup-node@v6
        with:
          node-version: lts/*
          cache: 'npm'

      - name: Install dependencies
        run: npm ci

      - name: Build
        run: npm run build

      - name: Copy index.html to 404.html (SPA-Routing)
        run: cp dist/index.html dist/404.html

      - name: Setup Pages
        uses: actions/configure-pages@v5

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v4
        with:
          path: './dist'

      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

**Wichtig:** In den Repository-Settings unter **Settings > Pages > Source** muss **GitHub Actions** ausgewaehlt sein.

### 2.2 Routing: HashRouter vs. BrowserRouter

| Aspekt | HashRouter | BrowserRouter + 404-Trick |
|---|---|---|
| **URL-Format** | `/#/kapitel/grundlagen` | `/kapitel/grundlagen` |
| **Setup** | Trivial, keine Server-Konfiguration | 404.html muss index.html spiegeln |
| **SEO** | Schlecht (Hash-Fragmente werden nicht indexiert) | Besser, aber 404-Status bleibt |
| **Aesthetik** | Weniger ansprechend | Saubere URLs |
| **Zuverlaessigkeit** | 100% zuverlaessig | Funktioniert, aber hacky |

**Empfehlung: HashRouter**

Fuer eine Lern-Webseite ist SEO sekundaer (kein oeffentliches Ranking noetig). HashRouter ist die zuverlaessigste Loesung fuer GitHub Pages ohne Workarounds. Falls spaeter saubere URLs gewuenscht sind, kann der 404.html-Trick ergaenzt werden (Workflow oben kopiert bereits `index.html` nach `404.html`).

```typescript
import { HashRouter } from 'react-router-dom'

function App() {
  return (
    <HashRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/kapitel/:id" element={<Chapter />} />
      </Routes>
    </HashRouter>
  )
}
```

### 2.3 Base-Path Handling

In `vite.config.ts`:
```typescript
base: '/REPO-NAME/'
```

Fuer React Router muss kein zusaetzliches `basename` gesetzt werden, wenn HashRouter verwendet wird, da der Hash-Teil unabhaengig vom Base-Path ist.

---

## 3. Styling

### Vergleich

| Kriterium | Tailwind CSS | CSS Modules | styled-components / Emotion | shadcn/ui |
|---|---|---|---|---|
| **Ansatz** | Utility-First | Scoped CSS | CSS-in-JS | Komponentenbibliothek (Tailwind-basiert) |
| **Bundle-Size** | Sehr klein nach Purging (<10 KB) | Minimal | Runtime-Overhead (~12-15 KB) | Nur verwendete Komponenten |
| **DX fuer Animationen** | Begrenzt (Klassen-basiert) | Volle CSS-Kontrolle | Dynamische Styles einfach | Vorgefertigte Animationen |
| **Custom Widgets** | Flexibel, aber verbose | Volle Freiheit | Volle Freiheit + dynamisch | Eingeschraenkt auf vorhandene Komponenten |
| **Konfiguration** | `tailwind.config.js` noetig | Kein Extra-Setup | Plugin noetig | Tailwind + Radix UI Setup |
| **Lernkurve** | Mittel (Utility-Klassen lernen) | Gering | Mittel | Mittel |

### Empfehlung: **Tailwind CSS + shadcn/ui (selektiv)**

**Begruendung:**
- **Tailwind CSS** als Basis-Styling: Schnelle Entwicklung, konsistentes Design-System, exzellentes Tree-Shaking (Produktionsbundles unter 10 KB)
- **shadcn/ui selektiv** fuer Standard-UI-Elemente (Buttons, Dialoge, Tooltips, Accordions): Die Komponenten werden als Quellcode ins Projekt kopiert und sind vollstaendig anpassbar. Basiert auf Radix UI (accessible by default)
- **CSS Modules ergaenzend** fuer besonders komplexe, custom Animationswidgets, bei denen reine Tailwind-Klassen zu unuebersichtlich werden
- Framer Motion (siehe Abschnitt 5) uebernimmt die dynamischen Animationen -- kein CSS-in-JS Runtime noetig

**Setup:**
```bash
npm install -D tailwindcss @tailwindcss/vite
npx shadcn@latest init
```

**Tailwind v4 Integration in vite.config.ts:**
```typescript
import tailwindcss from '@tailwindcss/vite'

export default defineConfig({
  plugins: [react(), tailwindcss()],
})
```

---

## 4. State Management

### Vergleich

| Kriterium | React Context + localStorage | Zustand + persist | Jotai |
|---|---|---|---|
| **Setup-Aufwand** | Gering (nativ) | Gering (1 Dependency) | Gering (1 Dependency) |
| **Persistierung** | Manuell implementieren | Built-in `persist` Middleware | Manuell oder via `atomWithStorage` |
| **Re-Render-Verhalten** | Alle Consumer rendern bei jeder Aenderung | Granular (Selector-basiert) | Granular (Atom-basiert) |
| **DevTools** | React DevTools | Zustand DevTools | Jotai DevTools |
| **Bundle-Size** | 0 KB (nativ) | ~1.2 KB (gzipped) | ~2.4 KB (gzipped) |
| **Boilerplate** | Viel (Provider, Reducer, Actions) | Minimal | Minimal |
| **Skalierbarkeit** | Schlecht bei vielen States | Gut | Sehr gut |

### Empfehlung: **Zustand mit persist-Middleware**

**Begruendung:**
- Built-in `persist`-Middleware fuer localStorage -- kein manueller Serialisierungs-Code noetig
- Minimaler Boilerplate: Ein Store-Definition reicht
- Granulare Re-Renders ueber Selektoren (kein unnuetiges Re-Rendering der gesamten App)
- Sehr kleine Bundle-Size (~1.2 KB gzipped)
- De-facto-Standard fuer mittlere React-Apps in 2025/2026
- React Context wuerde bei vielen Quiz-States und Kapitel-Fortschritten zu Performance-Problemen fuehren

**Datenmodell fuer Lernfortschritt:**

```typescript
import { create } from 'zustand'
import { persist } from 'zustand/middleware'

interface LearningProgress {
  // Abgeschlossene Kapitel
  completedChapters: string[]
  // Quiz-Ergebnisse: chapterId -> { score, maxScore, attempts, lastAttempt }
  quizResults: Record<string, {
    score: number
    maxScore: number
    attempts: number
    lastAttempt: string  // ISO-Datum
  }>
  // Drag & Drop Uebungen: exerciseId -> completed
  exerciseResults: Record<string, boolean>
  // Aktuelles Kapitel (fuer "Weitermachen wo du aufgehoert hast")
  currentChapter: string | null
  // Gesamtfortschritt in Prozent
  overallProgress: number

  // Actions
  completeChapter: (chapterId: string) => void
  saveQuizResult: (chapterId: string, score: number, maxScore: number) => void
  completeExercise: (exerciseId: string) => void
  setCurrentChapter: (chapterId: string) => void
  resetProgress: () => void
}

export const useLearningStore = create<LearningProgress>()(
  persist(
    (set, get) => ({
      completedChapters: [],
      quizResults: {},
      exerciseResults: {},
      currentChapter: null,
      overallProgress: 0,

      completeChapter: (chapterId) => set((state) => ({
        completedChapters: [...new Set([...state.completedChapters, chapterId])],
      })),

      saveQuizResult: (chapterId, score, maxScore) => set((state) => ({
        quizResults: {
          ...state.quizResults,
          [chapterId]: {
            score,
            maxScore,
            attempts: (state.quizResults[chapterId]?.attempts ?? 0) + 1,
            lastAttempt: new Date().toISOString(),
          },
        },
      })),

      completeExercise: (exerciseId) => set((state) => ({
        exerciseResults: { ...state.exerciseResults, [exerciseId]: true },
      })),

      setCurrentChapter: (chapterId) => set({ currentChapter: chapterId }),

      resetProgress: () => set({
        completedChapters: [],
        quizResults: {},
        exerciseResults: {},
        currentChapter: null,
        overallProgress: 0,
      }),
    }),
    {
      name: 'dsgvo-learning-progress',  // localStorage-Key
    }
  )
)
```

---

## 5. Animation & Interaktion

### 5.1 Primaere Animation-Library: Motion (ehemals Framer Motion)

**Empfehlung: Motion (framer-motion) v12+**

- 30.7k GitHub-Stars, 3.6M woechentliche Downloads -- dominante React-Animationsbibliothek
- Hybrid-Engine: Web Animations API fuer 120fps Performance + JavaScript-Fallback fuer Spring-Physik und Gesten
- Declarative API: `initial`, `animate`, `exit`, `whileHover`, `whileTap`
- `AnimatePresence` fuer Ein-/Ausblende-Animationen
- Layout-Animationen fuer fliessende Uebergaenge
- `useReducedMotion` Hook fuer Accessibility (siehe Abschnitt 7)

```bash
npm install motion
```

**Beispiel -- Kapitel-Uebergang:**
```tsx
import { motion, AnimatePresence } from 'motion/react'

function ChapterTransition({ chapter }: { chapter: ReactNode }) {
  return (
    <AnimatePresence mode="wait">
      <motion.div
        key={chapterId}
        initial={{ opacity: 0, y: 20 }}
        animate={{ opacity: 1, y: 0 }}
        exit={{ opacity: 0, y: -20 }}
        transition={{ duration: 0.3 }}
      >
        {chapter}
      </motion.div>
    </AnimatePresence>
  )
}
```

### 5.2 Drag & Drop: @dnd-kit

**Empfehlung: @dnd-kit**

- Moderner Nachfolger von react-beautiful-dnd
- Built-in Keyboard-Support (Enter/Space zum Starten, Pfeiltasten zum Bewegen, Escape zum Abbrechen)
- Konfigurierbare ARIA-Attribute und Screen-Reader-Announcements
- Touch, Mouse und Keyboard-Sensoren out of the box
- Sortierbare Listen, Grid-Layouts, Multi-Container DnD

```bash
npm install @dnd-kit/core @dnd-kit/sortable @dnd-kit/utilities
```

### 5.3 Performance-Ueberlegungen

| Thema | Empfehlung |
|---|---|
| **Animierte Properties** | Nur `transform` und `opacity` animieren -- diese laufen auf dem GPU-Compositor und blockieren nicht den Main Thread |
| **Viele gleichzeitige Animationen** | `layout`-Prop sparsam einsetzen; statt 50 Elemente einzeln zu animieren: `staggerChildren` in Variants nutzen |
| **Schwere Widgets** | Lazy Loading fuer Animationswidgets (z.B. Datenstrom-Visualisierung) via `React.lazy()` |
| **Scroll-Animationen** | Motion's `useScroll` + `useTransform` statt Scroll-Event-Listener (nutzt ScrollTimeline API) |
| **will-change** | Motion setzt `will-change` automatisch -- nicht manuell hinzufuegen |

---

## 6. Projektstruktur

### Empfohlene Ordnerstruktur

```
dsgvo-webapp/
├── .github/
│   └── workflows/
│       └── deploy.yml
├── public/
│   └── favicon.svg
├── src/
│   ├── app/
│   │   ├── App.tsx                    # Root-Komponente mit Router
│   │   └── routes.tsx                 # Route-Definitionen (lazy imports)
│   ├── chapters/                      # Kapitel als Feature-Module
│   │   ├── grundlagen/
│   │   │   ├── index.tsx              # Kapitel-Entry (lazy-loadable)
│   │   │   ├── sections/             # Sektionen innerhalb des Kapitels
│   │   │   │   ├── was-ist-dsgvo.tsx
│   │   │   │   └── geschichte.tsx
│   │   │   ├── quiz/
│   │   │   │   └── grundlagen-quiz.tsx
│   │   │   └── exercises/
│   │   │       └── zuordnung.tsx      # Drag & Drop Uebung
│   │   ├── betroffenenrechte/
│   │   │   ├── index.tsx
│   │   │   ├── sections/
│   │   │   ├── quiz/
│   │   │   └── exercises/
│   │   ├── datenschutzprinzipien/
│   │   │   └── ...
│   │   └── _shared/
│   │       └── chapter-layout.tsx     # Gemeinsames Layout fuer alle Kapitel
│   ├── components/                    # Shared UI-Komponenten
│   │   ├── ui/                        # shadcn/ui Komponenten (Button, Dialog, etc.)
│   │   ├── widgets/                   # Interaktive Lern-Widgets
│   │   │   ├── quiz-widget.tsx
│   │   │   ├── drag-drop-exercise.tsx
│   │   │   ├── timeline-widget.tsx
│   │   │   ├── flowchart-widget.tsx
│   │   │   └── matching-game.tsx
│   │   ├── navigation/
│   │   │   ├── sidebar.tsx
│   │   │   ├── chapter-nav.tsx
│   │   │   └── progress-bar.tsx
│   │   └── layout/
│   │       ├── page-layout.tsx
│   │       └── header.tsx
│   ├── content/                       # Statischer Lerninhalt
│   │   ├── chapters.json             # Kapitel-Metadaten (Titel, Reihenfolge, Beschreibung)
│   │   └── glossar.json              # DSGVO-Fachbegriffe
│   ├── stores/                        # Zustand Stores
│   │   └── learning-store.ts
│   ├── hooks/                         # Custom Hooks
│   │   ├── use-chapter-progress.ts
│   │   └── use-reduced-motion.ts
│   ├── lib/                           # Utilities
│   │   └── utils.ts                   # cn() Helper etc.
│   ├── styles/
│   │   └── globals.css                # Tailwind-Imports + Custom Properties
│   ├── main.tsx                       # Entry Point
│   └── vite-env.d.ts
├── index.html
├── vite.config.ts
├── tailwind.config.ts
├── tsconfig.json
├── package.json
└── README.md
```

### Designentscheidungen

- **Feature-basiert:** Jedes Kapitel ist ein eigenstaendiges Feature-Modul mit eigenen Sections, Quiz und Uebungen. Das erleichtert Code-Splitting und paralleles Arbeiten.
- **Content als JSON:** Kapitel-Metadaten als JSON erlauben einfache Navigation und Fortschrittsberechnung ohne Parsing. Die eigentlichen Lerninhalte sind React-Komponenten (nicht MDX), da viele interaktive Widgets eingebettet werden muessen.
- **Flache Hierarchie:** Maximal 3 Verschachtelungsebenen, um Import-Pfade lesbar zu halten.
- **Shared Widgets:** Wiederverwendbare Lern-Widgets (Quiz, DnD, Timeline) liegen zentral in `components/widgets/` und werden von allen Kapiteln verwendet.

---

## 7. Accessibility

### 7.1 ARIA-Labels fuer interaktive Widgets

```tsx
// Quiz-Widget
<fieldset aria-label="Quiz: Welche Daten sind personenbezogen?">
  <legend className="sr-only">Frage 1 von 5</legend>
  {options.map((option) => (
    <label key={option.id}>
      <input
        type="radio"
        name="q1"
        value={option.id}
        aria-describedby={`feedback-${option.id}`}
      />
      {option.text}
    </label>
  ))}
</fieldset>

// Fortschrittsbalken
<div
  role="progressbar"
  aria-valuenow={progress}
  aria-valuemin={0}
  aria-valuemax={100}
  aria-label={`Lernfortschritt: ${progress}% abgeschlossen`}
/>
```

### 7.2 Keyboard-Navigation fuer Drag & Drop

@dnd-kit bietet out-of-the-box:
- **Aktivierung:** `Enter` oder `Space` auf dem draggable Element
- **Bewegung:** Pfeiltasten (hoch/runter/links/rechts)
- **Ablegen:** `Enter` oder `Space`
- **Abbrechen:** `Escape`

Zusaetzlich konfigurierbar:
```tsx
<DndContext
  screenReaderInstructions={{
    draggable: 'Druecken Sie die Leertaste, um das Element zu greifen. ' +
               'Verwenden Sie die Pfeiltasten zum Bewegen. ' +
               'Druecken Sie die Leertaste erneut zum Ablegen.'
  }}
  announcements={{
    onDragStart: ({ active }) => `Element ${active.id} wurde aufgenommen.`,
    onDragOver: ({ active, over }) =>
      over ? `Element ${active.id} wurde ueber ${over.id} bewegt.` : undefined,
    onDragEnd: ({ active, over }) =>
      over ? `Element ${active.id} wurde auf ${over.id} abgelegt.` : `Element ${active.id} wurde zurueckgelegt.`,
    onDragCancel: ({ active }) => `Verschieben von ${active.id} abgebrochen.`,
  }}
>
```

### 7.3 Reduced Motion Support

```tsx
import { useReducedMotion } from 'motion/react'

function AnimatedWidget({ children }: { children: ReactNode }) {
  const shouldReduceMotion = useReducedMotion()

  return (
    <motion.div
      initial={{ opacity: 0, y: shouldReduceMotion ? 0 : 20 }}
      animate={{ opacity: 1, y: 0 }}
      transition={{
        duration: shouldReduceMotion ? 0 : 0.3,
      }}
    >
      {children}
    </motion.div>
  )
}
```

Zusaetzlich in CSS:
```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

### 7.4 Screenreader-Kompatibilitaet bei Animationen

- Animierte Inhalte muessen nach Abschluss der Animation im DOM bleiben und fokussierbar sein
- `aria-live="polite"` fuer dynamisch eingeblendete Ergebnisse (Quiz-Feedback, Fortschrittsmeldungen)
- Dekorative Animationen mit `aria-hidden="true"` markieren
- Fokus-Management: Nach Seitenwechsel Fokus auf Hauptinhalt setzen (`<main tabIndex={-1} ref={mainRef}>`)
- shadcn/ui-Komponenten (basierend auf Radix UI) liefern ARIA-Rollen und Keyboard-Handling automatisch

---

## 8. Performance

### 8.1 Code-Splitting pro Kapitel

Jedes Kapitel wird als eigener Chunk geladen:

```tsx
// src/app/routes.tsx
import { lazy, Suspense } from 'react'

const Grundlagen = lazy(() => import('../chapters/grundlagen'))
const Betroffenenrechte = lazy(() => import('../chapters/betroffenenrechte'))
const Datenschutzprinzipien = lazy(() => import('../chapters/datenschutzprinzipien'))

function AppRoutes() {
  return (
    <Suspense fallback={<ChapterSkeleton />}>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/kapitel/grundlagen" element={<Grundlagen />} />
        <Route path="/kapitel/betroffenenrechte" element={<Betroffenenrechte />} />
        <Route path="/kapitel/prinzipien" element={<Datenschutzprinzipien />} />
      </Routes>
    </Suspense>
  )
}
```

### 8.2 Lazy Loading von schweren Widgets

```tsx
// Innerhalb eines Kapitels: Schwere Widgets erst laden, wenn sichtbar
const DataFlowVisualization = lazy(() => import('../../components/widgets/flowchart-widget'))

function GrundlagenKapitel() {
  return (
    <div>
      <h1>DSGVO-Grundlagen</h1>
      <p>Einleitender Text...</p>

      {/* Schwere Animation erst laden, wenn der User scrollt */}
      <Suspense fallback={<WidgetPlaceholder height={400} />}>
        <DataFlowVisualization />
      </Suspense>
    </div>
  )
}
```

### 8.3 Bundle-Size Budget

| Chunk | Budget | Inhalt |
|---|---|---|
| **Initial Bundle** | < 150 KB (gzipped) | React, Router, Zustand, Tailwind, Shell/Navigation |
| **Pro Kapitel** | < 80 KB (gzipped) | Kapitel-Komponenten + spezifische Widgets |
| **Motion (Animation)** | ~17 KB (gzipped) | Wird beim ersten animierten Kapitel geladen |
| **@dnd-kit** | ~12 KB (gzipped) | Nur in Kapiteln mit Drag & Drop |
| **Gesamt** | < 300 KB (gzipped) | Alles zusammen, beim Laden des ersten Kapitels |

### 8.4 Vite-Optimierungen

```typescript
// vite.config.ts
export default defineConfig({
  plugins: [react(), tailwindcss()],
  base: '/REPO-NAME/',
  build: {
    rollupOptions: {
      output: {
        manualChunks: {
          'react-vendor': ['react', 'react-dom', 'react-router-dom'],
          'animation': ['motion'],
          'dnd': ['@dnd-kit/core', '@dnd-kit/sortable', '@dnd-kit/utilities'],
        },
      },
    },
    // Warnung bei Chunks > 200 KB
    chunkSizeWarningLimit: 200,
  },
})
```

---

## Zusammenfassung: Empfohlener Tech-Stack

| Bereich | Technologie | Version |
|---|---|---|
| **Build-Tool** | Vite | 6.x |
| **Framework** | React + TypeScript | 19.x |
| **Routing** | react-router-dom (HashRouter) | 7.x |
| **Styling** | Tailwind CSS + shadcn/ui (selektiv) | Tailwind 4.x |
| **State Management** | Zustand (mit persist-Middleware) | 5.x |
| **Animationen** | Motion (framer-motion) | 12.x |
| **Drag & Drop** | @dnd-kit | 6.x |
| **Deployment** | GitHub Pages via GitHub Actions | - |
| **Paketmanager** | npm | 10.x |

### Abhaengigkeiten (package.json)

```json
{
  "dependencies": {
    "react": "^19.0.0",
    "react-dom": "^19.0.0",
    "react-router-dom": "^7.0.0",
    "zustand": "^5.0.0",
    "motion": "^12.0.0",
    "@dnd-kit/core": "^6.0.0",
    "@dnd-kit/sortable": "^8.0.0",
    "@dnd-kit/utilities": "^3.0.0"
  },
  "devDependencies": {
    "@vitejs/plugin-react": "^4.0.0",
    "typescript": "^5.7.0",
    "vite": "^6.0.0",
    "tailwindcss": "^4.0.0",
    "@tailwindcss/vite": "^4.0.0",
    "@types/react": "^19.0.0",
    "@types/react-dom": "^19.0.0"
  }
}
```

---

## Quellen

- [Vite Static Deploy Guide](https://vite.dev/guide/static-deploy)
- [Vite vs Next.js 2025 (Strapi)](https://strapi.io/blog/vite-vs-nextjs-2025-developer-framework-comparison)
- [Next.js vs Vite 2026 (DEV Community)](https://dev.to/shadcndeck_dev/nextjs-vs-vite-choosing-the-right-tool-in-2026-38hp)
- [GitHub Pages SPA Routing Discussion](https://github.com/orgs/community/discussions/64096)
- [BrowserRouter 404 Fix](https://dev.to/anushibin007/solve-404-when-using-browserrouter-with-github-pages-492e)
- [Tailwind vs shadcn/ui (Codelevate)](https://www.codelevate.com/blog/tailwind-css-vs-shadcn-ui-which-one-to-choose-for-your-project)
- [State Management 2025 (DEV Community)](https://dev.to/saswatapal/do-you-need-state-management-in-2025-react-context-vs-zustand-vs-jotai-vs-redux-1ho)
- [Zustand vs Jotai vs React Context 2026](https://inhaq.com/blog/react-state-management-2026-redux-vs-zustand-vs-jotai.html)
- [Motion for React Documentation](https://motion.dev/docs/react)
- [Framer Motion Complete Guide 2026](https://inhaq.com/blog/framer-motion-complete-guide-react-nextjs-developers)
- [Best React Animation Libraries 2026 (LogRocket)](https://blog.logrocket.com/best-react-animation-libraries/)
- [@dnd-kit Documentation](https://dndkit.com/)
- [@dnd-kit Accessibility Guide](https://docs.dndkit.com/guides/accessibility)
- [React Folder Structure 2025 (Robin Wieruch)](https://www.robinwieruch.de/react-folder-structure/)
- [Motion Accessibility Docs](https://motion.dev/docs/react-accessibility)
- [Accessible Animations (Josh W. Comeau)](https://www.joshwcomeau.com/react/prefers-reduced-motion/)
- [Code Splitting in React with Vite](https://medium.com/@akashsdas_dev/code-splitting-in-react-w-vite-eae8a9c39f6e)
- [Vite GitHub Pages Deployer Action](https://github.com/marketplace/actions/vite-github-pages-deployer)
