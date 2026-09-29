---
title: Casi di utilizzo dei servizi finanziari
description: Scopri come le organizzazioni di servizi finanziari utilizzano Adobe Experience Platform per personalizzare le offerte di prodotti, evitare l’abbandono e approfondire le relazioni con i clienti.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: 1f22d684-11bd-473d-8b10-5f88cb0cd088
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
    internal-label: Real-Time Customer Data Platform
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
    internal-label: Journey Optimizer
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '4039'
ht-degree: 0%
---
# Casi di utilizzo dei servizi finanziari

Le organizzazioni di servizi finanziari si affidano a Adobe Experience Platform per unificare i dati dei clienti attraverso i canali bancari, di prestito e di investimento, consentendo esperienze personalizzate che rafforzano le relazioni e stimolano la crescita. Riunendo l&#39;attività dell&#39;account, la cronologia delle transazioni e i segnali comportamentali, queste organizzazioni possono fornire l&#39;offerta giusta al momento giusto mantenendo la fiducia e la conformità che i clienti si aspettano.

## Lead Sturturing di alto valore

Identifica i potenziali clienti di alto valore in base ai dati e al comportamento del profilo, quindi coltiva i potenziali clienti con contenuti e offerte personalizzati tramite percorsi automatizzati. Combinando i dettagli demografici, l’attività di navigazione e i segnali di coinvolgimento, le istituzioni finanziarie possono dare priorità ai lead più propensi a convertirli e guidarli attraverso un percorso personalizzato per diventare clienti.

### Impatto aziendale

Le organizzazioni che implementano lo sviluppo di lead di alto valore vedono tassi di conversione più elevati tra lead e clienti e nel contempo creano una pipeline di vendita più sana e prevedibile.

### Come implementare

Utilizza il pattern [Multi-Step Orchestrated Percorsi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) per creare sequenze di sviluppo automatizzate che si adattano in base ai segnali di coinvolgimento e preparazione del potenziale cliente. Questo è il modello corretto quando il caso d’uso richiede un flusso di messaggi sequenziale e multiplo nell’arco di giorni con diramazioni condizionali basate su metriche di coinvolgimento: un singolo messaggio attivato non può soddisfare la logica di sviluppo adattivo o la logica di dipendenza tra i passaggi di qualifica.

### Considerazioni tecniche

- Integra i dati CRM di lead-scoring e gli eventi comportamentali del sito web nei profili di potenziale cliente unificati per potenziare la logica di ingresso nel percorso e diramazione.
- Assicurati che il consenso e le preferenze di consenso siano applicati in ogni punto di contatto, in particolare per l’estensione tramite telefono ed e-mail disciplinata dalle normative di marketing finanziario.
- Configura la limitazione del percorso per evitare di sopraffare i potenziali clienti con più comunicazioni durante brevi finestre di valutazione.
- Tenere conto della latenza dei dati tra le interazioni di filiali o consulenti e dell’impegno digitale per mantenere pertinenti i messaggi di crescita.


## Consigli di prodotto per clienti esistenti

Consigliare prodotti finanziari pertinenti, come carte di credito, prestiti e prodotti di investimento, ai clienti esistenti in base al loro profilo, alla cronologia delle transazioni e allo stadio di vita. Questo caso d’uso trasforma i dati degli account quotidiani in informazioni fruibili che rivelano il miglior prodotto successivo per ogni cliente.

### Impatto aziendale

I consigli di prodotti personalizzati aumentano i tassi di adozione dei prodotti e aumentano in modo misurabile il valore del ciclo di vita dei clienti aumentando la quota di portafoglio.

### Come implementare

Utilizza il pattern [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) per valutare ogni cliente in base alle offerte di prodotti idonee in tempo reale, classificando i consigli in base alla rilevanza e alla priorità aziendale. Questo è il modello corretto quando la selezione delle offerte deve tenere conto delle regole di idoneità finanziaria e dei vincoli di idoneità normativa, vincoli che richiedono una logica decisionale regolamentata anziché una classificazione di affinità comportamentale da sola.

### Considerazioni tecniche

- Unifica i dati delle transazioni, i saldi contabili e i prodotti in un unico profilo cliente in modo che i modelli decisionali abbiano una visione completa delle relazioni esistenti.
- Applica le regole di idoneità finanziaria e i vincoli di idoneità normativa come protezioni rigide all’interno del motore decisionale prima di classificare le offerte.
- Coordina la consegna delle offerte tra i canali online banking, app mobile, e-mail e advisor per evitare conflitti o duplicazioni delle raccomandazioni.
- Implementa un limite di frequenza per categoria di prodotto per evitare l’affaticamento delle raccomandazioni, in particolare per i prodotti ad alta considerazione come i mutui e i conti di investimento.


