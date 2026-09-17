---
title: Attivazione di Edge
description: Scopri le differenze tra le velocità di attivazione di Edge, streaming e batch, e visualizza in anteprima i passaggi del laboratorio per la creazione di un segmento Edge e la configurazione dell’inoltro degli eventi.
doc-type: overview-page
solution: Experience Platform
exl-id: 9ecadff9-3838-4cd4-93b1-7c23a232f84c
source-git-commit: 8b3391d41cd4a3ea6cb52d5167e627b7f6bd2c6e
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%
---

# Attivazione di Edge

## Riepilogo velocità di attivazione

Adobe offre tre velocità di attivazione per soddisfare le diverse esigenze:

1. Edge
1. Streaming
1. Batch

Scopriremo come effettuare l’attivazione utilizzando Adobe Edge con Event Forwarding, Edge Audiences e Edge Personalization. Verrà quindi mostrato come utilizzare le destinazioni di streaming dall’hub sia per Edge che per una destinazione esterna.

>[!IMPORTANT]
>
>Completare l&#39;[installazione di Postman](../../setup.md) prima di avviare questa esercitazione. È inoltre necessario accedere a [webhook.site](https://webhook.site/) per acquisire l&#39;evento inviato alla destinazione esterna.

>[!NOTE]
>
>Non copriremo l’attivazione batch in questo laboratorio. L&#39;attivazione batch può essere pianificata a intervalli diversi e la tempistica rende difficile la visualizzazione in un ambiente di laboratorio senza avere almeno 3-24 ore.



## Cosa coprirà il laboratorio

- Creare un segmento di Edge
- Configura inoltro eventi
- Inviare un evento Edge
- Questo trigger
  - Segmento Edge da qualificare
  - Inoltro eventi su Edge da inviare al webhook
