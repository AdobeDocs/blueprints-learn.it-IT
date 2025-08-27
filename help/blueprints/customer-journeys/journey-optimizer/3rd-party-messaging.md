---
title: Journey Optimizer - Blueprint per messaggistica di terze parti
description: Dimostra come utilizzare Adobe Journey Optimizer con sistemi di messaggistica di terze parti per inviare comunicazioni personalizzate.
solution: Journey Optimizer
exl-id: 3a14fc06-6d9c-4cd8-bc5c-f38e253d53ce
source-git-commit: 0a3ebcbc6029df46bd988cb8f15ecf838f80c3c9
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 61%

---

# Blueprint per messaggistica di terze parti

Dimostra come utilizzare Adobe Journey Optimizer con sistemi di messaggistica di terze parti per inviare comunicazioni personalizzate.

<br>

## Architettura

<img src="images/3rd-party-messaging-architecture.svg" alt="Architettura di riferimento per il blueprint Journey Optimizer" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Prerequisiti

**Adobe Experience Platform**

* Gli schemi e i set di dati devono essere configurati nel sistema prima di poter configurare le origini dati di Journey Optimizer.
* Per gli schemi basati su classi Experience Event, aggiungi &quot;Gruppo di campi ID evento di orchestrazione&quot; quando desideri che venga attivato un evento che non sia un evento basato su regole
* Per gli schemi basati su singole classi di profilo, aggiungi il gruppo di campi &quot;Dettagli test profilo&quot; per poter caricare i profili di test da utilizzare con Journey Optimizer

**Applicazione di messaggistica di terze parti**

* Deve supportare le chiamate API REST per l’invio di payload transazionali.

<br>

## Guardrail

[Link al prodotto per i guardrail Journey Optimizer](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html)

[Guardrail e indicazioni sulla latenza End to End](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html)

<br>

## Fasi di implementazione

### Adobe Experience Platform

#### Schema/set di dati

1. [Configura gli schemi](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&lang=it) in Experience Platform in base ai dati forniti dal cliente.
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) in Experience Platform per i dati da acquisire.
1. [Aggiungere etichette di utilizzo dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=it) ai set di dati in Experience Platform a scopo di governance.
1. [Creare le policy](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=it) che necessarie per applicare la governance alle destinazioni

#### Profilo/identità

1. [Creare namespace specifici per il cliente](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it)
1. [Aggiungere le identità agli schemi](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it)
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile)
1. [Impostare i criteri di unione](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=it) per viste diverse del [!UICONTROL profilo cliente in tempo reale] (opzionale)
1. Creare segmenti da utilizzare in Journey

#### Origini/destinazioni

1. [Inserire i dati in Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&lang=it) utilizzando API di streaming e connettori di origini.

### Journey Optimizer

1. Configura l’origine dati di Experience Platform e determina quali campi devono essere memorizzati in cache come parte del percorso
1. I dati in streaming, utilizzati per avviare un percorso di clienti, devono essere configurati prima per ottenere un ID di orchestrazione. Questo ID di orchestrazione viene quindi fornito allo sviluppatore per l’utilizzo durante l’acquisizione
1. Configurare le origini dati esterne.
1. Configurare le azioni personalizzate per l’applicazione di terze parti.

### Configurazione push mobile (opzionale per l’eventuale raccolta di token da terze parti)

1. Implementare Experience Platform Mobile SDK per raccogliere i token push e le informazioni di accesso da associare ai profili cliente noti.
1. Utilizzare i tag di Adobe e creare una proprietà mobile con la seguente estensione:
   * Adobe Journey Optimizer
   * Rete Edge di Adobe Experience Platform
   * Identità per [!DNL Edge Network]
   * Mobile Core
1. Assicurati di disporre di un flusso di dati dedicato per le implementazioni di app mobili rispetto alle implementazioni web.
1. Per ulteriori informazioni, consulta la [guida di Adobe Journey Optimizer Mobile](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer/).

<br>

## Documentazione correlata

* [Documentazione di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it)
* [Documentazione di Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html)
* [Documentazione di Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html)
* [Descrizione del prodotto Journey Optimizer](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer.html)