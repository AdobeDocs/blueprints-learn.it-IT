---
title: Casi d’uso per contenuti multimediali e intrattenimento
description: Scopri come le organizzazioni di media e intrattenimento utilizzano Adobe Experience Platform per personalizzare l’individuazione dei contenuti, ridurre l’abbandono degli abbonati e aumentare il coinvolgimento del pubblico.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: cfcf689f-9579-447f-9ef9-72e0c80c1f27
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '3363'
ht-degree: 0%

---

# Casi d’uso per contenuti multimediali e intrattenimento

Le organizzazioni che operano nel settore dei media e dell&#39;intrattenimento utilizzano Adobe Experience Platform per unificare i dati sul pubblico provenienti da piattaforme di streaming, librerie di contenuti e account di abbonati, creando un&#39;unica vista per ogni visualizzatore o ascoltatore. Questa base consente l’individuazione personalizzata dei contenuti, la conservazione proattiva degli abbonati e strategie di coinvolgimento che consentono ai tipi di pubblico di tornare per sempre.

## Motore consigli contenuti

Fornisci consigli sui contenuti personalizzati, inclusi film, programmi TV, musica e articoli, in base alla cronologia di visualizzazione e ascolto, alle preferenze e a un comportamento utente simile. Quando il pubblico vede contenuti su misura per i propri interessi, trascorre più tempo esplorando il catalogo e scoprendo titoli che altrimenti avrebbe mancato.

### Impatto aziendale

Le organizzazioni che distribuiscono motori di consigli personalizzati sui contenuti vedono un miglioramento del coinvolgimento dei contenuti e un aumento significativo del tempo totale di visione o ascolto per utente.

### Come implementare

