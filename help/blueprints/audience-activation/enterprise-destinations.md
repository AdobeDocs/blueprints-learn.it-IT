---
title: Attivazione di tipi di pubblico e profili alla blueprint delle destinazioni Enterprise
description: Attivazione di tipi di pubblico e profili nelle destinazioni aziendali
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: b0664edc3d29d693d33eefc3b3c6da8bf7308224
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---

# Attivazione di tipi di pubblico e profili alla blueprint delle destinazioni Enterprise

Condividi modifiche ed eventi di profilo e pubblico in streaming o in batch da [!UICONTROL Real-time Customer Data Platform] agli archivi dati e alle applicazioni aziendali. Questi eventi di profilo e pubblico possono essere utilizzati per avviare un&#39;azione di vendita o supporto al cliente, ad esempio per dare seguito a un processo di applicazione abbandonato o a una registrazione di un webinar oppure per aggiornare le applicazioni aziendali con gli attributi e le informazioni più recenti del cliente da [!UICONTROL Real-time Customer Data Platform].

## Casi d&#39;uso

* Attivazione di profili e pubblico su destinazioni di archiviazione cloud o di streaming per il tracciamento, l’archiviazione, l’analisi e l’attivazione di dati e informazioni sui clienti.

## Applicazioni

* Attivazione Adobe Experience Platform

## Architettura

<img src="assets/enterprise_destination.svg" alt="Architettura di riferimento per lo scenario di attivazione Enterprise" style="border:1px solid #4a4a4a" />

## Guardrail

[Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

Soglie di latenza e velocità effettiva:

Segmentazione streaming:

* Fino a 5 minuti per la segmentazione in streaming, fino a 1500 eventi al secondo
* Fino a 11 minuti per l&#39;attivazione in streaming

Segmentazione in batch:
Una volta al giorno o avviato manualmente tramite API.

* Circa 1 ora per lavoro per un massimo di 10 TB di dimensioni dell&#39;archivio profili
* Circa 2 ore per lavoro per dimensioni da 10 TB a 100 TB di profilo

## Passaggi di implementazione

1. Creare schemi per i dati da acquisire.
1. Crea set di dati per i dati da acquisire.
1. Configura le identità e gli spazi dei nomi di identità corretti sullo schema per assicurarti che i dati acquisiti possano essere uniti in un profilo unificato.
1. Abilita gli schemi e i set di dati per l’elaborazione dei profili.
1. Configura le origini per l’acquisizione dei dati.
1. Segmenti di authoring in Experience Platform, da valutare in batch o in streaming. Il sistema determina automaticamente se il segmento viene valutato come batch o in streaming.
1. Configura le destinazioni per la condivisione degli attributi di profilo e delle appartenenze al pubblico nelle destinazioni desiderate.

## Considerazioni sull’implementazione

Attivazione di attributi e identità

* [!UICONTROL Real-time Customer Data ] Platform può attivare le iscrizioni al pubblico e le modifiche di attributi e identità che si verificano per i profili che sono membri di segmenti selezionati per l’attivazione. Se l’obiettivo è quello di attivare attributi o identità, devi definire un segmento globale che includa tutti i profili a cui vengono inviati gli aggiornamenti di attributi e identità. A questo punto, puoi selezionare il segmento e gli attributi desiderati da attivare come parte della configurazione di destinazione.
* Le destinazioni batch non supportano l’attivazione di eventi di modifica solo attributi. È possibile inviare iscrizioni di pubblico complete o incrementali insieme agli attributi selezionati per l’attivazione, ma non è possibile attivare eventi di modifica di solo attributi tramite destinazioni batch.

Attivazione di segmenti batch nelle destinazioni di streaming

* È supportata l’attivazione dei segmenti in batch per le destinazioni in streaming. I processi dei segmenti in batch inseriscono i messaggi nella pipeline una volta che il processo del segmento è stato completato per l’attivazione in streaming

Attivazione di segmenti in streaming su destinazioni batch

* È supportata l’attivazione dei segmenti in streaming verso la destinazione batch. La pianificazione della destinazione batch esporta le appartenenze dei segmenti di profilo in base alla pianificazione della destinazione batch. Ciò include sia le appartenenze ai segmenti determinate tramite i metodi di streaming che i metodi batch.

Attivazione di eventi di esperienza

* L’attivazione di eventi di esperienza non elaborati non è supportata. Per attivarsi in base agli eventi di esperienza, è necessario creare un segmento con le regole necessarie che includono o escludono la logica dell’evento di esperienza. Questo crea un segmento definito rispetto agli eventi di esperienza e l’appartenenza al segmento può essere attivata come proxy per l’attivazione di eventi di esperienza non elaborati. Considera anche l’utilizzo di [!UICONTROL Launch Server Side] per attivare eventi di esperienza non elaborati raccolti tramite SDK.

## Documentazione correlata

* [Documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)
* [Panoramica delle destinazioni di archiviazione cloud](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [Destinazione HTTP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [[!UICONTROL Descrizione del prodotto Real-time Customer Data ] Platform](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Documentazione sulla segmentazione](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)

## Video e Tutorials correlati

* [[!UICONTROL Real-time Customer Data ] PlatformView](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo di  [!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Creare segmenti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
