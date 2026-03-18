# AB 02 — Datenschutz und NHPlus

> **Thema:** DSGVO im Kontext einer Pflegeheim-Anwendung
>
> **Sozialform:** Arbeitsteilung in der Gruppe — ein Gruppenmitglied kann parallel zu AB01 recherchieren
>
> **Zeitrahmen:** ~2-3 Unterrichtsstunden

**Nach Bearbeitung dieses Arbeitsblatts könnt ihr:**
- konkrete Datenschutzverstöße in einer bestehenden Anwendung identifizieren
- Verstöße den relevanten DSGVO-Artikeln zuordnen
- technische Anforderungen für eine datenschutzkonforme Software ableiten

## Vorbereitung: DSGVO-Grundlagen erarbeiten

Bearbeite **zuerst** die interaktive DSGVO-Webapp, um die notwendigen Grundlagen zu erarbeiten:

> **https://berndheidemann.github.io/dsgvo/**

Die dort vermittelten Inhalte bilden die Basis für die folgenden Aufgaben.

## Kontext: Besondere Kategorien personenbezogener Daten

NHPlus verwaltet Daten eines Pflegeheims. Pflegeheime verarbeiten **Gesundheitsdaten**, die laut Art. 9 DSGVO als *besondere Kategorien personenbezogener Daten* gelten. Das ist die **höchste Sensibilitätsstufe** — für die Verarbeitung gelten verschärfte Anforderungen.

Behaltet bei der folgenden Analyse im Hinterkopf: Es geht nicht nur um „Namen und Adressen", sondern um psychische Zustandsbeschreibungen, Pflegestufen und medizinische Behandlungsprotokolle.

## Aufgabe 1: Verstöße in NHPlus identifizieren

Analysiere die Anwendung NHPlus und ihren Quellcode. Untersuche die Anwendung dabei systematisch in den folgenden drei Bereichen. Gebt für jeden Verstoß an: **Was** verstößt, **wogegen** (DSGVO-Artikel) und **warum** es ein Problem ist.

### a) Sicherheitsmaßnahmen (Art. 32 DSGVO)

Untersucht, welche technischen Schutzmaßnahmen vorhanden oder **nicht** vorhanden sind:

- Wie ist der Zugang zur Anwendung geschützt?
- Wie sind die Daten in der Datenbank geschützt?
- Kann nachvollzogen werden, wer wann welche Daten eingesehen oder geändert hat?
- Können verschiedene Benutzer unterschiedliche Rechte haben?

### b) Grundprinzipien der Datenverarbeitung (Art. 5 DSGVO)

Untersucht, ob die Anwendung die Grundprinzipien einhält:

- **Datenminimierung:** Werden nur Daten erhoben, die für den Zweck notwendig sind? Gibt es überflüssige Felder?
- **Speicherbegrenzung:** Gibt es ein Konzept, wie lange Daten aufbewahrt werden? Werden Daten irgendwann gelöscht?
- **Transparenz:** Dokumentiert die Anwendung, welche Daten sie zu welchem Zweck verarbeitet?

### c) Betroffenenrechte (Art. 15-22 DSGVO)

Untersucht, ob Patienten ihre Rechte ausüben können:

- Kann ein Patient **Auskunft** über alle seine gespeicherten Daten erhalten (Art. 15)?
- Kann ein Patient die **Löschung** seiner Daten verlangen — und funktioniert das vollständig (Art. 17)?
- Können Daten in einem gängigen Format **exportiert** werden (Art. 20)?

## Aufgabe 2: Technische Anforderungen ableiten

Leite aus deinen Erkenntnissen aus der DSGVO-Webapp und Aufgabe 1 **für jeden gefundenen Verstoß eine konkrete technische Anforderung** ab, die NHPlus erfüllen muss, um datenschutzkonform zu sein.

Formuliere die Anforderungen so, dass sie als Grundlage für User Stories in [AB 03](AB03-User-Stories-Akzeptanzkriterien-Tasks-Testfaelle.md) dienen können.

---

## Relevante Ressourcen

- [AB 01 — Analyse der Architektur](AB01-Analyse-der-Architektur.md) (technischer Kontext)
- [AB 03 — User Stories & Planung](AB03-User-Stories-Akzeptanzkriterien-Tasks-Testfaelle.md) (eure Anforderungen fließen hier ein)

---

*Weiter mit [AB 03 — User Stories & Planung](AB03-User-Stories-Akzeptanzkriterien-Tasks-Testfaelle.md)*
