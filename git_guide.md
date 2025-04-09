# Git und GitHub Leitfaden für Portfolio-Projekte

In diesem Leitfaden zeige ich dir, wie du Git und GitHub für dein Portfolio-Projekt nutzen kannst. Git ist ein unverzichtbares Werkzeug für die Versionskontrolle deiner Code-Dateien, während GitHub dir ermöglicht, dein Projekt zu veröffentlichen und mit anderen zu teilen.

## Was ist Versionskontrolle?

Stell dir vor, du schreibst an einem Jupyter Notebook für deine Datenanalyse. Nach einigen Tagen Arbeit merkst du, dass dein Code nicht mehr funktioniert. Du hast aber keine Ahnung, was genau du verändert hast und möchtest zu einer älteren, funktionierenden Version deines Codes zurückkehren. Vielleicht kennst du auch die folgende Situation: Du speicherst deine Dateien als `projekt.ipynb`, `projekt_final.ipynb`, `projekt_final_v2.ipynb` und irgendwann verlierst du den Überblick.

An dieser Stelle kommt Git ins Spiel. Git ist ein Versionskontrollsystem, das es dir ermöglicht, Änderungen an deinen Dateien zu verfolgen, frühere Versionen wiederherzustellen und mit anderen zusammenzuarbeiten. Mit Git erstellst du regelmäßig "Schnappschüsse" (Commits) deines Projekts. Diese Schnappschüsse kannst du jederzeit ansehen und bei Bedarf zu ihnen zurückkehren.

## Was ist Git?

Git ist ein dezentrales Versionskontrollsystem, das ursprünglich für die Entwicklung des Linux-Kernels entwickelt wurde. Es erlaubt dir:

1. **Änderungen zu verfolgen**: Git dokumentiert, wer wann welche Änderungen vorgenommen hat.
2. **Zusammenarbeit**: Mehrere Personen können gleichzeitig am selben Projekt arbeiten, ohne sich gegenseitig zu stören.
3. **Versionen zu verwalten**: Du kannst zu jedem früheren Zustand deines Projekts zurückkehren.
4. **Parallel zu arbeiten**: Du kannst an verschiedenen Funktionen gleichzeitig arbeiten, ohne das Hauptprojekt zu beeinträchtigen.

## Was ist GitHub?

GitHub ist eine webbasierte Plattform, die Git als Grundlage nutzt. Es bietet zusätzliche Funktionen wie:

1. **Remote Repositories**: Ein zentraler Ort, an dem dein Code gespeichert wird und auf den alle Teammitglieder zugreifen können.
2. **Issues und Pull Requests**: Werkzeuge zur Diskussion von Änderungen und Problemen.
3. **Projektmanagement**: Kanban-Boards, Meilensteine und mehr zur Organisation deiner Arbeit.
4. **Social Coding**: Andere Entwickler können dein Projekt sehen, "forken" (kopieren) und dazu beitragen.

GitHub ist wie ein soziales Netzwerk für Code. Es erleichtert die Zusammenarbeit und ist ideal, um dein Portfolio zu präsentieren.

## Installation von Git

Git ist ein Kommandozeilenprogramm, das du auf deinem Computer installieren musst. Obwohl wir Git hauptsächlich über die grafische Oberfläche von VS Code verwenden werden, ist es wichtig, dass Git auf deinem System installiert ist.

### Windows

Du kannst Git unter Windows mit dem eingbauten Paketmanager `winget` installieren:

Öffne dazu die PowerShell und führe den folgenden Befehl aus:

```powershell
winget install --id Git.Git -e --source winget
```

Sollte das nicht funktionieren kannst du Git auch manuell installieren:

