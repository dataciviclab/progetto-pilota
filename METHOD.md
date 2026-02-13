# 🧠 Metodo del progetto

## 🎯 Obiettivo

Verificare se l’aumento della percentuale di raccolta differenziata (RD) nei comuni italiani tra 2019 e 2023 sia accompagnato da:

* riduzione dei rifiuti urbani totali (RU)
* riduzione dei rifiuti pro capite
* oppure da un aumento complessivo dei rifiuti prodotti

L’obiettivo non è fare una classifica, ma distinguere:

* miglioramento strutturale
* miglioramento “percentuale”
* greenwashing statistico


## 📌 Assunzioni

* La % RD è una proxy di qualità del sistema di gestione rifiuti.
* I rifiuti pro capite sono più informativi dei rifiuti totali.
* La popolazione ISTAT associata al dataset è sufficientemente coerente.
* Le variazioni 2020–2023 sono significative per analisi tendenziale.
* I dati ISPRA comunali sono comparabili anno su anno.


## ⚠️ Limiti dei dati

* ISPRA pubblica dati aggregati, non micro-dati operativi.
* Alcuni comuni hanno dati mancanti o incompleti.
* La pandemia (2020–2021) può alterare trend reali.
* I cambi di perimetro comunale (fusioni) possono introdurre rumore.
* Non distinguiamo tipologie di rifiuti oltre l’aggregato RU/RD.


## 🔬 Scelte metodologiche

* Confronto 2020 vs 2023 per ridurre rumore annuale.
* Uso di **delta assoluti e non solo percentuali**.
* Calcolo rifiuti pro capite (kg/abitante).
* Aggregazione 1 riga per comune-anno.
* Riempimento NaN con 0 solo per export BI (non per analisi core).
* Classificazione in quadranti:

  * RD ↑ / RU ↓ → virtuoso strutturale
  * RD ↑ / RU ↑ → miglioramento percentuale ma non strutturale
  * RD ↓ / RU ↑ → peggioramento
  * RD ↓ / RU ↓ → caso anomalo

Abbiamo scelto il confronto diretto tra anni invece di regressione lineare perché:

* il progetto è esplorativo
* l’obiettivo è leggibilità civica
* vogliamo replicabilità semplice


## 🚫 Cosa NON copre questo progetto

* Non misura qualità del materiale raccolto.
* Non analizza costi di gestione rifiuti.
* Non include dati impiantistici.
* Non valuta impatto ambientale reale.
* Non considera flussi extra-comunali (trasferimenti rifiuti).


## 🔁 Come replicare

### Dataset

* ISPRA – Catasto Rifiuti – Dettaglio Comunale
* Anni: 2019–2023
* Livello: Comune

### Notebook

* `01_source_raw`
* `02_raw_clean`
* `03_clean_mart`

### Passaggi principali

1. Scaricare CSV annuali ISPRA.
2. Eseguire RAW → CLEAN (parsing numeri IT + standardizzazione colonne).
3. Calcolare:
   * RU totali
   * RU pro capite
   * % RD
4. Creare delta 2020–2023.
5. Classificare comuni per quadrante.
6. Esportare:
   * Parquet
   * CSV

