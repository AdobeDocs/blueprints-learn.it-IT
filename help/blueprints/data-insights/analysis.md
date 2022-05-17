---
title: Blueprint per analisi e intelligence dei dati
description: Questo blueprint dimostra la capacità di Adobe Experience Platform di eseguire query esplorative e analisi dei dati presenti nel data lake.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: a972ea56-d1c8-45da-9044-ed31222a2441
source-git-commit: 011f5b247ccd606348b4cbb4210218f28eddbd4c
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 82%

---

# Blueprint per analisi e intelligence dei dati

Il blueprint per analisi e intelligence dei dati comprende la capacità di Adobe Experience Platform di eseguire query esplorative e analisi dei dati presenti nel data lake.

Experience Platform [!UICONTROL Query Service] consente di eseguire query SQL sui dati.

Experience Platform consente le connessioni con client SQL di terze parti, interfacce e strumenti di Business Intelligence (BI) per connettersi direttamente ai dati, accedere ai dati ed eseguire query all&#39;interno di Experience Platform, utilizzando [!DNL PostgreSQL] protocollo.

Alcune protezioni si applicano al timeout della query e alla quantità di dati inclusi nel risultato della query, come indicato nella sezione guardrail di seguito.

## Casi di utilizzo

* Query interattiva e aggregazione dei dati
* Accesso per righe e colonne ai dati acquisiti per l’esplorazione e la convalida
* Creazione di dashboard e visualizzazione dei dati tramite strumenti di Business Intelligence

## Applicazioni

* Adobe Experience Platform  

## Architettura

<img src="assets/data_exploration.svg" alt="Architettura di riferimento per il blueprint per esplorazione e reporting dei dati aziendali" style="width:90%; border:1px solid #4a4a4a" />

## Guardrail

Per informazioni su best practice e guardrail, consulta la documentazione di Query Service.
[Guida a Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/best-practices/writing-queries.html?lang=it#best-practices)

## Fasi di implementazione

1. [Creare schemi](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) per i dati da acquisire.
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) per i dati da acquisire.
1. [Inserire i dati](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=it) in Experience Platform.
1. Verificare che i dati siano disponibili per [[!UICONTROL Query Service]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/queries/explore-data.html?lang=it) e [[!UICONTROL Data Science Workspace]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/load-data-in-jupyterlab-notebooks.html?lang=it) per accesso e query raw.
1. [Collegare gli strumenti di Business Intelligence e i client SQL a [!UICONTROL Query Service]](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.qsvc.dash) per la visualizzazione, l’interrogazione e l’esplorazione dei dati.

## Documentazione correlata

* [Descrizione del prodotto Adobe Experience Platform Intelligence](https://helpx.adobe.com/it/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* Documentazione di [[!UICONTROL Query Service]](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=it)
