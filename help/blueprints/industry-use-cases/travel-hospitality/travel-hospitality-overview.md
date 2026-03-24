---
title: Casi di utilizzo di viaggi e ospitalità
description: Scopri come le organizzazioni di viaggi e ospitalità utilizzano Adobe Experience Platform per personalizzare le esperienze di prenotazione, recuperare le prenotazioni abbandonate e fidelizzare gli ospiti.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: fbdcc015-96a4-4015-93e2-3fc7db375c13
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '3648'
ht-degree: 0%

---

# Casi di utilizzo di viaggi e ospitalità

Le organizzazioni che si occupano di viaggi e ospitalità utilizzano Adobe Experience Platform per riunire in un’unica vista i dati degli ospiti provenienti da motori di prenotazione, programmi fedeltà, sistemi di gestione delle proprietà e punti di contatto digitali. Questa base unificata potenzia esperienze personalizzate che ispirano prenotazioni, recuperano prenotazioni abbandonate e creano il tipo di fedeltà degli ospiti che guida visite ripetute.

## Home page personalizzata per nuovi visitatori

Mostra consigli personalizzati su crociera, hotel e destinazione sulla homepage in base alla posizione geografica del visitatore e al suo comportamento di navigazione. È molto più probabile che i nuovi visitatori che vedono immediatamente le opzioni di viaggio rilevanti approfondiscano ulteriormente e inizino il processo di prenotazione.

### Impatto aziendale

La personalizzazione della home page per i nuovi visitatori determina tassi di conversione migliorati, presentando opzioni di viaggio che corrispondono alla posizione e agli interessi del visitatore, anziché contenuti generici.

### Come implementare

Utilizza il pattern [Visitatore anonimo Web Personalization](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md). Questo approccio offre contenuti personalizzati ai visitatori che non si sono ancora identificati, utilizzando i segnali disponibili come geolocalizzazione, tipo di dispositivo e origine di riferimento per personalizzare l’esperienza dalla prima pagina. Questo è il modello corretto quando il visitatore non si è ancora identificato e la personalizzazione deve basarsi sui segnali disponibili come la geolocalizzazione, il tipo di dispositivo e la sorgente di riferimento. La personalizzazione dei visitatori noti richiede un profilo autenticato che non esiste ancora.

### Considerazioni tecniche

- I dati di geolocalizzazione devono essere risolti con precisione al limite per fornire le destinazioni, le valute e le porte di partenza appropriate per l’area geografica senza aggiungere latenza al caricamento della home page.
- Le regole di Personalization devono tenere conto delle tendenze di viaggio stagionali per regione, ad esempio per far emergere destinazioni con tempo caldo per i visitatori in climi freddi durante i mesi invernali.
- Le strategie di contenuto di fallback sono essenziali per i visitatori la cui posizione non può essere determinata o che arrivano tramite servizi di anonimizzazione.
- L’integrazione con il feed di disponibilità del sistema di prenotazione assicura che le proprietà e gli itinerari in primo piano siano effettivamente prenotabili, evitando frustrazioni nel promuovere opzioni tutto esaurito.


## Percorso di recupero per abbandono carrello

Rileva automaticamente quando un cliente abbandona il carrello di prenotazione e attiva un percorso e-mail in più passaggi con offerte personalizzate per incoraggiarne il completamento. Le prenotazioni abbandonate rappresentano una delle maggiori perdite di ricavi in viaggi e ospitalità, e un follow-up tempestivo mentre l’intento di viaggio è ancora fresco recupera una quota significativa di tali prenotazioni.

### Impatto aziendale

I programmi efficaci di recupero delle prenotazioni consentono di ottenere tassi significativi di recupero del carrello e possono generare ricavi incrementali significativi in base al volume di prenotazione e al valore medio del viaggio.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio risponde a un evento di abbandono del carrello in tempo reale, inviando un promemoria tempestivo mentre l’intento di viaggio del cliente è ancora elevato. Questo è il modello corretto quando l’attivatore è un evento di comportamento del cliente in tempo reale e la risposta richiesta è un messaggio singolo e sensibile al tempo, anziché una sequenza di sviluppo in più fasi o una selezione dinamica dell’offerta che cambia in base alla risposta del cliente.

