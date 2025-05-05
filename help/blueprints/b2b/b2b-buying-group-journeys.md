---
title: Blueprint per l’acquisto di attività di marketing e gestione dei Percorsi basate su gruppi
description: Scopri come ideare, progettare e creare un percorso idoneo che porti a un gruppo di acquisto in Adobe Journey Optimizer B2B edition.
solution: Journey Optimizer B2B Edition
exl-id: 0a9da49c-f13a-4f2a-8407-277def2db591
source-git-commit: b777ea5c301fb1fac39bc243b09a02a2f411f40e
workflow-type: tm+mt
source-wordcount: '2118'
ht-degree: 0%

---

# Acquisto di un modello di marketing e gestione dei Percorsi basato su gruppi

Attualmente i team di marketing devono affrontare molte sfide per fornire alle vendite lead qualificati. Una di queste sfide è lavorare con le persone giuste nell&#39;organizzazione ed è di solito evidente nello sforzo e nella precisione. Con _punteggio lead_, il gruppo è troppo ristretto e i team potrebbero perdere le persone giuste. Con il _punteggio account_, è necessario uno sforzo maggiore per identificare la persona giusta con una visualizzazione così ampia di un account.

In questa sfida viene introdotto il concetto di **_gruppo di acquisto_**. Un gruppo di acquisto consente agli esperti di marketing di trovare il gruppo giusto di persone nell’account e di lavorare con tali persone attraverso la lente di qualificazione dei lead e identificazione del loro ruolo nel gruppo.

## Utilizzo dei gruppi di acquisto per qualificare lead e account

La creazione di un gruppo di acquisto e il suo impegno a completarlo aumentano l’efficacia dell’attività di marketing nella qualificazione e portano a opportunità di vendita. I gruppi di acquisto si basano sulla corrispondenza dei lead per creare modelli di ruolo collegati alle finalità della soluzione.

Un esempio di gruppo di acquisto potrebbe essere _Gruppo di acquisto di seed di Acme Corp_, che ha un interesse per la soluzione di _Seed guidati da IA_.

I gruppi di acquisto rappresentano un gruppo di persone dell’azienda che sono interessate a una soluzione attraverso un intento di soluzione. Un gruppo di acquisto può essere identificato per più di una soluzione e i singoli utenti appaiono in più gruppi di acquisto.

Grazie alle nuove funzionalità B2B di Journey Optimizer B2B edition, è ora possibile affrontare queste sfide:

* Mancanza di _campagne di marketing customer-first_.
* Conversione incoerente di Marketing Qualified Lead (MQL) in Sales Qualified Lead (SQL), che richiede l&#39;allineamento delle iniziative con le vendite per sviluppare MQL
* Mancanza di un meccanismo di vendita per identificare e indirizzare gli account _competitivi_.
* Rischio di concentrazione nei ricavi e nella pipeline.

I seguenti KPI sono in linea con la misurazione del successo dei casi d’uso:

* **Consapevolezza**: i clienti target che visualizzano i tuoi annunci pubblicitari vengono indirizzati al tuo sito Web a una velocità superiore rispetto a prima?
* **Coinvolgimento**: i clienti target accedono al tuo sito Web e sono interessati ai contenuti?
* **Tempo**: quanto tempo impiega il team vendite per trovare e aggiungere contatti da vari strumenti all&#39;opportunità?
* **Costo**: quanto costa ogni lead su ogni piattaforma?

## Marketing basato su account

Un caso d’uso comune e su cui si concentra questo blueprint, è un’iniziativa di marketing basata sull’account. Questo caso d’uso esplora il punto in cui il gruppo di acquisto creato viene popolato con un lead quando questi sono associati a un ruolo e a un interesse per la soluzione.

Mentre guidi un individuo attraverso il percorso, raccogli ulteriori informazioni sul lead (Flusso di lavoro del gruppo acquisti), tramite moduli, sincronizzazione CRM e attivazione LinkedIn.

Quando un lead dimostra chiaramente l&#39;interesse della soluzione, indica un evento di business definito da un obiettivo di business. A questo punto, l&#39;azienda è sicura che il lead sia realmente interessato a un prodotto. In Journey Optimizer B2B edition, il lead è associato a un gruppo di acquisto per tale soluzione in un modello di ruoli (ad esempio influencer, decision maker, campioni e sponsor).

Come illustrato nel diagramma seguente, è possibile raccogliere i dettagli nei moduli o tramite l’attivazione di LinkedIn e qualificare un intento della soluzione quando si è verificata un’interazione con un chat-bot.

