---
title: Casi di utilizzo del settore sanitario
description: Scopri come le organizzazioni sanitarie utilizzano Adobe Experience Platform per migliorare il coinvolgimento dei pazienti, semplificare il coordinamento delle cure e ottenere risultati migliori.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2356'
ht-degree: 1%

---


# Casi di utilizzo del settore sanitario

Le organizzazioni sanitarie utilizzano Adobe Experience Platform per creare profili unificati dei pazienti e fornire comunicazioni personalizzate e tempestive in ogni punto di contatto. Collegando i dati clinici, comportamentali e sulle preferenze in un’unica posizione, i team di assistenza possono coinvolgere i pazienti in modo più efficace, mantenendo al contempo gli standard più elevati di privacy e conformità.

## Automazione promemoria appuntamento

Inviare promemoria personalizzati per gli appuntamenti tramite e-mail, SMS e notifiche push in base alle preferenze di comunicazione e al tipo di appuntamento di ciascun paziente. I promemoria automatici riducono gli appuntamenti mancati e consentono di mantenere i programmi in esecuzione senza problemi, consentendo al personale di concentrarsi sulla cura dei pazienti.

### Impatto aziendale

Le organizzazioni che implementano promemoria automatizzati per gli appuntamenti in genere ottengono un miglioramento del 30-40% nelle percentuali di visualizzazione degli appuntamenti e una riduzione significativa dei costosi no-show.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Gli eventi di creazione e aggiornamento degli appuntamenti dal sistema di pianificazione fungono da trigger naturali per messaggi di promemoria pertinenti e tempestivi.

### Considerazioni tecniche

- Assicurarsi che tutte le informazioni di contatto del paziente e i dettagli degli appuntamenti siano trasmessi e memorizzati in conformità con i requisiti HIPAA, utilizzando etichette di utilizzo dei dati appropriate per limitare l’accesso non autorizzato.
- Integrazione con il sistema di pianificazione delle cartelle cliniche elettroniche per acquisire in tempo reale gli eventi di creazione, annullamento e riprogrammazione degli appuntamenti.
- Applica i criteri di gestione del consenso in modo che i promemoria vengano inviati solo tramite i canali in cui il paziente ha esplicitamente acconsentito.
- Configurare le regole di soppressione per evitare promemoria duplicati o eccessivi quando gli appuntamenti vengono ripianificati in rapida successione.


## Campagne di aderenza ai medicinali

Inviare promemoria personalizzati e contenuti educativi per aiutare i pazienti a mantenere la rotta con i loro programmi di trattamento e terapie. Messaggi personalizzati basati sul tipo di farmaco, sulla posologia e sull’anamnesi dei pazienti favoriscono una migliore aderenza e migliori risultati in termini di salute.

### Impatto aziendale

Le campagne personalizzate di aderenza ai farmaci in genere portano a un miglioramento del 20-30% nei tassi di aderenza, portando a risultati di salute misurabilmente migliori e meno riammissioni ospedaliere.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). L’aderenza al medicinale richiede un approccio prolungato e multi-touch con promemoria crescenti, punti di contatto educativi e check-in di follow-up nel corso di un piano di trattamento.

### Considerazioni tecniche

- Applica etichette di utilizzo dei dati rigorose a tutte le informazioni sanitarie protette relative ai dati di medicazione e diagnosi per prevenire l’attivazione a valle non autorizzata.
- Integrazione con i sistemi di cartelle cliniche elettroniche e farmaceutiche per ricevere i dati di riempimento e ricarica della prescrizione che attivano i passaggi di percorso.
- Implementa una solida gestione del consenso per garantire che i pazienti abbiano accettato di ricevere comunicazioni relative al medicinale e possano revocare il consenso in qualsiasi momento.
- Progetta la logica di percorso per rilevare i pattern di non coinvolgimento e passare alle notifiche del team di assistenza quando un paziente potrebbe essere a rischio di non aderenza.


## Promemoria Preventive Care

Ricorda in modo proattivo ai pazienti le cure preventive raccomandate, come vaccinazioni, screening e controlli annuali in base alla loro età, anamnesi e fattori di rischio. Promemoria tempestivi per l’assistenza preventiva aiutano a colmare le lacune nell’assistenza e a migliorare la salute generale della popolazione.

