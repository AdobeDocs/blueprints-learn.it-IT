---
title: Casi di utilizzo assicurazioni
description: Scopri in che modo le compagnie di assicurazione utilizzano Adobe Experience Platform per personalizzare la gestione delle policy, migliorare le esperienze di richiesta di risarcimento e promuovere la fidelizzazione dei clienti.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: a082598f-555b-49a4-b201-a55bee793959
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '3272'
ht-degree: 0%

---

# Casi di utilizzo assicurazioni

Le organizzazioni assicurative utilizzano Adobe Experience Platform per unificare i dati dei titolari di polizze tra i sistemi di gestione delle polizze, delle richieste di rimborso e del coinvolgimento, al fine di fornire comunicazioni personalizzate in ogni fase della relazione con il cliente. Collegando i segnali comportamentali con le informazioni relative alle regole e alle richieste di rimborso, gli assicuratori possono coinvolgere in modo proattivo i clienti con offerte pertinenti, aggiornamenti tempestivi dei servizi e supporto significativo per la conservazione e il valore del ciclo di vita.

## Campagne di rinnovo dei criteri

Invia promemoria e offerte personalizzati per il rinnovo dei criteri in base alla cronologia dei criteri, alla registrazione delle richieste e alle preferenze di copertura di ogni cliente. Un&#39;azione di rinnovamento tempestiva e pertinente riduce i tassi di fallimento delle politiche e rafforza le relazioni a lungo termine con la clientela, rendendo più facile per gli assicurati capire le loro opzioni e agire.

### Impatto aziendale

Le organizzazioni che implementano campagne di rinnovo personalizzate delle policy possono vedere tassi di rinnovo migliorati, riducendo direttamente l’abbandono dei clienti e proteggendo i ricavi premium ricorrenti.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Questo approccio costruisce una sequenza di rinnovo temporizzata che procede dal preavviso iniziale fino all&#39;inoltro di solleciti e, se necessario, un messaggio finale di urgenza, adattando la cadenza e l&#39;offerta in base al fatto che l&#39;assicurato abbia agito con contatti precedenti. Questo è il modello corretto quando la tempistica è determinata da una data di contratto anziché da un evento cliente discreto e l’intento aziendale richiede un flusso sequenziale di più messaggi su 30 o più giorni con diramazione condizionale basata sul coinvolgimento: la messaggistica attivata da un evento gestisce le risposte reattive a eventi discreti, ma non può soddisfare la logica di programmazione basata sul calendario o le dipendenze di escalation necessarie per una campagna di rinnovo.

### Considerazioni tecniche

- Integrazione con il sistema di gestione delle policy per ricevere gli eventi relativi alla data di rinnovo e i dettagli delle policy correnti, garantendo che i messaggi riflettano la copertura accurata e informazioni premium.
- Applica le etichette di governance dei dati a tutti i dati personali identificabili e di politica finanziaria per rispettare le normative statali in materia di assicurazione e i requisiti sulla privacy dei dati.
- Configurare le regole di soppressione per impedire l&#39;invio di messaggi di rinnovo agli assicurati che hanno già rinnovato o che dispongono di richieste attive che possono influire sui termini di rinnovo.
- Coordina i tempi con le assegnazioni degli agenti o dei broker in modo che i messaggi diretti al cliente siano in linea con qualsiasi attività svolta dall’agente assegnato.


## Consigli sui prodotti di cross-selling

Consigliare prodotti assicurativi aggiuntivi come la copertura di vita, casa o auto in base alle politiche esistenti di ciascun cliente, la fase di vita e il profilo di rischio. I consigli personalizzati sui prodotti aiutano gli assicurati a individuare le lacune di copertura e a creare un portafoglio di protezione più completo.

### Impatto aziendale

I consigli di cross-selling personalizzati contribuiscono a migliorare i tassi di conversione delle cross-selling, aumentando le policy per famiglia e il valore complessivo della durata di vita del cliente.

### Come implementare

