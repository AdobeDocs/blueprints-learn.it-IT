---
title: Analisi B2B
description: Scopri come includere le informazioni a livello di account B2B nell’analisi del percorso clienti cross-channel.
solution: Customer Journey Analytics, Real-Time Customer Data Platform
exl-id: 9d576e5c-cbd2-4c60-a6b0-88f8b8b963b4
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1811'
ht-degree: 2%

---

# Analisi B2B

Questa guida descrive il modello di casi d&#39;uso di analisi B2B, che utilizza [!DNL Customer Journey Analytics] ([!DNL CJA]) B2B edition e [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition per incorporare informazioni a livello di account B2B nell&#39;analisi del percorso clienti cross-channel. È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono comprendere il funzionamento di questo modello, gli obiettivi aziendali supportati, i casi di utilizzo tattici che consente e le applicazioni Adobe coinvolte.

Analytics B2B estende le funzionalità standard di [!DNL CJA] con connessioni basate su account, contenitori specifici di B2B (account, account globale, opportunità, gruppo di acquisto) e reporting a livello di account. Questa funzionalità consente alle organizzazioni di analizzare il coinvolgimento di marketing e vendite a livello di account, monitorare la progressione delle opportunità, misurare la completezza dei gruppi di acquisto e attribuire i ricavi ai punti di contatto di marketing attraverso cicli di vendita B2B estesi.

## Schema del caso d’uso

**Analisi B2B**

Includere informazioni a livello di account B2B nell’analisi del percorso clienti cross-channel.

**Piano di esecuzione:** Connessione dati B2B > Configurazione visualizzazione dati account > Analisi Workspace > Pubblicazione dashboard

## Panoramica del caso d’uso

Le organizzazioni B2B devono affrontare una sfida di analisi fondamentale: i loro clienti non sono persone singole, ma account composti da più parti interessate, gruppi di acquisto e opportunità. Le analisi standard basate su persone non possono rispondere a domande come &quot;Quali account sono più coinvolti?&quot;, &quot;Quanto sono completi i nostri gruppi di acquisto?&quot; o &quot;Quali punti di contatto di marketing determinano la progressione dell’opportunità?&quot;

Analytics B2B affronta questo problema sfruttando [!DNL CJA] B2B edition per creare visualizzazioni analitiche incentrate sull&#39;account che combinano dati comportamentali a livello di persona con dimensioni di account, opportunità e gruppo di acquisto. [!DNL RT-CDP] B2B edition fornisce l’unificazione del profilo dell’account sottostante e la risoluzione delle identità B2B che alimenta il livello di analisi. Insieme, queste soluzioni consentono alle organizzazioni di creare analisi di percorso cross-channel a livello di account, correlare il coinvolgimento di marketing con la progressione della pipeline e fornire informazioni fruibili ai team di marketing e di vendita.

Il pubblico di destinazione include i team operativi di marketing B2B, i leader della generazione della domanda, gli analisti delle operazioni di ricavo e i responsabili delle vendite che necessitano di visibilità sul coinvolgimento a livello di account e sullo stato della pipeline.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### Migliorare analisi e reporting

Migliora le funzionalità di reporting per informazioni di marketing più veloci e fruibili tramite dashboard unificate e strumenti self-service. L’analisi B2B consente alle organizzazioni di consolidare i dati di coinvolgimento a livello di account da più origini in un unico ambiente analitico, fornendo visibilità cross-channel sul modo in cui i programmi di marketing influenzano la pipeline e i ricavi.

**KPI:** efficienza, produttività

[Ulteriori informazioni sul miglioramento di analisi e reporting](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)

### Abilitare il processo decisionale basato sui dati

Fornisci ai team analisi self-service, informazioni sui clienti in tempo reale e previsioni basate sull’intelligenza artificiale come guida per la strategia. L’analisi a livello di account fornisce ai team di marketing e vendite i dati necessari per assegnare le priorità agli account, ottimizzare le strategie di coinvolgimento e allineare le opportunità della pipeline.

**KPI:** efficienza, produttività

[Ulteriori informazioni sull’abilitazione del processo decisionale basato sui dati](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)

### Migliorare la qualificazione e la conversione dei lead

