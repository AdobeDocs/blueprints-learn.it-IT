---
title: Personalizzazione web e mobile con dati online e offline
description: Sincronizza la personalizzazione web con l’e-mail e altre personalizzazioni di canali per utenti noti e anonimi.
landing-page-description: Sincronizza la personalizzazione web con l’e-mail e altre personalizzazioni di canali per utenti noti e anonimi.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 070c78ee3cf32e70af90c6cbcdd77d5258a32fb7
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 93%

---

# Personalizzazione web e mobile con dati online e offline

Sincronizza la personalizzazione web con l’e-mail e altre personalizzazioni di canali per utenti noti e anonimi.

## Casi di utilizzo

* Ottimizzazione della pagina di destinazione
* Targeting dei profili comportamentali e offline
* Personalizzazione basata su precedenti visualizzazioni di prodotti/contenuti, affinità di prodotti/contenuti, attributi ambientali, dati del pubblico di terze parti e dati demografici, nonché informazioni approfondite offline come dati da transazioni, fedeltà e sistema di gestione delle relazioni con i clienti, e dati modellati
* Utilizza Adobe Target per la condivisione e il targeting dei tipi di pubblico definiti in Real-time Customer Data Platform su siti web e app mobili.

## Applicazioni

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (opzionale): consente di aggiungere dati sul pubblico di terze parti, grafici dei dispositivi basati su co-op, nonché di far emergere i segmenti di Platform in Adobe Analytics e viceversa.
* Adobe Analytics (opzionale): aggiunge la possibilità di creare segmenti basati su dati comportamentali cronologici e sulla segmentazione granulare dei dati di Adobe Analytics

## Pattern di integrazione

<table class="tg" style="undefined;table-layout: fixed; width: 790px">
<colgroup>
<col style="width: 20px">
<col style="width: 276px">
<col style="width: 229px">
<col style="width: 265px">
</colgroup>
<thead>
  <tr>
    <th class="tg-y6fn">#</th>
    <th class="tg-f7v4">Pattern di integrazione</th>
    <th class="tg-y6fn">Funzionalità</th>
    <th class="tg-f7v4">Prerequisiti</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">1</td>
    <td class="tg-73oq"><span style="font-weight:400;font-style:normal">Condivisione del pubblico in modalità batch e in streaming da RTCDP a Target e Audience Manager, tramite il servizio di condivisione del pubblico</span></td>
    <td class="tg-0lax"><span style="font-weight:400;font-style:normal">- Condividi i tipi di pubblico in modalità batch e streaming da RTCDP a Target e Audience Manager tramite il servizio di condivisione del pubblico I tipi di pubblico valutati in tempo reale richiedono Web SDK e la valutazione del pubblico in tempo reale, come descritto nel pattern di integrazione 3.</span></td>
    <td class="tg-73oq">- È necessario il provisioning della proiezione del pubblico tramite il servizio di condivisione del pubblico.<br>- L’integrazione con Target richiede la stessa organizzazione IMS usata per l’istanza di Experience Platform.<br>- L’identità deve essere risolta in ECID affinché possa essere condivisa con la rete Edge e utilizzata da Target. AAM confronta le identità con un proprio elenco di identità approvate.<br>- Questa integrazione non richiede l’implementazione di Web SDK.</td>
  </tr>
  <tr>
    <td class="tg-0lax">2</td>
    <td class="tg-73oq">Condivisione del pubblico in modalità batch e in streaming da RTCDP a Target tramite l’approccio Edge</td>
    <td class="tg-0lax">- Condividi i tipi di pubblico in modalità batch e streaming da RTCDP a Target tramite la rete Edge. I tipi di pubblico valutati in tempo reale richiedono Web SDK e la valutazione del pubblico in tempo reale, come descritto nel pattern di integrazione 3.</td>
    <td class="tg-73oq"><span style="text-decoration:none">- Attualmente in versione beta</span><br>- La destinazione Target deve essere configurata nelle destinazioni RTCDP.<br>- L’integrazione con Target richiede la stessa organizzazione IMS usata per l’istanza di Experience Platform.<br>Non richiede Web SDK. Supporta Web SDK e AT.js. <br>- Se si utilizza AT.js, è supportata solo la ricerca dei profili rispetto all’ECID. <br>- Per le ricerche tramite ID da spazi dei nomi personalizzati nella rete Edge, è necessaria l’implementazione del Web SDK e ogni identità deve essere impostata come identità nella mappa delle identità.</td>
  </tr>
  <tr>
    <td class="tg-0lax">3</td>
    <td class="tg-73oq">Condivisione della valutazione dei segmenti in tempo reale da RTCDP sulla rete Edge a Target tramite la rete Edge mediante Web SDK.</td>
    <td class="tg-0lax">- Valuta i tipi di pubblico in tempo reale sul server Edge per la personalizzazione della pagina corrente o successiva.</td>
    <td class="tg-73oq"><span style="text-decoration:none">- Attualmente in versione beta</span><br>- La destinazione Target deve essere configurata nelle destinazioni RTCDP.<br>- L’integrazione con Target richiede la stessa organizzazione IMS usata per l’istanza di Experience Platform.<br>- È necessario implementare Web SDK.<br>- Supportato anche tramite API.</td>
  </tr>
