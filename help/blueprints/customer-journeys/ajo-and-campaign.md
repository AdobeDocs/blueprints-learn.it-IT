---
title: Blueprint per Journey Optimizer con Adobe Campaign
description: Mostra come Adobe Journey Optimizer può essere utilizzato con Adobe Campaign per inviare messaggi in modo nativo utilizzando il server di messaggistica in tempo reale in Campaign.
solution: Journey Optimizer, Campaign, Campaign v8, Campaign Classic v7, Campaign Standard
exl-id: 076446a9-dfb9-464c-a04f-6864b8cb7b48
source-git-commit: 6901596cbb661ffa8cf57c6ae958db1978bf1520
workflow-type: ht
source-wordcount: '504'
ht-degree: 100%

---

# Journey Optimizer con Adobe Campaign

Mostra come Adobe Journey Optimizer può essere utilizzato con Adobe Campaign per inviare messaggi in modo nativo utilizzando il server di messaggistica in tempo reale in Campaign.

<br>

## Architettura

<img src="assets/ajo-campaign-architecture.svg" alt="Architettura di riferimento per il blueprint Journey Optimizer" style="width:100%; border:1px solid #4a4a4a" />

>[!IMPORTANT]
>È possibile utilizzare sia Journey Optimizer che Campaign per inviare messaggi in modo indipendente l’uno dall’altro, ma occorre tenere conto di alcuni aspetti tecnici. Se desideri seguire questo percorso, collabora con il tuo Pre-Sales Enterprise Architect per essere certo di comprendere tutti i requisiti necessari per l’implementazione.

<br>

## Prerequisiti

### Adobe Experience Platform

* Gli schemi e i set di dati devono essere configurati nel sistema prima di poter configurare le origini dati di Journey Optimizer.
* Per poter attivare un evento non basato su regole, aggiungi il gruppo di campi Orchestration eventID agli schemi di eventi Experience basati su classi.
* Per poter caricare profili di test da utilizzare con Journey Optimizer, aggiungi il gruppo di campi “Profile test details” agli schemi per singoli profili basati su classi.
* Journey Optimizer e Campaign devono entrambi essere presenti nella stessa organizzazione IMS.

### Campaign v7/v8 o Campaign Standard

* L’istanza di esecuzione del servizio di messaggistica in tempo reale (ad es. Message Center) deve essere ospitata da Adobe Managed Cloud Services.
* L’authoring dei messaggi viene eseguito direttamente nell’istanza di Campaign.

<br>

## Guardrail

[Link al prodotto per i guardrail Journey Optimizer](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=it)

### Ulteriori guardrail per Journey Optimizer

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
* Gli eventi di business non sono supportati.
* Integrazioni in uscita verso sistemi di terze parti
   * Singoli indirizzi IP statici non sono supportati, in quanto la nostra infrastruttura è multi-tenant (inserire tutti gli indirizzi IP dei datacenter nell’elenco degli IP consentiti).
   * Per le azioni personalizzate sono supportati solo i metodi POST e PUT.
   * Autenticazioni supportate: token | password | OAuth2
* Non è possibile creare pacchetti e spostare singoli componenti di Adobe Experience Platform o Journey Optimizer tra diverse sandbox. È necessario reimplementarli nei nuovi ambienti.

<br>

### Integrazioni di Campaign

Per informazioni sull’integrazione con la tua versione specifica di Adobe Campaign e Adobe Journey Optimizer, consulta la guida corrispondente per ogni versione di Adobe Campaign.

* [Adobe Journey Optimizer e Campaign v7](ajo-and-campaign-v7.md)
* [Adobe Journey Optimizer e Campaign v8](ajo-and-campaign-v8.md)