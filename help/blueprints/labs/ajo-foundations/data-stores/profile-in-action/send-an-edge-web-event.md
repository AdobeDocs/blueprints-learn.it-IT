---
title: Inviare un evento web Edge
description: Scopri come inviare un evento web simulato ad Adobe Edge Network tramite una chiamata API Postman utilizzando il tuo ID dello stream di dati.
doc-type: article
solution: Experience Platform
exl-id: 0823bcf7-35d9-492e-ad8d-3e8327f77dd8
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---


# Inviare un evento web Edge

## Finalità di apprendimento

Invia un evento web simulato ad Adobe Edge Network utilizzando l’API.

Per simulare una pagina web caricata e inviata all’Edge di AEP, invia una chiamata Postman al flusso di dati creato.

Questo invia un evento senza token OAuth.  Assicurati di avere Postman aperto sul computer per eseguire questo laboratorio.

>[!NOTE]
>
>Poiché non trasmetti un token autenticato, non recupererai alcun attributo.

## Aspettative del laboratorio

1. Evento esperienza per accedere a Edge
1. Configurazione dello stream di dati
1. Configurazione dello stream di dati per utilizzare il servizio AEP
   1. Pubblico Edge da eseguire
   2. Invia evento all&#39;hub
1. Risposta di Postman per includere il pubblico di Edge (ma nessun attributo)
1. Archivio profili per ricevere un evento e aggiungere un frammento di profilo di evento
1. Archivio identità per aggiungere una relazione
1. Set di dati da ricevere e archiviare nel Data Lake



## Aggiorna variabile di ambiente Postman

Prima di poter eseguire la richiesta API è necessario aggiungere l’ID dello stream di dati all’ambiente delle variabili di Postman. Inizia raccogliendo i seguenti valori:

### Raccogliere l’ID dello stream di dati

1. Dovresti avere già l&#39;**ID Datastream**

>[!NOTE]
>
>**Se hai perso l&#39;ID Datastream**
>
>1. Nella barra a sinistra, fai clic su **Flussi di dati** (sotto l&#39;intestazione Raccolta dati)
>2. Seleziona lo stream di dati e copia il valore **ID dello stream di dati**
>
>![Elenco di flussi di dati che mostra l&#39;ID dello stream di dati da copiare](assets/send-an-edge-web-event-gather-datastream-id.png)



### Passa alla chiamata

1. **Barra laterale sinistra Postman** -> `Collections`
1. **Raccolta** -> `AJO Bootcamp (Labs)`
1. **Cartella** -> `Profile & Journey Labs`
1. **Richiesta API** -> `Create Web Event`

![Barra laterale di Postman per passare alla richiesta Crea evento web](assets/send-an-edge-web-event-postman-create-web-event-request.png)

### Aggiorna variabile DATASTREAM\_CONFIG

1. Fai clic su **Variabili nella richiesta** in alto a destra

   ![Variabili nella richiesta nella barra degli strumenti di Postman](assets/send-an-edge-web-event-click-variables-in-request.png)

2. Aggiorna **DATASTREAM_CONFIG** **Value** con **ID datastream** dal primo passaggio della pagina.

   ![Variabile DATASTREAM_CONFIG aggiornata con ID datastream](assets/send-an-edge-web-event-update-datastream-config-variable.png)

3. **Salva** il tuo aggiornamento (ctrl+s o comando+s)
4. Fai clic su &#39;**X**&#39; nell&#39;angolo superiore destro della barra laterale dell&#39;ambiente per chiudere la barra laterale

   ![Chiusura della barra laterale dell&#39;ambiente Postman dopo il salvataggio](assets/send-an-edge-web-event-close-environment-sidebar.png)

5. La richiesta **Crea evento Web** è ora pronta per l&#39;invio poiché tutte le variabili sono ora blu e hanno un valore nell&#39;ambiente.

![Crea richiesta evento Web con tutte le variabili popolate](assets/send-an-edge-web-event-request-ready-to-send.png)

## Eseguire l’API

Eseguire la richiesta facendo clic sul pulsante **Invia**.

La risposta si presenta così:

![Esempio di risposta OK 200 dalla richiesta Crea evento web](assets/send-an-edge-web-event-api-response-example.png)

Quello che vedete tornare nella risposta sono questi aspetti fondamentali:

- Una risposta 200 OK indica che i dati sono stati inviati e accettati correttamente da Edge Network

## Riassunto

L&#39;evento è stato inviato e accettato correttamente da Edge Network
