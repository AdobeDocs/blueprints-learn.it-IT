---
title: Percorso orchestrato con più passaggi
description: Scopri come guidare un profilo attraverso un percorso multi-touch diramato con attese, condizioni e più azioni messaggio nel tempo.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 5667b188-1b20-4a85-aebb-74efd5f771a1
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1798'
ht-degree: 5%

---

# Percorso orchestrato in più passaggi

Questa guida descrive il modello di casi d&#39;uso del percorso orchestrato in più passaggi, che utilizza [!DNL Adobe Journey Optimizer] (AJO) e [!DNL Real-Time Customer Data Platform] (RT-CDP) per orchestrare percorsi di clienti multi-touch diramati che distribuiscono più messaggi nel tempo. È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono comprendere il funzionamento di questo modello, gli obiettivi aziendali supportati, i casi di utilizzo tattici che consente e le applicazioni Adobe coinvolte.

## Schema del caso d’uso

**Percorso orchestrato con più passaggi**

Guida un profilo attraverso un percorso multi-touch diramato con attese, condizioni e azioni con più messaggi nel tempo.

**Piano di esecuzione:** Valutazione del pubblico > Esecuzione del Percorso (più nodi) > Diramazione condizione > Consegna messaggi (xN) > Criteri di uscita > Generazione rapporti

## Panoramica del caso d’uso

I percorsi orchestrati in più passaggi sono destinati a scenari aziendali in cui un singolo messaggio non è sufficiente per ottenere il risultato desiderato per il cliente. Invece di un invio una tantum, il percorso guida ogni profilo attraverso una sequenza di punti di contatto, e-mail, messaggi SMS, notifiche push o messaggi in-app, suddivisi su giorni o settimane, con una logica di diramazione che adatta il percorso in base agli attributi del profilo, ai segnali comportamentali o ai dati dell’evento.

Questi percorsi sono il modello di campagna più complesso disponibile in AJO. Combinano una voce basata su pubblico o evento con un’area di lavoro costituita da nodi di azione (messaggi), nodi di condizione (logica di diramazione), nodi di attesa (ritardi) e criteri di uscita (eventi di conversione o timeout). Ogni profilo procede nel percorso in modo indipendente, al proprio ritmo, ricevendo contenuti contestualmente rilevanti in ogni fase.

Questo modello riassume i modelli più semplici: attivazione batch dei messaggi in uscita per campagne a invio singolo e messaggistica attivata da eventi per risposte a evento singolo. Utilizza questo modello quando il caso d’uso richiede di coltivare un profilo attraverso più interazioni nel tempo.

>[!NOTE]
>Se il percorso richiede la selezione dinamica dell&#39;offerta, del contenuto o del canale ottimale nei singoli punti decisionali, consulta [percorso cross-channel con decisioning](cross-channel-journey-with-decisioning.md). Questo modello estende questo modello con l’integrazione di AJO Decisioning.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### Miglioramento della conservazione dei clienti

Coinvolgi e rinnova i clienti esistenti tramite esperienze basate sul valore aggiunto e lo sviluppo di relazioni continuative.

**KPI:** mantenimento, valore del ciclo di vita del cliente, coinvolgimento

