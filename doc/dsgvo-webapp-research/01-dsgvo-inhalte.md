# DSGVO-Inhalte fuer die interaktive Lern-Webseite

> Zielgruppe: 11. Klasse IT-Ausbildung (Fachinformatiker, IT-Kaufleute)
> Fokus: Allgemeine DSGVO-Grundlagen, nicht NHPlus-spezifisch
> Quellen: dsgvo-gesetz.de, dejure.org, BfDI, Stiftung Datenschutz

---

## Inhaltspriorisierung

Die Artikel sind in zwei Kategorien eingeteilt:

| Prioritaet | Artikel | Begruendung |
|------------|---------|-------------|
| **Kern** | Art. 5, Art. 6, Art. 9, Art. 15, Art. 17, Art. 25, Art. 32 | Zentral fuer das Verstaendnis und direkt relevant fuer NHPlus (Gesundheitsdaten, Loeschkonzept, TOMs) |
| **Vertiefung** | Art. 16, Art. 18, Art. 20, Art. 21, Art. 22 | Wichtig fuer Gesamtbild, aber fuer NHPlus-Transfer weniger kritisch. Werden ueber den Betroffenenrechte-Kompass (optionales Widget) abgedeckt |

In der Webseite werden die **Kern-Artikel** in den Pflicht-Widgets behandelt. Die **Vertiefungs-Artikel** erscheinen im optionalen Betroffenenrechte-Kompass und in der Tell-Phase als Uebersichtstabelle.

---

## Artikel-Vernetzung

Die DSGVO-Artikel stehen nicht isoliert nebeneinander, sondern bilden ein Normgeflecht:

```
Art. 5 (Grundsaetze) ─── ist die uebergeordnete Klammer
  ├── Art. 5a (Rechtmaessigkeit)  ──→  konkretisiert durch Art. 6 (Rechtsgrundlagen)
  ├── Art. 5a (Transparenz)       ──→  konkretisiert durch Art. 12-14 (Informationspflichten)
  ├── Art. 5c (Datenminimierung)  ──→  konkretisiert durch Art. 25 (Privacy by Design)
  ├── Art. 5d (Richtigkeit)       ──→  ermoeglicht durch Art. 16 (Berichtigungsrecht)
  ├── Art. 5e (Speicherbegrenzung)──→  ermoeglicht durch Art. 17 (Loeschrecht)
  └── Art. 5f (Integritaet)       ──→  konkretisiert durch Art. 32 (TOMs)

Art. 9 (Besondere Kategorien) ──→  verschaerft Art. 6 fuer sensible Daten
Art. 15-22 (Betroffenenrechte) ──→  setzen Art. 5a (Transparenz) + 5d (Richtigkeit) um
```

Diese Zusammenhaenge werden in Kapitel 5 (Lebenszyklus-Timeline) als interaktives Beziehungsdiagramm visualisiert.

---

## 1. Art. 5 DSGVO -- Grundsaetze der Datenverarbeitung *(Kern)*

### Ueberblick

Art. 5 ist das "Grundgesetz" der DSGVO. Er definiert sechs Grundprinzipien, die **bei jeder Verarbeitung** personenbezogener Daten eingehalten werden muessen. Dazu kommt die Rechenschaftspflicht: Der Verantwortliche muss die Einhaltung nicht nur sicherstellen, sondern auch **nachweisen** koennen.

### Die sechs Grundsaetze im Detail

#### a) Rechtmaessigkeit, Treu und Glauben, Transparenz

**Erklaerung:** Daten duerfen nur auf Basis einer Rechtsgrundlage (siehe Art. 6) verarbeitet werden. Die Verarbeitung muss fair und fuer die betroffene Person nachvollziehbar sein.

**Beispiele:**
- Ein Online-Shop muss in seiner Datenschutzerklaerung klar erklaeren, welche Daten er erhebt und warum.
- Eine Fitness-App darf nicht heimlich Standortdaten tracken, ohne das transparent zu kommunizieren.
- Eine Schule muss Eltern informieren, wenn sie ein digitales Klassenbuch einfuehrt.

**Gesetzestext-Auszug:**
> Personenbezogene Daten muessen auf rechtmaessige Weise, nach Treu und Glauben und in einer fuer die betroffene Person nachvollziehbaren Weise verarbeitet werden.

**Idee fuer interaktive Umsetzung:** "Transparenz-Check" -- Die Schueler bekommen Screenshots von echten (anonymisierten) Datenschutzerklaerungen und muessen bewerten: Ist das verstaendlich? Was fehlt? Was ist unklar formuliert?

---

#### b) Zweckbindung

**Erklaerung:** Daten duerfen nur fuer den Zweck verwendet werden, fuer den sie urspruenglich erhoben wurden. Eine Zweckentfremdung ist verboten.

