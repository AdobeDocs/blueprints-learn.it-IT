---
title: Blueprint di accesso ed esportazione dei dati
description: Questo modello fornisce una panoramica di tutti i metodi con cui è possibile accedere ai dati ed esportarli da Adobe Experience Platform e dalle applicazioni.
product: adobe experience platform
solution: Experience Platform, Journey Optimizer, Real-time Customer Data Platform, Tags
exl-id: 2ca51a29-2db2-468f-8688-fc8bc061b47b
source-git-commit: c0fe0e94e30351f593e32ea0e6809dd832f976ad
workflow-type: tm+mt
source-wordcount: '1513'
ht-degree: 5%

---

# Blueprint di accesso ed esportazione dei dati

La Blueprint di accesso ed esportazione dei dati delinea tutti i metodi possibili con cui è possibile accedere ai dati o esportarli da Adobe Experience Platform e dalle applicazioni.

La Blueprint è suddivisa in due categorie per l&#39;accesso ai dati da Experience Platform e applicazioni. In primo luogo, approcci per l&#39;acquisizione di dati provenienti da Experienci Platform e applicazioni; questo sarebbe considerato un metodo di tipo push per l’uscita dei dati. In secondo luogo, approcci per i dati di accesso provenienti da Experienci Platform e applicazioni; questo sarebbe considerato un metodo di accesso ai dati di tipo pull.

Approcci per l’accesso ai dati

