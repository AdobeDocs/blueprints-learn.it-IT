---
title: Settore delle telecomunicazioni - Journey Optimizer per messaggi a impulso
description: Fornisci ai clienti offerte personalizzate in tempo reale, con un onboarding efficiente per la fedeltà a lungo termine.
solution: Experience Platform, Journey Optimizer
kt: 9486
source-git-commit: 7a81ea5d71355323a784e12207542fb7dd6b286b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 12%

---


# La sfida dell&#39;industria delle telecomunicazioni

Prima di implementare questo Blueprint, le campagne e-mail della società di telecomunicazioni &quot;aggiungi una nuova riga&quot; si basavano sul fatto che l&#39;utente si fosse convertito e verificato solo dopo un periodo di attesa di 7 giorni. Una volta soddisfatti questi criteri, sono stati avviati tutti i punti di contatto aggiuntivi.

Questa limitazione doveva essere risolta al fine di avviare un seguito più tempestivo per gli utenti che desideravano aggiungere una linea prima del periodo di attesa attuale di 7 giorni.

## Approccio Adobe

* I dati di Adobe Analytics per identificare gli utenti che non sono riusciti a convertire per aggiungere una nuova riga sono inclusi come origine dati da utilizzare in Adobe Journey Optimizer.
* Adobe Journey Optimizer utilizza una regola ogni volta quando i clienti ricevono un messaggio &quot;abbandono&quot; personalizzato progettato per incoraggiare un cliente a convertire aggiungendo una nuova riga al proprio account.


## Valore aziendale fornito

| Obiettivi | tattiche | Valore non caricato |
|---|---|---|
| **Aumento dei tassi di conversione delle campagne **<br></br>**Aumentare i ricavi annuali dei conti**</ul> | <ul><li>Crea un nuovo segmento in tempo quasi reale per gli utenti che hanno mostrato un interesse nell’aggiungere una riga ma non sono ancora stati convertiti.</li><li>Guidare il follow-up per i clienti non convertiti con un secondo punto di contatto per i non convertitori interessati. </li><li>Utilizza una strategia di test per misurare le prestazioni del percorso e ottimizzarle per la conversione tramite e-mail.</li></ul> | <ul><li><strong>Esperienze Di Alta Qualità E Rilevanti:</strong> Con l’orchestrazione dei percorsi in atto, i clienti sperimentano messaggi più pertinenti che riducono la fidelizzazione dell’elenco delle e-mail.</li><li><strong>Journey Orchestration su scala:</strong>È possibile creare un percorso personalizzato e più temporale per incrementare le conversioni e i ricavi totali.</li></ul> |

## Blueprint chiave: Pubblico e attivazione con applicazioni Experience Cloud

<strong>Descrizione</strong>
<ul><li>Esegui messaggi attivati e in streaming utilizzando Adobe Experience Platform, come hub centrale per lo streaming dei dati, i profili clienti e la segmentazione, con Journey Orchestration per l’orchestrazione del percorso in streaming e la distribuzione dei messaggi</li></ul>

<strong>Applicazioni Experience Cloud</strong>
<ul><li>Adobe Journey Optimizer</li></ul> 
<br>

### Architettura Blueprint

<a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer.html?lang=it"><img alt="L&#39;immagine thumbnail di un&#39;azienda di telecomunicazioni offre offerte personalizzate in tempo reale, mentre con un onboarding efficiente per la fedeltà a lungo termine." src="https://experienceleague.adobe.com/docs/blueprints-learn/assets/journey-optimizer.png?lang=en"/></a>





