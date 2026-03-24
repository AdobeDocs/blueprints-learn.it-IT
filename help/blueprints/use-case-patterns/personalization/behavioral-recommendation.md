---
title: Consigli comportamentali
description: Scopri come generare consigli su elementi e contenuti utilizzando strategie di selezione e modelli di classificazione.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: db16e773-e0da-46c4-9fa5-d16f04feb46b
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7545'
ht-degree: 2%

---

# Raccomandazioni comportamentali

Questa guida illustra come implementare i consigli sui contenuti e i prodotti comportamentali utilizzando [!DNL Adobe Journey Optimizer] (AJO) Decisioning, [!DNL Real-Time Customer Data Platform] (RT-CDP) e [!DNL Adobe Experience Platform] (AEP). È progettato per architetti di soluzioni, tecnici di marketing e ingegneri dell’implementazione che devono fornire esperienze di consigli personalizzate su canali web, app mobili ed e-mail.

Presenta tutte le opzioni di implementazione valide, considerazioni sulle decisioni in ogni fase e collegamenti alla documentazione di [!DNL Adobe Experience League]. La funzione Consigli comportamentali genera consigli a livello di elemento o di contenuto utilizzando segnali comportamentali (visualizzazioni di prodotto, acquisti, interazioni di contenuto, query di ricerca) combinati con strategie di selezione e modelli di classificazione di AJO Decisioning. A differenza di offer decisioning, che governa un set limitato di offerte, promozioni o incentivi utilizzando regole di idoneità e vincoli di business, questo modello opera su cataloghi di articoli di grandi dimensioni in continua evoluzione (prodotti, articoli, video) in cui la selezione è guidata da segnali di affinità comportamentale piuttosto che da idoneità regolamentata.

## Panoramica del caso d’uso

Le organizzazioni con cataloghi di prodotti, librerie di contenuti o librerie multimediali devono rendere visibili a ogni visitatore gli elementi più rilevanti in base alla cronologia comportamentale e all’attività durante la sessione. Che si tratti di un carosello &quot;consigliato per te&quot; su una pagina home, di un widget di cross-selling su una pagina di dettagli del prodotto o di consigli di prodotto incorporati in una campagna e-mail, la sfida di fondo è la stessa: abbinare il profilo comportamentale di ogni visitatore agli elementi più rilevanti di un catalogo, quindi fornire tali consigli nel canale giusto al momento giusto.

Questo modello affronta tale sfida acquisendo segnali comportamentali in tempo reale tramite [!DNL Web SDK] o [!DNL Mobile SDK], elaborandoli tramite strategie di selezione di AJO Decisioning che combinano gli attributi degli elementi con il contesto comportamentale e distribuendo gli elementi consigliati tramite canali web, in-app o e-mail. I modelli di classificazione possono essere basati su formule (ad esempio, in base al punteggio di affinità tra categorie) o classificati in base all’intelligenza artificiale (ad esempio, modello di consigli personalizzato). Il modello gestisce anche scenari di avvio a freddo per nuovi visitatori senza cronologia comportamentale configurando consigli di fallback.

Il pubblico di destinazione di questo modello include i team di merchandising di e-commerce, i team di personalizzazione dei contenuti e i team di esperienza digitale che desiderano migliorare il coinvolgimento, la conversione e il valore medio dell’ordine attraverso consigli personalizzati basati sul comportamento effettivo degli utenti.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### [Incrementa le vendite incrociate e incrementa i ricavi](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)

Promuovere prodotti o servizi complementari e di alta qualità ai clienti esistenti in base al comportamento e alla cronologia degli acquisti.

**KPI:** % vendite incrociate/upselling, ricavi incrementali, valore ciclo di vita cliente

### [Aumentare i tassi di conversione](../../business-objectives/revenue-monetization/increase-conversion-rates.md)

Migliora la percentuale di visitatori e potenziali clienti che completano le azioni desiderate, ad esempio acquisti, iscrizioni o invii di moduli.

**KPI:** Tassi di conversione, Conversione lead, Costo per lead

### [Distribuisci esperienze cliente personalizzate](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

Personalizza contenuti, offerte e messaggi in base a preferenze, comportamenti e fasi del ciclo di vita individuali.

**KPI:** coinvolgimento, tassi di conversione, soddisfazione del cliente (CSAT)

## Esempi di casi d’uso tattici

Di seguito sono riportate le implementazioni tattiche comuni di questo modello:

- Widget di cross-selling del prodotto sulla pagina dei dettagli del prodotto (&quot;anche i clienti hanno acquistato&quot;)
- Carosello &quot;Consigliato per te&quot; sulla home page in base alla cronologia dei browser
- Consigli sui contenuti sul sito multimediale in base al comportamento di lettura
- Widget &quot;Visualizzato di recente&quot; combinato con elementi simili
- Consigli sui prodotti complementari post-acquisto
- Invia raccomandazioni di prodotti e-mail in base all’affinità comportamentale
- Raccomandazioni specifiche per categoria in base al comportamento di navigazione nella sessione
- Nuova classificazione dei risultati di ricerca in base ai segnali comportamentali

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare l’efficacia delle implementazioni di consigli comportamentali.

| KPI | Approccio di misurazione |
| --- | --- |
| Frequenza di click-through dei consigli (CTR) | Clic sugli articoli consigliati divisi per impression di consigli |
| Tasso di conversione consigli | Acquisti o azioni desiderate dai clic sui consigli divisi per il totale dei clic sui consigli |
| Ricavi influenzati dalla funzione Consigli | Ricavi totali da ordini che includevano almeno un prodotto basato su consigli |
| Incremento valore medio ordine (AOV) | Aumento del valore medio dell’ordine per le sessioni che richiedono consigli rispetto a quelle senza |
| Articoli per ordine | Numero di elementi per ordine per le sessioni di consigli |
| Copertura consigli | Percentuale di visualizzazioni di pagina o sessioni idonee che hanno ricevuto consigli personalizzati (non di fallback) |
| Cold-Start Fallback Rate | Percentage of recommendation requests served by fallback logic due to insufficient behavioral history |

## Schema del caso d’uso

**Consigli comportamentali**

Generate item-level or content-level recommendations based on behavioral signals, using AJO Decisioning selection strategies and ranking models to serve contextual content.

**Function chain:** Behavioral Signal Ingestion > Decisioning Strategy Evaluation > Recommendation Delivery > Reporting

