---
title: Real-Time CDP con blueprint Adobe Campaign
description: Mostra come Adobe Experience Platform e il suo Profilo cliente in tempo reale e lo strumento di segmentazione centralizzata possono essere utilizzati con Adobe Campaign per fornire conversazioni personalizzate.
solution: Experience Platform, Campaign v8, Campaign Classic v7, Campaign Standard
source-git-commit: 1c46cbdfc395de4fc9139966cf869ba1feeceaaa
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 58%

---

# Real-Time CDP con blueprint Adobe Campaign

Mostra come Adobe Experience Platform e il suo Profilo cliente in tempo reale e lo strumento di segmentazione centralizzata possono essere utilizzati con Adobe Campaign per fornire conversazioni personalizzate.

<br>

## Applicazioni

* Adobe Experience Platform Real-Time CDP
* Adobe Campaign v7 o Campaign Standard

<br>

## Architettura

<img src="assets/rtcdp-campaign-architecture.svg" alt="Architettura di riferimento per il blueprint per messaggistica batch e Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Prerequisiti

* Si consiglia di effettuare il provisioning di Experience Platform e Campaign nella stessa organizzazione IMS e di utilizzare Adobe Admin Console per l’accesso degli utenti. In questo modo i clienti possono utilizzare lo switcher della soluzione direttamente dall&#39;interfaccia utente di marketing

<br>

## Guardrail

### Adobe Campaign

* Supporta solo le distribuzioni di unità organizzative singole di Adobe Campaign
* Adobe Campaign è la sorgente originale per tutti i profili attivi: i profili devono quindi esistere in Adobe Campaign e non dovrebbero essere creati nuovi profili in base ai segmenti di Experience Platform.
* I flussi di lavoro di esportazione da Campaign si devono eseguire al massimo ogni 4 ore.
* Gli schemi e i set di dati XDM per Adobe Campaign wideLog, trackingLogs e gli indirizzi non consegnabili non sono pronti e devono essere progettati e costruiti

### Experience Platform di condivisione del segmento CDP

* Raccomandazione di un limite di 20 segmenti
* L&#39;attivazione è limitata a ogni 24 ore
* Sono disponibili per l’attivazione solo gli attributi dello schema di unione (nessun supporto per array/mappe/eventi esperienza)
* Raccomandazione su non più di 20 attributi per segmento
* Un file per segmento di tutti i profili con stato di appartenenza “realized” OPPURE, se la partecipazione al segmento viene aggiunta al file come attributo, sia i profili “realized” che “exited”
* Sono supportate le esportazioni incrementali e complete di segmenti
* La crittografia dei file non è supportata.

<br>

## Fasi di implementazione

### Adobe Experience Platform

#### Schema/Set di dati

1. [Configurare singoli schemi di profilo, di esperienza e di entità multiple](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, in base ai dati forniti dal cliente
1. Creare schemi di Adobe Campaign per broadLog, trackingLog, indirizzi non consegnabili e preferenze profilo (opzionale)
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) in Experience Platform per i dati da acquisire.
1. [Aggiungere etichette di utilizzo dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=it) ai set di dati in Experience Platform a scopo di governance.
1. [Creare le policy](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=it) che necessarie per applicare la governance alle destinazioni

#### Profilo/Identità

1. [Creare namespace specifici per il cliente](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it)
1. [Aggiungere le identità agli schemi](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=it)
1. [Impostare i criteri di unione](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=it) per le diverse viste di [!UICONTROL Real-time Customer Profile] (opzionale)
1. Creare segmenti da utilizzare in Adobe Campaign

#### Origini/Destinazioni

1. [Inserire i dati in Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=it) utilizzando API di streaming e connettori di origini
1. Configurare la destinazione di archiviazione BLOB di [!DNL Azure] da utilizzare con Adobe Campaign

#### Adobe Campaign

1. Configurare gli schemi per il profilo, i dati di ricerca e i relativi dati di personalizzazione della consegna

>[!IMPORTANT]
>
>A questo punto, è fondamentale comprendere quale modello di dati si trova all’interno di Experience Platform per i dati di profilo ed eventi, in modo da sapere quali saranno richiesti in Adobe Campaign.

#### Flussi di lavoro per l’importazione

1. Caricare e acquisire dati di profilo semplificati in Adobe Campaign sFTP
1. Caricare e acquisire i dati di personalizzazione di orchestrazione e messaggistica in Adobe Campaign sFTP.
1. Acquisire segmenti di Experience Platform da BLOB di [!DNL Azure] tramite flussi di lavoro

#### Flussi di lavoro per l’esportazione

1. Inviare i log di Adobe Campaign a Experience Platform tramite flussi di lavoro ogni quattro ore (broadLog, trackingLog, indirizzi non consegnabili)
1. Inviare le preferenze profilo a Experience Platform tramite flussi di lavoro creati dal servizio di consulenza ogni quattro ore (facoltativo)


### Configurazione push mobile

* Due approcci supportati per l’integrazione con i dispositivi mobili per le notifiche push:
   * SDK per dispositivi mobili di Experience Platform
   * SDK per Campaign Mobile
* Experience Platform di percorso dell’SDK di Mobile:
   * Sfrutta i tag di Adobe e l’estensione Campaign Classic per configurare la tua integrazione con l’SDK di Experience Platform Mobile
   * Necessità di una conoscenza operativa dei tag Adobi e della raccolta dei dati
   * Per distribuire l&#39;SDK, integrarsi con FCM (Android) e APNS (iOS) per ottenere il token push, configurare l&#39;app per la ricezione di notifiche push e gestire le interazioni push, è necessario che l&#39;esperienza di sviluppo mobile con le notifiche push sia in Android che in iOS sia con FCM (Android) e APNS ()
* SDK per Campaign Mobile
   * Segui la [Documentazione di Campaign SDK](SDK di Campaign Mobile) Segui la documentazione di distribuzione qui descritta.

   >[!IMPORTANT]
   >Se distribuisci l’SDK di Campaign e lavori con altre applicazioni Experience Cloud, per la raccolta dei dati dovrai utilizzare l’SDK di Experience Platform Mobile. Questo creerà chiamate lato client duplicate sul dispositivo.

## Documentazione correlata

* [Documentazione di Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [Documentazione di Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=it)
* [Documentazione di Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=it)
* [Documentazione di Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=it)
* [Documentazione di Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
