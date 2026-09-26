---
title: Attivazione di Adobe Real-Time CDP
description: Architettura di riferimento per l’attivazione di tipi di pubblico e dati di profilo da Adobe Real-Time CDP a destinazioni per annunci pubblicitari, social, archiviazione cloud e aziendali.
solution: Real-Time Customer Data Platform, Experience Platform
source-git-commit: ce7331f279a6e59db95ca3b763148440598cde84
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%
---
# Attivazione di Adobe Real-Time CDP

Questa architettura mostra come Adobe [!DNL Real-Time Customer Data Platform] ([!DNL Real-Time CDP]) attiva tipi di pubblico e dati di profilo a destinazioni pubblicitarie, social, archiviazione cloud e enterprise tramite flussi di dati in streaming e batch.

## Attivazione di tipi di pubblico e profili

L&#39;architettura illustra il percorso di attivazione condivisa da tipi di pubblico e profili [!DNL Real-Time CDP] alle applicazioni di destinazione. Include l&#39;attivazione delle destinazioni per le piattaforme pubblicitarie e social, nonché le destinazioni aziendali utilizzate per l&#39;archiviazione, l&#39;analisi e i flussi di lavoro delle applicazioni a valle.

![Architettura di attivazione profilo e pubblico di Adobe Real-Time CDP](assets/real_time_cdp_activation.png){width="1000" zoomable="yes"}

## Modelli di casi d’uso supportati

L’architettura precedente supporta i seguenti modelli di casi d’uso:

- [Attivazione del pubblico alle destinazioni](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md): attiva i tipi di pubblico valutati per pubblicità, social, archiviazione cloud, CRM e altre destinazioni Enterprise.
- [Personalizzazione Web visitatore anonimo](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md): supporta l&#39;attivazione del pubblico e la personalizzazione basata sul profilo nei canali digitali.

## Flussi di dati primari e punti di integrazione

- Acquisire dati del cliente da più origini in [!DNL Real-Time CDP].
- Unificare gli attributi di identità e profilo in [!DNL Real-Time Customer Profile].
- Valuta i profili in tipi di pubblico per l’attivazione.
- Trasmetti o batch le modifiche del pubblico e del profilo alle destinazioni per annunci pubblicitari, social, archiviazione cloud e aziendali.
- Utilizza i dati di profilo e pubblico attivati nei flussi di lavoro di marketing, vendita, supporto, analisi e personalizzazione a valle.

## Ulteriori informazioni

- [Destinazioni di Adobe Real-Time CDP](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/home)
- [Attivare i tipi di pubblico nelle destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Guardrail di Adobe Real-Time CDP](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/guardrails/overview)
