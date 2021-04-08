---
title: Blueprint di analisi dei dati e intelligenza
description: Questo modello mostra la capacità all’interno di Adobe Experience Platform di eseguire query esplorative e analisi dei dati esistenti nel data lake.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: 3b22dfdd-3fbe-40b3-b798-1ee983723039,a972ea56-d1c8-45da-9044-ed31222a2441
translation-type: tm+mt
source-git-commit: cd98c46d948af9026449c947496df82fd1be6718
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Blueprint di analisi dei dati e intelligenza

L’analisi e l’intelligenza dei dati comprende la possibilità all’interno di Adobe Experience Platform di eseguire query esplorative e analisi dei dati esistenti nel data lake.

Il servizio Query di Experience Platform consente l&#39;esecuzione di query SQL sui dati. Data Science Workspace consente l’esplorazione dei dati, la scienza dei dati e i carichi di lavoro di apprendimento automatico da eseguire sui dati.

Inoltre, Experience Platform consente connessioni con client SQL di terze parti, interfacce e strumenti di Business Intelligence (BI) per connettersi, accedere ed eseguire query dirette ai dati all&#39;interno di Experience Platform, utilizzando il protocollo PostgreSQL.

Alcune protezioni si applicano al timeout della query e alla quantità di dati inclusi nel risultato della query, come indicato nei dettagli dello scenario.

## Casi d&#39;uso

* Query interattiva e aggregazione dei dati
* Accesso a righe e colonne per l’esplorazione e la convalida dei dati acquisiti
* Dashboard e visualizzazione dei dati tramite strumenti di Business Intelligence

## Applicazioni

* Adobe Experience Platform

## Architettura

<img src="assets/dataexplore.svg" alt="Architettura di riferimento per la blueprint Enterprise Data Exploration and Reporting (Esplorazione dei dati e reporting)" style="border:1px solid #4a4a4a" />

## Guardrail

* Limite di tempo di 10 minuti per le query interattive
* Limite di 100 record restituito nell&#39;interfaccia utente
* Limite di 50.000 record restituito tramite il connettore SQL

## Passaggi di implementazione

1. Configura set di dati e schemi per l’inserimento dei dati nel data lake.
1. Acquisisci dati.
1. Conferma che i dati siano disponibili per Query Service e Data Science Workspace per l’accesso e la query non elaborati.
1. Collegare gli strumenti di Business Intelligence e i client SQL a Query Service per visualizzazione, query dei dati e esplorazione.

## Documentazione correlata

* [Descrizione del prodotto Adobe Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Documentazione del servizio query](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en)