---
title: Messaggi attivati e blueprint Adobe Experience Platform
description: Esegui messaggi ed esperienze attivate utilizzando Adobe Experience Platform come hub centrale streaming dati, profili cliente e segmentazione.
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
translation-type: tm+mt
source-git-commit: 844fff1cefe367575beb5c03aa0f0d026eb9f39b
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 1%

---

# Messaggi attivati e blueprint Adobe Experience Platform

Esegui messaggi ed esperienze attivate utilizzando Adobe Experience Platform come hub centrale streaming dati, profili cliente e segmentazione.

## Casi d&#39;uso

* Messaggi attivati
* Conferme di registrazione
* Carrello acquisti e moduli di richiesta abbandonati
* Messaggi attivati dalla posizione

## Architettura

<img src="assets/triggered.svg" alt="Architettura di riferimento per lo scenario di messaggistica attivata e Adobe Experience Platform" style="border:1px solid #4a4a4a" />

## Modelli di integrazione

* Adobe Experience Platform -> Journey Orchestration

## Prerequisiti

* Adobe Experience Platform
* Journey Orchestration

## Guardrail

### Journey Orchestration

* Vedi il link per [maggiori dettagli sulle limitazioni](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=en#starting-with-journeys)
* La funzione di limitazione è disponibile tramite l’impostazione API per garantire che il sistema di destinazione non sia saturato fino al punto di errore. I messaggi che superano il limite vengono eliminati completamente e non vengono mai inviati. La limitazione non è ancora supportata.
   * connessioni massime: Numero massimo di connessioni http/s che una destinazione può gestire
   * conteggio massimo chiamate: Numero massimo di chiamate da effettuare nel parametro periodInMs
   * periodInMs: Tempo in millisecondi
* I percorsi avviati per l’appartenenza al segmento possono funzionare in due modalità:
   * segmenti batch (aggiornato ogni 24 ore)
   * Segmenti in streaming (&lt;qualificazione di 5 minuti)
* Segmenti in batch: Assicurati di comprendere il volume giornaliero di utenti qualificati e di garantire che il sistema di destinazione sia in grado di gestire il throughput burst per percorso e in tutti i percorsi
* Segmenti in streaming: Assicurati che la frammentazione iniziale delle qualifiche di profilo possa essere gestita insieme al volume giornaliero di qualificazione in streaming per percorso e per tutti i percorsi
* La destinazione finale deve supportare il payload REST API e JSON
* Non supporta attualmente Offer Decisioning
* Consulta le protezioni per l’inserimento di profili e dati [per Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

### Campaign Standard

* Può supportare solo 14 tps (50 k all&#39;ora) in throughput
* I percorsi avviati per l’appartenenza ai segmenti non sono supportati
* Gli eventi di reazione all’apertura o ai clic dei messaggi transazionali sono supportati all’interno del Journey Orchestration.
* I registri di messaggistica transazionale non sono attualmente sincronizzati in modo nativo in Experience Platform, richiedendo una configurazione manuale. Si consiglia di esportare i registri al massimo ogni quattro ore.


## Passaggi di implementazione

### Adobe Experience Platform

#### Schema/Set di dati

1. Configura ad Experience Platform schemi di profilo individuale, evento esperienza e più entità in base ai dati forniti dal cliente.
1. Crea schemi di Campaign per i seguenti elementi: wideLog, trackingLog, indirizzi non recapitati e preferenze di profilo (facoltativo).
1. Aggiungi le etichette di utilizzo dei dati al set di dati per la governance.
1. Creare criteri per applicare la governance sulle destinazioni.

#### Profilo/identità

1. Crea qualsiasi namespace specifico per il cliente.
1. Aggiungi identità agli schemi.
1. Abilita schemi e set di dati per il profilo.
1. Imposta le regole di unione per le diverse visualizzazioni di Profilo cliente in tempo reale (facoltativo).
1. Crea segmenti per l’utilizzo della campagna.

#### Origini/Destinazioni

1. Acquisisci dati in Experience Platform utilizzando API di streaming e connettori sorgente.
1. Configura la destinazione di archiviazione BLOB [!DNL Azure] da utilizzare con Campaign.

#### Implementazione di app mobili

1. Implementa Campaign SDK per Campaign Classic o Experience Platform SDK per Campaign Standard. Se è presente Experience Platform Launch, si consiglia di utilizzare l&#39;estensione Campaign Classic/Standard con Experience Platform SDK.


### Journey Orchestration

1. I dati di streaming utilizzati per avviare un percorso cliente devono essere configurati prima all&#39;interno del Journey Orchestration per ottenere un ID orchestrazione. Questo ID di orchestrazione viene quindi fornito allo sviluppatore da utilizzare con l’acquisizione.
1. Configura origini dati esterne.
1. Configura azioni personalizzate.

### Campaign Standard

1. Configura i modelli di messaggistica con le impostazioni di personalizzazione appropriate.
1. Configura l’esportazione dei flussi di lavoro per esportare i registri di messaggistica transazionali. Si consiglia di eseguire al massimo ogni quattro ore.


## Documentazione correlata

* [Documentazione di Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Documentazione del Journey Orchestration](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=en)
* [Documentazione di Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [Documentazione di Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [Documentazione del Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [Documentazione Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
