---
title: Inoltro degli eventi
description: Scopri come inoltrare i dati evento in tempo reale raccolti tramite Edge Network a destinazioni non Adobe per scopi di analisi, archiviazione o pubblicità.
solution: Experience Platform
exl-id: 24964d27-db56-4fa4-a79f-1b6750564b34
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1165'
ht-degree: 0%

---

# Inoltro eventi

Questa guida descrive il modello di caso d&#39;uso per l&#39;inoltro degli eventi, che utilizza l&#39;elaborazione lato server in Edge Network [!DNL Adobe Experience Platform] per distribuire dati evento in tempo reale a destinazioni non Adobe, ad esempio piattaforme di analisi di terze parti, endpoint di archiviazione cloud, reti pubblicitarie o webhook personalizzati. È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono comprendere il funzionamento di questo modello, gli obiettivi aziendali supportati, i casi di utilizzo tattici che consente e le applicazioni Adobe coinvolte.

## Schema del caso d’uso

Questa sezione descrive il modello e il piano di esecuzione utilizzati per implementare l’inoltro degli eventi.

**Inoltro eventi**: inoltra i dati evento in tempo reale raccolti tramite Edge Network a destinazioni non Adobe per scopi di analisi, archiviazione o pubblicità.

**Piano di esecuzione:** Configurazione flusso di dati > Definizione regola evento > Mapping destinazione > Esecuzione inoltro > Monitoraggio

## Panoramica del caso d’uso

Le organizzazioni che raccolgono dati comportamentali tramite l&#39;API di [!DNL Adobe Experience Platform] Web SDK, Mobile SDK o Server spesso devono condividere lo stesso flusso di eventi con sistemi non Adobe: piattaforme di analisi come [!DNL Google Analytics] o [!DNL Snowflake], reti pubblicitarie per il monitoraggio delle conversioni, data warehouse per l&#39;archiviazione a lungo termine o servizi interni personalizzati. In genere, questo richiedeva la proliferazione di tag lato client, che aumenta il peso delle pagine, introduce latenza e crea rischi per la privacy e la governance.

L’inoltro degli eventi risolve questo problema operando lato server su Edge Network. Quando un’interazione con un visitatore attiva un evento tramite Web SDK o l’API server, tale evento viene instradato attraverso un flusso di dati a Edge Network. Le regole di inoltro degli eventi, configurate in una proprietà di inoltro degli eventi dedicata, valutano i dati degli eventi in arrivo e li inoltrano selettivamente a una o più destinazioni configurate. Questo approccio lato server riduce l’ingrossamento dei tag lato client, migliora le prestazioni delle pagine, centralizza la governance dei dati e offre all’organizzazione il controllo esatto sui dati che lasciano l’ecosistema Adobe.

Il pubblico di destinazione per questo modello include organizzazioni che hanno già distribuito (o intendono distribuire) l&#39;API server o Web SDK [!DNL Adobe Experience Platform] per la raccolta dei dati e desiderano estendere tale investimento distribuendo i dati evento agli endpoint non Adobe senza aggiungere tag JavaScript lato client.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### Migliorare la qualità e la governance dei dati

Garantire dati puliti, completi e conformi per un targeting accurato, una riduzione degli sprechi e analisi affidabili. L&#39;inoltro degli eventi centralizza la distribuzione dei dati sul lato server, offrendo all&#39;organizzazione un unico punto di controllo per i dati condivisi con i sistemi esterni, riducendo il rischio di perdita di dati e garantendo l&#39;applicazione dei criteri di governance prima che i dati lascino l&#39;Edge Network [!DNL Adobe].

**KPI:** efficienza, risparmi sui costi

Per ulteriori informazioni, consulta [Migliorare la qualità e la governance dei dati](../../business-objectives/cost-efficiency/improve-data-quality-governance.md).

### Consolidamento e modernizzazione delle tecnologie di marketing

Ridurre la frammentazione degli strumenti e il debito tecnico con la migrazione a piattaforme unificate e scalabili. L’inoltro degli eventi consente alle organizzazioni di sostituire più tag dei fornitori lato client con un unico meccanismo di distribuzione dei dati lato server, riducendo il sovraccarico di caricamento delle pagine e semplificando lo stack di tecnologia.

**KPI:** Risparmio sui costi, efficienza, rapidità di commercializzazione

Per ulteriori informazioni, vedere [Consolidare e modernizzare la tecnologia di marketing](../../business-objectives/cost-efficiency/consolidate-modernize-marketing-technology.md).

## Esempi di casi d’uso tattici

Di seguito sono riportati gli scenari tattici comuni in cui si applica questo modello di caso d’uso.

