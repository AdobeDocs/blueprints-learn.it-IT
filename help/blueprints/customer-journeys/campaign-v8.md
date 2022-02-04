---
title: Blueprint Campaign v8
description: Adobe Campaign v8 è lo strumento di campagna di nuova generazione creato per i canali di marketing tradizionali come e-mail e direct mail. Fornisce solide funzionalità di ETL e gestione dei dati per aiutare a creare e curare la campagna perfetta. Il motore di orchestrazione fornisce programmi di marketing multi-touch avanzati con un focus principale sui percorsi basati su batch.  Viene inoltre fornito con un server di messaggistica scalabile in tempo reale che consente ai team di marketing di inviare messaggi predefiniti basati su un payload completo da qualsiasi sistema IT per elementi quali reimpostazione della password, conferma dell’ordine, e-Receips (Ricezione elettronica) e molto altro ancora.
solution: Campaign v8
source-git-commit: 1c46cbdfc395de4fc9139966cf869ba1feeceaaa
workflow-type: tm+mt
source-wordcount: '1084'
ht-degree: 3%

---

# Blueprint Campaign v8

Adobe Campaign v8 è lo strumento di campagna di nuova generazione creato per i canali di marketing tradizionali come e-mail e direct mail. Fornisce solide funzionalità di ETL e gestione dei dati per aiutare a creare e curare la campagna perfetta. Il motore di orchestrazione fornisce programmi di marketing multi-touch avanzati con un focus principale sui percorsi basati su batch.  Viene inoltre fornito con un server di messaggistica scalabile in tempo reale che consente ai team di marketing di inviare messaggi predefiniti basati su un payload completo da qualsiasi sistema IT per elementi quali reimpostazione della password, conferma dell’ordine, e-Receips (Ricezione elettronica) e molto altro ancora.

<br>

## Casi di utilizzo

* Programmi di messaggistica in batch molto complessi
* Campagne di onboarding e di re-marketing
* Pubblicità Direct Mail, opuscolo e campagne pubblicitarie
* Messaggistica transazionale semplice (ad esempio reimpostazione della password, ricezioni e-mail, conferme di ordine, ecc.)

<br>

## Architettura

<img src="assets/campaign-v8-architecture.svg" alt="Architettura di riferimento per la blueprint di Campaign v8" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Pattern di integrazione

| Scenario | Descrizione | Funzionalità |
| :-- | :--- | :--- |
| [Journey Optimizer con Adobe Campaign](ajo-and-campaign.md) | Mostra come utilizzare Adobe Journey Optimizer per orchestrare esperienze 1:1 utilizzando il Profilo del cliente in tempo reale e come sfruttare il sistema di messaggistica transazionale nativo di Adobe Campaign per inviare il messaggio | Sfruttare il Profilo cliente in tempo reale e la potenza di Journey Optimizer per orchestrare le esperienze attuali e allo stesso tempo utilizzare le funzionalità di messaggistica nativa in tempo reale di Adobe Campaign per la comunicazione dell’ultimo miglio<br><br>Considerazioni:<br><ul><li>Può inviare fino a 1 milione di messaggi all&#39;ora tramite il server di messaggio in tempo reale<li>Journey Optimizer non esegue alcuna limitazione in modo da garantire il controllo tecnico da parte di un architetto aziendale pre-vendita</li><li>Offer Decisioning non è supportato nei payload per Campaign v8</li></ul> |

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

* Lo storage può essere scalato fino a 200M di profili con possibilità di scalabilità fino a 1B
* Configurazione e controllo dell’accesso utente tramite Adobe Admin Console
* Il caricamento dei dati in Campaign deve essere eseguito tramite file batch
   * Il supporto per il caricamento dei dati API è principalmente per la gestione di profili o oggetti semplici all’interno del database (ovvero per creare e aggiornare). Non è destinato a essere utilizzato per caricare grandi volumi di dati o operazioni simili a lotti.
   * L’utilizzo delle API per leggere i dati a scopo di applicazione personalizzata non è supportato
   * I dati caricati tramite API vengono memorizzati nel database delle applicazioni e quindi replicati ogni ora nel database Cloud
* Le chiamate API sono limitate a 15 al secondo o 150.000 al giorno su scala

### Ridimensionamento del server di messaggistica in batch

* Scalabilità fino a 20 M messaggi all&#39;ora

### Ridimensionamento del server di messaggistica in tempo reale

* Può inviare fino a 1 milione di messaggi all&#39;ora
* Per impostazione predefinita viene eseguito il provisioning di un solo (1) server di messaggistica in tempo reale. In questo modo, qualsiasi comunicazione con il server viene effettuata tramite un token di sessione che scade tra 24 ore
* Facoltativamente è possibile distribuire fino a otto (8) server di messaggistica in tempo reale, ma l&#39;autenticazione supporta solo l&#39;utente/pass
* L’approccio consigliato è sempre quello di utilizzare un server di messaggistica in tempo reale per sfruttare, ove possibile, l’autenticazione basata sui token di sessione

### Configurazione SMS

* Campaign offre la possibilità di integrarsi con un provider SMS. Il provider viene acquistato dal cliente e integrato con la campagna per l’invio di messaggi basati su SMS
* Il supporto avviene tramite il protocollo SMPP
* Ci sono tre (3) diversi tipi di SMS che tutti gli Adobi possono supportare:
   * SMS MT (Mobile Terminated): un SMS inviato da Adobe Campaign ai telefoni cellulari tramite il provider SMPP.
   * SMS MO (origine mobile): un SMS inviato da un dispositivo mobile ad Adobe Campaign tramite il provider SMPP.
   * SMS SR (Status Report) o DR o DLR (Delivery Receipt): una ricevuta di ritorno inviata dal dispositivo mobile ad Adobe Campaign tramite il provider SMPP che indica che l’SMS è stato ricevuto correttamente. Adobe Campaign può anche ricevere SR che indica che il messaggio non può essere consegnato, spesso con una descrizione dell’errore.

### Configurazione push mobile

* Solo l’SDK Campaign è supportato per Campaign v8. Contatta l’Assistenza clienti Adobe per accedere
* Segui la [Documentazione di Campaign SDK](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/integrating-campaign-sdk-into-the-mobile-application.html?lang=en) per scoprire come installare e configurare l’SDK

   >[!IMPORTANT]
   >Altre applicazioni di Experience Cloud richiedono l’utilizzo dell’SDK di Experience Platform Mobile per la raccolta dei dati. Si tratta di un SDK diverso e dovrà essere installato insieme all’SDK di Campaign

<br>

## Fasi di implementazione

Consulta la guida introduttiva per [Implementazione di Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/implement/implement.html?lang=en)


## Documentazione correlata

* [Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=en)
* [Descrizione del prodotto Campaign v8](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/launch.html?lang=it)
* [Documentazione di Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
