# 📓 /notebooks – Pipeline e analisi

Questa cartella contiene notebook (Colab / Jupyter) per:
- ingestione dati (raw)
- pulizia/normalizzazione (clean)
- aggregazioni e KPI (mart)
- analisi esplorative (quando servono)

---

## ✅ Regole minime

- notebook numerati: `01_...`, `02_...`, `03_...`
- eseguibili dall’inizio alla fine (no “celle magiche”)
- commenti brevi: **cosa** fai e **perché**
- niente path locali: usare riferimenti chiari al Drive / cartelle di progetto

---

## 🔁 Collegamento con `/data`

Ogni notebook dovrebbe aggiornare (o citare) i README di:
- `/data/raw`
- `/data/clean`
- `/data/mart`

Così chi arriva dopo capisce:
- da dove arrivano i dati
- cosa è stato fatto
- dove trovare i file su Drive

---
