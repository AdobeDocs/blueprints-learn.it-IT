---
title: Blueprint per Journey Optimizer con Adobe Campaign
description: Mostra come Adobe Journey Optimizer può essere utilizzato con Adobe Campaign per inviare messaggi in modo nativo utilizzando il server di messaggistica in tempo reale in Campaign.
solution: Journey Optimizer, Campaign, Campaign v8, Campaign Classic v7, Campaign Standard
exl-id: 076446a9-dfb9-464c-a04f-6864b8cb7b48
source-git-commit: 37fa3bc00175a4636766564f0b8fb847fa8a951e
workflow-type: ht
source-wordcount: '1150'
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

### Campaign (v7/v8)

* L’istanza di esecuzione del Centro messaggi deve essere ospitata da Adobe Managed Cloud Services.
* La versione deve essere v7 build >21.1 oppure v8
* Velocità della messaggistica
   * AC (v7) 50.000 all’ora
   * AC (v8) fino a 1 milione all’ora in base al pacchetto
* AC (v7) supporta solo i percorsi avviati da eventi.
   * I percorsi non possono essere avviati da segmenti o appartenenza a segmenti.
   * Non sono supportati i percorsi basati su eventi di tipo Leggi pubblico e Business, a causa del volume che può essere inviato alle istanze di esecuzione.
* AC (v7) e AC (v8) non supportano la funzionalità Gestione delle decisioni nei messaggi.
* Non viene applicata alcuna limitazione delle chiamate API in uscita verso Campaign.
* I registri di messaggistica transazionale non vengono sincronizzati nativamente in AEP. È necessario un intervento di consulenza. Si consiglia di esportare i registri al massimo ogni 4 ore.

<br>

### Campaign Standard

* Supporta una velocità di 14 tps (50.000 all’ora).
* Supporta solo i percorsi avviati da eventi.
   * I percorsi non possono essere avviati da segmenti o appartenenza a segmenti.
   * Non sono supportati i percorsi basati su eventi di tipo Leggi pubblico e Business, a causa del volume che può essere inviato alle istanze di esecuzione.
* Le attività di apertura e clic da messaggi transazionali inviate a Campaign Standard sono esposte nativamente come “eventi di reazione” nell’area di lavoro del percorso Journey Optimizer.
* I registri di messaggistica transazionale non vengono sincronizzati nativamente in Experience Platform. È necessario un intervento di consulenza. Si consiglia di esportare i registri al massimo ogni 4 ore.

<br>

## Fasi di implementazione

### Adobe Experience Platform

#### Schema/set di dati

1. [Configurare singoli schemi di profilo, di esperienza e di entità multiple](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, in base ai dati forniti dal cliente
1. Creare schemi basati su classi di eventi Experience per broadLog, trackingLog e le tabelle di Adobe Campaign degli indirizzi a cui non possono essere consegnati i messaggi (facoltativo).
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) in Experience Platform per i dati da acquisire.
1. [Aggiungere etichette di utilizzo dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=it) ai set di dati in Experience Platform a scopo di governance.
1. [Creare i criteri](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=it) necessari per applicare la governance alle destinazioni

#### Profilo/Identità

1. [Creare namespace specifici per il cliente](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it)
1. [Aggiungere le identità agli schemi](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it)
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=it)
1. [Impostare i criteri di unione](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=it) per le diverse viste di [!UICONTROL Real-time Customer Profile] (opzionale)
1. Creare segmenti da utilizzare in Journey

#### Origini/Destinazioni

1. [Inserire i dati in Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=it) utilizzando API di streaming e connettori di origini.

### Journey Optimizer

1. Configurare l’origine dati di Experience Platform e determinare quali campi devono essere memorizzati nella cache come parte dei dati del profilo. I dati in streaming utilizzati per avviare un percorso cliente devono prima essere configurati in Journey Optimizer, per ottenere un ID di orchestrazione. Questo ID di orchestrazione viene quindi fornito allo sviluppatore che potrà utilizzarlo con l’acquisizione.
1. Configurare le origini dati esterne.
1. Configurare le azioni personalizzate per l’istanza di Campaign.

### Campaign v7/v8 o Campaign Standard

* I modelli di messaggistica devono essere configurati con un contesto di personalizzazione appropriato.
* I flussi di lavoro di esportazione devono essere configurati per esportare i registri di messaggistica transazionali da restituire a Experience Platform. Si consiglia di eseguirli al massimo ogni 4 ore.

### Configurazione push mobile (opzionale)

1. Implementare Experience Platform Mobile SDK per raccogliere i token push e le informazioni di accesso da associare ai profili cliente noti.
1. Utilizzare i tag di Adobe e creare una proprietà mobile con la seguente estensione:
   * Adobe Journey Optimizer | Adobe Campaign Classic | Adobe Campaign Standard
   * Rete Edge di Adobe Experience Platform
   * Identità  per rete Edge
   * Mobile Core
1. Assicurati di disporre di un flusso di dati dedicato per le implementazioni di app mobili rispetto alle implementazioni web.
1. Per ulteriori informazioni, consulta la [guida di Adobe Journey Optimizer Mobile](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer).

   >[!IMPORTANT]
   >Per poter inviare comunicazioni in tempo reale tramite Journey Optimizer e notifiche push in batch tramite Campaign, potrebbe essere necessario raccogliere token mobili sia in Journey Optimizer che in Campaign. Per l’acquisizione dei token push, Campaign v8 richiede l’utilizzo esclusivo di Campaign SDK.

<br>

## Documentazione correlata

* [Documentazione di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it)
* [Documentazione di Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
* [Documentazione di Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=it)
* [Descrizione del prodotto Journey Optimizer](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer.html)
* [Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=it)
* [Documentazione di Campaign v7](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=it)
* [Documentazione di Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=it)
