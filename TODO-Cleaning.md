# 🧹 Datenbereinigung & Vereinheitlichung – To-Do Liste

Diese To-Do-Liste beschreibt alle notwendigen Schritte, um die Survey-CSV-Datei zu bereinigen, zu vereinheitlichen und für spätere Analysen oder Visualisierungen nutzbar zu machen.

---

## 1. Fehlende Werte standardisieren

### Kategoriale Spalten
- `NaN` → **"Keine Angabe"**
- Datentyp `object` beibehalten

### Numerische Spalten
- `NaN` **nicht ersetzen**
- Datentyp `int`/`float` belassen  
  → wichtig für statistische Auswertungen (Durchschnitt, Median, Histogramme)

---

## 2. Kategorische Text-Spalten bereinigen

### Ziel
Eine einheitliche und konsistente Darstellung, um spätere Gruppierungen und Analysen zu erleichtern.

### Maßnahmen
- Whitespace entfernen (Trimmen)
- Einheitliche Groß-/Kleinschreibung (z. B. `title()` oder `lower()`)
- Zusammenführen identischer kategorischer Werte mit unterschiedlicher Schreibweise  
  *Beispiel: „Self taught“ und „self-taught“*
- Optional: Seltene Kategorien in **"Other"** gruppieren

### Beispiele betroffener Spalten
- `MainBranch`
- `EdLevel`
- `Employment`
- `Country`
- `OrgSize`
- `Industry`
- `AISelect`
- `AIPrimaryUse`

---

## 3. Mehrfachauswahl-Spalten vereinheitlichen (`;`-getrennte Werte)

### Typische Probleme
- Uneinheitliche Formatierungen
- Semikolon-separierte Werte
- NaN-Werte
- Inkonsistente Reihenfolgen

### Maßnahmen
- Aufsplitten in Listen  
  `"Python; JavaScript"` → `["Python", "JavaScript"]`
- Werte trimmen
- Duplikate in Listen entfernen
- Optionale alphabetische Sortierung der Werte
- NaN → **leere Liste** oder **"Keine Angabe"**

### Beispiele
- `DevType`
- `LanguageHaveWorkedWith`
- `LanguageWantToWorkWith`
- `DatabaseHaveWorkedWith`
- `ToolsTechHaveWorkedWith`
- `PlatformHaveWorkedWith`

---

## 4. Likert-Skalen (1–5 oder 1–7) vereinheitlichen

### Maßnahmen
- Typ in `int` konvertieren (falls möglich)
- NaN-Werte unverändert lassen
- Optional: Mapping auf semantische Labels  
  (z. B. *1 = Strongly disagree*, *5 = Strongly agree*)

### Beispiele
- `AIAssistImprove`
- `AIAssistLikelihood`
- `AIAgentChallenges...`
- `AIAssistImpact...`

---

---

## 7. Freitextfelder minimal bereinigen

### Maßnahmen
- Trim
- Entfernen von Sonderzeichen oder HTML-Elementen
- NaN → **"Keine Angabe"**

### Beispiele
- `AISentiment`
- `AIHarm`
- `AIFreeText...`

---

## 8. Encoding und Sonderzeichen vereinheitlichen

### Maßnahmen
- Unicode-Normalisierung (NFC)
- Einheitliche Apostrophe (`'` statt `’`)
- Unerwünschte typografische Zeichen entfernen

---

# ✔ Ergebnis

Nach Umsetzung dieser Bereinigungsschritte ist der Datensatz:

- **konsistent**,  
- **auswertbar**,  
- **sauber strukturiert**,  
- **maschinenlesbar**,  
- optimal vorbereitet für:  
  - statistische Analysen  
  - Visualisierungen  
  - Machine Learning  
  - Dashboarding  
  - Langzeit-Auswertungen