### Considerazioni tecniche

- Le soglie di rilevamento dell’abbandono del carrello devono tenere conto dei cicli di considerazione più lunghi tipici degli acquisti di viaggi; un ritardo di 2-4 ore prima del primo promemoria è spesso più appropriato dei 30-60 minuti utilizzati nel settore retail.
- Il contenuto dell’e-mail deve richiamare dinamicamente i prezzi correnti, la disponibilità della camera o della cabina e le immagini dal sistema di prenotazione al momento dell’invio, poiché l’inventario e le tariffe dei viaggi cambiano frequentemente.
- Gli incentivi personalizzati, come aggiornamenti gratuiti o crediti di resort, devono essere gestiti tramite regole aziendali che tengano conto del margine, della stagionalità e del livello di fedeltà del cliente.
- La logica di soppressione deve escludere i clienti che hanno completato la prenotazione tramite un altro canale, ad esempio un call center o un agente di viaggio, per evitare messaggi di follow-up irrilevanti.


## Targeting ad alta intenzione dei visitatori

Identifica i visitatori con un intento di acquisto elevato utilizzando il punteggio di propensione basato sull’intelligenza artificiale ed esegui il targeting con offerte e contenuti personalizzati. Riconoscere quali visitatori hanno più probabilità di prenotare consente all’organizzazione di concentrare le offerte e le attività di vendita più convincenti sui viaggiatori più vicini a prendere una decisione.

### Impatto aziendale

Il targeting di visitatori ad alto intento con offerte personalizzate determina una conversione migliore per questi segmenti, concentrando gli investimenti di marketing dove offre il massimo ritorno.

### Come implementare

Utilizza il pattern [Visitatore noto Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md). Questo approccio utilizza dati di profilo in tempo reale e segnali comportamentali per personalizzare l’esperienza web per i visitatori identificati, fornendo contenuti e offerte personalizzati che corrispondono al loro livello di preparazione all’acquisto. Questo è il modello corretto quando la personalizzazione è guidata dagli attributi di profilo e dai punteggi di tendenza per i clienti identificati anziché da un modello di affinità comportamentale e quando il cliente ha già eseguito l’autenticazione, rendendo disponibili i segnali di appartenenza ai segmenti e di intento.

### Considerazioni tecniche

- I modelli di tendenza devono essere formati su segnali di intento specifici per il viaggio, come ricerche di date, visualizzazioni di pagina per la determinazione dei prezzi, attività di confronto delle stanze e visite ripetute alla stessa destinazione in una breve finestra.
- Gli interventi ad alto intento, come i prompt delle chat in tempo reale o le offerte a tempo limitato, dovrebbero apparire nei punti di decisione naturali del flusso di prenotazione anziché interrompere l’esperienza di navigazione.
- Il modello di punteggio dovrebbe distinguere tra intento di ricerca e intento di prenotazione, in quanto i viaggiatori spesso effettuano ricerche mesi prima di essere pronti per l’acquisto.
- [!DNL Real-Time Customer Data Platform] attributi calcolati possono aggregare i segnali comportamentali tra le sessioni per mantenere un punteggio intento aggiornato per ogni visitatore.


## Campagne di upselling post-prenotazione

Dopo che un cliente ha completato una prenotazione, attiva automaticamente campagne di upselling per aggiornamenti della cabina, escursioni a terra, pacchetti di ristorazione e altri servizi ausiliari. Il periodo tra prenotazione e viaggio è il momento in cui gli ospiti sono più entusiasti del loro prossimo viaggio e più ricettivi a migliorare la loro esperienza.

### Impatto aziendale