Utilizza il pattern [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md). Real-time Decisioning valuta i segnali esistenti di copertura, stadio di vita e comportamento di ogni cliente per selezionare i prodotti consigliati più rilevanti dal catalogo disponibile. Questo è il modello corretto quando la selezione del prodotto deve tenere conto delle regole di idoneità, delle linee guida per la sottoscrizione e dei requisiti di idoneità normativi, vincoli che richiedono una logica decisionale regolamentata anziché una classificazione di affinità comportamentale.

### Considerazioni tecniche

- Integra i dati delle policy da tutte le linee di prodotto in un profilo cliente unificato in modo che il motore decisionale abbia una visione completa della copertura esistente durante la selezione dei consigli.
- Configurare le regole di idoneità all&#39;interno del modello decisionale per escludere i prodotti già in possesso di un cliente o in conflitto con le linee guida per la sottoscrizione per il proprio profilo di rischio.
- Coinvolgi i team legali e di conformità per verificare che le regole di idoneità per i consigli sui prodotti siano in linea con i requisiti di marketing e idoneità applicabili per le assicurazioni statali prima del lancio.
- Coordina l’output delle decisioni con il portale degli agenti in modo che i prodotti consigliati siano visibili agli agenti assegnati che potrebbero avere conversazioni dirette con il cliente.


## Personalization processo richieste di rimborso

Personalizzare le comunicazioni di processo, gli aggiornamenti dello stato e le risorse di supporto in base al tipo di richiesta di rimborso, alle preferenze del cliente e alla cronologia delle richieste. Un&#39;esperienza di reclamo trasparente e ben comunicata riduce l&#39;ansia durante i momenti di stress e crea una fiducia duratura con gli assicurati.

### Impatto aziendale

Le comunicazioni personalizzate per le richieste di rimborso consentono di ottenere punteggi migliori per la soddisfazione delle richieste, riducendo le richieste e aumentando la probabilità di rinnovo delle politiche dopo una richiesta di rimborso.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Il processo di richiesta di rimborso è un&#39;esperienza in più fasi, con fasi distinte (archiviazione, indagine, adeguamento e liquidazione) che richiedono comunicazioni su misura e un calendario adattativo. Si tratta del modello corretto quando il caso d’uso richiede un flusso di messaggi multipli in sequenza nell’arco di giorni con diramazioni condizionali basate su eventi di stato delle attestazioni: un singolo messaggio attivato non può soddisfare la logica di dipendenza tra fasi di attestazioni sequenziali.

### Considerazioni tecniche

- Integrazione con il sistema di gestione delle richieste di rimborso per ricevere in tempo reale gli eventi di modifica dello stato che consentono di far avanzare il cliente attraverso la fase di percorso appropriata.
- Progettare la logica di diramazione del percorso che adatta il tono di messaggistica e i contenuti in base al tipo di richiesta di risarcimento, ad esempio collisione automatica rispetto a danni alle proprietà rispetto a richieste di risarcimento danni.
- Implementa le regole di soppressione durante le indagini attive sulle richieste di rimborso per impedire che messaggi di marketing o di cross-selling raggiungano i clienti in momenti sensibili.
- Assicurati che tutti i dati relativi alle richieste di rimborso che fluiscono nel profilo del cliente siano etichettati con restrizioni di governance dei dati appropriate per impedirne l’utilizzo al di fuori delle comunicazioni di servizio.


## Valutazione e prevenzione dei rischi

Fornisci informazioni personalizzate sulla valutazione del rischio e suggerimenti sulla prevenzione in base al tipo di policy, alla posizione geografica e ai fattori di rischio specifici di ciascun cliente. L’educazione proattiva al rischio aiuta gli assicurati a ridurre l’esposizione alle perdite, a vantaggio sia del cliente che dell’assicuratore.

### Impatto aziendale

L’impegno personalizzato nella prevenzione dei rischi stimola un maggiore impegno nella prevenzione, contribuendo a ridurre la frequenza delle richieste di risarcimento e a migliorare la soddisfazione dei clienti.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). L’educazione alla prevenzione dei rischi è più efficace in quanto è un percorso multi-touch sostenuto che fornisce indicazioni pertinenti nel tempo e si adatta in base al coinvolgimento dei clienti e ai fattori di rischio stagionali. Questo è il modello giusto quando il percorso deve fornire contenuti per periodi prolungati con correzioni stagionali dei tempi e diramazioni basate sul coinvolgimento: i messaggi attivati dagli eventi non possono gestire la programmazione predittiva o la frequenza in più passaggi necessaria per un&#39;istruzione sostenuta.

