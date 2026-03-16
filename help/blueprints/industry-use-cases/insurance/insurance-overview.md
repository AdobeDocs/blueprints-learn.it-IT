---
title: Casi di utilizzo assicurazioni
description: Scopri in che modo le compagnie di assicurazione utilizzano Adobe Experience Platform per personalizzare la gestione delle policy, migliorare le esperienze di richiesta di risarcimento e promuovere la fidelizzazione dei clienti.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2494'
ht-degree: 0%

---


# Casi di utilizzo assicurazioni

Le organizzazioni assicurative utilizzano Adobe Experience Platform per unificare i dati dei titolari di polizze tra i sistemi di gestione delle polizze, delle richieste di rimborso e del coinvolgimento, al fine di fornire comunicazioni personalizzate in ogni fase della relazione con il cliente. Collegando i segnali comportamentali con le informazioni relative alle regole e alle richieste di rimborso, gli assicuratori possono coinvolgere in modo proattivo i clienti con offerte pertinenti, aggiornamenti tempestivi dei servizi e supporto significativo per la conservazione e il valore del ciclo di vita.

## Campagne di rinnovo dei criteri

Invia promemoria e offerte personalizzati per il rinnovo dei criteri in base alla cronologia dei criteri, alla registrazione delle richieste e alle preferenze di copertura di ogni cliente. Un&#39;azione di rinnovamento tempestiva e pertinente riduce i tassi di fallimento delle politiche e rafforza le relazioni a lungo termine con la clientela, rendendo più facile per gli assicurati capire le loro opzioni e agire.

### Impatto aziendale

Le organizzazioni che implementano campagne di rinnovo personalizzate delle policy registrano in genere un miglioramento del 25-35% nei tassi di rinnovo, riducendo direttamente l’abbandono dei clienti e proteggendo i ricavi premium ricorrenti.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Le date di rinnovo delle polizze sono eventi naturali che innescano un’attività di sensibilizzazione tempestiva e personalizzata nel momento in cui gli assicurati prendono la decisione di rinnovo.

### Considerazioni tecniche

- Integrazione con il sistema di gestione delle policy per ricevere gli eventi relativi alla data di rinnovo e i dettagli delle policy correnti, garantendo che i messaggi riflettano la copertura accurata e informazioni premium.
- Applica le etichette di governance dei dati a tutti i dati personali identificabili e di politica finanziaria per rispettare le normative statali in materia di assicurazione e i requisiti sulla privacy dei dati.
- Configurare le regole di soppressione per impedire l&#39;invio di messaggi di rinnovo agli assicurati che hanno già rinnovato o che dispongono di richieste attive che possono influire sui termini di rinnovo.
- Coordina i tempi con le assegnazioni degli agenti o dei broker in modo che i messaggi diretti al cliente siano in linea con qualsiasi attività svolta dall’agente assegnato.


## Consigli sui prodotti di cross-selling

Consigliare prodotti assicurativi aggiuntivi come la copertura di vita, casa o auto in base alle politiche esistenti di ciascun cliente, la fase di vita e il profilo di rischio. I consigli personalizzati sui prodotti aiutano gli assicurati a individuare le lacune di copertura e a creare un portafoglio di protezione più completo.

### Impatto aziendale

I consigli di cross-selling personalizzati in genere determinano un miglioramento del 20-30% nei tassi di conversione di cross-selling, aumentando le policy per famiglia e il valore complessivo della vita del cliente.

### Come implementare

Utilizza il pattern [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md). Real-time Decisioning valuta i segnali esistenti di copertura, stadio di vita e comportamento di ogni cliente per selezionare i prodotti consigliati più rilevanti dal catalogo disponibile.

### Considerazioni tecniche

- Integra i dati delle policy da tutte le linee di prodotto in un profilo cliente unificato in modo che il motore decisionale abbia una visione completa della copertura esistente durante la selezione dei consigli.
- Configurare le regole di idoneità all&#39;interno del modello decisionale per escludere i prodotti già in possesso di un cliente o in conflitto con le linee guida per la sottoscrizione per il proprio profilo di rischio.
- Applicare le regole di conformità alle normative per garantire che le raccomandazioni sui prodotti siano conformi ai requisiti di marketing e idoneità delle assicurazioni specifici dello stato.
- Coordina l’output delle decisioni con il portale degli agenti in modo che i prodotti consigliati siano visibili agli agenti assegnati che potrebbero avere conversazioni dirette con il cliente.


## Personalization processo richieste di rimborso

