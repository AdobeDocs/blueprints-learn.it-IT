---
title: Attivazione messaggi in uscita in batch
description: Scopri come valutare un pubblico e consegnare un messaggio in uscita pianificato in un’esecuzione batch singola.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 192853ce-02ab-46e6-9092-3db5354bc19c
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1701'
ht-degree: 4%

---

# Attivazione di messaggi in batch in uscita

Questa guida descrive il modello di caso d’uso per l’attivazione di messaggi in uscita in batch, che utilizza [!DNL Adobe Journey Optimizer] (AJO) e [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) per inviare messaggi in uscita pianificati ai segmenti di pubblico definiti. È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono comprendere il funzionamento di questo modello, gli obiettivi aziendali supportati, i casi di utilizzo tattici che consente e le applicazioni Adobe coinvolte.

L’attivazione batch dei messaggi in uscita è il pattern di campagna fondamentale per la messaggistica in uscita uno-a-molti. Copre l’intero ciclo di vita, dalla definizione del pubblico alla consegna dei messaggi e all’analisi delle prestazioni.

## Schema del caso d’uso

**Attivazione messaggi in uscita in batch**

Valuta un pubblico, quindi distribuisci un messaggio in uscita pianificato (e-mail, SMS, push) a tutti i profili idonei in un’unica esecuzione batch.

**Piano di esecuzione:** Valutazione del pubblico > Authoring dei messaggi > Esecuzione della campagna > Generazione rapporti

## Panoramica del caso d’uso

Le organizzazioni spesso devono inviare un singolo messaggio a un segmento di pubblico noto in un momento specifico o in risposta a un evento di sistema. Questo modello soddisfa tale requisito combinando la valutazione del pubblico in [!DNL RT-CDP] con la creazione dei messaggi e l&#39;esecuzione della campagna in [!DNL Journey Optimizer].

Lo scenario aziendale è semplice: definisci chi deve ricevere il messaggio, creane il contenuto con la personalizzazione, associa il pubblico e il messaggio in una campagna o in un percorso ed esegui l’invio secondo una pianificazione, tramite la qualificazione del pubblico o un attivatore di sistema. Il risultato è un messaggio consegnato con reporting completo sulle metriche di consegna, coinvolgimento e conversione.

Questo modello si applica ogni volta che un obiettivo di business può essere avanzato distribuendo un singolo messaggio a un pubblico noto in un’unica esecuzione. Si differenzia dalla messaggistica attivata dagli eventi, che risponde agli eventi comportamentali in tempo reale, e dai percorsi orchestrati in più passaggi, che guidano i profili attraverso più punti di contatto nel tempo. L’attivazione in batch è il modello di campagna più semplice e il punto di partenza più comune per i casi di utilizzo dei messaggi in uscita.

## Obiettivi aziendali chiave

Questa sezione identifica gli obiettivi aziendali principali supportati dall&#39;attivazione in batch dei messaggi in uscita.

### Aumentare il coinvolgimento nelle e-mail e nelle campagne

**Descrizione:** migliora i tassi di apertura, i tassi di click-through e la risposta complessiva alla campagna tramite contenuto ottimizzato e targeting.

**KPI:** tassi aperti, coinvolgimento, tassi di conversione

### Aumento dei ricavi e delle vendite

**Descrizione:** incrementa i ricavi principali tramite canali digitali ottimizzati, campagne e percorsi di clienti.

**KPI:** Tassi di conversione, Ricavi incrementali, Valore medio ordine

