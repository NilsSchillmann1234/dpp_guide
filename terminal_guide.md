<!-- Hier ist ein Leitfaden zum Package Manager UV, den ich für die Teilnehmer eines Projekt-Portfolio Kurses in meinem Unternehmen erstellt habe. Der Leitfaden baut stark auf den einsatz des Integrierten Terminals von Visual Studio Code auf. Da viele unsere Teilnehmer nicht mit dem Terminal vertraut sind, möchte ich, dass du einen weiteren Leitfaden zum Umgang mit dem Terminal (Für Windows und MacOS nutzer) erstellst. Der Leitfaden sollte die grundlegenden Befehle und Konzepte abdecken, die für die Arbeit mit dem Terminal in VSCode erforderlich sind. Vor allem sollte der Leitfaden gut auf die Arbeit mit dem UV-Paketmanager abgestimmt sein, wobei die Arbeit mit UV in dem bereitgestellten Leitfaden bereits behandelt wird. Der Leitfaden sollte auch einige Beispiele enthalten, die den Teilnehmern helfen, die Konzepte zu verstehen und anzuwenden. Der Leitfaden sollte in Markdown-Format verfasst sein und gut strukturiert sein, um eine einfache Navigation zu ermöglichen. Verwende Überschriften, Absätze und Listen, um den Text klar und übersichtlich zu gestalten. Achte darauf, dass der Leitfaden für Anfänger geeignet ist und keine Vorkenntnisse im Umgang mit dem Terminal voraussetzt. Verwende den gleichen Duktus wie in dem bereitgestellten Leitfaden, um eine konsistente Sprache und Terminologie zu gewährleisten.  -->



# Terminal-Leitfaden für Visual Studio Code

In diesem Leitfaden lernst du die grundlegenden Konzepte und Befehle für die Arbeit mit dem Terminal in Visual Studio Code (VS Code) kennen. Das Terminal ist ein leistungsstarkes Werkzeug, mit dem du Programme wie den UV-Paketmanager steuern kannst, ohne die grafische Benutzeroberfläche zu verwenden.

## Was ist ein Terminal?

Ein Terminal (auch Kommandozeile oder Konsole genannt) ist eine textbasierte Schnittstelle zum Betriebssystem. Statt mit der Maus zu klicken, gibst du Textbefehle ein, die dein Computer ausführt. Obwohl das zunächst einschüchternd wirken kann, bietet das Terminal eine effiziente und präzise Möglichkeit, mit deinem Computer zu interagieren.

In VS Code ist das Terminal bereits integriert, sodass du es direkt in deiner Programmierumgebung nutzen kannst, ohne zwischen verschiedenen Anwendungen wechseln zu müssen.

## Das Terminal in VS Code öffnen

Es gibt mehrere Möglichkeiten, das Terminal in VS Code zu öffnen:

- **Über das Menü**: Wähle `Terminal` > `Neues Terminal` in der Menüleiste.
- **Über die Tastenkombination**: 
  - Windows/Linux: `Strg + Umschalt + ö` oder `Strg + #`
  - macOS: `Cmd + Umschalt + ö`
- **Über die Kommandopalette**: Drücke `Strg + Umschalt + P` (Windows/Linux) oder `Cmd + Umschalt + P` (macOS), gib "Terminal: Neues Terminal erstellen" ein und drücke Enter.

Das Terminal erscheint dann im unteren Bereich deines VS Code-Fensters:

![VS Code Terminal](Hier könnte ein Bild des VS Code Terminals stehen.)

## Terminal-Typen

Je nach Betriebssystem gibt es unterschiedliche Standard-Terminals:

- **Windows**: PowerShell (neuere Windows-Versionen) oder Command Prompt (cmd.exe)
- **macOS**: zsh (neuere macOS-Versionen) oder bash
- **Linux**: Meistens bash oder eine andere Shell deiner Distribution

Du kannst zwischen verschiedenen Terminal-Typen wechseln, indem du das Dropdown-Menü neben dem Plus-Symbol im Terminal-Bereich verwendest.

## Grundlegende Terminalbefehle

### Navigation im Dateisystem