See the Pattern Composition section under Implementation Considerations for guidance on combining patterns.

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Adobe Journey Optimizer] (AJO) Decisioning** -- Selection strategies, ranking models, item catalogs, and decision policies that evaluate behavioral signals and return the most relevant items for each visitor
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** -- Behavioral profile data accumulation, audience evaluation for recommendation scoping, and computed attributes for behavioral affinity scoring
- **[!DNL Adobe Experience Platform] (AEP)** -- Behavioral event ingestion via [!DNL Web SDK] and [!DNL Mobile SDK], [!DNL Edge Network] processing, XDM schema management for event and catalog data

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve esistere | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Presunto sul posto | Sandbox di AJO con autorizzazioni Decisioning abilitate. User roles provisioned with access to item catalog management, selection strategy configuration, and channel surface administration. | [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home), [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/it/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Obbligatorio | Experience Event schema capturing behavioral signals (product views, add-to-cart, purchases, content interactions) with item/product identifiers. Item catalog schema (product attributes, categories, images, prices) for the recommendation item set. Schema di profilo con campi di identità. Tutti gli schemi abilitati per [!DNL Real-Time Customer Profile]. | [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home), [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/schema/composition), [Crea un set di dati](https://experienceleague.adobe.com/it/docs/experience-platform/catalog/datasets/create) |
| Origini dati e raccolta | Obbligatorio | Lo streaming degli eventi comportamentali in tempo reale tramite [!DNL Web SDK] o [!DNL Mobile SDK] è fondamentale. La qualità dei consigli dipende da nuovi segnali comportamentali. I dati del catalogo degli articoli devono essere acquisiti (in batch o in streaming). Gli stream di dati configurati con il servizio AJO abilitato per le decisioni di Edge. | [Panoramica di Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/home), [Panoramica di Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview), [Configura flussi di dati](https://experienceleague.adobe.com/it/docs/experience-platform/datastreams/configure) |
| Configurazione identità e profilo | Obbligatorio | I segnali comportamentali devono essere associati a un’identità (nota o anonima tramite ECID) per creare profili comportamentali. Per i consigli dei visitatori noti, è necessario configurare l’identità autenticata (ID del sistema di gestione delle relazioni con i clienti, e-mail). Criterio di unione attivo su Edge per la distribuzione di consigli in tempo reale. | [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home), [Panoramica dei criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview) |
| Definizione e segmentazione del pubblico | Consigliato | I tipi di pubblico possono essere utilizzati per formulare raccomandazioni (ad esempio, per consigliare solo prodotti premium ai membri premium) o per filtrarli. Non strettamente necessario se le raccomandazioni sono puramente comportamentali. Obbligatorio per i consigli basati su e-mail (opzione C) per definire il pubblico target. | [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home), [Guida dell&#39;interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Consigliato | Attributi calcolati come i punteggi di affinità tra categorie, la frequenza di interazione con il prodotto, l’attualità degli acquisti e la spesa totale migliorano la qualità della classificazione dei consigli. [!DNL Customer AI] i punteggi di tendenza possono migliorare ulteriormente la rilevanza prevedendo la probabilità di acquisto. | [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview), [Panoramica di IA per l&#39;analisi dei clienti](https://experienceleague.adobe.com/it/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Data Lifecycle Management | Consigliato | I dati relativi agli eventi comportamentali devono prevedere politiche di scadenza appropriate; la rilevanza delle raccomandazioni si riduce con dati obsoleti. L’impostazione di criteri di scadenza dei set di dati sui set di dati degli eventi comportamentali garantisce l’aggiornamento e gestisce l’archiviazione. L’applicazione del consenso garantisce l’utilizzo conforme dei dati comportamentali. | [Scadenze set di dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-lifecycle/ui/dataset-expiration), [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/it/docs/experience-platform/data-lifecycle/home) |
| Etichettatura e applicazione dell’utilizzo dati | Consigliato | Le etichette di governance sui dati comportamentali garantiscono l’utilizzo conforme della cronologia delle interazioni per i consigli. Particolarmente importante quando i dati comportamentali includono modelli di navigazione, cronologia degli acquisti o segnali di interesse sui prodotti finanziari o sanitari. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home), [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview) |
| Monitoraggio e osservabilità | Consigliato | È necessario monitorare la latenza di consegna dei consigli, i tassi di fallback e lo stato di acquisizione del catalogo articoli. Gli avvisi sugli errori di acquisizione degli eventi comportamentali e sugli errori di decisione contribuiscono a mantenere la qualità dei consigli. | [Panoramica di Observability Insights](https://experienceleague.adobe.com/it/docs/experience-platform/observability/home), [Panoramica degli avvisi](https://experienceleague.adobe.com/it/docs/experience-platform/observability/alerts/overview) |
| Reporting e analisi | Incluso | Il reporting sulle prestazioni dei consigli fa parte del passaggio 4 della catena di funzioni. [!DNL Customer Journey Analytics] l’analisi dell’efficacia dei consigli, dell’impatto sui ricavi e delle prestazioni a livello di elemento tra superfici e segmenti fornisce informazioni approfondite sull’ottimizzazione. | [Panoramica di CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-overview/cja-overview), [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/home) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Journey Optimizer] (AJO)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Decisioni | Impostazione catalogo articoli e strategia di selezione | Configurare cataloghi di elementi (elementi decisionali), strategie di selezione con modelli di classificazione comportamentale, regole di filtro e consigli di fallback |
| Configurazione canali | Configurazione canale e superficie | Configurare superfici di consegna per canali web (esperienze basate su codice), in-app, schede di contenuto o e-mail in cui verrà eseguito il rendering dei consigli |
| Authoring dei messaggi | Configurazione di contenuto e consegna | Progettare modelli di rendering dei consigli, layout di visualizzazione degli elementi ed espressioni di personalizzazione per gli elementi consigliati |
| Reporting e analisi delle prestazioni | Reporting e ottimizzazione | Monitorare le metriche di click-through, conversione e ricavi per i consigli tramite i rapporti nativi di AJO e l&#39;integrazione di [!DNL Customer Journey Analytics] |

### [!DNL Real-Time CDP] (RT-CDP)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Valutazione del pubblico | Ambito pubblico (opzione C) | Valuta i segmenti di pubblico utilizzati per definire i consigli o la popolazione target per le campagne e-mail di consigli |
| Arricchimento del profilo | Arricchimento del segnale comportamentale | Arricchisci i profili con attributi calcolati (punteggi di affinità tra categorie, frequenza di interazione) per migliorare la classificazione dei consigli |

## Prerequisiti

Completa quanto segue prima di iniziare l’implementazione:

- [ Provisioning di ] AJO Decisioning eseguito e abilitato nella sandbox di destinazione
- [ ] [!DNL Web SDK] o [!DNL Mobile SDK] è distribuito e sta raccogliendo eventi comportamentali con identificatori di prodotto/contenuto
- [ ] I dati del catalogo prodotti o contenuti sono disponibili per l&#39;acquisizione (nome prodotto, categoria, prezzo, URL immagine, disponibilità)
- [ ] Gli schemi di eventi comportamentali includono identificatori di elementi/prodotti collegati agli elementi del catalogo
- [ Lo stream di dati ] è configurato con il servizio [!DNL Adobe Journey Optimizer] abilitato (necessario per le decisioni di Edge)
- [ Il criterio di unione ] con `isActiveOnEdge: true` è configurato (obbligatorio per i consigli Web/app in tempo reale)
- [ ] Per consigli e-mail (Opzione C): la superficie del canale e-mail è configurata e convalidata
- [ ] Per consigli e-mail (opzione C): il pubblico di destinazione è definito e sta valutando

## Opzioni di implementazione

Le opzioni seguenti descrivono diversi approcci per l’implementazione delle raccomandazioni comportamentali. Scegli l’opzione che meglio si adatta ai requisiti dei canali e ai vincoli tecnici.

### Opzione A: consigli web in tempo reale

**Consigliato per:** Consigli per prodotti e contenuti su pagine Web: widget per la cross-selling di pagine di dettagli prodotto, caroselli di consigli per home page, inserzioni personalizzate di pagine categorie e personalizzazione dei risultati di ricerca.

**Funzionamento:**

I segnali comportamentali vengono raccolti in tempo reale tramite [!DNL Web SDK] mentre i visitatori navigano sul sito. Ogni visualizzazione di pagina, interazione del prodotto o query di ricerca viene trasmessa in streaming ad AEP e associata al profilo del visitatore (tramite ECID per i visitatori anonimi o identità autenticata per i visitatori noti). Quando viene caricata una pagina contenente una superficie di consigli, [!DNL Web SDK] richiede una valutazione del decisioning da AJO tramite [!DNL Edge Network]. Il motore delle decisioni valuta il profilo comportamentale del visitatore in base alla strategia di selezione, applica la logica di classificazione, esclude gli articoli non idonei (già acquistati, esauriti) e restituisce gli articoli consigliati.

I consigli vengono sottoposti a rendering sulla pagina tramite esperienze basate su codice o superfici di canali web. Il rendering può essere un carosello, una griglia, un widget a elemento singolo o qualsiasi layout personalizzato definito nel modello di consigli. Gli eventi di impression e clic vengono tracciati automaticamente in AEP per la generazione di rapporti sulle prestazioni.

**Considerazioni chiave:**

- Edge Decisioning richiede che il criterio di unione sia attivo su Edge
- La latenza dei consigli dipende dal tempo di risposta [!DNL Edge Network] (SLA inferiore a 500 ms per richieste con ambito singolo)
- I visitatori anonimi ricevono consigli in base al comportamento durante la sessione; i visitatori noti beneficiano della cronologia comportamentale tra sessioni diverse
- I visitatori con avvio a freddo senza cronologia comportamentale ricevono consigli di fallback

**Vantaggi:**

- Personalizzazione in tempo reale basata sul comportamento durante la sessione
- Consegna dei consigli al secondo secondario tramite [!DNL Edge Network]
- Funziona sia per i visitatori anonimi che per quelli noti
- Impression e tracciamento dei clic automatici
- Non è necessario ricaricare la pagina per aggiornare i consigli

**Limitazioni:**

- L’archivio profili di Edge contiene un sottoinsieme di attributi di profilo completi
- Modelli di classificazione complessi con molti attributi di profilo possono richiedere una valutazione lato hub
- Richiede l&#39;implementazione di [!DNL Web SDK] con il tracciamento degli eventi comportamentali

**Experience League:**

- [Distribuire le offerte tramite l’API Edge Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Panoramica di Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/home)

### Opzione B: consigli per le app mobili

**Consigliato per:** consigli di prodotti in-app, feed di contenuti personalizzati, consigli basati su notifiche ed esperienze di e-commerce mobile.

**Funzionamento:**

I segnali comportamentali vengono raccolti tramite [!DNL Mobile SDK] mentre gli utenti interagiscono con l&#39;app. Le visualizzazioni dei prodotti, le interazioni con i contenuti, le ricerche e gli acquisti vengono inviati in streaming ad AEP. Quando viene caricata una schermata contenente una superficie di consigli, [!DNL Mobile SDK] richiede una valutazione del decisioning. I consigli vengono trasmessi tramite messaggi in-app, schede di contenuto o esperienze basate su codice all’interno dell’app mobile.

Le schede di contenuto sono particolarmente indicate per i casi di utilizzo consigliati nelle app mobili, in quanto persistono in un’esperienza simile ai feed, che gli utenti possono consultare quando lo desiderano. I messaggi in-app possono essere utilizzati per consigli contestuali attivati da comportamenti specifici (ad esempio, mostrare prodotti complementari dopo aver aggiunto un elemento al carrello).

**Considerazioni chiave:**

- [!DNL Mobile SDK] deve essere configurato con il tracciamento degli eventi comportamentali per le interazioni rilevanti
- Le schede di contenuto forniscono una superficie di consigli persistente; i messaggi in-app sono temporanei
- Offline behavior tracking requires SDK queue management for deferred event submission
- App store update cycles affect how quickly recommendation rendering changes can be deployed

**Vantaggi:**

- Native mobile experience with smooth, app-integrated recommendation rendering
- Content cards provide a persistent, browsable recommendation feed
- In-app messages enable contextual, behavior-triggered recommendations
- Leverages device-level signals (location, app usage patterns) for enhanced relevance

**Limitazioni:**

- Requires [!DNL Mobile SDK] integration and app development resources
- Rendering changes require app updates (unless using code-based experiences with server-driven layouts)
- Offline periods create gaps in behavioral signal collection

**Experience League:**

- [Panoramica di Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Option C: Email behavioral recommendations

**Best for:** Product recommendations in email campaigns -- abandoned browse emails with viewed product recommendations, post-purchase cross-sell emails, periodic &quot;picks for you&quot; digests, and re-engagement emails with personalized product suggestions.

**Funzionamento:**

Behavioral profile data accumulated from prior sessions informs recommendation selection at email send time or render time. An audience is defined to target the appropriate recipients (e.g., visitors who browsed but did not purchase, customers who made a recent purchase). A campaign or journey is configured to send an email that includes recommendation placements. At send time, AJO Decisioning evaluates each recipient&#39;s behavioral profile against the selection strategy and injects the recommended items into the email content.

This option relies on accumulated behavioral history rather than in-session signals. Computed attributes (category affinity scores, recent product views, purchase frequency) significantly improve recommendation quality for email because they distill behavioral history into profile-level signals that the selection strategy can evaluate efficiently.

**Considerazioni chiave:**

- Email recommendations are evaluated at send time, not open time -- the behavioral profile state at the moment of send determines the recommendations
- Computed attributes are strongly recommended to improve ranking quality
- Email rendering limitations (no JavaScript, limited CSS) constrain recommendation display formats
- Requires a configured and validated email channel surface

**Vantaggi:**

- Leverages full behavioral history across sessions for deeper personalization
- Integrates with existing campaign and journey workflows
- Effective for re-engagement and win-back scenarios where web/app touchpoints are unavailable
- Can include multiple recommendation placements within a single email

**Limitazioni:**

- Recommendations are static at send time -- they do not update when the email is opened
- Email rendering constraints limit recommendation display formats
- Requires audience evaluation and campaign/journey orchestration infrastructure
- Higher implementation complexity due to additional dependencies (channel configuration, audience definition, campaign execution)

**Experience League:**

- [Creare un messaggio e-mail](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/create-email)
- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Confronto delle opzioni

The following table summarizes the key differences between implementation options.

| Criteri | Option A: Web Real-Time | Option B: Mobile App | Option C: Email Behavioral |
| --- | --- | --- | --- |
| Ideale per | Consigli per pagine web (PDP, home page, categoria) | Consigli in-app e feed di contenuti | Campagne e-mail con consigli sui prodotti |
| Sorgente del segnale comportamentale | In sessione + tra sessioni ([!DNL Web SDK]) | Interazioni in-app ([!DNL Mobile SDK]) | Cronologia comportamentale accumulata (profilo) |
| Latenza consigli | Secondi secondari ([!DNL Edge Network]) | Secondi secondari ([!DNL Edge Network]) | Al momento dell’invio (valutazione lato hub) |
| Tipo di visitatore | Anonimo e noto | Noto (utenti dell’app) | Noto (destinatari e-mail) |
| Complessi | Medio | Medium - Alta | Alta |
| Dipendenza canale | [!DNL Web SDK], superficie esperienza basata su codice | [!DNL Mobile SDK], superficie scheda in-app/contenuto | Superficie del canale e-mail, pubblico, campagna/percorso |
| Richiede | Distribuzione [!DNL Web SDK], criterio di unione Edge | Distribuzione [!DNL Mobile SDK], criterio di unione Edge | Superficie e-mail, definizione del pubblico, configurazione della campagna |

### Scegli l’opzione giusta

Utilizza le seguenti indicazioni per selezionare l’opzione migliore per la tua situazione:

- **Inizia con l&#39;opzione A** se il tuo obiettivo principale sono i consigli sui prodotti in tempo reale sul tuo sito Web. Si tratta del punto di partenza più comune e fornisce valore immediato con la minore complessità di implementazione.
- **Scegli l&#39;opzione B** se la tua app mobile è un canale di coinvolgimento primario e i consigli in-app genererebbero un incremento significativo della conversione. L&#39;opzione B può essere eseguita in parallelo con l&#39;opzione A utilizzando le stesse strategie di selezione e gli stessi cataloghi di articoli.
- **Aggiungi l&#39;opzione C** quando desideri estendere i consigli comportamentali nelle campagne e-mail. Questo viene generalmente sovrapposto all’opzione A o B, utilizzando gli stessi cataloghi di elementi e le stesse strategie di selezione, ma con modelli di rendering specifici per e-mail e targeting basato sul pubblico.
- **Combina le opzioni A + C** per un pattern comune: consigli Web in tempo reale per i visitatori attivi, più consigli per e-mail abbandonate durante la navigazione o dopo l&#39;acquisto per i visitatori che se ne vanno senza convertirsi.

## Fasi di implementazione

Le seguenti fasi ti guidano attraverso l’implementazione end-to-end delle raccomandazioni comportamentali.

### Fase 1: configurare lo schema di eventi comportamentali e la raccolta dati

**Funzione applicazione:** AEP: Modellazione e preparazione dati (F2), AEP: Origini dati e raccolta (F3)

Questa fase stabilisce gli schemi XDM, i set di dati e i meccanismi di raccolta dei dati che acquisiscono segnali comportamentali e dati del catalogo degli elementi. Questa base dati è ciò da cui dipende tutta la logica dei consigli.

#### Decisione: progettazione schema evento comportamentale

Quali segnali comportamentali dovrebbero guidare i consigli?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo visualizzazioni prodotto | Semplici consigli per la vendita incrociata/upselling | Minore sforzo di implementazione; profondità di segnale limitata |
| Visualizzazioni prodotto + acquisti | Consigli con logica di esclusione degli acquisti e di cross-selling | Sforzo moderato; abilita il filtro &quot;escludi già acquistato&quot; |
| Suite comportamentale completa (visualizzazioni, acquisti, componenti aggiuntivi al carrello, ricerche, interazioni con i contenuti) | Consigli sofisticati con classificazione a più segnali | Massima qualità del segnale; richiede strumentazione [!DNL Web SDK]/[!DNL Mobile SDK] completa |

#### Decisione: metodo di acquisizione catalogo articoli

Come verrà acquisito il catalogo di prodotti o contenuti in AEP?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Acquisizione in batch tramite connettore di origine | Gli aggiornamenti del catalogo sono periodici (giornalieri/settimanali) | Configurazione semplificata; le modifiche al catalogo non si riflettono in tempo reale |
| Acquisizione in streaming | Il catalogo richiede aggiornamenti quasi in tempo reale (variazioni di prezzo, disponibilità) | Più complesso; assicura che i consigli riflettano l’inventario corrente |
| Caricamento manuale/API | Catalogo di piccole dimensioni con modifiche non frequenti | Configurazione più semplice; non scalabile per cataloghi grandi o dinamici |

**Navigazione interfaccia utente:** Gestione dati > Schemi > Crea schema; Raccolta dati > Flussi di dati > Nuovo flusso di dati

**Dettagli configurazione chiave:**

- Lo schema Evento esperienza deve includere identificatori di prodotto/elemento (SKU, ID prodotto, ID contenuto) nel payload dell’evento
- Lo schema del catalogo articoli deve includere gli attributi utilizzati per filtrare e classificare: categoria, prezzo, URL immagine, stato disponibilità, tag
- Il servizio [!DNL Adobe Journey Optimizer] dello stream di dati deve essere abilitato per le decisioni di Edge
- Le chiamate [!DNL Web SDK] `sendEvent` devono includere dati di interazione prodotto mappati ai campi di e-commerce XDM

**Documentazione di Experience League:**

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home)
- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/schema/composition)
- [Panoramica di Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/home)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/it/docs/experience-platform/datastreams/configure)
- [Define a relationship between two schemas](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/tutorials/relationship-api)

### Fase 2: configurare identità e profilo

**Funzione applicazione:** AEP: configurazione identità e profilo (F4)

This phase sets up identity namespaces, primary identity designations, and merge policies that ensure behavioral signals are correctly associated with visitor profiles and available for real-time recommendation delivery.

#### Decision: Merge policy for Edge decisioning

Does the recommendation use case require real-time Edge evaluation?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Active on Edge merge policy | Options A and B (web and mobile real-time recommendations) | Required for sub-second recommendation delivery; only one Edge merge policy per sandbox |
| Standard merge policy (not on Edge) | Option C only (email recommendations evaluated at send time) | Sufficient for hub-side evaluation; does not consume the Edge merge policy slot |

#### Decisione: identità visitatore anonimo vs. identità visitatore nota

Come devono essere gestiti i segnali comportamentali provenienti da visitatori anonimi?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo ECID (anonimo) | Consigli principalmente per i visitatori anonimi in base al comportamento durante la sessione | Configurazione più semplice; nessuna continuità tra sessioni a meno che il visitatore non si autentichi |
| ECID + identità autenticata (ID CRM, e-mail) | Raccomandazioni tra sessioni per i visitatori noti con unione di identità | Profili comportamentali più completi; richiede un flusso di autenticazione |
| Entrambi con collegamento del grafico delle identità | Percorso completo da anonimo a noto con unione identità | Più completo; richiede la configurazione delle regole di collegamento delle identità |

**Navigazione interfaccia utente:** Identità > Spazi dei nomi identità; Profili > Criteri di unione

**Dettagli configurazione chiave:**

- Lo spazio dei nomi ECID è preconfigurato e utilizzato automaticamente da [!DNL Web SDK] e [!DNL Mobile SDK]
- È necessario creare spazi dei nomi di identità personalizzati (ID CRM, ID fedeltà) per l’identità autenticata
- L’identità primaria nello schema Experience Event deve essere ECID per eventi comportamentali web/mobili
- I criteri di unione devono utilizzare Private Device Graph per l’unione delle identità tra dispositivi diversi

**Documentazione di Experience League:**

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home)
- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview)
- [Regole di collegamento del grafo identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/identity-linking-logic)

