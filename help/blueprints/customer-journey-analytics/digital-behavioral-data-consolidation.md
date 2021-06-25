---
title: Analisi del percorso cross-channel
description: Analizza ed estrai informazioni dalle interazioni che avvengono durante il percorso del cliente.
solution: Experience Platform, Customer Journey Analytics, Data Collection
kt: 7208
exl-id: b042909c-d323-40d5-8b35-f3e5e3e26694
source-git-commit: 9fe9d67c5f97b633e45155bd54e2006f1b797332
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 100%

---

# Blueprint per analisi del percorso cross-channel

Crea una visione unica e consolidata del comportamento dei clienti attraverso i vari canali, grazie all’integrazione di dati provenienti da varie proprietà web, mobili e offline.

## Casi di utilizzo

* Analizzare le interazioni con i clienti su desktop e dispositivi mobili per comprendere il comportamento dei clienti ed estrarre informazioni utili per ottimizzare le esperienze digitali.
* Analizzare le interazioni con i clienti attraverso i canali, inclusi i canali digitali e offline, come le interazioni di supporto e gli acquisti in-store per comprendere meglio e ottimizzare il percorso del cliente. 

## Applicazioni

* Adobe Experience Platform
* Customer Journey Analytics
* Adobe Analytics (opzionale)

## Pattern di integrazione

* Adobe Experience Platform → Customer Journey Analytics
* Adobe Analytics → Adobe Experience Platform → Customer Journey Analytics

## Architettura

<img src="assets/CJA.svg" alt="Architettura di riferimento per il blueprint per Customer Journey Analytics" style="border:1px solid #4a4a4a" />

## Fasi di implementazione

1. [Creare schemi](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html?lang=it) per i dati da acquisire.
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) per i dati da acquisire.
1. [Inserire i dati](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=it) in Experience Platform
I dati devono essere inseriti in Platform prima di essere elaborati in Customer Journey Analytics.
1. Analizzare i set di dati relativi agli eventi multicanale da analizzare in unione, per assicurarsi che abbiano un ID di namespace comune o che siano riconfigurati tramite la funzionalità di composizione basata sul campo di Customer Journey Analytics. 

   >[!NOTE]
   >
   >Customer Journey Analytics attualmente non utilizza il profilo o i servizi di identità di Experience Platform per l’unione dei dati.

1. Eseguire sui dati eventuali operazioni di preparazione personalizzata o unione delle identità basate sul campo, affinché in Customer Journey Analytics venga inserita una chiave comune per tutti i set di dati delle serie temporali.
1. Assegnare ai dati di ricerca un ID primario che può essere associato a un campo nei dati dell’evento. Ai fini delle licenze conta come righe.
1. Impostare lo stesso ID primario per i dati del profilo e i dati degli eventi.
1. Configurare una connessione per l’acquisizione di dati da Experience Platform a Customer Journey Analytics. Una volta inseriti nel data lake, i dati vengono elaborati in Customer Journey Analytics entro 90 minuti.
1. Configurare una vista dati sulla connessione per selezionare dimensioni e metriche specifiche da includere nella vista. Anche le impostazioni di attribuzione e allocazione vengono configurate nella vista dati. Queste impostazioni vengono calcolate al momento della generazione del rapporto.
1. Creare un progetto per configurare dashboard e rapporti in Analysis Workspace.

## Considerazioni sull’implementazione

### Considerazioni sull’unione delle identità

* I dati delle serie temporali da unire devono avere lo stesso ID di namespace su ogni record.
* Il processo di unione di set di dati eterogenei richiede una chiave persona/entità primaria comune a tutti i set di dati.
* Le unioni basate su chiave secondaria attualmente non sono supportate.
* Il processo di unione delle identità basate sul campo consente di riconfigurare le identità in righe in base a successivi record di ID transitori, come gli ID di autenticazione. Questo consente di risolvere diversi record in un unico ID per l’analisi a livello di persona invece che a livello di dispositivo o cookie.
* L’unione avviene una volta alla settimana, con successiva ripetizione.

## Domande frequenti

* Quali sono gli impatti a valle dei modelli di dati in Customer Journey Analytics?

   In Customer Journey Analytics gli oggetti e gli attributi dello stesso campo XDM si fondono in un’unica dimensione. Per unire più attributi di vari set di dati nella stessa dimensione di Customer Journey Analytics, i set di dati devono fare riferimento allo stesso campo o schema XDM.

## Documentazione correlata

* [Descrizione del prodotto Customer Journey Analytics](https://helpx.adobe.com/it/legal/product-descriptions/customer-journey-analytics.html)
* [Documentazione di Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics.html?lang=it)
* [Tutorial su Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html?lang=it)
