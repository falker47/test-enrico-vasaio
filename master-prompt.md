# ROLE

Sei un Senior Frontend Engineer esperto in Data Visualization e logiche di gioco.
Stiamo implementando il "Modulo Patronus" per la nostra app Pottermore Custom.

# CONTEXT & GOAL

Creare un'esperienza immersiva e misteriosa dove l'utente seleziona parole istintive per scoprire il proprio Patronus.
L'algoritmo si basa su un sistema di "Filtraggio Progressivo" utilizzando dataset CSV reali.

# DATA SOURCES (Files in `/data`)

1. `patronus_master.csv`: Il database principale. Colonne: [Patronus, First Question Set, Second..., Fifth...].
2. `patronus_unusual.csv`: Mapping per lo Step 6 (se sbloccato).
3. `patronus_rare.csv`: Mapping per lo Step 7 (se sbloccato).
4. `it_patronus.json`: File chiave-valore per le traduzioni (Inglese -> Italiano).

# LOGIC REQUIREMENTS (The Engine)

1. **State Management**:

   - Mantenere un array `candidates` che all'inizio contiene TUTTE le righe del `patronus_master.csv`.
   - Mantenere traccia del `currentStep` (da 1 a 7).

2. **The Loop (Step 1-5)**:

   - Ad ogni step, mostra le parole opzionabili (tratte dalle colonne del CSV corrispondente allo step corrente).
   - _Visualizzazione_: Usa `it_patronus.json` per mostrare la parola in ITALIANO all'utente, ma usa la chiave INGLESE per la logica.
   - _Azione Utente_: Quando l'utente clicca una parola (es. "Sun"):
     - Filtra l'array `candidates`: mantieni solo i Patronus che hanno "Sun" nella colonna relativa a quello step.
     - Esempio: Se siamo allo Step 1, controlla la colonna "First Question Set".

3. **The Branching Logic (Critical)**:

   - Al termine dello Step 5, controlla i `candidates` rimasti.
   - **Caso A (Unusual):** Se tra i candidati c'è un animale presente nel file `patronus_unusual.csv`, NON mostrare il risultato. Procedi allo Step 6.
   - **Caso B (Very Rare):** Se i candidati sono nel file `patronus_rare.csv`, procedi fino allo Step 7.
   - **Caso C (Common):** Se nessuno dei candidati è in quelle liste, ferma il quiz e mostra il risultato (se sono rimasti più candidati, scegline uno a caso tra quelli validi).

4. **Parsing CSV**:
   - Usa una libreria come `papaparse` o una funzione custom per leggere i CSV all'avvio.
   - Nota: Le celle dei CSV contengono più valori separati da `/` (es. "Glow/Blade/Wind"). Il filtro deve controllare se la parola scelta è _inclusa_ in quella stringa.

# UI/UX SPECIFICATIONS

- **Atmosphere**: Full screen, sfondo scuro/blu notte.
- **Interazione**: Le parole non devono essere bottoni statici. Devono apparire in posizioni semi-casuali sullo schermo, con un effetto "fade-in" etereo (framer-motion).
- **Hover**: Al passaggio del mouse, la parola deve illuminarsi (effetto bagliore esterno).
- **Result**: Alla fine, mostra "Il tuo Patronus è: [Nome Animale]". (Bonus: se riesci, cerca un'immagine placeholder su Unsplash con query `[Nome Animale] animal`).

# EXECUTION STEPS

1. Crea la funzione di utility per caricare e parsare i 3 CSV.
2. Crea il hook `usePatronusLogic` che gestisce il filtraggio degli array.
3. Crea il componente UI che renderizza le parole usando il file di traduzione.
