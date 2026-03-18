# Bewertungsraster — Lernsituation NHPlus

Dieses Raster zeigt euch, woran eure Arbeit gemessen wird. Nutzt es zur Selbstkontrolle.

## Gesamtbewertung

| Bereich | Gewichtung | Beschreibung |
|---|---|---|
| **Architekturverständnis** (AB 01) | 15% | Verständnis von DAO, MVP, Singleton; korrekte Erklärungen |
| **DSGVO-Analyse** (AB 02) | 15% | Vollständigkeit der gefundenen Verstöße; korrekte Zuordnung zu DSGVO-Artikeln |
| **Planung** (AB 03) | 20% | Qualität der User Stories, Akzeptanzkriterien, Tasks und Testfälle; ER-Diagramm |
| **Implementierung** (AB 04) | 35% | Funktionsfähigkeit, Code-Qualität, Einhaltung der Architektur |
| **Testen & Reflexion** (AB 05) | 15% | Testdokumentation, JUnit-Tests, Retrospektive |

## Detailkriterien Implementierung (AB 04)

| Kriterium | Sehr gut | Ausreichend | Nicht bestanden |
|---|---|---|---|
| **Pfleger-Modul** | CRUD vollständig, alle Akzeptanzkriterien erfüllt | Grundfunktionen vorhanden, kleinere Mängel | Modul fehlt oder nicht lauffähig |
| **Login-System** | Passwort-Hashing, Fehlermeldung bei falschem Login | Login funktioniert, Passwort im Klartext | Kein Login implementiert |
| **Architekturkonformität** | Alle Patterns korrekt angewandt (DAO, MVP, Singleton) | Patterns erkennbar, kleinere Abweichungen | Patterns ignoriert, Code unstrukturiert |
| **Code-Qualität** | Javadoc, sinnvolle Benennung, keine Code-Duplikation | Javadoc vorhanden, Code lesbar | Kein Javadoc, unverständlicher Code |
| **Git-Historie** | Regelmäßige Commits aller Mitglieder, aussagekräftige Messages | Commits vorhanden, aber unregelmäßig | Keine oder nur ein Commit |

## Hinweise

- Das Bewertungsraster dient der **Transparenz** — ihr wisst von Anfang an, worauf es ankommt.
- Die **Gruppenarbeit** wird durch die Git-Historie nachvollzogen. Jedes Mitglied muss eigene Commits haben.
- DSGVO-User-Stories, die ihr plant aber nicht umsetzt, fließen **positiv** in die Planungsnote ein.