Le campagne di upselling post-prenotazione aumentano il valore medio dell’ordine e incrementano i ricavi accessori, trasformando una singola prenotazione in una transazione molto più preziosa.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Questo percorso in più passaggi guida i clienti attraverso una sequenza temporale di opportunità di upselling, adattando le offerte in base a ciò che l’ospite ha già acquistato e al suo coinvolgimento con i messaggi precedenti. Questo è il modello corretto quando il caso d’uso richiede un flusso di messaggi multipli in sequenza nell’arco di giorni con diramazioni condizionali in base agli eventi di coinvolgimento e alla disponibilità dell’inventario. Un singolo messaggio attivato non può soddisfare la logica di dipendenza tra i momenti di upselling o le regolazioni degli orari in base alla prossimità della data di viaggio.

### Considerazioni tecniche

- Il percorso deve integrarsi con il sistema di prenotazione per sapere esattamente cosa l&#39;ospite ha prenotato, quali aggiornamenti sono disponibili per il loro itinerario specifico e i prezzi correnti per ogni opzione ausiliaria.
- Gli orari di upselling devono essere scaglionati strategicamente; gli aggiornamenti della cabina possono essere offerti poco dopo la prenotazione, mentre le escursioni e i pacchetti di ristorazione hanno prestazioni migliori con l&#39;avvicinarsi della data di viaggio.
- L&#39;inventario e la disponibilità dei prodotti ausiliari devono essere controllati al momento della presentazione dell&#39;offerta, poiché la capacità di escursione e la disponibilità dell&#39;aggiornamento cambiano continuamente.
- La personalizzazione di [!DNL Journey Optimizer] deve tenere conto del numero di viaggiatori nella prenotazione, consigliando escursioni appropriate per la famiglia per prenotazioni familiari ed esperienze orientate alle coppie per prenotazioni a due persone.


## Campagne di riconquista per i clienti inattivi

Identifica i clienti che non hanno prenotato per dodici o più mesi e coinvolgili con offerte di fidelizzazione e contenuti personalizzati in base alle loro preferenze di viaggio passate. Il coinvolgimento degli ospiti inattivi è molto più conveniente rispetto all&#39;acquisizione di nuovi clienti, e i viaggiatori del passato hanno già una certa familiarità con il marchio che riduce la barriera al rebooking.

### Impatto aziendale

Campagne di riconquista ben mirate consentono di ottenere tassi di riattivazione significativi tra i clienti inattivi, recuperando ricavi da ospiti che altrimenti non tornerebbero mai.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Questo percorso, articolato in più fasi, coinvolge nuovamente i clienti in difficoltà con una serie progressiva di messaggi che evolvono dall&#39;ispirazione all&#39;incentivo sulla base della risposta del cliente. Questo è il modello corretto quando non esiste un evento di attivazione discreto e la tempistica deve essere calcolata in base ai modelli del ciclo di vita del cliente e ai modelli di prenotazione stagionale: i messaggi attivati da un evento non possono gestire la logica di escalation progressiva o la necessità di temporizzare le offerte intorno alle finestre di pianificazione dei viaggi tipiche.

### Considerazioni tecniche

- La segmentazione dei clienti scaduta deve tenere conto della frequenza di prenotazione tipica nella categoria di viaggio; un cliente che prenota annualmente non deve essere segnalato come decaduto dopo solo sei mesi di inattività.
- I contenuti di ritorno devono fare riferimento alle preferenze di viaggio passate del cliente, come destinazioni preferite, tipi di cabina o stagioni di viaggio, per dimostrare che il brand li ricorda e li apprezza.
- Le offerte dovrebbero diffondersi in tutto il percorso, iniziando con contenuti ispiratori e progredendo verso incentivi monetari solo se i messaggi precedenti non generano coinvolgimento.
- Le registrazioni dei clienti devono essere confrontate con il sistema di prenotazione per eventuali prenotazioni effettuate tramite canali offline come agenzie di viaggio o call center per evitare di inviare messaggi di recupero ai clienti che sono effettivamente attivi.


