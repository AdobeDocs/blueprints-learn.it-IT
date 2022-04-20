---
title: Panoramica di Web/Mobile Personalization
description: Sincronizza la personalizzazione web con l’e-mail e altre personalizzazioni di canali per utenti noti e anonimi.
landing-page-description: Sincronizza la personalizzazione web con l’e-mail e altre personalizzazioni di canali per utenti noti e anonimi.
solution: Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection, Experience Platform
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 4d0313e079a6f0f48f9c958f598f0fd02b90fd5f
workflow-type: tm+mt
source-wordcount: '1229'
ht-degree: 81%

---


# Personalization Web/Mobile con dati cliente noti

## Casi di utilizzo

* Personalizzazione online con dati noti dei clienti
* Ottimizzazione della pagina di destinazione
* Personalizzazione basata su precedenti visualizzazioni di prodotti/contenuti, affinità di prodotti/contenuti, attributi ambientali e dati demografici, nonché dati offline quali dati da transazioni, dal programma fedeltà e dal sistema CRM, e dati modellati
* Utilizza Adobe Target per la condivisione e il targeting dei tipi di pubblico definiti in Real-time Customer Data Platform su siti web e app mobili.

## Applicazioni

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (facoltativo): Aggiunge dati di pubblico di terze parti, grafico dei dispositivi basato su co-op
* Adobe Analytics (opzionale): aggiunge la possibilità di creare segmenti basati su dati comportamentali cronologici e sulla segmentazione granulare dei dati di Adobe Analytics.

## Pattern di integrazione

| Pattern di integrazione | Funzionalità | Prerequisiti |
|---|---|---|
| Valutazione dei segmenti in tempo reale sul server Edge condiviso da Real-time Customer Data Platform a Target | <ul><li>Valutare i tipi di pubblico in tempo reale sul server Edge per la personalizzazione della pagina corrente o successiva.</li><li>Inoltre, i segmenti valutati in streaming o in modalità batch verranno proiettati sulla rete Edge e inclusi nella valutazione e personalizzazione dei segmenti Edge.</li></ul> | <ul><li>È necessario implementare Web/Mobile SDK.</li><li>Il Datastream deve essere configurato in Experience Edge con l’estensione Target e Experience Platform abilitata</li><li>La destinazione Target deve essere configurata nelle destinazioni di Real-time Customer Data Platform.</li><li>L’integrazione con Target richiede la stessa organizzazione IMS usata per l’istanza di Experience Platform.</li></ul> |
| Condivisione dei tipi di pubblico in streaming e in batch da Real-time Customer Data Platform a Target tramite l’approccio Edge | <ul><li>I tipi di pubblico in streaming e in batch devono essere condivisi da Real-time Customer Data Platform a Target tramite la rete Edge. I tipi di pubblico valutati in tempo reale richiedono l&#39;implementazione di WebSDK e Edge Network.</li></ul> | <ul><li>L’SDK per web/Mobile non è necessario per la condivisione di tipi di pubblico in streaming e in batch su Target, anche se è necessario per abilitare la valutazione dei segmenti edge in tempo reale.</li><li>Se si utilizza AT.js, è supportata solo l’integrazione dei profili rispetto allo spazio dei nomi dell’identità ECID.</li><li>Per le ricerche tramite identità da spazi dei nomi personalizzati nella rete Edge, è necessario implementare Web SDK e ogni identità deve essere impostata nella mappa delle identità.</li><li>La destinazione Target deve essere configurata nelle destinazioni di Real-time Customer Data Platform.</li><li>L’integrazione con Target richiede la stessa organizzazione IMS usata per l’istanza di Experience Platform.</li></ul> |
| Condivisione dei tipi di pubblico in streaming e in batch da Real-time Customer Data Platform a Target e Audience Manager tramite il servizio Audience Sharing | <ul><li>Questo modello di integrazione può essere sfruttato quando è necessario un arricchimento aggiuntivo da dati di terze parti e tipi di pubblico in Audience Manager.</li></ul> | <ul><li>L’SDK per web/Mobile non è necessario per la condivisione di tipi di pubblico in streaming e in batch su Target, anche se è necessario per abilitare la valutazione dei segmenti edge in tempo reale.</li><li>Se si utilizza AT.js, è supportata solo l’integrazione dei profili rispetto allo spazio dei nomi dell’identità ECID.</li><li>Per le ricerche tramite identità da spazi dei nomi personalizzati nella rete Edge, è necessario implementare Web SDK e ogni identità deve essere impostata nella mappa delle identità.</li><li>È necessario il provisioning della proiezione del pubblico tramite il servizio di condivisione del pubblico.</li><li>La destinazione Target deve essere configurata nelle destinazioni di Real-time Customer Data Platform.</li><li>L’integrazione con Target richiede la stessa organizzazione IMS usata per l’istanza di Experience Platform.</li></ul> |

## Condivisione in tempo reale, in streaming e in batch del pubblico su Adobe Target

Architettura

<img src="assets/RTCDP+Target.png" alt="Architettura di riferimento del blueprint per la personalizzazione web con dati online/offline" style="width:90%; border:1px solid #4a4a4a" />

