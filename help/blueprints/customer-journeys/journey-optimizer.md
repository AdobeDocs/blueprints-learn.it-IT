---
title: Journey Optimizer - Messaggi attivati e blueprint Adobe Experience Platform
description: Esegui messaggi ed esperienze attivate utilizzando Adobe Experience Platform come hub centrale per lo streaming di dati, profili dei clienti e segmentazione.
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: dc13a1fe9a32f70497c5c73485618e6989b7a644
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 49%

---

# Journey Optimizer

Adobe Journey Optimizer è un sistema appositamente progettato che consente ai team di marketing di reagire in tempo reale ai comportamenti dei clienti e di incontrarli dove si trovano. Le funzionalità di gestione dei dati sono state spostate in Adobe Experience Platform, consentendo ai team di marketing di concentrarsi sulle attività migliori: che sta creando un percorso di clienti di livello mondiale e conversazioni personalizzate.  Questo modello delinea le capacità tecniche dell&#39;applicazione e fornisce un&#39;analisi approfondita dei vari componenti architettonici che compongono Adobe Journey Optimizer.

## Casi di utilizzo

* Messaggi attivati
* Conferme di registrazione
* Abbandoni del carrello e del modulo di richiesta
* Messaggi attivati dalla posizione

## Architettura

<img src="assets/journey-optimizer.png" alt="Architettura di riferimento per il blueprint per messaggistica attivata e Adobe Experience Platform" style="border:1px solid #4a4a4a" />

## Pattern di integrazione

* Adobe Experience Platform -> Journey Optimizer

## Prerequisiti

1. È necessario effettuare il provisioning del cliente per Experience Cloud con un’organizzazione IMS valida
1. Push mobile

* Per creare l’app, il cliente deve avere uno sviluppatore mobile disponibile
* Adobe Experience Platform Mobile SDK
* Adobe Launch
   * Proprietà mobile
      * Estensioni:
         * Estensione Adobe Journey Optimizer
         * Adobe Experience Platform Edge Network
         * Identità
         * Core mobile
         * Profilo
   * Configurazioni app
   * Datastreams
      * Abilitato per Experience Platform
      * Set di dati evento - utilizzato per la raccolta del comportamento generale dei dispositivi mobili
      * Set di dati del profilo - Set di dati del profilo push AJO (non può essere diverso)

## Guardrail

* Per ulteriori dettagli sulle limitazioni, fai clic su questo link.
* Segmenti in batch: è necessario assicurarsi di comprendere il volume giornaliero di utenti qualificati e assicurarsi che il sistema di destinazione sia in grado di gestire il throughput burst per percorso e in tutti i percorsi
* Segmenti in streaming: è necessario garantire che lo scoppio iniziale delle qualifiche di profilo possa essere gestito insieme al volume giornaliero di qualificazione in streaming per percorso e per tutti i percorsi
* Attività di aggiornamento del profilo : il Profilo del cliente in tempo reale può essere aggiornato in modo nativo da un percorso.  Si verifica un ritardo di fino a 1 minuto nell’elaborazione dell’aggiornamento nell’archivio dei profili
* Eventi aziendali: è possibile attivare un percorso basato su segmenti di lettura da avviare in base a una chiamata esterna al sistema JO
* Supporta in modo nativo solo l’Offer decisioning nei messaggi. Supporto futuro tramite azione nativa
* Canali supportati:
   * E-mail
   * Push (FCM / APNS)
   * Endpoint API per il resto
* Elabora eventi 5k al secondo con scalabilità orizzontale (wallet is limit)
* Il test A/B viene eseguito utilizzando due consegne e determinando i risultati tramite QS o CJA
* Integrazione Litmus - deve avere un account con Litmus per sfruttare l&#39;integrazione

## Fasi di implementazione

### Adobe Experience Platform

#### Schema/set di dati

1. [Configurare singoli schemi di profilo, di esperienza e di entità multiple](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html?lang=it) in Experience Platform, in base ai dati forniti dal cliente
1. Creare schemi di Adobe Campaign per broadLog, trackingLog, indirizzi non consegnabili e preferenze profilo (opzionale)
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) in Experience Platform per i dati da acquisire.
1. [Aggiungere etichette di utilizzo dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=it) ai set di dati in Experience Platform a scopo di governance.
1. [Creare i criteri](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=it) necessari per applicare la governance alle destinazioni

#### Profilo/Identità

1. [Creare namespace specifici per il cliente](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it)
1. [Aggiungere le identità agli schemi](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=it)
1. [Impostare i criteri di unione](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=it) per le diverse viste di [!UICONTROL Real-time Customer Profile] (opzionale)
1. Creare segmenti da utilizzare in Campaign

#### Origini/Destinazioni

1. [Inserire i dati in Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=it) utilizzando le API di streaming e i connettori di origini. 1. Configurare la destinazione di archiviazione BLOB di [!DNL Azure] da utilizzare con Adobe Campaign.

#### Implementazione di app mobili

1. Implementare Adobe Campaign SDK per Adobe Campaign Classic o Experience Platform SDK per Adobe Campaign Standard. Se è presente Experience Platform Launch, si consiglia di utilizzare l’estensione Adobe Campaign Classic o Adobe Campaign Standard con Experience Platform SDK.


### Journey Orchestration

1. I dati di streaming utilizzati per avviare un percorso cliente devono prima essere configurati in Journey Optimizer per ottenere un ID orchestrazione. Questo ID di orchestrazione viene quindi fornito allo sviluppatore che potrà utilizzarlo con l’acquisizione.
1. Configurare le origini dati esterne.
1. Configurare le azioni personalizzate.

## Documentazione correlata

* [Documentazione di Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [Documentazione di Journey Optimizer](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=it)
* [Documentazione di Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=it)
* [Documentazione di Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
