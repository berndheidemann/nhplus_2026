# Bewertungsraster — Lernsituation NHPlus

Dieses Raster zeigt euch, woran eure Arbeit gemessen wird. Nutzt es zur Selbstkontrolle.

## Gesamtbewertung

| Bereich | Gewichtung | Beschreibung |
|---|---|---|
| **Architekturverständnis** (AB 01) | 10% | Verständnis von DAO, MVP, Singleton; korrekte Erklärungen |
| **DSGVO-Analyse** (AB 02) | 10% | Vollständigkeit der gefundenen Verstöße; korrekte Zuordnung zu DSGVO-Artikeln; Ableitung technischer Anforderungen |
| **Planung** (AB 03) | 20% | Qualität der User Stories, Akzeptanzkriterien, Tasks und Testfälle; ER-Diagramm |
| **Implementierung** (AB 04) | 45% | Funktionsfähigkeit, Code-Qualität, Einhaltung der Architektur |
| **Testen & Reflexion** (AB 05) | 15% | Testdokumentation, JUnit-Tests, Retrospektive |

## Detailkriterien Implementierung (AB 04)

| Kriterium | Sehr gut | Ausreichend | Nicht bestanden |
|---|---|---|---|
| **Pfleger-Modul** | Alle vier CRUD-User-Stories umgesetzt, alle Akzeptanzkriterien erfüllt | Grundfunktionen (Anlegen, Anzeigen) vorhanden, kleinere Mängel bei Ändern/Löschen | Modul fehlt oder nicht lauffähig |
| **Login-System** | Passwort-Hashing mit Salt, Fehlermeldung bei falschem Login | Hashing vorhanden, aber ohne Salt oder nur einfaches SHA-256 | Kein Login **oder** Passwort im Klartext gespeichert |
| **Architekturkonformität** | Alle Patterns korrekt angewandt (DAO, MVP, Singleton) | Patterns erkennbar, kleinere Abweichungen | Patterns ignoriert, Code unstrukturiert |
| **Code-Qualität** | Javadoc, sinnvolle Benennung, keine Code-Duplikation | Javadoc vorhanden, Code lesbar | Kein Javadoc, unverständlicher Code |
| **Team-Workflow** | Feature-Branches pro Workstream, saubere Pull Requests, Kopplungspunkte sichtbar abgestimmt | Commits von allen Mitgliedern vorhanden, aber direkt auf `main` oder PR-Prozess lückenhaft | Keine oder nur ein Mitglied committet, kein erkennbarer Workflow |
| **Zusätzliche DSGVO-Umsetzung** *(optional — Bonus)* | Eine der beiden frei gewählten DSGVO-Stories zusätzlich funktionsfähig implementiert, Akzeptanzkriterien erfüllt | Umsetzung angefangen, aber nicht vollständig | *kein Punktabzug* — nur Planung in AB 03 reicht für die Grundbewertung |

## Hinweise

- Das Bewertungsraster dient der **Transparenz** — ihr wisst von Anfang an, worauf es ankommt.
- Die **Gruppenarbeit** wird durch die Git-Historie und den Team-Workflow nachvollzogen. Jedes Mitglied muss eigene Commits haben.
- **DSGVO-User-Stories**, die ihr plant aber nicht umsetzt, fließen positiv in die Planungsnote in AB 03 ein. Zusätzliche, über den Pflichtumfang hinaus umgesetzte DSGVO-Stories werten die Implementierungsnote nach oben (siehe Zeile „Zusätzliche DSGVO-Umsetzung" in der Tabelle oben).
