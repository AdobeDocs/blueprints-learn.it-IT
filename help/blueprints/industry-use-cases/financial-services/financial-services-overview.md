---
title: Casi di utilizzo dei servizi finanziari
description: Scopri come le organizzazioni di servizi finanziari utilizzano Adobe Experience Platform per personalizzare le offerte di prodotti, evitare l’abbandono e approfondire le relazioni con i clienti.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2209'
ht-degree: 1%

---


# Casi di utilizzo dei servizi finanziari

Le organizzazioni di servizi finanziari si affidano a Adobe Experience Platform per unificare i dati dei clienti attraverso i canali bancari, di prestito e di investimento, consentendo esperienze personalizzate che rafforzano le relazioni e stimolano la crescita. Riunendo l&#39;attività dell&#39;account, la cronologia delle transazioni e i segnali comportamentali, queste organizzazioni possono fornire l&#39;offerta giusta al momento giusto mantenendo la fiducia e la conformità che i clienti si aspettano.

## Lead Sturturing di alto valore

Identifica i potenziali clienti di alto valore in base ai dati e al comportamento del profilo, quindi coltiva i potenziali clienti con contenuti e offerte personalizzati tramite percorsi automatizzati. Combinando i dettagli demografici, l’attività di navigazione e i segnali di coinvolgimento, le istituzioni finanziarie possono dare priorità ai lead più propensi a convertirli e guidarli attraverso un percorso personalizzato per diventare clienti.

### Impatto aziendale

Le organizzazioni che implementano lo sviluppo di lead di alto valore in genere assistono a un aumento del 25-35% nei tassi di conversione lead-cliente, mentre creano una pipeline di vendita più sana e prevedibile.

### Come implementare

Utilizza il pattern [Multi-Step Orchestrated Percorsi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) per creare sequenze di sviluppo automatizzate che si adattano in base ai segnali di coinvolgimento e preparazione del potenziale cliente.

### Considerazioni tecniche

- Integra i dati CRM di lead-scoring e gli eventi comportamentali del sito web nei profili di potenziale cliente unificati per potenziare la logica di ingresso nel percorso e diramazione.
- Assicurati che il consenso e le preferenze di consenso siano applicati in ogni punto di contatto, in particolare per l’estensione tramite telefono ed e-mail disciplinata dalle normative di marketing finanziario.
- Configura la limitazione del percorso per evitare di sopraffare i potenziali clienti con più comunicazioni durante brevi finestre di valutazione.
- Tenere conto della latenza dei dati tra le interazioni di filiali o consulenti e dell’impegno digitale per mantenere pertinenti i messaggi di crescita.


## Consigli di prodotto per clienti esistenti

Consigliare prodotti finanziari pertinenti, come carte di credito, prestiti e prodotti di investimento, ai clienti esistenti in base al loro profilo, alla cronologia delle transazioni e allo stadio di vita. Questo caso d’uso trasforma i dati degli account quotidiani in informazioni fruibili che rivelano il miglior prodotto successivo per ogni cliente.

### Impatto aziendale

I consigli di prodotti personalizzati incrementano del 20-30% i tassi di adozione dei prodotti e aumentano in modo misurabile il valore della durata di vita dei clienti aumentando la quota di portafoglio.

### Come implementare

Utilizza il pattern [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) per valutare ogni cliente in base alle offerte di prodotti idonee in tempo reale, classificando i consigli in base alla rilevanza e alla priorità aziendale.

### Considerazioni tecniche

- Unifica i dati delle transazioni, i saldi contabili e i prodotti in un unico profilo cliente in modo che i modelli decisionali abbiano una visione completa delle relazioni esistenti.
- Applica le regole di idoneità finanziaria e i vincoli di idoneità normativa come protezioni rigide all’interno del motore decisionale prima di classificare le offerte.
- Coordina la consegna delle offerte tra i canali online banking, app mobile, e-mail e advisor per evitare conflitti o duplicazioni delle raccomandazioni.
- Implementa un limite di frequenza per categoria di prodotto per evitare l’affaticamento delle raccomandazioni, in particolare per i prodotti ad alta considerazione come i mutui e i conti di investimento.


