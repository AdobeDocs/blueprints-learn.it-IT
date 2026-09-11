---
title: Trasmetti un evento ordine
description: Esercitazione sulla creazione di un flusso di dati in streaming API HTTP per inviare un evento di ordine di esempio e collegarlo a un profilo cliente esistente.
doc-type: article
solution: Experience Platform
exl-id: 558c21d1-f9b7-489b-9153-5f10d0b8448a
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Trasmetti un evento ordine

## Prerequisiti

1. Hai scaricato [File di esempio](../sample-files.md) e vedi il file denominato —> **Lab\_Single\_Order\_sample.json**
1. Hai completato correttamente l&#39;esercitazione [Using Data Landing Zone](./using-data-landing-zone/overview.md) e disponi di un set di mappatura valido da importare

## Sfida

Eseguire la seguente serie di operazioni come nel laboratorio precedente.

1. Creare un nuovo account utilizzando il connettore di origine API HTTP
1. Imposta un flusso di dati utilizzando il nuovo account per inviare dati nel set di dati Ordini cliente
1. Riutilizza il set di mappatura dal laboratorio [Using Data Landing Zone](./using-data-landing-zone/overview.md)
1. In Postman compila il **Crea evento ordine** con le informazioni necessarie per inviare correttamente i dati e allegarli al record Account cliente creato in precedenza
1. Verifica che l’ordine sia collegato al tuo profilo

>[!TIP]
>
>Buona fortuna e che gli dei di Adobe Experience Platform siano con voi!
