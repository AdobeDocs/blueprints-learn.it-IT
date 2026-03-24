---
title: Healthcare Use Cases
description: Discover how healthcare organizations use Adobe Experience Platform to improve patient engagement, streamline care coordination, and drive better health outcomes.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: 8da82711-a783-488d-a0ed-070b33ecbbc4
source-git-commit: 0236bd326730ee9a0be621ee0e60ddc3d352410d
workflow-type: tm+mt
source-wordcount: '3818'
ht-degree: 0%

---

# Healthcare Use Cases

Healthcare organizations use Adobe Experience Platform to build unified patient profiles and deliver personalized, timely communications across every touchpoint. By connecting clinical, behavioral, and preference data in one place, care teams can engage patients more effectively while maintaining the highest standards of privacy and compliance.

>[!IMPORTANT]
>Healthcare use cases involve protected health information (PHI) subject to HIPAA and other applicable regulations. Before implementing any of these patterns, ensure that [!DNL Adobe Experience Platform] is provisioned as a HIPAA-eligible service and that a Business Associate Agreement (BAA) is in place with Adobe. The technical considerations in each section highlight key compliance requirements but are not exhaustive. Work with your legal, compliance, and security teams to validate your implementation against all applicable regulatory requirements.

## Appointment Reminder Automation

Send personalized appointment reminders through email, text message, and push notifications based on each patient&#39;s communication preferences and appointment type. Automated reminders reduce missed appointments and keep schedules running smoothly, freeing staff to focus on patient care.

### Impatto aziendale

Organizations that implement automated appointment reminders see measurable improvements in appointment show rates and a meaningful reduction in costly no-shows.

### Come implementare

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. Appointment creation and update events from the scheduling system serve as natural triggers for timely, relevant reminder messages. This is the right pattern when a discrete appointment event is the trigger and the required response is a single, time-sensitive notification — rather than a sustained engagement sequence, since patients need immediate confirmation without follow-up steps.

### Considerazioni tecniche

- Ensure all patient contact information and appointment details are transmitted and stored in compliance with HIPAA requirements, using appropriate data usage labels to restrict unauthorized access.
- Integrate with the electronic health records scheduling system to capture appointment creation, cancellation, and rescheduling events in real time.
- Apply consent management policies so that reminders are only sent through channels the patient has explicitly opted into.
- Configure suppression rules to prevent duplicate or excessive reminders when appointments are rescheduled in quick succession.


## Medication Adherence Campaigns

Send personalized reminders and educational content to help patients stay on track with their medication schedules and treatment plans. Tailored messaging based on medication type, dosing schedule, and patient history drives better adherence and improved health outcomes.

### Impatto aziendale

Le campagne personalizzate di aderenza ai farmaci aiutano a migliorare i tassi di aderenza, portando a migliori risultati in termini di salute e a un minor numero di riammissioni ospedaliere.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). L’aderenza al medicinale richiede un approccio prolungato e multi-touch con promemoria crescenti, punti di contatto educativi e check-in di follow-up nel corso di un piano di trattamento. Questo è lo schema giusto perché la gestione dei farmaci richiede un flusso sequenziale di messaggi multipli in giorni o settimane con ramificazioni condizionali basate su eventi di ricarica e segnali di coinvolgimento — un singolo messaggio attivato non può soddisfare la logica di dipendenza tra i passaggi educativi e i percorsi di escalation.

### Considerazioni tecniche

- Applica etichette di utilizzo dei dati rigorose a tutte le informazioni sanitarie protette relative ai dati di medicazione e diagnosi per prevenire l’attivazione a valle non autorizzata.
- Integrazione con i sistemi di cartelle cliniche elettroniche e farmaceutiche per ricevere i dati di riempimento e ricarica della prescrizione che attivano i passaggi di percorso.
- Implementa una solida gestione del consenso per garantire che i pazienti abbiano accettato di ricevere comunicazioni relative al medicinale e possano revocare il consenso in qualsiasi momento.
- Progetta la logica di percorso per rilevare i pattern di non coinvolgimento e passare alle notifiche del team di assistenza quando un paziente potrebbe essere a rischio di non aderenza.


