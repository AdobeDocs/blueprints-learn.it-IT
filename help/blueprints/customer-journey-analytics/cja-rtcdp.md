---
title: Blueprint per Customer Journey Analytics con Real-time Customer Data Platform  l’acquisizione e la creazione
description: Unifica e analizza dati e comportamenti dei clienti da tutto il percorso del cliente in Customer Journey Analytics, e pubblica i tipi di pubblico da CJA a RTCDP
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 9e1ba723-63f2-4622-ba67-f2a315c3ba0c
source-git-commit: 2d7d2fff6c430b66e4a2935d4c68b5a8b9ecfae2
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 98%

---

# Blueprint per Customer Journey Analytics con Real-time Customer Data Platform  l’acquisizione e la creazione 

Crea e pubblica i tipi di pubblico identificati da Customer Journey Analytics (CJA) nel profilo cliente in tempo reale in Adobe Experience Platform, per eseguire attività di targeting dei clienti e personalizzazione. Questa soluzione è ideale per creare tipi di pubblico sulla base di dati storici, nonché tipi di pubblico più mirati con filtri granulari e campi calcolati in Customer Journey Analytics.

## Guida alla pubblicazione dei tipi di pubblico in Customer Journey Analytics

Consulta la seguente documentazione per informazioni su come implementare e configurare la pubblicazione dei tipi di pubblico da Customer Journey Analytics a Real-time Customer Data Platform. [Documentazione](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=it)

## Architettura per i blueprint per Customer Journey Analytics

![Diagramma dell’architettura](assets/CJA.svg){zoomable=&quot;yes&quot;}

## Diagramma dei guardrail per i blueprint per Customer Journey Analytics

* Per informazioni dettagliate sui guardrail e le latenze end-to-end, consulta il [documento sui guardrail relativi all’implementazione](../experience-platform/deployment/guardrails.md).

![Diagramma dei guardrail](../experience-platform/assets/CJA_guardrails.svg){zoomable=&quot;yes&quot;}

## Domande frequenti

* Se in RTCDP non esiste un profilo corrispondente inviato da CJA, verrà creato un nuovo profilo oppure i tipi di pubblico vengono registrati da CJA solo per i profili già presenti? Sì, verrà creato un nuovo profilo. Di conseguenza, se l’implementazione RTCDP è solo per i clienti noti, le regole del pubblico CJA dovrebbero essere scritte in modo da filtrare solo i profili con identità note. Si evita così, se necessario, che il conteggio dei profili RTCDP venga incrementato dai profili anonimi.

* CJA invia i dati del pubblico come eventi della pipeline oppure come semplice file che va anche al data lake? I tipi di pubblico CJA vengono inviati in streaming al servizio Profilo di RTCDP; inoltre, i dati vengono anche memorizzati nel data lake come set di dati.

* Quali identità vengono inviate da CJA? CJA invia tutte le identità che sono state configurate come “ID persona” durante la configurazione di CJA.

* Cosa viene impostato come identità principale? Viene impostata l’identità selezionata dall’utente come ID di “persona” al momento della configurazione di CJA.

* I messaggi di CJA vengono elaborati anche dal servizio Identity? Ad esempio, CJA è in grado di aggiungere identità a un grafo di identità profilo tramite la condivisione del pubblico? No, il servizio Identity non elabora i messaggi di CJA.

## Articoli di blog correlati

* [[!DNL Blueprint for Multi-Channel Orchestration in Adobe Experience Platform]](https://medium.com/adobetech/blueprint-for-multi-channel-orchestration-in-adobe-experience-platform-c68317e94184)
* [[!DNL Leveraging External Data Platforms in Adobe Experience Platform Journey Orchestration]](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17)
* [[!DNL Event-Based Triggering on Adobe Experience Platform Orchestration Service using Apache Airflow]](https://medium.com/adobetech/event-based-triggering-on-adobe-experience-platform-orchestration-service-using-apache-airflow-8607b28251f1)
* [[!DNL Adobe Campaign Classic Integration with Journey Orchestration]](https://medium.com/adobetech/adobe-campaign-classic-integration-with-journey-orchestration-ae577653281)
* [[!DNL Demonstrating the Power of Adobe's New Journey Orchestration Service to Build Personalized Omnichannel Experiences in Real-Time]](https://medium.com/adobetech/demonstrating-the-power-of-adobes-new-journey-orchestration-service-to-build-personalized-aa60d88cd34)
* [[!DNL Journey Orchestration in an Omnichannel World]](https://medium.com/adobetech/journey-orchestration-in-an-omnichannel-world-3a2d32d556d9)