[Ulteriori informazioni sul miglioramento della customer retention](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### Migliorare l’onboarding dei clienti

Accelerare il time-to-value per i nuovi clienti con esperienze di benvenuto e percorsi di attivazione semplificati e personalizzati.

**KPI:** coinvolgimento, mantenimento, tassi di conversione

[Ulteriori informazioni su come migliorare l’onboarding dei clienti](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)

### Rivolgersi nuovamente ai clienti inattivi

Recupera i clienti inattivi o inattivi con campagne di riattivazione mirate basate su segnali comportamentali.

**KPI:** coinvolgimento, mantenimento, tassi di conversione

[Ulteriori informazioni sul miglioramento della customer retention](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### Recupera carrelli e percorsi abbandonati

Coinvolgi nuovamente gli utenti che abbandonano durante i flussi di acquisto, applicazione o iscrizione con follow-up personalizzati e tempestivi.

**KPI:** tassi di conversione, ricavi incrementali, coinvolgimento

[Ulteriori informazioni sul ripristino di carrelli e percorsi abbandonati](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)

## Esempi di casi d’uso tattici

Gli scenari seguenti illustrano le applicazioni comuni del pattern di percorso orchestrato in più passaggi.

- **Serie sull&#39;onboarding dei clienti**: e-mail di benvenuto, seguita da formazione sulle funzioni, quindi da una richiesta di attivazione nei primi 14 giorni dopo la registrazione
- **Campagna di ricoinvolgimento**: un promemoria e-mail, quindi un&#39;offerta di incentivo e un avviso finale per i clienti inattivi di oltre 3 settimane
- **percorso milestone fedeltà** — Notifica di aggiornamento livello, seguita da un&#39;offerta esclusiva, quindi da un promemoria di rinnovo in vista dell&#39;anniversario di iscrizione
- **Sequenza di riconquista** - E-mail con &quot;Ci manchi&quot;, poi offerta di sconto via e-mail, quindi un promemoria SMS finale per gli acquirenti inattivi
- **percorso di adozione del prodotto**: benvenuto di prova, suggerimenti di utilizzo, quindi richiesta di aggiornamento con l&#39;avanzare del periodo di prova
- **Sequenza di rinnovo dell&#39;abbonamento** - Notifica di 30 giorni, promemoria di 7 giorni, quindi messaggio di scadenza per i prossimi rinnovi dell&#39;abbonamento
- **Alimentazione post-acquisto**: e-mail di ringraziamento, guida all&#39;utilizzo, consigli sulla vendita incrociata, quindi una richiesta di revisione oltre 30 giorni dopo l&#39;acquisto

## Indicatori chiave di prestazioni

Utilizza i KPI seguenti per misurare l’efficacia dell’implementazione di un percorso orchestrato in più passaggi.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Percentuale di completamento percorso | Percentuale di profili che completano l’intero percorso senza uscire anticipatamente | Rapporto percorso: chiuso (completato) / inserito |
| Tasso di conversione passo | Percentuale di profili che avanzano da un passaggio all’altro | Metriche per nodo nel rapporto percorso |
| Tasso di coinvolgimento canale | Percentuali di apertura, percentuali di click-through e percentuali di risposta a ogni punto di contatto | Metriche di consegna e coinvolgimento per messaggio |
| Tasso di conversione criteri di uscita | Percentuale di profili che attivano l’evento di uscita (ad esempio, acquisto, iscrizione) prima del timeout del percorso | Conteggio hit criteri di uscita / Totale inserito |
| Tempo di conversione | Durata media dall’inserimento del percorso all’evento di criteri di uscita | Percorsi analytics: timestamp di ingresso per timestamp evento di conversione |
| Percentuale percorso di abbandono | Percentuale di profili che non coinvolgono più ogni passaggio (analisi di abbandono) | Visualizzazione dell’abbandono di CJA nei passaggi del percorso |
| Tasso di mantenimento/ricoinvolgimento | Percentuale di profili target che tornano allo stato attivo | Analisi comportamentale post-percorso in CJA |

## Applicazioni

Per implementare questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Adobe Journey Optimizer](AJO)**: motore di orchestrazione del Percorso, authoring dei messaggi, configurazione dei canali, sperimentazione dei contenuti, gestione dei conflitti e della frequenza e reporting
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — Valutazione e definizione del pubblico per tipi di pubblico di ingresso nel percorso, dati del profilo per la personalizzazione e diramazione delle condizioni
- **[!DNL Adobe Experience Platform](AEP)** — Archivio profili, servizio Identity, acquisizione dati evento e infrastruttura dati di base

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sulle funzionalità utilizzate in questa implementazione.

### Percorsi

- [Introduzione ai percorsi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Creare un percorso](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Proprietà del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Pubblicare il percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [Test del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)

### Attività percorso

- [Attività Read audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Eventi generali](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Eventi di qualificazione del pubblico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Attività Condizione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Attività Attendi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Aggiungere un messaggio in un percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Attività Fine](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [Configurare un’azione personalizzata](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions)

### Gestione delle entrate e delle uscite

- [Gestione voci percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Criteri di uscita](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### Configurazione dei canali

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Impostare le superfici di canale](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delega sottodomini](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Creare pool IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Piani di riscaldamento IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Configurare il canale SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Authoring e personalizzazione dei messaggi

- [Creare un messaggio e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Utilizzare i componenti di contenuto Designer e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Funzioni di supporto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilizzare i frammenti di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anteprima e test del contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Sperimentazione sui contenuti

- [Introduzione all’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Creare un esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapporto sull’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Calcoli statistici](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### Frequenza, conflitti e priorità

- [Regole di frequenza](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Panoramica sulle regole business](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Introduzione alla gestione dei conflitti e delle priorità](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Punteggi di priorità](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Limitazione di percorso e arbitrato](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Identificare potenziali conflitti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Tipi di pubblico e segmentazione

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/edge-segmentation)

### Reporting e analisi

- [Rapporto live del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

### Consenso e governance

- [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Gestire l’elenco di soppressione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Data Foundation

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica del profilo](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