**Beispiele:**
- Eine Arztpraxis erhebt Gesundheitsdaten zur Behandlung -- darf diese nicht fuer Werbezwecke nutzen.
- Ein Online-Shop erhebt die E-Mail-Adresse fuer die Bestellbestaetigung -- darf sie nicht automatisch fuer den Newsletter verwenden.
- Eine Schule erhebt Kontaktdaten fuer Notfaelle -- darf diese nicht an Unternehmen fuer Berufsmessen weitergeben.

**Gesetzestext-Auszug:**
> Personenbezogene Daten muessen fuer festgelegte, eindeutige und legitime Zwecke erhoben werden und duerfen nicht in einer mit diesen Zwecken nicht zu vereinbarenden Weise weiterverarbeitet werden.

**Idee fuer interaktive Umsetzung:** "Zweck-Zuordnung" -- Drag-and-Drop-Spiel: Verschiedene Datenverarbeitungen muessen dem richtigen Zweck zugeordnet werden. Falsche Zuordnungen werden rot markiert und erklaert, warum das ein Verstoss waere.

---

#### c) Datenminimierung

**Erklaerung:** Es duerfen nur so viele Daten erhoben werden, wie fuer den jeweiligen Zweck tatsaechlich notwendig sind. "So wenig wie moeglich, so viel wie noetig."

**Beispiele:**
- Eine Fitness-App braucht fuer einen Schrittzaehler keine Religionszugehoerigkeit.
- Ein Newsletter-Dienst braucht nur die E-Mail-Adresse, nicht Geburtsdatum, Adresse und Telefonnummer.
- Eine Bewerbungsplattform darf nicht nach dem Familienstand fragen, wenn das fuer die Stelle irrelevant ist.

**Gesetzestext-Auszug:**
> Personenbezogene Daten muessen dem Zweck angemessen und erheblich sowie auf das fuer die Zwecke der Verarbeitung notwendige Mass beschraenkt sein.

**Idee fuer interaktive Umsetzung:** "Formular-Redesign" -- Die Schueler sehen ein ueberladenes Registrierungsformular (z.B. fuer einen einfachen Newsletter) und muessen entscheiden: Welche Felder sind wirklich noetig? Welche sind ueberfluessig? Sie koennen Felder streichen und erhalten Feedback.

---

#### d) Richtigkeit

**Erklaerung:** Personenbezogene Daten muessen sachlich richtig und aktuell sein. Falsche Daten muessen korrigiert oder geloescht werden.

**Beispiele:**
- Wenn ein Patient umzieht, muss die Arztpraxis die Adresse aktualisieren.
- Ein Social-Media-Profil zeigt eine falsche Altersangabe -- der Nutzer muss das korrigieren koennen.
- Eine Schule muss die Kontaktdaten von Erziehungsberechtigten aktuell halten.

**Gesetzestext-Auszug:**
> Personenbezogene Daten muessen sachlich richtig und erforderlichenfalls auf dem neuesten Stand sein; es sind alle angemessenen Massnahmen zu treffen, damit personenbezogene Daten, die im Hinblick auf die Zwecke ihrer Verarbeitung unrichtig sind, unverzueglich geloescht oder berichtigt werden.

**Idee fuer interaktive Umsetzung:** "Datenbank-Audit" -- Die Schueler sehen eine fiktive Patientendatenbank mit offensichtlichen Fehlern (veraltete Adressen, doppelte Eintraege, falsche Schreibweisen) und muessen die Probleme identifizieren.

---

#### e) Speicherbegrenzung

**Erklaerung:** Daten duerfen nur so lange gespeichert werden, wie sie fuer den urspruenglichen Zweck benoetigt werden. Danach muessen sie geloescht oder anonymisiert werden.

**Beispiele:**
- Ein Online-Shop muss Kundendaten nach Ablauf der gesetzlichen Aufbewahrungsfristen loeschen.
- Eine Bewerbung, die abgelehnt wurde, darf nur fuer eine begrenzte Zeit (ca. 6 Monate) gespeichert werden.
- Videoaufnahmen einer Ueberwachungskamera in einem Geschaeft sollten nach wenigen Tagen automatisch ueberschrieben werden.

**Gesetzestext-Auszug:**
> Personenbezogene Daten muessen in einer Form gespeichert werden, die die Identifizierung der betroffenen Personen nur so lange ermoeglicht, wie es fuer die Zwecke, fuer die sie verarbeitet werden, erforderlich ist.

**Idee fuer interaktive Umsetzung:** "Zeitstrahl-Challenge" -- Verschiedene Datensaetze auf einem Zeitstrahl: Die Schueler muessen entscheiden, ab wann welche Daten geloescht werden muessen. Z.B. Bewerbungsdaten, Rechnungen, Videoaufnahmen, Arztberichte.

---

#### f) Integritaet und Vertraulichkeit

**Erklaerung:** Daten muessen durch technische und organisatorische Massnahmen vor unbefugtem Zugriff, Verlust und Zerstoerung geschuetzt werden.

