# AB 01 — Analyse der Architektur von NHPlus

> **Themen:** DAO-Pattern, MVP-Pattern, Singleton-Pattern, generische Klassen, JDBC
>
> **Sozialform:** Gruppenarbeit (2-3 Personen), Ergebnisse im Plenum vorstellen
>
> **Zeitrahmen:** ~4 Unterrichtsstunden

**Nach Bearbeitung dieses Arbeitsblatts könnt ihr:**
- das Zusammenspiel der Schichten im DAO-Pattern erklären
- begründen, warum Singleton und Factory-Pattern eingesetzt werden
- den Ablauf im MVP-Pattern bei einer Benutzerinteraktion nachvollziehen
- einschätzen, was nötig ist, um die Architektur um ein neues Modul zu erweitern
- eine erste kleine Änderung an der bestehenden Codebasis vornehmen und testen

## Vorbereitung

1. Startet die Anwendung über den Run-Button in IntelliJ. Klickt euch durch die Anwendung und findet heraus, was sie alles kann!
2. Lest das Informationsblatt [MVP in JavaFX](MVP%20in%20JavaFX.md), um die verwendete Architektur zu verstehen.
3. Studiert das Klassendiagramm [„Umsetzung des DAO-Pattern in NHPlus"](Klassendiagramm%20Umsetzung%20des%20DAO-Pattern.jpg).

## Aufgaben

### 1. DAO-Pattern: create-Methode

Erläutert das Zusammenspiel von `DaoImp`, `PatientDao` und der Datenbanktabelle `patient`, wenn die im Interface `Dao` definierte Methode `void create(T t) throws SQLException` aufgerufen wird, um einen neuen Patienten anzulegen.

### 2. Erweiterung um ein Pfleger-Modul

Stellt euch vor, ihr sollt die Anwendung um ein Modul erweitern, das **Pflegekräfte** verwaltet. Innerhalb dieses Moduls können Pflegekräfte angezeigt, angelegt, geändert und gelöscht werden.

- Was müsstet ihr dafür in dieser Architektur tun?
- Welchen Vorteil bietet diese Architektur im Vergleich zu einer Architektur, in der es zu jeder Modelklasse eine konkrete DAO-Klasse gibt (also das DAO-Interface und die abstrakte Klasse `DaoImp` nicht existierten)?
- Geht bei eurer Antwort auch darauf ein, weswegen eine generische Klasse (`<T>`) verwendet wurde.

### 3. ConnectionBuilder, DaoFactory und das Singleton-Pattern

Erklärt die Aufgaben der Klassen `ConnectionBuilder` und `DaoFactory`.

- Warum hält `PatientDao` keine eigene Datenbankverbindung?
- Warum sind `ConnectionBuilder` und `DaoFactory` als Singleton implementiert? Was wäre das Problem, wenn es mehrere Instanzen gäbe?

### 4. MVP-Pattern

Erklärt das Zusammenspiel der Klassen `Patient`, `AllPatientController` und `AllPatientView.fxml` im verwendeten MVP-Pattern im folgenden Anwendungsfall:

> Der Benutzer gibt im Bereich unter der Ansicht aller Patienten vollständig die Daten eines neuen Patienten ein und drückt den Button *Hinzufügen*.

Erläutert, was genau in der View, im Model und im Presenter nacheinander abläuft. Der Ablauf zum Speichern des neuen Patienten muss nicht beschrieben werden (siehe Aufgabe 1).

Worin liegt der Unterschied zu einer MVC-Architektur?

### 5. Erste eigene Änderung

Öffnet die Klasse `SetUpDB` im Package `utils`. Fügt in der Methode `setUpPatients()` einen weiteren Testpatienten mit frei gewählten Daten hinzu. Startet die Anwendung und überprüft:

- Erscheint der neue Patient in der Tabelle?
- Wird er in der Datenbank gespeichert? (Prüft über die IntelliJ-Datenbankansicht mit `SELECT * FROM patient`)

> **Reflexion:** Welchen Weg nehmen die Daten vom `SetUpDB`-Aufruf bis zur Anzeige in der GUI?
> Nutzt eure Erkenntnisse aus den Aufgaben 1 und 4, um den Weg zu beschreiben.

---

## Relevante Ressourcen

- [Klassendiagramm: Umsetzung des DAO-Pattern](Klassendiagramm%20Umsetzung%20des%20DAO-Pattern.jpg)
- [MVP in JavaFX](MVP%20in%20JavaFX.md)
- [JDBC-Treiber einbinden](HowToAddJDBC.md)
- [Informationsblatt: User Stories](IB-User-Stories.md)

---

*Weiter mit [AB 02 — Datenschutzanalyse](AB02-Datenschutzanalyse.md)*
