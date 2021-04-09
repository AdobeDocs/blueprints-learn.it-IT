---
title: Blueprint di personalizzazione web comportamentale
description: Personalizza in base al comportamento online e ai dati sul pubblico.
solution: Experience Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7085thumb-web-personalization-scenario1.jpg
exl-id: b9882c2c-cb45-4efa-a85c-8fe48f641a12
translation-type: tm+mt
source-git-commit: 087da6c5c5c6a6e9deee890d2ea02cf8591bdf15
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# Blueprint comportamentale per la personalizzazione web/mobile

Personalizza in base al comportamento online e ai dati sul pubblico.

## Casi d&#39;uso

* Ottimizzazione della pagina di destinazione
* Targeting comportamentale
* Personalizzazione basata su precedenti visualizzazioni di prodotto/contenuto, affinità prodotto/contenuto, attributi ambientali, dati di pubblico di terze parti e dati demografici

## Applicazioni

* Adobe Target
* Adobe Analytics (facoltativo)
* Adobe Audience Manager (opzionale)

## Architettura

<img src="assets/personalization.svg" alt="Architettura di riferimento per il Blueprint di personalizzazione web comportamentale" style="border:1px solid #4a4a4a" />


## Guardrail

Per impostazione predefinita, il servizio di condivisione dei segmenti consente di condividere un massimo di 75 tipi di pubblico per ciascuna suite di rapporti di Adobe Analytics. Se per la condivisione di tipi di pubblico viene utilizzato un Audience Manager, non vi è alcun limite al numero di tipi di pubblico che possono essere condivisi. 

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
| Adobe Analytics (facoltativo) | Platform Web SDK* o AppMeasurement.js 1.6.4+ |  |
| Servizio Experience Cloud Identity | Platform Web SDK* o VisitorAPI.js 2.0+ |  |
| Experience Platform Mobile SDK (facoltativo) | 4.11 o superiore per iOS e Android™ |  |
| Experience Platform Web SDK | 1.0, la versione corrente dell&#39;SDK Experience Platform ha [vari casi d&#39;uso non ancora supportati per le applicazioni Experience Cloud](https://github.com/adobe/alloy/projects/5) |  |

## Passaggi di implementazione

1. [Implementa ](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html) Target Adobe per le tue applicazioni web o mobili.

   Se utilizzi Audience Manager o Analytics:

1. [Implementare Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html)
1. [Implementare Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html)
1. [Implementazione del servizio Experience Cloud Identity](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html)

   >[!NOTE]
   >
   >Ogni applicazione deve utilizzare l&#39;ID Experience Cloud e far parte della stessa organizzazione Experience Cloud per consentire la condivisione del pubblico tra le applicazioni.

1. [Richiedi il provisioning per i servizi di condivisione delle persone e del pubblico (tipi di pubblico condivisi)](https://www.adobe.com/go/audiences)
1. Crea segmenti in [Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-build.html) o [Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/segments/segment-builder.html) e [configura tali tipi di pubblico per la condivisione nell&#39;Experience Cloud](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html) (se utilizzi Audience Manager o Adobe Analytics)
1. Una volta che i tipi di pubblico sono disponibili in Adobe Target, possono essere utilizzati per [eseguire il targeting delle esperienze con Adobe Target](https://experienceleague.adobe.com/docs/target/using/audiences/target.html)

## Documentazione correlata

* [Tipi di pubblico di Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/audiences/audience-library.html)
* [Integrare Audience Manager con Adobe Target](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/aam-target-integration.html)
* [Condivisione dei segmenti di Adobe Analytics tramite Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)


## Post di blog correlati

* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Integrating Adobe Experience Platform Decisioning Engine with AEM Websites]](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL How Adobe Experience Platform Can Help Customers Personalize Their Mobile Messaging in Real-Time with Journey Orchestration Service and a Mobile Messaging Vendor]](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
