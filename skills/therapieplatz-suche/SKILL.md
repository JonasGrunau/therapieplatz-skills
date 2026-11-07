---
name: therapieplatz-suche
description: Findet Psychotherapeut:innen ODER Psychiater:innen (Fachärzt:innen, z. B. für eine medikamentöse ADHS-Einstellung) in der Nähe einer Adresse – mit Kassensitz, passendem Angebot und Erreichbarkeit – und erstellt individuell formulierte Anfrage-E-Mails. Nutze den Skill immer, wenn jemand einen Therapieplatz, eine Psychotherapie, eine:n Psychiater:in, Nervenarzt, eine Praxis für Medikamenten-Einstellung oder eine Liste von Praxen in seiner Nähe sucht oder Anfrage-Mails an Praxen schreiben will – auch ohne das Wort Skill.
license: MIT
---

# Therapieplatz-Suche (Psychotherapie oder Psychiatrie)

Dieser Skill nimmt Menschen in einer belastenden Lage einen Großteil der mühsamen Platzsuche ab. Er fragt die nötigen Angaben ab, recherchiert passende Praxen mit **verifizierter** Kontakt-E-Mail, schreibt eine Liste in den aktuellen Ordner und erstellt Anfrage-E-Mails (als Gmail-Entwürfe oder als Datei).

Arbeite sorgfältig und ehrlich: Eine Liste mit erfundenen oder falschen Kontaktdaten schadet mehr, als sie nützt.

## Ablauf im Überblick

1. Art der Behandlung wählen: **Psychotherapie** oder **Psychiatrie**
2. Angaben erfragen
3. Suche (mit Timeout)
4. Ergebnisliste als Datei schreiben
5. Eine Muster-Mail zur Freigabe zeigen
6. Nach Freigabe: individuell formulierte Entwürfe erstellen (Gmail oder Datei)

---

## Schritt 1 – Art der Behandlung

Frage zuerst (mit dem Frage-Tool, falls vorhanden):

- **Psychotherapie** – Gesprächs-/Verhaltenstherapie bei psychologischen oder ärztlichen Psychotherapeut:innen. Keine Medikamente.
- **Psychiatrie** – fachärztliche Behandlung bei Fachärzt:innen für Psychiatrie (und Psychotherapie), Nervenheilkunde bzw. Neurologie und Psychiatrie, z. B. für Diagnostik oder eine **medikamentöse Einstellung** (etwa bei ADHS, Depression).

Ist es aus dem Gespräch schon klar, übernimm es und frage nicht erneut. Alle weiteren Schritte unterscheiden sich je nach Modus; Abschnitte sind mit **[PT]** (Psychotherapie) bzw. **[PSY]** (Psychiatrie) markiert.

---

## Schritt 2 – Angaben erfragen

Frage die Angaben ab, **bevor** die Suche startet. Bereits Bekanntes übernehmen, nur Fehlendes nachfragen.

Für beide Modi:
- **Name** (Absender der Mails)
- **Adresse** (Ausgangspunkt für die Entfernung)
- **E-Mail-Adresse** für den Footer der Mails (muss nicht das Gmail-Konto sein)
- **Telefonnummer** (optional, aber empfohlen – viele Praxen vergeben Termine nur telefonisch und bitten ausdrücklich um eine Rückrufnummer)
- **Versicherung**: gesetzlich (GKV) oder privat (PKV); bei GKV optional der Name der Kasse
- **Geschlecht der Behandler:in**: weiblich / männlich / egal
- **Verkehrsmittel**: ÖPNV oder Auto
- **Maximale Fahrzeit**, z. B. 30 Minuten
- **Anzahl gewünschter Ergebnisse**, z. B. 15–20
- **Timeout** (optional): nach wie vielen Minuten ohne neuen Treffer abgebrochen wird (Standard 10)

Zusätzlich **[PT]**:
- **Therapieverfahren**: Verhaltenstherapie (VT), tiefenpsychologisch fundiert (TP), analytisch, systemisch oder „egal“

Zusätzlich **[PSY]**:
- **Anliegen**, z. B. „medikamentöse ADHS-Einstellung“, „Weiterbehandlung Depression“, „Zweitmeinung“
- **Liegt bereits eine Diagnose vor?** Wenn ja, von wem (z. B. Klinik, Ambulanz, Psychotherapeut:in). Manche Praxen übernehmen keine extern gestellten Diagnosen – das ist ein wichtiger Filter.
- **Geht es um Medikamente, die ein BtM-Rezept brauchen** (z. B. Stimulanzien wie Methylphenidat bei ADHS)? Viele Praxen stellen grundsätzlich keine BtM-Rezepte aus.

