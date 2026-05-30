---
title: Acquisto di soluzioni di marketing e gestione dei Percorsi basate su gruppi
description: Scopri come sviluppare percorsi a livello di account che qualifichino i lead in gruppi di acquisto per migliorare l’efficacia del marketing B2B.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 2bf57f67-80c8-4368-98d2-05706427772d
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 1%

---

# Acquisto di soluzioni di marketing e gestione dei percorsi basate su gruppi

In questa guida viene descritto il modello di casi d&#39;uso di marketing e gestione dei percorsi basati su gruppi di acquisto, che utilizza [!DNL Adobe Journey Optimizer B2B Edition] e [!DNL Real-Time CDP B2B Edition] per implementare l&#39;orchestrazione dei percorsi a livello di account con la gestione dei gruppi di acquisto. È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono comprendere il funzionamento di questo modello, gli obiettivi aziendali supportati, i casi di utilizzo tattici che consente e le applicazioni Adobe coinvolte.

A differenza dei modelli di percorso a livello di persona, questo modello opera a livello di account, qualificando i singoli lead in gruppi di acquisto associati agli interessi della soluzione, valutando il coinvolgimento a livello di gruppo di acquisto e orchestrando percorsi di account con più passaggi che progrediscono attraverso le fasi della pipeline verso la preparazione alle vendite.

## Schema del caso d’uso

**Acquisto di attività di marketing e gestione dei percorsi basate sui gruppi**

Sviluppa percorsi a livello di account che qualifichino i lead in gruppi di acquisto per migliorare l’efficacia del marketing B2B.

**Piano di esecuzione:** Identificazione account > Definizione gruppo di acquisto > Qualificazione lead > Esecuzione Percorso di conti > Punteggio coinvolgimento > Generazione rapporti

## Panoramica del caso d’uso

Le organizzazioni B2B devono affrontare una sfida fondamentale: le decisioni di acquisto vengono prese raramente da un singolo individuo. Gli acquisti B2B complessi coinvolgono più parti interessate — decisori, influencer, campioni, titolari del budget e valutatori tecnici — che collettivamente formano un &quot;gruppo di acquisto&quot;. Il marketing tradizionale basato su lead tratta ogni persona in modo indipendente, senza il segnale critico che indica se la giusta combinazione di ruoli all’interno di un account è attiva e pronta per l’acquisto.

L’acquisto di attività di marketing e gestione dei percorsi basate su gruppi risolve questo problema spostando l’unità di orchestrazione dai singoli lead agli account e ai gruppi di acquisto. Il modello consente agli addetti al marketing B2B di definire gli interessi delle soluzioni (i prodotti o i servizi venduti), creare modelli di gruppi di acquisto che specificano quali ruoli sono necessari per una decisione di acquisto, qualificare i lead in ingresso rispetto a tali ruoli, valutare il coinvolgimento a livello di gruppo di acquisto e orchestrare percorsi di account che rispondano ai segnali di completezza e preparazione dei gruppi di acquisto.

Il risultato desiderato è il miglioramento della qualità e della velocità della pipeline: il marketing consegna gli account alle vendite solo quando le persone giuste all’interno dell’account sono coinvolte e il gruppo di acquisto è sufficientemente completo, riducendo lo sforzo di vendita sprecato e accelerando la progressione delle transazioni.

## Obiettivi aziendali chiave

Questo modello di caso d’uso supporta i seguenti obiettivi aziendali.

### Migliorare la qualificazione e la conversione dei lead

Aumenta la qualità dei lead e accelera la progressione della pipeline tramite valutazione, nutrimento e follow-up personalizzato.

**KPI:** conversione lead, conversione prospect/lead, efficienza

