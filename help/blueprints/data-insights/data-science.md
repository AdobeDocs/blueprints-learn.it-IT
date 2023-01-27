---
title: Progettazione dati personalizzata per la blueprint di arricchimento dei profili
description: Questo blueprint mostra come le informazioni basate su Data Science possono essere acquisite in Experience Platform per arricchire il profilo del cliente in tempo reale.
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: b18d491fdefc57762932d1570401b5437bf97c76
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 95%

---

# Progettazione dati personalizzata per la blueprint di arricchimento dei profili

Il blueprint per la personalizzazione basata su Data Science per l’arricchimento del profilo illustra come è possibile utilizzare i dati per addestrare, implementare e valutare modelli al fine di fornire informazioni basate sull’apprendimento automatico in Experience Platform e Real-time Customer Data Platform, mediante strumenti di data science e machine learning. Le informazioni modellate possono essere acquisite in Experience Platform per arricchire il profilo cliente in tempo reale. Esempi di informazioni basate sull’apprendimento automatico includono valutazione del ciclo di vita, affinità per prodotto e categoria, propensione alla conversione o all’abbandono.

## Casi d’uso

* Estrarre informazioni approfondite e individuare eventuali pattern dai dati dei clienti, quindi addestrare e valutare i modelli utilizzando questi dati.
* Arricchire [!UICONTROL Real-time Customer Profile] con elementi di conoscenza e attributi basati su modelli, per una personalizzazione più granulare e una migliore ottimizzazione del percorso
* Addestrare e valutare i modelli per determinare informazioni sui clienti, come valore del ciclo di vita del cliente, propensione alla conversione o all’abbandono, affinità per prodotti e contenuti e valutazione del coinvolgimento

## Architettura

<img src="assets/data_science.svg" alt="Architettura di riferimento per il blueprint per la personalizzazione Data Science per l’arricchimento del profilo" style="width:90%; border:1px solid #4a4a4a" />

## Guardrail

* Per informazioni dettagliate sui guardrail e sulle latenze end-to-end per l’acquisizione dei risultati data science in Experience Platform e nel profilo cliente in tempo reale, vedi i guardrail per l’acquisizione dei dati e il diagramma della latenza riportati nel [documento sui guardrail relativi all’implementazione](../experience-platform/deployment/guardrails.md).

## Passaggi di implementazione

1. [Creare schemi](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=it) per i dati da acquisire.
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) per i dati da acquisire.
1. [Inserire i dati](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=it) in Experience Platform.

Per i risultati del modello da acquisire nel profilo cliente in tempo reale, assicurati di effettuare le seguenti operazioni prima di acquisire i dati:

1. [Configurare correttamente le identità e i relativi spazi dei nomi](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it) nello schema, affinché i dati acquisiti possano essere uniti in un profilo unificato.
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=it).

## Considerazioni sull’implementazione

* Nella maggior parte dei casi i risultati del modello devono essere acquisiti come attributi di profilo, e non come eventi di esperienza. I risultati del modello possono essere semplici stringhe di attributi. Se devi acquisire più risultati del modello, è preferibile utilizzare un campo di tipo mappa o array.
* Il set di dati dello snapshot di profilo giornaliero (esportazione giornaliera dei dati degli attributi del profilo unificato) può essere utilizzato per addestrare i modelli sui dati degli attributi di profilo. La documentazione sui set di dati dello snapshot del profilo è disponibile [qui](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=it#profile-attribute-datasets).
* Per estrarre i dati da Experience Platform, è possibile utilizzare i seguenti metodi.
   * Data Access SDK
      * I dati sono in formato non elaborato.
      * I dati di eventi esperienza di profilo restano nello stato non elaborato e non unificato.
   * Destinazioni RTCDP
      * I dati in uscita possono includere solo attributi di profilo e appartenenze ai segmenti.

## Documentazione correlata

* [Descrizione del prodotto Adobe Experience Platform Intelligence](https://helpx.adobe.com/it/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Adobe Experience Platform Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=it)

## Post di blog correlati

* [[!DNL Content and Commerce AI: Personalizing Your Interactions with Customers Through Content Intelligence]](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [[!DNL An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [[!DNL Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)