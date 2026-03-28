---
title: Casi d’uso per la vendita al dettaglio
description: Scopri come le organizzazioni di vendita al dettaglio utilizzano Adobe Experience Platform per personalizzare le esperienze di acquisto, recuperare i carrelli abbandonati e promuovere la fidelizzazione dei clienti.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: 89a5b6b5-bb71-4154-bb3b-f6dbbbef13eb
source-git-commit: 3542d76106fada9019b70a8cc9fd4c74872d4995
workflow-type: tm+mt
source-wordcount: '7216'
ht-degree: 0%

---

# Casi d’uso per la vendita al dettaglio

Le organizzazioni di vendita al dettaglio utilizzano Adobe Experience Platform per unificare i dati dei clienti provenienti da negozi online, sedi fisiche e programmi fedeltà in un’unica vista di ogni acquirente. Questa base consente esperienze di acquisto personalizzate, un’attività di sensibilizzazione tempestiva che recupera i ricavi persi e strategie di fidelizzazione che mantengono i clienti al loro ritorno.

## Consigli di prodotto personalizzati

Mostra consigli di prodotti personalizzati su home page, pagine di categorie e pagine di dettagli dei prodotti in base alla cronologia di navigazione, alla cronologia degli acquisti e a comportamenti simili dei clienti. Quando i clienti vedono prodotti su misura per i loro interessi, trascorrono più tempo esplorando e hanno molte più probabilità di acquistare.

### Impatto aziendale

I rivenditori visualizzano tassi di click-through e tassi di conversione migliorati quando distribuiscono consigli personalizzati invece di elenchi di prodotti statici.

### Come implementare