Frage **nicht** neugierig nach Details der Erkrankung. Der Skill organisiert nur die Kontaktaufnahme.

---

## Schritt 3 – Suche

Ziel: so viele passende Praxen wie gewünscht, jeweils mit **Name, Praxisadresse und verifizierter Kontakt-E-Mail**.

### Filterkriterien

Eine Praxis kommt nur auf die Hauptliste, wenn sie **alle** Kriterien erfüllt:

- **Versicherung**: bei GKV nur Praxen **mit Kassensitz / Kassenzulassung**; bei PKV auch Privatpraxen.
- **Zielgruppe**: Erwachsene (sofern nicht anders gewünscht) – reine **Kinder- und Jugendpraxen ausschließen**.
- **Geschlecht** passend zur Präferenz (bei „egal“ keine Einschränkung).
- **Erreichbarkeit** innerhalb der Maximalzeit mit dem gewählten Verkehrsmittel.
- **E-Mail vorhanden** und auf einer realen Quelle gesehen.

**[PT]** zusätzlich:
- Approbierte:r psychologische:r oder ärztliche:r Psychotherapeut:in
- **Verfahren** passt (bei „egal“ keine Einschränkung)

**[PSY]** zusätzlich:
- **Facharzt**: Psychiatrie (und Psychotherapie), Nervenheilkunde oder Neurologie und Psychiatrie. **Ausschließen**: reine Psychosomatiker:innen und psychologische Psychotherapeut:innen (sie dürfen keine Medikamente verordnen), reine Neurolog:innen.
- **Anliegen passt**: Ist auf der Website ausdrücklich ausgeschlossen, was gesucht wird (z. B. „keine ADHS-Diagnostik/-Behandlung“, „keine BtM-Rezepte“, „keine Neupatienten“), dann nicht auf die Hauptliste, sondern unter „Ausgeschlossen“ mit Grund.
- Markiere je Praxis, ob das Anliegen **ausdrücklich erwähnt**, **nicht erwähnt** oder **ausgeschlossen** ist. Praxen mit ausdrücklicher Erwähnung zuerst.

### Quellen

Verzeichnisse zeigen meist **keine** E-Mail. Der zuverlässige Weg führt über die **Praxis-Website (Impressum/Kontakt)**.

**[PT]**
- `therapie.de/therapeutensuche` – gefilterte Ergebnisse z. B. über
  `https://www.therapie.de/therapeutensuche/ergebnisse/?abrechnungsverfahren=1&ort=PLZ&verfahren=2`
  (`verfahren=2` = Verhaltenstherapie, `abrechnungsverfahren=1` = GKV/Kassenleistung)
- `arztsuche.116117.de` (amtliche Arztsuche, nur Kassensitze – oft JavaScript-lastig)
- jameda, Praxis-Websites

**[PSY]**
- Websuche „Psychiater [Ort] Kassenpatienten“, „Nervenarzt [Ort]“, „[Anliegen] Erwachsene Psychiater [Ort] Kasse“
- Verzeichnisse als Kandidatenquelle: `arzt-auskunft.de`, `portal-der-psyche.de`, `neurologen-und-psychiater-im-netz.org`, bei ADHS `adhs-autismus-adressen.de`, `arztsuche.116117.de`
- Psychiatrische MVZs und **Psychiatrische Institutsambulanzen (PIA)** großer Kliniken als ergänzende Option (oft Überweisung nötig) – separat auflisten

### Vorgehen

1. **Kandidaten sammeln** aus den Quellen oben. Bei zu wenigen Treffern benachbarte, gut erreichbare Orte/Stadtteile einzeln durchsuchen.
2. **E-Mail & Kassenstatus verifizieren**: Praxis-Website öffnen, E-Mail im Impressum/Kontakt ablesen. Kassenstatus möglichst belegen („alle Kassen“, KV-Angabe im Impressum, 116117-Eintrag).
   - Verschleierte Adressen („info (at) praxis.de“, per JavaScript oder Cloudflare kodiert) dürfen ausgeschrieben werden, wenn sie eindeutig von der Praxisseite stammen.
   - Stammt eine E-Mail nur aus einem Verzeichnis, als „Quelle: Verzeichnis“ kennzeichnen.
   - Adressen, die laut Website **nicht** für Patientenanfragen gedacht sind (Webmaster, Datenschutz, „nur für Wartungszwecke“), **nicht** verwenden.
