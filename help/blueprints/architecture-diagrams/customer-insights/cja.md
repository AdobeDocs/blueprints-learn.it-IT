---
title: Customer Journey Analytics con Real-time Customer Data Platform
description: Unifica e analizza dati e comportamenti dei clienti da tutto il percorso del cliente in Customer Journey Analytics, e pubblica i tipi di pubblico da CJA a RTCDP
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 9e1ba723-63f2-4622-ba67-f2a315c3ba0c
TQID: https://experienceleague.adobe.com/gbNXsco0cQIcn5O83ofB-rb0PF65v7kaTZ7mTngqHks
product_v2:
  - id: e98b7246-966c-4318-9e95-cad2f7a17dc7
    internal-label: Customer Journey Analytics
feature_v2:
  - id: ce577701-5b9e-4fe4-8fa3-4eedea976da4
    internal-label: Components
source-git-commit: ce7331f279a6e59db95ca3b763148440598cde84
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 8%
---

# Adobe Customer Journey Analytics

Adobe Customer Journey Analytics unisce i dati di interazione del cliente provenienti da Adobe Experience Platform e da altre origini in un servizio di analisi basato sul percorso. Questa architettura fornisce i riferimenti di base per l’analisi cross-channel, le derivazioni di CJA B2B e la pubblicazione di tipi di pubblico CJA in Real-Time CDP.

## Architettura Customer Journey Analytics

Questo diagramma mostra il flusso principale di dati di interazione con il cliente in Customer Journey Analytics per connessioni, visualizzazioni dati, analisi e creazione di tipi di pubblico.

![Architettura di base di Adobe Customer Journey Analytics](assets/cja.png){width="1000" zoomable="yes"}

## Derivazioni dell&#39;architettura

- B2B Customer Journey Analytics estende l’architettura di base con dimensioni di account, opportunità, gruppo di acquisto e persona per l’analisi basata su account.
- Con la condivisione del pubblico in CJA vengono pubblicati i tipi di pubblico creati da Customer Journey Analytics a Real-Time CDP per l’attivazione e l’esecuzione del percorso a valle.

## Flussi di dati primari e punti di integrazione

- I dati di interazione del cliente vengono raccolti in Adobe Experience Platform da web, dispositivi mobili, e-commerce, CRM e altre origini.
- I set di dati di Experience Platform vengono selezionati in una connessione Customer Journey Analytics.
- Le visualizzazioni dati espongono metriche, dimensioni e campi calcolati per l’analisi cross-channel.
- I tipi di pubblico di Customer Journey Analytics possono essere pubblicati in Real-Time CDP per l’attivazione.
- Customer Journey Analytics insights può essere utilizzato con Journey Optimizer tramite l’architettura di integrazione dedicata.

## Modelli di casi d’uso supportati

- [Analisi B2B](/help/blueprints/use-case-patterns/b2b/account-analytics.md): analisi di percorsi a livello di account, opportunità e persona con dimensioni B2B.
- [Analisi dei clienti e generazione insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md): analisi del comportamento cross-channel e generazione di informazioni di percorso.

## Ulteriori informazioni

- [Panoramica di Customer Journey Analytics](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-overview/cja-overview)
- [Connessioni Customer Journey Analytics](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-connections/create-connection)
- [Pubblicare tipi di pubblico di Customer Journey Analytics](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/audiences/publish)
