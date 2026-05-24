---
title: Modelli di casi d’uso
description: Scopri i modelli di casi d’uso per l’implementazione di Adobe Experience Platform e delle applicazioni per raggiungere gli obiettivi aziendali chiave.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
doc-type: overview-page
exl-id: 58caa6ad-0d1c-4290-9614-c68c9c9028bb
source-git-commit: e79d9d6490e4f50c4611dd879b53f0e63a90cd65
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 0%

---

# Modelli di casi d’uso

I modelli di casi d’uso definiscono approcci di implementazione ripetibili per Adobe Experience Platform e le applicazioni. Ogni modello descrive una funzionalità specifica, il piano di esecuzione che la distribuisce, le applicazioni coinvolte e i [obiettivi aziendali chiave](/help/blueprints/business-objectives/overview.md) supportati.

Utilizza le tabelle seguenti per trovare il modello che soddisfa le tue esigenze di implementazione, quindi segui il collegamento alla documentazione completa sull’implementazione, comprese opzioni, fasi, guida decisionale e documentazione di Experience League.

## Creazione e attivazione del pubblico

I seguenti modelli consentono di creare, valutare e attivare segmenti di pubblico tra canali e destinazioni.

| Pattern | Funzionalità principale | Soluzioni di base |
| --- | --- | --- |
| [Attivazione del pubblico alle destinazioni](audience-building-activation/audience-activation-to-destinations.md) | Valutare e pubblicare segmenti di pubblico in destinazioni esterne per il targeting o l’eliminazione | [!DNL Real-Time CDP] |
| [Pubblico Collaboration](audience-building-activation/audience-collaboration-segment-match.md) | Condividere e abbinare segmenti di pubblico tra sandbox o organizzazioni utilizzando Segment Match (Corrispondenza segmenti) | [!DNL Real-Time CDP], [!DNL Experience Platform] |
| [Inoltro eventi](audience-building-activation/event-forwarding.md) | Inoltra i dati evento in tempo reale raccolti tramite Edge Network a destinazioni non Adobe | [!DNL Experience Platform] (Edge Network, inoltro eventi) |
| [Ricerca profilo in tempo reale per supporto e vendite](audience-building-activation/real-time-profile-lookup.md) | Ricerche di profili cliente in tempo reale che forniscono contesto per scenari di vendita e supporto assistiti da agenti | [!DNL Real-Time CDP], [!DNL Experience Platform] |
| [Data Science personalizzata per l&#39;arricchimento del profilo](audience-building-activation/data-science-profile-enrichment.md) | Acquisire informazioni basate sulla scienza dei dati in Experience Platform per arricchire il profilo cliente in tempo reale | [!DNL Experience Platform] |

## Personalizzazione

I seguenti modelli forniscono esperienze personalizzate a visitatori noti e sconosciuti su superfici web e app.

| Pattern | Funzionalità principale | Soluzioni di base |
| --- | --- | --- |
| [Personalizzazione Web visitatore anonimo](personalization/anonymous-visitor-web-personalization.md) | Distribuisci contenuti personalizzati in base a segnali comportamentali durante la sessione per visitatori non identificati | [!DNL Journey Optimizer] (canale web), [!DNL Real-Time CDP] |
| [Personalizzazione web/app visitatore noto](personalization/known-visitor-web-app-personalization.md) | Distribuisci contenuti personalizzati, offerte o promozioni ai visitatori identificati in base al profilo in tempo reale e all’iscrizione al segmento | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Offer Decisioning](personalization/offer-decisioning.md) | Utilizza la logica decisionale centralizzata per selezionare l’offerta o il contenuto migliore per un profilo tra canali diversi | [!DNL Journey Optimizer] (Decisioning), [!DNL Real-Time CDP] |
| [Consigli comportamentali](personalization/behavioral-recommendation.md) | Generare consigli su articoli e contenuti utilizzando strategie di selezione e modelli di classificazione | [!DNL Journey Optimizer] (Decisioning), [!DNL Real-Time CDP] |
| [Accesso profilo Edge per Personalization Web/Mobile](personalization/edge-profile-access.md) | Accesso in tempo reale al profilo edge per la personalizzazione di web e dispositivi mobili ad alta velocità, a bassa latenza | [!DNL Real-Time CDP], [!DNL Experience Platform] (Edge Network) |
| [Condivisione del pubblico con Adobe Target](personalization/audience-sharing-with-target.md) | Condividere profili e tipi di pubblico di Real-Time CDP con Adobe Target per la personalizzazione web e mobile dei clienti noti | [!DNL Real-Time CDP], [!DNL Target], [!DNL Experience Platform] |

## Gestione e orchestrazione delle campagne

I seguenti modelli coprono la consegna di messaggi pianificata, attivata e in più passaggi tra canali.

| Pattern | Funzionalità principale | Soluzioni di base |
| --- | --- | --- |
| [Attivazione messaggi in uscita in batch](campaign-management-orchestration/batch-outbound-message-activation.md) | Valuta un pubblico, quindi consegna un messaggio in uscita pianificato in un’esecuzione batch singola | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Messaggistica attivata da eventi](campaign-management-orchestration/event-triggered-messaging.md) | Ascolta un evento comportamentale o di sistema in tempo reale, quindi distribuisci un messaggio contestuale al profilo che attiva | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [percorso orchestrato con più passaggi](campaign-management-orchestration/multi-step-orchestrated-journey.md) | Guida un profilo attraverso un percorso multi-touch diramato con attese, condizioni e più azioni messaggio | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [percorso cross-channel con decisioning](campaign-management-orchestration/cross-channel-journey-with-decisioning.md) | Orchestrazione di un percorso in più passaggi che incorpora decisioni in tempo reale per selezionare canali, contenuti o offerte ottimali | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Orchestrazione in batch di Campaign v8 e messaggistica transazionale](campaign-management-orchestration/campaign-v8-orchestration.md) | Esecuzione di campagne batch, orchestrazione multi-touch, gestione dei dati basata su ETL e messaggistica transazionale in Campaign v8 | [!DNL Campaign] v8 |
| [Integrazione della messaggistica di terze parti con Journey Optimizer](campaign-management-orchestration/third-party-messaging.md) | Integrare Journey Optimizer con sistemi di messaggistica di terze parti per comunicazioni personalizzate tramite API REST | [!DNL Journey Optimizer] |