### Impatto aziendale

L&#39;estensione proattiva dell&#39;assistenza preventiva comporta in genere un aumento del 25-35% dei tassi di completamento dell&#39;assistenza preventiva, contribuendo a migliorare la salute della popolazione e a ridurre i costi del trattamento a lungo termine.

### Come implementare

Utilizza il pattern [Attivazione messaggi in uscita in batch](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md). Il modo migliore per inviare promemoria di cure preventive consiste nel programmare campagne batch che valutino l’idoneità del paziente rispetto alle linee guida cliniche su una cadenza regolare.

### Considerazioni tecniche

- Crea segmenti di pubblico utilizzando criteri di riferimento clinici (età, genere, anamnesi familiare, date di screening precedenti) mentre applichi etichette di utilizzo dei dati a tutte le informazioni sanitarie protette utilizzate nella segmentazione.
- Coordina con i team clinici per garantire che il contenuto del promemoria sia in linea con le linee guida di assistenza preventiva e i protocolli organizzativi attuali basati sulle evidenze.
- Implementare un limite di frequenza per evitare di sopraffare i pazienti che si qualificano per più raccomandazioni di cure preventive contemporaneamente.
- Mantenere una traccia di audit di tutte le comunicazioni di cure preventive inviate per i report normativi e la documentazione sulle misure di qualità.


## Campagne Di Follow-Up Post-Visita

Invia automaticamente sondaggi post-visita, istruzioni per l’assistenza e promemoria per gli appuntamenti di follow-up in base al tipo di visita e alle esigenze specifiche di ciascun paziente. Un follow-up tempestivo migliora la soddisfazione dei pazienti e garantisce la continuità delle cure dopo ogni incontro.

### Impatto aziendale

Le campagne automatizzate di follow-up post-visita in genere raggiungono un miglioramento del 40-50% nelle percentuali di risposta al sondaggio e punteggi di soddisfazione dei pazienti misurabilmente più elevati.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Gli eventi di completamento delle visite dal sistema di cartelle cliniche elettroniche forniscono un trigger naturale e tempestivo per le comunicazioni di follow-up su misura per il tipo di incontro.

### Considerazioni tecniche

- Integrare con il sistema di cartelle cliniche elettroniche per ricevere gli eventi di dimissione dalla visita che includono il tipo di visita, il fornitore e le istruzioni di assistenza pertinenti senza esporre note cliniche complete.
- Applica le etichette di utilizzo dei dati a qualsiasi contenuto di istruzioni per l’assistenza sanitaria per garantire che le informazioni sanitarie protette vengano condivise solo attraverso canali sicuri e autorizzati dal paziente.
- Configurare le regole di tempo che tengono conto del tipo di visita, ad esempio i follow-up post-chirurgici possono richiedere tempi diversi rispetto ai controlli di routine.
- Includere collegamenti sicuri al portale del paziente per il completamento del sondaggio e la pianificazione degli appuntamenti, anziché raccogliere informazioni sullo stato tramite canali non protetti.


## Programmi di gestione delle malattie croniche

Personalizzare comunicazioni sulla gestione della malattia cronica, contenuti educativi e promemoria di monitoraggio in base alla condizione specifica e al piano di trattamento di ciascun paziente. Un impegno costante e pertinente aiuta i pazienti a svolgere un ruolo attivo nella gestione della loro salute nel tempo.

### Impatto aziendale

I programmi personalizzati di gestione delle malattie croniche in genere vedono un aumento del 30-40% nei tassi di coinvolgimento del programma, che porta a migliori risultati nella gestione delle malattie e a una riduzione dell&#39;utilizzo delle cure di emergenza.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). La gestione della malattia cronica è intrinsecamente un’esperienza a più punti di contatto di lunga durata che richiede messaggi adattivi basati sul coinvolgimento del paziente e sui suoi obiettivi di salute.

### Considerazioni tecniche