1. Besuche die offizielle Git-Website: [https://git-scm.com/download/win](https://git-scm.com/download/win)
2. Lade den Installer herunter und führe ihn aus.
3. Die Standardeinstellungen sind in der Regel in Ordnung. Achte darauf, dass "Git Bash" und "Git GUI" ausgewählt sind und das git zum PATH hinzugefügt wird.

### macOS

1. Die einfachste Methode ist die Installation über Homebrew:
   ```bash
   brew install git
   ```
2. Alternativ kannst du Git auch von der offiziellen Website herunterladen: [https://git-scm.com/download/mac](https://git-scm.com/download/mac)

### Linux

Verwende den Paketmanager deiner Distribution:

```bash
# Für Ubuntu/Debian
sudo apt-get update
sudo apt-get install git

# Für Fedora
sudo dnf install git
```

Nach der Installation kannst du überprüfen, ob Git korrekt installiert ist:

```bash
git --version
```

## Git-Konfiguration

Bevor du Git verwendest, solltest du deinen Namen und deine E-Mail-Adresse konfigurieren. Dies ist wichtig, da Git diese Informationen bei jedem Commit speichert.

```bash
git config --global user.name "Dein Name"
git config --global user.email "deine.email@example.com"
```

## Die wichtigsten Git-Konzepte

Bevor wir mit den ersten Befehlen starten, ist es wichtig, einige grundlegende Konzepte zu verstehen:

### Repository

Ein Repository (oder kurz "Repo") ist ein Projekt, das von Git verwaltet wird. Es enthält alle Dateien des Projekts sowie die vollständige Versionshistorie. Ein Repository kann lokal auf deinem Computer oder remote auf einem Server wie GitHub existieren.

### Commit

Ein Commit ist ein "Schnappschuss" deines Projekts zu einem bestimmten Zeitpunkt. Jeder Commit hat eine eindeutige ID und eine Nachricht, die beschreibt, welche Änderungen vorgenommen wurden.

### Branch

Ein Branch ist eine parallele Version deines Projekts. Der Hauptbranch wird üblicherweise als "main" (früher "master") bezeichnet. Branches ermöglichen es dir, an neuen Funktionen zu arbeiten, ohne den Hauptcode zu beeinflussen.

### Merge

Beim Mergen werden Änderungen aus einem Branch in einen anderen übernommen. Dies geschieht typischerweise, wenn eine Funktion fertiggestellt ist und in den Hauptbranch integriert werden soll.

### Clone

Das Klonen eines Repositories erstellt eine lokale Kopie eines Remote-Repositories auf deinem Computer.

### Push und Pull

"Push" sendet deine lokalen Änderungen (Commits) an das Remote-Repository (z.B. auf GitHub). "Pull" holt Änderungen aus dem Remote-Repository und integriert sie in deine lokale Kopie.

## Git in VS Code verwenden

VS Code hat eine hervorragende Git-Integration, die es dir ermöglicht, die meisten Git-Aktionen direkt aus der grafischen Oberfläche auszuführen.

### Ein neues Repository erstellen

1. Öffne deinen Projektordner in VS Code.
2. Klicke auf das Source-Control-Symbol in der linken Seitenleiste (es sieht aus wie eine Verzweigung).
3. Klicke auf "Initialize Repository" oder drücke auf "Publish to GitHub".

Alternativ kannst du ein Repository auch über die Kommandozeile erstellen:

```bash
cd mein-projekt
git init
```

### Änderungen vornehmen und committen

1. Nachdem du Änderungen an deinen Dateien vorgenommen hast, werden diese in VS Code im Source-Control-Tab angezeigt.
2. Klicke auf das "+" neben den geänderten Dateien, um sie zu "stagen" (für den nächsten Commit vorzumerken).
3. Gib eine aussagekräftige Commit-Nachricht ein, die beschreibt, was du geändert hast.
4. Klicke auf den Haken (✓) oder drücke Ctrl+Enter, um die Änderungen zu committen.

Über die Kommandozeile würde das so aussehen:

```bash
git add .                   # Alle Änderungen stagen
git commit -m "Beschreibung der Änderungen"  # Änderungen committen
```

### Verbindung zu GitHub herstellen

Um dein lokales Repository mit GitHub zu verbinden, musst du ein Repository auf GitHub erstellen und es als "Remote" hinzufügen.

In VS Code:
1. Öffne die Command Palette (Ctrl+Shift+P).
2. Gib "Git: Add Remote" ein und wähle diese Option aus.
3. Füge die URL deines GitHub-Repositories ein (z.B. `https://github.com/dein-username/dein-repo.git`).
4. Gib einen Namen für den Remote ein (normalerweise "origin").

Über die Kommandozeile:

```bash
git remote add origin https://github.com/dein-username/dein-repo.git
```

### Änderungen pushen

Nachdem du Änderungen committet hast, kannst du sie zu GitHub pushen:

In VS Code:
1. Klicke auf die Schaltfläche "Publish Branch" oder "Sync" in der Statusleiste unten links.

Über die Kommandozeile:

```bash
git push -u origin main  # Beim ersten Push
git push                 # Bei nachfolgenden Pushes
```

### Änderungen pullen

Wenn andere Änderungen am Repository vorgenommen haben, musst du diese zu deiner lokalen Kopie hinzufügen:

In VS Code:
1. Klicke auf die Schaltfläche "Sync" in der Statusleiste oder im Source-Control-Tab.

Über die Kommandozeile:

```bash
git pull
```

## Git-Workflow für Portfolio-Projekte

Hier ist ein typischer Workflow für dein Portfolio-Projekt:

1. **Repository einrichten**:
   - Erstelle ein neues Repository auf GitHub.
   - Klone es auf deinen Computer oder initialisiere ein neues lokales Repository und verbinde es mit GitHub.

2. **Projekte strukturieren**:
   - Erstelle eine klare Ordnerstruktur für dein Projekt.
   - Füge eine README.md-Datei hinzu, die dein Projekt beschreibt.
   - Denke an eine `.gitignore`-Datei, um nicht benötigte Dateien auszuschließen (wie den `.venv`-Ordner).

3. **Regelmäßig committen**:
   - Mache kleine, häufige Commits, die jeweils eine Änderung oder eine Funktion abschließen.
   - Schreibe aussagekräftige Commit-Nachrichten.

4. **Mit Branches arbeiten** (fortgeschritten):
   - Nutze Branches für neue Funktionen oder Experimente.
   - Merge sie zurück in den Hauptbranch, wenn du zufrieden bist.

5. **Regelmäßig pushen und pullen**:
   - Pushe deine Änderungen regelmäßig zu GitHub, um eine Sicherung zu haben.
   - Pulle Änderungen, wenn du an mehreren Computern arbeitest oder mit anderen zusammenarbeitest.

## Die `.gitignore`-Datei

Die `.gitignore`-Datei ist eine wichtige Komponente deines Git-Projekts. Sie gibt an, welche Dateien und Ordner Git ignorieren soll. Das ist besonders nützlich für:

- Große Dateien, die nicht ins Repository gehören
- Generierte Dateien, die jeder selbst erzeugen kann
- Vertrauliche Informationen wie API-Schlüssel oder Passwörter
- Umgebungsspezifische Dateien wie der `.venv`-Ordner

Ein Beispiel für eine `.gitignore`-Datei für ein Python-Datenprojekt:

```
# Python virtual environment
.venv/
venv/
ENV/

# Python cache files
__pycache__/
*.py[cod]
*$py.class

# Jupyter Notebook
.ipynb_checkpoints

# Distribution / packaging
dist/
build/
*.egg-info/

# Local configuration
.env
config.local.json

# VS Code settings
.vscode/

# OS generated files
.DS_Store
Thumbs.db
```

VS Code erstellt normalerweise automatisch eine `.gitignore`-Datei, wenn du ein neues Repository initialisierst, aber du kannst sie auch manuell erstellen und bearbeiten.

## Best Practices

Hier sind einige Best Practices für die Arbeit mit Git:

1. **Committen und pushen nicht vergessen**: Mache es dir zur Gewohnheit, am Ende jeder Arbeitssitzung zu committen und zu pushen.

2. **Aussagekräftige Commit-Nachrichten**: Eine gute Commit-Nachricht erklärt, WAS geändert wurde und WARUM.

3. **Kleine, fokussierte Commits**: Jeder Commit sollte eine logische Einheit sein, die eine bestimmte Änderung oder Funktion abschließt.

4. **Branches für neue Funktionen**: Wenn du an einer neuen Funktion arbeitest, erstelle einen separaten Branch dafür.

5. **Regelmäßige Pulls**: Wenn du mit anderen zusammenarbeitest, pulle regelmäßig, um Konflikte zu vermeiden.

6. **README.md pflegen**: Halte deine README.md-Datei aktuell. Sie ist das Erste, was andere sehen, wenn sie dein Projekt auf GitHub besuchen.

## Typische Probleme und Lösungen

### Merge-Konflikte

Merge-Konflikte treten auf, wenn zwei Personen dieselbe Datei an derselben Stelle geändert haben. Git weiß dann nicht, welche Änderung es behalten soll.

In VS Code werden Merge-Konflikte direkt im Editor angezeigt, und du kannst auswählen, welche Änderung du behalten möchtest. Du kannst auch beide Änderungen kombinieren, wenn das sinnvoll ist.

### Datei aus der Staging-Area entfernen

Wenn du eine Datei versehentlich gestaged hast, kannst du sie unstagen:

In VS Code:
1. Klicke auf das "-" neben der Datei im Source-Control-Tab.

Über die Kommandozeile:

```bash
git reset HEAD dateiname
```

### Lokale Änderungen verwerfen

Wenn du Änderungen an einer Datei rückgängig machen möchtest:

In VS Code:
1. Rechtsklick auf die Datei im Source-Control-Tab.
2. Wähle "Discard Changes".

Über die Kommandozeile:

```bash
git checkout -- dateiname
```

### Zurück zu einem früheren Commit

Wenn du zu einem früheren Zustand deines Projekts zurückkehren möchtest:

In VS Code:
1. Öffne die Commit-Historie im Source-Control-Tab.
2. Rechtsklick auf den gewünschten Commit.
3. Wähle "Checkout".

Über die Kommandozeile:

```bash
git checkout commit-hash
```

## GitHub als Portfolio

GitHub ist mehr als nur ein Ort, um deinen Code zu speichern. Es kann auch als Portfolio dienen, um deine Fähigkeiten potenziellen Arbeitgebern zu präsentieren.

### README.md optimieren

Die README.md-Datei ist das Herzstück deines Projekts auf GitHub. Sie sollte enthalten:

1. **Projekttitel und kurze Beschreibung**
2. **Motivation**: Warum hast du dieses Projekt erstellt?
3. **Technologien**: Welche Technologien und Bibliotheken hast du verwendet?
4. **Installation**: Wie kann jemand dein Projekt lokal ausführen?
5. **Projektergebnisse**: Was hast du herausgefunden?
6. **Schlussfolgerungen**: Was sind deine Erkenntnisse?
7. **Zukünftige Arbeiten**: Was könntest du in Zukunft verbessern?

### GitHub-Profil personalisieren

GitHub ermöglicht es dir, ein spezielles Repository mit deinem Benutzernamen zu erstellen (z.B. `dein-username/dein-username`), dessen README.md auf deinem Profil angezeigt wird. Dies ist ein großartiger Ort, um dich, deine Fähigkeiten und deine besten Projekte vorzustellen.

### GitHub Pages

Mit GitHub Pages kannst du statische Websites direkt aus deinem Repository erstellen. Das ist besonders nützlich für Data-Science-Projekte, bei denen du Visualisierungen oder interaktive Dashboards teilen möchtest.

---

Du hast nun die Grundlagen von Git und GitHub kennengelernt. Es gibt noch viele weitere Funktionen und Möglichkeiten, die du erkunden kannst, aber das hier Beschriebene sollte ausreichen, um dein Portfolio-Projekt erfolgreich zu verwalten. Falls du tiefer in Git einsteigen möchtest, empfehle ich dir die offizielle [Git-Dokumentation](https://git-scm.com/doc) oder das kostenlose Buch [Pro Git](https://git-scm.com/book).

Ich wünsche dir viel Erfolg mit deinem Portfolio-Projekt und freue mich darauf, es auf GitHub zu sehen!