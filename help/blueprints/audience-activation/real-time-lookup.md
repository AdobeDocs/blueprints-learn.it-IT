---
title: Accesso in tempo reale al profilo Edge per Personalization web e mobile
description: '[!UICONTROL Accesso al Profilo cliente in tempo reale] ai server Edge di per fornire contesto per la personalizzazione web e mobile in tempo reale.'
solution: Real-Time Customer Data Platform, Data Collection
kt: 719
source-git-commit: 2fad3a8a9210d703130f251b0bd7cc4c0b7cbd32
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 6%

---

# Accesso in tempo reale al profilo Edge per Personalization web e mobile

Il blueprint Real-time Edge Profile Access for Web and Mobile Personalization mostra come le applicazioni web e mobili possono accedere al [!UICONTROL Profilo cliente in tempo reale] di Adobe Experience Platform alla periferia per una personalizzazione ad alta velocità e bassa latenza.

Le applicazioni possono accedere agli attributi del profilo in tempo reale e ai tipi di pubblico periferici con latenza di millisecondi. Gli attributi, le appartenenze al pubblico e le funzioni basate su modelli memorizzati nel profilo come attributi sono accessibili in tempo reale per la personalizzazione della stessa pagina e della pagina successiva su canali web e mobili.

Con questa funzionalità, puoi fornire esperienze altamente personalizzate sui tuoi siti web e applicazioni mobili basate sul Profilo cliente in tempo reale, inclusi tipi di pubblico derivati da comportamenti in tempo reale, attributi acquisiti nel Profilo cliente in tempo reale e informazioni calcolate.

>[!NOTE]
>
>L’accesso al profilo di Edge è progettato specificamente per casi di utilizzo ad alta velocità effettiva e a bassa latenza, come la personalizzazione in entrata web/mobile e il Offer Decisioning in tempo reale. Per scenari di throughput inferiore, come il supporto assistito da agente o le interazioni di vendita, l’API di ricerca del profilo Hub è più appropriata. Per l&#39;accesso al profilo basato su hub, vedere il blueprint [Real-time Profile Access for Support and Sales Scenarios](customer-activity.md).

## Applicazioni

* Real-time Customer Data Platform
* Raccolta dati di Adobe Experience Platform (Web SDK / Mobile SDK)
* API server di Edge Network

## Casi di utilizzo

* Personalizzazione in tempo reale su canali web e mobili per esperienze cliente note
* Personalizzazione della stessa pagina e della pagina successiva basata su attributi di profilo e pubblico in tempo reale
* Personalizzazione dei contenuti e delle offerte basata sui profili dei clienti, inclusi dati comportamentali in tempo reale, attributi e informazioni calcolate
* Integrazione con motori di personalizzazione, sistemi di gestione dei contenuti e applicazioni esterne per decisioni in tempo reale
* Test e ottimizzazione dei contenuti con contesto di profilo in tempo reale

## Prerequisiti

Se desideri che il profilo venga aggiornato in tempo reale con i dati in streaming, questo blueprint richiede l’utilizzo di uno dei seguenti metodi di raccolta dati. È possibile accedere in tempo reale al profilo Edge senza dover raccogliere i dati direttamente sul profilo Edge; i dati possono essere raccolti nell’hub e proiettati anche sul profilo Edge. Tieni presente che verrà aggiunta la latenza per i dati raccolti nell’hub e quindi proiettati nell’Edge.

* Utilizza [Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html?lang=it) per raccogliere dati dal tuo sito Web.
* Utilizza [Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/) se desideri raccogliere dati dalla tua app mobile.
* Utilizza l&#39;[API server di Edge Network](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=it) se non utilizzi Web SDK o Mobile SDK o se implementi una connessione più diretta tra server.

>[!IMPORTANT]
>
>Prima di implementare la personalizzazione Edge, leggi la guida su come [attivare i dati sul pubblico nelle destinazioni di personalizzazione Edge](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations). Questa guida illustra i passaggi di configurazione necessari per i casi di utilizzo della personalizzazione della stessa pagina e della pagina successiva, su più componenti di Experience Platform.

## Diagramma architettura

<img src="assets/real-time-edge-lookup.svg" alt="Architettura di riferimento per l’accesso ai profili Edge per web e Personalization mobile" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## Guardrail

