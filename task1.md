# TASK

Implementare la logica e l'interfaccia della "Sorting Ceremony" (Smistamento) usando i dati ufficiali estratti.

## DATA SOURCE

Ho creato un file chiamato `sorting_data.json` che contiene l'array completo delle domande e dei pesi.
- Usa questo file come "Source of Truth".
- Struttura pesi: `g` (Gryffindor), `r` (Ravenclaw), `h` (Hufflepuff), `s` (Slytherin).
- IMPORTANTE: Noterai che alcune risposte (es. nel quiz "Pet") assegnano punti a più case contemporaneamente o con valori diversi (es. 25, 50, 100). L'algoritmo deve sommare esattamente questi valori.

## LOGIC REQUIREMENTS

1. **Extended Mode**: L'utente deve rispondere a TUTTE le domande presenti nel JSON (non solo 8 random).
2. **Scoring**:
   - Inizializza punteggi: G=0, R=0, H=0, S=0.
   - Ad ogni risposta, somma i valori `scores` ai totali.
   - Alla fine, la casa con il punteggio più alto vince.
3. **Localization (Italiano)**:
   - Il JSON ha i testi in INGLESE.
   - Crea un file di mapping `it.json` (o un oggetto di traduzione) dove mappi l'ID della domanda e le risposte in ITALIANO.
   - In frontend, mostra SOLO il testo italiano, ma usa l'ID per recuperare il punteggio dal JSON originale.
   - Esempio traduzione: "Dawn or dusk?" -> "Alba o Tramonto?".

## UI REQUIREMENTS

- Crea un componente `SortingQuiz`.
- Mostra una domanda alla volta con animazioni fluide (Framer Motion).
- Background scuro, font elegante (es. serif/medievale).
- Al termine, mostra il risultato con l'emblema della casa vincente.

Procedi creando prima la logica di importazione dati e il file di traduzione per le prime 5 domande come test.