---
title: Eccitazione dopo l'acquisto
description: Scopri come creare un percorso post-acquisto basato su eventi che attiva un’e-mail di notifica di spedizione con dettagli di tracciamento dinamico da un’API di terze parti.
doc-type: overview-page
solution: Experience Platform
exl-id: 570dc378-e7a3-4895-8f14-89d420b6b340
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---


# Eccitazione dopo l&#39;acquisto

## Prerequisiti

>[!WARNING]
>
>Prima di avviare questo laboratorio, è necessario aver completato i seguenti laboratori

Prima di avviare questo laboratorio, è necessario che i seguenti laboratori siano stati completati:

- **Archivi dati - Archivio relazionale in azione** **—>** [Dimension di destinazione profilo](../../data-stores/relational-store-in-action/profile-target-dimension.md)
- **Archivi dati — Configura canali e-mail —>** [Configura per profilo](../../data-stores/configure-email-channels/configure-for-profile.md)
  *(il completamento può richiedere fino a 3 ore)*

Se non lo hai ancora fatto, completa questi moduli ora

## Panoramica di Lab

Questo video illustra come il caso di utilizzo di eccitazione post-acquisto si mappa su un percorso, esaminando le domande fondamentali e l’architettura per l’invio di una notifica di spedizione personalizzata una volta spedito un ordine.

>[!VIDEO](https://video.tv.adobe.com/v/3491146/)

## Obiettivi di apprendimento

- Creare un Percorso che inizia con un evento unitario
- Imposta e configura un’azione personalizzata per chiamare un sistema di terze parti e restituire le informazioni utilizzate in un Percorso
- Eseguire un percorso in streaming in un payload dell’evento
- Testare ed eseguire il debug di profili e Percorsi
- Convalidare l’esperienza prevista tramite reporting e registri
- Configurare la personalizzazione in un’e-mail semplice e visualizzarla in azione



## Descrizione del caso d’uso

Quando un cliente effettua un ordine, vuoi inviare un messaggio di conferma con i dettagli dell’ordine.  Una volta spedito l’ordine, vuoi attivare un secondo messaggio con informazioni di tracciamento recuperate in modo dinamico da un’API di terze parti.

**Callout chiave:**

- L’ordine iniziale effettuato verrebbe in genere implementato come messaggio transazionale, in quanto le persone non vogliono aspettare una conferma ma semplicemente ordinare qualcosa.
- La notifica di spedizione dell’ordine può essere implementata anche utilizzando la messaggistica transazionale, ma può essere integrata in un percorso che consente un’azione personalizzata per recuperare le informazioni di spedizione e migliorare la comunicazione con il cliente.

>[!NOTE]
>
>In questa esercitazione verrà compilato solo il messaggio Ordine spedito e il messaggio Conferma ordine verrà ignorato.
