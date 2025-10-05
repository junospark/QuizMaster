
# 📘 Interaktives KI-Quiz (KI_Quiz_dark_final.html)

## 🇩🇪 **Beschreibung**
Dieses Projekt ist ein vollständig im Browser laufendes interaktives Quiz-System mit Dashboard, Statistik, Editor und Import-/Export-Funktionen.  
Es basiert auf HTML, JavaScript und `localStorage`, benötigt also **keinen Server**.

---

## 🔧 **Funktionen**

### Dashboard
- Übersicht über **Gesamtfragen**, **gelernte Fragen**, **heute beantwortete Fragen**, **verbleibende Tage**  
- Fortschritts- und Planungsdiagramme mit **Chart.js**  
- Lernfortschritt pro Thema  

### Fragen-Datenbank
- Fragen erstellen, bearbeiten, löschen  
- Rich-Text-Editor mit Formatierungen, Farben, Tabellen  
- Suchen und Filtern von Fragen  

### Quiz-Modus
- Auswahl nach Thema, Schwierigkeit oder Suchbegriff  
- Fortschrittsanzeige pro Frage und gesamt  
- Automatische Speicherung der Lernstände  

### Fortschrittsanzeige
Unten rechts wird dauerhaft angezeigt:  
**Dateiname** (z. B. `KI_Quiz_dark_final.html`) und **zuletzt geändert am** (z. B. `04.10.2025`).

---

## 📥 **Import und Export**

### 🧾 Excel-Import (`.xlsx`)
Die Excel-Datei muss folgende Spalten enthalten:

| Spaltenname | Beschreibung | Beispiel |
|--------------|---------------|-----------|
| **Thema** | Kategorie oder Themengebiet der Frage | KI-Grundlagen |
| **Frage** | Der eigentliche Fragetext | Was bedeutet KI? |
| **Antworten** | Alle Antwortmöglichkeiten in **einer Zelle**, getrennt durch **Zeilenumbrüche** (ALT+ENTER in Excel) | Künstliche Intelligenz<br>Kinetische Integration<br>Kreative Ideenfindung |
| **Lösung** | Der oder die **korrekten Antworten als Volltext**, ebenfalls mit **Zeilenumbrüchen**, exakt wie in der Spalte „Antworten“ | Künstliche Intelligenz |
| **Schwierigkeit** *(optional)* | frei definierbar (z. B. „leicht“, „mittel“, „schwer“) | mittel |
| **Kommentar** *(optional)* | Zusatzinfo oder Erklärung zur Frage | KI bezeichnet Systeme mit lernfähigem Verhalten |

**Hinweise:**
- Die **erste Zeile** enthält die Spaltenüberschriften.  
- Zeilenumbrüche werden im Import automatisch erkannt (`\n` oder ALT+ENTER).  
- Leere Zeilen werden ignoriert.  
- Bei mehreren richtigen Antworten müssen alle richtigen Antworten vollständig und in separaten Zeilen untereinander in der **„Lösung“-Zelle** stehen.  
- Der Importer erkennt automatisch passende Spaltennamen (auch mit leicht abweichender Schreibweise).

---

### 💾 JSON-Import / -Export

Beim Export erzeugt das System eine `.json`-Datei mit folgendem Aufbau:

```json
[
  {
    "id": "abc123xyz",
    "nr": 1,
    "topic": "KI-Grundlagen",
    "text": "Was bedeutet KI?",
    "answers": [
      "Künstliche Intelligenz",
      "Kinetische Integration",
      "Kreative Ideenfindung"
    ],
    "solution": [
      "Künstliche Intelligenz"
    ],
    "comment": "KI steht für Künstliche Intelligenz.",
    "difficulty": "leicht",
    "progress": 2,
    "createdAt": "2025-10-05T09:00:00.000Z",
    "updatedAt": "2025-10-05T09:30:00.000Z",
    "history": []
  }
]
```

**Wichtig:**
- `answers` enthält **Textantworten als Array**.  
- `solution` enthält **die vollständigen Antworttexte**, **nicht die Indexnummern**.  
- Beim Import wird jede Frage anhand ihres Inhalts verglichen, vorhandene IDs werden überschrieben.  

---

## 💾 **Datenhaltung (Local Storage)**

Alle Daten werden lokal im Browser gespeichert:

| Bereich | Schlüssel | Inhalt |
|----------|------------|--------|
| Fragen-Datenbank | `quizdb_v2` | Alle Fragen und Lernstände |
| Einstellungen | `quiz_settings` | Wiederholungsziel, Start-/Enddatum |
| Datensatz-Info | `quiz_datasetInfo` | Dateiname, Version, Änderungsdatum |

Die Daten bleiben **auch nach einem Neustart des Browsers** erhalten, solange der lokale Speicher nicht gelöscht wird.

---

## 🧹 **Cache-Verhalten**

Wenn der Browser-Cache oder `localStorage` gelöscht wird:
- Alle Fragen, Fortschritte und Einstellungen gehen verloren.  
- Das Quiz startet mit einer leeren Datenbank.  
- Importiere anschließend deine `.xlsx`- oder `.json`-Datei erneut.

---

## 🌐 **Verwendung auf einer Website**
- Die Datei `KI_Quiz_dark_final.html` kann direkt auf einem Webserver oder über **GitHub Pages** bereitgestellt werden.  
- Kein Backend erforderlich — alle Funktionen laufen vollständig im Browser.  
- Für Offline-Verwendung genügt ein Doppelklick auf die Datei.

---

## ⚙️ **Technische Hinweise**
- Unterstützte Browser: Chrome, Edge, Firefox, Safari (Desktop & Mobil)  
- Abhängigkeiten über CDN:
  - `xlsx.js` – Excel-Import  
  - `chart.js` + `chartjs-plugin-zoom` – Diagramme  
  - `DOMPurify` – sichere HTML-Kommentare

---

## 🇬🇧 **English Summary**

### Excel File Format
| Column | Description | Example |
|---------|--------------|----------|
| **Topic** | Question category | AI Basics |
| **Question** | Question text | What does AI stand for? |
| **Answers** | All possible answers **inside one cell**, separated by **line breaks** (ALT+ENTER) | Artificial Intelligence<br>Kinetic Integration<br>Creative Ideation |
| **Solution** | The **full correct answers as text**, separated by **line breaks**, exactly as in “Answers” | Artificial Intelligence |
| **Difficulty** | optional (easy, medium, hard) | medium |
| **Comment** | optional explanation | AI means Artificial Intelligence |

### JSON File Format
```json
{
  "topic": "AI Basics",
  "text": "What does AI stand for?",
  "answers": ["Artificial Intelligence", "Kinetic Integration", "Creative Ideation"],
  "solution": ["Artificial Intelligence"],
  "difficulty": "easy",
  "comment": "AI means Artificial Intelligence"
}
```

**Notes:**
- `answers` and `solution` contain full text, not numeric indexes.  
- Line breaks (`\n`) in Excel cells are interpreted automatically.  
- Empty rows are ignored.
