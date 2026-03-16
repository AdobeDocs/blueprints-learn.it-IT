---
title: Acquisto di soluzioni di marketing e gestione dei Percorsi basate su gruppi
description: Scopri come sviluppare percorsi a livello di account che qualifichino i lead in gruppi di acquisto per migliorare l’efficacia del marketing B2B.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7932'
ht-degree: 0%

---


# Acquisto di soluzioni di marketing e gestione dei percorsi basate su gruppi

Questa guida fornisce un riferimento completo all’implementazione per l’acquisto di soluzioni di marketing e gestione dei percorsi basate su gruppi. È progettato per architetti di soluzioni, tecnici di marketing e ingegneri di implementazione che devono implementare l&#39;orchestrazione dei percorsi a livello di account con la gestione dei gruppi di acquisto tramite [!DNL Adobe Journey Optimizer B2B Edition] e [!DNL Real-Time CDP B2B Edition].

Utilizza questo documento per capire cosa configurare, dove esistono opzioni di implementazione e quali compromessi sono alla base di ogni decisione.

A differenza dei modelli di percorso a livello di persona, questo modello opera a livello di account, qualificando i singoli lead in gruppi di acquisto associati agli interessi della soluzione, valutando il coinvolgimento a livello di gruppo di acquisto e orchestrando percorsi di account con più passaggi che progrediscono attraverso le fasi della pipeline verso la preparazione alle vendite.

## Panoramica del caso d’uso

Le organizzazioni B2B devono affrontare una sfida fondamentale: le decisioni di acquisto vengono prese raramente da un singolo individuo. Gli acquisti B2B complessi coinvolgono più parti interessate — decisori, influencer, campioni, titolari del budget e valutatori tecnici — che collettivamente formano un &quot;gruppo di acquisto&quot;. Il marketing tradizionale basato su lead tratta ogni persona in modo indipendente, senza il segnale critico che indica se la giusta combinazione di ruoli all’interno di un account è attiva e pronta per l’acquisto.

L’acquisto di attività di marketing e gestione dei percorsi basate su gruppi risolve questo problema spostando l’unità di orchestrazione dai singoli lead agli account e ai gruppi di acquisto. Il modello consente agli addetti al marketing B2B di definire gli interessi delle soluzioni (i prodotti o i servizi venduti), creare modelli di gruppi di acquisto che specificano quali ruoli sono necessari per una decisione di acquisto, qualificare i lead in ingresso rispetto a tali ruoli, valutare il coinvolgimento a livello di gruppo di acquisto e orchestrare percorsi di account che rispondano ai segnali di completezza e preparazione dei gruppi di acquisto.

Il risultato desiderato è il miglioramento della qualità e della velocità della pipeline: il marketing consegna gli account alle vendite solo quando le persone giuste all’interno dell’account sono coinvolte e il gruppo di acquisto è sufficientemente completo, riducendo lo sforzo di vendita sprecato e accelerando la progressione delle transazioni.

## Obiettivi aziendali chiave

Questo modello di caso d’uso supporta i seguenti obiettivi aziendali.

### Migliorare la qualificazione e la conversione dei lead

Aumenta la qualità dei lead e accelera la progressione della pipeline tramite valutazione, nutrimento e follow-up personalizzato.

**KPI:** conversione lead, conversione prospect/lead, efficienza