**Obiettivo aziendale correlato:** [Aumento ricavi e vendite](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

### Semplificare l’esecuzione della campagna

**Descrizione:** riduci il tempo di creazione delle campagne e semplifica la distribuzione di campagne multicanale tramite modelli, automazione e processi standardizzati.

**KPI:** Velocità al mercato, efficienza, completamento puntuale %

## Esempi di casi d’uso tattici

Gli scenari seguenti illustrano le applicazioni comuni dell’attivazione batch dei messaggi in uscita.

- **Annuncio di vendita o messaggio e-mail promozionale** — Trasmetti un&#39;offerta promozionale a un segmento di clienti idonei in una data pianificata
- **Notifica push di lancio del prodotto** — Notifica ai clienti interessati la disponibilità di un nuovo prodotto tramite push
- **Newsletter o e-mail di riepilogo** - Distribuisci periodicamente aggiornamenti dei contenuti ai tipi di pubblico degli abbonati
- **Invito alla registrazione dell&#39;evento** - Invita potenziali clienti qualificati a webinar, conferenze o eventi di persona
- **E-mail di promemoria per il rinnovo dell&#39;abbonamento** — Ricorda ai clienti che si avvicinano alle date di rinnovo di intervenire
- **Notifica milestone programma fedeltà** — Congratularsi con i membri che hanno raggiunto livelli fedeltà o soglie di punti
- **E-mail call-to-action specifica** — Consente di eseguire un&#39;azione mirata come il completamento di un acquisto, l&#39;aggiornamento delle preferenze o la registrazione a un programma
- **Campagna SMS per vendita flash o offerta limitata nel tempo**: invia promozioni urgenti e limitate nel tempo tramite SMS al pubblico che ha acconsentito

## Indicatori chiave di prestazioni

La tabella seguente definisce i KPI utilizzati per misurare l’efficacia della campagna.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Percentuale di consegna | Percentuale di messaggi consegnati correttamente ai destinatari | Consegnato / Inviato x 100 |
| Percentuale aperture | Percentuale di messaggi recapitati aperti dai destinatari | Aperture univoche/consegnate x 100 |
| Percentuale di click-through (CTR) | Percentuale di messaggi consegnati in cui è stato fatto clic su un collegamento | Clic univoci / 100 consegnati |
| Percentuale di clic per apertura (CTOR) | Percentuale di messaggi aperti in cui è stato fatto clic su un collegamento | Clic/Aperture univoche x 100 |
| Tasso di conversione | Percentuale di destinatari che hanno completato l’azione desiderata | Conversioni / Consegnate x 100 |
| Percentuale annullamenti iscrizione | Percentuale di destinatari che hanno annullato l’abbonamento dopo la ricezione del messaggio | Annullamenti iscrizione/Consegne x 100 |
| Percentuale non recapitate | Percentuale di messaggi non recapitati | Mancato recapito / Inviato x 100 |
| Ricavo per e-mail inviata | Ricavi attribuiti alla campagna divisi per messaggi inviati | Ricavi / Inviati - Totale |

## Applicazioni

Per implementare questo modello vengono utilizzate le seguenti applicazioni.

- **[!DNL Adobe Journey Optimizer](AJO)** — Authoring dei messaggi, configurazione del canale, esecuzione della campagna, orchestrazione del percorso, sperimentazione dei contenuti, regole di frequenza e reporting
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — Valutazione del pubblico, consenso e applicazione della governance
- **[!DNL Adobe Experience Platform](AEP)** — Archivio profili, servizio identità, schemi, set di dati, raccolta dati

## Documentazione correlata

Questa sezione fornisce collegamenti completi alla documentazione di [!DNL Experience League] organizzati per argomento.

### Campagne

- [Introduzione alle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Creare una campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Campagne attivate da API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### Percorsi

- [Introduzione ai percorsi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Leggi percorso di pubblico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### Configurazione dei canali

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delega sottodomini](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Creare pool IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Piani di riscaldamento IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Impostazioni superficie e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configurare il canale SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Gestire l’elenco di soppressione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Authoring e personalizzazione dei messaggi

- [Creare un messaggio e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Utilizzare i componenti di contenuto Designer e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [Importare o codificare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/code-content)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Funzioni di supporto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### Gestione dei contenuti

- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilizzare i frammenti di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anteprima e test del contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Inviare bozze e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [Rendering di e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)

### Sperimentazione sui contenuti

- [Introduzione all’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Creare un esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapporto sull’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Calcoli statistici](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### Gestione della frequenza e dei conflitti

- [Regole di frequenza](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Panoramica sulle regole business](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Introduzione alla gestione dei conflitti e delle priorità](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Punteggi di priorità](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identificare potenziali conflitti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Limitazione di percorso e arbitrato](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### Tipi di pubblico e segmentazione

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Composizione del pubblico](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Generazione rapporti

- [Rapporto live delle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapporto live del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### Governance dei dati e consenso

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview)
- [Gruppo di campi Consenso e preferenze](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Modellazione dati e identità

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Guardrail

- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Guardrail di acquisizione](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Tutorial e guida introduttiva

- [Introduzione a Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/get-started)
- [Creare la prima campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Creare il primo percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
