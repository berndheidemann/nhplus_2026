# AB 03 — User Stories, Akzeptanzkriterien, Tasks, Testfälle

> **Thema:** Planung der Erweiterung von NHPlus
>
> **Sozialform:** Gruppenarbeit (2-3 Personen)
>
> **Zeitrahmen:** ~3-4 Unterrichtsstunden

**Nach Bearbeitung dieses Arbeitsblatts könnt ihr:**
- User Stories mit Akzeptanzkriterien formulieren
- aus User Stories konkrete Entwicklungs-Tasks ableiten
- Testfälle aus Akzeptanzkriterien ableiten
- ein einfaches ER-Diagramm für eine neue Entität erstellen
- den Aufwand einer User Story grob einschätzen

> **Hinweis:** Zum Aufbau und zur Formulierung von User Stories siehe das [Informationsblatt: User Stories](IB-User-Stories.md). Dort findet ihr auch vollständige Beispiele zu den bereits implementierten Modulen (Patienten, Behandlungen).

## Aufgabenstellung

Plant innerhalb eurer Gruppe die Erweiterung von NHPlus. Dabei sind **zwei Bereiche** zu bearbeiten:

### 1. Pfleger-Verwaltung

NHPlus soll um ein vollständiges Modul zur Verwaltung von Pflegekräften erweitert werden (vgl. AB01, Aufgabe 2). Erstellt dafür User Stories, die mindestens das Anlegen, Anzeigen, Ändern und Löschen von Pflegekräften abdecken.

**Datenmodellierung:** Erstellt ein ER-Diagramm für die Pfleger-Tabelle und ihre Beziehung zu bestehenden Tabellen (Patient, Treatment). Leitet daraus das `CREATE TABLE`-Statement ab.

### 2. Datenschutz-Fixes

Für **drei Verstöße**, die ihr in [AB 02](AB02-Datenschutzanalyse.md) identifiziert habt, erstellt ihr eine User Story, die den Verstoß behebt. Eine davon muss die bisher fehlende Zugangsbeschränkung behandeln.

---

Für jede User Story:

1. Formuliert die **User Story** im Format: *Als \<Rolle\> möchte ich \<Funktionalität\>, um \<Nutzen\> zu erreichen.*
2. Definiert **Akzeptanzkriterien**, die festlegen, wann die User Story fertig implementiert ist.
3. Leitet **Tasks** ab — welche Klassen müssen neu erstellt, welche bestehenden Klassen angepasst werden?
4. Leitet aus den Akzeptanzkriterien **Testfälle** ab.

Teilt die User Stories so auf, dass **jedes Gruppenmitglied mindestens eine User Story verantwortet**.

---

## Vorlage

Für jede User Story ist die folgende Tabellenstruktur zu verwenden (für weitere User Stories kopieren):

### User Story

> Als \<Rolle\> möchte ich \<Funktionalität\>, um \<Nutzen\> zu erreichen.

### Akzeptanzkriterien

| Nr. | Kriterium |
|-----|-----------|
| A_1 | |
| A_2 | |
| ... | |

### Tasks

| Nr. | Task |
|-----|------|
| T_1 | |
| T_2 | |
| ... | |

### Aufwandsschätzung

| User Story | Geschätzte Stunden | Tatsächliche Stunden |
|---|---|---|
| US 1 | | *(nach AB 04 ausfüllen)* |
| US 2 | | *(nach AB 04 ausfüllen)* |

> **Hinweis:** Schätzt den Aufwand jeder User Story in Stunden. Am Ende von AB 04 tragt ihr die tatsächliche Zeit ein und vergleicht. Das Schätzen von Aufwänden ist eine wichtige Kompetenz in der Softwareentwicklung.

### Testfälle

**TF1:**

| | |
|---|---|
| **Vorbedingung** | |
| **Testschritte** | |
| **Erwartetes Ergebnis** | |

**TF2:**

| | |
|---|---|
| **Vorbedingung** | |
| **Testschritte** | |
| **Erwartetes Ergebnis** | |

---

## Relevante Ressourcen

- [Informationsblatt: User Stories](IB-User-Stories.md) — Erklärung und vollständige Beispiele
- [AB 01 — Analyse der Architektur](AB01-Analyse-der-Architektur.md) — technischer Kontext und Architekturverständnis
- [AB 02 — Datenschutzanalyse](AB02-Datenschutzanalyse.md) — eure identifizierten Verstöße und Anforderungen

---

*Weiter mit [AB 04 — Implementierung](AB04-Implementierung.md)*
