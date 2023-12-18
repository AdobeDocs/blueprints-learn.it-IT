---
title: Modello di integrazione per Real-Time CDP con Adobe Campaign v8
description: Mostra come utilizzare Adobe Experience Platform, il profilo cliente in tempo reale e lo strumento di segmentazione centralizzata con Adobe Campaign v8, per fornire conversazioni personalizzate.
solution: Real-Time Customer Data Platform, Campaign
exl-id: d0291088-02ed-4e7e-b538-018ea40e38c6
source-git-commit: 5f9384abe7f29ec764428af33c6dd1f0a43f5a89
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 100%

---

# Modello di integrazione per Real-Time CDP con Adobe Campaign v8

Mostra come utilizzare Adobe Experience Platform, il profilo cliente in tempo reale e lo strumento di segmentazione centralizzata con Adobe Campaign, per fornire conversazioni personalizzate.

<br>

## Applicazioni

* Adobe Experience Platform Real-Time CDP
* Adobe Campaign v8

<br>

## Architettura

<img src="assets/rtcdp-campaignv8-architecture.svg" alt="Architettura di riferimento del blueprint per il modello di integrazione di messaggistica batch e Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Prerequisiti

* Provisioning del cliente per Experience Cloud con un’organizzazione IMS valida
* Si consiglia di effettuare il provisioning di Adobe Experience Platform e Campaign nella stessa organizzazione IMS per un URL di accesso singolo.
* Per il cliente deve essere eseguito il provisioning dell’istanza v8 di Campaign.
* Il cliente deve essere idoneo e deve avere accesso a RTCDP, alle origini e alle destinazioni.
* Deve esistere il contesto del prodotto Adobe Campaign.
<br>

## Fasi di implementazione

Consulta la seguente documentazione su come configurare il connettore di origini di Campaign v8 per Adobe Experience Platform, e il connettore di destinazioni di Real-time Customer Data Platform per Campaign v8.
[Connettori per Campaign e AEP](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/ac-aep.html?lang=it)

## Guardrail

### Adobe Campaign

* Consulta la documentazione del connettore di origini per Campaign - [Connettore origine per Campaign](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/adobe-applications/campaign.html?lang=it)
* Supporta solo le implementazioni di Adobe Campaign per singole unità organizzative


### Condivisione dei segmenti Experience Platform Real-time Customer Data Platform

* Consulta la documentazione sul connettore di destinazioni RTCDP per Campaign - [Connessione di RTCDP per Campaign](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html?lang=it)

* Vedi i guardrail per l’acquisizione di profili e dati per AEP - [Collegamento](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)