- Progettare una logica di diramazione del percorso che si adatta in base a metriche specifiche per la condizione (ad esempio, tendenze della glicemia per la gestione del diabete o letture della pressione arteriosa per i programmi di ipertensione).
- Implementa una rigida governance dei dati con [!DNL Adobe Experience Platform] etichette di utilizzo per classificare e proteggere i dati di integrità specifici della condizione in tutto il percorso.
- Integrazione con dispositivi di monitoraggio dei pazienti remoti e sistemi di valutazione dei risultati riferiti dai pazienti per alimentare i dati sanitari in tempo reale nei punti decisionali del percorso.
- Crea percorsi di escalation del team di assistenza all’interno del percorso in modo che il mancato coinvolgimento o le tendenze sanitarie attivino gli avvisi al personale clinico appropriato.


## Nuovo Percorso di onboarding per i pazienti

Automatizza un percorso di onboarding in più fasi per i nuovi pazienti, che include informazioni sull’accoglienza, istruzioni per l’accesso al portale del paziente e indicazioni sulla pianificazione degli appuntamenti. Un’esperienza di onboarding fluida imposta il tono di una relazione impegnativa e a lungo termine con il paziente.

### Impatto aziendale

I nuovi percorsi automatizzati di onboarding dei pazienti determinano in genere un miglioramento del 50-60% nei tassi di attivazione del portale e un coinvolgimento precoce dei pazienti notevolmente più elevato.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). L’onboarding del paziente è un processo naturalmente sequenziale, in più fasi, in cui ogni comunicazione si basa sulla precedente e si adatta a seconda che il paziente abbia completato le azioni chiave.

### Considerazioni tecniche

- Integrazione con il percorso di registrazione dei pazienti per attivare immediatamente il sistema di onboarding non appena viene creata una nuova cartella clinica, assicurando una prima impressione tempestiva.
- Utilizza la risoluzione delle identità per unire eventuali record preesistenti (ad esempio, da una visita al sito web o una richiesta di appuntamento) con il nuovo profilo del paziente, al fine di evitare comunicazioni duplicate.
- Verificare che i collegamenti e le credenziali di attivazione del portale vengano consegnati tramite canali sicuri e conformi a HIPAA e che scadano dopo un periodo definito.
- Progettare il percorso per rilevare gli eventi di attivazione del portale e di completamento del modulo in modo che i passaggi successivi si adattino anziché ripetere le informazioni su cui il paziente ha già agito.


## Consegna personalizzata di contenuti sanitari

Distribuisci contenuti personalizzati sull’educazione sanitaria, suggerimenti sul benessere e risorse personalizzate in base alle condizioni, agli interessi e agli obiettivi sanitari di ciascun paziente. I contenuti rilevanti creano fiducia, migliorano l’alfabetizzazione sanitaria e consentono ai pazienti di prendere decisioni informate in merito alle loro cure.

### Impatto aziendale

La distribuzione personalizzata di contenuti sanitari in genere raggiunge un aumento del 35-45% nei tassi di coinvolgimento dei contenuti, portando a un miglioramento misurabile dell’istruzione dei pazienti e dell’alfabetizzazione sanitaria.

### Come implementare

Utilizza il Percorso [cross-channel con modello Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md). La distribuzione dei contenuti sanitari beneficia di decisioni in tempo reale che selezionano i contenuti più rilevanti per ciascun paziente in base alle sue condizioni, preferenze e al suo impegno passato, attraverso il canale preferito.

### Considerazioni tecniche

- Applica le etichette di classificazione dei contenuti e di utilizzo dei dati a tutti i materiali per l’educazione sanitaria per garantire che i contenuti specifici per la condizione vengano forniti solo ai pazienti che hanno acconsentito a ricevere informazioni sulla salute su tale argomento.
- Integra il motore decisionale con un archivio di contenuti regolarmente rivisto e approvato dai team clinici per garantire la precisione medica.
- Implementare regole di affaticamento dei contenuti per evitare di distribuire in eccesso i contenuti su un singolo argomento e per bilanciare il materiale educazionale tra le varie esigenze di salute di un paziente.
- Tieni traccia dei segnali di coinvolgimento dei contenuti (aperture, clic, tempo trascorso) per perfezionare continuamente la rilevanza dei contenuti senza raccogliere o archiviare informazioni sanitarie protette aggiuntive.