### Considerazioni tecniche

- Integrazione con fornitori di dati sul rischio di terze parti per informazioni su meteo, rischio geografico e rischio immobiliare che arricchiscono i profili dei clienti con punteggi di rischio specifici per la posizione.
- Progetta una logica di percorso stagionale che offra contenuti di prevenzione pertinenti in anticipo rispetto ai periodi ad alto rischio, come la preparazione della stagione degli uragani per gli assicurati costieri o suggerimenti meteorologici invernali per i clienti con clima freddo.
- Applicare etichette di governance dei dati per distinguere i dati di valutazione dei rischi utilizzati per l’educazione dei clienti dai dati utilizzati nelle decisioni di sottoscrizione attuariale.
- Coordinare il contenuto della prevenzione dei rischi con la copertura specifica dell&#39;assicurato in modo che le raccomandazioni siano pertinenti per i pericoli che la polizza effettivamente copre.


## Notifiche di modifica criteri

Invia notifiche personalizzate su modifiche dei criteri, aggiornamenti della copertura e nuove opzioni in base ai criteri specifici e alle preferenze di comunicazione di ciascun cliente. Notifiche chiare e tempestive tengono informati gli assicurati e riducono la confusione circa il loro status di copertura.

### Impatto aziendale

Le notifiche personalizzate di modifica delle policy consentono di migliorare i tassi di conferma delle notifiche, riducendo le richieste di assistenza ai clienti e migliorando la comprensione complessiva da parte dell’assicurato.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Gli eventi di modifica delle policy dal sistema di amministrazione fungono da trigger naturali per le notifiche immediate e rilevanti attraverso il canale preferito di ciascun cliente. Questo è il modello corretto quando l’evento che scatena l’evento è un evento di sistema (cambiamento di politica) anziché il comportamento del cliente e la comunicazione richiesta è immediata e reattiva anziché una sequenza di acquisizione sostenuta.

### Considerazioni tecniche

- Integrazione con il sistema di amministrazione delle policy per acquisire in tempo reale gli eventi di approvazione, modifica e modifica del rinnovo, garantendo che le notifiche riflettano lo stato delle policy più recente.
- Prima di attivare le comunicazioni automatizzate, rivolgiti al team legale per verificare che le notifiche di modifica dei criteri soddisfino i requisiti relativi a tempistica, lingua e canale di consegna stabiliti dallo stato.
- Configurare la logica di priorità dei canali in base all&#39;urgenza e al tipo di modifica; ad esempio, le riduzioni di copertura potrebbero richiedere canali più immediati rispetto agli aggiornamenti informativi.
- Mantenere un audit trail della consegna per tutte le notifiche di modifica delle policy per supportare la documentazione di conformità alle normative e la risoluzione delle controversie.


## Recupero di abbandono preventivo

Rivolgiti ai clienti che hanno iniziato ma non hanno completato un preventivo di assicurazione con messaggi di follow-up personalizzati e offerte personalizzate. Un intervento tempestivo di recupero riporta i potenziali clienti al processo di quotazione e risolve gli ostacoli comuni al completamento.

### Impatto aziendale

Le campagne di recupero dell’abbandono delle quotazioni favoriscono il miglioramento dei tassi di completamento delle quotazioni, convertendo un maggior numero di potenziali clienti in assicurati e riducendo i costi di acquisizione dei clienti.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). L’abbandono delle quotazioni è un evento comportamentale che attiva un follow-up tempestivo mentre l’interesse e l’intento del potenziale cliente sono ancora freschi. Questo è il modello giusto quando il trigger è un comportamento discreto del cliente (abbandono) e la risposta richiesta è un ricoinvolgimento sensibile al tempo, piuttosto che una sequenza di sviluppo in più fasi o decisioni di offerta complesse.

### Considerazioni tecniche

