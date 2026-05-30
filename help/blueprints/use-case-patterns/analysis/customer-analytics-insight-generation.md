---
title: Customer Analytics e Insight Generation
description: Scopri come creare aree di lavoro di analisi cross-channel, metriche calcolate e dashboard per l’analisi del comportamento e delle prestazioni.
solution: Customer Journey Analytics, Experience Platform
exl-id: 235a4eb0-91ae-4030-b90e-7eda08c67ae1
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1717'
ht-degree: 3%

---

# Analisi dei clienti e generazione di insight

Questa guida descrive il modello di use case per la generazione di analisi clienti e insight, che connette [!DNL Adobe Experience Platform] set di dati a [!DNL Customer Journey Analytics] per creare visualizzazioni dati, aree di lavoro di analisi freeform, metriche calcolate, dashboard e scorecard per dispositivi mobili e, facoltativamente, pubblicare nuovamente i tipi di pubblico definiti da CJA in [!DNL Adobe Experience Platform] per l&#39;attivazione.

È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono comprendere il funzionamento di questo modello, gli obiettivi aziendali supportati, i casi di utilizzo tattici che consente e le applicazioni Adobe coinvolte.

A differenza degli altri modelli della tassonomia che si concentrano sull’attivazione e sul coinvolgimento (invio di messaggi, personalizzazione dei contenuti, attivazione di tipi di pubblico), questo modello si concentra sulla comprensione, l’analisi del comportamento dei clienti, la misurazione delle prestazioni delle campagne, l’identificazione delle tendenze e la generazione di informazioni utili per le decisioni su strategie e ottimizzazione.

## Schema del caso d’uso

**Analisi dei clienti e generazione insight**

Crea aree di lavoro di analisi cross-channel, metriche calcolate e dashboard per comprendere il comportamento dei clienti e le prestazioni della campagna.

**Piano di esecuzione:** Connessione dati > Configurazione visualizzazione dati > Analisi Workspace > Pubblicazione dashboard

## Panoramica del caso d’uso

Le organizzazioni devono comprendere il comportamento dei clienti nei diversi canali, il funzionamento delle campagne, dove i clienti abbandonano i percorsi, quali contenuti risuonano e come diversi segmenti vengono mantenuti nel tempo. La generazione di analisi dei clienti e insight soddisfa questa esigenza collegando i dati multicanale avanzati di [!DNL Adobe Experience Platform] a [!DNL Customer Journey Analytics], dove gli analisti possono creare aree di lavoro a forma libera, metriche personalizzate, configurare modelli di attribuzione e pubblicare dashboard per l&#39;utilizzo da parte delle parti interessate.

Il modello è destinato a più tipi di pubblico: analisti di marketing che necessitano di analisi esplorative approfondite, manager di campagne che necessitano di dashboard delle prestazioni, manager di prodotto che necessitano di informazioni approfondite sul coinvolgimento e la fidelizzazione e dirigenti che necessitano di scorecard KPI immediate. L’approccio di implementazione varia in base all’obiettivo analitico principale: misurazione delle prestazioni della campagna, analisi dei percorsi cross-channel, attivazione del pubblico basata sull’analisi o insights guidati sui prodotti.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

**Migliorare analisi e reporting**

Migliora le funzionalità di reporting per informazioni di marketing più veloci e fruibili tramite dashboard unificate e strumenti self-service.

- **KPI:** efficienza, produttività

Per ulteriori informazioni su questo obiettivo aziendale, consulta [Migliorare Analytics e reporting](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md).

**Abilitare il processo decisionale basato sui dati**

Fornisci ai team analisi self-service, informazioni sui clienti in tempo reale e previsioni basate sull’intelligenza artificiale come guida per la strategia.

- **KPI:** efficienza, produttività

Per ulteriori informazioni su questo obiettivo aziendale, consulta [Abilita processo decisionale basato sui dati](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md).

**Migliora attribuzione marketing**

Misura accuratamente l’impatto di punti di contatto, canali e campagne di marketing sui risultati di conversione e di ricavo.

- **KPI:** efficienza, ricavi incrementali

