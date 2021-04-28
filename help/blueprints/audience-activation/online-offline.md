---
title: Blueprint Audience Activation online/offline
description: Audience Activation con dati online/offline
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 24b6ffe3021389d33e84688a8f1a90711ca4b772
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 35%

---

# Blueprint Audience Activation online/offline

Per il targeting e la personalizzazione online, utilizza attributi ed eventi offline come dati da ordini, transazioni, sistema di gestione delle relazioni con i clienti o fedeltà, insieme a dati sul comportamento online.

Attiva specifici tipi di pubblico in base a destinazioni note basate sul profilo, come provider di posta elettronica, social network e destinazioni pubblicitarie.

## Casi di utilizzo

* Targeting per tipi di pubblico noti su destinazioni social e pubblicitarie.
* Personalizzazione online con attributi online e offline.
* Attivazione del pubblico su canali noti, come e-mail e SMS.

## Applicazioni

* Adobe Experience Platform
* [!UICONTROL Real-time Customer Data Platform]

## Architettura

<img src="assets/onoff.svg" alt="Architettura di riferimento per la blueprint di Audience Activation online/offline" style="border:1px solid #4a4a4a" />

## Guardrail

* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)

### Guardrail per la valutazione e l’attivazione dei segmenti

| Tipo di segmentazione | Frequenza | Throughput | Latenza (valutazione del segmento) | Latenza (attivazione segmento) | Payload di attivazione |
|---|---|---|---|---|---|
| Segmentazione Edge | La segmentazione Edge è attualmente in versione beta e consente di valutare la segmentazione in tempo reale valida su Experience Platform Edge Network per le decisioni in tempo reale e sulla stessa pagina tramite Adobe Target e Adobe Journey Optimizer. |  | ~100 ms | Disponibile immediatamente per la personalizzazione in Adobe Target, per la ricerca di profili nel profilo Edge e per l’attivazione tramite destinazioni basate su cookie. | Iscrizioni relative al pubblico disponibili in Edge per ricerche di profilo e destinazioni basate su cookie.<br>Le iscrizioni al pubblico e gli attributi del profilo sono disponibili per Adobe Target e Journey Optimizer. |
| Segmentazione in streaming | Ogni volta che un nuovo evento di streaming o un nuovo record viene acquisito nel profilo del cliente in tempo reale e la definizione del segmento è un segmento di streaming valido. <br>Consulta la  [documentazione sulla ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it) segmentazione per informazioni sui criteri dei segmenti in streaming | Fino a 1500 eventi al secondo. | ~ p95 &lt;5min | Destinazioni streaming: Le iscrizioni al pubblico in streaming vengono attivate entro circa 10 minuti o in modalità micro-batch in base ai requisiti della destinazione.<br>Destinazioni pianificate: Le appartenenze al pubblico in streaming vengono attivate in batch in base al tempo di consegna della destinazione pianificato. | Destinazioni streaming: Modifiche all’appartenenza al pubblico, valori di identità e attributi di profilo.<br>Destinazioni pianificate: Modifiche all’appartenenza al pubblico, valori di identità e attributi di profilo. |
| Segmentazione incrementale | Una volta all’ora per i nuovi dati che sono stati acquisiti nel profilo del cliente in tempo reale dall’ultima valutazione del segmento incrementale o batch. |  |  | Destinazioni streaming: Le iscrizioni incrementali al pubblico vengono attivate entro circa 10 minuti o in micro-batch in base ai requisiti della destinazione.<br>Destinazioni pianificate: Le iscrizioni incrementali al pubblico vengono attivate in batch in base al tempo di consegna pianificato per la destinazione. | Destinazioni streaming: Solo modifiche dell&#39;appartenenza al pubblico e valori di identità.<br>Destinazioni pianificate: Modifiche all’appartenenza al pubblico, valori di identità e attributi di profilo. |
| Segmentazione in batch | Una volta al giorno in base a una pianificazione prestabilita del sistema impostata o avviata manualmente tramite API. |  | Circa un&#39;ora per lavoro per un massimo di 10 TB di dimensioni dell&#39;archivio profili, 2 ore per lavoro per 10 TB a 100 TB di dimensioni dell&#39;archivio profili. Le prestazioni del processo del segmento batch dipendono dal numero di profili, dalle dimensioni dei profili e dal numero di segmenti valutati. | Destinazioni streaming: Le iscrizioni a gruppi di pubblico vengono attivate entro circa 10 giorni dal completamento della valutazione della segmentazione o in micro-batch in base ai requisiti della destinazione.<br>Destinazioni pianificate: Le appartenenze a un pubblico batch vengono attivate in base al tempo di consegna della destinazione pianificato. | Destinazioni streaming: Solo modifiche dell&#39;appartenenza al pubblico e valori di identità.<br>Destinazioni pianificate: Modifiche all’appartenenza al pubblico, valori di identità e attributi di profilo. |

