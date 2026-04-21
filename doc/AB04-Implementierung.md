# AB 04 — Implementierung

> **Thema:** Umsetzung der geplanten Module
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

## Meilensteine

Orientiert euch an folgenden Meilensteinen, um den Fortschritt im Blick zu behalten:

| Meilenstein | Zeitrahmen | Deliverable |
|---|---|---|
| **M1: Datenschicht** | UStd 1-3 | Model-Klasse + DAO + DB-Tabelle + Testdaten in SetUpDB |
| **M2: Oberfläche** | UStd 4-7 | FXML-View + Controller + Navigation im Hauptfenster |
| **M3: Login** | UStd 8-10 | Login-System funktionsfähig |
| **M4: Integration** | UStd 11-12 | Alle Module zusammengeführt, erste manuelle Tests |

> **Sprint-Review (Mitte AB 04):** Nach Meilenstein M2 sollte jede Gruppe ihren aktuellen Stand vorstellen können. Bereitet euch auf eine kurze Präsentation (5-10 Minuten) vor.

## Anforderungen

- Jede implementierte User Story muss die **Akzeptanzkriterien aus AB 03** erfüllen.
- Jedes Gruppenmitglied committet seinen eigenen Code (erkennbar in der Git-Historie).
- **Empfehlung:** Erstellt für jede User Story einen eigenen Branch (`git checkout -b feature/pfleger-modul`). Merged fertige Features über Pull Requests in den `main`-Branch.

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
