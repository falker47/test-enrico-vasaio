# TASK

Creare il modulo "Wand Selection Ceremony" (La scelta della Bacchetta).

## DATA & LOGIC SOURCE

Utilizza il file `wand_data.json` come struttura base.
La logica della bacchetta NON è a punteggio, ma combinatoria (Lookup Table).
La bacchetta finale è un oggetto composto da 4 proprietà calcolate separatamente:

1. **WOOD (Legno)**:
   - Input richiesti: `eyes` (Occhi) + `pride` (Tratto) + `path` (Percorso).
   - Logica: Cerca la corrispondenza esatta nella tabella dei legni.
   - *Nota per l'AI:* Poiché la tabella dei legni completa (CSV) è troppo grande per il JSON, implementa una funzione `getWoodType(eyes, trait, path)` che accetta un oggetto di mapping o usa un file separato `woods_db.js` che conterrà tutte le combinazioni estratte dal file "All Woods.csv".

2. **CORE (Nucleo)**:
   - Input richiesti: `fear` (Paura) + `artefact` (Oggetto scelto).
   - Usa la tabella `logic.cores`.

3. **FLEXIBILITY (Flessibilità)**:
   - Input richiesti: `pride` (Tratto) + `birth_day` (Data di nascita).
   - Logica: Determina se il giorno di nascita è PARI (Even) o DISPARI (Odd).
   - Usa la tabella `logic.flexibilities` incrociando il Tratto e la Parità del giorno.

4. **LENGTH (Lunghezza)**:
   - Input richiesti: `height` (Altezza) + `artefact` (Oggetto).
   - Usa la tabella `logic.lengths`.

## UI FLOW

1. Mostra le 7 domande in sequenza.
2. Per la domanda "Artefact", visualizza un baule o una griglia di oggetti misteriosi (icone o immagini placeholder).
3. Per la domanda "Path", mostra 3 card visuali (Mare, Foresta, Castello).
4. Alla fine, rivela la bacchetta completa con una descrizione generata in Italiano: "La tua bacchetta è in legno di [Wood], nucleo di [Core], lunghezza [Length] pollici e flessibilità [Flexibility]."

## TRANSLATION

Come per lo Smistamento, crea un file `it_wand.json` per mappare tutte le domande e le opzioni (es. "Dusty Bottle" -> "Bottiglia Impolverata") in Italiano.