Per ulteriori informazioni su questo obiettivo aziendale, consulta [Migliorare l&#39;attribuzione marketing](/help/blueprints/business-objectives/analytics-insights/improve-marketing-attribution.md).

**Ottimizzare le spese di marketing e il ROI**

Ottimizza l’allocazione del budget di marketing comprendendo quali canali e campagne generano il massimo ritorno.

- **KPI:** efficienza, ricavi incrementali

Per ulteriori informazioni su questo obiettivo aziendale, consulta [Ottimizzare le spese di marketing e il ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md).

## Esempi di casi d’uso tattici

Di seguito sono riportati alcuni esempi di casi di utilizzo tattici che è possibile implementare con questo modello.

- Dashboard delle prestazioni della campagna: metriche di consegna, tassi di coinvolgimento, conversione e attribuzione dei ricavi per e-mail, SMS, push e campagne multimediali a pagamento
- Analisi dell’abbandono del percorso di clienti: identifica dove i clienti abbandonano nei funnel di acquisto, registrazione o onboarding
- Analisi della fidelizzazione delle coorti: misura il livello di fidelizzazione delle diverse coorti di acquisizione nel corso di settimane, mesi e trimestri
- Modellazione di attribuzione dei canali: confronta l’attribuzione di primo contatto, ultimo contatto, lineare e decadimento nel tempo per capire quali canali favoriscono le conversioni
- Analisi delle prestazioni dei contenuti: identificazione dei contenuti più rilevanti per segmento, canale e fase del ciclo di vita
- Analisi dell’utilizzo e dell’adozione dei prodotti: monitoraggio dell’adozione delle funzioni, della frequenza di coinvolgimento e delle tendenze di crescita degli utenti
- Analisi della fase del ciclo di vita del cliente: segmentare e analizzare i clienti per fase del ciclo di vita (nuova, attiva, a rischio, scaduta)
- Dashboard di ottimizzazione del marketing mix: confronto tra l&#39;investimento dei canali e il contributo ai ricavi
- Reporting e valutazione del coinvolgimento cross-channel: creazione di punteggi di coinvolgimento compositi dalle interazioni web, app, e-mail e campagne

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare il successo di questo modello di caso d’uso.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Efficienza | Riduzione dei tempi di insight e delle attività manuali di reporting | Tracciare il tempo impiegato dagli analisti per creare rapporti prima e dopo l’implementazione di CJA |
| Produttività | Numero di analisi self-service create dagli utenti aziendali | Monitorare la creazione di progetti Workspace e l’utilizzo del dashboard |
| Reddito Incrementale | Ricavi attribuiti a decisioni di ottimizzazione basate su informazioni | Misura l’incremento dei ricavi dalle campagne ottimizzate in base all’analisi CJA |
| Tassi di conversione | Tassi di completamento dei funnel tra i principali percorsi di clienti | Tracciare i tassi di fallout a ogni passaggio del percorso utilizzando la visualizzazione Abbandono di CJA |
| Coinvolgimento | Profondità e frequenza dell’interazione del cliente tra i canali | Creare metriche calcolate per il punteggio di coinvolgimento in CJA |
| Conservazione | Tassi di restituzione dei clienti in periodi di tempo definiti | Utilizzare l’analisi per coorte con CJA per misurare le curve di fidelizzazione |

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Customer Journey Analytics] (CJA)** — Connessioni, visualizzazioni dati, analisi dell&#39;area di lavoro, analisi guidata, metriche calcolate, dashboard, pubblicazione di tipi di pubblico e analisi dei contenuti
- **[!DNL Adobe Experience Platform] (AEP)** — Data lake, set di dati, schemi XDM, dati di profilo ed eventi che alimentano le connessioni CJA

## Documentazione correlata

Le risorse seguenti forniscono informazioni aggiuntive per questo modello di caso d’uso.

### [!DNL Customer Journey Analytics] — Guida introduttiva

- [Panoramica di CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-overview/cja-overview)
- [Guardrail CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-admin/guardrails)

### Connessioni

- [Panoramica delle connessioni](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-connections/overview)
- [Creare o modificare una connessione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-connections/create-connection)
- [Gestire le connessioni](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-connections/manage-connections)

### Visualizzazioni dati

- [Panoramica delle visualizzazioni dati](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/data-views)
- [Creare o modificare una visualizzazione dati](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Panoramica delle impostazioni dei componenti](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Impostazioni persistenza](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Impostazioni di attribuzione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Impostazioni formato](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Deduplica delle metriche](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [Includi/escludi valori](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [Impostazioni di sessione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/session-settings)
- [Campi derivati](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/derived-fields)

### Workspace e analisi

- [Panoramica di Workspace](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/home)
- [Creare un progetto](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Tabella a forma libera](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Visualizzazione del flusso](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Visualizzazione Abbandono](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Tabella coorte](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Pannello Attribuzione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Dimensioni di raggruppamento](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [Condividi progetti](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Programmare progetti](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Panoramica sull’esportazione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/export/export-cloud)

### Analisi guidata

- [Panoramica dell’analisi guidata](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/overview)
- [Vista funnel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Visualizzazione tendenze](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Visualizzazione frequenza di coinvolgimento](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [Vista Mantenimento](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [Visualizzazione crescita attiva](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [Vista impatto sulla versione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/impact/release)
- [Visualizzazione impatto primo utilizzo](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/impact/first-use)
- [Vista Timeline](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/streams/timeline)

### Componenti

- [Panoramica sui filtri](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Creare filtri](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Panoramica delle metriche calcolate](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Creare metriche calcolate](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Funzioni metriche calcolate](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [Panoramica delle annotazioni](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/annotations/overview)
- [Intervalli di date](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)
- [Componente metriche](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/apply-create-metrics)

### Pubblicazione del pubblico

- [Panoramica di Audiences](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Creare e pubblicare tipi di pubblico](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/audiences/publish)
- [Gestire i tipi di pubblico](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/audiences/manage)

### Analisi dei contenuti

- [Content Analytics](https://experienceleague.adobe.com/it/docs/analytics-platform/using/content-analytics/content-analytics)
- [Configurazione Content Analytics](https://experienceleague.adobe.com/en/docs/analytics-platform/using/content-analytics/config/configuration)

### Dashboard e scorecard

- [Crea una scorecard per dispositivi mobili](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Configurare e curare le scorecard](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Dashboard di Adobe Analytics: guida esecutiva](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Visualizzazione Numero di riepilogo](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)

### Fondamenti di AEP

- [Panoramica sui set di dati](https://experienceleague.adobe.com/it/docs/experience-platform/catalog/datasets/overview)
- [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home)
- [Panoramica sulle origini](https://experienceleague.adobe.com/it/docs/experience-platform/sources/home)
- [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home)
- [Panoramica di Audience Portal](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/audience-portal)

### Integrazione del reporting in AJO

- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Rapporto e-mail della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/campaign-global-report-cja-email)
- [Rapporto e-mail percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/journey-global-report-cja-email)

### Tutorial e guide

- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/schema/composition)
- [Panoramica di Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/home)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/it/docs/experience-platform/datastreams/configure)