Dettagli della sequenza

<img src="assets/RTCDP+Target_flow.png" alt="Architettura di riferimento del blueprint per la personalizzazione web con dati online/offline" style="width:90%; border:1px solid #4a4a4a" />

Architettura d’insieme

<img src="assets/personalization_with_apps.png" alt="Architettura di riferimento per il blueprint per la personalizzazione web con dati online/offline" style="width:90%; border:1px solid #4a4a4a"/>

## Modelli di implementazione

Personalization cliente noto è supportato tramite diversi approcci di implementazione.

### Modello di implementazione 1 - Edge Network con SDK per web/dispositivi mobili (approccio consigliato)

Utilizzo della rete Edge con Web/Mobile SDK. La segmentazione edge in tempo reale richiede l’approccio di implementazione dell’SDK per web/Mobile o dell’API Edge.

[Consulta il blueprint per Experience Platform Web/Mobile SDK](../data-ingestion/websdk.md)

### Modello di implementazione 2: SDK specifici per l’applicazione

Mediante SDK tradizionali per specifiche applicazioni (ad esempio, AT.js e AppMeasurement.js). La valutazione dei segmenti Edge in tempo reale non è supportata utilizzando questo approccio di implementazione. Tuttavia, lo streaming e la condivisione di audience in batch dall’hub di Experience Platform sono supportati utilizzando questo approccio di implementazione.

[Fai riferimento alla blueprint SDK specifica per l’applicazione](../data-ingestion/appsdk.md)

### Fasi di implementazione

1. [Implementare Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=it) per le applicazioni web o mobili
1. [Implementare Experience Platform e il [!UICONTROL profilo cliente in tempo reale]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=it) e assicurarsi che i tipi di pubblico creati siano attivati sul server Edge configurando il [criterio di unione](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=it#create-a-merge-policy) applicabile affinché sia attivo sul server Edge.
1. Implementare [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=it). Experience Platform Web SDK è necessario per la segmentazione Edge in tempo reale, ma non per la condivisione di tipi di pubblico in streaming e in batch da Real-time Customer Data Platform a Target. Al momento la segmentazione in tempo reale tramite Mobile SDK e l’API non è supportata.
1. [Configurare la rete Edge con uno stream di dati Edge](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=it)
1. [Abilitare Adobe Target come destinazione in Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=it)
1. (Facoltativo) [Implementare Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=it).
1. (Facoltativo) [Richiedi il provisioning per la condivisione del pubblico tra Experience Platform e Adobe Target (pubblico condiviso)](https://www.adobe.com/go/audiences) per condividere tipi di pubblico da Experience Platform a Target.

## Guardrail

[Fai riferimento ai guardrail nella panoramica dei blueprint per personalizzazione web/mobile.](overview.md)

## Considerazioni sull’implementazione

Prerequisiti per l’identità

* Quando si utilizza il modello di implementazione 1 descritto in precedenza con la rete Edge e Web SDK, è possibile utilizzare qualsiasi identità primaria. Per la personalizzazione al primo accesso, l’identità primaria definita dalla richiesta di personalizzazione deve corrispondere all’identità primaria del profilo da Real-time Customer Data Platform. L’unione delle identità tra dispositivi anonimi e clienti noti viene elaborata sull’hub e successivamente proiettata sulla rete Edge.
* La condivisione di tipi di pubblico da Adobe Experience Platform ad Adobe Target richiede l’uso di ECID come identità se si utilizza il servizio Audience Sharing, come descritto per lo scenario 3 dei casi di utilizzo.
* Inoltre, è possibile utilizzare identità alternative per condividere i tipi di pubblico di Experience Platform con Adobe Target tramite Audience Manager. Experience Platform attiva i tipi di pubblico in Audience Manager tramite i seguenti spazi dei nomi supportati: IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Tieni presente che Audience Manager e Target risolvono l’appartenenza a un pubblico tramite l’identità ECID. Pertanto l’ECID è comunque necessario per la condivisione finale del pubblico in Adobe Target.

## Documentazione correlata

### Documentazione di SDK

* [Documentazione di Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it)
* [Documentazione del servizio Experience Cloud ID](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=it)

### Documentazione sulle connessioni

* [Connessione Adobe Target per Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en)
* [Configurazione dello stream di dati Edge](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)
* [Condivisione dei segmenti Experience Platform con Audience Manager e altre soluzioni Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=it)

### Documentazione sulla segmentazione

* [Panoramica sulla segmentazione in Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=it)
* [Segmentazione in tempo reale](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=it)
* [Segmentazione in streaming](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it)
* [Condivisione dei segmenti di Adobe Analytics tramite Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=it)
* [Configurazione dei criteri di unione](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=en#create-a-merge-policy)

### Tutorial

* [Personalizzazione con hit successivo con Real-time CDP e Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=it)

### Articoli di blog correlati

* [Adobe annuncia la personalizzazione avanzata sulla stessa pagina con Adobe Target e Real-time Customer Data Platform](https://blog.adobe.com/en/publish/2021/10/05/adobe-announces-same-page-enhanced-personalization-with-adobe-target-real-time-customer-data-platform)
* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Adobe Experience Platform’s Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
