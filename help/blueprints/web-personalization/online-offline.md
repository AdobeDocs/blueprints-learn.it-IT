---
title: Blueprint di personalizzazione web online/offline
description: Sincronizza la personalizzazione web con le e-mail e altre personalizzazioni del canale note e anonime.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
translation-type: tm+mt
source-git-commit: cbc9c48041d00c45fc75d3bb65bd865f1f7ecc9c
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 0%

---

# Blueprint Web/personalizzazione mobile online/offline

Sincronizza la personalizzazione web con le e-mail e altre personalizzazioni del canale note e anonime.

## Casi d&#39;uso

* Ottimizzazione della pagina di destinazione
* Targeting comportamentale e offline del profilo
* Personalizzazione basata su precedenti visualizzazioni di prodotto/contenuto, affinità prodotto/contenuto, attributi ambientali, dati di pubblico di terze parti e dati demografici, oltre a informazioni offline come transazioni, dati di gestione delle relazioni con i clienti e fedeltà e informazioni modellate

## Applicazioni

* [!UICONTROL Piattaforma dati cliente in tempo reale]
* Adobe Target
* Adobe Audience Manager (facoltativo): Aggiunge dati di pubblico di terze parti, grafici dei dispositivi basati su co-op, la capacità di far superficie ai segmenti di Platform in Adobe Analytics e la capacità di far superficie ai segmenti Adobe Analytics in Platform
* Adobe Analytics (facoltativo): Aggiunge la possibilità di creare segmenti in base ai dati comportamentali storici e alla segmentazione a grana fine dai dati di Adobe Analytics

## Architettura

<img src="assets/onoff.svg" alt="Architettura di riferimento per la blueprint di personalizzazione web online/offline" style="border:1px solid #4a4a4a" />

## Guardrail

* I segmenti condivisi da Experience Platform a Audience Manager vengono condivisi in pochi minuti dalla realizzazione del segmento, sia tramite il metodo di valutazione in streaming che in batch. Esiste una sincronizzazione iniziale della configurazione del segmento tra Experience Platform ed Audience Manager di circa 4 ore affinché le appartenenze al segmento di Experience Platform inizino a essere realizzate nei profili di Audience Manager. Una volta all’interno dei profili di Audience Manager, le appartenenze ai segmenti di Experience Platform sono disponibili per la personalizzazione della stessa pagina tramite Adobe Target.
* Tieni presente che per le realizzazioni di segmenti che si verificano all’interno della sincronizzazione della configurazione di segmenti di 4 ore tra Experience Platform e Audience Manager, queste realizzazioni di segmenti saranno realizzate in Audience Manager sul successivo processo di segmenti batch come segmenti &quot;esistenti&quot;.
* Condivisione in batch di segmenti dall’Experience Platform: una volta al giorno o avviata manualmente tramite API. Una volta realizzate queste appartenenze, queste vengono condivise in Audience Manager in pochi minuti e sono disponibili per la personalizzazione della pagina stessa/successiva in Target.
* La segmentazione in streaming viene realizzata entro circa 5 minuti. Una volta che queste realizzazioni dei segmenti si verificano, vengono condivisi in Audience Manager in pochi minuti e sono disponibili per la personalizzazione della pagina stessa/successiva in Target.
* Per impostazione predefinita, il servizio di condivisione dei segmenti consente di condividere un massimo di 75 tipi di pubblico per ciascuna suite di rapporti di Adobe Analytics. Se il cliente dispone di una licenza di Audience Manager, non vi è alcun limite al numero di tipi di pubblico che possono essere condivisi tra Adobe Analytics e Adobe Target o Audience Manager e Adobe Target.

## Modelli di implementazione

Il modello di personalizzazione web/mobile può essere implementato tramite i seguenti approcci come descritto di seguito.

1. Utilizzo di Platform Web SDK/Mobile SDK e Edge Network.
1. Utilizzo di SDK tradizionali specifici per le applicazioni (ad esempio, AppMeasurement.js)

### 1. Piattaforma SDK per web/dispositivi mobili e approccio Edge

<img src="assets/websdkflow.svg" alt="Architettura di riferimento per l’SDK per web Platform/Mobile e l’approccio di rete Edge" style="border:1px solid #4a4a4a" />

### 2. Approccio SDK specifico per l’applicazione

<img src="assets/appsdkflow.png" alt="Architettura di riferimento per l’approccio SDK specifico per l’applicazione" style="border:1px solid #4a4a4a" />

## Prerequisiti per l’implementazione

| Applicazione/Servizio | Libreria richiesta | Note |
|---|---|---|
| Adobe Target | Platform Web SDK*, at.js 0.9.1+ o mbox.js 61+ | at.js è da preferire in quanto mbox.js non viene più sviluppato. |
| Adobe Audience Manager (facoltativo) | Platform Web SDK* o dil.js 5.0+ |  |
| Adobe Analytics (facoltativo) | Platform Web SDK* o AppMeasurement.js 1.6.4+ | Il tracciamento di Adobe Analytics deve utilizzare la raccolta dati regionali (RDC). |
| Servizio Experience Cloud ID | Platform Web SDK* o VisitorAPI.js 2.0+ | (consigliato) Utilizza il Experience Platform Launch per distribuire il servizio ID in modo che l&#39;ID sia impostato prima di qualsiasi chiamata dell&#39;applicazione |
| Experience Platform Mobile SDK (facoltativo) | 4.11 o superiore per iOS e Android™ |  |
| Experience Platform Web SDK | 1.0, la versione corrente dell&#39;SDK Experience Platform ha [vari casi d&#39;uso non ancora supportati per le applicazioni Experience Cloud](https://github.com/adobe/alloy/projects/5) |  |


## Passaggi di implementazione

1. [Implementare ](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html) Target Adobe per le applicazioni web o mobili
1. [Implementare Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html)  (facoltativo)
1. [Implementare Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html)   (facoltativo)
1. [Implementare il profilo cliente in Experience Platform e in tempo  [!UICONTROL reale]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html)
1. Implementazione di [Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html) o [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
   >[!NOTE]
   >
   >Ogni applicazione deve utilizzare l&#39;ID Experience Cloud e far parte della stessa organizzazione Experience Cloud per consentire la condivisione del pubblico tra le applicazioni.
1. [Richiedi il provisioning per la condivisione del pubblico tra Experience Platform e Adobe Target (pubblico condiviso)](https://www.adobe.com/go/audiences)

## Documentazione correlata

* [Experience Platform di condivisione di segmenti con Audience Manager e altre soluzioni Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html)
* [Panoramica sulla segmentazione di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html)
* [Segmentazione streaming](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Panoramica di Experience Platform Segment Builder](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html)
* [Connettore sorgente Audience Manager](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html)
* [Condivisione dei segmenti di Adobe Analytics tramite Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)
* [Documentazione Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Documentazione del servizio ID di Experience Cloud](https://experienceleague.adobe.com/docs/id-service/using/home.html)
* [Documentazione del Experience Platform Launch](https://experienceleague.adobe.com/docs/launch/using/home.html)

## Post di blog correlati

* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Build an Optimal Online Experience: Enrich Unified Profile with Query Service]](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
* [[!DNL Integrating Adobe Experience Platform Decisioning Engine with AEM Websites]](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [[!DNL Adobe Experience Platform’s Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL How Adobe Experience Platform Can Help Customers Personalize Their Mobile Messaging in Real-Time with Journey Orchestration Service and a Mobile Messaging Vendor]](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
* [[!DNL Build an Optimal Online Experience: Enrich Unified Profile with Query Service]](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
