---
title: Integrazione di Adobe Real-Time CDP e Adobe Target
description: Scopri in che modo i tipi di pubblico e il contesto del profilo di Real-Time Customer Data Platform si integrano con Adobe Target tramite Edge Network.
landing-page-description: Scopri in che modo i tipi di pubblico e il contesto del profilo di Real-Time Customer Data Platform si integrano con Adobe Target tramite Edge Network.
short-description: Scopri in che modo i tipi di pubblico e il contesto del profilo di Real-Time Customer Data Platform si integrano con Adobe Target tramite Edge Network.
solution: Real-Time Customer Data Platform, Target, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
TQID: https://experienceleague.adobe.com/1ti2SqfAFOgnKbaJ70xwGI-xHDE1WXJ7-oTStcJJy1E
product_v2:
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
    internal-label: Real-Time Customer Data Platform
feature_v2:
  - id: a37e4ecd-c740-426a-addf-cb1b483c5c5a
    internal-label: Segmentation
  - id: adee20bd-51f4-461d-b9db-d215f8756eeb
    internal-label: Audiences
  - id: ba929a52-9339-4154-9487-317dc875a3c7
    internal-label: Use cases
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
    internal-label: Implementation
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
subfeature_v2:
  - id: cbd4a8d8-97a6-4ac9-b8d6-b6c1f28d3342
    internal-label: Segments
  - id: cdd3e38b-fec2-4f39-8b10-83ddaab1ac16
    internal-label: B2B
  - id: d1823595-9241-4128-8a33-e4ac3bf08773
    internal-label: Audiences
  - id: ee602049-8a18-43df-9299-a689a025a371
    internal-label: Use cases
  - id: fd0ff162-b6d3-4a11-8aeb-e165a01c0f0a
    internal-label: at.js
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
    internal-label: Measurement
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
source-git-commit: 0c41931afad32e806d57271439e31dda84a4b2ca
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 17%
---
# Integrazione di Adobe Real-Time CDP e Adobe Target

Questa architettura mostra come [!DNL Real-Time Customer Data Platform] e [!DNL Adobe Target] si integrano tramite Edge Network. Consente di scegliere tra la valutazione del pubblico in tempo reale ai margini e la condivisione di tipi di pubblico in streaming o in batch con Target.

## Applicazioni

* [!DNL Real-Time Customer Data Platform]
* [!DNL Adobe Target]
* Edge Network [!DNL Experience Platform]
* Experience Platform Web SDK o Edge Network Server API

## Scegli un approccio di integrazione

### Valutazione del pubblico in tempo reale ai margini

Utilizza questo approccio quando [!DNL Adobe Target] ha bisogno di tipi di pubblico e attributi di profilo valutati edge per la personalizzazione della stessa pagina o della pagina successiva. Implementare l&#39;API Web SDK o Edge Network Server e configurare uno stream di dati con i servizi [!DNL Adobe Target] e [!DNL Experience Platform] abilitati.

### Condivisione in streaming e in batch del pubblico su Target

Utilizzare questo approccio quando i tipi di pubblico valutati in [!DNL Real-Time Customer Data Platform] devono essere disponibili in [!DNL Adobe Target] senza valutazione Edge in tempo reale. Configurare la destinazione [!DNL Adobe Target] nella sandbox di produzione predefinita. L’implementazione dell’API Web SDK o Edge Network Server è necessaria solo per la valutazione Edge in tempo reale o per le ricerche personalizzate dello spazio dei nomi delle identità.

## Diagramma dell’architettura

Questo diagramma mostra i punti di integrazione principali tra la raccolta dati, Edge Network, [!DNL Real-Time Customer Data Platform] e [!DNL Adobe Target].

<img src="assets/real_time_cdp_target.svg" alt="Architettura per l’integrazione di Real-Time Customer Data Platform e Adobe Target" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Diagramma del flusso di dati

Questa sequenza mostra come una richiesta client raggiunge Edge Network, valuta i tipi di pubblico e il contesto del profilo, invia una richiesta di personalizzazione a [!DNL Adobe Target] e restituisce l&#39;esperienza risultante al client.

<img src="assets/real_time_cdp_target_data_flow_detail.svg" alt="Flusso di dati per l’integrazione con Real-Time Customer Data Platform e Adobe Target" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Considerazioni sull’implementazione

* [!DNL Adobe Target] e [!DNL Real-Time Customer Data Platform] devono utilizzare la stessa organizzazione IMS.
* La destinazione [!DNL Adobe Target] supporta la sandbox di produzione predefinita in [!DNL Real-Time Customer Data Platform].
* Per le ricerche personalizzate dello spazio dei nomi delle identità nel server Edge di, utilizza Web SDK o Edge Network Server API e includi ogni identità nella mappa delle identità.
* Se utilizzi at.js, l’integrazione dei profili supporta solo lo spazio dei nomi delle identità ECID.

## Documentazione correlata

### Configurare l’integrazione

* [Connessione Adobe Target per Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=it)
* [Configurazione dello stream di dati di Edge](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=it)

### Implementare al bordo

* [Documentazione di Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=it)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it)
* [Documentazione del servizio Experience Cloud ID](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=it)

### Valutare i tipi di pubblico

* [Panoramica sulla segmentazione di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=it)
* [Segmentazione in tempo reale](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=it)
* [Segmentazione in streaming](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it)
* [Configurazione criterio di unione](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=it#create-a-merge-policy)
