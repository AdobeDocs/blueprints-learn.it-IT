---
title: Guarderail per Experience Platform e applicazioni
description: I guardrail definiscono le aspettative a livello di prestazioni e l’impatto per i componenti e i servizi in Adobe Experience Platform e nelle relative applicazioni
solution: Experience Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: a5d127c2a9e18ebbf25012475b9f474c07575362
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 10%

---


# Guardrail

I guardrail riflettono i vincoli di sistema, le latenze previste e le aspettative di prestazioni per ottimizzare l’architettura del cliente e le prestazioni del caso d’uso, nonché per garantire stabilità, evitare errori o risultati imprevisti.

## Tipi di guardrail

| Tipo di guardrail | Descrizione |
|---|---|
| Guardrail delle prestazioni (limite morbido) | I guardrail delle prestazioni sono limiti di utilizzo che si riferiscono all’ambito dei casi d’uso e delineano le prestazioni previste in condizioni normali. Quando viene superato, è possibile che si verifichi un peggioramento delle prestazioni e della latenza. I guardrail delle prestazioni sono documentati nei documenti di Experience League nelle sezioni di guardrail per ciascuna soluzione, come descritto di seguito. |
| Limite statico (limite rigido) | Si tratta di limiti applicati dal sistema che non possono essere superati. I limiti statici sono in genere associati contrattualmente e delineati nel contratto del cliente e nelle [descrizioni prodotto](https://helpx.adobe.com/legal/product-descriptions.html). |

>[!NOTE]
>
> I guardrail non sono destinati a essere accordi sui livelli di servizio, ma piuttosto indicazioni per configurazioni ottimali e comportamenti di sistema attesi. Eventuali guardrail che rappresentano limiti di sistema o contrattuali o accordi sul livello di servizio saranno documentati in modo specifico nei contratti con i clienti e nelle descrizioni dei prodotti. Se ti interessa conoscere i limiti personalizzati, contatta il rappresentante dell’assistenza clienti.

>[!NOTE]
>
> Per i casi d’uso con rigide esigenze di latenza o prestazioni, Adobe consiglia di discutere i dettagli con il team del tuo account Adobe e con il partner dell’implementazione. Ogni configurazione del cliente può variare tra i pattern di acquisizione dei dati, i conteggi e la ricchezza dei profili, le regole dei segmenti e i canali di attivazione. È quindi importante progettare e testare il caso d’uso per ottimizzarne le prestazioni e comprenderne appieno le caratteristiche.

## Documentazione di riferimento sui guardrail per Adobe Experience Platform e relative applicazioni

Nelle pagine seguenti vengono fornite informazioni sui guardrail per le funzioni, i servizi e le applicazioni di Adobe Experience Platform:

**applicazioni di Experience Platform**

* [Panoramica sui guardrail di Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Guardrail di condivisione del pubblico di Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
* [guardrail di acquisizione dati di Customer Journey Analytics](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Guardrail Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html)

**Servizi Experience Platform**

* [Guardrail per l’acquisizione dei dati](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html)
* [[!DNL Edge Network] Guardrail API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [Guardrail di segmentazione e profilo cliente in tempo reale](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)
* [Guardrail per il servizio Identity](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=it)
* [Guardrail per il servizio Query](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=it)
* [Guardrail per l’attivazione delle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=it)

## Diagrammi di latenza end-to-end {#end-to-end-latency}

### Edge Network Experience Platform e latenze osservate primarie dall’hub {#edge-hub-latencies}

Il diagramma seguente illustra le latenze osservate primarie a livello di spigolo e hub di cui tenere conto durante l’architettura del caso d’uso nell’Experience Platform e nelle applicazioni.

![Experience Platform [!DNL Edge Network] e latenze osservate primarie hub.](/help/blueprints/experience-platform/deployment/assets/aep_edge_hub_latency_v1.svg "Latenze osservate primarie per Edge Network Experience Platform e hub"){width="1000" zoomable="yes"}

### Acquisizione dei dati {#data-ingestion}

Nel diagramma seguente vengono visualizzati i valori previsti della latenza di acquisizione dei dati tramite [acquisizione in streaming](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html) e [acquisizione in batch](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=it) per l&#39;importazione di dati in Real-Time CDP. Fai clic sull’immagine per visualizzarne una versione ad alta risoluzione.

![Panoramica visiva di alto livello sull&#39;acquisizione dei dati.](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg "Panoramica visiva di alto livello sull&#39;acquisizione dei dati e valori di latenza"){width="1000" zoomable="yes"}

### Segmentazione {#segmentation}

Il diagramma seguente mostra i valori di latenza previsti quando si lavora con tipi di pubblico nel [servizio di segmentazione di Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=it). Fai clic sull’immagine per visualizzarne una versione ad alta risoluzione.

![Panoramica visiva di alto livello sulla segmentazione.](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg "Segmentazione dei valori di panoramica visiva di alto livello e latenza"){width="1000" zoomable="yes"}

### Real-time Customer Data Platform e [!DNL Edge Network] {#adobe-edge-latency}

Il diagramma seguente mostra i valori di latenza previsti quando si sfrutta [!DNL Edge Network], ad esempio per sfruttare i tipi di pubblico RTCDP in [Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=it). Fai clic sull’immagine per visualizzarne una versione ad alta risoluzione.

![Panoramica visiva di alto livello di Adobe Edge Network e Experience Platform.](/help/blueprints/experience-platform/deployment/assets/RTCDP_Edge_guardrails.svg "Esportazione di tipi di pubblico in Adobe Target: panoramica visiva di alto livello e latenza"){width="1000" zoomable="yes"}

### Blueprint per   {#customer-journey-analytics}

Nel diagramma seguente vengono visualizzati i valori di latenza previsti quando si lavora con [Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=en). Fai clic sull’immagine per visualizzarne una versione ad alta risoluzione.

![Utilizzo della panoramica visiva di alto livello del Customer Journey Analytics.](/help/blueprints/experience-platform/deployment/assets/CJA_guardrails.svg "Utilizzo dei valori di latenza e panoramica visiva di alto livello del Customer Journey Analytics"){width="1000" zoomable="yes"}

### Blueprint per   {#journey-optimizer}

Nel diagramma seguente vengono visualizzati i valori di latenza previsti per l&#39;utilizzo di [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=en). Fai clic sull’immagine per visualizzarne una versione ad alta risoluzione.

![Utilizzo della panoramica visiva di alto livello di Adobe Journey Optimizer.](/help/blueprints/experience-platform/deployment/assets/AJO_guardrails.svg "Utilizzo dei valori di latenza e panoramica visiva di alto livello di Adobe Journey Optimizer"){width="1000" zoomable="yes"}