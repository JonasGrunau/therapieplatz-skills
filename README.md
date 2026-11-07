# Therapieplatz-Skills für Claude

Zwei [Claude-Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview), die bei der mühsamen Suche nach einem **Psychotherapieplatz** oder einem **Psychiater-Termin** (z. B. für eine medikamentöse ADHS-Einstellung) helfen. Sie richten sich an gesetzlich und privat Versicherte in Deutschland.

> Wer gerade psychisch belastet ist, hat oft keine Kraft, 20 Praxen herauszusuchen, anzuschreiben und Absagen zu sortieren. Diese Skills übernehmen den Großteil davon.

## Was die Skills können

### 1. `therapieplatz-suche`
- Fragt zuerst: **Psychotherapie** oder **Psychiatrie**?
- Sucht passende Praxen in der Nähe: Kassensitz, gewünschtes Verfahren bzw. Anliegen, Fahrzeit mit ÖPNV oder Auto, Geschlecht der Behandler:in.
- Liest Kontakt-E-Mails nur von echten Quellen ab, meist dem Impressum, und **erfindet nichts**.
- Schreibt eine Liste (`THERAPEUTEN.md` bzw. `PSYCHIATER.md`) und **individuell formulierte Anfrage-Mails** als Gmail-Entwürfe oder als Datei. Gesendet wird nichts automatisch.

### 2. `rueckmeldungen-erfassen`
- Wertet die Antworten der Praxen aus: Zusage, Absage, Warteliste, Rückfrage, keine Antwort.
- Führt eine saubere **Nachweisliste** mit Anrufplan für Praxen, die nur telefonisch erreichbar sind.
- Erklärt den Weg über die **Terminservicestelle 116117**.
- Erstellt **nach Rückfrage** einen Antrag auf Kostenerstattung nach **§ 13 Abs. 3 SGB V** („Systemversagen“) und bei Ablehnung einen Widerspruch.

Dazu gibt es zwei PDFs zum Ausdrucken und Weitergeben:
- [`docs/Leitfaden-Psychiater-Termin.pdf`](docs/Leitfaden-Psychiater-Termin.pdf): Schritt für Schritt zum Psychiater-Termin, von der 116117 über den Antrag bis zum Widerspruch.
- [`docs/Anleitung-Praxis-Suche-mit-Claude.pdf`](docs/Anleitung-Praxis-Suche-mit-Claude.pdf): Wie man die Skills mit **Claude Desktop und Gmail** nutzt, verständlich auch ohne Technikwissen.

## Installation

**Claude.ai / Claude Desktop**
1. Beide ZIP-Dateien aus [`dist/`](dist/) herunterladen (nicht entpacken).
2. In Claude unter *Einstellungen → Capabilities* „Code execution and file creation“ einschalten und bei *Skills* über „Upload skill“ beide ZIPs hochladen.
3. Gmail unter *Connectors* verbinden.

Skills gibt es in den Plänen Pro, Max, Team und Enterprise. Eine verständliche Schritt-für-Schritt-Anleitung steht in [`docs/Anleitung-Praxis-Suche-mit-Claude.pdf`](docs/Anleitung-Praxis-Suche-mit-Claude.pdf).

**Claude Code**
```bash
git clone https://github.com/JonasGrunau/therapieplatz-skills.git
cp -r therapieplatz-skills/skills/* ~/.claude/skills/
```

**Als Projektordner (empfohlen)**
Den Ordner klonen und darin mit Claude arbeiten. Die [`CLAUDE.md`](CLAUDE.md) verweist auf die Skills. Listen, Rückmeldungen und Anträge landen dann gesammelt in diesem Ordner. Die [`.gitignore`](.gitignore) sorgt dafür, dass diese persönlichen Dateien nicht versehentlich committet werden.

## Nutzung

Einfach in eigenen Worten schreiben, zum Beispiel:

- „Ich suche einen Therapieplatz für Verhaltenstherapie in der Nähe von 80331 München.“
- „Ich brauche einen Psychiater für eine ADHS-Medikation, gesetzlich versichert, maximal 30 Minuten mit der Bahn.“
- „Scanne meine Mails nach Rückmeldungen der Praxen.“
- „Erstelle mir den Antrag auf Kostenerstattung für die Krankenkasse.“

Empfohlene Verbindungen: **Gmail** (für Entwürfe und das Auswerten der Antworten) und **Websuche**. Ohne Gmail schreibt der Skill die Mails in eine Datei.

## Wichtig

- **Keine Rechts- oder ärztliche Beratung.** Die Skills erstellen Entwürfe. Kassen und Gerichte entscheiden im Einzelfall unterschiedlich. Verbindliche Hilfe gibt es beim VdK, beim SoVD, bei der Unabhängigen Patientenberatung oder bei Fachanwält:innen für Sozialrecht.
- **Datenschutz.** Du verarbeitest dabei Gesundheitsdaten mit einem KI-Dienst. Gib nur so viel an, wie für die Anfrage nötig ist. Persönliche Arbeitsdateien gehören nicht in ein öffentliches Repo.
- **Nichts wird automatisch gesendet oder gelöscht.** Versand und Entscheidungen bleiben bei dir.
- **Im Notfall:** Ärztlicher Bereitschaftsdienst **116117**, Notruf **112**, Telefonseelsorge **0800 111 0 111**. Viele Bundesländer haben zusätzlich einen psychiatrischen Krisendienst, in Bayern **0800 655 3000**.

## Mitmachen

Verbesserungen sind willkommen, zum Beispiel weitere Verzeichnisse, Hinweise für andere Bundesländer oder Kassen sowie Erfahrungen mit Anträgen. Bitte als Issue oder Pull Request, **ohne persönliche Gesundheitsdaten**.

## Lizenz

[MIT](LICENSE)
