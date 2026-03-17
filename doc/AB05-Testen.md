# AB 05 — Testen

> **Thema:** Qualitätssicherung durch manuelle und automatisierte Tests
>
> **Sozialform:** Gruppenarbeit (2-3 Personen)
>
> **Zeitrahmen:** ~2-3 Unterrichtsstunden

**Nach Bearbeitung dieses Arbeitsblatts könnt ihr:**
- Testfälle systematisch durchführen und dokumentieren
- zwischen manuellem und automatisiertem Testen unterscheiden
- die Qualität eurer Implementierung anhand der Akzeptanzkriterien überprüfen

## Aufgabe 1: Manuelle Tests durchführen

Führt die Testfälle durch, die ihr in [AB 03](AB03-User-Stories-Akzeptanzkriterien-Tasks-Testfaelle.md) definiert habt. Dokumentiert die Ergebnisse in der Datei [Testing.md](Testing.md) in folgender Tabellenform:

| Testfall | Beschreibung | Ergebnis | Bemerkung |
|----------|-------------|----------|-----------|
| TF1 | Alle Pfleger anzeigen | Bestanden / Nicht bestanden | ggf. Fehlerdetails |
| TF2 | ... | ... | ... |

Für jeden **nicht bestandenen** Testfall:
- Beschreibt das tatsächliche Verhalten.
- Behebt den Fehler im Code.
- Führt den Test erneut durch und dokumentiert das Ergebnis.

## Aufgabe 2: Weitere Tests

Testet auch Szenarien, die über eure Testfälle aus AB 03 hinausgehen:

- **Grenzwerte:** Was passiert bei leeren Eingabefeldern? Bei sehr langen Texten?
- **Zusammenspiel:** Funktioniert das Löschen eines Patienten, der Behandlungen hat?
- **Konsistenz:** Werden Änderungen sofort in der Datenbank gespeichert?

Dokumentiert auch diese Tests in [Testing.md](Testing.md).

## Aufgabe 3 (Zusatz): JUnit-Tests

Schreibt mindestens **zwei JUnit-Tests** für eine eurer DAO-Klassen. Testet z.B.:
- Einen neuen Datensatz anlegen und wieder auslesen (`create` + `read`)
- Einen Datensatz löschen und prüfen, dass er nicht mehr existiert (`deleteById` + `read`)

> **Hinweis:** JUnit 5 ist bereits als Dependency in der `pom.xml` eingebunden. Erstellt eure Testklassen im Verzeichnis `src/test/java/` in der gleichen Package-Struktur wie der zu testende Code.

---

## Relevante Ressourcen

- [AB 03 — User Stories & Testfälle](AB03-User-Stories-Akzeptanzkriterien-Tasks-Testfaelle.md) — eure definierten Testfälle
- [AB 04 — Implementierung](AB04-Implementierung.md) — der zu testende Code
- [Testing.md](Testing.md) — hier dokumentiert ihr eure Testergebnisse

---

*Zurück zur [Projekt-Übersicht](README.md)*
