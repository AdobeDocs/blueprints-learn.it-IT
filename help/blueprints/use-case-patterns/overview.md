---
title: Modelli di casi d’uso
description: Scopri i modelli di casi d’uso per l’implementazione di Adobe Experience Platform e delle applicazioni per raggiungere gli obiettivi aziendali chiave.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
doc-type: overview-page
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---


# Modelli di casi d’uso

I modelli di casi d’uso definiscono approcci di implementazione ripetibili per Adobe Experience Platform e le applicazioni. Ogni modello descrive una funzionalità specifica, la catena di funzioni che la distribuisce, le applicazioni coinvolte e gli [obiettivi aziendali chiave](/help/blueprints/business-objectives/overview.md) supportati.

Utilizza le tabelle seguenti per trovare il modello che soddisfa le tue esigenze di implementazione, quindi segui il collegamento alla documentazione completa sull’implementazione, comprese opzioni, fasi, guida decisionale e documentazione di Experience League.

## Creazione e attivazione del pubblico

I seguenti modelli consentono di creare, valutare e attivare segmenti di pubblico tra canali e destinazioni.

| Pattern | Funzionalità principale | Soluzioni di base |
| --- | --- | --- |
| [Audience Activation alle destinazioni](audience-building-activation/audience-activation-to-destinations.md) | Valutare e pubblicare segmenti di pubblico in destinazioni esterne per il targeting o l’eliminazione | [!DNL Real-Time CDP] |
| [Audience Collaboration con corrispondenza segmento](audience-building-activation/audience-collaboration-segment-match.md) | Condividere e abbinare segmenti di pubblico tra sandbox o organizzazioni utilizzando Segment Match (Corrispondenza segmenti) | [!DNL Real-Time CDP], [!DNL Experience Platform] |
| [Inoltro eventi](audience-building-activation/event-forwarding.md) | Inoltra i dati evento in tempo reale raccolti tramite Edge Network a destinazioni non Adobe | [!DNL Experience Platform] (Edge Network, inoltro eventi) |
| [Attivazione del pubblico B2B](audience-building-activation/b2b-audience-activation.md) | Attiva tipi di pubblico B2B basati sull’account tra canali web, e-mail e pubblicitari | [!DNL Real-Time CDP] B2B edition |

## Personalizzazione

I seguenti modelli forniscono esperienze personalizzate a visitatori noti e sconosciuti su superfici web e app.

| Pattern | Funzionalità principale | Soluzioni di base |
| --- | --- | --- |
| [Visitatore anonimo Web Personalization](personalization/anonymous-visitor-web-personalization.md) | Distribuisci contenuti personalizzati in base a segnali comportamentali durante la sessione per visitatori non identificati | [!DNL Journey Optimizer] (canale web), [!DNL Real-Time CDP] |
| [Web visitatore conosciuto/App Personalization](personalization/known-visitor-web-app-personalization.md) | Distribuisci contenuti personalizzati, offerte o promozioni ai visitatori identificati in base al profilo in tempo reale e all’iscrizione al segmento | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Offer Decisioning](personalization/offer-decisioning.md) | Utilizza la logica decisionale centralizzata per selezionare l’offerta o il contenuto migliore per un profilo tra canali diversi | [!DNL Journey Optimizer] (Decisioning), [!DNL Real-Time CDP] |
| [Consigli comportamentali](personalization/behavioral-recommendation.md) | Generare consigli su articoli e contenuti utilizzando strategie di selezione e modelli di classificazione | [!DNL Journey Optimizer] (Decisioning), [!DNL Real-Time CDP] |

## Gestione e orchestrazione delle campagne

I seguenti modelli coprono la consegna di messaggi pianificata, attivata e in più passaggi tra canali.

| Pattern | Funzionalità principale | Soluzioni di base |
| --- | --- | --- |
| [Attivazione messaggi in uscita in batch](campaign-management-orchestration/batch-outbound-message-activation.md) | Valuta un pubblico, quindi consegna un messaggio in uscita pianificato in un’esecuzione batch singola | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Messaggi attivati da eventi](campaign-management-orchestration/event-triggered-messaging.md) | Ascolta un evento comportamentale o di sistema in tempo reale, quindi distribuisci un messaggio contestuale al profilo che attiva | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Percorso orchestrato con più passaggi](campaign-management-orchestration/multi-step-orchestrated-journey.md) | Guida un profilo attraverso un percorso multi-touch diramato con attese, condizioni e più azioni messaggio | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Percorso cross-channel con decisioning](campaign-management-orchestration/cross-channel-journey-with-decisioning.md) | Orchestrazione di un percorso in più passaggi che incorpora decisioni in tempo reale per selezionare canali, contenuti o offerte ottimali | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Acquisto di attività di marketing e gestione dei Percorsi basate sui gruppi](campaign-management-orchestration/buying-group-based-marketing.md) | Sviluppare percorsi a livello di account che qualifichino i lead in gruppi di acquisto per migliorare l’efficacia del marketing B2B | [!DNL Journey Optimizer] B2B edition, [!DNL Real-Time CDP] B2B edition |

## Analisi

I seguenti modelli supportano l’analisi dei comportamenti e delle prestazioni cross-channel.

| Pattern | Funzionalità principale | Soluzioni di base |
| --- | --- | --- |
| [Analisi dei clienti e generazione Insight](analysis/customer-analytics-insight-generation.md) | Creare aree di lavoro di analisi cross-channel, metriche calcolate e dashboard per l’analisi del comportamento e delle prestazioni | [!DNL Customer Journey Analytics], [!DNL Experience Platform] |
| [Analisi B2B](analysis/b2b-analytics.md) | Includere informazioni a livello di account B2B nell’analisi del percorso clienti cross-channel | [!DNL Customer Journey Analytics] B2B edition, [!DNL Real-Time CDP] B2B edition |

## Esperienza conversazionale

I seguenti modelli consentono interazioni conversazionali basate sull’intelligenza artificiale e brand-safe sulle proprietà digitali.

| Pattern | Funzionalità principale | Soluzioni di base |
| --- | --- | --- |
| [Esperienza conversazionale Brand Concierge](conversational-experience/brand-concierge-conversational-experience.md) | Trasforma le proprietà digitali in esperienze di conversazione basate sull’intelligenza artificiale e brand-safe che guidano l’individuazione dei clienti | [!DNL Brand Concierge], [!DNL Experience Platform], [!DNL Real-Time CDP] |