Personalizzare le comunicazioni di processo, gli aggiornamenti dello stato e le risorse di supporto in base al tipo di richiesta di rimborso, alle preferenze del cliente e alla cronologia delle richieste. Un&#39;esperienza di reclamo trasparente e ben comunicata riduce l&#39;ansia durante i momenti di stress e crea una fiducia duratura con gli assicurati.

### Impatto aziendale

Le comunicazioni personalizzate delle richieste di rimborso consentono di ottenere in genere un miglioramento del 40-50% nei punteggi di soddisfazione delle richieste di rimborso, riducendo i reclami e aumentando la probabilità di rinnovo delle politiche dopo una richiesta di rimborso.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Il processo di richiesta di rimborso è un&#39;esperienza in più fasi, con fasi distinte (archiviazione, indagine, adeguamento e liquidazione) che richiedono comunicazioni su misura e un calendario adattativo.

### Considerazioni tecniche

- Integrazione con il sistema di gestione delle richieste di rimborso per ricevere in tempo reale gli eventi di modifica dello stato che consentono di far avanzare il cliente attraverso la fase di percorso appropriata.
- Progettare la logica di diramazione del percorso che adatta il tono di messaggistica e i contenuti in base al tipo di richiesta di risarcimento, ad esempio collisione automatica rispetto a danni alle proprietà rispetto a richieste di risarcimento danni.
- Implementa le regole di soppressione durante le indagini attive sulle richieste di rimborso per impedire che messaggi di marketing o di cross-selling raggiungano i clienti in momenti sensibili.
- Assicurati che tutti i dati relativi alle richieste di rimborso che fluiscono nel profilo del cliente siano etichettati con restrizioni di governance dei dati appropriate per impedirne l’utilizzo al di fuori delle comunicazioni di servizio.


## Valutazione e prevenzione dei rischi

Fornisci informazioni personalizzate sulla valutazione del rischio e suggerimenti sulla prevenzione in base al tipo di policy, alla posizione geografica e ai fattori di rischio specifici di ciascun cliente. L’educazione proattiva al rischio aiuta gli assicurati a ridurre l’esposizione alle perdite, a vantaggio sia del cliente che dell’assicuratore.

### Impatto aziendale

L’impegno personalizzato per la prevenzione dei rischi comporta in genere un miglioramento del 30-40% nel coinvolgimento nella prevenzione, contribuendo a ridurre la frequenza delle richieste di risarcimento e a migliorare la soddisfazione dei clienti.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). L’educazione alla prevenzione dei rischi è più efficace in quanto è un percorso multi-touch sostenuto che fornisce indicazioni pertinenti nel tempo e si adatta in base al coinvolgimento dei clienti e ai fattori di rischio stagionali.

### Considerazioni tecniche

- Integrazione con fornitori di dati sul rischio di terze parti per informazioni su meteo, rischio geografico e rischio immobiliare che arricchiscono i profili dei clienti con punteggi di rischio specifici per la posizione.
- Progetta una logica di percorso stagionale che offra contenuti di prevenzione pertinenti in anticipo rispetto ai periodi ad alto rischio, come la preparazione della stagione degli uragani per gli assicurati costieri o suggerimenti meteorologici invernali per i clienti con clima freddo.
- Applicare etichette di governance dei dati per distinguere i dati di valutazione dei rischi utilizzati per l’educazione dei clienti dai dati utilizzati nelle decisioni di sottoscrizione attuariale.
- Coordinare il contenuto della prevenzione dei rischi con la copertura specifica dell&#39;assicurato in modo che le raccomandazioni siano pertinenti per i pericoli che la polizza effettivamente copre.


## Notifiche di modifica criteri

Invia notifiche personalizzate su modifiche dei criteri, aggiornamenti della copertura e nuove opzioni in base ai criteri specifici e alle preferenze di comunicazione di ciascun cliente. Notifiche chiare e tempestive tengono informati gli assicurati e riducono la confusione circa il loro status di copertura.

### Impatto aziendale

Le notifiche personalizzate di modifica delle policy consentono in genere un miglioramento del 50-60% nei tassi di conferma delle notifiche, riducendo le richieste di assistenza al cliente e migliorando la comprensione complessiva da parte dell’assicurato.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Gli eventi di modifica delle policy dal sistema di amministrazione fungono da trigger naturali per le notifiche immediate e rilevanti attraverso il canale preferito di ciascun cliente.

### Considerazioni tecniche

