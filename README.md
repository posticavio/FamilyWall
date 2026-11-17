# FamilyWall

App familiare condivisa, ispirata alle funzioni di FamilyWall e progettata per l'uso quotidiano della famiglia. Il progetto segue il MONO Design System e potrà integrarsi con MONO Ecosystem.

## Obiettivo

Dare a ogni componente della famiglia una vista semplice e affidabile di impegni, attività, spesa, pasti e scadenze. La schermata iniziale deve rispondere rapidamente a tre domande:

1. Che cosa succede oggi?
2. Chi deve occuparsene?
3. Che cosa non va dimenticato?

## Principi di prodotto

- **Mobile-first:** le azioni più comuni sono rapide e comode da telefono.
- **Condiviso:** gli elementi familiari sono visibili ai membri autorizzati e indicano chiaramente il responsabile.
- **Un solo dato:** agenda, attività, scadenze e spese si collegano tra loro senza duplicazioni.
- **Chiaro nel quotidiano:** priorità, orari, responsabili e stato sono leggibili a colpo d'occhio.
- **Adattabile:** sezioni e calendari possono essere attivati e organizzati secondo le esigenze della famiglia.
- **Coerente con MONO:** design system, accessibilità, navigazione responsive e regole CRUD standard MONO.
- **Allegati su Drive:** documenti e file non testuali risiedono in cartelle Drive dedicate e si aprono dalla relativa scheda.

## Utenti e permessi

- **Adulti:** gestione completa degli elementi condivisi; assegnazione delle attività e gestione delle impostazioni.
- **Profili dei figli:** calendario, routine e informazioni organizzative; accesso configurabile in base all'età e al dispositivo.
- **Invitati o familiari:** accesso limitato alle sezioni o agli eventi condivisi con loro.

I permessi devono essere configurabili. I dati personali e sanitari richiedono una sezione riservata e non devono apparire nella bacheca generale.

## Navigazione iniziale

1. **Oggi** — riepilogo di impegni, attività, scadenze e promemoria.
2. **Calendario** — viste giorno, settimana e mese con filtri per persona e area.
3. **Attività** — assegnatario, scadenza, ricorrenza, priorità, checklist e stato.
4. **Spesa** — lista condivisa, quantità, reparto, priorità e stato di acquisto.
5. **Pasti** — piano pasti, ricette e ingredienti collegati alla spesa.
6. **Famiglia** — profili, routine, informazioni utili e impostazioni.

Documenti e finanze potranno essere mostrati come sezioni o collegamenti integrati, senza duplicare i dati delle app MONO dedicate.

## Schermata “Oggi”

Ordine proposto:

- **Prossimo impegno**, con ora, luogo, partecipanti e azione per aprire la navigazione o chiamare.
- **Agenda di oggi**, ordinata per orario e raggruppabile per persona.
- **Da fare**, con attività scadute e in scadenza, assegnatario e completamento rapido.
- **Promemoria e scadenze**, con accesso al pagamento o al documento collegato.
- **Pasto previsto** e scorciatoia agli ingredienti mancanti.
- Pulsante persistente **Aggiungi**, con creazione rapida di evento, attività, spesa, pasto o nota.

Gli elementi completati restano consultabili nella relativa sezione; le attività scadute rimangono visibili in “Oggi” finché non vengono completate o riprogrammate.

## Ambito della prima versione (MVP)

### Incluso

- Spazio condiviso per la famiglia e membri autorizzati.
- Dashboard “Oggi”.
- Calendario familiare con colori e filtri per area/persona.
- Attività con assegnatario, scadenza, ricorrenza, priorità e checklist.
- Lista della spesa condivisa.
- Piano pasti essenziale e ricette collegate agli ingredienti.
- Notifiche per gli elementi assegnati o condivisi.
- Ricerca e gestione completa degli elementi (creazione, lettura, modifica, archiviazione/eliminazione).
- Layout responsive, PWA e stati offline di base da definire.

### Da pianificare dopo l’MVP

- Importazione e sincronizzazione con Google Calendar.
- Collegamento a Drive per documenti e allegati.
- Finanze e scadenze con collegamento all’app Finanze MONO.
- Routine e checklist per i figli.
- Bacheca familiare e commenti sugli elementi.
- Automazioni e assistente AI per inserimento da linguaggio naturale.
- Widget e viste personalizzabili.

## Flussi principali

### Aggiungere un impegno

Creazione rapida → titolo e data/ora → area e partecipanti → luogo e promemoria → salva. L’evento compare nel calendario e nella vista “Oggi” dei partecipanti.

### Assegnare un’attività

Nuova attività → descrizione → assegnatario → scadenza o ricorrenza → priorità/checklist → salva. Il responsabile riceve la notifica; l’attività resta visibile fino al completamento o alla riprogrammazione.

### Pianificare un pasto

Selezione del giorno → ricetta → porzioni → ingredienti mancanti aggiunti alla spesa. Le quantità sono sempre visibili accanto agli ingredienti.

## Entità principali

- **Famiglia**
- **Membro**
- **Profilo figlio**
- **Calendario/area**
- **Evento**
- **Attività**
- **Ricorrenza**
- **Promemoria**
- **Voce della spesa**
- **Pasto**
- **Ricetta**
- **Documento/collegamento esterno**
- **Notifica**

Le entità devono avere identificativi stabili, date di creazione/modifica e regole esplicite per eliminazione, archiviazione e sincronizzazione.

## Design e interazione

- Applicare il MONO Design System: tipografia, spaziature, colori, componenti e modalità chiara/scura.
- Mobile-first con navigazione inferiore sulle schermate piccole e navigazione adattiva su desktop.
- Nessun overflow orizzontale; target touch ampi e testi leggibili.
- Filtri e ricerca accessibili da controlli compatti, con pannelli chiari su richiesta.
- Colori coerenti per le aree, con icone ed etichette oltre al colore per garantire accessibilità.
- Conferma per eliminazioni; preferire archiviazione recuperabile quando appropriato.

## Decisioni ancora da prendere

- Nome definitivo e icona dell’app.
- App autonoma o modulo di MONO Ecosystem con accesso diretto.
- Provider di autenticazione e modello di condivisione con la famiglia.
- Calendari esterni da sincronizzare e quale sistema mantiene il dato principale.
- Regole delle notifiche e quiet hours.
- Tecnologia e backend in coerenza con MONO App Factory.
- Modalità offline e risoluzione dei conflitti tra modifiche simultanee.

## Percorso di lavoro

1. Confermare i flussi MVP e il modello di condivisione.
2. Definire architettura, dati e integrazioni.
3. Disegnare le schermate principali secondo MONO Design System.
4. Implementare prima dashboard, calendario e attività.
5. Aggiungere spesa e pasti collegati.
6. Verificare l’esperienza su smartphone e desktop prima del rilascio.

## Privacy

Questo repository è pubblico. Non inserire qui dati personali reali, credenziali, informazioni sanitarie o documenti della famiglia. Usare dati fittizi negli esempi e nelle schermate dimostrative.
