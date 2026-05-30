---
title: Percorso cross-channel con decisioning
description: Scopri come orchestrare un percorso con più passaggi che incorporano decisioni in tempo reale per selezionare canali, contenuti o offerte ottimali.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: eabdd91f-bb7d-4de3-adb5-5940d3ca4a78
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1983'
ht-degree: 5%

---

# Percorso cross-channel con decisioni

Questa guida descrive il percorso cross-channel con modello di caso d&#39;uso decisioning, che utilizza [!DNL Adobe Journey Optimizer] e [!DNL Adobe Real-Time Customer Data Platform] per orchestrare percorsi multi-step e multicanale che incorporano decisioni in tempo reale in uno o più nodi di percorso. È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono comprendere il funzionamento di questo modello, gli obiettivi aziendali supportati, i casi di utilizzo tattici che consente e le applicazioni Adobe coinvolte.

Il percorso cross-channel con decisioning è il modello di orchestrazione delle campagne più sofisticato nell&#39;ecosistema [!DNL Adobe Experience Platform]. Estende percorsi orchestrati in più passaggi incorporando decisioni in tempo reale, utilizzando [!DNL AJO] Decisioning per valutare il contesto corrente di un profilo e selezionare in modo dinamico il canale, il contenuto o l&#39;offerta ottimale in uno o più punti decisionali all&#39;interno dell&#39;area di lavoro del percorso.

## Schema del caso d’uso

**percorso cross-channel con decisioning**

Orchestrazione di un percorso multicanale in più passaggi che incorpora decisioni in tempo reale in uno o più nodi per selezionare il canale, il contenuto o l’offerta ottimale.

**Piano di esecuzione:** Valutazione del pubblico > Esecuzione del Percorso > Nodo di decisione > Selezione canale > Consegna messaggi > Reporting

## Panoramica del caso d’uso

Le organizzazioni devono sempre più spesso fornire percorsi di clienti adattativi e personalizzati che rispondano in modo dinamico al contesto in tempo reale di ogni individuo, anziché seguire una sequenza fissa e predeterminata. Il canale preferito dai clienti, la cronologia del coinvolgimento, il livello di fedeltà, il valore previsto per il ciclo di vita e gli interessi attuali dei prodotti contribuiscono a determinare quale sia l’azione migliore da intraprendere in ogni punto di contatto.

Il percorso cross-channel con il decisioning soddisfa questa esigenza combinando due potenti funzionalità di [!DNL AJO]: l&#39;orchestrazione del percorso (che gestisce il flusso in più passaggi, la tempistica, le condizioni e la distribuzione del canale) e il decisioning (che valuta le regole di idoneità, applica le strategie di classificazione e seleziona l&#39;offerta ottimale o la variante di contenuto a ogni punto decisionale).

Questo modello è appropriato quando:

- Il percorso deve adattarsi in modo dinamico allo stato in tempo reale di ciascun profilo, anziché seguire un canale fisso o una sequenza di contenuti
- Offerte multiple, varianti di contenuto o canali sono candidati in uno o più nodi di percorso e l’opzione migliore deve essere selezionata in base al contesto del profilo
- Per ottimizzare la selezione delle offerte in tutto il percorso è necessaria una classificazione basata su IA o su formula
- L’organizzazione desidera consolidare la logica di selezione dei canali e la gestione delle offerte in un framework decisionale centralizzato anziché mantenere una logica di ramificazione complessa

Il pubblico di destinazione include gli addetti al marketing che gestiscono programmi del ciclo di vita, percorsi di fidelizzazione, sequenze di riconquista e flussi di onboarding in cui la personalizzazione su larga scala richiede un processo decisionale automatizzato in ogni punto di contatto.

>[!NOTE]
>Se il percorso non richiede decisioni dinamiche sui singoli nodi, ad esempio un programma di sviluppo o onboarding a sequenza fissa, vedere [percorso orchestrato in più passaggi](multi-step-orchestrated-journey.md). Tale modello è più semplice da configurare e non richiede AJO Decisioning.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

