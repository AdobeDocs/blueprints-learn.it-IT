---
title: Eseguire il flusso di lavoro
description: Scopri come eseguire un flusso di lavoro di Campaign orchestrato in modalità di test e risolvere i problemi relativi all’eliminazione di alcuni record da un invio SMS a causa di join di dimensioni di destinazione mancanti.
doc-type: article
solution: Experience Platform
exl-id: c3b35b27-92ae-44ca-a5fb-3f76990f9db4
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 0%

---


# Eseguire il flusso di lavoro

## Obiettivo

Nei passaggi successivi scoprirai come testare il flusso di lavoro e, soprattutto, l’attività SMS utilizzando la modalità di test.



## Verifica flusso di lavoro

1. Al termine, il flusso di lavoro finale si presenterà simile al seguente. Controlla che tutto sia a posto. Vedi:

   ![Area di lavoro del flusso di lavoro finale pronta per il test](assets/run-the-workflow-final-workflow-canvas.png)

2. Se non hai già interrotto il flusso di lavoro, assicurati di farlo ora facendo clic sul pulsante **Interrompi** in alto a destra.

   ![Pulsante Interrompi in alto a destra del flusso di lavoro](assets/run-the-workflow-click-stop-button.png)

   >[!NOTE]
   >
   >Se lo si desidera, è possibile provare a fare clic sul pulsante Riavvia, ma è probabile che venga visualizzato un errore poiché sono state aggiunte attività dopo la creazione del flusso di lavoro e la cache non è più valida.



3. Fai clic sul pulsante **Inizio** per eseguire e verificare l&#39;fine del flusso di lavoro

   ![Pulsante Avvia per eseguire il test del flusso di lavoro](assets/run-the-workflow-click-start-button.png)



4. Controlla i risultati in arrivo nell&#39;attività SMS facendo clic su **Risultato** (sono presenti due risultati, quindi utilizza quello a sinistra come mostrato di seguito) e quindi nella barra a sinistra facendo clic sul pulsante **Anteprima risultati**.

   ![Transizione risultati sinistra selezionata prima dell&#39;attività SMS](assets/run-the-workflow-select-result-transition.png)

   ![Pulsante Anteprima risultati nella barra a destra](assets/run-the-workflow-click-preview-results.png)



5. Sono presenti **33 record** e la dimensione di targeting corrisponde all&#39;ID cliente (la chiave di join per il profilo)

![33 record con dimensione di targeting corrispondente all&#39;ID cliente](assets/run-the-workflow-33-records-customer-id.png)



## Testare l’attività SMS

1. Chiudi la finestra precedente e fai clic sull&#39;**attività SMS**, quindi sul pulsante **Esegui test** nella barra a destra

   ![Esegui il pulsante di test nell&#39;attività SMS](assets/run-the-workflow-click-run-test-sms.png)



2. Quasi immediatamente viene visualizzato un nuovo pulsante con l&#39;etichetta **Visualizza report**.  Fare clic sul pulsante **Visualizza report** per passare alla schermata del report.

   ![Pulsante Visualizza report per il test attività SMS](assets/run-the-workflow-click-view-report.png)

   >[!NOTE]
   >
   >Inizialmente questa schermata non verrà compilata perché l’esecuzione dei test richiede un po’ di tempo. Potrebbe essere necessario aggiornare alcune volte prima di visualizzare i risultati.



3. Quando ottieni risultati, vedi che il target era al 100%!

   ![Risultati invio test SMS con destinazione 100%](assets/run-the-workflow-100-percent-targeted.png)

   *Attendi, un minuto...il risultato in arrivo era di 33 record, quindi dove è andato il 4?*



4. Torna all&#39;area di lavoro del flusso di lavoro e fai clic sulla transizione **Risultato** che entra nell&#39;attività SMS, quindi fai clic su **Anteprima risultati** nella barra a destra.

   ![Revisione dei risultati della transizione dopo il test SMS](assets/run-the-workflow-recheck-transition-results.png)



5. Nella schermata Risultati anteprima scorri fino alla fine della tabella e noterai che **4 record** hanno una **dimensione di targeting vuota**.

![4 record con una dimensione di targeting vuota nella parte inferiore della tabella](assets/run-the-workflow-4-records-missing-dimension.png)



## Spiegazione

Ecco cos&#39;è successo.

- Avevi 33 righe cliente a cui inviare un messaggio SMS
- Dopo la modifica dell&#39;attività dimensione 4 di quelle linee cliente non aveva un conto cliente associato
- L’unione a Real-Time Customer Profile richiede di disporre di un ID cliente e, poiché questi 4 record non contengono alcun nome, non è possibile cercare un profilo o crearne uno nuovo al volo

Risultato —> Campagne orchestrate elimina questi 4 record durante l’esecuzione del messaggio

>[!NOTE]
>
>È in arrivo un miglioramento per affrontare questo problema in due modi:
>
>1. Assicurati che venga creato un registro di esclusione per i record a cui manca una dimensione di targeting al momento dell’invio
>2. Aggiornare l’attività di modifica della dimensione per eseguire un inner join anziché un join esterno che rimuoverebbe questi 4 record in primo piano

>[!TIP]
>
>Congratulazioni! Ora sei ufficialmente certificato per lanciare le tue Orchestrated Campaigns e trasmettere messaggi al mondo—responsabilmente, speriamo. Lanciati sul mercato come una maestosa magia digitale!



## Pubblicazione del flusso di lavoro

Non lo farete in laboratorio, ma per il contesto ecco cosa succede al momento della pubblicazione:

1. Il modulo di pianificazione entra se per la campagna è impostata una pianificazione
1. Le attività Save Audience creano la shell del pubblico in nel Portale pubblico e i profili qualificati iniziano a acquisirli
1. Viene avviata l’esecuzione del messaggio per la prima attività messaggio nel flusso di lavoro
   - Le ricerche di profilo vengono eseguite sullo snapshot del profilo
     - I profili corrispondenti rispettano il consenso trovato sul profilo
     - I profili non corrispondenti vengono creati al volo
   - I registri di consegna vengono creati in `AJO Message Feedback Event Dataset`
