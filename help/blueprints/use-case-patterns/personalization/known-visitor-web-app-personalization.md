---
title: Personalization Web/app visitatore noto
description: Scopri come distribuire contenuti, offerte o promozioni personalizzati a visitatori identificati in base al profilo in tempo reale e all’iscrizione ai segmenti.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 585adc0e-f528-4a09-b931-ef6b45fa8ec8
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7968'
ht-degree: 2%

---

# Personalizzazione web/app per visitatore noto

Questo piano di riferimento fornisce una guida completa all&#39;implementazione per la distribuzione di contenuti personalizzati a visitatori identificati su superfici digitali tramite [!DNL Adobe Journey Optimizer] (AJO) e [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP). È progettato per architetti di soluzioni, tecnici di marketing e ingegneri dell’implementazione che devono comprendere tutti gli approcci all’implementazione praticabili, le decisioni che devono essere prese in ogni fase e la documentazione Experience League che supporta la configurazione.

La personalizzazione web/app per visitatore noto è il modello di personalizzazione principale per le esperienze digitali autenticate. A differenza della personalizzazione anonima dei visitatori, che si basa esclusivamente su segnali comportamentali durante la sessione, questo modello sfrutta l’intero profilo unificato: dati comportamentali storici, appartenenza ai segmenti, livello di fedeltà, cronologia degli acquisti, fase del ciclo di vita, attributi calcolati e punteggi di tendenza. Supporta la personalizzazione tra le pagine web (tramite il canale web AJO), i messaggi in-app mobili e le schede di contenuto.

Questa guida presenta tutte le opzioni di implementazione valide, basate su segmenti, decisioni e multi-superficie, con compromessi, indicazioni decisionali e riferimenti alla documentazione di [!DNL Adobe Experience League].

## Panoramica del caso d’uso

Le organizzazioni con proprietà digitali autenticate (siti di e-commerce, portali bancari, servizi di abbonamento, programmi fedeltà, app mobili) devono fornire esperienze personalizzate che riflettano il rapporto di ciascun cliente con il marchio. Quando un visitatore effettua l’accesso o viene riconosciuto tramite la risoluzione di identità, la piattaforma può accedere al proprio profilo unificato completo e fornire contenuti personalizzati per attributi, comportamenti e preferenze specifici.

Questo modello riguarda lo scenario in cui un visitatore identificato arriva su una proprietà web o apre un’app mobile e il sistema deve determinare il contenuto, l’offerta o la promozione ottimale da visualizzare in base ai dati di profilo in tempo reale e all’iscrizione al pubblico. La decisione di personalizzazione avviene al limite in millisecondi, consentendo la distribuzione di contenuti al secondo secondario senza latenza percepibile.

Il modello supporta sia la personalizzazione deterministica (in cui il contenuto specifico è mappato su segmenti di pubblico specifici) che le decisioni dinamiche (in cui AJO Decisioning valuta le regole di idoneità e le strategie di classificazione per selezionare il contenuto ottimale per profilo). Si estende su più superfici digitali: pagine web, messaggi in-app per dispositivi mobili e schede di contenuto, consentendo una personalizzazione coerente nel percorso digitale del cliente.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### Fornire esperienze cliente personalizzate

Personalizza contenuti, offerte e messaggi in base a preferenze, comportamenti e fasi del ciclo di vita individuali. Per ulteriori informazioni, consulta [Distribuire esperienze cliente personalizzate](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md).

**KPI:** coinvolgimento, tassi di conversione, soddisfazione del cliente (CSAT)

### Aumentare il coinvolgimento con il sito Web

Migliora il tempo sul sito, le pagine per sessione e l’interazione con i contenuti web tramite esperienze rilevanti. For more information, see [Increase website engagement](../../business-objectives/acquisition-growth/increase-website-engagement.md).

**KPIs:** Time On (web) Page, Engagement, Conversion Rates

### Increase mobile app engagement

Drive daily active usage, feature adoption, and in-app conversions through personalized in-app experiences.

**KPI:** coinvolgimento, mantenimento, tassi di conversione

## Esempi di casi d’uso tattici

The following are common tactical implementations of this pattern:

- Homepage hero personalization by loyalty tier or lifecycle stage -- display different hero banners based on whether the customer is new, active, at-risk, or VIP
- Product recommendation carousel based on purchase history -- surface relevant product suggestions using past purchase data and product affinity scores
- Personalized promotional banner by customer segment -- show different promotions to high-value, at-risk, and new customer segments
- In-app message for mobile users based on feature adoption -- guide users to underutilized features based on their usage patterns
- Content card with personalized offer on account dashboard -- persistent, dismissible offers tailored to the customer&#39;s profile
- Personalized pricing or discount display based on customer tier -- show tier-specific pricing or exclusive discounts to loyalty program members
- Cross-sell recommendation widget based on owned products -- suggest complementary products or services based on current portfolio
- Personalized navigation or content ordering based on interests -- reorder content modules or navigation elements based on demonstrated preferences

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare l’efficacia di questo modello di caso d’uso.

| KPI | Approccio di misurazione | Benchmark guidance |
| --- | --- | --- |
| Personalization Engagement Rate | Clicks and interactions with personalized content elements divided by impressions | Personalized content should outperform default content by 20-50% |
| Conversion Rate Lift | Conversion rate for personalized experiences versus control/default experiences | Target 10-30% lift over non-personalized experiences |
| Percentuale di click-through (CTR) | Clic su CTA, offerte e consigli personalizzati divisi per impression | Monitoraggio per superficie (web, in-app, scheda di contenuti) e per segmento |
| Ricavo per visita | Ricavi attribuiti a sessioni con esperienze personalizzate | Confrontare le coorti di visitatori personalizzati e non personalizzati |
| Tasso di interazione scheda contenuto | Clic e licenziamenti sulla scheda contenuto relativi alle impression | Tracciamento per tipo di carta e segmento di pubblico |
| Coinvolgimento messaggi in-app | Interazioni dei messaggi in-app (clic su CTA, chiusure) relative alle impression | Confrontare segmenti di pubblico e tipi di messaggi diversi |
| Tempo sulla pagina | Tempo medio trascorso su pagine con contenuti personalizzati rispetto a quello predefinito | Le pagine personalizzate devono mostrare un tempo di permanenza maggiore |
| Tasso di accettazione offerta | Percentuale di offerte selezionate con decisioni che risultano in un evento di conversione | Tracciamento per offerta, posizionamento e strategia di classificazione |

