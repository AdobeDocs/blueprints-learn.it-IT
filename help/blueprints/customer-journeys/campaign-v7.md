---
title: Blueprint per Campaign v7
description: Adobe Campaign v7 è lo strumento per la gestione delle campagne, creato per i canali di marketing tradizionali come e-mail e direct mail. Fornisce solide funzionalità di ETL e gestione dei dati per agevolare la creazione e cura di una campagna perfetta. Il suo motore di orchestrazione consente programmi di marketing multi-touch avanzati, con attenzione particolare ai percorsi basati su batch. Inoltre, viene fornito con un server di messaggistica in tempo reale che consente ai team di marketing di inviare messaggi predefiniti basati su un payload completo da qualsiasi sistema IT per situazioni quali reimpostazione delle password, conferme degli ordini, ricevute elettroniche e altre ancora.
solution: Campaign,Campaign Classic v7
exl-id: 71c808f5-59e6-4f49-a6ba-581ed508bc04
source-git-commit: 37fa3bc00175a4636766564f0b8fb847fa8a951e
workflow-type: ht
source-wordcount: '1193'
ht-degree: 100%

---

# Blueprint per Campaign v7

Adobe Campaign v7 è lo strumento per la gestione delle campagne, creato per i canali di marketing tradizionali come e-mail e direct mail. Fornisce solide funzionalità di ETL e gestione dei dati per agevolare la creazione e cura di una campagna perfetta. Il suo motore di orchestrazione consente programmi di marketing multi-touch avanzati, con attenzione particolare ai percorsi basati su batch. Inoltre, viene fornito con un server di messaggistica in tempo reale che consente ai team di marketing di inviare messaggi predefiniti basati su un payload completo da qualsiasi sistema IT per situazioni quali reimpostazione delle password, conferme degli ordini, ricevute elettroniche e altre ancora.

<br>

## Casi di utilizzo

* Programmi di messaggistica basati su batch
* Campagne di onboarding e di re-marketing
* Pubblicità direct mail, brochure e campagne pubblicitarie su riviste
* Volumi bassi di messaggistica transazionale semplice (ad esempio per reimpostare la password, inviare ricevute per e-mail, confermare gli ordini, ecc.)

<br>

## Architettura

<img src="assets/campaign-v7-architecture.svg" alt="Architettura di riferimento per il blueprint per Campaign v7" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Pattern di integrazione

| Scenario | Descrizione | Funzionalità |
| :-- | :--- | :--- |
| [Journey Optimizer con Adobe Campaign](ajo-and-campaign.md) | Mostra come utilizzare Adobe Journey Optimizer per orchestrare esperienze 1:1 utilizzando il profilo del cliente in tempo reale, e come sfruttare il sistema di messaggistica transazionale nativo di Adobe Campaign per inviare il messaggio. | Sfrutta il profilo cliente in tempo reale e la potenza di Journey Optimizer per orchestrare le esperienze attuali, e utilizza le funzionalità di messaggistica nativa in tempo reale di Adobe Campaign per le comunicazioni della fase finale.<br><br>Considerazioni:<br><ul><li>È possibile inviare fino a 50.000 messaggi all’ora tramite il server di messaggi in tempo reale.<li>Journey Optimizer non applica alcuna limitazione; assicurati che gli aspetti tecnici siano approvati da un Pre-Sales Enterprise Architect.</li><li>La funzionalità Gestione delle decisioni non è supportata nei payload verso il server di messaggistica in tempo reale di Campaign v7.</li></ul> |
| [Real-Time CDP con Adobe Campaign](rtcdp-and-campaign.md) | Mostra come utilizzare Real-Time CDP di Adobe Experience Platform e il suo strumento di segmentazione centralizzata con Adobe Campaign, per fornire conversazioni personalizzate. | <ul><li>Condivisione di tipi di pubblico da Real-Time CDP ad Adobe Campaign tramite flussi di lavoro per lo scambio di file di archiviazione cloud e acquisizione Adobe Campaign. </li><li>Condividi facilmente i dati di consegna e interazione dalle conversazioni dei clienti in Real-time CDP da Adobe Campaign, per migliorare sia il profilo cliente in tempo reale che il reporting cross-channel sulle campagne di messaggistica.</li></ul> |

<br>

## Prerequisiti

### Server applicazioni e server per messaggistica in tempo reale

* Adobe Campaign Client Console, per interagire con e utilizzare il software Campaign v8. Si tratta di un client basato su Windows che utilizza protocolli Internet standard (SOAP, HTTP, ecc.). Assicurati che nella tua organizzazione siano state abilitate le autorizzazioni necessarie per distribuire, installare ed eseguire software.

* Elenco di indirizzi IP consentiti
   * Individua gli intervalli IP che tutti gli utenti utilizzeranno durante l’accesso alla console client.
   * Individua i sistemi aziendali che dovranno poter dialogare con il server di messaggistica in tempo reale, e assicurati che vi sia stato assegnato un indirizzo o intervallo di indirizzi IP statico che possa essere incluso nell’elenco degli indirizzi consentiti.
   * Può essere configurato e controllato tramite il Pannello di controllo Campaign.
