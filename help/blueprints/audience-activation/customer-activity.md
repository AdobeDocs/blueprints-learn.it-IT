---
title: Accesso al profilo in tempo reale per scenari di supporto e vendita
description: Le ricerche in [!UICONTROL Real-time Customer Profile] forniscono informazioni sul contesto utili per fornire assistenza tecnica e commerciale mediante un operatore.
solution: Data Collection
kt: 7195
exl-id: 3616cbf1-2e59-4e68-a1ff-1d2e3b344a1c
TQID: https://experienceleague.adobe.com/Ci9pUbGCLQ9uhlQ9l1na7A2NiI9CpCRMLrUSN6lSOnU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
  - id: ba929a52-9339-4154-9487-317dc875a3c7
  - id: c132d929-fa62-4271-803e-b823be07b914
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
  - id: e5ae22e3-a3b0-46ed-804f-9abf1bbe3e74
  - id: ee602049-8a18-43df-9299-a689a025a371
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 368
ht-degree: 54%

---

# Accesso al profilo in tempo reale per scenari di supporto e vendita

>[!TIP]
>Questo blueprint è disponibile anche come [modello di casi d&#39;uso](/help/blueprints/use-case-patterns/audience-building-activation/real-time-profile-lookup.md) in Creazione e attivazione pubblico.

Il blueprint Real-time Profile Access for Support and Sales Scenarios mostra come le applicazioni esterne possono accedere al [!UICONTROL Profilo cliente in tempo reale] di Adobe Experience Platform.

Le applicazioni esterne possono accedere ai profili mediante una richiesta GET tramite API. Gli attributi, gli eventi, le appartenenze ai segmenti e le funzioni basate sul modello memorizzati nel profilo possono quindi essere utilizzati anche in tali applicazioni esterne non Adobe.

Grazie a questa funzionalità, quando un cliente chiama il call center è possibile far emergere un contesto articolato. Gli operatori del supporto potrebbero, ad esempio, avere visibilità sul valore del ciclo di vita del cliente, sulla sua propensione all’abbandono o sulle campagne di marketing a cui è stato esposto. Gli agenti di vendita possono inoltre trarre vantaggio da un maggior contesto o da una migliore comprensione del cliente.

>[!NOTE]
>
>La ricerca del profilo nell’hub non è destinata a casi di utilizzo ad alta velocità effettiva e a bassa latenza, come la personalizzazione in entrata web/mobile. La ricerca del profilo nell’hub è destinata a scenari di latenza inferiore, ad esempio per il supporto assistito da agenti o per le interazioni di vendita. Per scenari a bassa latenza e a throughput elevato, come la personalizzazione web/mobile o il Offer Decisioning in tempo reale, è necessario sfruttare il profilo Edge. Il profilo Edge consente l&#39;accesso in tempo reale tramite [Connessione Personalization personalizzata](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) di Real-time Customer Data Platform.

## Casi di utilizzo

* Contesto del consumatore più approfondito, per le interazioni tramite operatore, come le esperienze di assistenza tecnica o commerciale. Utilizzando la ricerca del profilo in Experience Platform, gli agenti possono ricevere maggiori informazioni di contesto sul cliente, come acquisti recenti, interazioni con le campagne, tendenze, pubblico di appartenenza e altri attributi e informazioni che vengono memorizzati nel profilo del cliente in tempo reale.

## Architettura

<img src="assets/customer_activity_hub.svg" alt="Architettura di riferimento del blueprint per hub delle attività dei clienti" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## Guardrail

* [Guardrail per [!UICONTROL dati Profilo cliente in tempo reale]](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)

## Documentazione correlata

* [Descrizione del prodotto Adobe Experience Platform Activation](https://helpx.adobe.com/it/legal/product-descriptions/adobe-experience-platform0.html)
* [[!UICONTROL Documentazione del profilo cliente in tempo reale]](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=it)
* [Guardrail del profilo](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)
* [API di ricerca profilo](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
