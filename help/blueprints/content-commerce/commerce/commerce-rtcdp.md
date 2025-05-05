---
title: Adobe Commerce - Blueprint per RTCDP
description: Integrazione di Adobe Experience Platform con Adobe Commerce per creare una singola vista dei clienti e personalizzare in modo intelligente le esperienze su uno storefront digitale e tra canali diversi.
solution: Real-Time Customer Data Platform, Commerce
exl-id: e2fc5e1c-c865-4c24-9b82-861a34aba487
source-git-commit: 80a4716a7ed64ec30b9c60b3444affc5bd8984e4
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 1%

---

# ADOBE COMMERCE e RTCDP

L&#39;estensione [!DNL Data Connection] consente ai clienti di Adobe Commerce di integrarsi direttamente con Adobe Experience Platform per arricchire il profilo del cliente e personalizzare le esperienze in vetrina digitale e altri canali.

## Funzionalità tecniche abilitate

* Dati della vetrina (lato client, ad esempio aggiunta al carrello, abbandoni del carrello e così via) raccolti e inviati a qualsiasi prodotto Adobe Experience Cloud.
* Stato dell&#39;ordine di back office su qualsiasi prodotto Adobe Experience Cloud
* Gli ordini storici dei back office possono essere inviati a Adobe Experience Platform
* Condividere e personalizzare i tipi di pubblico RTCDP in Adobe Commerce

## Prerequisiti

Per utilizzare l&#39;estensione [!DNL Data Connection], è necessario disporre dei seguenti elementi:

* Adobe Commerce 2.4.4 o versione successiva
* Adobe ID e ID organizzazione
* Adobe Experience Platform/RTCDP
* [Adobe Client Data Layer (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html?lang=it). L’ACDL è necessario per raccogliere i dati dell’evento vetrina.

## Passaggi di onboarding

### Raccolta di dati da Adobe Commerce a Adobe Experience Platform

* [Installa](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/install.html?lang=it) l&#39;estensione [!DNL Data Connection].
* [Accedi](https://helpx.adobe.com/it/manage-account/using/access-adobe-id-account.html) al tuo account Adobe e visualizza per confermare l&#39;ID organizzazione. L’ID organizzazione è l’ID associato alla società di Experience Cloud con provisioning. Questo ID è una stringa alfanumerica composta da 24 caratteri, seguita da (deve includere) @AdobeOrg.
* [Crea o aggiorna](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/update-xdm.html?lang=it) lo schema XDM con gruppi di campi specifici per Commerce.
* [Crea un set di dati](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html?lang=it#create-a-dataset) in base allo schema creato o aggiornato. Questo set di dati conterrà i dati Commerce inviati.
* [Crea un flusso di dati](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=it) e seleziona lo schema XDM che contiene i gruppi di campi specifici di Commerce.
* [Connetti a Servizi Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=it).
* [Connetti a Adobe Experience Platform](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/connect-data.html?lang=it).

### Connettersi alla destinazione Commerce da Adobe Experience Platform per la condivisione del pubblico

Per connettersi alla destinazione Adobe Commerce:

* Nell&#39;interfaccia [Adobe Experience Platform](https://experience.adobe.com/platform/), vai a Destinazioni > Catalogo.
* Seleziona Personalization.
* Seleziona la destinazione Adobe Commerce da evidenziare, quindi fai clic su Configura.
* Segui i passaggi descritti nell&#39;[esercitazione sulla configurazione della destinazione](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/connect-destination.html?lang=it).

## Dati predefiniti

* Eventi Storefront (browser/app)
* Eventi back office
* Dati ordine cronologico

Per l&#39;elenco completo degli eventi supportati, fare riferimento a [Eventi Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/event-forwarding/events.html?lang=it)

## Architettura

<img src="../commerce/assets/commerce_rtcdp.png" alt="Architettura Adobe Commerce RTCDP" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Guide all’implementazione correlate

| Guida | Collegamento |
|:----|:----|
| Connettore piattaforma | [Panoramica del connettore Adobe Commerce Experience Platform](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/overview.html?lang=it) |
| Destinazione Commerce | [Connessione Adobe Commerce in RTCDP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-commerce.html?lang=it) |
| Edge Personalization | [Attiva i tipi di pubblico nelle destinazioni di personalizzazione Edge](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations.html?lang=it) |