- Integrare con la piattaforma di quotazione online per acquisire eventi di abbandono insieme ai dettagli del preventivo già forniti dal cliente, consentendo un nuovo coinvolgimento personalizzato.
- Configurare regole temporali che bilanciano l’urgenza con la rispettabilità — follow-up iniziale entro poche ore, con un numero limitato di promemoria successivi nei giorni successivi.
- Applica le regole di consenso e privacy per garantire che il follow-up venga inviato solo ai potenziali clienti che hanno acconsentito alle comunicazioni di marketing, in particolare per i clienti che non hanno ancora stabilito una relazione basata su policy.
- Includi collegamenti profondi che restituiscono il prospect direttamente all&#39;offerta salvata anziché richiedere il riavvio del processo dall&#39;inizio.


## Offerte di prodotti basate su Life Stage

Identificare i clienti che entrano in una nuova fase di vita, ad esempio matrimonio, acquisto di una casa, famiglia in crescita o pensione, e offrire prodotti assicurativi pertinenti che soddisfino le loro esigenze di protezione in continua evoluzione. Il targeting nella fase di vita aiuta gli assicurati a creare la copertura giusta al momento giusto.

### Impatto aziendale

Le offerte di prodotti basate su fasi di vita consentono di migliorare i tassi di adozione dei prodotti, consolidando le relazioni con i clienti durante i momenti decisionali chiave.

### Come implementare

Utilizza il Percorso [cross-channel con modello Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md). Le transizioni Life Stage traggono vantaggio dall&#39;orchestrazione cross-channel combinata con il decisioning in tempo reale per selezionare il prodotto più rilevante e distribuirlo nel canale preferito dal cliente nel momento ottimale. Questo è il modello corretto quando il percorso deve coordinare la consegna su più canali per garantire offerte coerenti sfruttando al contempo le decisioni per selezionare il prodotto più appropriato per la fase vita rilevata: l’orchestrazione in più passaggi da sola non può fornire l’idoneità in tempo reale e la valutazione dell’idoneità necessarie per i consigli sui prodotti assicurativi.

### Considerazioni tecniche

- Crea modelli di rilevamento della fase di vita utilizzando segnali comportamentali quali cambiamenti di indirizzo, aggiornamenti dei beneficiari e modelli di ricerca online, combinati con eventi di cambiamento delle policy.
- Configura il motore delle decisioni con regole di idoneità e idoneità del prodotto che corrispondano a ogni fase del ciclo di vita alle raccomandazioni di copertura appropriate.
- Coordinare le offerte della fase di vita con l’agente o il broker assegnato in modo che siano preparati a supportare il cliente con una conversazione consultiva quando l’offerta viene consegnata.
- Applica le etichette di governance dei dati a qualsiasi origine dati di terze parti utilizzata per l’inferenza nella fase di vita per garantire la conformità alle normative sulla privacy dei dati e alle pratiche di marketing corrette.


## Opportunità di sconto e risparmio

Identifica e comunica opportunità di sconto personalizzate, come bundling, driver sicuri, fedeltà e sconti di fatturazione non cartacea, in base al profilo e al comportamento di ciascun cliente. Le comunicazioni proattive sul risparmio dimostrano valore e rafforzano la relazione prezzo-valore.

### Impatto aziendale

Le comunicazioni personalizzate relative a sconti e risparmi consentono di ottimizzare i tassi di utilizzo degli sconti, migliorando la soddisfazione dei clienti e riducendo l&#39;abbandono basato sui prezzi.

### Come implementare

Utilizza il pattern [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md). Real-time Decisioning valuta l’idoneità di ogni cliente agli sconti disponibili e seleziona l’opportunità di risparmio più incisiva da presentare al momento giusto. Questo è il modello corretto quando la selezione degli sconti deve tenere conto delle limitazioni di stacking, delle restrizioni normative e di calcoli attuariali accurati, vincoli che richiedono una logica decisionale regolamentata anziché semplici controlli di idoneità.

### Considerazioni tecniche

