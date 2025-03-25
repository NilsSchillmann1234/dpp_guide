# UV-Python-Paketmanagement-Leitfaden

In diesem Leitfaden zeige ich dir, wie du UV für dein Data-Science-Projekt nutzen kannst. UV ist ein moderner und schneller Paketmanager für Python, der dir hilft, deine Projektumgebung sauber und übersichtlich zu halten.

## Was ist ein Virtual Environment?

Bei der Arbeit mit Python sind wir oft auf externe Pakete wie Pandas, Matplotlib, Scikit-Learn etc. angewiesen, die zusätzlich zu Python auf unserem System installiert werden müssen. Üblicherweise können diese Pakete mit dem in Python eingebauten Paketmanager `pip` installiert werden. Beispielsweise würde der Befehl `pip install pandas` das Paket Pandas auf unserem Rechner in einer globalen Umgebung installieren, sodass alle Python-Skripte direkt damit arbeiten können. Wenn wir jedoch an mehreren Projekten gleichzeitig arbeiten oder unser Projekt mit anderen teilen möchten, stoßen wir schnell auf ein Problem. Die global installierten Pakete von `pip` werden in einer bestimmten Version installiert. Projekte können jedoch aufgrund ihrer Historie auf unterschiedliche Versionen der Pakete angewiesen sein. Daher ist es nicht ratsam, diese immer global zu installieren. An dieser Stelle kommen virtuelle Umgebungen oder Virtual Environments ins Spiel, bei denen Pakete in einem speziellen Ordner für jedes Projekt individuell installiert werden.

## Was ist UV?

UV ist ein Paketmanager für Python, ein kleines Hilfsprogramm, das zusätzlich zu Python installiert wird und uns bei der Arbeit mit virtuellen Umgebungen unterstützt. Mit UV können wir unsere Python-Projekte aufsetzen und beliebige Pakete für diese Projekte installieren. UV sorgt dafür, dass alle Pakete kompatibel zueinander sind und dokumentiert die verwendeten Pakete in einer eigenen Datei namens `pyproject.toml`. Dies hat den Vorteil, dass unsere Projekte sauber voneinander getrennt sind. Zudem hilft es dabei, unsere Projekte mit anderen auf GitHub zu teilen, da wir nicht alle Pakete mit unserem Projekt ausliefern müssen. Da UV die installierten Pakete in der `pyproject.toml`-Datei dokumentiert, reicht es aus, diese Datei in unserem Projekt vorzuhalten. Wenn andere nun die gleichen Pakete installieren möchten, kann UV diese automatisch in der richtigen Konfiguration installieren.

UV legt dabei einen `.venv`-Ordner in deinem Projektverzeichnis an. Dieser Ordner enthält alle installierten Pakete und die Python-Umgebung. Da dieser Ordner sehr groß werden kann und für jedes System neu erstellt werden sollte, gehört er nicht ins Git-Repository. Wir werden später noch sehen, wie wir ihn in der `.gitignore`-Datei ausschließen können.

Es gibt neben UV noch weitere Paketmanager, die für diesen Zweck genutzt werden können. `pip` ist der bekannteste von ihnen, da er mit Python geliefert wird und nicht zusätzlich installiert werden muss. Anaconda ist ebenfalls ein beliebter Paketmanager und vor allem im Bereich Data Science sehr verbreitet. Wir haben uns hier für UV entschieden, weil es deutlich moderner und schneller ist als die genannten Alternativen.


## Installation von UV

Zunächst müssen wir verstehen, dass UV ein rein Terminal basiertes Programm ist. Es bietet also keine grafische Benutzeroberfläche sondern wird über ein sogenanntes Terminal bedient. Das bedeutet, dass wir alle Aktionen in Form von Text-Befehlen ausführen müssen. Dazu kannst du unter Windows die `PowerShell` und unter MacOS/Linux das Terminal verwenden. Solltest du noch keine Erfahrung mit dem Terminal haben kannst du dir in unserem [Leitfaden zum Terminal](terminal_guide.md) die Grundlagen anschauen.