## Promemoria Preventive Care

Ricorda in modo proattivo ai pazienti le cure preventive raccomandate, come vaccinazioni, screening e controlli annuali in base alla loro età, anamnesi e fattori di rischio. Promemoria tempestivi per l’assistenza preventiva aiutano a colmare le lacune nell’assistenza e a migliorare la salute generale della popolazione.

### Impatto aziendale

La sensibilizzazione proattiva all’assistenza preventiva si traduce in un miglioramento dei tassi di completamento dell’assistenza preventiva, contribuendo a migliorare la salute della popolazione e a ridurre i costi del trattamento a lungo termine.

### Come implementare

Utilizza il pattern [Attivazione messaggi in uscita in batch](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md). Il modo migliore per inviare promemoria di cure preventive consiste nel programmare campagne batch che valutino l’idoneità del paziente rispetto alle linee guida cliniche su una cadenza regolare. Questo è lo schema corretto quando il pubblico è predefinito da criteri di linee guida cliniche, la tempistica di consegna è pianificata su una frequenza regolare piuttosto che basata su eventi e non è richiesto alcun ramificazione o processo decisionale in tempo reale.

### Considerazioni tecniche

- Crea segmenti di pubblico utilizzando criteri di riferimento clinici (età, genere, anamnesi familiare, date di screening precedenti) mentre applichi etichette di utilizzo dei dati a tutte le informazioni sanitarie protette utilizzate nella segmentazione.
- Coordina con i team clinici per garantire che il contenuto del promemoria sia in linea con le linee guida di assistenza preventiva e i protocolli organizzativi attuali basati sulle evidenze.
- Implementare un limite di frequenza per evitare di sopraffare i pazienti che si qualificano per più raccomandazioni di cure preventive contemporaneamente.
- Mantenere una traccia di audit di tutte le comunicazioni di cure preventive inviate per i report normativi e la documentazione sulle misure di qualità.


## Campagne Di Follow-Up Post-Visita

Invia automaticamente sondaggi post-visita, istruzioni per l’assistenza e promemoria per gli appuntamenti di follow-up in base al tipo di visita e alle esigenze specifiche di ciascun paziente. Un follow-up tempestivo migliora la soddisfazione dei pazienti e garantisce la continuità delle cure dopo ogni incontro.

### Impatto aziendale

Le campagne automatizzate di follow-up post-visita consentono di migliorare i tassi di risposta al sondaggio e di ottenere punteggi più elevati di soddisfazione dei pazienti.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Gli eventi di completamento delle visite dal sistema di cartelle cliniche elettroniche forniscono un trigger naturale e tempestivo per le comunicazioni di follow-up su misura per il tipo di incontro. Questo è il modello corretto quando si verifica un evento di completamento di una visita discreta e la risposta richiesta è un follow-up immediato personalizzato in base al tipo di evento, anziché una sequenza in più fasi, in quanto ogni visita genera la propria necessità di follow-up indipendente.

### Considerazioni tecniche

- Integrare con il sistema di cartelle cliniche elettroniche per ricevere gli eventi di dimissione dalla visita che includono il tipo di visita, il fornitore e le istruzioni di assistenza pertinenti senza esporre note cliniche complete.
- Applica le etichette di utilizzo dei dati a qualsiasi contenuto di istruzioni per l’assistenza sanitaria per garantire che le informazioni sanitarie protette vengano condivise solo attraverso canali sicuri e autorizzati dal paziente.
- Configurare le regole di tempo che tengono conto del tipo di visita, ad esempio i follow-up post-chirurgici possono richiedere tempi diversi rispetto ai controlli di routine.
- Includere collegamenti sicuri al portale del paziente per il completamento del sondaggio e la pianificazione degli appuntamenti, anziché raccogliere informazioni sullo stato tramite canali non protetti.


## Programmi di gestione delle malattie croniche

