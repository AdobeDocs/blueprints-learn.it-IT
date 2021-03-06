---
title: Blueprint per l’attivazione in base a pubblico e profili con le applicazioni Experience Cloud
description: Gestisci profili e pubblico in Experience Platform e condividili con le applicazioni Experience Cloud.
solution: Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services
kt: 7722
exl-id: f36014e8-170d-47e1-b4ec-10c0ea70612d
source-git-commit: 3425495df36ff8da0f2fd737b35d294ccafe31bd
workflow-type: ht
source-wordcount: '741'
ht-degree: 100%

---

# Blueprint per l’attivazione in base a pubblico e profili con le applicazioni Experience Cloud

Gestisci profili e pubblico in Experience Platform e condividili con le applicazioni Experience Cloud. Crea e condividi segmenti e approfondimenti sui clienti in Experience Platform, e condividili con le applicazioni Experience Cloud.

L’attivazione con applicazioni Experience Cloud è strettamente allineata al [blueprint per l’attivazione dei clienti noti](known.md).

## Casi di utilizzo

* Personalizzazione e targeting attraverso i canali di interazione con il cliente basati su Experience Cloud
* Condivisione dei dati di pubblico e profilo tra Experience Platform e le applicazioni Experience Cloud

## Applicazioni

* Adobe Experience Platform
* [!UICONTROL Real-time Customer Data Platform]
* Experience Platform Activation
* Applicazioni Experience Cloud
   * Adobe Audience Manager
   * Adobe Target
   * Adobe Campaign
   * Journey Optimizer

## Architettura

Nella sezione sull’[architettura di Experience Platform e relative applicazioni](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-applications.html?lang=it) trovi ulteriori diagrammi relativi alle integrazioni di Experience Platform con le applicazioni Experience Cloud.

### Attivazione in base a pubblico e profili con le applicazioni Experience Cloud

<img src="../experience-platform/assets/aep+apps_horizontal.svg" alt="Architettura di riferimento per l’attivazione in base a pubblico e profili con le applicazioni Experience Cloud" style="width:90%; border:1px solid #4a4a4a" />
<br>

## Guardrail

Fai riferimento ai [guardrail nella pagina Panoramica di attivazione in base a pubblico e profili](overview.md)

## Considerazioni sull’implementazione

* Per condividere i dati del profilo con le destinazioni, è necessario includere il valore di identità specifico utilizzato dalla destinazione nel payload. Tutte le identità necessarie per una destinazione target devono essere inserite in Platform e configurate come identità per [!UICONTROL Real-time Customer Profile].

### Condivisione del pubblico da Real-time Customer Data Platform a Audience Manager

* Per ulteriori informazioni, consulta la documentazione seguente. [Condivisione dei segmenti Experience Platform con Audience Manager e altre soluzioni Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=it).

* L’appartenenza a un pubblico viene condivisa direttamente da RTCDP a Audience Manager non appena la valutazione del segmento, in batch o in streaming, viene completata e inserita nel profilo cliente in tempo reale. Se il profilo qualificato contiene informazioni di indirizzamento regionali per i dispositivi del profilo, l’appartenenza al pubblico da RTCDP viene qualificata in modalità streaming nella relativa rete Edge di Audience Manager. Se le informazioni di indirizzamento regionali sono state applicate a un profilo con una marca temporale negli ultimi 14 giorni, verranno valutate in streaming nella rete Edge di Audience Manager. Se i profili di RTCDP non contengono informazioni di indirizzamento regionali o se queste risalgono a oltre 14 giorni prima, le appartenenze al profilo vengono inviate alla posizione dell’hub di Audience Manager per la valutazione e l’attivazione basate su batch. I profili idonei per l’attivazione Edge vengono attivati entro pochi minuti dalla qualifica del segmento in RTCDP. I profili non qualificati per l’attivazione Edge vengono gestiti nell’hub di Audience Manager e l’elaborazione può richiedere 12-24 ore.

* Le informazioni di indirizzamento regionali sulla cui rete Edge è memorizzato il profilo di Audience Manager possono essere raccolte in Experience Platform da Audience Manager, Visitor ID Service, Analytics, Launch o direttamente dal Web SDK come set di dati distinto per la classe dei record di profilo, utilizzando il gruppo di campi XDM “data capture region information”.

* Per le situazioni di attivazione in cui i tipi di pubblico sono condivisi da Experience Platform a Audience Manager, le seguenti identità vengono condivise automaticamente: ECID, IDFA, GAID, indirizzi e-mail con hashing (EMAIL_LC_SHA256), AdCloud ID. Al momento, gli spazi dei nomi personalizzati non vengono condivisi.

* Il pubblico di Experience Platform può essere condiviso tramite le destinazioni di Audience Manager se le identità di destinazione richieste sono incluse nel [!UICONTROL profilo cliente in tempo reale], oppure nel caso in cui le identità nel [!UICONTROL profilo cliente in tempo reale] possono essere correlate alle identità di destinazione richieste collegate in Audience Manager.

### Condivisione del pubblico da Real-time Customer Data Platform a Target

* Nel [blueprint per la personalizzazione web e mobile con dati online e offline](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/online-offline.html?lang=it) trovi ulteriori dettagli sulla condivisione di profili e pubblico da Real-time Customer Data Platform a Target.

### Condivisione del pubblico da Real-time Customer Data Platform a Campaign e Journey Optimizer

* Nei [blueprint per customer journey](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/overview.html?lang=it) trovi ulteriori dettagli sulla condivisione di profili e pubblico da Real-time Customer Data Platform a Campaign e Journey Optimizer.

## Documentazione correlata

* Descrizione del prodotto [[!UICONTROL Real-time Customer Data Platform]](https://helpx.adobe.com/it/legal/product-descriptions/real-time-customer-data-platform.html)
* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)
* [Documentazione sulla segmentazione](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it)
* [Documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=it)

## Video e tutorial correlati

* Panoramica di [[!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=it)
* [Demo di [!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=it)
* [Creare segmenti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=it)
