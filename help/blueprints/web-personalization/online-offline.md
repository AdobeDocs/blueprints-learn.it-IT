---
title: Personalizzazione web e mobile con dati online e offline
description: Sincronizza la personalizzazione web con l’e-mail e altre personalizzazioni di canali per utenti noti e anonimi.
landing-page-description: Sincronizza la personalizzazione web con l’e-mail e altre personalizzazioni di canali per utenti noti e anonimi.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 0dda473e727ee367f6fa9ad78c9201d18bc064b9
workflow-type: ht
source-wordcount: '1531'
ht-degree: 100%

---


# Personalizzazione web e mobile con dati online e offline

## Casi di utilizzo

* Personalizzazione online con dati online e offline e profili noti
* Ottimizzazione della pagina di destinazione
* Personalizzazione basata su precedenti visualizzazioni di prodotti/contenuti, affinità di prodotti/contenuti, attributi ambientali e dati demografici, nonché dati offline quali dati da transazioni, dal programma fedeltà e dal sistema CRM, e dati modellati
* Utilizza Adobe Target per la condivisione e il targeting dei tipi di pubblico definiti in Real-time Customer Data Platform su siti web e app mobili.

## Applicazioni

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (opzionale): consente di aggiungere dati sul pubblico di terze parti, grafi dei dispositivi basati su co-op, nonché di far emergere i tipi di pubblico di Real-time Customer Data Platform in Adobe Analytics e viceversa.
* Adobe Analytics (opzionale): aggiunge la possibilità di creare segmenti basati su dati comportamentali cronologici e sulla segmentazione granulare dei dati di Adobe Analytics.

## Scenari di casi di utilizzo

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
    <th class="tg-f7v4">Scenari di casi di utilizzo</th>
    <th class="tg-y6fn">Funzionalità</th>
    <th class="tg-f7v4">Prerequisiti</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">1</td>
<td class="tg-73oq">Valutazione dei segmenti in tempo reale sul server Edge condiviso da Real-time Customer Data Platform a Target</td>
    <td class="tg-0lax">- Valutare i tipi di pubblico in tempo reale sul server Edge per la personalizzazione della pagina corrente o successiva.<br>- Inoltre, i segmenti valutati in streaming o in modalità batch verranno proiettati sulla rete Edge e inclusi nella valutazione e personalizzazione dei segmenti Edge.</td>
    <td class="tg-73oq">- Modello di implementazione 1 descritto di seguito.<br>- È necessario implementare Web/Mobile SDK.<br>- Al momento il supporto per la segmentazione in tempo reale basata su Mobile SDK e API non è disponibile<br>- Lo stream di dati deve essere configurato in Experience Edge con l’estensione Target ed Experience Platform abilitata; l’ID dello stream di dati verrà fornito nella configurazione della destinazione di Target.<br>- La destinazione di Target deve essere configurata nelle destinazioni di Real-time Customer Data Platform.<br>- L’integrazione con Target richiede la stessa organizzazione IMS usata per l’istanza di Experience Platform.</td> 
  </tr>
  <tr>
    <td class="tg-0lax">2</td>
    <td class="tg-73oq">Condivisione dei tipi di pubblico in streaming e in batch da Real-time Customer Data Platform a Target tramite l’approccio Edge</td>
    <td class="tg-0lax">- I tipi di pubblico in streaming e in batch devono essere condivisi da Real-time Customer Data Platform a Target tramite la rete Edge. I tipi di pubblico valutati in tempo reale richiedono Web SDK e la valutazione del pubblico in tempo reale, come descritto nel modello di integrazione 1.<br>- Questa integrazione viene generalmente utilizzata per condividere i tipi di pubblico in streaming e batch utilizzando gli SDK tradizionali, invece della migrazione a Edge Collection e Web SDK, per i tipi di pubblico in tempo reale, in streaming e in batch come descritto nel modello di integrazione 1.</td>
    <td class="tg-73oq">- Modello di implementazione 1 o 2 descritto di seguito.<br>- Web/Mobile SDK non è necessario per la condivisione di tipi di pubblico in streaming e in batch con Target, ma è necessario per la valutazione dei segmenti Edge in tempo reale come descritto nel modello di integrazione 1. <br>- Se si utilizza AT.js, è supportata solo l’integrazione dei profili rispetto allo spazio dei nomi dell’identità ECID. <br>- Per le ricerche tramite identità da spazi dei nomi personalizzati nella rete Edge, è necessario implementare Web SDK e ogni identità deve essere impostata nella mappa delle identità.<br>- Lo stream di dati deve essere configurato in Experience Edge; l’ID dello stream di dati verrà fornito nella configurazione di destinazione di Target.<br>- La destinazione di Target deve essere configurata nelle destinazioni di Real-time Customer Data Platform.<br>- L’integrazione con Target richiede la stessa organizzazione IMS usata per l’istanza di Experience Platform.</td>
  </tr>
  <tr>
    <td class="tg-0lax">3</td>
    <td class="tg-73oq"><span style="font-weight:400;font-style:normal">Condivisione dei tipi di pubblico in streaming e in batch da Real-time Customer Data Platform a Target e Audience Manager tramite il servizio Audience Sharing</span></td>
    <td class="tg-0lax"><span style="font-weight:400;font-style:normal">- Condividere i tipi di pubblico in modalità batch e streaming da Real-time Customer Data Platform a Target e Audience Manager tramite il servizio Audience Sharing.<br>- Questo modello di integrazione può essere sfruttato quando è necessario arricchire ulteriormente i dati con dati di terze parti e tipi di pubblico in Audience Manager. In caso contrario, si consigliano i modelli di integrazione 1 e 2. I tipi di pubblico valutati in tempo reale richiedono Web SDK e la valutazione del pubblico in tempo reale, come descritto nel modello di integrazione 1.</span></td>
    <td class="tg-73oq">- Modello di implementazione 1 o 2 descritto di seguito.<br>- Per questa integrazione non è necessario implementare Web/Mobile SDK.<br>- È necessario il provisioning della proiezione del pubblico tramite il servizio Audience Sharing.<br>- L’integrazione con Target richiede la stessa organizzazione IMS usata per l’istanza di Experience Platform.<br>- L’identità deve essere risolta in ECID affinché possa essere condivisa con la rete Edge e utilizzata da Target.</td>
  </tr>
