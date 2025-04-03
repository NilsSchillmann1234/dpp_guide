<!-- 
Vervollständige den Leitfaden zum Thema Visual Studio Code.
Der Leitfaden richtet sich an Teilnehmende des Projekt-Portfolio Kurses meines Unternehmens. Die Teilnehmer haben bereits Kurse zu Themen wie Data Science, Data Analytics und Python besucht. In den vergangenen Trainings haben die Teilnehmenden nur in einer von uns bereitgestellten Jupyter Server instanz an Jupyter Notebooks gearbeitet. In diesem Training soll es darum gehen, das die Teilnehmenden selbstständig ein eigenen Porjekt auf ihrem eigenen Rechner umsetzten. Da sie bislang nur auf unserer Website Programmiert haben möchte ich eine Reihe von Leitfäden für sie bereitstellen in denen sie an die Arbeit mit VSCode, UV (Python Package manager) und Git herangeführt werden.
Folgende Leitfäden werden den Teilnehmern zur verfügung gestellt:
- [Leitfaden für den Code Editor Visual Studio Code (coming soon)](./vscode_guide.md)
- [Leitfaden für das Terminal (coming soon)](./terminal_guide.md)
- [Leitfaden für den Python Paketmanager UV](./uv_guide.md)
- [Leitfaden für Git (coming soon)](./git_guide.md)
- [Beispieldatensätze](./data_sets.md)
- [Referenzprojekt zur Inspiration](https://github.com/jzatstackfuel/DPP-Referenzprojekt)

Hier ist der Erste (unvollständige) Entwurd zum Thema VSCode. Die Teilnehmer sollen mit der Software soweit vertraut gemacht werden, dass sie den folgenden Leitfäden folgen können.

Vervollständige diesen Leitfaden. Halte dich an den Duktus der bereits etabliert wurde. Richte dich nach den Kommentaren zu den entsprechenden Kapiteln.
-->


# Visual Studio Code - Leitfaden für Python-Entwicklung

In diesem Leitfaden zeige ich dir, wie du mit dem Code-Editor **Visual Studio Code** (VSCode) effektiv arbeiten kannst. VSCode ist ein leistungsstarker und vielseitiger Editor, der besonders für die Python-Entwicklung geeignet ist. Wir werden uns ansehen, wie du VSCode installierst, die Oberfläche navigierst, den Editor an deine Bedürfnisse anpasst und mit Python-Projekten, insbesondere unter Verwendung von UV und Jupyter Notebooks, arbeitest.

## Einführung

### Was ist Visual Studio Code?

**Visual Studio Code (VSCode)** ist ein kostenloser, plattformübergreifender Code-Editor von Microsoft. Er bietet zahlreiche Funktionen wie Code-Vervollständigung, Debugging, Git-Integration und Unterstützung für eine Vielzahl von Programmiersprachen durch Erweiterungen. Neben VSCode gibt es noch eine vielzahl weiterer Entwicklungsumgebungen für Python wie PyCharm, Spider oder das aus dem DataLab bekannte JupyterLab. Grundsätzlich kannst du dein Projekt mit jedem dieser Tools aufsetzten.

### Vorteile von VSCode für die Python-Entwicklung

- **Leichtgewichtiger Editor** mit großer Funktionalität
- **IntelliSense**: intelligente Code-Vervollständigung
- **Integriertes Terminal** für die Ausführung von Befehlen (z. B. UV, python, git etc.)
- **Erweiterbar** durch eine Vielzahl von **Extensions** (Erweiterungen)
- **Unterstützung von Jupyter Notebooks** direkt im Editor
- **Plattformübergreifend**: verfügbar für Windows, macOS und Linux

### Download und Installation von VSCode

**Download**:

   Besuche die offizielle Website von VSCode: [https://code.visualstudio.com/](https://code.visualstudio.com/) und lade die passende Version für dein Betriebssystem herunter.

**Installation auf Windows**:

   - Führe die heruntergeladene `.exe`-Datei aus.
   - Folge den Anweisungen des Installationsassistenten.
   - Optional *Empfohlen*: Aktiviere die Option **"Code zu PATH hinzufügen"**, um VSCode über die Kommandozeile zu starten.
   - Optional *Empfohlen*: Aktiviere die beiden Optionen **"In Code Öffnen"** für das Kontext Menü.

**Installation auf macOS**:

   - Öffne das heruntergeladene `.zip`-Archiv.
   - Ziehe die Anwendung **Visual Studio Code** in den Ordner **Programme**.

Nachdem du VSCode installiert hast solltest du dich mit der Oberfläche vertraut machen. Microsoft stellt dafür ein Umfangreiche [Dokumentation](https://code.visualstudio.com/docs) zur verfügung, in der alle Wichtigen features erklärt werden.

## Einrichtung

In dem [Get Started](https://code.visualstudio.com/docs/getstarted/getting-started) Guide wirst du in die Grundlagen von VSCode eingeführt. Dir wird ein Überblick über das grundlegende Interface, die Einstellungen, das arbeiten mit Source Control (Git) sowie die Erweiterung der Software mit Language Extensions (z.b. für Python) gegeben. Lies dir diesen Guide durch um dich mit den Grundlagen von VSCode vertraut zu machen.

### Erweiterungen

Der größte Vorteil von VSCode ist seine Erweiterbarkeit durch Extensions (Erweiterungen). Für unsere Python-Entwicklung benötigst du einige wichtige Erweiterungen, die dir die Arbeit erheblich erleichtern werden.

Um Erweiterungen zu installieren, klicke auf das Extensions-Symbol in der Activity Bar am linken Rand (oder drücke `Ctrl+Shift+X` auf Windows bzw. `Cmd+Shift+X` auf macOS).

Hier sind die empfohlenen Erweiterungen für dein Python-Projekt:

1. **Python Extension**:
   - Die offizielle Python-Erweiterung von Microsoft
   - Bietet IntelliSense, Linting, Debugging, Code Navigation, Code Formatierung und vieles mehr
   - Suche nach "Python" und installiere die Erweiterung von Microsoft

2. **Jupyter Extension**:
   - Ermöglicht die Arbeit mit Jupyter Notebooks direkt in VSCode
   - Unterstützt das Ausführen von Code-Zellen, das Anzeigen von Plots und die Integration mit dem Python-Interpreter
   - Suche nach "Jupyter" und installiere die Erweiterung von Microsoft

3. **Even Better TOML**:
   - Bietet Syntax-Highlighting und Unterstützung für TOML-Dateien
   - Besonders nützlich für die Arbeit mit `pyproject.toml`-Dateien, die für moderne Python-Projekte verwendet werden
   - Suche nach "Even Better TOML" und installiere die Erweiterung von tamasfe

4. **Ruff**:
   - Ein schneller Python Linter und Code-Formatter
   - Hilft dir, deinen Code sauber und nach den Python-Standards zu formatieren
   - Suche nach "Ruff" und installiere die entsprechende Erweiterung

Nach der Installation dieser Erweiterungen sollte VSCode automatisch deine Python-Umgebung erkennen und die entsprechenden Funktionen zur Verfügung stellen. Falls du weitere Erweiterungen benötigst, kannst du jederzeit den [Extension Marketplace](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace) durchsuchen.



### Terminal

Ein wichtiger Bestandteil der Arbeit mit VSCode ist das integrierte Terminal, das dir ermöglicht, Befehle direkt aus dem Editor heraus auszuführen, ohne zwischen verschiedenen Anwendungen wechseln zu müssen.

**Öffnen des Terminals**:

- Drücke `` Ctrl+` `` (Windows/Linux) oder `` Cmd+` `` (macOS).
- Alternativ kannst du über das Menü "Terminal" > "New Terminal" ein neues Terminal öffnen.

**Grundlegende Terminal-Funktionen in VSCode**:

1. **Mehrere Terminals verwalten**:
   - Du kannst mehrere Terminal-Instances haben, zwischen denen du über das Dropdown-Menü in der Terminal-Leiste wechseln kannst.
   - Teile das Terminal-Fenster horizontal oder vertikal mit dem "Split"-Button.

2. **Terminal-Typ auswählen**:
   - In Windows kannst du zwischen PowerShell, Command Prompt und WSL wählen.
   - In macOS/Linux stehen verschiedene Shells wie Bash, Zsh oder Fish zur Verfügung.

3. **Befehle ausführen**:
   - Führe Python-Skripte aus: `python mein_skript.py`
   - Verwende UV für Paketmanagement (siehe [UV Leitfaden](uv_guide.md))
   - Arbeite mit Git (siehe [Git Leitfaden](git_guide.md))

4. **Terminal-Ausgabe durchsuchen**:
   - Nutze `Ctrl+F` (Windows/Linux) oder `Cmd+F` (macOS), um in der Terminal-Ausgabe zu suchen.

5. **Terminaleinstellungen anpassen**:
   - Passe Schriftart, Größe und andere Einstellungen über die VSCode-Einstellungen an.

Das Terminal ist ein mächtiges Werkzeug für die Python-Entwicklung und wird besonders nützlich sein, wenn du mit UV Pakete installierst, Git für die Versionskontrolle verwendest oder deine Python-Skripte ausführst.

Für eine ausführlichere Einführung in die Arbeit mit dem Terminal, lies bitte den [Terminal Leitfaden](./terminal_guide.md), der detaillierte Informationen und Beispiele enthält.

## Tipps für effizientes Arbeiten mit VSCode

Hier sind einige zusätzliche Tipps, die dir helfen können, produktiver mit VSCode zu arbeiten:

### Nützliche Tastenkombinationen

- `Ctrl+P` (Windows/Linux) oder `Cmd+P` (macOS): Schnelles Öffnen von Dateien
- `Ctrl+Shift+P` (Windows/Linux) oder `Cmd+Shift+P` (macOS): Befehlspalette öffnen
- `Ctrl+Space`: IntelliSense manuell auslösen
- `Alt+Up/Down` (Windows/Linux) oder `Option+Up/Down` (macOS): Zeilen nach oben/unten verschieben
- `Ctrl+/` (Windows/Linux) oder `Cmd+/` (macOS): Zeile/Auswahl kommentieren/auskommentieren

### Workspace-Dateien

VSCode verwendet Workspace-Dateien (`.code-workspace`), um Projekteinstellungen zu speichern. Diese sind besonders nützlich, wenn du mit mehreren Ordnern in einem Projekt arbeitest. Du kannst eine Workspace-Datei erstellen, indem du "File" > "Save Workspace As..." auswählst.

### Snippets

Snippets sind Code-Vorlagen, die dir helfen, häufig verwendeten Code schnell einzufügen. Du kannst vordefinierte Snippets verwenden oder eigene erstellen:

1. Öffne die Befehlspalette (`Ctrl+Shift+P` / `Cmd+Shift+P`).
2. Tippe "Snippets" und wähle "Preferences: Configure User Snippets".
3. Wähle "python.json", um Python-spezifische Snippets zu erstellen.

Hier ist ein Beispiel für ein einfaches Snippet:

```json
"Print variable": {
  "prefix": "pv",
  "body": [
    "print(f\"{$1} = {${1}}\")"
  ],
  "description": "Print a variable with its name"
}
```

## Zusammenfassung

Visual Studio Code ist ein vielseitiger und leistungsstarker Editor, der dir alle Werkzeuge bietet, die du für die Python-Entwicklung benötigst. Mit den richtigen Erweiterungen und Einstellungen kannst du eine Umgebung schaffen, die perfekt auf deine Bedürfnisse zugeschnitten ist.

In diesem Leitfaden haben wir die grundlegende Installation und Einrichtung von VSCode für die Python-Entwicklung behandelt, sowie die Arbeit mit Python-Skripten und Jupyter Notebooks. Nutze diese Grundlagen, um dein eigenes Projekt zu erstellen und damit zu experimentieren.

Für weitere Informationen zu spezifischen Themen, schau dir die anderen Leitfäden an:
- [Leitfaden für das Terminal](./terminal_guide.md)
- [Leitfaden für den Python Paketmanager UV](./uv_guide.md)
- [Leitfaden für Git](./git_guide.md)

Viel Erfolg bei deinem Projekt-Portfolio!