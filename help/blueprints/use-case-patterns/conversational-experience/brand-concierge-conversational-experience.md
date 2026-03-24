---
title: Esperienza conversazionale Brand Concierge
description: Scopri come trasformare le proprietà digitali in esperienze di conversazione basate sull’intelligenza artificiale e brand-safe che guidano l’individuazione dei clienti.
solution: Experience Platform, Real-Time Customer Data Platform
exl-id: a9545328-316d-446a-9308-18af61c58d1c
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7239'
ht-degree: 0%

---

# Esperienza di conversazione Brand Concierge

Questa guida fornisce un riferimento completo all&#39;implementazione per le esperienze di conversazione basate sull&#39;intelligenza artificiale che utilizzano [!DNL Adobe Brand Concierge], integrato con [!DNL Adobe Experience Platform] (AEP) e [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]). È progettato per architetti di soluzioni, tecnici di marketing e ingegneri di implementazione che devono implementare agenti di conversazione sicuri per il brand nelle proprietà digitali.

Descrive tutti gli approcci possibili per la distribuzione di esperienze conversazionali, dai chatbot per la consulenza sui prodotti agli assistenti completi per la navigazione del sito, con indicazioni su quando scegliere ogni opzione. Il piano tratta la configurazione dell’agente, la governance del brand, l’integrazione dei contenuti, le strategie di distribuzione, l’arricchimento dei profili dai segnali di conversazione e l’ottimizzazione delle analisi.

[!DNL Brand Concierge] consente ai brand di distribuire agenti conversazionali intelligenti che comprendono la voce del brand, accedono a cataloghi di prodotti e contenuti approvati, forniscono consigli personalizzati basati su dati di profilo in tempo reale e acquisiscono segnali di intento e di sentiment nel profilo cliente unificato. Il risultato è un&#39;esperienza di conversazione che si sente naturale e sul marchio, arricchendo la comprensione di ogni cliente da parte dell&#39;organizzazione.

## Panoramica del caso d’uso

Le organizzazioni cercano sempre più di trasformare le esperienze digitali statiche in conversazioni dinamiche basate sull’intelligenza artificiale che guidano i clienti attraverso l’individuazione, la selezione dei prodotti e le decisioni di acquisto. [!DNL Adobe Brand Concierge] affronta questo problema fornendo un livello di intelligenza artificiale conversazionale orchestrato che si trova al di sopra delle proprietà digitali esistenti, basato su AEP Agent Orchestrator.

Questo modello è distinto dalle implementazioni chatbot tradizionali perché è integrato in modo nativo con il profilo unificato di AEP, utilizza guardrail di governance del brand per garantire che ogni risposta sia allineata agli standard del brand e invia segnali conversazionali nella piattaforma dati del cliente per la personalizzazione e l’attivazione a valle.

Il pubblico di destinazione include team di esperienza digitale, manager di e-commerce, content strategist e tecnici di marketing che devono distribuire esperienze conversazionali intelligenti per stimolare il coinvolgimento, la conversione e l’arricchimento dei profili.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### Fornire esperienze cliente personalizzate

Personalizza contenuti, offerte e messaggi in base a preferenze, comportamenti e fasi del ciclo di vita individuali.

**KPI:** coinvolgimento, tassi di conversione, soddisfazione del cliente (CSAT)

