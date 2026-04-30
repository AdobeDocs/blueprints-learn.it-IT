---
title: Accesso in tempo reale al profilo Edge per Personalization web e mobile
description: '[!UICONTROL Accesso al Profilo cliente in tempo reale] ai server Edge di per fornire contesto per la personalizzazione web e mobile in tempo reale.'
solution: Real-Time Customer Data Platform, Data Collection
kt: 719
exl-id: 61b81d00-c4bd-41b2-8161-683814947b56
TQID: https://experienceleague.adobe.com/H59c3UBbNCQFs3H0VL5iVDKKZ5D3CFt4ri2RVwNlq7s
product_v2: id: fdddec33-c9cb-4459-b8b6-2664395a6f10
feature_v2: id: ba929a52-9339-4154-9487-317dc875a3c7
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: bce87dde-a4ab-44c9-8a18-ad66e4ddb377id: c4147b6e-073b-4d3c-9ab1-d60f2f4434efid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: d3cdead0-685a-4489-9250-4bb709942f66id: e0eb8757-182f-49f3-94a4-1587d16f5094id: e1e0219c-f879-479f-8427-888ed2a6e9c2id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 631
ht-degree: 8%

---

# Accesso in tempo reale al profilo Edge per Personalization web e mobile

>[!TIP]
>Questo blueprint è disponibile anche come [caso d&#39;uso](/help/blueprints/use-case-patterns/personalization/edge-profile-access.md) in Personalization.

Il blueprint Real-time Edge Profile Access for Web and Mobile Personalization mostra come le applicazioni web e mobili possono accedere al [!UICONTROL Profilo cliente in tempo reale] di Adobe Experience Platform alla periferia per una personalizzazione ad alta velocità e bassa latenza.

Le applicazioni possono accedere agli attributi del profilo in tempo reale e ai tipi di pubblico periferici con latenza di millisecondi. Gli attributi, le appartenenze al pubblico e le funzioni basate su modelli memorizzati nel profilo come attributi sono accessibili in tempo reale per la personalizzazione della stessa pagina e della pagina successiva su canali web e mobili.

Con questa funzionalità, puoi fornire esperienze altamente personalizzate sui tuoi siti web e applicazioni mobili basate sul Profilo cliente in tempo reale, inclusi tipi di pubblico derivati da comportamenti in tempo reale, attributi acquisiti nel Profilo cliente in tempo reale e informazioni calcolate.

>[!NOTE]
>
>L’accesso al profilo di Edge è progettato specificamente per casi di utilizzo ad alta velocità effettiva e a bassa latenza, come la personalizzazione in entrata web/mobile e il Offer Decisioning in tempo reale. Per scenari di throughput inferiore, come il supporto assistito da agente o le interazioni di vendita, l’API di ricerca del profilo Hub è più appropriata. Per l&#39;accesso al profilo basato su hub, vedere il blueprint [Real-time Profile Access for Support and Sales Scenarios](customer-activity.md).

## Applicazioni

* Real-time Customer Data Platform
* Raccolta dati di Adobe Experience Platform (Web SDK / Mobile SDK)
* API server di Edge Network

## Casi di utilizzo

* Personalizzazione in tempo reale su canali web e mobili per esperienze cliente note
* Personalizzazione della stessa pagina e della pagina successiva basata su attributi di profilo e pubblico in tempo reale
* Personalizzazione dei contenuti e delle offerte basata sui profili dei clienti, inclusi dati comportamentali in tempo reale, attributi e informazioni calcolate
* Integrazione con motori di personalizzazione, sistemi di gestione dei contenuti e applicazioni esterne per decisioni in tempo reale
* Test e ottimizzazione dei contenuti con contesto di profilo in tempo reale

## Diagramma architettura

<img src="assets/real-time-edge-lookup.svg" alt="Architettura di riferimento per l’accesso ai profili Edge per web e Personalization mobile" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## Guardrail

* [Guardrail per [!UICONTROL dati Profilo cliente in tempo reale]](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)
* [Guardrail di Edge Network](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* I profili Edge hanno un TTL (time-to-live) di 14 giorni. Se un utente non è attivo sul server Edge per 14 giorni, il profilo Edge potrebbe scadere e richiedere il recupero dall’hub, il che potrebbe influire sulla personalizzazione della prima pagina.
* La funzione di personalizzazione di Edge supporta la valutazione in tempo reale dell’iscrizione al pubblico per i tipi di pubblico che soddisfano i criteri di segmentazione Edge. I tipi di pubblico in batch e in streaming dall’hub sono disponibili anche al limite con la configurazione appropriata.

## Documentazione correlata

### Configurazioni di destinazione

* [Connessione Personalization personalizzata](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) - Guida all&#39;implementazione primaria
* [Panoramica sulle destinazioni di Personalization](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/overview)
* [Attivare i tipi di pubblico per Edge Personalization Destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)
* [Cercare in tempo reale gli attributi del profilo sul bordo](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-profile-lookup)

### Documentazione di SDK

* [Documentazione di Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html)
* [Documentazione di Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/)
* [Documentazione API del server Edge Network](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=it)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it)
* [Risposte ai comandi in Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html)

### Documentazione su profilo e segmentazione

* [[!UICONTROL Documentazione del profilo cliente in tempo reale]](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)
* [Guardrail del profilo](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)

### Tutorial

* [Personalizzazione dell’hit successivo con Real-Time CDP e Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html)
* [Configurazione dello stream di dati](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=it)
