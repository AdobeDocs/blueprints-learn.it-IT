---
title: Journey Optimizer - Blueprint per messaggistica attivata e Adobe Experience Platform
description: Esegui messaggi ed esperienze attivate utilizzando Adobe Experience Platform come hub centrale per lo streaming di dati, profili dei clienti e segmentazione.
solution: Experience Platform, Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 2ead62f94e761cd9453be284a9fde3c5803879eb
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 42%

---

# Journey Optimizer

Adobe Journey Optimizer è un sistema appositamente progettato che consente ai team di marketing di reagire in tempo reale ai comportamenti dei clienti e di incontrarli là dove si trovano. Le funzionalità di gestione dei dati sono state trasferite in Adobe Experience Platform, consentendo ai team di marketing di concentrarsi sul loro punto di forza: la creazione di percorsi cliente d’eccellenza e conversazioni personalizzate.  Questo blueprint delinea le funzionalità tecniche dell’applicazione e descrive i vari componenti dell’architettura di Adobe Journey Optimizer.

<br>

## Casi di utilizzo

* Messaggi attivati
* Conferma di benvenuto e registrazione
* Abbandoni del carrello e del modulo di richiesta
* Messaggi attivati dalla posizione
* Esperienze all&#39;interno dello stadio
* Esperienze di viaggio e ospitalità pre-arrivo e soggiorno

<br>

## Architettura

<img src="assets/ajo-architecture.svg" alt="Architettura di riferimento blueprint Journey Optimizer" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Scenari di blueprint

| Scenario | Descrizione | Funzionalità |
| :-- | :--- | :--- |
| [Messaggistica di terze parti](3rd-party-messaging.md) | Mostra come Adobe Journey Optimizer può essere utilizzato con sistemi di messaggistica di terze parti per orchestrare e inviare comunicazioni personalizzate | Distribuisci comunicazioni personalizzate 1:1 al momento ai clienti mentre interagiscono con il tuo marchio o azienda<br><br>Considerazioni:<br><ul><li>Il sistema di terze parti deve supportare token portatori per l&#39;autenticazione</li><li>Nessun supporto per gli IP statici a causa dell’architettura multi-tenant</li><li>Presta attenzione ai vincoli architettonici del sistema di terze parti quando si tratta di chiamate API al secondo.  Potrebbe essere necessario che il cliente acquisti un volume aggiuntivo dal fornitore di terze parti per supportare il volume proveniente da Journey Optimizer</li><li>Non supporta l’Offer decisioning nei messaggi o nei payload</li></ul> |

<br>

## Pattern di integrazione

| Integrazione | Descrizione | Funzionalità |
| :-- | :--- | :--- |
| [Journey Optimizer con Adobe Campaign](ajo-and-campaign.md) | Mostra come utilizzare Adobe Journey Optimizer per orchestrare esperienze 1:1 utilizzando il Profilo del cliente in tempo reale e come sfruttare il sistema di messaggistica transazionale nativo di Adobe Campaign per inviare il messaggio | Sfruttare il Profilo cliente in tempo reale e la potenza di Journey Optimizer per orchestrare le esperienze attuali e allo stesso tempo utilizzare le funzionalità di messaggistica nativa in tempo reale di Adobe Campaign per la comunicazione dell’ultimo miglio<br><br>Considerazioni:<br><ul><li>L’applicazione Campaign deve essere nella build v7 >21.1 o v8</li><li>Velocità effettiva messaggistica</li><ul><li>Campaign v7 - fino a 50.000 all’ora</li><li>Campaign v8 - fino a 1 milione all’ora</li><li>Campaign Standard - fino a 50 k all&#39;ora</li></ul><li>Non viene eseguita alcuna limitazione, pertanto i casi d’uso necessitano di un controllo tecnico da parte di un architetto Enterprise</li><li>Nessun supporto per l’utilizzo di Offer Decisioning nel messaggio inviato da Campaign</li></ul> |

<br>

## Prerequisiti