### Fase 3: Impostare il catalogo articoli e la strategia di selezione

**Funzione applicazione:** AJO: Decisioning

Questa fase configura il catalogo degli elementi (elementi decisionali), le strategie di selezione che combinano segnali comportamentali con attributi degli elementi per la classificazione, regole di filtro per escludere gli elementi non idonei e consigli di fallback per i profili con avvio a freddo.

#### Decisione: ambito catalogo articoli

Quali articoli sono disponibili per i consigli?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Catalogo dei prodotti (e-commerce) | Consigliare prodotti fisici o digitali per l&#39;acquisto | Gli attributi degli articoli includono prezzo, categoria, disponibilità, immagini |
| Catalogo dei contenuti (media/pubblicazione) | Articoli consigliati, video o contenuti educativi | Gli attributi degli elementi includono argomento, autore, data di pubblicazione e tipo di contenuto |
| Catalogo ibrido | Raccomandazione di prodotti e contenuti | Richiede uno schema di elementi unificato che soddisfi entrambi i tipi |

#### Decisione: approccio di classificazione

Come devono essere classificati gli articoli idonei per determinare i consigli migliori?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Classificazione basata su formule | Cancella la logica di business per la classificazione (ad esempio, ordina per punteggio di affinità tra categorie moltiplicato per la popolarità dell’elemento) | Classificazione trasparente e verificabile; richiede una formula di classificazione definita |
| Classificato in base all’intelligenza artificiale (ottimizzazione automatica) | L’apprendimento automatico dovrebbe determinare una classificazione ottimale in base ai dati di conversione | Richiede almeno 1.000 eventi di conversione per l&#39;apprendimento dei modelli; meno trasparente |
| Basato su priorità (manuale) | Ordinamento dei consigli semplice e curato manualmente | Più facile da configurare; non si adatta al comportamento individuale |

