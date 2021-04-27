---
title: Attivazione di tipi di pubblico e profili alla blueprint delle destinazioni Enterprise
description: Attivazione di tipi di pubblico e profili nelle destinazioni aziendali
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: 2f35195b875d85033993f31c8cef0f85a7f6cccc
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 15%

---

# Attivazione di tipi di pubblico e profili alla blueprint delle destinazioni Enterprise

Condividi modifiche ed eventi di profilo e pubblico in streaming o in batch da [!UICONTROL Real-time Customer Data Platform] agli archivi dati e alle applicazioni aziendali. Questi eventi di profilo e pubblico possono essere utilizzati per avviare un&#39;azione di vendita o supporto al cliente, ad esempio per dare seguito a un processo di applicazione abbandonato o a una registrazione di un webinar oppure per aggiornare le applicazioni aziendali con gli attributi e le informazioni più recenti del cliente da [!UICONTROL Real-time Customer Data Platform].

## Casi di utilizzo

* Attivazione di profili e pubblico su destinazioni di archiviazione cloud o di streaming per il tracciamento, l’archiviazione, l’analisi e l’attivazione di dati e informazioni sui clienti.

## Applicazioni

* Adobe Experience Platform Attivazione

## Architettura

<img src="assets/enterprise_destination.svg" alt="Architettura di riferimento per lo scenario di attivazione Enterprise" style="border:1px solid #4a4a4a" />

## Guardrail

[Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)

### Guardrail per la valutazione e l’attivazione dei segmenti

| Tipo di segmentazione | Frequenza | Throughput | Latenza (Valutazione segmento) | Latenza (attivazione segmento) | Payload di attivazione |
|-|-|-|-|-|-|-|
| Segmentazione Edge | La segmentazione di Edge è attualmente in versione beta e consente di valutare la segmentazione in tempo reale valida su Experience Platform Edge Network per le decisioni in tempo reale e sulla stessa pagina tramite Adobe Target e Adobe Journey Optimizer. |  | ~100 ms | Disponibile immediatamente per la personalizzazione in Adobe Target, per la ricerca di profili nel profilo Edge e per l’attivazione tramite destinazioni basate su cookie. | Appartenenze al pubblico disponibili in Edge per ricerche di profilo e destinazioni basate su cookie.<br>Le iscrizioni al pubblico e gli attributi del profilo sono disponibili per Adobe Target e Journey Optimizer.  |
| Segmentazione streaming | Ogni volta che un nuovo evento di streaming o un nuovo record viene acquisito nel profilo del cliente in tempo reale e la definizione del segmento è un segmento di streaming valido. <br>Consulta la  [documentazione sulla ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it) segmentazione per informazioni sui criteri dei segmenti in streaming | Fino a 1500 eventi al secondo.  | ~ p95 &lt;5min | Destinazioni streaming: Le iscrizioni al pubblico in streaming vengono attivate entro circa 10 minuti o in modalità micro-batch in base ai requisiti della destinazione.<br>Destinazioni pianificate: Le appartenenze al pubblico in streaming vengono attivate in batch in base al tempo di consegna della destinazione pianificato. | Destinazioni streaming: Modifiche all’appartenenza al pubblico, valori di identità e attributi di profilo.<br>Destinazioni pianificate: Modifiche all’appartenenza al pubblico, valori di identità e attributi di profilo. |
| Segmentazione incrementale | Una volta all’ora per i nuovi dati che sono stati acquisiti nel profilo del cliente in tempo reale dall’ultima valutazione del segmento incrementale o batch. |  |  | Destinazioni streaming: Le iscrizioni incrementali al pubblico vengono attivate entro circa 10 minuti o in micro-batch in base ai requisiti della destinazione.<br>Destinazioni pianificate: Le iscrizioni incrementali al pubblico vengono attivate in batch in base al tempo di consegna pianificato per la destinazione. | Destinazioni streaming: Solo modifiche dell&#39;appartenenza al pubblico e valori di identità.<br>Destinazioni pianificate: Modifiche all’appartenenza al pubblico, valori di identità e attributi di profilo. |
| Segmentazione in batch | Una volta al giorno in base a una pianificazione prestabilita del sistema impostata o ad hoc avviato manualmente tramite API. |  | Circa un&#39;ora per lavoro per un massimo di 10 TB di dimensioni dell&#39;archivio profili, 2 ore per lavoro per 10 TB a 100 TB di dimensioni dell&#39;archivio profili. Le prestazioni del processo del segmento batch dipendono dal numero di profili, dalle dimensioni dei profili e dal numero di segmenti valutati. | Destinazioni streaming: Le iscrizioni a gruppi di pubblico vengono attivate entro circa 10 giorni dal completamento della valutazione della segmentazione o in micro-batch in base ai requisiti della destinazione.<br>Destinazioni pianificate: Le appartenenze a un pubblico batch vengono attivate in base al tempo di consegna della destinazione pianificato. | Destinazioni streaming: Solo modifiche dell&#39;appartenenza al pubblico e valori di identità.<br>Destinazioni pianificate: Modifiche all’appartenenza al pubblico, valori di identità e attributi di profilo. |



