# METHOD – Progetto Pilota: Rifiuti comunali (ISPRA)

## 🎯 Domanda civica

Ci sono comuni che migliorano la raccolta differenziata (%) ma aumentano i rifiuti totali?

Il progetto è **descrittivo**: osserva pattern nei dati senza inferenze causali o giudizi normativi.

---

# 📦 Architettura dati del progetto

Pipeline logica:

RAW → CLEAN → MART → DASHBOARD

- RAW: dati originali immutabili
- CLEAN: dati puliti e standardizzati
- MART: dataset pronti per analisi/KPI
- DASHBOARD: sola visualizzazione pubblica

Il Metodo documenta **tutte le trasformazioni fino al MART**.
Le dashboard non introducono logiche dati.

---

# 1️⃣ Fonte → RAW

### Notebook: 01_source_raw.ipynb

Fonte:
ISPRA – Catasto Rifiuti Comunali  
https://www.catasto-rifiuti.isprambiente.it/

Operazioni:
- download CSV originali per anno (2019–2023)
- salvataggio immutabile su Drive
- nessuna trasformazione
- tracciabilità tramite metadata.json

Principio:
RAW è intoccabile e replica esattamente la fonte ufficiale.

---

# 2️⃣ RAW → CLEAN

### Notebook: 02_raw_clean.ipynb

Obiettivo:
Costruire un dataset comunale multi-anno pulito e coerente.

Trasformazioni effettuate:

- identificazione header reale ISPRA
- rimozione righe spurie / tab
- standardizzazione nomi colonne (snake_case)
- parsing numeri formato italiano (migliaia ".", decimali ",", %, "-")
- conversione tipi numerici
- normalizzazione codice ISTAT
- aggiunta campo `anno`
- concatenazione multi-anno (append)
- esportazione parquet
- generazione profili e metadati (_meta)

Output:

---

## 🔁 Riproducibilità tecnica

L’intera pipeline è pubblica e completamente replicabile tramite i notebook del repository.

### Fonte → RAW
Download dei CSV originali dal portale ISPRA  
[notebooks/01_source_raw.ipynb](notebooks/01_source_raw.ipynb)

### RAW → CLEAN
Pulizia, normalizzazione colonne, parsing numerico e consolidamento multi-anno  
[notebooks/02_raw_clean.ipynb](notebooks/02_raw_clean.ipynb)

### CLEAN → MART
Costruzione delle metriche analitiche e dei dataset pronti per dashboard  
[notebooks/03_clean_mart.ipynb](notebooks/03_clean_mart.ipynb)

Eseguendo i notebook nell’ordine indicato è possibile rigenerare completamente i dataset CLEAN e MART a partire dai dati ufficiali ISPRA.
