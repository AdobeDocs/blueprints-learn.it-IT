---
title: Guarderail per Experience Platform e applicazioni
description: I guardrail definiscono le aspettative a livello di prestazioni e l’impatto per i componenti e i servizi in Adobe Experience Platform e nelle relative applicazioni
solution: Experience Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 13%

---


# Guardrail

I guardrail riflettono i vincoli di sistema, le latenze previste e le aspettative di prestazioni per ottimizzare l’architettura del cliente e le prestazioni del caso d’uso, nonché per garantire stabilità, evitare errori o risultati imprevisti.

## Tipi di guardrail

| Tipo di guardrail | Descrizione |
|---|---|
| Guardrail delle prestazioni (limite morbido) | I guardrail delle prestazioni sono limiti di utilizzo che si riferiscono all’ambito dei casi d’uso e delineano le prestazioni previste in condizioni normali. Quando viene superato, è possibile che si verifichi un peggioramento delle prestazioni e della latenza. I guardrail delle prestazioni sono documentati nei documenti di Experience League nelle sezioni di guardrail per ciascuna soluzione come descritto di seguito. |
| Limite statico (limite rigido) | Si tratta di limiti applicati dal sistema che non possono essere superati. I limiti statici sono in genere associati contrattualmente e delineati nel contratto del cliente e nelle [descrizioni prodotto](https://helpx.adobe.com/legal/product-descriptions.html). |

>[!NOTE]
>
> I guardrail non sono destinati a essere accordi sui livelli di servizio, ma piuttosto indicazioni per configurazioni ottimali e comportamenti di sistema attesi. Eventuali guardrail che rappresentano limiti di sistema o contrattuali o accordi sul livello di servizio saranno documentati in modo specifico nei contratti con i clienti e nelle descrizioni dei prodotti. Se ti interessa conoscere i limiti personalizzati, contatta il rappresentante dell’assistenza clienti.

>[!NOTE]
>
> Per i casi d’uso con rigide esigenze di latenza o prestazioni, Adobe consiglia di discutere i dettagli con il team del tuo account Adobe e con il partner dell’implementazione. Ogni configurazione del cliente può variare tra i pattern di acquisizione dei dati, i conteggi e la ricchezza dei profili, le regole dei segmenti e i canali di attivazione. È quindi importante progettare e testare il caso d’uso per ottimizzarne le prestazioni e comprenderne appieno le caratteristiche.

## Documentazione di riferimento sui guardrail per Adobe Experience Platform e relative applicazioni

Nelle pagine seguenti vengono fornite informazioni sui guardrail per le funzioni, i servizi e le applicazioni di Adobe Experience Platform:

**Applicazioni Experience Platform**

* [Panoramica sui guardrail di Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Guardrail di condivisione del pubblico Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
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

### Latenze osservate primarie di Experience Platform Edge Network e Hub {#edge-hub-latencies}

Il diagramma seguente illustra le latenze osservate primarie a livello di perimetro e hub di cui tenere conto durante l’architettura del caso d’uso in Experience Platform e Applications.

![Latenze osservate primarie di Experience Platform [!DNL Edge Network] e hub.](/help/blueprints/experience-platform/assets/aep_edge_hub_latency_v1.svg "Latenze osservate primarie per Experience Platform Edge Network e hub"){width="1000" zoomable="yes"}