- Integrazione con il sistema di amministrazione delle policy per acquisire in tempo reale gli eventi di approvazione, modifica e modifica del rinnovo, garantendo che le notifiche riflettano lo stato delle policy più recente.
- Applicare le regole di conformità alle normative per garantire che le notifiche soddisfino i requisiti di comunicazione imposti dallo stato per le modifiche delle politiche, inclusi il linguaggio richiesto e i tempi di consegna.
- Configurare la logica di priorità dei canali in base all&#39;urgenza e al tipo di modifica; ad esempio, le riduzioni di copertura potrebbero richiedere canali più immediati rispetto agli aggiornamenti informativi.
- Mantenere un audit trail della consegna per tutte le notifiche di modifica delle policy per supportare la documentazione di conformità alle normative e la risoluzione delle controversie.


## Recupero di abbandono preventivo

Rivolgiti ai clienti che hanno iniziato ma non hanno completato un preventivo di assicurazione con messaggi di follow-up personalizzati e offerte personalizzate. Un intervento tempestivo di recupero riporta i potenziali clienti al processo di quotazione e risolve gli ostacoli comuni al completamento.

### Impatto aziendale

Le campagne di recupero dell’abbandono delle quotazioni determinano in genere un miglioramento del 20-30% nei tassi di completamento delle quotazioni, convertendo più potenziali clienti in assicurati e riducendo i costi di acquisizione dei clienti.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). L’abbandono delle quotazioni è un evento comportamentale che attiva un follow-up tempestivo mentre l’interesse e l’intento del potenziale cliente sono ancora freschi.

### Considerazioni tecniche

- Integrare con la piattaforma di quotazione online per acquisire eventi di abbandono insieme ai dettagli del preventivo già forniti dal cliente, consentendo un nuovo coinvolgimento personalizzato.
- Configurare regole temporali che bilanciano l’urgenza con la rispettabilità — follow-up iniziale entro poche ore, con un numero limitato di promemoria successivi nei giorni successivi.
- Applica le regole di consenso e privacy per garantire che il follow-up venga inviato solo ai potenziali clienti che hanno acconsentito alle comunicazioni di marketing, in particolare per i clienti che non hanno ancora stabilito una relazione basata su policy.
- Includi collegamenti profondi che restituiscono il prospect direttamente all&#39;offerta salvata anziché richiedere il riavvio del processo dall&#39;inizio.


## Offerte di prodotti basate su Life Stage

Identificare i clienti che entrano in una nuova fase di vita, ad esempio matrimonio, acquisto di una casa, famiglia in crescita o pensione, e offrire prodotti assicurativi pertinenti che soddisfino le loro esigenze di protezione in continua evoluzione. Il targeting nella fase di vita aiuta gli assicurati a creare la copertura giusta al momento giusto.

### Impatto aziendale

Le offerte di prodotti basati su fasi di vita raggiungono in genere un miglioramento del 35-45% nei tassi di adozione dei prodotti in fasi di vita, approfondendo le relazioni con i clienti durante i momenti decisionali chiave.

### Come implementare

Utilizza il Percorso [cross-channel con modello Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md). Le transizioni Life Stage traggono vantaggio dall&#39;orchestrazione cross-channel combinata con il decisioning in tempo reale per selezionare il prodotto più rilevante e distribuirlo nel canale preferito dal cliente nel momento ottimale.

### Considerazioni tecniche

- Crea modelli di rilevamento della fase di vita utilizzando segnali comportamentali quali cambiamenti di indirizzo, aggiornamenti dei beneficiari e modelli di ricerca online, combinati con eventi di cambiamento delle policy.
- Configura il motore delle decisioni con regole di idoneità e idoneità del prodotto che corrispondano a ogni fase del ciclo di vita alle raccomandazioni di copertura appropriate.
- Coordinare le offerte della fase di vita con l’agente o il broker assegnato in modo che siano preparati a supportare il cliente con una conversazione consultiva quando l’offerta viene consegnata.
- Applica le etichette di governance dei dati a qualsiasi origine dati di terze parti utilizzata per l’inferenza nella fase di vita per garantire la conformità alle normative sulla privacy dei dati e alle pratiche di marketing corrette.


## Opportunità di sconto e risparmio

Identifica e comunica opportunità di sconto personalizzate, come bundling, driver sicuri, fedeltà e sconti di fatturazione non cartacea, in base al profilo e al comportamento di ciascun cliente. Le comunicazioni proattive sul risparmio dimostrano valore e rafforzano la relazione prezzo-valore.

### Impatto aziendale