- Integrazione con i sistemi di valutazione e fatturazione delle policy per calcolare in tempo reale l’idoneità allo sconto e gli importi dei risparmi potenziali per ciascun cliente.
- Configura regole di decisione che tengano conto delle limitazioni dello stacking degli sconti e garantiscano che gli importi di risparmio comunicati siano accurati sotto il profilo attuariale e approvati dal team di determinazione prezzi.
- Per le comunicazioni relative agli sconti, applicare le normative specifiche dello stato, poiché alcuni stati prevedono limitazioni sul modo in cui gli sconti assicurativi possono essere commercializzati e applicati.
- Tieni traccia dei risultati di adozione degli sconti per perfezionare continuamente il modello decisionale e assegnare la priorità ai messaggi di risparmio che risuonano di più con i diversi segmenti di clienti.


## Denuncia e prevenzione delle frodi

Utilizza il rilevamento intelligente delle frodi per identificare i pattern delle richieste di rimborso sospette e personalizzare le comunicazioni investigative mantenendo al contempo la fiducia dei clienti. Un&#39;efficace prevenzione delle frodi protegge gli assicurati onesti, mantenendo equi i premi e assicurando che le richieste legittime siano trattate rapidamente.

### Impatto aziendale

I programmi intelligenti di prevenzione delle frodi in materia di richieste di risarcimento migliorano i tassi di rilevamento delle frodi, riducendo i pagamenti fraudolenti e i costi complessivi delle richieste di risarcimento.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Gli eventi di valutazione del rischio di frode attivano le comunicazioni di investigazione appropriate e gli adeguamenti del processo in tempo reale, garantendo che le richieste di rimborso segnalate ricevano attenzione immediata. Si tratta del modello corretto quando un evento derivato dal sistema (punteggio di rischio di frode) è il trigger e l’azione richiesta è l’adeguamento immediato del processo interno con un’attenta comunicazione con il cliente, anziché uno scenario di percorso o di decisione in più fasi.

### Considerazioni tecniche

- È possibile integrare i punteggi relativi al rischio di frode dal sistema di analisi delle richieste di rimborso nel profilo cliente applicando etichette di governance dei dati rigorose per evitare che i dati delle indagini sulle frodi vengano visualizzati nelle comunicazioni rivolte al cliente.
- Progetta percorsi di comunicazione che mantengano un tono professionale e rispettoso per i clienti le cui richieste sono in fase di revisione, preservando la relazione indipendentemente dall’esito dell’indagine.
- Implementa controlli dell’accesso basati sui ruoli per garantire che gli indicatori di frode siano visibili solo ai team di investigatori autorizzati e non vengano mai visualizzati nelle visualizzazioni standard degli agenti o del servizio clienti.
- Coordinarsi con il servizio di risoluzione identità [!DNL Adobe Experience Platform] per rilevare pattern tra profili correlati, ad esempio indirizzi condivisi o numeri di telefono collegati a più richieste sospette.


## Programmi di benessere e prevenzione

Personalizza le comunicazioni del programma di benessere, i promemoria di partecipazione e le notifiche di ricompensa per i clienti di assicurazioni sulla salute e sulla vita in base ai loro obiettivi e al loro livello di coinvolgimento. Programmi di benessere attivi migliorano i risultati per la salute degli assicurati e costruiscono una base di clienti più forte e più impegnata.

### Impatto aziendale

Le comunicazioni personalizzate relative al programma di salute e prevenzione consentono di migliorare i tassi di partecipazione al programma, contribuendo a migliorare i risultati sanitari e a ridurre la frequenza delle richieste di rimborso.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). I programmi di benessere sono esperienze di coinvolgimento sostenuto con milestone, sfide e premi che richiedono un&#39;orchestrazione adattiva basata sull&#39;attività e sul progresso di ciascun partecipante. Questo è il modello corretto quando il caso d’uso richiede un flusso di messaggi a lungo termine e multiplo con diramazioni basate sul coinvolgimento e regolazioni temporali adattive: i messaggi attivati dagli eventi non possono gestire la logica milestone complessa o la necessità di regolare la frequenza delle comunicazioni in base al tracciamento sostenuto delle attività.

### Considerazioni tecniche