* Gestione delle chiavi sFTP
   * Assicurati di avere le chiavi pubbliche SSH da utilizzare con l’sFTP per Campaign. Può essere configurato e controllato tramite il Pannello di controllo Campaign.

### E-mail

* Tieni pronto un sottodominio da utilizzare per l’invio dei messaggi.
* Il sottodominio può essere completamente delegato ad Adobe (consigliato) oppure è possibile utilizzare CNAME verso server DNS specifici per Adobe (personalizzati).
* Per garantire il corretto recapito dei messaggi, è necessario un record Google TXT per ciascun sottodominio.

### Push per dispositivi mobili

* Uno sviluppatore per dispositivi mobili dovrà implementare, configurare e generare l’app mobile.
* Adobe fornisce solo un SDK per la raccolta delle informazioni necessarie da FCM (Android) e APNS (iOS) per inviare i payload dei messaggi ai propri server. È invece responsabilità del cliente decidere come programmare, implementare e gestire l’app mobile, e come eseguirne il debug.

### Web app (facoltativo)

* È possibile delegare un sottodominio aggiuntivo per le pagine di destinazione e di annullamento dell’abbonamento ospitate da Campaign.
* Si consiglia vivamente di usare un certificato SSL.

<br>

## Guardrail

### Determinare la dimensione del server delle applicazioni

* L’archiviazione può essere aumentata per supportare fino a 100 milioni di profili.
* Configura e controlla l’accesso degli utenti tramite Adobe Admin Console (consigliato) o localmente nell’applicazione stessa.
* Il caricamento dei dati in Campaign deve essere eseguito tramite file di batch.
   * Il supporto per il caricamento dei dati API è principalmente per la gestione di profili o oggetti semplici nel database (creazione e aggiornamento). Non è pensato per essere utilizzato per l’upload di grandi volumi di dati né operazioni in batch.
   * Non è supportato l’utilizzo delle API per leggere i dati ai fini di un’applicazione personalizzata.
* Le chiamate API sono limitate a 15 al secondo o 150.000 al giorno su scala.

### Determinare la dimensione del server per messaggistica in batch

* È possibile gestire fino a 2,5 milioni di messaggi all’ora.

### Determinare la dimensione del server di messaggistica in tempo reale

* È possibile inviare fino a 50.000 messaggi all’ora.
* Per impostazione predefinita, sono previsti due server per la messaggistica in tempo reale. È possibile aumentarli fino a otto server per la messaggistica in tempo reale.

### Configurazione SMS

* Campaign offre la possibilità di integrazione con un provider SMS. Il provider viene acquisito dal cliente e integrato con Campaign per l’invio di messaggi basati su SMS.
* Il supporto avviene tramite protocollo SMPP.
* Ci sono tre (3) diversi tipi di SMS, tutti supportati da Adobe:
   * SMS MT (Mobile Terminated): SMS inviato da Adobe Campaign ai telefoni cellulari tramite il provider SMPP.
   * SMS MO (Mobile Originated): SMS inviato da un dispositivo mobile ad Adobe Campaign tramite il provider SMPP.
   * SMS SR (Status Report), DR o DLR (Delivery Receipt): ricevuta di ritorno inviata dal dispositivo mobile ad Adobe Campaign tramite il provider SMPP, per segnalare che l’SMS è stato ricevuto correttamente. Adobe Campaign può anche ricevere un SMS SR che segnala la mancata consegna di un messaggio, spesso con una descrizione dell’errore.

### Configurazione push per dispositivi mobili

* Due approcci supportati per l’integrazione con dispositivi mobili per le notifiche push:
   * Experience Platform Mobile SDK (consigliato)
   * Campaign Mobile SDK
* Approccio con Experience Platform Mobile SDK:
   * Sfrutta i tag di Adobe e l’estensione Campaign Classic per configurare l’integrazione con Experience Platform Mobile SDK.
   * È richiesta la conoscenza delle funzioni Tag e Raccolta dati di Adobe.
   * È richiesta esperienza di sviluppo mobile con notifiche push per Android e iOS per: implementazione dell’SDK; integrazione con FCM (Android) e APNS (iOS) per recuperare il token push token; configurazione dell’app per la ricezione delle notifiche push; e gestione delle interazioni push.
* Campaign Mobile SDK
   * Per accedervi, contatta l’Assistenza clienti di Adobe.
   * Per informazioni su come installare e configurare l’SDK, consulta la [documentazione di Campaign SDK](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/integrating-campaign-sdk-into-the-mobile-application.html?lang=it).

   >[!IMPORTANT]
   >Se implementi Campaign SDK e utilizzi altre applicazioni Experience Cloud, per la raccolta dati dovrai utilizzare Experience Platform Mobile SDK. Si tratta di un SDK diverso da installare insieme a Campaign SDK.

<br>

## Fasi di implementazione

Consulta la [Guida introduttiva](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/starting-with-adobe-campaign/about-adobe-campaign-classic.html?lang=it) per l’implementazione di Adobe Campaign v7.


## Documentazione correlata

* [Documentazione di Campaign v7](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=it)
* [Descrizione del prodotto Campaign v7](https://helpx.adobe.com/it/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/launch.html?lang=it)
* [Documentazione di Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
