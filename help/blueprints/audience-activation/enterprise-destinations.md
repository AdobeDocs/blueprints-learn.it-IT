---
title: Profilo ed Audience Activation alle destinazioni Enterprise
description: Profilo ed Audience Activation alle destinazioni Enterprise
solution: Experience Platform,Real-time Customer Data Platform,Target,Audience Manager,Analytics,Experience Cloud Services,Data Collection
kt: 7086
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5
translation-type: tm+mt
source-git-commit: 98d44067a1640dc8b695cb0d25f69ec26be647e1
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---

# Scenario sul profilo e sull’Audience Activation alle destinazioni Enterprise

Replica e aggiornamento delle modifiche del profilo negli archivi dati aziendali per casi d’uso relativi all’attivazione e al reporting.

Avviare un&#39;azione di vendita o supporto al cliente tramite la notifica di un&#39;azione del cliente da Real-time Customer Data Platform ai sistemi e alle applicazioni aziendali.

## Casi d&#39;uso

* Attivazione di profili e pubblico nelle destinazioni di archiviazione cloud o di streaming per il tracciamento, l’archiviazione, l’analisi e l’attivazione dei dati e delle informazioni dei clienti.

## Applicazioni

* Attivazione Adobe Experience Platform

## Architettura

<img src="assets/enterprise_destination.svg" alt="Architettura di riferimento per lo scenario di attivazione Enterprise" style="border:1px solid #4a4a4a" />

## Guardrail

[Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

Soglie di latenza e di uscita:

Segmentazione streaming:

* Fino a 5 minuti per la segmentazione in streaming, fino a 1500 eventi al secondo
* Fino a 11 minuti per l&#39;attivazione in streaming

Segmentazione in batch:
Una volta al giorno o avviato manualmente tramite API

* Circa 1 ora per lavoro per un massimo di 10 TB di dimensioni dell&#39;archivio profili
* Circa 2 ore per lavoro per dimensioni da 10 TB a 100 TB di profilo

## Passaggi di implementazione

1. Creare schemi per i dati da acquisire
1. Creare set di dati per l’acquisizione
1. Configura le identità e gli spazi dei nomi di identità corretti sullo schema per assicurarti che i dati acquisiti possano essere uniti in un profilo unificato.
1. Abilita gli schemi e i set di dati per l’elaborazione dei profili.
1. Configurare eventuali origini per l’acquisizione dei dati
1. Segmenti di authoring in Experience Platform, da valutare in batch o in streaming. Il sistema determina automaticamente se il segmento viene valutato come batch o in streaming.
1. Configura le destinazioni per la condivisione degli attributi di profilo e delle appartenenze al pubblico nelle destinazioni desiderate.

## Considerazioni sull’implementazione

Attivazione di attributi e identità

* Real-time Customer Data Platform può attivare sia le appartenenze al pubblico che le modifiche agli attributi e alle identità che si verificano per i profili che sono membri di segmenti selezionati per l’attivazione. Di conseguenza, se il caso d’uso è quello di attivare attributi e/o identità, è necessario definire un segmento globale che includa tutti i profili per i quali verranno inviati gli aggiornamenti di attributi/identità. Una volta installato, il segmento e gli attributi desiderati da attivare possono essere selezionati come parte della configurazione di destinazione.
* Le destinazioni batch non supportano l’attivazione di eventi di modifica solo degli attributi. L’appartenenza al pubblico piena o incrementale può essere inviata insieme agli attributi selezionati per l’attivazione, ma solo gli eventi di modifica dell’attributo non possono essere attivati tramite destinazioni batch.

Attivazione del segmento batch alle destinazioni in streaming

* È supportata l’attivazione dei segmenti in batch per le destinazioni in streaming. I processi dei segmenti in batch inseriscono i messaggi nella pipeline una volta che il processo del segmento è stato completato per l’attivazione in streaming

Attivazione dei segmenti in streaming alle destinazioni in batch

* È supportata l’attivazione dei segmenti in streaming verso la destinazione batch. Il programma di destinazione batch esporta le appartenenze ai segmenti dei profili in base al programma di destinazione batch. Ciò include sia le appartenenze ai segmenti determinate tramite i metodi di streaming che i metodi batch.

Attivazione di eventi esperienza

* L&#39;attivazione di eventi di esperienza non elaborati non è attualmente supportata. Per attivare rispetto agli eventi di esperienza, è necessario creare un segmento con le regole necessarie che includono/escludono la logica dell’evento di esperienza su cui attivare. Questo crea un segmento definito rispetto agli eventi di esperienza e l’appartenenza al segmento può essere attivata come proxy per l’attivazione di eventi di esperienza non elaborati. Valuta anche la possibilità di sfruttare Launch Server Side per l’attivazione di eventi di esperienza non elaborati raccolti tramite SDK.

## Documentazione correlata

* [Descrizione del prodotto Real-time Customer Data Platform](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Documentazione sulla segmentazione](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## Video e Tutorials correlati

* [Panoramica di Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo di Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Creare segmenti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