- Integrare con i feed di dati di applicazioni per dispositivi indossabili e di salute utilizzando l&#39;acquisizione in streaming di [!DNL Adobe Experience Platform], applicando etichette chiare per la governance dei dati per distinguere i dati relativi alla salute dai dati relativi a richieste di rimborso o sottoscrizioni.
- Implementa meccanismi di consenso separati per la raccolta dei dati sulla salute per garantire che i partecipanti comprendano come vengono utilizzati i loro dati sulle attività sanitarie e possano rinunciare senza influenzare i loro criteri.
- Progettare la logica di percorso che regola l&#39;intensità del programma e la frequenza di comunicazione in base al livello di coinvolgimento di ciascun partecipante per prevenire l&#39;affaticamento e incoraggiare la partecipazione prolungata.
- Coinvolgi i team legali e di conformità per rivedere le strutture di incentivi per il benessere e i programmi di sconti premium per la conformità alle normative di assicurazione statali applicabili prima del lancio.


## Coordinamento agente e broker

Consente la comunicazione e il coordinamento personalizzati tra i clienti e gli agenti o i broker loro assegnati in base alle esigenze dei criteri, alla cronologia dei servizi e alle preferenze. Un migliore coordinamento crea un’esperienza fluida in cui i clienti si sentono supportati da un consulente esperto che comprende appieno la loro relazione.

### Impatto aziendale

Comunicazioni efficaci di coordinamento degli agenti e dei broker si traducono in un maggiore coinvolgimento degli agenti, che porta a relazioni più solide con i clienti e a una maggiore conservazione, guidata da interazioni di consulenza affidabili.

### Come implementare

Utilizza il pattern [Attivazione messaggi in uscita in batch](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md). Il coordinamento degli agenti si realizza in modo ottimale tramite attivazioni batch pianificate che forniscono agli agenti elenchi con priorità di assistenza ai clienti, punti di contatto e azioni consigliate a cadenza regolare. Questo è lo schema corretto quando il pubblico è ampio e predefinito, la tempistica di consegna è pianificata su base ricorrente anziché basata su eventi e non è necessario alcun diramamento in tempo reale o processo decisionale.

### Considerazioni tecniche

- Integrare con il sistema di gestione degli agenti per mantenere accurate assegnazioni agente-cliente e garantire che le comunicazioni riflettano la relazione corretta, soprattutto durante le transizioni agente.
- Progetta l’attivazione dei dati nel portale dell’agente, in modo che gli agenti ricevano una visualizzazione consolidata delle informazioni sul cliente, dei prossimi rinnovi e delle azioni consigliate senza esporre dati comportamentali non elaborati.
- Applica le etichette di governance dei dati per limitare quali elementi dei dati del cliente vengono condivisi con partner di broker esterni rispetto agli agenti vincolati, rispettando i limiti contrattuali e normativi della condivisione dei dati.
- Implementa cicli di feedback dalle interazioni degli agenti nel profilo cliente in modo che le informazioni provenienti da conversazioni telefoniche o di persona arricchiscano la vista unificata e migliorino la personalizzazione futura.


## Risposta agli eventi catastrofici

Comunica in modo proattivo con i clienti delle aree colpite durante calamità naturali o eventi catastrofici con informazioni di supporto personalizzate, indicazioni sulla presentazione delle richieste di rimborso e risorse di emergenza. Una mobilitazione rapida ed empatica durante una crisi dimostra l’impegno dell’assicuratore a essere presente quando i clienti ne hanno più bisogno.

### Impatto aziendale

Le comunicazioni proattive di risposta agli eventi catastrofici consentono di migliorare i tassi di comunicazione dei clienti durante gli eventi, accelerando la presentazione delle richieste e rafforzando la fiducia e la fedeltà dei clienti a lungo termine.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Le dichiarazioni di eventi catastrofici fungono da trigger ad alta priorità per un’estensione immediata e personalizzata a tutti i contraenti nell’area geografica interessata. Questo è lo schema giusto quando si innesca un evento esterno ad alta priorità e la risposta richiesta è immediata, ampia e geografica, con informazioni critiche in termini di tempo, piuttosto che modelli di comportamento dei singoli clienti o sequenze complesse.

### Considerazioni tecniche