#### Decisione: regole di filtro

Quali elementi devono essere esclusi dai consigli?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Escludi articoli già acquistati | Consigli per il cross-selling e l&#39;individuazione | Richiede cronologia acquisti nel profilo comportamentale |
| Escludi articoli esauriti | E-commerce con inventario dinamico | Richiede aggiornamenti del catalogo in tempo reale o quasi reale |
| Escludi elementi precedentemente ignorati | Consigli sui contenuti in cui gli utenti possono ignorare i suggerimenti | Richiede il tracciamento dei licenziamenti negli eventi comportamentali |
| Filtro con ambito di categoria | Raccomandazioni limitate a categorie specifiche | Utilizza gli attributi dell&#39;elemento per il filtro |

#### Decision: Cold-start strategy

What should be shown for new visitors with no behavioral history?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Popular items (global bestsellers) | General-purpose fallback | Simple to maintain; not personalized |
| Category-specific popular items | Visitor has arrived on a category page | Contextually relevant fallback; requires page context |
| Curated editorial picks | Brand wants editorial control over cold-start experience | Requires manual curation and updates |
| Trending items (time-weighted popularity) | Dynamic fallback reflecting current trends | Requires trending signal computation |

**UI navigation:** [!DNL Journey Optimizer] > Components > Decision Management > Decisions; [!DNL Journey Optimizer] > Components > Decision Management > Offers; [!DNL Journey Optimizer] > Components > Decision Management > Placements

