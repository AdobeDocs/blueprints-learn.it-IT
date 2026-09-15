---
title: Invia evento ordine all'hub
description: Scopri come inviare in streaming un evento di ordine all’hub tramite API, creare un segmento di ordine in streaming, attivarlo in una destinazione e convalidare i risultati del profilo.
doc-type: article
solution: Experience Platform
exl-id: d5de39d7-7340-487a-86fa-504344daeab7
source-git-commit: 8b3391d41cd4a3ea6cb52d5167e627b7f6bd2c6e
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 0%
---

# Invia evento ordine all&#39;hub

>[!IMPORTANT]
>
>Completare l&#39;[installazione di Postman](../../postman-setup/postman-installation.md) prima di avviare questa esercitazione. È inoltre necessario accedere a [webhook.site](https://webhook.site/) e alla destinazione **Webhook DEP streaming** creata nel [caso di utilizzo acquisizione](../use-case-1-acquisition/configure-destinations/setup-streaming-destination.md).

## Streaming su Hub e Edge

Nel caso d’uso #1 abbiamo inviato un evento ad Edge.  In alcuni casi d’uso potrebbe essere presente un sistema back-end che desidera eseguire il streaming in un evento, ma non deve inviarlo all’Edge.  Questa esercitazione mostra come eseguire questa operazione eseguendo lo streaming in un evento Order all’hub.

## Crea un segmento dell’ordine (se non lo hai ancora fatto)

Fai clic su Pubblico nella barra a sinistra, quindi fai clic sul pulsante Crea pubblico in alto a destra.

![Fai clic su Pubblico nella barra a sinistra, quindi fai clic su Crea pubblico](assets/send-order-event-to-hub-click-create-audience-button.png)

Trova la scheda del tipo di evento Ordine inserito e trascinala sull’area di lavoro.

![Trascina la scheda del tipo di evento Ordine inoltrato nell&#39;area di lavoro](assets/send-order-event-to-hub-drag-order-placed-event-onto-canvas.png)

## Aggiorna regole evento

Apporta le seguenti modifiche alle regole dell’evento (potrebbe essere necessario espandere l’evento per visualizzarlo)

1. In Ultimo
1. 15
1. Minutes
1. Modifica alla valutazione in streaming

Salva come **Streaming evento ordine (entro 15 minuti)**



![Salva il pubblico come evento di ordine in streaming (entro 15 minuti) con valutazione in streaming](assets/send-order-event-to-hub-save-streaming-evaluation-rule.png)

## Attiva nella destinazione

Apri il pubblico appena creato se è chiuso.

Fai clic su Attiva nella destinazione



![Fare clic su Attiva nella destinazione per il pubblico dell&#39;ordine](assets/send-order-event-to-hub-click-activate-to-destination.png)

### Destinazione

Seleziona la destinazione di streaming creata in precedenza (webhook DEP streaming)



![Selezionare la destinazione del webhook DEP di streaming](assets/send-order-event-to-hub-select-streaming-destination.png)

### Mappatura

Lascia sola la mappatura e fai clic su Avanti

![Lascia la mappatura invariata e fai clic su Avanti](assets/send-order-event-to-hub-leave-mapping-click-next.png)

Fai clic su Fine

## Apri Postman

Avvia postman sul computer e passa alla seguente chiamata API:

1. **Barra laterale sinistra Postman** —> `Collections`
1. **Raccolta** —> `AEP Foundations Bootcamps (labs)`
1. **Cartella** —> Laboratorio profili
1. **Richiesta API** —> `Create Order Event`

![Apri la richiesta API di creazione evento ordine in Postman](assets/send-order-event-to-hub-create-order-event-api-request.png)


## Modifica richiesta API

Per creare la richiesta API di esempio è necessario compilare i seguenti elementi nel corpo della richiesta API.

Inizia raccogliendo i seguenti valori:

## Trova endpoint di streaming dell’account

1. Passa a **Origini** nella barra a sinistra, quindi fai clic su **Account** nel menu di navigazione in alto
1. Cerca **dep: API HTTP \[raw]**, evidenzia la riga, copia e salva il valore dell&#39;**endpoint di streaming** da qualche parte a cui potrai fare riferimento in seguito

Account  e copia il relativo endpoint di streaming&rbrack;(assets/send-order-event-to-hub-http-api-raw-streaming-endpoint.png &quot;dep: HTTP API \[raw]&quot;)

## Trova ID flusso di dati

1. Trova il record per **dep: Orders (stream)** e fai clic sul collegamento dei flussi di dati
1. Nella barra a destra copia e salva i valori **ID flusso di dati** da qualche parte a cui puoi fare riferimento in seguito

>[!NOTE]
>
>Fare clic in uno spazio vuoto sulla riga.  NON fare clic sui collegamenti blu.

![Copia l&#39;ID del flusso di dati per il flusso di dati Dep: Orders (stream)](assets/send-order-event-to-hub-orders-stream-dataflow-id.png "Flusso di dati Web e ID del set di dati")

## Crea richiesta API finale

Copia i valori salvati nei passaggi precedenti nelle posizioni evidenziate di seguito.

- **Rosso** —> `Streaming Endpoint URL`
- **Verde** —> `Dataflow ID`

Al termine, la richiesta API finale dovrebbe essere simile a questa

>[!CAUTION]
>
>NON ESEGUIRE ANCORA!

![Richiesta API di creazione evento ordine completata con endpoint di streaming e ID flusso di dati inseriti](assets/send-order-event-to-hub-final-order-api-request.png)


## Eseguire l’API

1. Salva la chiamata API facendo clic sul pulsante **Salva**
1. Esegui la richiesta facendo clic sul pulsante **Invia**

In caso di esito positivo, la chiamata dovrebbe dare la seguente risposta...

![Risposta API riuscita dopo l&#39;invio dell&#39;evento ordine](assets/send-order-event-to-hub-successful-api-response.png)

## Convalida

1. Vai sul tuo profilo e controlla il tuo profilo per vedere che l’evento è stato acquisito sul profilo.  Dovrebbe apparire in secondi.
   1. Cercare il profilo utilizzando l’e-mail nell’ordine
1. Convalida che il profilo è qualificato per i segmenti (potrebbero essere necessari alcuni minuti). Dovrebbe apparire in secondi o minuti.
   1. Streaming evento ordine (entro 15 minuti)
1. Controlla il tuo webhook per vedere se la Destinazione ha notificato al webhook un segmento &quot;realizzato&quot;.  Dovrebbe apparire tra 5-10 minuti.
1. Dopo 15-30 minuti, puoi anche controllare il set di dati con quanto segue:
   1. Modifica il nome della tabella seguente con quello della sandbox.  Per trovarlo, vai all&#39;elenco dei set di dati e filtra su &quot;`dest`&quot;, apri il set di dati e copia il nome della tabella nella barra a destra.

```sql
SELECT * FROM profile_export_for_destination_merge_policy_xxx
WHERE extSourceSystemAudit.LASTREFERENCEDDATE >= CURRENT_DATE
AND identitymap['email'][0].ID in ('depche.mode@dep.com')
ORDER BY extSourceSystemAudit.LASTREFERENCEDDATE DESC
LIMIT 10
```
