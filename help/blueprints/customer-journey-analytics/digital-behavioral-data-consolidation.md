---
title: Scenario di consolidamento dei dati comportamentali digitali
description: Analizza ed estrae informazioni dalle interazioni dei clienti nel percorso di clienti.
solution: Experience Platform, Customer Journey Analytics, Data Collection
kt: 7208
translation-type: tm+mt
source-git-commit: e1a9881996a181310bdc32cb083e4c5654139bf0
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---


# Scenario di consolidamento dei dati comportamentali digitali

Avere un’unica vista consolidata del comportamento dei clienti tra vari canali unificando i dati provenienti da varie proprietà web, mobili e offline.

## Casi d&#39;uso

* Analizza le interazioni dei clienti su desktop e dispositivi mobili per comprendere il comportamento dei clienti ed estrarre informazioni per ottimizzare le esperienze digitali dei clienti.
* Analizza le interazioni dei clienti su tutti i canali, compresi i canali digitali e offline, come le interazioni di supporto e gli acquisti in-store per comprendere e ottimizzare meglio il percorso dei clienti. 

## Applicazioni

* Adobe Experience Platform
* Customer Journey Analytics
* Adobe Analytics (facoltativo)

## Modelli di integrazione

* Adobe Experience Platform → Customer Journey Analytics
* Adobe Analytics → Adobe Experience Platform → Customer Journey Analytics

## Architettura

<img src="assets/CJA.svg" alt="Architettura di riferimento per la blueprint del Customer Journey Analytics" style="border:1px solid #4a4a4a" />

## Guardrail

Acquisizione dei dati nel Customer Journey Analytics:

* Assimilazione dati al lago: API ~ 7 GB/ora, connettore sorgente ~ 200 GB/ora, streaming al lago ~ 15 minuti, connettore sorgente Adobe Analytics al lago ~ 45 minuti.
* Dopo la pubblicazione dei dati sul data lake, l&#39;elaborazione in Customer Journey Analytics può richiedere fino a 90 minuti.

## Passaggi di implementazione

1. Configura set di dati e schemi.
1. Inserire dati in Platform.
I dati devono essere acquisiti in Platform prima di essere elaborati in Customer Journey Analytics.
1. Analizza i set di dati evento cross-channel da analizzare nell’unione per assicurarti che abbiano un ID spazio dei nomi comune o che vengano reinseriti tramite la funzionalità di unione dei Customer Journey Analytics basata sui campi. 

   >[!NOTE]
   >
   >Al momento, Customer Journey Analytics non utilizza i servizi Profilo di Experience Platform o Identity per l’unione.

1. Esegui qualsiasi preparazione di dati personalizzati o utilizza l’unione di identità basata sui campi sui dati per garantire una chiave comune tra i set di dati delle serie temporali da acquisire nel Customer Journey Analytics.
1. Attribuisci ai dati di ricerca un ID primario che possa unirsi a un campo nei dati dell’evento. Conta come righe nella licenza.
1. Imposta lo stesso ID principale per i dati di profilo come ID principale dei dati dell’evento.
1. Configura una connessione dati per l’acquisizione di dati da Experience Platform a Customer Journey Analytics. Dopo l&#39;atterraggio dei dati nel lago dati, si trasforma in Customer Journey Analytics entro 90 minuti.
1. Configura una visualizzazione dati sulla connessione per selezionare le dimensioni e le metriche specifiche da includere nella visualizzazione. Le impostazioni di attribuzione e allocazione sono configurate anche nella visualizzazione dati. Queste impostazioni vengono calcolate al momento del rapporto.
1. Crea un progetto per configurare dashboard e rapporti in Analysis Workspace.

## Considerazioni sull’implementazione

### Considerazioni sull’unione delle identità

* I dati della serie temporale da separare devono avere lo stesso namespace ID su ogni record.
* Il processo di unione di diversi set di dati richiede una chiave primaria comune per la persona/entità nei set di dati.
* Le unioni basate su chiave secondarie non sono attualmente supportate.
* Il processo di unione delle identità basato sui campi consente di reinserire le identità nelle righe in base ai record ID transitori successivi, ad esempio un ID di autenticazione. Ciò consente di risolvere record diversi a un singolo ID per l&#39;analisi a livello di persona anziché a livello di dispositivo o cookie.
* Le cuciture succedono una volta alla settimana, con ripetizione dopo il punto.

## Domande frequenti

* Quali sono gli impatti a valle dei modelli di dati in Customer Journey Analytics?

   Gli oggetti e gli attributi dello stesso campo XDM si uniscono in una dimensione del Customer Journey Analytics. A  unisce più attributi da diversi set di dati alla stessa dimensione di Customer Journey Analytics, i set di dati devono fare riferimento allo stesso campo o schema XDM.

## Documentazione correlata

* [Descrizione del prodotto Customer Journey Analytics](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics.html)
* [Documentazione del Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics.html)
* [Esercitazioni sul Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html)




