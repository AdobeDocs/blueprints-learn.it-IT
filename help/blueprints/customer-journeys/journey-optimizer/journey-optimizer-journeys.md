---
title: '[!DNL Journey Optimizer] - Messaggistica attivata e blueprint Adobe Experience Platform'
description: Esegui messaggi ed esperienze attivate utilizzando Adobe Experience Platform come hub centrale per lo streaming di dati, profili dei clienti e segmentazione.
solution: Journey Optimizer
source-git-commit: 0a3ebcbc6029df46bd988cb8f15ecf838f80c3c9
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 9%

---

# [!DNL Journey Optimizer] - Blueprint Percorsi

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

[[!DNL Journey Optimizer] Collegamento prodotto guardrail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[Guardrail e indicazioni sulla latenza End to End](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html?lang=it)

<br>

## Documentazione correlata

- [[!DNL Experience Platform] documentazione](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
- [[!DNL Experience Platform] Documentazione sui tag](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it)
- [[!DNL Experience Platform Mobile SDK] documentazione](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
- [[!DNL Journey Optimizer] documentazione](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=it)
- [[!DNL Journey Optimizer] descrizione del prodotto](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer.html)