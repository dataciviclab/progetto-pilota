# 🧠 /data/mart

# Dataset MART – Raccolta differenziata e rifiuti urbani (ISPRA)

Questa cartella contiene i **dataset MART (Modeling / Analytics Ready Table)** 
derivati dal Catasto Rifiuti ISPRA a livello comunale.

I dataset sono progettati per:
- rispondere a una **domanda civica specifica**
- essere utilizzati direttamente in **dashboard Power BI**
- supportare analisi comparative e temporali sui comuni italiani

---

## Domanda civica

**Ci sono comuni che migliorano la raccolta differenziata (%) ma aumentano i rifiuti totali?**

---

## Dataset disponibili

### 1️⃣ MART – Confronto comunale 2020–2023

**Nome files**
- mart_comuni_delta_2020_2023_dashboard.csv
- mart_comuni_delta_2020_2023_dashboard.paequet


**Granularità**
- 1 riga = 1 comune (codice ISTAT a 6 cifre)

**Descrizione**
Dataset “wide” che confronta due anni (2020 e 2023) per ciascun comune,
calcolando variazioni di raccolta differenziata e rifiuti urbani.

È il dataset principale utilizzato per rispondere alla domanda civica.
Contiene già le variazioni e la classificazione analitica,
così da garantire coerenza tra dataset, dashboard e documentazione.

**Schema colonne principali**
- `istat_comune_6` (string)
- `comune` (string)
- `provincia` (string)
- `regione` (string)
- `percentuale_rd_2020` (float)
- `percentuale_rd_2023` (float)
- `delta_rd_pp` (float, punti percentuali)
- `totale_ru_t_2020` (float, tonnellate)
- `totale_ru_t_2023` (float, tonnellate)
- `delta_ru_totali_t` (float)
- `ru_pro_capite_kg_2020` (float)
- `ru_pro_capite_kg_2023` (float)
- `delta_ru_pro_capite` (float)
- `quadrante` (string)
- `rd_su_rifiuti_su` (boolean)
- `virtuoso_strutturale` (boolean)

**KPI principali**
- Numero comuni analizzati
- % comuni con RD in aumento e rifiuti in aumento
- Numero di comuni “virtuosi strutturali”
- Distribuzione dei comuni per classe di andamento

**Uso consigliato**
- Scatter plot (Δ RD% vs Δ rifiuti)
- KPI di sintesi
- Classifiche dei comuni migliori e peggiori

---

### 2️⃣ Serie storica comunale 2019–2023

**Nome files**
- serie_comuni_rd_ru_2019_2023.csv
- serie_comuni_rd_ru_2019_2023.paequet

**Granularità**
- 1 riga = 1 comune × 1 anno

**Descrizione**
Dataset in formato “long” che contiene la serie storica annuale
di raccolta differenziata e rifiuti urbani per ciascun comune.

È pensato per analisi di approfondimento temporale
e per una seconda pagina di dashboard.

**Schema colonne principali**
- `istat_comune_6` (string)
- `comune` (string)
- `provincia` (string)
- `regione` (string)
- `anno` (int)
- `popolazione` (float)
- `totale_ru_t` (float)
- `ru_pro_capite_kg` (float)
- `percentuale_rd` (float)

**KPI e analisi possibili**
- Trend temporali RD%
- Trend rifiuti pro capite
- Analisi di continuità o inversione dei trend
- Drill-down da dashboard principale

---

## Origine dei dati

- **Fonte**: ISPRA – Catasto Rifiuti
- **Livello**: Produzione e raccolta differenziata su scala comunale
- **Periodo coperto**: 2019–2023

I dataset MART derivano dal dataset **clean** prodotto nel notebook di pulizia
e sono accompagnati da controlli qualità e metadati.

---

## Note metodologiche

- Il confronto 2020–2023 è una scelta analitica per evidenziare
  variazioni strutturali nel medio periodo.
- La serie storica completa è fornita per approfondimenti e analisi di trend.
- I dataset non includono dati raw, ma solo output pronti per analisi e visualizzazione.
- ### Calcolo delle variazioni e classificazione

Le variazioni (`delta_rd_pp`, `delta_ru_totali_t`, `delta_ru_pro_capite`)
sono calcolate nel notebook MART come differenza tra 2023 e 2020:

- Δ RD (pp) = percentuale_rd_2023 − percentuale_rd_2020
- Δ RU totali (t) = totale_ru_t_2023 − totale_ru_t_2020
- Δ RU pro capite (kg) = ru_pro_capite_kg_2023 − ru_pro_capite_kg_2020

La classificazione dei comuni in quadranti (es. migliorano RD ma aumentano RU)
è generata direttamente nel dataset MART e non nel layer di visualizzazione.

Power BI utilizza tali colonne senza ricalcolare la logica analitica.

---

## Link ai file

I file MART sono disponibili nella [cartella Drive del progetto](https://drive.google.com/drive/folders/1Y1CCmyshifHTIQ1TT0jpNl-9C_HzLDgP?usp=drive_link)

e vengono rigenerati localmente tramite il notebook [`03_clean_mart.ipynb`](https://github.com/dataciviclab/progetto-pilota/blob/main/notebooks/03_clean_mart.ipynb)
