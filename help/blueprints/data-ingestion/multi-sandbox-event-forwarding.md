---
title: Raccolta di dati per l’inoltro di eventi con più sandbox
description: Scopri come configurare i dati raccolti con Experience Platform Web e Mobile SDK per raccogliere un singolo evento e inoltrarli a più sandbox di Experience Platform.
solution: Data Collection
kt: 7202
source-git-commit: e9a9abeaa722bb2f9a232f4e861b1b5eae86edd1
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 4%

---


# Raccolta di dati per l’inoltro di eventi con più sandbox

Questo blueprint mostra come configurare i dati raccolti con Experience Platform Web e Mobile SDK per raccogliere un singolo evento e inoltrarlo a più sandbox di AEP. Questo blueprint è specifico per la raccolta dati multi-sandbox che utilizza [!UICONTROL Inoltro eventi] per raggiungere questo obiettivo.

Oltre a replicare l’evento con [!UICONTROL Inoltro eventi] funzioni, puoi aggiungere, filtrare o manipolare i dati raccolti originali che soddisfano i requisiti di altre sandbox.

[!UICONTROL Inoltro eventi] utilizza una proprietà separata che contiene [!UICONTROL Elementi dati], [!UICONTROL Regole], e [!UICONTROL Estensioni] necessari per soddisfare i requisiti dei dati. Con un evento in arrivo, [!UICONTROL Inoltro eventi] può raccogliere i dati e gestirli in base alle esigenze prima dell’inoltro.

La sandbox di destinazione richiede un endpoint di streaming HTTP configurato, utilizzato dall’Adobe [!UICONTROL Connettore cloud] estensione.

## Casi di utilizzo

* Reporting globale dei dati: quando si utilizzano più sandbox per isolare gli ambienti operativi e la necessità di consolidare la raccolta dati in un’unica sandbox per il reporting tra sandbox diverse. Instradamento di un evento Experience Edge tramite [!UICONTROL Inoltro eventi] in una sandbox di reporting consente a ogni ambiente operativo sandbox di inviare dati raccolti in tempo reale a una sandbox di reporting.

* Gestione della raccolta di dati da sandbox diverse in base a diverse regole di dati per ciascun ambiente operativo sandbox.

## Applicazioni

* [!DNL Experience Platform] Raccolta dati
* [!UICONTROL Inoltro eventi]
* AEP [!UICONTROL Estensione]
* [!UICONTROL Estensione Cloud Connector]

## Considerazioni

Con [!UICONTROL Inoltro eventi] per quanto riguarda l’approccio all’invio di dati a più sandbox, è necessario tenere conto di alcune considerazioni con l’architettura della soluzione.

### Nessun dato HIPAA

[!UICONTROL Inoltro eventi] non è considerato pronto per HIPAA e non deve essere utilizzato in nessun caso di utilizzo HIPAA in cui vengono raccolti dati HIPAA. Tuttavia, l&#39;infrastruttura utilizzata per [!UICONTROL Inoltro eventi] è considerato pronto per HIPAA ed è esclusivamente a discrezione del cliente. Mentre il [!UICONTROL Inoltro eventi] La proprietà Tag risiede in [!UICONTROL Inoltro eventi] sistema, l&#39;intero payload di dati raccolto viene inviato [!UICONTROL Inoltro eventi] sistema di elaborazione. È questo processo che rende [!UICONTROL Inoltro eventi] riguardanti i casi d’uso dell’HIPAA. Con l&#39;intero payload inviato al [!UICONTROL Inoltro eventi] sistema, includerebbe tutti i valori HIPAA. Anche se il [!UICONTROL Inoltro eventi] Le regole filtrano tali dati prima di inviarli alla destinazione, in modo che i dati HIPAA vengano comunque spediti a un&#39;infrastruttura non compatibile con HIPAA. Tuttavia, i dati di payload non vengono mai memorizzati e sono semplicemente un pass-through.

### Flussi di dati e punti finali di streaming diversi

Quando i dati scorrono attraverso gli stream di dati dalla [!UICONTROL Rete Edge di Platform], quando si utilizza [!UICONTROL Inoltro eventi] per un’altra sandbox di AEP, è necessario non utilizzare mai lo stesso flusso di dati o lo stesso punto finale di streaming dello stream di dati che crea la raccolta originale. Questo può essere dannoso per l&#39;istanza AEP e può potenzialmente attivare una situazione DoS.

### Volume di traffico stimato

I volumi di traffico sono necessari per la revisione con ogni caso d’uso. Questo è importante in quanto volumi elevati potrebbero causare una situazione di limitazione e i clienti vengono avvisati se ciò si verifica.

## Architettura

![Multi-sandbox [!UICONTROL Inoltro eventi]](assets/multi-sandbox-data-collection.png)

1. Raccolta e invio di dati evento a [!UICONTROL Rete Edge di Platform] è necessario per utilizzare [!UICONTROL Inoltro eventi]. I clienti possono utilizzare tag Adobe per il lato client o [!UICONTROL API del server di rete Edge di Platform] per la raccolta dati server-to-server. Il [!UICONTROL API di Platform Edge Network] può fornire una funzionalità di raccolta da server a server. Ciò, tuttavia, richiede un diverso modello di programmazione per essere implementato. Fai riferimento a [Panoramica API server di rete Edge](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=en).

1. I payload raccolti vengono inviati dall’implementazione dei tag al [!UICONTROL Rete Edge di Platform] al [!UICONTROL Inoltro eventi] servizio ed elaborato in proprio [!UICONTROL Elementi dati], [!UICONTROL Regole] e [!UICONTROL Azioni]. Ulteriori informazioni sulle differenze tra [Tag e [!UICONTROL Inoltro eventi]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en#differences-from-tags).

1. Un [!UICONTROL Inoltro eventi] è necessaria anche per ricevere i dati evento raccolti da [!UICONTROL Rete Edge di Platform]. Se i dati dell’evento sono stati inviati alla rete Edge di Platform da un’implementazione di Tag implementata o da una raccolta da server a server. Gli autori definiscono gli elementi di dati, le regole e le azioni utilizzati per arricchire i dati dell’evento prima di inoltrarli alla seconda sandbox. Valuta l’utilizzo del codice personalizzato [!DNL JavaScript] elemento dati per strutturare i dati per l’acquisizione sandbox. In combinazione con le funzionalità di preparazione dati di Platform, puoi gestire la struttura dei dati in diverse opzioni.

1. Attualmente, l’utilizzo dell’Adobe [!UICONTROL Estensione Cloud Connector] è richiesto all&#39;interno di [!UICONTROL Inoltro eventi] Proprietà. Una volta che le regole elaborano o arricchiscono i dati dell’evento, il Cloud Connector viene utilizzato all’interno di una chiamata di recupero configurata per un POST che invia il payload alla seconda sandbox

1. Per la seconda sandbox è necessario un endpoint di streaming per l’acquisizione dei dati. Puoi anche prendere in considerazione le funzionalità di preparazione dati in AEP per facilitare l’acquisizione e la mappatura di [!UICONTROL Inoltro eventi] payload a XDM. Consulta la documentazione di AEP Creare un [Connessione streaming API HTTP tramite l’interfaccia utente](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=it)
