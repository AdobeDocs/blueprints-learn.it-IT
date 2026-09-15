---
title: Caso d’uso #1 - Acquisition
description: Definisci un caso di utilizzo di acquisizione che includa i visitatori di pagina iPhone 14 che non hanno ordinato o posseduto il dispositivo e pianifica l'approccio per la creazione di un pubblico.
doc-type: overview-page
solution: Experience Platform
exl-id: a85b1eb1-88f4-41b2-acce-2e34dbe6aff8
source-git-commit: 8b3391d41cd4a3ea6cb52d5167e627b7f6bd2c6e
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%
---

# Caso d’uso #1: acquisizione

## Panoramica

Questo video illustra come approcciare la creazione del pubblico per il caso di utilizzo dell’acquisizione iPhone 14.

>[!VIDEO](https://video.tv.adobe.com/v/3459402/?quality=12&learn=on)



**Definizione del caso d&#39;uso**

Attiva tutti i profili che hanno visitato una pagina di prodotto di iPhone 14 e non esiste alcun ordine per un iPhone 14 o non hanno un iPhone 14 attivo.

>[!IMPORTANT]
>
>Completare l&#39;[installazione di Postman](../../setup.md) prima di avviare questa esercitazione. È inoltre necessario accedere a [webhook.site](https://webhook.site/) per acquisire i dati del pubblico attivato.



## Attività di analisi

Analizzare quanto sopra e annotare:

1. Quali campi sono necessari per risolvere questo caso d’uso?
1. Il metodo di valutazione deve essere Streaming?
1. Quali sono le ramificazioni dello streaming quando gli eventi utilizzati nel pubblico arrivano in momenti diversi?
1. Come facciamo a sapere cosa significa &quot;attivo&quot;?
1. Quali altre informazioni vorresti conoscere?

**Ricorda**: quando riceviamo i requisiti dalle parti interessate, queste tendono a essere incomplete, a utilizzare un&#39;altra terminologia e a fare supposizioni senza saperlo. È tuo compito far emergere tutto questo e guidarli verso qualcosa che possa essere fatto.



## Approccio

Per questo caso d’uso verrà suddiviso in più tipi di pubblico:

1. Nessun ordine esistente iPhone/Pixel
1. Nessun iPhone/Pixel attivo
1. IPhone/Pixel visitato &amp; Nessun ordine esiste iPhone/Pixel &amp; Nessun iPhone/Pixel attivo