## Fasi di implementazione

1. Creare schemi per i dati da acquisire.
1. Crea set di dati per i dati da acquisire.
1. Configurare correttamente le identità e i relativi namespace nello schema, affinché i dati acquisiti possano essere uniti in un profilo unificato.
1. Abilita gli schemi e i set di dati per l’elaborazione dei profili.
1. Configura le origini per l’acquisizione dei dati.
1. Segmenti di authoring in Experience Platform, da valutare in batch o in streaming. Il sistema determina automaticamente se un segmento deve essere valutato in batch o in streaming.
1. Configurare le destinazioni per condividere gli attributi del profilo e delle appartenenze al pubblico con le destinazioni desiderate.

## Considerazioni sull’implementazione

Attivazione di attributi e identità

* [!UICONTROL Real-time Customer Data ] Platform può attivare le iscrizioni al pubblico e le modifiche di attributi e identità che si verificano per i profili che sono membri di segmenti selezionati per l’attivazione. Se l’obiettivo è quello di attivare attributi o identità, devi definire un segmento globale che includa tutti i profili a cui vengono inviati gli aggiornamenti di attributi e identità. A questo punto, puoi selezionare il segmento e gli attributi desiderati da attivare come parte della configurazione di destinazione.
* Le destinazioni batch non supportano l’attivazione di eventi di modifica solo attributi. È possibile inviare iscrizioni di pubblico complete o incrementali insieme agli attributi selezionati per l’attivazione, ma non è possibile attivare eventi di modifica di solo attributi tramite destinazioni batch.

Attivazione di segmenti batch nelle destinazioni di streaming

* È supportata l’attivazione dei segmenti in batch per le destinazioni in streaming. I processi dei segmenti in batch inseriscono i messaggi nella pipeline una volta che il processo del segmento è stato completato per l’attivazione in streaming

Attivazione di segmenti in streaming su destinazioni batch

* È supportata l’attivazione dei segmenti in streaming verso la destinazione batch. La pianificazione della destinazione batch esporta le appartenenze dei segmenti di profilo in base alla pianificazione della destinazione batch. Ciò include sia le appartenenze ai segmenti determinate tramite i metodi di streaming che i metodi batch.

Attivazione di eventi di esperienza

* L’attivazione di eventi di esperienza non elaborati non è supportata. Per attivarsi in base agli eventi di esperienza, è necessario creare un segmento con le regole necessarie che includono o escludono la logica dell’evento di esperienza. Questo crea un segmento definito rispetto agli eventi di esperienza e l’appartenenza al segmento può essere attivata come proxy per l’attivazione di eventi di esperienza non elaborati. Considera anche l’utilizzo di [!UICONTROL Launch Server Side] per attivare eventi di esperienza non elaborati raccolti tramite SDK.

## Documentazione correlata

* [Documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=it)
* [Panoramica delle destinazioni di archiviazione cloud](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [Destinazione HTTP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [Descrizione del prodotto Real-time Customer Data Platform](https://helpx.adobe.com/it/legal/product-descriptions/real-time-customer-data-platform.html)
* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Documentazione sulla segmentazione](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)

## Video e tutorial correlati

* [Panoramica di Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=it)
* [[!UICONTROL Demo di Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=it)
* [Creare segmenti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=it)
