---
title: Settore telecomunicazioni - Journey Optimizer per messaggistica basata su trigger
description: Fornisci ai clienti offerte personalizzate in tempo reale e con onboarding efficiente dei clienti per assicurarne la fidelizzazione a lungo termine.
solution: Journey Optimizer
kt: 9486
exl-id: fa4a6569-3972-4b97-91f1-7ca8ffd3c5b3
source-git-commit: 1a0ce987fc615080bb78fb8ecf60c96e362a95c0
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 100%

---

# Le sfide nel settore telecomunicazioni

Prima di implementare questo blueprint, le campagne e-mail condotte da questa società di telecomunicazioni per l’aggiunta di una nuova linea si basavano sull’avvenuta conversione dell’utente, che veniva verificata solo dopo un periodo di attesa di 7 giorni. Una volta soddisfatti questi criteri, venivano avviati eventuali ulteriori punti di contatto.

Per poter avviare le attività di follow-up in modo più tempestivo per gli utenti che desideravano aggiungere una linea prima dell’attuale periodo di attesa di 7 giorni, era necessario superare questa limitazione.

## L’approccio Adobe

* Integrare in Adobe Journey Optimizer i dati Adobe Analytics come origine dati, per individuare gli utenti non convertiti all’aggiunta di una nuova linea.
* Utilizzare in Adobe Journey Optimizer una regola per definire quando inviare al cliente a rischio di “abbandono” un messaggio personalizzato volto a incoraggiarne la conversione e la richiesta di una nuova linea.


## Valore aziendale conseguito

| Obiettivi | Tattiche | Nuovo valore |
|---|---|---|
| **Migliorare il tasso di conversione delle campagne **<br></br>** Incrementare le entrate annuali dagli account**</ul> | <ul><li>Creare un nuovo segmento in tempo quasi reale per gli utenti interessati all’aggiunta di una nuova linea ma non ancora convertiti.</li><li>Attivare un secondo punto di contatto per il follow-up dei clienti interessati ma non ancora convertiti. </li><li>Utilizzare una strategia di test per misurare le prestazioni del percorso e ottimizzarle per la conversione tramite e-mail.</li></ul> | <ul><li><strong>Esperienze rilevanti e di alta qualità:</strong> con l’orchestrazione dei percorsi, i clienti ricevono messaggi più pertinenti e quindi si riduce il tasso di abbandono delle mailing list.</li><li><strong>Journey Orchestration adattabile:</strong> è possibile creare percorsi personalizzati e tempestivi per incrementare le conversioni e i ricavi totali.</li></ul> |

## Blueprint principale: Audience e attivazione con applicazioni Experience Cloud

### Descrizione

<ul><li>Messaggi attivati e in streaming utilizzando Adobe Experience Platform, come hub centrale per lo streaming dei dati, i profili clienti e la segmentazione, utilizzando Journey Orchestration per l’orchestrazione del percorso e la distribuzione dei messaggi</li></ul>

### Applicazioni Experience Cloud

<ul><li>Adobe Journey Optimizer</li></ul>

### Architettura del blueprint

<a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer.html?lang=it"><img alt="immagine di una società di telecomunicazioni che invia offerte personalizzate in tempo reale, con onboarding efficiente dei clienti per assicurarne la fidelizzazione a lungo termine." src="https://experienceleague.adobe.com/docs/blueprints-learn/assets/ajo-architecture.svg"/></a>