**Beispiele:**
- Eine Arztpraxis verschluesselt Patientendaten auf dem Server.
- Ein Online-Shop nutzt HTTPS fuer die Datenuebertragung.
- Ein Unternehmen hat ein Berechtigungskonzept: Nicht jeder Mitarbeiter hat Zugriff auf alle Kundendaten.

**Gesetzestext-Auszug:**
> Personenbezogene Daten muessen in einer Weise verarbeitet werden, die eine angemessene Sicherheit der personenbezogenen Daten gewaehrleistet, einschliesslich Schutz vor unbefugter oder unrechtmaessiger Verarbeitung und vor unbeabsichtigtem Verlust, unbeabsichtigter Zerstoerung oder unbeabsichtigter Schaedigung durch geeignete technische und organisatorische Massnahmen.

**Idee fuer interaktive Umsetzung:** "Sicherheits-Szenario" -- Die Schueler sehen ein Buero-Setup (Bildschirm sichtbar vom Flur, Post-it mit Passwort am Monitor, offener Aktenschrank) und muessen alle Sicherheitsluecken finden und Verbesserungen vorschlagen.

---

### Rechenschaftspflicht (Art. 5 Abs. 2)

**Erklaerung:** Der Verantwortliche muss nicht nur die Grundsaetze einhalten, sondern auch **beweisen koennen**, dass er sie einhaelt. Das bedeutet: Dokumentation, Protokollierung, Nachvollziehbarkeit.

**Gesetzestext-Auszug:**
> Der Verantwortliche ist fuer die Einhaltung des Absatzes 1 verantwortlich und muss dessen Einhaltung nachweisen koennen ("Rechenschaftspflicht").

---

## 2. Art. 6 DSGVO -- Rechtmaessigkeit der Verarbeitung *(Kern)*

### Ueberblick

Art. 6 ist die zentrale Norm fuer die Frage: **Darf ich diese Daten ueberhaupt verarbeiten?** Die DSGVO folgt dem Prinzip "Verbot mit Erlaubnisvorbehalt" -- jede Datenverarbeitung ist grundsaetzlich verboten, es sei denn, es gibt eine Rechtsgrundlage.

### Die sechs Rechtsgrundlagen

#### a) Einwilligung

**Erklaerung:** Die betroffene Person hat freiwillig, informiert und eindeutig zugestimmt. Die Einwilligung muss jederzeit widerrufbar sein.

**Beispiele:**
- Cookie-Banner: "Ich stimme der Verwendung von Analyse-Cookies zu."
- Newsletter-Anmeldung mit Double-Opt-In (Bestaetigungsmail).
- Ein Patient unterschreibt eine Einwilligungserklaerung fuer eine klinische Studie.

**Idee fuer interaktive Umsetzung:** "Einwilligungs-Designer" -- Die Schueler gestalten ein DSGVO-konformes Cookie-Banner. Kriterien: Freiwilligkeit, Informiertheit, Widerrufbarkeit, kein Dark Pattern.

---

#### b) Vertragserfullung

**Erklaerung:** Die Verarbeitung ist noetig, um einen Vertrag zu erfuellen oder vorvertragliche Massnahmen durchzufuehren.

**Beispiele:**
- Ein Online-Shop braucht die Lieferadresse, um eine Bestellung auszuliefern.
- Ein Arbeitgeber verarbeitet Bankdaten, um das Gehalt zu ueberweisen.
- Eine Versicherung braucht Gesundheitsdaten fuer den Abschluss einer Krankenversicherung.

---

#### c) Rechtliche Verpflichtung

**Erklaerung:** Die Verarbeitung ist notwendig, weil ein Gesetz es vorschreibt.

**Beispiele:**
- Steuerrecht: Ein Unternehmen muss Rechnungsdaten 10 Jahre aufbewahren.
- Arbeitsrecht: Arbeitgeber muessen Lohnabrechnungen dokumentieren.
- Infektionsschutzgesetz: Aerzte muessen bestimmte Krankheiten melden.

---

#### d) Lebenswichtige Interessen

**Erklaerung:** Die Verarbeitung ist noetig, um das Leben einer Person zu schuetzen. Kommt selten vor und nur in Notfaellen.

**Beispiele:**
- Ein bewusstloser Patient wird in die Notaufnahme eingeliefert -- seine Daten werden verarbeitet, obwohl er nicht einwilligen kann.
- Beim einem schweren Unfall werden Blutgruppe und Allergien ohne Einwilligung abgerufen.

---

#### e) Oeffentliches Interesse / Oeffentliche Gewalt

**Erklaerung:** Die Verarbeitung ist fuer eine Aufgabe im oeffentlichen Interesse oder in Ausuebung oeffentlicher Gewalt noetig.

**Beispiele:**
- Eine Behoerde verarbeitet Daten fuer die Steuerverwaltung.
- Ein oeffentliches Gesundheitsamt erfasst Daten zur Pandemiebekaempfung.
- Die Polizei verarbeitet Daten zur Strafverfolgung.

