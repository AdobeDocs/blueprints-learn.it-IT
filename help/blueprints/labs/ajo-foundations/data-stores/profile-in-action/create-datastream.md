---
title: Creare un flusso di dati
description: Scopri come creare e configurare un flusso di dati con i servizi Adobe Experience Platform, Offer Decisioning e Journey Optimizer per abilitare l’elaborazione degli eventi di Edge.
doc-type: article
solution: Experience Platform
exl-id: 37873340-476a-4303-886d-de4835bba8df
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# Creare un flusso di dati

## Finalità di apprendimento

Crea e configura un flusso di dati con i servizi richiesti per abilitare l’elaborazione degli eventi di Edge.

Un flusso di dati definisce quali servizi lo utilizzeranno.

- Quando invii dati ad Edge specifichi quale Datastream utilizzare
- I dati inviati a questi flussi di dati possono quindi intervenire in base al servizio configurato
  - Adobe Experience Platform

## Creare un nuovo flusso di dati

1. Nella barra a sinistra sotto **Raccolta dati** fai clic su **Flussi di dati**
1. Quindi fai clic su **Nuovo flusso di dati** per crearne uno

![Elenco flussi di dati con il pulsante Nuovo flusso di dati evidenziato](assets/create-datastream-new-datastream-button.png)

## Configurare lo stream di dati

Configura lo stream di dati con le seguenti informazioni:

1. Nome -> **Datastream SB + \&lt;nome sandbox> (ovvero Datastream SB01)**
1. Schema di mappatura -> **dep: Web**
1. Attiva **su** tutte le opzioni in **Geolocalizzazione e ricerca di rete** per acquisire queste informazioni.
1. Al termine, fai clic sul pulsante **Salva**

>[!WARNING]
>
>Non fare clic su Salva e Aggiungi mappatura.  In caso contrario, è sufficiente annullare l&#39;operazione

![Modulo di configurazione dello stream di dati con nome e campi dello schema di mappatura](assets/create-datastream-configure-datastream-form.png "Configura lo stream di dati")



Dopo aver salvato lo stream di dati, viene visualizzata la seguente schermata:

![Schermata di conferma dopo il salvataggio del nuovo flusso di dati](assets/create-datastream-created-confirmation.png "Schermata finale creata")

## Aggiungi servizio Adobe Experience Platform

Questo ti consente di inviare i dati all’hub e inviarli a un set di dati per i dati ricevuti da questo flusso di dati.

1. Fai clic sul pulsante blu **Aggiungi servizio** al centro della schermata

   ![Pulsante Aggiungi servizio nella schermata di configurazione dello stream di dati](assets/create-datastream-add-service-button.png)

2. Configura i seguenti elementi:
   - **Servizio** -> `Adobe Experience Platform`
   - **Set di dati evento** -> `dep: Web`
   - **Set di dati profilo** -> `dep: Customer Account`
   - **Seleziona casella di controllo** -> `Offer Decisioning`
   - **Seleziona casella di controllo** -> `Adobe Journey Optimizer`
3. Al termine, fai clic su **Salva**

![Finestra di dialogo per la configurazione del servizio Adobe Experience Platform con campi set di dati evento e profilo](assets/create-datastream-configure-aep-service.png)

Il servizio verrà aggiunto allo stream di dati

![Servizio Adobe Experience Platform aggiunto allo stream di dati](assets/create-datastream-aep-service-added.png "Servizio Adobe Experience Platform aggiunto allo stream di dati")

**Copia** e **salva** il **ID Datastream** nel computer locale (verrà utilizzato in seguito in Postman)

![Campo ID flusso di dati da copiare e salvare per un uso successivo](assets/create-datastream-copy-datastream-id.png)

## Riassunto

Dovresti disporre di un flusso di dati funzionante con il servizio Adobe Experience Platform configurato.
