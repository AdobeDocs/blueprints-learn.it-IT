---
title: Guarderail per Experience Platform e applicazioni
description: I guardrail definiscono le aspettative a livello di prestazioni e l’impatto per i componenti e i servizi in Adobe Experience Platform e nelle relative applicazioni
solution: Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 2ff576ccb4ac3f9e2bdb690b6e9242d674214c33
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 15%

---

# Guardrail

I guardrail sono soglie consigliate che forniscono indicazioni per i dati, le latenze osservate e l’utilizzo del sistema in Adobe Experience Platform e nelle applicazioni. I guardrail riflettono i vincoli di sistema e le aspettative di prestazioni per ottimizzare l’architettura del cliente e le prestazioni del caso d’uso, e aiutano a evitare errori o risultati imprevisti. I guardrail non sono destinati a essere accordi sui livelli di servizio; gli accordi sui livelli di servizio sono documentati nelle Descrizioni dei prodotti collegate di seguito e negli accordi di licenza con il cliente. I guardrail hanno lo scopo di fornire indicazioni nell’architettura di soluzioni per casi d’uso specifici dei clienti, al fine di garantire stabilità ed esecuzione.

Per informazioni sugli accordi sui livelli di servizio specifici per applicazioni e funzionalità, consultare [Descrizioni di applicazioni e funzionalità](#application-feature-descriptions) nella parte inferiore della pagina.

Tieni presente che, per qualsiasi caso di utilizzo di un cliente con rigidi requisiti di latenza o volume, Adobe consiglia di rivedere il caso di utilizzo in dettaglio con il team dell’account e il partner di implementazione di Adobe. In alcuni casi è consigliabile testare e osservare una determinata implementazione del caso d’uso prima dell’avvio della produzione del caso d’uso per osservare e comprendere il comportamento previsto - in quanto ogni implementazione del cliente ha diversi fattori in gioco, tra cui la natura e la frequenza dell’acquisizione dei dati, le specifiche delle regole dei segmenti che vengono create e i vari canali di attivazione e payload - ogni implementazione del caso d’uso avrà prestazioni osservate variabili. Di conseguenza, è meglio stabilire e testare le prestazioni previste fin dall’inizio per garantire un’architettura e un’implementazione adeguate in base ai requisiti di latenza e prestazioni del caso d’uso.


## Documentazione di riferimento sui guardrail per Adobe Experience Platform e relative applicazioni

Nelle pagine seguenti vengono fornite informazioni sui guardrail per le funzioni, i servizi e le applicazioni di Adobe Experience Platform:

**applicazioni Experienci Platform**

* [Panoramica sui guardrail di Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Guardrail di condivisione del pubblico Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
* [Guardrail di acquisizione dati di Customer Journey Analytics](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Guardrail Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html)

**servizi Experienci Platform**

* [Guardrail per l’acquisizione dei dati](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html)
* [Guardrail per Edge Network API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [Guardrail di segmentazione e profilo cliente in tempo reale](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)
* [Guardrail per il servizio Identity](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=it)
* [Guardrail per il servizio Query](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=it)
* [Guardrail per l’attivazione delle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=it)

## Diagrammi di latenza end-to-end {#end-to-end-latency}

### Latenze osservate primarie da rete Edge e hub Experienci Platform {#edge-hub-latencies}

Il diagramma seguente illustra le latenze osservate primarie a livello di spigolo e hub di cui tenere conto durante l’architettura del caso d’uso nell’Experience Platform e nelle applicazioni.

![Latenze osservate primarie della rete Edge e dell&#39;hub di Experience Platform.](/help/blueprints/experience-platform/deployment/assets/aep_edge_hub_latency.svg "Latenze osservate primarie di Experienci Platform Edge Network e hub"){width="1000" zoomable="yes"}

### Acquisizione dei dati {#data-ingestion}

Il diagramma seguente mostra i valori previsti della latenza di acquisizione dei dati tramite [acquisizione in streaming](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html) e [acquisizione batch](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=it) quando si importano dati in Real-Time CDP. Fai clic sull’immagine per visualizzarne una versione ad alta risoluzione.

![Panoramica visiva di alto livello sull’acquisizione dei dati.](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg "Acquisizione dei dati: panoramica visiva di alto livello e valori di latenza"){width="1000" zoomable="yes"}

### Segmentazione {#segmentation}

Il diagramma seguente mostra i valori di latenza previsti quando si lavora con tipi di pubblico in [Servizio di segmentazione di Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=it). Fai clic sull’immagine per visualizzarne una versione ad alta risoluzione.

![Panoramica visiva di alto livello sulla segmentazione.](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg "Segmentazione dei valori di panoramica visiva e latenza di alto livello"){width="1000" zoomable="yes"}

### Real-time Customer Data Platform e Edge Network {#adobe-edge-latency}

Il diagramma seguente mostra i valori di latenza previsti quando si utilizza la rete Edge, ad esempio per sfruttare i tipi di pubblico RTCDP in [Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=it). Fai clic sull’immagine per visualizzarne una versione ad alta risoluzione.

![Panoramica visiva di alto livello su Adobe Edge Network e Experienci Platform.](/help/blueprints/experience-platform/deployment/assets/RTCDP_Edge_guardrails.svg "Esportazione di tipi di pubblico in Adobe Target: panoramica visiva di alto livello e latenza"){width="1000" zoomable="yes"}

### Blueprint per   {#customer-journey-analytics}

Il diagramma seguente mostra i valori di latenza previsti quando si lavora con [Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=en). Fai clic sull’immagine per visualizzarne una versione ad alta risoluzione.

![Utilizzo di una panoramica visiva di alto livello del Customer Journey Analytics.](/help/blueprints/experience-platform/deployment/assets/CJA_guardrails.svg "Utilizzo dei valori Customer Journey Analytics di panoramica visiva di alto livello e latenza"){width="1000" zoomable="yes"}

### Blueprint per   {#journey-optimizer}

Il diagramma seguente mostra i valori di latenza previsti quando si lavora con [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=en). Fai clic sull’immagine per visualizzarne una versione ad alta risoluzione.

![Utilizzo della panoramica visiva di alto livello di Adobe Journey Optimizer.](/help/blueprints/experience-platform/deployment/assets/AJO_guardrails.svg "Utilizzo dei valori di latenza e panoramica visiva di alto livello di Adobe Journey Optimizer"){width="1000" zoomable="yes"}

## Descrizioni di applicazioni e funzionalità {#application-feature-descriptions}

Per informazioni sugli accordi sui livelli di servizio specifici per le funzioni, fare riferimento alle descrizioni dei prodotti riportate di seguito:

* [Experience Platform Collection Enterprise](https://helpx.adobe.com/it/legal/product-descriptions/adobe-experience-platform-collection-enterprise.html)
* [Real-time Customer Data Platform](https://helpx.adobe.com/it/legal/product-descriptions/real-time-customer-data-platform.html)
* [B2B Customer Data Platform](https://helpx.adobe.com/it/legal/product-descriptions/adobe-experience-platform-b2b.html)
* [Experience Platform Activation](https://helpx.adobe.com/it/legal/product-descriptions/adobe-experience-platform0.html)
* [Experience Platform Intelligence](https://helpx.adobe.com/it/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Intelligent Services](https://helpx.adobe.com/it/legal/product-descriptions/intelligent-services.html)
* [Data Distiller](https://helpx.adobe.com/it/legal/product-descriptions/data-distiller.html)
* [Customer Journey Analytics](https://helpx.adobe.com/it/legal/product-descriptions/customer-journey-analytics.html)
* [Journey Optimizer](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer.html)
* [Journey Orchestration](https://helpx.adobe.com/it/legal/product-descriptions/journey-orchestration.html)
* [Offer Decisioning](https://helpx.adobe.com/it/legal/product-descriptions/offer-decisioning-app-service.html)
