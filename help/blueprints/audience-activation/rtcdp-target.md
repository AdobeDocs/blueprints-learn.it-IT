---
title: Customer Personalization noto con Target
description: Integra profili e pubblico di RTCDP con Adobe Target.
landing-page-description: Integra profili e pubblico di RTCDP con Adobe Target.
short-description: Integra profili e pubblico di RTCDP con Adobe Target.
solution: Real-Time Customer Data Platform, Target, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
TQID: https://experienceleague.adobe.com/1ti2SqfAFOgnKbaJ70xwGI-xHDE1WXJ7-oTStcJJy1E
product_v2:
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
feature_v2:
  - id: a37e4ecd-c740-426a-addf-cb1b483c5c5a
  - id: adee20bd-51f4-461d-b9db-d215f8756eeb
  - id: ba929a52-9339-4154-9487-317dc875a3c7
  - id: c132d929-fa62-4271-803e-b823be07b914
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
subfeature_v2:
  - id: cbd4a8d8-97a6-4ac9-b8d6-b6c1f28d3342
  - id: cdd3e38b-fec2-4f39-8b10-83ddaab1ac16
  - id: d1823595-9241-4128-8a33-e4ac3bf08773
  - id: ee602049-8a18-43df-9299-a689a025a371
  - id: fd0ff162-b6d3-4a11-8aeb-e165a01c0f0a
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 735
ht-degree: 37%

---

# Customer Personalization noto con Target

>[!TIP]
>Questo blueprint è disponibile anche come [caso d&#39;uso](/help/blueprints/use-case-patterns/personalization/audience-sharing-with-target.md) in Personalization.

## Casi di utilizzo

* Personalizzazione online con dati dei clienti noti
* Ottimizzazione della pagina di destinazione
* Personalizzazione basata su precedenti visualizzazioni di prodotti/contenuti, affinità di prodotti/contenuti, attributi ambientali e dati demografici, nonché dati offline quali dati da transazioni, dal programma fedeltà e dal sistema CRM, e dati modellati
* Condividere e indirizzare i tipi di pubblico definiti in Real-time Customer Data Platform su siti web e app mobili tramite Adobe Target

## Applicazioni

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target

### Documentazione di riferimento

* [Connessione Adobe Target per Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html)
* [Configurazione dello stream di dati Edge](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=it)

## Modelli di integrazione

| Modello di integrazione | Funzionalità | Prerequisiti |
|--------------------|------------|---------------|
| **Valutazione dei segmenti in tempo reale su Edge condivisa da Real-time Customer Data Platform a Target** | : valuta i tipi di pubblico in tempo reale per la personalizzazione della stessa pagina o della pagina successiva in Edge. <br>- Anche tutti i segmenti valutati in streaming o in modalità batch verranno proiettati in Edge Network per essere inclusi nella valutazione e nella personalizzazione dei segmenti edge. | - È necessario implementare Web/Mobile SDK per l’API server di Edge Network. <br>- Lo stream di dati deve essere configurato in Experience Edge con l&#39;estensione Target e Experience Platform abilitata. <br>- La destinazione di destinazione deve essere configurata in Destinazioni Real-time Customer Data Platform. <br>- L’integrazione con Target richiede la stessa organizzazione IMS usata per l’istanza di Experience Platform. |
| **Condivisione in streaming e in batch del pubblico da Real-time Customer Data Platform a Target tramite l&#39;approccio Edge** | - I tipi di pubblico in streaming e in batch devono essere condivisi da Real-time Customer Data Platform a Target tramite la rete Edge. <br>- I tipi di pubblico valutati in tempo reale richiedono l&#39;implementazione di Web SDK e Edge Network. | - L’implementazione di SDK per web/mobile o API per Edge di Target non è necessaria per la condivisione di tipi di pubblico RTCDP in streaming o in batch con Target, ma è necessaria per abilitare la valutazione Edge in tempo reale. <br>- Se si utilizza AT.js, è supportata solo l’integrazione dei profili rispetto allo spazio dei nomi dell’identità ECID. <br>- Per le ricerche personalizzate dello spazio dei nomi delle identità in Edge, è necessaria la distribuzione API Web SDK/Edge e ogni identità deve essere impostata come identità nella mappa delle identità. <br>- La destinazione di destinazione deve essere configurata in Destinazioni Real-time Customer Data Platform. È supportata solo la sandbox di produzione predefinita in RTCDP. <br>- L’integrazione con Target richiede la stessa organizzazione IMS usata per l’istanza di Experience Platform. |
| **Condivisione in streaming e in batch del pubblico da Real-time Customer Data Platform a Target e Audience Manager tramite l&#39;approccio del servizio di condivisione del pubblico** | : questo modello di integrazione può essere utilizzato quando desideri un ulteriore arricchimento dai dati e dai tipi di pubblico di terze parti in Audience Manager. | - Web/Mobile SDK non è richiesto per la condivisione di tipi di pubblico in streaming e in batch su Target, ma è necessario per abilitare la valutazione Edge in tempo reale. <br>- Se si utilizza AT.js, è supportata solo l’integrazione dei profili rispetto allo spazio dei nomi dell’identità ECID. <br>- Per le ricerche personalizzate dello spazio dei nomi delle identità in Edge, è necessaria la distribuzione API Web SDK/Edge e ogni identità deve essere impostata come identità nella mappa delle identità. <br>- È necessario eseguire il provisioning della proiezione del pubblico tramite il servizio di condivisione del pubblico. <br>- L’integrazione con Target richiede la stessa organizzazione IMS usata per l’istanza di Experience Platform. <br>- Solo i tipi di pubblico della sandbox di produzione predefinita supportano il servizio core di condivisione del pubblico. |

## Condivisione del pubblico in tempo reale, in streaming e in batch con Adobe Target

Architettura

![Architettura di riferimento per il blueprint di Web Personalization online/offline](assets/RTCDP+Target.svg)

Dettagli della sequenza

![Architettura di riferimento per il blueprint di Web Personalization online/offline](assets/RTCDP+Target_flow.svg)

Architettura d’insieme

![Architettura di riferimento per il blueprint di Web Personalization online/offline](assets/personalization_with_apps.svg)

## Documentazione correlata

### Documentazione di SDK

* [Documentazione di Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=it)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it)
* [Documentazione del servizio Experience Cloud ID](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=it)

### Documentazione sulla segmentazione

* [Panoramica sulla segmentazione di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=it)
* [Segmentazione in tempo reale](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=it)
* [Segmentazione in streaming](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it)
* [Condivisione dei segmenti di Adobe Analytics tramite Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=it)
* [Configurazione criterio di unione](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=it#create-a-merge-policy)

### Tutorial

* [Personalizzazione dell’hit successivo con Real-Time CDP e Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=it)