![percorso di gruppi di acquisto](./assets/buying-group-journey-diagram.svg){zoomable="yes"}

Quando la percentuale di completamento del gruppo di acquisto è sufficientemente alta, il gruppo viene condiviso con il team vendite tramite SQL o SOL per convertire i lead nell&#39;account in una vendita completata.

## Soluzione incentrata sull&#39;account

L’obiettivo della gestione dei lead B2B è sugli account e sui relativi lead. Il livello tecnico è configurato per supportare i dati che rappresentano queste caratteristiche, un requisito fondamentale per la corretta segmentazione degli account e la gestione dei percorsi.

### Requisiti

La soluzione incentrata sull&#39;account richiede le applicazioni e i servizi seguenti:

* Adobe Journey Optimizer B2B edition
* B2B edition di Adobe Real-time Customer Data Platform (RTCDP)
* Adobe Marketo Engage

>[!NOTE]
>
>Le licenze di Journey Optimizer B2B edition devono includere i seguenti elementi:
><ul><li>Istanza B2B edition di Journey Optimizer connessa a Experience Platform B2B</li><li>Istanza di Marketo Engage sincronizzata con RTCDP</li></ul>
>&gt;<br/>
>&gt;Per i clienti di Marketo Engage esistenti, l’approccio consigliato è quello di connettersi all’istanza esistente.
>&gt;<br/><br/>
>&gt;Sono disponibili estensioni aggiuntive per la soluzione per migliorare la ricchezza dei profili:
>&gt;<ul><li>Origini aggiuntive a RTCDP per arricchire il profilo</li><li>Destinazione RTCDP al Marketo Engage</li></ul>

L&#39;implementazione di questa soluzione richiede inoltre una chiara comprensione del concetto di _account_ e _gruppo di acquisto_ e del modo in cui amplificano e accelerano la qualifica di lead di vendita. Con questa comprensione, devi anche identificare il punteggio di completezza del gruppo di acquisto desiderato.

### Architettura

