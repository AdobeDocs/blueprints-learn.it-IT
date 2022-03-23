---
title: Blueprint per attivazione del pubblico con dati anonimi
description: Scopri come rivolgerti a un pubblico specifico su canali web e pubblicitari sulla base di dati anonimi e comportamentali dei clienti. Questa funzionalità consente di creare customer experience personalizzate e coerenti in tempo reale su tutti i dispositivi.
landing-page-description: Scopri come rivolgerti a un pubblico specifico su canali web e pubblicitari sulla base di dati anonimi e comportamentali dei clienti.
solution: Experience Platform, Audience Manager
kt: 7211
thumbnail: null
exl-id: f17599f1-2e75-4cbe-841a-9fd1dae71ada
source-git-commit: f46c09a88cf2b49c816ab27c5daef20c01e99b09
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 40%

---

# Blueprint per attivazione del pubblico con dati anonimi

L&#39;attivazione del pubblico anonimo è la capacità di indirizzare e personalizzare il pubblico attraverso canali web, mobili e pubblicitari basati su dispositivi e dati comportamentali anonimi.

## Casi di utilizzo

* Esegui il targeting e la personalizzazione anonimi del pubblico digitale sul sito web, sull’app mobile o sui canali pubblicitari supportati.
* Ottimizza le esperienze di pagina di destinazione e pre-autenticazione in base a dispositivi e caratteristiche comportamentali noti.
* Sfrutta la rete dati di terze parti di Audience Manager per perfezionare ed espandere ulteriormente il pubblico per il targeting.


## Applicazioni

Sia Audience Manager che Real-time Customer Data Platform possono essere utilizzati per alimentare l&#39;Audience Activation anonimo per le destinazioni onsite e pubblicitarie. Real-time Customer Data Platform supporta solo un sottoinsieme di destinazioni pubblicitarie con identificatori di dispositivo anonimi catalogati in [documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/overview.html?lang=en).

Microsoft Bing, Google DV360 e TradeDesk sono le principali destinazioni pubblicitarie Real-time Customer Data Platform supportate per il targeting basato su dispositivi anonimi. Oltre a questi, Real-time Customer Data Platform supporta numerose destinazioni basate su clienti note catalogate in [documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/overview.html?lang=en) e come descritto nella [blueprint di attivazione dei clienti noto](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).

## Architettura

<img src="assets/anonymous_activation.svg" alt="Architettura di riferimento per il blueprint Attivazione del pubblico con dati anonimi" style="width:80%; border:1px solid #4a4a4a" />

## Fasi di implementazione

<!-- These steps should link to help. -->

1. [Implementare Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=it#implementation-integration-guides).
1. Raccogliere i dati per Audience Manager.
1. Configurare i segnali e le caratteristiche da utilizzare nelle definizioni dei segmenti.
1. Creare i segmenti in Audience Manager.
1. Configurare le destinazioni in Audience Manager per condividere i tipi di pubblico.

Per le fasi di implementazione di Real-time Customer Data Platform, consulta [blueprint di attivazione dei clienti noto](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).

## Documentazione correlata

* [Audience Manager](https://experienceleague.adobe.com/docs/audience-manager.html?lang=it)
* [Experience Cloud [!UICONTROL Audiences]](https://experienceleague.adobe.com/docs/core-services/interface/audiences/audience-library.html?lang=it)
* [Integrare Audience Manager con Target](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/aam-target-integration.html?lang=it)
* [Condivisione dei segmenti Adobe Analytics tramite Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=it)
* [Blueprint di attivazione del cliente noto](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).
* [Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html)