## Campagne di prevenzione dell’abbandono

Identifica i clienti a rischio di abbandono utilizzando la previsione di abbandono basata sull’intelligenza artificiale e coinvolgili con offerte di fidelizzazione e comunicazioni personalizzate. L&#39;individuazione precoce dei segnali di disimpegno consente alle istituzioni finanziarie di intervenire prima che un cliente chiuda i conti o trasferisca le attività altrove.

### Impatto aziendale

Gli sforzi proattivi di prevenzione dell’abbandono aiutano a ridurre l’attrito dei clienti, proteggendo i flussi di reddito ricorrenti e riducendo il costo della sostituzione dei clienti.

### Come implementare

Utilizza il pattern [Cross-Channel Percorsi with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) per attivare i percorsi di conservazione quando i punteggi dei rischi di abbandono superano le soglie definite, con decisioni incorporate per selezionare l&#39;offerta di conservazione più convincente. Questo è il modello corretto quando il percorso deve coordinare la distribuzione tra i canali per evitare offerte di conservazione duplicate e quando la selezione dell’offerta richiede soglie di punteggio dei rischi e vincoli di business. L’orchestrazione in più passaggi non fornisce di per sé il livello decisionale in tempo reale necessario per selezionare l’offerta di conservazione ottimale per cliente.

### Considerazioni tecniche

- Le tendenze dell&#39;attività dell&#39;account di feed, la cronologia delle interazioni del servizio e la frequenza di coinvolgimento vengono inserite in [!DNL Customer AI] modelli di propensione di abbandono per generare punteggi di rischio.
- Definire soglie di rischio di abbandono specifiche per le linee di prodotto, poiché i segnali di disimpegno per il controllo dei conti differiscono da quelli per i portafogli di investimento.
- Rivedi i criteri di targeting e soppressione con i team legali e di privacy per garantire la conformità alle normative applicabili in materia di prestito equo e parità di trattamento prima di attivare le offerte di conservazione.
- Sviluppa una logica di soppressione per escludere i clienti che abbandonano a causa di azioni di frode o conformità, dove l’estensione della conservazione sarebbe inappropriata.


## Dashboard account personalizzato

Personalizza la dashboard di online banking e l’esperienza delle app mobili in base all’attività dell’account, alle preferenze e agli obiettivi finanziari di ciascun cliente. Una dashboard personalizzata consente ai clienti di individuare ciò che conta di più e di ottenere informazioni rilevanti senza richiedere di effettuare ricerche.

### Impatto aziendale

Le dashboard personalizzate aumentano i tassi di coinvolgimento e migliorano in modo significativo i punteggi di soddisfazione dei clienti, rendendo il digital banking intuitivo e pertinente.

### Come implementare

Utilizza il pattern [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) per distribuire blocchi di contenuti personalizzati in tempo reale, riflettori sui prodotti e informazioni finanziarie nelle esperienze digitali autenticate. Questo è il modello corretto quando la personalizzazione è guidata dagli attributi di profilo e dall’attività dell’account anziché da un modello di affinità comportamentale e quando la latenza dei secondi secondari è fondamentale per l’esperienza utente.

### Considerazioni tecniche

- Utilizza [!DNL Edge Network] per le decisioni di personalizzazione di secondo secondario nelle sessioni bancarie autenticate in cui la latenza influisce direttamente sull&#39;esperienza utente.
- Aggrega i dati delle transazioni in attributi di profilo precalcolati, ad esempio categorie di spesa e tendenze di risparmio, per evitare il calcolo in tempo reale di set di dati di grandi dimensioni.
- Rispetta gli standard di accessibilità e assicurati che i contenuti personalizzati soddisfino gli stessi requisiti normativi di informativa dei contenuti statici.
- Coordina la logica di personalizzazione tra canali web e mobili in modo che i clienti possano vedere un’esperienza coerente indipendentemente dal dispositivo.


## Offerte di prodotti basate su Life Stage

Identifica i clienti che entrano in nuove fasi della vita come matrimonio, acquisto di una casa o pensione e offre in modo proattivo prodotti e servizi finanziari pertinenti. L&#39;anticipazione di queste tappe fondamentali consente alle istituzioni di posizionarsi come partner di fiducia nei momenti finanziari cruciali.