Utilizza il pattern [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Questo approccio utilizza modelli di consigli basati sull’intelligenza artificiale che imparano continuamente dalle interazioni del pubblico per evidenziare i contenuti più rilevanti per ogni individuo. Questo è il modello corretto quando il set di elementi è di grandi dimensioni e in continua evoluzione (cataloghi di contenuto) e la selezione è guidata dall’affinità comportamentale appresa dalla cronologia di visualizzazione, anziché da un set limitato di offerte disciplinate da regole di idoneità.

### Considerazioni tecniche

- I metadati del catalogo dei contenuti, tra cui genere, cast, regista, tag dell’umore e valutazioni dei contenuti, devono essere acquisiti e tenuti aggiornati per garantire che i consigli riflettano l’intera gamma di titoli disponibili.
- I segnali di visualizzazione e ascolto devono scorrere quasi in tempo reale, in modo che i consigli vengano aggiornati all’interno di una singola sessione di navigazione mentre un utente guarda o salta i contenuti.
- I modelli di consigli richiedono una strategia di avvio a freddo per i nuovi abbonati che non hanno una cronologia di visualizzazione, in genere per tornare ai contenuti di tendenza, curati editorialmente o popolari a livello regionale.
- Le finestre di gestione delle licenze e della disponibilità dei contenuti devono essere incluse nella logica dei consigli in modo che gli utenti non vengano mai considerati titoli consigliati non disponibili nella propria area geografica o rimossi dal catalogo.


## Prevenzione abbandono abbonamento

Identifica gli abbonati che rischiano di essere annullati e coinvolgili con consigli, offerte e campagne di conservazione di contenuti personalizzati. Mantenere gli abbonati esistenti è molto più conveniente che acquistarne di nuovi, e una mobilitazione proattiva al momento giusto può evitare una quota significativa di cancellazioni.

### Impatto aziendale

Programmi efficaci di prevenzione dell’abbandono offrono riduzioni significative dell’abbandono degli abbonati, proteggendo i ricavi ricorrenti e migliorando il valore a lungo termine del ciclo di vita del pubblico.

### Come implementare

Utilizza il Percorso [cross-channel con modello Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md). Questo approccio combina l’orchestrazione del percorso con il decisioning in tempo reale per selezionare la migliore offerta di conservazione o contenuti consigliati per ogni abbonato a rischio su ogni canale. Questo è il modello corretto quando il percorso deve coordinare la distribuzione tra i canali per evitare offerte di conservazione duplicate e quando la selezione delle offerte richiede regole di idoneità basate sul valore e sul livello di rischio dell’abbonato: l’orchestrazione in più passaggi non fornisce da sola il livello decisionale in tempo reale necessario.

### Considerazioni tecniche

- Il punteggio di rischio di abbandono deve incorporare segnali di coinvolgimento come la diminuzione del tempo di attesa, la frequenza di accesso ridotta e le cadute di completamento dei contenuti per identificare gli abbonati a rischio prima che raggiungano la pagina di cancellazione.
- Le offerte di mantenimento devono essere suddivise in più livelli in base al valore e al livello di rischio dell’abbonato, da contenuti personalizzati di rilievo alle estensioni di piani scontati, per bilanciare la protezione dei ricavi con l’impatto sui margini.
- Il percorso deve eliminare i messaggi di conservazione per gli abbonati che hanno già rinnovato o aggiornato, richiedendo l’integrazione in tempo reale con il sistema di fatturazione dell’abbonamento.
- [!DNL Journey Optimizer] regole di decisioning devono tenere conto del tipo di piano, della durata e della cronologia di rimborso delle offerte passate del sottoscrittore per evitare di presentare offerte che si sentono generiche o ripetitive.


## Notifiche sulla versione di nuovi contenuti

Avvisa gli abbonati in merito alle nuove versioni dei contenuti che corrispondono alle loro preferenze e alla cronologia di visualizzazione. Le notifiche tempestive sui nuovi contenuti favoriscono il coinvolgimento immediato e ricordano agli abbonati il valore continuo del loro abbonamento.

### Impatto aziendale

Le notifiche di rilascio personalizzate migliorano il coinvolgimento nei nuovi contenuti entro la prima settimana di rilascio, accelerano il pubblico e migliorano le metriche di prestazione dei contenuti.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio risponde agli eventi di rilascio dei contenuti, abbinando nuovi titoli ai profili di preferenza degli abbonati per fornire notifiche tempestive e pertinenti. Questo è lo schema corretto quando l’attivatore è un evento di sistema (rilascio di contenuti) anziché il comportamento del cliente e la comunicazione richiesta è immediata e reattiva anziché una sequenza di acquisizione sostenuta.

### Considerazioni tecniche

- I calendari di rilascio dei contenuti devono essere integrati in modo che le notifiche possano essere pianificate o attivate nel momento in cui diventano disponibili nuovi titoli, evitando avvisi prematuri per i contenuti non ancora accessibili.
- La corrispondenza delle preferenze degli abbonati deve prendere in considerazione più dimensioni, tra cui affinità di genere, attori o registi preferiti, serie guardate in precedenza e interessi di franchising, per garantire che le notifiche si sentano personalmente rilevanti.
- Il volume di notifica deve essere gestito con attenzione tramite il limite di frequenza per evitare che gli abbonati si sentano sopraffatti durante i periodi di rilascio massiccio di contenuti.
- I dati relativi al fuso orario e alle abitudini di visualizzazione dovrebbero informare i tempi di consegna in modo che le notifiche arrivino quando è più probabile che ogni abbonato sia coinvolto, anziché a un singolo orario di invio globale.


## Esperienza homepage personalizzata

Personalizza dinamicamente la pagina home e le pagine di individuazione dei contenuti per mostrare i contenuti più rilevanti in base al profilo e al comportamento di ogni utente. Quando i visualizzatori vedono immediatamente il contenuto allineato con i loro gusti all’apertura dell’app, interagiscono più rapidamente e navigano più a lungo.

### Impatto aziendale

Le esperienze di home page personalizzate migliorano il coinvolgimento della home page e migliorano in modo significativo l’individuazione dei contenuti, in particolare per le piattaforme con librerie di contenuti di grandi dimensioni e in crescita.

### Come implementare

Utilizza il pattern [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). This approach uses selection strategies and ranking models to reorder content rows and featured titles on the homepage based on each visitor&#39;s profile and real-time behavior. This is the right pattern when the item set is large and continuously changing and selection is driven by behavioral affinity to rank content rows dynamically — rather than a static curated set or simple attribute-based personalization.

### Considerazioni tecniche

- Homepage personalization must execute quickly enough to avoid perceived load delays; edge-based decisioning or server-side rendering is often required to meet sub-second response time expectations.
- The personalization logic should blend individual preferences with editorial and promotional priorities, ensuring that tentpole releases, seasonal content, and partner-promoted titles still receive appropriate visibility.
- Content row strategies, such as &quot;Continue Watching,&quot; &quot;Because You Watched,&quot; and &quot;Trending Now,&quot; each require distinct data inputs and ranking logic that must be orchestrated into a cohesive page layout.
- [!DNL Experience Platform] Web SDK implementation must capture homepage interactions, including row scrolls, tile clicks, and hover behavior, to continuously refine the ranking models.


## Watchlist and Favorites Reminders

Send reminders to users about content in their watchlist that they have not watched yet, along with personalized recommendations for similar titles. Watchlists represent strong intent signals, and gentle reminders can convert that intent into actual viewing.

### Impatto aziendale

Watchlist reminder programs drive improved watchlist completion rates, turning saved intent into active engagement and increasing overall platform usage.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). This approach triggers reminders based on watchlist activity and inactivity signals, sending timely nudges when content has been saved but not yet started. This is the right pattern when a discrete behavioral signal (watchlist inactivity) is the trigger and the required response is a single, time-sensitive message — rather than a multi-step sequence or a continuous recommendation stream.

