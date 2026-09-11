---
hold: true
title: Pianifica flusso di dati
description: Configura una pianificazione ricorrente del flusso di dati di 15 minuti con backfill abilitato e scopri come gli orari di avvio UTC influiscono sulle esecuzioni.
doc-type: article
solution: Experience Platform
exl-id: 9865b1eb-0d98-4cae-a928-69ea897607ca
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# Pianifica flusso di dati

Nel passaggio **Pianificazione**:

1. Imposta **Frequenza** su Minuti.
1. Impostare **Intervallo** su 15, ovvero 15 minuti.
1. Attiva l&#39;opzione **Backfill**.

>[!NOTE]
>
>Osserva che l&#39;**ora di inizio** è in UTC.
>
>Il Coordinated Universal Time (UTC) è uno standard temporale globale utilizzato come punto di riferimento per la conservazione del tempo in tutto il mondo. Per un team distribuito in tutto il mondo, fornisce un riferimento comune per diverse aree geografiche e paesi, semplificando il coordinamento delle attività e la pianificazione degli eventi in base ai diversi fusi orari.
>
>In diverse parti dell’interfaccia utente di AEP, l’ora UTC è la base della pianificazione temporale. L&#39;ora UTC è 1 ora indietro rispetto all&#39;ora di Londra. Se non sei sicuro dell’ora UTC, è sufficiente Google &quot;Ora UTC&quot;.

>[!NOTE]
>
>In pratica, l&#39;opzione **Backfill** esegue una retrocompilazione unica di tutti i file e le esecuzioni successive acquisiscono nuovi file.

![Pianificazione dell&#39;esecuzione del flusso di dati con le opzioni di frequenza, intervallo e backfill impostate](assets/schedule-dataflow-scheduling-dataflow-run.png "Pianificazione dell&#39;esecuzione del flusso di dati")

Rivedi il flusso di dati e fai clic su **Fine.**

![Verifica della configurazione del flusso di dati finale prima di fare clic su Fine](assets/schedule-dataflow-review-final-dataflow.png "Verifica il flusso di dati finale")

>[!CAUTION]
>
>Se scegli l&#39;opzione **Esegui una volta** per il flusso di dati, non potrai modificare questa pianificazione o aggiornare il flusso di dati in un secondo momento. Tuttavia, puoi eseguire il flusso di dati su richiesta, ovvero eseguirlo nuovamente se devi acquisire nuovi dati.

Dopo aver fatto clic su **Fine**, viene visualizzata la schermata **Flussi dati**. La creazione del flusso di dati dovrebbe richiedere alcuni minuti. Lo stato dell&#39;ultima esecuzione del flusso di dati indica **Nessuna esecuzione**. La prima corsa dovrebbe calciare in un paio di minuti.

![Schermata Flussi dati che mostra il nuovo flusso di dati con stato Nessuna esecuzione](assets/schedule-dataflow-dataflows-screen-no-runs-status.png "Schermata Origini flussi dati")

> [!NOTE]
>
>Devi aggiornare la pagina continuamente per visualizzare l’aggiornamento di stato, in quanto il backend non invia aggiornamenti all’interfaccia utente.

>[!NOTE]
>
>Se hai attivato tutti gli avvisi, riceverai un avviso nel browser nell’angolo superiore destro del browser quando il flusso inizia a funzionare e viene completato correttamente o non riesce
