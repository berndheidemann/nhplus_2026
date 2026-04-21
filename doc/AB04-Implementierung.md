# AB 04 — Implementierung

> **Thema:** Umsetzung der geplanten Module
>
> **Zeitrahmen:** ~10-14 Unterrichtsstunden

**Nach Bearbeitung dieses Arbeitsblatts könnt ihr:**
- eine bestehende Anwendung eigenständig um neue Module erweitern
- die vorhandene Architektur (DAO-Pattern, MVP-Pattern) auf neue Anforderungen übertragen
- im Team an einer gemeinsamen Codebasis arbeiten

## Aufgabenstellung

Setzt die User Stories aus [AB 03](AB03-User-Stories-Akzeptanzkriterien-Tasks-Testfaelle.md) um.

### Pflichtumfang

1. **Pfleger-Modul vollständig implementieren** — alle User Stories zur Pfleger-Verwaltung müssen umgesetzt sein und die Akzeptanzkriterien erfüllen.
2. **Login-System implementieren** — die Anwendung darf nur nach erfolgreicher Anmeldung nutzbar sein.

Die beiden frei gewählten DSGVO-Stories aus AB 03 (ohne Login) bleiben als dokumentierte Planung stehen; ihre freiwillige Umsetzung wird im Bewertungsraster positiv berücksichtigt (siehe Zeile „Zusätzliche DSGVO-Umsetzung").

### Hinweis zum Login-System

Für das Login-System benötigt ihr:

- Eine neue Tabelle `user` in der Datenbank mit mindestens den Spalten `username` und `password_hash`.
- **Passwörter dürfen nicht im Klartext gespeichert werden!** Verwendet Hashing (z.B. SHA-256 mit Salt). Recherchiert dazu `MessageDigest` in Java.
- Eine neue FXML-View `LoginView.fxml` mit zwei Eingabefeldern (Benutzername, Passwort) und einem Login-Button.
- Einen `LoginController`, der die Eingabe gegen die Datenbank prüft.
- Das Login-Fenster wird **vor** dem Hauptfenster geladen. Erst nach erfolgreicher Anmeldung wird das Hauptfenster geöffnet.

> **Tipp:** Beginnt mit einer einfachen Variante und erweitert schrittweise. Ein funktionierendes Login mit SHA-256 ist besser als ein geplantes, aber nicht umgesetztes System mit BCrypt.

## Orientierung

Die bestehenden Klassen dienen euch als Vorlage — studiert sie, bevor ihr eigene Module entwickelt:

| Schicht | Bestehende Beispiele | Eure Aufgabe |
|---------|---------------------|--------------|
| **Model** | `Patient.java`, `Treatment.java` | Neue Modelklassen erstellen |
| **DAO** | `PatientDao.java`, `TreatmentDao.java` | Neue DAO-Klassen von `DaoImp` ableiten |
| **View** | `AllPatientView.fxml`, `AllTreatmentView.fxml` | Neue FXML-Views erstellen |
| **Controller** | `AllPatientController.java`, `AllTreatmentController.java` | Neue Controller erstellen |

> **Tipp zum Einstieg in FXML:** JavaFX und FXML haben wir nicht explizit behandelt. Öffnet `AllPatientView.fxml` im SceneBuilder und baut eure Pfleger-View analog auf — so seht ihr direkt, wie TableView, Textfelder und Buttons verdrahtet werden.

Denkt außerdem an:

- `DaoFactory` — registriert eure neuen DAOs dort.
- `module-info.java` — tragt neue Packages ein, wenn ihr welche erstellt.
- `SetUpDB` — erweitert die Klasse um Testdaten für eure neuen Tabellen.
- `MainWindowController` — bindet eure neuen Views in die Navigation ein.

## Workstream-Vorschlag

Das Pfleger-Modul und das Login-System lassen sich in eurer 3er-Gruppe parallel entwickeln. Teilt die Arbeit so auf — jeder übernimmt einen Workstream:

| Workstream | Inhalt | Typische Dateien |
|---|---|---|
| **A: Data Layer** | Pfleger-Model + DAO + DB-Tabelle + JUnit-Tests | `Caregiver.java`, `CaregiverDao.java`, `SetUpDB.java`, `CaregiverDaoTest.java` |
| **B: UI Layer** | Pfleger-View (FXML) + Controller + Einbindung in die Navigation | `AllCaregiverView.fxml`, `AllCaregiverController.java`, Anpassungen in `MainWindowController` |
| **C: Login-System** | User-Tabelle + Passwort-Hashing + LoginView + LoginController + Start-Reihenfolge | `User.java`, `UserDao.java`, `LoginView.fxml`, `LoginController.java`, Anpassungen in `Main.java` |

**Kopplungspunkte** — diese Dateien werden von mehreren Workstreams berührt. Editiert sie nicht parallel! Sprecht euch ab, wer wann einen Merge in diese Dateien setzt:

- `DaoFactory` (A und C ergänzen je eine Factory-Methode)
- `MainWindowController` (B bindet die neue View ein)
- `Main.java` (C ändert die Start-Reihenfolge)
- `module-info.java` (bei neuen Packages)
- `SetUpDB` (A und C ergänzen je Testdaten)

> **Tipp:** B hängt von A ab (ohne DAO keine View mit Daten). Startet A zuerst, B kann parallel mit Stubs beginnen. C läuft komplett unabhängig — ideal für den dritten Workstream.

## Git-Workflow

Ihr arbeitet zum ersten Mal ernsthaft im Team mit Git. Damit Merges nicht ins Chaos kippen, gilt die folgende **Merge-Choreographie**:

1. **Feature-Branch pro Workstream:** `git checkout -b feature/pfleger-dao` (A), `feature/pfleger-view` (B), `feature/login` (C).
2. **Vor jedem Push:** `git pull --rebase origin main` — holt die letzten Änderungen und setzt eure Commits obendrauf.
3. **Pull Request statt direktem Merge:** Eröffnet einen PR auf GitHub. Vor dem Merge prüft jemand aus der Gruppe, ob die Anwendung noch startet.
4. **Kopplungspunkt-Regel:** Wer eine der oben genannten Kopplungs-Dateien anfasst, sagt das in der Gruppe an und merged zuerst. Erst danach ziehen die anderen den neuen Stand.
5. **Kleine Commits, frühe Merges:** Nicht tagelang an einem Branch arbeiten. Je länger ein Branch lebt, desto aufwändiger der Merge.

> **Bei Merge-Konflikt:** Nicht einfach `--theirs` oder `--ours` nehmen! Öffnet beide Versionen im IntelliJ-Merge-Tool und entscheidet bewusst, welche Änderung bleibt. Oft sind beide nötig.

## Meilensteine

Orientiert euch an folgenden Meilensteinen, um den Fortschritt im Blick zu behalten:

| Meilenstein | Zeitrahmen | Deliverable |
|---|---|---|
| **M1: Datenschicht** | UStd 1-3 | Model-Klasse + DAO + DB-Tabelle + Testdaten in SetUpDB |
| **M2: Oberfläche** | UStd 4-8 | FXML-View + Controller + Navigation im Hauptfenster |
| **M3: Login** | UStd 9-12 | Login-System funktionsfähig |
| **M4: Integration** | UStd 13-14 | Alle Module zusammengeführt, erste manuelle Tests |

## Anforderungen

- Jede implementierte User Story muss die **Akzeptanzkriterien aus AB 03** erfüllen.
- Jedes Gruppenmitglied committet seinen eigenen Code (erkennbar in der Git-Historie).
- Arbeitet nach der Merge-Choreographie aus dem Abschnitt [Git-Workflow](#git-workflow) — Feature-Branches und Pull Requests sind Pflicht.

## Javadoc

Dokumentiert jede Klasse, die ihr neu erstellt, mit Javadoc. Orientiert euch an `PatientDao.java` — dort seht ihr, wie gute Javadoc aussieht.

**Was muss dokumentiert werden?**

| Element | Javadoc nötig? | Was beschreiben? |
|---|---|---|
| Klasse | Ja | Zweck und Verantwortung der Klasse |
| Konstruktor (public) | Ja | Was initialisiert wird, `@param` für jeden Parameter |
| Methode (public) | Ja | Was sie tut, `@param`, `@return`, `@throws` |
| Getter/Setter | Nein | Nur wenn das Feld erklärungsbedürftig ist |

**Beispiel:**

```java
/**
 * Provides database access for {@link Caregiver} objects.
 * Implements CRUD operations using the DAO pattern.
 */
public class CaregiverDao extends DaoImp<Caregiver> {

    /**
     * Generates a <code>PreparedStatement</code> to persist a new caregiver.
     *
     * @param caregiver Object of class <code>Caregiver</code> to persist.
     * @return <code>PreparedStatement</code> to insert the given caregiver.
     */
    @Override
    protected PreparedStatement getCreateStatement(Caregiver caregiver) {
        // ...
    }
}
```

> **Tipp:** Wenn ihr beim Dokumentieren merkt, dass eine Klasse oder Methode mehrere Aufgaben hat — ändert es! Javadoc hilft nicht nur den Lesern, sondern auch euch, Designprobleme zu erkennen.

## Tipp

Fangt mit dem **Model** und dem **DAO** an. Wenn die Datenhaltung funktioniert, baut die **View** und den **Controller**.

---

## Relevante Ressourcen

- [AB 03 — User Stories & Planung](AB03-User-Stories-Akzeptanzkriterien-Tasks-Testfaelle.md) — eure User Stories und Tasks
- [AB 01 — Analyse der Architektur](AB01-Analyse-der-Architektur.md) — Architekturverständnis
- [MVP in JavaFX](MVP%20in%20JavaFX.md) — Zusammenspiel von View, Model und Presenter
- [Technische Referenz](Technische-Referenz.md) — Hinweise zu Datenbank, SceneBuilder, module-info

---

*Weiter mit [AB 05 — Testen](AB05-Testen.md)*
