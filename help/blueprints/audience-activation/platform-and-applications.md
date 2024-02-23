---
title: Blueprint per l’attivazione in base a pubblico e profili con le applicazioni Experience Cloud
description: Gestisci profili e pubblico in Experience Platform e condividili con le applicazioni Experience Cloud.
solution: Real-Time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services
kt: 7722
exl-id: f36014e8-170d-47e1-b4ec-10c0ea70612d
source-git-commit: 2dab717d638bdbc0a903861ec743a81f2aed986d
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 97%

---

# Blueprint per l’attivazione in base a pubblico e profili con le applicazioni Experience Cloud

Gestisci profili e pubblico in Experience Platform e condividili con le applicazioni Experience Cloud. Crea e condividi segmenti e approfondimenti sui clienti in Experience Platform, e condividili con le applicazioni Experience Cloud.

L’attivazione con applicazioni Experience Cloud è allineata al [blueprint per l’attivazione dei clienti noti](known.md).

## Casi di utilizzo

* Personalizzazione e targeting attraverso i canali di interazione con il cliente basati su Experience Cloud
* Condivisione dei dati di pubblico e profilo tra Experience Platform e le applicazioni Experience Cloud
* Creazione di informazioni approfondite da dati multicanale, inclusi i dati sul comportamento online e i modelli di data science, per arricchire il profilo cliente in tempo reale in Experience Platform, che può quindi essere condiviso con le applicazioni Experience Cloud.

## Applicazioni

* Adobe Experience Platform
* [!UICONTROL Real-time Customer Data Platform]
* Experience Platform Activation
* Applicazioni Experience Cloud
   * Adobe Audience Manager
   * Adobe Target
   * Adobe Campaign
   * Journey Optimizer
   * Marketo Engage
   * Adobe Commerce
   * Customer Journey Analytics

## Architettura

Nella sezione sull’[architettura di Experience Platform e relative applicazioni](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-applications.html?lang=it) trovi ulteriori diagrammi relativi alle integrazioni di Experience Platform con le applicazioni Experience Cloud.

### Attivazione in base a pubblico e profili con le applicazioni Experience Cloud

<img src="../experience-platform/assets/aep+apps.svg" alt="Architettura di riferimento per l’attivazione in base a pubblico e profili con le applicazioni Experience Cloud" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />
<br>

## Guardrail

Consulta la sezione [protezioni nella pagina Panoramica di Audience e Profile Activation](overview.md) e [guardrail di distribuzione](../experience-platform/deployment/guardrails.md) pagina.

## Considerazioni sull’implementazione

* Per condividere i dati del profilo con le destinazioni, è necessario includere il valore di identità specifico utilizzato dalla destinazione nel payload. Tutte le identità necessarie per una destinazione target devono essere inserite in Platform e configurate come identità per il [!UICONTROL profilo cliente in tempo reale].

### Condivisione del pubblico da Real-time Customer Data Platform a Audience Manager

* Per ulteriori informazioni, consulta la documentazione seguente. [Condivisione dei segmenti Experience Platform con Audience Manager e altre soluzioni Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=it).

* L’appartenenza a un pubblico viene condivisa direttamente da RTCDP a Audience Manager non appena la valutazione del segmento, in batch o in streaming, viene completata e inserita nel profilo cliente in tempo reale.
* Se il profilo qualificato contiene informazioni di indirizzamento regionali per i dispositivi del profilo, l’appartenenza al pubblico da RTCDP viene qualificata in modalità streaming nella relativa rete Edge di Audience Manager. Se le informazioni di indirizzamento regionali sono state applicate a un profilo con una marca temporale negli ultimi 14 giorni, verranno valutate in streaming nella rete Edge di Audience Manager. Se i profili RTCDP non contengono informazioni di indirizzamento regionali o se queste risalgono a oltre 14 giorni prima, le appartenenze al pubblico da RTCDP vengono inviate alla posizione dell’hub di Audience Manager per la valutazione e l’attivazione basate su batch.
* In presenza di informazioni di indirizzamento regionali, i profili sono idonei per l’attivazione Edge e vengono attivati entro pochi minuti dalla qualifica del segmento in RTCDP. I profili non qualificati per l’attivazione Edge vengono gestiti nell’hub di Audience Manager e l’elaborazione può richiedere 12-24 ore.
* Le informazioni di indirizzamento regionali sulla cui rete Edge è memorizzato il profilo di Audience Manager possono essere raccolte in Experience Platform da Audience Manager, Visitor ID Service, Analytics, Launch o direttamente dal Web SDK come set di dati distinto per la classe dei record di profilo, utilizzando il gruppo di campi XDM “data capture region information”. Per ulteriori informazioni, consulta il [documento su come ottenere informazioni regionali](https://experienceleague.adobe.com/docs/id-service/using/reference/regions.html?lang=it).
* Per le situazioni di attivazione in cui i tipi di pubblico sono condivisi da Experience Platform a Audience Manager, le seguenti identità vengono condivise automaticamente: ECID, IDFA, GAID, indirizzi e-mail con hashing (EMAIL_LC_SHA256), AdCloud ID. Al momento, gli spazi dei nomi personalizzati non vengono condivisi.
* Il pubblico di Experience Platform può essere condiviso tramite le destinazioni di Audience Manager se le identità di destinazione richieste sono incluse nel [!UICONTROL profilo cliente in tempo reale], oppure nel caso in cui le identità nel [!UICONTROL profilo cliente in tempo reale] possono essere correlate alle identità di destinazione richieste collegate in Audience Manager.

### Condivisione del pubblico da Real-time Customer Data Platform a Target

* Nel [blueprint Personalizzazione per clienti noti - Target e RTCDP](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/web-personalization/known-personalization.html) trovi ulteriori dettagli sulla condivisione di profili e pubblico da Real-time Customer Data Platform a Target.

### Condivisione del pubblico da Real-time Customer Data Platform a Campaign e Journey Optimizer

* Nei [blueprint per customer journey](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=it) trovi ulteriori dettagli sulla condivisione di profili e pubblico da Real-time Customer Data Platform a Campaign e Journey Optimizer.

### Condivisione del pubblico da Real-time Customer Data Platform a Marketo Engage

* Per ulteriori informazioni sulla condivisione di profili e pubblico da Real-time Customer Data Platform a Marketo Engage, consulta il [blueprint per l’attivazione B2B](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=it).

### Condivisione del pubblico da Real-time Customer Data Platform a Customer Journey Analytics

* Per ulteriori informazioni sulla condivisione del pubblico da Real-time Customer Data Platform a Customer Journey Analytics, consulta [Tipi di pubblico RTCDP condivisi con il Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/ingest-aep-segments.html?lang=it).

## Documentazione correlata

* Descrizione del prodotto [[!UICONTROL Real-time Customer Data Platform]](https://helpx.adobe.com/it/legal/product-descriptions/real-time-customer-data-platform.html)
* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)
* [Documentazione sulla segmentazione](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it)
* [Documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=it)

## Video e tutorial correlati

* Panoramica di [[!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=it)
* [Demo di [!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=it)
* [Creare segmenti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=it)