Utilizza il pattern [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Questo approccio utilizza modelli di consigli basati sull’intelligenza artificiale che imparano continuamente dalle interazioni dei clienti per individuare i prodotti più rilevanti per ogni singolo utente. Questo è il pattern corretto quando il set di elementi è di grandi dimensioni e in continua evoluzione e la selezione è guidata dall’affinità comportamentale, anziché da un set limitato di offerte disciplinate dalle regole di idoneità.

### Considerazioni tecniche

- I dati del catalogo dei prodotti devono essere acquisiti e mantenuti aggiornati, inclusi attributi dei prodotti, immagini, prezzi e disponibilità, per garantire che i consigli riflettano ciò che i clienti possono effettivamente acquistare.
- I segnali comportamentali come le visualizzazioni del prodotto, gli eventi da aggiungere al carrello e gli acquisti devono scorrere quasi in tempo reale per mantenere aggiornati i consigli all’interno di una singola sessione di navigazione.
- I modelli di consigli richiedono una strategia di avvio a freddo per i nuovi visitatori che non dispongono di cronologia di navigazione e che in genere si rifanno ai prodotti di tendenza o più venduti.
- È necessario monitorare attentamente le prestazioni di caricamento delle pagine, in quanto le chiamate di personalizzazione non dovrebbero aggiungere una latenza visibile all’esperienza di acquisto.


## Ripristino e-mail carrello abbandonato

Invia automaticamente promemoria e-mail personalizzati ai clienti che hanno abbandonato il carrello, inclusi gli articoli rimasti e le offerte pertinenti, per incoraggiarne il completamento. L’abbandono del carrello è una delle maggiori fonti di perdita di ricavi nel settore del commercio al dettaglio e un follow-up tempestivo può recuperare una quota significativa di tali vendite.

### Impatto aziendale

Programmi di recupero del carrello efficaci migliorano i tassi di recupero del carrello e possono generare ricavi incrementali significativi a seconda del volume del negozio.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio risponde a un evento di abbandono del carrello in tempo reale, inviando un promemoria tempestivo mentre l’intento di acquisto è ancora elevato. Si tratta del modello corretto quando l’attivazione è rappresentata da un’azione discreta del cliente e la risposta richiesta è un messaggio singolo e sensibile al tempo, anziché una sequenza in più fasi o una selezione dinamica dell’offerta.

### Considerazioni tecniche

- Il rilevamento dell’abbandono del carrello richiede la definizione di una soglia di inattività (solitamente 30-60 minuti) prima di attivare il primo promemoria, evitando di inviare messaggi ai clienti che stanno ancora effettuando acquisti attivi.
- Il contenuto delle e-mail deve richiamare dinamicamente le immagini, i prezzi e la disponibilità correnti del prodotto dal catalogo al momento dell’invio, in quanto gli articoli possono essere venduti o cambiare il prezzo tra l’abbandono e la consegna.
- Le regole di quota limite devono impedire ai clienti di ricevere più e-mail dal carrello in un breve periodo, soprattutto se abbandonano frequentemente i carrelli.
- Gli elenchi di consenso e soppressione devono essere controllati prima dell’invio e i clienti che hanno completato l’acquisto tramite un altro canale devono essere esclusi in tempo reale.


## Campagne urgenti basate sull’inventario

Attiva avvisi e campagne in tempo reale quando l’inventario dei prodotti è basso, creando urgenza e incoraggiando l’acquisto immediato. Gli acquirenti che vedono che rimangono solo pochi oggetti sono motivati ad agire rapidamente piuttosto che ritardare la loro decisione.

### Impatto aziendale

Le campagne a bassa urgenza di inventario favoriscono una conversione migliore dei prodotti in primo piano, contribuendo al contempo a ridurre le scorte in eccesso accelerando la vendita di articoli con movimenti lenti.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio risponde agli eventi di soglia di inventario, attivando automaticamente i messaggi di urgenza quando i livelli di scorte scendono al di sotto dei limiti definiti. Questo è lo schema corretto quando l’evento che scatena l’evento è un evento di sistema piuttosto che un comportamento del cliente e la comunicazione richiesta è immediata e reattiva piuttosto che una sequenza di acquisizione sostenuta.

### Considerazioni tecniche

- I feed di inventario devono integrarsi con la piattaforma di dati del cliente quasi in tempo reale, in modo che i messaggi di urgenza riflettano i livelli di stock effettivi anziché i dati obsoleti.
- I livelli di soglia dovrebbero essere configurati per categoria di prodotto, poiché una soglia di &quot;scorte basse&quot; per un prodotto di grande volume differisce notevolmente da una soglia per un prodotto di lusso.
- I messaggi devono essere veritieri e conformi alle normative per la protezione dei consumatori; mostrare una falsa scarsità può danneggiare la fiducia del marchio e può violare gli standard pubblicitari in alcuni mercati.
- La messaggistica in loco e i canali e-mail devono essere coordinati in modo che un cliente che ha già acquistato non continui a ricevere notifiche di urgenza per lo stesso prodotto.


## Consigli di cross-selling e upselling

Puoi visualizzare i prodotti di cross-selling e upselling pertinenti al momento del pagamento, tramite e-mail e nelle pagine dei prodotti in base ai modelli di acquisto e alle relazioni tra i prodotti. Suggerire alternative complementari o premium al momento giusto aumenta le dimensioni del carrello senza richiedere ai clienti di cercare gli articoli correlati.

### Impatto aziendale

Strategie di cross-selling e upselling ben eseguite aumentano il valore medio degli ordini e incrementano i ricavi per transazione, contribuendo a una maggiore economia generale del paniere.

### Come implementare

Utilizza il pattern [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md). Questo approccio utilizza una logica decisionale centralizzata per valutare tutte le offerte disponibili e selezionare la migliore opzione di cross-selling o upselling per ogni cliente e contesto. Questo è il modello corretto quando la selezione dell’offerta deve tenere conto delle regole di margine, disponibilità di inventario e relazione di prodotto, vincoli di business che richiedono una logica decisionale regolamentata anziché una classificazione di affinità comportamentale.

### Considerazioni tecniche

- I dati sulle relazioni tra i prodotti, comprese le associazioni &quot;frequentemente acquistati insieme&quot; e i percorsi di aggiornamento, devono essere conservati e aggiornati regolarmente per riflettere gli attuali modelli di acquisto.
- La logica di classificazione delle offerte deve tenere conto dei livelli di margine, rilevanza e inventario, in modo che le opzioni più redditizie e disponibili emergano per prime.
- I consigli di cross-selling al momento del pagamento devono essere caricati rapidamente e non interrompere il flusso di acquisto; suggerimenti lenti o intrusivi possono effettivamente ridurre la conversione.
- Le regole di decisione di [!DNL Journey Optimizer] devono includere le offerte di fallback in modo che ogni cliente idoneo riceva un consiglio, anche quando l&#39;opzione con il punteggio più alto non è disponibile.


## Nuova serie di benvenuto per i clienti

Automatizza una serie di benvenuto con più e-mail per i nuovi clienti con consigli di prodotto personalizzati, narrazione del brand e offerte speciali. Le prime interazioni dopo l’adesione di un cliente modellano la loro relazione a lungo termine con il marchio, rendendo questa serie uno dei programmi di maggiore impatto che un retailer può eseguire.

### Impatto aziendale

Una serie di benvenuto ben progettata guida un forte coinvolgimento tra i nuovi clienti e migliora in modo significativo il valore del ciclo di vita creando in anticipo l’affinità con il marchio.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Questo percorso di sviluppo multi-touch guida i nuovi clienti attraverso una sequenza di messaggi di introduzione al brand, di individuazione dei prodotti e di incentivazione, adattandosi in base al loro coinvolgimento. Questo è il modello corretto quando il caso d’uso richiede un flusso sequenziale di più messaggi nell’arco di giorni con diramazioni condizionali basate su eventi di coinvolgimento: un singolo messaggio attivato non può soddisfare la logica di dipendenza tra i passaggi.

### Considerazioni tecniche

- Il trigger di ingresso al percorso deve acquisire in modo affidabile gli eventi di creazione di nuovi clienti da tutte le origini di registrazione, inclusi web, app mobili, punti vendita in-store e mercati di terze parti.
- I passaggi di attesa tra le e-mail devono essere configurati in base ai dati di coinvolgimento; i clienti che aprono e fanno clic potrebbero ricevere il messaggio successivo prima, mentre i clienti meno coinvolti beneficiano di una maggiore spaziatura.
- I consigli sui prodotti nelle e-mail di benvenuto devono riflettere ciò che il cliente ha navigato o acquistato durante la sua prima visita, non i best-seller generici.
- I clienti che effettuano un acquisto durante la serie di benvenuto devono passare a un flusso successivo all’acquisto, anziché continuare a ricevere messaggi incentrati sull’acquisizione.


## Avvisi di riduzione prezzo

Avvisa i clienti tramite e-mail o notifica push quando i prodotti nella lista dei desideri o gli articoli visualizzati in precedenza scendono di prezzo. Gli acquirenti che hanno mostrato interesse ma non hanno acquistato sono molto reattivi alle riduzioni di prezzo, rendendo questo uno dei modi più efficienti per convertire il corrispettivo in vendite.

### Impatto aziendale

Gli avvisi di ribasso dei prezzi generano tassi di conversione più elevati tra i destinatari e aumentano in misura misurabile la soddisfazione dei clienti, aiutandoli a percepire il valore migliore.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio risponde agli eventi di cambiamento del prezzo del prodotto, confrontandoli con i segnali di interesse del cliente per fornire notifiche tempestive. Questo è il modello corretto quando il trigger è un evento di catalogo e la finestra di consegna è sensibile al tempo: un percorso sostenuto sarebbe troppo lento e non è necessario alcun follow-up a più passaggi oltre la notifica iniziale.

### Considerazioni tecniche

- Per rilevare le variazioni di prezzo è necessario confrontare i prezzi correnti con i valori precedenti nel feed del catalogo dei prodotti e attivare solo avvisi per riduzioni significative, anziché fluttuazioni minori.
- I segnali di interesse del cliente (aggiunte alla lista dei desideri, visualizzazioni delle pagine dei prodotti, tempo trascorso sulle pagine dei prodotti) devono essere memorizzati e confrontati in modo efficiente con potenziali migliaia di modifiche giornaliere dei prezzi.
- Le notifiche devono includere il prezzo originale, il nuovo prezzo e l&#39;importo dei risparmi per comunicare chiaramente il valore; messaggi vaghi di &quot;riduzione del prezzo&quot; sottoeseguono determinati callout di risparmio.
- È possibile utilizzare [!DNL Real-Time Customer Data Platform] segmenti per gli acquirenti attenti al prezzo per assegnare priorità alla consegna degli avvisi e adattare il tono di messaggistica.


## Promemoria rifornimento

Inviare promemoria automatici ai clienti per i prodotti che acquistano regolarmente, come articoli in abbonamento e materiali di consumo, per incoraggiare acquisti ripetuti prima che scadano. I promemoria proattivi riducono la possibilità che i clienti passino a un concorrente semplicemente perché hanno dimenticato di riordinare.

### Impatto aziendale

I programmi di promemoria per il rifornimento consentono di migliorare i tassi di acquisto ripetuti e la fidelizzazione dei clienti, semplificando il rifornimento dei prodotti su cui si basano.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Questo percorso pianificato ricorrente utilizza le previsioni della frequenza di acquisto per inviare promemoria nel momento ottimale prima che un cliente abbia probabilmente bisogno di una ricarica. Questo è il modello corretto quando non esiste un evento di attivazione discreto e la tempistica deve essere calcolata a partire da modelli di frequenza di acquisto che ricalibrano dinamicamente — i messaggi attivati da eventi non possono gestire gli adeguamenti predittivi di pianificazione o tempistica quando i clienti riordinano in anticipo o in ritardo.

### Considerazioni tecniche

- Il calcolo della frequenza di acquisto deve tenere conto dei diversi tassi di consumo per le varie categorie di prodotti; un promemoria per il caffè dovrebbe arrivare con una frequenza diversa da quella per i materiali per la pulizia.
- Il percorso deve modificare dinamicamente la tempistica quando un cliente riordina prima o dopo il previsto, ricalibrando il promemoria successivo in base ai dati di acquisto aggiornati.
- I promemoria devono includere un collegamento diretto per il riordino o un’opzione di riacquisto con un solo clic per ridurre al minimo l’attrito e massimizzare la conversione dalla notifica.
- I clienti che hanno già effettuato un riordine tramite un altro canale (in-store, servizio di abbonamento) devono essere eliminati per evitare di inviare promemoria irrilevanti.


## Pagine di categorie personalizzate

Personalizza dinamicamente le pagine delle categorie per mostrare i prodotti più rilevanti in base alle preferenze di ciascun cliente, agli acquisti precedenti e al comportamento di navigazione. Quando i consumatori vedono prodotti allineati con i loro gusti nella parte superiore della pagina, scoprono ciò che vogliono più velocemente e convertono a tassi più elevati.

### Impatto aziendale

Le pagine personalizzate delle categorie migliorano il coinvolgimento delle pagine delle categorie e migliorano significativamente l’individuazione dei prodotti, in particolare per i rivenditori con cataloghi di grandi dimensioni.

### Come implementare

Utilizza il pattern [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Questo approccio utilizza strategie di selezione e modelli di classificazione per riordinare i prodotti sulle pagine delle categorie in base al profilo e al comportamento in tempo reale di ogni visitatore. Questo è il modello corretto quando l’attività classifica un set di prodotti grande e aperto utilizzando segnali di affinità comportamentale; in questo caso, offer decisioning non è appropriato perché non esistono regole di idoneità o vincoli aziendali che limitano quali prodotti vengono visualizzati.

### Considerazioni tecniche

- La classificazione del prodotto deve essere eseguita abbastanza rapidamente da evitare ritardi percepiti nel caricamento delle pagine; spesso per le pagine di categorie con centinaia di prodotti è necessario ricorrere alla personalizzazione lato server o al decisioning basato su Edge.
- La logica di personalizzazione deve combinare le preferenze individuali con le regole di merchandising, garantendo che i prodotti promossi, i nuovi arrivati e gli articoli stagionali ricevano ancora la visibilità appropriata.
- Dovrebbe essere presente un’infrastruttura di test A/B per misurare su base continuativa l’impatto sui ricavi dell’ordinamento personalizzato rispetto alle regole di merchandising predefinite.
- L&#39;implementazione di [!DNL Experience Platform] Web SDK deve acquisire le interazioni delle pagine delle categorie (profondità di scorrimento, clic sul prodotto, utilizzo del filtro) per perfezionare continuamente i modelli di classificazione.


## Campagne di follow-up post-acquisto

Invia e-mail post-acquisto con suggerimenti per l’assistenza sui prodotti, suggerimenti sui prodotti correlati, richieste di revisione e informazioni sul programma fedeltà. Il periodo immediatamente successivo all’acquisto coincide con il momento in cui i clienti sono più coinvolti con il brand, rendendolo una finestra ideale per approfondire la relazione e incoraggiare attività future.

### Impatto aziendale

Le campagne post-acquisto efficaci aumentano i tassi di invio delle recensioni e aumentano i tassi di acquisto ripetuto, trasformando gli acquirenti una tantum in clienti fedeli.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Questo flusso post-acquisto in più passaggi utilizza una logica di diramazione per personalizzare i messaggi di follow-up in base al tipo di prodotto, al segmento di cliente e al coinvolgimento con le e-mail precedenti della serie. Questo è il modello corretto perché il follow-up si estende su più giorni, dipende dagli eventi di stato di evasione e dai rami in base alla categoria del prodotto e agli eventi di ritorno. Un singolo messaggio attivato non può supportare la logica condizionale richiesta nell’intera sequenza temporale successiva all’acquisto.

### Considerazioni tecniche

- Il percorso deve tenere conto dello stato di evasione dell’ordine; i suggerimenti per l’assistenza e le richieste di revisione devono essere inviati solo dopo la consegna del prodotto, non immediatamente dopo l’acquisto.
- Il contenuto specifico del prodotto (istruzioni per la cura, guide per l’uso, suggerimenti per gli accessori) richiede un sistema di mappatura del contenuto che associ ogni categoria di prodotto ai relativi materiali di follow-up.
- I tempi delle richieste di revisione devono essere ottimizzati in base alla categoria del prodotto; l’elettronica può richiedere un periodo di utilizzo più lungo prima di una revisione significativa, mentre l’abbigliamento può essere rivisto poco dopo la consegna.
- I clienti che avviano un reso o uno scambio devono essere automaticamente rimossi dal flusso standard post-acquisto e reindirizzati a un percorso di ripristino del servizio.


## Offerte esclusive per i clienti VIP

Identifica i clienti di alto valore e fornisci offerte esclusive, accesso anticipato alle vendite ed esperienze di acquisto personalizzate che premiano la loro fedeltà. Mantenere i clienti top-tier è molto più conveniente che acquistarne di nuovi, e il trattamento esclusivo rafforza la connessione emotiva che li mantiene in spesa.

### Impatto aziendale

I programmi VIP generano un forte coinvolgimento da parte dei clienti top-tier e migliorano in modo misurabile il valore del ciclo di vita del cliente riducendo l&#39;abbandono tra i segmenti più redditizi.

### Come implementare

Utilizza il Percorso [cross-channel con modello Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md). Questo approccio combina l’orchestrazione del percorso con il decisioning in tempo reale per la selezione delle offerte, garantendo a ogni cliente VIP l’offerta esclusiva più rilevante su ogni canale. Questo è il modello corretto quando il percorso deve coordinare la distribuzione tra i canali per evitare offerte duplicate e quando la selezione delle offerte richiede regole di idoneità e vincoli di business. L’orchestrazione in più passaggi non fornisce da sola il livello di decisione in tempo reale necessario per determinare quale offerta esclusiva riceve ogni VIP.

### Considerazioni tecniche

- I criteri di segmentazione di VIP devono essere chiaramente definiti utilizzando le metriche di attualità, frequenza e valore monetario; i segmenti devono essere aggiornati con frequenza tale da acquisire i clienti che si sono recentemente qualificati o non qualificati.
- Le offerte esclusive devono essere applicate al momento del rimborso (web, app, store) per impedire ai clienti non VIP di accedervi, il che richiede l’integrazione con i sistemi di promozione e di prezzo.
- Le preferenze di canale variano notevolmente tra i clienti di alto valore; alcuni preferiscono la posta elettronica, altri rispondono alle notifiche dell’app o alla direct mailing, pertanto il percorso dovrebbe adattare i canali di consegna in base al coinvolgimento passato.
- Le decisioni di [!DNL Journey Optimizer] devono coordinarsi tra i canali per evitare che un cliente VIP riceva la stessa offerta simultaneamente tramite e-mail, push e SMS.


## Notifiche esaurite

Consenti ai clienti di registrarsi per ricevere notifiche quando i prodotti esauriti diventano disponibili, quindi di inviargli automaticamente una notifica tramite e-mail o messaggio di testo. L&#39;acquisizione della domanda di prodotti non disponibili impedisce la perdita delle vendite e offre ai clienti un motivo per tornare al negozio piuttosto che acquistare da un concorrente.

### Impatto aziendale

Le notifiche back-in-stock ottengono forti tassi di conversione tra gli abbonati e riducono in modo significativo le vendite perse per i prodotti ad alta domanda che sperimentano stockout temporanei.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio attiva le notifiche sugli eventi di back-in-stock, abbinando gli aggiornamenti di inventario alle iscrizioni alle notifiche dei clienti per inviare avvisi tempestivi. Questo è il modello corretto perché il trigger è un evento di sistema di inventario discreto, la consegna è critica in termini di tempo (l’inventario può essere venduto di nuovo rapidamente) e la comunicazione è una singola notifica anziché un percorso continuo.

### Considerazioni tecniche

- Il monitoraggio dell’inventario deve rilevare rapidamente gli eventi di riassortimento; ritardi anche di poche ore possono comportare nuovamente la vendita del prodotto prima che i clienti avvisati abbiano la possibilità di effettuare l’acquisto.
- Quando un prodotto popolare viene rifornito in quantità limitata, le notifiche devono essere scaglionate o classificate in base alla data di registrazione per evitare di inviare avvisi a più clienti di quanti ne possa servire l’inventario disponibile.
- Il meccanismo di abbonamento alle notifiche deve acquisire le preferenze del canale (e-mail o messaggio di testo) e soddisfare i requisiti di consenso per ciascun canale, in particolare per gli SMS.
- Gli attributi del profilo [!DNL Real-Time Customer Data Platform] devono tenere traccia dei prodotti che ogni cliente sta guardando in modo che le notifiche duplicate non vengano ripetute se lo stesso prodotto viene rifornito più volte.


## Personalization per bozza social

Visualizza una bozza social personalizzata, incluse recensioni, valutazioni e suggerimenti &quot;I clienti che hanno acquistato questo hanno acquistato anche&quot;, in base al profilo e alle preferenze di ciascun cliente. Personalizzare la bozza social per riflettere le esperienze di clienti simili genera fiducia in modo più efficace rispetto ai soli rating generici.

### Impatto aziendale

La bozza sociale personalizzata aumenta i tassi di conversione e migliora la fiducia dei consumatori, in particolare per i nuovi acquirenti e i prodotti a prezzi più elevati in cui l’esitazione di acquisto è maggiore.

### Come implementare

Utilizza il pattern [Visitatore noto Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md). Questo approccio personalizza i contenuti web per i visitatori identificati, selezionando le recensioni più rilevanti e gli elementi di prova social in base al profilo, alle preferenze e al contesto di navigazione del cliente. Questo è il modello giusto quando la personalizzazione è guidata dagli attributi di profilo e dall’appartenenza a un segmento anziché da un modello di affinità comportamentale. I consigli comportamentali non sono appropriati in questo caso perché la selezione della bozza social dipende da chi è il cliente, non dagli elementi che ha navigato.

### Considerazioni tecniche

- I dati di revisione e valutazione devono essere strutturati e contrassegnati dagli attributi del cliente (come contesto di acquisto, segmento di cliente e caso di utilizzo del prodotto) per consentire un filtraggio e una personalizzazione significativi.
- Gli elementi di prova social devono essere caricati in modo asincrono per evitare di bloccare il rendering della pagina del prodotto principale, in quanto i dati di revisione possono provenire da una piattaforma di revisione di terze parti con tempi di risposta variabili.
- Le normative sulla privacy richiedono che tutti i dati dei clienti utilizzati per far corrispondere le recensioni ai visitatori vengano gestiti in base alle preferenze di consenso; la visualizzazione di contenuti &quot;piacenti ai clienti&quot; implica la profilazione che può richiedere la divulgazione.
- L&#39;iscrizione al pubblico di [!DNL Experience Platform] può essere utilizzata per selezionare le recensioni da evidenziare, mostrando le recensioni degli appassionati di outdoor di altri acquirenti piuttosto che le recensioni generiche più votate.


## IA Product Advisor

I retailer online trasportano migliaia di SKU su gerarchie di categorie complesse, rendendo difficile per gli acquirenti trovare il prodotto giusto senza effettuare ricerche estese o abbandonate. Un consulente di prodotto basato sull’intelligenza artificiale coinvolge gli acquirenti in un dialogo naturale a più turni, ponendo domande mirate su esigenze, preferenze e budget, quindi limita l’assortimento a un set curato di consigli personalizzati. L’esperienza rispecchia le indicazioni che un esperto interno al negozio potrebbe fornire, su scala digitale.

### Impatto aziendale

I rivenditori che utilizzano il rilevamento guidato delle conversazioni vedono tassi di conversione e valore medio dell’ordine migliorati rispetto alla navigazione non assistita, riducendo al contempo i resi dei prodotti attraverso decisioni di acquisto più informate.

### Come implementare

Utilizza il pattern [Esperienza conversazionale di Brand Concierge](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md). Questo approccio distribuisce Product Advisor Agent rispetto a un catalogo di prodotti strutturato, utilizzando AEP Agent Orchestrator e i dati del profilo cliente in tempo reale per generare consigli di prodotti personalizzati e sicuri per il brand attraverso un dialogo naturale. Questo è lo schema corretto quando l’obiettivo è il discovery conversazionale interattivo a più turni guidato dalle esigenze dichiarate dal cliente, distinto dalla messaggistica attivata dagli eventi, unidirezionale e reattiva a un’azione specifica, e dalle esperienze web personalizzate, che mostrano i consigli in modo passivo anziché coinvolgere i clienti nella conversazione. Richiede la configurazione di AEP Agent Orchestrator e della governance del brand.

### Considerazioni tecniche

- Il catalogo dei prodotti deve essere strutturato con dati di attributi completi, tra cui dimensioni, materiale, compatibilità, disponibilità e prezzi, in quanto i consigli di Product Advisor Agent sono basati sul contenuto del catalogo e non possono fornire consigli affidabili sui prodotti con attributi incompleti.
- La ricerca del profilo cliente in tempo reale tramite RT-CDP deve essere configurata con attivazione Edge in modo che la cronologia degli acquisti, il comportamento di navigazione e i dati del livello fedeltà siano accessibili durante la conversazione in tempo reale senza latenza che potrebbe interrompere l’esperienza.
- È necessario definire guardrail per la governance del brand per specificare in che modo l’agente gestisce articoli esauriti, confronti tra prodotti competitivi, dichiarazioni sui prezzi promozionali e argomenti vietati, garantendo che ogni risposta sia allineata agli standard del marchio per la vendita al dettaglio.
- Gli eventi conversazionali, inclusi segnali di intento, interazioni di prodotto e accettazione di consigli, devono essere acquisiti come ExperienceEvents XDM e inviati in streaming ad AEP, arricchendo i profili dei clienti con dati di affinità di prodotto che migliorano la personalizzazione futura su tutti i canali.


## Analisi attribuzione cross-channel

Misura in che modo ogni punto di contatto di marketing (ricerca a pagamento, e-mail, promozioni social e in-store) contribuisce alle conversioni di acquisto online e offline. I retailer che si affidano all’attribuzione last-touch sottovalutano sistematicamente i canali funnel superiori e prendono decisioni sull’allocazione del budget in base a un’immagine incompleta del percorso di acquisto.

### Impatto aziendale

I team di marketing al dettaglio che passano dall’attribuzione &quot;ultimo contatto&quot; a quella &quot;multi-touch&quot; hanno una visione più chiara dei canali che determinano le intenzioni di acquisto, con decisioni di budget più informate e un maggiore ritorno sulla spesa di marketing.

### Come implementare

Utilizza il pattern [Customer Analytics &amp; Insight Generation](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md). Questo approccio collega i dati degli eventi online e offline (clic web, impegni e-mail, transazioni fedeltà e record dei punti vendita) a Customer Journey Analytics, dove è possibile configurare e confrontare modelli di attribuzione lungo l’intero percorso di acquisto. Questo è lo schema corretto quando l’obiettivo è la misurazione e la generazione di insight in un percorso complesso e multicanale, anziché attivare tipi di pubblico o attivare messaggi, e quando l’analisi richiede Customer Journey Analytics anziché uno strumento CDP o di orchestrazione delle campagne.

### Considerazioni tecniche

- I dati delle transazioni nei punti vendita e e-commerce devono condividere un identificatore coerente del cliente in modo che le conversioni in negozio e online possano essere unite in un’unica vista cross-channel in CJA.
- Nella visualizzazione dati di CJA è necessario configurare più modelli di attribuzione: primo contatto, ultimo contatto, lineare e decadimento nel tempo, in modo che gli analisti possano confrontarli uno accanto all’altro senza dover ricreare l’analisi.
- Per includere i canali a pagamento nel percorso di attribuzione insieme ai canali di proprietà, è necessario acquisire le impression multimediali a pagamento e i dati di clic da piattaforme di annunci esterne tramite connettori di origine o caricamenti batch.
- È necessario definire finestre di conversione e periodi di lookback del credito per tipo di canale, in quanto l’intervallo di attribuzione rilevante per un clic di ricerca a pagamento differisce in modo significativo da quello di una campagna e-mail stagionale.

## Segmentazione del pubblico e attivazione per contenuti multimediali a pagamento

Crea segmenti di pubblico di alto valore da profili cliente unificati e attivali su destinazioni di media a pagamento come Google Ads, Meta e The Trade Desk per campagne di acquisizione e retargeting. L’unificazione dei dati comportamentali, transazionali e sulla fedeltà consente un targeting più preciso che riduce gli sprechi e le spese pubblicitarie e migliora il ritorno sull’investimento delle campagne.

### Impatto aziendale

I retailer che attivano pubblici di prime parti di alta qualità vedono percentuali di corrispondenza migliori sulle piattaforme a pagamento, costo per acquisizione ridotto e maggiore ritorno sulla spesa pubblicitaria rispetto ai segmenti di terze parti.

### Come implementare

Utilizza il pattern [Audience Activation to Destinations](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md) per valutare l&#39;iscrizione del pubblico rispetto ai profili unificati e pubblicare segmenti in destinazioni di contenuti multimediali a pagamento connesse in base a pianificazione o streaming. Questo è il modello corretto quando il requisito principale è la pubblicazione dei segmenti su sistemi esterni, anziché la messaggistica orchestrata o le decisioni in tempo reale.

### Considerazioni tecniche

- La risoluzione delle identità nei dati web, mobili e di fidelizzazione è necessaria per creare profili cliente completi prima dell’attivazione: i profili frammentati riducono la qualità del pubblico e le percentuali di corrispondenza.
- I connettori di destinazione devono essere configurati per ogni piattaforma di media a pagamento, con i flag di consenso appropriati rispettati a livello di profilo per impedire l’attivazione di dati non consentiti.
- La frequenza di aggiornamento del segmento deve essere allineata con gli obiettivi della campagna: i tipi di pubblico di acquisizione possono richiedere aggiornamenti giornalieri, mentre i tipi di pubblico di retargeting possono beneficiare di aggiornamenti in tempo quasi reale per escludere acquirenti recenti.
- L’analisi di sovrapposizione tra i tipi di pubblico di acquisizione e di mantenimento consente di evitare la contaminazione incrociata nel caso in cui i clienti esistenti ricevano messaggi di acquisizione di nuovi clienti.


## Soppressione dei clienti per le campagne di acquisizione

Elimina i clienti esistenti e i convertitori recenti dall&#39;acquisizione e dalla spesa attivando i tipi di pubblico di esclusione in destinazioni di media a pagamento, riducendo gli sprechi di spesa. La sincronizzazione continua degli elenchi di soppressione assicura che i budget a pagamento siano destinati a potenziali clienti nuovi anziché a persone che si sono già convertite o che sono attivamente coinvolte.

### Impatto aziendale

Eliminare i clienti esistenti dalle campagne di acquisizione riduce la spesa per i supporti a pagamento sprecati, migliora il costo per le metriche di acquisizione e impedisce ai clienti esistenti di ricevere messaggi irrilevanti per la fase della relazione.

### Come implementare

Utilizza il pattern [Audience Activation to Destinations](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md) per pubblicare su una pianificazione frequente tipi di pubblico di esclusione (acquirenti recenti, abbonati attivi, clienti di alto valore) su ogni destinazione di media a pagamento. Questo è il pattern corretto quando l’obiettivo è la pubblicazione dei segmenti per l’eliminazione anziché orchestrare un percorso rivolto al cliente.

### Considerazioni tecniche

- I tipi di pubblico di eliminazione richiedono una chiara definizione di chi escludere, in genere clienti che hanno acquistato negli ultimi 30-90 giorni, membri fedeltà attivi e conversioni di e-mail recenti.
- Gli elenchi di esclusione devono essere aggiornati con una frequenza tale da escludere gli acquirenti prima che gli annunci vengano distribuiti; elenchi di soppressione obsoleti causano l’attrito più marcato nei periodi di vendita al dettaglio di grandi volumi.
- La qualità della corrispondenza delle identità influisce direttamente sulla precisione dell’eliminazione: una scarsa corrispondenza di e-mail o ID dispositivo farà sì che i clienti esistenti continuino a visualizzare annunci di acquisizione.
- Assicurati che i tipi di pubblico per l’eliminazione siano distinti da quelli per la fidelizzazione, in modo che le campagne di recupero possano comunque raggiungere i clienti inattivi che non devono essere eliminati.


## Esperienze web personalizzate per visitatori noti

Distribuisci banner hero personalizzati, consigli di prodotto e contenuti promozionali ai visitatori autenticati del sito web in base al loro profilo in tempo reale, all’iscrizione al segmento e alla cronologia comportamentale. Quando i clienti di ritorno vedono esperienze personalizzate in base al loro stato di fedeltà, alla cronologia degli acquisti e alle preferenze, i tassi di coinvolgimento e la conversione migliorano notevolmente rispetto alle esperienze homepage generiche.

### Impatto aziendale

I rivenditori che personalizzano per i visitatori noti vedono un miglioramento significativo nelle metriche di coinvolgimento, tra cui il tempo sul sito, le pagine per sessione e il tasso di conversione, con il maggiore impatto tra i membri fedeltà che visitano frequentemente.

### Come implementare

Utilizza il pattern [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) per fornire esperienze personalizzate basate sul profilo al caricamento della pagina utilizzando l&#39;appartenenza al segmento in tempo reale e gli attributi del profilo. Questo è il modello giusto quando l’esperienza deve essere guidata da dati di profilo collegati all’identità anziché da segnali di sola sessione e quando le decisioni sui contenuti non richiedono una classificazione delle offerte complessa o vincoli di business.

### Considerazioni tecniche

- Prima di poter attivare la personalizzazione basata sul profilo, è necessario eseguire l’autenticazione; il sito web necessita di un meccanismo per identificare il visitatore e risolvere il suo ECID in un profilo noto.
- Le ricerche di profilo in tempo reale devono essere completate entro il budget di latenza per il caricamento della pagina, in genere richiedendo una valutazione del profilo implementato edge anziché chiamate API lato server sul percorso di rendering critico.
- Le varianti di contenuto devono essere progettate per tutti i segmenti di pubblico di destinazione, inclusa un’esperienza predefinita per i visitatori che non corrispondono a nessuna regola di personalizzazione.
- Le decisioni di Personalization devono essere registrate per l’analisi, consentendo test A/B delle varianti di contenuto e l’attribuzione di miglioramenti del coinvolgimento a segmenti specifici.


## Personalization Web visitatore anonimo

Personalizza i contenuti per i visitatori non identificati del sito web utilizzando segnali comportamentali durante la sessione come pagine visualizzate, categorie di prodotti visualizzate e sorgenti di riferimento. Poiché la maggior parte del traffico web di vendita al dettaglio è anonimo, la personalizzazione per visitatori non riconosciuti espande notevolmente la portata della personalizzazione nel sito oltre il segmento autenticato.

### Impatto aziendale

I retailer che forniscono esperienze personalizzate a visitatori anonimi hanno riscontrato un miglioramento nei tassi di coinvolgimento e conversione della prima visita, con un impatto particolarmente forte sui visitatori in arrivo da fonti specifiche di campagne o che navigano su pagine di categorie a forte intento.

### Come implementare

Utilizza il pattern [Visitatore anonimo Web Personalization](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md) per valutare i segnali comportamentali nella sessione al perimetro e fornire varianti di contenuto rilevanti senza richiedere l&#39;autenticazione. Questo è il modello corretto quando la personalizzazione deve funzionare immediatamente dalla prima interazione senza affidarsi a un profilo persistente, in particolare per il traffico di acquisizione e per i visitatori che non hanno ancora effettuato l’accesso.

### Considerazioni tecniche

- La personalizzazione in sessione si basa sui dati degli eventi in streaming raccolti tramite Edge Network; le regole di valutazione edge devono essere distribuite e testate prima di inviare il traffico.
- Le varianti di contenuto devono essere progettate in base a comportamenti di sessione ad alto segnale (sorgente di riferimento, prima pagina visualizzata, categoria di prodotto esaminata), anziché in base ad attributi a basso segnale che non consentono di prevedere in modo affidabile l’intento.
- I requisiti di privacy devono essere valutati attentamente; in alcune giurisdizioni la personalizzazione comportamentale richiede il consenso anche per i visitatori anonimi.
- Le regole di Personalization per i visitatori anonimi devono essere più semplici e veloci da valutare rispetto alle regole per i visitatori noti, in quanto i vincoli di latenza edge sono più rigidi.


## Percorso serie di benvenuto

Organizza un percorso di benvenuto in più fasi per i nuovi clienti registrati, che fornisce contenuti di onboarding, formazione sui prodotti e un incentivo per il primo acquisto su canali e-mail e push. Una serie di benvenuto ben progettata imposta il tono per la relazione con il cliente e aumenta significativamente la probabilità che un nuovo dichiarante si converta al loro primo acquisto.

### Impatto aziendale

I programmi della serie Welcome consentono di ottenere miglioramenti significativi nei tassi di attivazione dei nuovi clienti e nella conversione al primo acquisto, con un impatto maggiore quando la serie combina contenuti educativi con un incentivo tempestivo e personalizzato.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) per progettare una sequenza di onboarding di più giorni con passaggi di attesa, diramazioni del canale in base al coinvolgimento ed eliminazione al raggiungimento del primo obiettivo di acquisto. Questo è il modello corretto quando il caso d’uso richiede un flusso di comunicazione sequenziale e spaziato nel tempo con logica condizionale: un singolo messaggio attivato non è sufficiente per guidare un nuovo cliente attraverso l’esperienza di onboarding.

### Considerazioni tecniche

- L’ingresso nel percorso deve essere attivato da eventi di registrazione dell’account in tempo reale, in modo che il primo messaggio di benvenuto arrivi immediatamente mentre l’intento di registrazione è elevato.
- Il percorso deve includere condizioni di uscita che eliminino i messaggi rimanenti quando un nuovo cliente completa il primo acquisto; continuare la serie di benvenuto dopo l’acquisto mina la rilevanza del messaggio.
- La preferenza per il canale deve essere rispettata in tutto; i passaggi di notifica push richiedono l’installazione dell’app e il consenso push, con fallback delle e-mail per i clienti senza consenso.
- Personalization nella serie welcome migliora la conversione ma richiede un numero sufficiente di dati di profilo per essere significativi: i nuovi profili spesso richiedono un fallback su bestseller o prodotti di tendenza.


## Ripristino dell&#39;abbandono del carrello

Attiva notifiche e-mail e push in tempo reale quando un cliente abbandona il carrello, con promemoria di prodotto personalizzati e incentivi limitati nel tempo per completare l’acquisto. L’abbandono del carrello è uno dei casi di utilizzo con il ROI più elevato nel settore retail, in quanto consente di recuperare i ricavi da clienti che hanno già dimostrato una forte intenzione di acquisto.

### Impatto aziendale

I programmi di abbandono del carrello ben eseguiti recuperano una quota significativa di ricavi abbandonati, con tassi di recupero più elevati quando il primo messaggio arriva entro un’ora dall’abbandono e include gli elementi esatti rimasti nel carrello.

### Come implementare

Utilizza il pattern [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) per rispondere all&#39;evento di abbandono del carrello con una comunicazione attivata immediatamente mentre l&#39;intento di acquisto è ancora attivo. Si tratta del modello corretto quando l’evento scatenante è un’azione discreta del cliente e il requisito principale è una risposta tempestiva e personalizzata, anziché una sequenza di sviluppo di più settimane o decisioni di offerta complesse con vincoli aziendali.

### Considerazioni tecniche

- Il rilevamento dell’abbandono del carrello richiede una soglia di inattività definita (in genere 30-60 minuti) per evitare di inviare messaggi ai clienti che stanno ancora navigando o completando attivamente il flusso di pagamento.
- Il contenuto dell’e-mail deve riprodurre dinamicamente le immagini, i prezzi e lo stato dell’inventario correnti al momento dell’invio, in quanto gli articoli possono andare in vendita o cambiare prezzo tra l’abbandono e la consegna dei messaggi.
- La logica di soppressione deve escludere i clienti che hanno completato l’acquisto tramite un altro canale tra il rilevamento dell’abbandono e l’invio di messaggi.
- Le regole per il limite di frequenza dovrebbero evitare messaggi di abbandono del carrello in finestre brevi, in particolare per i clienti che abbandonano abitualmente i carrelli come comportamento di navigazione.


## Percorso di coinvolgimento post-acquisto

Fornisci comunicazioni post-acquisto, tra cui conferma degli ordini, aggiornamenti delle spedizioni, raccomandazioni di cross-selling e richieste di revisione attraverso un percorso orchestrato in più passaggi. La fase di post-acquisto rappresenta uno dei momenti di maggior coinvolgimento nel ciclo di vita del cliente, rendendolo un momento ideale per fidelizzare i clienti e introdurre prodotti complementari pertinenti.

### Impatto aziendale

I rivenditori con percorsi strutturati post-acquisto vedono tassi di acquisto ripetuti e tassi di invio delle recensioni dei clienti migliorati, contribuendo alla fidelizzazione a lungo termine e alla prova sociale che supporta l’acquisizione futura.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) per orchestrare una sequenza di comunicazioni post-acquisto programmate per le principali attività cardine: conferma ordine, spedizione, consegna e follow-up post-consegna. Questo è il modello corretto quando il caso d’uso si estende su più giorni con più obiettivi: un singolo messaggio attivato non può contenere l’arco dalla conferma transazionale alla creazione di fidelizzazione per rivedere la richiesta.

