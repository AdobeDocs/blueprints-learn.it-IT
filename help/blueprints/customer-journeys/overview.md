---
title: Blueprint per customer journey
description: Offri esperienze cliente individuali, puntuali e orchestrate su diversi schermi.
solution: Journey Optimizer, Campaign, Experience Platform
exl-id: 273d024f-a220-4336-89f2-e3bffafcdc37
TQID: https://experienceleague.adobe.com/vJUJiLr7je-Pp2daoYoNYipfVBRyaEYNv-XCx9PrjzM
product_v2: id: cb954087-f4fc-4456-afb9-e939cabcdc79id: dfc56824-e8b9-499e-85d4-21aedb507314id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: a37e4ecd-c740-426a-addf-cb1b483c5c5aid: c132d929-fa62-4271-803e-b823be07b914id: d998adac-2f81-400b-a669-d07bb196e4ebid: daec7ead-f475-492a-a3b3-02ae08565d6fid: df64005d-8f9a-422e-ba4d-c6f6dc3454b4id: fe338112-e2ce-4876-8989-fc4d497613f1
subfeature_v2: id: d1823595-9241-4128-8a33-e4ac3bf08773
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5520579-b31f-4df7-9281-f0d9f91e2edcid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: bce87dde-a4ab-44c9-8a18-ad66e4ddb377id: df401a2a-327d-468c-a5e4-b7b7ccd071a0id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: a99add31cc9f485db119ca00426798545e6a7316
workflow-type: tm+mt
source-wordcount: 235
ht-degree: 13%

---

# Blueprint per customer journey

I team di marketing moderni richiedono piattaforme in grado di supportare sia il coinvolgimento reattivo (risposta ai comportamenti dei singoli clienti) che l’estensione proattiva (outreach proattivo), avviando campagne che guidano il pubblico nei funnel di conversione. Questi casi d’uso si estendono su canali come e-mail, SMS, push e, in misura crescente, su canali web e in-app.

Adobe Journey Optimizer e Adobe Campaign v8 supportano due modelli fondamentali per il coinvolgimento dei clienti:

- Percorsi attivati dal cliente: orchestrazione basata su eventi e in tempo reale, basata su comportamenti e segnali individuali.
- Campagne avviate dal brand: push con tempistica strategica che introducono i tipi di pubblico nei funnel di coinvolgimento in base alla segmentazione o alla logica di business.

Entrambe le soluzioni consentono la comunicazione in uscita tra canali tradizionali e digitali. AJO supporta inoltre l’integrazione con i canali in entrata (ad esempio, app web e mobili) tramite i servizi di condivisione dello stato del pubblico e decisioning, consentendo la personalizzazione unificata cross-channel.

La scelta tra questi strumenti dipende da considerazioni architetturali quali la tolleranza di latenza, i requisiti di canale, la strategia di integrazione dei dati e la scalabilità.

<br>

| Blueprint | Descrizione | Architettura |
|---|---|:---:|
| **[Adobe Journey Optimizer](journey-optimizer/journey-optimizer-overview.md)** | Combina l&#39;orchestrazione del profilo 1:1 basata sugli eventi con comunicazioni del brand basate sul pubblico su più canali come e-mail, sms, web, push, messaggi in-app, desktop e così via. | <img src="journey-optimizer/images/ajo-architecture.svg" alt="Architettura di riferimento per il blueprint Journey Optimizer" style="width:75%; border:1px solid #4a4a4a" class="modal-image" /> |
| **[Adobe [!DNL Campaign] v8](campaign-v8/campaign-v8-overview.md)** | Focalizzato sulla gestione di campagne multicanale basata su batch, ideale per i canali di marketing tradizionali come e-mail, SMS e direct mail. | <img src="campaign-v8/images/campaign-v8-architecture.svg" alt="Architettura di riferimento per il blueprint per Campaign v8" style="width:75%; border:1px solid #4a4a4a" class="modal-image" /> |

<br>

## Blueprint obsoleti

| Blueprint | Architettura |
|---|:---:|
| **[Adobe [!DNL Campaign] v7](campaign-v7/campaign-v7-overview.md)** | <img src="campaign-v7/images/campaign-v7-architecture.svg" alt="Architettura di riferimento per il blueprint per Campaign v7" style="width:50%; border:1px solid #4a4a4a" class="modal-image" /> |