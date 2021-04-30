---
title: Blueprint di analisi dei dati e intelligenza
description: Questo blueprint dimostra la capacità di Adobe Experience Platform di eseguire query esplorative e analisi dei dati presenti nel data lake.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: 3b22dfdd-3fbe-40b3-b798-1ee983723039,a972ea56-d1c8-45da-9044-ed31222a2441
translation-type: tm+mt
source-git-commit: 9e0954334e8b8a8c5bf52651611e7afa165f6d21
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 44%

---

# Blueprint di analisi dei dati e intelligenza

L’analisi e l’intelligenza dei dati comprende la possibilità all’interno di Adobe Experience Platform di eseguire query esplorative e analisi dei dati esistenti nel data lake.

Il Experience Platform [!UICONTROL Query Service] consente l&#39;esecuzione di query SQL sui dati. [!UICONTROL Data Science ] Workspaceconsente l’esplorazione dei dati, la scienza dei dati e i carichi di lavoro di apprendimento automatico da eseguire sui dati.

Inoltre, Experience Platform consente connessioni con client SQL di terze parti, interfacce e strumenti di Business Intelligence (BI) per connettersi, accedere ed eseguire query dirette ai dati all&#39;interno di Experience Platform, utilizzando il protocollo [!DNL PostgreSQL].

Alcune protezioni si applicano al timeout della query e alla quantità di dati inclusi nel risultato della query, come indicato nei dettagli della blueprint.

## Casi di utilizzo

* Query interattiva e aggregazione dei dati
* Accesso per righe e colonne ai dati acquisiti per l’esplorazione e la convalida
* Creazione di dashboard e visualizzazione dei dati tramite strumenti di Business Intelligence

## Applicazioni

* Adobe Experience Platform

## Architettura

<img src="assets/data_exploration.svg" alt="Architettura di riferimento per il blueprint per esplorazione e reporting dei dati aziendali" style="border:1px solid #4a4a4a" />

## Guardrail

* Limite di tempo di 10 minuti per le query interattive
* Limite di 100 record restituiti nell’interfaccia utente
* Limite di 50.000 record restituiti tramite SQL Connector

## Fasi di implementazione

1. Configurare gli insiemi di dati e gli schemi per l’acquisizione dei dati nel data lake.
1. Acquisire i dati.
1. Conferma che i dati siano disponibili per [!UICONTROL Query Service] e [!UICONTROL Data Science Workspace] per l&#39;accesso e la query non elaborati.
1. Connetti gli strumenti di Business Intelligence e i client SQL a [!UICONTROL Query Service] per visualizzazione, query dei dati e esplorazione.

## Documentazione correlata

* [Descrizione del prodotto Adobe Experience Platform Intelligence](https://helpx.adobe.com/it/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Documentazione di Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=it)