### Impatto aziendale

Le offerte attivate dalla fase di vita ottengono tassi di adozione dei prodotti più elevati, superando le campagne generiche e rafforzando nel contempo le relazioni con i clienti a lungo termine.

### Come implementare

Utilizza il pattern [Cross-Channel con Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) per rilevare gli indicatori della fase di vita e orchestrare percorsi multi-touch con una selezione di offerte incorporata personalizzata per ogni fase cardine. Questo è il modello giusto quando il percorso deve coordinare la distribuzione tra i canali durante i momenti finanziari principali e quando la selezione dell’offerta richiede controlli di idoneità e regole aziendali: l’orchestrazione in più passaggi non fornisce da sola il livello decisionale necessario per garantire la conformità e la rilevanza.

### Considerazioni tecniche

- Combina segnali di prime parti come modifiche di indirizzi, aperture di conti congiunti e depositi di grandi dimensioni con dati di terze parti autorizzati per dedurre le transizioni nelle fasi di vita.
- Gestisci gli eventi di vita sensibili con attenzione nel tono e nella frequenza dei messaggi, in quanto le milestone erroneamente dedotte possono erodere la fiducia.
- L’idoneità normativa dello strato viene verificata in offer decisioning in modo che i prodotti consigliati siano in linea con la situazione finanziaria verificata del cliente.
- Crea periodi di raffreddamento tra le campagne della fase &quot;vita&quot; per evitare la sovrapposizione dell’attività quando più indicatori si attivano in una breve finestra.


## Avvisi e consigli basati sulle transazioni

Invia avvisi in tempo reale per le transazioni e fornisci consigli personalizzati in base ai pattern di spesa e all’attività dell’account. Notifiche tempestive e pertinenti mantengono i clienti informati e creano momenti naturali per far emergere indicazioni finanziarie utili.

### Impatto aziendale

Gli avvisi basati sulle transazioni aumentano il coinvolgimento, migliorando la consapevolezza della sicurezza e creando punti di contatto di alto valore per consigli personalizzati.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) per rispondere agli eventi delle transazioni in tempo reale con avvisi e consigli contestualmente rilevanti. Questo è lo schema giusto quando l&#39;attivatore è un evento di sistema piuttosto che un comportamento del cliente e quando la comunicazione richiesta è immediata e reattiva piuttosto che una sequenza di acquisizione sostenuta — la latenza dell&#39;avviso influisce direttamente sull&#39;efficacia della sicurezza.

### Considerazioni tecniche

- Acquisire eventi di transazione tramite una pipeline di streaming con requisiti di distribuzione a bassa latenza, poiché gli avvisi di sicurezza perdono valore se ritardati di più di pochi minuti.
- Applica le preferenze e le soglie degli avvisi definiti dal cliente in modo che le notifiche riflettano le singole impostazioni anziché le regole uguali per tutti.
- Separa gli avvisi di sicurezza obbligatori dai messaggi di consiglio facoltativi nell’architettura di messaggistica per garantire che le notifiche di conformità non vengano mai eliminate.
- Tenere conto degli elevati volumi di transazioni durante i periodi di picco, ad esempio i giorni lavorativi e le festività, progettando una capacità di throughput scalabile in base alla domanda.


## Recupero abbandono richiesta carta di credito

Identifica i clienti che hanno iniziato ma non hanno completato le applicazioni per le carte di credito e coinvolgili nuovamente con messaggi e offerte personalizzati. L’abbandono delle applicazioni rappresenta un pubblico con intenti elevati che spesso ha bisogno solo di un piccolo spintone per completare il processo.

### Impatto aziendale

Le campagne di recupero degli abbandoni migliorano i tassi di completamento delle applicazioni, aumentando direttamente l’acquisizione di nuovi account da parte di un pubblico che ha già espresso interesse.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) per rilevare gli eventi di abbandono delle applicazioni e attivare messaggi di follow-up tempestivi che rispondono a motivi comuni di abbandono. Si tratta del modello corretto quando l&#39;attivazione è un&#39;azione del cliente discreta (abbandono) e la risposta richiesta è un messaggio sensibile al tempo consegnato prima che i dati dell&#39;applicazione diventino obsoleti. Una sequenza in più fasi non può soddisfare l&#39;urgenza e la finestra di ripristino ristretta.

### Considerazioni tecniche

