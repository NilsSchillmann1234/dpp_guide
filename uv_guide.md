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
winget install --id=astral-sh.uv -e
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

Wir können in diesem Leitfaden nur die Grundlagen von UV behandeln. Falls du dich dafür interessierst was mit UV noch alles möglich ist lege ich dir die offizielle [Dokumentation](https://docs.astral.sh/uv/getting-started/) der Entwickler ans Herz.


<!---
TODO: uv --help
-->

## Projekt erstellen `uv init`

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
- `--python`: Legt die Python-Version fest, z.B. `uv init --python=3.12`
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
In dieser Datei werden wichtige Information zu unserem Projekt abgelegt. Programme wie UV nutzen diese Datei um Einstellungen für das Projekt zu verwalten. Wenn du dich dafür interessierst wie diese Datei Aufgebaut ist und funktioniert kannst du gerne einen Blick in den Offiziellen [Python Packaging Guide](https://packaging.python.org/en/latest/guides/writing-pyproject-toml/) werfen. Für den Anfang musst du aber nur wissen, das UV hier einige Metadaten für unser Projekt angelegt hat und unter dem Punkt `dependencies` die Namen der benötigten Packete für unser Projekt hinterlegt.

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

## Pakete installieren `uv add`

Für ein Data Science Projekt brauchst du typischerweise einige Bibliotheken. Um mit Jupyter Notebooks zu arbeiten kannst du das Paket `jupyter` installieren. Dieses bietet dir den Jupyter Kernel, der für die Ausführung der Zellen im Notebook zuständig ist, und den Jupyter Server, der eine einfache Webbasierte Benutzeroberfläche für einen Internetbrowser bietet. Du kennst den Jupyter Server wahrscheinlich schon in Form des DataLab von StackFuel. Wenn du deine Notebooks mit VSCode bearbeiten möchtest reicht es aus, wenn du nur das Packet `ipykernel` installierst, da VSCode selbst die Benutzeroberfläche darstellt.

Darüber hinaus können wir einige Bibliotheken gebrauchen die du bereits aus unseren Trainings kennst. Zu nennen wären hier `pandas`, `matplotlib`, `seaborn`, `scikit-learn` etc..

Um ein Packet mit uv zu installieren kannst du den Befehl `uv add` gefolgt von einem oder mehrer Packetnamen verwenden.

```bash
uv add ipykernel pandas matplotlib
```

Nach diesem Befehl hat sich deine pyproject.toml verändert:
```toml
[project]
name = "mein-data-projekt"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
requires-python = ">=3.12"
dependencies = [
    "ipykernel>=6.29.5",
    "matplotlib>=3.10.1",
    "pandas>=2.2.3",
]

```

**Hinweis:** Die oben stehenden Versionsnummern können in deinem Fall vom Beispiel abweichen. Das liegt daran, dass uv stehts versucht die aktuellsten Versionen der Packete zu installieren und diese regelmäßig aktualisiert und weiter entwickelt werden.

In der `pyproject.toml` finden wir die Packete welche wir explizit durch `uv add` als Abhängigkeit (dependency) für unser Projekt definiert haben. Damit ist klar, dass unser Projekt auf diesen Bibliotheken aufbaut und jeder, der unser Projekt selbst ausführen möchte, diese Packete installiert haben muss. Allerdings haben diese Packete selbst ebenfalls abhängigkeiten von anderen Packeten die wir nicht explizit angegeben haben. So sind die Packete `pandas` und `matplotlib` beispielsweise von `numpy` abhängig. UV installiert diese zusätzlichen abhängigkeiten automatisch für uns mit und dokumentiert alle installierten Packete in der `uv.lock` Datei. UV hat also `numpy` ebenfalls installiert und wir können dieses Packet in unseren Notebooks verwenden. Allerdings sollten wir, falls wir `numpy` explizit in unserem Quellcode verwenden, dieses auch in unserer `pyproject.toml` Datei auflisten bzw. mit `uv add` hinzufügen und uns nicht darauf verlassen, dass es durch `pandas` oder `matplotlib` installiert wird.

UV hat spätestens jetzt einen Ordner `.venv` in unserem Projekt angelegt und dort die entsprechenden Packete installiert. Falls du diesen Ordner nicht siehst musst du in den Einstellungen deines Dateiexplorers "versteckte" oder "ausgeblendete" Elemente anzeigen lassen. Das ist nun unser Virtuelles Environment das speziell für unser Projekt angelegt wurde.

Du kannst nun in VSCode dein erstes Notebook z.B. `test.ipynb` anlegen. Nachdem du diese Datei geöffnet hast solltest du als erstes den Kernel oben rechts in der Ecke definieren. Hier wähle einfach das `.venv` aus, welches uv gerade für uns angelget hat. Mehr dazu in unserem [VSCode guide](vscode_guide.md).


## Pakete entfernen `uv remove`

Wenn du versehentlich ein Packet installiert hast welches du nicht benötigst, kannst du dieses mit dem Befehl `uv remove` wieder deinstallieren. UV wird es dann aus der `pyproject.toml` Datei entfernen und das Packet inklusiver aller Abhängigkeiten, die nicht von anderen Packeten verwendet werden, löschen.

```bash
uv remove matplotlib
```

## Virtuelle Umgebung synchronisieren `uv sync`

Wir haben gesehen, dass UV die Bibliotheken, die wir über `uv add` installieren, in der `pyproject.toml` sowie der `uv.lock` Datei einträgt. Aber was wenn wir uns das projekt frisch von GitHub geklont haben und nun das Environment komplett neu aufsetzten wollen? In diesem Fall sind die Bibliotheken bereits in der `project.toml` und `uv.lock` eingetragen allerdings noch nicht installiert. Für diesen Fall gibt es den Befehl `uv sync`. Mit diesem Befehl versucht UV die entsprechenden Dateien und das Environmen zu synchronisieren. Das bedeutet alles was in der `pyproject.toml` Datei steht, aber noch nicht im environment existiert, wird nachinstalliert.

Dieser Befehl ist immer dann wichtig, wenn das Environment von jemand anderem geändert wurde. Stell dir vor ein Kollege arbeitet gerade an einem neuen Feature und braucht dafür eine Bibliothek, welche noch nicht Teil des Environment ist. Er installiert dieses Packet bei sich durch `uv add` und UV aktualisiert seine Version der `pyproject.toml` Datei. Wenn er fertig ist pusht er seinen neuen Code zusammen mit der aktualisierten `pyproject.toml` auf GitHub. Wenn du dir nun das Projekt pullst wirst du ein Packet in deiner `pyproject.toml` haben, welches nicht Teil deines Environment ist, da das Environment selbst nicht Teil des GitRepositorys ist. In dieser Situation kannst du einfach `uv sync` im Terminal eingeben und UV kümmert sich darum das alles korrekt installiert wird.

**UV add:**
- Fügt neue Pakete hinzu und aktualisiert pyproject.toml
- Installiert die Pakete direkt

**UV sync:**
- Synchronisiert das venv mit pyproject.toml
- Nützlich wenn du das Projekt frisch geklont oder gepullt hast

Tipp: Führe `uv sync` aus, wenn deine Teammitglieder neue Pakete hinzugefügt haben und du die Änderungen übernehmen möchtest.

## Code ausführen `uv run`

Wir haben nun ein Environment und können dort Packete installieren und unseren Programmcode schreiben. Doch was wenn wir diesen Code nun ausführen wollen? Üblicherweise rufen wir im Terminal das Programm `python` bzw. `python3` unter Linux auf und übergeben dem Programm unser Script zur ausführung.
``` bash
python hello.py
```

Allerdings kriegen wir hier ein Problem. Unser Virtuelles Environment ist unserem Betriebssystem nicht bekannt. Es wird versuchen eine global installierte Python version auf dem System zu finden und diese auszuführen. Diese Version wird aber ebenfalls nicht mit den Bibliotheken aus unserem Environment vertraut sein.

Die konventionelle Lösung für das Problem ist es, das Virtuelle Environment zunächst zu "aktivieren". Im `.venv/Scripts` Ordner liegen mehrere Scripte, welche für unterschiedliche Terminal vorgesehen sind. Bei der ausführung des Richtigen Scripts wird nun dem Betriebssystem die Richtige Python Version samt aller installierten Bibliotheken bekannt gemacht, so dass, solange das environment aktiv ist, die richtige Python version mit `python hello.py` aufgerufen wird.

UV macht die ganze sache ein wenig einfacher. Da UV selbst ein Programm ist, dass unser environment kennt solange wir es im richtigen Pfad aufrufen, können wir den befehl `uv run` für die ausführung von Python Code verwenden.
```bash
uv run hello.py
```

UV kümmert sich dann darum, dass die Richtige Python Version unsere Environment für die ausführung verwendet wird.


---


Du hast nun die wichtigesten Befehle und Funktionen von UV kennen gelernt um dein Projekt aufzusetzten und `.py` Dateien sowie jupyter Notebooks auszuführen. UV bietet noch einige weitere Möglichkeiten die du dir gerne bei bedarf anschauen kannst. Dafür empfehlen wir die offizielle [Dokumentation](https://docs.astral.sh/uv/) der Entwickler.

Ich wünsche dir viel Spaß mit deinem Python Projekt.