**Dettagli configurazione chiave:**

- Create decision items representing each product or content item in the catalog, with attributes (category, price, image URL, tags)
- Define selection strategies that combine item catalog filtering with behavioral ranking logic
- Configure ranking models -- formula-based expressions can reference profile attributes (e.g., category affinity scores from computed attributes)
- Create fallback offers/items that serve as default recommendations for cold-start profiles
- Organize items into collections using collection qualifiers (tags) for logical grouping
- Set up filtering rules within selection strategies to enforce business rules (exclude purchased, in-stock only)

**Documentazione di Experience League:**

- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Creare i posizionamenti](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Creare regole di decisione](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Creare offerte di fallback](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Creare le raccolte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Phase 4: Configure channel and surface

**Funzione applicazione:** AJO: Configurazione canale

This phase configures the delivery surfaces where recommendations will be rendered. The configuration varies significantly by implementation option.

#### Decision: Delivery surface type

Where will recommendations be displayed?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Code-based experience (web) | Recommendation widget on web pages with custom rendering | Maximum flexibility for rendering; requires front-end development |
| Web channel surface | Standard web personalization surface | Utilizza AJO Web Designer; meno flessibile rispetto a quello basato su codice |
| Messaggio in-app | Consigli contestuali attivati dal comportamento dell’app | Effimero; scompare dopo l&#39;interazione o il licenziamento |
| Scheda contenuto (mobile) | Feed di consigli persistenti nell’app mobile | Persiste finché l’utente non agisce; esperienza di feed navigabile |
| E-mail | Consigli di prodotto incorporati nelle campagne e-mail | Statico al momento dell’invio; soggetto ai vincoli di rendering di e-mail |

**Opzioni divergenti:**

**Per L&#39;Opzione A (Consigli Web In Tempo Reale):**
Configura una superficie di esperienza basata su codice o una superficie di canale web. Le esperienze basate su codice offrono la massima flessibilità per il rendering personalizzato dei consigli (caroselli, griglie, schede articolo). L’URI della superficie identifica la posizione in cui vengono visualizzati i consigli nella pagina.

**Per L&#39;Opzione B (Consigli Per App Mobile):**
Configurare le superfici dei messaggi o delle schede di contenuto in-app. Le schede di contenuto sono consigliate per i feed di consigli persistenti. I messaggi in-app funzionano bene per i consigli contestuali attivati dal comportamento.

**Per L&#39;Opzione C (Email Behavioral Recommendations):**
Configura una superficie di canale e-mail con delega del sottodominio, assegnazione del pool IP e impostazioni del mittente. Assicurati che la superficie sia convalidata per il recapito.

**Navigazione interfaccia utente:** Amministrazione > Canali > Superfici di canale > Crea superficie

**Documentazione di Experience League:**

- [Impostare le superfici di canale](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configurare il canale SMS](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Phase 5: Configure content and delivery

**Funzione applicazione:** AJO: authoring dei messaggi

This phase defines the recommendation rendering templates that control how recommended items are displayed to the visitor. This includes item layout design, personalization expressions that pull item attributes (name, image, price, link), and the overall recommendation experience design.

#### Decision: Recommendation display format

How should recommended items be rendered?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Carousel (horizontal scroll) | Homepage or category page with limited vertical space | Familiar UX pattern; shows multiple items in compact space |
| Grid (multi-row) | Dedicated recommendation section with ample space | Shows more items at once; works well for &quot;recommended for you&quot; sections |
| Single item widget | Contextual recommendation in a specific page location (e.g., sidebar) | Minimal footprint; high-impact placement |
| Inline email block | Recommendations embedded within email body | Subject to email HTML/CSS constraints; typically 2-4 items |

#### Decision: Number of recommendations to display

Quanti elementi deve restituire la decisione per posizionamento?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| 3-4 elementi | Widget consigli standard | Bilancia la rilevanza con la densità visiva |
| 6-8 elementi | Carosello con layout a scorrimento o griglia | Più opzioni per il visitatore; richiede una profondità di catalogo sufficiente |
| 1 elemento | Consigli contestuali per un singolo prodotto | Massima rilevanza, rendering più semplice |
| Oltre 10 elementi | Esperienza di consigli in stile feed | Casi d’uso relativi ai contenuti (contenuti multimediali, pubblicazioni) |

**Opzioni divergenti:**

**Per L&#39;Opzione A (Consigli Web In Tempo Reale):**
Progetta il rendering dei consigli utilizzando modelli di esperienza basati su codice. Utilizza HTML/CSS/JavaScript per creare il layout carosello, griglia o widget. Le espressioni Personalization fanno riferimento agli attributi di risposta della decisione (nome articolo, URL immagine, prezzo, URL prodotto). Il rilevamento delle impression e dei clic viene gestito automaticamente da [!DNL Web SDK].

**Per L&#39;Opzione B (Consigli Per App Mobile):**
Configura i modelli per schede di contenuto o messaggi in-app con la logica di visualizzazione degli elementi. Utilizza strutture di contenuto basate su JSON riprodotte dall’app mobile in modalità nativa. Includi collegamenti profondi per ogni elemento consigliato.

**Per L&#39;Opzione C (Email Behavioral Recommendations):**
Progetta i contenuti delle e-mail utilizzando E-mail Designer. Insert recommendation placements using decision-powered content blocks. Configure personalization expressions for item attributes within the email template. Subject line personalization can reference top recommended items.

**UI navigation:** Content Management > Content Templates; Campaign/Journey > Edit content > Email Designer

**Dettagli configurazione chiave:**

- Each recommendation placement must reference the decision created in Phase 3
- Personalization expressions use Handlebars syntax to render item attributes
- For web: configure the code-based experience to call the decision and render the response
- For email: embed the decision in the email action within the campaign or journey
- Preview recommendations using test profiles with known behavioral history

**Documentazione di Experience League:**

- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Anteprima e test del contenuto](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### Phase 6: Set up audience scoping and campaign/journey (Option C only)

**Application Function:** RT-CDP: Audience Evaluation, AJO: Campaign Execution or Journey Orchestration

For email-based recommendations (Option C), this phase defines the target audience and configures the campaign or journey that delivers the recommendation email. Le opzioni A e B saltano questa fase perché i consigli vengono consegnati in tempo reale al caricamento della pagina o dello schermo.

#### Decisione: metodo di valutazione del pubblico

Come deve essere valutato il pubblico di destinazione delle e-mail di consigli?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Valutazione in batch | Campagne e-mail di consigli pianificate (giornaliero, riepilogo settimanale) | Tempistica di invio prevedibile; pubblico valutato prima dell’invio |
| Valutazione in streaming | E-mail di consigli attivate da eventi (navigazione abbandonata, post-acquisto) | Qualificazione del pubblico in tempo quasi reale; coppie con orchestrazione del percorso |

#### Decisione: meccanismo di consegna

L’e-mail deve essere consegnata tramite una campagna o un percorso?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Campagna pianificata | Esplosioni di e-mail per consigli una tantum o ricorrenti a un pubblico definito | Configurazione più semplice; valutazione e invio in batch del pubblico |
| Percorso con voce di pubblico | E-mail di consigli in corso attivate dalla qualificazione del pubblico | Abilita flussi in più passaggi (ad esempio e-mail di consigli seguita da promemoria) |
| Percorso attivato da eventi | E-mail di consiglio attivata da un evento specifico (abbandono navigazione, acquisto) | Attivazione in tempo reale; richiede l&#39;immissione di un percorso basato su eventi |

**Navigazione interfaccia utente:** Cliente > Tipi di pubblico > Crea pubblico > Genera regola; Campagne > Crea campagna; Percorsi > Crea percorso

**Dettagli configurazione chiave:**

- Define the target audience using segment rule expressions referencing behavioral history (e.g., &quot;viewed products in the last 7 days but did not purchase&quot;)
- Configure the campaign or journey with the email action referencing the channel surface from Phase 4
- Embed the decision from Phase 3 in the email content
- Set scheduling and frequency rules to avoid over-messaging

**Documentazione di Experience League:**

- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Rapporto live delle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)

### Phase 7: Configure reporting and optimization

**Application Function:** AJO: Reporting &amp; Performance Analysis, S5: Reporting &amp; Analysis

This phase establishes performance monitoring for recommendation click-through, conversion, and revenue metrics. It creates the reporting infrastructure to measure recommendation effectiveness and identify optimization opportunities.

#### Decisione: profondità di reporting

Quale livello di analisi dei rapporti è necessario?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo rapporti nativi di AJO | Basic recommendation performance monitoring | Quick setup; limited to AJO-tracked metrics |
| AJO + [!DNL Customer Journey Analytics] integration | Cross-channel recommendation impact analysis and revenue attribution | Richiede connessione [!DNL Customer Journey Analytics] e visualizzazione dati; fornisce informazioni più approfondite |
| Area di lavoro [!DNL Customer Journey Analytics] completa con dashboard personalizzati | Programma di ottimizzazione continuo con analisi a livello di elemento, segmento e superficie | Più completo; richiede [!DNL Customer Journey Analytics] esperienza e configurazione |

**Navigazione interfaccia utente:** Campagne > Seleziona campagna > Report tempo totale; Percorsi > Seleziona percorso > Report tempo totale; [!DNL Customer Journey Analytics] > Progetti > Crea nuovo progetto

**Dettagli configurazione chiave:**

- Rivedi i rapporti sulle campagne e sul percorso AJO per le metriche di consegna e coinvolgimento
- Per l&#39;integrazione con [!DNL Customer Journey Analytics], crea una connessione che includa i set di dati dell&#39;evento esperienza di AJO (feedback messaggi, tracciamento e-mail, decisioni)
- Crea una visualizzazione dati [!DNL Customer Journey Analytics] con dimensioni specifiche per i consigli (nome elemento, categoria elemento, superficie consiglio) e metriche (impression, clic, conversioni, ricavi)
- Creare metriche calcolate per CTR consigli, tasso di conversione e ricavi per impression
- Crea [!DNL Customer Journey Analytics] pannelli dell&#39;area di lavoro confrontando le prestazioni dei consigli tra superfici, segmenti e periodi di tempo

**Documentazione di Experience League:**

- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Creare o modificare una connessione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-connections/create-connection)
- [Creare o modificare una visualizzazione dati](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/home)
- [Panoramica delle metriche calcolate](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

## Considerazioni sull’implementazione

Review the following guardrails, pitfalls, best practices, and trade-offs before and during implementation.

### Guardrail e limiti

- Maximum of 10,000 approved personalized offers (decision items) per sandbox -- [Decision Management guardrails](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/get-started/guardrails)
- Massimo 30 posizionamenti per decisione
- Maximum of 30 collection scopes per decision request
- Offer Delivery response time SLA: less than 500ms at P95 for single-scope Edge requests
- I modelli di classificazione IA richiedono almeno 1.000 eventi di conversione per la formazione
- Offer capping counters may have a lag of up to a few seconds in high-throughput scenarios
- Edge decisions are limited to profile attributes available in the edge profile store
- Only one merge policy can be active on Edge per sandbox -- [Profile guardrails](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)
- Maximum of 25 active computed attributes per sandbox -- [Computed attributes guardrails](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview)
- Maximum of 4,000 segment definitions per sandbox -- [Segmentation guardrails](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)
- Streaming ingestion: maximum 20,000 records per second per HTTP connection -- [Ingestion guardrails](https://experienceleague.adobe.com/it/docs/experience-platform/ingestion/guardrails)

### Insidie comuni

- **Decision returns only fallback items:** Verify that personalized decision items are approved, within their validity date range, and that eligibility rules match the visitor&#39;s profile attributes. Check that capping limits have not been reached.
- **Edge delivery returns empty personalization:** Ensure the datastream is configured with the [!DNL Adobe Journey Optimizer] service enabled and that the decision scope is correctly formatted in the [!DNL Web SDK] request.
- **Ranking formula not applied:** Verify that the formula is syntactically valid and references accessible profile attributes. Formula errors silently fall back to priority-based ranking.
- **Stale recommendations:** If behavioral event data is not flowing in real time, recommendations will be based on outdated behavioral profiles. Verify [!DNL Web SDK] or [!DNL Mobile SDK] is actively streaming events.
- **Cold-start fallback rate is too high:** If a large percentage of visitors receive fallback recommendations, consider enriching the cold-start strategy with contextual signals (current page category, referral source) rather than relying solely on behavioral history.
- **Recommendations not rendering on page:** Verify that the code-based experience surface URI matches the page URL pattern and that the [!DNL Web SDK] is correctly requesting and rendering the decision response.
- **Catalog items missing from recommendations:** Ensure all catalog items have been ingested as decision items, tagged with the correct collection qualifiers, and included in the appropriate collections referenced by the selection strategy.

### Best practice

- Inizia con un modello di classificazione basato su formule utilizzando attributi calcolati (affinità tra categorie, recency di interazione) prima di investire in modelli con classificazione basata su IA. I modelli basati su formule sono trasparenti, verificabili e forniscono una base solida per il confronto.
- Implementa il tracciamento delle impression e dei clic dal primo giorno. Senza i dati di interazione, i modelli di classificazione di IA non possono essere addestrati e non è possibile misurare l’efficacia dei consigli.
- Crea strategie di selezione separate per diverse superfici di consigli (homepage, PDP, e-mail) anziché riutilizzare una singola strategia ovunque. Superfici diverse rispondono alle esigenze degli utenti.
- Utilizza attributi calcolati per distillare la cronologia comportamentale in segnali di classificazione. I dati dell’evento non elaborati sono troppo granulari per una classificazione efficace basata su formule; segnali aggregati come &quot;punteggio di affinità tra categorie&quot; e &quot;giorni dall’ultimo acquisto&quot; sono più efficaci.
- Testa i consigli di fallback separatamente dai consigli personalizzati. Assicurati che gli elementi di fallback siano valori predefiniti di alta qualità e appropriati per il brand che forniscano una buona esperienza ai nuovi visitatori.
- Monitora il tasso di fallback a freddo come metrica di integrità chiave. Un tasso di fallback decrescente nel tempo indica una crescente copertura comportamentale.
- Per i consigli e-mail, la pianificazione invia negli orari in cui il profilo comportamentale è più completo (ad esempio, dopo le ore di picco di navigazione, non durante le attività).

### Decisioni di compromesso

I seguenti compromessi devono essere valutati in base alle tue esigenze specifiche.

#### Segnali in tempo reale e cronologia accumulata

I segnali comportamentali durante la sessione forniscono rilevanza immediata ma profondità limitata. L’anamnesi comportamentale accumulata fornisce profondità, ma può essere obsoleta. L’equilibrio tra queste fonti incide sulla qualità dei consigli.

- **L&#39;opzione A favorisce:** Segnali in tempo reale per rilevanza immediata, integrati dalla cronologia accumulata per i visitatori noti
- **L&#39;opzione C favorisce:** Cronologia accumulata esclusivamente, poiché le e-mail vengono inviate in modo asincrono
- **Consiglio:** per web e dispositivi mobili (opzioni A e B), combina i segnali in-session con attributi calcolati derivati dal comportamento storico. Per l’e-mail (opzione C), investi massicciamente in attributi calcolati che riassumono la cronologia comportamentale in segnali a livello di profilo utilizzabili.

#### Modelli basati su formule e modelli basati su IA

La classificazione basata su formule è trasparente e immediata. I modelli con classificazione AI si adattano automaticamente, ma richiedono dati di formazione e offrono meno visibilità nelle decisioni di classificazione.

- **Preferenze basate su formule:** Trasparenza, verificabilità, distribuzione immediata e controllo aziendale dettagliato sulla logica di classificazione
- **Preferenze basate sull&#39;intelligenza artificiale:** ottimizzazione automatizzata, individuazione di pattern non evidenti e riduzione dello sforzo di ottimizzazione manuale
- **Consiglio:** inizia con una classificazione basata su formule per stabilire una linea di base delle prestazioni e accumulare i dati di conversione. Passare ai modelli classificati in base all’intelligenza artificiale una volta che si dispone di dati di formazione sufficienti (oltre 1.000 eventi di conversione) e si desidera ottimizzare oltre ciò che è possibile ottenere con il tuning manuale delle formule.

#### Copertura dei consigli e rilevanza

L’allargamento del catalogo degli articoli e l’attenuazione delle regole di filtro aumentano la percentuale di richieste che ricevono consigli personalizzati, ma possono ridurre la rilevanza per ogni consiglio.

- **Elevata copertura a favore:** massimizzare il numero di visitatori che visualizzano consigli personalizzati; utile quando l&#39;obiettivo principale è il coinvolgimento
- **Preferenze di rilevanza elevata:** solo elementi altamente rilevanti, anche se per un numero maggiore di visitatori vengono visualizzati consigli di fallback; utile quando l&#39;obiettivo principale è la conversione
- **Consiglio:** inizia con un filtro moderato (escludi articoli acquistati ed esauriti) e monitora sia il tasso di fallback che il tasso di conversione. Restringi le regole di filtro solo se i dati di conversione lo supportano.

#### Profondità di Personalization e complessità dell&#39;implementazione

Segnali comportamentali più ricchi e modelli di classificazione più sofisticati migliorano la qualità dei consigli, ma aumentano la complessità dell’implementazione e il carico di manutenzione.

- **Un&#39;implementazione più semplice favorisce:** un time-to-value più rapido, una manutenzione inferiore, un debug e un&#39;iterazione più semplici
- **Personalizzazione più approfondita a favore di:** Incremento della conversione, migliore esperienza del cliente, differenziazione della concorrenza
- **Consiglio:** Implementare in fasi. Inizia con i segnali di visualizzazione del prodotto e la classificazione basata su formule (fase 1). Aggiungere attributi calcolati per l’arricchimento comportamentale (fase 2). Valuta i modelli classificati in base all’intelligenza artificiale una volta che la base è matura e sono disponibili dati di formazione sufficienti (fase 3).

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sulle tecnologie e le funzionalità utilizzate in questo modello.

### Gestione delle decisioni

- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Creare i posizionamenti](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Creare regole di decisione](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Creare offerte di fallback](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Creare le raccolte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Creare qualificatori di raccolta](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Distribuire le offerte tramite l’API Edge Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)

### Raccolta dati e Web/Mobile SDK

- [Panoramica di Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/home)
- [Installare Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/install/overview)
- [Panoramica di Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/it/docs/experience-platform/datastreams/configure)
- [Panoramica dell’API del server Edge Network](https://experienceleague.adobe.com/it/docs/experience-platform/edge-network-server-api/overview)

### XDM e modellazione dati

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home)
- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/schema/composition)
- [Create a dataset](https://experienceleague.adobe.com/it/docs/experience-platform/catalog/datasets/create)
- [Define a relationship between two schemas](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/tutorials/relationship-api)

### Identità e profilo

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home)
- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview)
- [Panoramica del profilo cliente in tempo reale](https://experienceleague.adobe.com/it/docs/experience-platform/profile/home)

### Tipi di pubblico e segmentazione

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/edge-segmentation)

