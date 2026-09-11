---
hold: true
title: Testare la campagna
description: Scopri come eseguire una campagna orchestrata in modalità di test e capire perché un canale e-mail basato su profilo di AEP genera errori di consegna che un canale basato su relazioni evita.
doc-type: article
solution: Experience Platform
exl-id: e77ae8ab-f18f-4683-8fdd-ba4f4629d96c
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 0%

---


# Testare la campagna

## Obiettivo

Nei passaggi successivi eseguirai la campagna in modalità di test per confermare le funzioni previste per la campagna prima di pubblicarla. In questo caso, la modalità di test non invia effettivamente le e-mail, ma aiuta a verificare l’intero flusso e identificare tempestivamente i problemi.

## Avvia il flusso di lavoro

1. Una volta configurati i due flussi e-mail, la campagna si presenta come segue. Fai clic sul pulsante **Avvia** per eseguire la campagna in **Modalità test**

![Fare clic su Avvia per eseguire la campagna in modalità di test](assets/test-the-campaign-click-start-test-mode.png)

>[!NOTE]
>
>Come accennato nel laboratorio precedente, la modalità di test ti consente di convalidare l’esecuzione della campagna e i risultati delle varie attività. Ogni attività viene eseguita in sequenza fino al raggiungimento della fine del flusso.



&#x200B;2. Viene avviata l’esecuzione di test di tutte le attività della campagna, verifica i risultati

![Esecuzione test delle attività campagna in corso](assets/test-the-campaign-verify-execution-results.png)



## #1 report e-mail

1. Per verificare la consegna di e-mail, fai clic sull&#39;attività **Invia e-mail utilizzando l&#39;attributo di profilo** e nel riquadro a destra fai clic su **Esegui test**

![Esegui il test per l&#39;e-mail utilizzando l&#39;attività dell&#39;attributo del profilo](assets/test-the-campaign-run-test-profile-attribute.png)

&#x200B;2. Attendi il messaggio di conferma, quindi fai clic su **Visualizza report** per visualizzare i dettagli del test e-mail

![Fare clic su Visualizza report per visualizzare i dettagli del test e-mail](assets/test-the-campaign-view-report-1.png)

&#x200B;3. La pagina del rapporto e-mail presenta le statistiche della campagna e lo stato di esecuzione. Il test E-mail è una verifica dell’attività per garantire che non vi siano errori e non invii e-mail. In genere il completamento richiede circa \~**5** minuti.

![Pagina report e-mail con statistiche campagna](assets/test-the-campaign-campaign-statistics-1.png)

>[!NOTE]
>
>Potrebbe essere necessario aggiornare la pagina alcune volte per visualizzare il risultato del test finale.



&#x200B;4. Una volta completato il test e-mail, vengono presentati i risultati. Percentuale di errori. Fare clic su **Visualizza altro** per conoscerne il motivo.

![Frequenza errori con collegamento Visualizza altro](assets/test-the-campaign-error-rate-view-more.png)

&#x200B;5. Il motivo indica `Email address not found in profile`

![Motivo: indirizzo e-mail non trovato nel profilo](assets/test-the-campaign-email-not-found-reason.png)

>[!NOTE]
>
>Poiché l&#39;**indirizzo di consegna** configurato per l&#39;attività E-mail, **Indirizzo e-mail utilizzando l&#39;attributo Profilo**, è stato configurato per l&#39;utilizzo dell&#39;attributo Profilo `personalEmail.address`, è stata creata una dipendenza dal **Profilo AEP**.
>
>Dei **38** ID cliente qualificati dallo schema relazionale, il sistema ha trovato solo **7** profili AEP corrispondenti. Per i restanti **31** profili AEP non esistevano, causando il messaggio di errore `Email address not found in profile`.
>
>È importante ricordare che i dati nel datalake e nell&#39;archivio relazionale vengono mantenuti **coerenti** quando si utilizzano gli attributi del profilo AEP nelle campagne orchestrate.



## #2 report e-mail

1. Ripeti lo stesso processo per l&#39;attività **E-mail utilizzando Target Dimension**

![Esegui il test per la posta elettronica utilizzando l&#39;attività di Target Dimension](assets/test-the-campaign-run-test-target-dimension.png)

&#x200B;2. Attendi il messaggio di conferma, quindi fai clic su **Visualizza report** per visualizzare i dettagli del test e-mail

![Fare clic su Visualizza report per visualizzare i dettagli del test e-mail](assets/test-the-campaign-view-report-2.png)

&#x200B;3. Una volta completato il test e-mail, vengono presentati i risultati. In questo caso, non ci saranno errori

![Statistiche campagna senza errori](assets/test-the-campaign-campaign-statistics-2.png)

>[!NOTE]
>
>Poiché l&#39;**indirizzo di consegna** per l&#39;attività E-mail **E-mail tramite Target Dimension** è stato configurato per l&#39;utilizzo di `dep_rel_customer_account.email`, dallo schema Relazionale, non vi è alcuna dipendenza dai profili AEP o dai relativi attributi.
>
>Tutti gli ID cliente qualificati **38** hanno e-mail corrispondenti nell&#39;archivio relazionale e potrebbero essere indirizzati correttamente senza errori.



## Interrompere il flusso di lavoro

Fai clic sul pulsante **Interrompi** per interrompere la **modalità di test** per la campagna

>[!TIP]
>
>Entrambe le configurazioni del canale e-mail sono state testate all’interno della stessa campagna e sono state osservate differenze tra l’utilizzo di un attributo di profilo AEP e l’utilizzo di Target Dimension nella configurazione del canale e-mail.
>
>Congratulazioni, questo conclude il laboratorio di consegna dei messaggi.

## Riassunto

Ora hai visto come testare la campagna creata per comprenderne il flusso e il comportamento. In questo caso, le sfumature dell’utilizzo delle diverse impostazioni per la configurazione del canale e-mail sono state ben comprese durante l’esecuzione del flusso di test.

Ulteriori informazioni sulla modalità di test della campagna [qui](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/launch/start-monitor-campaigns), se sei interessato.
