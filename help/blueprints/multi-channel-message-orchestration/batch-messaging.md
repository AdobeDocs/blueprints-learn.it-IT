---
title: Blueprint per messaggistica batch e Adobe Experience Platform
description: Esegui campagne di messaggistica pianificate e in batch utilizzando Adobe Experience Platform come hub centrale per i profili clienti e la segmentazione.
solution: Experience Platform, Campaign
kt: 7196
exl-id: 4e55218c-c158-4f78-9f0b-c03528d992fa
translation-type: tm+mt
source-git-commit: 01f70fe432d7be38b71889ae19c0d5fe4cf0f78a
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 82%

---

# Blueprint per messaggistica batch e Adobe Experience Platform

Esegui campagne di messaggistica pianificate e in batch utilizzando Adobe Experience Platform come hub centrale per i profili clienti e la segmentazione.

## Casi di utilizzo

* Campagne e-mail pianificate
* Campagne di onboarding e di re-marketing

## Applicazioni

* Adobe Experience Platform
* Adobe Campaign Classic o Standard

## Pattern di integrazione

* Adobe Experience Platform → Adobe Campaign Classic
* Adobe Experience Platform → Adobe Campaign Standard

## Architettura

<img src="assets/aepbatch.svg" alt="Architettura di riferimento per il blueprint per messaggistica batch e Adobe Experience Platform" style="border:1px solid #4a4a4a" />

## Guardrail

* Supporta solo le implementazioni di Adobe Campaign per singole unità organizzative
* Adobe Campaign è la sorgente originale per tutti i profili attivi: i profili devono quindi esistere in Adobe Campaign e non dovrebbero essere creati nuovi profili in base ai segmenti di Experience Platform.
* L’attuazione dell’appartenenza ai segmenti da Experience Platform è latente sia in batch (1 al giorno) che in streaming (~5 minuti).

Condivisione dei segmenti di **[!UICONTROL Real-time Customer Data Platform] con Adobe Campaign:**

* Si consiglia un limite di 20 segmenti
* L’attivazione è limitata a ogni 24 ore
* Sono disponibili per l’attivazione solo gli attributi dello schema di unione (nessun supporto per array/mappe/eventi esperienza).
* Si raccomanda di non superare i 20 attributi per segmento
* Un file per segmento di tutti i profili con stato di appartenenza “realized” OPPURE, se la partecipazione al segmento viene aggiunta al file come attributo, sia i profili “realized” che “exited”
* Sono supportate le esportazioni incrementali o di segmenti completi.
* La crittografia dei file non è supportata.
* I flussi di lavoro di esportazione da Adobe Campaign si devono eseguire al massimo ogni 4 ore.
* Vedi [guardrail per l’acquisizione di dati e profili per Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it).

## Fasi di implementazione

### Adobe Experience Platform

#### Schema/Set di dati

1. [Configurare singoli schemi di profilo, di esperienza e di entità multiple in Experience Platform, in base ai dati forniti dal cliente](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html)
1. Creare schemi di Adobe Campaign per broadLog, trackingLog, indirizzi non consegnabili e preferenze profilo (opzionale)
1. [Crea ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) dati in Experience Platform per i dati da acquisire.
1. [Aggiungi etichette di utilizzo dei dati ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html) in Experience Platform al set di dati per la governance.
1. [Creare le policy che necessarie per applicare la governance alle destinazioni](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html)

#### Profilo/Identità

1. [Crea qualsiasi namespace](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html) specifico per il cliente.
1. [Aggiungi identità agli schemi](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Abilita gli schemi e i set di dati per Profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Imposta ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) criteri di unione per diverse visualizzazioni del profilo cliente  [!UICONTROL in tempo reale]  (facoltativo).
1. Creare segmenti da utilizzare in Adobe Campaign

#### Fonti / destinazioni

1. [Inserire i dati in Experience Platform utilizzando API di streaming e connettori di origini](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)
1. Configurare la destinazione di archiviazione BLOB di [!DNL Azure] da utilizzare con Adobe Campaign

#### Implementazione di app mobili

1. Implementare Adobe Campaign SDK per Adobe Campaign Classic o Experience Platform SDK per Adobe Campaign Standard. Se è presente Experience Platform Launch, si consiglia di utilizzare l’estensione Adobe Campaign Classic o Adobe Campaign Standard con Experience Platform SDK.

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


## Documentazione correlata

* [Documentazione di Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [Documentazione di Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=it)
* [Documentazione di Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=it)
* [Documentazione di Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=it)
* [Documentazione di Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