### Computed attributes and profile enrichment

- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview)
- [Guida dell’interfaccia utente attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/ui)
- [Panoramica di Customer AI](https://experienceleague.adobe.com/it/docs/experience-platform/intelligent-services/customer-ai/overview)

### Configurazione dei canali

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Impostare le superfici di canale](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delega sottodomini](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)

### Authoring e personalizzazione dei messaggi

- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### Reporting e analisi

- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Panoramica di CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-overview/cja-overview)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/home)
- [Panoramica delle metriche calcolate](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

### Governance dei dati e ciclo di vita

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home)
- [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview)
- [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/it/docs/experience-platform/data-lifecycle/home)
- [Scadenze set di dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-lifecycle/ui/dataset-expiration)

### Monitoraggio e osservabilità

- [Panoramica di Observability Insights](https://experienceleague.adobe.com/it/docs/experience-platform/observability/home)
- [Panoramica degli avvisi](https://experienceleague.adobe.com/it/docs/experience-platform/observability/alerts/overview)

### Guardrail

- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/get-started/guardrails)
- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)
- [Guardrail di acquisizione](https://experienceleague.adobe.com/it/docs/experience-platform/ingestion/guardrails)
- [Guardrail del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/guardrails)

### Tutorial e guide

- [Panoramica sulle origini](https://experienceleague.adobe.com/it/docs/experience-platform/sources/home)
- [Panoramica sui tag](https://experienceleague.adobe.com/it/docs/experience-platform/tags/home)
- [Gruppo di campi Consenso e preferenze](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/field-groups/profile/consents)
