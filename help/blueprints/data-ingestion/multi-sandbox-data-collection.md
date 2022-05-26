---
title: Blueprint di raccolta dati di inoltro di più eventi sandbox
description: Trasmetti i dati raccolti dagli SDK di Experience Platform a più sandbox utilizzando Event Forwarding
solution: Data Collection
kt: 7202
source-git-commit: 8ea7041103f86f034740f00a607ae36ca0b358cf
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Blueprint di raccolta dati di inoltro di più eventi sandbox

Il Blueprint di raccolta dati di inoltro di eventi con più sandbox mostra come i dati raccolti con Adobe Experience Platform Web e gli SDK mobili possono essere configurati per raccogliere un singolo evento e inoltrare a più Sandbox AEP. Questa blueprint è un caso d’uso specifico che utilizza la funzione di inoltro eventi dei tag di Adobe.

Oltre a replicare l’evento, utilizzando le funzioni Inoltro eventi puoi aggiungere, filtrare o manipolare i dati raccolti originali che soddisfano i requisiti per altre sandbox. Ad esempio, la Sandbox A deve ricevere tutti gli elementi di dati dell’evento e la Sandbox B dovrebbe ricevere solo dati non PII.

Event Forwarding utilizza una proprietà Tag separata che contiene gli elementi dati, le regole e le estensioni necessarie per i requisiti di dati. Con un evento in entrata, la proprietà Event Forwarding può raccogliere i dati e gestirli in base alle esigenze prima dell’inoltro.

Per la sandbox di destinazione è necessario un punto finale di streaming HTTP configurato che verrà utilizzato dall’estensione HTTPS di inoltro eventi.



## Casi di utilizzo

* Reporting globale dei dati : quando si utilizzano più sandbox per isolare gli ambienti operativi e la necessità di consolidare la raccolta dei dati in un unico sandbox per il reporting tra sandbox. Evento Inoltra a una sandbox di reporting consente a ogni ambiente operativo sandbox di inviare dati raccolti in tempo reale a una sandbox di reporting
* Gestisci la raccolta di dati tra le sandbox in base a diverse regole di dati per ogni ambiente operativo sandbox. Ambienti operativi che richiedono il filtraggio di dati sensibili quali il settore sanitario e i servizi finanziari

## Applicazioni

* Raccolta di Adobe Experience Platform

## Architettura

<img src="assets/multi-Sandbox-Data-Collection.svg" alt="Architettura di riferimento per l’inoltro di eventi multisandbox" style="width:90%; border:1px solid #4a4a4a" />

1. Gli autori di tag definiscono sia una proprietà Tag che una proprietà Inoltro eventi. In questo caso, gli autori definiranno gli elementi dati, le regole e le azioni che gestiscono la raccolta dei dati. Tieni presente che il codice della proprietà dei tag viene eseguito sul client e distribuito da un host CDN. Il codice della proprietà Event Forwarding viene eseguito sul server Adobe Edge.

1. I dati raccolti sul client vengono inviati al server Edge. I clienti hanno anche la possibilità di inviare i dati al proprio server prima come metodo di raccolta lato server.
WebSDK può fornire una funzionalità di raccolta da server a server. Ciò richiede tuttavia un diverso modello di programmazione da implementare. Consulta la documentazione **Panoramica API server di rete Edge** di seguito

1. Platform Edge Server riceve i payload di raccolta dati e orchestra il flusso di dati verso i sistemi richiesti, come Target e Analytics.

1. Gli elementi dati della proprietà Event Forwarding vengono utilizzati per accedere ai dati evento in arrivo nel payload. Le regole possono anche essere utilizzate per manipolare i dati dell’evento in base alle esigenze prima dell’inoltro. Come la formattazione dei dati in XDM richiesto per l’acquisizione dei dati in streaming

1. Event Forwarding fornisce l’estensione HTTPS che consente di inoltrare i dati dell’evento a un punto finale HTTPS.

1. La sandbox 2 è configurata con un punto finale in streaming che riceve l’evento inoltrato.

## Documentazione correlata

* [Documentazione sull’inoltro degli eventi](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=it)
* [Video sull’inoltro degli eventi](https://experienceleague.adobe.com/docs/launch-learn/tutorials/server-side/overview.html?lang=it)
* [Lezione sull’inoltro degli eventi](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/event-forwarding/setup-event-forwarding.html?lang=it) nel tutorial su Web SDK
* [Panoramica di Experience Platform WebSDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=it)
* [Panoramica API server di rete Edge](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=it)

## Articoli di blog correlati

* [[!DNL Boosting Website Performance with Adobe Experience Platform Web SDK and Edge Network]](https://medium.com/adobetech/boosting-website-performance-with-adobe-experience-platform-web-sdk-and-edge-network-329fcf70fdf9)
* [[!DNL Solving Implementation Pain Points with Adobe Experience Platform Web SDK and Edge Network]](https://medium.com/adobetech/solving-implementation-pain-points-with-adobe-experience-platform-web-sdk-and-edge-network-880b635e6819)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Adobe Experience Platform Web SDK — Adobe Target]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-adobe-target-9b9f621d271)
* [[!DNL Adobe Experience Platform Web SDK Migration Scenarios for Adobe Analytics]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-migration-scenarios-for-adobe-analytics-91c255ec82b0)
* [[!DNL Unify Your Adobe Experience Platform Services with Adobe Experience Platform Web SDK]](https://medium.com/adobetech/unify-your-adobe-experience-platform-services-with-adobe-experience-platform-web-sdk-75cf6851a9fc)
* [[!DNL Accelerate Your Mobile Application Development with Adobe Experience Platform Mobile SDK and Launch]](https://medium.com/adobetech/accelerate-your-mobile-application-development-with-adobe-experience-platform-mobile-sdk-and-launch-ed023536d611)
* [[!DNL Simplifying Customer Workflows with Adobe Experience Platform Web SDK]](https://medium.com/adobetech/simplifying-customer-workflows-with-adobe-experience-platform-web-sdk-4e54fe134f4a)