Personalizzare comunicazioni sulla gestione della malattia cronica, contenuti educativi e promemoria di monitoraggio in base alla condizione specifica e al piano di trattamento di ciascun paziente. Un impegno costante e pertinente aiuta i pazienti a svolgere un ruolo attivo nella gestione della loro salute nel tempo.

### Impatto aziendale

I programmi personalizzati di gestione della malattia cronica vedono tassi di coinvolgimento del programma aumentati, che portano a migliori risultati nella gestione della malattia e a un utilizzo ridotto delle cure di emergenza.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). La gestione della malattia cronica è intrinsecamente un’esperienza a più punti di contatto di lunga durata che richiede messaggi adattivi basati sul coinvolgimento del paziente e sui suoi obiettivi di salute. Questo è il modello giusto perché la gestione della malattia cronica richiede una messaggistica adattativa per un periodo prolungato con diramazioni condizionali basate su metriche cliniche e modelli di coinvolgimento. La messaggistica attivata dagli eventi non può gestire la rivalutazione dinamica in corso necessaria per adeguare gli interventi in base all’evoluzione dei dati sanitari.

### Considerazioni tecniche

- Progettare una logica di diramazione del percorso che si adatta in base a metriche specifiche per la condizione (ad esempio, tendenze della glicemia per la gestione del diabete o letture della pressione arteriosa per i programmi di ipertensione).
- Implementa una rigida governance dei dati con [!DNL Adobe Experience Platform] etichette di utilizzo per classificare e proteggere i dati di integrità specifici della condizione in tutto il percorso.
- Integrazione con dispositivi di monitoraggio dei pazienti remoti e sistemi di valutazione dei risultati riferiti dai pazienti per alimentare i dati sanitari in tempo reale nei punti decisionali del percorso.
- Crea percorsi di escalation del team di assistenza all’interno del percorso in modo che il mancato coinvolgimento o le tendenze sanitarie attivino gli avvisi al personale clinico appropriato.


## Nuovo Percorso di onboarding per i pazienti

Automatizza un percorso di onboarding in più fasi per i nuovi pazienti, che include informazioni sull’accoglienza, istruzioni per l’accesso al portale del paziente e indicazioni sulla pianificazione degli appuntamenti. Un’esperienza di onboarding fluida imposta il tono di una relazione impegnativa e a lungo termine con il paziente.

### Impatto aziendale

I nuovi percorsi automatizzati di onboarding dei pazienti contribuiscono a migliorare i tassi di attivazione del portale e a rafforzare il coinvolgimento precoce dei pazienti.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). L’onboarding del paziente è un processo naturalmente sequenziale, in più fasi, in cui ogni comunicazione si basa sulla precedente e si adatta a seconda che il paziente abbia completato le azioni chiave. Questo è il modello corretto perché l’onboarding richiede un flusso sequenziale e dipendente su più giorni con ramificazioni basate sulle azioni del paziente (attivazione del portale, completamento del modulo). Un approccio batch o con un singolo messaggio non può adattarsi alle interdipendenze tra i passaggi né al completamento progressivo.

### Considerazioni tecniche

- Integrazione con il percorso di registrazione dei pazienti per attivare immediatamente il sistema di onboarding non appena viene creata una nuova cartella clinica, assicurando una prima impressione tempestiva.
- Utilizza la risoluzione delle identità per unire eventuali record preesistenti (ad esempio, da una visita al sito web o una richiesta di appuntamento) con il nuovo profilo del paziente, al fine di evitare comunicazioni duplicate.
- Verificare che i collegamenti e le credenziali di attivazione del portale vengano consegnati tramite canali sicuri e conformi a HIPAA e che scadano dopo un periodo definito.
- Progettare il percorso per rilevare gli eventi di attivazione del portale e di completamento del modulo in modo che i passaggi successivi si adattino anziché ripetere le informazioni su cui il paziente ha già agito.


## Consegna personalizzata di contenuti sanitari

