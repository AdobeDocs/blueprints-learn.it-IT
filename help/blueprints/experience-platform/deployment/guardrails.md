---
title: Guardrail di Experience Platform e applicazione e latenze end-to-end
description: I guardrail definiscono le aspettative a livello di prestazioni e l’impatto per i componenti e i servizi in Adobe Experience Platform e nelle relative applicazioni
solution: Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: a16d7e925b7f5e9a379214d01280e4fef56344af
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 22%

---

# Guardrail e latenze end-to-end

I guardrail sono soglie consigliate che forniscono indicazioni per i dati, le latenze osservate e l’utilizzo del sistema in Adobe Experience Platform e nelle applicazioni. I guardrail riflettono i vincoli di sistema e le aspettative di prestazioni per ottimizzare l’architettura del cliente e le prestazioni del caso d’uso, e aiutano a evitare errori o risultati imprevisti. I guardrail non sono destinati ad essere accordi sui livelli di servizio.

Per informazioni sugli accordi sui livelli di servizio specifici per applicazioni e funzionalità, consultare [Descrizioni di applicazioni e funzionalità](#application-feature-descriptions) nella parte inferiore della pagina.


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

### Acquisizione dei dati {#data-ingestion}

Il diagramma seguente mostra i valori previsti della latenza di acquisizione dei dati tramite [acquisizione in streaming](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html) e [acquisizione batch](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=it) quando si importano dati in Real-Time CDP. Fai clic sull’immagine per visualizzarne una versione ad alta risoluzione.

![Panoramica visiva di alto livello sull’acquisizione dei dati.](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg "Acquisizione dei dati: panoramica visiva di alto livello e valori di latenza"){width="1000" zoomable="yes"}

### Segmentazione {#segmentation}

Il diagramma seguente mostra i valori di latenza previsti quando si lavora con tipi di pubblico in [Servizio di segmentazione di Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=it). Fai clic sull’immagine per visualizzarne una versione ad alta risoluzione.

![Panoramica visiva di alto livello sulla segmentazione.](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg "Segmentazione dei valori di panoramica visiva e latenza di alto livello"){width="1000" zoomable="yes"}

### Real-time Customer Data Platform e Adobe Target {#adobe-target-latency}

Il diagramma seguente mostra i valori di latenza previsti per l’esportazione dei tipi di pubblico da Real-Time CDP a [Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=it). Fai clic sull’immagine per visualizzarne una versione ad alta risoluzione.

![Esportare in Adobe Target: panoramica visiva di alto livello.](/help/blueprints/experience-platform/deployment/assets/RTCDP_Target_guardrails.svg "Esportazione di tipi di pubblico in Adobe Target: panoramica visiva di alto livello e valori di latenza"){width="1000" zoomable="yes"}

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
