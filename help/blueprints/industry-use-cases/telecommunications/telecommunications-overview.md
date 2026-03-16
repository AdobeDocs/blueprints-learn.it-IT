---
title: Casi d'uso delle telecomunicazioni
description: Scopri come le aziende di telecomunicazioni utilizzano Adobe Experience Platform per ridurre l’abbandono, promuovere gli aggiornamenti dei dispositivi e migliorare il coinvolgimento dei clienti.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2295'
ht-degree: 1%

---


# Casi d&#39;uso delle telecomunicazioni

Le società di telecomunicazioni utilizzano Adobe Experience Platform per creare una visione unificata di ciascun abbonato e fornire esperienze personalizzate che riducono l&#39;abbandono, aumentano gli aggiornamenti del piano e dei dispositivi e rafforzano le relazioni a lungo termine con i clienti. Collegando i dati di utilizzo della rete, le informazioni di fatturazione e le interazioni con i clienti, i fornitori di telecomunicazioni possono anticipare le esigenze degli abbonati e coinvolgerli al momento giusto attraverso i loro canali preferiti.

## Consigli per l&#39;aggiornamento dei dispositivi

Identifica i clienti idonei per gli aggiornamenti dei dispositivi e presenta consigli personalizzati sui dispositivi e offerte di aggiornamento in base a modelli di utilizzo e preferenze. Analizzando le tempistiche dei contratti, l&#39;età dei dispositivi e il comportamento di navigazione individuale, i provider di telecomunicazioni possono fornire i dispositivi e le opzioni di finanziamento più rilevanti a ciascun abbonato.

### Impatto aziendale

Le organizzazioni che implementano i consigli per l’aggiornamento dei dispositivi registrano in genere un aumento del 30-40% nei tassi di conversione dell’aggiornamento, fornendo l’offerta giusta al momento giusto attraverso il canale preferito dal cliente.

### Come implementare

Utilizza il pattern [Cross-Channel Percorsi with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) per orchestrare percorsi di aggiornamento che valutino l&#39;idoneità di ogni abbonato, le preferenze del dispositivo e l&#39;affinità dei canali, in modo da fornire offerte di aggiornamento personalizzate per e-mail, notifiche dell&#39;app ed esperienze in-store.

### Considerazioni tecniche

- Integrare l&#39;inventario dei dispositivi e i sistemi di determinazione dei prezzi per garantire che i consigli riflettano la disponibilità corrente e i prezzi promozionali.
- Connetti i dati di gestione dei contratti per identificare con precisione le finestre di idoneità all’aggiornamento e le offerte di aggiornamento anticipato.
- Incorpora la telemetria dell’utilizzo del dispositivo (capacità di archiviazione, stato della batteria, metriche delle prestazioni) per rafforzare la rilevanza dei consigli.
- Coordinati con le piattaforme di vendita al dettaglio ed e-commerce per mantenere un’esperienza di aggiornamento coerente tra i canali digitali e in-store.


## Pianificare campagne di ottimizzazione

Analizza i pattern di utilizzo dei clienti e consiglia modifiche ottimali del piano per risparmiare denaro o ottenere funzioni migliori in base alle loro esigenze effettive. Raggiungere in modo proattivo le raccomandazioni del piano crea fiducia e riduce il rischio che gli abbonati abbandonino per i concorrenti con prezzi più semplici.

### Impatto aziendale

Le campagne di ottimizzazione dei piani in genere determinano un aumento del 25-35% dei tassi di modifica dei piani, migliorando la soddisfazione dei clienti e aumentando al contempo il reddito medio per utente quando gli abbonati passano a piani che corrispondono meglio al loro consumo.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) per creare una campagna multi-touch che identifichi le incongruenze tra utilizzo e pianificazione, istruisca gli abbonati sulle opzioni migliori e li guidi attraverso il processo di modifica del piano con follow-up tempestivi.

### Considerazioni tecniche

- Acquisisci dati di utilizzo storici e in tempo reale (minuti vocali, consumo di dati, chiamate internazionali) per identificare con precisione le mancate corrispondenze del piano.
- Connetti i dati del sistema di fatturazione per calcolare i risparmi potenziali o i guadagni delle funzionalità per ogni modifica del piano consigliata.
- Tenere conto delle regole di determinazione prezzi promozionali e degli obblighi contrattuali durante la generazione delle raccomandazioni del piano.
- Integrazione con i portali self-service per consentire agli abbonati di completare le modifiche al piano direttamente dai punti di contatto della campagna.