## Raccomandazioni per itinerari dinamici

Mostra itinerari e destinazioni di crociera personalizzati in base alle prenotazioni precedenti del cliente, alla cronologia di navigazione e alle preferenze dichiarate. Quando i viaggiatori vedono itinerari adatti ai loro interessi e al loro stile di viaggio, si impegnano più profondamente con l&#39;esperienza di pianificazione e si spostano verso la prenotazione più rapidamente.

### Impatto aziendale

I consigli di itinerario personalizzati contribuiscono a migliorare il coinvolgimento con le pagine di itinerario, aiutando i clienti a trovare più rapidamente il viaggio giusto e riducendo il calo di abbandono che si verifica quando i viaggiatori si sentono sopraffatti da troppe opzioni.

### Come implementare

Utilizza il pattern [Visitatore noto Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md). Questo approccio personalizza i contenuti del sito web per i visitatori identificati, utilizzando i dati del loro profilo e la cronologia comportamentale per delineare gli itinerari e le destinazioni più rilevanti. Questo è il modello giusto quando la personalizzazione è guidata dagli attributi del profilo e dalla cronologia delle prenotazioni anziché da un modello di affinità comportamentale, che consente a una logica basata su regole di tenere conto della logistica dei viaggi, come i porti di partenza e le date, insieme alle preferenze del cliente.

### Considerazioni tecniche

- La logica dei consigli di itinerario deve incorporare le date di navigazione o di soggiorno, i porti di partenza e le preferenze di durata insieme all’interesse della destinazione per presentare opzioni che siano al tempo stesso interessanti e pratiche per il cliente.
- L&#39;integrazione con il sistema centrale di prenotazione assicura che gli itinerari consigliati abbiano inventario disponibile e riflettano i prezzi correnti, evitando frustrazione di promuovere viaggi tutto esaurito o proprietà completamente prenotate.
- I fattori stagionali dovrebbero influenzare fortemente le raccomandazioni; i clienti che hanno prenotato in precedenza crociere estive nel Mediterraneo dovrebbero vedere opzioni stagionali simili piuttosto che alternative fuori stagione.
- I criteri di unione profili [!DNL Experience Platform] devono unificare correttamente il comportamento di navigazione da più dispositivi in modo che la ricerca condotta su dispositivi mobili si rifletta nei consigli sul desktop.


## Prodotti visualizzati di recente sulla homepage

Visualizza sulla homepage crociere, alberghi o destinazioni visualizzate di recente per ricordare ai visitatori il loro interesse e incoraggiare le visite di ritorno. I viaggiatori spesso effettuano ricerche su più sessioni prima di prenotare e, facendo emergere i loro interessi precedenti, eliminano l’attrito di iniziare la ricerca su ogni volta che ritornano.

### Impatto aziendale

Mostrando i prodotti di viaggio recentemente sfogliati sulla homepage aumenta il coinvolgimento per la visita di ritorno, aiutando i clienti a riprendere da dove hanno lasciato e accorciando il percorso per prenotare.

### Come implementare

Utilizza il pattern [Visitatore noto Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md). Questo approccio utilizza i dati di profilo memorizzati del visitatore per eseguire il rendering degli elementi visualizzati in precedenza sulla home page, creando continuità tra le sessioni di navigazione. Questo è il modello corretto quando la personalizzazione si basa su dati di profilo persistenti tra sessioni e dispositivi, anziché sull’affinità comportamentale in tempo reale, e quando le regole di rilevanza sono basate sul tempo (recency) anziché sulla classificazione algoritmica.

### Considerazioni tecniche

