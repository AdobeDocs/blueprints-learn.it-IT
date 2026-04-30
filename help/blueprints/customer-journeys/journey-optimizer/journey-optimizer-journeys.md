---
title: '[!DNL Journey Optimizer] - Messaggistica attivata e blueprint Adobe Experience Platform'
description: Esegui messaggi ed esperienze attivate utilizzando Adobe Experience Platform come hub centrale per lo streaming di dati, profili dei clienti e segmentazione.
solution: Journey Optimizer
exl-id: 70573eb9-cd69-4fe6-b2ae-dae81665a308
TQID: https://experienceleague.adobe.com/MuodOvJ52G9lmUAmsuj06q1aTXkRg7W0Bj6nxLp96N8
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
feature_v2:
  - id: a653cc2e-bc85-4353-a306-399e5b247978
  - id: d998adac-2f81-400b-a669-d07bb196e4eb
  - id: fe338112-e2ce-4876-8989-fc4d497613f1
  - id: fe96aceb-8194-4a8a-a6b0-75302d02804d
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 357
ht-degree: 12%

---

# [!DNL Journey Optimizer] - Blueprint Percorsi

>[!TIP]
>Questo blueprint è disponibile anche come [modello di casi d&#39;uso](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) in Gestione e orchestrazione campagne.

I Percorsi Adobe Journey Optimizer sono flussi di lavoro basati su eventi e in tempo reale che offrono esperienze personalizzate e in più passaggi in base ai comportamenti dei singoli clienti. Supportano un’ampia gamma di canali, tra cui e-mail, SMS, notifiche push, messaggistica in-app, esperienze basate su codice e integrazioni personalizzate basate su API, consentendo ai brand di coinvolgere i clienti in modo contestuale attraverso i punti di contatto preferiti.

<br>

## Architettura

<img src="images/ajo-journeys-architecture.svg" alt="Architettura di riferimento Adobe Journey Optimizer - Blueprint Percorsi" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Considerazioni sull&#39;architettura dei Percorsi

- **Aggiornamento profilo**: i Percorsi AJO si basano su aggiornamenti in tempo reale del profilo cliente. Assicurati che le origini dati che alimentano in Adobe Experience Platform (AEP) siano configurate per l’acquisizione a bassa latenza per mantenere l’accuratezza del profilo.
- **Elaborazione eventi scalabile:** Assicurarsi che l&#39;infrastruttura possa gestire elevati volumi di trigger di percorso e di recapito dei messaggi.
- **Integrazione modulare:** API di progettazione e azioni personalizzate per collegare AJO a sistemi esterni per la personalizzazione dinamica.
- **Risoluzione identità**: è fondamentale unire in modo accurato le identità dei clienti tra dispositivi e canali diversi. Le identità non allineate possono portare a percorsi interrotti o mal indirizzati.
- **Tempistica qualifica segmento**: i percorsi basati sul pubblico dipendono dall&#39;appartenenza al segmento. Scopri la frequenza con cui vengono valutati i segmenti e come tale tempistica influisce sull’ingresso nel percorso e sulla personalizzazione.
- **Condizioni di ingresso Percorso**: i profili devono soddisfare condizioni specifiche per poter accedere a un percorso. Queste condizioni devono essere attentamente progettate per evitare esclusioni o sovrapposizioni involontarie.
- **Valutazione del pubblico e latenza**: i passaggi di lettura del pubblico dipendono dalle valutazioni dei segmenti in Adobe Experience Platform, che potrebbero non verificarsi in tempo reale. Crea percorsi consapevoli della frequenza e della latenza di valutazione per evitare ritardi nella qualificazione del pubblico e garantire una personalizzazione tempestiva.

<br>

## Guardrail

[Collegamento prodotto guardrail [!DNL Journey Optimizer]](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[Guardrail e guida alla latenza end-to-end](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

<br>

## Documentazione correlata

- [[!DNL Experience Platform] documentazione](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
- [Documentazione di [!DNL Experience Platform] tag](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it)
- [[!DNL Experience Platform Mobile SDK] documentazione](https://experienceleague.adobe.com/docs/mobile.html)
- [[!DNL Journey Optimizer] documentazione](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html)
- [[!DNL Journey Optimizer] descrizione prodotto](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer.html)
