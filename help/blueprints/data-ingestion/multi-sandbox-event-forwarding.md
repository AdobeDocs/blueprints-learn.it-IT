---
title: Raccolta di dati per l’inoltro di eventi a più sandbox
description: Scopri come i dati raccolti tramite Experience Platform Web SDK e Mobile SDK possono essere configurati in modo da raccogliere un singolo evento e inoltrarlo a più sandbox Experience Platform.
solution: Data Collection
kt: 7202
exl-id: 3d9d312a-50b6-435f-b277-076e0c442a5f
source-git-commit: cb36f47232261d6ddc6659949272c9832baec0da
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 100%

---

# Raccolta di dati per l’inoltro di eventi a più sandbox

Questo blueprint illustra come i dati raccolti tramite Experience Platform Web SDK e Mobile SDK possono essere configurati in modo da raccogliere un singolo evento e inoltrarlo a più sandbox AEP. Questo blueprint è specifico per la raccolta dati per più sandbox mediante le funzioni di [!UICONTROL inoltro eventi].

Oltre a replicare l’evento, le funzioni di [!UICONTROL inoltro eventi] consentono di aggiungere, filtrare o manipolare i dati raccolti originali che soddisfano i requisiti per altre sandbox.

La funzione di [!UICONTROL inoltro eventi] utilizza una proprietà distinta che contiene gli [!UICONTROL elementi dati], le [!UICONTROL regole] e le [!UICONTROL estensioni] necessari per i requisiti dei dati. Con un evento in entrata, la proprietà di [!UICONTROL inoltro eventi] può raccogliere i dati e gestirli in base alle esigenze prima dell’inoltro stesso.

Nella sandbox di destinazione deve essere configurato un endpoint di streaming HTTP, che viene utilizzato dall’estensione Adobe [!UICONTROL Cloud Connector].

## Casi di utilizzo

* Reporting globale dei dati: è utile quando si utilizzano più sandbox per isolare gli ambienti operativi e si desidera consolidare la raccolta dati in un’unica sandbox per generare rapporti su tutte le sandbox. L’instradamento di un evento Experience Edge tramite l’[!UICONTROL inoltro eventi] a una sandbox di reporting consente all’ambiente operativo di ogni sandbox di inviare i dati raccolti in tempo reale a una sandbox di reporting.

* Gestione della raccolta di dati da sandbox diverse in base a diverse regole di dati per l’ambiente operativo di ciascuna sandbox.

## Applicazioni

* [!DNL Experience Platform] Raccolta dati
* [!UICONTROL Inoltro eventi]
* [!UICONTROL Estensione] AEP
* [!UICONTROL Estensione Cloud Connector]

## Considerazioni

Quando si ricorre all’[!UICONTROL inoltro eventi] come approccio per inviare dati a più sandbox, è necessario tenere conto di alcune considerazioni in merito all’architettura della soluzione.

### Nessun dato HIPAA

L’[!UICONTROL inoltro eventi] non è considerato compatibile con HIPAA e non deve essere utilizzato in alcun caso d’uso HIPAA in cui vengano raccolti dati HIPAA. Tuttavia, l’infrastruttura utilizzata per l’[!UICONTROL inoltro eventi] è considerata compatibile con HIPAA ed è a esclusiva discrezione del cliente. La proprietà Tag per l’[!UICONTROL inoltro eventi] si trova nel sistema di [!UICONTROL inoltro eventi]; tuttavia, l’intero payload dei dati raccolti viene inviato al sistema di [!UICONTROL inoltro eventi] per l’elaborazione. È a causa di questo processo che l’[!UICONTROL inoltro eventi] non è indicato per i casi d’uso HIPAA. Quando l’intero payload viene inviato al sistema di [!UICONTROL inoltro eventi], potrebbe includere anche eventuali valori HIPAA. Anche se le regole di [!UICONTROL inoltro eventi] filtrano i dati prima di inviarli alla loro destinazione, tali dati HIPAA vengono comunque inviati a un’infrastruttura non compatibile con HIPAA. Tuttavia, i dati del payload non vengono mai memorizzati: si tratta semplicemente di un passaggio.

### Diversi stream di dati ed endpoint di streaming

Durante il flusso di dati attraverso gli stream di dati dalla [!UICONTROL rete Edge di Platform], quando si utilizza l’[!UICONTROL inoltro eventi] verso un’altra sandbox AEP, è ASSOLUTAMENTE necessario non utilizzare MAI lo stesso stream di dati o endpoint di streaming dello stream di dati da cui viene eseguita la raccolta originale. Questo può avere un effetto dannoso sull’istanza AEP e può potenzialmente attivare una situazione DoS.

### Stima dei volumi di traffico

I volumi di traffico devono essere verificati per ogni caso d’uso. Volumi elevati, infatti, potrebbero causare una situazione di limitazione; se questo si verifica, il cliente riceve una notifica.

## Architettura

![ [!UICONTROL Inoltro eventi per più sandbox]](assets/multi-sandbox-data-collection.png)

1. Per utilizzare l’[!UICONTROL inoltro eventi] è necessario raccogliere e inviare dati evento alla [!UICONTROL rete Edge di Platform]. È possibile utilizzare i tag Adobe lato client o [!UICONTROL Platform Edge Network Server API] per la raccolta dati server-to-server. [!UICONTROL Platform Edge Network API] può fornire una funzionalità di raccolta da server a server. Tuttavia, ciò richiede l’implementazione di un diverso modello di programmazione. Consulta [Panoramica di Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=it).

1. I payload raccolti vengono inviati dall’implementazione dei tag alla [!UICONTROL rete Edge di Platform] al servizio di [!UICONTROL inoltro eventi] e vengono elaborati in base a specifici [!UICONTROL elementi dati], [!UICONTROL regole] e [!UICONTROL azioni]. Scopri di più su [tag e [!UICONTROL inoltro eventi]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=it#differences-from-tags).

1. Inoltre, per ricevere i dati degli eventi raccolti dalla [!UICONTROL rete Edge di Platform], è necessaria una proprietà di [!UICONTROL inoltro eventi]. Questa indica se i dati evento sono stati inviati alla rete Edge di Platform da un’implementazione di tag o da una raccolta da server a server. Gli autori definiscono gli elementi dati, le regole e le azioni da utilizzare per arricchire i dati evento prima di inoltrarli alla seconda sandbox. Per strutturare i dati da acquisire nella sandbox, puoi utilizzare un elemento dati [!DNL JavaScript] con codice personalizzato. Questo, insieme alle funzionalità di Platform per la preparazione dei dati, ti offrirà diverse opzioni per gestire la struttura dei dati.

1. Attualmente, è necessario utilizzare l’[!UICONTROL estensione Adobe Cloud Connector] all’interno della proprietà di [!UICONTROL inoltro eventi]. Una volta che le regole elaborano o arricchiscono i dati evento, Cloud Connector viene utilizzato in una chiamata fetch configurata per un POST che invia il payload alla seconda sandbox

1. Per la seconda sandbox è necessario un endpoint di streaming per l’acquisizione dei dati. Per l’acquisizione e la mappatura dei payload di [!UICONTROL inoltro eventi] in XDM, puoi anche servirti delle funzionalità di preparazione dati disponibili in AEP. Consulta la documentazione di AEP su come [creare una connessione streaming API HTTP tramite l’interfaccia utente](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=it)
