---
title: Blueprint di preparazione e acquisizione dei dati
description: Questo modello mostra tutti i metodi con cui i dati possono essere acquisiti e preparati in Adobe Experience Platform.
solution: Experience Platform,Data Collection
kt: 7204
thumbnail: null
exl-id: 21f8a73e-6be7-448e-8cd3-ebee9fc848e1,5c3c94b6-c928-4d93-8b38-f8bd2aad2e68
translation-type: tm+mt
source-git-commit: 2343151a1ed5374c299fb9317f6282c232d5d23b
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---

# Blueprint di preparazione e acquisizione dei dati

Il piano di preparazione e acquisizione dei dati include tutti i metodi con cui i dati possono essere preparati e acquisiti in Adobe Experience Platform.

La preparazione dei dati include la mappatura dei dati di origine sullo schema Experience Data Model (XDM). Include inoltre l’esecuzione di trasformazioni sui dati, tra cui la formattazione della data, la suddivisione/concatenazione/conversioni dei campi e l’unione/l’unione/il reinserimento dei record. La preparazione dei dati consente di unificare i dati dei clienti per fornire analisi aggregate/filtrate, compresi i rapporti o la preparazione dei dati per l’assemblaggio del profilo cliente/scienza/attivazione dei dati.

## Architettura

<img src="assets/dataingest.svg" alt="Architettura di riferimento per il progetto di preparazione e acquisizione dei dati" style="border:1px solid #4a4a4a" />

## Metodi di acquisizione dei dati

| Metodi di ingestione | Descrizione |
|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SDK per web/mobile | Latenza:<ul><li>In tempo reale: raccolta pagine identica a Edge Network</li><li>Acquisizione in streaming da profilo ~1 minuto</li><li>Acquisizione in streaming verso data lake (micro batch ~15 minuti)</ul>Documentazione: <ul><li>[SDK per web](https://experienceleague.corp.adobe.com/docs/web-sdk.html)</li><li>[SDK per dispositivi mobili](https://experienceleague.adobe.com/docs/mobile.html?lang=en)</li></ul> |
| Sorgenti di streaming | Latenza:<ul><li>In tempo reale: raccolta pagine identica a Edge Network</li><li>Acquisizione in streaming da profilo ~1 minuto</li><li>Acquisizione in streaming verso data lake (micro batch ~15 minuti)</li></ul>[Documentazione](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en#connectors) |
| API Streaming | Latenza:<ul><li>In tempo reale: raccolta pagine identica a Edge Network</li><li>Acquisizione in streaming da profilo ~1 minuto</li><li>Acquisizione in streaming verso data lake (micro batch ~15 minuti)</li><li>7 GB/ora</li></ul>[Documentazione](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html?lang=en#what-can-you-do-with-streaming-ingestion%3F) |
| Strumenti ETL | Utilizza gli strumenti ETL per modificare e trasformare i dati aziendali prima dell’acquisizione in Experience Platform.<br><br>Latenza:<ul><li>A seconda della pianificazione esterna degli strumenti ETL, vengono applicate le protezioni standard per l’acquisizione in base al metodo utilizzato per l’acquisizione.</li></ul> |
| Origini batch | Recupero pianificato da origini<br>Latenza: ~ 200 GB/ora<br><br>[Documentazione](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en#connectors)<br>[Tutorials video](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/overview.html) |
| API Batch | Latenza:<ul><li>Acquisizione batch in profilo in base a dimensioni e carichi di traffico ~45 minuti</li><li>Acquisizione batch in data lake in base a dimensioni e carichi di traffico</li></ul>[Documentazione](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/overview.html?lang=en#batch) |
| Connettori applicazione Adobe | Acquisizione automatica dei dati provenienti dalle applicazioni Adobe Experience Cloud<ul><li>Adobe Analytics: [Documentazione](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=en#connectors) e [Esercitazione video](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/ingest-data-from-adobe-analytics.html)</li><li>Audience Manager: [Documentazione](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=en#connectors) e [Esercitazione video](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/ingest-data-from-aam.html)</li></ul> |


## Metodi di preparazione dei dati

| Metodi di preparazione dei dati | Descrizione |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [!UICONTROL Data Science Workspace]  - Preparazione dei dati | Trasformazione guidata da un modello, trasformazione scriptata.<br>[Documentazione](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=en) |
>[!NOTE]
>
>| Strumento ETL esterno ([!DNL Snaplogic], [!DNL Mulesoft], [!DNL Informatica] e così via) | Esegui trasformazioni complesse in strumenti ETL e utilizza API o connettori standard di origine Experience Platform per acquisire i dati risultanti.                                                                                                                                                               |

| [!UICONTROL Servizio query] - Preparazione dati                                  | Join, Splits, Merge, Transform, Query e Filter in un nuovo set di dati. Utilizzo di Crea tabella come selezione (CTAS) <br>[Documentazione](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en#sql)                                                                       |
| Funzioni mappatore XDM e preparazione dati (streaming e batch)     | Mappatura gli attributi di origine in formato CSV o JSON in attributi XDM durante l’acquisizione di Experienci Platform.<br>funzioni di calcolo sui dati durante l’acquisizione; ovvero formattazione dei dati, suddivisione, concatenazione e così via.<br>[Documentazione](https://experienceleague.adobe.com/docs/experience-platform/data-prep/home.html?lang=en) |

## Post di blog correlati

* [[!DNL Leveraging External Data Platforms in Adobe Experience Platform Journey Orchestration]](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17?source=your_stories_page-------------------------------------)
* [[!DNL High Throughput Ingestion with Iceberg]](https://medium.com/adobetech/high-throughput-ingestion-with-iceberg-ccf7877a413f?source=your_stories_page-------------------------------------)
* [[!DNL Query Service Tricks in Adobe Experience Platform (Writing Queries and Storing Derived Datasets)]](https://medium.com/adobetech/query-service-tricks-in-adobe-experience-platform-writing-queries-and-storing-derived-datasets-eaee0d6d683e?source=your_stories_page-------------------------------------)
* [[!DNL Digging into Adobe Experience Platform’s Experience Data Model to More Fully Understand the Power of Real-time Customer Profile]](https://medium.com/adobetech/digging-into-adobe-experience-platforms-experience-data-model-to-more-fully-understand-the-power-3e109271e04f?source=your_stories_page-------------------------------------)
* [[!DNL An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a?source=your_stories_page-------------------------------------)
* [[!DNL Modeling XDM Data for Data Science at Scale on Adobe Experience Platform]](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7?source=your_stories_page-------------------------------------)