3. **Parallelisieren**: Wenn Subagenten verfügbar sind, mehrere parallel einsetzen (z. B. einen pro Stadtteil/Ortsgruppe). Klar instruieren: **niemals E-Mails oder Praxen erfinden**; eine E-Mail nur mit Quell-URL melden, sonst „NICHT GEFUNDEN“; bereits bekannte Praxen nicht doppelt melden.
4. **Sonderfälle**
   - Gemeinschaftspraxis mit **gemeinsamem Postfach** → später **ein** Entwurf, der alle anspricht.
   - Praxis wünscht laut Website **nur telefonische** Anfragen → trotzdem aufnehmen, aber markieren; in der Mail ankündigen, dass man zusätzlich anruft.
   - Praxen **ohne E-Mail** nicht verwerfen, sondern als **Telefon-Leads** (mit Nummer und Telefonzeiten, falls auf der Website) gesondert listen.
   - Fahrzeiten sind Schätzwerte; bei ÖPNV grob über Linien/Stationen abschätzen und als ungefähr kennzeichnen.

### Timeout

Wenn **X Minuten** (Standard 10) vergehen, **ohne dass ein neuer verifizierter Treffer** hinzukommt, Suche beenden und mit dem Gefundenen weiterarbeiten. Zeit per Shell tracken (`date +%s` beim Start und bei jedem neuen Treffer merken).

Danach ehrlich sagen, wie viele Treffer gefunden wurden und warum abgebrochen wurde, und anbieten, mit **größerem Radius** oder breiteren Kriterien weiterzusuchen. Bei einer Erweiterung bereits gefundene Praxen ausschließen und neue Einträge an die bestehende Liste anhängen.

---

## Schritt 4 – Liste erstellen

Schreibe die Ergebnisse ins **aktuelle Arbeitsverzeichnis**:
- **[PT]** `THERAPEUTEN.md`
- **[PSY]** `PSYCHIATER.md`

Vorhandene Dateien nicht überschreiben, sondern nachfragen bzw. ergänzen.

Im Kopf **Suchkriterien** und das Feld **`Erstellt am:`** mit dem Systemdatum (`date +%d.%m.%Y`, nicht schätzen). Dieses Datum ist später das Stichdatum für Fristen.

Vorlage:

```markdown
# [Psychotherapeut:innen | Psychiater:innen] für [Name] – [Verfahren | Anliegen], [Versicherung]

**Suchkriterien:** [...] · Erwachsene · per [Verkehrsmittel] in ~[X] Min. von [Adresse]
**Erstellt am:** [Datum] · [N] Einträge mit E-Mail + [M] Telefon-Leads

> Hinweis: Erreichbarkeitszeiten sind Schätzwerte – bitte konkrete Verbindung selbst prüfen.

## A. Praxen mit E-Mail

## 1. [Titel Vorname Nachname]
- **Praxis:** [Straße Nr., PLZ Ort]
- **E-Mail:** [adresse] *(ggf. „Quelle: Verzeichnis“)*
- **Telefon:** [Nummer, Telefonzeiten falls bekannt]
- [Berufsbezeichnung] · [Verfahren bzw. Anliegen: ausdrücklich / nicht erwähnt] · [Kassenstatus + Beleg]
- *[Besonderheiten, z. B. nur telefonische Terminvergabe]*
- *[nächste Station · ~Fahrzeit]*

## B. 📞 Telefon-Leads (ohne E-Mail)
| Praxis | Adresse | Telefon | Hinweis |

## C. Ausgeschlossen
- [Praxis] – [Grund, z. B. nur Privat, keine BtM-Rezepte, Aufnahmestopp]

### Quellen
- [Impressum-/Website-URL je Eintrag]
```

---

## Schritt 5 – Muster-Mail zur Freigabe

Zeige **eine** Beispiel-Mail und warte auf Freigabe, bevor Entwürfe entstehen. Knapp, höflich, keine überflüssigen Begründungen, keine Details zur Erkrankung.

