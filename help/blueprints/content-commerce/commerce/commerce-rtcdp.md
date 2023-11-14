---
title: Adobe Commerce - Blueprint per RTCDP
description: Integrazione di Adobe Experience Platform con Adobe Commerce per creare una singola vista dei clienti e personalizzare in modo intelligente le esperienze su uno storefront digitale e tra canali diversi.
solution: Real-Time Customer Data Platform, Commerce
source-git-commit: abb946358ceeee1af427c5b362ed2f48f733a6c9
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# ADOBE COMMERCE e RTCDP

Questa esperienza integrata aiuta i clienti di Adobe Commerce a integrarsi direttamente con Adobe Experience Platform per arricchire il profilo del cliente e personalizzare le esperienze in vetrina digitale e altri canali.

## Funzionalità tecniche abilitate

* Dati di vetrina (lato client) raccolti e inviati a qualsiasi prodotto Adobe Experience Cloud. (aggiungi al carrello, abbandoni del carrello, ecc.)
* Stato dell&#39;ordine di back office su qualsiasi prodotto Adobe Experience Cloud
* Gli ordini storici dei back office possono essere inviati a Adobe Experience Platform
* Condividere e personalizzare i tipi di pubblico RTCDP in Adobe Commerce

## Prerequisiti

Per utilizzare il connettore di Experience Platform, è necessario disporre dei seguenti elementi:

* Adobe Commerce 2.4.4 o versione successiva
* Adobe ID e ID organizzazione
* Adobe Experience Platform/RTCDP
* [Adobe Client Data Layer (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html?lang=en). L’ACDL è necessario per raccogliere i dati dell’evento vetrina.

## Passaggi di onboarding

### Raccolta di dati da Adobe Commerce a Adobe Experience Platform

* [Installa](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/install.html?lang=en) l’estensione del connettore di Experience Platform.
* [Accedi](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) sul tuo account Adobe e visualizza per confermare l’ID organizzazione. L’ID organizzazione è l’ID associato alla società di Experience Cloud con provisioning. Questo ID è una stringa alfanumerica composta da 24 caratteri, seguita da (deve includere) @AdobeOrg.
* [Crea o aggiorna](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/update-xdm.html?lang=en) lo schema XDM con gruppi di campi specifici di Commerce.
* [Creare un set di dati](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html?lang=en#create-a-dataset) in base allo schema creato o aggiornato. Questo set di dati conterrà i dati Commerce inviati.
* [Creare un flusso di dati](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) e seleziona lo schema XDM che contiene i gruppi di campi specifici di Commerce.
* [Connetti a Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en).
* [Connetti a Adobe Experience Platform](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/connect-data.html?lang=en).

### Connettersi alla destinazione Commerce da Adobe Experience Platform per la condivisione del pubblico

Per connettersi alla destinazione Adobe Commerce:

* In [Interfaccia Adobe Experience Platform](https://experience.adobe.com/platform/), vai a Destinazioni > Catalogo.
* Seleziona Personalizzazione.
* Seleziona la destinazione Adobe Commerce da evidenziare, quindi fai clic su Configura.
* Segui i passaggi descritti in [esercitazione sulla configurazione della destinazione](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/connect-destination.html?lang=en).

## Dati predefiniti

* Eventi Storefront(Browser/App)
* Eventi back office
* Dati ordine cronologico

Per l’elenco completo degli eventi supportati, consulta [Eventi Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/event-forwarding/events.html?lang=en)

## Architettura

<img src="../commerce/assets/commerce_rtcdp.png" alt="Architettura Adobe Commerce RTCDP" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Guide all’implementazione correlate

| Guida  | Collegamento |
|:----|:----|
| Connettore piattaforma | [Panoramica del connettore di Experience Platform Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/overview.html?lang=en) |
| Destinazione commerce | [Connessione Adobe Commerce in RTCDP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-commerce.html?lang=en) |
| Personalizzazione Edge | [Attivare i tipi di pubblico per Edge Personalization Destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations.html?lang=en) | |