Aumenta la qualità dei lead e accelera la progressione della pipeline tramite valutazione, nutrimento e follow-up personalizzato. CJA B2B edition fornisce intervalli di lookback di account estesi per 13 mesi appositamente progettati per i cicli di vendita B2B, consentendo un’attribuzione multi-touch accurata in tutto il percorso di account.

**KPI:** efficienza, ricavi incrementali

[Ulteriori informazioni sul miglioramento della qualificazione e conversione dei lead](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

## Esempi di casi d’uso tattici

Gli scenari seguenti illustrano come questo modello può essere applicato nella pratica.

- **Analisi del punteggio di coinvolgimento dell&#39;account**: misura e classifica gli account in base al loro coinvolgimento aggregato su web, e-mail, eventi e interazioni di contenuto per identificare gli account con intenti elevati per il follow-up delle vendite
- **Monitoraggio della completezza del gruppo di acquisto**: analizza la composizione del gruppo di acquisto tra gli account per identificare le lacune nella copertura dei ruoli e assegnare la priorità all&#39;acquisizione dei lead per i gruppi di acquisto incompleti
- **Correlazione della pipeline dell&#39;opportunità** — Correlazione dei dati dell&#39;impegno di marketing con la progressione della fase dell&#39;opportunità per capire quali campagne e punti di contatto guidano l&#39;avanzamento della pipeline
- **Attribuzione B2B multi-touch**: applica modelli di attribuzione con intervalli di lookback di 13 mesi ai punti di contatto di marketing del credito nell&#39;intero percorso di acquisto B2B dal primo contatto al vincitore chiuso
- **Mappatura percorso di account**: visualizza il percorso di account cross-channel dalla conoscenza iniziale fino alla creazione e alla chiusura delle opportunità, identificando percorsi comuni e punti di attrito
- **Influenza delle campagne sulla pipeline**: misura in che modo campagne specifiche influenzano la creazione di pipeline dell&#39;account, l&#39;avanzamento delle opportunità e la generazione di ricavi
- **Progressione dell&#39;engagement dei gruppi di acquisto**: verifica l&#39;evoluzione dei punteggi di engagement dei gruppi di acquisto nel tempo e correlazione delle soglie di engagement con i risultati delle opportunità
- **Prestazioni dei contenuti basati sull&#39;account**: analisi delle risorse e degli argomenti di contenuto che risuonano con segmenti di account, settori o ruoli di gruppi di acquisto specifici
- **Dashboard di allineamento vendite e marketing** — Crea dashboard condivise che forniscano sia ai team di marketing che a quelli di vendita una visione unificata del coinvolgimento dell&#39;account, dell&#39;integrità della pipeline e dell&#39;attribuzione dei ricavi
- **Segmentazione account per l&#39;attivazione**: crea segmenti B2B in base all&#39;analisi a livello di account (ad esempio, &quot;account altamente coinvolti senza opportunità aperte&quot;) e pubblicali per l&#39;attivazione a valle

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare il successo di questo modello di caso d’uso.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Punteggio di coinvolgimento dell’account | Aggregare metriche di coinvolgimento in tutti i contatti all’interno di un account | Metrica calcolata che combina visite web, interazioni e-mail, partecipazione a eventi e download di contenuti a livello di account |
| Completezza gruppo acquisti | Percentuale di ruoli richiesti completati all’interno di un gruppo di acquisto | Rapporto tra i ruoli completati e il totale dei ruoli richiesti per gruppo di acquisto, tracciato nel tempo |
| Pipeline influenzata dal marketing | Ricavi in pipeline toccati dalle attività di marketing | Valore dell’opportunità in cui i contatti dell’account associati hanno punti di contatto di marketing nella finestra di attribuzione |
| Tasso di conversione da account a opportunità | Percentuale di account coinvolti che generano opportunità qualificate | Conti con opportunità divisi per il totale dei conti impegnati in un periodo definito |
| Lunghezza media ciclo di offerta | Tempo dal primo contatto marketing al vincitore chiuso | Durata media dal primo punto di contatto attribuito alla data di chiusura dell’opportunità |
| Ricavi da attribuzione marketing | Ricavi attribuiti ai punti di contatto di marketing | Ricavi da opportunità realizzate chiuse con tocchi di marketing, distribuiti per modello di attribuzione |
| Raggiungimento e penetrazione dell’account | Numero di contatti coinvolti per account di destinazione | Contatti univoci con interazioni di marketing per account, rispetto al totale dei contatti noti |
| Coinvolgimento contenuti per ruolo di acquisto | Metriche di coinvolgimento segmentate per ruolo di gruppo di acquisto | Visualizzazioni di pagina, download e tempo trascorso suddivisi per persona/ruolo all’interno dei gruppi di acquisto |

## Applicazioni

Per implementare questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Customer Journey Analytics]B2B edition**: fornisce connessioni basate su account, contenitori di visualizzazione dati specifici di B2B, analisi dell&#39;area di lavoro a livello di account, analisi del gruppo di acquisto, analisi delle opportunità, segmentazione B2B e attribuzione B2B con intervalli di lookback estesi
- **[!DNL Real-Time CDP]B2B edition** — Fornisce le basi dati B2B tra cui l&#39;unificazione del profilo account, la risoluzione dell&#39;identità B2B, le classi di schema B2B (account, opportunità, gruppo acquisti) e l&#39;integrazione [!DNL Marketo Engage] per l&#39;acquisizione dei dati del coinvolgimento B2B