</tbody>
</table>

## Scenari 1 e 2 - Condivisione del pubblico in tempo reale, in streaming e in batch con Adobe Target

Architettura

<img src="assets/RTCDP+Target.png" alt="Architettura di riferimento del blueprint per la personalizzazione web con dati online/offline" style="width:80%; border:1px solid #4a4a4a" />

Dettagli della sequenza

<img src="assets/RTCDP+Target_flow.png" alt="Architettura di riferimento del blueprint per la personalizzazione web con dati online/offline" style="width:80%; border:1px solid #4a4a4a" />

Caso di utilizzo, scenari 1 e 2 - Panoramica dell’architettura

<img src="assets/personalization_with_apps.png" alt="Architettura di riferimento del blueprint per la personalizzazione web con dati online/offline" style="width:80%; border:1px solid #4a4a4a"/>

### I passaggi di implementazione per lo scenario del caso di utilizzo 1 supportano anche lo scenario del caso di utilizzo 2

1. [Implementare Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=it) per le applicazioni web o mobili
1. [Implementare Experience Platform e il [!UICONTROL profilo cliente in tempo reale]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=it) e assicurarsi che i tipi di pubblico creati siano attivati sul server Edge configurando il [criterio di unione](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=it#create-a-merge-policy) applicabile affinché sia attivo sul server Edge.
1. Implementare [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=it). Experience Platform Web SDK è necessario per la segmentazione Edge in tempo reale, ma non per la condivisione di tipi di pubblico in streaming e in batch da Real-time Customer Data Platform a Target. Al momento la segmentazione in tempo reale tramite Mobile SDK e l’API non è supportata.
1. [Configurare la rete Edge con uno stream di dati Edge](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=it)
1. [Abilitare Adobe Target come destinazione in Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=it)

<br>

## Scenario 3 - Condivisione dei tipi di pubblico in streaming e in batch tramite il servizio Audience Sharing su Adobe Target ed Audience Manager

Architettura

<img src="assets/audience_share_architecture.png" alt="Architettura di riferimento del blueprint per la personalizzazione web con dati online/offline" style="width:80%; border:1px solid #4a4a4a" />

### I passaggi di implementazione per lo scenario 3 supportano anche lo scenario 2

1. [Implementare Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=it) per le applicazioni web o mobili
1. [Implementare Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=it) (opzionale)
1. [Implementare Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=it) (opzionale)
1. [Implementare Experience Platform e [!UICONTROL Real-time Customer Profile]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=it)
1. Implementare il [Servizio Experience Cloud Identity](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=it)
1. [Richiedere il provisioning per la condivisione del pubblico tra Experience Platform e Adobe Target (pubblico condiviso)](https://www.adobe.com/go/audiences) per condividere i tipi di pubblico da Experience Platform a Target.
1. (Facoltativo) [Configurare la rete Edge con uno stream di dati Edge](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=it) (necessario solo per il modello di integrazione 2, in cui il pubblico non deve essere condiviso con Audience Manager o arricchito da tipi di pubblico o dati di Audience Manager)
1. (Facoltativo) [Abilitare Adobe Target come destinazione in Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=it) per condividere i tipi di pubblico in streaming e in batch da Real-time Customer Data Platform direttamente ala rete Edge, anziché tramite il servizio Audience Sharing e Audience Manager.

<br>

## Modelli di implementazione

La personalizzazione online e offline è supportata mediante diversi approcci di implementazione.

### Modello di implementazione 1 - Supporta i casi di utilizzo degli scenari 1 e 2. Rete Edge con Web/Mobile SDK (approccio consigliato)

Utilizzo della rete Edge con Web/Mobile SDK
<img src="assets/web_sdk_flow.png" alt="Architettura di riferimento per l’approccio con SDK per specifiche applicazioni" style="width:80%; border:1px solid #4a4a4a" />

Diagramma della sequenza

<img src="assets/RTCDP+Target_sequence.png" alt="Architettura di riferimento del blueprint per la personalizzazione web con dati online/offline" style="width:80%; border:1px solid #4a4a4a" />

<br>

### Modello di implementazione 2 - Supporta i casi di utilizzo degli scenari 2 e 3. SDK per specifiche applicazioni

Mediante SDK tradizionali per specifiche applicazioni (ad esempio, AT.js e AppMeasurement.js)
<img src="assets/app_sdk_flow.png" alt="Architettura di riferimento per l’approccio con SDK per specifiche applicazioni" style="width:80%; border:1px solid #4a4a4a" />

<br>

## Guardrail

[Fai riferimento ai guardrail nella panoramica dei blueprint per personalizzazione web/mobile.](overview.md)

## Considerazioni sull’implementazione

Prerequisiti per l’identità

* Quando si utilizza il modello di implementazione 1 descritto in precedenza con la rete Edge e Web SDK, è possibile utilizzare qualsiasi identità primaria. Per la personalizzazione al primo accesso, l’identità primaria definita dalla richiesta di personalizzazione deve corrispondere all’identità primaria del profilo da Real-time Customer Data Platform. L’unione delle identità tra dispositivi anonimi e clienti noti viene elaborata sull’hub e successivamente proiettata sulla rete Edge.
* La condivisione di tipi di pubblico da Adobe Experience Platform ad Adobe Target richiede l’uso di ECID come identità se si utilizza il servizio Audience Sharing, come descritto per lo scenario 3 dei casi di utilizzo.
* Inoltre, è possibile utilizzare identità alternative per condividere i tipi di pubblico di Experience Platform con Adobe Target tramite Audience Manager. Experience Platform attiva i tipi di pubblico in Audience Manager tramite i seguenti spazi dei nomi supportati: IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Tieni presente che Audience Manager e Target risolvono l’appartenenza a un pubblico tramite l’identità ECID. Pertanto l’ECID è comunque necessario per la condivisione finale del pubblico in Adobe Target.

## Documentazione correlata

### Documentazione di SDK

* [Documentazione di Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=it)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it)
* [Documentazione del servizio Experience Cloud ID](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=it)

### Documentazione sulle connessioni

* [Connessione Adobe Target per Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=it)
* [Configurazione dello stream di dati Edge](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=it)
* [Condivisione dei segmenti Experience Platform con Audience Manager e altre soluzioni Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=it)

### Documentazione sulla segmentazione

* [Panoramica sulla segmentazione in Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=it)
* [Segmentazione in tempo reale](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=it)
* [Segmentazione in streaming](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it)
* [Condivisione dei segmenti di Adobe Analytics tramite Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=it)
* [Configurazione dei criteri di unione](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=it#create-a-merge-policy)

### Tutorial

* [Personalizzazione con hit successivo con Real-time CDP e Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=it)

### Articoli di blog correlati

* [Adobe annuncia la personalizzazione avanzata sulla stessa pagina con Adobe Target e Real-time Customer Data Platform](https://blog.adobe.com/en/publish/2021/10/05/adobe-announces-same-page-enhanced-personalization-with-adobe-target-real-time-customer-data-platform)
* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Adobe Experience Platform’s Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
