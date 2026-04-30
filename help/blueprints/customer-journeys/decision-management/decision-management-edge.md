---
title: Blueprint per la gestione delle decisioni tramite rete Edge
description: Presenta ai consumatori offerte personalizzate su tutti i canali, incluse le esperienze web e mobili in tempo reale.
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
TQID: https://experienceleague.adobe.com/SwjKOJIL5WidXtVuLCNbBpNz3mhe0EvD93IhMfxI1oY
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: c132d929-fa62-4271-803e-b823be07b914
  - id: d998adac-2f81-400b-a669-d07bb196e4eb
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
  - id: df64005d-8f9a-422e-ba4d-c6f6dc3454b4
  - id: fe338112-e2ce-4876-8989-fc4d497613f1
subfeature_v2:
  - id: e5ae22e3-a3b0-46ed-804f-9abf1bbe3e74
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: c18d9e03-ac7d-4811-9c92-3e92ddc70ade
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 492
ht-degree: 67%

---

# Journey Optimizer - [!DNL Decision Management] su blueprint Edge

>[!TIP]
>Questo blueprint è disponibile anche come [caso d&#39;uso](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) in Personalization.

[!DNL Decision Management] è un servizio fornito come parte di [!DNL Journey Optimizer]. Questo blueprint riassume i casi di utilizzo e le capacità tecniche dell’applicazione e descrive nel dettaglio i vari componenti dell’architettura di Gestione delle decisioni e le relative considerazioni.

>[!MORELIKETHIS]
>
>Per ulteriori informazioni su [!DNL Decision Management], consulta la [panoramica blueprint](decision-management-overview.md) o visita la [documentazione del prodotto](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=it).

[!DNL Decision Management] può essere distribuito in due modi. Il primo avviene tramite l&#39;hub [!DNL Experience Platform], che è un&#39;architettura di un singolo centro dati. Con questo approccio mediante “hub”, le offerte vengono eseguite, personalizzate e distribuite con una latenza di pochi secondi. Pertanto, l’architettura con hub è più adatta per esperienze del cliente che non richiedono latenze inferiori al secondo, ad esempio per decisioni di offerta destinate a chioschi o esperienze assistite da agenti, come call center o interazioni con persone.

Il secondo approccio è tramite Experience Platform [!DNL Edge Network], che è un&#39;infrastruttura distribuita a livello globale e geograficamente posizionata per fornire esperienze veloci di secondi secondari e millisecondi. L’esperienza del consumatore finale eseguita dall’infrastruttura Edge più vicina alla geolocalizzazione dei consumatori per ridurre al minimo la latenza. [!DNL Decision Management] su Edge è progettato per offrire ai clienti esperienze in tempo reale. comprese le richieste di personalizzazione in entrata per web e dispositivi mobili.

Questo blueprint tratta le specifiche di Gestione delle decisioni sulla rete Edge.

Per ulteriori informazioni su Gestione delle decisioni tramite hub, consulta il blueprint [Gestione delle decisioni tramite hub](decision-management-hub.md).

## Casi di utilizzo per Gestione delle decisioni tramite rete Edge

* Casi d’uso di streaming in cui la latenza del contesto del profilo è rigorosa al di sotto di 15 minuti e l’esecuzione della gestione delle decisioni è al di sotto del secondo.
* Personalizzazione online tramite esperienze web o mobile in entrata.
* Esecuzione di percorsi cross-channel: offerte coerenti su web, dispositivi mobili, e-mail e altri canali di interazione tramite Adobe Journey Optimizer.

## Architettura

<img src="images/offers_edge.svg" alt="Architettura di riferimento del blueprint per Gestione delle decisioni tramite rete Edge" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Modelli di integrazione

| Integrazione | Descrizione |
| :-- | :--- |
| [Gestione delle decisioni con Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html?lang=it) | La funzionalità Gestione delle decisioni può essere integrata con Adobe Target in modo che le offerte possano essere testate e consegnate come esperienze Target. |

## Guardrail

* Per i guardrail relativi a Journey Optimizer, consulta i seguenti [Guardrail per Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html?lang=it).

* Per i guardrail relativi a Gestione delle decisioni, fai riferimento alla [Descrizione del prodotto Gestione delle decisioni](https://helpx.adobe.com/it/legal/product-descriptions/offer-decisioning-app-service.html).

[Guardrail e guida alla latenza end-to-end](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html?lang=it)

## Documentazione correlata

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=it)
* [Gestione delle decisioni per Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=it)
* [Descrizione del prodotto Adobe Journey Optimizer](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer.html)
* [Descrizione del prodotto Adobe Decision Management](https://helpx.adobe.com/it/legal/product-descriptions/offer-decisioning-app-service.html)
