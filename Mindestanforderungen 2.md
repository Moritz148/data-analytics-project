# Mindestanforderungen 2
## 1. Visualisierungen erstellen

Erstellen Sie jeweils **eine Visualisierung** zu jedem der folgenden Charttypen.  
Beschreiben Sie textuell, was Sie in dem Chart sehen, und geben Sie ggf. eine **Interpretation** an.

### 🔹 Line-Chart
- **Themen:** Einkommen, Satisfaction
- **Bearbeiter:** Moritz / Jonas
### 🔹 Bar-Chart
- **Themen:** X, Y
- **Bearbeiter:** Moritz / Jonas

### 🔹 Histogramm
- **Themen:**
  - Altersverteilung
  - Programmiersprachenverteilung (Anzahl je Programmiersprache)
- ### TODO Jonas
  - MainBranch
  - Age
  - EdLevel
  - Employment
  - Country
  - WorkExp
  - LearnCodeChoose
  - LearnCode
  - LearnCodeAI
  - AILearnHow
  - YearsCode
  - DevType
  - RemoteWork
  - OrgSize  
- ### TODO Moritz
  - Industry
  - AIThreat
  - NewRole *(ggf. numerisch umwandeln)*
  - ToolCountWork
  - ToolCountPersonal
  - LanguageChoice
  - LanguageHaveWorkedWith *(splitten nach „;“)*
  - LanguageWantToWorkWith *(splitten nach „;“)*
  - DevEnsChoice *(splitten)*
  - DevEnsHaveWorkedWith *(splitten)*  
  - DevEnsWantToWorkWith *(splitten)*
  - OpSysPersonalUse *(splitten)*
  - OpSysProfessionalUse *(splitten)*
  - JobSatisfaction  
### 🔹 Box-Plot
- **Themen:**
  - Job Satisfaction
  - Alter
  - Years of Experience (Code)
  - **Bearbeiter:** Denny

### 🔹 Scatter-Plot
- **Themen:** Alter vs. Years of Experience (Code)
- **Bearbeiter:** Denny
---

## 2. Sortierung des Datensatzes

Sortieren Sie den Datensatz **dauerhaft oder für eine bestimmte Analyse** und begründen Sie, warum diese Sortierung sinnvoll ist.

### Beispiel:
- **Spalte:** JobSat (Job Satisfaction)
  - Zufriedenheit
  - Unzufriedenheit
- **Bearbeiter:** Denny
---

## 3. Statistische Zusammenfassung

Erstellen Sie eine **statistische Zusammenfassung** von mindestens **einer Spalte**.
- **Bearbeiter:** Denny
---

## 4. Gruppierung durchführen

Führen Sie mindestens **eine Gruppierung** durch und erklären Sie, warum diese sinnvoll war.

### Beispiel: JobSat
- **Gruppen:**
  - 0–3 → unzufrieden  
  - 4–6 → OK  
  - 7–10 → zufrieden
- **Weitere Spalten:**
  - Count
  - Altersklasse (count)
  - Gehaltsdurchschnitt (zuerst umrechnen)
- **Bearbeiter:** Denny
---

## 5. Erkenntnisse dokumentieren

Dokumentieren Sie jeweils **mindestens eine Erkenntnis** bezüglich:
- der **Datenstruktur**
- der **Daten**
- der **geschäftlichen Domäne**

- **Bearbeiter:** Denny

---
# Sonstige Erkenntnisse:

## Datenbereinigung

- Einkommen schrittmäßig / Gehaltsklassen (z. B. 10.000 €-Steps)
- Programmiersprachen unterteilen (Semikolon-getrennt)
- Gewünschte Technologien (Semikolon-getrennt)
- **LearnToCode**-Spalte (Semikolon-getrennt → Lernwilligkeit)
- **CareerChange**-Spalte („NewRole“)
- Prüfen: Spalte **Employed**
- Währungen / Gehälter umrechnen  
  - Wechselkurs 2025 (Stichtag festlegen)  
  - → *Feature Engineering*  
  - Tool: [PyCurrency-Converter](https://pypi.org/project/PyCurrency-Converter/)
- Einzelne relevante Spalten bereinigen

---

## Weitere Analysen

- Manager- und Teamkultur (JobSat → Zufriedenheit / Manager Ranking)
- Einstellung zu KI
- Alle Spalten mit **„SO“** droppen (Überprüfung, ob Stack Overflow-bezogen)
- Beginn der Dokumentation, um **Nachvollziehbarkeit** sicherzustellen
- Mapping von einzelnen Spaltenwerten → Einsehbar in csv survey_results_schema
---

## 9. Hinweise zur Zusammenarbeit

- Dokumentation von Schritten, Entscheidungen und Begründungen
- Gemeinsames Verständnis der Daten schaffen
- Einheitliche Strukturierung für Visualisierungen, Bereinigung und Analyse