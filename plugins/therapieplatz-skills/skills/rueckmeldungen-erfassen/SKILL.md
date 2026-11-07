---
name: rueckmeldungen-erfassen
description: Wertet die Antworten der Praxen aus, die mit dem Skill therapieplatz-suche angeschrieben wurden (Psychotherapie oder Psychiatrie). Dokumentiert Zusagen, Absagen, Wartelisten, Telefon-Leads und ausbleibende Antworten als Nachweisliste, erstellt einen Anrufplan und bereitet – erst nach Rückfrage – einen Antrag auf Kostenerstattung nach § 13 Abs. 3 SGB V sowie bei Ablehnung einen Widerspruch vor. Nutze den Skill, wenn jemand wissen will, ob es Zu- oder Absagen gab, die Rückmeldungen erfassen lassen will, eine Absagen-Dokumentation braucht oder ein Kostenerstattungsverfahren angehen möchte – auch ohne das Wort Skill.
license: MIT
---

# Rückmeldungen erfassen & Kostenerstattung vorbereiten

Dieser Skill knüpft an `therapieplatz-suche` an. Er prüft die Antworten der angeschriebenen Praxen, führt eine saubere Nachweisliste und hilft – wenn alle regulären Wege erschöpft sind – beim Antrag auf Kostenerstattung nach **§ 13 Abs. 3 SGB V** („Systemversagen“) bei der gesetzlichen Krankenkasse.

**Wichtig:** Die Anforderungen unterscheiden sich je nach Kasse und Einzelfall. Der Skill erstellt sorgfältige Entwürfe, ersetzt aber keine Rechtsberatung. Weise darauf hin, die Voraussetzungen mit der Kasse, einem Sozialverband (z. B. VdK, SoVD) oder der Unabhängigen Patientenberatung abzugleichen.

## Ablauf im Überblick

1. Modus und Liste bestimmen
2. Daten der Krankenkasse (`KRANKENKASSE.md`)
3. Antworten auswerten (Gmail, sonst manuell)
4. Nachweisliste schreiben (inkl. Anrufplan)
5. Stand bewerten und reagieren
6. Vor dem Antrag: Terminservicestelle 116117 prüfen
7. Antrag nach § 13 Abs. 3 SGB V – nur nach ausdrücklicher Zustimmung
8. Bei Ablehnung: Widerspruch

---

## Schritt 1 – Modus und Liste

Suche im aktuellen Verzeichnis nach der Ergebnisliste:
- `THERAPEUTEN.md` → Modus **Psychotherapie [PT]**, Nachweisliste `RÜCKMELDUNGEN.md`
- `PSYCHIATER.md` → Modus **Psychiatrie [PSY]**, Nachweisliste `RÜCKMELDUNGEN-PSYCHIATER.md`

Gibt es beide, frage, welche Suche ausgewertet werden soll. Gibt es keine, biete an, zuerst `therapieplatz-suche` auszuführen, oder lass dir die kontaktierten Praxen nennen.

**Stichdatum** ist das Feld `Erstellt am:` aus der Liste – **nicht** der Datei-Zeitstempel. Das heutige Datum per Shell (`date +%Y-%m-%d`). Existiert die Nachweisliste schon, ergänze sie (nicht überschreiben).

---

## Schritt 2 – Daten der Krankenkasse

Gibt es `KRANKENKASSE.md`, Angaben daraus lesen. Sonst fragen und speichern:
1. **Name der gesetzlichen Krankenkasse**
2. **Kontaktweg für Anträge** (E-Mail, Postadresse oder App). Im Zweifel die Service-Adresse aus dem Impressum der Kasse und den Hinweis, dass viele Kassen Anträge lieber per App oder Post annehmen.

```markdown
# Krankenkasse
- **Name:** [Kasse]
- **Kontakt für Anträge:** [E-Mail / Postadresse]
- **Erfasst am:** [Datum]
```

---

## Schritt 3 – Antworten auswerten

### Mit Gmail-Connector

Für jede Praxis der Liste die Antworten suchen (Absender-Adresse oder -Domain, Antworten in den Threads der gesendeten Anfragen). Auch **Antworten von anderen Adressen derselben Praxis** (z. B. `anmeldung@…` statt `info@…`) berücksichtigen. Volltext lesen, nicht nur die Vorschau.

