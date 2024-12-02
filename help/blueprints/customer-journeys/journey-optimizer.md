---
title: '[!DNL Journey Optimizer] - Messaggistica attivata e blueprint Adobe Experience Platform'
description: Esegui messaggi ed esperienze attivate utilizzando Adobe Experience Platform come hub centrale per lo streaming di dati, profili dei clienti e segmentazione.
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: a1f3aef5b508575019bd651b9706efc7d6db5306
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 53%

---

# [!DNL Journey Optimizer] blueprint

Adobe [!DNL Journey Optimizer] è un sistema appositamente progettato per consentire ai team di marketing di reagire in tempo reale ai comportamenti dei clienti e di incontrarli ovunque si trovino. Le funzionalità di gestione dei dati sono state spostate nell&#39;Adobe [!DNL Experience Platform], consentendo ai team di marketing di concentrarsi su ciò che fanno meglio: ovvero la creazione di conversazioni personalizzate e di percorso di clienti di altissimo livello.

Questo blueprint illustra le funzionalità tecniche dell&#39;applicazione e fornisce informazioni approfondite sui vari componenti dell&#39;architettura che compongono [!DNL Journey Optimizer].

## Casi di utilizzo

* Messaggi attivati
* Conferme di benvenuto e registrazione
* Abbandoni del carrello e del modulo di richiesta
* Messaggi attivati dalla posizione
* Esperienze all’interno di uno stadio
* Esperienze di viaggio e ospitalità prima e durante il soggiorno

## Architettura

<img src="assets/ajo-architecture.svg" alt="Architettura di riferimento per il blueprint Journey Optimizer" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Scenari del blueprint

| Scenario | Descrizione | Funzionalità |
| :-- | :--- | :--- |
| [Messaggistica di terze parti](3rd-party-messaging.md) | Dimostra come Adobe [!DNL Journey Optimizer] può essere utilizzato con sistemi di messaggistica di terze parti per orchestrare e inviare comunicazioni personalizzate | Invia ai clienti comunicazioni 1:1 personalizzate sul momento mentre interagiscono con il tuo brand o la tua azienda.<br><br>Considerazioni:<br><ul><li>Il sistema di terze parti deve supportare i bearer token per l’autenticazione.</li><li>Gli IP statici non sono supportati, a causa dell’architettura multi-tenant.</li><li>Considera i vincoli dell’architettura del sistema di terze parti in termini di chiamate API al secondo. Potrebbe essere necessario che il cliente acquisti un volume aggiuntivo dal fornitore di terze parti per supportare il volume proveniente da [!DNL Journey Optimizer]</li><li>La funzionalità Gestione delle decisioni non è supportata nei messaggi o nei payload.</li></ul> |

<br>

## Modelli di integrazione

| Integrazione | Descrizione | Funzionalità |
| :-- | :--- | :--- |
| [[!DNL Journey Optimizer] con Adobe Campaign](ajo-and-campaign.md) | Mostra come utilizzare Adobe [!DNL Journey Optimizer] per orchestrare esperienze 1:1 utilizzando Real-Time Customer Profile e come sfruttare il sistema nativo di messaggistica transazionale di Adobe Campaign per inviare il messaggio | Sfrutta il profilo cliente in tempo reale e la potenza di [!DNL Journey Optimizer] per orchestrare le esperienze del momento utilizzando le funzionalità native di messaggistica in tempo reale di Adobe Campaign per effettuare la comunicazione dell&#39;ultimo miglio<br><br>Considerazioni:<br><ul><li>La versione dell’applicazione Campaign deve essere v7 build >21.1 oppure v8</li><li>Velocità della messaggistica</li><ul><li>Campaign v7: fino a 50.000 all’ora</li><li>Campaign v8: fino a 1 milione all’ora</li><li>Campaign Standard: fino a 50.000 all’ora</li></ul><li>Non viene applicata alcuna limitazione; pertanto i casi d’uso devono superare una verifica tecnica da parte di un Enterprise Architect.</li><li>Non è supportato l’utilizzo di Gestione delle decisioni nei messaggi inviati da Campaign.</li></ul> |

<br>

## Prerequisiti

Adobe [!DNL Experience Platform]:

* Gli schemi e i set di dati devono essere configurati nel sistema prima di poter configurare [!DNL Journey Optimizer] origini dati
* Per poter attivare un evento non basato su regole, aggiungi il gruppo di campi Orchestration eventID agli schemi di eventi Experience basati su classi.
* Per gli schemi basati su singole classi di profilo, aggiungere il gruppo di campi &quot;Dettagli test profilo&quot; per caricare i profili di test da utilizzare con [!DNL Journey Optimizer]

E-mail:

* Deve essere disponibile un sottodominio da utilizzare per l’invio dei messaggi.
* Il sottodominio può essere completamente delegato ad Adobe (consigliato) oppure è possibile utilizzare CNAME verso server DNS specifici per Adobe (personalizzati).
* Per garantire il corretto recapito dei messaggi, è necessario un record Google TXT per ciascun sottodominio.

Push mobile:

* Per creare l’app, il cliente deve disporre di uno sviluppatore di app mobili.
* SDK per dispositivi mobili di Adobe Experience Platform

## Guardrail

[[!DNL Journey Optimizer] Collegamento prodotto guardrail](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html)

[Guardrail e indicazioni sulla latenza End to End](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## Documentazione correlata

* [[!DNL Experience Platform] documentazione](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [[!DNL Experience Platform] Documentazione sui tag](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it)
* [[!DNL Experience Platform Mobile SDK] documentazione](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
* [[!DNL Journey Optimizer] documentazione](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=it)
* [[!DNL Journey Optimizer] descrizione del prodotto](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer.html)
