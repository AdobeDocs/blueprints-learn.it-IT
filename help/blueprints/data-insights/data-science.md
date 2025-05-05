---
title: Blueprint per personalizzazione Data Science per l’arricchimento del profilo
description: Scopri come acquisire in [!DNL Experience Platform] le informazioni basate sulla scienza dei dati per arricchire Real-time Customer Profile.
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 7f3bc307f74aa88a7a73f3e50cc48bd16f58b37f
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 69%

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

* Per i guardrail dettagliati e le latenze end-to-end durante l&#39;acquisizione dei risultati della data science in [!DNL Experience Platform] e nel profilo cliente in tempo reale, fare riferimento ai guardrail di acquisizione dati e al diagramma di latenza a cui si fa riferimento nel [documento sui guardrail di distribuzione](../experience-platform/deployment/guardrails.md).

## Fasi di implementazione

1. [Creare schemi](https://experienceleague.adobe.com/?lang=it&recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=it) per i dati da acquisire.
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) per i dati da acquisire.
1. [Acquisire dati](https://experienceleague.adobe.com/?lang=it&recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=it) in [!DNL Experience Platform].

Per i risultati del modello da acquisire nel profilo cliente in tempo reale, assicurati di effettuare le seguenti operazioni prima di acquisire i dati:

1. [Configurare correttamente le identità e i relativi spazi dei nomi](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it) nello schema, affinché i dati acquisiti possano essere uniti in un profilo unificato.
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=it).

## Considerazioni sull’implementazione

* Nella maggior parte dei casi i risultati del modello devono essere acquisiti come attributi di profilo, e non come eventi di esperienza. I risultati del modello possono essere semplici stringhe di attributi. Se devi acquisire più risultati del modello, è preferibile utilizzare un campo di tipo mappa o array.
* Il set di dati dello snapshot di profilo giornaliero (esportazione giornaliera dei dati degli attributi del profilo unificato) può essere utilizzato per addestrare i modelli sui dati degli attributi di profilo. La documentazione sui set di dati dello snapshot del profilo è disponibile [qui](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=it#profile-attribute-datasets).
* Per estrarre i dati da [!DNL Experience Platform] è possibile utilizzare i seguenti metodi
   * Data Access SDK
      * I dati sono in formato non elaborato.
      * I dati di eventi esperienza di profilo restano nello stato non elaborato e non unificato.
   * Destinazioni RTCDP
      * I dati in uscita possono includere solo attributi di profilo e appartenenze ai segmenti.

## Documentazione correlata

* [Adobe [!DNL Experience Platform] Descrizione del prodotto Intelligence](https://helpx.adobe.com/it/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Adobe [!DNL Experience Platform] Servizio query](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=it)

## Articoli di blog correlati

* [Intelligenza artificiale per contenuti e commerce: personalizzazione delle interazioni con i clienti tramite Content Intelligence](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [Un&#39;analisi introduttiva dei dati esplorativi sull&#39;Adobe [!DNL Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [Apprendimento automatico nei prodotti Adobe Experience per ottimizzare l’esperienza utente](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe [!DNL Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)