Kategorien:
- **Zusage** – Termin oder Platz zeitnah angeboten (Warteliste ≤ 3 Monate zählt als positiv).
- **Absage** – kein Platz, keine Neupatient:innen, Aufnahmestopp. Grund notieren. Als Absage gelten auch:
  - **Warteliste > 3 Monate** (Grund: „Warteliste, Wartezeit > 3 Monate“)
  - **[PSY]** keine BtM-Rezepte, keine Behandlung des Anliegens, keine Übernahme extern gestellter Diagnosen
  - bei GKV: **nur Privat- bzw. Selbstzahlertermin** angeboten (Angebot als Option vermerken)
- **Rückfrage / Lead** – Praxis bittet um Anruf oder um weitere Informationen. Offen und wichtig – hervorheben.
- **Automatische Antwort** – Eingangsbestätigung ohne Entscheidung: **keine** Absage. Die Praxis bleibt offen; Hinweise wie Telefonzeiten übernehmen.
- **Keine Antwort** – endgültig erst, wenn seit dem Stichdatum **mehr als 7 Tage** vergangen sind, sonst „offen“.

Telefonische Ergebnisse, die der Nutzer berichtet (z. B. „bei Praxis X angerufen, Absage“), übernehmen – mit Datum und dem Vermerk „telefonisch“. Kann eine Telefonnummer keiner Praxis eindeutig zugeordnet werden, nachfragen statt raten.

### Ohne Gmail-Connector

Ehrlich sagen, dass keine automatische Auswertung möglich ist, und pro Praxis den Status erfragen.

---

## Schritt 4 – Nachweisliste schreiben

Struktur:

```markdown
# Rückmeldungen [Psychotherapie | Psychiatrie]

**Bezug:** Suche laut [Liste] vom [Stichdatum]
**Versand der Anfragen:** [Datum, Anzahl]
**Dokumentiert am:** [heute]
**7-Tage-Frist:** [läuft ab am … | abgelaufen am …]
**Stand:** [N] Zusagen · [N] Absagen · [N] Leads · [N] offen · [N] ohne Antwort

## ✅ Zusage
## 🟡 Rückfragen / Leads
## ❌ Absagen
### 1. [Name / Praxis]
- **Adresse:** …
- **Kontakt:** [E-Mail an … | Telefonat] am [Datum]
- **Status:** Absage – Antwort vom [Datum]: „[kurzes wörtliches Zitat des Grundes]“
## ⌛ Keine Antwort (Frist abgelaufen)
## ⏳ Noch offen
```

- Jeder Eintrag: **Name, Adresse, Kontaktart und -datum, Ergebnis mit Datum und Grund** (möglichst als kurzes wörtliches Zitat). Das ist der spätere Nachweis gegenüber der Kasse.
- **Datensparsam:** Persönliche Angaben, die der Nutzer in Mails an Praxen gemacht hat (z. B. Vorerkrankungen), **nicht** in die Liste übernehmen – nur „Hintergrund geschildert“.
- **Telefonzeiten miterfassen:** Verweist eine Antwort auf einen Anruf, Telefonnummer und Zeiten aus der Mail übernehmen; fehlen konkrete Zeiten, kurz (1–2 Seitenaufrufe) auf der Praxis-Website nachsehen und als „von der Website“ kennzeichnen, sonst „keine festen Zeiten genannt“.
- **Anrufplan:** Bei mehreren Anruf-Leads einen Abschnitt „📞 Anrufplan“ mit Tabelle (Praxis · Zeiten · Nummer), Überschneidungen und einem konkreten Zeitblock (mit Alternative) ergänzen.

---

## Schritt 5 – Stand bewerten

- **Mindestens eine echte Zusage:** Herzlich und ehrlich erleichtert gratulieren (das ist nach einer zermürbenden Suche eine große Nachricht), Termin und Mitbringsel nennen. Kein Erstattungsantrag nötig. Läuft bereits ein Antrag, empfehlen, der Kasse nach dem Termin Bescheid zu geben.
- **Noch offene Praxen innerhalb der 7-Tage-Frist:** Stand zusammenfassen (Absagen, Leads, offen, Fristende) und anbieten, später erneut zu prüfen. Hier endet der Durchlauf, außer der Nutzer möchte ausdrücklich schon jetzt den Antrag vorbereiten.
- **Alles abgesagt oder > 7 Tage ohne Antwort:** weiter mit Schritt 6.