**[Distribuisci esperienze cliente personalizzate](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
Personalizza contenuti, offerte e messaggi in base a preferenze, comportamenti e fasi del ciclo di vita individuali.
**KPI:** coinvolgimento, tassi di conversione, soddisfazione del cliente (CSAT)

**[Aumenta la fedeltà dei clienti e il valore del ciclo di vita](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
Approfondisci le relazioni con i clienti e massimizza il valore a lungo termine tramite programmi di fidelizzazione, premi e coinvolgimento personalizzato.
**KPI:** Valore ciclo di vita cliente, mantenimento, upselling/cross-selling %

**[Miglioramento della conservazione dei clienti](../../business-objectives/customer-experience/improve-customer-retention.md)**
Coinvolgi e rinnova i clienti esistenti tramite esperienze basate sul valore aggiunto e lo sviluppo di relazioni continuative.
**KPI:** mantenimento, valore del ciclo di vita del cliente, coinvolgimento

**[Incrementa le vendite incrociate e incrementa i ricavi](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
Promuovere prodotti o servizi complementari e di alta qualità ai clienti esistenti in base al comportamento e alla cronologia degli acquisti.
**KPI:** % vendite incrociate/upselling, ricavi incrementali, valore ciclo di vita cliente

## Esempi di casi d’uso tattici

Gli scenari seguenti illustrano come applicare nella pratica il percorso cross-channel con il decisioning.

- **percorso di recupero adattivo**: un percorso in più passaggi in cui il processo decisionale seleziona il canale (e-mail, push o SMS) in base alla cronologia di coinvolgimento di ciascun profilo e seleziona in modo dinamico la migliore offerta di incentivo in base al valore previsto del ciclo di vita
- **percorso del ciclo di vita con le migliori azioni successive**: le decisioni determinano cosa comunicare in ogni fase del ciclo di vita del cliente, scegliendo tra contenuti di onboarding, offerte di cross-selling, premi fedeltà o incentivi alla fidelizzazione
- **Onboarding personalizzato con selezione dinamica dei contenuti**: nuovo percorso di onboarding dei clienti in cui ogni punto di contatto utilizza il decisioning per selezionare i contenuti, i suggerimenti o le offerte di attivazione più rilevanti per la formazione sui prodotti
- **percorso di programmi fedeltà cross-channel con premi personalizzati** — I membri fedeltà progrediscono attraverso un percorso in cui il processo decisionale seleziona offerte di premi personalizzate in base a livello, cronologia acquisti e affinità tra categorie
- **Nuovo coinvolgimento dinamico con ottimizzazione di canali e incentivi** — Nuovo coinvolgimento inattivo del cliente in cui sia il canale di sensibilizzazione che l&#39;incentivo vengono selezionati in modo dinamico per massimizzare la probabilità di risposta
- **Consigli sul ciclo di vita del cliente con contenuti classificati in base all&#39;intelligenza artificiale**: percorso di sviluppo continuo in cui il decisioning basato sull&#39;intelligenza artificiale seleziona i contenuti o i prodotti più rilevanti in ogni punto di contatto

## Indicatori chiave di prestazioni

Utilizza i seguenti KPI per misurare l’efficacia di questo modello di caso d’uso.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Percentuale di completamento percorso | Percentuale di profili che completano l’intero percorso | Rapporto percorso: completato/inserito |
| Tasso di accettazione offerta | Percentuale di offerte selezionate con decisioni che sono coinvolte con (selezionate, riscattate) | Rapporto sulle decisioni: clic sulle offerte/impression delle offerte |
| Tasso di coinvolgimento canale | Percentuali di apertura e clic su ogni canale utilizzato nel percorso | Metriche di consegna per canale nel rapporto del percorso |
| Tasso di conversione | Percentuale di partecipanti al percorso che hanno completato l&#39;azione di conversione target | Tracciamento degli eventi di uscita dal percorso o analisi CJA funnel |
| Percentuale di offerte di fallback | Percentuale di richieste di decisione che restituiscono l’offerta di fallback anziché un’offerta personalizzata | Rapporto Decisioning: selezioni di fallback/selezioni totali |
| Impatto del valore del ciclo di vita del cliente | Variazione di CLV per i partecipanti al percorso rispetto al gruppo di controllo | Analisi per coorte CJA con confronto dei dati di sospensione |
| Ricavi da vendite incrociate/upselling | Ricavi incrementali attribuiti alle offerte selezionate nel processo decisionale | Analisi dell’attribuzione CJA sulle conversioni guidate dall’offerta |
| Decisioning dell’efficacia della classificazione | Differenza di prestazioni tra le offerte classificate in base all’intelligenza artificiale e la selezione casuale/basata sulla priorità | Esperimento A/B che confronta le strategie di classificazione |

## Applicazioni

Per implementare questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Adobe Journey Optimizer] ([!DNL AJO])** — orchestrazione del Percorso (progettazione area di lavoro con più passaggi, condizioni di ingresso, attese, condizioni, criteri di uscita), authoring dei messaggi tra canali, configurazione della superficie di canale, gestione dei conflitti e delle priorità
- **[!DNL Adobe Journey Optimizer]Decisioning** — Gestione di offerte e contenuti, regole di idoneità, strategie di classificazione (priorità, formula, IA), criteri di decisione, posizionamenti, offerte di fallback
- **[!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP])** — Valutazione del pubblico per i segmenti di idoneità delle offerte e delle voci di percorso, arricchimento dei profili con attributi calcolati e punteggi di propensione, applicazione del consenso e della governance
- **[!DNL Adobe Experience Platform] ([!DNL AEP])** — Archivio Profilo cliente in tempo reale, servizio Identity per la risoluzione cross-channel, modellazione dati e infrastruttura di acquisizione

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sulle funzionalità utilizzate in questo modello di caso d’uso.

### Orchestrazione percorso

- [Introduzione ai percorsi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Creare un percorso](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Proprietà del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Attività Read audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Eventi generali](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Eventi di qualificazione del pubblico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Attività Condizione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Attività Attendi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Aggiungere un messaggio in un percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Criteri di uscita](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Gestione voci percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Test del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Pubblicare il percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### Gestione delle decisioni

- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Creare i posizionamenti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Creare regole di decisione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Creare offerte di fallback](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Creare le raccolte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Creare qualificatori di raccolta](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Configurazione dei canali

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delega sottodomini](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Creare pool IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Piani di riscaldamento IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Impostazioni superficie e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configurare il canale SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Authoring e personalizzazione dei messaggi

- [Creare un messaggio e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilizzare i frammenti di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anteprima e test del contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Gestione dei conflitti, delle priorità e delle frequenze

- [Panoramica sulla gestione dei conflitti e delle priorità](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Punteggi di priorità](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identificare potenziali conflitti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Limitazione di percorso e arbitrato](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Regole di frequenza](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### Tipi di pubblico e segmentazione

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Composizione del pubblico](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Reporting e analisi

- [Rapporto live del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Profilo e identità

- [Panoramica del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Panoramica di Customer AI](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Governance dei dati e consenso

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Gestire l’elenco di soppressione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Guardrail

- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Guardrail del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
