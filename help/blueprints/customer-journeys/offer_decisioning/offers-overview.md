---
title: Panoramica dell’Offer decisioning
description: Offri offerte personalizzate tra i vari percorsi di clienti.
solution: Experience Platform, Journey Optimizer
source-git-commit: 7f566536c4ff5a6af321d60058ad67c13c28bf64
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 2%

---

# Journey Optimizer - Panoramica Offer decisioning

Per ulteriori informazioni su Gestione delle decisioni, consulta la documentazione del prodotto [QUI](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)

Adobe Decision Management è un servizio fornito come parte di Adobe Journey Optimizer. Questo modello delinea i casi d’uso e le capacità tecniche dell’applicazione e fornisce un’analisi approfondita dei vari componenti architettonici e considerazioni che costituiscono un Offer decisioning.

Journey Optimizer viene utilizzato per fornire ai clienti la migliore offerta ed esperienza possibile in tutti i punti di contatto al momento giusto. Ad Offer decisioning, semplifica la personalizzazione con una libreria centrale di offerte di marketing e un motore decisionale che applica regole e vincoli ai profili avanzati e in tempo reale creati da Adobe Experience Platform per aiutarti a inviare ai clienti l’offerta giusta al momento giusto.

La capacità di gestione delle decisioni è costituita da due componenti principali:

* Libreria offerte centralizzata, l’interfaccia in cui puoi creare e gestire i diversi elementi che compongono le offerte, e definirne regole e vincoli.
* Il motore decisionale dell’offerta che sfrutta i dati Adobe Experience Platform e i profili cliente in tempo reale, insieme alla Libreria offerte, per selezionare il momento giusto, i clienti e i canali a cui verranno consegnate le offerte.

<img src="../assets/offers_overview.png" alt="Offer Decisioning" style="width:100%; border:1px solid #4a4a4a" />

La gestione delle decisioni può essere implementata in due modi.

## Gestione delle decisioni sull&#39;hub

La prima è via Adobe Experience Platform hub, un&#39;architettura centrale del data center. Nell’approccio &quot;hub&quot; le offerte vengono eseguite, personalizzate e distribuite con latenza >500 ms. Pertanto, l’architettura dell’hub è più adatta per le esperienze dei clienti che non richiedono latenza inferiore al secondo, ad esempio le decisioni di offerta che vengono fornite per i chioschi o le esperienze assistite dagli agenti, come nei call center o nelle interazioni personali. Anche le offerte inserite in e-mail, messaggi SMS o notifiche push e altre campagne in uscita sono basate sull’approccio hub. Per ulteriori informazioni su Gestione delle decisioni sull&#39;hub, consulta [Gestione delle decisioni sull&#39;hub](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-hub.html?lang=en) blueprint.

### Casi d&#39;uso per la gestione delle decisioni sull&#39;hub

* Offerte personalizzate su chioschi ed esperienze in-store.
* Offerte personalizzate tramite l’esperienza assistita dell’agente, ad esempio ai call center o alle interazioni di vendita.
* Offerte incluse in e-mail, SMS o altre interazioni in uscita.
* Esecuzione di percorsi cross-channel: coerenza delle offerte su web, dispositivi mobili, e-mail e altri canali di interazione tramite Adobe Journey Optimizer.

## Gestione delle decisioni a margine

Il secondo approccio è tramite Experience Edge Network, un’infrastruttura geograficamente distribuita a livello globale per distribuire esperienze di secondo e millisecondi rapidi. L’esperienza del consumatore finale eseguita dall’infrastruttura edge più vicina alla geolocalizzazione dei consumatori per ridurre al minimo la latenza. La funzione di gestione delle decisioni sul server Edge è progettata per offrire ai consumatori esperienze in tempo reale, ad esempio richieste di personalizzazione in entrata per dispositivi web o mobili. Per ulteriori informazioni su Gestione delle decisioni sul server Edge, consulta [Gestione delle decisioni a margine](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-edge.html?lang=en) blueprint.

### Casi d&#39;uso per la gestione delle decisioni a margine

* Personalizzazione online tramite esperienze in entrata web o mobile.
* Esecuzione di percorsi cross-channel: coerenza delle offerte su web, dispositivi mobili, e-mail e altri canali di interazione tramite Adobe Journey Optimizer.

## Documentazione correlata

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html)
* [Gestione delle decisioni Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Descrizione del prodotto Adobe Journey Optimizer](https://helpx.adobe.com/it/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe Offer decisioning Descrizione del prodotto](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)