### Considerazioni tecniche

- L’integrazione del sistema di gestione degli ordini è necessaria per ricevere eventi di acquisto e spedizione in tempo reale; i ritardi nell’acquisizione degli eventi creano tempi imbarazzanti nelle comunicazioni post-acquisto.
- I consigli di vendita incrociata nella sequenza post-acquisto richiedono dati del catalogo dei prodotti in tempo reale e l’inferenza del modello di consigli al momento del rendering dei messaggi per riflettere l’inventario e i prezzi correnti.
- I messaggi di richiesta di revisione devono essere conformi ai termini di servizio della piattaforma per le revisioni incentivate e devono essere temporizzati dopo che il cliente ha avuto tempo sufficiente per utilizzare il prodotto.
- Il coordinamento dei canali è importante: i clienti non devono ricevere e-mail e messaggi push per la stessa milestone a meno che non abbiano contattato il primo canale.


## Campagna di aggiornamento livello fedeltà

Identifica i clienti che si avvicinano alle soglie del livello di fedeltà e distribuisci campagne mirate che li incoraggiano a raggiungere il livello successivo con offerte personalizzate in base alla cronologia e alle preferenze di acquisto. Quando i clienti sono a portata di un aggiornamento di livello, la messaggistica mirata con incentivi personalizzati crea un’urgenza e determina un comportamento di acquisto incrementale.

