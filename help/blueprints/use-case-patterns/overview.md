---
title: Use Case Patterns
description: Learn about the use case patterns for implementing Adobe Experience Platform and applications to achieve key business objectives.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
doc-type: overview-page
exl-id: 58caa6ad-0d1c-4290-9614-c68c9c9028bb
source-git-commit: 27f7e230982807ec70ca96af7f737944a6588f27
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 0%

---

# Use case patterns

Use case patterns define repeatable implementation approaches for Adobe Experience Platform and applications. Each pattern describes a specific capability, the function chain that delivers it, the applications involved, and the [key business objectives](/help/blueprints/business-objectives/overview.md) it supports.

Use the tables below to find the pattern that matches your implementation needs, then follow the link to the full implementation reference including options, phases, decision guidance, and Experience League documentation.

## Audience building &amp; activation

The following patterns help you build, evaluate, and activate audience segments across channels and destinations.

| Pattern | Primary Capability | Core Solutions |
| --- | --- | --- |
| [Audience activation to destinations](audience-building-activation/audience-activation-to-destinations.md) | Evaluate and publish audience segments to external destinations for targeting or suppression | [!DNL Real-Time CDP] |
| [Audience Collaboration](audience-building-activation/audience-collaboration-segment-match.md) | Share and match audience segments across sandboxes or organizations using Segment Match | [!DNL Real-Time CDP], [!DNL Experience Platform] |
| [Inoltro eventi](audience-building-activation/event-forwarding.md) | Forward real-time event data collected via Edge Network to non-Adobe destinations | [!DNL Experience Platform] (Edge Network, event forwarding) |
| [Attivazione pubblico B2B](audience-building-activation/b2b-audience-activation.md) | Activate account-based B2B audiences across web, email, and advertising channels | [!DNL Real-Time CDP] B2B edition |

## Personalizzazione

The following patterns deliver tailored experiences to known and unknown visitors across web and app surfaces.

| Pattern | Primary Capability | Core Solutions |
| --- | --- | --- |
| [Anonymous visitor web personalization](personalization/anonymous-visitor-web-personalization.md) | Deliver personalized content based on in-session behavioral signals for unidentified visitors | [!DNL Journey Optimizer] (canale web), [!DNL Real-Time CDP] |
| [Personalizzazione web/app visitatore noto](personalization/known-visitor-web-app-personalization.md) | Distribuisci contenuti personalizzati, offerte o promozioni ai visitatori identificati in base al profilo in tempo reale e all’iscrizione al segmento | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Offer Decisioning](personalization/offer-decisioning.md) | Utilizza la logica decisionale centralizzata per selezionare l’offerta o il contenuto migliore per un profilo tra canali diversi | [!DNL Journey Optimizer] (Decisioning), [!DNL Real-Time CDP] |
| [Consigli comportamentali](personalization/behavioral-recommendation.md) | Generare consigli su articoli e contenuti utilizzando strategie di selezione e modelli di classificazione | [!DNL Journey Optimizer] (Decisioning), [!DNL Real-Time CDP] |

## Gestione e orchestrazione delle campagne

I seguenti modelli coprono la consegna di messaggi pianificata, attivata e in più passaggi tra canali.

| Pattern | Funzionalità principale | Soluzioni di base |
| --- | --- | --- |
| [Attivazione messaggi in uscita in batch](campaign-management-orchestration/batch-outbound-message-activation.md) | Valuta un pubblico, quindi consegna un messaggio in uscita pianificato in un’esecuzione batch singola | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Messaggistica attivata da eventi](campaign-management-orchestration/event-triggered-messaging.md) | Ascolta un evento comportamentale o di sistema in tempo reale, quindi distribuisci un messaggio contestuale al profilo che attiva | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [percorso orchestrato con più passaggi](campaign-management-orchestration/multi-step-orchestrated-journey.md) | Guida un profilo attraverso un percorso multi-touch diramato con attese, condizioni e più azioni messaggio | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [percorso cross-channel con decisioning](campaign-management-orchestration/cross-channel-journey-with-decisioning.md) | Orchestrazione di un percorso in più passaggi che incorpora decisioni in tempo reale per selezionare canali, contenuti o offerte ottimali | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Acquisto di attività di marketing e gestione dei percorsi basate sui gruppi](campaign-management-orchestration/buying-group-based-marketing.md) | Sviluppare percorsi a livello di account che qualifichino i lead in gruppi di acquisto per migliorare l’efficacia del marketing B2B | [!DNL Journey Optimizer] B2B edition, [!DNL Real-Time CDP] B2B edition |

