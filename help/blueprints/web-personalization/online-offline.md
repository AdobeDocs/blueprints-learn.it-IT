---
title: Blueprint di personalizzazione web online/offline
description: Sincronizza la personalizzazione web con la posta elettronica e altre personalizzazioni di canali per utenti noti e anonimi.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
translation-type: tm+mt
source-git-commit: 2f35195b875d85033993f31c8cef0f85a7f6cccc
workflow-type: tm+mt
source-wordcount: '1091'
ht-degree: 48%

---

# Blueprint Web/personalizzazione mobile online/offline

Sincronizza la personalizzazione web con la posta elettronica e altre personalizzazioni di canali per utenti noti e anonimi.

## Casi di utilizzo

* Ottimizzazione della pagina di destinazione
* Targeting dei profili comportamentali e offline
* Personalizzazione basata su precedenti visualizzazioni di prodotti/contenuti, affinità di prodotti/contenuti, attributi ambientali, dati del pubblico di terze parti e dati demografici, nonché informazioni approfondite offline come dati da transazioni, fedeltà e sistema di gestione delle relazioni con i clienti, e dati modellati

## Applicazioni

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (opzionale): consente di aggiungere dati sul pubblico di terze parti, grafici dei dispositivi basati su co-op, nonché di far emergere i segmenti di Platform in Adobe Analytics e viceversa.
* Adobe Analytics (opzionale): aggiunge la possibilità di creare segmenti basati su dati comportamentali cronologici e sulla segmentazione granulare dei dati di Adobe Analytics

## Architettura

<img src="assets/onoff.svg" alt="Architettura di riferimento per la blueprint di personalizzazione web online/offline" style="border:1px solid #4a4a4a" />

## Guardrail

### Guardrail per la valutazione e l’attivazione dei segmenti

| Tipo di segmentazione | Frequenza | Throughput | Latenza (Valutazione segmento) | Latenza (attivazione segmento) |
|-|-|-|-|-|-|
| Segmentazione Edge | La segmentazione di Edge è attualmente in versione beta e consente di valutare la segmentazione in tempo reale valida su Experience Platform Edge Network per le decisioni in tempo reale e sulla stessa pagina tramite Adobe Target e Adobe Journey Optimizer. |  | ~100 ms | Disponibile immediatamente per la personalizzazione in Adobe Target, per la ricerca di profili nel profilo Edge e per l’attivazione tramite destinazioni basate su cookie. |
| Segmentazione streaming | Ogni volta che un nuovo evento di streaming o un nuovo record viene acquisito nel profilo del cliente in tempo reale e la definizione del segmento è un segmento di streaming valido. <br>Consulta la  [documentazione sulla ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it) segmentazione per informazioni sui criteri dei segmenti in streaming | Fino a 1500 eventi al secondo.  | ~ p95 &lt;5min | Una volta realizzate queste realizzazioni, queste vengono condivise con Audience Manager e il servizio di condivisione del pubblico in pochi minuti e sono disponibili per la personalizzazione della pagina stessa/successiva in Adobe Target. |
| Segmentazione incrementale | Una volta all’ora per i nuovi dati che sono stati acquisiti nel profilo del cliente in tempo reale dall’ultima valutazione del segmento incrementale o batch. |  |  | Una volta realizzate queste appartenenze, queste vengono condivise con Audience Manager e il servizio di condivisione del pubblico in pochi minuti e sono disponibili per la personalizzazione della pagina stessa/successiva in Adobe Target. |
| Segmentazione in batch | Una volta al giorno in base a una pianificazione prestabilita del sistema impostata o ad hoc avviato manualmente tramite API. |  | Circa un&#39;ora per lavoro per un massimo di 10 TB di dimensioni dell&#39;archivio profili, 2 ore per lavoro per 10 TB a 100 TB di dimensioni dell&#39;archivio profili. Le prestazioni del processo del segmento batch dipendono dal numero di profili, dalle dimensioni dei profili e dal numero di segmenti valutati. | Una volta realizzate queste appartenenze, queste vengono condivise con Audience Manager e il servizio di condivisione del pubblico in pochi minuti e sono disponibili per la personalizzazione della pagina stessa/successiva in Adobe Target. |

### Guardrail per la condivisione del pubblico tra più applicazioni