## Prevenzione dell’abbandono per clienti di alto valore

Identifica i clienti di alto valore a rischio di abbandono e coinvolgili con offerte di conservazione personalizzate e servizi proattivi per i clienti. Combinando segnali comportamentali come il declino dell’utilizzo, chiamate di servizio ripetute e navigazione competitiva con dati sul valore del ciclo di vita, i provider possono intervenire prima che un abbonato decida di partire.

### Impatto aziendale

I programmi di prevenzione dell’abbandono rivolti agli abbonati di alto valore raggiungono in genere una riduzione del 20-30% dell’abbandono, proteggendo ricavi ricorrenti significativi e riducendo i costi di acquisizione dei clienti sostitutivi.

### Come implementare

Utilizza il pattern [Cross-Channel Percorsi with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) per monitorare i segnali di rischio di abbandono in tempo reale, determinare l&#39;offerta di conservazione migliore per ogni abbonato e orchestrare attività di sensibilizzazione personalizzate tra i canali digitali e il call center.

### Considerazioni tecniche

- Crea punteggi di propensione di abbandono combinando le tendenze di utilizzo, la cronologia delle interazioni dei servizi e i dati di sentiment dalle trascrizioni dei call center.
- Integrare i sistemi di call center e retail in modo che gli agenti abbiano visibilità sulle offerte di fidelizzazione già presentate attraverso i canali digitali.
- Collega i dati di intelligence sulla concorrenza (richieste di esclusione, confronti tra piani della concorrenza) per perfezionare il punteggio di rischio e le strategie di offerta.
- Stabilisci regole di governance per evitare il contatto eccessivo degli abbonati a rischio, che può accelerare l’abbandono invece di impedirlo.


## Nuovo Percorso di onboarding del cliente

Automatizza un percorso di onboarding personalizzato per i nuovi clienti con informazioni di benvenuto, indicazioni sulla configurazione dell’account e tutorial sulle funzioni. Un’esperienza di onboarding strutturata aiuta gli abbonati a scoprire rapidamente il valore completo del loro piano e dei loro servizi, gettando le basi per la conservazione a lungo termine.

### Impatto aziendale

I percorsi di onboarding ben progettati aumentano in genere le percentuali di attivazione delle funzioni del 50-60%, portando a punteggi di soddisfazione più elevati e a un calo dell’abbandono scolastico tra i nuovi abbonati.

### Come implementare

Utilizza il pattern [Multi-Step Orchestrated Percorsi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) per creare un&#39;esperienza di onboarding in sequenza che si adatta in base al tipo di piano, al dispositivo e al coinvolgimento di ogni abbonato con i passaggi di onboarding precedenti.

### Considerazioni tecniche

- Integra i sistemi di provisioning dell’account per attivare il percorso di onboarding immediatamente dopo l’attivazione e personalizza i contenuti in base al piano e al dispositivo specifici dell’abbonato.
- Connetti i dati di coinvolgimento dell’app per tenere traccia delle funzioni esaminate dall’abbonato e modificare di conseguenza i messaggi di onboarding successivi.
- Coordina con la piattaforma di assistenza clienti per assicurarti che gli agenti siano a conoscenza della fase di onboarding di un abbonato in caso di domande.
- Supporto di più percorsi di onboarding per diversi segmenti di clienti, ad esempio singoli abbonati, amministratori di family plan e account aziendali.


## Avvisi e raccomandazioni sull’utilizzo dei dati

Invia avvisi personalizzati quando i clienti si avvicinano ai limiti di dati e consiglia aggiornamenti del piano o componenti aggiuntivi dati in base a modelli di utilizzo. Notifiche tempestive e utili trasformano un’esperienza potenzialmente frustrante in un momento di coinvolgimento nel rafforzamento della fiducia.

### Impatto aziendale

Gli avvisi proattivi sull’utilizzo dei dati determinano in genere un aumento del 40-50% degli acquisti di componenti aggiuntivi dati, riducendo al contempo i reclami per shock sulle fatture e migliorando la soddisfazione complessiva dei clienti.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) per inviare avvisi in tempo reale quando vengono superate le soglie di utilizzo, con consigli personalizzati basati sui modelli di consumo cronologici e sui dettagli del piano del sottoscrittore.