Distribuisci contenuti personalizzati sull’educazione sanitaria, suggerimenti sul benessere e risorse personalizzate in base alle condizioni, agli interessi e agli obiettivi sanitari di ciascun paziente. I contenuti rilevanti creano fiducia, migliorano l’alfabetizzazione sanitaria e consentono ai pazienti di prendere decisioni informate in merito alle loro cure.

### Impatto aziendale

La distribuzione personalizzata di contenuti sanitari raggiunge tassi di coinvolgimento dei contenuti più elevati, con conseguente miglioramento dell’istruzione dei pazienti e dell’alfabetizzazione sanitaria.

### Come implementare

Utilizza il Percorso [cross-channel con modello Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md). La distribuzione dei contenuti sanitari beneficia di decisioni in tempo reale che selezionano i contenuti più rilevanti per ciascun paziente in base alle sue condizioni, preferenze e al suo impegno passato, attraverso il canale preferito. Questo è il modello corretto quando la selezione del contenuto deve tenere conto delle condizioni del paziente, delle preferenze di consenso e delle preferenze di canale, evitando al contempo la distribuzione duplicata o faticosa: l’orchestrazione in più passaggi non fornisce da sola il livello decisionale in tempo reale necessario per adattare l’inventario di contenuti dinamici alle esigenze del singolo paziente.

### Considerazioni tecniche

- Applica le etichette di classificazione dei contenuti e di utilizzo dei dati a tutti i materiali per l’educazione sanitaria per garantire che i contenuti specifici per la condizione vengano forniti solo ai pazienti che hanno acconsentito a ricevere informazioni sulla salute su tale argomento.
- Integra il motore decisionale con un archivio di contenuti regolarmente rivisto e approvato dai team clinici per garantire la precisione medica.
- Implementare regole di affaticamento dei contenuti per evitare di distribuire in eccesso i contenuti su un singolo argomento e per bilanciare il materiale educazionale tra le varie esigenze di salute di un paziente.
- Tieni traccia dei segnali di coinvolgimento dei contenuti (aperture, clic, tempo trascorso) per perfezionare continuamente la rilevanza dei contenuti senza raccogliere o archiviare informazioni sanitarie protette aggiuntive.


## Notifica risultati lab

Avvisa i pazienti quando i risultati del laboratorio sono disponibili attraverso il loro canale di comunicazione preferito con messaggi personalizzati e sicuri. La notifica tempestiva incoraggia i pazienti a rivedere rapidamente i risultati e a seguire il loro team di assistenza quando necessario.

### Impatto aziendale

Le notifiche automatizzate dei risultati di laboratorio consentono di aumentare i tassi di visualizzazione dei risultati, migliorando la comunicazione con il paziente e consentendo un più rapido follow-up clinico quando i risultati richiedono un intervento.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). La disponibilità dei risultati di laboratorio è un evento discreto che richiede una notifica singola immediata attraverso il canale preferito dal paziente. Questo è il modello corretto quando si attiva un evento di laboratorio discreto e la risposta richiesta è una singola notifica immediata, piuttosto che una sequenza multipla, poiché i pazienti hanno bisogno di un avviso tempestivo per controllare il loro portale senza ulteriori comunicazioni di follow-up.

### Considerazioni tecniche

- Non includere mai i valori effettivi dei risultati di laboratorio nei messaggi di notifica: solo informare il paziente che i risultati sono disponibili e indirizzarli al portale sicuro del paziente per i dettagli.
- È possibile integrarsi con il sistema di informazioni di laboratorio per ricevere eventi pronti per i risultati applicando rigide etichette di utilizzo dei dati, al fine di evitare che eventuali dati clinici fluiscano nei canali di marketing.
- Implementa la logica di conservazione del provider in modo che le notifiche vengano inviate solo dopo che il medico ordinante ha rivisto e rilasciato i risultati per la visualizzazione del paziente.
- Verificare che tutti i collegamenti di notifica puntino a sessioni del portale dei pazienti autenticate e crittografate che soddisfino i requisiti di sicurezza HIPAA.


## Verifica copertura assicurativa