---

#### f) Berechtigtes Interesse

**Erklaerung:** Die Verarbeitung dient einem berechtigten Interesse des Verantwortlichen, solange die Interessen der betroffenen Person nicht ueberwiegen. Erfordert immer eine **Interessenabwaegung**.

**Beispiele:**
- Ein Unternehmen installiert Videoueberwachung zum Schutz vor Einbruch (aber: Abwaegung mit Privatsphaere der Mitarbeiter).
- Direktwerbung an Bestandskunden (aber: mit Widerspruchsmoeglichkeit).
- IT-Sicherheitsmassnahmen wie das Loggen von IP-Adressen.

**Idee fuer interaktive Umsetzung:** "Rechtsgrundlagen-Finder" -- Die Schueler bekommen verschiedene Szenarien praesentiert und muessen die passende Rechtsgrundlage aus Art. 6 auswaehlen und begruenden. Bei "berechtigtem Interesse" muessen sie zusaetzlich eine Interessenabwaegung durchfuehren.

---

### Gesetzestext-Auszug (Art. 6 Abs. 1)

> Die Verarbeitung ist nur rechtmaessig, wenn mindestens eine der nachstehenden Bedingungen erfuellt ist:
> a) Die betroffene Person hat ihre Einwilligung zu der Verarbeitung der sie betreffenden personenbezogenen Daten fuer einen oder mehrere bestimmte Zwecke gegeben;
> b) die Verarbeitung ist fuer die Erfuellung eines Vertrags [...] erforderlich;
> c) die Verarbeitung ist zur Erfuellung einer rechtlichen Verpflichtung erforderlich;
> d) die Verarbeitung ist erforderlich, um lebenswichtige Interessen [...] zu schuetzen;
> e) die Verarbeitung ist fuer die Wahrnehmung einer Aufgabe erforderlich, die im oeffentlichen Interesse liegt;
> f) die Verarbeitung ist zur Wahrung der berechtigten Interessen des Verantwortlichen [...] erforderlich, sofern nicht die Interessen [...] der betroffenen Person [...] ueberwiegen.

---

## 3. Art. 9 DSGVO -- Besondere Kategorien personenbezogener Daten *(Kern)*

### Ueberblick

Art. 9 schuetzt besonders sensible Daten mit einem **generellen Verarbeitungsverbot**. Der Schutz geht ueber den von Art. 6 hinaus, weil diese Daten ein besonders hohes Diskriminierungspotenzial haben.

### Was sind besondere Kategorien?

- Rassische und ethnische Herkunft
- Politische Meinungen
- Religioese oder weltanschauliche Ueberzeugungen
- Gewerkschaftszugehoerigkeit
- **Genetische Daten**
- **Biometrische Daten** (zur eindeutigen Identifizierung)
- **Gesundheitsdaten**
- Daten zum Sexualleben oder der sexuellen Orientierung

### Warum sind Gesundheitsdaten besonders geschuetzt?

Gesundheitsdaten sind besonders schuetzenswert, weil:
- Sie intime Informationen ueber den koerperlichen und psychischen Zustand einer Person enthalten.
- Sie bei Bekanntwerden zu Diskriminierung fuehren koennen (z.B. bei Versicherungen, Arbeitgebern).
- Sie nicht rueckgaengig gemacht werden koennen -- eine bekannt gewordene Diagnose kann nicht "vergessen" werden.
- Der Begriff "Gesundheitsdaten" ist sehr weit gefasst: Er umfasst nicht nur medizinische Diagnosen, sondern auch Fitnessdaten, Allergien, Brillenstaerke, psychische Befunde etc.

**Beispiele fuer Gesundheitsdaten:**
- Diagnosen und Behandlungsplaene in einer Arztpraxis
- Herzfrequenz und Schlafdaten einer Smartwatch
- Allergien, die in der Schulkantine dokumentiert werden

### Ausnahmen vom Verbot (Art. 9 Abs. 2)

Die Verarbeitung ist trotz des generellen Verbots erlaubt bei:
1. **Ausdrueckliche Einwilligung** der betroffenen Person
2. **Arbeits- und Sozialrecht** (z.B. Krankmeldungen an den Arbeitgeber)
3. **Schutz lebenswichtiger Interessen** (Notfall, Person kann nicht einwilligen)
4. **Verarbeitung durch gemeinnuetzige Organisationen** (nur fuer Mitglieder)
5. **Offensichtlich oeffentlich gemachte Daten**
6. **Rechtsansprueche** geltend machen
7. **Erhebliches oeffentliches Interesse**
8. **Gesundheitsvorsorge und medizinische Versorgung** (durch Fachpersonal mit Schweigepflicht)
9. **Oeffentliche Gesundheit** (z.B. Pandemiebekaempfung)
10. **Archiv-, Forschungs- und Statistikzwecke**