### Impatto aziendale

Le campagne di aggiornamento del livello fedeltà incrementano il volume degli acquisti e migliorano il coinvolgimento del programma, con il maggiore impatto tra i membri del livello intermedio che si avvicinano alla soglia successiva e hanno mostrato un’attività di acquisto recente.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) per creare una campagna di prossimità a livello che entra nei clienti quando raggiungono una soglia di spesa definita al di sotto del livello successivo e li guida attraverso una sequenza di messaggi di benefit e offerte di incentivi. Questo è il modello corretto quando il caso d’uso richiede il monitoraggio di un attributo di profilo calcolato nel tempo e l’orchestrazione di una campagna con più passaggi collegata all’avanzamento del cliente verso un obiettivo.

### Considerazioni tecniche

- I dati della piattaforma fedeltà, come il saldo dei punti, lo stato dei livelli e le soglie dei livelli, devono essere acquisiti e mantenuti aggiornati nel profilo del cliente in modo che i calcoli di prossimità dei livelli siano accurati.
- Le campagne di aggiornamento di livello devono essere eliminate per i clienti che hanno già raggiunto il livello di destinazione o il cui stato di fedeltà è cambiato dall’ingresso della campagna.
- Gli incentivi personalizzati nella campagna di aggiornamento dovrebbero essere limitati alle offerte per le quali il cliente è effettivamente idoneo e che non compromettono il valore percepito della struttura a livello.
- La campagna deve includere chiare condizioni di uscita per i clienti che completano l’aggiornamento a metà percorso, passando a un messaggio di congratulazioni anziché continuare la sequenza di persuasione.