### Guardrail per la condivisione del pubblico tra applicazioni diverse

| Integrazioni di applicazioni di pubblico | Frequenza | Throughput/Volume | Latenza (valutazione del segmento) | Latenza (attivazione segmento) |
|---|---|---|---|---|
| Audience Manager di Real-time Customer Data Platform | In base al tipo di segmentazione, consulta la tabella delle protezioni di segmentazione riportata sopra. | In base al tipo di segmentazione, consulta la tabella delle protezioni di segmentazione riportata sopra. | In base al tipo di segmentazione, consulta la tabella delle protezioni di segmentazione riportata sopra. | Entro pochi minuti dal completamento della valutazione del segmento.<br>La sincronizzazione della configurazione iniziale del pubblico tra Real-time Customer Data Platform e Audience Manager richiede circa 4 ore.<br>Tutte le iscrizioni al pubblico realizzate durante il periodo di 4 ore verranno scritte in Audience Manager sul successivo processo di segmentazione del batch come appartenenze al pubblico &quot;esistenti&quot;. |
| Adobe Analytics all’Audience Manager |  | Per impostazione predefinita è possibile condividere un massimo di 75 tipi di pubblico per ciascuna suite di rapporti di Adobe Analytics. Se viene utilizzata una licenza di Audience Manager, non vi è alcun limite al numero di tipi di pubblico che possono essere condivisi tra Adobe Analytics e Adobe Target o Adobe Audience Manager e Adobe Target. |  |  |
| Adobe Analytics alla piattaforma dati cliente in tempo reale | Non disponibile | Non disponibile | Non disponibile | Non disponibile |





## Fasi di implementazione

1. Configurare schemi e set di dati in Experience Platform.
1. Configurare correttamente le identità e i relativi namespace nello schema, affinché i dati acquisiti possano essere uniti in un profilo unificato.
1. Attivare lo schema e i set di dati per il profilo.
1. Acquisire i dati in Platform.
1. Effettuare il provisioning della condivisione di segmenti [!UICONTROL Real-time Customer Data Platform] tra Experience Platform e Audience Manager per i tipi di pubblico definiti in Experience Platform da condividere con Audience Manager.
1. Creare segmenti in Experience Platform, da valutare in batch o in streaming. Il sistema determina automaticamente se un segmento deve essere valutato in batch o in streaming.
1. Configurare le destinazioni per condividere gli attributi del profilo e delle appartenenze al pubblico con le destinazioni desiderate.

## Considerazioni sull’implementazione

* Per condividere i dati del profilo con le destinazioni, è necessario includere il valore di identità specifico utilizzato dalla destinazione nel payload. Qualsiasi identità necessaria per una destinazione di destinazione deve essere assimilata in Platform e configurata come identità per il [!UICONTROL Profilo cliente in tempo reale].

* Per gli scenari di attivazione in cui il pubblico viene condiviso tra Experience Platform e Audience Manager, tutte le identità incluse in [!UICONTROL Real-time Customer Profile] vengono condivise con Audience Manager. Il pubblico di Experience Platform può essere condiviso tramite le destinazioni di Audience Manager se le identità di destinazione richieste sono incluse in [!UICONTROL Real-time Customer Profile], oppure nel caso in cui le identità in [!UICONTROL Real-time Customer Profile] possono essere correlate alle identità di destinazione richieste collegate in Audience Manager.

## Documentazione correlata

* [Descrizione del prodotto Real-time Customer Data Platform](https://helpx.adobe.com/it/legal/product-descriptions/real-time-customer-data-platform.html)
* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Documentazione sulla segmentazione](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=it)

## Video e tutorial correlati

* [Panoramica di Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=it)
* [[!UICONTROL Demo di Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=it)
* [Creare segmenti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=it)