Verifica e comunicazione proattiva delle informazioni sulla copertura assicurativa ai pazienti prima degli appuntamenti per ridurre le sorprese di fatturazione e migliorare l’esperienza complessiva del paziente. Una comunicazione di copertura chiara e anticipata crea fiducia e riduce le controversie di fatturazione post-visita.

### Impatto aziendale

La verifica proattiva della copertura assicurativa si traduce in un miglioramento dei tassi di conferma della copertura prima della visita e in una riduzione significativa delle controversie sulla fatturazione e dei reclami dei pazienti.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Gli eventi di pianificazione degli appuntamenti fungono da trigger per avviare la verifica della copertura e comunicare i risultati al paziente prima della visita. Questo è il modello corretto quando si attiva un evento di pianificazione degli appuntamenti discreto e la risposta richiesta è un&#39;unica notifica sensibile al tempo relativa alla copertura, anziché una sequenza di coinvolgimento in più fasi, in quanto il paziente ha bisogno di un messaggio chiaro prima dell&#39;appuntamento.

### Considerazioni tecniche

- Integrare con i sistemi di verifica dell&#39;idoneità all&#39;assicurazione per recuperare lo stato di copertura in tempo reale senza memorizzare i dati completi sulle richieste di risarcimento nella piattaforma dati cliente.
- Applica etichette di utilizzo dati a tutte le informazioni finanziarie e assicurative per limitarne l’utilizzo alle sole comunicazioni relative alla fatturazione.
- Configurare la tempistica dei messaggi in modo da consentire un lead time sufficiente prima dell&#39;appuntamento per consentire ai pazienti di risolvere eventuali problemi di copertura o contattare il proprio fornitore di assicurazioni.
- Includi istruzioni chiare e informazioni di contatto per il reparto fatturazione in modo che i pazienti possano porre domande o fornire dettagli assicurativi aggiornati prima della visita.


## Promemoria Appuntamenti Telehealth

Inviare promemoria personalizzati per gli appuntamenti di telesanità che includono istruzioni di connessione, suggerimenti per la preparazione e informazioni sul supporto tecnico. Gli efficaci promemoria per la telesanità riducono le visite virtuali mancate e aiutano i pazienti a sentirsi sicuri utilizzando gli strumenti di assistenza digitale.

### Impatto aziendale

I promemoria personalizzati per appuntamenti di telesanità aiutano a migliorare le percentuali di visite virtuali e ad accelerare l&#39;adozione complessiva della telesanità nella popolazione di pazienti.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Gli eventi di pianificazione degli appuntamenti di Telehealth forniscono un trigger naturale per i promemoria tempestivi che includono dettagli di connessione e indicazioni sulla preparazione. Questo è lo schema corretto quando un evento di appuntamento di telesanità discreto è l&#39;evento scatenante e la risposta richiesta è un singolo promemoria immediato con linee guida tecniche — piuttosto che una sequenza in più fasi, dal momento che i pazienti hanno bisogno di istruzioni chiare prima dell&#39;appuntamento senza successivi messaggi di follow-up.

### Considerazioni tecniche

- Includere istruzioni di connessione specifiche della piattaforma (desktop o mobile) in base alle preferenze note del dispositivo del paziente o ai dati delle sessioni di telesanità passate.
- Assicurarsi che tutti i collegamenti di connessione e gli identificatori di sessione di telesanità vengano consegnati tramite canali crittografati conformi HIPAA e che scadano dopo l&#39;intervallo di appuntamenti pianificato.
- Integrazione con la piattaforma di telesanità per rilevare quando un paziente si è connesso correttamente in modo che i messaggi di promemoria secondari possano essere eliminati.
- Fornire un percorso di fallback alle informazioni di contatto del supporto tecnico per i pazienti che non sono connessi entro una finestra definita prima dell’ora di inizio dell’appuntamento.


## Programma di benessere

Personalizza comunicazioni, sfide e premi del programma di benessere in base agli obiettivi di salute, al livello di attività e alle preferenze di ciascun paziente. Coinvolgere programmi di benessere motivano i pazienti ad adottare abitudini più sane e mantenere il benessere a lungo termine.

