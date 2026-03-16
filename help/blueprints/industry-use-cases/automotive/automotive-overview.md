---
title: Casi di utilizzo del settore automobilistico
description: Scopri come le organizzazioni del settore automobilistico utilizzano Adobe Experience Platform per personalizzare il percorso di acquisto dei veicoli, migliorare la fidelizzazione dei servizi e fidelizzare i proprietari.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '1843'
ht-degree: 0%

---


# Casi d’uso per il settore automobilistico

Le organizzazioni automobilistiche utilizzano Adobe Experience Platform per unificare i dati dei clienti provenienti dalle interazioni dei concessionari, dalla ricerca online sui veicoli, dai record dei servizi e dai sistemi di automobili collegate in un&#39;unica vista di ciascun proprietario. Questa base consente esperienze personalizzate durante l’intero ciclo di vita della proprietà, dalla ricerca iniziale sui veicoli all’acquisto, al servizio e alla fedeltà.

## Riepilogo del caso d’uso

| Caso d’uso | Descrizione | Impatto aziendale | Modello di implementazione |
| --- | --- | --- | --- |
| [Percorso di acquisto veicolo Personalization](#vehicle-purchase-journey-personalization) | Personalizza il percorso di acquisto del veicolo dalla ricerca all’acquisto con le relative raccomandazioni per il veicolo, le opzioni di finanziamento e le informazioni sui dealer. Quando i potenziali acquirenti ricevono una guida personalizzata in ogni fase, si spostano attraverso il funnel di vendita più rapidamente e con maggiore fiducia. | Aumento del 20-30% dei tassi di conversione lead-acquisto, miglioramento della pipeline di vendita | [Percorso cross-channel con decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| [Promemoria appuntamenti di servizio](#service-appointment-reminders) | Invia promemoria di assistenza personalizzati in base al chilometraggio del veicolo, alla cronologia del servizio e alle preferenze del cliente. Un&#39;attività proattiva mantiene i veicoli sotto controllo e garantisce il ritorno dei clienti al dealer piuttosto che cercare fornitori terzi. | Aumento del 40-50% degli appuntamenti di servizio, aumento dei ricavi | [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [Campagne Di Valore Di permuta](#trade-in-value-campaigns) | Offrire in modo proattivo valutazioni del valore di permuta ai clienti che potrebbero essere pronti per l&#39;aggiornamento. Raggiungere i proprietari nel punto giusto del loro ciclo di proprietà accelera il percorso verso un nuovo acquisto di veicoli. | aumento del 25-35% del trade-in, aumento delle vendite di nuovi veicoli | [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [Consigli su parti e accessori](#parts-and-accessories-recommendations) | Consigliare parti, accessori e aggiornamenti pertinenti in base al modello del veicolo, alla durata di proprietà e alle preferenze del cliente. Raccomandazioni personalizzate per il mercato post-vendita generano ricavi incrementali e aiutano i proprietari a ottenere di più dal proprio veicolo. | Aumento del 30-40% degli acquisti di parti/accessori, aumento dei ricavi nel mercato post-vendita | [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| [Notifiche di richiamo veicolo](#vehicle-recall-notifications) | Inviare notifiche di richiamo personalizzate con le opzioni di pianificazione del servizio e le informazioni sulla sicurezza. Comunicazioni di richiamo tempestive e chiare proteggono la sicurezza dei clienti e dimostrano l&#39;impegno del brand per un supporto responsabile della proprietà. | Aumento del 60-70% delle percentuali di risposta al richiamo, maggiore conformità in materia di sicurezza | [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [Nuove Campagne Di Lancio Modelli](#new-model-launch-campaigns) | Puoi indirizzare l’attività ai clienti che potrebbero essere interessati ai nuovi lanci di modelli in base al veicolo, alle preferenze e alla cronologia degli acquisti correnti. Il targeting mirato del pubblico massimizza l’impatto del lancio e crea uno slancio nell’ordine iniziale. | Aumento del 35-45% del coinvolgimento nelle campagne di lancio, maggiore interesse per i nuovi modelli | [Attivazione messaggi in uscita in batch](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| [Offerte di finanziamento e assicurazione](#financing-and-insurance-offers) | Presenta offerte di finanziamento e assicurazione personalizzate in base al profilo di credito, alla selezione dei veicoli e alla tempistica di acquisto. Prodotti finanziari su misura eliminano le barriere all&#39;acquisto e aiutano i clienti a sentirsi sicuri delle loro condizioni. | Aumento del 25-35% dei tassi di accettazione del finanziamento, aumento dei ricavi per vendita | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| [Pianificazione unità di prova](#test-drive-scheduling) | Pianificazione personalizzata delle unità di test con consigli dei dealer e disponibilità del veicolo. Rendendo più semplice per gli acquirenti interessati mettersi al volante si accelera il percorso di acquisto. | Aumento del 50-60% dei tassi di completamento delle unità di test, miglioramento della conversione delle vendite | [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [Programmi fedeltà del proprietario](#owner-loyalty-programs) | Personalizza comunicazioni, premi e offerte esclusive del programma fedeltà in base alla cronologia della proprietà e al livello di fedeltà. Riconoscere i proprietari a lungo termine rafforza la connessione emotiva con il brand. | Aumento del 40-50% del coinvolgimento nel programma fedeltà, aumento degli acquisti ripetuti | [Percorso cross-channel con decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| [Garanzia e piani di assistenza estesi](#warranty-and-extended-service-plans) | Consigliare la garanzia e piani di assistenza estesi in tempi ottimali in base all&#39;età del veicolo, al chilometraggio e ai modelli di acquisto. Un&#39;attività di outreach ben programmata acquisisce i ricavi prima della scadenza delle garanzie di fabbrica. | Aumento del 20-30% dell&#39;adozione della garanzia estesa, maggiori ricavi dal servizio | [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [Attivazione funzionalità per auto collegate](#connected-car-feature-activation) | Personalizza le raccomandazioni sulle funzioni dell’auto collegata in base alle funzionalità del veicolo e alle preferenze tecnologiche. Aiutare i proprietari a scoprire le funzionalità inutilizzate aumenta la soddisfazione e rafforza la relazione digitale. | Aumento del 35-45% dei tassi di attivazione delle funzioni, migliore esperienza del cliente | [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [Coordinazione rete rivenditori](#dealer-network-coordination) | Abilita i consigli personalizzati dei dealer in base alla posizione del cliente, alle preferenze e all’inventario dei dealer. Mettere in contatto i clienti con i rivenditori giusti migliora l&#39;esperienza di acquisto e di servizio. | Aumento del 30-40% dei tassi di coinvolgimento dei dealer, migliore coordinamento delle vendite | [Web visitatore conosciuto/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

## Considerazioni tecniche per caso d’uso

### Personalizzazione percorso di acquisto veicolo

- I dati di inventario dei veicoli provenienti dai sistemi di gestione dei concessionari devono essere integrati e aggiornati frequentemente in modo che le raccomandazioni riflettano l’effettiva disponibilità presso i concessionari nelle vicinanze.
- Per identificare con precisione i segnali di intento di acquisto, è necessario acquisire il comportamento di ricerca dei clienti nel sito web, incluse le attività di configurazione del veicolo, l’utilizzo degli strumenti di confronto e i download delle brochure.
- I modelli di valutazione dei lead devono tenere conto sia del coinvolgimento online che dei segnali offline, come le visite dei dealer e le richieste telefoniche, per dare priorità ai potenziali clienti con le migliori intenzioni.
- I profili [!DNL Real-Time Customer Data Platform] devono unire le sessioni di ricerca Web anonime con le identità note dei clienti una volta che un potenziale cliente si registra o visita un rivenditore.

### Promemoria appuntamenti assistenza

- I dati relativi al chilometraggio e alla telematica dei veicoli provenienti dai sistemi di automobili collegati o dai registri dei servizi dei concessionari devono confluire nei profili dei clienti per attivare i promemoria agli intervalli di servizio corretti.
- I messaggi di promemoria devono includere collegamenti di pianificazione con un solo clic che precompilano le informazioni sul veicolo del cliente e articoli di assistenza consigliati per ridurre al minimo l’attrito per la prenotazione.
- I record della cronologia dei servizi devono essere integrati per evitare di consigliare i servizi completati di recente e per personalizzare il promemoria con gli elementi di manutenzione specifici in scadenza.
- La data e l&#39;ora del messaggio di [!DNL Journey Optimizer] devono tenere conto della capacità del servizio del dealer e delle ore di funzionamento per garantire che i clienti possano prenotare appuntamenti quando ricevono il promemoria.

### Campagne di permuta

- I dati di valutazione dei veicoli forniti da fornitori terzi devono essere integrati e aggiornati regolarmente per garantire che le stime delle permute condivise con i clienti siano accurate e competitive.
- I modelli del ciclo di vita della proprietà devono tenere conto di fattori quali le date di scadenza del leasing, le tempistiche di rimborso del prestito e la durata media della proprietà per segmento di veicolo, al fine di individuare la finestra di estensione ottimale.
- I messaggi di Campaign devono fare riferimento in modo dinamico al veicolo corrente del cliente e suggerire opzioni di aggiornamento specifiche in linea con le sue preferenze e il suo budget.
- [!DNL Experience Platform] segmenti devono escludere i clienti che hanno acquistato di recente un veicolo o che si trovano attualmente in una controversia relativa a un servizio attivo, per evitare un&#39;attività di outreach scaduta.

### Raccomandazioni su parti e accessori

- I dati del catalogo dei prodotti devono includere informazioni sulla compatibilità del veicolo in modo che i consigli mostrino solo parti e accessori che si adattano all&#39;anno, alla marca e al modello del veicolo specifico del cliente.
- I fattori stagionali e regionali dovrebbero influenzare le raccomandazioni; gli accessori invernali dovrebbero essere promossi nei climi più freddi, mentre gli aggiornamenti delle prestazioni potrebbero risuonare di più nelle regioni con comunità di appassionati attivi.
- Il comportamento di navigazione nelle pagine di parti e accessori deve essere acquisito e associato ai profili dei clienti per perfezionare i consigli in base al loro interesse.
- L&#39;implementazione del Web SDK [!DNL Experience Platform] deve acquisire i dati del numero di identificazione del veicolo dalle sessioni autenticate per garantire l&#39;accuratezza del filtro di compatibilità.

### Notifiche di ritiro del veicolo

- Le registrazioni del numero di identificazione del veicolo devono essere conservate accuratamente nei profili dei clienti in modo che le notifiche di richiamo raggiungano tutti i proprietari interessati e non vadano ai clienti non interessati.
- La messaggistica di richiamo deve essere conforme ai requisiti normativi per il contenuto delle notifiche di sicurezza, i tempi e la conferma della consegna in ogni mercato applicabile.
- La consegna multicanale (e-mail, messaggi di testo, notifiche push e posta fisica) deve essere utilizzata per massimizzare la portata, in quanto le comunicazioni critiche per la sicurezza richiedono una maggiore garanzia di consegna rispetto ai messaggi di marketing.
- [!DNL Journey Optimizer] deve tenere traccia dello stato della risposta di richiamo a livello individuale e inoltrare le comunicazioni di follow-up ai proprietari che non hanno pianificato il servizio entro un intervallo di tempo definito.

### Nuove campagne di lancio di modelli

- I segmenti di pubblico per le campagne di lancio devono considerare il modello di veicolo corrente, la durata della proprietà, i segnali di interesse del modello passati e la capacità demografica di identificare le prospettive a più alta propensione.
- Il contenuto di Launch deve essere personalizzato in modo da fare riferimento al veicolo corrente del cliente ed evidenziare miglioramenti o funzionalità specifici che rispondono alle sue probabili priorità.
- La tempistica delle campagne deve coordinarsi con le date di embargo e i programmi di lancio regionali per garantire che i clienti ricevano informazioni al momento giusto per il proprio mercato.
- L&#39;attivazione del pubblico [!DNL Real-Time Customer Data Platform] deve sincronizzare i segmenti di launch con le piattaforme pubblicitarie per il supporto coordinato di contenuti multimediali a pagamento, insieme all&#39;estensione del canale di proprietà.

### Offerte di finanziamento e assicurazione

- Le regole di idoneità per le offerte finanziarie devono essere configurate con attenzione per rispettare le normative sui prestiti, garantendo che le offerte presentate ai clienti siano quelle per le quali possono effettivamente qualificarsi.
- L’integrazione dei dati del profilo di credito richiede una gestione sicura e rigidi controlli di accesso, in quanto le informazioni finanziarie sono soggette a requisiti più severi in materia di privacy e regolamentazione.
- La presentazione dell&#39;offerta deve indicare chiaramente termini, tassi e condizioni in conformità con le normative finanziarie dei consumatori in ogni mercato applicabile.
- [!DNL Journey Optimizer] le regole decisionali dovrebbero tenere conto del prezzo del veicolo, dell&#39;acconto e delle preferenze di durata del prestito per classificare le offerte in base alla rilevanza anziché semplicemente in base al tasso.

### Pianificazione unità di prova

- I sistemi di inventario dei dealer devono essere integrati per confermare che il modello di veicolo e il ritaglio specifici a cui il cliente è interessato sono disponibili per il test drive presso il dealer consigliato.
- I consigli basati sulla posizione dei dealer devono tenere in considerazione l&#39;indirizzo del cliente, la valutazione dei dealer e la disponibilità attuale degli appuntamenti per suggerire l&#39;opzione più conveniente.
- I messaggi di conferma e promemoria relativi al test dell&#39;unità devono includere indicazioni stradali, informazioni di contatto del dealer e cosa aspettarsi, riducendo la percentuale di non-show.
- I dati comportamentali di [!DNL Experience Platform] dovrebbero identificare il momento ottimale per suggerire un&#39;unità di test, evitando un&#39;estensione prematura ai ricercatori in fase iniziale che non sono ancora pronti.

### Programmi fedeltà del proprietario

- I calcoli del livello fedeltà devono includere più dimensioni del coinvolgimento, tra cui visite di assistenza, acquisti di componenti, referenze e partecipazione a eventi, non solo la cronologia degli acquisti dei veicoli.
- I sistemi di erogazione dei premi presso i concessionari e i centri di assistenza devono essere integrati in modo che i benefici di fedeltà possano essere riscattati senza problemi al momento del servizio.
- Le comunicazioni dovrebbero adattarsi in base alla fase del ciclo di vita della proprietà, offrendo ai nuovi proprietari proposte di valore diverse nel primo anno rispetto ai proprietari a lungo termine che si avvicinano a un potenziale aggiornamento.
- La logica di percorso [!DNL Journey Optimizer] deve rilevare le modifiche dei livelli in tempo reale e attivare messaggi di congratulazioni o di ricoinvolgimento quando i clienti passano da un livello all&#39;altro.

### Garanzia e piani di assistenza estesi

- Le date di scadenza della garanzia e i dettagli della copertura devono essere monitorati con precisione nei profili dei clienti per attivare la sensibilizzazione al momento giusto, in genere 60-90 giorni prima della scadenza.
- Il chilometraggio e i modelli di utilizzo dei veicoli ricavati dai dati delle autovetture collegate o dalle registrazioni dei servizi dovrebbero informare le raccomandazioni del piano, in quanto i conducenti con chilometraggio elevato beneficiano di una copertura diversa rispetto ai proprietari con chilometraggio ridotto.
- Il contenuto del confronto dei piani deve essere chiaro e privo di gergo, in modo da aiutare i clienti a comprendere esattamente ciò che è coperto e il valore relativo ai potenziali costi di riparazione.
- [!DNL Real-Time Customer Data Platform] segmenti devono distinguere tra i clienti con garanzie di fabbrica in scadenza, quelli con piani estesi esistenti prossimi al rinnovo e quelli senza copertura corrente.

### Attivazione funzione auto collegata

- I dati della piattaforma dell’autovettura collegata devono essere integrati per identificare quali elementi sono disponibili su ciascun veicolo e quali sono già stati attivati o utilizzati dal proprietario.
- Il tracciamento dell’adozione delle funzioni deve acquisire eventi di attivazione, frequenza di utilizzo e profondità di coinvolgimento per personalizzare la sequenza e la velocità dei consigli sulle funzioni.
- I canali di notifica nel veicolo devono essere coordinati con le notifiche e-mail e nell’app per inviare messaggi nel momento più pertinente dal punto di vista contestuale, ad esempio per suggerire funzioni di navigazione quando viene rilevato un viaggio stradale.
- I profili di [!DNL Experience Platform] devono memorizzare i dati di configurazione della tecnologia del veicolo, inclusi i pacchetti installati e le versioni del software, per garantire che le funzionalità consigliate siano compatibili con il veicolo specifico del proprietario.

### Coordinamento della rete dei dealer

- Le informazioni sull&#39;inventario dei dealer devono essere integrate e aggiornate frequentemente per garantire che la disponibilità dei veicoli mostrata ai clienti rifletta accuratamente ciò che si trova sul lotto di ogni dealer.
- La logica di assegnazione cliente-dealer deve considerare la prossimità, la specializzazione del dealer, le preferenze linguistiche, e qualsiasi relazione esistente con il dealer per fornire la migliore corrispondenza.
- Le regole di instradamento dei lead devono garantire che, quando un cliente esprime interesse per l’acquisto online, l’interrogazione raggiunga rapidamente il rivenditore appropriato con il contesto completo dell’attività di ricerca del cliente.
- La risoluzione delle identità [!DNL Experience Platform] deve gestire gli scenari in cui un cliente interagisce con più concessionari, mantenendo un profilo unificato nel rispetto della visione di ogni concessionario sulle proprie relazioni con i clienti.
