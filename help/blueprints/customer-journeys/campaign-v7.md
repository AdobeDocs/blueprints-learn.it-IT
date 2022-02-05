---
title: Blueprint di Campaign v7
description: Adobe Campaign v7 è uno strumento di campagna generato per i canali di marketing tradizionali come e-mail e direct mail. Fornisce solide funzionalità di ETL e gestione dei dati per aiutare a creare e curare la campagna perfetta. Il motore di orchestrazione fornisce programmi di marketing multi-touch avanzati con un focus principale sui percorsi basati su batch.  Viene inoltre fornito con un server di messaggistica in tempo reale che consente ai team di marketing di inviare messaggi predefiniti basati su un payload completo da qualsiasi sistema IT per elementi quali reimpostazione della password, conferma dell’ordine, e-Receips (Ricezione elettronica) e molto altro ancora.
solution: Campaign Classic v7
exl-id: 71c808f5-59e6-4f49-a6ba-581ed508bc04
source-git-commit: 0c072465c2cac954631fe3a8dbdcef280ee397ab
workflow-type: tm+mt
source-wordcount: '1193'
ht-degree: 3%

---

# Blueprint di Campaign v7

Adobe Campaign v7 è uno strumento di campagna generato per i canali di marketing tradizionali come e-mail e direct mail. Fornisce solide funzionalità di ETL e gestione dei dati per aiutare a creare e curare la campagna perfetta. Il motore di orchestrazione fornisce programmi di marketing multi-touch avanzati con un focus principale sui percorsi basati su batch.  Viene inoltre fornito con un server di messaggistica in tempo reale che consente ai team di marketing di inviare messaggi predefiniti basati su un payload completo da qualsiasi sistema IT per elementi quali reimpostazione della password, conferma dell’ordine, e-Receips (Ricezione elettronica) e molto altro ancora.

<br>

## Casi di utilizzo

* Programmi di messaggistica basati su batch
* Campagne di onboarding e di re-marketing
* Pubblicità Direct Mail, opuscolo e campagne pubblicitarie
* Messaggi transazionali semplici a basso volume (ad esempio reimpostazione della password, ricezioni e-mail, conferme di ordine, ecc.)

<br>

## Architettura

<img src="assets/campaign-v7-architecture.svg" alt="Architettura di riferimento per la blueprint di Campaign v7" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Pattern di integrazione

| Scenario | Descrizione | Funzionalità |
| :-- | :--- | :--- |
| [Journey Optimizer con Adobe Campaign](ajo-and-campaign.md) | Mostra come utilizzare Adobe Journey Optimizer per orchestrare esperienze 1:1 utilizzando il Profilo del cliente in tempo reale e come sfruttare il sistema di messaggistica transazionale nativo di Adobe Campaign per inviare il messaggio | Sfruttare il Profilo cliente in tempo reale e la potenza di Journey Optimizer per orchestrare le esperienze attuali e allo stesso tempo utilizzare le funzionalità di messaggistica nativa in tempo reale di Adobe Campaign per la comunicazione dell’ultimo miglio<br><br>Considerazioni:<br><ul><li>Può inviare fino a 50.000 messaggi all&#39;ora tramite il server di messaggi in tempo reale<li>Journey Optimizer non esegue alcuna limitazione in modo da garantire il controllo tecnico da parte di un architetto aziendale pre-vendita</li><li>Offer Decisioning non è supportato nei payload del server di messaggistica in tempo reale Campaign v7</li></ul> |
| [Real-Time CDP con Adobe Campaign](rtcdp-and-campaign.md) | Mostra come Adobe Experience Platform Real-Time CDP e il suo strumento di segmentazione centralizzata possono essere utilizzati con Adobe Campaign per fornire conversazioni personalizzate | <ul><li>Condivisione di tipi di pubblico da Real-Time CDP ad Adobe Campaign tramite l’utilizzo di flussi di lavoro di scambio file di archiviazione cloud e di acquisizione Adobe Campaign </li><li>Condividi facilmente i dati di consegna e interazione dalle conversazioni dei clienti nella Real-time CDP di Adobe Campaign per migliorare sia il Profilo del cliente in tempo reale che il reporting cross-channel sulle campagne di messaggistica</li></ul> |

<br>

## Prerequisiti

### Server applicazioni e server di messaggistica in tempo reale

* La console client di Adobe Campaign è necessaria per interagire e utilizzare il software Campaign v8. È un client basato su Windows e utilizza protocolli Internet standard (SOAP, HTTP, ecc.). Assicurati di disporre delle autorizzazioni necessarie abilitate nella tua organizzazione per distribuire, installare ed eseguire il software

* Inserimento degli indirizzi IP nell’elenco Consentiti
   * Identificare gli intervalli IP che tutti gli utenti sfrutteranno durante l’accesso alla console client
   * Identifica i sistemi aziendali autorizzati a parlare con il server di messaggistica in tempo reale e assicurati che dispongano di un IP o di un intervallo assegnati statisticamente che è possibile elenco consentiti
   * Può essere configurato e controllato tramite il Pannello di controllo Campaign Campaign