---

## Schritt 6 – Vor dem Antrag: Terminservicestelle 116117

Kassen lehnen Anträge oft ab, wenn der reguläre Vermittlungsweg nicht genutzt wurde („Termin-Schwierigkeiten allein sind kein Grund“). Frage deshalb, ob schon versucht wurde, und empfiehl es sonst **vor** dem Antrag:

- **[PT]** Über die 116117 einen Termin für eine **psychotherapeutische Sprechstunde** und ggf. eine **Akutbehandlung** vermitteln lassen. Ergebnis und eine Dringlichkeitsbescheinigung (z. B. Formular PTV 11 aus der Sprechstunde) sichern.
- **[PSY]** Beim Hausarzt eine **Überweisung mit Dringlichkeits-Code** holen (und nach dem **Hausarzt-Vermittlungsfall** fragen). Mit Code muss die 116117 einen Facharzttermin vermitteln, der **höchstens 4 Wochen** entfernt liegt; gelingt das nicht, muss sie einen **ambulanten Termin im Krankenhaus** anbieten. Diesen Termin **wahrnehmen**, nicht ablehnen (Ablehnen schwächt den Antrag), und dort festhalten lassen, ob Einstellung und Folgebehandlung möglich sind. Alternative mit mehreren Terminen: **Psychiatrische Institutsambulanzen (PIA)**.

Alle Ergebnisse (Datum, Anruf, Ergebnis) in die Nachweisliste aufnehmen.

---

## Schritt 7 – Antrag nach § 13 Abs. 3 SGB V

**Immer zuerst fragen** (Frage-Tool), ob der Antrag jetzt erstellt werden soll – auch wenn alle Bedingungen erfüllt sind und auch in automatischen/geplanten Läufen. Ohne klares „Ja“ nur den Stand melden.

Vor dem Schreiben klären:
- **Wichtig:** Der Antrag muss gestellt werden, **bevor** eine Privatbehandlung beginnt.
- Gibt es eine **konkrete Privatpraxis** bzw. einen Selbstzahlertermin? Wenn ja, nennen und nach einem Kostenvoranschlag fragen.
- Welche **besonderen medizinischen oder sozialen Gründe** für Dringlichkeit soll der Antrag nennen? Nur aufnehmen, was der Nutzer selbst nennt und freigibt. **Keine Diagnosen oder Schweregrade erfinden**, sensible Details (z. B. Suchtvorgeschichte) nur mit ausdrücklicher Zustimmung.
- Versichertennummer und Geburtsdatum: nicht erfinden, als `[bitte ergänzen]` markieren.

Datei: `E-MAIL-KRANKENKASSE.md` [PT] bzw. `E-MAIL-KRANKENKASSE-PSYCHIATER.md` [PSY]. Ton: professionell und sauber, zugleich menschlich.

Vorlage (Platzhalter füllen):

