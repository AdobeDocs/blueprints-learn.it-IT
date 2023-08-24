---
title: Blueprint per attivazione in base a pubblico e profili con destinazioni basate su file e streaming verso soluzioni aziendali
description: Attivazione in base a pubblico e profili con destinazioni verso soluzioni aziendali
solution: Real-Time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5
source-git-commit: ae7347be5095ca4a7f99f9371dd94d87097112b0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 100%

---

# Blueprint per attivazione in base a pubblico e profili con destinazioni basate su file e streaming verso soluzioni aziendali

Condividi eventi e modifiche di profili e pubblico in streaming o in batch da [!UICONTROL Real-time Customer Data Platform] con archivi dati e applicazioni aziendali. Gli eventi di profilo e pubblico possono essere utilizzati per avviare un’azione di vendita o supporto al cliente, ad esempio per dare seguito all’abbandono di un processo di iscrizione o di registrazione a un webinar, oppure per aggiornare le applicazioni aziendali con gli attributi e le informazioni più recenti del cliente da [!UICONTROL Real-time Customer Data Platform].

## Casi di utilizzo

* Attivazione di profili e pubblico per destinazioni di archiviazione cloud o di streaming per il tracciamento, l’archiviazione, l’analisi e l’attivazione di dati e informazioni sui clienti.

## Applicazioni

* Adobe Experience Platform  Activation

## Architettura

<img src="assets/known_activation.svg" alt="Architettura di riferimento per lo scenario di attivazione aziendale" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />


## Guardrail

[Fai riferimento ai guardrail come indicato nella panoramica Attivazione in base a pubblico e profili.](overview.md)

## Fasi di implementazione

1. [Creare schemi](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=it) per i dati da acquisire.
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) per i dati da acquisire.
1. [Configurare correttamente le identità e i relativi spazi dei nomi](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it) nello schema, affinché i dati acquisiti possano essere uniti in un profilo unificato.
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=it).
1. [Inserire i dati](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=it) in Experience Platform.
1. [Abilitare la condivisione dei segmenti [!UICONTROL Real-time Customer Data Platform]](https://www.adobe.com/go/audiences) tra Experience Platform e Audience Manager per i tipi di pubblico definiti in Experience Platform da condividere con Audience Manager.
1. [Creare segmenti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=it) in Experience Platform. Il sistema determina automaticamente se un segmento deve essere valutato in batch o in streaming.
1. [Configurare le destinazioni](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html?lang=it) per condividere gli attributi del profilo e delle appartenenze al pubblico con le destinazioni desiderate.

## Documentazione correlata

* [Documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=it)
* [Panoramica delle destinazioni di archiviazione cloud](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=it#catalog)
* [Destinazione HTTP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=it#overview)
* Descrizione del prodotto [[!UICONTROL Real-time Customer Data Platform]](https://helpx.adobe.com/it/legal/product-descriptions/real-time-customer-data-platform.html)
* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)
* [Documentazione sulla segmentazione](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it)

## Video e tutorial correlati

* Panoramica di [[!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=it)
* [Demo di [!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=it)
* [Creare segmenti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=it)
