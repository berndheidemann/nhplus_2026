# Spec — Einheitliches Abgabeformat für NHPlus-Lernsituation

**Datum:** 2026-04-22
**Status:** Approved (Brainstorm abgeschlossen, Umsetzung beauftragt)

## Problem & Ziel

Die README sagt aktuell „Schreibt eure Antworten direkt in die Aufgaben-Markdowns im `doc/`-Ordner **oder** verlinkt von dort auf eigene Dateien." Diese weiche Vorgabe führt dazu, dass jede Gruppe ein eigenes Format wählt — unvergleichbar, schwer zu bewerten, keine konsistente Oberfläche für Peer-Review.

Ziel: **Ein einheitliches, per Template vorgegebenes Abgabeformat**, das pro AB klarstellt, *wo* die Gruppe was einträgt, und für den Lehrer konsistente Oberfläche für die Bewertung schafft.

## Kernentscheidungen

1. **Separater Ordner `abgabe/`** mit einer Markdown-Datei pro AB (`AB01.md` – `AB05.md`). Aufgabenstellung in `doc/` bleibt inhaltlich erhalten und ist für Folgejahrgänge wiederverwendbar.
2. **Hybrid-Template-Struktur**: Tabellenskelette überall, wo Vergleichbarkeit zwischen Gruppen zählt (User Stories, Testfälle, Workstreams); freie Form bei Erklärungsaufgaben (AB 01, AB 04 Abweichungen).
3. **Einheitlicher Meta-Header** pro AB-Datei: nur Gruppe + Mitglieder + Bezug-Link zur Aufgabenstellung. Kein Datum (Git), kein Repo-Link (its-learning), keine Commit-Hashes.
4. **Workstream-Zuordnung statt Story-Ownership**: In AB 04 wird pro Workstream (A/B/C) der Verantwortliche eingetragen. In AB 03 gibt es **keine** Story-Ownership — User Stories gehören dem Team, das entspricht echter agiler Praxis.
5. **Aufwandsschätzung komplett entfernt**: Weder in AB 03 noch in AB 04 noch in AB 05. Ohne Referenzerfahrung wäre Schätzung Pseudo-Messen; stattdessen in AB 05 die qualitative Reflexionsfrage *„Welche Story/welcher Workstream war überraschend aufwändig oder leicht — und warum?"*.
6. **ER-Diagramm / CREATE TABLE aus AB 03 entfernt**: Schülern reicht die Umsetzung im `SetUpDB.java`-Code, keine zusätzliche Markdown-Repräsentation.
7. **„Neue Klassen"-Liste in AB 04 entfernt**: Git zeigt das, kein Extra-Dokumentationsaufwand.

## Architektur

```
nhplus_2026/
├── doc/                        ← Aufgabenstellungen (angepasst: AB03, AB05, Bewertungsraster)
├── abgabe/                     ← NEU — Schülerarbeit
│   ├── README.md               ← Orientierung: Was liegt hier, wie nutzen
│   ├── AB01.md                 ← Template mit Meta-Header + freier Form
│   ├── AB02.md                 ← Template mit Tabellen für Verstöße + Anforderungen
│   ├── AB03.md                 ← Template mit User-Story-Blöcken + INVEST-Check
│   ├── AB04.md                 ← Template: Workstreams, Leseauftrag, Abweichungen
│   └── AB05.md                 ← Template: Test-Tabellen + Retrospektive
└── README.md                   ← Abschnitt „Ergebnisse dokumentieren" neu
```

## Meta-Header-Schema

Jede `abgabe/ABxx.md` beginnt mit:

```markdown
# Abgabe AB 0x — <Titel>

| Feld | Wert |
|---|---|
| Gruppe | <Gruppenname oder Nr.> |
| Mitglieder | Vorname Nachname, Vorname Nachname, Vorname Nachname |

> **Bezug:** [AB 0x — <Titel>](../doc/AB0x-…md)

---
```

## Template-Inhalt pro AB

### `abgabe/AB01.md` — Architektur-Analyse
H2 pro Aufgabe (1.–5.), unter jeder Überschrift ein kurzes Zitat der Aufgabenstellung + `_Eure Antwort hier._`-Platzhalter. Keine Tabellen.

### `abgabe/AB02.md` — DSGVO-Analyse
Drei H2-Abschnitte (Art. 32, Art. 5, Art. 15–22). Pro Abschnitt eine Tabelle `Verstoß | DSGVO-Artikel | Warum problematisch`. Abschließend H2 *„Technische Anforderungen"* mit Tabelle `Nr. | Anforderung | Bezug zu Verstoß`.