## Documentazione correlata

Le risorse seguenti forniscono informazioni aggiuntive per l’implementazione di questo modello di caso d’uso.

**[!DNL CJA]B2B edition**

- [Panoramica di CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [Panoramica di CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-overview/cja-overview)
- [Guardrail CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-admin/guardrails)

**Connessioni**

- [Panoramica delle connessioni](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-connections/overview)
- [Creare o modificare una connessione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-connections/create-connection)
- [Gestire le connessioni](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-connections/manage-connections)

**Visualizzazioni dati**

- [Panoramica delle visualizzazioni dati](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/data-views)
- [Creare o modificare una visualizzazione dati](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Panoramica delle impostazioni dei componenti](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Impostazioni persistenza](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Impostazioni di attribuzione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Impostazioni formato](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Campi derivati](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [Impostazioni di sessione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/session-settings)

**Workspace e analisi**

- [Panoramica di Workspace](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/home)
- [Creare un progetto](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Tabella a forma libera](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Visualizzazione del flusso](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Visualizzazione Abbandono](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Tabella coorte](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Pannello Attribuzione](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Condividi progetti](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Programmare progetti](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Dimensioni di raggruppamento](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

**Componenti**

- [Panoramica sui filtri](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Creare filtri](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Panoramica delle metriche calcolate](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Creare metriche calcolate](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Panoramica delle annotazioni](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/annotations/overview)
- [Intervalli di date](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

**Tipi di pubblico**

- [Panoramica di Audiences](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Creare e pubblicare tipi di pubblico](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/audiences/publish)
- [Gestire i tipi di pubblico](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/audiences/manage)

**Dashboard e scorecard**

- [Crea una scorecard per dispositivi mobili](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Configurare e curare le scorecard](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Dashboard di Adobe Analytics: guida esecutiva](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dashboards/set-up-execs)

**Analisi guidata**

- [Panoramica dell’analisi guidata](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/overview)
- [Vista funnel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Visualizzazione tendenze](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Vista Mantenimento](https://experienceleague.adobe.com/it/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

**[!DNL RT-CDP]B2B edition**

- [Panoramica di RT-CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#702702)
- [Schemi B2B edition](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/schemas/b2b)
- [Panoramica sulle origini B2B](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/sources/b2b)

**AEP data foundation**

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home)
- [Panoramica sulle origini](https://experienceleague.adobe.com/it/docs/experience-platform/sources/home)
- [Connettore Marketo Engage](https://experienceleague.adobe.com/it/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home)
- [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home)

**Governance dei dati e ciclo di vita**

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home)
- [Advanced Data Lifecycle Management](https://experienceleague.adobe.com/it/docs/experience-platform/data-lifecycle/home)

**Tutorial e guide**

- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/schema/composition)
- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview)
- [Panoramica di Observability Insights](https://experienceleague.adobe.com/it/docs/experience-platform/observability/home)
