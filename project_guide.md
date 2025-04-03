<!-- 
TODO:
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