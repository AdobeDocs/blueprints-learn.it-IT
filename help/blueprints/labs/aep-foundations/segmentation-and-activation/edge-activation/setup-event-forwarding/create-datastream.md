---
title: Crea stream di dati
description: Crea e configura un flusso di dati con i servizi di inoltro eventi e Adobe Experience Platform per instradare gli eventi edge in ingresso.
doc-type: article
solution: Experience Platform
exl-id: f7ada451-2f87-48f4-8673-7bfa0df9d0d3
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 1%

---


# Crea stream di dati

Un flusso di dati definisce quali servizi lo utilizzeranno.

- Quando invii dati ad Edge specifichi quale Datastream utilizzare
- I dati inviati a questi flussi di dati possono quindi intervenire in base al servizio configurato
  - Inoltro degli eventi
  - Adobe Experience Platform

## Creare un nuovo flusso di dati

1. Nella barra a sinistra sotto **Raccolta dati** fai clic su **Flussi di dati**
1. Quindi fai clic su **Nuovo flusso di dati** per crearne uno

![Elenco flussi di dati con il pulsante Nuovo flusso di dati evidenziato](assets/create-datastream-new-datastream-button.png)

## Configurare lo stream di dati

Configura lo stream di dati con le seguenti informazioni:

1. Nome -> **Datastream SB + \&lt;nome sandbox> (ovvero Datastream SB01)**
1. Schema eventi -> **dep: Web**
1. Attiva **su** tutte le opzioni in **Geolocalizzazione e ricerca di rete**
1. Al termine, fai clic sul pulsante **Salva**

>[!WARNING]
>
>Non fare clic su Salva e Aggiungi mappatura.  In caso di errore, annullare l&#39;operazione

![Modulo di configurazione dello stream di dati con nome, schema eventi e opzioni di ricerca di geolocalizzazione impostati](assets/create-datastream-configure-datastream-form.png "Configura lo stream di dati")



Dopo aver salvato lo stream di dati viene visualizzata la seguente schermata:

![Schermata di conferma visualizzata immediatamente dopo il salvataggio del nuovo flusso di dati](assets/create-datastream-created-confirmation-screen.png "Schermata finale creata")

## Aggiungi servizio di inoltro eventi

Questo consente di utilizzare l’inoltro degli eventi per i dati ricevuti da questo flusso di dati.



1. Fai clic su **Aggiungi servizio**

   ![Pagina dettagli flusso di dati con il pulsante Aggiungi servizio evidenziato](assets/create-datastream-add-service-button.png "Aggiungi servizio")

1. Configura i seguenti elementi:

   - Servizio -> Inoltro eventi
   - Property (Proprietà) -> Seleziona la proprietà creata nel passaggio precedente.  Deve essere denominato nel modo seguente: Proprietà inoltro eventi SB + \&lt;numero sandbox>
   - Ambiente -> Sviluppo

1. Al termine, fai clic su **Salva**

![Configurazione del servizio di inoltro eventi con proprietà e ambiente di sviluppo selezionati](assets/create-datastream-event-forwarding-service-config.png "Schermata di configurazione inoltro eventi")



## Aggiungi servizio Adobe Experience Platform

Questo ti consente di inviare i dati all’hub e inviarli a un set di dati per i dati ricevuti da questo flusso di dati.



1. Fai clic su **Aggiungi servizio**

   ![Pagina dettagli flusso di dati con il pulsante Aggiungi servizio evidenziato per aggiungere il servizio Adobe Experience Platform](assets/create-datastream-add-second-service-button.png "Aggiungi un nuovo servizio")

1. Configura i seguenti elementi:

   - Servizio -> Adobe Experience Platform
   - Set di dati evento -> dep: Web
   - Set di dati profilo -> dep: account cliente
   - Seleziona la casella di controllo -> Segmentazione Edge
   - Seleziona casella di controllo -> Destinazione Personalization

   ![Configurazione del servizio Adobe Experience Platform con set di dati evento, set di dati profilo e caselle di controllo di segmentazione impostate](assets/create-datastream-aep-service-config.png "Configurazione del servizio")

1. Al termine, fare clic su **Salva**.

1. La schermata finale dovrebbe essere simile a quella riportata di seguito, con due servizi presenti. **Copia** e **salva** l&#39;ID **Datastream** nel computer locale (verrà utilizzato in seguito in Postman)

![Configurazione dello stream di dati finale con i servizi di inoltro eventi e Adobe Experience Platform elencati](assets/create-datastream-final-configuration-both-services.png "Configurazione dello stream di dati finale")