| Pattern di integrazione di Audience Sharing | Dettaglio | Frequenza | Throughput | Latenza (Valutazione segmento) | Latenza (attivazione segmento) |
|-|-|-|-|-|-|-|
| Audience Manager di Real-time Customer Data Platform |  | In base al tipo di segmentazione - vedi la tabella delle protezioni di segmentazione riportata sopra. | In base al tipo di segmentazione - vedi la tabella delle protezioni di segmentazione riportata sopra. | In base al tipo di segmentazione - vedi la tabella delle protezioni di segmentazione riportata sopra. | Entro pochi minuti dal completamento della valutazione del segmento.<br>La sincronizzazione della configurazione iniziale del pubblico tra Real-time Customer Data Platform e Audience Manager richiede circa 4 ore.<br>Tutte le iscrizioni al pubblico realizzate durante il periodo di 4 ore verranno scritte in Audience Manager sul successivo processo di segmentazione del batch come appartenenze al pubblico &quot;esistenti&quot;. |
| Adobe Analytics all’Audience Manager | Per impostazione predefinita è possibile condividere un massimo di 75 tipi di pubblico per ogni suite di rapporti di Adobe Analytics. Se viene utilizzata una licenza di Audience Manager, non vi è alcun limite al numero di tipi di pubblico che possono essere condivisi tra Adobe Analytics e Adobe Target o Adobe Audience Manager e Adobe Target. |  |  |  |  |
| Adobe Analytics alla piattaforma dati cliente in tempo reale | Attualmente non disponibile. |  |  |  |  |

## Modelli di implementazione

Il modello di personalizzazione web/mobile può essere implementato tramite i seguenti approcci come descritto di seguito.

1. Utilizzo di [!UICONTROL Platform Web SDK] o [!UICONTROL Platform Mobile SDK] e [!UICONTROL Edge Network].
1. Utilizzo di SDK tradizionali specifici per le applicazioni (ad esempio, AppMeasurement.js)

### 1. Piattaforma SDK per web/dispositivi mobili e approccio Edge

<img src="assets/websdkflow.svg" alt="Architettura di riferimento per l’approccio [!UICONTROL Platform Web SDK] o [!UICONTROL Platform Mobile SDK] e [!UICONTROL Edge Network]" style="border:1px solid #4a4a4a" />

### 2. Approccio SDK specifico per l’applicazione

<img src="assets/appsdkflow.png" alt="Architettura di riferimento per l’approccio con SDK specifico per applicazione" style="border:1px solid #4a4a4a" />

## Prerequisiti di implementazione

| Applicazione/Servizio | Libreria necessaria | Note |
|---|---|---|
| Adobe Target | [!UICONTROL Platform Web SDK]*, at.js 0.9.1+ o mbox.js 61+ | at.js è da preferire in quanto mbox.js non viene più sviluppato. |
| Adobe Audience Manager (opzionale) | [!UICONTROL SDK] Web per piattaforma* o dil.js 5.0+ |  |
| Adobe Analytics (opzionale) | [!UICONTROL SDK per web di Platform]* o AppMeasurement.js 1.6.4+ | Il tracciamento di Adobe Analytics deve utilizzare Regional Data Collection (RDC). |
| Servizio Experience Cloud ID | [!UICONTROL SDK] per web di Platform* o VisitorAPI.js 2.0+ | (Consigliato) Utilizza Experience Platform Launch per implementare il servizio ID, in modo che l’ID venga impostato prima di qualsiasi chiamata |
| Experience Platform Mobile SDK (opzionale) | 4.11 o superiore per iOS e Android™ |  |
| Experience Platform Web SDK | 1.0, la versione attuale di Experience Platform SDK presenta [diversi casi di utilizzo non ancora supportati per le applicazioni Experience Cloud](https://github.com/adobe/alloy/projects/5) |  |


## Fasi di implementazione

1. [Implementare Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=it) per le applicazioni web o mobili
1. [Implementare Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=it) (opzionale)
1. [Implementare Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=it) (opzionale)
1. [[!UICONTROL Implementare Experience Platform e Real-time Customer Profile]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=it)
1. Implementare [Servizio Experience Cloud Identity](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=it) o [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=it)
   >[!NOTE]
   >
   >Per consentire la condivisione del pubblico tra diverse applicazioni, ogni applicazione deve utilizzare l’ID del servizio Experience Cloud ID e far parte della stessa organizzazione Experience Cloud.
1. [Richiedere il provisioning per la condivisione del pubblico tra Experience Platform e Adobe Target (tipi di pubblico condivisi)](https://www.adobe.com/go/audiences)

## Documentazione correlata

* [Condivisione dei segmenti Experience Platform con Audience Manager e altre soluzioni Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=it)
* [Panoramica sulla segmentazione in Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=it)
* [Segmentazione in streaming](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Panoramica di Experience Platform Segment Builder](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html?lang=it)
* [Connettore origini di Audience Manager](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=it)
* [Condivisione dei segmenti di Adobe Analytics tramite Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=it)
* [Documentazione di Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Documentazione del servizio Experience Cloud ID](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=it)
* [Documentazione di Experience Platform Launch](https://experienceleague.adobe.com/docs/launch/using/home.html?lang=it)

## Articoli di blog correlati

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
