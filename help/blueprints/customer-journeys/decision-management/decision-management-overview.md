---
title: Blueprint per la gestione delle decisioni
description: Presenta offerte personalizzate lungo i vari percorsi dei clienti.
solution: Experience Platform, Journey Optimizer
exl-id: 1bc9335c-5321-4d0c-939e-4f402e2e8f51
TQID: https://experienceleague.adobe.com/FWKq0QzEzCXp8TrfECmhY4E3ocA4zZkTGyHrrKQCOBw
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
  - id: fa683eda-48de-4558-af32-2673edcd44fe
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: d00e9f03-e50b-4162-b143-0c0817c937c2
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: a99add31cc9f485db119ca00426798545e6a7316
workflow-type: tm+mt
source-wordcount: 731
ht-degree: 76%

---

# Journey Optimizer - Progetti di gestione delle decisioni

Consulta la seguente documentazione per [Gestione delle decisioni](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=it)

Per i guardrail relativi alla gestione delle decisioni, consulta la seguente documentazione. [Guardrail Di Gestione Delle Decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails#decision-management.html)

La funzionalità Gestione delle decisioni è un servizio Adobe fornito come parte di Adobe Journey Optimizer. Questo blueprint riassume i casi di utilizzo e le capacità tecniche dell’applicazione e descrive nel dettaglio i vari componenti dell’architettura di Gestione delle decisioni e le relative considerazioni.

Journey Optimizer viene utilizzato per fornire ai clienti le migliori offerte ed esperienze possibili, in tutti i punti di contatto e al momento opportuno. La funzione Gestione delle decisioni semplifica la personalizzazione con una libreria centrale di offerte di marketing e un motore decisionale che applica regole e vincoli ai profili in tempo reale creati da Adobe Experience Platform. Ciò ti consente di inviare ai clienti l’offerta giusta al momento giusto.

La funzionalità Gestione delle decisioni è composta da due componenti principali:

* La libreria di offerte centralizzata, ossia l’interfaccia che permette di creare e gestire i diversi elementi che compongono le offerte e di definirne regole e vincoli.
* Il motore che elabora le decisioni delle offerte, che utilizza i dati e i profili cliente in tempo reale di Adobe Experience Platform nonché la libreria di offerte per determinare il momento giusto, i clienti e i canali a cui verranno presentate le offerte.

<img src="images/offers_overview.png" alt="Gestione delle decisioni" style="width:100%; border:1px solid #4a4a4a" />

Il servizio Gestione delle decisioni può essere implementato in due modi: tramite rete Edge o tramite hub. Ciascuno di questi metodi dispone di uno specifico set di interfacce e protocolli per il funzionamento del servizio, come descritto nei rispettivi blueprint indicati di seguito. Per ulteriori informazioni, consulta la [documentazione del servizio Gestione delle decisioni](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery-api/decisioning-vs-edge-apis.html?lang=it).

## Gestione delle decisioni tramite hub

Il primo approccio prevede l’utilizzo dell’hub Adobe Experience Platform, un’architettura con un datacenter centrale. L’architettura dell’hub è ideale per le esperienze dei clienti che non richiedono bassa latenza e throughput elevato, ma richiedono una visualizzazione più completa del profilo del cliente. Alcuni esempi includono decisioni di offerta fornite per i chioschi o esperienze assistite da agenti, come nei call center o nelle interazioni di persona. L’approccio tramite hub consente anche di gestire le offerte inserite in e-mail, SMS o notifiche push e altre campagne in uscita. Per ulteriori informazioni su Gestione delle decisioni tramite hub, consulta il blueprint [Gestione delle decisioni tramite hub](decision-management-hub.md).

* L’idoneità alle offerte può funzionare in base al profilo cliente in tempo reale completo, inclusi tutti gli attributi e gli eventi delle esperienze.

### Casi di utilizzo per Gestione delle decisioni tramite hub

* Offerte personalizzate per chioschi ed esperienze in-store.
* Offerte personalizzate tramite esperienze assistite da agenti, come call center o interazioni di vendita.
* Offerte incluse in e-mail, SMS o altre interazioni in uscita.
* Esecuzione di percorsi cross-channel: offerte coerenti su web, dispositivi mobili, e-mail e altri canali di interazione tramite Adobe Journey Optimizer.

### Considerazioni tecniche per Gestione delle decisioni tramite hub

* Accesso al profilo cliente in tempo reale completo, compresi appartenenze a un pubblico, attributi ed eventi di esperienza.

## Gestione delle decisioni tramite rete Edge

Il secondo approccio è tramite l&#39;esperienza [!DNL Edge Network], un&#39;infrastruttura distribuita a livello globale e geograficamente situata per fornire esperienze veloci di secondo e millisecondo. Per ridurre al minimo la latenza, l’esperienza del consumatore finale viene eseguita dall’infrastruttura Edge geograficamente più vicina. Il servizio Gestione delle decisioni sulla rete Edge è progettato per offrire ai consumatori esperienze in tempo reale, ad esempio con richieste di personalizzazione in entrata per web e dispositivi mobili. Per ulteriori informazioni su Gestione delle decisioni tramite rete Edge, consulta il blueprint [Gestione delle decisioni sulla rete Edge](decision-management-edge.md).

### Casi di utilizzo per Gestione delle decisioni tramite rete Edge

* Personalizzazione online tramite esperienze web o mobile in entrata.
* Esecuzione di percorsi cross-channel: offerte coerenti su web, dispositivi mobili, e-mail e altri canali di interazione tramite Adobe Journey Optimizer.

### Considerazioni tecniche per Gestione delle decisioni tramite rete Edge

* Accesso al profilo Edge in tempo reale. Nel profilo saranno disponibili solo i tipi di pubblico e gli attributi di profilo Edge proiettati.

## Documentazione correlata

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=it)
* [Gestione delle decisioni per Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=it)
* [Descrizione del prodotto Adobe Journey Optimizer](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer.html)
* [Descrizione del prodotto Adobe Decision Management](https://helpx.adobe.com/it/legal/product-descriptions/offer-decisioning-app-service.html)