## Notifica risultati lab

Avvisa i pazienti quando i risultati del laboratorio sono disponibili attraverso il loro canale di comunicazione preferito con messaggi personalizzati e sicuri. La notifica tempestiva incoraggia i pazienti a rivedere rapidamente i risultati e a seguire il loro team di assistenza quando necessario.

### Impatto aziendale

Le notifiche automatizzate dei risultati di laboratorio determinano in genere un aumento del 60-70% nelle percentuali di visualizzazione dei risultati, migliorando la comunicazione con il paziente e consentendo un follow-up clinico più rapido quando i risultati richiedono un intervento.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). La disponibilità dei risultati di laboratorio è un evento discreto che richiede una notifica singola immediata attraverso il canale preferito dal paziente.

### Considerazioni tecniche

- Non includere mai i valori effettivi dei risultati di laboratorio nei messaggi di notifica: solo informare il paziente che i risultati sono disponibili e indirizzarli al portale sicuro del paziente per i dettagli.
- È possibile integrarsi con il sistema di informazioni di laboratorio per ricevere eventi pronti per i risultati applicando rigide etichette di utilizzo dei dati, al fine di evitare che eventuali dati clinici fluiscano nei canali di marketing.
- Implementa la logica di conservazione del provider in modo che le notifiche vengano inviate solo dopo che il medico ordinante ha rivisto e rilasciato i risultati per la visualizzazione del paziente.
- Verificare che tutti i collegamenti di notifica puntino a sessioni del portale dei pazienti autenticate e crittografate che soddisfino i requisiti di sicurezza HIPAA.


## Verifica copertura assicurativa

Verifica e comunicazione proattiva delle informazioni sulla copertura assicurativa ai pazienti prima degli appuntamenti per ridurre le sorprese di fatturazione e migliorare l’esperienza complessiva del paziente. Una comunicazione di copertura chiara e anticipata crea fiducia e riduce le controversie di fatturazione post-visita.

### Impatto aziendale

La verifica proattiva della copertura assicurativa comporta in genere un miglioramento del 25-35% dei tassi di conferma della copertura pre-visita e una riduzione significativa delle controversie di fatturazione e dei reclami dei pazienti.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Gli eventi di pianificazione degli appuntamenti fungono da trigger per avviare la verifica della copertura e comunicare i risultati al paziente prima della visita.

### Considerazioni tecniche

- Integrare con i sistemi di verifica dell&#39;idoneità all&#39;assicurazione per recuperare lo stato di copertura in tempo reale senza memorizzare i dati completi sulle richieste di risarcimento nella piattaforma dati cliente.
- Applica etichette di utilizzo dati a tutte le informazioni finanziarie e assicurative per limitarne l’utilizzo alle sole comunicazioni relative alla fatturazione.
- Configurare la tempistica dei messaggi in modo da consentire un lead time sufficiente prima dell&#39;appuntamento per consentire ai pazienti di risolvere eventuali problemi di copertura o contattare il proprio fornitore di assicurazioni.
- Includi istruzioni chiare e informazioni di contatto per il reparto fatturazione in modo che i pazienti possano porre domande o fornire dettagli assicurativi aggiornati prima della visita.


## Promemoria Appuntamenti Telehealth

Inviare promemoria personalizzati per gli appuntamenti di telesanità che includono istruzioni di connessione, suggerimenti per la preparazione e informazioni sul supporto tecnico. Gli efficaci promemoria per la telesanità riducono le visite virtuali mancate e aiutano i pazienti a sentirsi sicuri utilizzando gli strumenti di assistenza digitale.

### Impatto aziendale

I promemoria personalizzati per appuntamenti di telesanità determinano in genere un miglioramento del 40-50% nelle visite virtuali e accelerano l&#39;adozione complessiva della telesanità in tutta la popolazione di pazienti.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Gli eventi di pianificazione degli appuntamenti di Telehealth forniscono un trigger naturale per i promemoria tempestivi che includono dettagli di connessione e indicazioni sulla preparazione.

### Considerazioni tecniche