## Orchestrazione di campagne cross-channel

Orchestrazione di campagne di marketing coordinate tra e-mail, SMS, push e canali web con ramificazioni di percorso, passaggi di attesa e limiti di frequenza per massimizzare il coinvolgimento senza affaticamento. L’orchestrazione cross-channel coordinata garantisce che i clienti ricevano un’esperienza di campagna coerente, indipendentemente dal canale a cui rispondono per primo, eliminando la messaggistica duplicata e le offerte in conflitto.

### Impatto aziendale

I rivenditori con funzionalità di orchestrazione cross-channel riscontrano tassi di coinvolgimento e conversione più elevati rispetto alle campagne single-channel, riducendo nel contempo i tassi di annullamento dell’abbonamento dovuti all’eccesso di comunicazioni non coordinate dovuto al canale.

### Come implementare

Utilizza il pattern [Cross-Channel Percorsi with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) per creare campagne che indirizzano i clienti attraverso sequenze di canali personalizzate in base alla cronologia del coinvolgimento, alle preferenze dei canali e ai segnali di risposta in tempo reale. Questo è il modello corretto quando la campagna richiede la selezione delle offerte gestite, il routing delle preferenze del canale e la ramificazione dinamica in base al coinvolgimento nel percorso, anziché una sequenza fissa inviata a tutti i destinatari della campagna.

