---
title: Casi d’uso per la vendita al dettaglio
description: Scopri come le organizzazioni di vendita al dettaglio utilizzano Adobe Experience Platform per personalizzare le esperienze di acquisto, recuperare i carrelli abbandonati e promuovere la fidelizzazione dei clienti.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2590'
ht-degree: 0%

---


# Casi d’uso per la vendita al dettaglio

Le organizzazioni di vendita al dettaglio utilizzano Adobe Experience Platform per unificare i dati dei clienti provenienti da negozi online, sedi fisiche e programmi fedeltà in un’unica vista di ogni acquirente. Questa base consente esperienze di acquisto personalizzate, un’attività di sensibilizzazione tempestiva che recupera i ricavi persi e strategie di fidelizzazione che mantengono i clienti al loro ritorno.

## Consigli di prodotto personalizzati

Mostra consigli di prodotti personalizzati su home page, pagine di categorie e pagine di dettagli dei prodotti in base alla cronologia di navigazione, alla cronologia degli acquisti e a comportamenti simili dei clienti. Quando i clienti vedono prodotti su misura per i loro interessi, trascorrono più tempo esplorando e hanno molte più probabilità di acquistare.

### Impatto aziendale

I retailer vedono in genere un aumento del 20-30% nei tassi di click-through e un miglioramento del 15-25% nei tassi di conversione quando inviano consigli personalizzati invece di elenchi di prodotti statici.

### Come implementare

