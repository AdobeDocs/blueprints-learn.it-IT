---
title: Blueprint Audience Activation online/offline
description: Audience Activation con dati online/offline
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 76fe52d8e83e075f9e7ce6e8596880181b01a7fd
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 79%

---

# Blueprint Audience Activation online/offline

Per il targeting e la personalizzazione online, utilizza attributi ed eventi offline come dati da ordini, transazioni, sistema di gestione delle relazioni con i clienti o fedeltà, insieme a dati sul comportamento online.

Attiva specifici tipi di pubblico in base a destinazioni note basate sul profilo, come provider di posta elettronica, social network e destinazioni pubblicitarie.

## Casi di utilizzo

* Targeting per tipi di pubblico noti su destinazioni social e pubblicitarie.
* Personalizzazione online con attributi online e offline.
* Attivazione del pubblico su canali noti, come e-mail e SMS.

## Applicazioni

* Adobe Experience Platform
* [!UICONTROL Real-time Customer Data Platform]

## Architettura

<img src="assets/online_offline_activation.svg" alt="Architettura di riferimento per la blueprint di Audience Activation online/offline" style="border:1px solid #4a4a4a" />

## Guardrail

Fai riferimento alle protezioni come descritto nella pagina Panoramica sull&#39;attivazione del pubblico e del profilo - [LINK](overview.md)

## Fasi di implementazione

1. Configurare schemi e set di dati in Experience Platform.
1. Configurare correttamente le identità e i relativi namespace nello schema, affinché i dati acquisiti possano essere uniti in un profilo unificato.
1. Attivare lo schema e i set di dati per il profilo.
1. Acquisire i dati in Platform.
1. Effettuare il provisioning della condivisione di segmenti [!UICONTROL Real-time Customer Data Platform] tra Experience Platform e Audience Manager per i tipi di pubblico definiti in Experience Platform da condividere con Audience Manager.
1. Creare segmenti in Experience Platform, da valutare in batch o in streaming. Il sistema determina automaticamente se un segmento deve essere valutato in batch o in streaming.
1. Configurare le destinazioni per condividere gli attributi del profilo e delle appartenenze al pubblico con le destinazioni desiderate.

## Considerazioni sull’implementazione

* Per condividere i dati del profilo con le destinazioni, è necessario includere il valore di identità specifico utilizzato dalla destinazione nel payload. Qualsiasi identità necessaria per una destinazione di destinazione deve essere assimilata in Platform e configurata come identità per il [!UICONTROL Profilo cliente in tempo reale].

* Per gli scenari di attivazione in cui il pubblico viene condiviso tra Experience Platform e Audience Manager, tutte le identità incluse in [!UICONTROL Real-time Customer Profile] vengono condivise con Audience Manager. Il pubblico di Experience Platform può essere condiviso tramite le destinazioni di Audience Manager se le identità di destinazione richieste sono incluse in [!UICONTROL Real-time Customer Profile], oppure nel caso in cui le identità in [!UICONTROL Real-time Customer Profile] possono essere correlate alle identità di destinazione richieste collegate in Audience Manager.

## Documentazione correlata

* [Descrizione del prodotto Real-time Customer Data Platform](https://helpx.adobe.com/it/legal/product-descriptions/real-time-customer-data-platform.html)
* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)
* [Documentazione sulla segmentazione](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it)
* [Documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=it)

## Video e tutorial correlati

* [Panoramica di Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=it)
* [[!UICONTROL Demo di Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=it)
* [Creare segmenti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=it)