### Gesetzestext-Auszug (Art. 9 Abs. 1)

> Die Verarbeitung personenbezogener Daten, aus denen die rassische und ethnische Herkunft, politische Meinungen, religioese oder weltanschauliche Ueberzeugungen oder die Gewerkschaftszugehoerigkeit hervorgehen, sowie die Verarbeitung von genetischen Daten, biometrischen Daten zur eindeutigen Identifizierung einer natuerlichen Person, Gesundheitsdaten oder Daten zum Sexualleben oder der sexuellen Orientierung einer natuerlichen Person ist untersagt.

### Idee fuer interaktive Umsetzung

**"Daten-Klassifizierer"** -- Die Schueler bekommen eine Liste von Datenfeldern (Name, E-Mail, Blutgruppe, Parteimitgliedschaft, Fingerabdruck, Gehalt, Diagnose, Lieblings-Pizza) und muessen sie klassifizieren: "normale" personenbezogene Daten vs. besondere Kategorien nach Art. 9. Bei jedem Feld erscheint eine Erklaerung.

---

## 4. Art. 12-22 DSGVO -- Betroffenenrechte *(Kern: Art. 15, 17 | Vertiefung: Art. 16, 18, 20, 21, 22)*

### Ueberblick

Kapitel III der DSGVO (Art. 12-22) gibt betroffenen Personen umfangreiche Rechte gegenueber den Verantwortlichen. Art. 12 regelt die allgemeinen Modalitaeten (Frist: 1 Monat, kostenlos, verstaendliche Sprache). Art. 13-22 definieren die einzelnen Rechte.

---

### Art. 15 -- Auskunftsrecht

**Erklaerung:** Jede Person kann von jedem Unternehmen erfahren, ob und welche Daten ueber sie gespeichert sind, zu welchem Zweck, an wen sie weitergegeben wurden und wie lange sie gespeichert werden.

**Beispiele:**
- Du fragst Facebook: "Welche Daten habt ihr ueber mich?" -- Facebook muss innerhalb eines Monats antworten.
- Ein Patient fragt seine Arztpraxis nach einer vollstaendigen Kopie seiner Patientenakte.
- Ein Mitarbeiter fragt die Personalabteilung, welche Daten ueber ihn gespeichert sind.

**Gesetzestext-Auszug:**
> Die betroffene Person hat das Recht, von dem Verantwortlichen eine Bestaetigung darueber zu verlangen, ob sie betreffende personenbezogene Daten verarbeitet werden; ist dies der Fall, so hat sie ein Recht auf Auskunft ueber diese personenbezogenen Daten und auf folgende Informationen: die Verarbeitungszwecke; die Kategorien personenbezogener Daten, die verarbeitet werden; die Empfaenger [...]

**Idee fuer interaktive Umsetzung:** "Auskunfts-Simulator" -- Die Schueler verfassen ein Auskunftsersuchen an ein fiktives Unternehmen. Dann wechseln sie die Rolle und muessen als Unternehmen pruefen, welche Informationen sie liefern muessen.

---

### Art. 16 -- Recht auf Berichtigung

**Erklaerung:** Wenn Daten falsch oder unvollstaendig sind, hat die betroffene Person das Recht, die Korrektur zu verlangen.

**Beispiele:**
- Dein Name ist bei der Krankenkasse falsch geschrieben -- du kannst die Berichtigung verlangen.
- Eine Schufa-Auskunft enthaelt einen falschen Eintrag -- du kannst die Korrektur fordern.
- Im Schulverwaltungssystem steht eine falsche Adresse -- die Eltern koennen die Berichtigung verlangen.

---

### Art. 17 -- Recht auf Loeschung ("Recht auf Vergessenwerden")

**Erklaerung:** Unter bestimmten Umstaenden kann eine Person verlangen, dass ihre Daten geloescht werden. Besonders bekannt als "Recht auf Vergessenwerden" im Internet.

**Wann besteht das Recht?**
- Daten sind fuer den Zweck nicht mehr noetig.
- Einwilligung wurde widerrufen.
- Widerspruch wurde eingelegt (ohne vorrangige Gruende dagegen).
- Daten wurden unrechtmaessig verarbeitet.
- Rechtliche Loeschpflicht besteht.

**Wann besteht das Recht NICHT?**
- Zur Ausuebung der Meinungsfreiheit.
- Zur Erfuellung einer rechtlichen Pflicht.
- Aus Gruenden der oeffentlichen Gesundheit.
- Fuer Archiv- oder Forschungszwecke.
- Zur Geltendmachung von Rechtsanspruechen.

**Beispiele:**
- Du loeschst dein Social-Media-Konto -- das Unternehmen muss deine Daten tatsaechlich loeschen (nicht nur deaktivieren).
- Ein veralteter Zeitungsartikel ueber dich in Google -- du kannst die Entfernung aus den Suchergebnissen verlangen.
- Ein ehemaliger Kunde verlangt von einem Online-Shop die Loeschung seines Kontos und aller Bestelldaten (aber: Aufbewahrungsfristen fuer Rechnungen beachten!).