- Integrazione con i servizi di monitoraggio delle catastrofi e i feed di dichiarazione delle catastrofi governative per attivare rapidamente le comunicazioni quando gli eventi vengono dichiarati per specifiche aree geografiche.
- Crea segmenti di pubblico geografico utilizzando i dati degli indirizzi dei contraenti e le informazioni sulla posizione delle proprietà per identificare con precisione i clienti nell’area interessata senza comunicare in modo eccessivo ai clienti non interessati.
- Configura il routing dei messaggi ad alta priorità che ignora le regole standard di limitazione della frequenza e soppressione per garantire che le informazioni critiche relative alla sicurezza e alle richieste di rimborso raggiungano immediatamente i clienti.
- Modelli di messaggio e configurazioni di percorso precompilati per i tipi di eventi catastrofici più comuni, in modo che le comunicazioni possano essere attivate entro poche ore dalla dichiarazione di un evento, anziché richiedere la creazione di contenuti durante la crisi.


## Personalization contenuto portale titolari di polizze

Personalizza il portale self-service autenticato e l’esperienza dell’app mobile per gli assicurati presentando le informazioni di copertura, gli strumenti e le risorse più rilevanti in base al loro comportamento di navigazione, al portfolio di policy e alle interazioni di servizio recenti. Un portale che si adatta al contesto attuale di ogni assicurato riduce l&#39;attrito e rende più facile per i clienti trovare ciò di cui hanno bisogno quando ne hanno bisogno.

### Impatto aziendale

La personalizzazione dell’esperienza del portale degli assicurati determina miglioramenti misurabili nel completamento delle attività self-service e nel coinvolgimento digitale, riducendo il volume dei centri di contatto in entrata e rafforzando la soddisfazione dei clienti con il canale digitale.

### Come implementare

Utilizza il pattern [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Segnali comportamentali provenienti da sessioni di portale autenticate, quali l&#39;utilizzo del calcolatore di copertura, le visualizzazioni dei documenti relativi alle policy, i controlli dello stato delle richieste di rimborso e il coinvolgimento nell&#39;argomento delle domande frequenti, consentono di formare un modello di consigli che riunisce in modo dinamico i contenuti e gli strumenti più rilevanti per il contesto corrente di ciascun assicurato. Questo è il modello corretto quando la personalizzazione è guidata da segnali comportamentali impliciti all’interno di una sessione autenticata e l’obiettivo è la classificazione di rilevanza di un catalogo di contenuti o risorse, anziché Offer Decisioning, che richiede l’idoneità regolamentata e l’approvazione attuariale prima di presentare un’offerta di prodotto, o Cross-Channel with Decisioning, che è più appropriato quando si coordina un’offerta di prodotto su più canali.

### Considerazioni tecniche

- Applica le etichette di governance dei dati ai segnali comportamentali raccolti nel portale per gli assicurati per distinguere l’analisi del coinvolgimento dai dati assicurativi regolamentati e impedisce che qualsiasi segnale derivato dalla cronologia delle richieste di risarcimento confluisca in modelli di personalizzazione senza un’esplicita revisione attuariale e di conformità.
- Integrare il modello comportamentale con il sistema di gestione delle polizze per garantire che i contenuti e le raccomandazioni sugli strumenti riflettano il portafoglio attivo delle polizze di ciascun assicurato, presentando strumenti di copertura automatica per gli assicurati automatici e risorse sulla proprietà per i proprietari di case, senza esporre i dati grezzi delle polizze al modello di raccomandazione oltre la classificazione della linea di prodotto.
- Implementa controlli di conformità specifici per lo stato per garantire che la personalizzazione dei comportamenti non costituisca una raccomandazione assicurativa o una richiesta di marketing ai sensi delle normative statali applicabili, in particolare quando i segnali comportamentali potrebbero implicare il rilevamento del gap di copertura.
- Coordina i segnali di personalizzazione del portale con il portale degli agenti in modo che gli agenti al servizio degli assicurati che hanno mostrato un comportamento di ricerca self-service forte ricevano una visione consolidata dell’impegno digitale del cliente insieme alla cronologia del servizio.
