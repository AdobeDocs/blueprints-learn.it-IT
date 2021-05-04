---
title: Pubblico e attivazione profilo
description: Offri ai clienti esperienze personalizzate basate su profili e attivate dal pubblico con Real-time Customer Data Platform.
solution: Experience Platform, Real-time Customer Data Platform
kt: null
thumbnail: null
exl-id: eeeb4325-d0e8-4fd8-86ab-0b8afdd0b69f
translation-type: tm+mt
source-git-commit: 58368eb06b9bbd6c332424bdcfa2789dde7d4c2f
workflow-type: tm+mt
source-wordcount: '1201'
ht-degree: 16%

---


# Attivazione di pubblico e profilo

L’attivazione di tipi di pubblico e profili è la chiave per il successo in un mondo di marketing basato sui dati. Tuttavia, molti brand continuano a concentrarsi sull’attivazione in base al canale, che spesso risulta in incoerenza a livello di portata e personalizzazione.

Con l’approccio di priorità al canale, ogni canale funziona come un silo in cui le attività di personalizzazione si rivolgono solo ai clienti che interagiscono con il brand su quel determinato canale. È una modalità che non riflette la realtà: i clienti infatti interagiscono con i brand tramite diversi punti di contatto. L’attivazione di tipi di pubblico e profili consente ai brand di collegare le interazioni dei clienti su più canali, per fornire un profilo e un pubblico centralizzati che possono essere attivati su tutti i canali.

| Blueprint | Descrizione | Applicazioni Experience Cloud |
|---|---|---|
| **[Audience Activation con dati anonimi](anonymous.md)** | <ul><li>Rivolgiti a un pubblico attraverso i vari canali web e pubblicitari sulla base di dati anonimi e comportamentali dei clienti.</li><li>Per una maggiore personalizzazione, puoi integrarli con dati sul pubblico di terze parti.</li></ul> | <ul><li>Adobe Audience Manager</li></ul> |
| **[Audience Activation con dati online/offline](online-offline.md)** | <ul><li>Consente di attivare destinazioni basate su profili note, ad esempio provider di posta elettronica, social network e destinazioni pubblicitarie. </li><li>Utilizza gli attributi e gli eventi offline, come ordini offline, transazioni, CRM o dati fedeltà, insieme al comportamento online per il targeting online e la personalizzazione.</li></ul> | <ul><li>Adobe Experience Platform</li><li> [!UICONTROL Real-time Customer Data Platform]</li><li>Adobe Audience Manager (opzionale)</li></ul> |
| **[Attivazione di tipi di pubblico e profili nelle destinazioni aziendali](enterprise-destinations.md)** | <ul><li>Replica e aggiornamento delle modifiche di profilo e pubblico negli archivi di dati aziendali per casi di attivazione e reporting. </li></ul><ul><li>Avvia un&#39;azione di vendita o supporto al cliente tramite la notifica di un&#39;azione del cliente da [!UICONTROL Real-time Customer Data Platform] ai sistemi e alle applicazioni aziendali.</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL Piattaforma dati cliente in tempo reale]</li><li>Attivazione Experience Platform</li><li>Adobe Audience Manager (opzionale)</li></ul> |
| **[Hub delle attività dei clienti](customer-activity.md)** | <ul><li>Contesto del consumatore più approfondito, per le interazioni tramite operatore, come le esperienze di assistenza tecnica o commerciale. Utilizzando la ricerca di profilo nell’Experience Platform, gli agenti possono ricevere più contesto sul consumatore, ad esempio acquisti recenti, interazioni di campagna, proprietà, appartenenze al pubblico e altri attributi e informazioni memorizzati nel profilo del cliente in tempo reale.</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |

## Guardrail per Blueprint di attivazione del pubblico e del profilo

### Diagramma del Guardrail

<img src="assets/activation_guardrails.svg" alt="Diagramma di Guardrail per le Blueprint di attivazione del pubblico e del profilo" style="border:1px solid #4a4a4a" />

* [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)

### Guardrail per la valutazione e l’attivazione dei segmenti

