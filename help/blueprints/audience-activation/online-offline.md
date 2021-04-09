---
title: Blueprint Audience Activation online/offline
description: Audience Activation online/offline.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 009a55715b832c3167e9a3413ccf89e0493227df
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 0%

---

# Blueprint Audience Activation online/offline

Utilizza gli attributi e gli eventi offline come ordini offline, transazioni, CRM o dati fedeltà, insieme al comportamento online per il targeting online e la personalizzazione.

Attiva i tipi di pubblico in destinazioni basate su profili note come provider di posta elettronica, social network e destinazioni pubblicitarie.

## Casi d&#39;uso

* Targeting del pubblico per tipi di pubblico noti su destinazioni social e pubblicitarie.
* Personalizzazione online con attributi online e offline.
* Attiva i tipi di pubblico in canali noti, ad esempio e-mail e SMS.

## Applicazioni

* Adobe Experience Platform
* [!UICONTROL Piattaforma dati cliente in tempo reale]

## Architettura

<img src="assets/onoff.svg" alt="Architettura di riferimento per la blueprint di Audience Activation online/offline" style="border:1px solid #4a4a4a" />

## Guardrail

* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* I lavori dei segmenti in batch vengono eseguiti una volta al giorno in base alla pianificazione predeterminata. I processi di esportazione del segmento vengono quindi eseguiti prima della consegna di destinazione pianificata. Tieni presente che i processi di segmento batch e i processi di consegna di destinazione vengono eseguiti separatamente. I processi di segmento batch e le prestazioni dei processi di esportazione dipendono dal numero di profili, dalle dimensioni dei profili e dal numero di segmenti valutati.
* I lavori dei segmenti in streaming vengono valutati in minuti dell’arrivo dei dati in streaming al profilo e scrivono immediatamente l’appartenenza al segmento al profilo e inviano un evento per le applicazioni a cui effettuare l’abbonamento.
* L’appartenenza al segmento in streaming viene eseguita immediatamente per le destinazioni di streaming e viene distribuita in eventi di appartenenza a un singolo segmento o in un micro-batch di eventi di profilo multipli a seconda dei pattern di acquisizione della destinazione. Le destinazioni pianificate avviano un processo di esportazione del segmento dal profilo prima della consegna, per tutti i segmenti valutati in streaming che vengono consegnati tramite la distribuzione pianificata di segmenti batch.
* Per condividere ad Audience Manager l&#39;appartenenza al segmento [!UICONTROL Real-time Customer Data Platform], questo accade in pochi minuti per i segmenti in streaming e in pochi minuti al termine della valutazione del segmento batch per la segmentazione batch.
* I segmenti condivisi da Experience Platform a Audience Manager vengono condivisi in pochi minuti dalla realizzazione del segmento, sia tramite il metodo di valutazione in streaming che in batch. Esiste una sincronizzazione iniziale della configurazione del segmento tra Experience Platform e Audience Manager una volta che il segmento viene creato inizialmente, dopo circa 4 ore che le appartenenze al segmento di Experience Platform possono iniziare a essere realizzate nei profili di Audience Manager. L’appartenenza al pubblico realizzata prima della configurazione della condivisione del pubblico di Experience Platform e Audience Manager o prima che i metadati del pubblico vengano sincronizzati da Experience Platform a Audience Manager non verrà realizzata in Audience Manager fino al seguente processo del segmento in cui vengono condivise le appartenenze al segmento &quot;esistenti&quot;.
* I processi di destinazione in batch o in streaming da segmenti batch possono condividere gli aggiornamenti degli attributi di profilo e le appartenenze ai segmenti.
* I lavori di segmentazione in streaming per le destinazioni in streaming condividono solo gli aggiornamenti di appartenenza al segmento.

## Passaggi di implementazione

1. Configura schemi e set di dati in Experience Platform.
1. Configura le identità e gli spazi dei nomi di identità corretti sullo schema per assicurarti che i dati acquisiti possano essere uniti in un profilo unificato.
1. Abilita lo schema e i set di dati per Profilo.
1. Inserire dati in Platform.
1. Effettuare il provisioning della condivisione di segmenti [!UICONTROL Real-time Customer Data Platform] tra Experience Platform e Audience Manager per i tipi di pubblico definiti in Experience Platform da condividere con Audience Manager.
1. Segmenti di authoring in Experience Platform, da valutare in batch o in streaming. Il sistema determina automaticamente se il segmento viene valutato come batch o in streaming.
1. Configura le destinazioni per la condivisione degli attributi di profilo e delle appartenenze al pubblico nelle destinazioni desiderate.

## Considerazioni sull’implementazione

* Per condividere i dati di profilo nelle destinazioni è necessario includere nel payload di destinazione il valore di identità specifico utilizzato dalla destinazione. Qualsiasi identità necessaria per una destinazione di destinazione deve essere assimilata in Platform e configurata come identità per il [!UICONTROL Profilo cliente in tempo reale].

* Per scenari di attivazione in cui i tipi di pubblico sono condivisi da Experience Platform a Audience Manager, tutte le identità incluse nel [!UICONTROL Profilo cliente in tempo reale] vengono condivise in Audience Manager. I tipi di pubblico di Experience Platform possono essere condivisi attraverso destinazioni di Audience Manager quando le identità di destinazione richieste sono incluse nel [!UICONTROL Profilo del cliente in tempo reale], o quando le identità nel [!UICONTROL Profilo del cliente in tempo reale] possono essere correlate alle identità di destinazione richieste collegate in Audience Manager.

## Documentazione correlata

* [[!UICONTROL Descrizione del prodotto Real-time Customer Data ] Platform](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Documentazione sulla segmentazione](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## Video e Tutorials correlati

* [[!UICONTROL Real-time Customer Data ] PlatformView](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo di  [!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Creare segmenti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
