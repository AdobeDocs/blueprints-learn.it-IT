---
title: Blueprint Customer Journey Analytics
description: Unificare e analizzare i dati e i comportamenti dei clienti da tutto il percorso del cliente
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 3bb2dada-f4cd-43f7-a0d0-f276510ad224
source-git-commit: b69e73349741b829f05d04cfac70aa0161ef7684
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 91%

---

# Blueprint Customer Journey Analytics

Customer Journey Analytics mostra come i brand possono unificare i dati e il comportamento dei clienti da vari canali di interazione e origini per creare una visione basata sul percorso di tutte le interazioni. È possibile eseguire report e analisi nel servizio applicativo Customer Journey Analytics, al fine di valutare e acquisire informazioni dettagliate sulle interazioni e sui pattern di comportamento dei clienti.

Un elenco completo dei casi d’uso per Customer Journey Analytics è disponibile nella documentazione di Customer Journey Analytics.

## Casi d’uso per Customer Journey Analytics

[I casi d’uso più comuni includono:](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cja-usecases.html?lang=it)

* Creare e pubblicare tipi di pubblico in Real-time Customer Data Platform
* Percorsi di conversione migliori/peggiori
* Coinvolgimento e conversione per canale
* Contenuti più visualizzati
* Categorie e prodotti di maggior successo
* Campagne che hanno portato alla conversione e a un maggior coinvolgimento
* Analisi dell’utilizzo degli strumenti per ottimizzare le esperienze self-service

## Architettura per Customer Journey Analytics

![Diagramma dell’architettura](assets/CJA.svg){zoomable="yes"}

Di seguito sono riportati alcuni esempi di casi d’uso principali.

| Blueprint | Descrizione | Applicazioni Experience Cloud |
|---|---|---|
| **[Analisi di Percorso cross-channel](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cross-channel.html?lang=it)** | <ul><li>Crea una visione unica e consolidata del comportamento dei clienti attraverso i vari canali, grazie all’integrazione di dati provenienti da varie proprietà web, mobili e offline.</li></ul> | <ul><li>Adobe Experience Platform</li><li>Customer Journey Analytics</li><li>Adobe Analytics (opzionale)</li></ul> |
| **[Tipi di pubblico di Publish in Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=it)** | <ul><li>Crea e pubblica i tipi di pubblico identificati da Customer Journey Analytics (CJA) nel profilo cliente in tempo reale in Adobe Experience Platform, per eseguire attività di targeting dei clienti e personalizzazione. Questa soluzione è ideale per creare tipi di pubblico sulla base di dati storici, nonché tipi di pubblico più mirati con filtri granulari e campi calcolati in Customer Journey Analytics.</li></ul> | <ul><li>Real-time Customer Data Platform</li><li>Customer Journey Analytics</li> |
| **[Analisi del Percorso di deflessione chiamate](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/call-center.html?lang=it)** | <ul><li>Individua i comportamenti più indicativi nel determinare le chiamate a un operatore, unendo i dati del call center ai dati sulle interazioni web, mobili e di altro tipo.</li><li>Questi approfondimenti possono quindi essere utilizzati per ottimizzare l’esperienza del cliente con migliori strumenti e contenuti self-service, e quindi ridurre la necessità di parlare con un operatore.  </li></ul> | <ul><li>Adobe Experience Platform</li><li>Customer Journey Analytics</li> |

## Diagramma dei guardrail per i blueprint per Customer Journey Analytics

* Per informazioni dettagliate sui guardrail e le latenze end-to-end, consulta il [documento sui guardrail relativi all’implementazione](../experience-platform/deployment/guardrails.md).

![Diagramma dei guardrail](../experience-platform/deployment/assets/CJA_guardrails.svg){zoomable="yes"}

## Articoli di blog correlati

* [[!DNL Blueprint for Multi-Channel Orchestration in Adobe Experience Platform]](https://medium.com/adobetech/blueprint-for-multi-channel-orchestration-in-adobe-experience-platform-c68317e94184){target="_blank"}
* [[!DNL Leveraging External Data Platforms in Adobe Experience Platform Journey Orchestration]](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17){target="_blank"}
* [[!DNL Event-Based Triggering on Adobe Experience Platform Orchestration Service using Apache Airflow]](https://medium.com/adobetech/event-based-triggering-on-adobe-experience-platform-orchestration-service-using-apache-airflow-8607b28251f1){target="_blank"}
* [[!DNL Adobe Campaign Classic Integration with Journey Orchestration]](https://medium.com/adobetech/adobe-campaign-classic-integration-with-journey-orchestration-ae577653281){target="_blank"}
* [[!DNL Demonstrating the Power of Adobe's New Journey Orchestration Service to Build Personalized Omnichannel Experiences in Real-Time]](https://medium.com/adobetech/demonstrating-the-power-of-adobes-new-journey-orchestration-service-to-build-personalized-aa60d88cd34){target="_blank"}
* [[!DNL Journey Orchestration in an Omnichannel World]](https://medium.com/adobetech/journey-orchestration-in-an-omnichannel-world-3a2d32d556d9){target="_blank"}
