---
title: offer decisioning sul bordo
description: Offri offerte personalizzate ai consumatori su tutti i canali, incluse le esperienze web e mobili in tempo reale.
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
source-git-commit: 7f566536c4ff5a6af321d60058ad67c13c28bf64
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 34%

---

# Journey Optimizer - Offer decisioning sul bordo

Per ulteriori informazioni su Gestione delle decisioni, consulta la documentazione del prodotto [QUI](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html) e l&#39;Offer decisioning [QUI](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-overview.html)

Adobe Decision Management è un servizio fornito come parte di Adobe Journey Optimizer. Questo modello delinea i casi d’uso e le capacità tecniche dell’applicazione e fornisce un’analisi approfondita dei vari componenti architettonici e considerazioni che costituiscono un Offer decisioning.

La gestione delle decisioni può essere implementata in due modi. La prima è tramite Adobe Experience Platform Hub, che è un’architettura di un singolo centro dati. Nell’approccio &quot;hub&quot; le offerte vengono eseguite, personalizzate e distribuite alla seconda latenza. Pertanto, l’architettura dell’hub è più adatta per l’esperienza del cliente che non richiede latenza inferiore al secondo, ad esempio le decisioni di offerta che vengono fornite per chioschi o esperienze assistite dagli agenti, come nei call center o nelle interazioni personali.

Il secondo approccio è tramite Experience Edge Network, un’infrastruttura geograficamente distribuita a livello globale per distribuire esperienze di secondo e millisecondi rapidi. L’esperienza del consumatore finale eseguita dall’infrastruttura edge più vicina alla geolocalizzazione dei consumatori per ridurre al minimo la latenza. La gestione delle decisioni sul server Edge è progettata per offrire ai consumatori esperienze in tempo reale. Queste includono esperienze come richieste di personalizzazione in entrata per dispositivi mobili o web.

Questo modello copre le specifiche di Gestione delle decisioni sul server Edge.

Per ulteriori informazioni su Gestione delle decisioni sull&#39;hub, consulta [Gestione delle decisioni sull&#39;hub](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-hub.html) blueprint.

## Casi d&#39;uso per la gestione delle decisioni a margine

* Personalizzazione online tramite esperienze in entrata web o mobile.
* Esecuzione di percorsi cross-channel: coerenza delle offerte su web, dispositivi mobili, e-mail e altri canali di interazione tramite Adobe Journey Optimizer.

<br>

## Architettura

<img src="../assets/offers_edge.svg" alt="Offer decisioning di architettura di riferimento sulla blueprint edge" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Pattern di integrazione

| Integrazione | Descrizione |
| :-- | :--- |
| [offer decisioning con Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html) | Offer Decisioning può essere integrato con Adobe Target in modo che le offerte possano essere testate e consegnate come esperienze Target. |

## Prerequisiti

Adobe Experience Platform

* Gli schemi e i set di dati devono essere configurati nel sistema prima di poter configurare le origini dati di Journey Optimizer.
* Per poter attivare un evento non basato su regole, aggiungi il gruppo di campi Orchestration eventID agli schemi di eventi Experience basati su classi.
* Per poter caricare profili di test da utilizzare con Journey Optimizer, aggiungi il gruppo di campi “Profile test details” agli schemi per singoli profili basati su classi.

<br>

## Guardrail

* Per le protezioni di Journey Optimizer, consulta quanto segue [Journey Optimizer Guardrail](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html).
* Ad Offer decisioning, le protezioni fanno riferimento ai seguenti elementi: [offer decisioning Descrizione del prodotto](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html).

### Guardrail per l’acquisizione dei dati

<img src="../assets/aep-data-ingestion-details-latency.svg" alt="Architettura di riferimento per il blueprint Journey Optimizer" style="width:80%; border:1px solid #4a4a4a" />

<br>

### Guardrail per l’attivazione

<img src="../assets/ajo-activation-details-latency.svg" alt="Architettura di riferimento per il blueprint Journey Optimizer" style="width:80%; border:1px solid #4a4a4a" />

<br>

## Modelli di implementazione

* Utilizza l’SDK web o mobile per la distribuzione su siti web e applicazioni mobili per implementare l’Offer decisioning in cui è stato implementato l’SDK.
   * [Blueprint SDK per web/mobile](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/data-ingestion/websdk.html?lang=it)
   * [WebSDK](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/offer-decisioning/offer-decisioning-overview.html)
   * [MobileSDK](https://aep-sdks.gitbook.io/docs/)

Oppure

* Per un’implementazione basata su server API, utilizza l’API del servizio di rete Edge per l’implementazione diretta da server a server di Offer Decisioning.
   * [API server di rete Edge](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/deliver-offers.html)

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

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html)
* [Gestione delle decisioni Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Descrizione del prodotto Adobe Journey Optimizer](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe Offer decisioning Descrizione del prodotto](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