* [API di accesso al profilo cliente in tempo reale](#rtcp-profile-access-api)
* [API di accesso ai dati](#data-access-api)
* [Query Service](#query-service)

Approcci all’esportazione dei dati

* [Tag lato client](#client-side-tags-extensions)
* [Inoltro eventi](#event-forwarding)
* [Destinazioni Real-time Customer Data Platform](#RTCDP-destinations)
* [Azioni personalizzate Journey Optimizer](#jo-custom-actions)

## Architettura della panoramica di accesso ed esportazione dei dati

<img src="../experience-platform/assets/aep_data_flow.svg" alt="Architettura di riferimento del blueprint per preparazione e acquisizione dei dati" style="width:90%; border:1px solid #4a4a4a" />

## Approcci per l’accesso ai dati

### API di accesso al profilo cliente in tempo reale {#rtcp-profile-access-api}

I clienti possono accedere a singoli profili unificati dall’archivio profili cliente in tempo reale, inclusi tutte le identità di profilo, le iscrizioni al pubblico, gli attributi e gli eventi di esperienza utilizzando l’API di accesso ai profili cliente in tempo reale.

Fai riferimento a [API di accesso al profilo cliente in tempo reale](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=en) documentazione per ulteriori informazioni.

#### Casi di utilizzo

* Ricercare un singolo profilo per aggiungere contesto all’interazione con il cliente dell’agente, ad esempio le interazioni di supporto tramite chat e call center, o un’interazione di vendita nel punto vendita.
* Consente di aggiungere contesto a una descrizione di personalizzazione effettuata da un sistema esterno, ad esempio un sistema di personalizzazione web o un sistema decisionale per le offerte.

#### Considerazioni

* Profilo cliente in tempo reale [guardrail](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) applicare.
* Progettato per la ricerca di singoli profili alla volta. Non utilizzato per l’accesso in massa al profilo o per il download dell’intera popolazione del profilo per l’utilizzo di analisi o scienza dei dati.
* Il tempo di risposta della ricerca del profilo è conforme alle protezioni del profilo. Requisiti di latenza in tempo reale bassa : ad esempio per gli stessi requisiti di personalizzazione delle pagine, utilizza il profilo Edge da a [Connessione Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=it) o [Connessione personalizzazione personalizzata](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/custom-personalization.html?lang=en) per l’accesso in tempo reale ai profili per nel browser e nella personalizzazione delle app.

### API di accesso ai dati {#data-access-api}

I clienti che utilizzano l’API di accesso ai dati possono accedere direttamente ai file di set di dati non elaborati memorizzati nel data lake di Experience Platform.

* Per ulteriori informazioni sull’utilizzo dell’API di accesso ai dati, consulta la [documentazione](https://experienceleague.adobe.com/docs/experience-platform/data-access/home.html?lang=en).

#### Casi di utilizzo

* Estrarre file di dati grezzi ed elaborati da Experience Platform per lo storage e la valutazione in ambienti aziendali.

#### Considerazioni

* Poiché l’accesso ai dati viene effettuato in modo asincrono in batch, l’accesso ai dati sarà intrinsecamente latente rispetto agli approcci in uscita dei dati in streaming, come l’utilizzo di Tag, Inoltro eventi o Destinazioni RTCDP.
* I file di dati elaborati in Experience Platform vengono memorizzati come raccolte di file in batch e vengono compressi e memorizzati in formato parquet. Come tali, quando accedono e scaricano i file in un ambiente diverso, devono essere sistematicamente accessibili dal loro batch e file al posto di un intero set di dati e le operazioni sui dati devono tenere conto dei file compressi in formato parquet.

### Servizio query {#query-service}

I clienti del servizio Query di experience platform possono eseguire query sui set di dati all’interno di Experience Platform e mantenere i risultati della query. È possibile utilizzare un client SQL per eseguire query e mantenere la risposta alla query nella destinazione di archiviazione desiderata supportata dal client SQL. L’interfaccia utente del servizio query può essere utilizzata per memorizzare il risultato SQL in un set di dati di destinazione nell’Experience Platform oppure i risultati possono essere salvati nel computer locale.

* Per ulteriori dettagli sulla connessione ai client SQL per mantenere i risultati SQL da Experience Platform Query Service, vedere quanto segue [documentazione](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=en).

#### Casi di utilizzo

* Eseguire query sui dati non elaborati dai set di dati di Experience Platform e mantenere i risultati della query.
* Esegui una query sul set di dati dello snapshot del profilo per estrarre informazioni sul profilo cliente in tempo reale. [Documentazione](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=en#profile-attribute-datasets).
* Le query di archiviazione vengono archiviate in un set di dati separato per l&#39;accesso o in un set di dati abilitato per il profilo che può essere successivamente esaminato tramite RTCDP e altre applicazioni di Experience Cloud che accedono al Profilo cliente in tempo reale.

#### Considerazioni

* Poiché i dati vengono interrogati in modo asincrono in batch, l’accesso ai dati sarà intrinsecamente latente rispetto agli approcci in uscita dei dati in streaming, come l’utilizzo di tag, inoltro eventi o destinazioni RTCDP.
* È possibile eseguire query solo sui dati disponibili nel data lake di Experience Platform utilizzando il servizio Query. Non è possibile eseguire query dirette sull&#39;archivio dei profili cliente in tempo reale, sul grafico dell&#39;identità e sul Customer Journey Analytics utilizzando il servizio query. Solo quando i set di dati vengono esportati nel data lake è possibile eseguire una query su questi set di dati, come nell’esempio del set di dati dello snapshot del profilo.
* Tieni presente che si applicano le protezioni per il numero di risultati della query e il timeout della query, come descritto in [Garanzie dei servizi di query](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=en) documentazione.

## Approcci per l’esportazione dei dati

### Estensioni tag lato client {#client-side-tags-extensions}

Le estensioni possono essere distribuite utilizzando la soluzione Tag di Adobe. Una volta implementata un’estensione, le richieste di dati vengono distribuite direttamente su un browser client o su un’applicazione e puoi invocare una richiesta per inviare dati e richieste alla destinazione desiderata.

Fai riferimento a [Panoramica sui tag](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en) documentazione per ulteriori informazioni.

#### Casi di utilizzo

* È possibile raccogliere informazioni sullo streaming non elaborato direttamente dagli ambienti lato client tramite l’utilizzo di tag.

#### Considerazioni

* Nessun accesso diretto a informazioni lato server, come il Profilo cliente in tempo reale Experience Platform e le iscrizioni al pubblico.
* L’aggiunta di tag di raccolta dati aggiuntivi alla pagina potrebbe aumentare i tempi di caricamento della pagina.
* Possibilità di impostare regole per richiedere dati solo quando vengono soddisfatti determinati criteri.
* I dati vengono raccolti direttamente dal cliente, limitando i tipi di trasformazione e di arricchimento che possono essere eseguiti prima della raccolta dei dati.

### Inoltro eventi {#event-forwarding}

Le richieste di raccolta dati vengono raccolte direttamente su Adobe Edge Network. Dalle richieste di rete Edge agli endpoint RESTful esterni può essere configurato per inoltrare queste richieste alla destinazione esterna.

Consulta quanto segue [Inoltro eventi](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en) documentazione per ulteriori informazioni.

#### Usa casi

* Raccogli informazioni di streaming non elaborato direttamente dagli ambienti lato client a un endpoint enterprise utilizzando l’inoltro degli eventi lato server di Adobe.

#### Considerazioni

* Per utilizzare l’inoltro eventi, i dati devono essere inviati a Edge Network tramite WebSDK o MobileSDK.
* L’approccio di inoltro degli eventi riduce il tempo di caricamento e il peso della pagina a causa dell’aggiunta di tag aggiuntivi sulla pagina.
* Al momento non è supportato alcun arricchimento dal profilo Edge o da altre origini dati.
* Sono supportati il filtraggio dei dati limitato e semplici trasformazioni di mappatura.

### Destinazioni Real-time Customer Data Platform {#RTCDP-destinations}

I dati degli attributi del profilo e i dati di iscrizione al pubblico possono essere attivati nelle destinazioni aziendali e pubblicitarie. Ciò significa che i dati in questione devono essere acquisiti nel Profilo cliente in tempo reale Experience Platform.

Fai riferimento a [Destinazioni Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=en) documentazione per ulteriori informazioni.

#### Casi di utilizzo

* Attiva le informazioni sull’attributo del profilo, inclusa l’iscrizione al pubblico, in archivi di dati aziendali interni, strumenti di analisi, sistemi e-mail o sistemi di supporto.
* Attiva l&#39;iscrizione al pubblico del profilo a un fornitore pubblicitario esterno per eseguire il targeting e personalizzare il contenuto per il profilo.

#### Considerazioni

* È possibile attivare gli attributi del profilo e le appartenenze al pubblico. Gli eventi di esperienza non elaborati non possono attualmente essere attivati come parte delle destinazioni RTCDP.
* Le attivazioni si verificano in streaming o in batch a seconda della natura dell’analisi dei segmenti e della natura del protocollo di acquisizione che la destinazione accetta.

### Azioni personalizzate Journey Optimizer {#jo-custom-actions}

I clienti di Journey Optimizer possono richiamare un’azione personalizzata dall’area di lavoro del percorso per inviare un payload o un messaggio a un endpoint API esterno configurato. Un’azione può essere configurata per qualsiasi servizio proveniente da qualsiasi provider che possa essere chiamato tramite un’API REST con un payload in formato JSON. Questo payload può includere informazioni sull’evento, gli attributi del profilo e i dati dell’evento precedenti, le trasformazioni e gli arricchimenti configurati nel percorso.

Fai riferimento a [Azioni personalizzate Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions.html?lang=en) documentazione per ulteriori informazioni.

#### Casi di utilizzo

* Eventi di attivazione da Experience Platform e Journey Optimizer che includono informazioni aggiuntive dal Profilo cliente in tempo reale.
* Notifica i sistemi esterni quando un cliente ha raggiunto un punto specifico di un percorso.

#### Considerazioni

* Guardrail sul throughput supportato da [Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=it) e gli arricchimenti sostenuti dal [Profilo cliente in tempo reale](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) applicare.
* Le azioni personalizzate possono essere eseguite in streaming una per una per ogni evento o profilo in un percorso. Non è possibile eseguire operazioni in blocco o l’uscita di dati in blocco sotto forma di file o richieste aggregate tra percorsi di clienti.
* Accesso in streaming agli attributi del profilo cliente in tempo reale e agli eventi di esperienza che possono essere inclusi nel payload di attivazione.
* I dati evento possono essere filtrati e possono essere applicate semplici trasformazioni di mappatura prima di inviare eventi a destinazioni esterne.