## Campagne di prevenzione dell’abbandono

Identifica i clienti a rischio di abbandono utilizzando la previsione di abbandono basata sull’intelligenza artificiale e coinvolgili con offerte di fidelizzazione e comunicazioni personalizzate. L&#39;individuazione precoce dei segnali di disimpegno consente alle istituzioni finanziarie di intervenire prima che un cliente chiuda i conti o trasferisca le attività altrove.

### Impatto aziendale

Le attività proattive di prevenzione dell’abbandono riducono in genere l’attrito dei clienti del 15-25%, proteggendo i flussi di reddito ricorrenti e riducendo il costo di sostituzione dei clienti.

### Come implementare

Utilizza il pattern [Cross-Channel Percorsi with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) per attivare i percorsi di conservazione quando i punteggi dei rischi di abbandono superano le soglie definite, con decisioni incorporate per selezionare l&#39;offerta di conservazione più convincente.

### Considerazioni tecniche

- Le tendenze dell&#39;attività dell&#39;account di feed, la cronologia delle interazioni del servizio e la frequenza di coinvolgimento vengono inserite in [!DNL Customer AI] modelli di propensione di abbandono per generare punteggi di rischio.
- Definire soglie di rischio di abbandono specifiche per le linee di prodotto, poiché i segnali di disimpegno per il controllo dei conti differiscono da quelli per i portafogli di investimento.
- Garantire che le offerte di fidelizzazione rispettino le norme in materia di prestiti equi e parità di trattamento, in modo che i segmenti ad alto rischio ricevano un trattamento equo.
- Sviluppa una logica di soppressione per escludere i clienti che abbandonano a causa di azioni di frode o conformità, dove l’estensione della conservazione sarebbe inappropriata.


## Dashboard account personalizzato

Personalizza la dashboard di online banking e l’esperienza delle app mobili in base all’attività dell’account, alle preferenze e agli obiettivi finanziari di ciascun cliente. Una dashboard personalizzata consente ai clienti di individuare ciò che conta di più e di ottenere informazioni rilevanti senza richiedere di effettuare ricerche.

### Impatto aziendale

Le dashboard personalizzate aumentano i tassi di coinvolgimento del 30-40% e migliorano in modo significativo i punteggi di soddisfazione dei clienti rendendo il digital banking intuitivo e pertinente.

### Come implementare

Utilizza il pattern [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) per distribuire blocchi di contenuti personalizzati in tempo reale, riflettori sui prodotti e informazioni finanziarie nelle esperienze digitali autenticate.

### Considerazioni tecniche

- Utilizza [!DNL Edge Network] per le decisioni di personalizzazione di secondo secondario nelle sessioni bancarie autenticate in cui la latenza influisce direttamente sull&#39;esperienza utente.
- Aggrega i dati delle transazioni in attributi di profilo precalcolati, ad esempio categorie di spesa e tendenze di risparmio, per evitare il calcolo in tempo reale di set di dati di grandi dimensioni.
- Rispetta gli standard di accessibilità e assicurati che i contenuti personalizzati soddisfino gli stessi requisiti normativi di informativa dei contenuti statici.
- Coordina la logica di personalizzazione tra canali web e mobili in modo che i clienti possano vedere un’esperienza coerente indipendentemente dal dispositivo.


## Offerte di prodotti basate su Life Stage

Identifica i clienti che entrano in nuove fasi della vita come matrimonio, acquisto di una casa o pensione e offre in modo proattivo prodotti e servizi finanziari pertinenti. L&#39;anticipazione di queste tappe fondamentali consente alle istituzioni di posizionarsi come partner di fiducia nei momenti finanziari cruciali.

### Impatto aziendale

Le offerte attivate dalla fase di vita raggiungono un tasso di adozione dei prodotti del 35-45%, superando in modo significativo le campagne generiche e rafforzando nel contempo le relazioni con i clienti a lungo termine.

### Come implementare