Le comunicazioni personalizzate relative a sconti e risparmi determinano in genere un miglioramento del 25-35% nei tassi di utilizzo degli sconti, migliorando la soddisfazione dei clienti e riducendo l&#39;abbandono basato sui prezzi.

### Come implementare

Utilizza il pattern [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md). Real-time Decisioning valuta l’idoneità di ogni cliente agli sconti disponibili e seleziona l’opportunità di risparmio più incisiva da presentare al momento giusto.

### Considerazioni tecniche

- Integrazione con i sistemi di valutazione e fatturazione delle policy per calcolare in tempo reale l’idoneità allo sconto e gli importi dei risparmi potenziali per ciascun cliente.
- Configura regole di decisione che tengano conto delle limitazioni dello stacking degli sconti e garantiscano che gli importi di risparmio comunicati siano accurati sotto il profilo attuariale e approvati dal team di determinazione prezzi.
- Per le comunicazioni relative agli sconti, applicare le normative specifiche dello stato, poiché alcuni stati prevedono limitazioni sul modo in cui gli sconti assicurativi possono essere commercializzati e applicati.
- Tieni traccia dei risultati di adozione degli sconti per perfezionare continuamente il modello decisionale e assegnare la priorità ai messaggi di risparmio che risuonano di più con i diversi segmenti di clienti.


## Denuncia e prevenzione delle frodi

Utilizza il rilevamento intelligente delle frodi per identificare i pattern delle richieste di rimborso sospette e personalizzare le comunicazioni investigative mantenendo al contempo la fiducia dei clienti. Un&#39;efficace prevenzione delle frodi protegge gli assicurati onesti, mantenendo equi i premi e assicurando che le richieste legittime siano trattate rapidamente.

### Impatto aziendale

I programmi intelligenti di prevenzione delle frodi nelle richieste di rimborso consentono in genere di migliorare del 15-25% i tassi di rilevamento delle frodi, riducendo i pagamenti fraudolenti e i costi complessivi delle richieste di rimborso.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Gli eventi di valutazione del rischio di frode attivano le comunicazioni di investigazione appropriate e gli adeguamenti del processo in tempo reale, garantendo che le richieste di rimborso segnalate ricevano attenzione immediata.

### Considerazioni tecniche

- È possibile integrare i punteggi relativi al rischio di frode dal sistema di analisi delle richieste di rimborso nel profilo cliente applicando etichette di governance dei dati rigorose per evitare che i dati delle indagini sulle frodi vengano visualizzati nelle comunicazioni rivolte al cliente.
- Progetta percorsi di comunicazione che mantengano un tono professionale e rispettoso per i clienti le cui richieste sono in fase di revisione, preservando la relazione indipendentemente dall’esito dell’indagine.
- Implementa controlli dell’accesso basati sui ruoli per garantire che gli indicatori di frode siano visibili solo ai team di investigatori autorizzati e non vengano mai visualizzati nelle visualizzazioni standard degli agenti o del servizio clienti.
- Coordinarsi con il servizio di risoluzione identità [!DNL Adobe Experience Platform] per rilevare pattern tra profili correlati, ad esempio indirizzi condivisi o numeri di telefono collegati a più richieste sospette.


## Programmi di benessere e prevenzione

Personalizza le comunicazioni del programma di benessere, i promemoria di partecipazione e le notifiche di ricompensa per i clienti di assicurazioni sulla salute e sulla vita in base ai loro obiettivi e al loro livello di coinvolgimento. Programmi di benessere attivi migliorano i risultati per la salute degli assicurati e costruiscono una base di clienti più forte e più impegnata.

### Impatto aziendale

Le comunicazioni personalizzate dei programmi di prevenzione e benessere in genere portano a un miglioramento del 30-40% nei tassi di partecipazione al programma, contribuendo a migliori risultati in termini di salute e a una riduzione della frequenza delle richieste di rimborso.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). I programmi di benessere sono esperienze di coinvolgimento sostenuto con milestone, sfide e premi che richiedono un&#39;orchestrazione adattiva basata sull&#39;attività e sul progresso di ciascun partecipante.

### Considerazioni tecniche