## Schema del caso d’uso

Questa sezione descrive il pattern di base e la relativa catena di funzioni.

**Personalizzazione web/app visitatore noto**

Distribuisci contenuti, offerte o promozioni personalizzati a un visitatore identificato in base al profilo in tempo reale e all’iscrizione ai segmenti su più superfici Web, in-app mobile e schede di contenuto.

**Catena di funzioni:** Valutazione del pubblico > Personalization Decisioning > Configurazione superficie/canale > Consegna contenuto > Tracciamento impression > Reporting

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Adobe Journey Optimizer] (AJO)**: configurazione del canale web, configurazione del canale in-app, configurazione del canale della scheda di contenuto, decisioning (selezione e classificazione dell&#39;offerta), authoring dei messaggi (creazione di contenuti personalizzati), esecuzione della campagna, sperimentazione dei contenuti e reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Valutazione del pubblico (edge, streaming e batch), ricerca dei profili in tempo reale tramite Edge Network, arricchimento dei profili con attributi calcolati e punteggi di propensione
- **[!DNL Adobe Experience Platform] (AEP)** — Archivio profili, servizio Identity, Web SDK, Mobile SDK, configurazione dello stream di dati, consegna rete Edge

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve esistere | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Presunto sul posto | Sandbox AJO con canale web, canale in-app e autorizzazioni di decisione configurate. Per gli utenti sono stati assegnati ruoli di addetto marketing e autore di contenuti. | [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home), [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Obbligatorio | Lo schema di profilo deve includere attributi utilizzati per la personalizzazione e la segmentazione (ad esempio, livello fedeltà, cronologia acquisti, interessi prodotto, fase del ciclo di vita). Schema Experience Event per il tracciamento delle interazioni web/app e gli eventi di conversione. Set di dati abilitati per [!DNL Real-Time Customer Profile]. | [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Origini dati e raccolta | Obbligatorio | Web SDK implementato nelle proprietà web per la distribuzione delle esperienze e il tracciamento delle impression. Mobile SDK implementato nelle app mobili per la distribuzione in-app e con scheda di contenuti. Stream di dati configurato con il servizio AJO abilitato per la personalizzazione Edge. Dati di profilo in tempo reale disponibili al limite per la personalizzazione di secondi secondari. | [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Mobile SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview), [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Configurazione identità e profilo | Obbligatorio | Known identity namespaces (CRM ID, email, authenticated user ID) configured. Identity stitching between anonymous and authenticated sessions operational for seamless transition from anonymous to known-visitor personalization. Edge merge policy configured with `isActiveOnEdge: true` to resolve the authenticated profile at the edge. | [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Panoramica dei criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Definizione e segmentazione del pubblico | Obbligatorio | Audiences defined using profile attributes, behavioral data, and computed attributes. Edge or streaming evaluation enabled for real-time personalization qualification. Audiences used for segment-based personalization must qualify for edge evaluation. | [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Consigliato | Computed attributes (e.g., [!DNL Customer AI] propensity scores, lifetime value, engagement score, product affinity, days since last purchase) significantly improve personalization quality by providing richer signals for audience definition and content selection. | [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview), [Panoramica di IA per l&#39;analisi dei clienti](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Data Lifecycle Management | Consigliato | Profile and event data retention policies ensure fresh, relevant data powers personalization decisions. Consent enforcement ensures personalization respects user preferences. | [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted) |
| Etichettatura e applicazione dell’utilizzo dati | Consigliato | Le etichette di governance sugli attributi di profilo utilizzati per la personalizzazione (in particolare gli attributi adiacenti ai dati PII come cronologia acquisti, posizione, dati finanziari) garantiscono la conformità con i criteri di utilizzo dei dati. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview) |
| Monitoraggio e osservabilità | Consigliato | Il monitoraggio delle prestazioni di consegna e personalizzazione di Edge consente di rilevare problemi di latenza, errori di consegna o problemi di aggiornamento dei dati che peggiorano l’esperienza personalizzata. | [Panoramica di Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home), [Panoramica degli avvisi](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| Reporting e analisi | Incluso | Il reporting sulle prestazioni di Personalization fa parte del passaggio 6 della catena di funzioni. [!DNL Customer Journey Analytics] L’analisi consente un’analisi approfondita dell’impatto della personalizzazione su conversione, coinvolgimento e ricavi nei segmenti di visitatori. | [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Guida all&#39;integrazione di AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Journey Optimizer] (AJO)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Configurazione canali | Configurazione di superficie e canale | Configurare superfici di canale web, in-app e schede di contenuto per la distribuzione di personalizzazione |
| Authoring dei messaggi | Authoring dei contenuti | Crea varianti di contenuto personalizzato con contenuto dinamico, espressioni di personalizzazione e blocchi condizionali per ogni superficie |
| Esecuzione della campagna | Configurazione e attivazione di Campaign | Creare e attivare campagne web (pianificate o attivate da API) che associano tipi di pubblico, superfici e contenuti |
| Decisioni | Impostazione delle decisioni (opzione B/C) | Configurare i criteri di decisione con regole di idoneità, strategie di classificazione ed elementi di offerta/contenuto per la personalizzazione dinamica |
| Sperimentazione sui contenuti | Ottimizzazione (opzionale) | Eseguire test A/B sulle varianti di contenuto personalizzato per ottimizzare le prestazioni |
| Frequenza e regole business | Configurazione e attivazione di Campaign | Applica i limiti di frequenza per le impression per evitare un eccesso di personalizzazione |
| Reporting e analisi delle prestazioni | Reporting e ottimizzazione | Monitorare la consegna della personalizzazione, il coinvolgimento e le metriche di conversione per superficie e segmento |

### [!DNL Real-Time CDP] (RT-CDP)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Valutazione del pubblico | Definizione e valutazione del pubblico | Definire e valutare i tipi di pubblico utilizzando gli attributi di profilo, i dati comportamentali e gli attributi calcolati con la valutazione Edge o in streaming |
| Ricerca profilo in tempo reale | Consegna dei contenuti (runtime) | Accedere agli attributi di profilo in tempo reale e alle iscrizioni ai segmenti tramite Edge Network per prendere decisioni sulla personalizzazione di un secondo secondario |
| Arricchimento del profilo | Pre-implementazione (supporto) | Arricchisci i profili con attributi calcolati, punteggi [!DNL Customer AI] e segnali comportamentali aggregati che migliorano la qualità della personalizzazione |

## Prerequisiti

Prima di implementare questo pattern di casi d’uso, assicurati di aver implementato quanto segue:

- [ ] Web SDK implementato nelle proprietà Web di destinazione con `alloy("sendEvent")` configurato per le visualizzazioni di pagina e il tracciamento delle interazioni
- [ ] Mobile SDK implementato nelle app mobili di destinazione (se vengono utilizzate superfici in-app o schede di contenuto)
- [ ] Datastream configured with [!DNL Adobe Journey Optimizer] service enabled
- [ ] Profile schema includes attributes used for personalization (loyalty tier, purchase history, product interests, lifecycle stage)
- [ ] Experience Event schema configured for impression and conversion tracking
- [ ] Known identity namespaces created and identity stitching operational between anonymous (ECID) and authenticated identities
- [ ] Edge merge policy configured with `isActiveOnEdge: true`
- [ ] Audiences defined with edge-eligible evaluation for real-time personalization
- [ ] Content assets (images, copy, CTAs) prepared for each personalization variant
- [ ] Personalization strategy documented: which attributes drive which content, for which surfaces

## Opzioni di implementazione

This section describes the available implementation approaches for this use case pattern.

### Option A: Segment-based web personalization

**Best for:** Deterministic personalization where specific content variants map directly to audience segments -- loyalty tier-specific hero banners, lifecycle stage messaging, customer segment promotional content. Ideal when the content-to-segment mapping is well-defined and does not require dynamic ranking or optimization.

**Funzionamento:**

Segment-based personalization maps content variants directly to audience segments. When a known visitor&#39;s profile is evaluated against edge-eligible audiences at page load, the system determines which segments the visitor belongs to and displays the corresponding content variant. Selection is based on segment membership priority -- if a visitor qualifies for multiple segments, the highest-priority segment&#39;s content is displayed.

This approach uses AJO web channel campaigns (or in-app/content card campaigns) with conditional content rules or multiple treatment targeting configurations. Each audience segment is associated with a specific content experience. No decisioning engine is involved -- the content selection logic is entirely segment-driven.

Content is authored using the AJO message authoring interface with dynamic content blocks that render different content based on audience membership or profile attributes. The Web SDK or Mobile SDK delivers the personalized experience in real time via the Edge Network.

**Considerazioni chiave:**

- Content variants must be pre-authored for each segment
- Segment definitions must be edge-eligible for real-time qualification
- Per aggiungere nuovi segmenti o varianti di contenuto è necessario aggiornare la configurazione della campagna
- La selezione del contenuto è deterministica: lo stesso segmento vede sempre lo stesso contenuto

**Vantaggi:**

- Semplicità di implementazione e manutenzione grazie a una chiara mappatura contenuto-segmento
- Facile da capire e spiegare alle parti interessate la logica di personalizzazione
- Nessun sovraccarico decisionale: risoluzione più rapida dei contenuti
- Controllo completo sul contenuto ricevuto da ogni segmento

**Limitazioni:**

- Flessibilità limitata con l’aumento del numero di segmenti e varianti di contenuto
- Impossibile ottimizzare in modo dinamico la selezione del contenuto in base a segnali a livello di profilo oltre l’iscrizione al segmento
- L’aggiunta di nuove varianti di contenuto richiede aggiornamenti manuali della campagna
- Non supporta gli scenari di offerta migliore successiva in cui più offerte competono per lo stesso posizionamento

**Experience League:**

- [Introduzione al canale web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Creare esperienze web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### Opzione B: Personalizzazione basata su decisioni

**Ideale per:** Personalizzazione dinamica in cui il contenuto o l&#39;offerta ottimale devono essere selezionati per profilo utilizzando le regole di idoneità e le strategie di classificazione: offerta migliore nella home page, consigli di prodotti personalizzati, selezione dinamica del banner promozionale. Ideale quando più offerte o elementi di contenuto competono per lo stesso posizionamento e il sistema deve scegliere quello migliore.

**Funzionamento:**

La personalizzazione basata sulle decisioni utilizza AJO Decisioning per valutare il profilo di ogni visitatore in base a un catalogo di articoli di contenuto o offerte, applicando le regole di idoneità per determinare quali articoli sono idonei e applicando quindi una strategia di classificazione (basata sulla priorità, basata su formule o con classificazione basata sull’intelligenza artificiale) per selezionare l’articolo ottimale per ogni posizionamento.

L’implementazione prevede la creazione di posizionamenti (dove viene visualizzato il contenuto), la definizione di offerte con regole di idoneità e rappresentazioni di contenuto, l’organizzazione di offerte in raccolte e la creazione di criteri decisionali che associano posizionamenti a raccolte con strategie di classificazione. In fase di runtime, quando un visitatore carica una pagina, Edge Network valuta il criterio di decisione in base al profilo del visitatore e restituisce il contenuto dell’offerta selezionata.

Questo approccio supporta scenari di personalizzazione sofisticati, tra cui offerte successive, promozioni personalizzate con limite e selezione di contenuti ottimizzati per l’intelligenza artificiale. Le offerte possono avere limiti di limite per profilo e globale, intervalli di date di validità e criteri di idoneità complessi che combinano attributi di profilo e appartenenza a un pubblico.

**Considerazioni chiave:**

- Richiede una configurazione più iniziale (posizionamenti, offerte, regole di idoneità, raccolte, decisioni)
- Le strategie di classificazione possono essere basate sulla priorità (manuale), basate su formule (espressione personalizzata) o basate sull’intelligenza artificiale (ottimizzazione automatica)
- La classificazione basata su IA richiede almeno 1.000 eventi di conversione per l’apprendimento dei modelli
- I contatori dei limiti di offerta possono presentare un lieve ritardo in scenari ad alto throughput
- Un’offerta di fallback deve essere configurata per i casi in cui nessuna offerta personalizzata è idonea

**Vantaggi:**

- Selezione dinamica dei contenuti per profilo senza mappatura hardcoded da segmento a contenuto
- Supporta criteri di idoneità e logica di classificazione complessi
- L’opzione con classificazione AI consente l’ottimizzazione automatica senza intervento manuale
- Il limite dell’offerta impedisce la sovraesposizione di contenuti specifici
- Gestione centralizzata delle offerte: le offerte possono essere riutilizzate su più campagne e canali

**Limitazioni:**

- Maggiore complessità di implementazione rispetto alla personalizzazione basata su segmenti
- La classificazione basata su IA richiede un volume di eventi di conversione sufficiente per l’apprendimento
- La valutazione delle decisioni aggiunge una latenza marginale rispetto alla distribuzione diretta dei contenuti basata su segmenti
- La classificazione basata su formula richiede una progettazione attenta per evitare la definizione di priorità non intenzionale

**Experience League:**

- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

**How this differs from Offer decisioning Option B:**

L’infrastruttura è identica: entrambi utilizzano AJO Decisioning alla periferia con Web SDK e un criterio di unione attivo per la rete Edge. The difference is what is being selected. This option manages content items where the selection criterion is personalization fit (segment membership, behavioral ranking). [Offer decisioning](offer-decisioning.md) Option B manages a governed offer catalog where eligibility rules, capping limits, and validity windows are business requirements. If your item set requires per-profile impression capping, regulatory eligibility constraints, or offer lifecycle management, use Offer decisioning Option B instead.

### Option C: Multi-surface personalization (web + in-app + content card)

**Best for:** Consistent personalization across multiple digital surfaces -- delivering coordinated personalized experiences on web pages, mobile in-app messages, and content cards. Ideal when the organization has both web and mobile app properties and wants unified personalization logic across all digital touchpoints.

**Funzionamento:**

Multi-surface personalization extends either Option A (segment-based) or Option B (decisioning-based) to deliver personalized content across multiple AJO surface types. Each surface type -- web, in-app, content card -- may have different content formats and delivery mechanisms, but the underlying personalization logic (audience membership or decisioning) is shared.

The implementation involves configuring channel surfaces for each surface type, authoring surface-specific content (web HTML/CSS for web surfaces, structured messages for in-app, card layouts for content cards), and creating campaigns that target the appropriate surface. The Web SDK handles web surface delivery, while the Mobile SDK handles in-app and content card delivery.

Content cards are particularly valuable for persistent, dismissible personalized messages on account dashboards or app home screens. In-app messages are ideal for contextual, session-specific communications. Web personalization handles hero banners, recommendation widgets, and promotional content.

**Considerazioni chiave:**

- Each surface type requires its own channel surface configuration and content authoring
- Web SDK and Mobile SDK must both be implemented and configured
- Content must be designed for each surface format (different dimensions, layouts, interaction patterns)
- Shared audiences and decisioning logic ensure consistency across surfaces
- Testing must cover all surface types across devices

**Vantaggi:**

- Esperienza di personalizzazione coerente in tutti i punti di contatto digitali
- Il pubblico condiviso e la logica decisionale riducono la duplicazione
- Le schede di contenuto forniscono una superficie di personalizzazione persistente e non intrusiva
- I messaggi in-app consentono la personalizzazione contestuale e specifica della sessione su dispositivi mobili

**Limitazioni:**

- Maggiore complessità di implementazione: richiede la configurazione per ogni tipo di superficie
- Richiede l’implementazione sia di Web SDK che di Mobile SDK
- Il contenuto deve essere progettato e mantenuto per ciascun formato di superficie
- L&#39;ambito del test aumenta con ogni tipo di superficie aggiuntiva

**Experience League:**

- [Panoramica del canale in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [Canale scheda contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Introduzione al canale web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)

### Confronto delle opzioni

La tabella seguente confronta le tre opzioni di implementazione.

| Criteri | Opzione A: Basata Su Segmenti | Opzione B: Basata Su Decisioni | Opzione C: superfici multiple |
| --- | --- | --- | --- |
| Ideale per | Mappatura segmento-contenuto nota | Selezione dinamica dei contenuti per profilo | Consistent personalization across web + mobile |
| Complessi | Bassa | Medium - Alta | High (builds on A or B) |
| Latenza | Fastest (direct segment resolution) | Slightly higher (decisioning evaluation) | Depends on underlying option (A or B) |
| Flessibilità | Limited to predefined segment-content pairs | High -- dynamic ranking and eligibility | Highest -- multi-surface with shared logic |
| Gestione dei contenuti | Manual segment-to-content mapping | Centralized offer library with eligibility rules | Per-surface content with shared personalization logic |
| Ottimizzazione | Manual A/B testing | AI-ranked auto-optimization available | Per-surface optimization |
| Richiede | Edge-eligible audiences, Web SDK | Placements, offers, eligibility rules, decisions | Web SDK + Mobile SDK, multiple surface configurations |
| Surfaces Supported | Web (primary) | Web (primary) | Web + in-app + scheda contenuto |

### Scegli l’opzione giusta

Inizia con queste domande per selezionare l’approccio di implementazione corretto:

1. **Quante superfici?** Se hai bisogno di personalizzazione sia su app web che su app mobili, scegli l’opzione C (che si basa su A o B per la logica sottostante). Se disponibile solo per il Web, scegliere tra A e B.

2. **La selezione dei contenuti è dinamica?** Se disponi di una mappatura ben definita dei segmenti alle varianti di contenuto (ad esempio, 3-5 livelli di fedeltà, ciascuno con un banner principale specifico), scegli l’opzione A. Se devi effettuare una selezione da un catalogo di offerte con idoneità e classificazione complesse, scegli l’opzione B.

3. **È necessaria una selezione ottimizzata per l&#39;intelligenza artificiale?** Se desideri che il sistema impari e ottimizzi automaticamente quale contenuto funziona meglio per ciascun profilo, scegli l’opzione B con decisioning basato sull’intelligenza artificiale.

4. **Quante varianti di contenuto?** Se disponi di meno di 10 varianti di contenuto con mappature di segmenti chiare, l’opzione A è più semplice. Se decine di offerte necessitano di filtri e classificazione di idoneità, l’opzione B viene scalata meglio.

5. **Intendi estendere ad altri canali?** Se la logica decisionale dovesse infine distribuire offerte tra e-mail, web e altri canali, l’opzione B fornisce le basi decisionali centralizzate che il Offer Decisioning cross-channel estende.

## Fasi di implementazione

Questa sezione descrive in dettaglio ogni fase dell’implementazione.

### Fase 1: definire i tipi di pubblico e configurare la valutazione

**Funzione applicazione:** RT-CDP: Audience Evaluation

**Configurazione:** definire i tipi di pubblico che determinano la selezione dei contenuti di personalizzazione. Questi tipi di pubblico rappresentano i segmenti di visitatori che riceveranno esperienze personalizzate: livelli di fedeltà, fasi del ciclo di vita, coorti comportamentali o gruppi di affinità per i prodotti.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: metodo di valutazione del pubblico**
>
>Quanto rapidamente deve essere risolta l’iscrizione al pubblico per la personalizzazione? Questo influisce direttamente sul fatto che la personalizzazione possa avvenire al caricamento della pagina o richieda un ritardo.
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Valutazione Edge | Personalizzazione web/app in tempo reale che richiede una qualificazione al secondo secondario | Limitato a semplici controlli degli attributi di profilo e appartenenza ai segmenti. Nessuna query di serie temporali o aggregazione complessa. Obbligatorio per la personalizzazione dei visitatori noti. |
>| Valutazione in streaming | Qualificazione in tempo quasi reale quando i profili entrano/escono da tipi di pubblico in base a eventi comportamentali | Supporta query a singolo evento e finestre temporali limitate. Le modifiche del pubblico si riflettono in pochi minuti. Adatto per superfici in-app e schede di contenuto in cui è accettabile un leggero ritardo. |
>| Valutazione in batch | Il pubblico giornaliero si aggiorna per i segmenti basati su aggregazioni complesse o pattern storici | Supporto completo della funzione di regola del segmento. Non adatto alla personalizzazione in tempo reale, ma può integrare i tipi di pubblico edge con segmenti precalcolati complessi. |

>[!NOTE]
>**Decisione: attributi Personalization**
>
>Quali attributi di profilo devono guidare la definizione del pubblico e la selezione del contenuto?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Attributi del profilo (livello fedeltà, fase ciclo di vita) | Personalizzazione deterministica basata sulle proprietà note del cliente | Attributi stabili e ben definiti. Facile da mappare alle varianti di contenuto. Disponibile al perimetro se il profilo è configurato correttamente. |
>| Segnali comportamentali (cronologia acquisti, modelli di navigazione) | Personalization basato su comportamenti e modelli di coinvolgimento recenti | Richiede attributi calcolati o segmenti di streaming. Più dinamico, ma più complesso da mantenere. |
>| Punteggi tendenza ([!DNL Customer AI]) | Personalizzazione predittiva in base alla probabilità di conversione, abbandono o acquisto | Richiede attributi calcolati. Abilita una personalizzazione sofisticata ma richiede dati di apprendimento del modello ML. |
>| Approccio combinato | La maggior parte delle implementazioni di produzione | Utilizza gli attributi del profilo per la segmentazione primaria con segnali comportamentali e punteggi di tendenza per il perfezionamento. |

**Navigazione interfaccia utente:** Cliente > Tipi di pubblico > Crea pubblico > Genera regola

**Dettagli configurazione chiave:**

- Definire i tipi di pubblico utilizzando il Generatore di segmenti con espressioni della regola di segmento che fanno riferimento agli attributi del profilo
- Assicurarsi che le espressioni delle regole del segmento siano idonee per la valutazione Edge (controlli degli attributi semplici, appartenenza al segmento)
- Configurare tipi di pubblico idonei per Edge per casi di utilizzo di personalizzazione in tempo reale
- Considera l’eliminazione dei tipi di pubblico per escludere i visitatori convertiti o esclusi di recente

**Documentazione di Experience League:**

- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Fase 2: configurare le decisioni (solo opzioni B e C)

**Application function:** AJO: Decisioning

**What you will configure:** Set up the decisioning infrastructure that dynamically selects the optimal content or offer for each visitor. This includes placements (where offers appear), offers (what content is available), eligibility rules (who qualifies), ranking strategies (how to choose the best), and decision policies (how everything connects).

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decision: Ranking strategy**
>
>How should eligible offers be ranked to select the best one for each visitor?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Basato su priorità (manuale) | Simple use cases with clear offer hierarchy | Each offer has a manual priority value. Highest priority eligible offer wins. Easy to understand and control. |
>| Basato su formula (espressione personalizzata) | When ranking should consider profile attributes | Custom ranking formulas reference profile data (e.g., score by loyalty tier + recency). Flexible but requires formula design and testing. |
>| Classificato in base all’intelligenza artificiale (ottimizzazione automatica) | When you want the system to automatically optimize offer selection | ML model learns which offers perform best for which profiles. Requires minimum 1,000 conversion events for training. Best for high-traffic placements. |

>[!NOTE]
>**Decision: Offer capping**
>
>Should there be limits on how many times an offer is shown to a visitor or across all visitors?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Limite per profilo | Impedisci a fatica di visualizzare ripetutamente la stessa offerta | Limita le impression per visitatore in un determinato periodo di tempo. Garantisce varietà nell’esperienza personalizzata. |
>| Limite globale | Limitare il numero totale di impression per un&#39;offerta promozionale o a disponibilità limitata | Limita le impression totali a tutti i visitatori. Utile per promozioni in quantità limitata. |
>| Nessun limite | Contenuti sempreverdi o offerte sempre pertinenti | Nessun limite di impression. Adatto a contenuti persistenti come i banner del livello fedeltà. |

**Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Componenti > Gestione decisioni

**Dettagli configurazione chiave:**

- Crea posizionamenti per ogni superficie in cui verranno visualizzate le offerte (banner web, area messaggi in-app, slot per schede di contenuto)
- Definire le regole di idoneità utilizzando le espressioni della regola di segmento che fanno riferimento agli attributi di profilo e all’iscrizione al pubblico
- Creare offerte personalizzate con rappresentazioni di contenuto per ogni posizionamento
- Creare un’offerta di fallback che copra tutti i posizionamenti (visualizzati quando nessuna offerta personalizzata è idonea)
- Organizzare le offerte con i qualificatori di raccolta (tag) e raggrupparle in raccolte
- Creare un criterio di decisione che associa i posizionamenti alle raccolte con la strategia di classificazione selezionata

**Documentazione di Experience League:**

- [Creare i posizionamenti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Creare regole di decisione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Creare offerte di fallback](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Creare le raccolte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Fase 3: configurazione di superfici e canali

**Funzione applicazione:** AJO: Configurazione canale

**Configurazione:** configurare le superfici di canale che definiscono dove verranno consegnati i contenuti personalizzati. Ogni tipo di superficie (web, in-app, scheda di contenuto) richiede la propria configurazione che specifica l’URI della superficie, il formato del contenuto e i parametri di consegna.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: superfici di destinazione**
>
>Quali superfici digitali riceveranno il contenuto personalizzato?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Solo canale web | Personalization si concentra sulle proprietà web | Richiede Web SDK. Implementazione più semplice. Copre banner hero, aree promozionali, widget di consigli. |
>| Solo canale in-app | Personalization si concentra sulle esperienze delle app mobili | Richiede Mobile SDK. Include messaggi contestuali e specifici della sessione all’interno dell’app. |
>| Solo canale scheda di contenuto | Messaggi personalizzati persistenti e inammissibili | Richiede Mobile SDK o Web SDK. Le schede persistono fino a quando non vengono ignorate. Ideale per dashboard e schermi home. |
>| Superfici multiple (opzione C) | Personalizzazione coerente su web e dispositivi mobili | Richiede sia Web SDK che Mobile SDK. Ogni superficie necessita di configurazione e contenuto separati. |

>[!NOTE]
>**Decisione: approccio alla configurazione della superficie web**
>
>Come deve essere configurata la superficie web per la distribuzione dei contenuti?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Applicazione a pagina singola | App web moderne con routing lato client | Usa `renderDecisions: true` nelle chiamate di Web SDK `sendEvent`. Contenuto sottoposto a rendering automaticamente da SDK. |
>| Applicazione multipagina (MPA) | Pagine web tradizionali sottoposte a rendering del server | Contenuti consegnati al caricamento della pagina tramite risposta Edge Network. Potrebbe essere necessaria una configurazione URI di superficie a livello di pagina. |

**Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Amministrazione > Canali > Superfici di canale

**Dettagli configurazione chiave:**

- Per le superfici web: configura l’URI della superficie web che corrisponde alle pagine di destinazione
- Per le superfici in-app: configura la superficie dell’app mobile con l’ID app e il tipo di superficie
- Per le superfici delle schede di contenuto: configura la superficie della scheda di contenuto con l’ID app o il contesto web
- Assicurati che lo stream di dati abbia il servizio AJO abilitato per la consegna di personalizzazione Edge

**Documentazione di Experience League:**

- [Introduzione al canale web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Configurazione del canale web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)
- [Prerequisiti per il canale in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [Configurazione scheda contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)

### Fase 4: Creazione dei contenuti

**Funzione dell&#39;applicazione:** AJO: authoring dei messaggi

**Configurazione:** creazione di varianti di contenuto personalizzate per ogni superficie e segmento o offerta. Ciò include la progettazione del layout visivo, l’aggiunta di espressioni di personalizzazione che fanno riferimento agli attributi del profilo, la configurazione di blocchi di contenuto condizionali e la creazione di frammenti di contenuto riutilizzabili.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: approccio contenuto**
>
>Come dovrebbero essere strutturati i contenuti personalizzati per questo caso d’uso?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Blocchi di contenuto condizionali | Sezioni di contenuto diverse all’interno dello stesso layout variano a seconda del pubblico | Una singola risorsa di contenuto con regole condizionali. Efficiente per varianti minori (titolo, testo CTA, scambio immagini). |
>| Varianti di contenuto separate per trattamento | Layout o design fondamentalmente diversi per pubblico | Risorse di contenuto complete multiple. Più flessibile, ma più facile da mantenere. Richiesto per la sperimentazione dei contenuti. |
>| Contenuti basati sulle decisioni | Contenuto selezionato dinamicamente da un catalogo di offerta | Le rappresentazioni di offerta definiscono il contenuto. La gestione dei contenuti è centralizzata nella libreria delle offerte. |

>[!NOTE]
>**Decisione: profondità Personalization**
>
>Quanto contenuto deve essere personalizzato?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Personalizzazione a livello di superficie | Solo elementi specifici sono personalizzati (immagine protagonista, CTA, banner offerta) | Riduzione della complessità. Personalizzazione incentrata su aree di alto impatto. Punto di partenza più comune. |
>| Personalizzazione a pagina intera | L’intero layout di pagina o l’ordinamento dei contenuti è personalizzato | Maggiore complessità. Richiede la creazione di contenuti estesi. Offre l’esperienza più personalizzata. |
>| Personalizzazione a livello di token | Token di personalizzazione in linea (nome, livello, saldo punti) | Forma più semplice. Inserisce i valori degli attributi di profilo nel contenuto altrimenti statico. |

**Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Campagne > Crea campagna > Modifica contenuto

**Opzioni divergenti:**

**Per l&#39;opzione A (basata su segmenti):**

- Puoi creare varianti di contenuto per ogni segmento di pubblico utilizzando il web designer o l’editor di codice
- Utilizzare blocchi di contenuto dinamici con condizioni basate sull’iscrizione al pubblico
- Configurare le espressioni di personalizzazione che fanno riferimento agli attributi del profilo (ad esempio, `{{profile.person.name.firstName}}`, `{{profile.loyalty.tier}}`)
- Imposta le regole condizionali per visualizzare contenuti diversi in base all’iscrizione al segmento

**Per l&#39;opzione B (basata su decisioni):**

- Creare rappresentazioni del contenuto delle offerte per ogni posizionamento definito nella fase 2
- Ogni offerta ha una o più rappresentazioni (HTML, image, JSON) corrispondenti ai posizionamenti
- Integrare l’output decisionale nella pagina web o nell’app incorporando i posizionamenti di decisione
- Il contenuto viene selezionato dinamicamente in fase di runtime; l’authoring si concentra sui singoli elementi dell’offerta

**Per l&#39;opzione C (multi-superficie):**

- Creare contenuti specifici per ogni superficie di destinazione (HTML web/CSS, messaggi strutturati in-app, layout della scheda dei contenuti)
- Mantenere una logica di personalizzazione coerente tra le superfici adattandosi ai vincoli di formato di ciascuna superficie
- Test del rendering del contenuto su ciascun tipo di superficie

**Documentazione di Experience League:**

- [Creare esperienze web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Funzioni di supporto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Creare messaggi in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [Creare schede di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/create-content-card)

### Fase 5: configurare e attivare le campagne

**Funzione dell&#39;applicazione:** AJO: Esecuzione della campagna

**Configurazione:** Crea e attiva la campagna AJO che associa il pubblico, la superficie e il contenuto per la consegna. Per la personalizzazione web, le campagne sono generalmente configurate per l’attivazione immediata o continua, anziché per invii pianificati una tantum.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: tipo di campagna**
>
>Come deve essere attivata la campagna di personalizzazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Campagna pianificata (sempre attiva) | Personalizzazione continua che viene eseguita in modo continuo per tutti i visitatori idonei | Impostare la data di inizio su immediata e nessuna data di fine. La campagna rimane attiva finché non viene arrestata manualmente. Più comune per la personalizzazione web. |
>| Campagna pianificata (con limiti di tempo) | Personalization associato a uno specifico periodo di promozione | Impostare le date di inizio e di fine. Campaign si interrompe automaticamente dopo la data di fine. Adatto per promozioni stagionali o offerte a tempo limitato. |
>| Campagna attivata da API | Personalization attivato da un evento applicazione specifico | Attivazione a livello di programmazione. Utile quando la personalizzazione dovrebbe apparire solo in risposta a specifici eventi di sistema. |

>[!NOTE]
>**Decisione: limite di frequenza**
>
>La frequenza delle impression deve essere limitata per questa personalizzazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Applicare le regole di frequenza | Personalizzazione promozionale o basata su offerte che potrebbero affaticare i visitatori | Impedisce che la stessa personalizzazione venga visualizzata troppe volte. Configurato tramite le regole aziendali di AJO. |
>| Nessun limite di frequenza | Personalizzazione dei contenuti Evergreen (banner livello fedeltà, contenuto dashboard) | Contenuti sempre rilevanti che non causano affaticamento. Non è necessario alcun limite di impression. |

**Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Campagne > Crea campagna

**Dettagli configurazione chiave:**

- Seleziona il canale web, in-app o della scheda di contenuto e la superficie configurata nella fase 3
- Associa il pubblico di destinazione definito nella fase 1
- Collegare i contenuti creati nella fase 4
- Configurare la pianificazione della campagna (immediata, intervallo di date o attivata da API)
- Rivedere e attivare la campagna
- Per la sperimentazione dei contenuti: abilita l’interruttore dell’esperimento, definisci i trattamenti, imposta l’allocazione del traffico e le metriche di successo prima dell’attivazione

**Documentazione di Experience League:**

- [Creare una campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Introduzione alle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Regole di frequenza](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Introduzione all’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Creare un esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### Fase 6: tenere traccia delle impression e raccogliere i dati

**Funzione dell&#39;applicazione:** AEP: Origini dati e raccolta

**Configurazione:** assicurati che le impression, le interazioni e le conversioni da esperienze personalizzate vengano tracciate nella piattaforma per il reporting, la rivalutazione del pubblico e l&#39;ottimizzazione del decisioning.

**Dettagli configurazione chiave:**

- Verifica che Web SDK invii `decisioning.propositionDisplay` eventi quando viene eseguito il rendering del contenuto personalizzato
- Verifica che Web SDK invii `decisioning.propositionInteract` eventi quando i visitatori interagiscono con contenuti personalizzati (clic, chiusure)
- Per Mobile SDK: verifica che vengano acquisiti gli eventi di interazione dei messaggi in-app e delle schede di contenuto
- Configurare il tracciamento degli eventi di conversione per le metriche di successo a valle (acquisti, iscrizioni, adozione di funzioni)
- Assicurati che gli eventi includano l’ID proposta per l’attribuzione a specifiche decisioni di personalizzazione

**Documentazione di Experience League:**

- [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Tracciare gli eventi con Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/commands/sendevent/overview)
- [Panoramica di Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)

### Fase 7: generare rapporti e ottimizzare

**Funzione dell&#39;applicazione:** AJO: Reporting &amp; Performance Analysis, Reporting &amp; Analysis

**Configurazione:** Imposta il monitoraggio e l&#39;analisi delle prestazioni per misurare l&#39;efficacia della personalizzazione tra superfici, segmenti e varianti di contenuto. Utilizza i rapporti nativi di AJO per le metriche operative e [!DNL Customer Journey Analytics] per l&#39;analisi dell&#39;impatto aziendale cross-channel.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: ambito di reporting**
>
>Quale livello di analisi è necessario per questo caso d’uso di personalizzazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Solo rapporti nativi di AJO | Monitoraggio operativo delle metriche di consegna e coinvolgimento | Rapporti incorporati sulle campagne con dati su impression, clic e conversione. Configurazione più rapida. |
>| Analisi cross-channel di CJA | Analisi approfondita dell’impatto della personalizzazione sui risultati aziendali | Richiede connessione CJA e visualizzazione dati. Consente l’analisi funnel, il confronto tra coorti e la modellazione di attribuzione tra canali diversi. |
>| Sia AJO che CJA | Visibilità operativa e analitica completa | Utilizza AJO per il monitoraggio quotidiano e CJA per l’analisi strategica. Consigliato per le implementazioni di produzione. |

**Navigazione interfaccia utente:**

- Rapporti di AJO: Campagne > Seleziona campagna > Visualizza rapporto
- CJA: Progetti > Crea nuovo progetto

**Dettagli configurazione chiave:**

- Accedere ai rapporti live delle campagne durante la consegna della personalizzazione attiva
- Esaminare i rapporti cronologici per le campagne completate o l’analisi periodica
- Per CJA: configura una connessione che includa i set di dati dell’evento esperienza AJO e crea una visualizzazione dati con metriche di personalizzazione
- Creare dashboard tenendo traccia del tasso di coinvolgimento nella personalizzazione, dell’incremento della conversione, del tasso di accettazione dell’offerta e dei ricavi per visita
- Per la personalizzazione basata sulle decisioni (opzione B): monitora le prestazioni dell’offerta in base al posizionamento e all’efficacia della strategia di classificazione

**Documentazione di Experience League:**

- [Rapporto live delle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapporto sull’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Considerazioni sull’implementazione

Questa sezione descrive guardrail, insidie comuni, best practice e decisioni di compromesso pertinenti a questo caso d’uso.

### Guardrail e limiti

- Edge Network lookups have a response time SLA of less than 200ms for edge-evaluated segments -- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximum of 4,000 segment definitions per sandbox -- [Segmentation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Edge segments are limited to simple attribute checks and segment membership queries -- no time-series queries -- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- Only one merge policy can be active on Edge per sandbox -- [Merge policies](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- Maximum of 10,000 approved personalized offers per sandbox -- [Decision Management guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum of 30 placements per decision -- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- I modelli di classificazione IA richiedono almeno 1.000 eventi di conversione per la formazione
- Offer Delivery response time SLA is less than 500ms at P95 for single-scope requests
- Massimo 500 campagne live attive per sandbox: [guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum of 25 active computed attributes per sandbox -- [Computed attributes guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)

### Insidie comuni

- **Edge merge policy not configured:** Without an edge-active merge policy, the Edge Network cannot resolve the authenticated profile, causing personalization to fail or fall back to anonymous behavior. Ensure exactly one merge policy has `isActiveOnEdge: true` in the sandbox.
- **Audience not edge-eligible:** If audience segment rule expressions use time-series queries, complex aggregations, or `inSegment()` references to batch-only segments, they will not qualify for edge evaluation and cannot power real-time personalization. Validate edge eligibility during audience definition.
- **Identity stitching gap during authentication:** When a visitor transitions from anonymous to authenticated, there may be a brief moment where the profile has not yet resolved. Ensure identity stitching is properly configured and that the Web SDK sends the authenticated identity via `identityMap` immediately upon login.
- **Missing fallback offer in decisioning:** If no fallback offer is configured and no personalized offer qualifies for a visitor, the decision returns empty content, creating a broken experience. Always configure a fallback offer that covers all placements.
- **Web SDK not sending proposition display events:** If `renderDecisions` is set to `true` but display events are not being sent, reporting will not reflect actual impressions. Verify event tracking by inspecting network requests in browser developer tools.
- **Content flicker on page load:** If personalized content is not pre-hidden during the decisioning call, visitors may see default content briefly before it is replaced. Use the pre-hiding snippet or CSS-based pre-hiding to eliminate flicker.

### Best practice

- Start with segment-based personalization (Option A) for initial implementation, then evolve to decisioning-based (Option B) as the offer catalog grows and optimization needs increase
- Use edge-evaluated audiences whenever possible for real-time personalization; reserve streaming and batch audiences for complementary use cases
- Implement content experimentation on personalized experiences to validate that personalization drives measurable lift over default content
- Design personalization with a graceful degradation strategy -- if the profile cannot be resolved at the edge, display well-designed default content rather than a broken experience
- Use computed attributes to create high-value personalization signals like engagement score, product affinity, and days since last purchase, which improve both segment-based and decisioning-based personalization quality
- Maintain a content governance process to ensure personalized content stays current, on-brand, and compliant across all surfaces
- Monitor personalization performance by segment to identify which audiences benefit most from personalization and where the lift is strongest

### Decisioni di compromesso

>[!NOTE]
>**Trade-off: Personalization granularity vs. content management complexity**
>
>More granular personalization (more segments, more content variants, more surfaces) delivers increasingly tailored experiences but requires proportionally more content creation, maintenance, and governance effort.
>
>- **Higher granularity favors:** Better customer experience, higher engagement, stronger conversion lift
>- **Lower granularity favors:** Faster implementation, lower content maintenance burden, simpler governance
>- **Recommendation:** Start with 3-5 high-impact segments (e.g., loyalty tiers or lifecycle stages) with clear content differentiation. Expand granularity based on measured performance lift. Use decisioning (Option B) to scale granularity without proportional content management growth.

>[!NOTE]
>**Trade-off: Real-time decisioning vs. deterministic content control**
>
>Decisioning-based personalization (Option B) provides dynamic optimization but reduces direct control over which content each visitor sees. Segment-based personalization (Option A) provides full deterministic control but limits dynamic optimization.
>
>- **Decisioning favors:** Scalability, automatic optimization, complex eligibility scenarios
>- **Segment-based favors:** Predictability, compliance control, stakeholder transparency
>- **Recommendation:** Use segment-based personalization for compliance-sensitive content (regulatory messaging, tier-specific pricing) where exact control is required. Use decisioning for promotional content, offers, and recommendations where dynamic optimization adds value.

>[!NOTE]
>**Trade-off: Edge data availability vs. personalization richness**
>
>Edge-evaluated personalization is limited to attributes available in the edge profile store. Richer personalization signals (full behavioral history, complex computed attributes) may require server-side lookup or pre-computation.
>
>- **Solo Edge favorisce:** Latenza al secondo, architettura più semplice
>- **L&#39;arricchimento precalcolato favorisce:** segnali di personalizzazione più ricchi, definizioni di pubblico più sofisticate
>- **Consiglio:** utilizza attributi calcolati per preaggregare segnali comportamentali avanzati in attributi di profilo disponibili per Edge. Questo fornisce la ricchezza dei dati comportamentali con la velocità della valutazione Edge.

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sulle tecnologie e le configurazioni a cui si fa riferimento in questa guida.

### Personalizzazione del canale web

- [Introduzione al canale web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Creare esperienze web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Configurazione del canale web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)

### Canali in-app e schede di contenuto

- [Panoramica del canale in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [Prerequisiti per il canale in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [Creare messaggi in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [Canale scheda contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Configurazione scheda contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)
- [Creare schede di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/create-content-card)

### Gestione delle decisioni

- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Creare i posizionamenti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Creare regole di decisione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Creare offerte di fallback](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Creare le raccolte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Personalization and content

- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Funzioni di supporto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilizzare i frammenti di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

### Tipi di pubblico e segmentazione

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Identità e profilo

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Regole di collegamento del grafo identità](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Panoramica del profilo](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Data collection and SDK

- [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Installare Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Panoramica di Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Panoramica dell’API del server Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### Campagne e sperimentazione

- [Introduzione alle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Creare una campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Introduzione all’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Creare un esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapporto sull’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### Attributi calcolati e arricchimento

- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Guida dell’interfaccia utente attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Panoramica di Customer AI](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Reporting e analisi

- [Rapporto live delle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Governance and privacy

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### Guardrail

- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Guardrail del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