Utilizza il pattern [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Questo approccio utilizza modelli di consigli basati sull’intelligenza artificiale che imparano continuamente dalle interazioni dei clienti per individuare i prodotti più rilevanti per ogni singolo utente.

### Considerazioni tecniche

- I dati del catalogo dei prodotti devono essere acquisiti e mantenuti aggiornati, inclusi attributi dei prodotti, immagini, prezzi e disponibilità, per garantire che i consigli riflettano ciò che i clienti possono effettivamente acquistare.
- I segnali comportamentali come le visualizzazioni del prodotto, gli eventi da aggiungere al carrello e gli acquisti devono scorrere quasi in tempo reale per mantenere aggiornati i consigli all’interno di una singola sessione di navigazione.
- I modelli di consigli richiedono una strategia di avvio a freddo per i nuovi visitatori che non dispongono di cronologia di navigazione e che in genere si rifanno ai prodotti di tendenza o più venduti.
- È necessario monitorare attentamente le prestazioni di caricamento delle pagine, in quanto le chiamate di personalizzazione non dovrebbero aggiungere una latenza visibile all’esperienza di acquisto.


## Ripristino e-mail carrello abbandonato

Invia automaticamente promemoria e-mail personalizzati ai clienti che hanno abbandonato il carrello, inclusi gli articoli rimasti e le offerte pertinenti, per incoraggiarne il completamento. L’abbandono del carrello è una delle maggiori fonti di perdita di ricavi nel settore del commercio al dettaglio e un follow-up tempestivo può recuperare una quota significativa di tali vendite.

### Impatto aziendale

I programmi di recupero del carrello efficaci forniscono un tasso di recupero del carrello del 25-35% e possono generare un ulteriore fatturato da $ 100.000 a $ 500.000 in base al volume del negozio.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio risponde a un evento di abbandono del carrello in tempo reale, inviando un promemoria tempestivo mentre l’intento di acquisto è ancora elevato.

### Considerazioni tecniche

- Il rilevamento dell’abbandono del carrello richiede la definizione di una soglia di inattività (solitamente 30-60 minuti) prima di attivare il primo promemoria, evitando di inviare messaggi ai clienti che stanno ancora effettuando acquisti attivi.
- Il contenuto delle e-mail deve richiamare dinamicamente le immagini, i prezzi e la disponibilità correnti del prodotto dal catalogo al momento dell’invio, in quanto gli articoli possono essere venduti o cambiare il prezzo tra l’abbandono e la consegna.
- Le regole di quota limite devono impedire ai clienti di ricevere più e-mail dal carrello in un breve periodo, soprattutto se abbandonano frequentemente i carrelli.
- Gli elenchi di consenso e soppressione devono essere controllati prima dell’invio e i clienti che hanno completato l’acquisto tramite un altro canale devono essere esclusi in tempo reale.


## Campagne urgenti basate sull’inventario

Attiva avvisi e campagne in tempo reale quando l’inventario dei prodotti è basso, creando urgenza e incoraggiando l’acquisto immediato. Gli acquirenti che vedono che rimangono solo pochi oggetti sono motivati ad agire rapidamente piuttosto che ritardare la loro decisione.

### Impatto aziendale

Le campagne a bassa urgenza di inventario in genere determinano un aumento del 30-40% nella conversione per i prodotti in primo piano, contribuendo anche a ridurre le scorte in eccesso accelerando la vendita di articoli con movimenti lenti.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio risponde agli eventi di soglia di inventario, attivando automaticamente i messaggi di urgenza quando i livelli di scorte scendono al di sotto dei limiti definiti.

### Considerazioni tecniche

- I feed di inventario devono integrarsi con la piattaforma di dati del cliente quasi in tempo reale, in modo che i messaggi di urgenza riflettano i livelli di stock effettivi anziché i dati obsoleti.
- I livelli di soglia dovrebbero essere configurati per categoria di prodotto, poiché una soglia di &quot;scorte basse&quot; per un prodotto di grande volume differisce notevolmente da una soglia per un prodotto di lusso.
- I messaggi devono essere veritieri e conformi alle normative per la protezione dei consumatori; mostrare una falsa scarsità può danneggiare la fiducia del marchio e può violare gli standard pubblicitari in alcuni mercati.
- La messaggistica in loco e i canali e-mail devono essere coordinati in modo che un cliente che ha già acquistato non continui a ricevere notifiche di urgenza per lo stesso prodotto.


## Consigli di cross-selling e upselling

Puoi visualizzare i prodotti di cross-selling e upselling pertinenti al momento del pagamento, tramite e-mail e nelle pagine dei prodotti in base ai modelli di acquisto e alle relazioni tra i prodotti. Suggerire alternative complementari o premium al momento giusto aumenta le dimensioni del carrello senza richiedere ai clienti di cercare gli articoli correlati.

### Impatto aziendale

Le strategie di cross-selling e upselling ben eseguite aumentano il valore medio degli ordini di 25-75 dollari e aumentano i ricavi per transazione del 10-15%.

### Come implementare

Utilizza il pattern [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md). Questo approccio utilizza una logica decisionale centralizzata per valutare tutte le offerte disponibili e selezionare la migliore opzione di cross-selling o upselling per ogni cliente e contesto.

### Considerazioni tecniche

- I dati sulle relazioni tra i prodotti, comprese le associazioni &quot;frequentemente acquistati insieme&quot; e i percorsi di aggiornamento, devono essere conservati e aggiornati regolarmente per riflettere gli attuali modelli di acquisto.
- La logica di classificazione delle offerte deve tenere conto dei livelli di margine, rilevanza e inventario, in modo che le opzioni più redditizie e disponibili emergano per prime.
- I consigli di cross-selling al momento del pagamento devono essere caricati rapidamente e non interrompere il flusso di acquisto; suggerimenti lenti o intrusivi possono effettivamente ridurre la conversione.
- Le regole di decisione di [!DNL Journey Optimizer] devono includere le offerte di fallback in modo che ogni cliente idoneo riceva un consiglio, anche quando l&#39;opzione con il punteggio più alto non è disponibile.


## Nuova serie di benvenuto per i clienti

Automatizza una serie di benvenuto con più e-mail per i nuovi clienti con consigli di prodotto personalizzati, narrazione del brand e offerte speciali. Le prime interazioni dopo l’adesione di un cliente modellano la loro relazione a lungo termine con il marchio, rendendo questa serie uno dei programmi di maggiore impatto che un retailer può eseguire.

### Impatto aziendale

Una serie di benvenuto ben progettata guida un tasso di coinvolgimento del 40-50% tra i nuovi clienti e migliora in modo significativo il valore del ciclo di vita creando in anticipo l’affinità per il marchio.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Questo percorso di sviluppo multi-touch guida i nuovi clienti attraverso una sequenza di messaggi di introduzione al brand, di individuazione dei prodotti e di incentivazione, adattandosi in base al loro coinvolgimento.

### Considerazioni tecniche

- Il trigger di ingresso al percorso deve acquisire in modo affidabile gli eventi di creazione di nuovi clienti da tutte le origini di registrazione, inclusi web, app mobili, punti vendita in-store e mercati di terze parti.
- I passaggi di attesa tra le e-mail devono essere configurati in base ai dati di coinvolgimento; i clienti che aprono e fanno clic potrebbero ricevere il messaggio successivo prima, mentre i clienti meno coinvolti beneficiano di una maggiore spaziatura.
- I consigli sui prodotti nelle e-mail di benvenuto devono riflettere ciò che il cliente ha navigato o acquistato durante la sua prima visita, non i best-seller generici.
- I clienti che effettuano un acquisto durante la serie di benvenuto devono passare a un flusso successivo all’acquisto, anziché continuare a ricevere messaggi incentrati sull’acquisizione.


## Avvisi di riduzione prezzo

Avvisa i clienti tramite e-mail o notifica push quando i prodotti nella lista dei desideri o gli articoli visualizzati in precedenza scendono di prezzo. Gli acquirenti che hanno mostrato interesse ma non hanno acquistato sono molto reattivi alle riduzioni di prezzo, rendendo questo uno dei modi più efficienti per convertire il corrispettivo in vendite.

### Impatto aziendale

Gli avvisi di riduzione dei prezzi generano un tasso di conversione del 20-30% tra i destinatari e aumentano in modo misurabile la soddisfazione dei clienti, aiutandoli a percepire il valore migliore.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio risponde agli eventi di cambiamento del prezzo del prodotto, confrontandoli con i segnali di interesse del cliente per fornire notifiche tempestive.

### Considerazioni tecniche

- Per rilevare le variazioni di prezzo è necessario confrontare i prezzi correnti con i valori precedenti nel feed del catalogo dei prodotti e attivare solo avvisi per riduzioni significative, anziché fluttuazioni minori.
- I segnali di interesse del cliente (aggiunte alla lista dei desideri, visualizzazioni delle pagine dei prodotti, tempo trascorso sulle pagine dei prodotti) devono essere memorizzati e confrontati in modo efficiente con potenziali migliaia di modifiche giornaliere dei prezzi.
- Le notifiche devono includere il prezzo originale, il nuovo prezzo e l&#39;importo dei risparmi per comunicare chiaramente il valore; messaggi vaghi di &quot;riduzione del prezzo&quot; sottoeseguono determinati callout di risparmio.
- È possibile utilizzare [!DNL Real-Time Customer Data Platform] segmenti per gli acquirenti attenti al prezzo per assegnare priorità alla consegna degli avvisi e adattare il tono di messaggistica.


## Promemoria rifornimento

Inviare promemoria automatici ai clienti per i prodotti che acquistano regolarmente, come articoli in abbonamento e materiali di consumo, per incoraggiare acquisti ripetuti prima che scadano. I promemoria proattivi riducono la possibilità che i clienti passino a un concorrente semplicemente perché hanno dimenticato di riordinare.

### Impatto aziendale

I programmi di promemoria per il rifornimento forniscono un tasso di acquisto ripetuto del 30-40% e migliorano in modo significativo la fidelizzazione dei clienti rendendo più semplice per gli acquirenti rifornire i prodotti su cui si basano.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Questo percorso pianificato ricorrente utilizza le previsioni della frequenza di acquisto per inviare promemoria nel momento ottimale prima che un cliente abbia probabilmente bisogno di una ricarica.

### Considerazioni tecniche

- Il calcolo della frequenza di acquisto deve tenere conto dei diversi tassi di consumo per le varie categorie di prodotti; un promemoria per il caffè dovrebbe arrivare con una frequenza diversa da quella per i materiali per la pulizia.
- Il percorso deve modificare dinamicamente la tempistica quando un cliente riordina prima o dopo il previsto, ricalibrando il promemoria successivo in base ai dati di acquisto aggiornati.
- I promemoria devono includere un collegamento diretto per il riordino o un’opzione di riacquisto con un solo clic per ridurre al minimo l’attrito e massimizzare la conversione dalla notifica.
- I clienti che hanno già effettuato un riordine tramite un altro canale (in-store, servizio di abbonamento) devono essere eliminati per evitare di inviare promemoria irrilevanti.


## Pagine di categorie personalizzate

Personalizza dinamicamente le pagine delle categorie per mostrare i prodotti più rilevanti in base alle preferenze di ciascun cliente, agli acquisti precedenti e al comportamento di navigazione. Quando i consumatori vedono prodotti allineati con i loro gusti nella parte superiore della pagina, scoprono ciò che vogliono più velocemente e convertono a tassi più elevati.

### Impatto aziendale

Le pagine personalizzate per categorie incrementano del 25-35% il coinvolgimento nelle pagine per categorie e migliorano in modo significativo l’individuazione dei prodotti, in particolare per i rivenditori con cataloghi di grandi dimensioni.

### Come implementare

Utilizza il pattern [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Questo approccio utilizza strategie di selezione e modelli di classificazione per riordinare i prodotti sulle pagine delle categorie in base al profilo e al comportamento in tempo reale di ogni visitatore.

### Considerazioni tecniche

- La classificazione del prodotto deve essere eseguita abbastanza rapidamente da evitare ritardi percepiti nel caricamento delle pagine; spesso per le pagine di categorie con centinaia di prodotti è necessario ricorrere alla personalizzazione lato server o al decisioning basato su Edge.
- La logica di personalizzazione deve combinare le preferenze individuali con le regole di merchandising, garantendo che i prodotti promossi, i nuovi arrivati e gli articoli stagionali ricevano ancora la visibilità appropriata.
- Dovrebbe essere presente un’infrastruttura di test A/B per misurare su base continuativa l’impatto sui ricavi dell’ordinamento personalizzato rispetto alle regole di merchandising predefinite.
- L&#39;implementazione di [!DNL Experience Platform] Web SDK deve acquisire le interazioni delle pagine delle categorie (profondità di scorrimento, clic sul prodotto, utilizzo del filtro) per perfezionare continuamente i modelli di classificazione.


## Campagne di follow-up post-acquisto

Invia e-mail post-acquisto con suggerimenti per l’assistenza sui prodotti, suggerimenti sui prodotti correlati, richieste di revisione e informazioni sul programma fedeltà. Il periodo immediatamente successivo all’acquisto coincide con il momento in cui i clienti sono più coinvolti con il brand, rendendolo una finestra ideale per approfondire la relazione e incoraggiare attività future.

### Impatto aziendale

Le campagne post-acquisto efficaci aumentano i tassi di invio delle recensioni del 15-20% e guidano una percentuale di acquisti ripetuti del 10-15%, trasformando gli acquirenti occasionali in clienti fedeli.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Questo flusso post-acquisto in più passaggi utilizza una logica di diramazione per personalizzare i messaggi di follow-up in base al tipo di prodotto, al segmento di cliente e al coinvolgimento con le e-mail precedenti della serie.

### Considerazioni tecniche

- Il percorso deve tenere conto dello stato di evasione dell’ordine; i suggerimenti per l’assistenza e le richieste di revisione devono essere inviati solo dopo la consegna del prodotto, non immediatamente dopo l’acquisto.
- Il contenuto specifico del prodotto (istruzioni per la cura, guide per l’uso, suggerimenti per gli accessori) richiede un sistema di mappatura del contenuto che associ ogni categoria di prodotto ai relativi materiali di follow-up.
- I tempi delle richieste di revisione devono essere ottimizzati in base alla categoria del prodotto; l’elettronica può richiedere un periodo di utilizzo più lungo prima di una revisione significativa, mentre l’abbigliamento può essere rivisto poco dopo la consegna.
- I clienti che avviano un reso o uno scambio devono essere automaticamente rimossi dal flusso standard post-acquisto e reindirizzati a un percorso di ripristino del servizio.


## Offerte esclusive per i clienti VIP

Identifica i clienti di alto valore e fornisci offerte esclusive, accesso anticipato alle vendite ed esperienze di acquisto personalizzate che premiano la loro fedeltà. Mantenere i clienti top-tier è molto più conveniente che acquistarne di nuovi, e il trattamento esclusivo rafforza la connessione emotiva che li mantiene in spesa.

### Impatto aziendale

I programmi VIP generano in genere un tasso di coinvolgimento del 50-70% da parte dei clienti di livello più alto e migliorano in modo misurabile il valore del ciclo di vita dei clienti riducendo l’abbandono tra i segmenti più redditizi.

### Come implementare

Utilizza il Percorso [cross-channel con modello Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md). Questo approccio combina l’orchestrazione del percorso con il decisioning in tempo reale per la selezione delle offerte, garantendo a ogni cliente VIP l’offerta esclusiva più rilevante su ogni canale.

### Considerazioni tecniche

- I criteri di segmentazione di VIP devono essere chiaramente definiti utilizzando le metriche di attualità, frequenza e valore monetario; i segmenti devono essere aggiornati con frequenza tale da acquisire i clienti che si sono recentemente qualificati o non qualificati.
- Le offerte esclusive devono essere applicate al momento del rimborso (web, app, store) per impedire ai clienti non VIP di accedervi, il che richiede l’integrazione con i sistemi di promozione e di prezzo.
- Le preferenze di canale variano notevolmente tra i clienti di alto valore; alcuni preferiscono la posta elettronica, altri rispondono alle notifiche dell’app o alla direct mailing, pertanto il percorso dovrebbe adattare i canali di consegna in base al coinvolgimento passato.
- Le decisioni di [!DNL Journey Optimizer] devono coordinarsi tra i canali per evitare che un cliente VIP riceva la stessa offerta simultaneamente tramite e-mail, push e SMS.


## Notifiche esaurite

Consenti ai clienti di registrarsi per ricevere notifiche quando i prodotti esauriti diventano disponibili, quindi di inviargli automaticamente una notifica tramite e-mail o messaggio di testo. L&#39;acquisizione della domanda di prodotti non disponibili impedisce la perdita delle vendite e offre ai clienti un motivo per tornare al negozio piuttosto che acquistare da un concorrente.

### Impatto aziendale

Le notifiche back-in-stock raggiungono un tasso di conversione del 40-50% tra gli abbonati e riducono in modo significativo le vendite perse per i prodotti ad alta domanda che sperimentano stockout temporanei.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio attiva le notifiche sugli eventi di back-in-stock, abbinando gli aggiornamenti di inventario alle iscrizioni alle notifiche dei clienti per inviare avvisi tempestivi.

### Considerazioni tecniche

- Il monitoraggio dell’inventario deve rilevare rapidamente gli eventi di riassortimento; ritardi anche di poche ore possono comportare nuovamente la vendita del prodotto prima che i clienti avvisati abbiano la possibilità di effettuare l’acquisto.
- Quando un prodotto popolare viene rifornito in quantità limitata, le notifiche devono essere scaglionate o classificate in base alla data di registrazione per evitare di inviare avvisi a più clienti di quanti ne possa servire l’inventario disponibile.
- Il meccanismo di abbonamento alle notifiche deve acquisire le preferenze del canale (e-mail o messaggio di testo) e soddisfare i requisiti di consenso per ciascun canale, in particolare per gli SMS.
- Gli attributi del profilo [!DNL Real-Time Customer Data Platform] devono tenere traccia dei prodotti che ogni cliente sta guardando in modo che le notifiche duplicate non vengano ripetute se lo stesso prodotto viene rifornito più volte.


## Personalization per bozza social

Visualizza una bozza social personalizzata, incluse recensioni, valutazioni e suggerimenti &quot;I clienti che hanno acquistato questo hanno acquistato anche&quot;, in base al profilo e alle preferenze di ciascun cliente. Personalizzare la bozza social per riflettere le esperienze di clienti simili genera fiducia in modo più efficace rispetto ai soli rating generici.

### Impatto aziendale

La bozza sociale personalizzata aumenta i tassi di conversione del 10-15% e migliora la fiducia degli acquirenti, in particolare per i nuovi acquirenti e per i prodotti a prezzi più elevati in cui l’esitazione di acquisto è maggiore.

### Come implementare

Utilizza il pattern [Visitatore noto Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md). Questo approccio personalizza i contenuti web per i visitatori identificati, selezionando le recensioni più rilevanti e gli elementi di prova social in base al profilo, alle preferenze e al contesto di navigazione del cliente.

### Considerazioni tecniche

- I dati di revisione e valutazione devono essere strutturati e contrassegnati dagli attributi del cliente (come contesto di acquisto, segmento di cliente e caso di utilizzo del prodotto) per consentire un filtraggio e una personalizzazione significativi.
- Gli elementi di prova social devono essere caricati in modo asincrono per evitare di bloccare il rendering della pagina del prodotto principale, in quanto i dati di revisione possono provenire da una piattaforma di revisione di terze parti con tempi di risposta variabili.
- Le normative sulla privacy richiedono che tutti i dati dei clienti utilizzati per far corrispondere le recensioni ai visitatori vengano gestiti in base alle preferenze di consenso; la visualizzazione di contenuti &quot;piacenti ai clienti&quot; implica la profilazione che può richiedere la divulgazione.
- L&#39;iscrizione al pubblico di [!DNL Experience Platform] può essere utilizzata per selezionare le recensioni da evidenziare, mostrando le recensioni degli appassionati di outdoor di altri acquirenti piuttosto che le recensioni generiche più votate.
