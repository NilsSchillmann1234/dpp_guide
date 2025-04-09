<!-- 
Vervollständige diesen Leitfaden, in dem Erklärt werden soll wie man ein einfaches Data-Science Projekt mit Python und UV aufsetzt.
Die Leser, Teilnehmer unseres Projekt-Portfolio Kurses bei StackFuel, haben in vorangegangenen Leitfäden bereits die Grundlagen mit VSCode, dem Terminal, dem Packetmanager UV und Git gelernt. In diesem Leitfaden soll es darum gehen wie das Projekt grundlegend Strukturiert und aufgesetzt wird. Behandle Folgende Punkte und Arbeite die Bereits geschriebenen Teile mit ein:
- Aufsetzten des Projekts mit `uv init`
- Aufbau der Projektstruktur mit sinnvollen unterordnern
- behandle die .gitignore und gib tips welche files enthalten sein sollen und welche nicht
- gehe auf die vor und nachteile bei der Frage Jupyter Notebooks oder Python Scripte ein (bereits enthalten)
- gehe darauf ein welche Bibliotheken nützlich sind und wie sie mit `uv add` dem Projekt hinzugefügt werden.
- gehe darauf ein, wie Gruppen ihr Git Projekt auf Github verwalten können und wie sie ihr Environment und Files synchronisieren können.
- gehe darauf ein, das bei Jupyter Notebooks die outputs vor einem Commit gecleaned werden sollten (und warum)
- gehe auf weitere Sinnvolle Abschnitte ein die ich hier noch nicht genannt habe, aber sinnvoll für einen solchen leitfaden sein könnten


 -->



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














---












# Data Science Projektleitfaden

