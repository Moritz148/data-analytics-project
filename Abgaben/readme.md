# Notebook-Übersicht / Ablauf

Dieses Projekt basiert auf den Daten der Stack Overflow Developer Survey 2025. Die Notebooks bauen schrittweise aufeinander auf: erst Exploration & Vorbereitung, dann Cleanup, danach Clustering/Klassifikation – einmal auf dem Cleanup-Datensatz und später auf dem OHE-Datensatz.

## Notebooks
**Falls die Notebooks ausgeführt werden, muss man auf die folgende Reihenfolge achten.**
### 1) Notebook 1 — Survey Basis / Initial Exploration
- Lädt den Rohdatensatz (`survey_results_public.csv`)
- Erster Überblick: relevante Spalten, Missing Values, erste einfache Auswertungen/Plots

### 2) Notebook 2 — Erste Anpassungen / Feature-Aufbereitung
- Bereinigung erster Felder (z. B. Harmonisierung von Kategorien, Umbenennungen)
- Ableitung erster Hilfsspalten/Features für spätere Analysen

### 3) Notebook 3 — Vertiefung / weitere Transformationen
- Feature-Engineering-Schritte
- Zusätzliche Analysen, Selektion/Filterung relevanter Attribute

### 4) Notebook 4 — Analyse / Vorbereitung finaler Struktur
- Letzte Anpassungen auf Basis von Notebook 2 (und ggf. 3)
- Ergebnis ist eine konsistente Datenbasis für den nächsten Cleanup-Schritt

### Cleanup-Notebook — Finales Cleaning & Export
- Entfernt/vereinheitlicht problematische Spalten, behandelt Missing Values/Datentypen
- Erzeugt den **Cleanup-Datensatz** als Basis für kommende Modelle

### Clustering (Cleanup) — Unsupervised Profile / Gruppenbildung
- Clustering auf dem Cleanup-Datensatz (`5_Clustering_ABGABE.ipynb`)
- Clusteranzahl über Elbow, Ergebnis: grobe Entwicklerprofile

### Klassifikation (SVC) — Cleanup-Datensatz
- SVC-Klassifikation auf dem Cleanup-Datensatz
- Zwei Zielvariablen:
  - **Employment** (`6_Klassifikation_SVC_employment.ipynb`)
  - **JobSat** (`6_Klassifikation_SVC_JobSat.ipynb`)

### OneHotEncoding-Notebook — OHE-Datensatz erzeugen
- One-Hot-Encoding (OHE) geeigneter kategorialer Spalten
- Export des **OHE-Datensatzes**, der in den weiteren Modellen verwendet wird

### Weitere Clustering-/Klassifikationsnotebooks (auf OHE)
- Clustering mit dem OHE-Datensatz (`5_Clustering_one-hot-encoded.ipynb`)
- Klassifikation mit dem OHE-Datensatz (`6_Klassifikation_SVC_employment_OHE.ipynb`)
- 
### 7) PCA / Dimensionsreduktion
- PCA auf rein numerischen Features (Cleanup-Datensatz)
- Ziel: Dimensionalität reduzieren, dabei möglichst viel Varianz/Information erhalten
- Pipeline mit Standardisierung + PCA (`n_components=0.9`)
- Notebook: `7_PCA_DimReduktion.ipynb`

### 8) Lineare Regression — Einkommen vorhersagen (`ConvertedCompTotal`)
- Regression auf dem **OHE-Datensatz** zur Vorhersage von `ConvertedCompTotal`
- Inklusive Train/Test-Split, Baselines, Evaluation (RMSE, R², MAE) & Lernkurve
- Enthält GridSearch

**8a) Naives Baseline-Modell (wenige Features)**
- Nutzt nur `WorkExp` und `Country_*` (OHE) als sehr einfache Referenz
- Notebook: `8_LineareRegression_extended_gridsearch_naive.ipynb`

**8b) Erweitertes Regressionsmodell (mehr Features)**
- Nutzt mehrere numerische Features + Dummies (OHE), inkl. Lernkurve & Koeffizientenanalyse
- Notebook: `8_LineareRegression_extended_gridsearch.ipynb`


## Abgabe-relevant

Als Abgabe zählen:
- Notebooks 1–4
- `5_Clustering_ABGABE.ipynb`
- `6_Klassifikation_XGBoost_employment_OHE_ABGABE.ipynb`
- `7_PCA_DimReduktion.ipynb`
- `8_LineareRegression_extended_gridsearch.ipynb`
- `8_LineareRegression_extended_gridsearch_naive.ipynb`

Alle übrigen Notebooks sind zusätzliche Lösungsansätze/Experimente.

## Python-Abhängigkeiten (`requirements.txt`)

Damit die Notebooks reproduzierbar auf einem anderen Rechner laufen, sind die verwendeten Python-Pakete in einer `requirements.txt` festgehalten.

### Installation (empfohlen in einem venv)
```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate

pip install -r requirements.txt