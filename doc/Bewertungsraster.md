# Bewertungsraster — Lernsituation NHPlus

Dieses Raster zeigt euch, woran eure Arbeit gemessen wird. Nutzt es zur Selbstkontrolle.

> **Abgabeort:** Eure Ergebnisse zu den fünf Arbeitsblättern tragt ihr in [`abgabe/AB01.md`](../abgabe/AB01.md) – [`abgabe/AB05.md`](../abgabe/AB05.md) ein.

## Gesamtbewertung

| Bereich | Gewichtung | Beschreibung |
|---|---|---|
| **Architekturverständnis** (AB 01) | 10% | Verständnis von DAO, MVP, Singleton; korrekte Erklärungen |
| **DSGVO-Analyse** (AB 02) | 10% | Vollständigkeit der gefundenen Verstöße; korrekte Zuordnung zu DSGVO-Artikeln; Ableitung technischer Anforderungen |
| **Planung** (AB 03) | 20% | Qualität der User Stories, Akzeptanzkriterien, Tasks und Testfälle |
| **Implementierung** (AB 04) | 45% | Funktionsfähigkeit, Code-Qualität, Einhaltung der Architektur |
| **Testen & Reflexion** (AB 05) | 15% | Testdokumentation, JUnit-Tests, Retrospektive |

## Detailkriterien Implementierung (AB 04)

| Kriterium | Sehr gut | Ausreichend | Nicht bestanden |
|---|---|---|---|
| **Pfleger-Modul** | Alle vier CRUD-User-Stories umgesetzt, alle Akzeptanzkriterien erfüllt | Grundfunktionen (Anlegen, Anzeigen) vorhanden, kleinere Mängel bei Ändern/Löschen | Modul fehlt oder nicht lauffähig |
| **Login-System** | `PasswordUtil` korrekt integriert (Salt und Hash werden beim Anlegen gespeichert, Prüfung über `verify`), Fehlermeldung bei falschem Login, Leseauftrag inhaltlich sauber beantwortet | Login funktioniert grundsätzlich, aber Fehlermeldung fehlt oder der Leseauftrag ist lückenhaft | Kein Login **oder** Passwort im Klartext **oder** `PasswordUtil` ignoriert und eigenes, fehlerhaftes Hashing gebaut |
| **Architekturkonformität** | Alle Patterns korrekt angewandt (DAO, MVP, Singleton) | Patterns erkennbar, kleinere Abweichungen | Patterns ignoriert, Code unstrukturiert |
| **Code-Qualität** | Javadoc vollständig, sinnvolle Benennung, lesbarer Code | Javadoc vorhanden, Code lesbar | Kein Javadoc, unverständlicher Code |
| **OO-Entwurfsprinzipien** *(anknüpfend an die Zuul-Lernsituation)* | **Geringe Kopplung** zwischen den DAO/MVP-Schichten (kein SQL im Controller, keine FXML-Typen im Model), **hohe Kohäsion / SRP** (jede neue Klasse hat eine klare Verantwortung), **saubere Kapselung** (Felder privat, Zugriff über Methoden), **DRY** (keine duplizierte Logik zwischen Patient- und Caregiver-Modul) | Prinzipien erkennbar angewandt, vereinzelte Verstöße (eine Klasse mit zwei Aufgaben, doppelte Logik an 1–2 Stellen) | Klare Verstöße: öffentliche Felder, Controller greift direkt auf die DB zu, dupliziertes DAO-Grundgerüst, „Gott-Klasse" |
| **Team-Workflow** | Feature-Branches pro Workstream, saubere Pull Requests, Kopplungspunkte sichtbar abgestimmt | Commits von allen Mitgliedern vorhanden, aber direkt auf `main` oder PR-Prozess lückenhaft | Keine oder nur ein Mitglied committet, kein erkennbarer Workflow |
| **Zusätzliche DSGVO-Umsetzung** *(optional — Bonus)* | Eine der beiden frei gewählten DSGVO-Stories zusätzlich funktionsfähig implementiert, Akzeptanzkriterien erfüllt | Umsetzung angefangen, aber nicht vollständig | *kein Punktabzug* — nur Planung in AB 03 reicht für die Grundbewertung |

## Hinweise

- Das Bewertungsraster dient der **Transparenz** — ihr wisst von Anfang an, worauf es ankommt.
- Die **Gruppenarbeit** wird durch die Git-Historie und den Team-Workflow nachvollzogen. Jedes Mitglied muss eigene Commits haben.
- **DSGVO-User-Stories**, die ihr plant aber nicht umsetzt, fließen positiv in die Planungsnote in AB 03 ein. Zusätzliche, über den Pflichtumfang hinaus umgesetzte DSGVO-Stories werten die Implementierungsnote nach oben (siehe Zeile „Zusätzliche DSGVO-Umsetzung" in der Tabelle oben).