### Impatto aziendale

Le campagne di coinvolgimento personalizzate nel programma di benessere ottengono tassi di partecipazione al programma più elevati, contribuendo a migliorare i risultati sanitari e a rafforzare la fedeltà dei pazienti.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). I programmi di benessere sono esperienze di coinvolgimento sostenuto con più tappe fondamentali, sfide e punti di contatto di ricompensa che richiedono un’orchestrazione adattiva basata sulla partecipazione e sul progresso dei pazienti. Questo è il modello giusto perché i programmi per il benessere richiedono un flusso sequenziale di più messaggi per un periodo di tempo prolungato con ramificazioni condizionali basate su milestone di partecipazione e pattern di coinvolgimento: i messaggi attivati da eventi non possono gestire l’orchestrazione adattiva e sostenuta necessaria per regolare le sfide e i premi in base al monitoraggio dei progressi in corso.

### Considerazioni tecniche

- Integra con dispositivi indossabili e feed di dati di applicazioni fitness applicando etichette chiare di utilizzo dei dati per distinguere i dati di salute dai dati clinici soggetti a requisiti normativi più severi.
- Implementa la gestione del consenso che consente ai pazienti di concedere e revocare l’autorizzazione per la raccolta di dati sul benessere indipendentemente dalle loro preferenze di comunicazione clinica.
- Progettare la logica di percorso che regola la difficoltà di sfida e la frequenza di comunicazione in base ai modelli di coinvolgimento di ogni paziente per evitare scoraggiamento o affaticamento.
- Assicurati che il monitoraggio dei premi e degli incentivi sia conforme alle normative sanitarie applicabili in materia di incentivi per i pazienti e ai requisiti anti-kickback.


## Coordinamento team di assistenza

Consentire la comunicazione e il coordinamento personalizzati tra i pazienti e i membri del loro team di assistenza in base al piano di assistenza e alle preferenze individuali. Un migliore coordinamento porta a transizioni di assistenza più fluide e a risultati migliori per i pazienti con esigenze di assistenza complesse.

### Impatto aziendale

Comunicazioni efficaci di coordinamento del team di assistenza si traducono in un coinvolgimento del team di assistenza migliorato e in risultati migliori di coordinamento dell’assistenza attraverso piani di assistenza multi-provider.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Il coordinamento del team di assistenza coinvolge più parti interessate e flussi di comunicazione continui che devono adattarsi in base alle fasi cardine del piano di assistenza, ai cambiamenti dello stato del paziente e alle azioni del provider. Questo è il modello giusto perché il coordinamento delle cure richiede flussi di messaggistica adattativi e in più fasi che si diramano in base alle fasi cardine del piano di assistenza e alle azioni del fornitore tra più parti interessate. Un messaggio singolo o un modello più semplice non può soddisfare le complesse interdipendenze e il routing dei messaggi basato sui ruoli necessari tra i team clinici.

### Considerazioni tecniche

- Implementare controlli dell’accesso basati sui ruoli e etichette di utilizzo dei dati per garantire che ogni membro dell’équipe di assistenza riceva solo le informazioni relative al paziente in base al suo ruolo nel piano di assistenza.
- Integrazione con i sistemi di gestione dell’assistenza e delle cartelle cliniche elettroniche per ricevere aggiornamenti del piano di assistenza, completamenti delle segnalazioni ed eventi di transizione dell’assistenza che attivano i messaggi di coordinazione.
- Progettare percorsi di comunicazione separati per i messaggi rivolti ai pazienti e ai fornitori, garantendo che la terminologia clinica sia utilizzata in modo appropriato per i fornitori, mentre i messaggi dei pazienti rimangano chiari e accessibili.
- Mantenere una pista di controllo completa di tutte le comunicazioni di coordinamento dell&#39;assistenza per garantire la conformità alle normative sulla continuità dell&#39;assistenza e ai requisiti di accreditamento.


## Analisi della Funnel del Percorso di pazienti e della carenza di assistenza