[Ulteriori informazioni sul miglioramento della qualificazione e conversione dei lead](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### Aumentare la generazione di lead

Genera lead più qualificati per la pipeline di vendita tramite moduli, eventi, contenuti e coinvolgimento multicanale.

**KPI:** potenziali clienti, costo per lead, conversione lead

[Ulteriori informazioni sull&#39;aumento della generazione di lead](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### Aumento dei profitti e delle vendite

Incrementa i ricavi aziendali con canali digitali ottimizzati, campagne e percorsi di clienti.

**KPI:** crescita dei ricavi, velocità della pipeline, tasso di chiusura delle transazioni

[Ulteriori informazioni sull&#39;aumento dei ricavi e delle vendite](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

## Esempi di casi d’uso tattici

Di seguito sono riportati scenari specifici in cui è possibile applicare questo modello.

- **Qualificazione del gruppo di acquisto specifico per la soluzione** — Definire i gruppi di acquisto per ogni linea di prodotti (ad esempio, &quot;Enterprise CRM&quot;, &quot;Data Platform&quot;, &quot;Security Suite&quot;) con i modelli di ruolo che specificano gli utenti tipo richiesti (buyer economico, valutatore tecnico, promotore, utente finale) e i lead qualificati dal sistema di automazione del CRM e del marketing rispetto a tali ruoli.
- **percorso di account per l&#39;accelerazione della pipeline** — Orchestrare un percorso di account in più passaggi che invia e-mail di crescita mirate a ruoli meno coinvolti all&#39;interno di un gruppo di acquisto, attiva gli avvisi di vendita quando vengono raggiunte le soglie di coinvolgimento e passa l&#39;account a una fase pronta per le vendite.
- **Campagne di completezza del gruppo di acquisto**: identifica gli account in cui i gruppi di acquisto hanno ruoli mancanti (ad esempio, nessun buyer economico identificato) e avvia campagne di acquisizione mirate per coinvolgere gli utenti tipo giusti all&#39;interno di tali account.
- **percorsi di account di cross-selling**: dopo la chiusura di un&#39;offerta iniziale, creare nuovi gruppi di acquisto per interessi di soluzioni complementari e orchestrare percorsi di account che alimentino il comitato di acquisto espanso.
- **Nuovo coinvolgimento per offerte in stallo**: rileva gli account in cui i punteggi di coinvolgimento dei gruppi di acquisto sono diminuiti e attiva percorsi di ricoinvolgimento con nuovi contenuti, coinvolgimento dei dirigenti o inviti a eventi.
- **Allineamento vendite e marketing tramite approfondimenti CRM**: verifica dello stato del percorso di acquisto, dei dati di coinvolgimento e dell&#39;avanzamento del gruppo di account direttamente in [!DNL Salesforce] o [!DNL Dynamics 365] in modo che i rappresentanti abbiano visibilità in tempo reale in account qualificati per il marketing.
- **Aggiornamenti dei gruppi di acquisto basati sugli eventi**: aggiorna automaticamente l&#39;iscrizione al gruppo di acquisto e i punteggi di coinvolgimento quando i lead partecipano a webinar, scaricano white paper, visitano pagine di prezzi o richiedono demo.
- **Coordinamento di account con più aree geografiche**: consente di gestire gruppi di acquisto in account globali in cui diversi contatti regionali ricoprono ruoli diversi, unificando il punteggio di coinvolgimento tra aree geografiche diverse.

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare l’efficacia di questo modello di caso d’uso.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Percentuale di completezza del gruppo di acquisto | Percentuale di gruppi di acquisto in cui sono stati inseriti tutti i ruoli richiesti | [!DNL AJO B2B] dashboard di Analytics: tieni traccia della copertura dei ruoli per gruppo di acquisto |
| Punteggio di coinvolgimento del gruppo di acquisto | Punteggio di coinvolgimento aggregato per tutti i membri di un gruppo di acquisto | Punteggio di coinvolgimento [!DNL AJO B2B]: punteggi a livello di persona aggregati al gruppo di acquisto |
| Percentuale account qualificati marketing (MQA) | Percentuale di account che raggiungono la soglia qualificata per il marketing | Criteri di uscita dal percorso di conti: i conti passano alla fase di preparazione alla vendita |
| Velocità della pipeline | Tempo medio dalla creazione del gruppo di acquisto all&#39;opportunità qualificata per le vendite | Integrazione CRM: tenere traccia delle transizioni di fase da [!DNL AJO B2B] alla pipeline CRM |
| Tasso di qualificazione del gruppo lead-acquisto | Percentuale di lead qualificati per l&#39;acquisto di ruoli gruppo | [!DNL AJO B2B] Gestione del gruppo di acquisto: rapporto lead qualificati e non qualificati |
| Percentuale di risposta avviso vendite | Percentuale di avvisi di vendita che risultano in attività di follow-up vendite | Approfondimenti vendite CRM: tracciare la conversione da avviso ad attività |
| Percentuale di completamento Percorso conto | Percentuale di account che completano il percorso di percorso previsto | [!DNL AJO B2B] dashboard di Analytics: metriche di completamento percorso |
| Tasso di coinvolgimento e-mail (B2B) | Percentuali di apertura e click-through per e-mail di crescita B2B | Rapporti di [!DNL AJO B2B]: metriche di consegna e coinvolgimento e-mail |

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni Adobe.

- **[!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])** — Orchesta i percorsi a livello di account, gestisce i gruppi di acquisto con modelli di ruolo e interessi nelle soluzioni, valuta il coinvolgimento a livello di persona e gruppo di acquisto, crea contenuti e-mail B2B, invia messaggi SMS, configura avvisi di vendita e fornisce dashboard di analisi B2B.
- **[!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])** - Unifica i profili account dai dati B2B tra sorgenti, risolve le relazioni tra persone e account, valuta i tipi di pubblico a livello di account, configura destinazioni specifiche per B2B ([!DNL Marketo Engage], [!DNL LinkedIn], CRM) e applica la governance dei dati nei dati B2B.

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sulle applicazioni e funzionalità a cui si fa riferimento in questa guida.

### [!DNL AJO B2B Edition]

- [Pagina principale della documentazione di AJO B2B edition](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [Panoramica sui gruppi di acquisto](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [Interessi soluzione](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Modelli di ruolo](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [Creare gruppi di acquisto](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)
- [Fasi del gruppo di acquisto](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Panoramica sui percorsi di account](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [Nodi del percorso di account](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [E-mail di avviso vendite](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [Approfondimenti vendite CRM](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)

### E-mail e contenuto B2B

- [Authoring di e-mail B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [Authoring di SMS in AJO B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [Assistente AI per l’authoring delle e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### Analisi e dashboard B2B

- [Dashboard dei gruppi di acquisto](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [Dashboard di coinvolgimento](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [Dashboard intelligente](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [Panoramica di CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### [!DNL RT-CDP B2B Edition]

- [Panoramica di RT-CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [Schemi B2B in Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Pubblico dell’account](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [Connettore sorgente Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)

### Data Foundation

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica sulle origini](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)

### Configurazione dei canali

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configurare il canale SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### Governance dei dati e privacy

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### Destinazioni

- [Panoramica sulle destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Catalogo delle destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [LinkedIn - Destinazione tipi di pubblico corrispondenti](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)

### Guardrail

- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Guardrail di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [Guardrail di acquisizione](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

### Tutorial e guida introduttiva

- [Guida introduttiva di AJO B2B edition](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [Tutorial su B2B edition per RT-CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-tutorial)