### `abgabe/AB03.md` — Planung
Drei H2: *Pfleger-Verwaltung*, *Datenschutz-Fixes*, *Qualitätscheck*.
- Pfleger-Verwaltung: Nur User-Story-Blöcke (je H3 *„User Story N: <Titel>"* mit vier Tabellen: User Story, Akzeptanzkriterien, Tasks, Testfälle). **Kein ER-Diagramm, kein CREATE TABLE.**
- Datenschutz-Fixes: H3 *Priorisierungs-Begründung* (2–3 Sätze) + Story-Blöcke.
- Qualitätscheck: INVEST-Tabelle + Peer-Review-Notizfeld.
- **Keine** Aufwandsschätzungs-Tabelle.

### `abgabe/AB04.md` — Implementierungs-Begleitdokument
Der Code liegt in `src/`. Die Datei enthält:
1. H2 *Workstream-Zuordnung* — Tabelle `Workstream | Inhalt | Verantwortlich` (drei Zeilen: A Data, B UI, C Login)
2. H2 *Leseauftrag PasswordUtil* — drei H3 mit je einer Frage + Antwort-Platzhalter
3. H2 *Abweichungen von der Planung* — Freitext 3–5 Sätze mit Aufgabenzitat

### `abgabe/AB05.md` — Testen & Retrospektive
Vier H2:
1. *Manuelle Tests* — Tabelle `TF | Beschreibung | Ergebnis | Bemerkung`
2. *Weitere Tests* — dieselbe Tabellenstruktur (Grenzwerte / Zusammenspiel / Konsistenz)
3. *JUnit-Tests* — Tabelle `Testklasse | Methode | Was wird geprüft` + kurze Reflexion
4. *Retrospektive* — vier H3 mit den überarbeiteten Fragen (neue Frage 3 statt Aufwandsvergleich)

## Kollateral-Änderungen an bestehenden Dateien

| Datei | Änderung |
|---|---|
| `doc/AB03-User-Stories-…md` | Story-Ownership-Satz entschärfen (Z. 41); Datenmodellierungs-Passage (Z. 22–24) streichen; Aufwandsschätzungs-Tabelle (Z. 82–90) streichen; „Vorlage"-Abschnitt komplett entfernen (Tabellenskelette leben ab sofort in `abgabe/AB03.md`, Duplikat verhindert Drift) und durch kurzen Verweis ersetzen |
| `doc/AB04-Implementierung.md` | Hinweis ergänzen: „Leseauftrag-Antworten in `abgabe/AB04.md`" |
| `doc/AB05-Testen.md` | Retro-Frage 3 ersetzen; `Testing.md`-Erwähnungen (Z. 15, 35, 49) → `abgabe/AB05.md` |
| `doc/Bewertungsraster.md` | „; ER-Diagramm" aus Z. 11 streichen; Einleitungssatz mit Verweis auf `abgabe/` |
| `README.md` | Abschnitt „Ergebnisse dokumentieren" neu: klare Anweisung auf `abgabe/ABxx.md` |
| `abgabe/README.md` | Neu: Orientierung für Schüler (was, wie, Reihenfolge) |
| `abgabe/AB01.md` – `abgabe/AB05.md` | Neu: Templates nach obiger Struktur |

## Out of Scope

- **Keine Aufwandsschätzung in irgendeiner Form** (weder Stunden noch T-Shirt-Größen) — wurde bewusst gegen diese Option entschieden.
- **Keine Selbstbewertung** — Schüler bewerten sich nicht selbst; das macht die Lehrkraft anhand des Bewertungsrasters.
- **Kein automatisches Linting der Abgaben** — Vergleichbarkeit entsteht durch Template-Struktur, nicht durch CI-Checks.
- **Kein Umbau der Aufgabenstellungen** über die oben genannten redaktionellen Änderungen hinaus — Lernziele und Aufgabentexte bleiben inhaltlich erhalten.

## Didaktische Begründungen (für Folgejahrgänge)

- **Story-Ownership in AB 03 entschärft**: Echte agile Praxis → User Stories gehören dem Team. Individuelle Bewertbarkeit erfolgt über Workstreams in AB 04 und Git-Historie.
- **Aufwandsschätzung entfernt**: Schüler ohne Referenzerfahrung produzieren Pseudo-Schätzungen. Qualitative Reflexion in AB 05 (welche Story war überraschend?) liefert denselben Lerneffekt ohne den Overhead.
- **ER-Diagramm entfernt**: CREATE TABLE wird ohnehin in `SetUpDB.java` als Code geschrieben. Eine zusätzliche Markdown-Repräsentation bringt keinen Lernzuwachs, erzeugt aber Überprüfungsaufwand.
