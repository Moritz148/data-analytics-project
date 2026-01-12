# Notebook-Übersicht / Ablauf

Dieses Projekt basiert auf den Daten der [Stack Overflow Developer Survey 2025](https://survey.stackoverflow.co/). 
Die Notebooks sind so konzipiert, dass sie schrittweise aufeinander aufbauen. Die Vorgehensweise gliedert sich in die folgenden Schritte: Exploration und Vorbereitung, Transformation/Feature Engineering, Cleanup/Export sowie Clustering/Klassifikation/Regression.

## Daten & Zwischenstände

- **Grundlegender Datensatz**
  - `survey_results_public.csv`

- **Zwischenstände**
  - `output_woche1.csv`
  - `output_woche2.csv`
  - `output_woche4.csv`
  - `survey_results_cleaned_final.csv`
  - `One-Hot-Encoded-final.csv`

## Notebooks in ihrere Reihenfolge
**_Falls die Notebooks ausgeführt werden, muss man auf die folgende Reihenfolge achten._**
### 1) Notebook 1 — Survey Basis / Initiale Exploration
- `1_NumPy_Pandas.ipynb`
- Überblick, erste Analysen, NumPy-Arrays
- Export: `output_woche1.csv`

### 2) Notebook 2 — Datenexploration
- `2_Datenexploration.ipynb`
- Bereinigung erster Felder (z. B. Harmonisierung von Kategorien, Umbenennungen)
- Ableitung erster Hilfsspalten/Features für spätere Analysen
- Exploration & Visualisierungen
- Export: `output_woche2.csv`

### 3) Notebook 3 — Datentransformation
- `3_Datentransformation.ipynb`
- Transformationen & Auswertungen 
- Zusätzliche Analysen, Selektion/Filterung relevanter Attribute

### 4) Notebook 4 — Feature Engineering & Time Series
- `4_Feature Engineering_Time Series.ipynb`
- Umrechnung des Gehalts auf USD mit dem [CurrencyConverter](https://pypi.org/project/CurrencyConverter/)
- Ergebnis ist eine konsistente Datenbasis für den nächsten Cleanup-Schritt
- Export: `output_woche4.csv`

### Cleanup-Notebook — Finales Cleaning & Export
- `Cleanup.ipynb`
- Entfernt/vereinheitlicht problematische Spalten, behandelt Missing Values/Datentypen
- Erzeugt den Cleanup-Datensatz als Basis für kommende Modelle
- Export: `survey_results_cleaned_final.csv`

### 5) Clustering (Cleanup)
- `5_Clustering_ABGABE.ipynb`
- Numerik + TF-IDF, Elbow-Methode, 2D-Plot via TruncatedSVD

### OneHotEncoding-Notebook — One-Hot-Encodeden Datensatz erzeugen
- `One-Hot-Encoding_mitSkala.ipynb`
- One-Hot-Encoding (OHE) geeigneter kategorialer Spalten
- Export des OHE-Datensatzes, der in den weiteren Modellen verwendet wird
- Export: `One-Hot-Encoded-final.csv`

### 5b) Clustering (OHE)
- `5_Clustering_one-hot-encoded.ipynb`
- Clustering auf OHE + Numerik

### 6) Klassifikation (SVC / XGBoost)
- Cleanup:
  - `6_Klassifikation_SVC_employment.ipynb`
  - `6_Klassifikation_SVC_JobSat.ipynb`
  - `6_Klassifikation_XGBoost_JobSat_ABGABE.ipynb`
- OHE:
  - `6_Klassifikation_SVC_employment_OHE.ipynb`
  - `6_Klassifikation_XGBoost_employment_OHE.ipynb`

### 7) PCA / Dimensionsreduktion
- PCA auf rein numerischen Features (Cleanup-Datensatz)
- Ziel: Dimensionalität reduzieren, dabei möglichst viel Varianz/Information erhalten
- Pipeline mit Standardisierung + PCA (`n_components=0.9`)
- Notebook: `7_PCA_DimReduktion.ipynb`

### 8) Lineare Regression — Einkommen vorhersagen (`ConvertedCompTotal`)
- Regression auf dem **OHE-Datensatz** zur Vorhersage von `ConvertedCompTotal`
- Inklusive Train/Test-Split, Baselines, Evaluation (RMSE, R², MAE) & Lernkurve
- Enthält GridSearch

**8a) Erweitertes Regressionsmodell (mehr Features)**
- Nutzt mehrere numerische Features + Dummies (OHE), inkl. Lernkurve & Koeffizientenanalyse
- Notebook: `8_LineareRegression_extended_gridsearch.ipynb`
- 
**8b) Naives Baseline-Modell (wenige Features)**
- Nutzt nur `WorkExp` und `Country_*` (OHE) als sehr einfache Referenz
- Notebook: `8_LineareRegression_extended_gridsearch_naive.ipynb`

## Abgabe-relevant

Hier sind die abgaberelevanten Notebooks aufgelistet::
- `1_NumPy_Pandas.ipynb`
- `2_Datenexploration.ipynb`
- `3_Datentransformation.ipynb`
- `4_Feature Engineering_Time Series.ipynb`
- `5_Clustering_ABGABE.ipynb`
- `6_Klassifikation_XGBoost_JobSat_ABGABE.ipynb`
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