- Integrare con i feed di dati di applicazioni per dispositivi indossabili e di salute utilizzando l&#39;acquisizione in streaming di [!DNL Adobe Experience Platform], applicando etichette chiare per la governance dei dati per distinguere i dati relativi alla salute dai dati relativi a richieste di rimborso o sottoscrizioni.
- Implementa meccanismi di consenso separati per la raccolta dei dati sulla salute per garantire che i partecipanti comprendano come vengono utilizzati i loro dati sulle attività sanitarie e possano rinunciare senza influenzare i loro criteri.
- Progettare la logica di percorso che regola l&#39;intensità del programma e la frequenza di comunicazione in base al livello di coinvolgimento di ciascun partecipante per prevenire l&#39;affaticamento e incoraggiare la partecipazione prolungata.
- Garantire che l&#39;incentivo al benessere e il monitoraggio dei premi siano conformi alle normative assicurative applicabili in materia di incentivi per gli assicurati e programmi di sconti sui premi.


## Coordinamento agente e broker

Consente la comunicazione e il coordinamento personalizzati tra i clienti e gli agenti o i broker loro assegnati in base alle esigenze dei criteri, alla cronologia dei servizi e alle preferenze. Un migliore coordinamento crea un’esperienza fluida in cui i clienti si sentono supportati da un consulente esperto che comprende appieno la loro relazione.

### Impatto aziendale

Comunicazioni efficaci di coordinamento degli agenti e dei broker si traducono in genere in un miglioramento del 35-45% nel coinvolgimento degli agenti, che porta a relazioni più solide con i clienti e a una maggiore fidelizzazione guidata da interazioni di consulenza affidabili.

### Come implementare

Utilizza il pattern [Attivazione messaggi in uscita in batch](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md). Il coordinamento degli agenti si realizza in modo ottimale tramite attivazioni batch pianificate che forniscono agli agenti elenchi con priorità di assistenza ai clienti, punti di contatto e azioni consigliate a cadenza regolare.

### Considerazioni tecniche

- Integrare con il sistema di gestione degli agenti per mantenere accurate assegnazioni agente-cliente e garantire che le comunicazioni riflettano la relazione corretta, soprattutto durante le transizioni agente.
- Progetta l’attivazione dei dati nel portale dell’agente, in modo che gli agenti ricevano una visualizzazione consolidata delle informazioni sul cliente, dei prossimi rinnovi e delle azioni consigliate senza esporre dati comportamentali non elaborati.
- Applica le etichette di governance dei dati per limitare quali elementi dei dati del cliente vengono condivisi con partner di broker esterni rispetto agli agenti vincolati, rispettando i limiti contrattuali e normativi della condivisione dei dati.
- Implementa cicli di feedback dalle interazioni degli agenti nel profilo cliente in modo che le informazioni provenienti da conversazioni telefoniche o di persona arricchiscano la vista unificata e migliorino la personalizzazione futura.


## Risposta agli eventi catastrofici

Comunica in modo proattivo con i clienti delle aree colpite durante calamità naturali o eventi catastrofici con informazioni di supporto personalizzate, indicazioni sulla presentazione delle richieste di rimborso e risorse di emergenza. Una mobilitazione rapida ed empatica durante una crisi dimostra l’impegno dell’assicuratore a essere presente quando i clienti ne hanno più bisogno.

### Impatto aziendale

Le comunicazioni proattive di risposta agli eventi catastrofici consentono in genere di ottenere un miglioramento del 60-70% nella percentuale di comunicazioni dei clienti durante gli eventi, accelerando in modo significativo la presentazione delle richieste e rafforzando la fiducia e la fedeltà dei clienti a lungo termine.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Le dichiarazioni di eventi catastrofici fungono da trigger ad alta priorità per un’estensione immediata e personalizzata a tutti i contraenti nell’area geografica interessata.

### Considerazioni tecniche

- Integrazione con i servizi di monitoraggio delle catastrofi e i feed di dichiarazione delle catastrofi governative per attivare rapidamente le comunicazioni quando gli eventi vengono dichiarati per specifiche aree geografiche.
- Crea segmenti di pubblico geografico utilizzando i dati degli indirizzi dei contraenti e le informazioni sulla posizione delle proprietà per identificare con precisione i clienti nell’area interessata senza comunicare in modo eccessivo ai clienti non interessati.
- Configura il routing dei messaggi ad alta priorità che ignora le regole standard di limitazione della frequenza e soppressione per garantire che le informazioni critiche relative alla sicurezza e alle richieste di rimborso raggiungano immediatamente i clienti.
- Modelli di messaggio e configurazioni di percorso precompilati per i tipi di eventi catastrofici più comuni, in modo che le comunicazioni possano essere attivate entro poche ore dalla dichiarazione di un evento, anziché richiedere la creazione di contenuti durante la crisi.
