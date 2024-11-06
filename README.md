# Sistema Generazione Piani Alimentari

Sistema integrato per la generazione di dati survey nutrizionali e la creazione di piani alimentari personalizzati. Il sistema è composto da due moduli principali che possono essere utilizzati in modo indipendente o in sequenza.

## Struttura Repository

```
├── generazione_survey_data/
│   ├── Generazione_survey.ipynb
│   └── README.md
├── generazione_piani_alimentari/
│   ├── Generatore_piani_v2.ipynb
│   ├── README.md
│   └── sample_data/
│       ├── survey_data.json
│       └── ricettario.json
└── README.md
```

## Moduli

### 1. Generazione Survey Data
Script per la generazione di dataset di survey nutrizionali con profili utente realistici basati su statistiche ISTAT 2022. Genera dati demografici, preferenze alimentari, allergie e obiettivi nutrizionali.

### 2. Generazione Piani Alimentari
Sistema di generazione di piani alimentari personalizzati basato sui dati delle survey. Utilizza un ricettario predefinito e regole nutrizionali per creare piani settimanali adatti alle esigenze individuali.

## Quick Start

1. Per generare nuovi dati survey:
   - Esegui `generazione_survey_data/Generazione_survey.ipynb`
   - Esporta i risultati in JSON

2. Per generare piani alimentari:
   - Utilizza i dati survey generati o il file di esempio `survey_data.json`
   - Esegui `generazione_piani_alimentari/Generatore_piani_v2.ipynb`

## Requisiti
- Python 3.10+
- Jupyter Notebook
- Dipendenze dettagliate nei README dei singoli moduli

## Note
- I dati generati sono simulati e non adatti per uso clinico
- Consultare i README specifici nei sottodirectory per dettagli implementativi

## Licenza
MIT License
