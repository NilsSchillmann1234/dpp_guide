# Visual Studio Code - Leitfaden für Python-Entwicklung

In diesem Leitfaden zeige ich dir, wie du mit dem Code-Editor **Visual Studio Code** (VSCode) effektiv arbeiten kannst. VSCode ist ein leistungsstarker und vielseitiger Editor, der besonders für die Python-Entwicklung geeignet ist. Wir werden uns ansehen, wie du VSCode installierst, die Oberfläche navigierst, den Editor an deine Bedürfnisse anpasst und mit Python-Projekten, insbesondere unter Verwendung von UV und Jupyter Notebooks, arbeitest.



## Einführung

### Was ist Visual Studio Code?

**Visual Studio Code (VSCode)** ist ein kostenloser, plattformübergreifender Code-Editor von Microsoft. Er bietet zahlreiche Funktionen wie Code-Vervollständigung, Debugging, Git-Integration und Unterstützung für eine Vielzahl von Programmiersprachen durch Erweiterungen. Neben VSCode gibt es noch eine vielzahl weiterer Entwicklungsumgebungen für Python wie PyCharm, Spider oder das aus dem DataLab bekannte JupyterLab. Grundsätzlich kannst du dein Projekt mit jedem dieser Tools aufsetzten.

### Vorteile von VSCode für die Python-Entwicklung

- **Leichtgewichtiger Editor** mit großer Funktionalität
- **IntelliSense**: intelligente Code-Vervollständigung
- **Integriertes Terminal** für die Ausführung von Befehlen (z. B. UV, python, git etc.)
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
<!---
Python Extension
Jupyter extension
Even Better TOML (für pyproject.toml)
RUFF (Code Formatter)
-->


[Extension Marketplace](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace)

### Progammieren in VSCode
Du bist mit der Arbeit an Jupyter Notebooks bereits aus unseren Trainings im DataLab vertraut. In der Softwareentwicklung und auch in der Data Science wird darüber hinaus mit *normalen* Python Scripten gearbeitet. Dies sind einfache Textdateien mit der Endung `.py` (Jupyter Notebooks haben die Endung `.ipynb`). Python Scripte können direkt vom Python Interpreter ausgeführt werden während für Jupyter Notebooks ein sogenannter **Kernel** installiert werden muss (mehr dazu im [UV Leitfaden](uv_guide.md). 

#### Notebooks vs. Scripte
<!--
Gegenüberstellung wann Notebooks und wann Scripte sinnvoll sind.
-->


#### Jupyter Notebooks
<!--
Kurze einführung in die Arbeit mit Jupyter in VSCode mit verweis auf die Dokumentation.
-->
[Jupyter Notebooks](https://code.visualstudio.com/docs/datascience/jupyter-notebooks)

#### Python Scripte
<!-- 
Kurze Einführung in die Arbeit mit Python Scripten in VSCode
-->


[Basic editing](https://code.visualstudio.com/docs/editing/codebasics)

### Terminal
<!-- 
Kurze Einführung wie das Terminal in VSCode bedient wird. Verweis auf den Terminal Leitfaden unter `./terminal_guide.md`.
-->






