# Informationsblatt: User Stories

## 1) User Stories allgemein

User Stories sind ein Werkzeug aus der agilen Softwareentwicklung, um Anforderungen an eine Software zu formulieren. Der Begriff „User Story" stammt aus dem Englischen und beschreibt im wörtlichen Sinne eine Geschichte (Story) eines Anwenders (User). Eine User Story beschreibt also eine gewünschte Funktionalität eines Systems aus Sicht des Anwenders.

Dabei bietet eine User Story vor allem drei Vorteile:

- Sie ist leicht zu verstehen und vermittelt die Wünsche der Anwender.
- Sie ist schnell erstellt und erleichtert die Schätzung des Aufwands zur Realisierung.
- Sie lässt sich schrittweise detaillieren und unterstützt so die iterative Entwicklung.

Die Anforderung wird dabei in einem Satz und mit einfachen Worten beschrieben. So ist sichergestellt, dass alle an der Entwicklung beteiligten Kollegen sie auch ohne technischen Hintergrund verstehen. User Stories formulieren das **WER**, **WAS** und **WARUM** einer Funktionalität — also wer möchte was von einem System, um welchen Nutzen davon zu haben. *Wie* die gewünschte Funktionalität später umgesetzt wird, ist für eine User Story unerheblich.

### Aufbau einer User Story

> **Als** \<User\> **möchte ich** \<Funktionalität\>, **um** \<Nutzen\> **zu erreichen.**

Auf der Rückseite der Karte, auf der die User Story notiert wird, stehen die **Akzeptanzkriterien**. Sie legen die Kriterien oder Eigenschaften fest, wann eine User Story vollständig implementiert wurde. Die Akzeptanzkriterien sind wiederum die Grundlage, um:

1. die **Aufgaben (Tasks)** festzulegen, die nötig sind, um die User Story umzusetzen, und
2. die **Testfälle** abzuleiten, um die Implementierung der Story zu testen.

---

## 2) User Stories aus NHPlus

### User Story 1: Patientenverwaltung

> **Als** Wohnbereichsleiter **möchte ich** die persönlichen Daten der Pflegepatienten verwalten können, **um** die Zimmerbelegung gemäß der Pflegestufen der Patienten vornehmen zu können.

#### Akzeptanzkriterien

| Nr. | Kriterium |
|-----|-----------|
| A_1 | Die persönlichen Daten eines Patienten bestehen aus der PatientenID, dem Nachnamen, Vornamen, Geburtsdatum, der Pflegestufe, Raumnummer im Pflegeheim und dem Vermögensstand. |
| A_2 | Alle Feldbelegungen sind verpflichtend. |
| A_3 | Alle Patienten werden mit ihren vollständigen Daten in einer tabellarischen Übersicht dargestellt. |
| A_4 | Jede Information zu einem Patienten kann aus der Übersicht heraus geändert werden. |
| A_5 | Es können neue Patienten hinzugefügt werden. |
| A_6 | Ein ausgewählter Patient kann gelöscht werden. |
| A_7 | Jede getätigte Änderung — Anlegen eines Patienten, Ändern der Stammdaten und das Löschen eines Patienten — wird in der Datenbank abgebildet. |

#### Tasks

| Nr. | Task |
|-----|------|
| T_1 | Modelklasse `Patient` erstellen: abgeleitet von `Person`, Konstruktoren mit und ohne PatientenID. |
| T_2 | Allgemein gültiges DAO erstellen: Interface `Dao` mit CRUD-Methoden (create, read, readAll, update, deleteByID), generischer Typ `T`. Implementierung durch die abstrakte Klasse `DAOImp`. DAO-Factory und `ConnectionBuilder` erstellen. `PatientDAO` erstellen. |
| T_3 | Datenbank mit einer Tabelle `Patient` anlegen, die die Stammdaten der Patienten hält. |
| T_4 | `AllPatientView` erstellen: TableView mit allen Patientendaten, darunter Textfelder zum Anlegen eines neuen Patienten, Button zum Hinzufügen und Löschen. |
| T_5 | `AllPatientController` erstellen: stellt die Methoden zum Anzeigen der Patienten, Ändern, Löschen und Hinzufügen bereit. |

#### Testfälle (Auszug)

**TF1: Alle Patienten anzeigen**

| | |
|---|---|
| **Vorbedingung** | Der Nutzer hat im Hauptfenster der Anwendung die Option *Patienten/innen* ausgewählt. |
| **Testschritte** | — |
| **Erwartetes Ergebnis** | Es werden alle Patienten, die in der Datenbank gespeichert sind, mit ihrer ID, Nachnamen, Vornamen, Geburtsdatum, Pflegestufe und Raumnummer in einer TableView angezeigt. |

**TF2: Patientendaten ändern**