### Considerazioni tecniche

- Reminder timing should be calibrated based on how long content has been on the watchlist and whether the user has been active on the platform recently, avoiding reminders during periods of heavy engagement when they are unnecessary.
- Watchlist data must sync across devices in real time so that a title added on mobile is immediately reflected in reminder eligibility calculations and not duplicated across platforms.
- Reminders should highlight contextual details such as expiring availability windows or new seasons of saved series to create natural urgency without feeling pushy.
- Content that has been removed from the catalog or is no longer available in the subscriber&#39;s region must be automatically excluded from reminder messages and replaced with alternative recommendations.


## Free Trial Conversion Campaigns

Engage free trial users with personalized content recommendations and offers to encourage subscription conversion before the trial period ends. The trial window is a critical opportunity to demonstrate enough value that users are willing to pay, and a structured conversion journey significantly outperforms a single end-of-trial reminder.

### Impatto aziendale

Well-designed trial conversion campaigns deliver meaningful improvements in trial-to-paid conversion rates, directly increasing subscriber acquisition efficiency and reducing cost per acquisition.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Questo percorso di sviluppo multi-touch guida gli utenti di prova attraverso una sequenza di individuazione dei contenuti, dimostrazione del valore e messaggi di conversione, adattandoli in base al loro coinvolgimento durante la prova. Questo è il modello corretto quando il caso d’uso richiede un flusso sequenziale di più messaggi nell’arco di giorni con diramazione condizionale in base agli eventi di coinvolgimento e alla durata di prova rimanente. Un singolo messaggio attivato non può soddisfare la logica di dipendenza tra i passaggi o la necessità di regolazioni della cadenza.

### Considerazioni tecniche

- Il percorso deve tenere traccia con precisione delle date di inizio e fine della sperimentazione, con una logica di ramificazione che regola la frequenza dei messaggi in base ai giorni di sperimentazione rimanenti e ai livelli di coinvolgimento osservati.
- I contenuti consigliati all’interno del percorso dovrebbero dare priorità ai titoli più coinvolgenti ed esclusivi della piattaforma per massimizzare il valore percepito di un abbonamento a pagamento durante la finestra di prova limitata.
- Gli utenti che eseguono la conversione prima del termine della versione di valutazione devono essere automaticamente spostati dal percorso di conversione in un nuovo flusso di benvenuto per gli abbonati, impedendo la messaggistica continua incentrata sulla versione di valutazione.
- Le condizioni di percorso di [!DNL Journey Optimizer] devono tenere conto del tipo di piano di valutazione, dell&#39;origine di riferimento e dell&#39;utilizzo del dispositivo per personalizzare l&#39;approccio di conversione per diversi segmenti di pubblico.


## Promemoria di visualizzazione di eventi live

Notifica agli utenti i prossimi eventi live, giochi sportivi o anteprime che corrispondono ai loro interessi e alla cronologia di visualizzazione. I contenuti live stimolano la visualizzazione degli appuntamenti, rafforzando le abitudini degli abbonati, e i promemoria tempestivi garantiscono che il pubblico non perda gli eventi a cui tiene.

### Impatto aziendale

I promemoria personalizzati per eventi live migliorano la visibilità degli eventi live, ottimizzando il pubblico per una programmazione in tempo reale di alto valore.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio attiva le notifiche in base ai dati di pianificazione dell’evento, confrontando i prossimi eventi con i profili di interesse degli abbonati per inviare promemoria tempestivi. Questo è lo schema corretto quando l’attivatore è un evento di sistema (pianificazione di eventi) anziché il comportamento del cliente e la comunicazione richiesta è immediata e vincolata al tempo, anziché una sequenza di acquisizione sostenuta.

