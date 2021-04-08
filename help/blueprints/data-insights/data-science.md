---
title: Progettazione dati personalizzata per la blueprint di arricchimento dei profili
description: Questo modello mostra come Adobe Experience Platform Data Science Workspace può utilizzare i dati all’interno di Experience Platform per addestrare, implementare e valutare modelli per fornire informazioni sull’apprendimento automatico provenienti dai dati.
solution: Experience Platform,Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
translation-type: tm+mt
source-git-commit: e9e8473f62fa222e483f7aeed33148433f1ec427
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Progettazione dati personalizzata per la blueprint di arricchimento dei profili

La blueprint di Custom Data Science for Profile Enrichment illustra come i dati in Adobe Experience Platform possono essere utilizzati in Data Science Workspace per addestrare, implementare e valutare modelli per fornire informazioni sull’apprendimento automatico. Questi modelli possono essere inviati direttamente a un set di dati abilitato per Profilo cliente in tempo reale per arricchire ulteriormente i profili dei clienti. Queste informazioni possono quindi essere utilizzate per la personalizzazione. Esempi di informazioni sull’apprendimento automatico includono il punteggio del valore del ciclo di vita, l’affinità tra prodotti e categorie, la propensione alla conversione o la propensione all’abbandono.

## Casi d&#39;uso

* Estrarre informazioni approfondite e individuare i pattern dai dati dei clienti in Experience Platform. Treni e modelli di punteggio da questi dati.
* Arricchisci il Profilo del cliente in tempo reale con approfondimenti e attributi basati su modelli per una personalizzazione più granulare e percorsi ottimizzati.
* Modelli di formazione e punteggio per determinare le informazioni sui clienti, ad esempio il valore del ciclo di vita del cliente, la propensione alla conversione o al abbandono, le affinità di prodotti e contenuti e i punteggi di coinvolgimento.

## Architettura

<img src="assets/datascience.svg" alt="Architettura di riferimento per la blueprint di personalizzazione dei dati per l’arricchimento dei profili" style="border:1px solid #4a4a4a" />

## Passaggi di implementazione

1. Creare schemi e set di dati.
1. Inserire dati in Experience Platform.
1. Creare un blocco appunti DSW.
1. Scegli una lingua. Sono supportati Python e PySpark.
1. Modello di authoring nel blocco appunti.
1. Addestra il modello.
1. Puntare il modello per generare previsioni con i dati di destinazione.
1. Abilita il set di dati dei risultati del modello per il profilo, se invii i risultati del modello al Profilo del cliente in tempo reale.

## Documentazione correlata

* [Descrizione del prodotto Adobe Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Documentazione di Data Science Workspace](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=en)
* [Tutorial su Data Science Workspace](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/understanding-data-science-workspace.html)

## Post di blog correlati

* [Semplificazione del ciclo di vita della scienza dei dati con l’esperienza della piattaforma Adobe](https://medium.com/adobetech/simplifying-the-data-science-lifecycle-with-adobe-platform-experience-8ea4f056d82f)
* [Content and Commerce AI: Personalizzazione delle interazioni con i clienti tramite Content Intelligence](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [Informazioni più approfondite sulla coorte con Data Science Workspace](https://medium.com/adobetech/gaining-a-deeper-understanding-of-churn-using-data-science-workspace-18a2190e0cf3)
* [Informazioni su Data Science in Adobe Experience Platform](https://medium.com/adobetech/understanding-data-science-in-adobe-experience-platform-5bce5a17b42)
* [Uno sguardo introduttivo all&#39;analisi esplorativa dei dati su Adobe Experience Platform](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [Taglio dei prodotti Adobe Experience con l&#39;apprendimento automatico per migliorare l&#39;esperienza degli utenti](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [Modellazione di dati XDM per Data Science su scala su Adobe Experience Platform](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7)
* [Segmentation.AI: Funzionalità di clustering automatizzato dell&#39;audience in Adobe Experience Platform](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)
* [Reimmaginazione dei notebook Jupyter per Enterprise Scale](https://medium.com/adobetech/reimagining-jupyter-notebooks-for-enterprise-scale-8bc6340d504a)
* [Accelerare gli approfondimenti intelligenti con Adobe Experience Platform Data Science Workspace](https://medium.com/adobetech/accelerate-intelligent-insights-with-adobe-experience-platform-data-science-workspace-89538bacbbea)
* [Anteprima delle previsioni delle serie temporali con Adobe Experience Platform](https://medium.com/adobetech/preview-of-time-series-forecasting-with-adobe-experience-platform-38a2fc778e89)
* [Taglio dei prodotti Adobe Experience con l&#39;apprendimento automatico per migliorare l&#39;esperienza degli utenti](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