Percorsi Utilizza il pattern [Cross-Channel con Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) per rilevare gli indicatori della fase di vita e orchestrare percorsi multi-touch con una selezione di offerte incorporata personalizzata per ogni fase cardine.

### Considerazioni tecniche

- Combina segnali di prime parti come modifiche di indirizzi, aperture di conti congiunti e depositi di grandi dimensioni con dati di terze parti autorizzati per dedurre le transizioni nelle fasi di vita.
- Gestisci gli eventi di vita sensibili con attenzione nel tono e nella frequenza dei messaggi, in quanto le milestone erroneamente dedotte possono erodere la fiducia.
- L’idoneità normativa dello strato viene verificata in offer decisioning in modo che i prodotti consigliati siano in linea con la situazione finanziaria verificata del cliente.
- Crea periodi di raffreddamento tra le campagne della fase &quot;vita&quot; per evitare la sovrapposizione dell’attività quando più indicatori si attivano in una breve finestra.


## Avvisi e consigli basati sulle transazioni

Invia avvisi in tempo reale per le transazioni e fornisci consigli personalizzati in base ai pattern di spesa e all’attività dell’account. Notifiche tempestive e pertinenti mantengono i clienti informati e creano momenti naturali per far emergere indicazioni finanziarie utili.

### Impatto aziendale

Gli avvisi basati sulle transazioni raggiungono un tasso di coinvolgimento del 50-60%, migliorando notevolmente la consapevolezza della sicurezza e creando punti di contatto di alto valore per consigli personalizzati.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) per rispondere agli eventi delle transazioni in tempo reale con avvisi e consigli contestualmente rilevanti.

### Considerazioni tecniche

- Acquisire eventi di transazione tramite una pipeline di streaming con requisiti di distribuzione a bassa latenza, poiché gli avvisi di sicurezza perdono valore se ritardati di più di pochi minuti.
- Applica le preferenze e le soglie degli avvisi definiti dal cliente in modo che le notifiche riflettano le singole impostazioni anziché le regole uguali per tutti.
- Separa gli avvisi di sicurezza obbligatori dai messaggi di consiglio facoltativi nell’architettura di messaggistica per garantire che le notifiche di conformità non vengano mai eliminate.
- Tenere conto degli elevati volumi di transazioni durante i periodi di picco, ad esempio i giorni lavorativi e le festività, progettando una capacità di throughput scalabile in base alla domanda.


## Recupero abbandono richiesta carta di credito

Identifica i clienti che hanno iniziato ma non hanno completato le applicazioni per le carte di credito e coinvolgili nuovamente con messaggi e offerte personalizzati. L’abbandono delle applicazioni rappresenta un pubblico con intenti elevati che spesso ha bisogno solo di un piccolo spintone per completare il processo.

### Impatto aziendale

Le campagne di recupero degli abbandoni migliorano i tassi di completamento delle applicazioni del 20-30%, aumentando direttamente l’acquisizione di nuovi account da parte di un pubblico che ha già espresso interesse.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) per rilevare gli eventi di abbandono delle applicazioni e attivare messaggi di follow-up tempestivi che rispondono a motivi comuni di abbandono.

### Considerazioni tecniche

- Acquisisci il passaggio specifico in cui l’applicazione è stata abbandonata per adattare la messaggistica, in quanto una persona che ha abbandonato al momento della verifica dell’identità ha bisogno di una rassicurazione diversa rispetto a una che ha abbandonato al momento della revisione dei termini.
- Rispetta le normative sul marketing creditizio, incluse le informazioni obbligatorie e le regole sul fair loan, in tutte le comunicazioni relative al recupero.
- Implementare la logica di decadimento temporale in modo che l&#39;estensione del ripristino si interrompa dopo una finestra definita, poiché i dati non aggiornati dell&#39;applicazione potrebbero non essere più validi per la prequalificazione.
- Coordinarsi con il sistema dell&#39;applicazione per eliminare i messaggi di recupero per i richiedenti che hanno completato tramite un canale diverso, ad esempio una visita presso una filiale o una telefonata.


## Raccomandazioni Portfolio per gli investimenti