### Considerazioni tecniche

- I dati di pianificazione degli eventi, inclusi gli orari di inizio, i team o i talenti partecipanti e i dettagli della trasmissione, devono essere acquisiti dai sistemi di programmazione e tenuti aggiornati per gestire le modifiche o le cancellazioni della pianificazione dell’ultimo minuto.
- I tempi di consegna dei promemoria devono tenere conto dei fusi orari e dei tipici lead time pre-evento; un promemoria inviato troppo presto viene dimenticato, mentre uno inviato troppo tardi salta l’inizio.
- La corrispondenza degli interessi deve includere sia preferenze esplicite, come team o generi preferiti, sia segnali impliciti come i pattern di visualizzazione degli eventi live passati, per identificare eventi rilevanti per ogni abbonato.
- Il coordinamento delle notifiche multi-dispositivo è importante affinché un abbonato non riceva contemporaneamente promemoria ridondanti sul telefono, sul tablet e sulla smart TV.


## Generazione di playlist personalizzate

Genera e aggiorna automaticamente playlist personalizzate in base alla cronologia di ascolto, alle preferenze e agli indicatori di umore di ogni utente. Le playlist curate riducono il lavoro di selezione dei contenuti e mantengono i ascoltatori coinvolti per sessioni più lunghe.

### Impatto aziendale

La generazione di playlist personalizzate migliora il coinvolgimento delle playlist e estende in modo significativo la durata media delle sessioni di ascolto, rafforzando le abitudini di utilizzo giornaliere della piattaforma.

### Come implementare

