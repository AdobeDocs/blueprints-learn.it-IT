---
title: Customer Analytics e Insight Generation
description: Scopri come creare aree di lavoro di analisi cross-channel, metriche calcolate e dashboard per l’analisi del comportamento e delle prestazioni.
solution: Customer Journey Analytics, Experience Platform
exl-id: 235a4eb0-91ae-4030-b90e-7eda08c67ae1
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '8947'
ht-degree: 1%

---

# Analisi dei clienti e generazione di insight

Questa guida fornisce un riferimento completo all’implementazione per l’analisi dei clienti e la generazione di insight. Descrive come connettere i set di dati [!DNL Adobe Experience Platform] a [!DNL Customer Journey Analytics], configurare le visualizzazioni dati, creare aree di lavoro per l&#39;analisi freeform, creare metriche calcolate, pubblicare dashboard e scorecard per dispositivi mobili e, facoltativamente, ripubblicare i tipi di pubblico definiti da CJA in [!DNL Adobe Experience Platform] per l&#39;attivazione.

È progettato per gli architetti di soluzioni, i tecnici di marketing e i tecnici dell’implementazione che devono comprendere tutti i percorsi di implementazione praticabili, i compromessi tra di essi e le decisioni di configurazione necessarie in ogni fase.

A differenza degli altri modelli della tassonomia che si concentrano sull’attivazione e sul coinvolgimento (invio di messaggi, personalizzazione dei contenuti, attivazione di tipi di pubblico), questo modello si concentra sulla comprensione, l’analisi del comportamento dei clienti, la misurazione delle prestazioni delle campagne, l’identificazione delle tendenze e la generazione di informazioni utili per le decisioni su strategie e ottimizzazione. È il modello e le coppie più comunemente composte con quasi ogni pattern di attivazione o personalizzazione.

## Panoramica del caso d’uso

Le organizzazioni devono comprendere il comportamento dei clienti nei diversi canali, il funzionamento delle campagne, dove i clienti abbandonano i percorsi, quali contenuti risuonano e come diversi segmenti vengono mantenuti nel tempo. La generazione di analisi dei clienti e insight soddisfa questa esigenza collegando i dati multicanale avanzati di [!DNL Adobe Experience Platform] a [!DNL Customer Journey Analytics], dove gli analisti possono creare aree di lavoro a forma libera, metriche personalizzate, configurare modelli di attribuzione e pubblicare dashboard per l&#39;utilizzo da parte delle parti interessate.

Il modello è destinato a più tipi di pubblico: analisti di marketing che necessitano di analisi esplorative approfondite, manager di campagne che necessitano di dashboard delle prestazioni, manager di prodotto che necessitano di informazioni approfondite sul coinvolgimento e la fidelizzazione e dirigenti che necessitano di scorecard KPI immediate. L’approccio di implementazione varia in base all’obiettivo analitico principale: misurazione delle prestazioni della campagna, analisi dei percorsi cross-channel, attivazione del pubblico basata sull’analisi o insights guidati sui prodotti.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

**Migliorare analisi e reporting**

Migliora le funzionalità di reporting per informazioni di marketing più veloci e fruibili tramite dashboard unificate e strumenti self-service.

- **KPI:** efficienza, produttività

Per ulteriori informazioni su questo obiettivo aziendale, consulta [Migliorare Analytics e reporting](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md).

**Abilitare il processo decisionale basato sui dati**

Fornisci ai team analisi self-service, informazioni sui clienti in tempo reale e previsioni basate sull’intelligenza artificiale come guida per la strategia.

- **KPI:** efficienza, produttività

Per ulteriori informazioni su questo obiettivo aziendale, consulta [Abilita processo decisionale basato sui dati](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md).

**Migliora attribuzione marketing**

Misura accuratamente l’impatto di punti di contatto, canali e campagne di marketing sui risultati di conversione e di ricavo.

- **KPI:** efficienza, ricavi incrementali

