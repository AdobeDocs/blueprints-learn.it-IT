---
title: Journey Optimizer con blueprint Adobe Campaign
description: Mostra come Adobe Journey Optimizer può essere utilizzato con Adobe Campaign per inviare messaggi in modo nativo utilizzando il server di messaggistica in tempo reale in Campaign
solution: Experience Platform, Journey Optimizer, Campaign v8, Campaign Classic v7, Campaign Standard
source-git-commit: 1c46cbdfc395de4fc9139966cf869ba1feeceaaa
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 26%

---

# Journey Optimizer con Adobe Campaign

Mostra come Adobe Journey Optimizer può essere utilizzato con Adobe Campaign per inviare messaggi in modo nativo utilizzando il server di messaggistica in tempo reale in Campaign.

<br>

## Architettura

<img src="assets/ajo-campaign-architecture.svg" alt="Architettura di riferimento blueprint Journey Optimizer" style="width:100%; border:1px solid #4a4a4a" />

>[!IMPORTANT]
>È possibile utilizzare sia Journey Optimizer che Campaign per inviare messaggi in modo indipendente l’uno dall’altro, ma occorre considerare alcune considerazioni tecniche. Se desideri seguire questo percorso, collabora con il tuo architetto prevendita Enterprise per essere certo di comprendere ciò che sarà necessario per supportare l&#39;implementazione.

<br>

## Prerequisiti

### Adobe Experience Platform

* Gli schemi e i set di dati devono essere configurati nel sistema prima di poter configurare le origini dati Journey Optimizer
* Per gli schemi basati su classi Experience Event, aggiungi il gruppo di campi &#39;Orchestration eventID quando vuoi che venga attivato un evento che non è un evento basato su regole
* Per gli schemi basati su singole classi di profilo aggiungi il gruppo di campi &quot;Dettagli test profilo&quot; per poter caricare i profili di test da utilizzare con Journey Optimizer
* Il provisioning di Journey Optimizer e Campaign avviene nella stessa organizzazione IMS

### Campaign v7/v8 o Campaign Standard

* L&#39;istanza di esecuzione del servizio di messaggistica in tempo reale (ad es. Message Center) deve essere ospitata da Adobe Managed Cloud Services
* L’authoring dei messaggi viene eseguito all’interno dell’istanza Campaign stessa

<br>

## Guardrail

[Journey Optimizer Guardrail Prodotto Link](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=it)

### Guardrail Journey Optimizer aggiuntivi

* L’utilizzo dell’app tramite l’API è ora disponibile per garantire che il sistema di destinazione non sia saturato fino al punto dell’errore. Ciò significa che i messaggi che superano il limite verranno eliminati completamente e non inviati. La limitazione non è supportata.
   * Numero massimo di connessioni - numero massimo di connessioni http/s gestite da una destinazione
   * Numero massimo di chiamate - numero massimo di chiamate da effettuare nel parametro periodInMs
   * periodInMs - tempo in millisecondi
* I percorsi avviati dall’iscrizione a un segmento possono funzionare in due modalità:
   * Segmenti in batch (aggiornati ogni 24 ore)
   * Segmenti in streaming (&lt;5min qualifica)
* Segmenti batch: necessario comprendere il volume giornaliero di utenti qualificati e accertarsi che il sistema di destinazione sia in grado di gestire il throughput burst per percorso e per tutti i percorsi.
* Segmenti in streaming: il burst iniziale delle qualifiche dei profili deve poter essere gestito insieme al volume giornaliero di qualificazione dello streaming, per ogni percorso e per tutti i percorsi.
* offer decisioning in non supportato
* Eventi aziendali non supportati
* Integrazioni in uscita con sistemi di terze parti
   * Nessun supporto per un singolo IP statico in quanto l’infrastruttura è multi-tenant (deve elenco consentiti tutti gli IP del centro dati)
   * Sono supportati solo i metodi POST e PUT per le azioni personalizzate
   * Supporto dell&#39;autenticazione: token | password | OAuth2
* Non è possibile creare pacchetti e spostare singoli componenti di Adobe Experience Platform o Journey Optimizer tra diverse sandbox. Deve essere reimplementato nei nuovi ambienti

<br>

### Campagna (v7/v8)

* L&#39;istanza di esecuzione del Centro messaggi deve essere ospitata da Cloud Services gestiti di Adobe
* Deve essere su v7 build >21.1 o v8
* Velocità effettiva messaggistica
   * AC (v7) 50 k all&#39;ora
   * AC (v8) fino a 1M all&#39;ora in base al pacchetto
