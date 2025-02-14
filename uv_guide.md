# UV Python Paketmanagement Leitfaden

Hey! Schön, dass du dich für UV interessierst. In diesem Leitfaden zeige ich dir, wie du UV für dein Data Science Projekt nutzen kannst. UV ist ein moderner und schneller Paketmanager für Python, der dir dabei hilft, deine Projektumgebung sauber und übersichtlich zu halten. 

## Was ist ein Virtual Environment?

Bevor wir mit UV loslegen, lass uns kurz über Virtual Environments (venv) sprechen. Ein venv ist wie ein eigener, isolierter Raum für dein Projekt. Hier können wir Python-Pakete installieren, ohne dass sie sich mit anderen Projekten in die Quere kommen. UV erstellt und verwaltet diese venvs automatisch für uns - du musst sie nicht mal aktivieren! 

UV legt dabei einen `.venv` Ordner in deinem Projektverzeichnis an. Dieser Ordner enthält alle installierten Pakete und die Python-Umgebung. Da dieser Ordner sehr groß werden kann und für jedes System neu erstellt werden sollte, gehört er nicht ins Git Repository. Wir werden später noch sehen, wie wir ihn in der `.gitignore` Datei ausschließen.

## Installation von UV

Je nachdem, welches Betriebssystem du verwendest, gibt es verschiedene Wege UV zu installieren:

**macOS**:
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**Linux**:
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**Windows**:
```bash
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Nach der Installation kannst du prüfen, ob alles geklappt hat:
```bash
uv --version
```

## Projekt erstellen

Lass uns ein neues Data Science Projekt erstellen! Erstelle zuerst einen neuen Ordner und wechsle hinein:

```bash
mkdir mein-data-projekt
cd mein-data-projekt
```

Da wir mit Git arbeiten werden, initialisieren wir zuerst ein Git Repository und erstellen eine `.gitignore` Datei:

```bash
git init
echo ".venv/" > .gitignore
```

Jetzt initialisieren wir das Projekt mit UV:

```bash
uv init
```

**Wichtige Parameter für uv init:**
- `--python`: Legt die Python-Version fest, z.B. `uv init --python=3.11`
- `--name`: Setzt den Projektnamen, z.B. `uv init --name="Mein Data Projekt"`

UV hat jetzt drei wichtige Dateien erstellt:

1. **pyproject.toml**: Dies ist deine Projekt-Konfigurationsdatei. Sie sieht etwa so aus:
```toml
[project]
name = "mein-data-projekt"
version = "0.1.0"
dependencies = []
```

2. **.python-version**: Enthält die Python-Version für dein Projekt:
```
3.11
```

3. **uv.lock**: Diese Datei speichert die exakten Versionen aller installierten Pakete. Sie sollte mit ins Git-Repository!

Diese drei Dateien sollten ins Git Repository aufgenommen werden:
```bash
git add pyproject.toml .python-version uv.lock
git commit -m "Initial project setup"
```

## Pakete installieren

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
