---
title: Blueprint per personalizzazione Data Science per l’arricchimento del profilo
description: Questo blueprint mostra come Data Science Workspace di Adobe Experience Platform può utilizzare i dati all’interno di Experience Platform per addestrare, distribuire e valutare modelli per ottenere dai dati informazioni basate sull’apprendimento automatico.
solution: Experience Platform,Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: f323d2deee5547abd0ccc8247a23ac7a144b2f07
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 97%

---

# Blueprint per personalizzazione Data Science per l’arricchimento del profilo

Il blueprint per la personalizzazione Data Science per l’arricchimento del profilo illustra come i dati in Adobe Experience Platform possono essere utilizzati in [!UICONTROL Data Science Workspace] per addestrare, implementare e valutare modelli che forniscono informazioni approfondite basate sull’apprendimento automatico. Questi modelli possono essere inviati direttamente a un set di dati abilitato per [!UICONTROL Real-time Customer Profile] per arricchire ulteriormente i profili dei clienti. Le informazioni approfondite possono quindi essere utilizzate per la personalizzazione. Esempi di informazioni basate sull’apprendimento automatico includono valutazione del ciclo di vita, affinità per prodotto e categoria, propensione alla conversione o all’abbandono.

## Casi di utilizzo

* Estrarre approfondimenti e individuare gli schemi partendo dai dati dei clienti in Experience Platform Addestrare e valutare i modelli derivati da questi dati
* Arricchire [!UICONTROL Real-time Customer Profile] con elementi di conoscenza e attributi basati su modelli, per una personalizzazione più granulare e una migliore ottimizzazione del percorso
* Addestrare e valutare i modelli per determinare informazioni sui clienti, come valore del ciclo di vita del cliente, propensione alla conversione o all’abbandono, affinità per prodotti e contenuti e valutazione del coinvolgimento

## Architettura

<img src="assets/data_science.svg" alt="Architettura di riferimento per il blueprint per la personalizzazione Data Science per l’arricchimento del profilo" style="width:80%; border:1px solid #4a4a4a" />

## Fasi di implementazione

1. [Creare schemi](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) per i dati da acquisire.
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) per i dati da acquisire.
1. [Inserire i dati](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=it) in Experience Platform.
1. [Creare un notebook DSW](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/load-data-in-jupyterlab-notebooks.html?lang=it).
1. Scegliere un linguaggio. Sono supportati Python e PySpark.
1. [Creare il modello](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/recipe-builder-template.html?lang=it) nel notebook.
1. [Addestrare il modello](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/schedule-training-scoring.html?lang=it).
1. [Valutare il modello](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/schedule-training-scoring.html?lang=en) per generare previsioni con i dati di destinazione.
1. [Attivare il set di dati dei risultati del modello per il profilo se si devono trasferire in [!UICONTROL Real-time Customer Profile]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/dsw-profile-segmentation.html?lang=it).

## Documentazione correlata

* [Descrizione del prodotto Adobe Experience Platform Intelligence](https://helpx.adobe.com/it/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* Documentazione di [[!UICONTROL Data Science Workspace]](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=it)
* Tutorial su [[!UICONTROL Data Science Workspace]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/understanding-data-science-workspace.html?lang=it)

## Articoli di blog correlati

* [[!DNL Simplifying the Data Science Lifecycle with Adobe Platform Experience]](https://medium.com/adobetech/simplifying-the-data-science-lifecycle-with-adobe-platform-experience-8ea4f056d82f)
* [[!DNL Content and Commerce AI: Personalizing Your Interactions with Customers Through Content Intelligence]](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [[!DNL Gaining a Deeper Understanding of Churn Using Data Science Workspace]](https://medium.com/adobetech/gaining-a-deeper-understanding-of-churn-using-data-science-workspace-18a2190e0cf3)
* [[!DNL Understanding Data Science In Adobe Experience Platform]](https://medium.com/adobetech/understanding-data-science-in-adobe-experience-platform-5bce5a17b42)
* [[!DNL An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [[!DNL Modeling XDM Data for Data Science at Scale on Adobe Experience Platform]](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7)
* [[!DNL Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)
* [[!DNL Reimagining Jupyter Notebooks for Enterprise Scale]](https://medium.com/adobetech/reimagining-jupyter-notebooks-for-enterprise-scale-8bc6340d504a)
* [[!DNL Accelerate Intelligent Insights with Adobe Experience Platform Data Science Workspace]](https://medium.com/adobetech/accelerate-intelligent-insights-with-adobe-experience-platform-data-science-workspace-89538bacbbea)
* [[!DNL A Preview of Time Series Forecasting with Adobe Experience Platform]](https://medium.com/adobetech/preview-of-time-series-forecasting-with-adobe-experience-platform-38a2fc778e89)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
