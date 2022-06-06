---
title: Gestione delle decisioni a margine
description: Presenta ai consumatori offerte personalizzate su tutti i canali, incluse le esperienze web e mobili in tempo reale.
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
source-git-commit: 5b2f7531cc05178127fb08d3fdafcbce70192ecd
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 69%

---

# Journey Optimizer - Gestione delle decisioni all&#39;avanguardia

Per ulteriori informazioni su Gestione delle decisioni, consulta la documentazione del prodotto [QUI](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=it) e la panoramica della gestione delle decisioni [QUI](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/decision-management-overview.html)

Adobe Decision Management è un servizio fornito come parte di Adobe Journey Optimizer. Il presente progetto delinea i casi d&#39;uso e le capacità tecniche dell&#39;applicazione e fornisce un&#39;analisi approfondita dei vari elementi architettonici e delle considerazioni che compongono la Gestione delle decisioni.

Il servizio Decision Management può essere implementato in due modi. Il primo approccio prevede l’utilizzo dell’hub Adobe Experience Platform, un’architettura con un singolo datacenter. Con questo approccio mediante “hub”, le offerte vengono eseguite, personalizzate e distribuite con una latenza di pochi secondi. Pertanto, l’architettura con hub è più adatta per esperienze del cliente che non richiedono latenze inferiori al secondo, ad esempio per decisioni di offerta destinate a chioschi o esperienze assistite da agenti, come call center o interazioni con persone.

Il secondo approccio prevede l’utilizzo della rete Experience Edge, un’infrastruttura geograficamente distribuita a livello globale per la distribuzione rapida di esperienze con una latenza inferiore al secondo o di millisecondi. Per ridurre al minimo la latenza, l’esperienza del consumatore finale viene eseguita dall’infrastruttura Edge geograficamente più vicina. Il servizio Decision Management sulla rete Edge è progettato per offrire ai consumatori esperienze in tempo reale, comprese le richieste di personalizzazione in entrata per web e dispositivi mobili.

Questo blueprint tratta le specifiche di Decision Management sulla rete Edge.

Per ulteriori informazioni su Decision Management tramite hub, consulta il blueprint [Decision Management tramite hub](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/decision-management-hub.html).

## Casi d&#39;uso per la gestione delle decisioni a margine

* Personalizzazione online tramite esperienze in entrata web o mobile.
* Esecuzione di percorsi cross-channel: offerte coerenti su web, dispositivi mobili, e-mail e altri canali di interazione tramite Adobe Journey Optimizer.

<br>

## Architettura

<img src="../assets/offers_edge.svg" alt="Architettura di riferimento Gestione delle decisioni sulla blueprint edge" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Pattern di integrazione

| Integrazione | Descrizione |
| :-- | :--- |
| [Gestione delle decisioni con Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html?lang=it) | La gestione delle decisioni può essere integrata con Adobe Target in modo che le offerte possano essere testate e consegnate come esperienze Target. |

## Prerequisiti

Adobe Experience Platform

* Gli schemi e i set di dati devono essere configurati nel sistema prima di poter configurare le origini dati di Journey Optimizer.
* Per poter attivare un evento non basato su regole, aggiungi il gruppo di campi Orchestration eventID agli schemi di eventi Experience basati su classi.
* Per poter caricare profili di test da utilizzare con Journey Optimizer, aggiungi il gruppo di campi “Profile test details” agli schemi per singoli profili basati su classi.

<br>

## Guardrail

* Per i guardrail relativi a Journey Optimizer, consulta i seguenti [Guardrail per Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html?lang=it).
* Per le protezioni della gestione delle decisioni si fa riferimento ai seguenti elementi: [Descrizione del prodotto per la gestione delle decisioni](https://helpx.adobe.com/it/legal/product-descriptions/offer-decisioning-app-service.html).
* Richieste al secondo = 5000.
* Latenza di risposta &lt; 250 ms.
* Accesso al profilo in tempo reale edge. Nel profilo saranno disponibili solo i tipi di pubblico e gli attributi di profilo edge proiettati.
* Se nelle esperienze della prima volta è richiesta la personalizzazione, l’hub sarà ideale in quanto è disponibile il profilo completo. Il profilo Edge deve sincronizzarsi dall’hub per la prima esperienza Edge. Pertanto, la prima esperienza dal bordo non includerà i dati del profilo precedentemente caricati sull&#39;hub.

### Guardrail per l’acquisizione dei dati

<img src="../assets/aep-data-ingestion-details-latency.svg" alt="Architettura di riferimento per il blueprint Journey Optimizer" style="width:80%; border:1px solid #4a4a4a" />

<br>

### Guardrail per l’attivazione

<img src="../assets/ajo-activation-details-latency.svg" alt="Architettura di riferimento per il blueprint Journey Optimizer" style="width:80%; border:1px solid #4a4a4a" />

<br>

## Modelli di implementazione

* Utilizza l’SDK web o mobile per la distribuzione su siti web e applicazioni mobili per implementare la gestione delle decisioni in cui è stato implementato l’SDK.
   * [Blueprint per Web/Mobile SDK](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/data-ingestion/websdk.html?lang=it)
   * [Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/offer-decisioning/offer-decisioning-overview.html?lang=it)
   * [Mobile SDK](https://aep-sdks.gitbook.io/docs/)

Oppure

* Per un’implementazione basata su server API, utilizza l’API del servizio di rete Edge per l’implementazione server-to-server della gestione delle decisioni.
   * [Edge Network Server API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/deliver-offers.html?lang=it)

<br>

## Fasi di implementazione

### Adobe Experience Platform

#### Schema/set di dati

1. [Configurare singoli schemi di profilo, di esperienza e di entità multiple](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, in base ai dati forniti dal cliente
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) in Experience Platform per i dati da acquisire.
1. [Aggiungere etichette di utilizzo dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=it) ai set di dati in Experience Platform a scopo di governance.
1. [Creare i criteri](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=it) necessari per applicare la governance alle destinazioni

#### Profilo/Identità

1. [Creare namespace specifici per il cliente](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it)
1. [Aggiungere le identità agli schemi](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=it)
1. [Impostare i criteri di unione](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=it) per le diverse viste di [!UICONTROL Real-time Customer Profile] (opzionale)
1. Creare segmenti da utilizzare in Journey

#### Origini/Destinazioni

1. [Inserire i dati in Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=it) utilizzando API di streaming e connettori di origini.

## Documentazione correlata

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=it)
* [Decision Management per Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Descrizione del prodotto Adobe Journey Optimizer](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe descrizione del prodotto per la gestione delle decisioni](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)