Per ulteriori informazioni su questo obiettivo aziendale, consulta [Migliorare l&#39;attribuzione marketing](/help/blueprints/business-objectives/analytics-insights/improve-marketing-attribution.md).

**Ottimizzare le spese di marketing e il ROI**

Ottimizza l’allocazione del budget di marketing comprendendo quali canali e campagne generano il massimo ritorno.

- **KPI:** efficienza, ricavi incrementali

Per ulteriori informazioni su questo obiettivo aziendale, consulta [Ottimizzare le spese di marketing e il ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md).

## Esempi di casi d’uso tattici

Di seguito sono riportati alcuni esempi di casi di utilizzo tattici che è possibile implementare con questo modello.

- Dashboard delle prestazioni della campagna: metriche di consegna, tassi di coinvolgimento, conversione e attribuzione dei ricavi per e-mail, SMS, push e campagne multimediali a pagamento
- Analisi dell’abbandono del percorso di clienti: identifica dove i clienti abbandonano nei funnel di acquisto, registrazione o onboarding
- Analisi della fidelizzazione delle coorti: misura il livello di fidelizzazione delle diverse coorti di acquisizione nel corso di settimane, mesi e trimestri
- Modellazione di attribuzione dei canali: confronta l’attribuzione di primo contatto, ultimo contatto, lineare e decadimento nel tempo per capire quali canali favoriscono le conversioni
- Analisi delle prestazioni dei contenuti: identificazione dei contenuti più rilevanti per segmento, canale e fase del ciclo di vita
- Analisi dell’utilizzo e dell’adozione dei prodotti: monitoraggio dell’adozione delle funzioni, della frequenza di coinvolgimento e delle tendenze di crescita degli utenti
- Analisi della fase del ciclo di vita del cliente: segmentare e analizzare i clienti per fase del ciclo di vita (nuova, attiva, a rischio, scaduta)
- Dashboard di ottimizzazione del marketing mix: confronto tra l&#39;investimento dei canali e il contributo ai ricavi
- Reporting e valutazione del coinvolgimento cross-channel: creazione di punteggi di coinvolgimento compositi dalle interazioni web, app, e-mail e campagne

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare il successo di questo modello di caso d’uso.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Efficienza | Riduzione dei tempi di insight e delle attività manuali di reporting | Tracciare il tempo impiegato dagli analisti per creare rapporti prima e dopo l’implementazione di CJA |
| Produttività | Numero di analisi self-service create dagli utenti aziendali | Monitorare la creazione di progetti Workspace e l’utilizzo del dashboard |
| Reddito Incrementale | Ricavi attribuiti a decisioni di ottimizzazione basate su informazioni | Misura l’incremento dei ricavi dalle campagne ottimizzate in base all’analisi CJA |
| Tassi di conversione | Tassi di completamento dei funnel tra i principali percorsi di clienti | Tracciare i tassi di fallout a ogni passaggio del percorso utilizzando la visualizzazione Abbandono di CJA |
| Coinvolgimento | Profondità e frequenza dell’interazione del cliente tra i canali | Creare metriche calcolate per il punteggio di coinvolgimento in CJA |
| Conservazione | Tassi di restituzione dei clienti in periodi di tempo definiti | Utilizzare l’analisi per coorte con CJA per misurare le curve di fidelizzazione |

## Schema del caso d’uso

**Analisi dei clienti e generazione insight**

Crea aree di lavoro di analisi cross-channel, metriche calcolate e dashboard per comprendere il comportamento dei clienti e le prestazioni della campagna.

**Catena di funzioni:** Connessione dati > Configurazione visualizzazione dati > Analisi Workspace > Creazione di metriche calcolate > Pubblicazione dashboard

Consulta la sezione [Opzioni di implementazione](#implementation-options) per informazioni sulla composizione.

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Customer Journey Analytics] (CJA)** — Connessioni, visualizzazioni dati, analisi dell&#39;area di lavoro, analisi guidata, metriche calcolate, dashboard, pubblicazione di tipi di pubblico e analisi dei contenuti
- **[!DNL Adobe Experience Platform] (AEP)** — Data lake, set di dati, schemi XDM, dati di profilo ed eventi che alimentano le connessioni CJA

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve essere al suo posto | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Presunto sul posto | È stato eseguito il provisioning del profilo di prodotto CJA con la creazione di un’area di lavoro e le autorizzazioni di accesso alla visualizzazione dati. Set di dati di AEP accessibili alla connessione CJA. Utenti assegnati ai ruoli CJA appropriati. | [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/it/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Obbligatorio | Gli schemi e i set di dati XDM che verranno collegati a CJA devono esistere in AEP. La progettazione degli schemi influisce direttamente sulle dimensioni e sulle metriche disponibili nelle visualizzazioni dati di CJA. Gli schemi evento richiedono campi timestamp; gli schemi di ricerca richiedono campi chiave. | [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home) |
| Origini dati e raccolta | Obbligatorio | I dati devono fluire nei set di dati di AEP: eventi web tramite Web SDK, eventi app tramite Mobile SDK, eventi campagna AJO, dati CRM tramite i connettori di origine. La ricchezza delle analisi dipende dall’ampiezza dei dati raccolti. | [Panoramica origini](https://experienceleague.adobe.com/it/docs/experience-platform/sources/home) |
| Configurazione identità e profilo | Obbligatorio | La configurazione dell’ID della persona nella connessione CJA determina il modo in cui gli eventi vengono uniti nei diversi set di dati. L’unione delle identità tra dispositivi in AEP migliora la capacità di CJA di creare percorsi completi per i clienti. Lo spazio dei nomi dell’identità deve essere configurato per il campo ID persona. | [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home) |
| Definizione e segmentazione del pubblico | Non applicabile | CJA crea i propri filtri e tipi di pubblico all’interno del contesto di analisi. I tipi di pubblico RT-CDP non sono un prerequisito, anche se CJA può pubblicare di nuovo i tipi di pubblico in AEP tramite la pubblicazione dei tipi di pubblico (opzione C). | [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Consigliato | Gli attributi calcolati di AEP possono arricchire i set di dati connessi a CJA, fornendo dimensioni e metriche aggiuntive per l’analisi (ad esempio, conteggio degli acquisti per tutto il ciclo di vita, giorni dall’ultima attività). Queste aggregazioni a livello di profilo diventano disponibili come dimensioni nelle visualizzazioni dati di CJA. | [Panoramica attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Consigliato | I criteri di conservazione dei set di dati influiscono sui dati storici disponibili in CJA. La conservazione a lungo termine è in genere desiderata per le analisi per consentire confronti su base annua e analisi delle tendenze a lungo termine. Configura i TTL dei set di dati per garantire una profondità storica adeguata. | [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/it/docs/experience-platform/data-lifecycle/home) |
| Etichettatura e applicazione dell’utilizzo dati | Consigliato | Le etichette di governance sui campi sensibili possono limitare ciò che viene visualizzato nelle visualizzazioni dati di CJA. Se nella connessione CJA sono inclusi dati PII o sensibili, le etichette di governance dei dati garantiscono un accesso conforme e impediscono l’esposizione non autorizzata nelle dashboard condivise. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home) |
| Monitoraggio e osservabilità | Consigliato | È necessario monitorare lo stato e l’aggiornamento dei dati della connessione CJA. Configura gli avvisi per gli errori del flusso di dati di origine e i problemi di acquisizione per garantire l’affidabilità e l’attualità del CJA di inserimento dei dati. | [Panoramica di Observability Insights](https://experienceleague.adobe.com/it/docs/experience-platform/observability/home) |
| Reporting e analisi | Incluso | Questa è l’implementazione per reporting e analisi. Quando un piano di riferimento per un altro modello include S5, utilizza questo piano di generazione di analisi dei clienti e insight per l’implementazione di analisi. | [Panoramica di CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-overview/cja-overview) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Customer Journey Analytics] (CJA)

Nella tabella seguente sono elencate le funzioni dell&#39;applicazione CJA utilizzate in questo modello.

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Connessione dati | Fase 1: Connessione dati | Associa i set di dati di AEP a una connessione CJA per l’analisi cross-channel, configurando i tipi di set di dati e l’ID persona per l’unione di set di dati diversi |
| Configurazione visualizzazione dati | Fase 2: configurazione della visualizzazione dati | Definisci dimensioni, metriche, modelli di attribuzione, impostazioni di persistenza, parametri di sessione e campi derivati che modellano la prospettiva analitica. |
| Analisi Workspace | Fase 3: analisi e creazione di metriche | Creare progetti di analisi a forma libera con tabelle, visualizzazioni, filtri, annotazioni e raggruppamenti delle dimensioni (opzioni A, B, C) |
| Analisi guidata | Fase 3: analisi e creazione di metriche | Utilizzare flussi di lavoro guidati strutturati per funnel, tendenze, fidelizzazione, crescita degli utenti e analisi della frequenza di coinvolgimento (opzione D) |
| Creazione di metriche calcolate | Fase 3: analisi e creazione di metriche | Definisci le metriche calcolate utilizzando formule, filtri e funzioni per KPI riutilizzabili come tasso di conversione, punteggio di coinvolgimento e ricavi per visita |
| Pubblicazione di dashboard e scorecard | Fase 4: pubblicazione del dashboard | Creare e condividere dashboard interattivi e scorecard per dispositivi mobili per la generazione di rapporti con le parti interessate |
| Pubblicazione dei tipi di pubblico | Fase 5: Pubblicazione dei tipi di pubblico (solo opzione C) | Pubblicare tipi di pubblico definiti da CJA nuovamente su AEP Real-Time Customer Profile per l’attivazione a valle |
| Content Analytics | Fase 3: analisi e creazione di metriche | Analizzare le tendenze delle prestazioni dei contenuti, le anomalie e l’eccesso tra le proprietà digitali (quando l’analisi dei contenuti è l’elemento attivo) |

### [!DNL Adobe Experience Platform] (AEP)

Nella tabella seguente sono elencate le funzioni dell’applicazione AEP utilizzate in questo modello.

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Data lake e set di dati | Prerequisito (F2, F3) | Fornisci i set di dati di evento, profilo e ricerca di origine che alimentano la connessione CJA |
| Servizio identità | Prerequisito (F4) | Fornisci la configurazione dello spazio dei nomi delle identità per l’unione degli ID persona nei diversi set di dati nella connessione CJA |

## Prerequisiti

Prima di implementare questo modello di caso d’uso, è necessario soddisfare i seguenti prerequisiti.

- [ È stato eseguito il provisioning di ] prodotti CJA per l&#39;organizzazione
- [ ] i profili di prodotto CJA sono configurati con l&#39;accesso utente appropriato (creazione area di lavoro, accesso visualizzazione dati)
- [ La sandbox di AEP ] contiene i set di dati di destinazione con flusso di dati (eventi web, eventi app, dati campagna, record CRM)
- [ ] schemi XDM definiti per tutti i set di dati di origine con gruppi di campi appropriati
- [ Il campo ID persona ] è identificato e disponibile in modo coerente in tutti i set di dati che saranno connessi
- [ In AEP sono configurati ] spazi dei nomi di identità per l&#39;ID persona utilizzato nell&#39;unione di connessioni CJA
- [ ] I requisiti delle parti interessate sono documentati: quali KPI, quali tipi di pubblico utilizzeranno le dashboard, quale livello di dettaglio
- [ ] Per le scorecard per dispositivi mobili: le parti interessate hanno installato l&#39;app mobile per dashboard di [!DNL Adobe Analytics]
- [ ] per l&#39;opzione C (Pubblicazione del pubblico): il profilo cliente in tempo reale di AEP è abilitato nella sandbox di destinazione
- [ ] per l&#39;opzione D (analisi guidata): lo SKU di CJA include funzionalità di analisi guidata

## Opzioni di implementazione

Questa sezione descrive le opzioni di implementazione disponibili per questo modello di caso d’uso.

### Opzione A: analisi delle prestazioni della campagna

**Ideale per:** Misurazione e ottimizzazione dell&#39;efficacia di campagne e percorsi: dashboard delle campagne e-mail, analisi funnel di percorso, confronto delle prestazioni dei canali e reporting del ROI del marketing.

**Funzionamento:**

Questa opzione collega i set di dati di AJO campaign e percorsi a CJA, configura le visualizzazioni dati con le metriche di consegna e coinvolgimento (invii, consegne, aperture, clic, mancati recapiti, annullamenti dell’iscrizione), crea dashboard delle prestazioni delle campagne e pubblica le scorecard per le parti interessate al marketing. L’attenzione è posta sulla comprensione delle prestazioni delle campagne di marketing nei diversi canali e nel tempo.

La visualizzazione dati è configurata con dimensioni specifiche per la campagna (nome della campagna, nome del percorso, tipo di canale, variante del messaggio) e metriche di consegna. Le metriche calcolate vengono create per misure derivate come tasso di apertura, tasso di click-through, tasso di conversione e ricavi per messaggio. I dashboard presentano questi KPI con periodi di confronto per l’analisi delle tendenze.

**Considerazioni chiave:**

- Richiede set di dati evento campagna AJO e percorso in AEP
- I modelli di attribuzione devono essere allineati con la filosofia di misurazione della campagna dell’organizzazione
- Valuta di includere sia rapporti nativi di AJO (per metriche di consegna operative) che CJA (per l’impatto aziendale cross-channel)

**Vantaggi:**

- Progettato appositamente per la misurazione e l’ottimizzazione delle campagne
- Consente il confronto tra campagne diverse e l’analisi del mix di canali
- Le metriche calcolate forniscono definizioni KPI standardizzate in tutte le campagne
- Le scorecard per dispositivi mobili forniscono prestazioni a colpo d’occhio ai leader di marketing

**Limitazioni:**

- Limitato ai dati di campagna e percorso; non fornisce il contesto di percorso completo del cliente
- Non include analisi di percorsi di percorso, abbandono o coorte
- L’attribuzione ha come ambito i punti di contatto della campagna anziché l’intero percorso di clienti

**Experience League:**

- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Panoramica di Workspace](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/home)

### Opzione B: analisi dei percorsi di clienti

**Ideale per:** Comprendere i percorsi dei clienti cross-channel: analisi dell&#39;abbandono, analisi del percorso, conservazione per coorte, modellazione di attribuzione e analisi della fase del ciclo di vita in punti di contatto Web, app, e-mail, CRM e offline.

**Funzionamento:**

Questa opzione connette più set di dati di AEP (eventi web, eventi app, dati di gestione delle relazioni con i clienti, interazioni delle campagne, record transazionali) per creare una visualizzazione cross-channel unificata del percorso di clienti. La visualizzazione dati è configurata con dimensioni e metriche che si estendono su tutti i canali. Le visualizzazioni Flusso, Abbandono, Coorte e Attribuzione di CJA vengono utilizzate per analizzare il modo in cui i clienti passano da un percorso all’altro, dove abbandonano, come vengono mantenuti i diversi segmenti e quali canali meritano il merito per le conversioni.

Si tratta dell’opzione di analisi più completa, che offre ad insight una visione completa dell’esperienza del cliente. È anche il più complesso da implementare, richiede un’attenta configurazione dell’ID persona per l’unione di più set di dati e una progettazione accurata della visualizzazione dati per esporre le dimensioni e le metriche corrette.

**Considerazioni chiave:**

- Richiede un ID persona coerente in tutti i set di dati connessi per un’analisi cross-channel accurata
- La progettazione di schemi in AEP influisce direttamente sulla qualità e sulla profondità dell’analisi di CJA
- Più set di dati nella connessione significa analisi più ricche ma tempi di retrocompilazione più lunghi
- La modellazione dell’attribuzione richiede definizioni chiare degli eventi di conversione

**Vantaggi:**

- Visibilità completa del percorso clienti cross-channel
- Suite completa di visualizzazioni di CJA: flusso, abbandono, coorte, attribuzione, tabelle a forma libera
- Consente l’individuazione di informazioni invisibili nel reporting a canale singolo
- Supporta le domande analitiche complesse sul comportamento dei clienti e sul ciclo di vita

**Limitazioni:**

- Maggiore complessità di implementazione grazie a connessioni a più set di dati e unione tra canali
- Richiede una pianificazione più anticipata per la configurazione della visualizzazione dati e i campi derivati
- Il backfill per connessioni di set di dati multipli di grandi dimensioni può richiedere giorni
- La qualità dell’analisi dipende dalla completezza e dalla coerenza dei dati sottostanti

**Experience League:**

- [Panoramica delle connessioni](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-connections/overview)
- [Visualizzazione del flusso](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Visualizzazione Abbandono](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Tabella coorte](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Pannello Attribuzione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/panels/attribution)

### Opzione C: Analytics con pubblicazione di tipi di pubblico

**Ideale per:** attivazione basata su analisi: individua segmenti interessanti tramite analisi CJA, quindi pubblicali di nuovo in AEP per l&#39;attivazione tramite destinazioni RT-CDP, campagne AJO o percorsi AJO.

**Funzionamento:**

Questa opzione estende l’opzione A o l’opzione B con la pubblicazione di tipi di pubblico da CJA. Gli analisti creano segmenti in CJA utilizzando dati comportamentali cross-channel e la potenza analitica completa dei filtri CJA, quindi pubblicano tali tipi di pubblico in AEP Real-time Customer Profile per l’attivazione a valle. Questo colma il divario tra insight e azione: i segmenti scoperti durante l’analisi esplorativa diventano tipi di pubblico utilizzabili senza dover essere ricreati manualmente in AEP Segment Builder.

I tipi di pubblico pubblicati vengono visualizzati nel Portale dei tipi di pubblico di AEP con origine &quot;CJA&quot; e possono essere attivati su qualsiasi destinazione RT-CDP, utilizzati come target delle campagne in AJO o utilizzati come condizioni di ingresso del percorso.

**Considerazioni chiave:**

- Richiede che il profilo cliente in tempo reale di AEP sia abilitato nella sandbox di destinazione
- La connessione CJA deve avere un ID persona valido che viene risolto in uno spazio dei nomi di identità AEP
- I tipi di pubblico pubblicati vengono conteggiati per l’adesione ad AEP dell’organizzazione
- La frequenza di aggiornamento deve essere configurata in base ai requisiti di attivazione (una volta, ogni 4 ore, ogni giorno, ogni settimana)

**Vantaggi:**

- Chiude il loop tra analisi e attivazione
- Consente l’individuazione di segmenti di alto valore utilizzando i dati comportamentali cross-channel di CJA
- I tipi di pubblico definiti in CJA possono sfruttare dimensioni e filtri non disponibili in AEP Segment Builder
- Supporta il perfezionamento iterativo dei criteri di pubblico in base a informazioni analitiche

**Limitazioni:**

- Massimo 75 tipi di pubblico pubblicati per cliente CJA
- La valutazione iniziale del pubblico può richiedere fino a 24 ore per set di dati di grandi dimensioni
- I tipi di pubblico pubblicati da CJA non possono essere modificati in AEP — le modifiche devono essere apportate in CJA
- Richiede uno spazio dei nomi identità e una configurazione di profilo aggiuntivi oltre alle analisi di base

**Experience League:**

- [Panoramica di Audiences](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Creare e pubblicare tipi di pubblico](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/audiences/publish)

### Opzione D: analisi guidata per team di prodotto

**Ideale per:** approfondimenti sull&#39;esperienza del prodotto: adozione delle funzionalità, tendenze del coinvolgimento degli utenti, analisi della fidelizzazione, conversione funnel e analisi dell&#39;impatto sulla versione utilizzando i flussi di lavoro di analisi guidata di CJA senza richiedere la configurazione di progetti Workspace a forma libera complessi.

**Funzionamento:**

Questa opzione utilizza l’analisi guidata di CJA per la generazione di insight strutturata e basata su modelli. L’analisi guidata fornisce tipi di analisi predefiniti (funnel, tendenze, fidelizzazione, crescita degli utenti, frequenza del coinvolgimento, impatto sul rilascio, primo utilizzo e timeline) che guidano gli analisti attraverso un flusso di lavoro strutturato per rispondere a domande specifiche su prodotti ed esperienze. È ideale per product manager e analisti che necessitano di informazioni rapide e mirate senza creare progetti a forma libera da zero.

L’implementazione collega i set di dati di AEP a CJA, configura una visualizzazione dati con dimensioni e metriche a livello di evento, quindi utilizza flussi di lavoro di analisi guidati per generare insights. I risultati possono essere salvati come pannelli nei progetti Workspace per ulteriori personalizzazioni.

**Considerazioni chiave:**

- L&#39;analisi guidata richiede l&#39;adesione ai prodotti CJA che include funzionalità di analisi guidata
- Ideale per l’analisi di prodotti ed esperienze anziché per la misurazione delle prestazioni delle campagne
- Fornisce flussi di lavoro strutturati più accessibili agli utenti non analisti
- Può essere combinata con l’analisi freeform di Workspace per un’esplorazione più approfondita

**Vantaggi:**

- Riduzione della barriera all&#39;ingresso: i flussi di lavoro strutturati guidano gli utenti nell&#39;analisi
- Progettato appositamente per rispondere alle domande sull&#39;esperienza del prodotto (funnel, conservazione, crescita, impatto)
- Tempi di insight più rapidi per le domande analitiche più comuni
- Le analisi salvate possono essere incorporate nei progetti Workspace insieme all’analisi a forma libera

**Limitazioni:**

- Meno flessibile rispetto all’analisi a forma libera di Workspace
- Limitato ai tipi di analisi predefiniti (funnel, tendenze, conservazione, crescita, frequenza, impatto, timeline)
- Il confronto dei segmenti supporta fino a 3 segmenti simultaneamente
- L’analisi di funnel supporta un massimo di 15 passaggi

**Experience League:**

- [Panoramica dell’analisi guidata](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/overview)
- [Vista funnel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Vista Mantenimento](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

### Confronto delle opzioni

La tabella seguente confronta le opzioni di implementazione disponibili.

| Criteri | Opzione A: Prestazioni della campagna | Opzione B: percorso del cliente | Opzione C: Analytics + attivazione | Opzione D: analisi guidata |
| --- | --- | --- | --- | --- |
| Ideale per | Misurazione e ottimizzazione delle campagne | Comprensione del percorso cross-channel | Attivazione del pubblico basata su Insight | Approfondimenti sull’esperienza del prodotto |
| Complessi | Low-Medium | Alta | Alta | Bassa |
| Set di dati richiesti | Eventi campagna/percorso AJO | Set di dati multicanale multipli | Come A o B, più identità del profilo | Set di dati evento con interazioni di prodotto |
| Visualizzazioni chiave | Tabelle a forma libera, numeri di riepilogo, linee di tendenza | Flusso, abbandono, coorte, attribuzione | Come A o B, più pubblicazione di pubblico | Funnel, tendenze, conservazione, crescita |
| Funzionalità di attivazione | No (solo reporting) | No (solo reporting) | Sì (pubblica i tipi di pubblico in AEP) | No (solo reporting) |
| Pubblico richiesto | Analisti di marketing, manager di campagne | Analisti di dati, architetti di percorso | Analisti e team di attivazione | Responsabili di prodotto, analisti di crescita |
| Funzioni CJA utilizzate | Connessione, Visualizzazione dati, Workspace, Metriche calcolate, Dashboard | Connessione, Visualizzazione dati, Workspace, Metriche calcolate, Dashboard | Come A o B, più Pubblicazione dei tipi di pubblico | Connessione, Visualizzazione dati, Analisi guidata, Dashboard |
| Tempo per il primo insight | Giorni | Weeks | Weeks | Ore-Giorni |

### Scegli l’opzione giusta

Utilizza le indicazioni seguenti per selezionare l’opzione di implementazione più adatta alle tue esigenze.

- **Se il tuo obiettivo principale è la misurazione dell&#39;efficacia della campagna** e i dati della campagna AJO fluiscono in AEP, inizia con **L&#39;opzione A**. Offre il time-to-value più veloce per la generazione di rapporti sulle prestazioni di marketing.

- **Se hai bisogno di comprendere l&#39;intero percorso di clienti** nei punti di contatto Web, app, e-mail e offline e hai più set di dati con un ID persona coerente, scegli **Opzione B**. Fornisce le funzionalità di analisi più approfondite, ma richiede un investimento più iniziale nella configurazione della visualizzazione dati.

- **Se desideri agire in base alle informazioni** pubblicando nuovamente in AEP i segmenti individuati da CJA per l&#39;attivazione in RT-CDP o AJO, scegli **Opzione C**. Questa funzione estende l’opzione A o B con pubblicazione di tipi di pubblico e richiede la configurazione del profilo cliente in tempo reale di AEP.

- **Se il tuo team ha bisogno di informazioni rapide e strutturate sui prodotti** senza la complessità dei progetti Workspace a forma libera e il tuo SKU CJA include l&#39;analisi guidata, scegli **Opzione D**. È il percorso più veloce per rispondere a specifiche domande sull’esperienza del prodotto.

- **Molte organizzazioni implementano più opzioni**: Opzione A per i dashboard delle campagne del team di marketing, Opzione B per l&#39;analisi cross-channel del team di analisi e Opzione D per approfondimenti self-service del team di prodotto. Queste opzioni condividono la stessa connessione CJA e la stessa infrastruttura di visualizzazione dati.

## Fasi di implementazione

Questa sezione descrive le fasi di implementazione dettagliate per questo modello di caso d’uso.

### Fase 1: Connessione dati

**Funzione dell&#39;applicazione:** CJA: connessione dati

Questa fase configura una connessione CJA che associa uno o più set di dati di AEP a CJA per l’analisi. La connessione definisce quali set di dati fluiscono in CJA, come gli eventi vengono uniti tra i set di dati tramite l’ID persona e come vengono acquisiti i dati storici e in streaming. Questo è il collegamento fondamentale tra il data lake di AEP e CJA.

#### Punti decisionali

In questa fase devono essere prese le seguenti decisioni.

>[!NOTE]
>**Decisione: selezione sandbox AEP**
>
>Quale sandbox di AEP contiene i set di dati di origine?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Sandbox di produzione | Dati live dei clienti per reporting sulla produzione | Usa per dashboard di produzione e reporting per le parti interessate |
>| Sandbox di sviluppo | Test e iterazione prima dell’implementazione di produzione | Usa per la configurazione iniziale e la convalida prima della promozione in produzione |

>[!NOTE]
>**Decisione: selezione del set di dati e designazione del tipo**
>
>Quali set di dati di AEP devono essere inclusi nella connessione e quale tipo devono essere assegnati?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Set di dati evento | Dati comportamentali con marca temporale (interazioni web, eventi app, interazioni campagna, transazioni) | Richiede un campo timestamp; costituisce il nucleo della maggior parte delle analisi |
>| Ricercare set di dati | Dati di riferimento chiave-valore (catalogo dei prodotti, metadati delle campagne, posizioni dei negozi) | Unito ai dati evento tramite una chiave condivisa; viene utilizzato solo lo stato più recente |
>| Set di dati del profilo | Attributi a livello di persona (livello di fedeltà, valore del ciclo di vita, attributi di gestione delle relazioni con i clienti) | Fornire arricchimento a livello di persona; viene utilizzato solo lo stato più recente |

>[!NOTE]
>**Decisione: configurazione ID persona**
>
>Quale campo funge da ID persona per l’unione di più set di dati?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| ID CRM | L’organizzazione ha un identificatore CRM coerente tra i canali | Fornisce l’unione cross-channel più accurata per i clienti noti |
>| ECID (Experience Cloud ID) | Analizzare principalmente il comportamento anonimo di web/app | Con ambito dispositivo; non esegue l’unione tra dispositivi senza risoluzione delle identità |
>| E-mail (con hash) | L’e-mail è l’identificatore comune nei diversi set di dati | Funziona bene quando l’e-mail viene acquisita in modo coerente tra i punti di contatto |
>| Spazio dei nomi personalizzato | L’organizzazione utilizza un identificatore proprietario | Deve corrispondere a uno spazio dei nomi di identità AEP per la pubblicazione di tipi di pubblico (opzione C) |

>[!NOTE]
>**Decisione: intervallo di backfill**
>
>Quanti dati storici devono essere importati nella connessione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Tutti i dati esistenti | Profondità storica massima necessaria per confronti su base annua e tendenze a lungo termine | Il completamento della retrocompilazione per set di dati di grandi dimensioni (miliardi di record) potrebbe richiedere giorni |
>| Intervallo date personalizzato | È rilevante solo la cronologia recente, oppure l&#39;ottimizzazione dello storage è un problema | Limita la profondità storica disponibile per l&#39;analisi |
>| Nessuna retrocompilazione | È necessaria solo un’analisi lungimirante | Configurazione della connessione più rapida; nessun dato storico disponibile finché non arrivano nuovi dati |

>[!NOTE]
>**Decisione: abilitazione streaming**
>
>I nuovi dati dovrebbero fluire in CJA quasi in tempo reale?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Abilita streaming | È necessario un reporting quasi in tempo reale (dati disponibili entro circa 90 minuti dall’acquisizione di AEP) | Più comune per le connessioni di produzione; consente l’analisi tempestiva |
>| Solo batch | È sufficiente l&#39;aggiornamento periodico e non è necessario lo streaming | Configurazione più semplice; dati disponibili dopo l’elaborazione batch |

#### Configurare la connessione dati

**Navigazione interfaccia utente:** CJA > Connessioni > Crea nuova connessione

Dettagli configurazione chiave:

- Il nome e la descrizione della connessione devono seguire le convenzioni di denominazione organizzative
- Il numero medio di eventi giornalieri viene utilizzato per la pianificazione della capacità di CJA
- Tutti i set di dati in una singola connessione devono provenire dalla stessa sandbox di AEP
- I campi ID persona devono essere coerenti tra tutti i set di dati per ottenere un’unione accurata tra i set di dati
- Verifica che il campo ID persona esista e sia popolato in ogni set di dati prima di aggiungerlo alla connessione

**Documentazione di Experience League:**

- [Panoramica delle connessioni](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-connections/overview)
- [Creare o modificare una connessione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-connections/create-connection)
- [Gestire le connessioni](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-connections/manage-connections)
- [Guardrail CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-admin/guardrails)

### Fase 2: configurazione della visualizzazione dati

**Funzione applicazione:** CJA: configurazione visualizzazione dati

Questa fase configura una visualizzazione dati che definisce la modalità di visualizzazione dei dati di connessione nell’analisi. La visualizzazione dati determina quali campi dello schema vengono esposti come dimensioni e metriche, in che modo i valori vengono attribuiti e persistenti, come vengono definite le sessioni e quali campi derivati trasformano i dati non elaborati in componenti pronti per l’analisi. È possibile creare più visualizzazioni dati da una singola connessione per diverse prospettive analitiche.

#### Punti decisionali

In questa fase devono essere prese le seguenti decisioni.

>[!NOTE]
>**Decisione: denominazione contenitore**
>
>Quale terminologia utilizzare per la corrispondenza tra i contenitori e il dominio aziendale?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Predefinito (persona/sessione/evento) | La terminologia di analisi standard è compresa dal team | Per la maggior parte delle implementazioni |
>| Nomi personalizzati (ad esempio acquirente/visita/interazione) | La terminologia specifica del dominio di business migliora l’adozione da parte degli utenti | Aiuta le parti interessate non tecniche a comprendere l’ambito dell’analisi |
>| Nomi B2B (ad esempio account/coinvolgimento/punto di contatto) | Analisi B2B in cui l’analisi a livello di account è il punto focale | Allinea l’ambito del contenitore con i concetti di business B2B |

>[!NOTE]
>**Decisione: timeout sessione**
>
>Quanto tempo di inattività definisce un limite di sessione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| 30 minuti (impostazione predefinita) | Definizione della sessione standard di analisi web | Standard di settore; in linea con la maggior parte dei benchmark di analisi |
>| 15 minuti | Contenuto in forma breve o siti transazionali in cui gli utenti eseguono rapidamente le attività | Crea più sessioni; può acquisire meglio intenti utente distinti |
>| 60 minuti o più | Contenuti in formato lungo, interazioni B2B complesse o percorsi complessi | Meno sessioni; acquisisce la ricerca estesa come sessioni singole |
>| Personalizzato con nuovi eventi di sessione | Alcuni eventi (ad esempio il lancio dell’app, il click-through di una campagna) devono sempre avviare una nuova sessione | Fornisce limiti di sessione basati sulla logica di business |

>[!NOTE]
>**Decisione: impostazioni predefinite modello di attribuzione**
>
>Quale modello di attribuzione predefinito deve essere applicato alle metriche di conversione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Ultimo contatto (impostazione predefinita) | Il credito deve andare al punto di contatto più recente prima della conversione | Semplice e intuitivo; può sottovalutare i canali di consapevolezza |
>| Primo contatto | Informazioni sui canali che determinano la conoscenza e l’acquisizione iniziali | Utile per l’analisi di acquisizione; ignora i punti di contatto di apprendimento |
>| Lineare | Tutti i punti di contatto devono condividere lo stesso credito | Distribuzione equa; può diluire l’impatto dei punti di contatto chiave |
>| Decadimento nel tempo | I punti di contatto recenti dovrebbero ricevere più credito rispetto a quelli distanti | Saldi recency con contributo storico |
>| A forma di U | Il primo e l’ultimo punto di contatto meritano più credito | Buono per comprendere sia i canali di acquisizione che quelli di chiusura |
>| Algoritmico | Attribuzione basata sui dati utilizzando i modelli AI di CJA | Più accurato ma richiede un volume di dati di conversione sufficiente |

>[!NOTE]
>**Decisione: logica del campo derivata**
>
>Sono necessarie regole aziendali personalizzate per trasformare i dati non elaborati in dimensioni pronte per l’analisi?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Classificazione del canale di marketing (caso/quando) | I codici di tracciamento non elaborati devono essere classificati in gruppi di canali | Caso di utilizzo più comune di campo derivato; critico per l’analisi dei canali |
>| Bucketing dei valori | I valori continui devono essere raggruppati in intervalli (ad esempio, livelli di valore dell’ordine) | Semplifica l’analisi delle metriche continue |
>| Unione campi | È necessario combinare più campi sorgente in un’unica dimensione | Utile quando lo stesso concetto esiste in percorsi di schema diversi tra set di dati |
>| Estrazione basata su Regex | È necessario analizzare i valori strutturati (ad esempio, estrazione del tipo di campagna dal codice della campagna) | Potente ma richiede un attento design del pattern regex |

#### Configurare la visualizzazione dati

**Navigazione interfaccia utente:** CJA > Visualizzazioni dati > Crea nuova visualizzazione dati

Dettagli configurazione chiave:

- Selezionare la connessione padre creata nella fase 1
- Configura il fuso orario e il tipo di calendario per soddisfare i requisiti di reporting
- Mappa i campi dello schema XDM sulle dimensioni con le impostazioni di persistenza (allocazione e scadenza) appropriate
- Mappa i campi dello schema XDM su metriche con impostazioni di formato (decimale, numero intero, valuta, percentuale, ora) e attribuzione
- Configura le regole di inclusione/esclusione sulle dimensioni per filtrare i valori irrilevanti
- Abilita la deduplicazione delle metriche dove necessario per evitare il doppio conteggio
- Creare campi derivati per la classificazione del canale di marketing, la suddivisione in blocchi di valori o l’unione di campi
- Massimo 5.000 dimensioni e 5.000 metriche per visualizzazione dati
- Massimo 100 campi derivati per visualizzazione dati

#### Dove le opzioni divergono

**Per l&#39;opzione A (analisi delle prestazioni della campagna):**

Mappa dimensioni specifiche della campagna: nome della campagna, nome del percorso, tipo di canale, variante del messaggio, riga dell’oggetto. Mappatura delle metriche di consegna: invii, consegne, aperture, clic, mancati recapiti, annullamenti dell’abbonamento. Configura l’attribuzione sulle metriche di conversione in base alla filosofia di misurazione della campagna.

**Per l&#39;opzione B (analisi percorso clienti):**

Mappare le dimensioni cross-channel: nome della pagina, schermata dell’app, canale, campagna, prodotto, tipo di contenuto. Mappa le metriche di coinvolgimento e conversione su tutti i canali. Configurare più modelli di attribuzione per l’analisi di confronto. Creazione di campi derivati per la classificazione del canale e l&#39;identificazione dello stadio del percorso.

**Per l&#39;opzione D (analisi guidata):**

Mappa dimensioni e metriche a livello di evento rilevanti per l’analisi dell’esperienza del prodotto: nome della funzione, azione dell’utente, tipo di coinvolgimento. Attenzione agli eventi che definiscono i passaggi di funnel, i criteri di conservazione e i segnali di crescita.

**Documentazione di Experience League:**

- [Panoramica delle visualizzazioni dati](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/data-views)
- [Creare o modificare una visualizzazione dati](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Panoramica delle impostazioni dei componenti](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Impostazioni persistenza](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Impostazioni di attribuzione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Impostazioni formato](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Deduplica delle metriche](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [Includi/escludi valori](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [Impostazioni di sessione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/session-settings)
- [Campi derivati](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/derived-fields)

### Fase 3: analisi e creazione di metriche

**Funzione dell&#39;applicazione:** CJA: Workspace Analysis, CJA: analisi guidata, CJA: creazione di metriche calcolate

Questa fase crea le aree di lavoro di analisi (progetti a forma libera o analisi guidata), le metriche calcolate per i KPI derivati, i filtri per l’analisi segmentata e le annotazioni per gli eventi chiave. Il valore analitico si realizza qui, creando tabelle, visualizzazioni e metriche che rispondono alle domande aziendali.

#### Punti decisionali

In questa fase devono essere prese le seguenti decisioni.

>[!NOTE]
>**Decisione: approccio di analisi**
>
>Questa analisi deve utilizzare progetti Workspace a forma libera o flussi di lavoro di analisi guidati?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Workspace a forma libera (opzioni A, B, C) | Analisi esplorativa approfondita, layout personalizzati, raggruppamenti complessi, visualizzazioni avanzate | Massima flessibilità; richiede abilità da analista; supporta tutti i tipi di visualizzazione |
>| Analisi guidata (opzione D) | Informazioni strutturate sui prodotti, risposte rapide a domande specifiche, utenti meno tecnici | Time-to-insight più rapido; limitato a tipi di analisi predefiniti; risparmio su Workspace per ulteriori personalizzazioni |
>| Entrambi | L’organizzazione ha bisogno sia di analisi approfondite che di informazioni strutturate rapide | Utilizza l’analisi guidata per le domande comuni; Workspace per un’esplorazione approfondita |

>[!NOTE]
>**Decisione: tipi di visualizzazione**
>
>Quali visualizzazioni comunicano meglio le informazioni per questo caso d’uso?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Tabella a forma libera | Esplorazione dettagliata dei dati con raggruppamenti delle dimensioni | Base della maggior parte delle analisi; supporta fino a 10 livelli di suddivisione |
>| Visualizzazione del flusso | Informazioni sul comportamento dei percorsi (flusso di pagina, transizioni dei canali) | Eccellente per l&#39;individuazione del percorso di percorso; può essere complesso con elevata cardinalità |
>| Visualizzazione Abbandono | Misurazione della conversione attraverso una sequenza definita di punti di contatto | Ideale per l’analisi funnel; mostra chiaramente il calo di utilizzo in ogni fase |
>| Tabella coorte | Analisi del mantenimento nel tempo per coorte di acquisizione | Mostra come i diversi gruppi mantengono un livello critico per l&#39;analisi del ciclo di vita |
>| Pannello Attribuzione | Confronto dei modelli di attribuzione per le metriche di conversione | Confronto di modelli affiancato; richiede una chiara definizione dell’evento di conversione |
>| Numero/modifica riepilogo | Visualizzazione dei KPI esecutivi con confronto su più periodi | Visualizzazione pulita e immediata delle metriche; ideale per le intestazioni delle dashboard |

>[!NOTE]
>**Decisione: formule metriche calcolate**
>
>Quali KPI aziendali richiedono metriche calcolate oltre alle metriche di visualizzazione dati di base?
>
>| Pattern di metrica | Esempio di formula | Quando utilizzare |
>| --- | --- | --- |
>| Rapporto / Tasso | Ordini/Visite | Tasso di conversione, tasso di click-through, tasso di mancato recapito |
>| Metrica filtrata | Ricavi (dove canale = &quot;e-mail&quot;) | Misure specifiche per canale o segmento |
>| Media per articolo | Ricavi/Ordini | Valore medio dell’ordine, ricavi per visita |
>| Formula composta | (Ricavi - Costi) / Ricavi | Percentuale margine, calcoli ROI |
>| Punteggio di coinvolgimento | Somma ponderata delle interazioni | Punteggio del coinvolgimento composito tra canali diversi |

#### Configurare analisi e metriche

**Navigazione interfaccia utente:**

- Workspace: CJA > Workspace > Progetti > Crea progetto > Progetto vuoto
- Analisi guidata: CJA > Home > Analisi guidata (oppure Workspace > Crea > Analisi guidata)
- Metriche calcolate: CJA > Componenti > Metriche calcolate > Crea
- Filtri: CJA > Componenti > Filtri > Crea filtro

Dettagli configurazione chiave:

- Selezionare la visualizzazione dati creata nella Fase 2 come visualizzazione dati del progetto
- Impostare intervalli di date e periodi di confronto appropriati per l&#39;analisi
- Creare tabelle a forma libera trascinando dimensioni nelle righe e metriche nelle colonne
- Aggiungi analisi dettagliate delle dimensioni per esplorare i dati a livelli più profondi (ad esempio, canale per campagna, pagina per prodotto)
- Creare filtri (segmenti) riutilizzabili per analisi specifiche per il pubblico (ambito a livello di persona, sessione o evento)
- Aggiungere annotazioni per contrassegnare eventi aziendali chiave (avvii di prodotti, campagne, incidenti)
- Imposta il formato metrico calcolato (decimale, percentuale, valuta, tempo) e la polarità (up è buono / up è cattivo)
- Condividere progetti Workspace con gli utenti di CJA quando si visualizzano o si modificano le autorizzazioni

#### Dove le opzioni divergono

**Per l&#39;opzione A (analisi delle prestazioni della campagna):**

Crea tabelle a forma libera con dimensioni della campagna suddivise per metriche di consegna e coinvolgimento. Crea metriche calcolate per tasso di apertura, tasso di click-through, tasso di conversione, ricavi per messaggio e ROI della campagna. Aggiungi visualizzazioni delle tendenze per monitorare le prestazioni delle campagne nel tempo. Confrontare le varianti di campagna con il confronto dei segmenti.

**Per l&#39;opzione B (analisi percorso clienti):**

Crea visualizzazioni di abbandono per identificare i punti di abbandono del percorso. Crea visualizzazioni di flusso per scoprire i pattern di navigazione tra i canali. Crea tabelle coorte per misurare la fidelizzazione per coorte di acquisizione. Configura il pannello Attribuzione per confrontare i modelli di attribuzione per le metriche di conversione. Creazione di metriche calcolate per tasso di completamento del percorso, punteggio di coinvolgimento cross-channel e conversione della fase del ciclo di vita.

**Per l&#39;opzione C (Analytics con pubblicazione del pubblico):**

Crea le aree di lavoro di analisi dall’opzione A o B, quindi identifica i segmenti di valore elevato o con prestazioni inferiori durante l’analisi. Crea filtri CJA che acquisiscono questi segmenti per la pubblicazione nella fase 5.

**Per l&#39;opzione D (analisi guidata):**

Seleziona il tipo di analisi guidata appropriato in base alla domanda aziendale. Configura eventi chiave, intervalli di date, metodi di conteggio e confronti tra segmenti. Salva le analisi completate come pannelli nei progetti Workspace per ulteriori personalizzazioni.

**Documentazione di Experience League:**

- [Panoramica di Workspace](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/home)
- [Creare un progetto](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Tabella a forma libera](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Visualizzazione del flusso](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Visualizzazione Abbandono](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Tabella coorte](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Pannello Attribuzione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Dimensioni di raggruppamento](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [Panoramica sui filtri](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Creare filtri](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Panoramica delle annotazioni](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/annotations/overview)
- [Panoramica delle metriche calcolate](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Creare metriche calcolate](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Funzioni metriche calcolate](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [Panoramica dell’analisi guidata](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/overview)
- [Vista funnel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Visualizzazione tendenze](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Vista Mantenimento](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [Visualizzazione crescita attiva](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [Visualizzazione frequenza di coinvolgimento](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [Vista impatto sulla versione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/impact/release)
- [Content Analytics](https://experienceleague.adobe.com/it/docs/analytics-platform/using/content-analytics/content-analytics)

### Fase 4: pubblicazione del dashboard

**Funzione applicazione:** CJA: pubblicazione dashboard e scorecard

Questa fase crea dashboard interattivi (progetti Workspace) e scorecard per dispositivi mobili che forniscono visibilità KPI alle parti interessate. I dashboard forniscono visibilità esecutiva e operativa attraverso numeri di riepilogo, linee di tendenza, raggruppamenti e annotazioni. Le scorecard per dispositivi mobili forniscono dati immediati sulle prestazioni tramite l&#39;app mobile [!DNL Adobe Analytics] per dashboard.

#### Punti decisionali

In questa fase devono essere prese le seguenti decisioni.

>[!NOTE]
>**Decisione: tipo di dashboard**
>
>Si tratta di una dashboard per Workspace desktop, di una scorecard per dispositivi mobili o di entrambi?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Progetto Workspace (desktop) | Dashboard interattivi dettagliati per analisti e addetti al marketing | Funzionalità di visualizzazione complete; supporta pannelli, tabelle e layout complessi |
>| Scorecard per dispositivi mobili | KPI immediati per dirigenti e stakeholder su dispositivi mobili | Limitato a 16 tessere; numeri di riepilogo con grafici sparkline di tendenza; richiede un’app mobile |
>| Entrambi | L’organizzazione ha bisogno sia di analisi dettagliate che di reporting mobile a livello esecutivo | Separa gli artefatti ma può condividere la stessa visualizzazione dati e le stesse metriche calcolate |

>[!NOTE]
>**Decisione: modello di condivisione**
>
>Chi deve ricevere il dashboard e come?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Condividi con utenti specifici | Pubblico limitato con esigenze di accesso specifiche | Controllo più granulare; richiede la gestione dei singoli utenti |
>| Condividi con gruppo di profili di prodotto | Accesso a livello di team allineato con i ruoli organizzativi | Efficiente per la distribuzione a livello di team; gestito tramite i profili di prodotto CJA |
>| Pianificare la consegna e-mail | Rapporti PDF/CSV ricorrenti per le parti interessate che non accedono a CJA | Consegna automatica; la frequenza massima è oraria; formati PDF e CSV |

>[!NOTE]
>**Decisione: visibilità annotazione**
>
>Gli eventi chiave devono essere annotati sulle linee di tendenza della dashboard?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Sì — crea annotazioni | Campagne principali, avvii di prodotti, incidenti sul sito o eventi stagionali possono spiegare le tendenze dei dati | Le annotazioni vengono visualizzate come marcatori nei grafici a linee e nelle tendenze delle scorecard; forniscono contesto per picchi o riduzioni di dati |
>| No | Il pubblico della dashboard ha familiarità con il contesto aziendale e le annotazioni aggiungerebbero confusione | Presentazione visiva più semplice |

#### Configurare le dashboard

**Navigazione interfaccia utente:**

- Dashboard di Workspace: CJA > Workspace > Crea progetto
- Scorecard per dispositivi mobili: CJA > Progetti > Crea > Scorecard per dispositivi mobili
- Condivisione: CJA > Workspace > Condividi > Condividi con gli utenti di Workspace
- Consegna programmata: CJA > Workspace > Condividi > Pianifica progetto

Dettagli configurazione chiave:

- Per le scorecard per dispositivi mobili, crea riquadri che visualizzano una singola metrica con un numero di riepilogo e una tendenza grafico sparkline
- Configura intervalli di date e periodi di confronto predefiniti (ad esempio, ultimi 30 giorni rispetto al periodo precedente o mese su mese)
- Aggiungere filtri con ambito di pubblico che i dirigenti possano attivare o disattivare le scorecard per dispositivi mobili
- Configurare la consegna e-mail pianificata per i rapporti PDF o CSV ricorrenti
- Massimo 16 sezioni per scorecard per dispositivi mobili; massimo 15 pannelli per progetto Workspace
- Le annotazioni sono limitate a 100 per visualizzazione dati

**Documentazione di Experience League:**

- [Crea una scorecard per dispositivi mobili](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Configurare e curare le scorecard](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Dashboard di Adobe Analytics: guida esecutiva](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Condividi progetti](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Programmare progetti](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Visualizzazione Numero di riepilogo](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)
- [Intervalli di date](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

### Fase 5: Pubblicazione dei tipi di pubblico (solo opzione C)

**Funzione dell&#39;applicazione:** CJA: Pubblicazione del pubblico

Questa fase configura la pubblicazione del pubblico CJA per inviare nuovamente i segmenti rilevati dall’analisi al profilo cliente in tempo reale di AEP per l’attivazione a valle nelle destinazioni RT-CDP, nelle campagne AJO o nei percorsi AJO.

#### Punti decisionali

In questa fase devono essere prese le seguenti decisioni.

>[!NOTE]
>**Decisione: aggiornamento cadenza**
>
>Con quale frequenza occorre aggiornare l’iscrizione al pubblico?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Una tantum (snapshot) | Pubblico specifico per la campagna che non necessita di aggiornamento continuo | Nessuna elaborazione in corso; ripubblicare per gli aggiornamenti |
>| Ogni 4 ore | Requisiti di attivazione in tempo quasi reale | Costi di elaborazione più elevati; ideale per tipi di pubblico che richiedono tempo |
>| Giornaliero | Cadenza di attivazione marketing standard | Freschezza e costi bilanciati; scelta più comune |
>| Ogni settimana | Pubblico stabile e lento | Elaborazione minima; adatta per segmenti a lungo termine |

>[!NOTE]
>**Decisione: spazio dei nomi identità**
>
>Quale spazio dei nomi di identità deve utilizzare CJA per la risoluzione dei membri del pubblico?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| ID CRM | Identificatore cliente principale dell’organizzazione | Massima precisione per corrispondenza cliente nota |
>| ECID | Principalmente pubblico basato su web/app | Con ambito dispositivo; potrebbe non essere possibile risolvere tutti i record del profilo |
>| E-mail (con hash) | E-mail è l’identificatore comune per l’attivazione | Deve corrispondere allo spazio dei nomi utilizzato nella configurazione delle identità di AEP |
>| Spazio dei nomi personalizzato | Identificatore proprietario utilizzato nell’organizzazione | Deve essere configurato nel servizio AEP Identity |

#### Configurare la pubblicazione di tipi di pubblico

**Navigazione interfaccia utente:** CJA > Componenti > Tipi di pubblico > Pubblica pubblico

Dettagli configurazione chiave:

- Definire i criteri di pubblico utilizzando i filtri di CJA (ambito persona, sessione o contenitore evento)
- Seleziona la visualizzazione dati e il filtro da pubblicare
- Configurare lo spazio dei nomi delle identità per la risoluzione del profilo di AEP
- Impostare la frequenza di aggiornamento in base alle esigenze di attivazione
- Monitorare lo stato di pubblicazione nell’elenco Tipi di pubblico di CJA (Componenti > Tipi di pubblico > Colonna Stato)
- Verifica che il pubblico venga visualizzato in AEP Audience Portal (Tipi di pubblico > Sfoglia > Filtra per origine &quot;CJA&quot;)
- Massimo 75 tipi di pubblico pubblicati per cliente CJA (in tutte le sandbox)
- La valutazione iniziale del pubblico può richiedere fino a 24 ore per set di dati di grandi dimensioni

**Documentazione di Experience League:**

- [Panoramica di Audiences](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Creare e pubblicare tipi di pubblico](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/audiences/publish)
- [Gestire i tipi di pubblico](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/audiences/manage)
- [Panoramica di Audience Portal](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/audience-portal)

## Considerazioni sull’implementazione

Questa sezione descrive guardrail, insidie comuni, best practice e decisioni di compromesso per questo modello di casi d’uso.

### Guardrail e limiti

A questa implementazione si applicano i seguenti guardrail e limiti.

- **Limiti di connessione:** Il numero massimo di connessioni per organizzazione è limitato dal diritto SKU di CJA. Una singola connessione può includere set di dati da una sola sandbox di AEP. — [guardrail CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-admin/guardrails)
- **Limiti visualizzazione dati:** massimo di 5.000 dimensioni e 5.000 metriche per visualizzazione dati. Massimo 100 campi derivati per visualizzazione dati con un massimo di 5 livelli di funzioni nidificate.
- **Limiti di Workspace:** massimo di 40 pannelli per progetto. Le tabelle a forma libera supportano fino a 10 analisi approfondite delle dimensioni. Massimo 50.000 righe per richiesta di rapporto.
- **Limiti scorecard:** massimo di 16 sezioni per scorecard mobile.
- **Latenza streaming:** I dati in streaming sono generalmente disponibili in CJA entro 90 minuti dall&#39;acquisizione di AEP.
- **Limiti di pubblicazione del pubblico:** massimo di 75 tipi di pubblico pubblicati per cliente CJA. La frequenza minima di aggiornamento è ogni 4 ore.
- **Limiti di analisi guidata:** l&#39;analisi Funnel supporta un massimo di 15 passaggi. Il confronto dei segmenti supporta fino a 3 segmenti simultaneamente.

### Insidie comuni

Quando implementi questo modello, tieni presenti i seguenti problemi comuni.

- **Mancata corrispondenza dell&#39;ID persona tra i set di dati:** tutti i set di dati in una connessione devono utilizzare un campo ID persona coerente per l&#39;analisi tra i set di dati. Gli ID persona non corrispondenti generano visualizzazioni cliente frammentate in cui la stessa persona appare come più persone. Verifica la coerenza dell’ID persona prima di creare la connessione.

- **Il backfill richiede un tempo inaspettatamente lungo:** La retrocompilazione di set di dati di grandi dimensioni con miliardi di record può richiedere giorni. Pianifica questo passaggio durante le tempistiche di implementazione e avvia la retrocompilazione in anticipo. Monitora lo stato della visualizzazione dei dettagli della connessione.

- **Visualizzazione dati che mostra &quot;Non specificato&quot; per la maggior parte dei valori di dimensione:** Il campo dello schema mappato potrebbe essere scarsamente popolato nei dati di origine. Controlla la qualità dei dati nel set di dati di origine prima di presumere un errore di configurazione. Valuta l’utilizzo di un campo derivato per la gestione di valori Null.

- **I conteggi delle sessioni non sembrano corretti:** Le impostazioni di timeout della sessione influiscono in modo significativo sulle metriche relative all&#39;ambito di sessione. Un timeout molto breve crea più sessioni, mentre un timeout molto lungo crea meno sessioni. I nuovi eventi di inizio sessione possono anche frammentare le sessioni in modo imprevisto. Rivedi e verifica le impostazioni della sessione in base ai modelli di comportamento degli utenti noti.

- **Il modello di attribuzione non si applica come previsto:** I modelli di attribuzione si applicano solo alle metriche, non alle dimensioni. Verificare che l&#39;intervallo di lookback sia impostato in modo appropriato per il ciclo aziendale. I brevi intervalli di lookback potrebbero perdere i primi punti di contatto di funnel.

- **Metriche calcolate che restituiscono zeri o valori imprevisti:** Verificare che le metriche di base a cui si fa riferimento nella formula contengano dati nella visualizzazione dati di destinazione per l&#39;intervallo date selezionato. Verifica la divisione per zero nelle metriche del rapporto. Recupera la definizione della metrica e verifica la struttura della formula.

- **Pubblicazione del pubblico non riuscita (opzione C):** La connessione CJA deve avere un ID persona valido che viene risolto in uno spazio dei nomi di identità AEP. Verifica la configurazione dello spazio dei nomi delle identità e che AEP Real-Time Customer Profile sia abilitato nella sandbox di destinazione.

### Best practice

Segui queste best practice per un’implementazione corretta.

- **Inizia con un&#39;unica connessione completa:** Crea una connessione che includa tutti i set di dati rilevanti, quindi crea più visualizzazioni dati per diverse prospettive analitiche. In questo modo si evita la proliferazione delle connessioni e si semplifica la gestione.

- **Utilizza i campi derivati per la classificazione del canale di marketing:** Anziché basarsi su codici di tracciamento non elaborati, crea campi derivati con logica Case When per classificare il traffico nei canali di marketing. In questo modo viene garantito un reporting dei canali coerente in tutte le analisi.

- **Crea un dizionario di metriche:** Documenta tutte le metriche calcolate con le relative formule, l&#39;uso previsto e gli intervalli di valori previsti. Condividi questo dizionario con il team di analisi per garantire un utilizzo coerente delle metriche nei vari progetti.

- **Progetta visualizzazioni dati per il tuo pubblico:** Crea visualizzazioni dati separate per i diversi gruppi di parti interessate: una visualizzazione dati di marketing con dimensioni e metriche incentrate sulla campagna e una visualizzazione dati del prodotto con dimensioni di funzionalità e coinvolgimento. Questo semplifica gli elenchi dei componenti per ciascun gruppo di utenti.

- **Annota tutto:** crea annotazioni per i lanci di campagne, le modifiche al sito, gli incidenti tecnici, la stagionalità e qualsiasi evento che possa spiegare le tendenze dei dati. Le annotazioni forniscono un contesto critico durante la revisione delle dashboard mesi dopo.

- **Verificare le metriche calcolate rispetto ai calcoli manuali:** Prima di basarsi su una metrica calcolata per le dashboard, eseguire un report con la metrica calcolata e i relativi componenti di base affiancati. Verificare che i valori calcolati corrispondano a un calcolo manuale.

- **Utilizzare i filtri in modo strategico:** creare filtri riutilizzabili per i pattern di segmentazione più comuni (nuovi e di ritorno, mobili e desktop, per area geografica). Applica questi filtri a livello di pannello anziché incorporarli in ogni tabella a forma libera.

- **Monitora regolarmente lo stato della connessione:** Controlla la visualizzazione dei dettagli della connessione per verificare la presenza di record ignorati, batch non riusciti e ritardi di streaming. I problemi di qualità dei dati a livello di connessione influiscono su tutte le analisi a valle.

### Decisioni di compromesso

Quando pianifichi l’implementazione, considera i seguenti compromessi.

>[!NOTE]
>**Compensazione: profondità dell&#39;analisi rispetto al tempo di insight**
>
>L’opzione B (Customer percorsi Analytics) fornisce le informazioni più approfondite cross-channel, ma richiede un investimento iniziale significativo nella configurazione della connessione, nella progettazione della visualizzazione dati e nella creazione di campi derivati. L’opzione D (analisi guidata) offre tempi di realizzazione più rapidi per insight con flussi di lavoro strutturati, ma offre una minore flessibilità analitica.
>
>- **L&#39;opzione B favorisce:** Comprensione completa, analisi multicanale complessa, modellazione di attribuzione, sviluppo di KPI personalizzati
>- **L&#39;opzione D favorisce:** velocità, accessibilità per utenti non analisti, domande strutturate sull&#39;esperienza del prodotto
>- **Consiglio:** inizia con l&#39;opzione D per ottenere informazioni immediate sui prodotti durante la creazione in parallelo dell&#39;infrastruttura dell&#39;opzione B. Molte organizzazioni vengono eseguite entrambe contemporaneamente per team diversi.

>[!NOTE]
>**Compensazione: completezza backfill e preparazione connessione**
>
>L’importazione di tutti i dati storici fornisce la massima profondità analitica per i confronti su base annua e l’analisi delle tendenze a lungo termine, ma la retrocompilazione per set di dati di grandi dimensioni può richiedere giorni. Limitando la retrocompilazione a un periodo recente, la connessione è pronta più rapidamente ma l’analisi storica è limitata.
>
>- **Tutti i dati sono a favore:** Analisi delle tendenze a lungo termine, confronti su base annua, analisi per coorte con cronologia estesa
>- **Backfill limitato favorisce:** connessione più rapida, tempo più rapido per il primo dashboard, ottimizzazione dello storage
>- **Consiglio:** eseguire il backfill di tutti i dati per le connessioni di produzione che supportano l&#39;analisi strategica. Utilizza backfill limitato per le connessioni di sviluppo e le implementazioni proof-of-concept.

>[!NOTE]
>**Compensazione: singola visualizzazione completa dei dati rispetto a più visualizzazioni mirate**
>
>Un’unica visualizzazione dati con tutte le dimensioni e le metriche fornisce un’area di lavoro analitica unificata, ma può sopraffare gli utenti con gli elenchi dei componenti. Visualizzazioni dati mirate multiple (una per team o caso d’uso) semplificano l’esperienza del componente ma richiedono il mantenimento di più configurazioni.
>
>- **Una singola visualizzazione dati favorisce:** analisi unificata, raggruppamenti tra domini, gestione più semplice
>- **Più visualizzazioni dati favoriscono:** elenchi di componenti pulenti, terminologia specifica del team, diverse definizioni di sessione per caso d&#39;uso
>- **Consiglio:** inizia con una visualizzazione dati principale, quindi crea visualizzazioni dati mirate aggiuntive se la complessità dell&#39;elenco dei componenti diventa un ostacolo all&#39;adozione. Tutte le visualizzazioni dati possono fare riferimento alla stessa connessione.

>[!NOTE]
>**Compensazione: streaming in tempo reale e acquisizione solo batch**
>
>L’abilitazione dello streaming sulla connessione CJA fornisce dati quasi in tempo reale (entro circa 90 minuti dall’acquisizione di AEP), ma elabora più dati in modo continuo. L’acquisizione solo batch elabora i dati periodicamente e può introdurre ritardi.
>
>- **Preferenze streaming:** Rapporti tempestivi, monitoraggio delle campagne attive, dashboard in tempo quasi reale
>- **Preferenze solo batch:** configurazione più semplice, finestre di elaborazione prevedibili, sufficienti per la generazione di rapporti settimanali o mensili
>- **Consiglio:** abilitare lo streaming per le connessioni di produzione. Il costo di elaborazione incrementale è minimo rispetto al valore dei dati tempestivi per il monitoraggio attivo delle campagne e delle dashboard operative.

## Documentazione correlata

Le risorse seguenti forniscono informazioni aggiuntive per questo modello di caso d’uso.

### [!DNL Customer Journey Analytics] — Guida introduttiva

- [Panoramica di CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-overview/cja-overview)
- [Guardrail CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-admin/guardrails)

### Connessioni

- [Panoramica delle connessioni](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-connections/overview)
- [Creare o modificare una connessione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-connections/create-connection)
- [Gestire le connessioni](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-connections/manage-connections)

### Visualizzazioni dati

- [Panoramica delle visualizzazioni dati](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/data-views)
- [Creare o modificare una visualizzazione dati](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Panoramica delle impostazioni dei componenti](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Impostazioni persistenza](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Impostazioni di attribuzione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Impostazioni formato](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Deduplica delle metriche](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [Includi/escludi valori](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [Impostazioni di sessione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/session-settings)
- [Campi derivati](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/derived-fields)

### Workspace e analisi

- [Panoramica di Workspace](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/home)
- [Creare un progetto](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Tabella a forma libera](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Visualizzazione del flusso](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Visualizzazione Abbandono](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Tabella coorte](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Pannello Attribuzione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Dimensioni di raggruppamento](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [Condividi progetti](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Programmare progetti](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Panoramica sull’esportazione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/export/export-cloud)

### Analisi guidata

- [Panoramica dell’analisi guidata](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/overview)
- [Vista funnel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Visualizzazione tendenze](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Visualizzazione frequenza di coinvolgimento](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [Vista Mantenimento](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [Visualizzazione crescita attiva](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [Vista impatto sulla versione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/impact/release)
- [Visualizzazione impatto primo utilizzo](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/impact/first-use)
- [Vista Timeline](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/streams/timeline)

### Componenti

- [Panoramica sui filtri](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Creare filtri](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Panoramica delle metriche calcolate](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Creare metriche calcolate](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Funzioni metriche calcolate](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [Panoramica delle annotazioni](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/annotations/overview)
- [Intervalli di date](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)
- [Componente metriche](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/apply-create-metrics)

### Pubblicazione del pubblico

- [Panoramica di Audiences](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Creare e pubblicare tipi di pubblico](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/audiences/publish)
- [Gestire i tipi di pubblico](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/audiences/manage)

### Analisi dei contenuti

- [Content Analytics](https://experienceleague.adobe.com/it/docs/analytics-platform/using/content-analytics/content-analytics)
- [Configurazione Content Analytics](https://experienceleague.adobe.com/en/docs/analytics-platform/using/content-analytics/config/configuration)

### Dashboard e scorecard

- [Crea una scorecard per dispositivi mobili](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Configurare e curare le scorecard](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Dashboard di Adobe Analytics: guida esecutiva](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Visualizzazione Numero di riepilogo](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)

### Fondamenti di AEP

- [Panoramica sui set di dati](https://experienceleague.adobe.com/it/docs/experience-platform/catalog/datasets/overview)
- [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home)
- [Panoramica sulle origini](https://experienceleague.adobe.com/it/docs/experience-platform/sources/home)
- [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home)
- [Panoramica di Audience Portal](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/audience-portal)

### Integrazione del reporting in AJO

- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Rapporto e-mail della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/campaign-global-report-cja-email)
- [Rapporto e-mail percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/journey-global-report-cja-email)

### Tutorial e guide

- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/schema/composition)
- [Panoramica di Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/home)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/it/docs/experience-platform/datastreams/configure)
