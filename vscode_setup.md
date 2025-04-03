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

### Programmieren in VSCode

Du bist mit der Arbeit an Jupyter Notebooks bereits aus unseren Trainings im DataLab vertraut. In der Softwareentwicklung und auch in der Data Science wird darüber hinaus mit *normalen* Python Scripten gearbeitet. Dies sind einfache Textdateien mit der Endung `.py` (Jupyter Notebooks haben die Endung `.ipynb`). Python Scripte können direkt vom Python Interpreter ausgeführt werden während für Jupyter Notebooks ein sogenannter **Kernel** installiert werden muss (mehr dazu im [UV Leitfaden](uv_guide.md)). 

#### Notebooks vs. Scripte

Jupyter Notebooks und Python-Skripte haben unterschiedliche Anwendungsbereiche und Vorteile. Hier ist ein Überblick, wann welches Format sinnvoll ist:

**Jupyter Notebooks eignen sich besonders für:**

- **Explorative Datenanalyse**: Wenn du Daten untersuchen und visualisieren möchtest, sind Notebooks ideal, da du Code und Ergebnisse direkt nebeneinander siehst.
- **Dokumentation**: Durch die Kombination von Markdown-Text und Code kannst du deine Analyse gut dokumentieren.
- **Präsentationen**: Notebooks eignen sich hervorragend, um Analysen und Ergebnisse zu präsentieren.
- **Lernen und Unterrichten**: Die interaktive Natur von Notebooks macht sie ideal für Lernzwecke.
- **Prototyping**: Schnelles Testen von Ideen und Konzepten.

**Python-Skripte (.py) sind besser geeignet für:**

- **Produktionscode**: Skripte lassen sich leichter in Produktionssysteme integrieren.
- **Wiederverwendbare Module**: Wenn du Code schreiben möchtest, der in anderen Projekten verwendet werden soll.
- **Größere Projekte**: Bei umfangreichen Projekten mit mehreren Dateien ist eine strukturierte Organisation mit Skripten übersichtlicher.
- **Performance**: Skripte werden in der Regel effizienter ausgeführt als Notebooks.
- **Versionskontrolle**: Python-Skripte sind einfacher mit Git zu verfolgen, da sie reiner Text sind.
- **Automatisierung**: Für regelmäßig laufende Tasks oder Batch-Verarbeitungen.

Für dein Projekt-Portfolio empfehlen wir einen hybriden Ansatz: Verwende Notebooks für die Exploration und Analyse deiner Daten und refaktoriere dann den Code in strukturierte Python-Module, wenn du eine wiederverwendbare Lösung erstellen möchtest.

#### Jupyter Notebooks

Die Arbeit mit Jupyter Notebooks in VSCode ähnelt der Arbeit im JupyterLab, jedoch mit einigen zusätzlichen Funktionen und einer anderen Benutzeroberfläche. Hier ist eine kurze Einführung:

1. **Notebook öffnen oder erstellen**:
   - Öffne ein bestehendes `.ipynb`-File oder erstelle ein neues, indem du auf "New File" klickst und `.ipynb` als Erweiterung angibst.
   - VSCode erkennt automatisch das Notebook-Format und öffnet es im Notebook-Editor.

2. **Kernel auswählen**:
   - Klicke auf "Select Kernel" in der oberen rechten Ecke des Notebooks.
   - Wähle den Python-Kernel aus, den du mit UV installiert hast (siehe [UV Leitfaden](uv_guide.md)).

3. **Code ausführen**:
   - Führe eine Zelle aus, indem du auf den "Run"-Button links neben der Zelle klickst oder `Shift+Enter` drückst.
   - Führe alle Zellen aus, indem du auf "Run All" in der Notebook-Toolbar klickst.

4. **Zellen hinzufügen und bearbeiten**:
   - Füge eine neue Zelle hinzu, indem du auf "+" in der Notebook-Toolbar klickst.
   - Ändere den Zelltyp (Code oder Markdown) über das Dropdown-Menü in der Zelle.

5. **Variablen anzeigen**:
   - Sieh dir die aktuellen Variablen und deren Werte im Variables-Explorer an (zu finden in der Notebook-Toolbar).

6. **Plots anzeigen**:
   - Plots werden direkt unter der Zelle angezeigt, in der sie erstellt wurden.
   - Du kannst Plots vergrößern, als Bilder speichern oder in andere Formate exportieren.

Für eine detailliertere Einführung in die Arbeit mit Jupyter Notebooks in VSCode, schau dir die offizielle [Jupyter Notebooks-Dokumentation](https://code.visualstudio.com/docs/datascience/jupyter-notebooks) an.

#### Python Scripte

Die Arbeit mit Python-Skripten in VSCode bietet dir zahlreiche Funktionen, die die Entwicklung erleichtern. Hier ist eine kurze Einführung:

1. **Python-Datei erstellen oder öffnen**:
   - Erstelle eine neue Datei mit der Endung `.py` oder öffne eine bestehende Python-Datei.
   - VSCode erkennt automatisch, dass es sich um eine Python-Datei handelt und aktiviert die entsprechenden Funktionen.

2. **Code schreiben mit IntelliSense**:
   - Während du Code schreibst, bietet dir VSCode Vorschläge für Funktionen, Methoden und Variablen an.
   - Du erhältst auch Dokumentation und Typhinweise, wenn du mit der Maus über Funktionen oder Variablen fährst.

3. **Code ausführen**:
   - Führe das gesamte Skript aus, indem du auf den "Run Python File"-Button (▶️) in der oberen rechten Ecke klickst.
   - Führe einzelne Codezeilen oder -blöcke aus, indem du sie markierst und `Shit+Enter` drückst (ähnlich wie in Jupyter Notebooks).

4. **Debugging**:
   - Setze Breakpoints, indem du links neben die Zeilennummer klickst.
   - Starte das Debugging mit F5 oder über das Debug-Menü.
   - Im Debug-Modus kannst du Variablen inspizieren, den Code schrittweise durchlaufen und Bedingungen überprüfen.

5. **Linting und Formatierung**:
   - VSCode zeigt dir automatisch Probleme in deinem Code an (z.B. nicht verwendete Variablen, Syntaxfehler).
   - Mit Ruff (oder anderen Formatierungstools) kannst du deinen Code automatisch formatieren (dafür drücke `Shift+Alt+F` auf Windows oder `Shift+Option+F` auf macOS).

6. **Codeorganisation**:
   - Nutze den Outline-View, um die Struktur deines Codes zu sehen (Klassen, Funktionen usw.).
   - Falte Code-Blöcke zusammen, indem du auf die Pfeile links neben den Definitionszeilen klickst.

Für eine umfassendere Einführung in die Grundlagen der Bearbeitung von Code in VSCode, lies den Abschnitt [Basic editing](https://code.visualstudio.com/docs/editing/codebasics) der offiziellen Dokumentation.

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