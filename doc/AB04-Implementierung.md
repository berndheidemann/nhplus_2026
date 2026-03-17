# AB 04 — Implementierung

> **Thema:** Umsetzung der geplanten Module
>
> **Sozialform:** Gruppenarbeit (2-3 Personen), Arbeitsteilung nach User Stories
>
> **Zeitrahmen:** ~8-12 Unterrichtsstunden

**Nach Bearbeitung dieses Arbeitsblatts könnt ihr:**
- eine bestehende Anwendung eigenständig um neue Module erweitern
- die vorhandene Architektur (DAO-Pattern, MVP-Pattern) auf neue Anforderungen übertragen
- im Team an einer gemeinsamen Codebasis arbeiten

## Aufgabenstellung

Setzt die User Stories aus [AB 03](AB03-User-Stories-Akzeptanzkriterien-Tasks-Testfaelle.md) um.

### Pflichtumfang

1. **Pfleger-Modul vollständig implementieren** — alle User Stories zur Pfleger-Verwaltung müssen umgesetzt sein und die Akzeptanzkriterien erfüllen.
2. **Login-System implementieren** — die Anwendung darf nur nach erfolgreicher Anmeldung nutzbar sein.

Weitere DSGVO-User-Stories aus AB 03, die ihr nicht mehr umsetzt, bleiben als dokumentierte Planung stehen.

## Orientierung

Die bestehenden Klassen dienen euch als Vorlage — studiert sie, bevor ihr eigene Module entwickelt:

| Schicht | Bestehende Beispiele | Eure Aufgabe |
|---------|---------------------|--------------|
| **Model** | `Patient.java`, `Treatment.java` | Neue Modelklassen erstellen |
| **DAO** | `PatientDao.java`, `TreatmentDao.java` | Neue DAO-Klassen von `DaoImp` ableiten |
| **View** | `AllPatientView.fxml`, `AllTreatmentView.fxml` | Neue FXML-Views erstellen |
| **Controller** | `AllPatientController.java`, `AllTreatmentController.java` | Neue Controller erstellen |

Denkt außerdem an:

- `DaoFactory` — registriert eure neuen DAOs dort.
- `module-info.java` — tragt neue Packages ein, wenn ihr welche erstellt.
- `SetUpDB` — erweitert die Klasse um Testdaten für eure neuen Tabellen.
- `MainWindowController` — bindet eure neuen Views in die Navigation ein.

## Anforderungen

- Jede implementierte User Story muss die **Akzeptanzkriterien aus AB 03** erfüllen.
- Jedes Gruppenmitglied committet seinen eigenen Code (erkennbar in der Git-Historie).

## Tipp

Fangt mit dem **Model** und dem **DAO** an. Wenn die Datenhaltung funktioniert, baut die **View** und den **Controller**.

---

## Relevante Ressourcen

- [AB 03 — User Stories & Planung](AB03-User-Stories-Akzeptanzkriterien-Tasks-Testfaelle.md) — eure User Stories und Tasks
- [AB 01 — Analyse der Architektur](AB01-Analyse-der-Architektur.md) — Architekturverständnis
- [MVP in JavaFX](MVP%20in%20JavaFX.md) — Zusammenspiel von View, Model und Presenter
- [Projekt-README](README.md) — Hinweise zu Datenbank, SceneBuilder, module-info

---

*Weiter mit [AB 05 — Testen](AB05-Testen.md)*