- **Arricchimento di analisi di terze parti** - Inoltra in tempo reale eventi di visualizzazione pagina, clic e conversione a [!DNL Google Analytics], [!DNL Snowflake] o altre piattaforme di analisi senza aggiungere tag lato client
- **Tracciamento conversione Advertising** - Invia eventi di acquisto e generazione lead a [!DNL Meta] API di conversione, [!DNL Google Ads], [!DNL TikTok] o [!DNL Snap] per la misurazione e l&#39;ottimizzazione della conversione lato server
- **Streaming data warehouse**: instrada i dati evento non elaborati a un data warehouse cloud ([!DNL Google BigQuery], [!DNL Amazon S3], [!DNL Azure Event Hubs]) per l&#39;archiviazione a lungo termine e l&#39;analisi offline
- **Integrazione webhook personalizzata**: inoltro di dati evento filtrati o trasformati a microservizi interni, sistemi CRM o piattaforme partner tramite endpoint HTTP
- **Riduzione dei tag e miglioramento delle prestazioni delle pagine**: sostituzione di più tag JavaScript del fornitore lato client con un&#39;unica implementazione di Web SDK e regole di inoltro degli eventi lato server, riducendo il peso delle pagine e migliorando Core Web Vitals
- **Condivisione dei dati conforme alla privacy**: applica il filtro dei dati e le regole di redazione a livello di campo lato server prima di condividere i dati dell&#39;evento con terze parti, assicurandosi che i dati PII vengano eliminati o sottoposti ad hashing prima di raggiungere i sistemi esterni
- **Distribuzione di eventi multi-cloud**: inoltra simultaneamente lo stesso flusso di eventi a più destinazioni (ad esempio, analytics, advertising e data warehouse) da un singolo set di regole lato server
- **Inoltro del segnale di frode in tempo reale**: inoltra eventi di transazione di valore elevato ai sistemi di rilevamento delle frodi per il punteggio del rischio in tempo reale e gli avvisi

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare il successo di questo modello di caso d’uso.

- **Riduzione del tempo di caricamento delle pagine**: è stato misurato un miglioramento della velocità di caricamento delle pagine e di Core Web Vitals dopo la migrazione dei tag lato client all&#39;inoltro eventi lato server
- **Tasso di successo della consegna dati** — Percentuale di eventi inoltrati correttamente agli endpoint di destinazione senza errori o timeout
- **Riduzione del numero di tag** — Numero di tag fornitore lato client rimossi dopo l&#39;implementazione di equivalenti lato server
- **Aggiornamento/latenza dati** — Tempo tra l&#39;occorrenza dell&#39;evento sul client e l&#39;arrivo dell&#39;evento all&#39;endpoint di destinazione (destinazione: da un secondo all&#39;altro)
- **Tasso di conformità alla governance**: percentuale di condivisioni di dati in uscita che passano attraverso le regole di filtro lato server, garantendo che nessun PII o dati con restrizioni raggiunga destinazioni non autorizzate
- **Efficienza operativa**: riduzione delle ore dedicate agli sviluppatori per la gestione delle distribuzioni di tag lato client e la risoluzione dei conflitti di tag

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Adobe Experience Platform] (Edge Network)** — Riceve e instrada dati evento in tempo reale da Web SDK, Mobile SDK o Server API tramite flussi di dati configurati
- **[!DNL Adobe Experience Platform] (Inoltro eventi)** - Fornisce il motore delle regole lato server per la valutazione, il filtraggio, la trasformazione e l&#39;inoltro dei dati evento a destinazioni esterne
- **[!DNL Adobe Experience Platform] (Tag / Raccolta dati)** - Gestisce il ciclo di vita, le estensioni, le regole e il flusso di lavoro di pubblicazione della proprietà di inoltro degli eventi

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sugli argomenti trattati in questa guida.

**Inoltro eventi**

- [Panoramica sull’inoltro degli eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [Guida introduttiva all’inoltro degli eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)
- [Monitoraggio inoltro eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring)
- [Segreti di inoltro eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)

**Estensioni di inoltro eventi**

- [Catalogo delle estensioni lato server](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [Estensione Adobe Cloud Connector](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [Estensione API per conversioni Meta](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/meta/overview)
- [Estensione Piattaforma Google Cloud](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [Estensione AWS](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/aws/overview)
- [Estensione Snowflake](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/snowflake/overview)
- [Estensione per conversioni avanzate di Google Ads](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-ads-enhanced-conversions/overview)
- [Estensione Mailchimp](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/mailchimp/overview)

**Raccolta dati e Edge Network**

- [Configurare gli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Panoramica sugli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview)
- [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Panoramica dell’API del server Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Panoramica sui tag](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