Mappatura del percorso di pazienti end-to-end dalla ricerca web iniziale fino alla pianificazione degli appuntamenti, alla somministrazione delle cure e al follow-up per identificare dove i pazienti si disimpegnano e quali popolazioni presentano lacune nelle cure preventive o croniche raccomandate. I percorsi sanitari che non hanno visibilità cross-channel non sono in grado di distinguere tra attrito programmato e disimpegno dei pazienti, limitando la loro capacità di migliorare l&#39;accesso e colmare le lacune nelle cure su larga scala.

### Impatto aziendale

Capire dove i pazienti abbandonano i percorsi di assistenza e quali segmenti di membri hanno la più alta concentrazione di lacune di assistenza consente ai team di gestione dell’assistenza e di marketing di concentrare le risorse di sensibilizzazione sulle popolazioni e sui punti di attrito che produrranno il massimo miglioramento nell’aderenza alle cure.

### Come implementare

Utilizza il pattern [Customer Analytics &amp; Insight Generation](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md). Questo approccio collega i dati comportamentali del web e del portale, i record del sistema di appuntamenti e i dati delle richieste di assistenza a Customer Journey Analytics, dove l’analisi dell’abbandono misura l’abbandono in ogni fase di pianificazione o assistenza e l’analisi di coorte identifica quali segmenti membri hanno i tassi di aderenza all’assistenza più bassi. Questo è il modello corretto quando l’obiettivo è la generazione di insight e l’analisi a livello di popolazione, per capire dove i percorsi si suddividono e chi è più a rischio, invece di attivare un’attività di sensibilizzazione o un elenco di soppressione.

### Considerazioni tecniche

- I dati di appuntamenti e attestazioni provenienti da sistemi clinici devono essere mappati su schemi XDM conformi a HIPAA prima dell’acquisizione in AEP e le etichette di utilizzo dei dati devono essere applicate per limitare l’accesso alle informazioni protette sull’integrità nelle visualizzazioni dati di CJA.
- Gli identificatori del paziente o del membro attraverso il portale web, il sistema di pianificazione e l’EHR devono essere risolti in un ID persona coerente nella connessione CJA per produrre una visualizzazione coerente del percorso tra sistemi senza duplicare gli individui.
- L’analisi del gap di assistenza richiede set di dati di ricerca che codifichino le definizioni delle linee guida cliniche, ad esempio gli intervalli di screening consigliati per età e condizione, in modo che i campi derivati da CJA possano segnalare ai membri che non hanno completato l’assistenza consigliata entro la finestra delle linee guida.
- La pianificazione dell’analisi di funnel deve acquisire sia le sessioni di pianificazione completate che quelle abbandonate, inclusi i punti di uscita nei flussi di pianificazione in più fasi, in modo che i punti di attrito siano visibili a livello di fase anziché come tassi di abbandono aggregati.


## Personalization dei contenuti del portale per i pazienti

Personalizza l’esperienza del portale del paziente autenticato presentando i contenuti, gli strumenti e le risorse sanitari più rilevanti in base al comportamento di navigazione e alla cronologia del coinvolgimento di ciascun paziente durante la sessione. Un portale che si adatta a ciò che un paziente sta attivamente ricercando, piuttosto che presentare la stessa esperienza statica a ogni visitatore, semplifica per i pazienti la ricerca di ciò di cui hanno bisogno e incoraggia un coinvolgimento più profondo con le risorse sanitarie disponibili.

### Impatto aziendale

La personalizzazione dell’esperienza del portale dei pazienti basata sul comportamento di coinvolgimento determina tassi migliorati di individuazione dei contenuti e completamento self-service, aiutando i pazienti a navigare nella propria assistenza in modo più sicuro senza richiedere l’intervento del team di assistenza.

### Come implementare

