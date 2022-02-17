---
title: Blueprint per attivazione con dati online e offline
description: Attivazione del pubblico con dati online/offline.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
source-git-commit: f1477d39a2b2349708ad74625bab6c5f4012ae1e
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 79%

---

# Blueprint per attivazione con dati online e offline

Per il targeting e la personalizzazione online, utilizza attributi ed eventi offline come dati da ordini, transazioni, sistema di gestione delle relazioni con i clienti o fedeltà, insieme a dati sul comportamento online.

Attiva specifici tipi di pubblico in base a destinazioni note basate sul profilo, come provider di posta elettronica, social network e destinazioni pubblicitarie.

Ulteriori dettagli relativi alle integrazioni tra Experience Platform e le applicazioni Experience Cloud sono disponibili nel [blueprint per l’attivazione in base a pubblico e profili con le applicazioni Experience Cloud](platform-and-applications.md).

## Casi di utilizzo

* Targeting per tipi di pubblico noti su destinazioni social e pubblicitarie.
* Personalizzazione online con attributi online e offline.
* Attivazione del pubblico su canali noti, come e-mail e SMS.

## Applicazioni

* Adobe Experience Platform
* [!UICONTROL Real-time Customer Data Platform]

## Architettura

### Attivazione per destinazioni con dati online e offline

<img src="assets/online_offline_activation.svg" alt="Architettura di riferimento per il blueprint Attivazione del pubblico con dati online/offline" style="width:80%; border:1px solid #4a4a4a" />
<br>

## Guardrail

[Fai riferimento ai guardrail come indicato nella panoramica Attivazione in base a pubblico e profili.](overview.md)

## Fasi di implementazione

1. [Creare schemi](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) per i dati da acquisire.
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) per i dati da acquisire.
1. [Configurare correttamente le identità e i relativi spazi dei nomi](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it) nello schema, affinché i dati acquisiti possano essere uniti in un profilo unificato.
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=it).
1. [Inserire i dati](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=it) in Experience Platform.
1. [Abilitare la condivisione dei segmenti [!UICONTROL Real-time Customer Data Platform]](https://www.adobe.com/go/audiences) tra Experience Platform e Audience Manager per i tipi di pubblico definiti in Experience Platform da condividere con Audience Manager.
1. [Creare segmenti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=it) in Experience Platform. Il sistema determina automaticamente se un segmento deve essere valutato in batch o in streaming.
1. [Configurare le destinazioni](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html?lang=it) per condividere gli attributi del profilo e delle appartenenze al pubblico con le destinazioni desiderate.

## Considerazioni sull’implementazione

* Per condividere i dati del profilo con le destinazioni, è necessario includere il valore di identità specifico utilizzato dalla destinazione nel payload. Tutte le identità necessarie per una destinazione target devono essere inserite in Platform e configurate come identità per [!UICONTROL Real-time Customer Profile].

### Condivisione del pubblico da Real-time Customer Data Platform a Audience Manager

* L’appartenenza a un pubblico viene condivisa direttamente da RTCDP a Audience Manager non appena la valutazione del segmento, in batch o in streaming, viene completata e inserita nel profilo cliente in tempo reale. Se il profilo qualificato contiene informazioni di indirizzamento regionali per i dispositivi del profilo, l’appartenenza al pubblico da RTCDP viene qualificata in modalità streaming nella relativa rete Edge di Audience Manager. Se le informazioni di indirizzamento regionali sono state applicate a un profilo con una marca temporale negli ultimi 14 giorni, verranno valutate in streaming in Audience Manager Edge. Se i profili di RTCDP non contengono informazioni di indirizzamento regionali o se le informazioni di indirizzamento regionale hanno una durata superiore a 14 giorni, le appartenenze al profilo vengono inviate all&#39;ubicazione di hub Audience Manager per la valutazione e l&#39;attivazione basate su batch. I profili idonei per l’attivazione di Edge verranno attivati entro pochi minuti dalla qualifica del segmento da RTCDP, i profili non qualificati per l’attivazione di Edge saranno qualificati nell’hub di Audience Manager e potrebbero avere un intervallo di tempo di 12-24 ore per l’elaborazione.

* Le informazioni di indirizzamento regionali su cui è memorizzato il profilo di Audience Manager di Edge possono essere raccolte ad Experience Platform da Audience Manager, Servizio ID visitatore, Analytics, Launch o direttamente dall’SDK per web come set di dati della classe di record di profilo separato utilizzando il gruppo di campi XDM &quot;informazioni sull’area di acquisizione dati&quot;.

* Per le situazioni di attivazione in cui i tipi di pubblico sono condivisi da Experience Platform a Audience Manager, le seguenti identità vengono condivise automaticamente: IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Al momento, gli spazi dei nomi personalizzati non vengono condivisi.

Il pubblico di Experience Platform può essere condiviso tramite le destinazioni di Audience Manager se le identità di destinazione richieste sono incluse in [!UICONTROL Real-time Customer Profile], oppure nel caso in cui le identità in [!UICONTROL Real-time Customer Profile] possono essere correlate alle identità di destinazione richieste collegate in Audience Manager.

## Documentazione correlata

* Descrizione del prodotto [[!UICONTROL Real-time Customer Data Platform]](https://helpx.adobe.com/it/legal/product-descriptions/real-time-customer-data-platform.html)
* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)
* [Documentazione sulla segmentazione](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it)
* [Documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=it)

## Video e tutorial correlati

* Panoramica di [[!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=it)
* [Demo di [!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=it)
* [Creare segmenti](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