### Considerazioni tecniche

- Connettersi ai feed di dati di utilizzo della rete che forniscono aggiornamenti del consumo quasi in tempo reale per attivare gli avvisi a soglie significative (75%, 90%, 100% dei limiti del piano).
- Integra i sistemi di fatturazione e di gestione dei piani per presentare prezzi aggiuntivi accurati e consentire acquisti con un solo tocco direttamente dal messaggio di avviso.
- Tenere conto dei pool di dati condivisi sui piani familiari avvisando sia il singolo utente che l&#39;amministratore del piano.
- Implementa il limite di frequenza per evitare il rischio di avvisi per gli abbonati che utilizzano in modo coerente grandi quantità di dati per ogni ciclo di fatturazione.


## Notifiche di interruzione del servizio

Avvisa in modo proattivo i clienti in caso di interruzioni del servizio, manutenzione o problemi di rete nella loro area con aggiornamenti personalizzati e offerte di rimborso. Raggiungere un contatto prima che i clienti si sentano frustrati dimostra responsabilità e riduce in modo significativo il volume di supporto in entrata.

### Impatto aziendale

Le notifiche proattive di interruzione delle attività raggiungono in genere un tasso di riconoscimento delle notifiche del 60-70% e riducono notevolmente il volume del call center durante le interruzioni del servizio, riducendo i costi di supporto e migliorando la percezione dei clienti.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) per rilevare gli eventi di rete e avvisare immediatamente gli abbonati interessati tramite i loro canali preferiti con dettagli rilevanti, tempi di risoluzione stimati e, se garantito, una compensazione appropriata.

### Considerazioni tecniche

- Integrazione con i sistemi di monitoraggio dei centri operativi di rete per ricevere in tempo reale i dati relativi alle interruzioni e agli eventi di manutenzione con informazioni relative all&#39;area geografica.
- Utilizza l’indirizzo dell’abbonato e i dati sulla posizione per identificare con precisione i clienti interessati ed evitare di avvisare quelli al di fuori dell’area interessata.
- Connettiti al sistema di fatturazione e crediti per automatizzare le offerte di credito del servizio per interruzioni prolungate in base al piano dell’abbonato e alla durata dell’interruzione.
- Coordina i messaggi tra i canali per fornire aggiornamenti di stato coerenti ed evitare l’invio di informazioni in conflitto in base all’evolversi della situazione.


## Gestione Family Plan

Personalizzare comunicazioni e offerte per gli amministratori di family plan in base ai modelli di utilizzo della famiglia e alle esigenze dei singoli membri. I piani di famiglia rappresentano account multi-linea di alto valore in cui il coinvolgimento con l&#39;amministratore del piano determina la conservazione su tutte le linee.

### Impatto aziendale

Le comunicazioni personalizzate per la gestione dei piani familiari in genere aumentano il coinvolgimento del piano familiare del 30-40%, portando a una maggiore conservazione della linea e a un maggiore valore del ciclo di vita per ogni account.

### Come implementare

Utilizza il pattern [Cross-Channel Percorsi with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) per analizzare l&#39;utilizzo tra tutti i membri della famiglia, identificare opportunità quali l&#39;aggiunta di righe o la regolazione di singoli limiti e fornire consigli personalizzati all&#39;amministratore del piano.

### Considerazioni tecniche

- Modellare le gerarchie di account della famiglia per distinguere l&#39;amministratore del piano dai singoli membri, rispettando i livelli di autorizzazione per le comunicazioni e le modifiche all&#39;account.
- Aggrega i dati di utilizzo su tutte le linee dell’account per identificare pattern e opportunità a livello di famiglia, ad esempio dati condivisi sottoutilizzati o cicli di aggiornamento dei dispositivi irregolari.
- Integra i sistemi di controllo genitori e di filtraggio dei contenuti per supportare funzioni specifiche per la famiglia nella personalizzazione.
- Assicurati che siano presenti i controlli sulla privacy in modo che i dettagli sull’utilizzo dei singoli membri vengano condivisi in modo appropriato con l’amministratore del piano in base alle autorizzazioni dell’account.