- Includere istruzioni di connessione specifiche della piattaforma (desktop o mobile) in base alle preferenze note del dispositivo del paziente o ai dati delle sessioni di telesanità passate.
- Assicurarsi che tutti i collegamenti di connessione e gli identificatori di sessione di telesanità vengano consegnati tramite canali crittografati conformi HIPAA e che scadano dopo l&#39;intervallo di appuntamenti pianificato.
- Integrazione con la piattaforma di telesanità per rilevare quando un paziente si è connesso correttamente in modo che i messaggi di promemoria secondari possano essere eliminati.
- Fornire un percorso di fallback alle informazioni di contatto del supporto tecnico per i pazienti che non sono connessi entro una finestra definita prima dell’ora di inizio dell’appuntamento.


## Programma di benessere

Personalizza comunicazioni, sfide e premi del programma di benessere in base agli obiettivi di salute, al livello di attività e alle preferenze di ciascun paziente. Coinvolgere programmi di benessere motivano i pazienti ad adottare abitudini più sane e mantenere il benessere a lungo termine.

### Impatto aziendale

Le campagne di coinvolgimento personalizzate nel programma di benessere in genere raggiungono un aumento del 30-40% nei tassi di partecipazione al programma, contribuendo a migliorare i risultati sanitari e a rafforzare la fedeltà dei pazienti.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). I programmi di benessere sono esperienze di coinvolgimento sostenuto con più tappe fondamentali, sfide e punti di contatto di ricompensa che richiedono un’orchestrazione adattiva basata sulla partecipazione e sul progresso dei pazienti.

### Considerazioni tecniche

- Integra con dispositivi indossabili e feed di dati di applicazioni fitness applicando etichette chiare di utilizzo dei dati per distinguere i dati di salute dai dati clinici soggetti a requisiti normativi più severi.
- Implementa la gestione del consenso che consente ai pazienti di concedere e revocare l’autorizzazione per la raccolta di dati sul benessere indipendentemente dalle loro preferenze di comunicazione clinica.
- Progettare la logica di percorso che regola la difficoltà di sfida e la frequenza di comunicazione in base ai modelli di coinvolgimento di ogni paziente per evitare scoraggiamento o affaticamento.
- Assicurati che il monitoraggio dei premi e degli incentivi sia conforme alle normative sanitarie applicabili in materia di incentivi per i pazienti e ai requisiti anti-kickback.


## Coordinamento team di assistenza

Consentire la comunicazione e il coordinamento personalizzati tra i pazienti e i membri del loro team di assistenza in base al piano di assistenza e alle preferenze individuali. Un migliore coordinamento porta a transizioni di assistenza più fluide e a risultati migliori per i pazienti con esigenze di assistenza complesse.

### Impatto aziendale

Comunicazioni efficaci di coordinamento del team di assistenza si traducono in genere in un miglioramento del 35-45% nel coinvolgimento del team di assistenza e in risultati misurabilmente migliori di coordinamento dell&#39;assistenza tra i piani di assistenza multi-provider.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Il coordinamento del team di assistenza coinvolge più parti interessate e flussi di comunicazione continui che devono adattarsi in base alle fasi cardine del piano di assistenza, ai cambiamenti dello stato del paziente e alle azioni del provider.

### Considerazioni tecniche

- Implementare controlli dell’accesso basati sui ruoli e etichette di utilizzo dei dati per garantire che ogni membro dell’équipe di assistenza riceva solo le informazioni relative al paziente in base al suo ruolo nel piano di assistenza.
- Integrazione con i sistemi di gestione dell’assistenza e delle cartelle cliniche elettroniche per ricevere aggiornamenti del piano di assistenza, completamenti delle segnalazioni ed eventi di transizione dell’assistenza che attivano i messaggi di coordinazione.
- Progettare percorsi di comunicazione separati per i messaggi rivolti ai pazienti e ai fornitori, garantendo che la terminologia clinica sia utilizzata in modo appropriato per i fornitori, mentre i messaggi dei pazienti rimangano chiari e accessibili.
- Mantenere una pista di controllo completa di tutte le comunicazioni di coordinamento dell&#39;assistenza per garantire la conformità alle normative sulla continuità dell&#39;assistenza e ai requisiti di accreditamento.
