---
title: Attivazione di tipi di pubblico e profili alla blueprint delle destinazioni Enterprise
description: Attivazione di tipi di pubblico e profili nelle destinazioni aziendali
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: da21d1796eb9a2c9c0f087d82606874ca55bd4ea
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 39%

---

# Attivazione di tipi di pubblico e profili alla blueprint delle destinazioni Enterprise

Condividi modifiche ed eventi di profilo e pubblico in streaming o in batch da [!UICONTROL Real-time Customer Data Platform] agli archivi dati e alle applicazioni aziendali. Questi eventi di profilo e pubblico possono essere utilizzati per avviare un&#39;azione di vendita o supporto al cliente, ad esempio per dare seguito a un processo di applicazione abbandonato o a una registrazione di un webinar oppure per aggiornare le applicazioni aziendali con gli attributi e le informazioni più recenti del cliente da [!UICONTROL Real-time Customer Data Platform].

## Casi di utilizzo

* Attivazione di profili e pubblico su destinazioni di archiviazione cloud o di streaming per il tracciamento, l’archiviazione, l’analisi e l’attivazione di dati e informazioni sui clienti.

## Applicazioni

* Adobe Experience Platform Attivazione

## Architettura

<img src="assets/enterprise_destination_activation.svg" alt="Architettura di riferimento per lo scenario di attivazione Enterprise" style="border:1px solid #4a4a4a" />


## Guardrail

Fai riferimento alle protezioni come descritto nella pagina Panoramica sull&#39;attivazione del pubblico e del profilo - [LINK](overview.md)

## Fasi di implementazione

1. Creare schemi per i dati da acquisire.
1. Crea set di dati per i dati da acquisire.
1. Configurare correttamente le identità e i relativi namespace nello schema, affinché i dati acquisiti possano essere uniti in un profilo unificato.
1. Abilita gli schemi e i set di dati per l’elaborazione dei profili.
1. Configura le origini per l’acquisizione dei dati.
1. Segmenti di authoring in Experience Platform, da valutare in batch o in streaming. Il sistema determina automaticamente se un segmento deve essere valutato in batch o in streaming.
1. Configurare le destinazioni per condividere gli attributi del profilo e delle appartenenze al pubblico con le destinazioni desiderate.

## Documentazione correlata

* [Documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=it)
* [Panoramica delle destinazioni di archiviazione cloud](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [Destinazione HTTP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [Descrizione del prodotto Real-time Customer Data Platform](https://helpx.adobe.com/it/legal/product-descriptions/real-time-customer-data-platform.html)
* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)
* [Documentazione sulla segmentazione](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it)

## Video e tutorial correlati

* [Panoramica di Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=it)
* [[!UICONTROL Demo di Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=it)
* [Creare segmenti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=it)
