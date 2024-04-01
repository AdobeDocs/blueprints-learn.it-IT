---
title: Blueprint per Journey Optimizer con Adobe Campaign v7
description: Mostra come Adobe Journey Optimizer può essere utilizzato con Adobe Campaign per inviare messaggi in modo nativo utilizzando il server di messaggistica in tempo reale in Campaign.
solution: Journey Optimizer, Campaign, Campaign Classic v7, Campaign Standard
exl-id: 6d9bc65c-cca0-453f-8106-d2895d005ada
source-git-commit: 60a7785ea0ec4ee83fd9a1e843f0b84fc4cb1150
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 97%

---

# Blueprint per Journey Optimizer con Adobe Campaign v7

Mostra come Adobe Journey Optimizer può essere utilizzato con Adobe Campaign per inviare messaggi in modo nativo utilizzando il server di messaggistica in tempo reale in Campaign.

<br>

## Architettura

<img src="assets/ajo-campaign-architecture.svg" alt="Architettura di riferimento per il blueprint Journey Optimizer" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

>[!IMPORTANT]
>È possibile utilizzare sia Journey Optimizer che Campaign per inviare messaggi in modo indipendente l’uno dall’altro, ma occorre tenere conto di alcuni aspetti tecnici. Se desideri seguire questo percorso, collabora con il tuo Pre-Sales Enterprise Architect per essere certo di comprendere tutti i requisiti necessari per l’implementazione.

<br>

## Prerequisiti

### Adobe Experience Platform

* Gli schemi e i set di dati devono essere configurati nel sistema prima di poter configurare le origini dati di Journey Optimizer.
* Per poter attivare un evento non basato su regole, aggiungi il gruppo di campi Orchestration eventID agli schemi di eventi Experience basati su classi.
* Per poter caricare profili di test da utilizzare con Journey Optimizer, aggiungi il gruppo di campi “Profile test details” agli schemi per singoli profili basati su classi.
* Journey Optimizer e Campaign devono entrambi essere presenti nella stessa organizzazione IMS.

### Campaign v7

* L’istanza di esecuzione del servizio di messaggistica in tempo reale (ad es. Message Center) deve essere ospitata da Adobe Managed Cloud Services.
* L’authoring dei messaggi viene eseguito direttamente nell’istanza di Campaign.

<br>

## Guardrail

[Link al prodotto per i guardrail Journey Optimizer](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=it)

[Guardrail e guida alla latenza end-to-end](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## Fasi di implementazione

### Adobe Experience Platform

#### Schema/set di dati

1. [Configurare singoli schemi di profilo, di esperienza e di entità multiple](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=it) in Experience Platform, in base ai dati forniti dal cliente
1. Creare schemi basati su classi di eventi Experience per broadLog, trackingLog e le tabelle di Adobe Campaign degli indirizzi a cui non possono essere consegnati i messaggi (facoltativo).
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) in Experience Platform per i dati da acquisire.
1. [Aggiungere etichette di utilizzo dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=it) ai set di dati in Experience Platform a scopo di governance.
1. [Creare le policy](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=it) che necessarie per applicare la governance alle destinazioni

#### Profilo/identità

1. [Creare namespace specifici per il cliente](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it)
1. [Aggiungere le identità agli schemi](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it)
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=it)
1. [Impostare i criteri di unione](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=it) per viste diverse del [!UICONTROL profilo cliente in tempo reale] (opzionale)
1. Creare segmenti da utilizzare in Journey

#### Origini/destinazioni

1. [Inserire i dati in Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=it) utilizzando API di streaming e connettori di origini.

### Journey Optimizer

1. Configurare l’origine dati di Experience Platform e determinare quali campi devono essere memorizzati nella cache come parte dei dati del profilo. I dati in streaming utilizzati per avviare un percorso cliente devono prima essere configurati in Journey Optimizer, per ottenere un ID di orchestrazione. Questo ID di orchestrazione viene quindi fornito allo sviluppatore che potrà utilizzarlo con l’acquisizione.
1. Configurare le origini dati esterne.
1. Configurare le azioni personalizzate per l’istanza di Campaign.

### Campaign v7

* I modelli di messaggistica devono essere configurati con un contesto di personalizzazione appropriato.
* Per Campaign v7 - I flussi di lavoro di esportazione devono essere configurati per l’esportazione dei registri di messaggistica transazionale da restituire a Experience Platform. Si consiglia di eseguirli al massimo ogni 4 ore.

### Configurazione push mobile (opzionale)

1. Implementare Experience Platform Mobile SDK per raccogliere i token push e le informazioni di accesso da associare ai profili cliente noti.
1. Utilizzare i tag di Adobe e creare una proprietà mobile con la seguente estensione:
   * Adobe Journey Optimizer | Adobe Campaign Classic | Adobe Campaign Standard
   * Adobe Experience Platform [!DNL Edge Network]
   * Identità per [!DNL Edge Network]
   * Mobile Core
1. Assicurati di disporre di un flusso di dati dedicato per le implementazioni di app mobili rispetto alle implementazioni web.
1. Per ulteriori informazioni, consulta la [guida di Adobe Journey Optimizer Mobile](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer).

   >[!IMPORTANT]
   >Per poter inviare comunicazioni in tempo reale tramite Journey Optimizer e notifiche push in batch tramite Campaign, potrebbe essere necessario raccogliere token mobili sia in Journey Optimizer che in Campaign. Per l’acquisizione dei token push, Campaign v8 richiede l’utilizzo esclusivo di Campaign SDK.

<br>

## Documentazione correlata

* [Documentazione di Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=it)
* [Descrizione del prodotto Journey Optimizer](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer.html)
* [Documentazione di Campaign v7](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=it)
