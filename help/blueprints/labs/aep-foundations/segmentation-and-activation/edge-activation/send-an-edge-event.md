---
hold: true
title: Inviare un evento Edge
description: Invia un evento web non autenticato a Edge tramite Postman e verificane il flusso attraverso l’inoltro degli eventi, l’acquisizione del profilo e la qualificazione del pubblico Edge.
doc-type: article
solution: Experience Platform
exl-id: 8d6e9552-1fa0-4f12-928c-03f836c1652e
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---


# Inviare un evento Edge

Ora che tutto è configurato, invia un evento all’Edge per vedere come funziona.

A questo scopo, utilizza Postman per inviare un evento Web allo stream di dati creato.

Questo invia un evento **senza token OAuth** per simulare una visualizzazione di pagina proveniente dal web e inviata ad Edge.  Assicurati di avere Postman aperto sul computer per eseguire questo laboratorio.

>[!NOTE]
>
>Poiché non trasmetti un token autenticato, non recupererai alcun attributo.

## Aspettative del laboratorio

1. Evento esperienza per accedere a Edge
1. Configurazione dello stream di dati per utilizzare il servizio di inoltro eventi
1. Inoltro eventi per inviare l’evento al webhook
1. Configurazione dello stream di dati per utilizzare il servizio AEP
   1. Pubblico Edge da eseguire
   1. Invia evento all&#39;hub
1. Risposta di Postman per includere il pubblico di Edge (ma nessun attributo)
1. Archivio profili per ricevere un evento e aggiungere un frammento di profilo di evento
1. Archivio identità per aggiungere una relazione
1. Set di dati da ricevere e archiviare nel Data Lake



## Passa alla chiamata

1. **Barra laterale sinistra di Postman** -> Raccolte
1. **Raccolta** -> Campi di avvio dei fondamenti di AEP (Labs)
1. **Cartella** -> Laboratorio profili
1. **Richiesta API** -> Crea evento Web Edge (nessuna autenticazione)

![Navigazione nella barra laterale di Postman per la richiesta API Create Web Event Edge (No Auth) nella cartella Profile Lab](assets/send-an-edge-event-navigate-to-the-postman-call.png)

## Modifica richiesta API

Prima di poter eseguire la richiesta API, devi aggiungere alcune informazioni aggiuntive alla richiesta. Inizia raccogliendo i seguenti valori:

## Raccogliere l’ID dello stream di dati

1. Nella barra a sinistra, fai clic su **Flussi di dati** (sotto l&#39;intestazione Raccolta dati)
1. Seleziona lo stream di dati e copia il valore **ID dello stream di dati**

![Elenco di flussi di dati con il valore ID flusso di dati evidenziato per la copia](assets/send-an-edge-event-gather-datastream-id.png)

## Aggiorna parametro di query Postman

1. Nella richiesta stessa fai clic su **Parametri**
1. Aggiorna **Valore** con l&#39;ID dello stream di dati del passaggio precedente
1. Fai clic sul pulsante **Salva** per salvare l&#39;aggiornamento

![Scheda Parametri di Postman con il valore ID dello stream di dati incollato nel campo Valore](assets/send-an-edge-event-update-datastream-id-param.png "Aggiorna dataStreamId")



Cambia l’e-mail nell’e-mail

![Il corpo della richiesta di Postman mostra il valore dell&#39;e-mail aggiornato all&#39;indirizzo e-mail del tester](assets/send-an-edge-event-change-email-param.png "Modifica l&#39;e-mail all&#39;e-mail")

## Eseguire l’API

Eseguire la richiesta facendo clic sul pulsante **Invia**.

![È in corso la selezione del pulsante Invia di Postman per eseguire la richiesta di Edge per la creazione dell&#39;evento Web](assets/send-an-edge-event-execute-request.png)

Quello che dovresti vedere tornare nella risposta è questo aspetto fondamentale:

- Una risposta 200 OK indica che i dati sono stati inviati e accettati correttamente da Edge Network

>[!NOTE]
>
>Eventuali segmenti in streaming e batch non vengono visualizzati finché non vengono valutati prima nell’hub

## Convalidare l’inoltro degli eventi

Su webhook.site dovresti visualizzare immediatamente lo stesso corpo del payload inviato tramite la richiesta Postman.

![Webhook.site che mostra il payload dell&#39;evento inoltrato ricevuto dall&#39;inoltro eventi](assets/send-an-edge-event-webhook-payload.png)

>[!NOTE]
>
>Osserva che il payload ha aggiunto le informazioni di ricerca geografica richieste durante la configurazione dello stream di dati utilizzato nella configurazione Edge

## Cercare il profilo

In Adobe Experience Platform, cerca il profilo appena inviato dall’evento appena inviato all’Edge Network. Passa a Profili -> Sfoglia per eseguire la ricerca utilizzando le seguenti informazioni:

- Criterio di unione -> Basato su tempo predefinito
- Spazio dei nomi identità -> E-mail
- Valore identità -> edge-email\@dep.com
  - Nota: modificare questa impostazione in modo che corrisponda all&#39;e-mail utilizzata nel passaggio *Aggiorna parametro di query Postman* precedente

1. Fai clic su **Visualizza** per cercare il profilo
1. Fai clic sul **ID profilo** per aprire il profilo

![Risultati della ricerca per la ricerca di profili con il collegamento Visualizza per aprire il profilo corrispondente](assets/send-an-edge-event-lookup-profile.png "Profilo di ricerca")

1. Fai clic su **Eventi** nella barra di navigazione superiore per visualizzare l&#39;evento appena inviato

![Scheda Eventi profilo con l&#39;evento esperienza appena inviato all&#39;Edge](assets/send-an-edge-event-view-profile-event.png "Visualizza l&#39;evento profilo")

1. Verifica che il profilo sia idoneo per i tipi di pubblico esaminando la scheda Appartenenza al pubblico nella navigazione superiore. Dovresti visualizzare quanto segue:

- Qualsiasi evento Edge (entro 15 minuti)
- dep: qualsiasi streaming di eventi (entro un’ora)

![Scheda Iscrizione al pubblico che mostra la qualifica per Qualsiasi evento Edge e dep: Qualsiasi evento Pubblico in streaming](assets/send-an-edge-event-any-event-streaming-within-the-last-hour.png)

## Come interpretare i controlli

1. Verifica la risposta 200 in Postman (payload formattato correttamente)
1. Verifica se il webhook dispone dell’evento (Inoltro eventi configurato correttamente)
1. Verifica se il profilo dispone degli eventi (servizio AEP configurato correttamente, evento ricevuto ed elaborato sull’hub)
1. Controlla se il profilo ha due identità (il grafo delle identità è collegato sull’hub) dopo alcuni minuti
1. Verifica se il profilo è idoneo per i tipi di pubblico (pubblico definito correttamente)
1. Controlla se Data Lake ha l&#39;evento.