Das Dateisystem deines Computers ist wie eine Baumstruktur organisiert, mit Ordnern (Verzeichnissen) und Dateien. Mit dem Terminal kannst du dich durch diese Struktur bewegen:

#### Aktuelles Verzeichnis anzeigen

Um zu sehen, in welchem Verzeichnis du dich gerade befindest:

- **Windows (PowerShell/CMD)**: `pwd` oder `cd`
- **macOS/Linux**: `pwd` (Print Working Directory)

```bash
pwd
# Beispielausgabe: /Users/deinname/projekte/mein-data-projekt
```

#### Inhalt eines Verzeichnisses anzeigen

Um alle Dateien und Ordner im aktuellen Verzeichnis anzuzeigen:

- **Windows (PowerShell)**: `dir` oder `ls`
- **Windows (CMD)**: `dir`
- **macOS/Linux**: `ls` (List)

```bash
ls
# Beispielausgabe: .git  .gitignore  .python-version  .venv  README.md  hello.py  pyproject.toml  uv.lock
```

Um mehr Details zu den Dateien anzuzeigen:

- **Windows (PowerShell)**: `ls -l` oder `Get-ChildItem | Format-Table -AutoSize`
- **Windows (CMD)**: `dir`
- **macOS/Linux**: `ls -l` (Liste mit Details)

#### In ein Verzeichnis wechseln

Um in einen anderen Ordner zu wechseln:

- **Alle Betriebssysteme**: `cd pfad/zum/ordner` (Change Directory)

```bash
cd mein-data-projekt
```

Um zum übergeordneten Verzeichnis zu wechseln:

- **Alle Betriebssysteme**: `cd ..`

```bash
cd ..
# Wenn du vorher in /Users/deinname/projekte/mein-data-projekt warst,
# bist du jetzt in /Users/deinname/projekte
```

Um zum Heimatverzeichnis (Home) zu wechseln:

- **Alle Betriebssysteme**: `cd` oder `cd ~`

```bash
cd
# Wechselt zu deinem Benutzerverzeichnis, z.B. /Users/deinname
```

#### Verzeichnis erstellen

Um einen neuen Ordner zu erstellen:

- **Alle Betriebssysteme**: `mkdir ordnername` (Make Directory)

```bash
mkdir neues-projekt
```

### Dateien und Ordner verwalten

#### Datei erstellen

Eine leere Datei erstellen:

- **Windows (PowerShell)**: `New-Item -ItemType File -Name dateiname.txt`
- **Windows (CMD)**: `type nul > dateiname.txt`
- **macOS/Linux**: `touch dateiname.txt`

```bash
# macOS/Linux
touch test.py

# Windows PowerShell
New-Item -ItemType File -Name test.py
```

#### Datei löschen

Eine Datei löschen:

- **Windows (PowerShell)**: `Remove-Item dateiname.txt` oder `del dateiname.txt`
- **Windows (CMD)**: `del dateiname.txt`
- **macOS/Linux**: `rm dateiname.txt` (Remove)

```bash
# macOS/Linux
rm test.py

# Windows PowerShell
Remove-Item test.py
```

#### Ordner löschen

Einen leeren Ordner löschen:

- **Windows (PowerShell)**: `Remove-Item ordnername` oder `rmdir ordnername`
- **Windows (CMD)**: `rmdir ordnername`
- **macOS/Linux**: `rmdir ordnername`

```bash
rmdir leerer-ordner
```

Einen Ordner mit Inhalt löschen (Vorsicht!):

- **Windows (PowerShell)**: `Remove-Item -Recurse -Force ordnername`
- **Windows (CMD)**: `rmdir /s /q ordnername`
- **macOS/Linux**: `rm -rf ordnername`

```bash
# macOS/Linux
rm -rf nicht-mehr-benoetigter-ordner

# Windows PowerShell
Remove-Item -Recurse -Force nicht-mehr-benoetigter-ordner
```

### Hilfe erhalten

Wenn du nicht weißt, wie ein Befehl funktioniert, kannst du die Hilfe aufrufen:

- **Windows (PowerShell)**: `Get-Help befehlsname` oder `befehlsname -?`
- **Windows (CMD)**: `befehlsname /?`
- **macOS/Linux**: `man befehlsname` oder `befehlsname --help`