[Ulteriori informazioni sulla distribuzione di esperienze cliente personalizzate](/help/blueprints/business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

### Migliorare il coinvolgimento dei clienti

Aumenta la frequenza e la profondità di interazione tra tutti i punti di contatto digitali e fisici.

**KPI:** coinvolgimento, pagina Time On (web), tassi di apertura

[Ulteriori informazioni sul miglioramento del coinvolgimento dei clienti](/help/blueprints/business-objectives/qualification-sales-b2b/improve-customer-engagement.md)

### Aumentare i tassi di conversione

Migliora la percentuale di visitatori e potenziali clienti che completano le azioni desiderate, ad esempio acquisti, iscrizioni o invii di moduli.

**KPI:** Tassi di conversione, Conversione lead, Costo per lead

[Ulteriori informazioni sull’aumento dei tassi di conversione](/help/blueprints/business-objectives/revenue-monetization/increase-conversion-rates.md)

### Acquisire nuovi clienti

Espandi la base di clienti tramite campagne di acquisizione mirate, tipi di pubblico simili e ottimizzazione di contenuti multimediali a pagamento.

**KPI:** nuovi clienti, costo acquisizione cliente, conversione potenziali clienti/lead

[Ulteriori informazioni sull&#39;acquisizione di nuovi clienti](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

## Esempi di casi d’uso tattici

Gli scenari seguenti illustrano come questo modello può essere applicato nella pratica.

- **Assistente all&#39;individuazione del prodotto**: distribuzione di un agente di conversazione nelle pagine dell&#39;elenco dei prodotti che pone domande mirate e limita i consigli sui prodotti in base alle esigenze, alle preferenze e al budget del cliente
- **Consulente confronto guidato**: aiuta i clienti a confrontare i prodotti uno accanto all&#39;altro tramite un dialogo naturale, evidenziando le differenze pertinenti alle priorità dichiarate
- **Concierge dimensioni e adattamento** — Abbigliamento guida o calzature per gli acquirenti attraverso la selezione delle dimensioni utilizzando domande e risposte conversazionali, riducendo i resi e aumentando la fiducia negli acquisti
- **Selettore abbonamento o piano**: guida i clienti attraverso le opzioni del livello di servizio o del piano di abbonamento con consigli personalizzati in base ai modelli di utilizzo e alle esigenze dichiarate
- **Assistente alla navigazione del sito**: aiuta i visitatori a trovare contenuti rilevanti, risorse di supporto o categorie di prodotti in base all&#39;intento dichiarato, riducendo le percentuali di mancato recapito su siti complessi
- **Consulenza pre-acquisto**: fornisci indicazioni di acquisto di alta considerazione (ad esempio, elettronica, prodotti finanziari, assicurazione) tramite conversazioni a più turni che generano un consiglio
- **Responsabile del programma fedeltà**: aiuta i membri fedeltà a scoprire premi, comprendere i vantaggi a livello e trovare opportunità di rimborso tramite l&#39;interazione conversazionale
- **Conversazione di ricoinvolgimento**: avvia un&#39;estensione conversazionale proattiva per i visitatori di ritorno in base alla cronologia di esplorazione precedente o agli elementi del carrello abbandonati
- **Riassegnazione di agenti live con contesto**: consegna senza problemi di richieste complesse agli agenti di vendita o di supporto live, mantenendo al contempo il contesto di conversazione completo e i dati del profilo cliente
- **Supporto post-acquisto e upselling**: coinvolgi i clienti dopo l&#39;acquisto con assistenza per la configurazione, suggerimenti di prodotti complementari e check-in di soddisfazione tramite canali conversazionali

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare il successo di questo modello di caso d’uso.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Tasso di coinvolgimento conversazione | Percentuale di visitatori che avviano e sostengono una conversazione | Conversazioni avviate / visualizzazioni pagina idonee |
| Tasso di completamento conversazione | Percentuale di conversazioni che raggiungono una risoluzione significativa | Conversazioni/conversazioni completate avviate |
| Tasso di conversione conversazionale | Percentuale di conversazioni che hanno portato all’azione desiderata (acquisto, iscrizione, modulo lead) | Conversioni da conversazione / conversazioni totali |
| Profondità media conversazione | Numero di giri per conversazione, che indica la qualità del coinvolgimento | Numero medio di messaggi per sessione |
| Soddisfazione del cliente (CSAT) | Punteggio di soddisfazione post-conversazione dal feedback in-experience | Risposte ai sondaggi o valutazioni &quot;pollici-su/giù&quot; |
| Tasso di accettazione consigli | Percentuale di consigli di prodotto accettati o su cui è stato fatto clic | Consigli seguiti/consigli serviti |
| Frequenza handoff agente live | Percentuale di conversazioni inoltrate ad agenti live | Conversazioni / Totale conversazioni |
| Percentuale di arricchimento del profilo | Percentuale di conversazioni che generano nuovi segnali di intento o preferenza | Profili arricchiti / Totale conversazioni |
| Ricavi influenzati dalla conversazione | Ricavi da acquisti in cui una conversazione [!DNL Brand Concierge] ha preceduto la conversione | Analisi dell’attribuzione sui percorsi conversazione-acquisto |
| Tempo di risoluzione | Durata media dall&#39;inizio della conversazione alla risoluzione o all&#39;handoff | Analisi delle marche temporali tra gli eventi di conversazione |

## Schema del caso d’uso

**Esperienza di conversazione Brand Concierge**

Trasforma le proprietà digitali in esperienze di conversazione basate sull’intelligenza artificiale e brand-safe che guidano l’individuazione dei clienti attraverso il dialogo naturale, arricchiscono i profili con segnali di intento e di sentiment e forniscono consigli di prodotto personalizzati.

**Catena di funzioni:** Configurazione agente > Impostazione Brand Governance > Integrazione dei contenuti > Distribuzione esperienza conversazionale > Arricchimento profilo > Analytics e ottimizzazione

## Applicazioni

Per implementare questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Brand Concierge]** - Applicazione di esperienza conversazionale basata sull&#39;intelligenza artificiale che fornisce l&#39;agente orchestrator, Product Advisor Agent, Site Advisory Agent, brand governance e analisi conversazionale
- **[!DNL Adobe Experience Platform](AEP)** — Unified data foundation che fornisce schemi XDM, risoluzione delle identità, profili cliente in tempo reale e infrastruttura di raccolta dati per i segnali conversazionali
- **[!DNL Real-Time CDP]([!DNL RT-CDP])** — Piattaforma dati cliente che fornisce la ricerca dei profili in tempo reale per conversazioni personalizzate, segmentazione del pubblico da segnali conversazionali e arricchimento dei profili con dati di intento e sentiment

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve essere al suo posto | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Obbligatorio | Sandbox con abilitazione per [!DNL Brand Concierge]; ruoli configurati per amministratori di esperienza di conversazione, content manager e utenti di analisi; criteri ABAC in uso per i dati di conversazione contenenti PII o segnali sensibili dei clienti | [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Obbligatorio | Schemi XDM per eventi conversazionali (classe ExperienceEvent con gruppi di campi specifici per la conversazione che acquisiscono intento, sentiment, interazioni di prodotto ed eventi di handoff); schema di profilo esteso con preferenze conversazionali e attributi di intento; schema di ricerca nel catalogo dei prodotti per consigli di base | [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Origini dati e raccolta | Obbligatorio | [!DNL Web SDK] o [!DNL Mobile SDK] configurati con flussi di dati che instradano i dati degli eventi di conversione ai set di dati di AEP; integrazione [!DNL Edge Network] per l&#39;acquisizione di eventi in tempo reale durante le conversazioni; dati del catalogo dei prodotti acquisiti tramite i connettori di origine o l&#39;acquisizione batch | [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home) |
| Configurazione identità e profilo | Obbligatorio | Spazi dei nomi di identità configurati per l’identificazione dei visitatori (ECID per anonimo, ID CRM o e-mail per autenticato); criterio di unione configurato con l’attivazione Edge per la ricerca dei profili in tempo reale durante le conversazioni; regole di collegamento delle identità per la continuità delle conversazioni tra dispositivi | [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| Definizione e segmentazione del pubblico | Presunto sul posto | Tipi di pubblico non necessari per l’implementazione conversazionale di base, ma necessari per strategie di conversazione personalizzate (ad esempio, segmenti di clienti di alto valore che ricevono flussi di conversazione diversi); si consiglia la valutazione in streaming o Edge per la personalizzazione delle conversazioni in tempo reale | [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Consigliato | Aggregare i segnali conversazionali in attributi a livello di profilo (ad esempio, conversazioni totali, interessi di prodotto dominanti, punteggio medio di sentiment) da utilizzare nella segmentazione e nella personalizzazione a valle | [Panoramica attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Consigliato | Configura i criteri di conservazione per i dati degli eventi di conversazione, gestisci il consenso per la registrazione delle conversazioni e la creazione di profili e supporta le richieste di eliminazione della privacy per le trascrizioni delle conversazioni | [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Etichettatura e applicazione dell’utilizzo dati | Consigliato | Etichettare i campi di dati conversazionali contenenti segnali PII, di sentiment o intenzionali; applicare criteri di governance che impediscano ai dati conversazionali sensibili di raggiungere destinazioni non autorizzate | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Monitoraggio e osservabilità | Consigliato | Monitora le pipeline di acquisizione degli eventi di conversazione, tieni traccia dei tassi di successo dell’arricchimento dei profili e genera avvisi sugli errori di flusso dei dati che potrebbero influire sulla qualità della personalizzazione della conversazione | [Panoramica di Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting e analisi | Incluso | Analizza le prestazioni della conversazione, il feedback del cliente, l&#39;attribuzione della conversione e l&#39;efficacia dell&#39;agente utilizzando [!DNL Brand Concierge] analisi integrate e [!DNL CJA] per l&#39;analisi dell&#39;impatto delle conversazioni cross-channel | [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Brand Concierge]

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Configurazione agente | Fase 1: Configurazione agente | Configurare l&#39;orchestratore di agenti [!DNL Brand Concierge] con le specializzazioni degli agenti (Product Advisor, Site Advisory) e le impostazioni di comportamento di base |
| Configurazione della governance dei marchi | Fase 2: configurazione della governance dei marchi | Definisci la voce del brand, il tono, i guardrail di messaggistica, i limiti dei contenuti approvati e gli argomenti vietati che modellano tutte le interazioni conversazionali |
| Integrazione dei contenuti | Fase 3: Integrazione dei contenuti | Collegare le origini di contenuto approvate dal marchio, tra cui i contenuti AEM, i cataloghi di prodotti, le knowledge base e altri dati attendibili per la preparazione delle risposte |
| Configurazione di Product Advisor | Fase 3: Integrazione dei contenuti | Configurare Product Advisor Agent per consigli di prodotti personalizzati, confronti guidati e distribuzione di risposte allineate al brand |
| Configurazione di Site Advisory | Fase 3: Integrazione dei contenuti | Configurare Site Advisory Agent per migliorare la navigazione adattando le interazioni in base al comportamento dei visitatori e ai segnali intento |
| Distribuzione di esperienze conversazionali | Fase 4: Distribuzione dell’esperienza conversazionale | Distribuisci esperienze conversazionali su tutti i canali supportati (web, app mobile, SDK personalizzato) con supporto per l’interazione testuale e vocale |
| Gestione flusso codice basso | Fase 4: Distribuzione dell’esperienza conversazionale | Consentire ai team di marketing di aggiornare il tono di conversazione, i flussi e i contenuti utilizzando gli strumenti di configurazione low-code |
| Arricchimento del profilo di conversazione | Fase 5: Arricchimento del profilo | Arricchisci i profili dei clienti di AEP con segnali di intento, sentiment, affinità tra prodotti e comportamento acquisiti durante le conversazioni |
| Analisi conversazionale | Fase 6: analisi e ottimizzazione | Monitora le metriche di coinvolgimento, il feedback dei clienti, i dati sulla conversione e la qualità delle conversazioni tramite dashboard di analisi integrate |
| Handoff agente live | Fase 4: Distribuzione dell’esperienza conversazionale | Configurare il trasferimento senza soluzione di continuità agli agenti di vendita o di supporto live, preservando al contempo il contesto completo della conversazione |

### [!DNL Real-Time CDP]

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Ricerca profilo in tempo reale | Fase 4: Distribuzione dell’esperienza conversazionale | Accedi agli attributi del profilo cliente in tempo reale e alle iscrizioni ai segmenti per personalizzare le risposte conversazionali in base ai dati noti del cliente |
| Arricchimento del profilo | Fase 5: Arricchimento del profilo | Arricchisci i profili con attributi calcolati derivati da eventi comportamentali conversazionali (punteggi di intento, tendenze dei sentiment, affinità di prodotto) |
| Valutazione del pubblico | Fase 5: Arricchimento del profilo | Valuta l’iscrizione al pubblico in base ai segnali conversazionali per consentire il targeting a valle dei segmenti conversazionali coinvolti |

## Prerequisiti

Gli elementi seguenti devono essere presenti prima dell’inizio dell’implementazione.

- [ L&#39;adesione ] [!DNL Adobe Brand Concierge] è attiva per l&#39;organizzazione
- [ ] licenze AEP e [!DNL RT-CDP] sono fornite con sufficienti autorizzazioni per profilo e volume di eventi
- [ ] documento sulle linee guida per i marchi disponibile che definisce voce, tono, messaggi approvati e argomenti vietati
- [ ] Catalogo di prodotti o archivio di contenuti preparato per l&#39;integrazione (risorse AEM, dati PIM o feed di prodotti strutturati)
- [ ] proprietà Web identificate per la distribuzione dell&#39;esperienza di conversazione con accesso tecnico per l&#39;integrazione di SDK
- [ Infrastruttura di ] agenti live disponibile se è richiesto il trasferimento (piattaforma del centro contatti, integrazione CRM)
- [ ] Framework di gestione del consenso attivo per l&#39;acquisizione e la profilazione dei dati conversazionali
- [ ] [!DNL Web SDK] o [!DNL Mobile SDK] già distribuito nelle proprietà di destinazione (o pianificato per la distribuzione simultanea)
- [ ] Allineamento delle parti interessate nell&#39;ambito della conversazione (solo consulenza prodotto, navigazione sito o entrambi)
- [ ] Privacy e revisione legale completate per l&#39;acquisizione e l&#39;utilizzo di dati conversazionali basati sull&#39;intelligenza artificiale

## Opzioni di implementazione

Le sezioni seguenti descrivono diversi approcci per l’implementazione di questo modello di caso d’uso.

### Opzione A: implementazione di Product Advisor

**Ideale per:** le organizzazioni di e-commerce e retail si sono concentrate sull&#39;individuazione guidata dei prodotti, sul confronto e sulle esperienze di consigli che determinano la conversione e il valore medio degli ordini.

**Funzionamento:**

Product Advisor Agent è configurato come specializzazione conversazionale principale. Si collega al catalogo dei prodotti, comprende gli attributi e le relazioni dei prodotti e guida i clienti attraverso il dialogo naturale per arrivare a consigli personalizzati. L’agente utilizza guardrail di governance del brand per garantire che i consigli siano in linea con le priorità aziendali (ad esempio, promozione di articoli in stock, evidenziazione di prodotti con margini favorevoli).

Product Advisor si integra con il profilo cliente in tempo reale per accedere alla cronologia degli acquisti, al comportamento di navigazione e ai dati sulle preferenze, consentendo consigli che tengono conto di ciò che il cliente già possiede, ha già considerato in precedenza o di cui potrebbe avere bisogno in base al proprio profilo. Le conversazioni vengono acquisite quando gli eventi di esperienza e i segnali di intento ritornano nel profilo per l’utilizzo a valle.

**Considerazioni chiave:**

- Richiede un catalogo dei prodotti ben strutturato con dati attributo completi per consigli efficaci
- I dati del prodotto devono essere aggiornati per evitare di raccomandare articoli esauriti o sospesi
- La governance del brand deve definire il modo in cui l’agente gestisce le menzioni di prodotto competitive e i confronti di prezzo

**Vantaggi:**

- Influisce direttamente sui ricavi misurabili attraverso la conversione guidata degli acquisti
- Riduce i tassi di restituzione dei prodotti attraverso decisioni di acquisto più informate
- Acquisisce segnali di intenti e affinità di prodotto di alto valore per la personalizzazione a valle
- Estensione naturale delle esperienze di e-commerce esistenti

**Limitazioni:**

- Richiede manutenzione e sincronizzazione continue del catalogo dei prodotti
- Limitato a conversazioni incentrate sul prodotto; le domande relative alla navigazione sul sito potrebbero non essere affrontate
- L’efficacia dipende dalla qualità e dalla completezza dei dati del catalogo

**Experience League:**

- [Panoramica di Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge product advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)

### Opzione B: implementazione di Site Advisory

**Ideale per:** organizzazioni con proprietà digitali complesse (media, servizi finanziari, assistenza sanitaria, tecnologia) in cui i visitatori necessitano di assistenza per la navigazione per trovare contenuti rilevanti, risorse o strumenti self-service.

**Funzionamento:**

Site Advisory Agent è configurato come specializzazione conversazionale principale. Indicizza la struttura del contenuto del sito, comprende le relazioni tra le pagine e le categorie di contenuto e adatta le sue indicazioni in base ai segnali di comportamento dei visitatori e alle intenzioni dichiarate. Quando un visitatore è coinvolto, l’agente interpreta le sue esigenze e le indirizza al contenuto, agli strumenti o alle risorse più rilevanti.

Site Advisory utilizza segnali comportamentali in tempo reale (pagina corrente, origine di riferimento, percorso di navigazione) combinati con i dati di profilo (visite precedenti, preferenze di contenuto, livello cliente) per fornire assistenza nella navigazione contestualmente rilevante. Questa funzione è particolarmente utile nei siti con gerarchie di contenuti approfondite, linee di prodotti multiple o flussi di lavoro self-service complessi.

**Considerazioni chiave:**

- Richiede l&#39;indicizzazione completa dei contenuti e la scansiona regolare quando il contenuto del sito cambia
- Più efficace sui siti con un’ampia gamma di contenuti, dove i visitatori spesso faticano a trovare ciò di cui hanno bisogno
- La governance del brand deve definire i limiti dell’ambito (a quali aree del sito può passare l’agente)

**Vantaggi:**

- Riduce i tassi di mancato recapito e migliora l&#39;individuazione dei contenuti su siti complessi
- Acquisisce segnali di intento di navigazione che rivelano lacune nei contenuti e problemi di esperienza utente
- Complessità di implementazione inferiore rispetto a Product Advisor (non è richiesta alcuna integrazione del catalogo prodotti)
- Fornisce informazioni analitiche su ciò che i visitatori stanno cercando ma non riescono a trovare

**Limitazioni:**

- Meno direttamente legato alla conversione dei ricavi rispetto alle conversazioni incentrate sui prodotti
- Richiede che i contenuti siano ben strutturati e regolarmente aggiornati per ottenere indicazioni accurate
- Può essere necessario un aggiornamento frequente man mano che la struttura del sito evolve

**Experience League:**

- [Panoramica di Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge site advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)

### Opzione C: implementazione combinata di Product Advisor e Site Advisory

**Ideale per:** organizzazioni che desiderano un&#39;esperienza di conversazione completa che copra sia l&#39;individuazione dei prodotti che la navigazione del sito, in genere grandi marchi di vendita al dettaglio o B2C con ampie proprietà digitali e diversi intenti dei visitatori.

**Funzionamento:**

Sia Product Advisor Agent che Site Advisory Agent sono configurati nell&#39;orchestratore [!DNL Brand Concierge]. L&#39;agente orchestrator utilizza il rilevamento intento per indirizzare le conversazioni alla specializzazione appropriata: le query relative al prodotto vengono inviate a Product Advisor mentre le query di navigazione e di ricerca dei contenuti vengono inviate a Site Advisory. L&#39;orchestratore gestisce transizioni senza soluzione di continuità tra specializzazioni all&#39;interno di un&#39;unica conversazione.

Questo approccio offre un&#39;esperienza di conversazione il più possibile completa, gestendo l&#39;intera gamma di esigenze dei visitatori, da &quot;Aiutami a trovare un prodotto&quot; a &quot;Dove posso controllare lo stato del mio ordine?&quot; I guardrail di governance del brand si applicano in modo uniforme a entrambe le specializzazioni, garantendo una voce coerente del brand indipendentemente dall’argomento della conversazione.

**Considerazioni chiave:**

- Maggiore complessità di implementazione che richiede l&#39;integrazione sia del catalogo dei prodotti che dei contenuti
- Il routing delle intenzioni tra specializzazioni deve essere ottimizzato per evitare conversazioni con indirizzi errati
- La configurazione della governance del brand è più ampia e copre sia i contesti di prodotto che quelli di navigazione

**Vantaggi:**

- Offre ai visitatori l’esperienza di conversazione più completa possibile
- Un singolo punto di ingresso gestisce diversi intenti dei visitatori senza richiedere interfacce separate
- Conversazioni tra specializzazioni diverse (ad esempio, domande sui prodotti che supportano la navigazione) gestite in modo naturale
- Arricchimento del profilo più ricco da diversi segnali di conversazione

**Limitazioni:**

- Implementazione più impegnativa e manutenzione continua
- Richiede il coordinamento tra i team del catalogo dei prodotti e dei contenuti
- Requisiti più complessi in materia di test e garanzia della qualità
- La configurazione della governance del brand è più complessa

**Experience League:**

- [Panoramica di Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)

### Confronto delle opzioni

| Criteri | Opzione A: Consulente di prodotto | Opzione B: consulenza sul sito | Opzione C: combinata |
| --- | --- | --- | --- |
| Ideale per | E-commerce, conversione basata sui prodotti | Siti con numerosi contenuti, navigazione self-service | Esperienza digitale ad ampio raggio |
| Complessi | Medio | Low-Medium | Alta |
| Time-to-value | 4-6 settimane | 3-5 settimane | 6-10 settimane |
| Impatto sui ricavi | Alta (influenza conversione diretta) | Medium (indiretto tramite coinvolgimento) | Massima (sia conversione che coinvolgimento) |
| Requisiti del contenuto | Catalogo prodotti con attributi avanzati | Indice contenuto sito | Catalogo dei prodotti e indice dei contenuti |
| Arricchimento del profilo | Affinità tra prodotti, intento di acquisto | Intento di navigazione, preferenze contenuto | Spettro di segnale completo |
| Manutenzione | Sincronizzazione catalogo prodotti | Reindicizzazione dei contenuti | Entrambi in corso |

### Scegli l’opzione giusta

Per iniziare, valuta l’obiettivo aziendale principale e le caratteristiche delle proprietà digitali:

1. **Se l&#39;obiettivo principale è la conversione del prodotto** e la proprietà digitale è incentrata sulla e-commerce, scegli **Opzione A (Product Advisor)**. Questo è il punto di partenza più comune per i marchi di vendita al dettaglio ed e-commerce.

2. **Se il tuo obiettivo principale è migliorare la reperibilità dei contenuti** e il tuo sito ha gerarchie di contenuti profonde o flussi di lavoro self-service complessi, scegli **Opzione B (Site Advisory)**. Questa funzione è ideale per i media, i servizi finanziari, le aziende del settore sanitario e le aziende tecnologiche.

3. **Se hai bisogno di una copertura completa** e hai esigenze sia di commerce che di navigazione dei contenuti, scegli **Opzione C (combinata)**. Considera di iniziare con una specializzazione e di aggiungere la seconda dopo la prima è stabile e ottimizzata.

Per la maggior parte delle organizzazioni si consiglia un approccio graduale: implementa prima una specializzazione, convalida le prestazioni e raccogli gli insegnamenti, quindi espandi alla distribuzione combinata.

## Fasi di implementazione

Le seguenti fasi delineano la sequenza di implementazione consigliata.

### Fase 1: configurazione dell’agente

**Funzione applicazione:** [!DNL Brand Concierge]: configurazione agente

Configurare l&#39;orchestrator principale dell&#39;agente [!DNL Brand Concierge], incluse la selezione delle specializzazioni dell&#39;agente (Product Advisor, Site Advisory o entrambi), la configurazione del comportamento dell&#39;agente di base e l&#39;impostazione della connessione tra [!DNL Brand Concierge] e AEP per l&#39;accesso al profilo e l&#39;acquisizione di eventi.

#### Decisione: selezione specializzazione agente

Determinare quali specializzazioni agente devono essere attivate per questa distribuzione.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo Product Advisor | Distribuzione incentrata su Commerce con targeting di individuazione e conversione dei prodotti | Richiede l&#39;integrazione del catalogo dei prodotti; percorso più veloce per influire sui ricavi |
| Solo siti consigliati | Distribuzione incentrata sui contenuti e sulla navigazione | Minore complessità di integrazione; ideale per siti non commerciali |
| Entrambe le specializzazioni | Copertura conversazionale completa tra prodotti e contenuti | Maggiore complessità; è consigliabile un rollout graduale a partire da uno |

#### Decisione: modello di avvio conversazione

Determina come devono iniziare le conversazioni sulla proprietà digitale.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Avviato dal visitatore (passivo) | Approccio predefinito in cui il widget chat è disponibile ma non coinvolge proattivamente | Riduzione del rischio di interruzione; si basa sulla consapevolezza del visitatore dell’opzione di chat |
| Coinvolgimento proattivo (attivato) | L’agente avvia la conversazione in base a segnali comportamentali (ad esempio tempo di permanenza prolungato, visite ripetute alla pagina, esitazione del carrello) | Tassi di coinvolgimento più elevati, ma rischia di infastidire i visitatori se i trigger sono troppo aggressivi; richiede una regolazione del trigger comportamentale |
| Ibrido (passivo con prompt contestuali) | Il widget Chat è passivo ma visualizza i prompt contestuali in base al contenuto della pagina o al comportamento del visitatore | Approccio equilibrato; guida alle richieste senza forzare il coinvolgimento |

#### Configurare l’agente

**Navigazione interfaccia utente:** [!DNL Experience Platform] > Assistente IA > [!DNL Brand Concierge] > Configurazione agente

Dettagli configurazione chiave:

- Definisci il nome e la descrizione dell’agente da visualizzare nell’interfaccia conversazionale
- Seleziona la sandbox di AEP contenente il profilo cliente e i dati evento a cui l’agente deve accedere
- Configurare l&#39;agente orchestrator per indirizzare le query tra specializzazioni in base al rilevamento intento
- Imposta i parametri della sessione di conversazione (durata timeout, durata massima della conversazione, limiti della sessione simultanea)
- Abilita l’integrazione della ricerca dei profili in tempo reale, in modo che l’agente possa accedere ai dati del profilo del visitatore durante le conversazioni

**Opzioni divergenti:**

**Per L&#39;Opzione A (Product Advisor):**
Abilitare la specializzazione di Product Advisor e configurarne la connessione all&#39;origine dati del catalogo prodotti. Imposta i parametri per i consigli di prodotto, tra cui il numero massimo di consigli per risposta, le preferenze di visualizzazione degli attributi del prodotto e le regole di gestione del confronto.

**Per L&#39;Opzione B (Site Advisory):**
Abilitare la specializzazione di Site Advisory e configurarne la connessione all&#39;indice di contenuto del sito. Imposta i parametri di navigazione, compresi i limiti dell’ambito del contenuto, la gestione delle categorie di pagina e le preferenze di generazione dei collegamenti profondi.

**Per L&#39;Opzione C (Combinata):**
Abilita entrambe le specializzazioni e configura la logica di indirizzamento intento dell&#39;orchestratore. Definire le regole di instradamento che determinano quando una conversazione deve essere gestita da Product Advisor rispetto a Site Advisory e come gestire le transizioni tra specializzazioni all&#39;interno di un&#39;unica conversazione.

**Documentazione di Experience League:**

- [Panoramica di Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Panoramica dell’Assistente AI](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/home)
- [AEP Agent Orchestrator](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)

### Fase 2: configurazione della governance del brand

**Funzione dell&#39;applicazione:** [!DNL Brand Concierge]: Impostazione della governance del brand

Configura i guardrail di governance del brand che modellano tutte le interazioni conversazionali. Ciò include definizioni di voce e tono del brand, limiti di contenuto approvati, argomenti vietati, linee guida sullo stile di risposta e regole di escalation. La governance del brand garantisce che ogni risposta generata dall’intelligenza artificiale sia allineata agli standard del brand.

#### Decisione: livello di rigore della governance

Determina quanto strettamente i guardrail di governance del brand devono vincolare le risposte conversazionali.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Governance rigorosa | Settori altamente regolamentati (servizi finanziari, assistenza sanitaria, assicurazioni) o marchi premium che richiedono un controllo preciso dei toni | Limita la flessibilità di conversazione; può comportare risposte più frequenti &quot;Non posso aiutare con quello&quot;; massima sicurezza del marchio |
| Governance moderata | La maggior parte dei marchi di consumo in cui la coerenza della voce del marchio è importante, ma una certa flessibilità di conversazione è accettabile | Buon equilibrio tra sicurezza del brand e naturalezza della conversazione; punto di partenza consigliato per la maggior parte delle implementazioni |
| Governance flessibile | Marchi occasionali o di lifestyle in cui la personalità conversazionale e il coinvolgimento sono prioritari | Sensazione di conversazione più naturale; richiede un monitoraggio più continuo per le risposte off-brand |

#### Decisione: strategia di gestione off-topic

Determina in che modo l&#39;agente deve gestire le domande al di fuori dell&#39;ambito configurato.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Reindirizza all&#39;ambito | L&#39;agente riconosce la domanda e reindirizza ad argomenti utili per | Mantiene il coinvolgimento, ma può frustrare i visitatori con legittime esigenze off-topic |
| Trasferimento ad agente live | L’agente offre di collegare il visitatore a un agente umano per domande non trattate | Migliore esperienza del cliente, ma richiede infrastruttura e personale live agent |
| Grave declino con le risorse | L&#39;agente spiega che non è in grado di risolvere il problema e fornisce collegamenti alle risorse o ai canali di supporto pertinenti | Fallback a basso attrito; non richiede la disponibilità di agenti live |

#### Configurare la governance del brand

**Navigazione interfaccia utente:** [!DNL Experience Platform] > Assistente IA > [!DNL Brand Concierge] > Governance del brand

Dettagli configurazione chiave:

- Definisci gli attributi del brand: nome del brand, tagline, missione, valori e caratteristiche di personalità che ispirano il tono conversazionale
- Imposta i parametri tonali: livello di formalità, tolleranza all’umorismo, livello di empatia e assertività per i consigli sui prodotti
- Configurare i limiti dei contenuti approvati: argomenti che l’agente è autorizzato a discutere e argomenti che sono esplicitamente vietati
- Definire le linee guida per il formato di risposta: lunghezza massima della risposta, utilizzo di elenchi rispetto alla prosa, criteri per le emoji e formattazione dei collegamenti
- Imposta trigger di escalation: condizioni che devono instradare automaticamente una conversazione a un agente live (ad esempio, rilevamento di reclami, segnali di insoddisfazione ripetuti, identificazione di clienti di alto valore)
- Configurare la gestione delle menzioni della concorrenza: come l&#39;agente deve rispondere quando i visitatori chiedono informazioni sui prodotti della concorrenza
- Definire i requisiti di dichiarazione di responsabilità e di notifica legale: informativa obbligatoria per i settori regolamentati

**Documentazione di Experience League:**

- [Governance del brand Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Informazioni operative sull’Assistente AI](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/home)

### Fase 3: integrazione dei contenuti

**Funzione applicazione:** [!DNL Brand Concierge]: integrazione dei contenuti, configurazione di Product Advisor, configurazione di Site Advisory

Configura le origini di contenuto che rispondono alle conversazioni in background in informazioni accurate e approvate dal brand. Ciò include l’integrazione del catalogo dei prodotti, le connessioni ai contenuti di AEM, le importazioni della knowledge base e le pianificazioni di aggiornamento dei contenuti.

#### Decisione: metodo di integrazione catalogo prodotti

Determina come devono essere forniti i dati di prodotto al Product Advisor Agent. (Solo opzioni A e C)

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Integrazione del set di dati di AEP | Il catalogo dei prodotti è già acquisito in AEP come set di dati di ricerca tramite i connettori di origine | Sfrutta l’infrastruttura dati esistente; mantiene i dati dei prodotti sincronizzati con i dati del profilo; richiede la modellazione e la raccolta di dati fondamentali per includere il catalogo dei prodotti |
| Integrazione dei feed diretti | Il catalogo dei prodotti esiste in una piattaforma PIM o commerce in grado di fornire un feed strutturato | Può offrire più dati di inventario e prezzo in tempo reale; richiede configurazione e pianificazione dei feed |
| Integrazione dei contenuti AEM | Il contenuto del prodotto viene gestito in AEM e deve fungere da origine dati di prodotto autorevole | Consigliato per i brand in cui AEM è l’hub di contenuti; assicura coerenza tra contenuti web e risposte conversazionali |

#### Decisione: frequenza di aggiornamento dei contenuti

Determina la frequenza con cui la knowledge base sul contenuto dell’agente deve essere aggiornata.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Tempo reale/quasi tempo reale | Disponibilità del prodotto, prezzi o modifiche frequenti al contenuto (ad esempio, vendite flash, vendita al dettaglio sensibile alle scorte) | Massima precisione ma maggiore carico dell&#39;infrastruttura; fondamentale per consigli sensibili all&#39;inventario |
| Aggiornamento giornaliero | Le modifiche al contenuto sono pianificate e pianificate (ad esempio, calendari editoriali, promozioni settimanali) | Buon equilibrio tra precisione e prestazioni; adatto per la maggior parte delle implementazioni |
| Aggiornamento su richiesta | Le modifiche al contenuto non sono frequenti e possono essere attivate manualmente quando si verificano aggiornamenti | Spese generali inferiori; adatto per cataloghi di prodotti statici o siti con contenuti stabili |

#### Configurare le origini di contenuto

**Navigazione interfaccia utente:** [!DNL Experience Platform] > Assistente IA > [!DNL Brand Concierge] > Origini contenuto

Dettagli configurazione chiave:

- Collegare le origini dati del catalogo prodotti con il mapping campi per nome prodotto, descrizione, attributi, prezzi, disponibilità, immagini e gerarchia di categorie
- Configurare l’indicizzazione dei contenuti per le pagine del sito, gli articoli della knowledge base, il contenuto delle domande frequenti e la documentazione di supporto
- Imposta i limiti dell&#39;ambito del contenuto definendo a quale contenuto l&#39;agente può fare riferimento e quale è escluso
- Configurare il comportamento di fallback del contenuto quando l’agente non è in grado di trovare contenuto rilevante per rispondere a una domanda
- Impostare le regole di qualità del contenuto: soglia minima di affidabilità del contenuto da includere nelle risposte, nei requisiti di citazione e nell’attribuzione della sorgente

**Opzioni divergenti:**

**Per L&#39;Opzione A (Product Advisor):**
Concentrati sull’integrazione del catalogo dei prodotti con la mappatura avanzata degli attributi di prodotto. Configura la logica dei consigli di Product Advisor Agent, compreso il numero di prodotti da suggerire, come gestire gli articoli esauriti, come presentare confronti tra prodotti e come incorporare i dati del profilo cliente (cronologia degli acquisti, comportamento di navigazione) nella classificazione dei consigli.

**Per L&#39;Opzione B (Site Advisory):**
Focus sull’indicizzazione del contenuto del sito con mappatura della gerarchia delle pagine. Configura la logica di navigazione dell&#39;agente Site Advisory e spiega come interpretare l&#39;intento del visitatore, quali categorie di contenuto assegnare la priorità, come gestire le richieste di navigazione ambigue e come adattare i suggerimenti in base al contesto della pagina corrente del visitatore e al comportamento della sessione.

**Per L&#39;Opzione C (Combinata):**
Configura sia le origini di contenuto del catalogo dei prodotti che quelle del sito. Assicurati che la logica di indirizzamento dei contenuti assegni correttamente il contenuto alla specializzazione appropriata e che i riferimenti incrociati tra il contenuto del prodotto e il contenuto di navigazione del sito siano mappati correttamente.

**Documentazione di Experience League:**

- [Configurazione contenuto Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge product advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)
- [Brand Concierge site advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)
- [Panoramica sulle origini](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)

### Fase 4: Distribuzione dell’esperienza conversazionale

**Funzione applicazione:** [!DNL Brand Concierge]: distribuzione esperienza conversazionale, gestione flusso codice basso, handoff agente live; [!DNL RT-CDP]: ricerca profilo in tempo reale

Distribuisci l’esperienza di conversazione sulle proprietà digitali di Target, tra cui la configurazione dei canali, la personalizzazione dei widget, l’integrazione della ricerca di profili per la personalizzazione, le regole di handoff degli agenti live e gli strumenti low-code per la gestione dei contenuti continua.

#### Decisione: canale di distribuzione

Determina a quali canali distribuire l’esperienza di conversazione.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Web (widget incorporato) | La proprietà web principale è il punto di contatto principale del cliente | Punto di partenza più comune; richiede l&#39;integrazione di [!DNL Web SDK]; supporta sia i visitatori anonimi che autenticati |
| App mobile (integrazione SDK) | L’app mobile è un canale significativo di coinvolgimento dei clienti | Richiede l&#39;integrazione di [!DNL Mobile SDK]. Considerare i vincoli di spazio su schermo per l&#39;interfaccia utente di conversazione |
| Distribuzione personalizzata di SDK | L&#39;esperienza conversazionale deve essere incorporata in un&#39;applicazione personalizzata, un chiosco o una proprietà digitale non standard | Massima flessibilità; richiede un maggiore impegno nello sviluppo; ideale per chioschi in-store o piattaforme proprietarie |
| Distribuzione multicanale | Esperienza conversazionale necessaria simultaneamente su web, dispositivi mobili e altri canali | Massima portata; richiede una governance del brand coerente tra i canali; ove possibile, il contesto della conversazione deve persistere tra i canali |

#### Decisione: approfondimento Personalization per le conversazioni

Determina la quantità di dati del profilo cliente che l’agente deve utilizzare per personalizzare le conversazioni.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo anonimo (contesto sessione) | Approccio basato sulla privacy o quando la maggior parte dei visitatori non è identificata | Utilizza solo segnali comportamentali durante la sessione; non è richiesta alcuna ricerca di profilo; è adatto per l’individuazione di prodotti anonimi |
| In base al profilo (visitatori autenticati) | I visitatori vengono in genere connessi e formulano consigli personalizzati in base al valore aggiunto della cronologia | Richiede la ricerca del profilo in tempo reale tramite [!DNL RT-CDP]; qualità dei consigli notevolmente migliore per i clienti noti |
| Personalizzazione progressiva | Combinazione di anonimato e autenticato con la creazione progressiva del profilo durante la conversazione | Inizia con il contesto della sessione; si arricchisce quando il visitatore fornisce informazioni o si autentica; bilancia privacy e personalizzazione |

#### Decisione: configurazione handoff dell’agente live

Stabilisci se le conversazioni devono essere scalabili per agenti umani vivi.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Nessuna consegna (solo self-service) | L’agente di IA può gestire tutti i tipi di conversazione previsti, oppure gli agenti live non sono disponibili | Distribuzione più semplice; può frustrare i visitatori con esigenze complesse; adatta per scenari di navigazione del prodotto a basso rischio |
| Handoff basato su regole | I trigger specifici dovrebbero passare agli agenti live (ad esempio, rilevamento dei reclami, clienti di alto valore, richieste complesse) | Comportamento di escalation prevedibile; richiede la definizione di regole di escalation e trigger; richiede l’integrazione della piattaforma dell’agente live |
| Consegna richiesta dal visitatore | I visitatori possono richiedere un agente attivo in qualsiasi punto della conversazione | Migliore esperienza del cliente; richiede personale agente sempre disponibile o gestione delle code; il contesto di conversazione deve essere trasferito |

#### Distribuire l’esperienza di conversazione

**Navigazione interfaccia utente:** [!DNL Experience Platform] > Assistente IA > [!DNL Brand Concierge] > Distribuzione

Dettagli configurazione chiave:

- Configura l&#39;aspetto del widget conversazionale: posizione, combinazione di colori, avatar, messaggio di benvenuto e stile di interazione (testo, voce o entrambi)
- Integrare con [!DNL Web SDK] o [!DNL Mobile SDK] per l&#39;acquisizione degli eventi e la risoluzione dei profili
- Configura la ricerca dei profili in tempo reale per accedere agli attributi del cliente, alle iscrizioni ai segmenti e alle attività recenti durante le conversazioni
- Configurare l’integrazione dell’handoff degli agenti live con la piattaforma del contact center, inclusi il protocollo di trasferimento del contesto, il routing della coda e la notifica degli agenti
- Abilita gli strumenti di gestione del flusso di codice basso per i team di marketing per aggiornare gli avvii delle conversazioni, i messaggi promozionali, i contenuti stagionali e le varianti di flusso senza il coinvolgimento degli sviluppatori
- Configurare le regole di persistenza delle sessioni di conversazione: per quanto tempo viene mantenuta la cronologia delle conversazioni, se le conversazioni possono riprendere tra sessioni diverse e continuità delle conversazioni tra dispositivi

**Documentazione di Experience League:**

- [Distribuzione Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Panoramica dell’API del server Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Endpoint &quot;profile API entities&quot;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/api/entities)
- [Panoramica del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Fase 5: Arricchimento del profilo

**Funzione applicazione:** [!DNL Brand Concierge]: Arricchimento del profilo conversazionale; [!DNL RT-CDP]: Arricchimento del profilo, Valutazione del pubblico

Configura la pipeline di acquisizione e arricchimento che restituisce i segnali conversazionali al profilo cliente unificato di AEP. Ciò include la mappatura degli eventi di conversazione su XDM, l’estrazione dei segnali di intento e di sentiment, la creazione di attributi calcolati dai dati conversazionali e la creazione di tipi di pubblico basati su comportamenti conversazionali.

#### Decisione: ambito di acquisizione del segnale conversational

Determina quali segnali conversazionali devono essere acquisiti e scritti nel profilo cliente.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo segnali di coinvolgimento di base | Arricchimento minimo del profilo; acquisisci lo stato di inizio, fine, durata e completamento della conversazione | Volume di dati più basso; sufficiente per analisi di base; valore di personalizzazione limitato |
| Segnali intento e preferenza | Acquisire gli interessi di prodotto dedotti, le preferenze dichiarate e le categorie di argomenti discusse | Valore di personalizzazione elevato; volume di dati moderato; più comunemente consigliato |
| Acquisizione completa del segnale | Acquisire finalità, sentiment, interazioni di prodotto, risposte ai consigli, eventi di handoff e punteggi di feedback | Arricchimento del profilo più completo; volume di dati più elevato; abilita analisi avanzate e personalizzazione basata su apprendimento automatico |

#### Decisione: Creazione di tipi di pubblico da dati conversazionali

Determina se i tipi di pubblico devono essere creati in base ai comportamenti di conversazione per l’attivazione a valle.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Nessun pubblico di conversazione | Dati conversazionali utilizzati solo per analisi, non per attivazione pubblico | Approccio più semplice; adatto se le conversazioni sono aggiuntive ai canali di coinvolgimento esistenti |
| Pubblico basato su intento | Creare tipi di pubblico in base agli interessi dichiarati dei prodotti o agli intenti di navigazione dalle conversazioni | Abilita il retargeting dei visitatori che hanno espresso interesse ma non hanno convertito; valore alto per commerce |
| Tipi di pubblico comportamentali | Crea tipi di pubblico in base ai pattern di coinvolgimento delle conversazioni (ad esempio, coinvolgimento elevato, conversazione abbandonata, visite ripetute) | Consente l&#39;orchestrazione del percorso basata sulle conversazioni e il follow-up su più canali |

#### Configurare l’arricchimento del profilo

**Navigazione interfaccia utente:** [!DNL Experience Platform] > Cliente > Profili > Attributi calcolati (per segnali derivati); Cliente > Tipi di pubblico > Crea pubblico (per tipi di pubblico conversazionali)

Dettagli configurazione chiave:

- Mappa gli eventi di conversazione ai campi dello schema XDM ExperienceEvent che acquisiscono l’ID della conversazione, il conteggio dei messaggi, gli argomenti trattati, i prodotti a cui si fa riferimento, i punteggi di sentiment e lo stato della risoluzione
- Configura l&#39;arricchimento del profilo [!DNL Brand Concierge] per scrivere i segnali di intento e preferenze nel profilo unificato
- Creazione di attributi calcolati dai dati dell’evento di conversazione: conversazioni totali (durata), interesse dominante per la categoria di prodotto (30 giorni), punteggio medio di sentiment (90 giorni), tasso di conversione da conversazione ad acquisto
- Definisci i segmenti di pubblico in streaming o in batch in base ai segnali conversazionali per l’attivazione a valle (ad esempio, &quot;Visitatori che hanno discusso della Categoria di prodotto X negli ultimi 7 giorni ma non hanno acquistato&quot;)
- Convalidare l’arricchimento del profilo ricercando profili di esempio per confermare che gli attributi conversazionali siano compilati

**Documentazione di Experience League:**

- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Guida dell’interfaccia utente attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Panoramica del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Fase 6: analisi e ottimizzazione

**Funzione applicazione:** [!DNL Brand Concierge]: Conversational Analytics

Imposta dashboard di analisi e reporting per misurare le prestazioni dell’esperienza di conversazione, identificare opportunità di ottimizzazione e tracciare i KPI. Ciò include analisi integrate di [!DNL Brand Concierge], integrazione opzionale di [!DNL CJA] per l&#39;impact analysis delle conversazioni tra canali e flussi di lavoro di ottimizzazione continui.

#### Decisione: profondità di Analytics

Determina il livello di analisi conversazionale necessario.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Analisi integrata di [!DNL Brand Concierge] | È sufficiente generare rapporti standard sul volume di conversazione, sul coinvolgimento, sulla soddisfazione e sulla conversione | Più veloce da attivare; copre i KPI di base; correlazione cross-channel limitata |
| Integrazione di [!DNL Brand Concierge] + [!DNL CJA] | Analisi cross-channel necessaria per comprendere in che modo le conversazioni influenzano percorsi di clienti più ampi | Richiede la connessione [!DNL CJA] e la configurazione della visualizzazione dati; abilita l&#39;analisi dell&#39;attribuzione tra conversazioni e altri canali |
| Stack di analisi completo ([!DNL Brand Concierge] + [!DNL CJA] + dashboard personalizzati) | Reporting a livello esecutivo, modellazione di attribuzione avanzata e creazione di tipi di pubblico personalizzati da approfondimenti di Analytics | Massima capacità analitica; richiede [!DNL CJA] competenze; consente l&#39;ottimizzazione delle conversazioni basate sui dati |

#### Configurare analisi e ottimizzazione

**Navigazione interfaccia utente:** [!DNL Experience Platform] > Assistente IA > [!DNL Brand Concierge] > Analytics; [!DNL Analytics Platform] > Workspace (per [!DNL CJA])

Dettagli configurazione chiave:

- Rivedi le dashboard di analisi integrate di [!DNL Brand Concierge]: tendenze del volume di conversazione, tasso di coinvolgimento, tasso di completamento, punteggi CSAT, tasso di accettazione dei consigli e frequenza di handoff
- Configurare la connessione [!DNL CJA] per includere i set di dati dell&#39;evento di conversazione per l&#39;analisi cross-channel (se si sceglie l&#39;integrazione [!DNL CJA])
- Genera l&#39;analisi dell&#39;area di lavoro [!DNL CJA] per l&#39;attribuzione da conversazione a conversione, identificando gli argomenti di conversazione correlati al comportamento d&#39;acquisto
- Impostare il monitoraggio della qualità della conversazione: tenere traccia degli argomenti in cui l&#39;agente ha difficoltà, delle domande comuni senza risposta e delle tendenze dei sentiment nel tempo
- Definire i flussi di lavoro di ottimizzazione: frequenza di revisione regolare per gli aggiornamenti sulla governance del brand, i trigger di aggiornamento dei contenuti e i miglioramenti del flusso di conversazione in base agli approfondimenti di Analytics

**Documentazione di Experience League:**

- [analisi Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Panoramica di CJA Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Creare o modificare una connessione CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Creare o modificare una visualizzazione dati di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)

## Considerazioni sull’implementazione

Le sezioni seguenti descrivono i guardrail, le insidie comuni, le best practice e le decisioni di compromesso da tenere presenti durante l’implementazione.

### Guardrail e limiti

- [!DNL Brand Concierge] esperienze conversazionali sono soggette ai limiti di velocità di generazione della risposta di IA; la capacità di conversazione simultanea dipende dal livello di adesione
- La ricerca del profilo in tempo reale durante le conversazioni è soggetta ai limiti di velocità API del profilo per sandbox — [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- L&#39;acquisizione dei dati di evento conversazionale segue i limiti standard di acquisizione in streaming di AEP — [Guardrail di acquisizione](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- La dimensione del catalogo dei prodotti e il volume dell&#39;indice di contenuto sono soggetti ai limiti di integrazione dei contenuti di [!DNL Brand Concierge]
- Un massimo di 25 attributi calcolati per sandbox si applica alle aggregazioni di segnali conversazionali — [Guardrail attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- Un massimo di 4.000 definizioni di segmenti per sandbox si applica ai tipi di pubblico per conversazione — [Guardrail di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### Insidie comuni

- **Definizione insufficiente di brand governance:** la distribuzione senza una configurazione completa di brand governance comporta risposte off-brand che danneggiano la fiducia dei clienti. Investire molto tempo nella Fase 2 per definire toni, limiti e regole di escalation prima della distribuzione.
- **Dati obsoleti del catalogo dei prodotti:** i consigli di Product Advisor basati su dati obsoleti relativi a inventario, prezzi o disponibilità scoraggiano i clienti ed erodono la fiducia. Stabilisci pipeline automatizzate di aggiornamento del contenuto con controlli di convalida.
- **Trigger di un coinvolgimento proattivo troppo aggressivo:** L&#39;impostazione di trigger comportamentali troppo aggressivi (ad esempio, l&#39;attivazione della conversazione dopo 3 secondi sulla pagina) infastidisce i visitatori e aumenta le percentuali di mancato recapito. Inizia con trigger conservativi e ottimizza in base ai dati di coinvolgimento.
- **Se si ignora l&#39;esperienza di un visitatore anonimo:** se si focalizza la personalizzazione solo sui visitatori autenticati, la maggior parte del traffico viene ignorata. Progetta flussi di conversazione che forniscano valore ai visitatori anonimi utilizzando segnali comportamentali durante la sessione.
- **Ignorare la configurazione di arricchimento del profilo:** La distribuzione di conversazioni senza acquisire i segnali nel profilo comporta la perdita di dati preziosi sulle finalità e sulle preferenze. Configura l’arricchimento del profilo in parallelo con la distribuzione, non come ulteriore considerazione.
- **Ignorare l&#39;esperienza di handoff di agenti live:** le esperienze di handoff scadenti (contesto perso, domande ripetute, tempi di attesa lunghi) danneggiano l&#39;esperienza di conversazione complessiva più che non offrire handoff. Test end-to-end del flusso di handoff completo prima dell’avvio.

### Best practice

- Iniziare con una specializzazione con un singolo agente (Product Advisor o Site Advisory) ed espanderla dopo aver stabilito le prestazioni di base.
- Conduci workshop sulla governance del brand con le parti interessate del marketing, legali e della customer experience prima di configurare i guardrail.
- Utilizzare la personalizzazione progressiva: avvia le conversazioni con risposte basate sul contesto di sessione e approfondisci la personalizzazione man mano che il visitatore fornisce informazioni o si autentica.
- Implementa test A/B di avvii di conversazione, prompt e formati di presentazione dei consigli utilizzando gli strumenti di gestione del flusso a basso codice.
- Pianifica una revisione regolare (settimanale o bisettimanale) dell’analisi delle conversazioni per identificare le lacune nei contenuti, i punti di errore comuni e le opportunità di ottimizzazione.
- Crea un ciclo di feedback tra gli aggiornamenti di analisi conversazionale e brand governance: utilizza i dati di conversazione per perfezionare i toni, aggiungere nuovi argomenti approvati e regolare le regole di escalation.
- Monitora le tendenze dei sentiment di conversazione come sistema di allarme rapido per problemi di prodotto, problemi del sito o cambiamenti di percezione del brand.
- Progettare flussi di conversazione che catturino naturalmente segnali che arricchiscono il profilo senza rendere l&#39;interazione come un&#39;interrogazione.

### Decisioni di compromesso

>[!NOTE]
>Le seguenti decisioni di compromesso devono essere valutate in base ai requisiti e ai vincoli specifici dell’organizzazione.

**Profondità della personalizzazione della conversazione rispetto alla semplicità della privacy**

Un’integrazione più approfondita dei profili consente conversazioni più personalizzate ed efficaci, ma aumenta la complessità della raccolta dei dati, i requisiti di consenso e il carico di conformità sulla privacy.

- **La personalizzazione approfondita favorisce:** tassi di conversione più elevati, migliore qualità dei consigli, arricchimento del profilo più ricco e conversazioni più coinvolgenti per i clienti fidelizzati
- **La semplicità della privacy favorisce:** distribuzione più rapida, gestione più semplice del consenso, riduzione dei rischi normativi e posizionamento del brand sulla base della privacy
- **Consiglio:** inizia con una personalizzazione progressiva che funziona bene per i visitatori anonimi e aggiunge una personalizzazione basata sul profilo per le sessioni autenticate. Questo offre valore a tutti i livelli di identificazione, mantenendo al contempo gestibile la conformità alla privacy. Implementa l’acquisizione del consenso per la profilazione conversazionale in linea con i framework di consenso esistenti.

**Rigorosità della governance del brand rispetto alla naturalità della conversazione**

Rigorosi guardrail di brand governance garantiscono che ogni risposta sia allineata agli standard del brand, ma vincoli eccessivamente rigidi fanno sentire le conversazioni robotiche e riducono il coinvolgimento.

- **La governance rigida favorisce:** la sicurezza del marchio, la conformità alle normative, la messaggistica coerente e il comportamento prevedibile degli agenti
- **La governance flessibile favorisce:** Flusso di conversazione naturale, maggiore coinvolgimento, migliore soddisfazione dei clienti e la capacità di gestire una più ampia gamma di query
- **Consiglio:** inizia con una governance moderata e stringi o allenta in base all&#39;analisi delle conversazioni. Monitora il tasso di risposte &quot;Non posso fare a meno di questo&quot; come indicatore di eccessiva restrizione. Utilizza gli strumenti di gestione del flusso low-code per eseguire rapidamente l’iterazione sulle impostazioni di governance senza il coinvolgimento degli sviluppatori.

**Aggiornamento dei contenuti in tempo reale rispetto alle prestazioni del sistema**

La sincronizzazione dei contenuti in tempo reale garantisce che l&#39;agente disponga sempre di dati correnti sui prodotti e sui contenuti, ma l&#39;aggiornamento continuo consuma più risorse dell&#39;infrastruttura e può introdurre una latenza.

- **L&#39;aggiornamento in tempo reale favorisce:** la precisione per i consigli sensibili all&#39;inventario, le promozioni sensibili al tempo e la rapida modifica dei contenuti
- **Aggiornamenti pianificati favoriscono:** stabilità del sistema, consumo prevedibile delle risorse e riduzione dei costi dell&#39;infrastruttura
- **Consiglio:** Utilizzare l&#39;aggiornamento giornaliero dei contenuti come impostazione predefinita, con l&#39;aggiornamento quasi in tempo reale solo per la disponibilità dell&#39;inventario e i dati relativi ai prezzi che influiscono materialmente sulla customer experience. Monitora le metriche di accuratezza dei contenuti per determinare se la frequenza di aggiornamento è adeguata.

**Acquisizione completa del segnale rispetto al sovraccarico di gestione dei dati**

L&#39;acquisizione di ogni segnale di conversazione fornisce l&#39;arricchimento e l&#39;analisi dei profili più avanzati, ma aumenta il volume dei dati, i costi di storage e la complessità di governance.

- **L&#39;acquisizione completa del segnale favorisce:** analisi avanzate, apprendimento del modello ML, arricchimento completo del profilo e valore massimo di personalizzazione a valle
- **L&#39;acquisizione selettiva favorisce:** riduzione dei costi di storage, semplificazione della governance dei dati, prestazioni di ricerca dei profili più veloci e maggiore conformità ai principi di minimizzazione dei dati
- **Consiglio:** Iniziare con l&#39;acquisizione del segnale di intento e preferenza (la via di mezzo) ed espanderla fino all&#39;acquisizione completa del segnale solo dopo aver verificato che i dati aggiuntivi creino un valore downstream misurabile. Applicazione di regole di scadenza dei dataset ai dati degli eventi di conversazione per gestire la crescita dello storage.

## Documentazione correlata

Le risorse seguenti forniscono informazioni aggiuntive per l’implementazione di questo modello di caso d’uso.

**[!DNL Brand Concierge]**

- [Panoramica di Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge product advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)
- [Brand Concierge site advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)
- [Panoramica dell’Assistente AI](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/home)

**[!DNL Adobe Experience Platform]**

- [Panoramica di AEP](https://experienceleague.adobe.com/en/docs/experience-platform/landing/home)
- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Panoramica del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

**Raccolta e integrazione dei dati**

- [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Panoramica di Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Panoramica dell’API del server Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Panoramica sulle origini](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)

**Identità e profilo**

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)

**Tipi di pubblico e segmentazione**

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

**Governance dei dati e privacy**

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Gruppo di campi Consenso e preferenze](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Panoramica di Privacy Service](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/home)
- [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

**Monitoraggio e osservabilità**

- [Panoramica di Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
- [Panoramica degli avvisi](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

**Analisi e reporting**

- [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Panoramica delle connessioni CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Panoramica delle visualizzazioni dati di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

**Guardrail**

- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Guardrail di acquisizione](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Guardrail di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