**Gesetzestext-Auszug:**
> Die betroffene Person hat das Recht, von dem Verantwortlichen zu verlangen, dass sie betreffende personenbezogene Daten unverzueglich geloescht werden, und der Verantwortliche ist verpflichtet, personenbezogene Daten unverzueglich zu loeschen, sofern einer der folgenden Gruende zutrifft [...]

**Idee fuer interaktive Umsetzung:** "Loeschungs-Dilemma" -- Die Schueler bekommen Loeschanfragen und muessen entscheiden: Muss geloescht werden? Darf nicht geloescht werden (z.B. wegen gesetzlicher Aufbewahrungspflicht)? Sie muessen ihre Entscheidung begruenden.

---

### Art. 18 -- Recht auf Einschraenkung der Verarbeitung

**Erklaerung:** Wenn die Richtigkeit der Daten bestritten wird oder die Verarbeitung unrechtmaessig ist, kann die betroffene Person verlangen, dass die Daten "eingefroren" werden -- gespeichert, aber nicht mehr aktiv verarbeitet.

**Beispiel:**
- Ein Kunde bestreitet, dass seine gespeicherte Adresse richtig ist. Waehrend der Klaerung darf das Unternehmen die Daten nicht fuer Werbung nutzen, aber muss sie aufbewahren.

---

### Art. 20 -- Recht auf Datenuebertragbarkeit

**Erklaerung:** Betroffene koennen ihre Daten in einem strukturierten, gaengigen und maschinenlesbaren Format erhalten und an einen anderen Anbieter uebertragen.

**Beispiele:**
- Du wechselst von Spotify zu Apple Music und willst deine Playlists mitnehmen.
- Du wechselst den Arzt und willst deine Gesundheitsdaten digital mitnehmen.
- Du wechselst die Bank und willst deine Kontobewegungen exportieren.

**Idee fuer interaktive Umsetzung:** "Datenumzug-Simulation" -- Die Schueler simulieren einen Anbieterwechsel: Welche Daten kann ich mitnehmen? In welchem Format? Was muss der alte Anbieter liefern?

---

### Art. 21 -- Widerspruchsrecht

**Erklaerung:** Betroffene koennen der Verarbeitung ihrer Daten widersprechen, besonders bei Direktwerbung (hier gilt der Widerspruch immer!). Bei anderen Verarbeitungen muss eine Interessenabwaegung stattfinden.

**Beispiele:**
- Du bekommst Werbung per Post -- ein Widerspruch muss sofort beachtet werden.
- Du wirst von einer Auskunftei bewertet (Scoring) und legst Widerspruch ein.
- Ein Mitarbeiter widerspricht der GPS-Ortung seines Dienstwagens.

---

### Art. 22 -- Automatisierte Einzelentscheidungen / Profiling

**Erklaerung:** Niemand darf einer Entscheidung unterworfen werden, die ausschliesslich auf automatisierter Verarbeitung beruht und die erhebliche Auswirkungen hat, es sei denn, es gibt Ausnahmen (Vertrag, Gesetz, Einwilligung mit Schutzmassnahmen).

**Beispiele:**
- Ein Kreditantrag wird automatisch abgelehnt, ohne dass ein Mensch draufgeschaut hat -- dagegen kann man sich wehren.
- Ein Algorithmus sortiert Bewerbungen aus -- die Betroffenen haben das Recht, eine menschliche Ueberpruefung zu verlangen.

**Idee fuer interaktive Umsetzung:** "Betroffenenrechte-Kompass" -- Ein interaktives Entscheidungstool: "Was ist dein Problem?" -> Der Schueler wird durch Fragen gefuehrt und erhaelt am Ende den passenden Artikel und ein Muster-Schreiben.

---

## 5. Art. 25 DSGVO -- Privacy by Design und Privacy by Default *(Kern)*

### Ueberblick

Art. 25 verlangt, dass Datenschutz **von Anfang an** in die Entwicklung von Systemen eingebaut wird (by Design) und dass die Voreinstellungen **datenschutzfreundlich** sind (by Default).

### Privacy by Design (Datenschutz durch Technikgestaltung)

**Erklaerung:** Schon bei der Planung und Entwicklung eines Systems muessen Datenschutzmassnahmen beruecksichtigt werden -- nicht erst nachtraeglich als Flickwerk.

**Beispiele:**
- Eine App wird so programmiert, dass sie Standortdaten nur waehrend der aktiven Nutzung erfasst, nicht im Hintergrund.
- Ein Krankenhaus-IT-System speichert Patientendaten von Anfang an verschluesselt, nicht erst nach dem ersten Datenleck.
- Ein Kontaktformular auf einer Website erhebt nur Name und E-Mail -- nicht automatisch auch IP-Adresse, Browser-Version und Standort.

