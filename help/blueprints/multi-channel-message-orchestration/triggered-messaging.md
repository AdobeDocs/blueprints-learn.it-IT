---
title: Messaggi attivati e blueprint Adobe Experience Platform
description: Esegui esperienze e messaggi attivati, utilizzando Adobe Experience Platform come hub centrale da cui trasmettere dati, profili cliente e segmentazioni.
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
translation-type: tm+mt
source-git-commit: 81df87f850b7ac4be9dce7a3b96d39a3a47685c5
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 69%

---

# Messaggi attivati e blueprint Adobe Experience Platform

Esegui esperienze e messaggi attivati, utilizzando Adobe Experience Platform come hub centrale da cui trasmettere dati, profili cliente e segmentazioni.

## Casi di utilizzo

* Messaggi attivati
* Conferme di registrazione
* Abbandoni del carrello e del modulo di richiesta
* Messaggi attivati dalla posizione

## Architettura

<img src="assets/triggered.svg" alt="Architettura di riferimento per la blueprint Adobe Experience Platform e la messaggistica attivata" style="border:1px solid #4a4a4a" />

## Pattern di integrazione

* Adobe Experience Platform -> Journey Orchestration

## Prerequisiti

* Adobe Experience Platform
* Journey Orchestration

## Guardrail

### Journey Orchestration

* Per [ulteriori dettagli sulle limitazioni](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=it#starting-with-journeys), fai clic su questo link.
* La funzione di limitazione è disponibile tramite l’impostazione API per garantire che il sistema di destinazione non sia saturato fino al punto di errore. Con la limitazione, i messaggi che superano il limite massimo vengono eliminati completamente e non vengono mai inviati. La regolazione della limitazione non è ancora supportata.
   * Max connessioni: numero massimo di connessioni http/s che una destinazione può gestire
   * Numero max chiamate: numero massimo di chiamate da effettuare nel parametro periodInMs
   * periodInMs: tempo in millisecondi
* I percorsi avviati dall’iscrizione a un segmento possono funzionare in due modalità:
   * segmenti batch (aggiornati ogni 24 ore)
   * segmenti in streaming (&lt;5 minuti di qualificazione)
* Segmenti batch: assicurati di comprendere il volume giornaliero di utenti qualificati in modo che il sistema di destinazione sia in grado di gestire il throughput burst per percorso e per tutti i percorsi.
* Segmenti in streaming: assicurati che il burst iniziale delle qualifiche dei profili possa essere gestito insieme al volume giornaliero di qualificazione dello streaming per percorso e per tutti i percorsi.
* La destinazione finale deve supportare REST API e il payload JSON.
* Attualmente non supporta Offer Decisioning.
* Vedi [guardrail per l’acquisizione di dati e profili per Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it).

### Adobe Campaign Standard

* È in grado di supportare solo 14 tps (50.000 all’ora) in termini di throughput.
* I percorsi avviati dalla partecipazione a un segmento non sono supportati.
* Gli eventi di reazione all’apertura/clic di un messaggio transazionale sono supportati in Journey Orchestration.
* I registri dei messaggi transazionali non sono attualmente sincronizzati in modo nativo con Experience Platform, e richiedono una configurazione manuale. Si consiglia di esportare i registri al massimo ogni quattro ore.


## Fasi di implementazione

### Adobe Experience Platform

#### Schema/set di dati

1. [Configurare singoli schemi di profilo, di esperienza e di entità multiple in Experience Platform, in base ai dati forniti dal cliente](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html)
1. Crea schemi Adobe Campaign per ampi log, trackingLog, indirizzi non recapitati e preferenze di profilo (facoltativo).
1. [Crea ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) dati in Experience Platform per i dati da acquisire.
1. [Aggiungi etichette di utilizzo dei dati ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html) in Experience Platform al set di dati per la governance.
1. [Creare le policy che necessarie per applicare la governance alle destinazioni](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html)

#### Profilo/identità

1. [Crea qualsiasi namespace](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html) specifico per il cliente.
1. [Aggiungi identità agli schemi](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Imposta ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) criteri di unione per diverse visualizzazioni del profilo cliente  [!UICONTROL in tempo reale]  (facoltativo).
1. Crea segmenti per l’utilizzo di Adobe Campaign.

#### Origini/Destinazioni

1. [Acquisisci dati in Experience ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) Platform utilizzando API di streaming e connettori sorgente.1. Configura la destinazione di archiviazione  [!DNL Azure] BLOB da utilizzare con Adobe Campaign.

#### Implementazione di app mobili

1. Implementa l’SDK per Adobe Campaign per Adobe Campaign Classic o l’SDK per Experience Platform per Adobe Campaign Standard. Se è presente un Experience Platform Launch, si consiglia di utilizzare l&#39;estensione Adobe Campaign Classic o Adobe Campaign Standard con Experience Platform SDK.


### Journey Orchestration

1. I dati di streaming utilizzati per avviare un percorso del cliente devono prima essere configurati in Journey Orchestration per ottenere un ID orchestrazione. Questo ID di orchestrazione viene quindi fornito allo sviluppatore che potrà utilizzarlo con l’acquisizione.
1. Configurare le origini dati esterne.
1. Configurare le azioni personalizzate.

### Adobe Campaign Standard

1. Configurare i modelli di messaggistica con le impostazioni di personalizzazione appropriate.
1. Configurare i flussi di lavoro di esportazione per esportare i registri dei messaggi transazionali. Si consiglia di eseguire al massimo ogni quattro ore.


## Documentazione correlata

* [Documentazione di Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [Documentazione di Journey Orchestration](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=it)
* [Documentazione di Adobe Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=it)
* [Documentazione di Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=it)
* [Documentazione di Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=it)
* [Documentazione di Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
