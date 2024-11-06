# MediterranIA - Generatore di Piani Alimentari

Questo script Python genera piani alimentari personalizzati basati su dati biometrici degli utenti e un database di ricette. È progettato per supportare una dieta mediterranea equilibrata, tenendo conto delle preferenze individuali, restrizioni alimentari e obiettivi nutrizionali.

## Funzionalità Principali

- Generazione automatica di piani alimentari settimanali personalizzati
- Supporto per diverse preferenze dietetiche (es. vegetariano, vegano)
- Gestione di allergie e intolleranze alimentari
- Calcolo automatico dei valori nutrizionali
- Validazione dei dati in input
- Ottimizzazione dei pasti in base agli obiettivi (perdita peso, mantenimento, massa muscolare)

## Requisiti

- Python 3.7+
- Google Colab environment
- Librerie richieste:
  - pandas
  - numpy
  - typing
  - json

## Struttura dei File di Input

### 1. File Survey (survey_data.json)

Contiene i dati degli utenti nel seguente formato:
```json
{
  "metadata": {
    "version": "1.0",
    "date": "2024-03-01"
  },
  "data": [
    {
      "ID Utente": "001",
      "Sesso": "M",
      "Età": 30,
      "Altezza (cm)": 175,
      "Peso (kg)": 70,
      "BMI": 22.9,
      "Obiettivo": "Mantenere peso",
      "Preferenza Dietetica": "nessuno",
      "Allergie Alimentari": "Nessuna",
      "Esclusioni Verdure": "Nessuna",
      "Preferenze Latte Vegetale": "Nessuna",
      "Porzioni Frutta al Giorno": 2,
      "Momento Consumo Frutta": ["Mattina", "Pomeriggio"]
    }
  ]
}
```

### 2. File Ricettario (ricettario.json)

Contiene il database delle ricette nel seguente formato:
```json
{
  "metadata": {
    "version": "1.0",
    "date": "2024-03-01"
  },
  "colazioni": [...],
  "pranzi": [
    {
      "id_pasto": "P001",
      "nome": "Nome Ricetta",
      "ingredienti": [
        {
          "nome": "Ingrediente 1",
          "quantita": 100,
          "unita": "g"
        }
      ],
      "valori_nutrizionali": {
        "calorie": 300,
        "proteine": 20,
        "carboidrati": 40,
        "grassi": 10
      },
      "proprieta": {
        "vegano": false,
        "vegetariano": true,
        "senza_glutine": true,
        "basso_sodio": true,
        "adatto_diabetici": true
      },
      "tempo_preparazione": 30,
      "difficolta": "media",
      "porzioni": 1
    }
  ],
  "cene": [...],
  "spuntini": [...]
}
```

## Output

Il programma genera un file JSON (es. `meal_plans_dataset_20241106_094936.json`) contenente:
- Piani alimentari settimanali per ogni utente
- Analisi nutrizionale dettagliata
- Verifica del raggiungimento degli obiettivi nutrizionali
- Statistiche aggregate

Un esempio di output è disponibile nella cartella `sample_data/meal_plans_dataset_20241106_094936.json`.

### Struttura Output
```json
{
  "metadata": {
    "version": "1.0",
    "date": "2024-11-06",
    "generated_profiles": 300
  },
  "meal_plans": [
    {
      "user_id": "001",
      "week_plan": {
        "monday": {
          "breakfast": {...},
          "lunch": {...},
          "dinner": {...},
          "snacks": [...]
        },
        // altri giorni...
      },
      "nutritional_analysis": {...},
      "goals_achieved": {...}
    }
    // altri utenti...
  ]
}
```

## Utilizzo

1. Avviare il notebook in Google Colab
2. Eseguire tutte le celle in ordine
3. Quando richiesto, caricare i file di input (survey_data.json e ricettario.json)
4. Il programma genererà automaticamente i piani alimentari e salverà l'output in un file JSON
   (vedere esempio in `sample_data/meal_plans_dataset_20241106_094936.json`)

## Componenti Principali

### RecipeManager
Gestisce il database delle ricette e la loro selezione in base ai criteri dell'utente:
- Compatibilità con preferenze dietetiche
- Gestione allergie
- Rotazione delle ricette per varietà
- Adattamento delle porzioni

### MealPlanGenerator
Genera i piani alimentari completi:
- Calcolo dei fabbisogni nutrizionali
- Bilanciamento dei pasti
- Verifica dei target nutrizionali
- Generazione dataset per analisi ML

## Validazione

Il sistema include controlli di validazione per:
- Formato e completezza dei file JSON
- Valori biometrici realistici
- Coerenza dei dati nutrizionali
- Compatibilità delle ricette con le restrizioni

## Note

- I file JSON devono essere codificati in UTF-8
- Le ricette vengono salvate in memoria per utilizzi futuri
- Il sistema mantiene traccia delle ricette utilizzate per evitare ripetizioni eccessive

## Limitazioni

- Non supporta piani alimentari più lunghi di una settimana
- Richiede un minimo di ricette per ogni tipo di pasto
- Non include gestione di intolleranze multiple

## Sviluppi Futuri

- Aggiunta supporto per piani multi-settimana
- Implementazione di preferenze orarie per i pasti
- Integrazione con database esterni di ricette
- Supporto per obiettivi più specifici
- Miglioramento dell'algoritmo di rotazione ricette
