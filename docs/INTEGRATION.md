# Collegamento con MONO Ecosystem

## Decisione di prodotto

FamilyWall è la vista familiare rapida e mobile-first. Agenda e spesa restano dati canonici di MONO Ecosystem: FamilyWall non crea copie autonome di eventi, attività, scadenze o voci della spesa.

Il repository MONO contiene già queste entità nel modello SQL:

- `planner_items`: eventi, attività e scadenze;
- `shopping_items`: elementi della lista della spesa;
- `households`, `memberships`, `users`: famiglia, account e permessi;
- `calendars`: aree come Casa, Bambini o Bollette;
- `links`: collegamenti tra record di moduli differenti.

## Stato attuale e blocco tecnico

Il prototipo FamilyWall salva le modifiche in `localStorage`, quindi i dati restano sul singolo browser.

L'API attuale di MONO costruisce lo stato applicativo in memoria all'avvio (`createDefaultState()` in `services/api/src/server.ts`). Questo non basta per la condivisione affidabile tra dispositivi e non deve essere trattato come archivio permanente. Inoltre, al momento l'identità API è ricavata da header inviati dal client e CORS consente qualsiasi origine: queste impostazioni sono adatte solo a una demo e devono essere sostituite da sessioni autenticate e controlli server-side prima di collegare dati familiari reali.

Per attivare la sincronizzazione serve prima collegare il servizio MONO al database PostgreSQL persistente e applicare autenticazione e autorizzazione ai suoi endpoint. Il browser FamilyWall non deve ricevere la credenziale database.

## Contratto applicativo previsto

FamilyWall deve usare il client API autenticato di MONO. La forma degli endpoint è indicativa e va allineata alle route realmente implementate:

- leggere agenda e arretrati della famiglia, filtrando per data, calendario e assegnatario;
- creare, modificare, completare e archiviare elementi di agenda;
- leggere, aggiungere, modificare e segnare come acquistati gli elementi della spesa;
- caricare l'household e i membri a partire dalla sessione autenticata, senza ID familiari codificati nell'app.

Ogni operazione deve verificare l'appartenenza dell'utente all'household e la visibilità del record. Il server restituisce gli ID canonici MONO, così link e aggiornamenti restano coerenti negli altri moduli.

## Regole di proprietà dei dati

| Esperienza FamilyWall | Record autorevole |
|---|---|
| Agenda del giorno | `planner_items` |
| Attività di famiglia | `planner_items` con `kind = task` |
| Impegni | `planner_items` con `kind = event` |
| Scadenze | `planner_items` con `kind = deadline` |
| Lista della spesa | `shopping_items` |
| Calendari e aree | `calendars` |
| Ricette e piano pasti | Entità da definire nel dominio MONO prima di sincronizzarli |

Ricette e pasti non vanno salvati come testo duplicato nelle voci della spesa. Quando il modulo pasti viene progettato, gli ingredienti devono collegarsi agli elementi della spesa tramite ID e quantità.

## Migrazione dal prototipo locale

I dati dimostrativi attualmente inclusi nel browser non sono dati familiari reali. Quando il backend sarà pronto:

1. mantenere il contenuto locale come cache/offline, non come fonte autorevole;
2. associare le modifiche pendenti a ID stabili e chiavi di idempotenza;
3. inviare le modifiche dopo autenticazione e verifica permessi;
4. risolvere i conflitti mostrando l'ultima versione server e l'azione da confermare;
5. rimuovere o esportare la cache demo prima di mostrare i dati MONO sincronizzati.

## Requisiti di rilascio

- Sessione autenticata; nessuna scrittura anonima sull'API.
- Due account familiari autorizzati tramite memberships.
- Autorizzazione server-side per ogni lettura e mutazione.
- Date e orari coerenti con Europe/Rome e regole DST.
- Errori di rete visibili; nessuna falsa conferma di sincronizzazione.
- CRUD e archiviazione coerenti con il Design System MONO.
- Nessun segreto, token o dato reale della famiglia nel repository pubblico.