<!-- ## Inhaltsverzeichnis
1. [Einführung](#einführung)
2. [Projekterstellung und -struktur](#projekterstellung-und--struktur)
3. [Versionskontrolle mit Git und GitHub](#versionskontrolle-mit-git-und-github)
4. [Pakete und Abhängigkeiten mit UV verwalten](#pakete-und-abhängigkeiten-mit-uv-verwalten)
5. [Jupyter Notebooks vs. Python Skripte](#jupyter-notebooks-vs-python-skripte)
6. [Zusammenarbeit in Gruppen](#zusammenarbeit-in-gruppen)
7. [Best Practices für Data Science Projekte](#best-practices-für-data-science-projekte)
8. [Häufige Herausforderungen und Lösungen](#häufige-herausforderungen-und-lösungen)
9. [Nächste Schritte](#nächste-schritte) -->

## Einführung

Herzlich willkommen zum letzten Teil unserer Leitfadenreihe für den Projekt-Portfolio Kurs bei StackFuel! Nachdem du dich bereits mit VSCode, dem Terminal, dem Paketmanager UV und Git vertraut gemacht hast, geht es in diesem Leitfaden darum, all dieses Wissen zusammenzuführen und ein vollständiges Data Science Projekt aufzusetzen.

Ob du alleine oder in einer Gruppe arbeitest, ob du einen öffentlich verfügbaren Datensatz verwendest oder eigene Daten analysierst – dieser Leitfaden wird dir helfen, dein Projekt professionell zu strukturieren und zu verwalten, damit du dich auf das Wesentliche konzentrieren kannst: die Datenanalyse und die Erkenntnisse, die du daraus gewinnst.

## Projekterstellung und -struktur

### Projekt mit UV initialisieren

Der erste Schritt bei jedem neuen Projekt ist die Erstellung einer isolierten Python-Umgebung (virtual environment). Mit UV geht das besonders einfach:

1. Erstelle zunächst einen neuen Projektordner und öffne diesen mit VSCode

2. Initialisiere eine neue virtuelle Umgebung mit UV indem du im eingbauten Terminal von VSCode folgenden Befehl ausführst:

```bash
uv init
```

Dieser befehl legt eine Reihe von Datein und Ordner in deinem Projektverzeichnis an. Schaue in den [UV Guide](uv_guide.md) um mehr über die Funktionsweise von UV zu erfahren.

### Eine sinnvolle Projektstruktur erstellen

Eine gut durchdachte Ordnerstruktur hilft dir dabei, den Überblick zu behalten und macht es anderen leichter, deinen Code zu verstehen. Hier ist eine bewährte Struktur für Data Science Projekte:

```
mein-data-science-projekt/
│
├── .venv/                 # Virtuelle Umgebung (wird automatisch von UV erstellt)
│
├── data/                  # Alle Datendateien
│   ├── raw/               # Rohdaten (unverändert)
│   ├── processed/         # Bereinigte und vorverarbeitete Daten
│   └── external/          # Externe Datenquellen (optional)
│
├── notebooks/             # Jupyter Notebooks für Exploration und Präsentation
│
├── src/                   # Quellcode für die Verwendung im Projekt
│   ├── __init__.py        # Macht src zu einem Python-Paket
│   ├── data/              # Skripte zum Herunterladen oder Generieren von Daten
│   ├── features/          # Skripte zur Feature-Erstellung/-Transformation
│   ├── models/            # Skripte zum Trainieren und Verwenden von Modellen
│   └── visualization/     # Skripte zur Visualisierung
│
├── tests/                 # Testcode für src
│
├── .gitignore             # Gibt an, welche Dateien nicht unter Versionskontrolle stehen
├── pyproject.toml         # Wird von UV erstellt und enthält Projektabhängigkeiten
├── README.md              # Projektbeschreibung und Nutzungsanleitung
├── .env                   # optional für Umgebungsvariablen (z.B. API-Keys, Passwörter, sollten nicht ins Repo)
└── setup.py               # Falls du eine Installation deines Pakets ermöglichen möchtest
```

Du kannst diese Struktur direkt über VSCode erstellen, indem du die Ordner und Dateien manuell anlegst. 

Diese Struktur ist flexibel – passe sie an die Bedürfnisse deines spezifischen Projekts an. Für kleine Projekte ist möglicherweise eine vereinfachte Version ausreichend.

## Versionskontrolle mit Git und GitHub

### .gitignore richtig einrichten

Die `.gitignore`-Datei ist entscheidend, um zu verhindern, dass unnötige oder sensible Dateien ins Repository gelangen. Hier kannst du beliebige Dateien und Ordner angeben, die Git ignorieren soll. Dies ist besonders wichtig für große Dateien, temporäre Dateien oder Umgebungsdateien.
Hier ist ein Beispiel für eine gute `.gitignore`-Datei für Data Science Projekte. Du musst nicht alle Einträge verstehen, aber sie geben dir eine Vorstellung davon, was du ignorieren solltest:

```
# Virtuelle Umgebung
.venv/
venv/
ENV/

# Byte-kompilierte / optimierte / DLL-Dateien
__pycache__/
*.py[cod]
*$py.class
*.so

# Distribution / Packaging
dist/
build/
*.egg-info/

# Jupyter Notebook
.ipynb_checkpoints

# Daten (optional, je nach Projektanforderungen)
data/raw/
data/processed/

# Modelle (können groß sein)
*.pkl
*.h5
*.joblib

# Logs
logs/
*.log

# Environment-spezifische Dateien
.env
.env.local
*.env

# IDE-spezifische Dateien
.idea/
.vscode/
*.swp
*.swo

# Betriebssystem-spezifische Dateien
.DS_Store
Thumbs.db
```

**Wichtig:** Die Entscheidung, ob du Daten und Modelle in das Repository aufnehmen möchtest, hängt von verschiedenen Faktoren ab:

- **Datengröße**: Git ist nicht für große Dateien optimiert. Dateien über 100MB sollten normalerweise nicht ins Repository.
- **Datenschutz**: Sensible oder private Daten sollten nie in ein öffentliches Repository.

Empfehlung: Erstelle Skripte, die deine Daten herunterladen oder generieren, anstatt die Rohdaten selbst zu speichern.

## Pakete und Abhängigkeiten mit UV verwalten

UV vereinfacht die Installation und Verwaltung von Python-Paketen für dein Projekt erheblich. Hier sind die wichtigsten Befehle:

### Pakete installieren

Um ein neues Paket zu installieren und zur `pyproject.toml` hinzuzufügen:

```bash
uv add ipykernel pandas numpy matplotlib scikit-learn
```

Dieser Befehl installiert die angegebenen Pakete und aktualisiert automatisch deine `pyproject.toml`-Datei.

### Nützliche Data Science Bibliotheken

Hier ist eine Liste der gängigsten Bibliotheken für Data Science Projekte:

1. **Datenmanipulation und -analyse**:
   - `pandas`: Für Datenverarbeitung und -analyse
   - `numpy`: Für numerische Berechnungen

2. **Datenvisualisierung**:
   - `matplotlib`: Grundlegende Visualisierungen
   - `seaborn`: Statistik-Visualisierungen auf Basis von matplotlib
   - `plotly`: Interaktive Grafiken
   - `bokeh`: Interaktive Web-Visualisierungen

3. **Machine Learning**:
   - `scikit-learn`: Für klassische ML-Algorithmen
   - `tensorflow` oder `pytorch`: Für Deep Learning
   - `xgboost` oder `lightgbm`: Für Gradient Boosting

4. **Datenzugriff und -speicherung**:
   - `sqlalchemy`: Allgemeine SQL-Datenbankinteraktion
   - `duckdb`: Moderne SQL-Datenbank für Analytics
   - `pymongo`: MongoDB-Zugriff
   - `pyarrow` oder `fastparquet`: Parquet-Dateiformate

5. **Statistik und wissenschaftliche Berechnungen**:
   - `scipy`: Wissenschaftliche Berechnungen
   - `statsmodels`: Statistische Modelle und Tests

6. **Projektunterstützung**:
   - `jupyter`: Für Notebooks inklusive Jupyter Server
   - `ipykernel`: Für Jupyter Notebooks in VSCode
   - `ipywidgets`: Für interaktive Elemente in Notebooks
   - `pytest`: Für Testautomatisierung
   - `black` und `ruff`: Für Code-Formatierung und Linting

Du wirst nur einen kleinen Teil dieser Pakete in deinem Projekt benötigen. Installiere nur die Pakete, die du tatsächlich verwendest, um die Größe deines Projekts zu minimieren.

### Abhängigkeiten synchronisieren

Wenn du mit anderen zusammenarbeitest, ist es wichtig, dass alle Teammitglieder dieselben Pakete und Versionen verwenden.

- Installiere Pakete immer mit `uv add`, damit sie in der `pyproject.toml`-Datei gespeichert werden. Du findest im Internet oft Beispiele, wie du Pakete mit `pip` installierst. Diese werden nicht in der `pyproject.toml` gespeichert und sind daher nicht reproduzierbar.
- Wenn du neue Pakete installiert hast und deine `pyproject.toml`-Datei aktualisiert wurde, erstelle einen Commit zu dieser Änderung, pushe dein Projekt auf GitHub und teile dies deinem Team mit, damit sie ihre Umgebung synchronisieren können.
- Teammitglieder können ihre Umgebung mit dem folgenden Befehl synchronisieren:

```bash
uv sync
```

Dieser Befehl installiert alle Pakete, die in der `pyproject.toml`-Datei aufgeführt sind, und stellt sicher, dass alle Teammitglieder dieselben Versionen verwenden.

## Jupyter Notebooks vs. Python Skripte

Du bist mit der Arbeit an Jupyter Notebooks bereits aus unseren Trainings im DataLab vertraut. In der Softwareentwicklung und auch in der Data Science wird darüber hinaus mit *normalen* Python Scripten gearbeitet. Dies sind einfache Textdateien mit der Endung `.py` (Jupyter Notebooks haben die Endung `.ipynb`). Python Scripte können direkt vom Python Interpreter ausgeführt werden während für Jupyter Notebooks ein sogenannter **Kernel** installiert werden muss.

### Notebooks vs. Scripte

Jupyter Notebooks und Python-Skripte haben unterschiedliche Anwendungsbereiche und Vorteile. Hier ist ein Überblick, wann welches Format sinnvoll ist:

**Jupyter Notebooks eignen sich besonders für:**

- **Explorative Datenanalyse**: Wenn du Daten untersuchen und visualisieren möchtest, sind Notebooks ideal, da du Code und Ergebnisse direkt nebeneinander siehst.
- **Dokumentation**: Durch die Kombination von Markdown-Text und Code kannst du deine Analyse gut dokumentieren.
- **Präsentationen**: Notebooks eignen sich hervorragend, um Analysen und Ergebnisse zu präsentieren.
- **Lernen und Unterrichten**: Die interaktive Natur von Notebooks macht sie ideal für Lernzwecke.
- **Prototyping**: Schnelles Testen von Ideen und Konzepten.

**Python-Skripte (.py) sind besser geeignet für:**

- **Produktionscode**: Skripte lassen sich leichter in Produktionssysteme integrieren.
- **Wiederverwendbare Module**: Wenn du Code schreiben möchtest, der in anderen Projekten oder Scripten verwendet werden soll.
- **Größere Projekte**: Bei umfangreichen Projekten mit mehreren Dateien ist eine strukturierte Organisation mit Skripten übersichtlicher.
- **Performance**: Skripte werden in der Regel effizienter ausgeführt als Notebooks.
- **Versionskontrolle**: Python-Skripte sind einfacher mit Git zu verfolgen, da sie reiner Text sind.
- **Automatisierung**: Für regelmäßig laufende Tasks oder Batch-Verarbeitungen.

Für dein Projekt-Portfolio empfehlen wir einen hybriden Ansatz: Verwende Notebooks für die Exploration und Analyse deiner Daten und refaktoriere dann den Code in strukturierte Python-Module, wenn du eine wiederverwendbare Lösung erstellen möchtest.

### Wichtig: Notebook-Outputs vor dem Commit bereinigen

Wenn du Jupyter Notebooks mit Git versionierst, ist es wichtig, die Ausgaben vor dem Commit zu bereinigen. Hier sind die Gründe dafür:

1. **Dateigröße**: Notebooks mit vielen oder großen Ausgaben (besonders Grafiken) können das Repository unnötig aufblähen da die outputs mit in die Notebook-Datei geschrieben werden.
2. **Versionskontrolle**: Änderungen in den Ausgaben erschweren es, die tatsächlichen Codeänderungen zu erkennen.
3. **Saubere Diff-Ansicht**: Ohne Ausgaben sind die Unterschiede zwischen Versionen klarer erkennbar.

Es gibt mehrere Möglichkeiten, Notebook-Ausgaben zu bereinigen:

**Manuell in VSCode:**
1. Öffne das Notebook in VSCode
2. Klicke auf die drei Punkte (...) in der oberen Leiste
3. Wähle "Clear All Outputs"

<!--  TODO: Zu testen
**Mit nbstripout (empfohlen):**
1. Installiere nbstripout: `uv add nbstripout`
2. Konfiguriere Git, um es automatisch zu verwenden: `nbstripout --install`

Diese Einrichtung stellt sicher, dass Ausgaben automatisch vor jedem Commit entfernt werden.
-->

## Zusammenarbeit in Gruppen

### Git-Workflow für Teams

Wenn du in einer Gruppe arbeitest, ist ein strukturierter Git-Workflow besonders wichtig. Hier ist ein einfacher, aber effektiver Workflow:

1. **Repository einrichten**:
   - Ein Teammitglied erstellt das Repository auf GitHub
   - Dieses Mitglied fügt alle anderen als Collaborators hinzu
   - Jeder klont das Repository: `git clone [repository-url]`

2. **Feature-Branch-Workflow**:
   - Erstelle für jedes Feature oder jede Aufgabe einen neuen Branch: `git checkout -b feature/datenbereinigung`
   - Arbeite an deinen Änderungen und committe regelmäßig: `git commit -m "Beschreibender Commit-Text"`
   - Synchronisiere deinen Branch mit dem Remote-Repository: `git push origin feature/datenbereinigung`
   - Wenn das Feature fertig ist, erstelle einen Pull Request auf GitHub

3. **Code Review und Merge**:
   - Ein anderes Teammitglied überprüft den Code im Pull Request
   - Nach der Genehmigung wird der Branch in den Hauptbranch (main/master) gemergt
   - Alle Teammitglieder aktualisieren ihre lokalen Repositories: `git pull origin main`

### Umgebungen synchronisieren

Um sicherzustellen, dass alle Teammitglieder mit denselben Paketversionen arbeiten:

1. **Zentrale requirements.txt pflegen**:
   - Wenn ein Teammitglied ein neues Paket installiert: `uv add paketname`
   - Requirements pushen: `git add requirements.txt && git commit -m "Add new dependency" && git push`
   - Andere Teammitglieder synchronisieren ihre Umgebung: `uv pip install -r requirements.txt`

2. **Alternativ: setup.py verwenden**:
   - Erstelle eine `setup.py`-Datei für dein Projekt
   - Definiere Abhängigkeiten dort
   - Jedes Teammitglied installiert das Projekt im Entwicklungsmodus: `pip install -e .`

### Zusammenarbeit an Notebooks

Bei der gemeinsamen Arbeit an Jupyter Notebooks gibt es einige Herausforderungen:

1. **Notebook-Konflikte vermeiden**:
   - Teile die Arbeit klar auf (z.B. verschiedene Notebooks für verschiedene Analysen)
   - Vermeide es, gleichzeitig am selben Notebook zu arbeiten

2. **Diff-Ansicht verbessern**:
   - Verwende `nbdime` für bessere Diff- und Merge-Operationen für Notebooks
   - Installation: `uv add nbdime`
   - Konfiguration: `nbdime config-git --enable`

3. **Dokumentation und Kommentare**:
   - Verwende Markdown-Zellen ausgiebig, um deinen Code zu dokumentieren
   - Füge Kommentare hinzu, die anderen Teammitgliedern helfen, deinen Code zu verstehen

## Best Practices für Data Science Projekte

### Code-Qualität sicherstellen

Verwende Linting-Tools, um deinen Code sauber und konsistent zu halten:

```bash
uv add black ruff
```

- `black`: Formatiert deinen Code automatisch
- `ruff`: Prüft deinen Code auf Fehler und Verbesserungsmöglichkeiten

Diese Tools kannst du in VSCode einrichten, sodass sie automatisch beim Speichern ausgeführt werden.

### Reproduzierbarkeit gewährleisten

1. **Random Seeds setzen**:
   ```python
   import numpy as np
   import random
   import torch
   
   # Setze Seeds für Reproduzierbarkeit
   SEED = 42
   random.seed(SEED)
   np.random.seed(SEED)
   torch.manual_seed(SEED)
   ```

2. **Datenpipelines dokumentieren**:
   - Speichere Zwischen- und Endversionen deiner Daten
   - Dokumentiere jeden Transformationsschritt ausführlich

3. **Modellparameter speichern**:
   - Speichere Hyperparameter und Modellkonfigurationen
   - Halte Trainings- und Evaluierungsprozesse in Logdateien fest

### Dokumentation pflegen

Eine gute README.md Datei ist entscheidend. Sie sollte enthalten:

1. **Projekttitel und -beschreibung**
2. **Installation und Setup**:
   ```
   # Installation
   git clone https://github.com/username/projektname.git
   cd projektname
   uv init
   source .venv/bin/activate  # oder .venv\Scripts\activate auf Windows
   uv pip install -r requirements.txt
   ```
3. **Nutzung**: Beispiele, wie das Projekt verwendet wird
4. **Datenquellen**: Woher stammen die Daten, wie kann man sie erhalten
5. **Projektstruktur**: Kurze Erklärung der Ordnerstruktur
6. **Teammitglieder**: Bei Gruppenprojekten

## Häufige Herausforderungen und Lösungen

### Große Dateien verwalten

Git ist nicht für große Dateien optimiert. Alternativen:

1. **Git LFS (Large File Storage)**:
   - Installation: `git lfs install`
   - Konfiguration: `git lfs track "*.csv" "*.pkl" "*.h5"`

2. **DVC (Data Version Control)**:
   - Installation: `uv add dvc`
   - Initialisierung: `dvc init`
   - Daten hinzufügen: `dvc add data/raw/large_dataset.csv`

3. **Cloud-Speicher**:
   - Speichere große Dateien in Google Drive, AWS S3, etc.
   - Erstelle Skripte zum automatischen Herunterladen

### Datenqualität sicherstellen

1. **Konsistenzprüfungen**:
   - Verwende `pandas-profiling` oder `great_expectations` für Datenqualitätsprüfungen
   - Installation: `uv add pandas-profiling great_expectations`

2. **Datenvalidierung**:
   - Definiere Schemas für deine Daten mit `pydantic` oder ähnlichen Bibliotheken
   - Installation: `uv add pydantic`

### Performance optimieren

1. **Große Datasets verarbeiten**:
   - Verwende `dask` für Out-of-Memory-Berechnungen
   - Chunke deine Daten in kleinere Teile

2. **Rechenintensive Operationen**:
   - Nutze Multiprocessing für parallele Verarbeitung
   - Verwende numba oder Cython für rechenintensive Operationen

## Nächste Schritte

Nachdem du dein Projekt aufgesetzt hast, stehen dir viele Wege offen:

1. **Deployment deiner Modelle**:
   - Als REST-API mit FastAPI oder Flask
   - Als Streamlit- oder Dash-Anwendung

2. **Automatisierte Tests hinzufügen**:
   - Unit-Tests mit pytest
   - Integration Tests für Datenpipelines

3. **CI/CD-Pipeline einrichten**:
   - Automatisierte Tests bei jedem Push
   - Automatisches Deployment deiner Anwendung

4. **Kennzahlen und Monitoring**:
   - MLflow für Experiment-Tracking
   - Prometheus/Grafana für Monitoring

### Fazit

Ein gut strukturiertes Projekt ist der Grundstein für erfolgreiche Data Science Arbeit. Mit den in diesem Leitfaden vorgestellten Werkzeugen und Methoden kannst du von Anfang an professionell arbeiten – egal ob allein oder im Team.

Denk daran, dass die perfekte Projektstruktur nicht existiert. Passe die Vorschläge an deine spezifischen Bedürfnisse und an die Größe deines Projekts an. Das Wichtigste ist, dass du und dein Team produktiv arbeiten können und eure Ergebnisse leicht reproduzierbar und verständlich sind.

Viel Erfolg bei deinem Data Science Projekt!