- I dati visualizzati di recente devono persistere tra dispositivi e sessioni che utilizzano la risoluzione dell’identità, in modo che un cliente che naviga sul telefono veda gli stessi elementi quando ritorna su un desktop.
- Gli articoli visualizzati devono mostrare lo stato attuale di disponibilità e prezzi, con indicatori chiari che indicano se un’opzione visualizzata in precedenza non è più disponibile o se il prezzo è cambiato dall’ultima visita.
- La finestra di aggiornamento per gli articoli visualizzati deve essere sintonizzata sui cicli di prenotazione dei viaggi; mostrare una crociera vista tre mesi fa potrebbe essere ancora rilevante, a differenza di un prodotto al dettaglio visto così tanto tempo fa.
- Considerazioni sulla privacy richiedono che il contenuto visualizzato di recente sia associato allo stato di consenso del cliente e un’opzione per cancellare la cronologia di navigazione dovrebbe essere facilmente accessibile.


## Finestra modale Intento di uscita con offerte mirate

Quando un visitatore mostra l’intento di uscita, mostra un modale personalizzato con offerte rilevanti in base al suo comportamento di navigazione durante la sessione. Prendere un visitatore in partenza con un’offerta interessante e contestualmente rilevante offre un’ultima opportunità per convertire gli interessi in una prenotazione prima che se ne vada.

### Impatto aziendale

I modali di intento di uscita con offerte di viaggio personalizzate recuperano conversioni significative tra i visitatori che altrimenti partirebbero senza prenotazione, generando ricavi che andrebbero completamente persi.

### Come implementare

Utilizza il pattern [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md). Questo approccio utilizza una logica decisionale centralizzata per valutare tutte le offerte disponibili e selezionare quella più rilevante per il visitatore in partenza in base al comportamento della sessione e ai dati del profilo. Questo è il modello corretto quando la selezione delle offerte deve tenere conto dell’idoneità del livello di fedeltà e dei vincoli di business relativi ai limiti di frequenza, vincoli che richiedono una logica decisionale regolamentata anziché un semplice consiglio comportamentale o un singolo messaggio attivato.

### Considerazioni tecniche

- Il rilevamento intento di uscita sui siti di prenotazione viaggi deve tenere conto del comportamento di navigazione con più schede, in quanto i viaggiatori spesso aprono più itinerari o proprietà in schede separate senza avere l’intenzione di partire.
- La selezione dell’offerta deve riflettere ciò che il visitatore ha navigato durante la sessione, presentando uno sconto sulla destinazione o proprietà specifica esaminata, anziché una promozione generica.
- La frequenza modale deve essere strettamente limitata per evitare che i visitatori vedano la stessa offerta in ogni visita, il che erode l’urgenza e l’esclusività percepita della promozione.
- Le regole di idoneità per le offerte di [!DNL Journey Optimizer] devono considerare il livello di fedeltà del visitatore e la cronologia delle prenotazioni per presentare incentivi di valore adeguato, offrendo agli ospiti premium vantaggi significativi anziché piccoli sconti.


## Programma fedeltà Personalization

Personalizza l’esperienza del sito web, le offerte e le comunicazioni in base al livello di fedeltà del cliente, al saldo dei punti e alla cronologia del coinvolgimento. I membri fedeltà che vedono il loro status riflesso in ogni punto di contatto si sentono riconosciuti e valutati, il che rafforza il loro impegno per il marchio e incoraggia l’avanzamento di livello.

### Impatto aziendale

La personalizzazione basata su livelli porta a un coinvolgimento migliore da parte dei membri fedeltà, approfondendo la relazione e accelerando i comportamenti di guadagno e rimborso che sostengono i ricavi a lungo termine.

### Come implementare

Utilizza il Percorso [cross-channel con modello Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md). Questo approccio combina l’orchestrazione del percorso con il decisioning in tempo reale per offrire l’offerta giusta attraverso il canale giusto per ogni membro fedeltà, adattandosi al suo livello, alle preferenze e alle attività recenti. Questo è il modello corretto quando il percorso deve coordinare la distribuzione tra i canali per evitare offerte duplicate e quando la selezione delle offerte richiede regole di idoneità basate su livelli e vincoli di rimborso. L’orchestrazione del percorso non fornisce da sola il livello decisionale multicanale necessario.

