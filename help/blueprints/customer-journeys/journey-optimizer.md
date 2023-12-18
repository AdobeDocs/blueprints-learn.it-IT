---
title: Journey Optimizer - Blueprint per messaggistica attivata e Adobe Experience Platform
description: Esegui messaggi ed esperienze attivate utilizzando Adobe Experience Platform come hub centrale per lo streaming di dati, profili dei clienti e segmentazione.
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 5f9384abe7f29ec764428af33c6dd1f0a43f5a89
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 97%

---

# Journey Optimizer blueprint

Adobe Journey Optimizer è un sistema appositamente progettato che consente ai team di marketing di reagire in tempo reale ai comportamenti dei clienti e di incontrarli là dove si trovano. Le funzionalità di gestione dei dati sono state trasferite in Adobe Experience Platform, consentendo ai team di marketing di concentrarsi sul loro punto di forza: la creazione di percorsi cliente d’eccellenza e conversazioni personalizzate. Questo blueprint delinea le funzionalità tecniche dell’applicazione e descrive i vari componenti dell’architettura di Adobe Journey Optimizer.

<br>

## Casi di utilizzo

* Messaggi attivati
* Conferme di benvenuto e registrazione
* Abbandoni del carrello e del modulo di richiesta
* Messaggi attivati dalla posizione
* Esperienze all’interno di uno stadio
* Esperienze di viaggio e ospitalità prima e durante il soggiorno

<br>

## Architettura

<img src="assets/ajo-architecture.svg" alt="Architettura di riferimento per il blueprint Journey Optimizer" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Scenari del blueprint

| Scenario | Descrizione | Funzionalità |
| :-- | :--- | :--- |
| [Messaggistica di terze parti](3rd-party-messaging.md) | Mostra come Adobe Journey Optimizer può essere utilizzato con sistemi di messaggistica di terze parti per orchestrare e inviare comunicazioni personalizzate. | Invia ai clienti comunicazioni 1:1 personalizzate sul momento mentre interagiscono con il tuo brand o la tua azienda.<br><br>Considerazioni:<br><ul><li>Il sistema di terze parti deve supportare i bearer token per l’autenticazione.</li><li>Gli IP statici non sono supportati, a causa dell’architettura multi-tenant.</li><li>Considera i vincoli dell’architettura del sistema di terze parti in termini di chiamate API al secondo. Per supportare il volume proveniente da Journey Optimizer, potrebbe essere necessario acquistare ulteriori volumi dal fornitore di terze parti.</li><li>La funzionalità Gestione delle decisioni non è supportata nei messaggi o nei payload.</li></ul> |

<br>

## Modelli di integrazione

| Integrazione | Descrizione | Funzionalità |
| :-- | :--- | :--- |
| [Journey Optimizer con Adobe Campaign](ajo-and-campaign.md) | Mostra come utilizzare Adobe Journey Optimizer per orchestrare esperienze 1:1 utilizzando il profilo del cliente in tempo reale, e come sfruttare il sistema di messaggistica transazionale nativo di Adobe Campaign per inviare il messaggio. | Sfrutta il profilo cliente in tempo reale e la potenza di Journey Optimizer per orchestrare le esperienze attuali, e utilizza le funzionalità di messaggistica nativa in tempo reale di Adobe Campaign per le comunicazioni della fase finale.<br><br>Considerazioni:<br><ul><li>La versione dell’applicazione Campaign deve essere v7 build >21.1 oppure v8</li><li>Velocità della messaggistica</li><ul><li>Campaign v7: fino a 50.000 all’ora</li><li>Campaign v8: fino a 1 milione all’ora</li><li>Campaign Standard: fino a 50.000 all’ora</li></ul><li>Non viene applicata alcuna limitazione; pertanto i casi d’uso devono superare una verifica tecnica da parte di un Enterprise Architect.</li><li>Non è supportato l’utilizzo di Gestione delle decisioni nei messaggi inviati da Campaign.</li></ul> |

<br>

## Prerequisiti

Adobe Experience Platform

* Gli schemi e i set di dati devono essere configurati nel sistema prima di poter configurare le origini dati di Journey Optimizer.
* Per poter attivare un evento non basato su regole, aggiungi il gruppo di campi Orchestration eventID agli schemi di eventi Experience basati su classi.
* Per poter caricare profili di test da utilizzare con Journey Optimizer, aggiungi il gruppo di campi “Profile test details” agli schemi per singoli profili basati su classi.

E-mail

* Deve essere disponibile un sottodominio da utilizzare per l’invio dei messaggi.
* Il sottodominio può essere completamente delegato ad Adobe (consigliato) oppure è possibile utilizzare CNAME verso server DNS specifici per Adobe (personalizzati).
* Per garantire il corretto recapito dei messaggi, è necessario un record Google TXT per ciascun sottodominio.

Push per dispositivi mobili

* Per creare l’app, il cliente deve disporre di uno sviluppatore di app mobili.
* SDK per dispositivi mobili di Adobe Experience Platform

<br>

## Guardrail

[Link al prodotto per i guardrail Journey Optimizer](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html)

[Guardrail e guida alla latenza end-to-end](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## Documentazione correlata

* [Documentazione di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [Documentazione sui tag di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it)
* [Documentazione di Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
* [Documentazione di Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=it)
* [Descrizione del prodotto Journey Optimizer](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer.html)
