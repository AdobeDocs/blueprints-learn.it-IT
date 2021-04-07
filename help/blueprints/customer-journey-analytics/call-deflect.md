---
title: Blueprint di analisi della deflessione delle chiamate
description: Analizza il comportamento dei clienti prima che contengano il call center.
solution: Experience Platform, Customer Journey Analytics
kt: 7209
exl-id: 13593c1c-4c58-4b8a-aa6c-7530fd679a14
translation-type: tm+mt
source-git-commit: 844fff1cefe367575beb5c03aa0f0d026eb9f39b
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# Blueprint di analisi del Percorso di riflessione delle chiamate

Analizza il comportamento di un cliente tra desktop e dispositivi mobili prima che contatta il call center. Identifica le opportunità per migliorare il percorso dei clienti comprendendo quali azioni i clienti tentano di completare, quali contenuti visualizzano e quali termini cercano prima di contattare l’assistenza clienti. Determina i contenuti e gli strumenti self-service che possono essere migliorati per aiutare i clienti a risolvere i problemi senza dover effettuare l’accesso.

## Casi d&#39;uso

* Analizzare il comportamento del cliente prima che i clienti contatta il supporto
* Scopri le opportunità di migliorare le funzionalità self-service

## Applicazioni

* Adobe Experience Platform
* Customer Journey Analytics

## Modelli di integrazione

* Adobe Experience Platform → Customer Journey Analytics

## Architettura

<img src="assets/CJA.svg" alt="Architettura di riferimento per la blueprint del Customer Journey Analytics" style="border:1px solid #4a4a4a" />

## Guardrail

Acquisizione dei dati nel Customer Journey Analytics:

* Assimilazione dati al lago: API ~ 7 GB/ora, connettore sorgente ~ 200 GB/ora, streaming al lago ~ 15 minuti, connettore sorgente Analytics al lago ~ 45 minuti.
* Dopo la pubblicazione dei dati sul data lake, l&#39;elaborazione in Customer Journey Analytics può richiedere fino a 90 minuti.

## Passaggi di implementazione

1. Configura set di dati e schemi.
1. Inserire dati in Platform.
I dati devono essere acquisiti in Platform prima dell’inserimento nel Customer Journey Analytics.
1. Analizza i set di dati evento cross-channel.
I set di dati analizzati nell’unione devono avere un ID comune dello spazio dei nomi o devono essere reimpostati tramite la funzionalità di unione dei Customer Journey Analytics basata sui campi. 

   >[!NOTE]
   >
   >Al momento, Customer Journey Analytics non utilizza i servizi Profilo di Experience Platform o Identity per l’unione.

1. Esegui qualsiasi preparazione di dati personalizzati o utilizza l’unione di identità basata su campi sui dati per garantire una chiave comune tra i set di dati delle serie temporali da acquisire nel Customer Journey Analytics.
1. Fornisci un ID primario per i dati di ricerca, che possono unirsi a un campo nei dati dell’evento. Conta come righe nella licenza.
1. Imposta lo stesso ID principale sui dati del profilo come ID principale dei dati dell’evento.
1. Configura una connessione dati per l’acquisizione di dati da Experience Platform a Customer Journey Analytics. Dopo l&#39;atterraggio dei dati nel lago dati, si trasforma in Customer Journey Analytics entro 90 minuti.
1. Configura una visualizzazione dati sulla connessione per selezionare le dimensioni e le metriche specifiche da includere nella visualizzazione. Le impostazioni di attribuzione e allocazione sono configurate anche nella visualizzazione dati. Queste impostazioni vengono calcolate al momento del rapporto.
1. Crea un progetto per configurare dashboard e rapporti in Analysis Workspace.

## Considerazioni sull’implementazione

### Considerazioni sull’unione delle identità

* I dati della serie temporale da separare devono avere lo stesso spazio dei nomi id su ogni record. Per collegare i dati del call center ai dati dei dispositivi anonimi, l’ID digitale deve essere associato all’ID chiamante. Questa associazione può avvenire attraverso diversi possibili meccanismi:
   * Il numero di chiamata è un numero di chiamata univoco per quel visitatore per quel momento, insieme a una tabella di ricerca per tenere traccia della relazione.
   * Richiedi all&#39;utente di eseguire l&#39;autenticazione prima di richiedere il supporto e di collegare questa autenticazione a un identificatore determinato dall&#39;agente di chiamata (ad esempio, numero di telefono o e-mail).
   * Utilizza un partner di onboarding per aiutare a digitare identificatori di dispositivo online con identificatori noti associati alla richiesta di supporto.
* Il processo di unione di diversi set di dati richiede una chiave primaria comune per la persona/entità nei set di dati.
* Le unioni basate su chiave secondarie non sono attualmente supportate.
* Il processo di unione delle identità basato sui campi consente di reinserire le identità nelle righe in base ai record ID transitori successivi, ad esempio un ID di autenticazione. Questo processo consente di risolvere record diversi a un singolo ID per l&#39;analisi a livello di persona anziché a livello di dispositivo o cookie.
* Le cuciture succedono una volta alla settimana, con ripetizione dopo il punto.

## Domande frequenti

* Quali sono gli impatti a valle dei modelli di dati in Customer Journey Analytics?

   Gli oggetti e gli attributi dello stesso campo XDM si uniscono in una dimensione del Customer Journey Analytics. Per unire più attributi da diversi set di dati alla stessa dimensione CJA, i set di dati devono fare riferimento allo stesso campo o schema XDM.

## Documentazione correlata

* [Descrizione prodotto Customer Journey Analytics](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics.html)
* [Documentazione del Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics.html)
* [Esercitazioni sul Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html)