* Gestione delle chiavi sFTP
   * Disponi di chiavi pubbliche SSH da utilizzare con l’sFTP fornito dalla campagna. Questo può essere configurato e controllato tramite il Pannello di controllo Campaign Campaign.

### E-mail

* Richiedere l’utilizzo di un sottodominio pronto per l’invio del messaggio
* Il sottodominio può essere delegato completamente all’Adobe (consigliato) oppure i CNAME possono essere utilizzati per puntare a server DNS specifici per Adobe (personalizzati)
* Per garantire il corretto recapito dei messaggi, è necessario un record TXT di Google per ciascun sottodominio

### Push per dispositivi mobili

* Disporre di uno sviluppatore mobile disponibile per distribuire, configurare e creare l’app mobile
* Adobe fornisce solo un SDK per raccogliere le informazioni necessarie da FCM (Android) e APNS (iOS) per inviare payload di messaggi ai propri server. La responsabilità del cliente è in quale modo l’app mobile deve essere codificata, implementata, gestita e sottoposta a debug

### Webapps (facoltativo)

* Può delegare un sottodominio aggiuntivo per le pagine di destinazione e di annullamento dell’abbonamento ospitate da Campaign
* Il certificato SSL è vivamente consigliato

<br>

## Guardrail

### Ridimensionamento del server applicazioni

* Lo storage può essere scalato fino a 100M di profili
* Configurazione e controllo dell’accesso utente tramite Adobe Admin Console (consigliato) o localmente nell’applicazione stessa
* Il caricamento dei dati in Campaign deve essere eseguito tramite file batch
   * Il supporto per il caricamento dei dati API è principalmente per la gestione di profili o oggetti semplici all’interno del database (ovvero per creare e aggiornare). Non è destinato a essere utilizzato per caricare grandi volumi di dati o operazioni simili a lotti.
   * L’utilizzo delle API per leggere i dati a scopo di applicazione personalizzata non è supportato
* Le chiamate API sono limitate a 15 al secondo o 150.000 al giorno su scala

### Ridimensionamento del server di messaggistica in batch

* Scalabilità fino a 2,5 M messaggi all&#39;ora

### Ridimensionamento del server di messaggistica in tempo reale

* Può inviare fino a 50.000 messaggi all&#39;ora
* Per impostazione predefinita, sono disponibili due server di messaggistica in tempo reale. Possibilità di scalare fino a otto server di messaggistica in tempo reale.

### Configurazione SMS

* Campaign offre la possibilità di integrarsi con un provider SMS. Il provider viene acquistato dal cliente e integrato con la campagna per l’invio di messaggi basati su SMS
* Il supporto avviene tramite il protocollo SMPP
* Ci sono tre (3) diversi tipi di SMS che tutti gli Adobi possono supportare:
   * SMS MT (Mobile Terminated): un SMS inviato da Adobe Campaign ai telefoni cellulari tramite il provider SMPP.
   * SMS MO (origine mobile): un SMS inviato da un dispositivo mobile ad Adobe Campaign tramite il provider SMPP.
   * SMS SR (Status Report) o DR o DLR (Delivery Receipt): una ricevuta di ritorno inviata dal dispositivo mobile ad Adobe Campaign tramite il provider SMPP che indica che l’SMS è stato ricevuto correttamente. Adobe Campaign può anche ricevere SR che indica che il messaggio non può essere consegnato, spesso con una descrizione dell’errore.

### Configurazione push mobile

* Due approcci supportati per l’integrazione con i dispositivi mobili per le notifiche push:
   * Experience Platform Mobile SDK (consigliato)
   * SDK per Campaign Mobile
* Experience Platform di percorso dell’SDK di Mobile:
   * Sfrutta i tag di Adobe e l’estensione Campaign Classic per configurare la tua integrazione con l’SDK di Experience Platform Mobile
   * Necessità di una conoscenza operativa dei tag Adobi e della raccolta dei dati
   * Per distribuire l&#39;SDK, integrarsi con FCM (Android) e APNS (iOS) per ottenere il token push, configurare l&#39;app per la ricezione di notifiche push e gestire le interazioni push, è necessario che l&#39;esperienza di sviluppo mobile con le notifiche push sia in Android che in iOS sia con FCM (Android) e APNS ()
* SDK per Campaign Mobile
   * Contatta l’Assistenza clienti Adobe per accedere
   * Segui la [Documentazione di Campaign SDK](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/integrating-campaign-sdk-into-the-mobile-application.html?lang=en) per scoprire come installare e configurare l’SDK

   >[!IMPORTANT]
   >Se distribuisci l’SDK di Campaign e lavori con altre applicazioni Experience Cloud, per la raccolta dei dati dovrai utilizzare l’SDK di Experience Platform Mobile. Si tratta di un SDK diverso e dovrà essere installato insieme all’SDK di Campaign

<br>

## Fasi di implementazione

Consulta la sezione [Guida introduttiva](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/starting-with-adobe-campaign/about-adobe-campaign-classic.html?lang=en) per l’implementazione di Adobe Campaign v7


## Documentazione correlata

* [Documentazione di Campaign v7](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=it)
* [Descrizione del prodotto Campaign v7](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/launch.html?lang=it)
* [Documentazione di Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
