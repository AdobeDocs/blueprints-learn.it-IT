---
title: Pubblico e attivazione profilo
description: Offri ai clienti esperienze personalizzate basate su profili e attivate dal pubblico con Real-time Customer Data Platform.
solution: Experience Platform, Real-time Customer Data Platform
kt: null
thumbnail: null
exl-id: eeeb4325-d0e8-4fd8-86ab-0b8afdd0b69f
translation-type: tm+mt
source-git-commit: 5471d9c0f6fdef6fbac72d5d35f32353ea5a5ee8
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 28%

---


# Attivazione di pubblico e profilo

L’attivazione di tipi di pubblico e profili è la chiave per il successo in un mondo di marketing basato sui dati. Tuttavia, molti brand continuano a concentrarsi sull’attivazione in base al canale, che spesso risulta in incoerenza a livello di portata e personalizzazione.

Con l’approccio di priorità al canale, ogni canale funziona come un silo in cui le attività di personalizzazione si rivolgono solo ai clienti che interagiscono con il brand su quel determinato canale. È una modalità che non riflette la realtà: i clienti infatti interagiscono con i brand tramite diversi punti di contatto. L’attivazione di tipi di pubblico e profili consente ai brand di collegare le interazioni dei clienti su più canali, per fornire un profilo e un pubblico centralizzati che possono essere attivati su tutti i canali.

| Blueprint | Descrizione | Applicazioni Experience Cloud |
|---|---|---|
| **[Audience Activation con dati anonimi](anonymous.md)** | <ul><li>Rivolgiti a un pubblico attraverso i vari canali web e pubblicitari sulla base di dati anonimi e comportamentali dei clienti.</li><li>Per una maggiore personalizzazione, puoi integrarli con dati sul pubblico di terze parti.</li></ul> | <ul><li>Adobe Audience Manager</li></ul> |
| **[Audience Activation con dati online/offline](online-offline.md)** | <ul><li>Consente di attivare destinazioni basate su profili note, ad esempio provider di posta elettronica, social network e destinazioni pubblicitarie. </li><li>Utilizza gli attributi e gli eventi offline, come ordini offline, transazioni, CRM o dati fedeltà, insieme al comportamento online per il targeting online e la personalizzazione.</li></ul> | <ul><li>Adobe Experience Platform</li><li> [!UICONTROL Real-time Customer Data Platform]</li><li>Adobe Audience Manager (opzionale)</li></ul> |
| **[Attivazione di tipi di pubblico e profili nelle destinazioni aziendali](enterprise-destinations.md)** | <ul><li>Replica e aggiornamento delle modifiche di profilo e pubblico negli archivi di dati aziendali per casi di attivazione e reporting. </li></ul><ul><li>Avvia un&#39;azione di vendita o supporto al cliente tramite la notifica di un&#39;azione del cliente da [!UICONTROL Real-time Customer Data Platform] ai sistemi e alle applicazioni aziendali.</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL Piattaforma dati cliente in tempo reale]</li><li>Attivazione Experience Platform</li><li>Adobe Audience Manager (opzionale)</li></ul> |
| **[Attivazione di pubblico e profilo con applicazioni Experience Cloud](platform-and-applications.md)** | </ul><li>Gestisci profili e pubblico in Experience Platform e condividerli con Experience Cloud Applications</li><li>Crea e condividi segmenti e approfondimenti di clienti avanzati in Experience Platform e condividili con le applicazioni Experience Cloud</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL Piattaforma dati cliente in tempo reale]</li><li>Attivazione Experience Platform</li><li>Applicazioni Experience Cloud</li></ul> |
| **[Hub delle attività dei clienti](customer-activity.md)** | <ul><li>Contesto del consumatore più approfondito, per le interazioni tramite operatore, come le esperienze di assistenza tecnica o commerciale. Utilizzando la ricerca di profilo nell’Experience Platform, gli agenti possono ricevere più contesto sul consumatore, ad esempio acquisti recenti, interazioni di campagna, proprietà, appartenenze al pubblico e altri attributi e informazioni memorizzati nel profilo del cliente in tempo reale.</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |



## Guardrail per Blueprint di attivazione del pubblico e del profilo

* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)


### Attivazione di attributi e identità

* [!UICONTROL Real-time Customer Data ] Platform può attivare le iscrizioni al pubblico e le modifiche di attributi e identità che si verificano per i profili che sono membri di segmenti selezionati per l’attivazione. Se l’obiettivo è quello di attivare attributi o identità, devi definire un segmento globale che includa tutti i profili a cui vengono inviati gli aggiornamenti di attributi e identità. A questo punto, puoi selezionare il segmento e gli attributi desiderati da attivare come parte della configurazione di destinazione.
* Le destinazioni batch non supportano l’attivazione di eventi di modifica solo attributi. È possibile inviare iscrizioni di pubblico complete o incrementali insieme agli attributi selezionati per l’attivazione, ma non è possibile attivare eventi di modifica di solo attributi tramite destinazioni batch.

### Attivazione di segmenti batch nelle destinazioni di streaming

* È supportata l’attivazione dei segmenti in batch per le destinazioni in streaming. I processi dei segmenti in batch inseriscono i messaggi nella pipeline una volta che il processo del segmento è stato completato per l’attivazione in streaming

### Attivazione di segmenti in streaming su destinazioni batch

* È supportata l’attivazione in streaming dei segmenti nelle destinazioni batch. La pianificazione della destinazione batch esporta le appartenenze dei segmenti di profilo in base alla pianificazione della destinazione batch. Ciò include sia le appartenenze ai segmenti determinate tramite i metodi di streaming che i metodi batch.

### Attivazione di eventi di esperienza

* L’attivazione di eventi di esperienza non elaborati non è supportata. Per attivarsi in base agli eventi di esperienza, è necessario creare un segmento con le regole necessarie che includono o escludono la logica dell’evento di esperienza. Questo crea un segmento definito rispetto agli eventi di esperienza e l’appartenenza al segmento può essere attivata come proxy per l’attivazione di eventi di esperienza non elaborati. Considera anche l’utilizzo di [!UICONTROL Launch Server Side] per attivare eventi di esperienza non elaborati raccolti tramite SDK.


## Articoli di blog correlati

* [[!DNL Blueprints for Audience Activation in Adobe Experience Platform]](https://medium.com/adobetech/a-blueprint-for-audience-activation-in-adobe-experience-platform-b2b30fae90fd)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
