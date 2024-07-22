---
title: Real-Time CDP con  [!DNL Campaign] v7 e modello di integrazione Campaign Standard
description: Mostra come Adobe Experience Platform e il suo Real-Time Customer Profile e lo strumento di segmentazione centralizzata possono essere utilizzati con Adobe [!DNL Campaign] per fornire conversazioni personalizzate.
solution: Real-Time Customer Data Platform, [!DNL Campaign]
exl-id: a15e8304-2763-42fc-9978-11f2482ea8b8
source-git-commit: 258aea64f6ff2f620b1adaa0c9ba4b02b47acce9
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 42%

---

# [!DNL Real-Time Customer Data Platform] con pattern di integrazione [!DNL Campaign]

Mostra come l&#39;Adobe [!DNL Experience Platform] e il relativo profilo cliente in tempo reale e strumento di segmentazione centralizzata possono essere utilizzati con l&#39;Adobe [!DNL Campaign] per fornire conversazioni personalizzate.

## Applicazioni

* Adobe [!DNL Experience Platform Real-Time Customer Data Platform]
* Adobe [!DNL Campaign] v7 o [!DNL Campaign Standard]

## Architettura

<img src="assets/rtcdp-campaign-architecture.svg" alt="Architettura di riferimento del blueprint per il modello di integrazione di messaggistica batch e Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Prerequisiti

* Si consiglia di eseguire il provisioning di Experience Platform e [!DNL Campaign] nella stessa organizzazione IMS e di utilizzare Adobe Admin Console per l’accesso degli utenti. I clienti potranno così passare da una soluzione all’altra direttamente dall’interfaccia utente per il marketing.

## Guardrail

Le sezioni seguenti descrivono i guardrail per questa integrazione.

### Adobe [!DNL Campaign]

* Supporta solo distribuzioni di singole unità organizzative Adobe [!DNL Campaign]
* L&#39;Adobe [!DNL Campaign] è l&#39;origine di verità per tutti i profili attivi, il che significa che i profili devono esistere nell&#39;Adobe [!DNL Campaign] e che non è consigliabile creare nuovi profili in base ai segmenti Experience Platform.
* [!DNL Campaign] flussi di lavoro di esportazione da eseguire al massimo ogni 4 ore
* Lo schema e i set di dati XDM per l&#39;Adobe [!DNL Campaign] broadLog, trackingLogs e indirizzi non consegnabili non sono predefiniti e devono essere progettati e generati

### Condivisione di segmenti Real-time Customer Data Platform

* Consulta il connettore di destinazione RTCDP [!DNL Campaign] - [Connessione campagna RTCDP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html?lang=it)

* Vedi [Guardrail predefiniti per [!DNL Real-Time Customer Profile Data] e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)

## Fasi di implementazione

Le sezioni seguenti descrivono i passaggi di implementazione per ciascuna applicazione.

### Adobe Experience Platform

#### Schema/set di dati

1. [Configurare singoli schemi di profilo, di esperienza e di entità multiple](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=it) in Experience Platform, in base ai dati forniti dal cliente
1. Creare schemi di Adobe [!DNL Campaign] per broadLog, trackingLog, indirizzi non recapitabili e preferenze di profilo (facoltativo).
1. [Creare set di dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=it) in Experience Platform per i dati da acquisire.
1. [Aggiungere etichette di utilizzo dati](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=it) ai set di dati in Experience Platform a scopo di governance.
1. [Creare le policy](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=it) che necessarie per applicare la governance alle destinazioni

#### Profilo/identità

1. [Creare namespace specifici per il cliente](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it)
1. [Aggiungere le identità agli schemi](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=it)
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=it)
1. [Impostare i criteri di unione](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=it) per viste diverse del [!UICONTROL profilo cliente in tempo reale] (opzionale)
1. Creazione di segmenti, ad Adobe [!DNL Campaign].

#### Origini/destinazioni

1. [Experience Platform e [!DNL Campaign] Origini e designazioni standard](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html?lang=it)
1. [Experience Platform e [!DNL Campaign] v7 origini e designazioni](https://experienceleague.adobe.com/docs/campaign-classic/using/integrating-with-adobe-experience-cloud/aep-sources-destinations/get-started-sources-destinations.html?lang=it)
1. [Inserire i dati in Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=it) utilizzando API di streaming e connettori di origini.
1. Configurare la destinazione dell&#39;archiviazione BLOB [!DNL Azure] da utilizzare con l&#39;Adobe [!DNL Campaign].

#### Adobe [!DNL Campaign]

1. Configurare gli schemi per il profilo, i dati di ricerca e i relativi dati di personalizzazione della consegna

>[!IMPORTANT]
>
>È fondamentale capire a questo punto quale sia il modello dati all&#39;interno di Experience Platform per i dati di profilo ed evento in modo da sapere quali dati saranno necessari nell&#39;Adobe [!DNL Campaign].

#### Flussi di lavoro per l’importazione

1. Caricare e acquisire dati di profilo semplificati in Adobe [!DNL Campaign] sFTP.
1. Caricare e acquisire i dati di personalizzazione di orchestrazione e messaggistica in Adobe [!DNL Campaign] sFTP.
1. Acquisire segmenti di Experience Platform da BLOB di [!DNL Azure] tramite flussi di lavoro

#### Flussi di lavoro per l’esportazione

1. Invia di nuovo i registri di Adobe [!DNL Campaign] ad Experience Platform tramite flussi di lavoro ogni quattro ore (broadLog, trackingLog, indirizzi non recapitabili).
1. Inviare le preferenze profilo a Experience Platform tramite flussi di lavoro creati dal servizio di consulenza ogni quattro ore (facoltativo)

### Configurazione push per dispositivi mobili

* Due approcci supportati per l’integrazione con dispositivi mobili per le notifiche push:
   * Experience Platform Mobile SDK
   * SDK di [!DNL Campaign] per dispositivi mobili
* Approccio con Experience Platform Mobile SDK:
   * Utilizza Adobe Tags e l&#39;estensione [!DNL Campaign Classic] per configurare la tua integrazione con Experience Platform Mobile SDK
   * È richiesta la conoscenza delle funzioni Tag e Raccolta dati di Adobe.
   * È richiesta esperienza di sviluppo mobile con notifiche push per Android e iOS per: implementazione dell’SDK; integrazione con FCM (Android) e APNS (iOS) per recuperare il token push token; configurazione dell’app per la ricezione delle notifiche push; e gestione delle interazioni push.
* SDK di [!DNL Campaign] per dispositivi mobili
   * Consulta la documentazione di [Campaign Classic SDK](https://developer.adobe.com/client-sdks/solution/adobe-campaign-classic/)

>[!IMPORTANT]
>
>Se distribuisci l&#39;SDK [!DNL Campaign] e lavori con altre applicazioni Experience Cloud, sarà necessario utilizzare l&#39;SDK di Experience Platform Mobile per la raccolta dei dati. Verranno create chiamate lato client duplicate sul dispositivo.

## Documentazione correlata

* [Adobe [!DNL Experience Platform] documentazione](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [[!DNL Campaign Classic] documentazione](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=it)
* [[!DNL Campaign Standard] documentazione](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=it)
* [[!DNL Experience Platform] Documentazione di Launch](https://experienceleague.adobe.com/docs/launch.html?lang=it)
* [[!DNL Experience Platform] Documentazione dell&#39;SDK per dispositivi mobili](https://experienceleague.adobe.com/docs/mobile.html?lang=it)
