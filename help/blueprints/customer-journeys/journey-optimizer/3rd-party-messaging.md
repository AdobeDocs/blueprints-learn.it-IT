---
title: Journey Optimizer - Blueprint per messaggistica di terze parti
description: Dimostra come utilizzare Adobe Journey Optimizer con sistemi di messaggistica di terze parti per inviare comunicazioni personalizzate.
solution: Journey Optimizer
exl-id: 3a14fc06-6d9c-4cd8-bc5c-f38e253d53ce
TQID: https://experienceleague.adobe.com/dlCwgPnHuoU0IGois2Yy3e9wPELIQsLkStzTBVl5M1M
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
feature_v2:
  - id: a653cc2e-bc85-4353-a306-399e5b247978
  - id: d556b755-390a-43f0-be32-a08cf6236126
  - id: d998adac-2f81-400b-a669-d07bb196e4eb
subfeature_v2:
  - id: af7571a6-3ddb-4c1c-abdf-4d4dde592140
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c7d04a2c-412a-4c9d-9d7a-4456eaa5adeb
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 577
ht-degree: 61%

---

# Blueprint per messaggistica di terze parti

>[!TIP]
>Questo blueprint è disponibile anche come [modello di casi d&#39;uso](/help/blueprints/use-case-patterns/campaign-management-orchestration/third-party-messaging.md) in Gestione e orchestrazione campagne.

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

[Collegamento prodotto guardrail Journey Optimizer](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=it)

[Guardrail e guida alla latenza end-to-end](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html?lang=it)

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
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/it/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile)
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
* [Documentazione di Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
* [Documentazione di Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=it)
* [Descrizione del prodotto Journey Optimizer](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer.html)