### Privacy by Default (Datenschutzfreundliche Voreinstellungen)

**Erklaerung:** Die Standard-Einstellungen eines Systems muessen die datenschutzfreundlichste Option sein. Der Nutzer muss aktiv mehr Datenverarbeitung erlauben, nicht aktiv weniger einschraenken.

**Beispiele:**
- Ein Social-Media-Profil ist bei der Erstellung standardmaessig "privat", nicht "oeffentlich".
- Cookie-Einstellungen sind standardmaessig auf "nur notwendige Cookies", nicht auf "alle akzeptieren".
- Eine Fitness-App teilt standardmaessig keine Daten mit Drittanbietern.

### Gesetzestext-Auszug (Art. 25 Abs. 1 -- gekuerzt)

> Unter Beruecksichtigung des Stands der Technik, der Implementierungskosten und der Art, des Umfangs, der Umstaende und der Zwecke der Verarbeitung [...] trifft der Verantwortliche sowohl zum Zeitpunkt der Festlegung der Mittel fuer die Verarbeitung als auch zum Zeitpunkt der eigentlichen Verarbeitung geeignete technische und organisatorische Massnahmen [...], die dafuer ausgelegt sind, die Datenschutzgrundsaetze wie etwa Datenminimierung wirksam umzusetzen und die notwendigen Garantien in die Verarbeitung aufzunehmen.

### Gesetzestext-Auszug (Art. 25 Abs. 2 -- gekuerzt)

> Der Verantwortliche trifft geeignete technische und organisatorische Massnahmen, die sicherstellen, dass durch Voreinstellung nur personenbezogene Daten, deren Verarbeitung fuer den jeweiligen bestimmten Verarbeitungszweck erforderlich ist, verarbeitet werden.

### Idee fuer interaktive Umsetzung

**"App-Einstellungs-Audit"** -- Die Schueler bekommen die Einstellungsseiten verschiedener (fiktiver) Apps gezeigt. Sie muessen bewerten: Welche Voreinstellungen sind DSGVO-konform (Privacy by Default)? Welche nicht? Sie koennen die Einstellungen "umkonfigurieren" und erhalten ein Bewertungsergebnis.

---

## 6. Art. 32 DSGVO -- Sicherheit der Verarbeitung (TOMs) *(Kern)*

### Ueberblick

Art. 32 verpflichtet Verantwortliche und Auftragsverarbeiter, **technische und organisatorische Massnahmen (TOMs)** zu treffen, um personenbezogene Daten angemessen zu schuetzen. Das Schutzniveau muss dem Risiko angemessen sein.

### Die vier Schutzziele

1. **Vertraulichkeit:** Nur befugte Personen duerfen auf die Daten zugreifen.
2. **Integritaet:** Daten duerfen nicht unbefugt veraendert werden.
3. **Verfuegbarkeit:** Daten muessen verfuegbar sein, wenn sie gebraucht werden.
4. **Belastbarkeit:** Systeme muessen auch unter Last oder bei Angriffen funktionieren.

### Konkrete Massnahmen laut Art. 32

#### a) Pseudonymisierung und Verschluesselung

**Pseudonymisierung:** Daten werden so veraendert, dass sie ohne zusaetzliche Informationen keiner Person mehr zugeordnet werden koennen.
- Beispiel: In einer Forschungsdatenbank wird der Patientenname durch eine ID ersetzt. Die Zuordnungstabelle wird separat und gesichert aufbewahrt.

**Verschluesselung:** Daten werden so umgewandelt, dass sie ohne den passenden Schluessel unlesbar sind.
- Beispiel: E-Mails werden mit Ende-zu-Ende-Verschluesselung gesendet. Selbst wenn sie abgefangen werden, kann niemand den Inhalt lesen.

#### b) Vertraulichkeit, Integritaet, Verfuegbarkeit und Belastbarkeit

- Zugriffskontrollen (Wer darf was sehen?)
- Firewalls und Virenschutz
- Regelmaessige Updates und Patches
- Schulung der Mitarbeiter

#### c) Rasche Wiederherstellung nach Zwischenfaellen

- Backups und Wiederherstellungsplaene
- Redundante Systeme
- Notfallplaene

#### d) Regelmaessige Ueberpruefung

- Penetrationstests
- Datenschutz-Audits
- Regelmaessige Risikobewertungen

### Organisatorische Massnahmen (Beispiele)

- Verpflichtung der Mitarbeiter auf Vertraulichkeit
- Schulungen zum Datenschutz
- Clean-Desk-Policy (keine sensiblen Dokumente offen auf dem Schreibtisch)
- Besucherregelungen
- Vier-Augen-Prinzip bei besonders sensiblen Vorgaengen

### Gesetzestext-Auszug (Art. 32 Abs. 1)