```
An: [Kontakt der Kasse]
Betreff: Antrag auf Kostenerstattung nach § 13 Abs. 3 SGB V – [ambulante Psychotherapie | fachärztlich-psychiatrische Behandlung ([Anliegen])] – Systemversagen

Sehr geehrte Damen und Herren,

ich bin bei Ihnen gesetzlich krankenversichert und beantrage hiermit nach § 13 Abs. 3 SGB V die Erstattung der Kosten für eine selbst beschaffte [ambulante Psychotherapie | ambulante fachärztlich-psychiatrische Behandlung (konkret: …)].

Versichertennummer: [bitte ergänzen]
Geburtsdatum: [bitte ergänzen]

Zur Ausgangslage:
[Nur vom Nutzer freigegebene Angaben: Diagnose/Befund und wer ihn gestellt hat, Empfehlung der Behandler:in, Einschränkungen im Alltag, besondere medizinische oder soziale Gründe für die Dringlichkeit.]

Meine Bemühungen um einen Behandlungsplatz:
Am [Datum] habe ich [N] [Psychotherapeut:innen | Fachärzt:innen für Psychiatrie] mit Kassenzulassung in zumutbarer Entfernung (bis ca. [X] Minuten mit [Verkehrsmittel]) angefragt. [Ergebnis der Terminservicestelle 116117 / des Krankenhaustermins.] Eine zeitnahe Behandlung als Sachleistung war nicht möglich.

Übersicht (Praxis – Adresse – Kontakt am – Ergebnis am/Grund):
[vollständige Liste aus der Nachweisliste]

Die schriftlichen Absagen kann ich Ihnen auf Wunsch gerne weiterleiten.

Damit liegt ein Systemversagen im Sinne von § 13 Abs. 3 SGB V vor: Die mir als Sachleistung zustehende Behandlung kann nicht rechtzeitig erbracht werden. Ein weiteres Zuwarten ist mir [aus den genannten Gründen] nicht zumutbar.

Ich bitte Sie daher, mir zu bestätigen, dass Sie die Kosten der Behandlung bei einer Behandler:in ohne Kassenzulassung bzw. als Privatleistung übernehmen. [Konkret: Praxis …, Termin ab …, Kostenvoranschlag liegt bei.] Sollten Sie mir stattdessen kurzfristig einen Behandlungsplatz bei einer Vertragspraxis vermitteln können, nehme ich diesen gerne an. Bitte teilen Sie mir mit, welche Unterlagen Sie noch benötigen.

Über eine zeitnahe schriftliche Rückmeldung würde ich mich sehr freuen.

Mit freundlichen Grüßen
[Name]
[Adresse]
[E-Mail]
[Telefon]
```

Hinweise:
- Die Absagenliste **ohne** Hinweise auf Online-Buchungsportale oder Wartelisten-Funktionen übernehmen – nur Ergebnis und Grund.
- Mit Gmail-Connector anbieten, den Antrag als **Entwurf** anzulegen; der Versand bleibt beim Nutzer.
- Empfehlen, eine Dringlichkeitsbescheinigung (Hausarzt, Psychotherapeut:in, PTV 11) und den Diagnosebefund beizulegen.

---

## Schritt 8 – Bei Ablehnung: Widerspruch

Liest der Nutzer eine Ablehnung vor (Mail, Brief oder PDF), zusammenfassen: Begründung, Vorschläge der Kasse, **Widerspruchsfrist (1 Monat nach Erhalt)**.

Einschätzen, ohne Rechtsberatung vorzutäuschen:
- Hat die Kasse § 13 Abs. 3 (Systemversagen) überhaupt geprüft oder nur die Wahl der Kostenerstattung (§ 13 Abs. 2)?
- Fehlt noch der Weg über die 116117 bzw. ein Krankenhaustermin? Dann diesen zuerst gehen.

Anbieten:
- einen kurzen **fristwahrenden Widerspruch** („Hiermit lege ich Widerspruch gegen Ihren Bescheid vom … ein. Die Begründung reiche ich nach.“) mit Vorgangsnummer als Entwurf,
- später die **Begründung** (Nachweisliste, 116117-Ergebnis, Bescheinigungen).

Bleibt die Kasse beim Nein: Klage beim Sozialgericht (Frist 1 Monat nach Widerspruchsbescheid; für Versicherte keine Gerichtskosten, ggf. Eilantrag). Für Unterstützung auf Sozialverbände und die Unabhängige Patientenberatung verweisen.

---

## Grundsätze

- **Nichts erfinden** – weder Antworten noch Versichertendaten, Diagnosen oder Telefonnummern-Zuordnungen.
- **Sensibel und respektvoll**, bei einer Zusage echte Freude zeigen.
- **Keine Rechtsberatung vortäuschen**, Entwürfe als Entwürfe kennzeichnen.
- **Nichts ungefragt senden oder löschen.** Absage-Mails sind Nachweise – vor dem Löschen darauf hinweisen, dass sie für Antrag oder Widerspruch noch gebraucht werden könnten.
- **Datumslogik:** Stichdatum aus `Erstellt am:` der Liste, nicht aus dem Dateisystem.