- Acquisisci il passaggio specifico in cui l’applicazione è stata abbandonata per adattare la messaggistica, in quanto una persona che ha abbandonato al momento della verifica dell’identità ha bisogno di una rassicurazione diversa rispetto a una che ha abbandonato al momento della revisione dei termini.
- Prima della distribuzione, collaborare con i team legali e di conformità per verificare che tutte le comunicazioni di ripristino soddisfino i requisiti di divulgazione di marketing del credito e le regole di consenso specifiche per il canale.
- Implementare la logica di decadimento temporale in modo che l&#39;estensione del ripristino si interrompa dopo una finestra definita, poiché i dati non aggiornati dell&#39;applicazione potrebbero non essere più validi per la prequalificazione.
- Coordinarsi con il sistema dell&#39;applicazione per eliminare i messaggi di recupero per i richiedenti che hanno completato tramite un canale diverso, ad esempio una visita presso una filiale o una telefonata.


## Raccomandazioni Portfolio per gli investimenti

Fornisci consigli di investimento personalizzati in base al profilo di rischio di ciascun cliente, alla cronologia degli investimenti e agli obiettivi finanziari. Le linee guida del portfolio basate sui dati aiutano i clienti a prendere decisioni informate approfondendo il coinvolgimento con i servizi di gestione patrimoniale.

### Impatto aziendale

I consigli di investimento personalizzati favoriscono una maggiore adozione dei prodotti di investimento e migliorano la diversificazione del portafoglio in tutta la base di clienti.

### Come implementare

Utilizza il pattern [Behavioral Recommendation](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) per analizzare il comportamento e le preferenze di investimento e quindi rendere visibili i consigli di portafoglio pertinenti tramite canali digitali e strumenti di consulenza. Questo è il modello corretto quando l’insieme di elementi (universo di investimento) è di grandi dimensioni e la selezione è guidata dall’affinità comportamentale e dall’allineamento del rischio, piuttosto che un insieme limitato di offerte disciplinate da rigorose regole di idoneità o dal solo processo decisionale per il controllo di idoneità.

### Considerazioni tecniche

- Integra feed di dati di brokeraggio e di custodia per mantenere una visualizzazione accurata e aggiornata delle attuali partecipazioni e allocazioni di ciascun cliente.
- Applicare i requisiti di idoneità imposti dalle normative sui titoli in modo che le raccomandazioni siano in linea con gli obiettivi documentati di investimento e tolleranza al rischio del cliente.
- Etichettare chiaramente i contenuti di investimento personalizzati come formativi o informativi laddove necessario, distinguendoli dalla consulenza formale in materia di investimenti che comporta obblighi fiduciari.
- Aggiorna regolarmente i modelli di consigli per tenere conto delle variazioni di mercato, della deriva del portafoglio e dei cambiamenti negli obiettivi dei clienti.


## Personalization avviso frodi

Personalizza gli avvisi di frode e le comunicazioni di sicurezza in base alle preferenze di comunicazione di ogni cliente e alla cronologia delle interazioni passate. Gli avvisi personalizzati aumentano la probabilità che i clienti notino, comprendano e agiscano in base alle notifiche di sicurezza critiche.

### Impatto aziendale

Gli avvisi personalizzati per frodi migliorano i tassi di risposta agli avvisi, rafforzando la conformità in materia di sicurezza e riducendo la finestra di esposizione durante le attività sospette.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) per inviare avvisi di frode tramite il canale preferito di ciascun cliente con dettagli contestuali che semplificano la conferma o la contestazione dell&#39;attività. Questo è lo schema giusto quando l&#39;evento scatenante è un evento di sistema piuttosto che un comportamento del cliente e quando la comunicazione richiesta è immediata e reattiva senza tempo per sequenze a più fasi — la latenza dell&#39;allarme è direttamente correlata con l&#39;esposizione a perdite finanziarie.

### Considerazioni tecniche

- Assegna priorità alla velocità di consegna e all’affidabilità rispetto a tutte le altre considerazioni di progettazione, in quanto la latenza dell’avviso di frode è direttamente correlata all’esposizione alle perdite finanziarie.
- Inoltra gli avvisi tramite il canale preferito verificato del cliente mantenendo i canali di fallback per garantire la consegna anche in caso di errore del canale principale.
- Archivia la cronologia delle interazioni degli avvisi per migliorare la rilevanza degli avvisi futuri e ridurre il falso positivo per i clienti che viaggiano frequentemente o effettuano acquisti atipici.
- Assicurati che il contenuto e i flussi di lavoro degli avvisi di frode siano conformi alle normative di sicurezza bancaria e non esporre i dettagli sensibili dell’account nelle anteprime dei messaggi o nelle righe dell’oggetto.