### Considerazioni tecniche

- I dati del programma fedeltà, tra cui lo stato del livello, i saldi dei punti e la cronologia degli guadagni, devono essere acquisiti e tenuti aggiornati per garantire che la personalizzazione del sito web e le offerte riflettano la posizione effettiva del cliente.
- Vantaggi specifici di livello, come l&#39;accesso anticipato alle prenotazioni, gli aggiornamenti gratuiti e i prezzi esclusivi, devono essere applicati al punto di rimborso, richiedendo una stretta integrazione con i sistemi di prenotazione e prezzi.
- Le modifiche del saldo dei punti derivanti da prenotazioni, soggiorni e transazioni dei partner dovrebbero attivare il ricalcolo delle regole di personalizzazione in tempo quasi reale, in modo che un cliente che ha appena guadagnato abbastanza punti per un premio veda immediatamente tale opzione.
- I tipi di pubblico di [!DNL Real-Time Customer Data Platform] devono essere strutturati in base ai livelli di fedeltà e ai milestone di coinvolgimento chiave, ad esempio per avvicinarsi al livello successivo o a rischio di abbassamento di livello.


## Promemoria di prenotazione multicanale

Invia promemoria di prenotazione personalizzati tramite e-mail, SMS e notifiche push ai clienti che hanno iniziato ma non completato la prenotazione. I viaggiatori iniziano spesso il processo di prenotazione e vengono interrotti, e raggiungendoli attraverso i loro canali preferiti con un promemoria e i dettagli del viaggio salvati li riporta a completare la prenotazione.

### Impatto aziendale

I promemoria di prenotazione multicanale migliorano i tassi di completamento della prenotazione, recuperando ricavi significativi dai clienti che intendevano prenotare ma che sono stati ignorati prima di terminare.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio attiva automaticamente i promemoria quando viene rilevato un evento di prenotazione incompleto, che invia messaggi tempestivi tra i canali preferiti del cliente. Questo è il modello corretto quando l’attivatore è un’azione discreta del cliente (avvio di una prenotazione) e la risposta richiesta è una consegna sensibile al tempo tra i canali preferiti, anziché una sequenza in più passaggi in cui ogni messaggio dipende dal coinvolgimento precedente o da modifiche della disponibilità.

### Considerazioni tecniche

- La logica di selezione del canale deve rispettare le preferenze di comunicazione dei clienti e ottimizzare la consegna in base ai modelli di coinvolgimento passati, inviando notifiche push ai clienti che rispondono bene al mobile e e-mail a coloro che lo preferiscono.
- Il contenuto del promemoria deve includere un collegamento profondo che restituisca al cliente direttamente la prenotazione salvata con tutte le selezioni intatte, eliminando l’attrito di reinserire le date di viaggio, le preferenze della camera e i dettagli dell’ospite.
- Le regole di tempistica e frequenza devono coordinarsi tra i canali per evitare di sopraffare il cliente; un’e-mail e una notifica push relativa alla stessa prenotazione devono essere distanziate in modo appropriato anziché essere inviate contemporaneamente.
- L’integrazione con il sistema di gestione delle proprietà o di prenotazione centrale deve verificare che il tipo di camera, la tariffa e le date selezionati in origine siano ancora disponibili prima di inviare il promemoria, aggiornando il messaggio se la disponibilità è cambiata.


## Campagna stagionale Personalization

Personalizza campagne e offerte in base alle preferenze stagionali, alle prenotazioni stagionali passate e alle tendenze stagionali correnti. I viaggiatori sono fortemente influenzati dalle stagioni, e le campagne che si allineano con i loro interessi stagionali dimostrati e le tendenze di viaggio attuali sono molto più convincenti rispetto alle promozioni generiche.

