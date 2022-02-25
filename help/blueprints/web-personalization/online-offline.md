---
title: Personalizzazione web e mobile con dati online e offline
description: Sincronizza la personalizzazione web con l’e-mail e altre personalizzazioni di canali per utenti noti e anonimi.
landing-page-description: Sincronizza la personalizzazione web con l’e-mail e altre personalizzazioni di canali per utenti noti e anonimi.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 8d01529c611b2dabeeb6b11a227e7c3a9f132774
workflow-type: tm+mt
source-wordcount: '1452'
ht-degree: 50%

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
* Adobe Audience Manager (facoltativo): Aggiunge dati di pubblico di terze parti, grafici dei dispositivi basati su co-op, la capacità di far emergere il pubblico di Real-time Customer Data Platform in Adobe Analytics e la capacità di far emergere il pubblico di Adobe Analytics in Real-time Customer Data Platform
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
<td class="tg-73oq">Valutazione dei segmenti in tempo reale sul server Edge condiviso da Real-time Customer Data Platform a Target</td>
    <td class="tg-0lax">- Valuta i tipi di pubblico in tempo reale sul server Edge per la personalizzazione della pagina corrente o successiva.<br>- Condivisione di tipi di pubblico in streaming e in batch da Real-time Customer Data Platform a Target tramite la rete Edge.</td>
    <td class="tg-73oq">- Il Datastream deve essere configurato in Experience Edge con l’estensione Target e Experience Platform abilitata, l’ID Datastream verrà fornito nella configurazione di destinazione di Target.<br>- La destinazione di destinazione deve essere configurata in Real-time Customer Data Platform Destinations.<br>- L’integrazione con Target richiede la stessa organizzazione IMS usata per l’istanza di Experience Platform.<br>- È necessario implementare Web SDK.<br>- L’SDK per dispositivi mobili e l’implementazione basata su API non sono attualmente disponibili</td> 
  </tr>
  <tr>
    <td class="tg-0lax">2</td>
    <td class="tg-73oq">Streaming e condivisione in batch dell'audience da Real-time Customer Data Platform a Target tramite l'approccio Edge</td>
    <td class="tg-0lax">- Condivisione di tipi di pubblico in streaming e in batch da Real-time Customer Data Platform a Target tramite la rete Edge. I tipi di pubblico valutati in tempo reale richiedono Web SDK e la valutazione del pubblico in tempo reale, come descritto nel pattern di integrazione 1.</td>
    <td class="tg-73oq">- Datastream deve essere configurato in Experience Edge, l’ID Datastream verrà fornito nella configurazione di destinazione di Target - anche se non è necessario implementare questo datastream per la personalizzazione o la condivisione di tipi di pubblico in streaming e batch in questo momento se si utilizza l’approccio di implementazione di AT.js, tuttavia deve essere configurato nella rete Edge.<br>- La destinazione di destinazione deve essere configurata in Real-time Customer Data Platform Destinations.<br>- L’integrazione con Target richiede la stessa organizzazione IMS usata per l’istanza di Experience Platform.<br>- WebSDK non è necessario per la condivisione di tipi di pubblico in streaming e batch a Target, anche se è necessario per abilitare la valutazione dei segmenti edge in tempo reale come descritto nel pattern di integrazione 1. <br>- Se si utilizza AT.js, è supportata solo l’integrazione del profilo rispetto allo spazio dei nomi di identità ECID. <br>- Per le ricerche dello spazio dei nomi di identità personalizzato in Edge, è necessaria la distribuzione WebSDK e ogni identità deve essere impostata come identità nella mappa di identità.</td>
  </tr>
  <tr>
    <td class="tg-0lax">3</td>
    <td class="tg-73oq"><span style="font-weight:400;font-style:normal">Streaming e condivisione in batch dell'audience da Real-time Customer Data Platform a Target ed Audience Manager tramite l'approccio al servizio di condivisione del pubblico</span></td>
    <td class="tg-0lax"><span style="font-weight:400;font-style:normal">- Condividi tipi di pubblico in streaming e in batch da Real-time Customer Data Platform a Target ed Audience Manager tramite il servizio Audience Sharing. Questo modello di integrazione può essere sfruttato quando è necessario un arricchimento aggiuntivo da dati di terze parti e tipi di pubblico in Audience Manager. In caso contrario, si consiglia il pattern di integrazione 1 e 2. I tipi di pubblico valutati in tempo reale richiedono Web SDK e la valutazione del pubblico in tempo reale, come descritto nel pattern di integrazione 1.</span></td>
    <td class="tg-73oq">- È necessario il provisioning della proiezione del pubblico tramite il servizio di condivisione del pubblico.<br>- L’integrazione con Target richiede la stessa organizzazione IMS usata per l’istanza di Experience Platform.<br>- L’identità deve essere risolta in ECID affinché possa essere condivisa con la rete Edge e utilizzata da Target.<br>- L’implementazione WebSDK non è necessaria per questa integrazione.</td>
  </tr>
</tbody>
</table>


## Architettura del modello di integrazione 1


Architettura dettagliata per il modello di integrazione 1

<img src="assets/RTCDP+Target.png" alt="Architettura di riferimento per il blueprint per la personalizzazione web con dati online/offline" style="width:80%; border:1px solid #4a4a4a" />

Diagramma della sequenza per il pattern di integrazione 1

