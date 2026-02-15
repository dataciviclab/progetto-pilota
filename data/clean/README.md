# 2️⃣ RAW → CLEAN

### Notebook: [02_raw_clean.ipynb](https://github.com/dataciviclab/progetto-pilota/blob/main/notebooks/02_raw_clean.ipynb)

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

## Output:
- [Dati](https://drive.google.com/drive/folders/1vmI6YXFG_ayTkgt8oQ22nUZx4q3OKYQM?usp=drive_link) 
- [Meta](https://drive.google.com/drive/folders/1U39QLGvwyHpOTgANNfI7VaA2hy-8vWLv?usp=drive_link)
