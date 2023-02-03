---
title: Journey Optimizer - Blueprint per messaggistica di terze parti
description: Mostra come Adobe Journey Optimizer può essere utilizzato con sistemi di messaggistica di terze parti per orchestrare e inviare comunicazioni personalizzate.
solution: Journey Optimizer
exl-id: 3a14fc06-6d9c-4cd8-bc5c-f38e253d53ce
source-git-commit: b18d491fdefc57762932d1570401b5437bf97c76
workflow-type: ht
source-wordcount: '823'
ht-degree: 100%

---

# Blueprint per messaggistica di terze parti

Mostra come Adobe Journey Optimizer può essere utilizzato con sistemi di messaggistica di terze parti per orchestrare e inviare comunicazioni personalizzate.

<br>

## Architettura

<img src="assets/3rd-party-messaging-architecture.svg" alt="Architettura di riferimento per il blueprint Journey Optimizer" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Prerequisiti

Adobe Experience Platform

* Gli schemi e i set di dati devono essere configurati nel sistema prima di poter configurare le origini dati di Journey Optimizer.
* Per poter attivare un evento non basato su regole, aggiungi il gruppo di campi Orchestration eventID agli schemi di eventi Experience basati su classi.
* Per poter caricare profili di test da utilizzare con Journey Optimizer, aggiungi il gruppo di campi “Profile test details” agli schemi per singoli profili basati su classi.

Applicazione di messaggistica di terze parti

* Deve supportare le chiamate API REST per l’invio di payload transazionali.

<br>

## Guardrail

[Link al prodotto per i guardrail Journey Optimizer](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=it)

Ulteriori guardrail Journey Optimizer:

* Ora la funzione di limitazione è disponibile tramite API per evitare che il sistema di destinazione venga saturato fino al punto di errore. I messaggi che superano il limite massimo vengono eliminati completamente e non vengono mai inviati. La regolazione della limitazione non è supportata.
   * Max connessioni: numero massimo di connessioni http/s che una destinazione può gestire
   * Numero max chiamate: numero massimo di chiamate da effettuare nel parametro periodInMs
   * periodInMs: tempo in millisecondi
* I percorsi avviati dall’appartenenza a un segmento possono funzionare in due modalità:
   * segmenti batch (aggiornati ogni 24 ore)
   * segmenti in streaming (&lt;5 minuti di qualificazione)
* Segmenti batch: necessario comprendere il volume giornaliero di utenti qualificati e accertarsi che il sistema di destinazione sia in grado di gestire il throughput burst per percorso e per tutti i percorsi.
* Segmenti in streaming: il burst iniziale delle qualifiche dei profili deve poter essere gestito insieme al volume giornaliero di qualificazione dello streaming, per ogni percorso e per tutti i percorsi.
* La funzionalità Gestione delle decisioni non è supportata
* Integrazioni in uscita con sistemi di terze parti
   * Singoli indirizzi IP statici non sono supportati, in quanto la nostra infrastruttura è multi-tenant (inserire tutti gli indirizzi IP dei datacenter nell’elenco degli IP consentiti).
   * Per le azioni personalizzate sono supportati solo i metodi POST e PUT.
   * Autenticazioni supportate: token | password | OAuth2
* Non è possibile creare pacchetti e spostare singoli componenti di Adobe Experience Platform o Journey Optimizer tra diverse sandbox. È necessario reimplementarli nei nuovi ambienti.

<br>

Sistema di messaggistica di terze parti

* È necessario determinare il carico di chiamate API transazionali che può essere supportato dal sistema.
   * Numero di chiamate consentite al secondo
   * Numero di connessioni
* È necessario determinare il tipo di autenticazione necessario per effettuare chiamate API.
   * Tipi di autenticazione: token | password | OAuth2 supportati tramite Journey Optimizer
   * Durata cache autenticazione: per quanto tempo resta valido il token? 
* Se è supportata solo l’acquisizione batch, è necessario l’invio in streaming a un motore di archiviazione cloud come Amazon Kinesis o Azure Event Grid 1st.
   * I dati possono essere inviati in batch a questi motori di archiviazione cloud e incanalati nel sistema di terze parti.
   * Eventuale middleware necessario deve essere fornito dal cliente o da terze parti.

<br>

## Fasi di implementazione

### Adobe Experience Platform

#### Schema/set di dati

1. [Configurare singoli schemi di profilo, di esperienza e di entità multiple](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=it) in Experience Platform, in base ai dati forniti dal cliente
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) in Experience Platform per i dati da acquisire.
1. [Aggiungere etichette di utilizzo dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=it) ai set di dati in Experience Platform a scopo di governance.
1. [Creare le policy](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=it) che necessarie per applicare la governance alle destinazioni

#### Profilo/identità

1. [Creare namespace specifici per il cliente](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it)
1. [Aggiungere le identità agli schemi](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it)
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=it)
1. [Impostare i criteri di unione](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=it) per viste diverse del [!UICONTROL profilo cliente in tempo reale] (opzionale)
1. Creare segmenti da utilizzare in Journey

#### Origini/destinazioni

1. [Inserire i dati in Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=it) utilizzando API di streaming e connettori di origini.

### Journey Optimizer

1. Configurare l’origine dati di Experience Platform e determinare quali campi devono essere memorizzati nella cache come parte dei dati del profilo. I dati in streaming utilizzati per avviare un percorso cliente devono prima essere configurati in Journey Optimizer, per ottenere un ID di orchestrazione. Questo ID di orchestrazione viene quindi fornito allo sviluppatore che potrà utilizzarlo con l’acquisizione.
1. Configurare le origini dati esterne.
1. Configurare le azioni personalizzate per l’applicazione di terze parti.

### Configurazione push mobile (opzionale per l’eventuale raccolta di token da terze parti)

1. Implementare Experience Platform Mobile SDK per raccogliere i token push e le informazioni di accesso da associare ai profili cliente noti.
1. Utilizzare i tag di Adobe e creare una proprietà mobile con la seguente estensione:
   * Adobe Journey Optimizer
   * Rete Edge di Adobe Experience Platform
   * Identità  per rete Edge
   * Mobile Core
1. Assicurati di disporre di un flusso di dati dedicato per le implementazioni di app mobili rispetto alle implementazioni web.
1. Per ulteriori informazioni, consulta la [guida di Adobe Journey Optimizer Mobile](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer).

<br>

## Documentazione correlata

* [Documentazione di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it)
* [Documentazione di Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
* [Documentazione di Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=it)
* [Descrizione del prodotto Journey Optimizer](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer.html)