Utilizza il pattern [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Questo approccio utilizza modelli basati sull’intelligenza artificiale che analizzano i pattern di ascolto, il comportamento degli skip e i segnali contestuali per generare e aggiornare playlist personalizzate per ogni utente. Questo è lo schema giusto quando l&#39;insieme di elementi è grande e in continua evoluzione e la selezione è guidata dall&#39;affinità comportamentale dalla cronologia di ascolto e dai segnali d&#39;umore — piuttosto che un insieme limitato di playlist governate da regole editoriali.

### Considerazioni tecniche

- I metadati del catalogo musicale, tra cui il tempo, il genere, i tag dell’umore, le relazioni dell’artista e le funzioni audio, devono essere riccamente taggati per consentire una cura sfumata delle playlist che vada oltre la semplice corrispondenza del genere.
- La frequenza di aggiornamento delle playlist dovrebbe bilanciare la freschezza con la familiarità; gli ascoltatori si aspettano nuove scoperte ma desiderano anche rivedere i preferiti, quindi i modelli devono fondere l&#39;esplorazione con il comfort.
- Segnali contestuali come l’ora del giorno, il giorno della settimana e il dispositivo di ascolto possono informare l’umore della playlist e il livello di energia, creando playlist che si sentono appropriate per il momento.
- I dati comportamentali [!DNL Experience Platform] devono acquisire eventi di ascolto granulari, inclusi salti, riproduzioni, salvataggi e durata della sessione, per perfezionare continuamente i modelli di consigli.


## Sincronizzazione dei contenuti tra piattaforme

Fornisci un’esperienza di contenuti perfetta su tutti i dispositivi sincronizzando cronologia di visualizzazione, preferenze e consigli in tempo reale. I visualizzatori si aspettano di fermarsi su un dispositivo e riprendere su un altro senza perdere il posto, e un’esperienza coerente su più piattaforme rafforza le abitudini di utilizzo quotidiane.

### Impatto aziendale

La sincronizzazione dei contenuti tra piattaforme migliora il coinvolgimento tra dispositivi e riduce in modo significativo gli attriti che possono causare l’abbandono della sessione quando gli utenti passano da un dispositivo all’altro.

### Come implementare

Utilizza il pattern [Visitatore noto Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md). Questo approccio personalizza l’esperienza per gli utenti identificati sulle piattaforme web e app, garantendo uno stato dei contenuti coerente e consigli indipendentemente dal dispositivo. Questo è il pattern corretto quando la personalizzazione è guidata dagli attributi di profilo (identità tra dispositivi, stato di avanzamento dell’orologio) e dall’appartenenza ai segmenti, anziché da un modello di affinità comportamentale o da una sequenza di orchestrazione del percorso.

### Considerazioni tecniche

- La risoluzione delle identità tra dispositivi deve collegare in modo affidabile le sessioni utente tra smart TV, app mobili, tablet e browser web per mantenere un singolo profilo unificato per ogni abbonato.
- I dati di avanzamento, tra cui la posizione esatta di riproduzione, lo stato di completamento dell’episodio e le preferenze di sottotitolo o traccia audio, devono essere sincronizzati con una latenza minima per offrire un’esperienza di ripresa davvero fluida.
- I modelli di consigli devono tenere conto del contesto del dispositivo, in quanto le preferenze di contenuto possono variare tra una sessione di mobile pendolarismo e una sessione di salotto serale su un grande schermo.
- I criteri di unione profili [!DNL Real-Time Customer Data Platform] devono essere configurati in modo da gestire sessioni simultanee su più dispositivi senza creare aggiornamenti di stato in conflitto.


## Personalization per condivisione social

Personalizza i prompt e i consigli per la condivisione social in base alle preferenze di contenuto e alle connessioni social di ogni utente. Rendendo facile e attraente per gli spettatori condividere ciò che amano, gli abbonati soddisfatti si trasformano in sostenitori organici che guidano la consapevolezza e l&#39;acquisizione.

### Impatto aziendale

Personalized social sharing prompts achieve improved social sharing rates, amplifying organic reach and reducing paid acquisition costs.

### Come implementare

Utilizza il pattern [Visitatore noto Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md). This approach personalizes in-app sharing experiences for identified users, surfacing contextually relevant sharing prompts based on the user&#39;s preferences and engagement patterns. This is the right pattern when personalization is driven by profile attributes and known engagement context rather than a behavioral affinity model, and the goal is to enhance in-moment experience without orchestrating a journey sequence.

### Considerazioni tecniche

- Sharing prompts should be triggered at natural moments of delight, such as completing a binge-worthy series or discovering a new favorite artist, rather than at arbitrary intervals that feel intrusive.
- Pre-populated sharing messages and imagery must be dynamically generated based on the specific content being shared, including appropriate thumbnails, descriptions, and deep links that drive recipients back to the platform.
- Privacy controls must ensure that viewing activity is only shared when the user explicitly initiates sharing; passive or automatic sharing of watch history without consent can damage trust.
- Social platform integration must comply with each network&#39;s sharing policies and handle authentication, rate limits, and content format requirements for platforms like Instagram, TikTok, and X.


## Premium Feature Upsell

Identifica gli utenti che potrebbero beneficiare di funzionalità Premium e presentare offerte di upselling personalizzate in base ai loro pattern di utilizzo. Targeted upsell messaging to users who are already demonstrating behaviors aligned with premium value is far more effective than blanket upgrade campaigns.

### Impatto aziendale

Personalized premium upsell campaigns drive improved premium feature adoption, growing average revenue per user while delivering features that genuinely match subscriber needs.

### Come implementare

Use the [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) pattern. This approach uses centralized decision logic to evaluate each subscriber&#39;s usage patterns and select the most relevant premium offer at the right moment. This is the right pattern when offer selection must account for usage pattern constraints and premium tier eligibility rules — constraints that require governed decisioning logic rather than behavioral affinity ranking alone.

### Considerazioni tecniche

- Usage pattern analysis must identify specific behaviors that indicate premium readiness, such as frequent use of features available in limited form on the basic plan, multi-device usage, or high content consumption volume.
- Offer presentation should highlight the specific premium benefits most relevant to each user&#39;s behavior rather than listing all premium features generically; a user who frequently downloads content should see offline viewing emphasized.
- Upsell timing should avoid moments of frustration, such as immediately after a paywall block, and instead leverage positive engagement moments when the subscriber is most receptive.
- [!DNL Journey Optimizer] decisioning rules must coordinate upsell offers across in-app messages, email, and push notifications to present a consistent offer without overwhelming the subscriber across channels.


## Content Completion Campaigns

Remind users to finish watching or listening to content they started but did not complete, accompanied by personalized recommendations for what to enjoy next. I contenuti incompleti rappresentano un coinvolgimento non realizzato e un leggero spostamento spesso converte una sessione abbandonata in un’esperienza completata.

### Impatto aziendale

Le campagne di completamento dei contenuti migliorano i tassi di completamento dei contenuti, aumentando il tempo totale di coinvolgimento e rafforzando la percezione del valore della piattaforma da parte degli abbonati.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio attiva i promemoria in base agli eventi di abbandono del contenuto, inviando messaggi tempestivi quando un utente si è messo in pausa lungo un titolo e non è più tornato all’interno di una finestra definita. Questo è lo schema corretto quando un segnale comportamentale discreto (abbandono dei contenuti) è l’attivatore e la risposta richiesta è un messaggio singolo e sensibile al tempo con contesto, anziché una selezione di offerte dinamiche o di percorso in più passaggi.

### Considerazioni tecniche

- Le soglie di abbandono devono essere calibrate per tipo di contenuto; un film in pausa all&#39;80% è un candidato di completamento forte, mentre un podcast interrotto dopo due minuti può indicare disinteresse piuttosto che interruzione dell&#39;ascolto.
- I messaggi di promemoria devono includere il titolo del contenuto specifico, una miniatura visiva e un collegamento diretto profondo che riprenda la riproduzione esattamente nel punto in cui l’utente si è interrotto.
- Il limite di frequenza deve evitare promemoria eccessivi per gli utenti che abitualmente campionano il contenuto senza finirlo; i bordi ripetuti per il contenuto che un utente ha scelto di abbandonare possono risultare invadenti.
- La disponibilità dei contenuti deve essere verificata al momento dell’invio, poiché i titoli possono uscire dalla piattaforma o modificare le aree di disponibilità tra l’evento di abbandono e la consegna del promemoria.


## Analisi del driver di abbandono degli abbonati e del coinvolgimento dei contenuti

Identifica i pattern di consumo dei contenuti, le modifiche della frequenza di coinvolgimento e i comportamenti di interazione del catalogo che precedono la cancellazione dell’abbonato e misura il modo in cui l’affinità dei contenuti varia tra i segmenti di abbonato e le coorti di acquisizione. Le attività di streaming e pubblicazione che non riescono a collegare il comportamento dei contenuti ai risultati di abbandono prendono decisioni sull’investimento dei contenuti in base ai conteggi di visualizzazione aggregata anziché all’impatto sulla conservazione.

### Impatto aziendale

La correlazione dei modelli di coinvolgimento dei contenuti con i risultati di fidelizzazione degli abbonati offre ai prodotti, alla strategia dei contenuti e ai team di marketing una base fattuale per dare priorità agli investimenti nel catalogo e progettare campagne di ricoinvolgimento in base ai comportamenti che supportano effettivamente gli abbonamenti.

### Come implementare

Utilizza il pattern [Analisi cliente e generazione Insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md). Questo approccio collega i dati degli eventi in streaming, i metadati dei contenuti, i record del ciclo di vita degli abbonamenti e la cronologia delle interazioni delle campagne a Customer Journey Analytics, dove l’analisi della conservazione per coorte misura il modo in cui l’affinità dei contenuti è correlata al mandato degli abbonati e l’analisi dell’abbandono identifica i pattern di abbandono del coinvolgimento che precedono l’annullamento. Questo è lo schema corretto quando l’obiettivo è comprendere i driver comportamentali dell’abbandono e le prestazioni dei contenuti, anziché attivare un messaggio di recupero o attivare un pubblico a rischio di abbandono per la soppressione.

### Considerazioni tecniche

- Gli eventi di consumo dei contenuti devono includere sia identificatori di contenuto che metadati a livello di sessione (eventi di inizio, pausa, completamento e salto), in modo da poter misurare la profondità del coinvolgimento oltre i conteggi di riproduzione non elaborati in CJA.
- Gli eventi del ciclo di vita dell’abbonamento, tra cui l’inizio della valutazione, la conversione, il mancato pagamento, il downgrade e l’annullamento, devono essere acquisiti come eventi discreti con marche temporali precise in modo che le finestre comportamentali pre-annullamento possano essere definite con precisione nei filtri di CJA.
- Gli attributi del catalogo dei contenuti come genere, formato, associazione di serie e attualità del rilascio devono essere disponibili come set di dati di ricerca nella connessione CJA, in modo che l’analisi del coinvolgimento dei contenuti possa essere suddivisa per dimensione del catalogo anziché richiedere l’analisi a livello del singolo titolo.
- L’analisi per coorte che confronta le curve di fidelizzazione per canale di acquisizione e il contenuto originale visualizzato richiede che sia la sorgente di acquisizione che il contenuto visualizzato per primo vengano acquisiti come dimensioni di profilo o di primo evento, disponibili per la definizione per coorte in CJA.
