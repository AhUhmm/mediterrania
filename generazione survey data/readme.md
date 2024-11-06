# Survey Data Generator

## Descrizione
Generatore di dati per survey nutrizionali che produce profili utente realistici basati su parametri statistici della popolazione italiana (ISTAT 2022). Lo script genera dataset casuali ma coerenti per analisi e testing di sistemi di pianificazione alimentare.

## Caratteristiche Principali

### Dati Generati
- **Dati Demografici**: età, genere, altezza, peso
- **Indicatori Salute**: BMI calcolato con validazione range
- **Obiettivi**: perdita peso, mantenimento, aumento massa muscolare
- **Preferenze Alimentari**: 
  - Diete (standard, vegetariana, vegana, gluten-free)
  - Latti vegetali (soia, riso, avena, nocciola)
  - Timing consumo frutta
  - Esclusioni verdure (intolleranze/preferenze)
- **Allergie**: alimentari e farmacologiche

### Validazioni e Controlli
- Range BMI realistici (16.0-35.0)
- Altezza valida (140-210 cm)
- Età valida (18-75 anni)
- Obiettivi peso realistici (max 15% perdita)
- Correlazioni allergie-preferenze alimentari

### Formati Export
- Excel (.xlsx)
  - Colonne tradotte in italiano
  - Formattazione automatica
- JSON (.json)
  - Include metadati
  - Struttura gerarchica
  - UTF-8 encoding

## Requisiti
```
python >= 3.10
pandas
numpy
openpyxl
seaborn
matplotlib
```

## Installazione
```bash
pip install -q openpyxl seaborn
```

## Utilizzo

### Google Colab
1. Crea un nuovo notebook
2. Copia le celle di codice nell'ordine fornito
3. Esegui le celle sequenzialmente

### Output Esempio
```python
# Generazione dataset
generator = SurveyDataGenerator()
test_data = generator.generate_dataset(n_samples=300)

# Export dati
export_dataset(test_data, 'survey_responses', ExportFormat.EXCEL)
export_dataset(test_data, 'survey_responses', ExportFormat.JSON)
```

## Struttura Dati

### Campi Dataset
| Campo | Descrizione | Tipo |
|-------|-------------|------|
| ID Utente | Identificativo progressivo | Integer |
| Sesso | M/F | String |
| Età | Anni | Integer |
| Altezza (cm) | Centimetri | Float |
| Peso (kg) | Chilogrammi | Float |
| BMI | Indice massa corporea | Float |
| Obiettivo | Obiettivo nutrizionale | String |
| Peso Target (kg) | Peso desiderato | Float |
| Preferenza Dietetica | Tipo di dieta | String |
| Ha Allergie | Flag presenza allergie | Boolean |
| Allergie Alimentari | Lista allergie alimentari | List[String] |
| Allergie ai Farmaci | Lista allergie farmaci | List[String] |
| Preferenze Latte Vegetale | Tipi latte vegetale | List[String] |
| Porzioni Frutta al Giorno | Numero porzioni | Integer |
| Momento Consumo Frutta | Timing consumo | List[String] |
| Esclusioni Verdure | Verdure non gradite/tollerate | List[String] |

### Distribuzioni Statistiche
- BMI: distribuzione normale con parametri ISTAT
- Età: ponderata 30-60 anni
- Allergie: 15% popolazione
- Preferenze dietetiche: 80% standard, 20% speciali

## Visualizzazioni
Lo script genera automaticamente grafici per:
- Distribuzione BMI per genere
- Distribuzione età per obiettivo
- Preferenze dietetiche
- Distribuzione allergie

## Note Implementative
- Generazione dati thread-safe
- Gestione errori robusta
- Logging integrato
- Documentazione inline
- Type hints Python

## Limitazioni
- Dati simulati, non per uso clinico
- Correlazioni semplificate
- Dataset monolingua (italiano)

## Prossimi Sviluppi
- Supporto multilingua
- Correlazioni avanzate
- Export formati addizionali
- Parametri popolazione configurabili
- Validazioni estese

## Licenza
MIT License

## Autori
Sviluppato per scopi formativi/testing

## Contatti
Per segnalazione bug o richieste feature aprire una issue su GitHub