Adobe Experience Platform

* Gli schemi e i set di dati devono essere configurati nel sistema prima di poter configurare le origini dati Journey Optimizer
* Per gli schemi basati su classi Experience Event, aggiungi il gruppo di campi &#39;Orchestration eventID quando vuoi che venga attivato un evento che non è un evento basato su regole
* Per gli schemi basati su singole classi di profilo aggiungi il gruppo di campi &quot;Dettagli test profilo&quot; per poter caricare i profili di test da utilizzare con Journey Optimizer

E-mail

* Deve essere pronto un sottodominio per l’invio del messaggio
* Il sottodominio può essere delegato completamente all’Adobe (consigliato) oppure i CNAME possono essere utilizzati per puntare a server DNS specifici per Adobe (personalizzati)
* Per garantire il corretto recapito dei messaggi, è necessario un record TXT di Google per ciascun sottodominio

Push per dispositivi mobili

* Per creare l’app, il cliente deve disporre di uno sviluppatore di app mobili.
* SDK per dispositivi mobili di Adobe Experience Platform

<br>

## Guardrail

[Journey Optimizer Guardrail Prodotto Link](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=it)

Tieni presenti questi elementi non elencati nel link qui sopra:

* Segmenti batch: necessario comprendere il volume giornaliero di utenti qualificati e accertarsi che il sistema di destinazione sia in grado di gestire il throughput burst per percorso e per tutti i percorsi.
* Segmenti in streaming: il burst iniziale delle qualifiche dei profili deve poter essere gestito insieme al volume giornaliero di qualificazione dello streaming, per ogni percorso e per tutti i percorsi.
* Supporta in modo nativo solo l’Offer decisioning nei messaggi (nessuna azione personalizzata)
* Tipi di messaggi supportati:
   * E-mail
   * Push (FCM/APNS)
   * Azioni personalizzate (tramite API Rest)
* Integrazioni in uscita con sistemi di terze parti
   * Nessun supporto per un singolo IP statico in quanto l’infrastruttura è multi-tenant (deve elenco consentiti tutti gli IP del centro dati)
   * Sono supportati solo i metodi POST e PUT per le azioni personalizzate
   * Autenticazione tramite token di autorizzazione o utente
* Non è possibile creare pacchetti e spostare singoli componenti di Adobe Experience Platform o Journey Optimizer tra diverse sandbox. Deve essere reimplementato nei nuovi ambienti

### Guardrail per l’acquisizione dei dati

<img src="assets/aep-data-ingestion-details-latency.svg" alt="Architettura di riferimento blueprint Journey Optimizer" style="width:80%; border:1px solid #4a4a4a" />

<br>

### Guardrail di attivazione

<img src="assets/ajo-activation-details-latency.svg" alt="Architettura di riferimento blueprint Journey Optimizer" style="width:80%; border:1px solid #4a4a4a" />

<br>

## Fasi di implementazione

### Adobe Experience Platform

#### Schema/set di dati

1. [Configurare singoli schemi di profilo, di esperienza e di entità multiple](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, in base ai dati forniti dal cliente
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
1. Configurare le origini dati esterne.
1. Configurare le azioni personalizzate.

### Configurazione push mobile

1. Implementa Experience Platform Mobile SDK per raccogliere token push e informazioni di accesso per eseguire il collegamento ai profili cliente noti
1. Utilizza i tag di Adobe e crea una proprietà mobile con la seguente estensione:
1. Adobe Journey Optimizer
1. Rete Edge di Adobe Experience Platform
1. Identità per Edge Network
1. Mobile Core
1. Assicurati di disporre di un datastream dedicato per le distribuzioni di app mobili rispetto alle distribuzioni web
1. Per ulteriori informazioni, consulta [Guida a Adobe Journey Optimizer Mobile](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)


## Documentazione correlata

* [Documentazione di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [Documentazione di Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
* [Documentazione di Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=it)
* [Descrizione del prodotto Journey Optimizer](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