## Campagne di aggiornamento 5G

Clienti idonei agli aggiornamenti di rete 5G con offerte e vantaggi personalizzati in base alla posizione e ai modelli di utilizzo. Con l&#39;espansione della copertura 5G, raggiungere gli abbonati in aree coperte di recente con messaggi pertinenti accelera l&#39;adozione e aumenta l&#39;utilizzo della rete.

### Impatto aziendale

Le campagne mirate di aggiornamento del 5G in genere determinano un aumento del 25-35% dei tassi di adozione del 5G tra gli abbonati idonei, sostenendo i rendimenti degli investimenti nella rete e la differenziazione competitiva.

### Come implementare

Utilizza il pattern [Batch Outbound Message Activation](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) per segmentare gli abbonati in base alla disponibilità della copertura 5G, alla compatibilità del dispositivo e all&#39;idoneità del piano, quindi distribuisci campagne di aggiornamento personalizzate che evidenziano i vantaggi più rilevanti per il profilo di utilizzo di ogni abbonato.

### Considerazioni tecniche

- Integrare le mappe di copertura della rete per identificare con precisione gli abbonati nelle aree con servizio 5G attivo ed evitare di promuovere aggiornamenti in cui la copertura non è ancora disponibile.
- Collegare i dati di compatibilità dei dispositivi per determinare quali abbonati necessitano di un nuovo dispositivo rispetto a quelli che dispongono già di hardware con capacità 5G.
- Coordina con i sistemi di inventario al dettaglio per garantire che i dispositivi e i piani promossi siano disponibili nel negozio preferito dell’abbonato o online.
- La messaggistica dei segmenti in base al profilo di utilizzo consente agli utenti di dati pesanti di ottenere vantaggi incentrati sulle prestazioni, mentre gli utenti occasionali ricevono copertura e messaggistica di affidabilità.


## Promemoria pagamenti fatture

Invia promemoria personalizzati per il pagamento delle fatture tramite i canali preferiti con opzioni di pagamento e informazioni sul saldo del conto. Promemoria tempestivi e pratici riducono i ritardi di pagamento e i relativi costi di riscossione, mantenendo al contempo positiva la relazione con il cliente.

### Impatto aziendale

I promemoria personalizzati per il pagamento delle fatture in genere migliorano le percentuali di pagamento puntuale del 20-30%, riducendo le spese di riscossione e riducendo al minimo le sospensioni del servizio che causano insoddisfazione dei clienti.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) per inviare promemoria in tempi ottimali prima della data di scadenza, personalizzati con il saldo dell&#39;abbonato, il metodo di pagamento preferito e un collegamento diretto per completare il pagamento.

### Considerazioni tecniche

- Integrazione con la piattaforma di fatturazione per accedere ai saldi dei conti in tempo reale, alle date di scadenza e alla cronologia dei pagamenti per ottenere contenuti di promemoria accurati.
- Connettiti ai sistemi di elaborazione dei pagamenti per abilitare il pagamento con un solo tocco o con un solo clic direttamente dal messaggio di promemoria.
- Implementa una logica di escalation che regola l’urgenza e la frequenza del promemoria con l’avvicinarsi della data di scadenza, nel rispetto delle preferenze di comunicazione.
- Supporta più metodi di pagamento (iscrizione al pagamento automatico, portafoglio digitale, bonifico bancario) e personalizza le opzioni presentate in base alla cronologia dell’abbonato.


## Consigli per il servizio aggiuntivo

Consiglia servizi aggiuntivi rilevanti come assicurazione sui dispositivi, archiviazione cloud e bundle di streaming in base al piano, all’utilizzo e alle preferenze del cliente. I consigli contestuali aumentano il valore che gli abbonati ricevono dalla loro relazione con il fornitore, mentre cresce il ricavo medio per utente.

### Impatto aziendale

I consigli personalizzati sul servizio aggiuntivo determinano in genere un aumento del 15-25% nei tassi di adozione dei componenti aggiuntivi, aumentando i ricavi dalla base di abbonati esistente senza il costo di acquisizione di nuovi clienti.

### Come implementare

Utilizza il pattern [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) per valutare il profilo di ogni abbonato, i servizi correnti e i segnali comportamentali per determinare l&#39;offerta del componente aggiuntivo più rilevante e presentarla attraverso il canale e il momento ottimali.