| | |
|---|---|
| **Vorbedingung** | Der Nutzer hat im Hauptfenster der Anwendung die Option *Patienten/innen* ausgewählt. |
| **Testschritte** | 1. Der User wählt per Doppelklick auf einen Nachnamen einen Patienten aus. 2. Der User ändert den Nachnamen. 3. Der User beendet die Eingabe mit der Entertaste. |
| **Erwartetes Ergebnis** | 1. Der geänderte Nachname wird in der TableView angezeigt. 2. Der geänderte Nachname wurde in der Datenbank gespeichert. |

**TF3: Patient anlegen**

| | |
|---|---|
| **Vorbedingung** | Der Nutzer hat im Hauptfenster der Anwendung die Option *Patienten/innen* ausgewählt. |
| **Testschritte** | 1. Der User hat den Nachnamen, Vornamen, Geburtsdatum, Pflegestufe und Raumnummer des anzulegenden Patienten in die dafür vorgesehenen Textfelder eingegeben. 2. Der User hat den Button *Hinzufügen* betätigt. |
| **Erwartetes Ergebnis** | 1. Der neue Patient wird mit allen eingetragenen Daten sowie einer automatisch erstellten ID als letzter Eintrag in der TableView angezeigt. 2. Der neue Patient wurde in der Datenbank gespeichert. |

---

### User Story 2: Behandlungsdokumentation

> **Als** Pflegekraft **möchte ich** die Behandlungen meiner Patienten dokumentieren und die Dokumentationen vergangener Behandlungen einsehen können, **um** geeignete Folgemaßnahmen ergreifen zu können.

#### Akzeptanzkriterien

| Nr. | Kriterium |
|-----|-----------|
| A_1 | Eine Behandlung besitzt eine ID, einen Patienten, ein Datum, Beginn, Ende, eine Kurz- und eine Langbeschreibung. |
| A_2 | Alle Behandlungen werden in einer tabellarischen Übersicht mit ihrer ID, der PatientenID, Datum, Beginn, Ende und Kurzbeschreibung angezeigt. |
| A_3 | Die Anzeige der Behandlungen kann durch Auswahl eines Patienten auf alle Behandlungen dieses Patienten eingeschränkt werden. Diese Einschränkung soll durch die Option „alle" wieder aufgehoben werden können. |
| A_4 | Durch Klick auf einen Button soll in einem neuen Fenster eine neue Behandlung angelegt werden können. |
| A_5 | Wurde beim Anlegen einer neuen Behandlung kein Patient ausgewählt, erscheint eine Fehlermeldung. |
| A_6 | Eine ausgewählte Behandlung soll gelöscht werden können. |
| A_7 | Jede Behandlung kann durch Auswahl in einem weiteren Fenster geöffnet werden, um nähere Informationen zu erfahren (Patient, Pflegestufe, Datum, Beginn, Ende, Kurzbeschreibung und Langbeschreibung). Es soll eine Möglichkeit zum Ändern der Daten und zum Verlassen des Fensters über die Option *Abbruch* geben. |

#### Tasks

| Nr. | Task |
|-----|------|
| T_1 | Modelklasse `Treatment` erstellen: Konstruktoren mit und ohne TreatmentID. |
| T_2 | `TreatmentDAO`-Klasse implementieren: abgeleitet von `DAOImp`; zusätzlich eine Methode, die alle Behandlungen anhand einer bestimmten PatientenID aus der DB bezieht, und eine Methode, die alle Behandlungen einer bestimmten PatientenID löscht. |
| T_3 | In der Datenbank eine Tabelle `Treatment` mit einem Fremdschlüssel auf die Tabelle `Patient` anlegen. |
| T_4 | `AllTreatmentView` erstellen: TableView mit den unter A_2 beschriebenen Behandlungsdaten, darunter ComboBox zur Auswahl der Patienten, Button zum Anlegen einer neuen Behandlung, Button zum Löschen einer Behandlung. |
| T_5 | `NewTreatmentView` erstellen: zeigt Patient mit Vor- und Nachnamen an. Über Textfelder können die Daten einer Behandlung angegeben werden. Button zum Anlegen und zum Abbrechen. |
| T_6 | `TreatmentView` erstellen: zeigt Patient mit vollem Namen und Pflegestufe an. Über Textfelder werden die Daten einer Behandlung angezeigt und können dort auch geändert werden. Button zum Ändern und zum Abbrechen. |
| T_7 | Aktualisierung des `AllPatientController`: Beim Löschen eines Patienten werden dessen Behandlungen ebenfalls gelöscht. |
| T_8 | Erstellen der Controller für die drei Views. |

---

*Siehe auch: [AB 03 — User Stories, Akzeptanzkriterien, Tasks, Testfälle](AB03-User-Stories-Akzeptanzkriterien-Tasks-Testfaelle.md)*