| Tipo di segmentazione | Casi di utilizzo | Frequenza | Throughput | Latenza (valutazione del segmento) | Latenza (attivazione segmento) | Payload di attivazione |
|--------------------------|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Segmentazione Edge | Personalizzazione web/mobile (stessa pagina/pagina successiva) | La segmentazione dei bordi è attualmente in versione beta e non è ancora disponibile al pubblico. | - | Circa 100 millisecondi | Target e Journey Optimizer:<ul><li>Disponibile immediatamente nella stessa richiesta di personalizzazione.</li></ul><br>Destinazioni basate su cookie:<ul><li>Disponibile per le decisioni relative alla pagina successiva.</li></ul> | Ricerche di profilo Edge (Target e Journey Optimizer):<ul><li>Appartenenze al pubblico</li><li>Attributi del profilo</li></ul><br>Destinazioni basate su cookie:<ul><li>Appartenenze al pubblico</li></ul> |
| Segmentazione in streaming | Marketing basato su trigger (streaming) | Ogni volta che un nuovo evento di streaming o un nuovo record viene acquisito nel profilo del cliente in tempo reale e la definizione del segmento è un segmento di streaming valido. <br>Consulta la documentazione sulla segmentazione per informazioni sulla documentazione  [della segmentazione dei criteri di segmento in streaming](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=it) | Fino a 1500 eventi al secondo. | Circa 5 minuti, p95 | Destinazioni streaming:<ul><li>Circa 1 minuto per Audience Manager e Target</li><li>Circa 10 minuti per destinazioni esterne o micro-batch a seconda della destinazione.</li></ul><br>Destinazioni pianificate:<ul><li>Attivazione a destinazioni esterne in batch in base al tempo di consegna di destinazione pianificato.</li></ul> | Destinazioni streaming: <ul><li>Modifiche all&#39;iscrizione al pubblico</li><li>Valori identità</li><li>Attributi del profilo</li></ul><br>Destinazioni pianificate:<ul><li>Modifiche all&#39;iscrizione al pubblico</li><li>Valori identità</li><li>Attributi del profilo</li></ul> |
| Segmentazione incrementale | <li>Messaggistica in batch<li>Campagne ed esperienze di targeting | Una volta all’ora per i nuovi dati che sono stati acquisiti nel profilo del cliente in tempo reale dall’ultima valutazione del segmento incrementale o batch. | Non applicabile | In base al numero di profili, alle dimensioni dei profili e al numero di segmenti oggetto della valutazione. | Destinazioni streaming:<ul><li>Circa 1 minuto per Audience Manager e Target</li><li>Circa 10 minuti per destinazioni esterne o micro-batch a seconda della destinazione.</li></ul><br>Destinazioni pianificate:<ul><li>Attivazione a destinazioni esterne in batch in base al tempo di consegna di destinazione pianificato.</li></ul> | Destinazioni streaming: <ul><li>Modifiche all&#39;iscrizione al pubblico</li><li>Valori identità</li></ul><br>Destinazioni pianificate:<ul><li>Modifiche all&#39;iscrizione al pubblico</li><li>Valori identità</li><li>Attributi del profilo</li></ul> |
| Segmentazione in batch | <ul><li>Messaggistica in batch</li><li>Campagne ed esperienze di targeting</li></ul> | Una volta al giorno in base a una pianificazione prestabilita del sistema impostata o avviata manualmente tramite API. | Non applicabile | In base al numero di profili, alle dimensioni dei profili e al numero di segmenti oggetto della valutazione.<ul><li>Circa un&#39;ora per lavoro per un massimo di 10 TB di dimensioni dell&#39;archivio profili</li><li>2 ore per lavoro per dimensioni da 10 TB a 100 TB per archivio profili.</li></ul> | Destinazioni streaming:<ul><li>Circa 1 minuto per Audience Manager e Target</li><li>Circa 10 minuti per destinazioni esterne o micro-batch a seconda della destinazione.</li></ul><br>Destinazioni pianificate:<ul><li>Attivazione a destinazioni esterne in batch in base al tempo di consegna di destinazione pianificato.</li></ul> | Destinazioni streaming: <ul><li>Modifiche all&#39;iscrizione al pubblico</li><li>Valori identità</li></ul><br>Destinazioni pianificate:<ul><li>Modifiche all&#39;iscrizione al pubblico</li><li>Valori identità</li><li>Attributi del profilo</li></ul> |

### Guardrail per la condivisione del pubblico tra applicazioni diverse

| Integrazioni di applicazioni di pubblico | Casi d&#39;uso | Frequenza | Throughput/Volume | Latenza (Valutazione segmento) | Latenza (attivazione segmento) |
|-|-|-|-|-|-|-|
| Audience Manager di Real-time Customer Data Platform | Arricchire la pubblicità di terze parti con i tipi di pubblico di profilo noti | In base al tipo di segmentazione - vedi la tabella delle protezioni di segmentazione riportata sopra. | In base al tipo di segmentazione - vedi la tabella delle protezioni di segmentazione riportata sopra. | In base al tipo di segmentazione - vedi la tabella delle protezioni di segmentazione riportata sopra. | <ul><li>Entro pochi minuti dal completamento della valutazione del segmento.</li><li>La sincronizzazione iniziale della configurazione del pubblico tra RTCDP e AAM richiede circa 4 ore.</li><li>Tutte le iscrizioni al pubblico realizzate durante il periodo di 4 ore verranno scritte in AAM sul successivo processo di segmentazione batch come appartenenze al pubblico &quot;esistenti&quot;.</li></ul> |
| Adobe Analytics all’Audience Manager | Arricchire la pubblicità di terze parti con un pubblico basato su comportamenti granulari |  | Per impostazione predefinita è possibile condividere un massimo di 75 tipi di pubblico per ogni suite di rapporti di Adobe Analytics. Se viene utilizzata una licenza di Audience Manager, non vi è alcun limite. |  |  |
| Adobe Analytics alla piattaforma dati cliente in tempo reale | Attualmente non disponibile. | Non attualmente disponibile | Non attualmente disponibile | Non attualmente disponibile | Non attualmente disponibile |


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
