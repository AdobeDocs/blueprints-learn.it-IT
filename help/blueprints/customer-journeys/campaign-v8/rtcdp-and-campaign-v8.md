---
title: Modello di integrazione per Real-Time CDP con Adobe Campaign v8
description: Mostra come utilizzare Adobe Experience Platform, il profilo cliente in tempo reale e lo strumento di segmentazione centralizzata con Adobe Campaign v8, per fornire conversazioni personalizzate.
solution: Real-Time Customer Data Platform, Campaign
exl-id: d0291088-02ed-4e7e-b538-018ea40e38c6
TQID: https://experienceleague.adobe.com/LANKBKui1B5RfyNI8ufsgjrC98TXpAf74IB-alwDTnk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: a99add31cc9f485db119ca00426798545e6a7316
workflow-type: tm+mt
source-wordcount: 264
ht-degree: 76%

---

# [!DNL Real-Time CDP] con modello di integrazione di Adobe [!DNL Campaign] v8

Mostra come Adobe [!DNL Experience Platform], il suo Real-Time Customer Profile e lo strumento di segmentazione centralizzata possono essere utilizzati con Adobe Campaign per fornire conversazioni personalizzate.

## Applicazioni

* Adobe [!DNL Experience Platform Real-Time CDP]
* Adobe [!DNL Campaign] v8

## Architettura

<img src="images/rtcdp-campaign-v8-architecture.svg" alt="Architettura di riferimento del blueprint per il modello di integrazione di messaggistica batch e Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Prerequisiti

* Provisioning del cliente per Experience Cloud con un’organizzazione IMS valida
* Si consiglia di eseguire il provisioning di Adobe Experience Platform e [!DNL Campaign] nella stessa organizzazione IMS per un singolo URL di accesso
* È necessario eseguire il provisioning del cliente per l&#39;istanza V8 di [!DNL Campaign]
* Il cliente deve essere idoneo e deve avere accesso a RTCDP, alle origini e alle destinazioni.
* Il contesto di prodotto di Adobe [!DNL Campaign] deve esistere

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