<img src="assets/RTCDP+Target_flow.png" alt="Architettura di riferimento per il blueprint per la personalizzazione web con dati online/offline" style="width:80%; border:1px solid #4a4a4a" />

<br>

<img src="assets/RTCDP+Target_sequence.png" alt="Architettura di riferimento per il blueprint per la personalizzazione web con dati online/offline" style="width:80%; border:1px solid #4a4a4a" />

Architettura della panoramica per il modello di integrazione 1

<img src="assets/personalization_with_apps.png" alt="Architettura di riferimento per il blueprint per la personalizzazione web con dati online/offline" style="width:80%; border:1px solid #4a4a4a"/>


## Implementazione per il modello di integrazione 1

Per la segmentazione in tempo reale sul bordo del [!UICONTROL SDK per web per Platform] e [!UICONTROL Rete Edge] devono essere implementati. [Consulta il blueprint per Experience Platform Web/Mobile SDK](../data-ingestion/websdk.md)

### Passaggi di implementazione per il modello di integrazione 1

1. [Implementare Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=it) per le applicazioni web o mobili
1. [Implementare Experience Platform e [!UICONTROL Real-time Customer Profile]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=it)
1. Implementare [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=it). Experience Platform Web SDK è necessario per la segmentazione Edge in tempo reale, ma non è necessario per la condivisione di audience in streaming e batch da Real-time Customer Data Platform a Target. Al momento il supporto per la segmentazione in tempo reale tramite l’SDK mobile e l’API non è disponibile.
1. [Configurare la rete Edge con un Datastream Edge](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)
1. [Abilitare Adobe Target come destinazione in Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=it)

## Implementazione dei pattern 2 e 3 di integrazione

Utilizzo di SDK tradizionali specifici per le applicazioni (ad esempio, AT.js e AppMeasurement.js)
<img src="assets/app_sdk_flow.png" alt="Architettura di riferimento per l’approccio con SDK per specifiche applicazioni" style="width:80%; border:1px solid #4a4a4a" />

### Passaggi di implementazione per i pattern di integrazione 2 e 3

1. [Implementare Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html) per le applicazioni web o mobili
1. [Implementare Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=it) (opzionale)
1. [Implementare Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=it) (opzionale)
1. [Implementare Experience Platform e [!UICONTROL Real-time Customer Profile]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html)
1. Implementare [Servizio Experience Cloud Identity](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=it)
1. [Richiedi il provisioning per la condivisione del pubblico tra Experience Platform e Adobe Target (pubblico condiviso)](https://www.adobe.com/go/audiences) per condividere tipi di pubblico da Experience Platform a Target.
1. (Facoltativo) [Configurare la rete Edge con un Datastream Edge](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html) Questo è necessario solo per il pattern di integrazione 2, in cui il pubblico non deve essere condiviso in Audience Manager o arricchito da tipi di pubblico o dati di Audience Manager.
1. (Facoltativo) [Abilitare Adobe Target come destinazione in Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en) per condividere audience in streaming e in batch da Real-time Customer Data Platform direttamente a Edge rispetto a tramite il servizio e l’Audience Manager di condivisione del pubblico.

## Guardrail

[Fai riferimento ai guardrail nella panoramica dei blueprint per personalizzazione web/mobile.](overview.md)

## Considerazioni sull’implementazione

Prerequisiti per l’identità

* Qualsiasi identità primaria può essere sfruttata quando si utilizza il pattern di integrazione 1 descritto in precedenza con la rete Edge e WebSDK. La prima personalizzazione di accesso richiede che l’identità principale del set di richieste di personalizzazione corrisponda all’identità principale del profilo di Real-time Customer Data Platform. L’unione delle identità tra dispositivi anonimi e clienti noti viene elaborata sull’hub e successivamente proiettata sul server Edge. Pertanto, se l’identità principale è impostata come identificatore del dispositivo, i dati dei clienti noti non verranno applicati fino alle sessioni successive in cui i profili anonimi e noti sono stati unificati.
* La condivisione di tipi di pubblico da Adobe Experience Platform ad Adobe Target richiede l’uso di ECID come identità quando si utilizza il servizio di condivisione del pubblico come descritto nel modello di integrazione 3 di cui sopra.
* Inoltre, è possibile utilizzare identità alternative per condividere i tipi di pubblico di Experience Platform con Adobe Target tramite Audience Manager. Experience Platform attiva i tipi di pubblico in Audience Manager tramite i seguenti spazi dei nomi supportati: IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Tieni presente che Audience Manager e Target risolvono l’appartenenza a un pubblico tramite l’identità ECID. Pertanto l’ECID è comunque necessario per la condivisione finale del pubblico in Adobe Target.

## Documentazione correlata

### Documentazione

* [Connessione Adobe Target per Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en)
* [Condivisione dei segmenti Experience Platform con Audience Manager e altre soluzioni Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=it)
* [Documentazione di Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Documentazione del servizio Experience Cloud ID](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=it)
* [Panoramica sulla segmentazione in Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=it)
* [Segmentazione in tempo reale](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html)
* [Segmentazione in streaming](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it)
* [Panoramica di Experience Platform Segment Builder](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html)
* [Connettore origini di Audience Manager](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=it)
* [Condivisione dei segmenti di Adobe Analytics tramite Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=it)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it)

### Tutorial

* [Personalizzazione con hit successivo con Real-time CDP e Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=it)

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
