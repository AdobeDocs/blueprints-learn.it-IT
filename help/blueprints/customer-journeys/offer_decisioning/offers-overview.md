---
title: Panoramica dell’Offer decisioning
description: Offri offerte personalizzate tra i vari percorsi di clienti.
solution: Experience Platform, Journey Optimizer
exl-id: f6271802-faab-4ffc-92d6-4c4d7d423ed4
source-git-commit: 7dcbf86b362350312a86445bbe7a020f5ccd1752
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 48%

---

# Journey Optimizer - Panoramica Offer decisioning

Per ulteriori informazioni sul servizio Decision Management, consulta la documentazione del prodotto, disponibile [QUI](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=it)

Adobe Decision Management è un servizio fornito come parte di Adobe Journey Optimizer. Questo blueprint riassume i casi di utilizzo e le capacità tecniche dell’applicazione e descrive nel dettaglio i vari componenti dell’architettura di Offer Decisioning e le relative considerazioni.

Journey Optimizer viene utilizzato per fornire ai clienti la migliore offerta ed esperienza possibile in tutti i punti di contatto al momento giusto. Ad Offer decisioning, semplifica la personalizzazione con una libreria centrale di offerte di marketing e un motore decisionale che applica regole e vincoli ai profili avanzati e in tempo reale creati da Adobe Experience Platform per aiutarti a inviare ai clienti l’offerta giusta al momento giusto.

La capacità di gestione delle decisioni è costituita da due componenti principali:

* Libreria offerte centralizzata, l’interfaccia in cui puoi creare e gestire i diversi elementi che compongono le offerte, e definirne regole e vincoli.
* Il motore decisionale dell’offerta che sfrutta i dati Adobe Experience Platform e i profili cliente in tempo reale, insieme alla Libreria offerte, per selezionare il momento giusto, i clienti e i canali a cui verranno consegnate le offerte.

<img src="../assets/offers_overview.png" alt="Offer Decisioning" style="width:100%; border:1px solid #4a4a4a" />

La gestione delle decisioni può essere implementata in due modi, sul bordo o tramite l&#39;hub. Ognuno di questi metodi dispone di un set specifico di interfacce e protocolli per il funzionamento del servizio, come descritto nei rispettivi progetti di seguito indicati. Ulteriori dettagli possono essere ottenuti anche nella documentazione sulla gestione delle decisioni [QUI](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery-api/decisioning-vs-edge-apis.html).

## Gestione delle decisioni sull&#39;hub

Il primo approccio prevede l’utilizzo dell’hub Adobe Experience Platform, un’architettura con un datacenter centrale. Con questo approccio mediante “hub”, le offerte vengono eseguite, personalizzate e distribuite con una latenza >500 ms. Pertanto, l’architettura con hub è più adatta per esperienze del cliente che non richiedono latenze inferiori al secondo, ad esempio per decisioni di offerta destinate a chioschi o esperienze assistite da agenti, come call center o interazioni con persone. Anche le offerte inserite in e-mail, messaggi SMS o notifiche push e altre campagne in uscita sono basate sull’approccio hub. Per ulteriori informazioni su Decision Management tramite hub, consulta il blueprint [Decision Management tramite hub](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-hub.html?lang=it).

* L’idoneità all’offerta può funzionare in base al profilo cliente in tempo reale completo, inclusi tutti gli attributi e gli eventi di esperienza

### Casi d&#39;uso per la gestione delle decisioni sull&#39;hub

* Offerte personalizzate per chioschi ed esperienze in-store.
* Offerte personalizzate tramite esperienze assistite da agenti, come call center o interazioni di vendita.
* Offerte incluse in e-mail, SMS o altre interazioni in uscita.
* Esecuzione di percorsi cross-channel: offerte coerenti su web, dispositivi mobili, e-mail e altri canali di interazione tramite Adobe Journey Optimizer.

### Gestione delle decisioni sulle considerazioni tecniche fondamentali

* Richieste al secondo = 2000.
* Latenza di risposta &lt; 500 ms.
* Accesso a un profilo cliente in tempo reale completo, compresi appartenenze al pubblico, attributi ed eventi di esperienza.

## Gestione delle decisioni a margine

Il secondo approccio prevede l’utilizzo della rete Experience Edge, un’infrastruttura geograficamente distribuita a livello globale per la distribuzione rapida di esperienze con una latenza inferiore al secondo o di millisecondi. Per ridurre al minimo la latenza, l’esperienza del consumatore finale viene eseguita dall’infrastruttura Edge geograficamente più vicina. Il servizio Decision Management sulla rete Edge è progettato per offrire ai consumatori esperienze in tempo reale, ad esempio con richieste di personalizzazione in entrata per web e dispositivi mobili. Per ulteriori informazioni su Decision Management tramite rete Edge, consulta il blueprint [Decision Management sulla rete Edge](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-edge.html?lang=it).

### Casi d&#39;uso per la gestione delle decisioni a margine

* Personalizzazione online tramite esperienze in entrata web o mobile.
* Esecuzione di percorsi cross-channel: offerte coerenti su web, dispositivi mobili, e-mail e altri canali di interazione tramite Adobe Journey Optimizer.

### Gestione delle decisioni sulle considerazioni tecniche di margine

* Richieste al secondo = 5000.
* Latenza di risposta &lt; 250 ms.
* Accesso al profilo in tempo reale edge. Nel profilo saranno disponibili solo i tipi di pubblico e gli attributi di profilo edge proiettati.
* Se nelle esperienze della prima volta è richiesta la personalizzazione, l’hub sarà ideale in quanto è disponibile il profilo completo. Il profilo Edge deve sincronizzarsi dall’hub per la prima esperienza Edge. Pertanto, la prima esperienza dal bordo non includerà i dati del profilo precedentemente caricati sull&#39;hub.

## Documentazione correlata

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=it)
* [Decision Management per Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Descrizione del prodotto Adobe Journey Optimizer](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer.html)
* [Descrizione del prodotto Adobe Offer Decisioning](https://helpx.adobe.com/it/legal/product-descriptions/offer-decisioning-app-service.html)