### Impatto aziendale

Le campagne personalizzate in base alla stagionalità aumentano la conversione delle prenotazioni stagionali, garantendo che gli investimenti di marketing siano concentrati sulle destinazioni e sui prodotti di viaggio che hanno più probabilità di risuonare con ogni cliente.

### Come implementare

Utilizza il pattern [Attivazione messaggi in uscita in batch](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md). Questo approccio distribuisce messaggi personalizzati per campagne stagionali a grandi tipi di pubblico su base pianificata, segmentando i clienti in base ai pattern di viaggio stagionali e alle preferenze. Questo è lo schema corretto quando il pubblico è ampio e predefinito dalla cronologia delle prenotazioni stagionali, la programmazione della consegna è basata su finestre di pianificazione stagionale anziché basata su eventi e non è necessario ricorrere a diramazioni o decisioni in tempo reale.

### Considerazioni tecniche

- I profili delle preferenze stagionali dei clienti devono essere elaborati sulla base di dati di prenotazione storici, identificando modelli quali vacanze estive costanti sulla spiaggia o viaggi di sci invernali per informare il targeting delle campagne.
- La pianificazione delle campagne deve tenere conto dei lead time del settore dei viaggi; le campagne per le vacanze estive dovrebbero essere lanciate all’inizio della primavera, quando le famiglie stanno pianificando, e non a giugno, quando la maggior parte delle prenotazioni è già stata effettuata.
- I prezzi e i feed di disponibilità per le scorte stagionali devono essere integrati in modo che le offerte promosse riflettano le tariffe in tempo reale e la disponibilità effettiva di camere o cabine durante i periodi di viaggio richiesti.
- [!DNL Experience Platform] tipi di pubblico devono combinare i dati delle preferenze stagionali con gli indicatori di attualità per dare la priorità ai clienti che si trovano nella loro tipica finestra di pianificazione per la prossima stagione.


## Consigli per la prenotazione di gruppi

Identifica i clienti che prenotano spesso viaggi di gruppo e consiglia proattivamente pacchetti di gruppo, opzioni per famiglie o prenotazioni con più camere. Le prenotazioni di gruppo rappresentano ricavi significativamente più elevati per transazione e i clienti con un modello comprovato di viaggi di gruppo rispondono bene alle opzioni curate che semplificano il processo di pianificazione.

### Impatto aziendale

I consigli proattivi di prenotazione di gruppo aumentano il valore medio dell’ordine per prenotazione, acquisendo il valore completo delle transazioni di viaggio di gruppo che altrimenti potrebbero essere suddivise tra più prenotazioni individuali.

### Come implementare

