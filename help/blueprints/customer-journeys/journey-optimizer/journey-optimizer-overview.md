---
title: '[!DNL Journey Optimizer] - Blueprint Percorsi'
description: Esegui messaggi ed esperienze attivate utilizzando Adobe Experience Platform come hub centrale per lo streaming di dati, profili dei clienti e segmentazione.
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 3a3988e93dd9e92f4f564bfedfa314e8e2b5d9ba
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 15%

---

# [!DNL Journey Optimizer] blueprint

Adobe [!DNL Journey Optimizer] è un&#39;applicazione nativa per il cloud basata su Adobe Experience Platform che consente l&#39;orchestrazione pianificata e in tempo reale dei percorsi di clienti su più canali. Supporta trigger guidati da eventi, segmentazione del pubblico e servizi decisionali per distribuire esperienze personalizzate tramite e-mail, SMS, push, web e messaggistica in-app. Si integra con i sistemi in entrata e in uscita, consentendo la gestione unificata dello stato del pubblico e il coinvolgimento contestuale lungo il ciclo di vita del cliente.

Questo blueprint illustra le funzionalità tecniche dell&#39;applicazione e fornisce informazioni approfondite sui vari componenti dell&#39;architettura che compongono [!DNL Journey Optimizer].

<br>

## Casi di utilizzo

>[!BEGINTABS]
>[!TAB Percorso (Basato Su Eventi, In Tempo Reale)]

- **Abandonment Recovery:** attiva messaggi personalizzati quando un utente abbandona un carrello, un modulo o una sessione tramite e-mail, push o in-app.
- **Iscrizione nuovo utente:** coinvolgi i nuovi utenti subito dopo la registrazione con le preferenze del nuovo account, le promozioni o i vantaggi pertinenti
- **Messaggistica transazionale:** invia conferme, avvisi o aggiornamenti in tempo reale (ad esempio, ordine spedito, reimpostazione password) utilizzando i trigger di evento.
- **Targeting contestuale:** Comunica con gli utenti nel momento in base ai segnali e alla posizione per guidare e indirizzare la loro esperienza
- **Vendita contestuale/cross-selling:** Distribuisci offerte personalizzate basate su attributi di profilo in tempo reale e interazioni recenti.

>[!TAB Orchestrazione campagna (pianificata, avviata dal marchio)]

- **Campagne promozionali**: avvia campagne multicanale e in più passaggi per il lancio di prodotti, offerte stagionali o eventi di vendita.
- **Lifecycle Marketing**: automatizza campagne ricorrenti come messaggi di compleanno, promemoria di rinnovo o milestone di fedeltà.
- **Push di Funnel basati sul pubblico**: segmenta e invia i tipi di pubblico in campagne strutturate in base alla logica di business o agli attributi di gestione delle relazioni con i clienti.
- **Newsletter e distribuzione dei contenuti**: pianifica e distribuisci contenuti personalizzati a tipi di pubblico mirati tramite e-mail e dispositivi mobili.
- **Campagne di ricoinvolgimento**: identifica gli utenti inattivi e li reintroduce nei flussi di coinvolgimento in base alle soglie di inattività.

>[!ENDTABS]

<br>

## Architettura

<img src="images/ajo-architecture.svg" alt="Blueprint per architettura di riferimento Adobe Journey Optimizer" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Scenari del blueprint

| Scenario | Descrizione |
| :-- | :-- |
| [Percorsi](journey-optimizer-journeys.md) | I Percorsi AJO in Adobe Journey Optimizer sono esperienze cliente automatizzate e personalizzate attivate da eventi in tempo reale o segmenti di pubblico, che consentono agli addetti al marketing di inviare messaggi rilevanti attraverso canali quali e-mail, SMS e notifiche push. |
| [Orchestrazione campagna](journey-optimizer-campaigns.md) | AJO Campaign Orchestration consente agli esperti di marketing di progettare ed eseguire campagne personalizzate cross-channel utilizzando dati in tempo reale e informazioni sul pubblico. Supporta il targeting dinamico, la consegna dei messaggi e la logica di percorso per ottimizzare il coinvolgimento dei clienti nei canali e-mail, SMS, push e personalizzati. |

<br>

## Pattern di integrazione

| Integrazione | Descrizione | Considerazioni tecniche |
| :-- | :-- | :-- |
| [Messaggistica di terze parti](3rd-party-messaging.md) | Dimostra come Adobe [!DNL Journey Optimizer] può integrarsi con piattaforme di messaggistica di terze parti per orchestrare e distribuire comunicazioni personalizzate ai clienti. | <ul><li>Il sistema di terze parti deve supportare l&#39;autenticazione con token **bearer**</li><li>**Gli IP statici non sono supportati** a causa dell&#39;architettura multi-tenant.</li><li>Tieni presente i **limiti di tariffa API** su sistemi di terze parti; i clienti potrebbero dover acquistare ulteriore capacità per gestire il traffico proveniente da **Adobe Journey Optimizer**.</li><li>**La gestione delle decisioni** non è supportata all&#39;interno dei payload dei messaggi o della logica di consegna.</li></ul> |
| [[!DNL Journey Optimizer] con Adobe Campaign v8](../campaign-v8/ajo-and-campaign-v8.md) | Dimostra come Adobe [!DNL Journey Optimizer] può integrarsi con le funzionalità di messaggistica transazionale di Adobe Campaign v8 per eseguire la consegna finale dei messaggi. | <ul><li>Non esiste alcuna limitazione dei messaggi. Limite di 4.000 messaggi per 5 minuti.</li><li>Supporta solo i percorsi avviati da eventi</li><li>La gestione delle decisioni non è supportata nei messaggi inviati da Campaign</li></ul> |

<br>

## Prerequisiti

Adobe [!DNL Experience Platform]:

- Gli schemi e i set di dati devono essere configurati nel sistema prima di poter configurare [!DNL Journey Optimizer] origini dati
- Per gli schemi basati su classi XDM Experience Event, aggiungi &quot;Gruppo di campi ID evento di orchestrazione&quot; quando desideri che venga attivato un evento che non sia un evento basato su regole
- Per gli schemi basati su classi di profilo individuali XDM, aggiungere il gruppo di campi &quot;Dettagli test profilo&quot; per caricare i profili di test da utilizzare con [!DNL Journey Optimizer]

<br>

E-mail:

- Deve essere disponibile un sottodominio da utilizzare per l’invio dei messaggi.
- Il sottodominio può essere completamente delegato ad Adobe (consigliato) oppure è possibile utilizzare CNAME verso server DNS specifici per Adobe (personalizzati).
- Per garantire il corretto recapito dei messaggi, è necessario un record Google TXT per ciascun sottodominio.

<br>

Push mobile:

- Per creare l’app, il cliente deve disporre di uno sviluppatore di app mobili.
- SDK per dispositivi mobili di Adobe Experience Platform

<br>

## Guardrail

[[!DNL Journey Optimizer] Collegamento prodotto guardrail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[Guardrail e indicazioni sulla latenza End to End](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html?lang=it)

## Documentazione correlata

- [[!DNL Experience Platform] documentazione](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
- [[!DNL Experience Platform] Documentazione sui tag](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it)
- [[!DNL Experience Platform Mobile SDK] documentazione](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
- [[!DNL Journey Optimizer] documentazione](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=it)
- [[!DNL Journey Optimizer] descrizione del prodotto](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer.html)