* [Guardrail per i dati del [!UICONTROL profilo cliente in tempo reale]](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)
* [Guardrail Edge Network](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* I profili Edge hanno un TTL (time-to-live) di 14 giorni. Se un utente non è attivo sul server Edge per 14 giorni, il profilo Edge potrebbe scadere e richiedere il recupero dall’hub, il che potrebbe influire sulla personalizzazione della prima pagina.
* La funzione di personalizzazione di Edge supporta la valutazione in tempo reale dell’iscrizione al pubblico per i tipi di pubblico che soddisfano i criteri di segmentazione Edge. I tipi di pubblico in batch e in streaming dall’hub sono disponibili anche al limite con la configurazione appropriata.

## Modelli di implementazione

La personalizzazione di Edge può essere implementata utilizzando la destinazione [Connessione Personalization personalizzata](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/personalization/custom-personalization) in Real-time Customer Data Platform. Questa destinazione supporta più metodi di raccolta dati a seconda del caso d’uso.

### Pattern 1: personalizzazione basata sull’iscrizione del pubblico con Web SDK/Mobile SDK

* Utilizza Adobe Experience Platform Web SDK o Mobile SDK con Edge Network per la personalizzazione basata sull’iscrizione del pubblico.
* Questo approccio offre bassa latenza e prestazioni migliori per la personalizzazione Edge in base alle appartenenze a un pubblico.
* La segmentazione Edge in tempo reale richiede l’implementazione di Web/Mobile SDK.
* Web SDK e Mobile SDK **supportano da soli la personalizzazione basata solo sull&#39;iscrizione al pubblico**.
* [Consulta la blueprint per Experience Platform Web e Mobile SDK](../experience-platform/deployment/websdk.md) per l&#39;implementazione basata su SDK.
* Per l&#39;implementazione di Mobile SDK, l&#39;estensione [Adobe Journey Optimizer - Decisioning](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/) deve essere installata in Mobile SDK.

### Pattern 2: personalizzazione basata su attributi con API server di Edge Network (obbligatorio per gli attributi del profilo)

>[!IMPORTANT]
>
>**Requisiti di personalizzazione basati su attributi:** Se desideri personalizzare in base agli attributi del profilo (non solo all&#39;appartenenza al pubblico), **devi** utilizzare l&#39;[API server di Edge Network](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=it) con integrazione lato server autenticata, indipendentemente dal fatto che si utilizzi anche Web SDK o Mobile SDK per la raccolta dei dati.

* Consente l’integrazione con motori di personalizzazione di terze parti e la personalizzazione basata su CDN.
* L&#39;API server di Edge Network è **necessaria** per recuperare in modo sicuro gli attributi del profilo per la personalizzazione.
* Puoi recuperare gli attributi del profilo tramite l’API server di Edge Network aggiungendo un’integrazione lato server che utilizza lo stesso flusso di dati già in uso per l’implementazione Web o Mobile SDK.
* Tutte le chiamate API del server Edge Network per gli attributi del profilo devono essere effettuate in un contesto autenticato per proteggere i dati sensibili.
* Questo modello consente sia la personalizzazione basata sull’iscrizione del pubblico che la personalizzazione basata sugli attributi.
* Appropriato per casi d’uso di personalizzazione lato server, integrazioni basate su API e scenari che richiedono l’accesso agli attributi di profilo.

## Fasi di implementazione

1. [Creare schemi](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&lang=it) per i dati da acquisire.
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) per i dati da acquisire.
1. [Configura le identità e gli spazi dei nomi di identità corretti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it) nello schema per garantire che i dati acquisiti possano essere uniti in un profilo unificato.
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=it).
1. [Inserire i dati](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&lang=it) in Experience Platform.
1. [Imposta i criteri di unione](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=it) per garantire la corretta unione delle identità e dei profili.
1. [Configura uno stream di dati](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=it) nella raccolta dati di Experience Platform con la configurazione di destinazione abilitata. Lo stream di dati determina in quale flusso di dati di Raccolta dati i tipi di pubblico verranno inclusi nella risposta alla pagina.
1. Implementare [Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html?lang=it) o [Mobile SDK](https://developer.adobe.com/client-sdks/home/) nelle proprietà Web e mobile per la raccolta dati.
1. Configura la segmentazione Edge per i tipi di pubblico che richiedono una valutazione in tempo reale. [Documentazione sulla segmentazione di Edge](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=it).
1. Nel catalogo delle destinazioni, impostare la destinazione [Connessione Personalization personalizzata](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/personalization/custom-personalization):
1. [Attiva il pubblico nella destinazione di personalizzazione Edge](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations). Seleziona i tipi di pubblico da attivare nella destinazione.
1. (Facoltativo per la personalizzazione basata su attributi) Se oltre all&#39;appartenenza al pubblico devi personalizzare in base agli attributi del profilo, implementa [Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=it) con integrazione lato server autenticata utilizzando lo stesso flusso di dati. **obbligatorio** per accedere agli attributi del profilo.
1. Implementa la logica di personalizzazione nell’app web/mobile per utilizzare i dati del pubblico e gli attributi di profilo esportati:
   * Se si utilizzano i tag in Adobe Experience Platform, utilizzare la funzionalità [invia evento completato](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=it) per accedere alla variabile `event.destinations` con i dati esportati.
   * Se non utilizzi i tag, utilizza [risposte ai comandi](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html?lang=it) per analizzare la risposta JSON da Adobe Experience Platform e recuperare gli ID del pubblico e gli attributi del profilo.

## Considerazioni sull’implementazione

### Considerazioni sull’identità

* Qualsiasi identità primaria può essere utilizzata per la personalizzazione Edge quando si utilizza Web SDK o Mobile SDK con Edge Network.
* Per la personalizzazione del primo accesso con dati cliente noti, la richiesta di personalizzazione deve utilizzare un’identità primaria che corrisponda all’identità cliente nota in Real-time Customer Data Platform. Se l’ID primario è impostato su ECID o su un’identità anonima che non è ancora stata unita al profilo cliente noto, la realizzazione dell’unione di identità richiederà del tempo, il che potrebbe influire sulla disponibilità di dati di profilo storici per la personalizzazione.
* I profili Edge devono essere inizializzati prima di poter essere utilizzati per la personalizzazione. I visitatori nuovi o i visitatori di ritorno il cui profilo Edge è scaduto (TTL di 14 giorni) possono beneficiare di una personalizzazione iniziale basata su dati di profilo limitati fino a quando il profilo Edge non è completamente popolato.

### Personalizzazione basata su attributi

>[!IMPORTANT]
>
>Gli attributi del profilo possono contenere dati sensibili. Per proteggere questi dati, **devi** utilizzare l&#39;[API server di Edge Network](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=it) durante la configurazione della destinazione Personalization personalizzata per la personalizzazione basata su attributi. Tutte le chiamate API del server Edge Network devono essere effettuate in un contesto autenticato.

* Per la personalizzazione basata su attributi che utilizzano gli attributi del profilo, devi aggiungere un’integrazione lato server con l’API server di Edge Network che utilizza lo stesso stream di dati utilizzato per l’implementazione Web o Mobile SDK.
* È necessario configurare gli attributi di profilo da includere nella proiezione Edge tramite la configurazione di destinazione Custom Personalization Connection.
* **Web SDK e Mobile SDK supportano solo la personalizzazione basata sull&#39;appartenenza al pubblico**. L&#39;API server di Edge Network è **necessaria** per recuperare in modo sicuro gli attributi del profilo per la personalizzazione.
* Se non implementi l’API server di Edge Network per l’accesso agli attributi, la personalizzazione sarà basata solo sull’iscrizione al pubblico.
* La risposta API per Personalization personalizzato con attributi include una sezione `attributes` oltre ai segmenti di pubblico.

### Considerazioni sul pubblico

* I tipi di pubblico valutati tramite streaming o segmentazione batch sull’hub sono proiettati al limite e possono essere utilizzati per la personalizzazione.
* I tipi di pubblico che soddisfano i criteri di segmentazione Edge vengono valutati in tempo reale al limite per la personalizzazione della stessa pagina.
* Configura tipi di pubblico appropriati per la valutazione Edge in base al loro utilizzo nei casi di utilizzo di personalizzazione in tempo reale.

## Documentazione correlata

### Configurazioni di destinazione

* [Connessione Personalization personalizzata](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/personalization/custom-personalization) - Guida all&#39;implementazione primaria
* [Panoramica sulle destinazioni Personalization](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/personalization/overview)
* [Attiva i tipi di pubblico nelle destinazioni di personalizzazione Edge](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)
* [Cerca gli attributi del profilo sul server Edge in tempo reale](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-edge-profile-lookup)

### Documentazione di SDK

* [Documentazione di Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html?lang=it)
* [Documentazione di Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/)
* [Documentazione API di Edge Network Server](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=it)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it)
* [Risposte ai comandi in Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html?lang=it)

### Documentazione su profilo e segmentazione

* Documentazione del [[!UICONTROL profilo cliente in tempo reale]](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=it)
* [Guardrail per il profilo](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)

### Tutorial

* [Personalizzazione con hit successivo con Real-Time CDP e Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=it)
* [Configurazione dello stream di dati](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=it)