* AC (v7) supporta solo il percorso avviato dall&#39;evento
   * Nessun membro del segmento o del segmento avviato dal Percorso
   * Il percorso basato su eventi di tipo Read Audience e Business non è supportato a causa del volume che può inviare alle istanze di esecuzione
* AC (v7) o AC (v8) non supporta l’Offer decisioning nei messaggi
* Nessuna limitazione delle chiamate API in uscita effettuate a Campaign
* I registri di messaggistica transazionali non vengono sincronizzati in modo nativo in AEP. Richiede consulenza. Raccomandazione di esportare i registri al massimo ogni 4 ore

<br>

### Campaign Standard

* Supporta 14 tps (50 k all&#39;ora) in throughput
* Supporta solo i percorsi generati dagli eventi
   * Nessun membro del segmento o del segmento avviato dal Percorso
   * Il percorso basato su eventi di tipo Read Audience e Business non è supportato a causa del volume che può inviare alle istanze di esecuzione
* Le attività di apertura e clic dai messaggi transazionali inviati ad Campaign Standard sono esposte in modo nativo come &quot;eventi di reazione&quot; all’interno dell’area di lavoro del percorso Journey Optimizer
* I registri di messaggistica transazionali non vengono sincronizzati in modo nativo nell’Experience Platform. Richiede consulenza. Raccomandazione di esportare i registri al massimo ogni 4 ore

<br>

## Fasi di implementazione

### Adobe Experience Platform

#### Schema/set di dati

1. [Configurare singoli schemi di profilo, di esperienza e di entità multiple](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, in base ai dati forniti dal cliente
1. Crea schemi basati su classi Experience Event per le tabelle di indirizzi wideLog, trackingLog e non-deliverable di Adobe Campaign (facoltativo).
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) in Experience Platform per i dati da acquisire.
1. [Aggiungere etichette di utilizzo dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=it) ai set di dati in Experience Platform a scopo di governance.
1. [Creare i criteri](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=it) necessari per applicare la governance alle destinazioni

#### Profilo/Identità

1. [Creare namespace specifici per il cliente](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it)
1. [Aggiungere le identità agli schemi](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=it)
1. [Impostare i criteri di unione](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=it) per le diverse viste di [!UICONTROL Real-time Customer Profile] (opzionale)
1. Crea segmenti per l’utilizzo del Percorso.

#### Origini/Destinazioni

1. [Inserire i dati in Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=it) utilizzando API di streaming e connettori di origini

### Journey Optimizer

1. Configura l’origine dati di Experience Platform e determina quali campi devono essere memorizzati nella cache come parte dei dati profileStreaming utilizzati per avviare un percorso cliente deve prima essere configurato in Journey Optimizer per ottenere un ID orchestrazione. Questo ID di orchestrazione viene quindi fornito allo sviluppatore che potrà utilizzarlo con l’acquisizione
1. Configurare le origini dati esterne
1. Configurare azioni personalizzate per l’istanza Campaign

### Campaign v7/v8 o Campaign Standard

* I modelli di messaggistica devono essere configurati con un contesto di personalizzazione appropriato
* I flussi di lavoro di esportazione devono essere configurati per esportare nuovamente i registri di messaggistica transazionali nell’Experience Platform . Si consiglia di eseguire al massimo ogni 4 ore

### Configurazione push mobile (opzionale)

1. Implementa Experience Platform Mobile SDK per raccogliere token push e informazioni di accesso per eseguire il collegamento ai profili cliente noti
1. Utilizza i tag di Adobe e crea una proprietà mobile con la seguente estensione:
   * Adobe Journey Optimizer | Adobe Campaign Classic | Adobe Campaign Standard
   * Rete Edge di Adobe Experience Platform
   * Identità per Edge Network
   * Mobile Core
1. Assicurati di disporre di un datastream dedicato per le distribuzioni di app mobili rispetto alle distribuzioni web
1. Per ulteriori informazioni, consulta [Guida a Adobe Journey Optimizer Mobile](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)

   >[!IMPORTANT]
   >Se desideri inviare comunicazioni in tempo reale tramite Journey Optimizer e notifiche push in batch tramite Campaign, potrebbe essere necessario raccogliere token mobili sia in Journey Optimizer che in Campaign. Campaign v8 richiede l’utilizzo esclusivo dell’SDK Campaign per l’acquisizione dei token push.

<br>

## Documentazione correlata

* [Documentazione di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [Documentazione di Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
* [Documentazione di Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=it)
* [Descrizione del prodotto Journey Optimizer](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=en)
* [Documentazione di Campaign v7](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=it)
* [Documentazione di Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=it)