Fornisci consigli di investimento personalizzati in base al profilo di rischio di ciascun cliente, alla cronologia degli investimenti e agli obiettivi finanziari. Le linee guida del portfolio basate sui dati aiutano i clienti a prendere decisioni informate approfondendo il coinvolgimento con i servizi di gestione patrimoniale.

### Impatto aziendale

I consigli di investimento personalizzati favoriscono un aumento del 25-35% nell’adozione dei prodotti di investimento e migliorano la diversificazione del portafoglio in tutta la base di clienti.

### Come implementare

Utilizza il pattern [Behavioral Recommendation](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) per analizzare il comportamento e le preferenze di investimento e quindi rendere visibili i consigli di portafoglio pertinenti tramite canali digitali e strumenti di consulenza.

### Considerazioni tecniche

- Integra feed di dati di brokeraggio e di custodia per mantenere una visualizzazione accurata e aggiornata delle attuali partecipazioni e allocazioni di ciascun cliente.
- Applicare i requisiti di idoneità imposti dalle normative sui titoli in modo che le raccomandazioni siano in linea con gli obiettivi documentati di investimento e tolleranza al rischio del cliente.
- Etichettare chiaramente i contenuti di investimento personalizzati come formativi o informativi laddove necessario, distinguendoli dalla consulenza formale in materia di investimenti che comporta obblighi fiduciari.
- Aggiorna regolarmente i modelli di consigli per tenere conto delle variazioni di mercato, della deriva del portafoglio e dei cambiamenti negli obiettivi dei clienti.


## Personalization avviso frodi

Personalizza gli avvisi di frode e le comunicazioni di sicurezza in base alle preferenze di comunicazione di ogni cliente e alla cronologia delle interazioni passate. Gli avvisi personalizzati aumentano la probabilità che i clienti notino, comprendano e agiscano in base alle notifiche di sicurezza critiche.

### Impatto aziendale

Gli avvisi personalizzati per frodi migliorano i tassi di risposta agli avvisi del 40-50%, rafforzando in modo significativo la conformità in materia di sicurezza e riducendo la finestra di esposizione durante le attività sospette.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) per inviare avvisi di frode tramite il canale preferito di ciascun cliente con dettagli contestuali che semplificano la conferma o la contestazione dell&#39;attività.

### Considerazioni tecniche

- Assegna priorità alla velocità di consegna e all’affidabilità rispetto a tutte le altre considerazioni di progettazione, in quanto la latenza dell’avviso di frode è direttamente correlata all’esposizione alle perdite finanziarie.
- Inoltra gli avvisi tramite il canale preferito verificato del cliente mantenendo i canali di fallback per garantire la consegna anche in caso di errore del canale principale.
- Archivia la cronologia delle interazioni degli avvisi per migliorare la rilevanza degli avvisi futuri e ridurre il falso positivo per i clienti che viaggiano frequentemente o effettuano acquisti atipici.
- Assicurati che il contenuto e i flussi di lavoro degli avvisi di frode siano conformi alle normative di sicurezza bancaria e non esporre i dettagli sensibili dell’account nelle anteprime dei messaggi o nelle righe dell’oggetto.


## Coinvolgimento programma fedeltà

Personalizza comunicazioni, premi e offerte del programma fedeltà in base al livello, al saldo dei punti e alla cronologia dei rimborsi di ciascun cliente. Comunicazioni pertinenti e tempestive sulla fidelizzazione mantengono i membri coinvolti e stimolano una maggiore partecipazione al programma.

### Impatto aziendale

L’impegno di fidelizzazione personalizzata aumenta la partecipazione al programma del 30-40% e porta a un riscatto dei punti misurabilmente più elevato, rafforzando la percezione del valore del programma.

### Come implementare

Utilizza il modello [Cross-Channel Percorsi con Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) per orchestrare comunicazioni fedeltà tra canali diversi, con decisioning incorporato per selezionare il premio o l&#39;offerta più rilevante per ogni membro.

### Considerazioni tecniche

