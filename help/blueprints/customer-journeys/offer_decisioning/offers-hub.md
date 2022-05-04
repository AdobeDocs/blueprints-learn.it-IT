---
title: offer decisioning sull'hub
description: Offri offerte personalizzate ai consumatori su tutti i canali, compresi chioschi, esperienze assistite dagli agenti, e-mail e altre consegne in uscita.
solution: Experience Platform, Journey Optimizer
exl-id: 5a386e18-bbac-4216-a35f-0a5016785e4a
source-git-commit: 494d70fca12a42befb7b726562d98cec17a21d22
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 32%

---

# Journey Optimizer - Offer decisioning sull&#39;hub

Adobe Decision Management è un servizio fornito come parte di Adobe Journey Optimizer. Questo modello delinea i casi d’uso e le capacità tecniche dell’applicazione e fornisce un’analisi approfondita dei vari componenti architettonici e considerazioni che costituiscono un Offer decisioning.

La gestione delle decisioni può essere implementata in due modi. La prima è via Adobe Experience Platform hub, un&#39;architettura centrale del data center. Nell’approccio &quot;hub&quot; le offerte vengono eseguite, personalizzate e distribuite con latenza >500 ms. Pertanto, l’architettura dell’hub è più adatta per le esperienze dei clienti che non richiedono latenza inferiore al secondo, ad esempio le decisioni di offerta che vengono fornite per i chioschi o le esperienze assistite dagli agenti, come nei call center o nelle interazioni personali. Anche le offerte inserite nelle e-mail e nelle campagne in uscita sono basate sull’approccio hub.

Il secondo approccio è tramite Experience Edge Network, un’infrastruttura geograficamente distribuita a livello globale per distribuire esperienze di secondo e millisecondi rapidi. L’esperienza del consumatore finale eseguita dall’infrastruttura edge più vicina alla geolocalizzazione dei consumatori per ridurre al minimo la latenza. La funzione di gestione delle decisioni sul server Edge è progettata per offrire ai consumatori esperienze in tempo reale, ad esempio richieste di personalizzazione in entrata per dispositivi web o mobili.

Questo progetto riguarderà le specifiche della gestione delle decisioni sull&#39;hub.

Per ulteriori informazioni su Gestione delle decisioni sul server Edge, consulta [Gestione delle decisioni a margine](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-edge.html?lang=en) blueprint.

Per ulteriori informazioni su Gestione delle decisioni, consulta la documentazione del prodotto [QUI](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)

## Casi di utilizzo

* Offerte personalizzate su chioschi ed esperienze in-store.
* Offerte personalizzate tramite l’esperienza assistita dell’agente, ad esempio ai call center o alle interazioni di vendita.
* Offerte incluse in e-mail, SMS o altre interazioni in uscita.
* Esecuzione di percorsi cross-channel: coerenza delle offerte su web, dispositivi mobili, e-mail e altri canali di interazione tramite Adobe Journey Optimizer.

<br>

## Architettura

<img src="../assets/offers_hub.svg" alt="Offer decisioning di architettura di riferimento sulla blueprint edge" style="width:100%; border:1px solid #4a4a4a" />

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

* Implementato in e-mail, SMS e canali in uscita tramite integrazione diretta con [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/offers-e2e.html).
* Per l’implementazione di Offer decisioning basata su API server, sfrutta i [Decisioning API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/decisioning-vs-edge-apis.html).
* Per l’implementazione delle decisioni basate su batch per consegnare le offerte in massa a un’applicazione di consegna dei messaggi, utilizza la [API Batch Decisioning](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/batch-decisioning-api.html).
* Per le esperienze in tempo reale basate su Edge, utilizza l’SDK per web/Mobile o l’API di Edge Decisioning come descritto in [offer decisioning sulla blueprint Edge](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-edge.html).
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