```bash
# macOS/Linux
man ls

# Windows PowerShell
Get-Help Get-ChildItem
```

## Pfade im Terminal verstehen

### Absolute und relative Pfade

- **Absolute Pfade** beginnen mit dem Wurzelverzeichnis:
  - Windows: `C:\Users\deinname\projekte`
  - macOS/Linux: `/Users/deinname/projekte`

- **Relative Pfade** beziehen sich auf dein aktuelles Verzeichnis:
  - `./datei.txt` (Datei im aktuellen Verzeichnis)
  - `../datei.txt` (Datei im übergeordneten Verzeichnis)
  - `ordner/datei.txt` (Datei im Unterordner)

### Besondere Pfadsymbole

- `.` - Das aktuelle Verzeichnis
- `..` - Das übergeordnete Verzeichnis
- `~` - Dein Heimatverzeichnis (Home)

```bash
# Beispiele
cd ~/projekte        # Wechselt zu /Users/deinname/projekte
cd ./unterordner     # Wechselt in den Unterordner des aktuellen Verzeichnisses
cd ../nachbarordner  # Wechselt zum Nachbarordner auf gleicher Ebene
```

## UV-Paketmanager im Terminal verwenden

Jetzt, da du die Grundlagen des Terminals kennst, können wir uns ansehen, wie du den UV-Paketmanager in VS Code verwendest. Hier sind die wichtigsten Befehle, die auch im UV-Leitfaden erklärt werden:

### Projekt initialisieren

```bash
# Verzeichnis erstellen und hineinwechseln
mkdir mein-data-projekt
cd mein-data-projekt

# Projekt mit UV initialisieren
uv init
```

### Pakete installieren

```bash
# Pakete installieren
uv add ipykernel pandas matplotlib
```

### Pakete entfernen

```bash
# Paket entfernen
uv remove matplotlib
```

### Environment synchronisieren

```bash
# Environment mit pyproject.toml synchronisieren
uv sync
```

### Code ausführen

```bash
# Python-Skript mit UV ausführen
uv run hello.py
```

## Praktische Tipps für die Terminal-Nutzung

### Tab-Vervollständigung

Du musst nicht immer den vollständigen Befehl oder Pfad tippen. Drücke die Tab-Taste, um automatisch zu vervollständigen:

1. Beginne mit der Eingabe eines Befehls oder Dateinamens
2. Drücke Tab
3. Wenn es mehrere Möglichkeiten gibt, zeigt dir das Terminal diese an oder vervollständigt bis zum gemeinsamen Teil

```bash
# Beispiel: Tippe 'cd mei' und drücke Tab
cd mei[Tab] → cd mein-data-projekt/
```

### Befehlsverlauf

Du kannst durch deinen Befehlsverlauf navigieren:

- Nach oben/unten mit den Pfeiltasten blättern
- `history` (macOS/Linux) oder `Get-History` (Windows PowerShell) zeigt dir deine letzten Befehle

```bash
# Zeige die letzten Befehle
history
```

### Mehrere Befehle hintereinander ausführen

Du kannst mehrere Befehle in einer Zeile ausführen:

- Mit `&&` (funktioniert auf allen Systemen): Der zweite Befehl wird nur ausgeführt, wenn der erste erfolgreich war

```bash
mkdir neues-projekt && cd neues-projekt && uv init
```

### Befehle abbrechen

Wenn ein Befehl zu lange dauert oder du einen Fehler gemacht hast:

- `Strg + C` bricht den aktuellen Befehl ab

### Terminal-Fenster leeren

Wenn das Terminal zu unübersichtlich wird:

- **Windows (PowerShell/CMD)**: `cls` oder `Clear-Host`
- **macOS/Linux**: `clear` oder `Strg + L`

## Fehlerbehebung im Terminal

### Häufige Fehlermeldungen

#### "Befehl nicht gefunden"

```
uv: command not found
```

Mögliche Lösungen:
- Überprüfe, ob UV korrekt installiert ist
- Bei Windows: Starte VS Code neu, um die PATH-Umgebungsvariable zu aktualisieren
- Verwende den vollständigen Pfad zum UV-Programm

#### "Zugriff verweigert"

```
Permission denied
```

