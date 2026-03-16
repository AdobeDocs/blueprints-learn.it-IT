---
title: Casi d’uso per contenuti multimediali e intrattenimento
description: Scopri come le organizzazioni di media e intrattenimento utilizzano Adobe Experience Platform per personalizzare l’individuazione dei contenuti, ridurre l’abbandono degli abbonati e aumentare il coinvolgimento del pubblico.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2644'
ht-degree: 0%

---


# Casi d’uso per contenuti multimediali e intrattenimento

Le organizzazioni che operano nel settore dei media e dell&#39;intrattenimento utilizzano Adobe Experience Platform per unificare i dati sul pubblico provenienti da piattaforme di streaming, librerie di contenuti e account di abbonati, creando un&#39;unica vista per ogni visualizzatore o ascoltatore. Questa base consente l’individuazione personalizzata dei contenuti, la conservazione proattiva degli abbonati e strategie di coinvolgimento che consentono ai tipi di pubblico di tornare per sempre.

## Motore consigli contenuti

Fornisci consigli sui contenuti personalizzati, inclusi film, programmi TV, musica e articoli, in base alla cronologia di visualizzazione e ascolto, alle preferenze e a un comportamento utente simile. Quando il pubblico vede contenuti su misura per i propri interessi, trascorre più tempo esplorando il catalogo e scoprendo titoli che altrimenti avrebbe mancato.

### Impatto aziendale

Le organizzazioni che distribuiscono motori di raccomandazione di contenuti personalizzati in genere assistono a un aumento del 30-40% nel coinvolgimento nei contenuti e a un aumento significativo del tempo totale di osservazione o ascolto per utente.

### Come implementare

