---
title: Raccolta di dati per l’inoltro di eventi a più sandbox
description: Scopri come i dati raccolti tramite Experience Platform Web SDK e Mobile SDK possono essere configurati in modo da raccogliere un singolo evento e inoltrarlo a più sandbox Experience Platform.
solution: Data Collection
kt: 7202
exl-id: ecc94fc8-9fad-4b88-a153-3d0fc00d8d58
source-git-commit: 72eb4e2ff276279a2fc88ead0b17d77cc8e99b97
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 55%

---

# Raccolta di dati per l’inoltro di eventi a più sandbox

Questo blueprint mostra come configurare i dati raccolti con [!DNL Experience Platform] Web e Mobile SDK per raccogliere un singolo evento e inoltrarlo a più sandbox AEP. Questo blueprint è specifico per la raccolta dati per più sandbox mediante le funzioni di [!UICONTROL inoltro eventi].

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

[!UICONTROL L&#39;inoltro degli eventi] non è considerato compatibile con HIPAA e non deve essere utilizzato nei casi di utilizzo HIPAA in cui vengono raccolti dati HIPAA.

Tuttavia, l&#39;infrastruttura utilizzata per [!UICONTROL Inoltro eventi] è considerata compatibile con HIPAA ed è a esclusiva discrezione del cliente. La proprietà Tag per l’[!UICONTROL inoltro eventi] si trova nel sistema di [!UICONTROL inoltro eventi]; tuttavia, l’intero payload dei dati raccolti viene inviato al sistema di [!UICONTROL inoltro eventi] per l’elaborazione. Questo processo crea [!UICONTROL Inoltro eventi] relativo ai casi d&#39;uso HIPAA. Con l&#39;intero payload inviato al sistema [!UICONTROL Inoltro eventi], questo processo includerebbe eventuali valori HIPAA. Anche se le regole di [!UICONTROL Inoltro eventi] filtrano tali dati prima di inviarli alla destinazione, tali dati HIPAA vengono comunque spediti a un&#39;infrastruttura non compatibile con HIPAA. Tuttavia, i dati di payload non vengono mai memorizzati e sono semplicemente un pass-through.

### Diversi stream di dati ed endpoint di streaming

Poiché i dati scorrono attraverso gli stream di dati da [!DNL Platform Edge Network], quando si utilizza [!UICONTROL Inoltro eventi] a un&#39;altra sandbox di AEP, è necessario non utilizzare mai lo stesso stream di dati o lo stesso endpoint di streaming dello stream di dati che crea la raccolta originale. Questo può avere un effetto dannoso sull’istanza AEP e può potenzialmente attivare una situazione DoS.

### Stima dei volumi di traffico

I volumi di traffico devono essere verificati per ogni caso d’uso. Volumi elevati, infatti, potrebbero causare una situazione di limitazione; se questo si verifica, il cliente riceve una notifica.

## Architettura

![ [!UICONTROL Inoltro eventi per più sandbox]](assets/multi-sandbox-data-collection.png)

1. Per utilizzare [!UICONTROL Inoltro eventi] è necessario raccogliere e inviare dati evento a [!DNL Platform Edge Network]. È possibile utilizzare i tag Adobe per il lato client o [!DNL Platform Edge Network Server API] per la raccolta dati server-to-server.

   [!DNL Platform Edge Network API] può fornire una funzionalità di raccolta da server a server. Ciò richiede tuttavia un diverso modello di programmazione da implementare. Consulta [Panoramica di Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=it).

1. I payload raccolti vengono inviati dall&#39;implementazione dei tag a [!DNL Platform Edge Network] al servizio [!UICONTROL Inoltro eventi] ed elaborati dai propri [!UICONTROL Elementi dati], [!UICONTROL Regole] e [!UICONTROL Azioni]. Per ulteriori informazioni sulle differenze, vedere [Tag e [!UICONTROL Inoltro eventi]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=it#differences-from-tags).

1. È inoltre necessaria una proprietà [!UICONTROL Inoltro eventi] per ricevere i dati dell&#39;evento raccolti da [!DNL Platform Edge Network], sia che tali dati dell&#39;evento siano stati inviati a [!DNL Platform Edge Network] da un&#39;implementazione di Tag distribuita o da un insieme server-to-server.

   Gli autori definiscono gli elementi dati, le regole e le azioni da utilizzare per arricchire i dati evento prima di inoltrarli alla seconda sandbox. Per strutturare i dati da acquisire nella sandbox, puoi utilizzare un elemento dati [!DNL JavaScript] con codice personalizzato. Questo, insieme alle funzionalità di Platform per la preparazione dei dati, ti offrirà diverse opzioni per gestire la struttura dei dati.

1. Attualmente, è necessario utilizzare l’[!UICONTROL estensione Adobe Cloud Connector] all’interno della proprietà di [!UICONTROL inoltro eventi]. Dopo che le regole elaborano o arricchiscono i dati dell&#39;evento, il [!UICONTROL connettore cloud] viene utilizzato in una chiamata di recupero configurata per un POST, inviando il payload alla seconda sandbox.

1. Per la seconda sandbox è necessario un endpoint di streaming per l’acquisizione dei dati. Puoi anche prendere in considerazione le funzionalità di [!UICONTROL Preparazione dati] in AEP per semplificare l&#39;acquisizione e la mappatura dei payload [!UICONTROL Inoltro eventi] in XDM. Consulta la documentazione di AEP su come [creare una connessione streaming API HTTP tramite l’interfaccia utente](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=it)
