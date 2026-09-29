---
title: Acquisizione del flusso
description: Carica i dati dell’account del cliente tramite un’origine di streaming nel Data Lake e nel profilo utilizzando un ingresso di streaming e l’API REST.
doc-type: overview-page
solution: Experience Platform
exl-id: 973a9cac-dc9d-4c5f-87c3-16a55efd1314
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%
---

# Acquisizione del flusso

## Obiettivi di apprendimento

In questo esercizio, caricheremo i dati dell’account cliente da un’origine di streaming a Adobe Experience Platform Data Lake e Profile. Cosa devi fare dopo aver preso questo laboratorio?

- Creazione di una presa di streaming
- Importazione set di mappatura da un altro flusso di dati
- Recupero ID flusso di dati e ID set di dati dall’interfaccia utente
- Utilizzo dell’API REST per acquisire un evento

>[!IMPORTANT]
>
>Completare l&#39;[installazione di Postman](../../setup.md) prima di avviare questa esercitazione.

>[!NOTE]
>
>Se non hai completato la creazione dello schema Account cliente nei laboratori precedenti, puoi esplorare il catalogo degli schemi e utilizzare invece **dep: Account cliente**
