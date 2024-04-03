---
title: Blueprint per analisi e intelligence dei dati
description: Utilizza Adobe [!DNL Experience Platform] (AEM) per eseguire query esplorative e analisi dei dati presenti nel data lake.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: a972ea56-d1c8-45da-9044-ed31222a2441
source-git-commit: 7f3bc307f74aa88a7a73f3e50cc48bd16f58b37f
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 59%

---

# Blueprint per analisi dei dati e intelligence

L&#39;analisi dei dati e l&#39;intelligence comprendono la capacità [!DNL Experience Platform] per eseguire query esplorative e analisi dei dati presenti nel data lake.

[!DNL Experience Platform]di [!UICONTROL Servizio query] consente di eseguire query SQL sui dati.

[!DNL Experience Platform] consente connessioni con client SQL di terze parti, interfacce e strumenti di Business Intelligence (BI) per connettersi, accedere ed eseguire query dirette sui dati all&#39;interno di [!DNL Experience Platform], utilizzando [!DNL PostgreSQL] protocollo.

## Casi di utilizzo

* Query interattiva e aggregazione dei dati
* Accesso per righe e colonne ai dati acquisiti per l’esplorazione e la convalida
* Creazione di dashboard e visualizzazione dei dati tramite strumenti di Business Intelligence

Per ulteriori casi d’uso comuni per Query Service, consulta [Casi d’uso per Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/use-cases/abandoned-browse.html?lang=it).

## Applicazioni

* Adobe [!DNL Experience Platform]

## Architettura

<img src="assets/data_exploration.svg" alt="Architettura di riferimento per il blueprint per esplorazione e reporting dei dati aziendali" style="width:90%; border:1px solid #4a4a4a" />

## Guardrail

Per informazioni su best practice e guardrail, consulta la documentazione di Query Service.
[Guida a Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=it)

## Fasi di implementazione

1. [Creare schemi](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=it) per i dati da acquisire.
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) per i dati da acquisire.
1. [Acquisire dati](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=it) in [!DNL Experience Platform].
1. Confermare che i dati siano disponibili per [[!UICONTROL Query Service]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/queries/explore-data.html?lang=it).
1. [Collegare gli strumenti di Business Intelligence e i client SQL a [!UICONTROL Query Service]](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=it) per la visualizzazione, l’interrogazione e l’esplorazione dei dati.

## Documentazione correlata

* [Adobe [!DNL Experience Platform] Descrizione del prodotto Intelligence](https://helpx.adobe.com/it/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* Documentazione di [[!UICONTROL Query Service]](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=it)
