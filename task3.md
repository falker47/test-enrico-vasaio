# TASK

Implementare il modulo "Patronus Charm" (L'Incanto Patronus).
Questo è il quiz più complesso perché utilizza un algoritmo di "Filtering & Branching".

## DATA SOURCES (CSV Files)

Nella cartella `/data` troverai 3 file CSV fondamentali. Caricali e convertili in oggetti/costanti utilizzabili all'avvio dell'app:
1. `patronus_master.csv`: Contiene le mappature per le domande 1-5.
2. `patronus_unusual.csv`: Contiene la mappatura per la domanda 6.
3. `patronus_rare.csv`: Contiene la mappatura per le domande 6 e 7.

## LOGIC ALGORITHM (The Filtering System)

L'utente parte con una lista di TUTTI i possibili animali (dal Master List).
Ad ogni step (Domande 1-5):
1. L'utente sceglie una parola (es. "Sun").
2. Il sistema filtra la lista degli animali rimanenti, mantenendo solo quelli che hanno "Sun" nella colonna corrispondente (es. "First Question Set" o "Third Question Set").
   - *Attenzione:* L'ordine delle colonne nel CSV corrisponde allo step (Step 1 = First Question Set, ecc.).

**Gestione Step 6 e 7 (Branching):**
- Dopo lo Step 5, se nella lista dei candidati rimasti ci sono animali presenti nel file `patronus_unusual.csv` o `patronus_rare.csv`:
  - NON mostrare ancora il risultato.
  - Sblocca lo Step 6.
  - Filtra in base alla scelta dello Step 6 usando i dati dei CSV Unusual/Rare.
- Dopo lo Step 6, se i candidati rimasti sono nel `patronus_rare.csv`:
  - Sblocca lo Step 7.
  - Filtra e mostra il risultato finale.

## UI/UX REQUIREMENTS

- **Ethereal Atmosphere:** Questo quiz deve sembrare un sogno. Usa sfondi scuri, particelle blu/argentate che fluttuano (stile "Expecto Patronum").
- **Word Selection:** Le parole non sono pulsanti statici. Devono apparire in posizioni leggermente random o fluttuare. Quando il mouse passa sopra, devono illuminarsi.
- **Timing:** Nel quiz originale c'è un timer (se non rispondi, cambia set). Per questa versione "Extended", DISABILITA il timer. Lascia che l'utente scelga con calma (come richiesto dalle specifiche Wizardmore Extended).

## CONFIGURATION

Usa il file `patronus_config.json` (che fornirò) per sapere quali gruppi di parole mostrare ad ogni step.

## TRANSLATION

Tutte le parole (es. "Glow", "Blade") sono in Inglese nei CSV.
Crea un file di traduzione `it_patronus.json` che mappa la parola inglese alla traduzione italiana (es. "Glow": "Bagliore").
L'UI mostra l'Italiano, la logica usa l'Inglese.