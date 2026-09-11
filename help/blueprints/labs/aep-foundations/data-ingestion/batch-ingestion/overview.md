---
hold: true
title: Acquisizione in batch
description: Carica i dati dell’account cliente tramite l’acquisizione batch nel Data Lake e nel profilo, correggendo al contempo gli errori di mappatura e qualità dei dati.
doc-type: overview-page
solution: Experience Platform
exl-id: 76830e79-8fc0-4fda-98b1-2c1de19e8158
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Acquisizione in batch

## Obiettivi di apprendimento

In questo esercizio, i dati dell’account cliente verranno caricati da un connettore di origine basato su file in AEP Data Lake e quindi nel profilo. Scopri quanto segue:

1. Informazioni sulle mappature passthrough
1. Correzione delle mappature passthrough generate da apprendimento automatico
1. Utilizzo dell’anteprima dei dati sorgente per verificare eventuali problemi di qualità dei dati
1. Programmazione di un’esecuzione del flusso di dati
1. Gestione degli errori derivanti da valori mancanti nei campi obbligatori
1. Gestione degli errori derivanti da errori di mancata corrispondenza dei tipi di dati
1. Gestione degli errori di acquisizione dei dati e ripristino da tali errori
1. Utilizzo iterativo dei dati di test per generare un set di mappatura completo.

>[!NOTE]
>
>Se non hai completato la creazione dello schema dell&#39;account cliente nei laboratori precedenti, puoi esplorare il catalogo degli schemi e utilizzare invece **dep: Account cliente**