Utilizza il pattern [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Questo approccio utilizza modelli basati sull’intelligenza artificiale che imparano dai modelli e dai comportamenti di prenotazione dei clienti per consigliare le opzioni di viaggio di gruppo più rilevanti per ciascun cliente. Questo è il modello corretto quando il set di articoli è di grandi dimensioni e in continua evoluzione (pacchetti di gruppi che evolvono con prezzi e disponibilità) e la selezione è guidata da modelli comportamentali della cronologia delle prenotazioni di gruppi anziché da un set limitato di offerte disciplinate da regole di idoneità.

### Considerazioni tecniche

- L’identificazione dei viaggi di gruppo richiede l’analisi della cronologia delle prenotazioni per pattern quali prenotazioni con più camere, prenotazioni con più passeggeri e prenotazioni coordinate effettuate in stretta collaborazione per le stesse date e destinazione.
- I prezzi dei pacchetti di gruppo devono essere estratti dal sistema di prenotazione in modo dinamico, poiché le tariffe di gruppo spesso differiscono dalle singole tariffe e possono richiedere dimensioni minime delle parti o finestre di prenotazione anticipate.
- Il contenuto dei consigli deve soddisfare le esigenze specifiche degli organizzatori del gruppo, incluse informazioni sulle opzioni di ristorazione del gruppo, sugli spazi per le riunioni, sugli sconti di prenotazione dei blocchi e sulla disponibilità di escursioni di gruppo.
- L&#39;arricchimento del profilo [!DNL Real-Time Customer Data Platform] deve contrassegnare i clienti come organizzatori di viaggi di gruppo in base ai loro modelli di prenotazione, abilitando campagne mirate durante i periodi di pianificazione di picco del gruppo, ad esempio la stagione di ricongiungimento familiare o le finestre di ritiro aziendali.


## Concierge prenotazione AI

Le organizzazioni di viaggio e ospitalità offrono percorsi di acquisto complessi e di alta considerazione in cui gli ospiti devono navigare voli, camere, categorie di camere, servizi ausiliari e benefici fedeltà prima di impegnarsi a una prenotazione. Le interfacce statiche di ricerca e filtro generano un eccesso di decisioni e aumentano il tasso di abbandono. Un portinaio di prenotazione AI coinvolge gli ospiti in conversazioni naturali per comprendere le loro intenzioni di viaggio, le dimensioni delle feste, le preferenze e il budget, quindi li guida passo dopo passo attraverso la pianificazione degli itinerari, la selezione degli alloggi e le opzioni aggiuntive, il tutto mentre emergono i vantaggi di fedeltà relativi al livello dell’ospite.

### Impatto aziendale

La guida alla prenotazione conversazionale migliora i tassi di completamento degli itinerari e l’allegato accessorio, riducendo il volume del call center per gli ospiti che altrimenti telefonerebbero per chiarire le opzioni.

### Come implementare

Utilizza il pattern [Esperienza conversazionale di Brand Concierge](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md). Questo approccio distribuisce Product Advisor Agent rispetto al catalogo proprietà e itinerario, utilizzando AEP Agent Orchestrator e i dati del profilo cliente in tempo reale per delineare opzioni personalizzate e consigli rilevanti per la fedeltà tramite la finestra di dialogo guidata a più turni. Questo è lo schema giusto quando l’obiettivo è il rilevamento interattivo e conversazionale a più turni che si basa su una decisione di prenotazione complessa, distinta dalla messaggistica attivata da eventi, che reagisce alle azioni dei viaggiatori discreti con un’estensione unidirezionale, e dalle esperienze web personalizzate, che presentano consigli passivi senza coinvolgere l’ospite in un dialogo. Richiede la configurazione di AEP Agent Orchestrator e della governance del brand.

### Considerazioni tecniche

- I dati sulla disponibilità e sulla tariffa devono essere mantenuti aggiornati attraverso un’integrazione quasi in tempo reale tra il sistema di prenotazione e il livello di contenuto di Brand Concierge, in quanto la raccomandazione di tipi di camera non disponibili o di prezzi errati all’interno di una conversazione erode immediatamente l’affidabilità.
- La ricerca del profilo cliente in tempo reale deve evidenziare il livello di fedeltà, la cronologia del soggiorno e le preferenze dichiarate, in modo che l’agente possa riconoscere proattivamente lo stato dell’ospite e personalizzare le raccomandazioni senza richiedere all’ospite di spiegare nuovamente le sue preferenze a ogni visita.
- La governance del brand deve definire il modo in cui l’agente gestisce le richieste di corrispondenza tariffaria, i riferimenti dei concorrenti e le situazioni in cui le date preferite dell’ospite o il tipo di camera non sono disponibili, garantendo che l’agente risponda agevolmente all’interno della voce del brand anziché presentare un vicolo cieco.
- I segnali di intento conversazionale, tra cui l’interesse della destinazione, la composizione del gruppo di viaggio e le preferenze accessorie espresse durante la finestra di dialogo, devono rifluire in AEP come dati ExperienceEvent, arricchendo i profili degli ospiti per informare le campagne e-mail a valle, fedeltà e ricoinvolgimento.