Utilizza il pattern [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). I segnali comportamentali durante le sessioni provenienti dal portale autenticato, inclusi le visualizzazioni di pagina dei contenuti, l&#39;utilizzo degli strumenti sanitari, il coinvolgimento nell&#39;argomento delle domande frequenti e l&#39;attività di pianificazione degli appuntamenti, consentono di formare un modello di consigli che riunisce le risorse più rilevanti per ogni paziente in base a ciò che sta attivamente esaminando, senza richiedere dati clinici come input. Questo è il modello corretto quando la personalizzazione è guidata da segnali comportamentali impliciti all’interno di una sessione autenticata e l’obiettivo è la classificazione di rilevanza di un catalogo di contenuti e risorse, anziché decisioni di idoneità governate, che è più appropriato quando i criteri clinici devono tenere conto di ciò che vede un paziente.

### Considerazioni tecniche

- Limita i segnali comportamentali utilizzati per i consigli sui dati di interazione del portale (visualizzazioni di contenuto, utilizzo dello strumento e modelli di navigazione) e implementa le etichette di utilizzo dei dati che impediscono il flusso degli interessi sanitari dedotti al di fuori della sessione del portale autenticato o nei canali di marketing.
- Implementa una libreria di contenuti esaminati clinicamente come pool di consigli, in modo che il modello possa presentare solo materiali per l’educazione sanitaria preapprovati, garantendo che ogni risorsa consigliata sia stata convalidata per l’accuratezza prima della distribuzione.
- Garantire che il sistema di raccomandazioni soddisfi i requisiti tecnici HIPAA per l’ambiente portale autenticato, inclusi i controlli di timeout della sessione e la registrazione di audit dei contenuti presentati a ciascun paziente e quando.
- Fornisci ai pazienti controlli visibili per cancellare la cronologia di navigazione del portale e rinunciare alla personalizzazione comportamentale, mantenendo la trasparenza e la fiducia nel modo in cui i dati del coinvolgimento vengono utilizzati nell’esperienza del portale.

## Promemoria sul coinvolgimento dei pazienti e sugli appuntamenti

Inviare promemoria di appuntamenti personalizzati, suggerimenti per l’integrità e comunicazioni di follow-up con percorsi multicanale conformi e in grado di riconoscere il consenso. I promemoria di appuntamento personalizzati e automatizzati riducono il tasso di mancata visualizzazione, garantendo al contempo la conformità delle comunicazioni alle normative sulla privacy sanitaria e alle preferenze di consenso del paziente.

### Impatto aziendale

Le organizzazioni sanitarie con programmi automatizzati di promemoria degli appuntamenti vedono riduzioni significative dei tassi di mancata presentazione e di cancellazione tardiva, migliorando l’utilizzo della pianificazione da parte del provider e i risultati relativi allo stato di salute dei pazienti attraverso una migliore adesione agli appuntamenti.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) per rispondere agli eventi di pianificazione degli appuntamenti con promemoria personalizzati e tempestivi programmati a intervalli ottimali prima della data dell&#39;appuntamento. Questo è lo schema giusto quando la comunicazione viene attivata da uno specifico evento di interazione del paziente e la risposta è un messaggio personalizzato, sensibile al tempo — piuttosto che una sequenza di nutrizione di più settimane o una selezione di offerte complesse.

### Considerazioni tecniche

- Tutte le comunicazioni con il paziente devono rispettare le normative vigenti sulla privacy dell&#39;assistenza sanitaria; il contenuto della messaggistica deve evitare di includere informazioni sulla salute protette oltre a quanto strettamente necessario per la comunicazione.
- La gestione del consenso deve essere applicata a livello di canale — i pazienti che non hanno optato per i promemoria SMS non devono ricevere messaggi, anche quando gli SMS sarebbero il canale di promemoria più efficace per la loro popolazione.
- L&#39;integrazione con il sistema di pianificazione deve consentire la consegna degli eventi dell&#39;appuntamento in tempo reale per consentire una pianificazione dei promemoria accurata rispetto alla pianificazione effettiva dell&#39;appuntamento, incluse le riprogrammazioni e le cancellazioni dello stesso giorno.
- Le sequenze di promemoria multicanale devono includere una logica di soppressione in modo che i pazienti che confermano l’appuntamento non continuino a ricevere messaggi di promemoria per quell’appuntamento.
