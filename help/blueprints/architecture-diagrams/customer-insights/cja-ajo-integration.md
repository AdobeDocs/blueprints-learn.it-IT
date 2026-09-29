---
title: Integrazione di Adobe Customer Journey Analytics e Adobe Journey Optimizer
description: Architettura per l’analisi delle campagne Adobe Journey Optimizer e delle informazioni sul percorso in Adobe Customer Journey Analytics e la pubblicazione di tipi di pubblico per l’esecuzione del percorso.
solution: Customer Journey Analytics, Journey Optimizer, Experience Platform
product_v2:
  - id: e98b7246-966c-4318-9e95-cad2f7a17dc7
    internal-label: Customer Journey Analytics
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
    internal-label: Journey Optimizer
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%
---
# Integrazione di Adobe Customer Journey Analytics e Adobe Journey Optimizer

Questa architettura mostra il flusso di dati di distribuzione e interazione di Adobe Journey Optimizer da Adobe Experience Platform a Customer Journey Analytics per informazioni su campagne e percorsi. I tipi di pubblico creati in Customer Journey Analytics possono essere pubblicati tramite Real-Time CDP per l’utilizzo nell’esecuzione di Journey Optimizer.

## Architettura di informazioni su campagne e percorsi

L’architettura collega i dati di consegna e interazione di Journey Optimizer con Experience Platform e Customer Journey Analytics per il reporting, l’analisi e la creazione di tipi di pubblico.

![Architettura di integrazione di Adobe Customer Journey Analytics e Adobe Journey Optimizer](assets/cja_ajo_integration.png){width="1000" zoomable="yes"}

## Flussi di dati primari e punti di integrazione

- I dati relativi a consegna, interazione ed efficacia di Journey Optimizer vengono condivisi con i servizi dati di Experience Platform.
- I dati di Experience Platform vengono acquisiti in Customer Journey Analytics tramite una connessione CJA.
- Le visualizzazioni dati e l’analisi di Customer Journey Analytics forniscono insight per campagne e percorsi.
- I tipi di pubblico creati in Customer Journey Analytics vengono pubblicati in Real-Time CDP.
- I tipi di pubblico di Real-Time CDP sono disponibili per l’esecuzione e la personalizzazione del percorso Journey Optimizer.

## Modelli di casi d’uso supportati

- [Analisi dei clienti e generazione insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md): analisi del comportamento di campagne e percorsi tra canali diversi.
- [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md): utilizza i segnali di clienti e percorsi per supportare la messaggistica orchestrata.

## Ulteriori informazioni

- [Reportistica di Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/reports/sharing-overview)
- [Panoramica di Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Pubblicare tipi di pubblico di Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
