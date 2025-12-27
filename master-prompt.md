## PROJECT IDENTITY

Stiamo costruendo "Wizarding World Custom", una Web App moderna che ricrea le versioni "Extended" dei tre grandi quiz di Pottermore (Smistamento, Bacchetta, Patronus) in un'unica interfaccia fluida e localizzata in Italiano.

## TECH STACK

- **Framework**: Next.js 14+ (App Router)
- **Language**: TypeScript (Strict mode)
- **Styling**: Tailwind CSS (per il layout) + Custom CSS (per effetti magici specifici)
- **Animations**: Framer Motion (OBBLIGATORIO per transizioni fluide tra le domande. Niente scatti.)
- **State Management**: Zustand (Store globale per salvare i risultati delle 3 cerimonie)
- **Data Parsing**: `papaparse` (per leggere i CSV del Patronus)

## FOLDER STRUCTURE (SIMPLIFIED & FLAT)

Adottiamo una struttura piatta per facilitare lo sviluppo. Non creare sottocartelle inutili nei componenti.

/src
/app -> Le pagine: page.tsx (Home), sorting/page.tsx, wand/page.tsx, patronus/page.tsx
/components -> Metti QUI tutti i componenti UI. - Esempi: `SortingQuiz.tsx`, `WandQuiz.tsx`, `PatronusQuiz.tsx`, `Card.tsx`, `ProgressBar.tsx`
/data -> Contiene i file JSON statici (`sorting_data.json`, `wand_data.json`)
/utils -> Funzioni pure. - `gameLogic.ts`: Calcolatori di punteggio. - `csvLoader.ts`: Caricamento dati Patronus.

## CORE RULES

1. **Language Strategy (English Logic / Italian UI)**:

   - I dati originali (JSON/CSV) sono in INGLESE e tali devono restare nella logica interna (ID, chiavi).
   - L'interfaccia utente deve essere rigorosamente in ITALIANO.
   - Usa i file di traduzione o mapping al volo. NON tradurre gli ID nel database.

2. **Quiz Logic Types**:

   - **Sorting Hat**: Logica ad "Accumulatore" (+5 punti a Grifondoro). Rispondi a tutte le 28 domande.
   - **Wand**: Logica a "Matrice di Decisione" (Occhi + Tratto = Legno).
   - **Patronus**: Logica a "Filtro Progressivo" su CSV (Branching paths).

3. **Immersive UX**:
   - L'app deve sembrare "magica". Usa background scuri, particelle, font serif eleganti.
   - Nessun reload di pagina durante il quiz.

## DATA SOURCES LOCATIONS

- I JSON (`sorting_data.json`, `wand_data.json`, `it_patronus.json`) si trovano in `/src/data`.
- I CSV del Patronus si trovano in `/public/data`.

## EXECUTION PLAN

Procediamo modulo per modulo.

1. **Setup**: Installa dipendenze (framer-motion, zustand, lucide-react, papaparse) e crea il Layout base.
2. **Sorting Module**: Implementa il quiz Casa usando `sorting_data.json`.
3. **Wand Module**: Implementa il quiz Bacchetta usando `wand_data.json`.
4. **Patronus Module**: Implementa il quiz Patronus leggendo i CSV.

Attendo istruzioni per iniziare la Fase 1 (Setup).
