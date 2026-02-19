# Dashboard – Raccolta differenziata vs Rifiuti urbani (ISPRA 2020–2023)

---
## Output

**Tipo:** Dashboard interattiva (Power BI)  

**Link pubblico:** [Dashboard interattiva](https://app.powerbi.com/view?r=eyJrIjoiZmE5MTNlZmItN2NkZC00ZTkyLWEwZGItMzE3ZWJkNzI0ZjZjIiwidCI6IjgwNjZmMmRlLTgxZDctNGVjNC04Y2E5LTgzNzVjOTA4NjViNSJ9)

**Ultimo aggiornamento:** 17-02-2026

> **Nota:** qui non ci sono file dati.  
> Trovi invece **descrizione, screenshot e guida di lettura** della dashboard.

---

## Overview

![Overview](./screenshots/overview.png)

## Tooltip personalizzato

![Tooltip](./screenshots/tooltip.png)

## Trend temporale + Top migliori e peggiori

![Trend](./screenshots/trend+top5.png)

## Confronto Comuni

![Trend](./screenshots/tabella.png)

---

### KPI principali
- Numero di comuni analizzati
- Comuni con RU pro capite valido
- Comuni RD↑ & RU↑ (N e %)  
- Virtuosi strutturali (N e %)

---

## Risposta alla domanda civica

L’analisi 2020–2023 mostra che la maggior parte dei comuni italiani aumenta la percentuale di raccolta differenziata. Tuttavia, questo miglioramento non si traduce automaticamente in una riduzione dei rifiuti prodotti.

Solo il **24,6% circa dei comuni (1913)** si colloca nel quadrante virtuoso (RD↑, RU↓), mostrando un miglioramento reale e non solo “sulla carta”.

Una quota significativa di territori registra un aumento della raccolta differenziata accompagnato da un aumento dei rifiuti urbani pro capite, evidenziando un miglioramento solo apparente dell’indicatore.

La relazione tra RD e RU non è quindi automaticamente inversa.

La dashboard consente di esplorare nel dettaglio questi comportamenti per territorio.

---

## Come leggere la dashboard

La dashboard è composta da cinque sezioni principali e un tooltip riepilogativo.

### KPI sintetici (in alto)
Mostrano:
- Numero di comuni analizzati
- Comuni con RU pro capite valido
- Comuni RD↑ & RU↑ (numero e percentuale)
- Virtuosi strutturali (numero e percentuale)

### Grafico a dispersione (Δ 2020–2023)
- **Asse X:** variazione della Raccolta Differenziata (punti percentuali)
- **Asse Y:** variazione dei Rifiuti Urbani pro capite (kg/abitante)
- Ogni punto rappresenta un comune
- I quadranti identificano le combinazioni RD/RU (RD↑RU↑, RD↑RU↓, RD↓RU↑, RD↓RU↓)

### Tooltip personalizzato (passando sopra al punto)
Mostra:
- Quadrante e Alert sintetico
- Comune, Provincia e Regione
- Δ RD (pp), Δ RU pro capite (kg/ab), Δ RU totali (t)
- Confronto 2020–2023 per RD (%), RU pro capite (kg/ab) e RU totali (t)

### Trend temporale 2019–2023
- Andamento medio nazionale o per il territorio selezionato
- Confronto tra RD (%) e RU pro capite (kg/abitante)

### Classifiche Top 5 (Δ 2020–2023)
- **Top 5 Peggiori (RD↑ ma RU↑):** comuni in cui aumenta la raccolta differenziata ma crescono anche i rifiuti pro capite
- **Top 5 Virtuosi strutturali (RD↑ e RU↓):** comuni in cui aumenta la raccolta differenziata e diminuiscono i rifiuti pro capite

### Tabella di confronto territoriale
- Δ RD e Δ RU pro capite
- RD 2020→2023 e RU pro capite 2020→2023
- Trend RD e Trend RU
- Quadrante e Alert sintetico (✓ / ▲ / ▽ / !!)

I filtri laterali (Regione, Provincia, Comune) permettono l’esplorazione territoriale.

---

## Limiti dell’analisi

- Analisi basata sulla variazione 2020–2023 (non serie lunga)  
- I comuni con RU pro capite non valido sono esclusi dai calcoli percentuali  
- I dati ISPRA possono essere soggetti a revisioni ex post
- L’aumento della RD non implica automaticamente riduzione RU  
- Il 2020 include effetti pandemia  
- I dati non considerano la qualità della raccolta  
- I comuni molto piccoli possono generare variazioni estreme in tonnellate
- Non include consorsi ma solo comuni 

---

# Metodo

## Dataset utilizzati
Fonte: **ISPRA – Catasto Rifiuti**  
Periodo: **2019–2023** (analisi variazioni 2020–2023)

---

## Costruzione del MART

Per ogni comune sono stati calcolati:

- Δ RD (punti percentuali)  
- Δ RU pro capite (kg/abitante)  
- Δ RU totali (tonnellate)  
- Classificazione quadrante  
- Flag “virtuoso strutturale”

### Definizione quadranti

| Quadrante   | Condizione (Δ 2023–2020) | Lettura                     |
| ----------- | ------------------------ | --------------------------- |
| **RD↑ RU↓** | ΔRD > 0 e ΔRU p.c. < 0   | Miglioramento strutturale (Virtuoso)   |
| **RD↑ RU↑** | ΔRD > 0 e ΔRU p.c. > 0   | RD migliora, RU aumenta     |
| **RD↓ RU↓** | ΔRD < 0 e ΔRU p.c. < 0   | RU diminuisce, RD peggiora  |
| **RD↓ RU↑** | ΔRD < 0 e ΔRU p.c. > 0   | Peggiora entrambi (critico) |


### Logica Alert (tabella)

- ✓ Virtuoso → RD↑ RU↓
- ▲ RU aumenta → RD↑ RU↑
- ▽ RD diminuisce → RD↓ RU↓
- !! Critico → RD↓ RU↑

---

## Scelte metodologiche

- Δ RD espresso in **punti percentuali (pp)**  
- Δ RU espresso in **kg per abitante**  
- Percentuali calcolate solo sui comuni con RU pro capite valido  
- Le misure sono calcolate a livello comunale (chiave: `istat_comune_6`)
- I delta sono calcolati come differenza 2023 − 2020

---

## Cosa si può dedurre

- Distribuzione territoriale dei comportamenti  
- Percentuale reale di miglioramento strutturale  
- Differenze regionali e comunali  
- Pattern di incoerenza tra RD e RU  

---

## Coerenza con i MART

La dashboard utilizza:

- `mart_comuni_delta_2020_2023.parquet`  
- `serie_comuni_2019_2023.parquet`

I file MART sono disponibili nella [cartella Drive del progetto](https://drive.google.com/drive/folders/1Y1CCmyshifHTIQ1TT0jpNl-9C_HzLDgP?usp=drive_link)

Lo schema è documentato nella cartella `/data`.

---

## Versione

**v1.0 – Dashboard finale pubblica**  

---