### Considerazioni tecniche

- I limiti di frequenza globali devono essere configurati su tutti i canali per evitare che i clienti ricevano comunicazioni eccessive quando più percorsi sono in esecuzione simultaneamente.
- I dati delle preferenze del canale devono essere correnti e fruibili: i profili di preferenza obsoleti da mesi indirizzeranno i clienti verso canali con cui non interagiscono più.
- La logica di orchestrazione del percorso deve gestire il reinserimento in modo agevole, impedendo ai clienti di accedere due volte alla stessa campagna e garantendo al contempo che non siano esclusi da campagne realmente nuove.
- I segnali di coinvolgimento in tempo reale (aperture di e-mail, clic sui collegamenti, sessioni web) devono rientrare nel percorso per abilitare la commutazione del canale e l’uscita anticipata per i clienti che si sono già convertiti.


## Esperienza conversazionale Brand Concierge

Distribuisci un agente conversazionale basato sull’intelligenza artificiale e sicuro per il brand in tutte le proprietà digitali per fornire assistenza personalizzata sui prodotti, aiuto nella navigazione del sito e trasferimento senza soluzione di continuità agli agenti live. Un concierge di IA in loco estende il servizio personalizzato su larga scala, aiutando gli acquirenti a scoprire i prodotti, confrontare le opzioni e completare gli acquisti senza richiedere l’intervento di un agente umano per le query più comuni.