![Architettura della soluzione per l&#39;acquisto di soluzioni di marketing e gestione dei percorsi](./assets/ajo-b2b-architecture.png){zoomable="yes"}

### Schema dati

Con qualsiasi implementazione di un’automazione di marketing basata sui dati, la progettazione di schemi è fondamentale per il successo dell’implementazione. Prima di progettare lo schema, esaminare gli spazi dei nomi e gli schemi [B2B](https://experienceleague.adobe.com/it/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo-namespaces) e accertarsi di conoscere l&#39;utilità di generazione automatica disponibile per generare un nuovo schema in un nuovo scenario di implementazione.

Gli schemi vengono arricchiti in modo specifico con elementi di dati B2B per supportare la relazione avanzata nei profili e includere la prospettiva dell&#39;account attraverso `sourceKey` per collegare eventi e profili allo schema dell&#39;account. Gli schemi rappresentano i requisiti organizzativi e i dati raccolti e profilati. Per soddisfare queste esigenze, gli schemi B2B sono flessibili e rappresentano un’estensione degli elementi B2B richiesti.

Durante la progettazione dello schema dati per l’organizzazione, è consigliabile rappresentare ed etichettare le entità principali nell’ERD con le entità di alto livello. (Vedi il primo diagramma nella [documentazione dello schema B2B RTCDP](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/tutorials/relationship-b2b)). Questo processo è molto utile per comprendere gli elementi dati richiesti da definire in ogni schema.

In questa fase, gli Eventi di esperienza non sono ancora in grado di influenzare i percorsi. Oltre agli schemi Experience Event, è consigliabile aggiungere all’account proprietà che rappresentano decisioni importanti in base alle attività degli utenti. Queste proprietà vengono utilizzate per gli elementi del percorso diviso nella finestra di progettazione del percorso.

>[!NOTE]
>
>Attualmente, l&#39;unica relazione supportata da Journey Optimizer B2B edition è quella diretta tramite l&#39;attributo `personComponents[0].sourceAccountKey.sourceKey` sull&#39;entità `Person`. L’espansione futura è pianificata per accogliere l’oggetto relazione account-persona nello schema B2b.

### Connettore sorgente Marketo Engage

Per arricchire gli elementi dati dell’account, puoi utilizzare i dati di Marketo Engage e i relativi dati B2B per arricchire la vista dell’account RTCDP e Journey Optimizer B2B edition. Impostando il connettore Source del Marketo Engage e mappando i dati del Marketo Engage agli attributi dello schema RTCDP, si consente il flusso dei dati dal Marketo Engage a RTCDP e, se designato, al profilo.

Per informazioni dettagliate sulla configurazione del connettore e sul mapping dei campi richiesti allo schema, consulta la [documentazione del connettore di Marketo Engage](https://experienceleague.adobe.com/it/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo).

### Guardrail

I guardrail di Journey Optimizer B2B edition sono descritti in dettaglio nella [pagina di descrizione del prodotto](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer-b2b.html).

Guardrail correlati all’implementazione

* Tutti i guardrail del pubblico B2B sono descritti nel blueprint di [Audience B2B e attivazione profilo](https://experienceleague.adobe.com/it/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails) e sono direttamente recepiti nel successo di Journey Optimizer B2B edition.
* Se l&#39;attivazione è necessaria tramite i canali del Marketo Engage nel percorso dell&#39;account o se CRM Sync viene utilizzato per arricchire l&#39;account, le [protezioni relative al Marketo Engage](https://helpx.adobe.com/it/legal/product-descriptions/adobe-marketo-engage---product-description.html#performance-guardrails) sono rilevanti.

Consulta la [documentazione dei guardrail di Real-Time CDP](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/guardrails/overview) per ulteriori dettagli sui guardrail di RTCDP.

### Provisioning

* Tutte le istanze devono trovarsi nella stessa organizzazione IMS.
* È possibile collegare una sola istanza di Journey Optimizer B2B edition a una sandbox di Experience Platform.
* Si consiglia di implementare il connettore Source [Marketo in Real-time Customer Data Platform](https://experienceleague.adobe.com/it/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo).

## Implementazione

I passaggi seguenti forniscono indicazioni per abilitare i gruppi di acquisto nell’istanza Journey Optimizer B2B edition, inclusa l’attivazione del pubblico per supportare l’espansione della base di account con particolare attenzione ai modelli di ruolo mancanti per i gruppi di acquisto.

### Passaggi preliminari

1. Definisci lo schema XDM che rappresenterà la visualizzazione aziendale di Account e Lead.

   Come primo passo, puoi definire e creare uno schema di esperienza progettato per soddisfare le esigenze dei casi d’uso B2B e coprire le origini dati, sia in batch che in tempo reale. Questa progettazione deve rappresentare il modo in cui l’azienda pensa alle entità account e persona e ai casi d’uso che desideri supportare. Affinché lo schema sia uno schema B2B, lo schema deve seguire le strutture disponibili nella [documentazione dello schema B2B RTCDP](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/tutorials/relationship-b2b).

   Una pratica utile consiste nell’estrarre i nomi delle entità dal diagramma e identificarli nello schema assegnandogli lo stesso marchio. Alcuni schemi richiedono chiavi specifiche, ad esempio `sourceKey`, per funzionare in RTCDP B2B. Nel breve periodo, la relazione _Many-to-Many_ tra account e persona tramite Account Person Relationship non è supportata in Journey Optimizer B2B. Utilizza gli script acceleratori per il miglior punto di partenza:

   * Utilizza lo script di creazione dello schema B2B [RTCDP](https://github.com/adobe/experience-platform-postman-samples/tree/master/Postman%20Collections/CDP%20Namespaces%20and%20Schemas%20Utility) per generare lo schema iniziale
   * Aggiungi campi specifici per il caso d’uso agli schemi generati per completare lo schema in base alle esigenze dell’organizzazione.

   In questa fase, è presente la connessione tra Marketo Engage e RTCDP e viene definita la struttura dello schema per accettare i dati dell’account e della persona per compilare i set di dati per i segmenti dell’account. Il passaggio successivo consiste nel collegare RTCDP a Marketo Engage e Journey Optimizer B2B edition.

1. Configura il connettore di Marketo Engage, inclusa la mappatura del Marketo Engage alla struttura XDM.

   Con la struttura e i campi XDM impostati, procedi al collegamento del Marketo Engage a RTCDP utilizzando il connettore, che alimenta i set di dati con i dati di Marketo Engage e Journey Optimizer B2B. Inizia organizzando la mappatura dei campi dalle classi Marketo Engage a RTCDP. Utilizza le informazioni contenute nella [documentazione del connettore](https://experienceleague.adobe.com/it/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo#field-mapping-from-marketo-engage-to-xdm) per identificare i campi da includere nell&#39;implementazione del Marketo Engage.

### Configurazione gruppo di acquisto

1. Creare tipi di pubblico per gli account in Journey Optimizer B2B edition o RTCDP.

   Per abilitare i tipi di pubblico per account, abilita l’opzione Pianificazione di tutti i tipi di pubblico nella pagina Customer → Audiences → Browse (Sfoglia). (Nei casi in cui questo non funziona, devi creare un segmento Profilo cliente per poter abilitare la creazione dei tipi di pubblico dell’account.)

   Per creare un segmento, segui i passaggi descritti nella [documentazione sul pubblico dell&#39;account](https://experienceleague.adobe.com/it/docs/journey-optimizer-b2b/user/account-audiences/account-audience-overview). L’utilizzo di Segment Builder con i campi di dati identificati come chiave per il pubblico del tuo account sarebbe l’attività chiave per definire il pubblico.

   In questa fase, si sa che l&#39;account conduce a concentrarsi su attraverso RTCDP e da utilizzare per i blocchi costitutivi del gruppo di acquisto.

1. Definisci il modello dei ruoli.

   In ogni gruppo di acquisto, identifica i ruoli che rappresentano il ruolo che i singoli utenti assumono nel gruppo a cui desideri indirizzare. Ad esempio, puoi utilizzare _decision maker_, _influencer_ e _champion_. Definisci anche il peso e le condizioni per questo ruolo nel gruppo di acquisto.

   Nella documentazione dei modelli di [ruoli](https://experienceleague.adobe.com/it/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates) è descritto questo processo e come definire condizioni speciali.

1. Definisci l’interesse della soluzione.

   Un interesse nella soluzione è un modo per indicare che i gruppi di acquisto si concentrano sulle attività e sulla strategia di marketing.

   Per definire un interesse di soluzione, segui i passaggi descritti nella [documentazione sugli interessi di soluzione](https://experienceleague.adobe.com/it/docs/journey-optimizer-b2b/user/buying-groups/solution-interests). Tieni presente che puoi utilizzarlo per associare il gruppo di acquisto a un’iniziativa di vendita nell’organizzazione.

1. Configura il gruppo di acquisto.

   Con i blocchi predefiniti del gruppo di acquisto pronti, configura il gruppo di acquisto per l’interesse della soluzione e il pubblico dell’account con un target per completare il modello dei ruoli con i membri giusti dell’account. Con questa configurazione, assegna un interesse per la soluzione al modello di ruoli identificato e attribuisci a ogni ruolo un peso nel successo delle vendite per quel prodotto specifico.

   Per creare il gruppo di acquisto, segui i passaggi descritti nella [documentazione sui gruppi di acquisto](https://experienceleague.adobe.com/it/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create).

   A questo punto, sei pronto a [creare un percorso](https://experienceleague.adobe.com/it/docs/journey-optimizer-b2b/user/account-journeys/journey-overview#get-started-with-a-journey) e iniziare a lavorare con il pubblico dell&#39;account per creare il gruppo di acquisto e qualificarlo per l&#39;interesse della soluzione.

### Attivazione pubblico

Aumenta la completezza del gruppo di acquisto tramite l’attivazione del pubblico.

1. Definisci un pubblico di account LinkedIn Ad Matched.

   Oltre alle attività di e-mail e compilazione di moduli, Journey Optimizer B2B edition offre una funzionalità LinkedIn Ad per aumentare l’ampiezza del tuo account e supportare lo sforzo di completare un gruppo di acquisto attraverso l’espansione dell’estensione dei lead dell’account e l’aumento della portata delle tue attività di marketing.

   Per utilizzare LinkedIn Paid Media per comunicare con gli account in cui i gruppi di acquisto non sono completati o coinvolti a sufficienza, espandere o coinvolgere il pubblico dell&#39;account, utilizzare la funzionalità [Tipi di pubblico associati all&#39;account di LinkedIn](https://experienceleague.adobe.com/it/docs/journey-optimizer-b2b/user/account-audiences/linkedin-account-matched-audiences) per generare i tipi di pubblico di LinkedIn Ad tramite i tipi di pubblico associati all&#39;account.

1. Attiva il pubblico per i gruppi di acquisto.

>[!TIP]
>
>Alcuni suggerimenti per campagne di successo:
>
>* Una campagna deve avere dei filtri di ruolo per adattarsi ai gruppi di acquisto con ruoli mancanti per aumentare il ROI.
>* Per acquisire i lead, indirizza i lead alla compilazione dei moduli (moduli LinkedIn o di Marketo Engage) e ridistribuisce i mancati riscontri nei moduli.