> Unter Beruecksichtigung des Stands der Technik, der Implementierungskosten und der Art, des Umfangs, der Umstaende und der Zwecke der Verarbeitung sowie der unterschiedlichen Eintrittswahrscheinlichkeit und Schwere des Risikos fuer die Rechte und Freiheiten natuerlicher Personen treffen der Verantwortliche und der Auftragsverarbeiter geeignete technische und organisatorische Massnahmen, um ein dem Risiko angemessenes Schutzniveau zu gewaehrleisten; diese Massnahmen schliessen gegebenenfalls unter anderem Folgendes ein:
> a) die Pseudonymisierung und Verschluesselung personenbezogener Daten;
> b) die Faehigkeit, die Vertraulichkeit, Integritaet, Verfuegbarkeit und Belastbarkeit der Systeme und Dienste im Zusammenhang mit der Verarbeitung auf Dauer sicherzustellen;
> c) die Faehigkeit, die Verfuegbarkeit der personenbezogenen Daten und den Zugang zu ihnen bei einem physischen oder technischen Zwischenfall rasch wiederherzustellen;
> d) ein Verfahren zur regelmaessigen Ueberpruefung, Bewertung und Evaluierung der Wirksamkeit der technischen und organisatorischen Massnahmen zur Gewaehrleistung der Sicherheit der Verarbeitung.

### Idee fuer interaktive Umsetzung

**"TOM-Baukasten"** -- Die Schueler bekommen ein Szenario (z.B. "Arztpraxis mit 3 Aerzten und einer Sprechstundenhilfe") und muessen aus einem Baukasten von Massnahmen die passenden TOMs zusammenstellen. Sie bekommen ein "Sicherheits-Score" und Feedback, ob sie das Risiko angemessen abgesichert haben. Zu wenig = Datenschutzluecke, zu viel = unverhaeltnismaessiger Aufwand.

---

## Zusammenfassung: Ueberblickstabelle

| Artikel | Thema | Kernaussage |
|---------|-------|-------------|
| Art. 5 | Grundsaetze | 6 Prinzipien + Rechenschaftspflicht |
| Art. 6 | Rechtmaessigkeit | 6 Rechtsgrundlagen (Verbot mit Erlaubnisvorbehalt) |
| Art. 9 | Besondere Kategorien | Generelles Verbot mit 10 Ausnahmen |
| Art. 12-22 | Betroffenenrechte | Auskunft, Loeschung, Berichtigung, Uebertragbarkeit, Widerspruch |
| Art. 25 | Privacy by Design/Default | Datenschutz von Anfang an einbauen |
| Art. 32 | TOMs | Technische und organisatorische Sicherheitsmassnahmen |

---

## Ideen fuer uebergreifende interaktive Elemente

### 1. "DSGVO-Szenario-Simulator"
Ein durchgaengiges Szenario (z.B. Gruendung eines Startups, Einfuehrung einer Schul-App), bei dem die Schueler bei jedem Schritt DSGVO-Entscheidungen treffen muessen. Jede Entscheidung hat Konsequenzen (Bussgeld, Datenschutzpanne, zufriedene Nutzer).

### 2. "Datenschutz-Quiz mit Leveln"
Vom Einsteiger bis zum Experten: Fragen zu allen Artikeln mit steigendem Schwierigkeitsgrad. Multiple-Choice, Lueckentexte, Zuordnungsaufgaben.

### 3. "Gesetzestext-Dolmetscher"
Ein Absatz des Gesetzestextes wird angezeigt. Die Schueler muessen ihn in eigenen Worten erklaeren. Dann wird die Musterloesung angezeigt und sie koennen vergleichen.

### 4. "Datenschutz-Inspektor"
Virtuelle Begehung eines Betriebs (Arztpraxis, Buero, Schule): Die Schueler muessen Datenschutzverstoesse finden und den passenden DSGVO-Artikel nennen.

---

## Quellen

- [DSGVO Gesetzestext -- dsgvo-gesetz.de](https://dsgvo-gesetz.de/)
- [dejure.org -- DSGVO](https://dejure.org/gesetze/DSGVO/)
- [BfDI -- Betroffenenrechte](https://www.bfdi.bund.de/DE/Buerger/Inhalte/Allgemein/Betroffenenrechte/Betroffenenrechte_Auskunftsrecht.html)
- [Stiftung Datenschutz -- Besondere Datenkategorien](https://stiftungdatenschutz.org/ehrenamt/praxisratgeber/praxisratgeber-detailseite/besondere-datenkategorien-272)
- [IHK Frankfurt -- Betroffenenrechte](https://www.frankfurt-main.ihk.de/recht/uebersicht-alle-rechtsthemen/datenschutzrecht/betroffenenrechte-5192968)
- [EU Kommission -- Privacy by Design](https://commission.europa.eu/law/law-topic/data-protection/rules-business-and-organisations/obligations/what-does-data-protection-design-and-default-mean_en)
