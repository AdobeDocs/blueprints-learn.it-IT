---
title: Modello di integrazione Real-Time CDP con Adobe Campaign v8
description: Mostra come Adobe Experience Platform e il suo Profilo cliente in tempo reale e lo strumento di segmentazione centralizzata possono essere utilizzati con Adobe Campaign v8 per fornire conversazioni personalizzate.
solution: Real-time Customer Data Platform, Campaign
source-git-commit: f8116387105cf1fe0adfc148562529d62ca90cfc
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 45%

---

# Modello di integrazione Real-Time CDP con Adobe Campaign v8

Mostra come utilizzare Adobe Experience Platform, il profilo cliente in tempo reale e lo strumento di segmentazione centralizzata con Adobe Campaign, per fornire conversazioni personalizzate.

<br>

## Applicazioni

* Adobe Experience Platform Real-Time CDP
* Adobe Campaign v8

<br>

## Architettura

<img src="assets/rtcdp-campaignv8-architecture.svg" alt="Architettura di riferimento del blueprint per il modello di integrazione di messaggistica batch e Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Prerequisiti

* Provisioning del cliente per Experience Cloud con un’organizzazione IMS valida
* Si consiglia di effettuare il provisioning di Adobe Experience Platform e Campaign nella stessa organizzazione IMS per l’URL di accesso singolo
* Il cliente deve essere predisposto per l’istanza V8 di Campaign
* Il cliente deve essere idoneo e avere accesso a RTCDP, Origini, Destinazioni.
* Il contesto del prodotto Adobe Campaign deve esistere

<br>

## Fasi di implementazione

Consulta la seguente documentazione sulla configurazione del connettore sorgente Campaign v8 su Adobe Experience Platform e del connettore di destinazione Real-time Customer Data Platform su Campaign v8.
[Connettori Campaign e AEP](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/ac-aep.html?lang=en)

## Guardrail

### Adobe Campaign

* Consulta la documentazione del connettore sorgente Campaign - [Connettore origine campagna](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/adobe-applications/campaign.html?lang=en)
* Supporta solo le implementazioni di Adobe Campaign per singole unità organizzative
* Adobe Campaign è la singola origine per tutti i profili attivi: i profili devono quindi esistere in Adobe Campaign e non dovrebbero essere creati nuovi profili in base ai segmenti di Experience Platform.


### Experience Platform di condivisione dei segmenti Real-time Customer Data Platform

* Fai riferimento al connettore di destinazione della campagna RTCDP - [Connessione campagna RTCDP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html)
* Si consiglia un limite di 50 segmenti
* Tieni presente che la realizzazione dell’appartenenza al segmento da AEP è latente sia per il batch (1 al giorno) che per lo streaming (~5 min) e in base al programma di valutazione del segmento.
* La latenza di attivazione è di almeno 3 ore
* Sono disponibili per l’attivazione solo gli attributi dello schema di unione (nessun supporto per array/mappe/eventi esperienza)
* Si raccomanda di non superare i 20 attributi per segmento
* Un file per segmento di tutti i profili con stato di appartenenza “realized” OPPURE, se la partecipazione al segmento viene aggiunta al file come attributo, sia i profili “realized” che “exited”
* Sono supportate le esportazioni incrementali o di segmenti completi.
* La crittografia dei file non è supportata.
* Vedi protezioni per l’inserimento di profili e dati per AEP - [Collegamento](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)