# NHPlus — Lernsituation Lernfeld 5

## Worum geht es?

NHPlus ist eine bestehende Anwendung zur Verwaltung eines Pflegeheims. Sie ermöglicht das Anlegen, Anzeigen, Ändern und Löschen von Patienten und deren Behandlungen. Die Anwendung ist mit **Java**, **JavaFX** und einer **SQLite-Datenbank** realisiert.

Eure Aufgabe ist es, die Anwendung zu **analysieren**, **zu erweitern** und **datenschutzkonform** zu machen.

## Was lernt ihr?

- Entwurfsmuster (DAO-Pattern, MVP-Pattern, Singleton, Factory) in einer bestehenden Codebasis erkennen und anwenden
- Eine relationale Datenbank über JDBC ansprechen
- Datenschutzanforderungen (DSGVO) analysieren und technisch umsetzen
- User Stories mit Akzeptanzkriterien, Tasks und Testfällen formulieren
- Im Team an einer gemeinsamen Codebasis arbeiten
- Software systematisch testen

## Ablauf

Die Lernsituation besteht aus fünf Arbeitsblättern, die aufeinander aufbauen:

| AB | Thema | Zeitrahmen | Was ihr tut |
|---|---|---|---|
| [AB 01](doc/AB01-Analyse-der-Architektur.md) | Analyse der Architektur | ~4 UStd | Bestehenden Code und Entwurfsmuster verstehen |
| [AB 02](doc/AB02-Datenschutzanalyse.md) | Datenschutzanalyse | ~2-3 UStd | DSGVO-Verstöße in NHPlus identifizieren |
| [AB 03](doc/AB03-User-Stories-Akzeptanzkriterien-Tasks-Testfaelle.md) | Planung | ~3-4 UStd | User Stories, Tasks und Testfälle erstellen |
| [AB 04](doc/AB04-Implementierung.md) | Implementierung | ~8-12 UStd | Pfleger-Modul und Login-System entwickeln |
| [AB 05](doc/AB05-Testen.md) | Testen | ~3 UStd | Manuell und mit JUnit testen, Retrospektive |

> **Tipp:** AB 01 und AB 02 können in der Gruppe **parallel** bearbeitet werden — ein Mitglied analysiert die Architektur, ein anderes recherchiert den Datenschutz.

## Erste Schritte

1. **Git-Repository anlegen:** Forkt oder klont dieses Repository in eurer Gruppe. Hinterlegt den Link zu eurem Repository in **Its-Learning**.
2. **Projekt in IntelliJ öffnen** und die Anwendung über den Run-Button starten. Klickt euch durch und findet heraus, was die App kann.
3. **Arbeitsblätter der Reihe nach bearbeiten** — beginnt mit [AB 01](doc/AB01-Analyse-der-Architektur.md).
4. Bei technischen Fragen zu IntelliJ, SQLite, SceneBuilder oder module-info: siehe [Technische Referenz](doc/Technische-Referenz.md).

## Ergebnisse dokumentieren

Dokumentiert die Ergebnisse jeder Phase als **Markdown** in eurem Repository. Schreibt eure Antworten **direkt in die Aufgaben-Markdowns** im `doc/`-Ordner oder verlinkt von dort auf eigene Dateien.

> **Hinweis:** Die Ergebnisse der einzelnen Phasen werden möglicherweise im Plenum vorgestellt. Bereitet euch entsprechend vor.

## Projektstruktur

```
src/main/java/de/hitec/nhplus/
├── Main.java                  ← Startklasse der Anwendung
├── model/                     ← Datenmodelle (Patient, Treatment, ...)
├── datastorage/               ← Datenbankzugriff (DAO-Pattern)
├── controller/                ← Presenter/Controller (MVP-Pattern)
└── utils/                     ← Hilfsfunktionen (DateConverter, SetUpDB)

src/main/resources/de/hitec/nhplus/
├── MainWindowView.fxml        ← Hauptfenster
├── AllPatientView.fxml        ← Patientenübersicht
└── ...                        ← Weitere Views

db/nursingHome.db              ← SQLite-Datenbank
```

## Datenbank zurücksetzen

Falls eure Datenbank durch Tests inkonsistent geworden ist, könnt ihr sie über die Klasse `SetUpDB` (im Package `utils`) zurücksetzen. **Achtung:** Das löscht alle Tabellen und erstellt sie mit Testdaten neu. Eigene Tabellenänderungen gehen dabei verloren.

## Wichtige Ressourcen

| Ressource | Beschreibung |
|---|---|
| [Technische Referenz](doc/Technische-Referenz.md) | IntelliJ-Einrichtung, SQLite, SceneBuilder, module-info |
| [MVP in JavaFX](doc/MVP%20in%20JavaFX.md) | Erklärung der verwendeten Architektur |
| [Informationsblatt: User Stories](doc/IB-User-Stories.md) | Aufbau und Beispiele für User Stories |
| [Klassendiagramm: DAO-Pattern](doc/Klassendiagramm%20Umsetzung%20des%20DAO-Pattern.jpg) | Übersicht der DAO-Schicht |
| [Bewertungsraster](doc/Bewertungsraster.md) | Woran eure Arbeit gemessen wird |

## Javadoc

Für jede Klasse, die ihr neu implementiert, muss eine Javadoc erstellt werden. Details und ein Beispiel findet ihr in [AB 04 — Implementierung](doc/AB04-Implementierung.md#javadoc).