[Ulteriori informazioni sul miglioramento della qualificazione e conversione dei lead](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### Aumentare la generazione di lead

Genera lead più qualificati per la pipeline di vendita tramite moduli, eventi, contenuti e coinvolgimento multicanale.

**KPI:** potenziali clienti, costo per lead, conversione lead

[Ulteriori informazioni sull&#39;aumento della generazione di lead](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### Aumento dei profitti e delle vendite

Incrementa i ricavi aziendali con canali digitali ottimizzati, campagne e percorsi di clienti.

**KPI:** crescita dei ricavi, velocità della pipeline, tasso di chiusura delle transazioni

[Ulteriori informazioni sull&#39;aumento dei ricavi e delle vendite](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

## Esempi di casi d’uso tattici

Di seguito sono riportati scenari specifici in cui è possibile applicare questo modello.

- **Qualificazione del gruppo di acquisto specifico per la soluzione** — Definire i gruppi di acquisto per ogni linea di prodotti (ad esempio, &quot;Enterprise CRM&quot;, &quot;Data Platform&quot;, &quot;Security Suite&quot;) con i modelli di ruolo che specificano gli utenti tipo richiesti (buyer economico, valutatore tecnico, promotore, utente finale) e i lead qualificati dal sistema di automazione del CRM e del marketing rispetto a tali ruoli.
- **percorso di account per l&#39;accelerazione della pipeline** — Orchestrare un percorso di account in più passaggi che invia e-mail di crescita mirate a ruoli meno coinvolti all&#39;interno di un gruppo di acquisto, attiva gli avvisi di vendita quando vengono raggiunte le soglie di coinvolgimento e passa l&#39;account a una fase pronta per le vendite.
- **Campagne di completezza del gruppo di acquisto**: identifica gli account in cui i gruppi di acquisto hanno ruoli mancanti (ad esempio, nessun buyer economico identificato) e avvia campagne di acquisizione mirate per coinvolgere gli utenti tipo giusti all&#39;interno di tali account.
- **percorsi di account di cross-selling**: dopo la chiusura di un&#39;offerta iniziale, creare nuovi gruppi di acquisto per interessi di soluzioni complementari e orchestrare percorsi di account che alimentino il comitato di acquisto espanso.
- **Nuovo coinvolgimento per offerte in stallo**: rileva gli account in cui i punteggi di coinvolgimento dei gruppi di acquisto sono diminuiti e attiva percorsi di ricoinvolgimento con nuovi contenuti, coinvolgimento dei dirigenti o inviti a eventi.
- **Allineamento vendite e marketing tramite approfondimenti CRM**: verifica dello stato del percorso di acquisto, dei dati di coinvolgimento e dell&#39;avanzamento del gruppo di account direttamente in [!DNL Salesforce] o [!DNL Dynamics 365] in modo che i rappresentanti abbiano visibilità in tempo reale in account qualificati per il marketing.
- **Aggiornamenti dei gruppi di acquisto basati sugli eventi**: aggiorna automaticamente l&#39;iscrizione al gruppo di acquisto e i punteggi di coinvolgimento quando i lead partecipano a webinar, scaricano white paper, visitano pagine di prezzi o richiedono demo.
- **Coordinamento di account con più aree geografiche**: consente di gestire gruppi di acquisto in account globali in cui diversi contatti regionali ricoprono ruoli diversi, unificando il punteggio di coinvolgimento tra aree geografiche diverse.

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare l’efficacia di questo modello di caso d’uso.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Percentuale di completezza del gruppo di acquisto | Percentuale di gruppi di acquisto in cui sono stati inseriti tutti i ruoli richiesti | [!DNL AJO B2B] dashboard di Analytics: tieni traccia della copertura dei ruoli per gruppo di acquisto |
| Punteggio di coinvolgimento del gruppo di acquisto | Punteggio di coinvolgimento aggregato per tutti i membri di un gruppo di acquisto | Punteggio di coinvolgimento [!DNL AJO B2B]: punteggi a livello di persona aggregati al gruppo di acquisto |
| Percentuale account qualificati marketing (MQA) | Percentuale di account che raggiungono la soglia qualificata per il marketing | Criteri di uscita dal percorso di conti: i conti passano alla fase di preparazione alla vendita |
| Velocità della pipeline | Tempo medio dalla creazione del gruppo di acquisto all&#39;opportunità qualificata per le vendite | Integrazione CRM: tenere traccia delle transizioni di fase da [!DNL AJO B2B] alla pipeline CRM |
| Tasso di qualificazione del gruppo lead-acquisto | Percentuale di lead qualificati per l&#39;acquisto di ruoli gruppo | [!DNL AJO B2B] Gestione del gruppo di acquisto: rapporto lead qualificati e non qualificati |
| Percentuale di risposta avviso vendite | Percentuale di avvisi di vendita che risultano in attività di follow-up vendite | Approfondimenti vendite CRM: tracciare la conversione da avviso ad attività |
| Percentuale di completamento Percorso conto | Percentuale di account che completano il percorso di percorso previsto | [!DNL AJO B2B] dashboard di Analytics: metriche di completamento percorso |
| Tasso di coinvolgimento e-mail (B2B) | Percentuali di apertura e click-through per e-mail di crescita B2B | Rapporti di [!DNL AJO B2B]: metriche di consegna e coinvolgimento e-mail |

## Schema del caso d’uso

**Acquisto di attività di marketing e gestione dei percorsi basate sui gruppi**

Sviluppa percorsi a livello di account che qualifichino i lead in gruppi di acquisto per migliorare l’efficacia del marketing B2B.

**Catena di funzioni:** Identificazione account > Definizione gruppo di acquisto > Qualificazione lead > Esecuzione Percorso di conti > Punteggio coinvolgimento > Generazione rapporti

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni Adobe.

- **[!DNL Journey Optimizer B2B Edition]([!DNL AJO B2B])** — Orchesta i percorsi a livello di account, gestisce i gruppi di acquisto con modelli di ruolo e interessi nelle soluzioni, valuta il coinvolgimento a livello di persona e gruppo di acquisto, crea contenuti e-mail B2B, invia messaggi SMS, configura avvisi di vendita e fornisce dashboard di analisi B2B.
- **[!DNL Real-Time CDP B2B Edition]([!DNL RT-CDP B2B])** - Unifica i profili account dai dati B2B tra sorgenti, risolve le relazioni tra persone e account, valuta i tipi di pubblico a livello di account, configura destinazioni specifiche per B2B ([!DNL Marketo Engage], [!DNL LinkedIn], CRM) e applica la governance dei dati nei dati B2B.

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve essere al suo posto | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Obbligatorio | Sandbox con provisioning di [!DNL AJO B2B Edition] e [!DNL RT-CDP B2B Edition] diritti abilitati. Ruoli configurati per gli addetti al marketing B2B, le operazioni di vendita e gli amministratori con le autorizzazioni appropriate per la gestione dei gruppi di acquisto, i percorsi di account e le impostazioni di integrazione CRM. | [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home), [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Obbligatorio | Schemi XDM B2B configurati utilizzando classi specifiche per B2B: XDM Business Account, XDM Business Opportunity, XDM Business Person (lead/contatto), XDM Business Campaign e XDM Business Marketing List. Devono essere presenti gruppi di campi per gli attributi dell’account, gli attributi della persona e i dati di attività/coinvolgimento. Set di dati creati e abilitati per il profilo per ogni schema. | [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Classi di schema B2B](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Origini dati e raccolta | Obbligatorio | Sono state stabilite pipeline di acquisizione dati B2B, in genere tramite il connettore di origine [!DNL Marketo Engage] o i connettori di origine CRM [!DNL Salesforce]/[!DNL Dynamics]. I dati di account, persona, opportunità, campagna e membri della campagna devono confluire nei set di dati di AEP. Per il punteggio di coinvolgimento, è necessario acquisire anche i dati di coinvolgimento comportamentale (visite web, interazioni e-mail, download di contenuti). | [Panoramica origini](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home), [Connettore Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| Configurazione identità e profilo | Obbligatorio | Risoluzione identità B2B configurata per risolvere le relazioni persona-account. Gli spazi dei nomi di identità per gli identificatori B2B ([!DNL Marketo] ID persona, [!DNL Salesforce] ID lead/contatto, ID account) devono esistere. Criteri di unione configurati per l’unificazione dei profili B2B. I profili account devono essere unificati dai dati provenienti da più origini. | [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Risoluzione identità B2B](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) |
| Definizione e segmentazione del pubblico | Obbligatorio | Definizioni del pubblico a livello di account create utilizzando gli attributi dell’account, gli attributi della persona e i dati dell’attività. I tipi di pubblico dell’account identificano i conti che inseriscono i percorsi dei gruppi di acquisto. La valutazione in batch è in genere sufficiente per i percorsi di account B2B, anche se la valutazione in streaming può essere utilizzata per i trigger di qualificazione dell’account in tempo reale. | [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Pubblico dell&#39;account](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Consigliato | Gli attributi calcolati possono aggregare gli eventi di coinvolgimento a livello di persona (aperture di e-mail, download di contenuti, partecipazione a webinar) nelle metriche di coinvolgimento a livello di account che alimentano il punteggio del gruppo di acquisto e la logica di qualificazione dell’account. | [Panoramica attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Consigliato | La gestione del consenso è fondamentale per le comunicazioni e-mail e SMS B2B. I criteri di scadenza dei set di dati consentono di gestire il ciclo di vita dei dati di coinvolgimento transitorio e di garantire la conformità ai requisiti di conservazione dei dati. | [Gestione avanzata del ciclo di vita dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Etichettatura e applicazione dell’utilizzo dati | Consigliato | I dati B2B spesso contengono informazioni aziendali sensibili e dati personali di contatti commerciali. I criteri di governance dei dati garantiscono l’uso conforme dei dati B2B tra le destinazioni, in particolare quando si attiva su piattaforme pubblicitarie o sistemi di terze parti. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Monitoraggio e osservabilità | Consigliato | Il monitoraggio garantisce che le pipeline di dati B2B (sincronizzazioni CRM/[!DNL Marketo]) siano integre, che i profili account siano aggiornati e che le esecuzioni del percorso di account procedano senza errori. Gli avvisi sugli errori del flusso di dati di origine sono fondamentali per la gestione della valuta dei dati. | [Panoramica di Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting e analisi | Incluso | I dashboard di analisi B2B all&#39;interno di [!DNL AJO B2B Edition] forniscono coinvolgimento del gruppo di acquisto, prestazioni del percorso di account e metriche della pipeline. [!DNL CJA B2B Edition] estende l’analisi con l’analisi dell’area di lavoro a livello di account, l’analisi del gruppo di acquisto e la correlazione delle opportunità. | [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Configurazione interessi soluzione | Fase 1: Impostazione del gruppo di interesse e di acquisto della soluzione | Definire gli interessi della soluzione che associano prodotti o servizi ai criteri di qualificazione del gruppo di acquisto |
| Gestione gruppo acquisti | Fase 1: Impostazione del gruppo di interesse e di acquisto della soluzione | Crea e gestisci gruppi di acquisto con modelli di ruolo, mappatura utenti tipo e definizioni di interessi per la soluzione |
| Journey Orchestration dell’account | Fase 3: Progettazione ed esecuzione del Percorso dell’account | Progetta e gestisci percorsi di account con più passaggi con condizioni, azioni e diramazioni basate sul coinvolgimento |
| Punteggio di coinvolgimento | Fase 2: qualificazione dei lead e valutazione del coinvolgimento | Punteggio del coinvolgimento a livello di persona all’interno dei gruppi di acquisto per misurare la completezza e la preparazione del gruppo di acquisto |
| Qualificazione dell’account | Fase 2: qualificazione dei lead e valutazione del coinvolgimento | Utilizzare agenti di qualifica dell’account basati sull’intelligenza artificiale per valutare la fattibilità dell’account e la qualità della pipeline |
| Authoring di e-mail B2B | Fase 3: Progettazione ed esecuzione del Percorso dell’account | Creare contenuti e-mail B2B con modelli, frammenti visivi, temi del brand e generazione di contenuti assistiti da intelligenza artificiale |
| Gestione canale SMS | Fase 3: Progettazione ed esecuzione del Percorso dell’account | Configurare e gestire le comunicazioni SMS all’interno dei percorsi di account B2B |
| Configurazione avviso vendite | Fase 4: Allineamento delle vendite e integrazione con le soluzioni CRM | Configura le e-mail di avviso sulle vendite per notificare ai team di vendita le fasi cardine del coinvolgimento dell’account e i segnali di acquisto |
| Approfondimenti vendite CRM | Fase 4: Allineamento delle vendite e integrazione con le soluzioni CRM | Fornisci visibilità in CRM ([!DNL Salesforce], [!DNL Dynamics]) per lo stato del gruppo di acquisto, i dati di coinvolgimento e l&#39;avanzamento del percorso di account |
| Dashboard di Analytics B2B | Fase 5: Reporting e ottimizzazione | Monitorare le prestazioni del percorso di account, il coinvolgimento dei gruppi di acquisto e le metriche della pipeline tramite dashboard intelligenti e di coinvolgimento |

### [!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Unificazione profilo account | Fase 0: Base di dati B2B | Consolidare i dati B2B tra origini diverse in profili di account unificati utilizzando classi di schema B2B XDM e gruppi di campi specializzati |
| Risoluzione identità B2B | Fase 0: Base di dati B2B | Risolvere le relazioni tra persone utilizzando gli identificatori primari, supportando gerarchie di account a più livelli e mappature molti-a-molti tra persone e account |
| Valutazione del pubblico dell’account | Fase 0: Base di dati B2B | Valuta l’iscrizione al segmento a livello di conto combinando gli attributi del conto, gli attributi della persona e i dati relativi all’attività |
| Configurazione destinazione account | Fase 4: Allineamento delle vendite e integrazione con le soluzioni CRM | Configurare connessioni a destinazioni specifiche di B2B ([!DNL Marketo Engage], [!DNL LinkedIn], sistemi di gestione delle relazioni con i clienti) con mapping dei campi a livello di account |
| Audience Activation dell’account | Fase 4: Allineamento delle vendite e integrazione con le soluzioni CRM | Pubblicare tipi di pubblico basati su account nelle destinazioni per il targeting e l’eliminazione basati su account |
| Integrazione di [!DNL Marketo Engage] | Fase 0: Base di dati B2B | Acquisire e attivare i dati in modo bidirezionale con [!DNL Marketo Engage] utilizzando i connettori di origine e di destinazione B2B nativi |
| Governance dei dati B2B | Fase 0: Base di dati B2B | Applicazione dei criteri di utilizzo dei dati e del consenso in tutti i processi di centralizzazione e attivazione dei dati dell’account B2B |

## Prerequisiti

Completa quanto segue prima di iniziare l’implementazione.

- Licenza [!DNL AJO B2B Edition] fornita e abilitata nella sandbox di destinazione
- Licenza [!DNL RT-CDP B2B Edition] fornita e abilitata nella sandbox di destinazione
- Il sistema CRM ([!DNL Salesforce] o [!DNL Microsoft Dynamics 365]) è accessibile con le credenziali API appropriate per la sincronizzazione bidirezionale dei dati
- Istanza [!DNL Marketo Engage] connessa (se si utilizza [!DNL Marketo] come piattaforma di automazione marketing) con il connettore di origine configurato
- Schemi XDM B2B distribuiti: classi di membri account, persona, opportunità, campagna e campagna con gruppi di campi obbligatori
- Dati dell’account e della persona acquisiti in AEP con relazioni persona-account risolte
- Canale e-mail configurato: sottodominio delegato, pool IP riscaldato e superficie di canale creata per l’invio e-mail B2B
- Provider SMS configurato (se il canale SMS è utilizzato nei percorsi di account): provisioning delle credenziali [!DNL Sinch], [!DNL Twilio] o [!DNL Infobip] eseguito
- Team vendite integrato nel componente CRM Sales Insights ([!DNL Salesforce] pacchetto AppExchange o soluzione [!DNL Dynamics] installata)
- Risorse di contenuto preparate: modelli e-mail B2B, temi del brand e frammenti visivi per e-mail di avviso su crescita e vendite
- Tassonomia di interesse della soluzione definita: elenco di prodotti/servizi a cui saranno associati gruppi di acquisto
- Modelli di ruolo del gruppo di acquisto progettati: utenti tipo e ruoli richiesti per ogni interesse della soluzione (ad esempio, buyer economico, valutatore tecnico, promotore)

## Opzioni di implementazione

Questa sezione descrive gli approcci di implementazione disponibili, ciascuno adattato alle diverse esigenze organizzative e ai diversi livelli di maturità.

### Opzione A: interesse per una singola soluzione con percorso di conti lineare

**Ideale per:** organizzazioni che non conoscono la gestione dei gruppi di acquisto e che desiderano iniziare con una singola linea di prodotti o offerta di soluzioni, convalidare l&#39;approccio e ripetere l&#39;iterazione prima di effettuare la scalabilità in base agli interessi di più soluzioni.

**Funzionamento:**

Questo approccio si concentra su un singolo interesse per la soluzione (un prodotto o servizio) con un modello di gruppo di acquisto. Un percorso di account lineare è progettato con fasi sequenziali: identificazione dell’account, formazione del gruppo di acquisto, coinvolgimento nutrizionale, soglia di punteggio di coinvolgimento e trasferimento delle vendite. Il percorso segue un percorso semplice senza diramazioni complesse o tracce parallele.

I lead sono qualificati per l&#39;acquisto di ruoli di gruppo quando vengono acquisiti dal CRM o [!DNL Marketo Engage]. Il percorso di account invia e-mail di formazione ai ruoli meno coinvolti, monitora i punteggi di coinvolgimento e attiva un avviso di vendita quando il gruppo di acquisto raggiunge una soglia di completezza e coinvolgimento definita. Questo approccio fornisce una prova di concetto chiara e misurabile prima di introdurre la complessità.

**Considerazioni chiave:**

- Implementazione e convalida più semplici, per una prima implementazione
- Limitato a un movimento di acquisto di prodotti/servizi alla volta
- La struttura del percorso lineare potrebbe non essere compatibile con i complessi cicli di acquisto a più stadi

**Vantaggi:**

- Time-to-value più rapido con complessità di configurazione minima
- Metriche di successo chiare associate a un’unica soluzione
- Facilità di spiegazione e acquisizione del consenso a livello organizzativo
- Reporting semplice e misurazione dei KPI

**Limitazioni:**

- Non affronta scenari di cross-selling o multi-prodotto
- Gli account interessati a più soluzioni richiedono percorsi separati e non coordinati
- Potrebbe non sfruttare appieno le funzionalità di gestione dei gruppi di acquisto

**Experience League:**

- [Panoramica di AJO B2B edition](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [Creare gruppi di acquisto](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)

### Opzione B: Interessi in più soluzioni con percorsi di account di succursale

**Ideale per:** organizzazioni con più linee di prodotti o offerte di servizi che devono gestire gruppi di acquisto distinti per interesse della soluzione, con percorsi di account che si ramificano in base agli interessi attivi della soluzione e alla distanza di ogni gruppo di acquisto nel processo di qualificazione.

**Funzionamento:**

Sono definiti più interessi per le soluzioni, ciascuno con il proprio modello di ruolo di gruppo di acquisto. Un percorso di account inizia con l’identificazione dell’account e valuta quali interessi della soluzione si applicano a ogni account in base a segnali comportamentali, dati firmografici o intento esplicito. I rami di percorso si occupano di ogni interesse della soluzione attiva, eseguendo percorsi di sviluppo paralleli per diversi gruppi di acquisto all’interno dello stesso account.

Il punteggio di coinvolgimento opera in modo indipendente per gruppo di acquisto, consentendo a un gruppo di acquisto di raggiungere la fattibilità di vendita mentre un altro è ancora in fase di sviluppo. Gli avvisi di vendita sono configurati in base all’interesse della soluzione, pertanto il team di vendita o lo specialista appropriato riceve una notifica quando un gruppo di acquisto specifico è idoneo. Gli approfondimenti CRM presentano tutti i gruppi di acquisto attivi per un account, fornendo alle vendite una visione olistica.

**Considerazioni chiave:**

- Richiede una tassonomia degli interessi di soluzione ben definita e modelli di gruppi di acquisto distinti
- La complessità del percorso aumenta con ogni ulteriore interesse per la soluzione
- È necessario pianificare il coordinamento tra gruppi di acquisto (ad esempio, contatti condivisi con più gruppi di acquisto)

**Vantaggi:**

- Supporto di strategie di vendita incrociata e multi-prodotto
- Il punteggio indipendente per gruppo di acquisto fornisce una visibilità granulare della pipeline
- I team di vendita ricevono avvisi mirati per ogni interesse della soluzione
- Ottimizza le funzionalità di gestione dei gruppi di acquisto di [!DNL AJO B2B Edition]

**Limitazioni:**

- Maggiore complessità dell&#39;implementazione e tempi di implementazione più lunghi
- Sono necessarie più risorse di contenuto (tracce e-mail separate per interesse della soluzione)
- La generazione di rapporti è più complessa con più gruppi di acquisto per account
- Rischio di contatti di messaggistica eccessiva che si trovano in più gruppi di acquisto (richiede la gestione della frequenza)

**Experience League:**

- [Interessi soluzione](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Percorsi di account](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)

### Opzione C: qualificazione dell’account assistito da IA con progressione automatica del percorso

**Ideale per:** organizzazioni B2B mature con dati storici significativi che desiderano sfruttare agenti di qualificazione degli account basati sull&#39;intelligenza artificiale per automatizzare la valutazione della preparazione dell&#39;account, ridurre lo sforzo di qualificazione manuale e regolare dinamicamente i percorsi di percorso in base ai punteggi di preparazione generati dall&#39;intelligenza artificiale.

**Funzionamento:**

Questo approccio si basa sulla base degli interessi per più soluzioni dell’opzione B, ma aggiunge la qualifica dell’account basata sull’intelligenza artificiale per automatizzare la transizione tra le fasi del percorso. Invece di affidarsi esclusivamente alle soglie di punteggio di coinvolgimento basate su regole, l’agente di qualificazione IA valuta la preparazione dell’account utilizzando un set più ampio di segnali: completezza del gruppo di acquisto, velocità di coinvolgimento, adattamento firmografico, modelli di conversione storici e dati di intento.

I percorsi di account utilizzano l’output di qualificazione dell’intelligenza artificiale per determinare i passaggi successivi: gli account con un punteggio di preparazione elevato vengono rapidamente monitorati in caso di avvisi di vendita, gli account di livello intermedio ricevono un’educazione più intensa e gli account con un basso livello di preparazione vengono inseriti in percorsi di consapevolezza a lungo termine. L’agente di intelligenza artificiale viene rivalutato continuamente all’arrivo di nuovi dati di coinvolgimento, consentendo la progressione dinamica del percorso senza intervento manuale.

**Considerazioni chiave:**

- Richiede dati storici sufficienti per formare modelli di qualificazione efficaci
- Gli output di IA devono essere convalidati in base ai risultati effettivi della pipeline prima della distribuzione completa
- Si combina bene con [!DNL CJA B2B Edition] per l&#39;analisi della precisione della qualifica e della correlazione della pipeline

**Vantaggi:**

- Riduce lo sforzo di qualificazione manuale ed elimina gli handoff arbitrari basati su soglie
- Si adatta dinamicamente ai cambiamenti del comportamento dell’account e dei modelli di coinvolgimento
- Migliore qualità della pipeline grazie all’integrazione di segnali multipli oltre ai semplici punteggi di coinvolgimento
- La rivalutazione continua impedisce che i conti rimangano bloccati in fasi di percorso non corrette

**Limitazioni:**

- Richiede dati di conversione storici per una formazione IA significativa
- Le decisioni di qualificazione &quot;scatola nera&quot; possono essere più difficili da comprendere e da fidarsi inizialmente dei team di vendita
- Più complesso risolvere i problemi quando gli account vengono qualificati in modo imprevisto o non lo sono affatto
- Dipende dalla qualità dei dati e dalla completezza di tutti i segnali di ingresso

**Experience League:**

- [Qualificazione dell’account](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Assistente AI in AJO B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)

### Confronto delle opzioni

| Criteri | Opzione A: interesse per una singola soluzione | Opzione B: Interessi in più soluzioni | Opzione C: qualificazione basata sull’IA |
| --- | --- | --- | --- |
| Ideale per | Prima implementazione, singola linea di prodotti | Organizzazioni con più prodotti | Organizzazioni mature con dati storici |
| Complessi | Bassa | Medium - Alta | Alta |
| Time-to-value | 2-4 settimane | 4-8 settimane | 6-12 settimane |
| Interessi soluzione | 1 | Più | Più |
| Struttura del percorso | Lineare | Branching, tracce parallele | Progressione dinamica basata sull’intelligenza artificiale |
| Approccio punteggio | Soglie basate su regole | Basato su regole per gruppo di acquisto | Qualificazione basata sull’intelligenza artificiale + regole |
| Requisiti del contenuto | Minimo (una pista di coltura) | Elevato (per ogni soluzione) | Selezione di contenuti dinamici e ad alta risoluzione |
| Allineamento vendite | Flusso di lavoro con un singolo avviso | Avvisi di interesse per soluzione | Avvisi con priorità e punteggio IA |
| Richiede | Base di dati B2B di base | Tassonomia della soluzione ben definita | Dati di conversione storici + tassonomia |

### Scegli l’opzione giusta

Inizia con queste domande per determinare l’approccio di implementazione migliore:

1. **Quanti prodotti o servizi distinti hanno comitati di acquisto indipendenti?** Se la risposta è una di queste (o se l’organizzazione desidera dimostrare prima il concetto), inizia con l’opzione A. In caso di più domande, passare alla domanda 2.

2. **Esistono dati storici sufficienti sulle offerte vinte/perse, sulla composizione del comitato di acquisto e sui modelli di coinvolgimento?** In caso affermativo e se l’organizzazione desidera ridurre al minimo la qualifica manuale, l’opzione C offre l’approccio più automatizzato. In caso contrario, l’opzione B fornisce supporto per più interessi delle soluzioni con punteggio basato su regole.

3. **Qual è la capacità di gestione delle modifiche dell&#39;organizzazione?** Le opzioni B e C richiedono un maggiore allineamento organizzativo (produzione di contenuti, abilitazione delle vendite, coordinamento interfunzionale). Se la capacità è limitata, iniziare con l&#39;opzione A ed espandere.

Un percorso di progressione comune è: iniziare con l’opzione A per dimostrare il concetto con un interesse per la soluzione, espandere l’opzione B aggiungendo gli interessi della soluzione man mano che aumenta la fiducia, quindi inserire il livello nella qualifica di IA dell’opzione C una volta che sono disponibili sufficienti dati storici per addestrare i modelli in modo efficace.

## Fasi di implementazione

Le fasi seguenti descrivono il processo di implementazione passo per passo di questo modello di caso d’uso.

### Fase 0: fondazione di dati B2B

**Funzioni dell&#39;applicazione:** [!DNL RT-CDP B2B]: unificazione profilo account, risoluzione identità B2B, integrazione [!DNL Marketo Engage], governance dati B2B, valutazione pubblico account

Questa fase stabilisce l&#39;infrastruttura di dati B2B in [!DNL RT-CDP B2B Edition]. Unificherai i dati dell&#39;account da CRM, automazione marketing e altre origini in un unico profilo account, risolverai le relazioni tra persone e account, configurerai la governance dei dati B2B e creerai tipi di pubblico a livello di account che confluiranno nella gestione dei gruppi di acquisto [!DNL AJO B2B Edition].

#### Decisione: strategia per le fonti di dati B2B

Quali sistemi fungono da origini primarie per i dati di account, persona e coinvolgimento?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| [!DNL Marketo Engage] come origine primaria | [!DNL Marketo] è la piattaforma di automazione marketing dell&#39;organizzazione con una ricca cronologia di coinvolgimento | Il connettore bidirezionale nativo semplifica la configurazione; il flusso automatico dei dati di coinvolgimento; le relazioni tra persone ereditate da [!DNL Marketo] |
| CRM ([!DNL Salesforce]/[!DNL Dynamics]) come origine primaria | CRM è il sistema di registrazione per account e contatti; [!DNL Marketo] non è utilizzato | Richiede la configurazione del connettore di origine del sistema di gestione delle relazioni con i clienti; i dati del coinvolgimento possono richiedere origini supplementari; relazioni persona-account da associazioni di contatto dell’account del sistema di gestione delle relazioni con i clienti |
| Ibrido: CRM per account + [!DNL Marketo] per il coinvolgimento | CRM possiede i dati master account/contatto mentre [!DNL Marketo] acquisisce il coinvolgimento comportamentale | Schema più comune per le organizzazioni che utilizzano entrambi; richiede un&#39;attenta risoluzione dell&#39;identità per collegare [!DNL Marketo] persone ai contatti CRM |

#### Decisione: strategia per il pubblico dell’account

Come definire i tipi di pubblico dell’account per l’immissione nel percorso?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Pubblico dell’account basato su firmware | Eseguire il targeting degli account in base al settore, alle dimensioni dell’azienda, al livello di fatturato o alla posizione geografica | Valido per elenchi di target ABM; non richiede dati di coinvolgimento; può essere ampio |
| Pubblico dell’account basato sul coinvolgimento | Eseguire il targeting degli account in cui le persone hanno mostrato segnali di intenti comportamentali | Richiede il flusso di dati di coinvolgimento; targeting più preciso; potrebbe mancare account con interesse latente |
| Firmografico e coinvolgimento combinati | Account di destinazione che corrispondono al profilo cliente ideale E mostrano coinvolgimento | Più preciso; richiede entrambi i tipi di dati; consigliato per la generazione di pipeline qualificate |

**Navigazione interfaccia utente:** Piattaforma > Origini > Catalogo > Seleziona origine ([!DNL Marketo Engage], [!DNL Salesforce], ecc.) > Configurazione del flusso di dati

**Dettagli configurazione chiave:**

- Configurare gli schemi XDM B2B per ogni entità B2B (account, persona, opportunità, campagna, membro della campagna) con i gruppi di campi richiesti
- Configurare i connettori di origine per CRM e/o [!DNL Marketo Engage] con la pianificazione appropriata (in genere intervalli di 1-4 ore per i dati B2B)
- Configurare gli spazi dei nomi di identità per gli identificatori B2B ([!DNL Marketo] ID persona, ID lead SFDC, ID contatto SFDC, ID account)
- Abilitare la risoluzione dell’identità B2B per collegare le persone agli account
- Creare tipi di pubblico a livello di account utilizzando la funzionalità Tipi di pubblico dell&#39;account in [!DNL RT-CDP]

**Documentazione di Experience League:**

- [Panoramica di RT-CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [Schemi B2B in Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Connettore sorgente Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Pubblico dell’account](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [Risoluzione dell’identità B2B](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)

### Fase 1: interesse della soluzione e configurazione del gruppo di acquisto

**Funzioni dell&#39;applicazione:** [!DNL AJO B2B]: configurazione interessi soluzione, gestione gruppi acquisti

Questa fase definisce gli interessi della soluzione (prodotti/servizi) e i modelli di gruppo di acquisto che costituiscono il nucleo del modello di gestione del gruppo di acquisto. Potrai creare interessi per la soluzione, definire modelli di ruolo con requisiti utente tipo e configurare il modo in cui i lead vengono qualificati per l’acquisto di ruoli di gruppo.

#### Decisione: granularità degli interessi della soluzione

A quale livello devono essere definiti gli interessi della soluzione?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Interessi per le soluzioni a livello di prodotto | Ogni prodotto ha il proprio gruppo di acquisto | Più granulare; abilita modelli di gruppi di acquisto specifici per prodotto; può comportare molti gruppi di acquisto per account |
| Interessi a livello di categoria della soluzione | Raggruppa i prodotti correlati in categorie di soluzioni (ad esempio, &quot;Marketing Cloud&quot; invece di prodotti singoli) | Più semplice da gestire; meno gruppi di acquisto; i ruoli possono essere più generici; consigliato per le distribuzioni iniziali |
| Interessi a livello di caso d’uso | Definire gli interessi relativi ai risultati aziendali anziché ai prodotti (ad esempio, &quot;Trasformazione digitale&quot;) | Si allinea con la vendita consultiva; l’acquisto di ruoli di gruppo può estendersi a più prodotti; più difficile da mappare alle fasi della pipeline CRM |

#### Decisione: progettazione modello ruolo gruppo di acquisto

Come definire i ruoli all’interno di ciascun gruppo di acquisto?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Modello di ruolo standard | Utilizza un set di ruoli comuni per tutti gli interessi della soluzione (ad esempio, acquirente economico, valutatore tecnico, campione, utente finale) | Punteggio e qualifica coerenti; più facile da gestire; potrebbe non acquisire ruoli specifici della soluzione |
| Modelli di ruolo specifici per la soluzione | Definisci ruoli univoci per interesse soluzione in base al comitato di acquisto effettivo per quel prodotto | Qualificazione più precisa; richiede una conoscenza più approfondita di ciascun processo di acquisto; manutenzione più elevata |
| Modelli di ruolo su più livelli | Definire i ruoli richiesti (must-have per la qualifica) e facoltativi (migliorare la completezza ma non obbligatorio) | Bilancia la precisione con la flessibilità; evita che criteri di qualificazione eccessivamente stringenti blocchino la pipeline |

**Navigazione interfaccia utente:** [!DNL AJO B2B Edition] > Gruppi di acquisto > Interessi soluzione > Crea interesse soluzione

**Navigazione interfaccia utente:** [!DNL AJO B2B Edition] > Gruppi di acquisto > Modelli ruolo > Crea modello ruolo

**Dettagli configurazione chiave:**

- Definire gli interessi di ciascuna soluzione con un nome, una descrizione e il risultato aziendale a cui si rivolge
- Crea modelli di ruolo che specificano gli utenti tipo richiesti per ciascun gruppo di acquisto (ad esempio, &quot;Responsabile delle decisioni&quot;, &quot;Influencer&quot;, &quot;Professionista&quot;, &quot;Sponsor esecutivo&quot;)
- Configurare i criteri di qualifica per il lead-ruolo: il modo in cui il sistema determina a quale persona è mappato un lead (in base alla qualifica professionale, al reparto, all’anzianità o agli attributi personalizzati)
- Imposta soglie di completezza: definisci la percentuale di ruoli da compilare affinché un gruppo di acquisto sia considerato &quot;completo&quot;
- Collega gli interessi della soluzione ai tipi di pubblico dell’account o agli attributi dell’account che indicano un potenziale interesse

**Opzioni divergenti:**

**Per L&#39;Opzione A (Interesse Soluzione Singola):**
Crea un interesse per la soluzione e un modello di ruolo. Concentrati su un movimento di acquisto chiaro e ben compreso per il prodotto o servizio principale dell’organizzazione.

**Per L&#39;Opzione B (Più Interessi Soluzione):**
Crea più interessi per la soluzione, ciascuno con il proprio modello di ruolo. Mappa ogni interesse della soluzione al tipo di prodotto/opportunità CRM appropriato per il tracciamento della pipeline a valle.

**Per l&#39;opzione C (qualifica assistita da IA):**
Configura gli interessi della soluzione e i modelli di ruolo come nell’opzione B, ma in aggiunta configura l’agente di qualificazione IA con dati storici sulle composizioni di gruppi di acquisto di successo e sui risultati dell’offerta per addestrare il modello di qualifica.

**Documentazione di Experience League:**

- [Panoramica sui gruppi di acquisto](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [Interessi soluzione](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Modelli di ruolo](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [Creare gruppi di acquisto](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)

### Fase 2: qualificazione dei lead e valutazione del coinvolgimento

**Funzioni dell&#39;applicazione:** [!DNL AJO B2B]: punteggio di coinvolgimento, qualifica dell&#39;account

Questa fase imposta il modello di valutazione del coinvolgimento che misura il coinvolgimento a livello di persona all’interno dei gruppi di acquisto e lo porta ai punteggi di preparazione a livello di gruppo di acquisto e di account. Puoi configurare le regole di punteggio, definire le soglie di coinvolgimento per la qualifica e, facoltativamente, abilitare la qualifica dell’account basata sull’intelligenza artificiale.

#### Decisione: modello di valutazione del coinvolgimento

Come si dovrebbe valutare il coinvolgimento a livello di persona e gruppo di acquisto?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Punteggio basato sulle attività | Assegna valori punto ad azioni specifiche (apertura e-mail = 5 punti, download contenuto = 15 punti, richiesta demo = 50 punti) | Trasparente e facile da regolare; richiede manutenzione continua con il cambiare dei contenuti e dei canali; più familiare a [!DNL Marketo] utenti |
| Punteggio ponderato in base all’attualità | Peso delle attività recenti superiore a quelle precedenti (modello di punteggio in declino) | Riflette meglio le intenzioni correnti; impedisce che punteggi elevati non aggiornati gonfiino le qualifiche; è più complesso da configurare |
| Punteggio basato sull’intelligenza artificiale | Utilizza l&#39;agente di qualificazione IA [!DNL AJO B2B] per generare punteggi di idoneità basati sul riconoscimento pattern | Più sofisticato; si adatta automaticamente; richiede dati storici; può essere inizialmente opaco per i team di vendita |

#### Decisione: approccio basato sulla soglia di qualifica

Quando un gruppo di acquisto deve essere considerato pronto per il passaggio di consegne?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo soglia punteggio | Gruppo di acquisto idoneo quando il punteggio di impegno aggregato supera un valore definito | Semplice da implementare; la soglia di punteggio potrebbe dover essere regolata nel tempo; non considera la composizione del ruolo |
| Completezza + soglia di punteggio | Il gruppo di acquisto è idoneo quando sono raggiunte sia la copertura minima dei ruoli che la soglia di punteggio | Qualificazione più solida; impedisce il passaggio di consegne di gruppi di acquisto con punteggi elevati ma senza ruoli chiave |
| Preparazione determinata dall’intelligenza artificiale | L’agente di qualificazione IA determina la fattibilità utilizzando più segnali oltre il punteggio e la completezza | Più sofisticato; tiene conto della velocità di acquisto, dei segnali competitivi e dei pattern storici; solo opzione C |

**Navigazione interfaccia utente:** [!DNL AJO B2B Edition] > Gruppi di acquisto > Punteggio di coinvolgimento > Configura regole punteggio

**Dettagli configurazione chiave:**

- Definire le regole per il punteggio di coinvolgimento: assegna valori di punto agli eventi comportamentali (aperture di e-mail, clic, visite alle pagine web, download di contenuti, invii di moduli, partecipazione a webinar, richieste demo)
- Configurare il decadimento del punteggio o la ponderazione dell’attualità se si utilizza il punteggio sensibile al tempo
- Imposta aggregazione punteggio a livello di gruppo di acquisto: il modo in cui i punteggi delle persone si combinano in un punteggio del gruppo di acquisto (somma, media ponderata o soglia minima per ruolo)
- Definire le soglie di qualifica: il punteggio e i livelli di completezza che attivano la transizione alla fase di acquisto successiva
- Configurare l’agente di qualificazione IA (opzione C): addestrarsi con i dati storici delle operazioni, definire i segnali che l’agente deve considerare e impostare le soglie di affidabilità

**Documentazione di Experience League:**

- [Punteggio di coinvolgimento](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Fasi del gruppo di acquisto](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Qualificazione dell’account](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)

### Fase 3: Progettazione ed esecuzione del percorso dell’account

**Funzioni dell&#39;applicazione:** [!DNL AJO B2B]: Journey Orchestration dell&#39;account, authoring di e-mail B2B, gestione dei canali SMS

Questa fase progetta e distribuisce il percorso di account che orchestra il coinvolgimento con i membri del gruppo di acquisto. Verranno creati percorsi di account con condizioni di ingresso, nodi di azione (e-mail, SMS), rami di condizione (in base alla fase del gruppo di acquisto, al punteggio di coinvolgimento, alla copertura del ruolo), passaggi di attesa e criteri di uscita.

#### Decisione: trigger di immissione Percorso

Quale evento o condizione fa entrare un account nel percorso?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Qualificazione del pubblico dell’account | L’account entra quando si unisce al pubblico di un account di destinazione | Orientata ai batch; adatta per voci basate su elenchi ABM; il pubblico deve essere predefinito |
| Evento di creazione gruppo di acquisto | L&#39;account viene immesso quando viene creato un gruppo di acquisto per l&#39;account | Basato su eventi; attivato dalla qualifica di lead in un ruolo di gruppo di acquisto; più in tempo reale |
| Modifica attributo account | L’account viene immesso quando viene modificato un attributo specifico (ad esempio, punteggio intento, livello account) | Richiede che l’attributo di attivazione venga aggiornato in tempo reale o quasi in tempo reale |

#### Decisione: mix di canali per lo sviluppo B2B

Quali canali deve utilizzare il percorso di account per coinvolgere i membri del gruppo di acquisto?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo e-mail | La maggior parte delle interazioni B2B avviene tramite e-mail; non esiste alcuna infrastruttura di consenso SMS | Configurazione più semplice; pattern B2B più comune; potrebbero mancare i contatti per la prima volta da dispositivo mobile |
| E-mail + SMS | L’organizzazione dispone di SMS opt-in dai contatti commerciali; sono necessarie notifiche ad alta urgenza | SMS efficaci per gli avvisi sensibili al tempo (promemoria di eventi, conferme di riunioni); richiede la configurazione del provider SMS |
| E-mail + SMS + Avvisi di vendita | Spettro completo: strategie di marketing via e-mail/SMS più notifiche del team di vendita | Più completo; richiede l’adozione da parte del team di vendita del flusso di lavoro di avviso; coordina i punti di contatto di marketing e vendita |

#### Decisione: strategia di ramificazione di Percorso

In che modo il ramo di percorso deve essere basato sullo stato dell’account e del gruppo di acquisto?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Branching basato su stage | Ramo basato sulla fase del gruppo di acquisto (ad esempio, consapevolezza, considerazione, decisione) | Si allinea alle fasi funnel tradizionali; contenuto mappato alle fasi; cancella percorso di progressione |
| Diramazione basata sui ruoli | Ramo per inviare contenuti diversi a diversi ruoli dei gruppi di acquisto (contenuti tecnici per i valutatori, contenuti sul ROI per gli acquirenti economici) | Più personalizzato; richiede risorse di contenuto specifiche per il ruolo; maggiore impegno nella produzione dei contenuti |
| Branching basato su coinvolgimento | Ramo basato sulle soglie di punteggio di coinvolgimento (coinvolgimento ridotto = coinvolgimento ripetuto, elevato = accelerazione) | Dinamico e reattivo; si adatta al comportamento effettivo; può creare strutture ramificate complesse |

**Navigazione interfaccia utente:** [!DNL AJO B2B Edition] > Percorsi account > Crea Percorso

**Dettagli configurazione chiave:**

- Creare l’area di lavoro del percorso di conti con la condizione di ingresso selezionata
- Aggiungere nodi del percorso di account: azioni e-mail, azioni SMS, passaggi di attesa, suddivisioni delle condizioni e diramazioni dei percorsi
- Creare contenuti e-mail B2B utilizzando il Designer e-mail B2B con temi del brand, frammenti visivi e generazione di contenuti assistiti da intelligenza artificiale
- Configurare i token di personalizzazione che fanno riferimento agli attributi dell’account, agli attributi della persona e ai dati del gruppo di acquisto
- Impostare le durate di attesa tra i punti di contatto (i percorsi B2B in genere utilizzano attese più lunghe: 3-7 giorni tra le e-mail)
- Definisci criteri di uscita: condizioni in base alle quali i conti lasciano il percorso (il gruppo di acquisto raggiunge la soglia di qualificazione, l’opportunità creata in CRM, l’account rinuncia)
- Configurare le azioni SMS se si utilizza un canale SMS (richiede la configurazione del provider SMS e il consenso di contatto)
- Verifica il percorso con account di test prima della pubblicazione

**Opzioni divergenti:**

**Per L&#39;Opzione A (Interesse Soluzione Singola):**
Progettare un percorso lineare con stadi sequenziali. L’ingresso si basa su un pubblico di un singolo account o su un evento di creazione di un gruppo di acquisto. Un percorso di e-mail nurture con crescente urgenza e profondità di contenuto.

**Per L&#39;Opzione B (Più Interessi Soluzione):**
Progetta un percorso con rami paralleli per ogni interesse della soluzione. Utilizza i nodi delle condizioni per indirizzare gli account alla traccia di sviluppo appropriata in base ai gruppi di acquisto esistenti. Ogni ramo ha le proprie soglie di contenuto e punteggio.

**Per l&#39;opzione C (qualifica assistita da IA):**
Progetta un percorso in cui i nodi della condizione valutino il punteggio di qualifica di IA anziché (o in aggiunta a) soglie basate su regole. Includi la selezione del percorso dinamico in cui l’IA determina se accelerare, gestire o de-assegnare la priorità a un account.

**Documentazione di Experience League:**

- [Panoramica sui percorsi di account](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [Nodi del percorso di account](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [Authoring di e-mail B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [Canale SMS in AJO B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [Assistente AI per l’authoring delle e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### Fase 4: Allineamento delle vendite e integrazione con il sistema CRM

**Funzioni dell&#39;applicazione:** [!DNL AJO B2B]: configurazione avviso vendite, informazioni sulle vendite CRM; [!DNL RT-CDP B2B]: configurazione destinazione account, Audience Activation account

Questa fase stabilisce il ponte tra marketing e vendite configurando le e-mail di avviso vendite, distribuendo gli Approfondimenti vendite CRM per la visibilità in-CRM e, facoltativamente, attivando i tipi di pubblico dell&#39;account per le destinazioni B2B ([!DNL LinkedIn], [!DNL Marketo], sistemi CRM).

#### Decisione: strategia di attivazione degli avvisi di vendita

Quando avvisare le vendite dello stato di gruppo di acquisto di un account?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Avvisi basati su Milestone | Notifica le vendite quando il gruppo di acquisto raggiunge target intermedi specifici (qualificato, completo, elevato coinvolgimento) | Notifiche discrete e chiare; previene l’eccesso di allerta; può perdere le tendenze di coinvolgimento graduale |
| Avvisi basati su soglie | Notifica le vendite quando il punteggio di coinvolgimento supera una soglia definita | Monitoraggio continuo; può attivare più avvisi quando i punteggi fluttuano vicino alla soglia |
| Avvisi di transizione di fase | Notifica le vendite quando il gruppo di acquisto passa a una nuova fase (ad esempio, da Considerazione a Decisione) | Si allinea alle fasi della pipeline; segnale più chiaro per l’azione di vendita; richiede definizioni di fasi ben definite |

#### Decisione: profondità dell’integrazione CRM

Quanto profondamente dovrebbero emergere i dati del gruppo di acquisto nel sistema CRM?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo avvisi di vendita (nessun componente CRM) | L&#39;organizzazione non utilizza [!DNL Salesforce] o [!DNL Dynamics] oppure l&#39;integrazione CRM non è fattibile | Minore sforzo di integrazione; le vendite ricevono notifiche e-mail ma nessun dashboard CRM; visibilità limitata |
| Dashboard Approfondimenti vendite CRM | L&#39;organizzazione utilizza [!DNL Salesforce] o [!DNL Dynamics] e desidera che lo stato del gruppo di acquisto sia visibile nel CRM | Richiede l’installazione del pacchetto CRM Sales Insights; fornisce informazioni approfondite a livello di account; consigliato per la maggior parte delle implementazioni |
| Sincronizzazione completa del sistema CRM bidirezionale | Le fasi del gruppo di acquisto e i punteggi vengono riscritti su oggetti CRM, influenzando il flusso di lavoro e il reporting CRM | Massima complessità di integrazione; abilita il reporting della pipeline nativo per il sistema CRM; richiede una configurazione CRM personalizzata |

**Navigazione interfaccia utente:** [!DNL AJO B2B Edition] > Amministrazione > Configurazione avviso vendite

**Navigazione interfaccia utente:** [!DNL AJO B2B Edition] > Amministrazione > Informazioni di vendita CRM > Configura

**Dettagli configurazione chiave:**

- Configurare i modelli e-mail per gli avvisi di vendita: include lo stato del gruppo di acquisto, gli utenti tipo coinvolti, il punteggio di coinvolgimento e le azioni successive consigliate
- Definire le regole di instradamento degli avvisi: quali rappresentanti o team di vendita ricevono gli avvisi in base alla proprietà dell’account, al territorio o all’interesse della soluzione
- Installa e configura CRM Sales Insights per [!DNL Salesforce] o [!DNL Dynamics 365]
- Mappa i dati del gruppo di acquisto su oggetti CRM in modo che le vendite possano visualizzare la composizione, il coinvolgimento e l’avanzamento del percorso di acquisto nel flusso di lavoro CRM
- Facoltativamente, configura le connessioni di destinazione dell&#39;account per attivare il pubblico dell&#39;account in [!DNL LinkedIn] (per pubblicità ABM), [!DNL Marketo Engage] (per follow-up a livello di lead) o altre destinazioni B2B

**Documentazione di Experience League:**

- [E-mail di avviso vendite](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [Approfondimenti vendite CRM](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)
- [Panoramica sulle destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [LinkedIn - Destinazione tipi di pubblico corrispondenti](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)

### Fase 5: Reporting e ottimizzazione

**Funzioni applicazione:** [!DNL AJO B2B]: dashboard di Analytics B2B

Questa fase stabilisce il framework di reporting e analisi per misurare le prestazioni del percorso di acquisto, l’efficacia del gruppo di account e l’impatto sulla pipeline. [!DNL AJO B2B Edition] fornisce dashboard di analisi incorporati; [!DNL CJA B2B Edition] (se concesso in licenza) estende l&#39;analisi con informazioni più approfondite a livello di account cross-channel.

#### Decisione: approccio alla comunicazione

Quali strumenti di analisi devono essere configurati per il monitoraggio continuo delle prestazioni?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo dashboard [!DNL AJO B2B] | Le dashboard incorporate di [!DNL AJO B2B Edition] sono sufficienti per l&#39;acquisto di metriche di percorso e gruppo | Configurazione più rapida; riguarda le metriche B2B di base; limitata capacità di analisi personalizzata |
| [!DNL AJO B2B] dashboard + [!DNL CJA B2B Edition] | L’organizzazione necessita di analisi più approfondite su più canali, analisi dei gruppi di acquisto, correlazione delle opportunità e attribuzione personalizzata | Richiede licenza [!DNL CJA B2B Edition]; più completo; supporta l&#39;analisi a forma libera a livello di account |
| [!DNL AJO B2B] dashboard + rapporti CRM | L’organizzazione preferisce centralizzare il reporting delle pipeline nel sistema di gestione delle relazioni con i clienti insieme all’acquisto di metriche di gruppo | Richiede lo sviluppo di dashboard CRM; combina metriche di marketing e vendite in un&#39;unica posizione; limitato alle funzionalità di reporting CRM |

**Navigazione interfaccia utente:** [!DNL AJO B2B Edition] > Dashboard > Panoramica coinvolgimento / Dashboard intelligente

**Dettagli configurazione chiave:**

- Accedi al dashboard di coinvolgimento [!DNL AJO B2B] per monitorare i punteggi di coinvolgimento del gruppo di acquisto, i tassi di completezza e la distribuzione della fase
- Accedi a Intelligent Dashboard per ottenere informazioni basate sull’intelligenza artificiale sulla preparazione dell’account e sulla qualità della pipeline
- Se utilizzi [!DNL CJA B2B Edition]: configura una connessione CJA basata sull&#39;account, inclusi [!DNL AJO B2B] set di dati, imposta una visualizzazione dati B2B con i contenitori Gruppo acquisti e Account e crea un&#39;analisi dell&#39;area di lavoro per la progressione del gruppo acquisti, la correlazione delle opportunità e l&#39;attribuzione
- Definire la frequenza di reporting: valutazioni settimanali delle prestazioni dei gruppi di acquisto, analisi di impatto della pipeline mensile, ottimizzazione del programma trimestrale
- Creare annotazioni per eventi significativi (avvii di campagne, aggiornamenti dei contenuti, modifiche al modello di punteggio) per correlarli alle tendenze delle prestazioni

**Documentazione di Experience League:**

- [Dashboard di analisi B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [Dashboard di coinvolgimento](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [Dashboard intelligente](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [Panoramica di CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

## Considerazioni sull’implementazione

Le sezioni seguenti descrivono i guardrail, le insidie comuni, le best practice e le decisioni di compromesso da tenere presenti durante l’implementazione.

### Guardrail e limiti

- [!DNL AJO B2B Edition] limiti di percorso dell&#39;account, inclusi il numero massimo di percorsi simultanei e di account al percorso, segui i guardrail di prodotto [!DNL AJO B2B Edition]: [guardrail B2B di AJO](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [!DNL RT-CDP B2B Edition] supporta fino a 50 classi di schema B2B e segue i guardrail standard di profilo e segmentazione: [guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- La valutazione del pubblico dell&#39;account funziona su pianificazioni batch; gli aggiornamenti del pubblico dell&#39;account in tempo reale non sono supportati per tutti i tipi di segmento - [Guardrail di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- L&#39;acquisizione del connettore di origine B2B ha intervalli di pianificazione minimi (in genere 15 minuti per [!DNL Marketo], che variano per le origini CRM) — [Guardrail di acquisizione](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- Le superfici del canale e-mail sono limitate a 10 per tipo di canale per sandbox — [guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

### Insidie comuni

- **Se si definiscono troppi ruoli per gruppo di acquisto:** Se si specificano troppi ruoli (ad esempio, se si richiedono 8-10 utenti tipo distinti), risulta quasi impossibile per i gruppi di acquisto raggiungere le soglie di completezza. Inizia con 3-5 ruoli essenziali ed espandi con la maturazione del modello.
- **Impostazione delle soglie di punteggio di coinvolgimento troppo alte o troppo basse:** Se le soglie sono troppo alte, nessun gruppo di acquisto è idoneo e la pipeline è affamata. Se troppo bassi, gli account non qualificati inondano le vendite. Inizia con l’analisi dei dati storici (se disponibile) e ripeti in base al feedback sulle vendite.
- **Ignorare la qualità della risoluzione da persona a account:** Se le persone non sono collegate correttamente agli account, i gruppi di acquisto avranno membri mancanti anche quando vengono coinvolte le persone giuste. Investire nella qualità della risoluzione delle identità prima di avviare percorsi di gruppi di acquisto.
- **Contatti di messaggistica in eccesso in più gruppi di acquisto:** Un singolo contatto può avere ruoli in più gruppi di acquisto (ad esempio, un CTO che è un valutatore tecnico per gli acquisti di CRM e Data Platform). Senza la gestione della frequenza, questa persona riceve e-mail da ogni percorso attivo. Implementare regole di frequenza tra percorsi.
- **Negligenza dell&#39;abilitazione alle vendite:** i team di vendita devono comprendere come interpretare i dati del gruppo di acquisto, i punteggi di coinvolgimento e gli avvisi di vendita. Senza formazione e adozione, il passaggio dal marketing alla vendita non riesce indipendentemente dalla qualità dei dati.
- **Trattamento dei percorsi di account come percorsi di persone:** I percorsi di account operano a livello di account, inviando e-mail a persone all&#39;interno dei gruppi di acquisto dell&#39;account. La progettazione del percorso deve tenere conto del fatto che più persone ricevono messaggi per ogni esecuzione del nodo dell&#39;account, che è fondamentalmente diversa dai [!DNL AJO] percorsi a livello di persona.

### Best practice

- **Iniziare con un interesse per la soluzione ed espandere**: verificare che il modello funzioni per un&#39;operazione di acquisto prima di passare a più interessi per la soluzione. Questo consente al team di perfezionare modelli di ruolo, modelli di punteggio e contenuti prima di aggiungere complessità.
- **Allinea i ruoli del gruppo di acquisto al processo di vendita CRM**: consente di mappare i ruoli del gruppo di acquisto agli utenti tipo già riconosciuti dal team di vendita. Usa la stessa lingua (buyer economico, campione, ecc.) quindi il passaggio è intuitivo.
- **Implementa un ciclo di feedback con le vendite**: raccogli regolarmente il feedback delle vendite sulla qualità degli account qualificati per il marketing. Utilizza questo feedback per regolare le soglie di punteggio di coinvolgimento e i criteri di qualifica del ruolo.
- **Progetta i contenuti per i ruoli, non solo per le fasi**. Diversi ruoli dei gruppi di acquisto richiedono contenuti diversi: i dirigenti desiderano un ritorno sull&#39;investimento e un impatto strategico, i valutatori tecnici desiderano l&#39;architettura e i dettagli di integrazione, gli utenti finali desiderano dimostrazioni di facile utilizzo. Mappare le risorse di contenuto ai ruoli per un’alimentazione più efficace.
- **Imposta CRM Sales Insights in anticipo** — Non attendere che l&#39;intero percorso sia attivo per distribuire la visibilità CRM. I team di vendita devono vedere i dati dei gruppi di acquisto formarsi in anticipo per fornire feedback sulla precisione dei ruoli e sul targeting degli account.
- **Utilizzare i passaggi di attesa in modo strategico** — I cicli di acquisto B2B sono lunghi. I passaggi di attesa del percorso dell’account devono riflettere questa realtà (intervalli di 5-14 giorni tra i contatti) anziché l’urgenza in stile consumer (1-3 giorni).
- **Monitora la velocità di coinvolgimento, non solo il punteggio di coinvolgimento**. Un gruppo di acquisto che passa da un punteggio di 20 a 80 in due settimane segnala un intento più forte di uno che raggiunge 80 in sei mesi. Configura il punteggio e la qualifica per tenere conto della velocità.

### Decisioni di compromesso

I seguenti compromessi devono essere valutati in base alle esigenze specifiche della tua organizzazione.

#### Completezza del gruppo di acquisto rispetto al volume della pipeline

L’obbligo di compilare tutti i ruoli prima di qualificare un gruppo di acquisto massimizza la qualità della pipeline, ma può limitare notevolmente il volume di account qualificati, in particolare per i nuovi prodotti o mercati in cui il database dell’organizzazione ha una copertura limitata.

- **Soglia di completezza più elevata favorisce:** qualità pipeline; le vendite ricevono gruppi di acquisto completamente formati; percentuali di vincita più elevate per account
- **Soglia di completezza inferiore favorisce:** volume pipeline; più account raggiungono le vendite; copertura più ampia; volume più elevato ma qualità potenzialmente inferiore
- **Consiglio:** inizia con una soglia moderata (60-70% di copertura dei ruoli) e regola in base ai dati del tasso di vincita effettivo. Per i mercati consolidati con una buona copertura dei dati, aumentare fino all&#39;80%+. Per i nuovi mercati, accetta inizialmente il 50-60% e utilizza campagne di completezza del gruppo di acquisto per colmare le lacune.

#### Granularità del punteggio rispetto alla semplicità operativa

I modelli di punteggio altamente granulari (con decine di tipi di attività, ponderazione dell’attualità e punteggio specifico per il ruolo) forniscono segnali di qualifica più precisi, ma sono più difficili da mantenere, spiegare e risolvere i problemi.

- **Maggiore granularità favorisce:** precisione della qualifica; differenziazione sfumata tra gli account; migliore allineamento con processi di acquisto complessi
- **Minore granularità favorisce:** semplicità operativa; facilità di manutenzione e spiegazione alle vendite; implementazione più rapida; meno casi edge
- **Consiglio:** inizia con un modello di punteggio semplice (10-15 tipi di attività, valori di punti uniformi) e aggiungi complessità solo quando il modello semplice non riesce a differenziare la qualità dell&#39;account. Documentare accuratamente il modello di punteggio per l’allineamento delle vendite.

#### Percorso singolo e più percorsi specializzati

Un percorso di account unico e completo che gestisce tutte le fasi e gli interessi delle soluzioni in un’unica area di lavoro offre un controllo unificato ma può diventare ingombrante. Più percorsi specializzati (uno per fase o interesse per la soluzione) sono più semplici da coordinare singolarmente.

- **Un singolo percorso favorisce:** visualizzazione olistica; assicura tempi e messaggi coerenti; è più semplice monitorare; un&#39;unica posizione per tutta la logica
- **Più percorsi favoriscono:** modularità; è più facile aggiornare una fase senza influire sugli altri; i diversi team possono possedere percorsi diversi; progettazione di aree di lavoro più pulite
- **Consiglio:** Per l&#39;opzione A, è appropriato un solo percorso. Per le opzioni B e C, utilizza un percorso di &quot;orchestrazione&quot; principale che indirizza gli account a percorsi secondari specializzati per interesse della soluzione o fase di acquisto.

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sulle applicazioni e funzionalità a cui si fa riferimento in questa guida.

### [!DNL AJO B2B Edition]

- [Pagina principale della documentazione di AJO B2B edition](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [Panoramica sui gruppi di acquisto](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [Interessi soluzione](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Modelli di ruolo](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [Creare gruppi di acquisto](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)
- [Fasi del gruppo di acquisto](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Panoramica sui percorsi di account](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [Nodi del percorso di account](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [E-mail di avviso vendite](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [Approfondimenti vendite CRM](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)

### E-mail e contenuto B2B

- [Authoring di e-mail B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [Authoring di SMS in AJO B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [Assistente AI per l’authoring delle e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### Analisi e dashboard B2B

- [Dashboard dei gruppi di acquisto](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [Dashboard di coinvolgimento](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [Dashboard intelligente](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [Panoramica di CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### [!DNL RT-CDP B2B Edition]

- [Panoramica di RT-CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [Schemi B2B in Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Pubblico dell’account](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [Connettore sorgente Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)

### Data Foundation

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica sulle origini](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)

### Configurazione dei canali

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configurare il canale SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### Governance dei dati e privacy

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### Destinazioni

- [Panoramica sulle destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Catalogo delle destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [LinkedIn - Destinazione tipi di pubblico corrispondenti](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)

### Guardrail

- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Guardrail di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [Guardrail di acquisizione](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

### Tutorial e guida introduttiva

- [Guida introduttiva di AJO B2B edition](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [Tutorial su B2B edition per RT-CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-tutorial)