## Coinvolgimento programma fedeltà

Personalizza comunicazioni, premi e offerte del programma fedeltà orchestrando l’arbitrato delle offerte in tempo reale tra servizi bancari online, app mobili, e-mail e canali di filiale per evitare che le offerte fedeltà duplicate o in conflitto raggiungano lo stesso membro simultaneamente. Le regole di idoneità basate su livelli, che definiscono a quali premi, promozioni e opzioni di rimborso può accedere ogni membro, vengono applicate a livello decisionale anziché risolte attraverso la sola segmentazione, garantendo che la selezione dell’offerta rispetti i vincoli del programma su ogni canale. I percorsi di fidelizzazione sono coordinati con campagne di marketing più ampie in modo che le offerte di prodotti e fedeltà non entrino in conflitto, offrendo ai membri un’esperienza coerente anziché messaggi concorrenti.

### Impatto aziendale

Il coinvolgimento personalizzato nella fidelizzazione aumenta la partecipazione al programma e porta a un riscatto dei punti misurabilmente più elevato, rafforzando la percezione del valore del programma.

### Come implementare

Utilizza il modello [Cross-Channel Percorsi con Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) per orchestrare comunicazioni fedeltà tra canali diversi, con decisioning incorporato per selezionare il premio o l&#39;offerta più rilevante per ogni membro. Questo è il modello corretto quando il percorso deve coordinare la distribuzione tra i canali per evitare l’affaticamento dei messaggi e le offerte in conflitto, e quando la selezione delle offerte richiede regole basate su livelli e vincoli dei membri. L’orchestrazione in più passaggi non fornisce di per sé il livello decisionale in tempo reale necessario per rispettare le regole di fedeltà e il trattamento differenziato dei membri.

### Considerazioni tecniche

- Sincronizza i dati della piattaforma fedeltà, tra cui lo stato dei livelli, i saldi dei punti e la cronologia dei rimborsi, nei profili dei clienti in tempo quasi reale per evitare di promuovere saldi scaduti o imprecisi.
- Logica di percorso dei segmenti per livello per fornire esperienze differenziate, in quanto i membri di alto livello si aspettano un trattamento esclusivo e un accesso anticipato alle promozioni.
- Coordina i messaggi di fidelizzazione con campagne di marketing più ampie per evitare l’eccesso di messaggi e le offerte in conflitto tra i programmi.
- Traccia l’attribuzione del rimborso tra i canali per misurare quali comunicazioni personalizzate determinano il maggiore ritorno sull’investimento del programma.


## Campagne di preapprovazione mutui

Puoi indirizzare l’attività ai clienti che potrebbero essere sul mercato di un mutuo sulla base di dati di profilo, segnali comportamentali e indicatori della fase di vita. La preapprovazione proattiva posiziona l&#39;ente come una comoda prima scelta durante una delle più grandi decisioni finanziarie che un cliente prenderà.

### Impatto aziendale

Le campagne mirate di preapprovazione dei mutui aumentano i tassi di applicazione e migliorano il volume di erogazione dei prestiti raggiungendo al momento giusto potenziali qualificati.

### Come implementare

Utilizza il pattern [Multi-Step Orchestrated Percorsi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) per guidare i potenziali clienti ipotecari attraverso una sequenza di sviluppo multi-touch dalla consapevolezza fino alla pre-approvazione, adattandosi in base ai segnali di coinvolgimento e qualifica. Questo è il modello corretto quando il caso d’uso richiede un flusso di messaggi multipli in sequenza su una timeline estesa con diramazioni condizionali basate su segnali di coinvolgimento e qualifica: un singolo messaggio attivato non può essere compatibile con la logica di sviluppo adattivo o il passaggio a processi di applicazione formali.

### Considerazioni tecniche

- Combina il comportamento di ricerca delle proprietà, le tendenze di crescita del risparmio e i segnali di scadenza del leasing per creare un modello di propensione che identifichi i probabili richiedenti mutuo.
- Assicurati che tutti i messaggi di pre-approvazione siano conformi alle normative sulla pubblicità dei mutui, incluse le informazioni richieste, la precisione delle tariffe e un linguaggio per la registrazione degli alloggi uguale.
- Coordinare la tempistica della campagna con le variazioni dell’ambiente dei tassi in modo che l’estensione sia allineata con condizioni di finanziamento favorevoli ed eviti riferimenti ai tassi superati.
- Crea flussi di lavoro di trasferimento per i responsabili del prestito in modo che i corsi nutriti digitalmente conducano agevolmente alla transizione nel processo formale di richiesta e sottoscrizione.


