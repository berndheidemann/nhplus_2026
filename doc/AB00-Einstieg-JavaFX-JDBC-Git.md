# AB 00 — Einstieg: JavaFX, JDBC und Git

> **Themen:** JavaFX-Grundlagen, JDBC-Grundlagen, Git-Workflow
>
> **Sozialform:** Einzelarbeit, anschließend Partnerarbeit
>
> **Zeitrahmen:** ~3 Unterrichtsstunden

**Nach Bearbeitung dieses Arbeitsblatts könnt ihr:**
- ein einfaches JavaFX-Fenster mit Steuerelementen erstellen
- mit JDBC Daten aus einer SQLite-Datenbank lesen
- die grundlegenden Git-Befehle anwenden

> **Hinweis:** Dieses Arbeitsblatt bereitet euch auf das Hauptprojekt NHPlus vor.
> Ihr lernt hier die Technologien kennen, die ihr ab AB 01 braucht.

## Teil A: JavaFX — Hello World (~45 min)

### Vorbereitung

Erstellt in IntelliJ ein neues Maven-Projekt mit JavaFX-Unterstützung oder nutzt das
bereitgestellte Template-Projekt.

### Aufgabe

Erstellt ein JavaFX-Fenster mit folgenden Elementen:

1. Ein **Label**, das den Text „Willkommen" anzeigt.
2. Ein **TextField**, in das ein Name eingegeben werden kann.
3. Ein **Button** mit der Beschriftung „Begrüßen".
4. Wenn der Button geklickt wird, soll das Label den Text „Willkommen, [Name]!" anzeigen.

**Hinweise:**
- Erstellt eine FXML-Datei für die View und eine Controller-Klasse.
- Nutzt den SceneBuilder, um die FXML-Datei grafisch zu bearbeiten:
  1. Rechtsklick auf die FXML-Datei → *Open In SceneBuilder*
  2. Zieht Steuerelemente per Drag & Drop auf die Oberfläche.
  3. Vergebt `fx:id`-Bezeichner im Bereich *Code* (rechts).
  4. Tragt den Controller unter *Controller* (links unten) ein.
- Im Controller: Deklariert die Steuerelemente mit `@FXML` und der fx:id als Variablennamen.

### Ergebnis

Zeigt euer Fenster dem Sitznachbarn. Funktioniert die Begrüßung?

---

## Teil B: JDBC — Daten aus SQLite lesen (~45 min)

### Vorbereitung

Öffnet das NHPlus-Projekt und startet die Anwendung einmal, damit die Datenbank
`db/nursingHome.db` erstellt wird.

### Aufgabe

Erstellt eine Klasse `SimpleQuery` mit einer `main`-Methode, die:

1. Eine Verbindung zur Datenbank `db/nursingHome.db` aufbaut.
2. Alle Patienten aus der Tabelle `patient` liest.
3. Für jeden Patienten Vorname, Nachname und Pflegestufe auf der Konsole ausgibt.
4. Die Verbindung am Ende schließt.

**Hinweise:**
```java
// Verbindung aufbauen
Connection connection = DriverManager.getConnection("jdbc:sqlite:db/nursingHome.db");

// SQL-Abfrage ausführen
Statement statement = connection.createStatement();
ResultSet result = statement.executeQuery("SELECT firstname, surname, carelevel FROM patient");

// Ergebnisse durchlaufen
while (result.next()) {
    String firstName = result.getString("firstname");
    String surname = result.getString("surname");
    String careLevel = result.getString("carelevel");
    System.out.println(firstName + " " + surname + " (Pflegestufe: " + careLevel + ")");
}

// Verbindung schließen
result.close();
statement.close();
connection.close();
```

### Ergebnis

Auf der Konsole sollte z.B. stehen:
```
Seppl Herberger (Pflegestufe: 4)
Martina Gerdsen (Pflegestufe: 5)
...
```

**Reflexionsfrage:** Was passiert, wenn ihr `result.getString("firstname")` durch
`result.getString(1)` ersetzt? Was ist robuster und warum?

---

## Teil C: Git — Grundlagen (~45 min)

### Vorbereitung

Stellt sicher, dass Git in IntelliJ konfiguriert ist (*File → Settings → Version Control → Git*).

### Die 5 wichtigsten Git-Befehle

| Befehl | Bedeutung |
|--------|-----------|
| `git status` | Zeigt geänderte/neue Dateien an |
| `git add <Datei>` | Nimmt Änderungen in die Staging-Area auf |
| `git commit -m "Nachricht"` | Speichert die Staging-Area als neuen Commit |
| `git push` | Lädt lokale Commits auf den Server hoch |
| `git pull` | Holt Änderungen vom Server und integriert sie |

### Aufgabe

1. Öffnet das Terminal in IntelliJ (*View → Tool Windows → Terminal*).
2. Führt `git status` aus. Was seht ihr?
3. Erstellt eine Datei `TEAM.md` im Projektverzeichnis mit euren Namen.
4. Führt `git add TEAM.md` und `git commit -m "Füge Team-Datei hinzu"` aus.
5. **Partnerarbeit:** Arbeitet zu zweit am gleichen Repository.
   - Person A ändert `TEAM.md` und committet.
   - Person B ändert dieselbe Datei und committet.
   - Person B führt `git pull` aus. Was passiert? Löst den Merge-Konflikt gemeinsam.

### Ergebnis

Ihr habt einen Merge-Konflikt gelöst. Das wird euch bei der Gruppenarbeit in AB 04 helfen!

> **Tipp für AB 04:** Erstellt für jede User Story einen eigenen Branch:
> `git checkout -b feature/pfleger-modul`. So vermeidet ihr die meisten Konflikte.

---

## Relevante Ressourcen

- [SceneBuilder Download](https://gluonhq.com/products/scene-builder/#download)
- [SQLite SQL-Dialekt](https://www.sqlite.org/lang.html)
- [Git-Dokumentation](https://git-scm.com/doc)

---

*Weiter mit [AB 01 — Analyse der Architektur](AB01-Analyse-der-Architektur.md)*
