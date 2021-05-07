---
title: Blueprint per attivazione del pubblico con dati online/offline
description: Attivazione del pubblico con dati online/offline.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 2fc1adc04a9ca2184c88970d5ba0785957327f68
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 74%

---

# Blueprint per attivazione del pubblico con dati online/offline

Per il targeting e la personalizzazione online, utilizza attributi ed eventi offline come dati da ordini, transazioni, sistema di gestione delle relazioni con i clienti o fedeltà, insieme a dati sul comportamento online.

Attiva specifici tipi di pubblico in base a destinazioni note basate sul profilo, come provider di posta elettronica, social network e destinazioni pubblicitarie.

La blueprint dell&#39;Audience Activation online/offline è allineata strettamente con la [attivazione del pubblico e del profilo con la blueprint delle applicazioni Experience Cloud](platform-and-applications.md). Ulteriori dettagli sono forniti in [Attivazione pubblico e profilo con Experience Cloud Applications Blueprint](platform-and-applications.md)   specifiche per le integrazioni tra le applicazioni Experience Platform e Experience Cloud.

## Casi di utilizzo

* Targeting per tipi di pubblico noti su destinazioni social e pubblicitarie.
* Personalizzazione online con attributi online e offline.
* Attivazione del pubblico su canali noti, come e-mail e SMS.

## Applicazioni

* Adobe Experience Platform
* [!UICONTROL Real-time Customer Data Platform]

## Architettura

### Audience Activation online/offline con destinazioni

<img src="assets/online_offline_activation.svg" alt="Architettura di riferimento per il blueprint Attivazione del pubblico con dati online/offline" style="border:1px solid #4a4a4a" />
<br>

### Audience Activation online/offline con applicazioni Experience Cloud

<img src="assets/activation+apps.svg" alt="Architettura di riferimento per la blueprint di Audience Activation online/offline con applicazioni Experience Cloud" style="border:1px solid #4a4a4a" />

## Guardrail

[Consulta le protezioni descritte nella pagina Panoramica sull’attivazione del pubblico e del profilo .](overview.md)

## Fasi di implementazione

1. [Creare schemi per i dati da acquisire.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html)
1. [Creare set di dati per i dati da acquisire.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html)
1. [Configurare correttamente le identità e i relativi namespace nello schema, affinché i dati acquisiti possano essere uniti in un profilo unificato.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)
1. [Abilita gli schemi e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Inserire i dati in Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)
1. [Abilitare la condivisione dei segmenti [!UICONTROL Real-time Customer Data Platform] tra Experience Platform e Audience Manager per i tipi di pubblico definiti in Experience Platform da condividere con Audience Manager.](https://www.adobe.com/go/audiences)
1. [Crea ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=it) segmenti in Experience Platform. Il sistema determina automaticamente se un segmento deve essere valutato in batch o in streaming.
1. [Configurare le destinazioni per condividere gli attributi del profilo e delle appartenenze al pubblico con le destinazioni desiderate.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html)

## Considerazioni sull’implementazione

* Per condividere i dati del profilo con le destinazioni, è necessario includere il valore di identità specifico utilizzato dalla destinazione nel payload. Tutte le identità necessarie per una destinazione target devono essere inserite in Platform e configurate come identità per [!UICONTROL Real-time Customer Profile].

* Per gli scenari di attivazione in cui il pubblico viene condiviso tra Experience Platform e Audience Manager, tutte le identità incluse in [!UICONTROL Real-time Customer Profile] vengono condivise con Audience Manager. Il pubblico di Experience Platform può essere condiviso tramite le destinazioni di Audience Manager se le identità di destinazione richieste sono incluse in [!UICONTROL Real-time Customer Profile], oppure nel caso in cui le identità in [!UICONTROL Real-time Customer Profile] possono essere correlate alle identità di destinazione richieste collegate in Audience Manager.

## Documentazione correlata

* Descrizione del prodotto [[!UICONTROL Real-time Customer Data Platform]](https://helpx.adobe.com/it/legal/product-descriptions/real-time-customer-data-platform.html)
* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)
* [Documentazione sulla segmentazione](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it)
* [Documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=it)

## Video e tutorial correlati

* Panoramica di [[!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=it)
* [Demo di [!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=it)
* [Creare segmenti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
