---
title: Blueprint Audience Activation online/offline
description: Audience Activation con dati online/offline
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 009a55715b832c3167e9a3413ccf89e0493227df
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 81%

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
* I processi di segmentazione batch vengono eseguiti una volta al giorno in base alla pianificazione prestabilita. I processi di esportazione dei segmenti vengono quindi eseguiti prima della consegna alla destinazione pianificata. Nota: i processi di segmentazione batch e di consegna alla destinazione vengono eseguiti separatamente. Le prestazioni dei processi di segmentazione batch e di esportazione dipendono dal numero e dalla dimensione dei profili e dal numero di segmenti valutati.
* I processi di segmentazione in streaming vengono valutati entro pochi dall’arrivo dei dati in streaming nel profilo, quindi l’appartenenza del segmento viene immediatamente scritta nel profilo e viene inviato un evento alle applicazioni interessate.
* L’appartenenza al segmento in streaming ha effetto immediatamente per le destinazioni di streaming e viene fornita in eventi di appartenenza a singolo segmento o in micro-batch di più eventi di profilo, a seconda dei pattern di acquisizione della destinazione. Le destinazioni pianificate avviano un processo di esportazione di segmenti dal profilo prima della consegna, per tutti i segmenti valutati in streaming che vengono consegnati tramite la consegna pianificata di segmenti in batch.
* Per condividere ad Audience Manager l&#39;appartenenza al segmento [!UICONTROL Real-time Customer Data Platform], questo accade in pochi minuti per i segmenti in streaming e in pochi minuti al termine della valutazione del segmento batch per la segmentazione batch.
* I segmenti condivisi da Experience Platform con Audience Manager vengono condivisi entro pochi minuti dalla realizzazione del segmento, sia con il metodo di streaming che con la valutazione batch. Esiste una sincronizzazione iniziale della configurazione del segmento tra Experience Platform e Audience Manager una volta che il segmento viene creato inizialmente, dopo circa 4 ore che le appartenenze al segmento di Experience Platform possono iniziare a essere realizzate nei profili di Audience Manager. L’appartenenza al pubblico realizzata prima della configurazione della condivisione di Experience Platform e Audience Manager o prima che i metadati del pubblico vengano sincronizzati tra Experience Platform e Audience Manager, verrà realizzata in Audience Manager solo al successivo processo di segmentazione in cui vengono condivise le appartenenze ai segmenti &quot;esistenti&quot;.
* I processi di destinazione in batch o streaming da processi di segmentazione batch possono condividere gli aggiornamenti degli attributi del profilo e le appartenenze ai segmenti.
* I processi di segmentazione in streaming verso destinazioni streaming condividono solo gli aggiornamenti dell’appartenenza al segmento.

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
* [Documentazione sulla segmentazione](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it)
* [Documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=it)

## Video e tutorial correlati

* [Panoramica di Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=it)
* [[!UICONTROL Demo di Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=it)
* [Creare segmenti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=it)
