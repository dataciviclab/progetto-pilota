# Filtro Dati Aggregati e Consorzi — Documentazione Bug

## Problema Identificato

I CSV raw ISPRA contengono nella stessa tabella due tipologie di record distinte, identificate dalla colonna `Dato riferito a`:

| Valore | Significato | Azione |
|--------|-------------|--------|
| `Comune` | Dati del singolo comune | Mantieni |
| `Vedi aggregazione: [nome]` | Dati di consorzio intercomunale | Rimuovi |
| `Aggregazione: [nome]` | Dati aggregati | Rimuovi |

Distribuzione nel dataset (anno 2019):

```
Comune:                                    7.721 righe (97,5%)
Vedi aggregazione: EVANCON-MONT CERVIN:       19 righe
Vedi aggregazione: ATOME4 S.P.A.:             17 righe
Vedi aggregazione: Grand Paradis:             12 righe
Vedi aggregazione: Grand Combin:              10 righe
... altri ~60 tipi di aggregazioni
Totale aggregazioni:                         194 righe (2,5%)
```

---

## Perché Causa un Problema

I record aggregati attribuiscono le tonnellate di rifiuti di un intero consorzio intercomunale (10-20 comuni) alla popolazione di un singolo comune. Il risultato è un valore pro capite fisicamente impossibile.

Esempio — **Bard (Valle d'Aosta)**:

- Popolazione del comune: 102 abitanti
- Tonnellate attribuite: 5.682 t (intero consorzio)
- Pro capite risultante: **55.712 kg/ab**
- Media nazionale di riferimento: ~500 kg/ab

Senza filtro, il dataset conteneva circa 800 comuni con valori pro capite superiori a 3.000 kg/ab, rendendo le analisi e il dashboard non veritieri.

---

## Soluzione Implementata

Filtro applicato nella funzione `clean_catasto()` del notebook `02_raw_clean`, che mantiene esclusivamente le righe con `Dato riferito a = "Comune"`.

```python
if "Dato riferito a" in df.columns:
    before = len(df)
    df = df[df["Dato riferito a"].astype(str).str.strip() == "Comune"].copy()
    filtered = before - len(df)
    if filtered > 0:
        print(f"Anno {year}: Filtrate {filtered} righe di aggregazioni/consorzi")
```

Righe filtrate per anno:

```
Anno 2019: 194 righe
Anno 2020: 185 righe
Anno 2021: 195 righe
Anno 2022: 183 righe
Anno 2023: 142 righe
Totale:    899 righe
```

---

## Impatto sul Dataset

| | Prima del filtro | Dopo il filtro |
|--|-----------------|----------------|
| Righe totali (5 anni) | ~39.500 | ~38.600 |
| Pro capite massimo | 55.712 kg/ab | ~2.000 kg/ab |
| Comuni con valori anomali (> 3.000 kg/ab) | ~800 | 0 |

---

## Note Tecniche

Il filtro viene applicato prima della standardizzazione dei nomi colonna, quindi usa il nome originale `"Dato riferito a"` (non la versione standardizzata `dato_riferito_a`).

Se in versioni future del dataset ISPRA questa colonna non fosse più presente, il filtro viene saltato senza errori e il notebook continua normalmente. In quel caso sarebbe necessario reintrodurre un filtro euristico basato sui valori pro capite.

I dati aggregati e i consorzi non vengono eliminati in modo permanente: rimangono disponibili nei file raw originali per eventuali analisi separate.