### Considerazioni tecniche

- Connettiti al catalogo dei servizi corrente dell’abbonato per evitare di consigliare i servizi che già dispone e per identificare i complementi naturali del loro piano esistente.
- Integra i dati dei partner e dei servizi di terze parti (fornitori di streaming, vettori assicurativi) per presentare prezzi accurati e offerte in bundle.
- Utilizza i dati sul dispositivo e sull’utilizzo per fornire consigli, ad esempio suggerendo un’assicurazione sui dispositivi per gli abbonati che dispongono di nuovi dispositivi premium o di archiviazione cloud per coloro che sono a corto di spazio di archiviazione sul dispositivo.
- Coordinati con la personalizzazione in-app e web per rafforzare i consigli sui componenti aggiuntivi in tutti i punti di contatto self-service.


## Personalization delle prestazioni di rete

Personalizzare le informazioni sulle prestazioni di rete e i consigli in base alla posizione, al dispositivo e ai modelli di utilizzo del cliente. Aiutando gli abbonati a ottimizzare la loro esperienza di connettività, si crea fiducia e si riducono i contatti di supporto associati ai problemi di prestazioni.

### Impatto aziendale

Le esperienze di prestazioni di rete personalizzate in genere aumentano il coinvolgimento dell’app del 35-45%, in quanto gli abbonati tornano a controllare la copertura, risolvere i problemi e scoprire suggerimenti di ottimizzazione su misura per la loro situazione.

### Come implementare

Utilizza il modello [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) per fornire dashboard personalizzati sulle prestazioni della rete, informazioni sulla copertura e consigli per l&#39;ottimizzazione nell&#39;esperienza dell&#39;app e dell&#39;account Web dell&#39;utente iscritto.

### Considerazioni tecniche

- Integrare le metriche di qualità della rete e i dati di copertura per fornire informazioni sulle prestazioni specifiche della posizione relative alla casa, al lavoro e alle aree visitate di frequente dell&#39;utente.
- Connetti i dati di diagnostica del dispositivo per offrire consigli personalizzati sulla risoluzione dei problemi in base al modello di dispositivo e alla versione del software specifici dell’abbonato.
- Utilizza i servizi edge di [!DNL Adobe Experience Platform] per fornire personalizzazione a bassa latenza nell&#39;esperienza dell&#39;app senza influire sulle prestazioni.
- Implementa i cicli di feedback in modo che gli abbonati possano segnalare i problemi di copertura, arricchendo i dati di rete e dimostrando al contempo la reattività alla loro esperienza.


## Coinvolgimento programma fedeltà

Personalizza comunicazioni, premi e offerte del programma fedeltà in base al livello, al saldo dei punti e alla cronologia dei rimborsi del cliente. Un’esperienza di fidelizzazione ben personalizzata rafforza la connessione emotiva con il brand e crea costi di passaggio significativi oltre i termini del contratto.

### Impatto aziendale

Il coinvolgimento personalizzato nel programma di fidelizzazione aumenta in genere la partecipazione al programma e il rimborso dei premi del 30-40%, aumentando i tassi di fidelizzazione tra gli abbonati iscritti.

### Come implementare

Utilizza il pattern [Cross-Channel Percorsi with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) per orchestrare comunicazioni personalizzate sulla fidelizzazione che evidenzino i premi rilevanti, avvisino gli abbonati dell&#39;avanzamento del livello e presentino opportunità di rimborso allineate alle loro preferenze e ai loro comportamenti.

### Considerazioni tecniche

- Integra la piattaforma fedeltà per accedere ai saldi dei punti in tempo reale, allo stato dei livelli e alla cronologia dei rimborsi per una personalizzazione accurata.
- Collega i cataloghi di premi dei partner per presentare un&#39;ampia gamma di opzioni di rimborso su misura per gli interessi dimostrati di ogni abbonato e i rimborsi passati.
- Coordina i messaggi di fidelizzazione con altri percorsi di campagne per garantire la complementarità tra le offerte di fidelizzazione e i premi fedeltà, piuttosto che creare conflitti tra di loro.
- La progressione del livello di supporto si sposta calcolando la vicinanza di un abbonato al livello successivo e presentando i passaggi utilizzabili per raggiungerlo.
