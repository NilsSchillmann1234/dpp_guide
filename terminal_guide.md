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

- **Windows (PowerShell)**: `Get-ChildItem | Format-Table -AutoSize`
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
mkdir data
```

> _Hinweis_: Du solltest deinen Projektordner immer direkt in VSCode öffnen und nicht als Ordner über das Terminal anlegen. Du kannst aber gerne Unterordner anlegen um Beispielsweise Code und Daten zu trennen.

````bash

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
````

> _Hinweis_: Du kannst neue Ordner und Dateien auch direkt in VS Code erstellen, indem du mit der rechten Maustaste auf den gewünschten Ordner klickst und "Neuer Ordner" oder "Neue Datei" auswählst.

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

- **Windows (PowerShell/CMD)**: `cls` oder `Clear-Host` oder `Strg + L`
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

### Mehrere Terminal-Fenster

Du kannst mehrere Terminal-Fenster nebeneinander öffnen:

1. Klicke auf das Plus-Symbol im Terminal-Bereich
2. Klicke auf das Split-Symbol (neben dem Plus), um das Terminal zu teilen

### Terminal-Schriftgröße ändern

1. `Strg + +` / `Strg + -` (oder `Cmd + +` / `Cmd + -` auf macOS) _gilt für ganz VSCode_
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

## Zusammenfassung

Das Terminal ist ein mächtiges Werkzeug, das dir hilft, effizienter mit deinem Computer zu arbeiten. Mit den grundlegenden Befehlen, die du in diesem Leitfaden gelernt hast, bist du gut gerüstet, um mit dem UV-Paketmanager in VS Code zu arbeiten.

Die wichtigsten Punkte:

- Das Terminal öffnest du in VS Code mit `Strg + ö` (Windows/Linux) oder `Cmd + ö` (macOS)
- Mit `cd`, `ls`/`dir` navigierst du durch das Dateisystem
- Tab-Vervollständigung und Befehlsverlauf helfen dir, effizienter zu arbeiten

Je mehr du das Terminal benutzt, desto vertrauter wirst du damit. Scheue dich nicht, es auszuprobieren – du kannst immer `Strg + C` drücken, um einen Befehl abzubrechen, wenn etwas nicht wie erwartet funktioniert.

Falls du weitere Fragen hast oder auf Probleme stößt, melde dich beim Mentoring-Team von StackFuel.