### Impatto aziendale

I rivenditori con funzionalità di consulenza AI segnalano tassi di risoluzione self-service migliorati, una riduzione del volume di supporto in entrata per le domande relative a prodotti e navigazione e una maggiore conversione tra i clienti che si impegnano con indicazioni conversazionali prima dell’acquisto.

### Come implementare

Utilizza il pattern [Esperienza conversazionale di Brand Concierge](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md) per distribuire un agente di intelligenza artificiale gestito basato sui dati del catalogo dei prodotti, sulle linee guida del brand e sul contesto del profilo cliente in tempo reale. Questo è il pattern corretto quando il caso d’uso richiede un’interazione in linguaggio naturale su un set di prodotti ampio e dinamico, anziché un chatbot basato su script con intenti fissi o un pattern che corrisponde a un canale specifico come l’e-mail.

### Considerazioni tecniche

- L’agente di IA deve basarsi sui dati correnti del catalogo dei prodotti, tra cui descrizioni, specifiche, disponibilità e prezzi, per fornire indicazioni accurate; dati di prodotto non aggiornati portano a consigli errati.
- Le protezioni per la sicurezza del marchio devono essere configurate in modo da impedire che l&#39;agente discuta di prodotti della concorrenza, prenda impegni di prezzo in conflitto con le promozioni o risponda a domande non correlate.
- La logica di handoff per gli agenti live richiede l’integrazione con la piattaforma di servizio e deve essere attivata quando l’agente di intelligenza artificiale non è in grado di risolvere la query del cliente dopo un numero definito di turni.
- L’integrazione dei dati del profilo consente all’agente di personalizzare le risposte in base alla cronologia degli acquisti e allo stato di fedeltà, ma è necessaria la risoluzione dell’identità prima dell’inizio della sessione di conversazione.

## Promemoria per il check-in con App Download CTA

Ricordate agli ospiti di effettuare il check-in e incoraggiateli a scaricare l&#39;app per accedere facilmente alle informazioni. I promemoria di check-in tempestivi, insieme alle richieste di download dell’app, stimolano il coinvolgimento dei dispositivi mobili e consentono esperienze in-site più ricche.

### Impatto aziendale

I rivenditori che combinano i promemoria di check-in con le chiamate all’azione per il download dell’app possono vedere tassi di adozione delle app più elevati e un maggiore coinvolgimento in negozio, in quanto i clienti che utilizzano l’app mobile tendono ad interagire più frequentemente con promozioni e contenuti in eventi.

### Come implementare

Utilizza il pattern [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) per attivare un promemoria di archiviazione con il download dell&#39;app CTA in base ai dati di partecipazione agli eventi o prenotazione. Questo è il modello corretto quando un singolo messaggio tempestivo deve essere inviato in risposta a un evento noto o a un trigger di pianificazione.

