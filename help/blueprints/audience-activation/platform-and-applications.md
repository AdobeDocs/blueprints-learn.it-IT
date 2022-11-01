---
title: Blueprint per l’attivazione in base a pubblico e profili con le applicazioni Experience Cloud
description: Gestisci profili e pubblico in Experience Platform e condividili con le applicazioni Experience Cloud.
solution: Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services
kt: 7722
exl-id: f36014e8-170d-47e1-b4ec-10c0ea70612d
source-git-commit: 6f10178e2d8d8877ec254e6ca83d1711fa4a82b0
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 68%

---

# Blueprint per l’attivazione in base a pubblico e profili con le applicazioni Experience Cloud

Gestisci profili e pubblico in Experience Platform e condividili con le applicazioni Experience Cloud. Crea e condividi segmenti e approfondimenti sui clienti in Experience Platform, e condividili con le applicazioni Experience Cloud.

L&#39;attivazione con le applicazioni Experience Cloud è allineata con la [Blueprint di attivazione del cliente noto](known.md).

## Casi di utilizzo

* Personalizzazione e targeting attraverso i canali di interazione con il cliente basati su Experience Cloud
* Condivisione dei dati di pubblico e profilo tra Experience Platform e le applicazioni Experience Cloud
* Crea informazioni approfondite dai dati multicanale, inclusi i dati comportamentali online e i modelli di scienza dei dati, per arricchire il profilo del cliente in tempo reale in Experience Platform, che può quindi essere condiviso con le applicazioni Experience Cloud.

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

<img src="../experience-platform/assets/aep+apps_horizontal.svg" alt="Architettura di riferimento per l’attivazione in base a pubblico e profili con le applicazioni Experience Cloud" style="width:90%; border:1px solid #4a4a4a" />
<br>

## Guardrail

Fai riferimento ai [guardrail nella pagina Panoramica di attivazione in base a pubblico e profili](overview.md) e [guardrail di distribuzione](../experience-platform/deployment/guardrails.md) pagina.

## Considerazioni sull’implementazione

* Per condividere i dati del profilo con le destinazioni, è necessario includere il valore di identità specifico utilizzato dalla destinazione nel payload. Tutte le identità necessarie per una destinazione target devono essere inserite in Platform e configurate come identità per [!UICONTROL Real-time Customer Profile].

### Condivisione del pubblico da Real-time Customer Data Platform a Audience Manager

* Per ulteriori informazioni, consulta la documentazione seguente. [Condivisione dei segmenti Experience Platform con Audience Manager e altre soluzioni Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=it).

* L’appartenenza a un pubblico viene condivisa direttamente da RTCDP a Audience Manager non appena la valutazione del segmento, in batch o in streaming, viene completata e inserita nel profilo cliente in tempo reale.
* Se il profilo qualificato contiene informazioni di indirizzamento regionali per i dispositivi del profilo, l’appartenenza al pubblico da RTCDP viene qualificata in modalità streaming nella relativa rete Edge di Audience Manager. Se le informazioni di indirizzamento regionali sono state applicate a un profilo con una marca temporale negli ultimi 14 giorni, verranno valutate in streaming in Audience Manager Edge. Se i profili di RTCDP non contengono informazioni di indirizzamento regionali o se le informazioni di indirizzamento regionale hanno una durata superiore a 14 giorni, le iscrizioni di pubblico RTCDP vengono inviate alla posizione di hub Audience Manager per la valutazione e l’attivazione basate su batch.
* Con le informazioni di routing regionali questi profili sono idonei per l’attivazione di Edge e verranno attivati entro pochi minuti dalla qualifica del segmento da RTCDP, i profili che non sono qualificati per l’attivazione di Edge si qualificano nell’hub di Audience Manager e possono avere un intervallo di tempo di 12-24 ore per l’elaborazione.
* Le informazioni di indirizzamento regionali sulla cui rete Edge è memorizzato il profilo di Audience Manager possono essere raccolte in Experience Platform da Audience Manager, Visitor ID Service, Analytics, Launch o direttamente dal Web SDK come set di dati distinto per la classe dei record di profilo, utilizzando il gruppo di campi XDM “data capture region information”. Per ulteriori informazioni, consulta il documento per ottenere informazioni regionali . [Collegamento](https://experienceleague.adobe.com/docs/id-service/using/reference/regions.html?lang=en).
* Per le situazioni di attivazione in cui i tipi di pubblico sono condivisi da Experience Platform a Audience Manager, le seguenti identità vengono condivise automaticamente: ECID, IDFA, GAID, indirizzi e-mail con hashing (EMAIL_LC_SHA256), AdCloud ID. Al momento, gli spazi dei nomi personalizzati non vengono condivisi.
* Il pubblico di Experience Platform può essere condiviso tramite le destinazioni di Audience Manager se le identità di destinazione richieste sono incluse nel [!UICONTROL profilo cliente in tempo reale], oppure nel caso in cui le identità nel [!UICONTROL profilo cliente in tempo reale] possono essere correlate alle identità di destinazione richieste collegate in Audience Manager.

### Condivisione del pubblico da Real-time Customer Data Platform a Target

* Nel [blueprint Personalizzazione per clienti noti - Target e RTCDP](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/known-personalization.html?lang=it) trovi ulteriori dettagli sulla condivisione di profili e pubblico da Real-time Customer Data Platform a Target.

### Condivisione del pubblico da Real-time Customer Data Platform a Campaign e Journey Optimizer

* Nei [blueprint per customer journey](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=en) trovi ulteriori dettagli sulla condivisione di profili e pubblico da Real-time Customer Data Platform a Campaign e Journey Optimizer.

### Condivisione del pubblico da Real-time Customer Data Platform a Marketo Engage

* Consulta la sezione [Blueprint di attivazione B2B](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=en) per ulteriori dettagli sulla condivisione di profili e pubblico da Real-time Customer Data Platform a Marketo Engage.

### Condivisione del pubblico da Real-time Customer Data Platform a Customer Journey Analytics

* Consulta la sezione [Tipi di pubblico RTCDP condivisi con il Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/ingest-aep-segments.html?lang=en) per ulteriori dettagli sulla condivisione di tipi di pubblico Real-time Customer Data Platform in Customer Journey Analytics.

## Documentazione correlata

* Descrizione del prodotto [[!UICONTROL Real-time Customer Data Platform]](https://helpx.adobe.com/it/legal/product-descriptions/real-time-customer-data-platform.html)
* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)
* [Documentazione sulla segmentazione](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it)
* [Documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=it)

## Video e tutorial correlati

* Panoramica di [[!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=it)
* [Demo di [!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=it)
* [Creare segmenti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=it)