## Analisi

I seguenti modelli supportano l’analisi dei comportamenti e delle prestazioni cross-channel.

| Pattern | Funzionalità principale | Soluzioni di base |
| --- | --- | --- |
| [Analisi dei clienti e generazione insight](analysis/customer-analytics-insight-generation.md) | Creare aree di lavoro di analisi cross-channel, metriche calcolate e dashboard per l’analisi del comportamento e delle prestazioni | [!DNL Customer Journey Analytics], [!DNL Experience Platform] |
| [Analisi B2B](analysis/b2b-analytics.md) | Includere informazioni a livello di account B2B nell’analisi del percorso clienti cross-channel | [!DNL Customer Journey Analytics] B2B edition, [!DNL Real-Time CDP] B2B edition |

## Esperienza conversazionale

I seguenti modelli consentono interazioni conversazionali basate sull’intelligenza artificiale e brand-safe sulle proprietà digitali.

| Pattern | Funzionalità principale | Soluzioni di base |
| --- | --- | --- |
| [Esperienza di conversazione Brand Concierge](conversational-experience/brand-concierge-conversational-experience.md) | Trasforma le proprietà digitali in esperienze di conversazione basate sull’intelligenza artificiale e brand-safe che guidano l’individuazione dei clienti | [!DNL Brand Concierge], [!DNL Experience Platform], [!DNL Real-Time CDP] |

## Selettore scenario

Utilizza questa guida quando uno scenario potrebbe adattarsi plausibilmente a più di un pattern. Rispondere alle domande di diramazione per trovare il pattern principale, quindi estendere facoltativamente con i pattern elencati.

### Riconquista con offerta di incentivo

*Un cliente decaduto non ha acquistato da 90 giorni. Desideri coinvolgerli di nuovo con un&#39;offerta mirata.*

- **La selezione delle offerte è dinamica (diversi clienti ricevono offerte diverse in base all&#39;idoneità o alla classificazione)?**
   - Sì → [Offer decisioning](personalization/offer-decisioning.md) come livello di offerta, racchiuso in [percorso orchestrato in più passaggi](campaign-management-orchestration/multi-step-orchestrated-journey.md) per la sequenza di ricoinvolgimento
   - No (stessa offerta a tutti i clienti non più validi) → [Solo percorso orchestrato in più passaggi](campaign-management-orchestration/multi-step-orchestrated-journey.md)

### Follow-up post acquisto

*Un cliente ha appena completato un acquisto. You want to send a confirmation, cross-sell recommendation, and loyalty reward notification.*

- **Does the sequence require adaptive branching based on real-time events (e.g., reward claimed, product reviewed)?**
   - Yes → [Multi-step orchestrated journey](campaign-management-orchestration/multi-step-orchestrated-journey.md)
   - No (fixed sequence, no branching) → [Batch outbound message activation](campaign-management-orchestration/batch-outbound-message-activation.md)
- **Does it include personalized product recommendations?**
   - Yes → Extend with [Behavioral recommendation](personalization/behavioral-recommendation.md) at the content layer

### Loyalty milestone personalization

*A customer reaches a new loyalty tier. You want to show personalized web content and send a congratulatory message.*

- **Is the web content personalized (different content per tier or segment)?**
   - Yes → [Known-visitor web/app personalization](personalization/known-visitor-web-app-personalization.md) for the web surface
- **Is the outbound message a single send or a nurture sequence?**
   - Single send → [Event-triggered messaging](campaign-management-orchestration/event-triggered-messaging.md)
   - Sequence → [Multi-step orchestrated journey](campaign-management-orchestration/multi-step-orchestrated-journey.md)

### Re-engagement campaign

*A segment of inactive users needs a multi-touch reactivation sequence.*

- **Do individual messages need to select from multiple offer variants in real time?**
   - Yes → [Cross-channel journey with decisioning](campaign-management-orchestration/cross-channel-journey-with-decisioning.md)
   - No → [Multi-step orchestrated journey](campaign-management-orchestration/multi-step-orchestrated-journey.md)
