---
title: Blueprint per raccolta dati per l’inoltro di eventi a più sandbox
description: Trasmetti dati raccolti per [!DNL Experience Platform] (AEP) SDK per più sandbox tramite Inoltro eventi
solution: Data Collection
kt: 7202
exl-id: c24a47fe-b3da-4170-9416-74d2b6a18f32
source-git-commit: 72eb4e2ff276279a2fc88ead0b17d77cc8e99b97
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 60%

---

# Blueprint per raccolta dati per l’inoltro di eventi con più sandbox

Il blueprint per la raccolta dati per l’inoltro di eventi con più sandbox mostra come vengono raccolti i dati con Adobe [!DNL Experience Platform] Gli SDK Web e Mobile possono essere configurati per raccogliere un singolo evento e inoltrarlo a più [!DNL Experience Platform] (AEP) sandbox. Questo blueprint è un caso d’uso specifico che utilizza la funzione di inoltro eventi dei tag di Adobe.

Oltre a replicare l’evento, le funzioni di inoltro eventi consentono di aggiungere, filtrare o manipolare i dati raccolti originali che soddisfano i requisiti per altre sandbox. Consideriamo ad esempio che la Sandbox A debba ricevere tutti gli elementi di dati di eventi, mentre la Sandbox B solo i dati non PII.

L’inoltro degli eventi utilizza una proprietà Tag separata che contiene gli elementi dati, le regole e le estensioni necessari per i requisiti dei dati. Con un evento in entrata, la proprietà di inoltro eventi può raccogliere i dati e gestirli in base alle esigenze prima dell’inoltro stesso.

La sandbox di destinazione avrebbe bisogno di un endpoint di streaming HTTP configurato che verrebbe utilizzato dall’estensione HTTPS di inoltro eventi.

## Casi di utilizzo

* Reporting globale dei dati: è utile quando si utilizzano più sandbox per isolare gli ambienti operativi e si desidera consolidare la raccolta dati in un’unica sandbox per generare rapporti su tutte le sandbox. L’inoltro eventi a una sandbox di reporting consente a ogni ambiente operativo sandbox di inviare i dati raccolti in tempo reale a una sandbox di reporting.
* Gestione della raccolta di dati da sandbox diverse in base a diverse regole di dati per ciascun ambiente operativo sandbox. Tali ambienti operativi richiedono il filtraggio di dati sensibili, ad esempio per il settore sanitario e servizi finanziari.

## Applicazioni

* Adobe [!DNL Experience Platform] Raccolta dati

## Architettura

<img src="assets/multi-Sandbox-Data-Collection.svg" alt="Architettura di riferimento per l’inoltro di eventi a più sandbox" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

1. Gli autori dei tag definiscono sia una proprietà Tag che una proprietà di inoltro eventi. In questo caso, gli autori definiscono gli elementi dati, le regole e le azioni che gestiscono la raccolta dati. Tieni presente che il codice della proprietà Tag viene eseguito sul client e distribuito da un host CDN. Il [!UICONTROL Proprietà inoltro eventi] il codice viene eseguito sull&#39;Adobe [!DNL Edge Server].

1. I dati raccolti sul client vengono inviati a [!DNL Edge Network]. I clienti hanno anche la possibilità di inviare prima i dati al proprio server come metodo di raccolta lato server. Web SDK può fornire una funzionalità di raccolta da server a server. Tuttavia, ciò richiede l’implementazione di un diverso modello di programmazione. Consulta la documentazione **[!DNL Edge Network]Panoramica dell’API server** sotto

1. Piattaforma [!DNL Edge Network] riceve i payload di raccolta dei dati e orchestra il flusso di dati verso i sistemi richiesti, come Target e Analytics.

1. Gli elementi dati della proprietà di inoltro eventi vengono utilizzati per accedere ai dati evento in arrivo nel payload. Le regole possono anche essere utilizzate per manipolare i dati evento in base alle esigenze, prima dell’inoltro. Ad esempio, per formattare i dati nell’XDM richiesto per l’acquisizione dei dati in streaming.

1. La funzione di inoltro eventi fornisce l’estensione HTTPS che consente di inoltrare i dati evento a un endpoint HTTPS.

1. La sandbox 2 è configurata con un endpoint di streaming che riceve l’evento inoltrato.

## Documentazione correlata

* [Documentazione sull’inoltro degli eventi](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=it)
* [Video sull’inoltro degli eventi](https://experienceleague.adobe.com/docs/launch-learn/tutorials/server-side/overview.html?lang=it)
* [Lezione sull’inoltro degli eventi](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/event-forwarding/setup-event-forwarding.html?lang=it) nel tutorial su Web SDK
* [[!DNL Experience Platform] Panoramica di Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=it)
* [[!DNL Edge Network] Panoramica dell’API server](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=it)

## Articoli di blog correlati

* [Aumentare le prestazioni del sito web con Adobe [!DNL Experience Platform] Web SDK e [!DNL Edge Network]](https://medium.com/adobetech/boosting-website-performance-with-adobe-experience-platform-web-sdk-and-edge-network-329fcf70fdf9)
* [Risoluzione dei problemi di implementazione con l’Adobe [!DNL Experience Platform] Web SDK e [!DNL Edge Network]](https://medium.com/adobetech/solving-implementation-pain-points-with-adobe-experience-platform-web-sdk-and-edge-network-880b635e6819)
* [Adobe [!DNL Experience Platform] SDK per web per Gestione dell’audience](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [Adobe [!DNL Experience Platform] SDK per web - Adobe Target](https://medium.com/adobetech/adobe-experience-platform-web-sdk-adobe-target-9b9f621d271)
* [Adobe [!DNL Experience Platform] Scenari di migrazione all’SDK per web per Adobe Analytics](https://medium.com/adobetech/adobe-experience-platform-web-sdk-migration-scenarios-for-adobe-analytics-91c255ec82b0)
* [Unificare l’Adobe [!DNL Experience Platform] Servizi con Adobe [!DNL Experience Platform] SDK per web](https://medium.com/adobetech/unify-your-adobe-experience-platform-services-with-adobe-experience-platform-web-sdk-75cf6851a9fc)
* [Accelerare lo sviluppo di applicazioni mobili con Adobe [!DNL Experience Platform] Mobile SDK e Launch](https://medium.com/adobetech/accelerate-your-mobile-application-development-with-adobe-experience-platform-mobile-sdk-and-launch-ed023536d611)
* [Semplificare i flussi di lavoro dei clienti con Adobe Experience Platform Web SDK](https://medium.com/adobetech/simplifying-customer-workflows-with-adobe-experience-platform-web-sdk-4e54fe134f4a)