## Analisi

I seguenti modelli supportano l’analisi dei comportamenti e delle prestazioni cross-channel.

| Pattern | Funzionalità principale | Soluzioni di base |
| --- | --- | --- |
| [Analisi dei clienti e generazione insight](analysis/customer-analytics-insight-generation.md) | Creare aree di lavoro di analisi cross-channel, metriche calcolate e dashboard per l’analisi del comportamento e delle prestazioni | [!DNL Customer Journey Analytics], [!DNL Experience Platform] |

## Attivazione e marketing B2B

I seguenti modelli riguardano scenari di marketing specifici per B2B: pubblico basato su account, orchestrazione di gruppi di acquisto e analisi B2B.

| Pattern | Funzionalità principale | Soluzioni di base |
| --- | --- | --- |
| [Attivazione pubblico B2B](b2b/account-audience-activation.md) | Attiva tipi di pubblico B2B basati sull’account tra canali web, e-mail e pubblicitari | [!DNL Real-Time CDP] B2B edition |
| [Acquisto di attività di marketing e gestione dei percorsi basate sui gruppi](b2b/buying-group-marketing.md) | Sviluppare percorsi a livello di account che qualifichino i lead in gruppi di acquisto per migliorare l’efficacia del marketing B2B | [!DNL Journey Optimizer] B2B edition, [!DNL Real-Time CDP] B2B edition |
| [Analisi B2B](b2b/account-analytics.md) | Includere informazioni a livello di account B2B nell’analisi del percorso clienti cross-channel | [!DNL Customer Journey Analytics] B2B edition, [!DNL Real-Time CDP] B2B edition |
| [Percorsi B2B con dati Marketo](b2b/marketo-data-journeys.md) | Distribuire Journey Optimizer B2B edition con i dati di Marketo per orchestrare percorsi di gruppi di acquisto e coinvolgimento degli account | [!DNL Journey Optimizer] B2B edition, [!DNL Marketo Engage], [!DNL Real-Time CDP] B2B edition |
| [Controller supporti a pagamento B2B AJO](b2b/paid-media-orchestration.md) | Orchestrazione di campagne multimediali a pagamento B2B utilizzando la logica a cascata per assegnare account alle campagne e attivarle nelle destinazioni | [!DNL Journey Optimizer] B2B edition, [!DNL Real-Time CDP] B2B edition |
| [Acquisizione e creazione di Marketo e Workfront](b2b/campaign-intake-and-creation.md) | Automatizzare l’inserimento delle richieste di campagne di marketing e la creazione di programmi Marketo Engage tramite Workfront Forms e Fusion | [!DNL Marketo Engage], [!DNL Workfront], [!DNL Workfront Fusion] |
| [Revisione e approvazione di Marketo e Workfront](b2b/campaign-review-and-approval.md) | Integrare i flussi di lavoro di verifica e approvazione di Workfront con le risorse e-mail di Marketo Engage utilizzando l’automazione Fusion | [!DNL Marketo Engage], [!DNL Workfront], [!DNL Workfront Fusion] |

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

*Un cliente ha appena completato un acquisto. Vuoi inviare una conferma, un consiglio di cross-selling e una notifica di premio fedeltà.*

- **La sequenza richiede diramazioni adattive basate su eventi in tempo reale (ad esempio, premio richiesto, prodotto esaminato)?**
   - Sì → [percorso orchestrato con più passaggi](campaign-management-orchestration/multi-step-orchestrated-journey.md)
   - Nessuna (sequenza fissa, nessuna diramazione) → [Attivazione messaggio batch in uscita](campaign-management-orchestration/batch-outbound-message-activation.md)
- **Include consigli di prodotto personalizzati?**
   - Sì → Estendi con [Consigli comportamentali](personalization/behavioral-recommendation.md) a livello di contenuto

### Personalizzazione milestone fedeltà

*Un cliente raggiunge un nuovo livello fedeltà. Desideri mostrare contenuti web personalizzati e inviare un messaggio di congratulazioni.*

- **Il contenuto Web è personalizzato (contenuto diverso per livello o segmento)?**
   - Sì → [Personalizzazione web/app visitatore noto](personalization/known-visitor-web-app-personalization.md) per la superficie web
- **Il messaggio in uscita è un singolo invio o una sequenza di sviluppo?**
   - Invio singolo → [Messaggistica attivata da eventi](campaign-management-orchestration/event-triggered-messaging.md)
   - Sequenza → [percorso orchestrato con più passaggi](campaign-management-orchestration/multi-step-orchestrated-journey.md)

### Campagna di ricoinvolgimento

*Un segmento di utenti inattivi richiede una sequenza di riattivazione multi-touch.*

- **I singoli messaggi devono essere selezionati da più varianti di offerta in tempo reale?**
   - Sì → [percorso cross-channel con decisioning](campaign-management-orchestration/cross-channel-journey-with-decisioning.md)
   - Nessun → [percorso orchestrato con più passaggi](campaign-management-orchestration/multi-step-orchestrated-journey.md)