</tbody>
</table>


## Architettura

Architettura della panoramica

<img src="assets/RTCDP+Target.png" alt="Architettura di riferimento per il blueprint per la personalizzazione web con dati online/offline" style="width:80%; border:1px solid #4a4a4a" />

Architettura del flusso di processo

<img src="assets/RTCDP+Target_flow.png" alt="Architettura di riferimento per il blueprint per la personalizzazione web con dati online/offline" style="width:80%; border:1px solid #4a4a4a" />

Architettura dettagliata

<img src="assets/personalization_with_apps.png" alt="Architettura di riferimento per il blueprint per la personalizzazione web con dati online/offline" style="width:80%; border:1px solid #4a4a4a"/>

## Guardrail

[Fai riferimento ai guardrail nella panoramica dei blueprint per personalizzazione web/mobile.](overview.md)

## Modelli di implementazione

Il blueprint per la personalizzazione web/mobile può essere implementato con i metodi descritti di seguito.

1. Mediante [!UICONTROL Platform Web SDK] o [!UICONTROL Platform Mobile SDK] e [!UICONTROL rete Edge].
1. Mediante SDK tradizionali per specifiche applicazioni (ad esempio, AppMeasurement.js)

### 1. Mediante Platform Web/Mobile SDK e rete Edge

[Consulta il blueprint per l’SDK Web/Mobile di Experience Platform](../data-ingestion/websdk.md)

### 2. Mediante SDK per specifiche applicazioni

<img src="assets/app_sdk_flow.png" alt="Architettura di riferimento per l’approccio con SDK per specifiche applicazioni" style="width:80%; border:1px solid #4a4a4a" />

## Prerequisiti per l’implementazione

Prerequisiti per l’identità

* La condivisione di tipi di pubblico da Adobe Experience Platform ad Adobe Target richiede l’utilizzo di ECID come identità.
* Inoltre, è possibile utilizzare identità alternative per condividere i tipi di pubblico di Experience Platform con Adobe Target tramite Audience Manager. Experience Platform attiva i tipi di pubblico in Audience Manager tramite i seguenti spazi dei nomi supportati: IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Tieni presente che Audience Manager e Target risolvono l’appartenenza a un pubblico tramite l’identità ECID. Pertanto l’ECID è comunque necessario per la condivisione finale del pubblico in Adobe Target.

| Applicazione/Servizio | Libreria necessaria | Note |
|---|---|---|
| Adobe Target | [!UICONTROL Platform Web SDK]*, at.js 0.9.1+ o mbox.js 61+ | at.js è da preferire in quanto mbox.js non viene più sviluppato. |
| Adobe Audience Manager (opzionale) | [!UICONTROL Platform Web SDK]* o dil.js 5.0+ |  |
| Adobe Analytics (opzionale) | [!UICONTROL Platform Web SDK]* o AppMeasurement.js 1.6.4+ | Il tracciamento di Adobe Analytics deve utilizzare Regional Data Collection (RDC). |
| Servizio Experience Cloud ID | [!UICONTROL Platform Web SDK]* o VisitorAPI.js 2.0+ | (Consigliato) Utilizza Experience Platform Launch per implementare il servizio ID, in modo che l’ID venga impostato prima di qualsiasi chiamata |
| Experience Platform Mobile SDK (opzionale) | 4.11 o superiore per iOS e Android™ |  |
| Experience Platform Web SDK | 1.0, la versione attuale di Experience Platform SDK presenta [diversi casi di utilizzo non ancora supportati per le applicazioni Experience Cloud](https://github.com/adobe/alloy/projects/5) |  |




## Fasi di implementazione

1. [Implementare Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=it) per le applicazioni web o mobili
1. [Implementare Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=it) (opzionale)
1. [Implementare Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=it) (opzionale)
1. [Implementare Experience Platform e [!UICONTROL Real-time Customer Profile]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=it)
1. Implementare il [servizio Experience Cloud Identity](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=it) o [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=it)
1. [Abilitare Adobe Target come destinazione in Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en) o per l’approccio alla condivisione del pubblico [Richiedi il provisioning per la condivisione del pubblico tra Experience Platform e Adobe Target (pubblico condiviso)](https://www.adobe.com/go/audiences) per condividere tipi di pubblico da Experience Platform a Target.
   >[!NOTE]
   >
   >Quando si utilizza il servizio di condivisione del pubblico tra RTCDP e Adobe Target, i tipi di pubblico devono essere condivisi tramite Experience Cloud ID e far parte della stessa organizzazione Experience Cloud. Per supportare identità diverse da ECID è necessario usare Web SDK e Experience Edge Network.


## Documentazione correlata

* [Condivisione dei segmenti Experience Platform con Audience Manager e altre soluzioni Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=it)
* [Panoramica sulla segmentazione in Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=it)
* [Segmentazione in streaming](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it)
* [Connessione Adobe Target per Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en)
* [Panoramica di Experience Platform Segment Builder](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html?lang=it)
* [Connettore origini di Audience Manager](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=it)
* [Condivisione dei segmenti di Adobe Analytics tramite Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=it)
* [Documentazione di Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Documentazione del servizio Experience Cloud ID](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=it)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it)

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