## Contenuti personalizzati di educazione finanziaria

Consegna contenuti, suggerimenti e risorse personalizzati di educazione finanziaria in base al profilo finanziario, agli obiettivi e agli interessi di ogni cliente. I contenuti educativi pertinenti creano fiducia, migliorano l&#39;alfabetizzazione finanziaria e creano opportunità organiche per introdurre prodotti pertinenti.

### Impatto aziendale

I contenuti personalizzati per l’istruzione aumentano i tassi di coinvolgimento nei contenuti e migliorano l’alfabetizzazione finanziaria dei clienti, il che a sua volta favorisce un’adozione più sicura dei prodotti.

### Come implementare

Utilizza il pattern [Cross-Channel Percorsi with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) per distribuire una sequenza curata di contenuti educativi tra canali, utilizzando il decisioning per abbinare gli argomenti alla situazione finanziaria e agli interessi di ogni cliente. Questo è il modello giusto quando il percorso deve coordinare la distribuzione tra i canali con percorsi di apprendimento progressivi e quando la selezione dell’argomento richiede regole di idoneità basate sul profilo finanziario. L’orchestrazione in più passaggi non fornisce da sola il livello decisionale necessario per far corrispondere i contenuti alla situazione finanziaria del cliente o prevenire violazioni dei prerequisiti.

### Considerazioni tecniche

- Mappa i contenuti educativi agli attributi del profilo finanziario, come il rapporto debito/reddito, il tasso di risparmio e l’esperienza di investimento, per garantire la rilevanza dell’argomento.
- Assegna tag ai contenuti con livelli di difficoltà e argomenti prerequisiti per creare percorsi di apprendimento progressivi anziché distribuire articoli una tantum disconnessi.
- Tieni traccia del coinvolgimento dei contenuti a livello di argomento per perfezionare i modelli di personalizzazione e identificare aree di interesse emergenti in tutta la base di clienti.
- Garantire che i contenuti educativi siano chiaramente distinti dal marketing dei prodotti per mantenere la conformità alle normative e preservare la fiducia dei clienti nell&#39;obiettività del programma.


## Guida ai prodotti finanziari di AI

Le organizzazioni di servizi finanziari offrono portafogli di prodotti (conti correnti e di risparmio, carte di credito, prodotti di prestito, opzioni assicurative e veicoli di investimento) che sono difficili da gestire per i clienti senza una guida personalizzata. I vincoli normativi impediscono alle esperienze digitali in prima linea di fornire consigli di investimento personalizzati, ma esiste un valore sostanziale nell’aiutare i clienti a comprendere come funzionano i prodotti, quali account soddisfano le esigenze dichiarate e come fare il passo successivo verso l’applicazione. Una guida ai prodotti finanziari coinvolge i clienti in conversazioni naturali, pone domande mirate sugli obiettivi finanziari e sulla fase di vita e li guida verso i prodotti giusti, senza entrare nel territorio regolamentato della consulenza.

### Impatto aziendale

L&#39;individuazione conversazionale guidata migliora i tassi di avvio delle applicazioni del prodotto e riduce il calo tra la consapevolezza e l&#39;applicazione, acquisendo al contempo segnali di intento che migliorano i flussi di lavoro a valle per l&#39;apprendimento e la consulenza.

### Come implementare

Utilizza il pattern [Esperienza conversazionale di Brand Concierge](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md). Questo approccio distribuisce Product Advisor Agent rispetto alla knowledge base e alla libreria di contenuti dei prodotti approvati, utilizzando AEP Agent Orchestrator e i dati del profilo cliente in tempo reale per guidare i clienti verso i prodotti appropriati attraverso una finestra di dialogo a più turni basata su contenuti governati dal marchio e soggetti a revisione della conformità. Questo è il modello giusto quando l’obiettivo è il rilevamento interattivo e conversazionale a più turni per aiutare i clienti a comprendere e selezionare autonomamente i prodotti finanziari, distinto dalla messaggistica attivata dagli eventi, che è unidirezionale e risponde a eventi account discreti, e dalle esperienze web personalizzate, che presentano i contenuti dei prodotti in modo passivo senza coinvolgere i clienti in un dialogo qualificato. Richiede la configurazione di AEP Agent Orchestrator e della governance del brand.

