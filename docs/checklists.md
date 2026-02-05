# Checklist per ruolo (Tasks in Project Board)

## Project Lead
### Prima di partire
- [ ] Domanda civica unica, chiara, misurabile
- [ ] Dataset ufficiali: fonte, periodo, livello
- [ ] Output pubblico deciso (dashboard/report/pagina)
- [ ] Issue create e assegnate per ruolo

### Durante
- [ ] Issue atomiche e chiare
- [ ] Decisioni documentate (commenti / issue)
- [ ] Scope sotto controllo (no extra non necessari)

### Chiusura
- [ ] DoD rispettata
- [ ] Limiti evidenti
- [ ] README pronto per pubblico
- [ ] Release/tag (opzionale)

---

## Data
### Input
- [ ] Raw immutato + link fonte
- [ ] Granularità confermata (anno/ente/territorio)

### Pulizia
- [ ] snake_case per colonne
- [ ] tipi corretti (date/numeric/string)
- [ ] null gestiti consapevolmente
- [ ] duplicati/outlier gestiti o segnalati

### Metriche
- [ ] metriche minime, non ridondanti
- [ ] aggregazioni coerenti con domanda
- [ ] naming metriche esplicito

### Output
- [ ] clean/mart riproducibili
- [ ] query/notebook commentati
- [ ] changelog sintetico in issue

---

## Metodo
- [ ] Cosa misura / non misura il dataset
- [ ] Assunzioni dichiarate
- [ ] Confronti omogenei (perimetro/periodo/definizioni)
- [ ] Cambi definizione nel tempo segnalati
- [ ] Limiti + bias noti dichiarati
- [ ] “Cosa NON si può concludere” scritto

---

## Viz
- [ ] 1 domanda = 1 vista principale
- [ ] titoli in forma di frase (non etichetta)
- [ ] unità sempre visibili
- [ ] filtri essenziali e sensati
- [ ] leggibile senza spiegazione
- [ ] niente scelte fuorvianti (scale, doppie scale, % senza base)

---

## QA
### Sanity
- [ ] totali coerenti
- [ ] ordini di grandezza sensati
- [ ] valori impossibili assenti
- [ ] regressioni controllate (se aggiornamenti)

### Cross-check
- [ ] confronto con fonte (o campione)
- [ ] confronto con anni precedenti
- [ ] confronto con dataset simili (se esistono)

### Output
- [ ] issue per anomalie residue con severità
- [ ] note QA in chiusura issue

---

## Doc
- [ ] spiegazione non tecnica
- [ ] acronimi spiegati
- [ ] struttura minima:
  - Cosa guardo
  - Perché conta
  - Cosa emerge
  - Cosa non emerge
  - Limiti
- [ ] link: dashboard + dati + metodo
- [ ] call-to-action: domanda civica finale