### Considerazioni tecniche

- I promemoria di check-in devono essere temporizzati in modo appropriato rispetto alla data dell’evento o della visita, in modo da massimizzare il coinvolgimento senza essere percepiti come troppo presto o troppo tardi.
- I collegamenti profondi per il download dell’app devono essere indirizzati all’app store corretto in base alla piattaforma del dispositivo del cliente (iOS o Android).
- I clienti che hanno già installato l’app devono ricevere un’altra variante di messaggio che salta il download di CTA e si concentra sulla funzionalità di archiviazione.

## Campagne di compleanno per i fan

Scegli i fan per il loro compleanno con un messaggio di compleanno personalizzato e un’offerta esclusiva. Le campagne di compleanno creano connessioni emotive con i fan e stimolano gli acquisti incrementali attraverso un’attività di sensibilizzazione tempestiva e personalizzata.

### Impatto aziendale

Le campagne di compleanno offrono costantemente tassi di apertura e conversione superiori alla media perché arrivano in un momento di importanza personale, creando buona volontà e incoraggiando i fan a trattarsi con un acquisto speciale.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) per inviare un messaggio personalizzato di compleanno quando arriva la data di compleanno del cliente. Questo è il pattern corretto quando un singolo messaggio basato su eventi viene inviato in base a un trigger di data dell’attributo del profilo.

### Considerazioni tecniche

- La data di compleanno deve essere acquisita nel profilo cliente e convalidata per evitare di inviare messaggi in date errate.
- Le offerte devono avere un intervallo di validità definito (ad esempio la settimana di compleanno) per creare un’urgenza e al tempo stesso dare ai clienti un tempo ragionevole per il riscatto.
- I fan senza un compleanno sul file devono essere esclusi dalla campagna anziché inviare un messaggio generico.

## Campagne di compleanno per gli acquirenti

Puoi indirizzare agli acquirenti il giorno del loro compleanno con un messaggio di compleanno personalizzato e un’offerta esclusiva. Le campagne di compleanno creano brand loyalty riconoscendo i clienti personalmente e incoraggiando un acquisto celebrativo.

### Impatto aziendale

Le offerte di compleanno personalizzate spingono a tassi di rimborso più elevati rispetto alle promozioni generiche perché si allineano con un momento in cui gli acquirenti sono già inclini a fare acquisti discrezionali per se stessi.

### Come implementare

Utilizza il pattern [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) per attivare un messaggio e un&#39;offerta di compleanno in base all&#39;attributo di profilo della data di nascita dell&#39;acquirente. Questo è il modello corretto quando un singolo messaggio personalizzato deve essere consegnato in una data di calendario specifica associata al profilo del cliente.

### Considerazioni tecniche

- La data di compleanno deve essere memorizzata come attributo di profilo e deve essere raccolta durante la registrazione o l&#39;iscrizione fedeltà.
- Nella personalizzazione delle offerte, è necessario tenere conto della cronologia e delle preferenze di acquisto del cliente per presentare suggerimenti di prodotto pertinenti insieme allo sconto di compleanno.
- La logica di soppressione duplicata è necessaria per i clienti che appaiono in più sistemi per evitare di inviare più messaggi di compleanno.

## Campagne di promozione Game Day

Scegli i fan per acquistare i biglietti per un gioco imminente con promozioni e offerte personalizzate. Le promozioni dei giorni di gioco stimolano la vendita dei biglietti raggiungendo il pubblico giusto con messaggi tempestivi e specifici per eventi.

### Impatto aziendale

Le promozioni mirate per le giornate di gioco migliorano le tariffe di vendita dei biglietti raggiungendo i tifosi con offerte pertinenti in base alle preferenze del loro team, alla frequenza passata e alla vicinanza alla sede.

### Come implementare

Utilizza il pattern [Batch Outbound Message Activation](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) per inviare messaggi promozionali ai tipi di pubblico di fan segmentati prima dei prossimi giochi. Questo è il modello corretto quando un batch di messaggi personalizzati deve essere inviato a un segmento di pubblico predefinito su base pianificata.

### Considerazioni tecniche

- I dati di pianificazione dei giochi devono essere integrati per attivare le promozioni al lead time giusto prima di ogni evento.
- La segmentazione del pubblico deve tenere conto dell’affinità tra team, della prossimità geografica e dei pattern di frequenza passati per massimizzare la rilevanza.
- I clienti che hanno già acquistato i biglietti per il gioco in promozione devono essere esclusi dai messaggi di acquisizione e possono ricevere offerte di upselling per aggiornamenti o componenti aggiuntivi.

## Campagne di promozione dei prodotti

Puoi indirizzare l’acquisto ai clienti, per promuovere i prodotti durante la campagna. Le campagne promozionali incrementano i ricavi collegando i clienti giusti con offerte tempestive allineate alle promozioni attive.

### Impatto aziendale

Le campagne mirate di promozione dei prodotti superano le promozioni di ampia portata, poiché si concentrano sui clienti che hanno maggiori probabilità di essere convertiti, riducendo gli sprechi promozionali e migliorando il ritorno sulle spese di marketing.

### Come implementare

Utilizza il pattern [Batch Outbound Message Activation](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) per inviare messaggi promozionali a segmenti di pubblico qualificati durante le finestre attive della campagna. Questo è il modello corretto quando un batch pianificato di messaggi promozionali personalizzati deve raggiungere un pubblico definito durante una campagna con limiti di tempo.

### Considerazioni tecniche

- Le date di inizio e fine della promozione devono essere gestite in modo da garantire che i messaggi vengano inviati solo durante la finestra di promozione attiva.
- La segmentazione del pubblico dovrebbe sfruttare la cronologia degli acquisti, il comportamento di navigazione e l’affinità di prodotto per rivolgersi agli acquirenti che hanno più probabilità di utilizzare i prodotti promossi.
- Per evitare spossatezza promozionale, è necessario applicare un limite di frequenza, soprattutto quando vengono eseguite più campagne contemporaneamente.

## Abbandono carrello

Coinvolgi nuovamente i clienti che abbandonano il carrello con promemoria personalizzati e incentivi per completare l’acquisto. Il recupero dell’abbandono del carrello è uno dei casi di utilizzo con il ROI più elevato nel marketing al dettaglio.

### Impatto aziendale

Le campagne di recupero dopo l’abbandono del carrello recuperano una percentuale significativa dei ricavi altrimenti persi coinvolgendo nuovamente gli acquirenti al momento del più alto intento di acquisto con promemoria e incentivi personalizzati.

### Come implementare

Utilizza il pattern [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) per attivare un messaggio di ripristino quando viene rilevato un evento di abbandono del carrello. Questo è il modello corretto quando un singolo messaggio in tempo reale deve essere inviato in risposta a un evento comportamentale, ad esempio se si lasciano gli elementi nel carrello senza completare l’estrazione.

### Considerazioni tecniche

- Il rilevamento dell’abbandono del carrello richiede una soglia di inattività definita (in genere 30-60 minuti) per distinguere il vero abbandono dai clienti che stanno ancora navigando.
- I contenuti del carrello devono essere trasmessi nel payload dell’evento per abilitare i promemoria di prodotto personalizzati nel messaggio di recupero.
- I clienti che completano il loro acquisto tra l’evento di abbandono e l’invio del messaggio devono essere eliminati per evitare messaggi irrilevanti.