- Sincronizza i dati della piattaforma fedeltà, tra cui lo stato dei livelli, i saldi dei punti e la cronologia dei rimborsi, nei profili dei clienti in tempo quasi reale per evitare di promuovere saldi scaduti o imprecisi.
- Logica di percorso dei segmenti per livello per fornire esperienze differenziate, in quanto i membri di alto livello si aspettano un trattamento esclusivo e un accesso anticipato alle promozioni.
- Coordina i messaggi di fidelizzazione con campagne di marketing più ampie per evitare l’eccesso di messaggi e le offerte in conflitto tra i programmi.
- Traccia l’attribuzione del rimborso tra i canali per misurare quali comunicazioni personalizzate determinano il maggiore ritorno sull’investimento del programma.


## Campagne di preapprovazione mutui

Puoi indirizzare l’attività ai clienti che potrebbero essere sul mercato di un mutuo sulla base di dati di profilo, segnali comportamentali e indicatori della fase di vita. La preapprovazione proattiva posiziona l&#39;ente come una comoda prima scelta durante una delle più grandi decisioni finanziarie che un cliente prenderà.

### Impatto aziendale

Le campagne mirate di preapprovazione dei mutui aumentano i tassi di applicazione del 20-30% e migliorano il volume di erogazione dei prestiti raggiungendo al momento giusto potenziali qualificati.

### Come implementare

Utilizza il pattern [Multi-Step Orchestrated Percorsi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) per guidare i potenziali clienti ipotecari attraverso una sequenza di sviluppo multi-touch dalla consapevolezza fino alla pre-approvazione, adattandosi in base ai segnali di coinvolgimento e qualifica.

### Considerazioni tecniche

- Combina il comportamento di ricerca delle proprietà, le tendenze di crescita del risparmio e i segnali di scadenza del leasing per creare un modello di propensione che identifichi i probabili richiedenti mutuo.
- Assicurati che tutti i messaggi di pre-approvazione siano conformi alle normative sulla pubblicità dei mutui, incluse le informazioni richieste, la precisione delle tariffe e un linguaggio per la registrazione degli alloggi uguale.
- Coordinare la tempistica della campagna con le variazioni dell’ambiente dei tassi in modo che l’estensione sia allineata con condizioni di finanziamento favorevoli ed eviti riferimenti ai tassi superati.
- Crea flussi di lavoro di trasferimento per i responsabili del prestito in modo che i corsi nutriti digitalmente conducano agevolmente alla transizione nel processo formale di richiesta e sottoscrizione.


## Contenuti personalizzati di educazione finanziaria

Consegna contenuti, suggerimenti e risorse personalizzati di educazione finanziaria in base al profilo finanziario, agli obiettivi e agli interessi di ogni cliente. I contenuti educativi pertinenti creano fiducia, migliorano l&#39;alfabetizzazione finanziaria e creano opportunità organiche per introdurre prodotti pertinenti.

### Impatto aziendale

I contenuti personalizzati per l’istruzione aumentano i tassi di coinvolgimento nei contenuti del 25-35% e migliorano l’alfabetizzazione finanziaria dei clienti, il che a sua volta favorisce un’adozione più sicura dei prodotti.

### Come implementare

Utilizza il pattern [Cross-Channel Percorsi with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) per distribuire una sequenza curata di contenuti educativi tra canali, utilizzando il decisioning per abbinare gli argomenti alla situazione finanziaria e agli interessi di ogni cliente.

### Considerazioni tecniche

- Mappa i contenuti educativi agli attributi del profilo finanziario, come il rapporto debito/reddito, il tasso di risparmio e l’esperienza di investimento, per garantire la rilevanza dell’argomento.
- Assegna tag ai contenuti con livelli di difficoltà e argomenti prerequisiti per creare percorsi di apprendimento progressivi anziché distribuire articoli una tantum disconnessi.
- Tieni traccia del coinvolgimento dei contenuti a livello di argomento per perfezionare i modelli di personalizzazione e identificare aree di interesse emergenti in tutta la base di clienti.
- Garantire che i contenuti educativi siano chiaramente distinti dal marketing dei prodotti per mantenere la conformità alle normative e preservare la fiducia dei clienti nell&#39;obiettività del programma.