### Considerazioni tecniche

- I guardrail per la governance del brand devono essere configurati con una revisione legale e di conformità per definire limiti di contenuto rigidi: l’agente deve guidare i clienti verso prodotti adatti in base alle esigenze dichiarate senza costituire consulenza per gli investimenti, e gli argomenti vietati (proiezioni di ritorno specifiche, garanzie, attestazioni di prestazioni comparative) devono essere esplicitamente definiti e applicati.
- Il livello di integrazione dei contenuti deve basarsi su descrizioni dei prodotti, divulgazioni e domande frequenti approvate in termini di conformità, anziché su richieste generate in modo dinamico, garantendo che ogni risposta fornita dall&#39;agente sia stata esaminata dai team legali e normativi prima della distribuzione.
- La ricerca del profilo cliente in tempo reale dovrebbe far emergere i dati della relazione (prodotti esistenti detenuti, durata dell&#39;account e segmenti di clienti) in modo che l&#39;agente possa evitare di raccomandare prodotti già detenuti dal cliente e possa adattare l&#39;orientamento al rapporto esistente tra il cliente e l&#39;ente.
- La consegna dell’agente live deve essere configurata per gli scenari in cui le esigenze del cliente superano l’ambito della guida conversazionale, ad esempio situazioni di prestito complesse o richieste di pianificazione finanziaria personalizzata, con il contesto di conversazione completo trasferito all’advisor ricevente per evitare che il cliente si ripeta.


## Analisi del driver di abbandono e di Funnel per l&#39;adozione del prodotto

Analizza dove i clienti abbandonano durante l’apertura di un account digitale, l’applicazione di un prestito o i flussi di onboarding degli investimenti e identifica i segnali comportamentali che precedono l’attrito del prodotto. Gli istituti finanziari che non vedono questi punti di riconsegna o precursori di abbandono non sono in grado di distinguere tra i fallimenti dell’esperienza del prodotto e l’interdizione, rendendo imprecisi gli sforzi di riparazione.

### Impatto aziendale

Sapere esattamente dove i richiedenti abbandonano i flussi digitali e quali comportamenti precedono la chiusura degli account consente ai team di prodotto e marketing di dare priorità ai miglioramenti delle esperienze che riducono l’abbandono ed estendono il mandato dei clienti.

### Come implementare

Utilizza il pattern [Customer Analytics &amp; Insight Generation](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md). Questo approccio collega i dati comportamentali digitali, i record di gestione delle relazioni con i clienti e i flussi di eventi dei prodotti a Customer Journey Analytics, dove le visualizzazioni di fallout identificano i passaggi di drop-off e l’analisi per coorte evidenzia differenze di conservazione tra le linee di prodotti e i segmenti di acquisizione. Questo è lo schema corretto quando l’obiettivo è comprendere e diagnosticare, analizzando dove i percorsi si guastano e cosa genera attrito, piuttosto che attivare un pubblico di soppressione o attivare un messaggio di conservazione.

### Considerazioni tecniche

- I dati dell’evento dell’applicazione digitale devono acquisire ogni passaggio nel flusso dell’onboarding o dell’applicazione come eventi discreti con identificatori di passaggio coerenti, in modo che l’analisi di abbandono di CJA possa isolare esattamente dove viene perso il volume.
- I dati relativi al possesso del prodotto CRM e allo stato dell’account devono essere uniti nella connessione CJA insieme ai dati comportamentali, in modo che l’analisi dell’abbandono possa correlare i comportamenti pre-attrito con gli esiti effettivi della chiusura dell’account.
- Le etichette di governance dei dati devono essere applicate a qualsiasi campo finanziario o di identità sensibile incluso nella connessione CJA per evitare l’esposizione PII nelle dashboard condivise a cui accedono gli analisti senza le autorizzazioni di amministratore dei dati.
- L’analisi per coorte di conservazione richiede un livello di annidamento dei dati storici sufficiente, in genere da 12 a 24 mesi, pertanto i criteri di conservazione dei set di dati in AEP devono essere configurati in modo da preservare la cronologia degli eventi necessaria per confronti di coorte significativi.

## Migliore Offer Decisioning successivo

Utilizza la logica decisionale centralizzata per selezionare l’offerta più rilevante per ogni cliente su tutti i canali, combinando regole di idoneità, vincoli aziendali e strategie di classificazione basate sull’intelligenza artificiale. La centralizzazione della selezione delle offerte assicura che ogni cliente riceva l’offerta di prodotti finanziari più contestualmente appropriata, nel rispetto dei requisiti di idoneità normativi e dei vincoli di business.

### Impatto aziendale

Le organizzazioni di servizi finanziari che utilizzano decisioni centralizzate sulle offerte migliori vedono tassi di adozione dei prodotti migliorati e ricavi più elevati per l’interazione con il cliente, con le prestazioni più elevate quando la selezione delle offerte tiene conto sia dei punteggi di tendenza che dei guardrail di idoneità.

### Come implementare

Utilizza il pattern [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) per creare un motore decisionale centralizzato che valuti l&#39;idoneità del cliente, applichi vincoli di business e utilizzi la classificazione basata su IA per selezionare l&#39;offerta ottimale per ogni interazione con il cliente su canali web, app e in uscita. Questo è il modello corretto quando la selezione delle offerte è troppo complessa per la sola personalizzazione basata su regole, e richiede una combinazione di logica di idoneità, regole di priorità e classificazione adattiva per effettuare la selezione ottimale da un catalogo di offerte.

### Considerazioni tecniche

- Le regole di idoneità per le offerte devono essere mantenute nel motore decisionale e in sincronia con i criteri di idoneità del prodotto dei sistemi principali del settore bancario o dei prodotti per evitare che le offerte non idonee emergano.
- I modelli di classificazione basati sull’intelligenza artificiale richiedono dati di formazione sufficienti dalle interazioni delle offerte passate per generare punteggi di propensione affidabili; i prodotti appena lanciati richiedono strategie di classificazione di fallback fino a quando non si accumulano dati sufficienti.
- I requisiti normativi nei servizi finanziari possono limitare ciò che può essere offerto a chi e tramite quale canale; la logica decisionale deve codificare questi vincoli come regole rigide anziché come preferenze morbide.
- Il tracciamento dell’eccesso di offerta è importante: i clienti che ricevono ripetutamente offerte per lo stesso prodotto che non hanno accettato dovrebbero vedersi declassare o sopprimere tale offerta dopo un numero definito di esposizioni.


## Dashboard di Customer Journey Analytics

Crea aree di lavoro di analisi cross-channel che combinano dati web, app, e-mail e call center per visualizzare percorsi di clienti, identificare punti di riconsegna e misurare l’attribuzione delle campagne. Un’area di lavoro di analisi unificata offre ai team di prodotto e marketing una panoramica completa del modo in cui i clienti passano da un canale all’altro e dei punti di contatto, consentendo decisioni basate sui dati su dove investire nel miglioramento del percorso.

### Impatto aziendale

Le organizzazioni di servizi finanziari con analisi di percorso cross-channel riducono il time-to-insight per i team di campagne e prodotti, consentendo un’identificazione più rapida delle opportunità di ottimizzazione ad alto impatto tra flussi di onboarding, funnel di applicazioni e percorsi di assistenza clienti.

### Come implementare

Utilizza il pattern [Customer Analytics &amp; Insight Generation](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) per unire i flussi di eventi da tutti i canali digitali e offline in un set di dati di analisi unificato, quindi crea visualizzazioni dell&#39;area di lavoro che espongono i flussi di percorso, i modelli di abbandono di funnel e di attribuzione. Questo è il modello corretto quando il requisito principale è l’insight analitico e la visualizzazione anziché l’attivazione in tempo reale; i dati vengono utilizzati per orientare le decisioni anziché attivare azioni rivolte al cliente.

### Considerazioni tecniche

- L’unione dei dati cross-channel richiede un identificatore del cliente coerente in tutti i sistemi di origine; nelle organizzazioni con strategie di identità frammentate, i percorsi incompleti compromettono l’analisi.
- I dati del call center e dell’interazione offline devono essere acquisiti e contrassegnati con marca temporale accurata per inserirli correttamente nella sequenza di percorso relativa ai punti di contatto digitali.
- La latenza dei dati tra i sistemi di origine e l’area di lavoro di Analytics influisce sulla rapidità con cui sono disponibili le informazioni; i casi di utilizzo di analisi ad alta frequenza possono richiedere l’acquisizione quasi in tempo reale, anziché feed batch giornalieri.
- I controlli sulla privacy e sulla governance dei dati devono essere applicati ai set di dati di Analytics per evitare che informazioni di identificazione personale vengano visualizzate in dashboard accessibili agli analisti che non dovrebbero avere accesso ai singoli record dei clienti.