**[PT]**
```
Betreff: Anfrage Therapieplatz – ambulante [Verfahren] ([gesetzlich/privat] versichert)

Sehr geehrte/r [Frau/Herr] [Titel] [Nachname],

ich suche derzeit einen Therapieplatz für eine ambulante [Verfahren] und wende mich daher an Ihre Praxis.

Ich bin [gesetzlich/privat] krankenversichert. Gerne würde ich erfahren, ob Sie aktuell freie Plätze haben oder mich auf eine Warteliste setzen können und wie eine erste Kontaktaufnahme (z. B. eine psychotherapeutische Sprechstunde) ablaufen kann.

Über eine kurze Rückmeldung würde ich mich sehr freuen. Vielen Dank für Ihre Zeit.

Mit freundlichen Grüßen
[Name]
[Adresse]
[E-Mail]
[Tel., falls angegeben]
```

**[PSY]**
```
Betreff: Terminanfrage – [Anliegen, z. B. medikamentöse Behandlung bei diagnostizierter ADHS] ([gesetzlich/privat] versichert)

Sehr geehrte/r [Frau/Herr] [Titel] [Nachname],

ich suche derzeit eine psychiatrische Praxis, die [Anliegen, z. B. mich bei bereits diagnostizierter ADHS im Erwachsenenalter medikamentös behandeln kann], und wende mich daher an Sie.

[Falls Diagnose vorhanden:] Die Diagnose wurde von [Stelle] gestellt; der Befund liegt mir vor und ich bringe ihn gerne mit. Ich bin [gesetzlich (Kasse) / privat] versichert. Gerne würde ich erfahren, ob Sie aktuell neue Patient:innen aufnehmen oder mich auf eine Warteliste setzen können und wie ich am besten einen ersten Termin vereinbare.

Über eine kurze Rückmeldung würde ich mich sehr freuen. Vielen Dank für Ihre Zeit.

Mit freundlichen Grüßen
[Name]
[Adresse]
[E-Mail]
[Tel., falls angegeben]
```

Hinweise:
- **Anrede korrekt** je Person (Frau/Herr, Titel). Gemeinschaftspraxis mit gemeinsamem Postfach: alle nennen oder „sehr geehrtes Praxisteam“.
- Praxis wünscht nur telefonische Terminvergabe → einen Satz ergänzen („Gerne rufe ich auch in Ihrer Sprechzeit an.“).
- Steht auf der Website etwas Relevantes (z. B. eigene ADHS-Sprechstunde, Online-Buchung), darf die Mail kurz darauf Bezug nehmen.

---

## Schritt 6 – Entwürfe erstellen

Erst nach Freigabe. **Ein Entwurf pro eindeutigem Postfach.**

**Gegen Spamfilter:** Viele gleichlautende Mails hintereinander landen leicht im Spam. Formuliere deshalb **jede Mail individuell**: anderer Betreff, anderer Einstieg, andere Satzreihenfolge und Grußformel – bei gleichem Inhalt und gleichen Fakten. Erfinde dabei nichts (z. B. keine Behauptung, man habe schon angerufen). Empfiehl dem Nutzer, die Mails **gestaffelt** (verteilt über Stunden oder Tage) zu senden.

**Mit Gmail-Connector:** Entwürfe anlegen. Kann der Connector Entwürfe aktualisieren, Korrekturen direkt einarbeiten; sonst neu anlegen und darauf hinweisen, alte Entwürfe von Hand zu löschen. Der **Versand bleibt beim Nutzer** – das klar sagen, keinen Versand versprechen.

**Ohne Gmail-Connector:** Alle Entwürfe in eine Datei schreiben (`EMAIL-ENTWUERFE.md`), je Empfänger mit Adresse, Betreff und Text.

Zum Abschluss kurz zusammenfassen: Anzahl Entwürfe, beste Treffer (ausdrücklich passendes Angebot), Telefon-Leads mit gemeinsamem Zeitfenster, nächster Schritt (nach einigen Tagen den Skill `rueckmeldungen-erfassen` nutzen).

---

## Grundsätze

- **Nichts erfinden.** Keine erfundenen Namen, Adressen, E-Mails, Telefonzeiten oder Kassenstatus. Im Zweifel weniger liefern und das offen sagen.
- **Sensibel bleiben.** Sachlich, warm, ohne neugierige Rückfragen zur Erkrankung.
- **Datensparsam.** Gesundheitsdaten nur so weit verwenden, wie für die Anfrage nötig; keine Daten in Dateien außerhalb des Arbeitsordners schreiben.
- **Transparenz.** Fahrzeiten als Schätzungen kennzeichnen, Quellen angeben, Tool-Grenzen (kein automatischer Versand) ehrlich nennen.
- **Keine medizinische Beratung.** Welche Behandlung oder welches Medikament passt, entscheidet die Ärztin bzw. der Arzt.
