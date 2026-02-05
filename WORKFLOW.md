# 🔁 WORKFLOW – come si lavora

Questo documento descrive il workflow standard per lavorare su un progetto DataCivicLab.

Obiettivo: **collaborazione semplice, asincrona, scalabile**.

---

## 🧭 Principio base

```text
Tutto parte da una Discussion.
Tutto finisce in una Pull Request.
```

---

## 1) Discussion → idee, domande, contesto

Le **Discussions** servono per:
- proporre una domanda civica
- discutere dataset e fonti
- fare scelte metodologiche (KPI, perimetro, definizioni)
- allineare rapidamente il team

👉 Nessun lavoro “pesante” parte senza almeno **una discussion iniziale**.

---

## 2) Issue → task concreti

Le **Issue** rappresentano lavoro reale.

Una issue dovrebbe:
- avere un obiettivo chiaro
- essere limitata (no mega-task)
- avere criteri di chiusura (Definition of Done)

Esempi:
- ingestione dataset X (raw)
- pulizia e normalizzazione (clean)
- costruzione mart + KPI base
- prima dashboard (MVP)

👉 Una issue = una cosa fatta.

---

## 3) Branch → lavorare senza rompere `main`

Ogni issue si lavora su un **branch dedicato**.

Naming consigliato:
```text
issue-12-clean-dataset-rifiuti
```

Regole:
- non lavorare direttamente su `main`
- PR piccole e frequenti > PR gigante

---

## 4) Pull Request → revisione e qualità

La **Pull Request (PR)** serve a:
- mostrare cosa è stato fatto
- permettere review e miglioramenti
- lasciare traccia delle decisioni

Una PR è pronta quando:
- il task è completo
- README / docs coinvolte sono aggiornate
- non sono stati caricati dati sul repo

---

## 5) Review → Merge

La review verifica:
- coerenza metodologica
- qualità dei notebook / query
- chiarezza della documentazione

Chi può approvare:
- **Project Lead** o **Maintainer** (vedi `GOVERNANCE.md`)

Dopo approvazione → merge su `main`.

---

## 📦 Dati e Drive (importante)

```text
GitHub = codice + metodo + documentazione
Drive  = dati
```

Nelle PR:
- **non** caricare CSV/XLS/Parquet “pesanti”
- inserire **link Drive** e schema/README aggiornati
- spiegare cosa è cambiato e perché

---

## ✅ Definition of Done (DoD)

Per chiudere un task, in generale:
- output prodotto (notebook/query/dashboard)
- documentazione aggiornata (almeno README rilevanti)
- link Drive inseriti correttamente
- controlli qualità minimi eseguiti

(Se vuoi una DoD più dettagliata: `docs/definition-of-done.md`.)

---
