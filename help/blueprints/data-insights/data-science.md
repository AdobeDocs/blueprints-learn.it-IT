---
title: Blueprint per personalizzazione Data Science per l’arricchimento del profilo
description: Scopri come acquisire in [!DNL Experience Platform] le informazioni basate sulla scienza dei dati per arricchire Real-time Customer Profile.
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 63%

---

# Blueprint per data science personalizzata per l’arricchimento dei profili

Il blueprint di data science personalizzato per l&#39;arricchimento dei profili illustra come utilizzare i dati per addestrare, distribuire e valutare modelli per fornire informazioni di apprendimento automatico su [!DNL Experience Platform] e [!DNL Real-Time Customer Data Platform] da strumenti di data science e apprendimento automatico.

Le informazioni modellate possono essere acquisite in [!DNL Experience Platform] per arricchire il profilo cliente in tempo reale. Esempi di informazioni basate sull’apprendimento automatico includono valutazione del ciclo di vita, affinità per prodotto e categoria, propensione alla conversione o all’abbandono.

## Casi di utilizzo

* Estrarre informazioni approfondite e individuare eventuali pattern dai dati dei clienti, quindi addestrare e valutare i modelli utilizzando questi dati.
* Arricchire il [!UICONTROL profilo cliente in tempo reale] con elementi di conoscenza e attributi basati su modelli, per una personalizzazione più granulare e una migliore ottimizzazione del percorso
* Addestrare e valutare i modelli per determinare informazioni sui clienti, come valore del ciclo di vita del cliente, propensione alla conversione o all’abbandono, affinità per prodotti e contenuti e valutazione del coinvolgimento

## Architettura

<img src="assets/data_science.svg" alt="Architettura di riferimento per il blueprint per la personalizzazione Data Science per l’arricchimento del profilo" style="width:90%; border:1px solid #4a4a4a" />

## Guardrail

* Per i guardrail dettagliati e le latenze end-to-end durante l&#39;acquisizione dei risultati della data science in [!DNL Experience Platform] e nel profilo cliente in tempo reale, fare riferimento ai guardrail di acquisizione dati e al diagramma di latenza a cui si fa riferimento nel [documento sui guardrail di distribuzione](../experience-platform/guardrails.md).

## Considerazioni sull’implementazione

* Nella maggior parte dei casi i risultati del modello devono essere acquisiti come attributi di profilo, e non come eventi di esperienza. I risultati del modello possono essere semplici stringhe di attributi. Se devi acquisire più risultati del modello, è preferibile utilizzare un campo di tipo mappa o array.
* Il set di dati dello snapshot di profilo giornaliero (esportazione giornaliera dei dati degli attributi del profilo unificato) può essere utilizzato per addestrare i modelli sui dati degli attributi di profilo. La documentazione sui set di dati dello snapshot del profilo è disponibile [qui](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=it#profile-attribute-datasets).

## Documentazione correlata

* [Adobe [!DNL Experience Platform] Descrizione del prodotto Intelligence](https://helpx.adobe.com/it/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Adobe [!DNL Experience Platform] Servizio query](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=it)

## Articoli di blog correlati

* [Intelligenza artificiale per contenuti e commerce: personalizzazione delle interazioni con i clienti tramite Content Intelligence](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [Analisi introduttiva dei dati esplorativi su Adobe [!DNL Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [Apprendimento automatico nei prodotti Adobe Experience per ottimizzare l’esperienza utente](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe [!DNL Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)