Je nachdem, welches Betriebssystem du verwendest, gibt es verschiedene Wege UV zu installieren. Für eine genauere beschreibung schaue in die [Dokumentation](https://docs.astral.sh/uv/getting-started/installation/) von UV.

Führe folgende Befehle, je nach Betreibssystem, in deinem Terminal aus.

### Windows
Windows hat einen eigenen Packetmanager für Programme namens Winget. Öffne eine PowerShell Konsole und gib folgenden Befehl ein:
```bash
winget install --id=astral-sh.uv  -e
```

Sollte das nicht funktionieren ist Winget auf deinem System noch nicht verfügbar. Versuche alternativ folgenden Befehl:
```bash
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### macOS / Linux
Für macOS und Linux systeme können wir UV über curl herunterladen und direkt installieren:
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

---


Solltest du Probleme mit der Installation haben schaue in die [Dokumentation](https://docs.astral.sh/uv/getting-started/installation/) oder melde dich beim Mentoring Team von StackFuel.

Nach der Installation kannst du prüfen, ob alles geklappt hat:
```bash
uv --version
```

Wir können in diesem Leitfaden nur die Grundlagen von UV behandeln. Falls du dich dafür interessierst was mit UV noch alles möglich ist lege ich dir die [Offizielle Dokumentation](https://docs.astral.sh/uv/getting-started/) der Entwickler ans Herz.



## Projekt erstellen (uv init)

Lass uns ein neues Data Science Projekt erstellen! Lege zunächst einen neuen Ordner an und wechsle hinein:

```bash
mkdir mein-data-projekt
cd mein-data-projekt
```

Jetzt initialisieren wir das Projekt mit UV:

```bash
uv init
```

**Wichtige Parameter für uv init:**
- `--python`: Legt die Python-Version fest, z.B. `uv init --python=3.11`
- `--name`: Setzt den Projektnamen, z.B. `uv init --name="mein-data-projekt"`

UV hat jetzt ein neues Projekt in unserem Ordner angelegt und einige Dateien und Ordner erstellt.


**pyproject.toml**: Dies ist deine Projekt-Konfigurationsdatei. Sie sieht etwa so aus:
```toml
[project]
name = "mein-data-projekt"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
requires-python = ">=3.12"
dependencies = []
```
Dies ist ein Konfigurationsdatei in der wichtige Informationen über unser Projekt abgelegt werden. Programme wie UV nutzen diese Datei um Einstellungen für das Projekt zu verwalten. Wenn du dich dafür interessiert wie diese Datei Aufgebaut ist und funktioniert kannst du gerne einen Blick in den Offiziellen [Python Packaging Guide](https://packaging.python.org/en/latest/guides/writing-pyproject-toml/) werfen. Für den Anfang musst du aber nur wissen, das UV hier einige Metadaten für unser Projekt angelegt hat und unter dem Punkt `dependencies` die Namen der benötigten Packete für unser Projekt hinterlegt.

**.python-version**: Enthält die Python-Version für dein Projekt. Z.B.:
```
3.12
```

**uv.lock**: Diese Datei speichert die exakten Versionen aller installierten Pakete. UV wird versuchen diese stehts mit der `pyproject.toml` und den tatsächlich installierten Packeten im `.venv` Ordner synchron zu halten.

Darüber hinaus hat UV wahrscheinlich die Dateien `README.md`, `hello.py`, `.gitignore` sowie ein git repository im Ordner `.git` angelegt. Falls du die letzten beiden nicht finden kannst musst du vermutlich in deinem Datei Explorer versteckte Elemente einblenden. Die `README.md` dient dazu dein Projekt zu beschreiben und zu Dokumentieren. Diese Datei wird unter GitHub standardmäßig auf der Startseite deines Projekts angezeigt. Die `hello.py` datei kannst du zum testen deines Setups verwenden. Falls du mit dem `.git` Ordner oder der `.gitignore` Datei nichts anfangen kannst schau dir unseren [Git Leitfaden](git_guide.md) an.


Diese drei Dateien sollten ins Git Repository aufgenommen werden:
```bash
git add pyproject.toml .python-version uv.lock
git commit -m "Initial project setup"
```

## Pakete installieren (uv add)

<!---
TODO: Weiter Überarbeiten
-->


Für ein Data Science Projekt brauchst du typischerweise einige Bibliotheken. Lass uns die wichtigsten installieren:

```bash
uv add pandas numpy matplotlib scikit-learn
```

Nach diesem Befehl hat sich deine pyproject.toml verändert:
```toml
[project]
name = "mein-data-projekt"
version = "0.1.0"
dependencies = [
    "pandas>=2.2.0",
    "numpy>=1.26.0",
    "matplotlib>=3.8.0",
    "scikit-learn>=1.4.0",
]
```

Die uv.lock Datei enthält jetzt die exakten Versionen und alle Abhängigkeiten dieser Pakete.

## Pakete entfernen

Möchtest du ein Paket wieder entfernen:
```bash
uv remove matplotlib
```

## UV sync vs. UV add

**UV add:**
- Fügt neue Pakete hinzu und aktualisiert pyproject.toml
- Installiert die Pakete direkt
- Gut für die schnelle Entwicklung

**UV sync:**
- Synchronisiert das venv mit pyproject.toml
- Nützlich wenn du das Projekt frisch geklont hast
- Verwendung: `uv sync`

Tipp: Führe `uv sync` aus, wenn deine Teammitglieder neue Pakete hinzugefügt haben und du die Änderungen übernehmen möchtest.

## Code ausführen mit UV run

Anstatt das venv zu aktivieren, kannst du deine Python-Skripte direkt mit UV ausführen. Erstellen wir ein einfaches Beispiel:

```python
# analyse.py
import pandas as pd
import numpy as np

data = pd.DataFrame({
    'x': np.random.randn(100),
    'y': np.random.randn(100)
})
print("Erste 5 Zeilen unserer Daten:")
print(data.head())
print("\nStatistische Zusammenfassung:")
print(data.describe())
```

Ausführen:
```bash
uv run python analyse.py
```

## UV tool verwenden

UV kann auch Python-Tools direkt ausführen. Ein besonders nützliches Tool für Data Science Projekte ist Ruff. Ruff ist ein ultraschneller Python Linter und Formatter in einem. Es hilft dir dabei:
- Code-Stil konsistent zu halten
- Potenzielle Fehler zu finden
- Performance-Probleme aufzudecken
- Unnötigen Code zu identifizieren

Lass uns Ruff installieren und verwenden:

```bash
uv add ruff
```

Jetzt können wir unseren Code mit Ruff überprüfen:
```bash
uv tool ruff check analyse.py
```

Und automatisch formatieren:
```bash
uv tool ruff format analyse.py
```

Ein großer Vorteil von Ruff ist, dass es viele verschiedene Lint-Tools ersetzt (wie flake8, isort, pycodestyle) und dabei viel schneller ist. Du kannst die Regeln in der pyproject.toml konfigurieren:

```toml
[tool.ruff]
# Aktiviere zusätzliche Regeln
select = [
    "E",  # Pycodestyle Fehler
    "F",  # Pyflakes
    "I",  # isort
    "N",  # PEP8 Naming
]
# Ignoriere bestimmte Regeln wenn nötig
ignore = []
```

## UVX für schnellen Zugriff

UVX ist wie eine Abkürzung - du kannst Python-Tools direkt ausführen, ohne sie erst zu installieren:

```bash
uvx ruff check analyse.py
```

## Praktische Tipps

1. **Projektstruktur**: Lege von Anfang an eine gute Struktur fest:
```
mein-data-projekt/
├── data/               # Rohdaten
├── notebooks/          # Jupyter Notebooks
├── src/               # Python Module
├── .gitignore         # Git-Ignore Datei
├── pyproject.toml     # Projekt-Konfiguration
├── .python-version    # Python Version
└── uv.lock           # Lock-Datei
```

2. **Requirements für unterschiedliche Umgebungen**: Du kannst in pyproject.toml verschiedene Abhängigkeitsgruppen definieren:
```toml
[project]
name = "mein-data-projekt"
version = "0.1.0"
dependencies = [
    "pandas>=2.2.0",
    "numpy>=1.26.0",
]

[project.optional-dependencies]
dev = [
    "ruff>=0.2.0",
    "pytest>=7.0.0",
]
```

3. **Jupyter Integration**: Für Jupyter Notebooks:
```bash
uv add jupyter
uv run jupyter notebook
```

Denk daran: UV kümmert sich um dein venv im Hintergrund - du musst es nie manuell aktivieren. Alle Befehle funktionieren direkt mit `uv run` oder `uv tool`.

## Git Best Practices

Hier noch einmal zusammengefasst, was in Git gehört und was nicht:

**In Git aufnehmen (git add):**
- pyproject.toml
- .python-version
- uv.lock
- .gitignore
- Deine Python-Skripte und Notebooks

**Nicht in Git aufnehmen (in .gitignore):**
- .venv/
- __pycache__/
- .ipynb_checkpoints/
- Lokale Konfigurationsdateien
- Große Datensätze

## Nächste Schritte

Jetzt bist du bereit, mit deinem Team am Data Science Projekt zu arbeiten! Denk daran:
- Committe immer die pyproject.toml und uv.lock
- Nutze `uv sync` nach dem Klonen oder Pull
- Verwende Ruff regelmäßig, um deinen Code sauber zu halten
- Teile neue Abhängigkeiten mit deinem Team

Viel Erfolg bei deinem Projekt! 🚀