Utilizza il pattern [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Questo approccio utilizza modelli di consigli basati sull’intelligenza artificiale che imparano continuamente dalle interazioni del pubblico per evidenziare i contenuti più rilevanti per ogni individuo.

### Considerazioni tecniche

- I metadati del catalogo dei contenuti, tra cui genere, cast, regista, tag dell’umore e valutazioni dei contenuti, devono essere acquisiti e tenuti aggiornati per garantire che i consigli riflettano l’intera gamma di titoli disponibili.
- I segnali di visualizzazione e ascolto devono scorrere quasi in tempo reale, in modo che i consigli vengano aggiornati all’interno di una singola sessione di navigazione mentre un utente guarda o salta i contenuti.
- I modelli di consigli richiedono una strategia di avvio a freddo per i nuovi abbonati che non hanno una cronologia di visualizzazione, in genere per tornare ai contenuti di tendenza, curati editorialmente o popolari a livello regionale.
- Le finestre di gestione delle licenze e della disponibilità dei contenuti devono essere incluse nella logica dei consigli in modo che gli utenti non vengano mai considerati titoli consigliati non disponibili nella propria area geografica o rimossi dal catalogo.


## Prevenzione abbandono abbonamento

Identifica gli abbonati che rischiano di essere annullati e coinvolgili con consigli, offerte e campagne di conservazione di contenuti personalizzati. Mantenere gli abbonati esistenti è molto più conveniente che acquistarne di nuovi, e una mobilitazione proattiva al momento giusto può evitare una quota significativa di cancellazioni.

### Impatto aziendale

Programmi efficaci di prevenzione dell’abbandono riducono del 20-30% l’abbandono degli abbonati, proteggendo le entrate ricorrenti e migliorando il valore a lungo termine per la durata del pubblico.

### Come implementare

Utilizza il Percorso [cross-channel con modello Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md). Questo approccio combina l’orchestrazione del percorso con il decisioning in tempo reale per selezionare la migliore offerta di conservazione o contenuti consigliati per ogni abbonato a rischio su ogni canale.

### Considerazioni tecniche

- Il punteggio di rischio di abbandono deve incorporare segnali di coinvolgimento come la diminuzione del tempo di attesa, la frequenza di accesso ridotta e le cadute di completamento dei contenuti per identificare gli abbonati a rischio prima che raggiungano la pagina di cancellazione.
- Le offerte di mantenimento devono essere suddivise in più livelli in base al valore e al livello di rischio dell’abbonato, da contenuti personalizzati di rilievo alle estensioni di piani scontati, per bilanciare la protezione dei ricavi con l’impatto sui margini.
- Il percorso deve eliminare i messaggi di conservazione per gli abbonati che hanno già rinnovato o aggiornato, richiedendo l’integrazione in tempo reale con il sistema di fatturazione dell’abbonamento.
- [!DNL Journey Optimizer] regole di decisioning devono tenere conto del tipo di piano, della durata e della cronologia di rimborso delle offerte passate del sottoscrittore per evitare di presentare offerte che si sentono generiche o ripetitive.


## Notifiche sulla versione di nuovi contenuti

Avvisa gli abbonati in merito alle nuove versioni dei contenuti che corrispondono alle loro preferenze e alla cronologia di visualizzazione. Le notifiche tempestive sui nuovi contenuti favoriscono il coinvolgimento immediato e ricordano agli abbonati il valore continuo del loro abbonamento.

### Impatto aziendale

Le notifiche di rilascio personalizzate in genere incrementano del 40-50% il coinvolgimento nei nuovi contenuti entro la prima settimana di rilascio, accelerando il pubblico e aumentando le metriche delle prestazioni dei contenuti.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio risponde agli eventi di rilascio dei contenuti, abbinando nuovi titoli ai profili di preferenza degli abbonati per fornire notifiche tempestive e pertinenti.

### Considerazioni tecniche

- I calendari di rilascio dei contenuti devono essere integrati in modo che le notifiche possano essere pianificate o attivate nel momento in cui diventano disponibili nuovi titoli, evitando avvisi prematuri per i contenuti non ancora accessibili.
- La corrispondenza delle preferenze degli abbonati deve prendere in considerazione più dimensioni, tra cui affinità di genere, attori o registi preferiti, serie guardate in precedenza e interessi di franchising, per garantire che le notifiche si sentano personalmente rilevanti.
- Il volume di notifica deve essere gestito con attenzione tramite il limite di frequenza per evitare che gli abbonati si sentano sopraffatti durante i periodi di rilascio massiccio di contenuti.
- I dati relativi al fuso orario e alle abitudini di visualizzazione dovrebbero informare i tempi di consegna in modo che le notifiche arrivino quando è più probabile che ogni abbonato sia coinvolto, anziché a un singolo orario di invio globale.


## Esperienza homepage personalizzata

Personalizza dinamicamente la pagina home e le pagine di individuazione dei contenuti per mostrare i contenuti più rilevanti in base al profilo e al comportamento di ogni utente. Quando i visualizzatori vedono immediatamente il contenuto allineato con i loro gusti all’apertura dell’app, interagiscono più rapidamente e navigano più a lungo.

### Impatto aziendale

Le esperienze di home page personalizzate determinano un aumento del 25-35% del coinvolgimento della home page e migliorano in modo significativo l’individuazione dei contenuti, in particolare per le piattaforme con librerie di contenuti di grandi dimensioni e in crescita.

### Come implementare

Utilizza il pattern [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Questo approccio utilizza strategie di selezione e modelli di classificazione per riordinare le righe di contenuto e i titoli in primo piano nella homepage in base al profilo e al comportamento in tempo reale di ogni visitatore.

### Considerazioni tecniche

- La personalizzazione della homepage deve essere eseguita abbastanza rapidamente da evitare ritardi di caricamento percepiti; spesso è necessario ricorrere a decisioni basate su Edge o al rendering lato server per soddisfare le aspettative relative ai tempi di risposta dei secondi secondari.
- La logica di personalizzazione deve combinare le preferenze individuali con priorità editoriali e promozionali, garantendo che le versioni con i puntini di sospensione, i contenuti stagionali e i titoli promossi dai partner ricevano ancora la visibilità appropriata.
- Le strategie per righe di contenuto, come &quot;Continua a guardare&quot;, &quot;Perché hai guardato&quot; e &quot;Tendenza attuale&quot;, richiedono input di dati distinti e una logica di classificazione che deve essere orchestrata in un layout di pagina coeso.
- L&#39;implementazione di [!DNL Experience Platform] Web SDK deve acquisire le interazioni della home page, inclusi gli scorrimento delle righe, i clic sulle sezioni e il comportamento al passaggio del mouse, per perfezionare continuamente i modelli di classificazione.


## Promemoria elenchi di controllo e preferiti

Invia promemoria agli utenti sui contenuti della watchlist che non hanno ancora guardato, insieme a consigli personalizzati per titoli simili. Le liste di controllo rappresentano segnali di intento forti, e i promemoria delicati possono convertire tale intento in visualizzazione effettiva.

### Impatto aziendale

I programmi di promemoria della watchlist raggiungono in genere un aumento del 30-40% nel tasso di completamento della watchlist, trasformando le intenzioni salvate in coinvolgimento attivo e aumentando l’utilizzo complessivo della piattaforma.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio attiva i promemoria in base all’attività dell’elenco di controllo e ai segnali di inattività, inviando punteggi tempestivi quando il contenuto è stato salvato ma non ancora avviato.

### Considerazioni tecniche

- La tempistica del promemoria deve essere calibrata in base a quanto tempo il contenuto è stato inserito nella watchlist e se l’utente è stato attivo sulla piattaforma di recente, evitando promemoria durante periodi di intenso coinvolgimento quando non sono necessari.
- I dati della watchlist devono essere sincronizzati tra i dispositivi in tempo reale, affinché un titolo aggiunto su dispositivi mobili venga immediatamente riportato nei calcoli di idoneità dei promemoria e non venga duplicato tra le piattaforme.
- I promemoria devono evidenziare i dettagli contestuali come le finestre di disponibilità in scadenza o le nuove stagioni di serie salvate per creare un’urgenza naturale senza sentirsi invadenti.
- I contenuti che sono stati rimossi dal catalogo o che non sono più disponibili nell’area dell’utente iscritto devono essere automaticamente esclusi dai messaggi di promemoria e sostituiti con consigli alternativi.


## Campagne di conversione di prova gratuite

Coinvolgi gli utenti di prova gratuiti con consigli e offerte di contenuti personalizzati per incoraggiare la conversione dell’abbonamento prima della fine del periodo di prova. La finestra di prova è un’opportunità fondamentale per dimostrare un valore sufficiente che gli utenti sono disposti a pagare, e un percorso di conversione strutturato offre prestazioni significativamente superiori a un singolo promemoria di fine prova.

### Impatto aziendale

Le campagne di conversione di prova ben progettate offrono un miglioramento del 25-35% nei tassi di conversione da prova a pagamento, aumentando direttamente l’efficienza di acquisizione degli abbonati e riducendo il costo per acquisizione.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Questo percorso di sviluppo multi-touch guida gli utenti di prova attraverso una sequenza di individuazione dei contenuti, dimostrazione del valore e messaggi di conversione, adattandoli in base al loro coinvolgimento durante la prova.

### Considerazioni tecniche

- Il percorso deve tenere traccia con precisione delle date di inizio e fine della sperimentazione, con una logica di ramificazione che regola la frequenza dei messaggi in base ai giorni di sperimentazione rimanenti e ai livelli di coinvolgimento osservati.
- I contenuti consigliati all’interno del percorso dovrebbero dare priorità ai titoli più coinvolgenti ed esclusivi della piattaforma per massimizzare il valore percepito di un abbonamento a pagamento durante la finestra di prova limitata.
- Gli utenti che eseguono la conversione prima del termine della versione di valutazione devono essere automaticamente spostati dal percorso di conversione in un nuovo flusso di benvenuto per gli abbonati, impedendo la messaggistica continua incentrata sulla versione di valutazione.
- Le condizioni di percorso di [!DNL Journey Optimizer] devono tenere conto del tipo di piano di valutazione, dell&#39;origine di riferimento e dell&#39;utilizzo del dispositivo per personalizzare l&#39;approccio di conversione per diversi segmenti di pubblico.


## Promemoria di visualizzazione di eventi live

Notifica agli utenti i prossimi eventi live, giochi sportivi o anteprime che corrispondono ai loro interessi e alla cronologia di visualizzazione. I contenuti live stimolano la visualizzazione degli appuntamenti, rafforzando le abitudini degli abbonati, e i promemoria tempestivi garantiscono che il pubblico non perda gli eventi a cui tiene.

### Impatto aziendale

I promemoria personalizzati per eventi live determinano in genere un aumento del 50-60% del pubblico di spettatori di eventi live, massimizzando il pubblico per una programmazione in tempo reale di alto valore.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio attiva le notifiche in base ai dati di pianificazione dell’evento, confrontando i prossimi eventi con i profili di interesse degli abbonati per inviare promemoria tempestivi.

### Considerazioni tecniche

- I dati di pianificazione degli eventi, inclusi gli orari di inizio, i team o i talenti partecipanti e i dettagli della trasmissione, devono essere acquisiti dai sistemi di programmazione e tenuti aggiornati per gestire le modifiche o le cancellazioni della pianificazione dell’ultimo minuto.
- I tempi di consegna dei promemoria devono tenere conto dei fusi orari e dei tipici lead time pre-evento; un promemoria inviato troppo presto viene dimenticato, mentre uno inviato troppo tardi salta l’inizio.
- La corrispondenza degli interessi deve includere sia preferenze esplicite, come team o generi preferiti, sia segnali impliciti come i pattern di visualizzazione degli eventi live passati, per identificare eventi rilevanti per ogni abbonato.
- Il coordinamento delle notifiche multi-dispositivo è importante affinché un abbonato non riceva contemporaneamente promemoria ridondanti sul telefono, sul tablet e sulla smart TV.


## Generazione di playlist personalizzate

Genera e aggiorna automaticamente playlist personalizzate in base alla cronologia di ascolto, alle preferenze e agli indicatori di umore di ogni utente. Le playlist curate riducono il lavoro di selezione dei contenuti e mantengono i ascoltatori coinvolti per sessioni più lunghe.

### Impatto aziendale

La generazione personalizzata di playlist aumenta del 40-50% il coinvolgimento nella playlist e estende significativamente la durata media della sessione di ascolto, rafforzando le abitudini di utilizzo giornaliere della piattaforma.

### Come implementare

Utilizza il pattern [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Questo approccio utilizza modelli basati sull’intelligenza artificiale che analizzano i pattern di ascolto, il comportamento degli skip e i segnali contestuali per generare e aggiornare playlist personalizzate per ogni utente.

### Considerazioni tecniche

- I metadati del catalogo musicale, tra cui il tempo, il genere, i tag dell’umore, le relazioni dell’artista e le funzioni audio, devono essere riccamente taggati per consentire una cura sfumata delle playlist che vada oltre la semplice corrispondenza del genere.
- La frequenza di aggiornamento delle playlist dovrebbe bilanciare la freschezza con la familiarità; gli ascoltatori si aspettano nuove scoperte ma desiderano anche rivedere i preferiti, quindi i modelli devono fondere l&#39;esplorazione con il comfort.
- Segnali contestuali come l’ora del giorno, il giorno della settimana e il dispositivo di ascolto possono informare l’umore della playlist e il livello di energia, creando playlist che si sentono appropriate per il momento.
- I dati comportamentali [!DNL Experience Platform] devono acquisire eventi di ascolto granulari, inclusi salti, riproduzioni, salvataggi e durata della sessione, per perfezionare continuamente i modelli di consigli.


## Sincronizzazione dei contenuti tra piattaforme

Fornisci un’esperienza di contenuti perfetta su tutti i dispositivi sincronizzando cronologia di visualizzazione, preferenze e consigli in tempo reale. I visualizzatori si aspettano di fermarsi su un dispositivo e riprendere su un altro senza perdere il posto, e un’esperienza coerente su più piattaforme rafforza le abitudini di utilizzo quotidiane.

### Impatto aziendale

La sincronizzazione dei contenuti tra piattaforme porta a un aumento del 30-40% del coinvolgimento tra dispositivi e riduce in modo significativo gli attriti che possono portare all’abbandono della sessione quando gli utenti passano da un dispositivo all’altro.

### Come implementare

Utilizza il pattern [Visitatore noto Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md). Questo approccio personalizza l’esperienza per gli utenti identificati sulle piattaforme web e app, garantendo uno stato dei contenuti coerente e consigli indipendentemente dal dispositivo.

### Considerazioni tecniche

- La risoluzione delle identità tra dispositivi deve collegare in modo affidabile le sessioni utente tra smart TV, app mobili, tablet e browser web per mantenere un singolo profilo unificato per ogni abbonato.
- I dati di avanzamento, tra cui la posizione esatta di riproduzione, lo stato di completamento dell’episodio e le preferenze di sottotitolo o traccia audio, devono essere sincronizzati con una latenza minima per offrire un’esperienza di ripresa davvero fluida.
- I modelli di consigli devono tenere conto del contesto del dispositivo, in quanto le preferenze di contenuto possono variare tra una sessione di mobile pendolarismo e una sessione di salotto serale su un grande schermo.
- I criteri di unione profili [!DNL Real-Time Customer Data Platform] devono essere configurati in modo da gestire sessioni simultanee su più dispositivi senza creare aggiornamenti di stato in conflitto.


## Personalization per condivisione social

Personalizza i prompt e i consigli per la condivisione social in base alle preferenze di contenuto e alle connessioni social di ogni utente. Rendendo facile e attraente per gli spettatori condividere ciò che amano, gli abbonati soddisfatti si trasformano in sostenitori organici che guidano la consapevolezza e l&#39;acquisizione.

### Impatto aziendale

I messaggi personalizzati di condivisione social raggiungono in genere un aumento del 20-30% del tasso di condivisione social, amplificando la portata organica e riducendo i costi di acquisizione a pagamento.

### Come implementare

Utilizza il pattern [Visitatore noto Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md). Questo approccio personalizza le esperienze di condivisione in-app per gli utenti identificati, visualizzando messaggi di richiesta di condivisione contestualmente rilevanti in base alle preferenze dell’utente e ai pattern di coinvolgimento.

### Considerazioni tecniche

- I prompt di condivisione dovrebbero essere attivati in momenti naturali di piacere, come il completamento di una serie degna di binge o la scoperta di un nuovo artista preferito, piuttosto che a intervalli arbitrari che si sentono invadenti.
- I messaggi e le immagini di condivisione precompilati devono essere generati in modo dinamico in base al contenuto specifico condiviso, incluse le miniature, le descrizioni e i collegamenti profondi appropriati che riportano i destinatari alla piattaforma.
- I controlli sulla privacy devono garantire che l’attività di visualizzazione sia condivisa solo quando l’utente avvia esplicitamente la condivisione; la condivisione passiva o automatica della cronologia di visualizzazione senza consenso può danneggiare l’attendibilità.
- L’integrazione della piattaforma social deve rispettare i criteri di condivisione di ogni rete e gestire l’autenticazione, i limiti di tariffa e i requisiti di formato dei contenuti per piattaforme come Instagram, TikTok e X.


## Funzione Premium Upselling

Identifica gli utenti che potrebbero beneficiare di funzionalità Premium e presentare offerte di upselling personalizzate in base ai loro pattern di utilizzo. La messaggistica mirata di upselling per gli utenti che stanno già dimostrando comportamenti allineati al valore premium è molto più efficace delle campagne di aggiornamento aperto.

### Impatto aziendale

Le campagne di upselling premium personalizzate incrementano del 15-25% l’adozione delle funzioni premium, generando un aumento del fatturato medio per utente e offrendo al contempo funzionalità che soddisfano le esigenze degli abbonati.

### Come implementare

Utilizza il pattern [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md). Questo approccio utilizza una logica decisionale centralizzata per valutare i pattern di utilizzo di ogni abbonato e selezionare l’offerta premium più rilevante al momento giusto.

### Considerazioni tecniche

- L’analisi del modello di utilizzo deve identificare comportamenti specifici che indicano una preparazione superiore, come l’uso frequente di funzioni disponibili in forma limitata sul piano di base, l’utilizzo multi-dispositivo o un elevato volume di consumo dei contenuti.
- La presentazione dell’offerta deve evidenziare i vantaggi premium specifici più rilevanti per il comportamento di ogni utente, anziché elencare genericamente tutte le funzioni premium; un utente che scarica frequentemente i contenuti deve vedere enfatizzata la visualizzazione offline.
- I tempi di upselling dovrebbero evitare momenti di frustrazione, come immediatamente dopo un blocco del paywall, e invece sfruttare i momenti di coinvolgimento positivo in cui l’abbonato è più ricettivo.
- [!DNL Journey Optimizer] regole di decisioning devono coordinare le offerte di upselling tra messaggi in-app, e-mail e notifiche push per presentare un&#39;offerta coerente senza sopraffare l&#39;abbonato tra i canali.


## Campagne di completamento dei contenuti

Ricordare agli utenti di terminare di guardare o ascoltare i contenuti che hanno iniziato ma non hanno completato, accompagnati da consigli personalizzati su cosa apprezzare dopo. I contenuti incompleti rappresentano un coinvolgimento non realizzato e un leggero spostamento spesso converte una sessione abbandonata in un’esperienza completata.

### Impatto aziendale

Le campagne di completamento dei contenuti raggiungono in genere un miglioramento del 35-45% nel tasso di completamento dei contenuti, aumentando il tempo totale di coinvolgimento e rafforzando la percezione del valore della piattaforma da parte dell’abbonato.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Questo approccio attiva i promemoria in base agli eventi di abbandono del contenuto, inviando messaggi tempestivi quando un utente si è messo in pausa lungo un titolo e non è più tornato all’interno di una finestra definita.

### Considerazioni tecniche

- Le soglie di abbandono devono essere calibrate per tipo di contenuto; un film in pausa all&#39;80% è un candidato di completamento forte, mentre un podcast interrotto dopo due minuti può indicare disinteresse piuttosto che interruzione dell&#39;ascolto.
- I messaggi di promemoria devono includere il titolo del contenuto specifico, una miniatura visiva e un collegamento diretto profondo che riprenda la riproduzione esattamente nel punto in cui l’utente si è interrotto.
- Il limite di frequenza deve evitare promemoria eccessivi per gli utenti che abitualmente campionano il contenuto senza finirlo; i bordi ripetuti per il contenuto che un utente ha scelto di abbandonare possono risultare invadenti.
- La disponibilità dei contenuti deve essere verificata al momento dell’invio, poiché i titoli possono uscire dalla piattaforma o modificare le aree di disponibilità tra l’evento di abbandono e la consegna del promemoria.