Mögliche Lösungen:
- Bei macOS/Linux: Verwende `sudo` vor dem Befehl (nur wenn du weißt, was du tust!)
- Überprüfe die Berechtigungen der Datei oder des Ordners
- Bei Windows: Starte VS Code als Administrator

#### "Datei oder Verzeichnis nicht gefunden"

```
No such file or directory
```

Mögliche Lösungen:
- Überprüfe, ob du im richtigen Verzeichnis bist (`pwd`)
- Überprüfe die Schreibweise des Datei- oder Ordnernamens
- Liste alle Dateien auf, um zu sehen, was verfügbar ist (`ls` oder `dir`)

## VS Code Terminal-Einstellungen

VS Code bietet viele Möglichkeiten, dein Terminal anzupassen:

### Terminal-Typ ändern

1. Öffne die VS Code-Einstellungen (`Strg + ,` oder `Cmd + ,`)
2. Suche nach "terminal.integrated.defaultProfile"
3. Wähle dein Betriebssystem und dann deinen bevorzugten Terminal-Typ

### Mehrere Terminal-Fenster

Du kannst mehrere Terminal-Fenster nebeneinander öffnen:

1. Klicke auf das Plus-Symbol im Terminal-Bereich
2. Klicke auf das Split-Symbol (neben dem Plus), um das Terminal zu teilen

### Terminal-Schriftgröße ändern

1. `Strg + +` / `Strg + -` (oder `Cmd + +` / `Cmd + -` auf macOS)
2. Oder über die Einstellungen: Suche nach "terminal.integrated.fontSize"

## Übungen zum Ausprobieren

Hier sind einige Übungen, mit denen du deine Terminal-Fähigkeiten verbessern kannst:

### Übung 1: Navigation und Dateioperationen

1. Öffne das Terminal in VS Code
2. Erstelle einen neuen Ordner namens "terminal-übung"
3. Wechsle in diesen Ordner
4. Erstelle eine leere Datei namens "test.txt"
5. Liste den Inhalt des Ordners auf
6. Wechsle zurück zum übergeordneten Verzeichnis

```bash
# Lösung
mkdir terminal-übung
cd terminal-übung
touch test.txt  # oder New-Item -ItemType File -Name test.txt (Windows PowerShell)
ls  # oder dir (Windows CMD)
cd ..
```

### Übung 2: UV-Projekt erstellen

1. Erstelle einen neuen Ordner für ein UV-Projekt
2. Initialisiere ein neues UV-Projekt
3. Füge die Pakete "pandas" und "matplotlib" hinzu
4. Erstelle eine Python-Datei namens "plot.py"
5. Führe die Datei mit UV aus

```bash
# Lösung
mkdir uv-übung
cd uv-übung
uv init
uv add pandas matplotlib
touch plot.py  # oder New-Item -ItemType File -Name plot.py (Windows PowerShell)
# Füge Code zu plot.py hinzu
uv run plot.py
```

## Zusammenfassung

Das Terminal ist ein mächtiges Werkzeug, das dir hilft, effizienter mit deinem Computer zu arbeiten. Mit den grundlegenden Befehlen, die du in diesem Leitfaden gelernt hast, bist du gut gerüstet, um mit dem UV-Paketmanager in VS Code zu arbeiten.

Die wichtigsten Punkte:
- Das Terminal öffnest du in VS Code mit `Strg + Umschalt + ö` (Windows/Linux) oder `Cmd + Umschalt + ö` (macOS)
- Mit `cd`, `ls`/`dir` und `mkdir` navigierst du durch das Dateisystem
- UV-Befehle werden direkt im Terminal ausgeführt: `uv init`, `uv add`, `uv sync`, `uv run`
- Tab-Vervollständigung und Befehlsverlauf helfen dir, effizienter zu arbeiten

Je mehr du das Terminal benutzt, desto vertrauter wirst du damit. Scheue dich nicht, es auszuprobieren – du kannst immer `Strg + C` drücken, um einen Befehl abzubrechen, wenn etwas nicht wie erwartet funktioniert.

Falls du weitere Fragen hast oder auf Probleme stößt, melde dich beim Mentoring-Team von StackFuel.

Viel Erfolg bei deinen Python-Projekten!