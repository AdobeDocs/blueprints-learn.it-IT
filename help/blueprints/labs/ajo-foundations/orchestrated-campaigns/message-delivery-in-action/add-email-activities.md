---
hold: true
title: Aggiungere attività e-mail
description: Scopri come aggiungere e configurare due attività e-mail su rami Fork separati utilizzando diverse configurazioni del canale e-mail in una campagna orchestrata.
doc-type: article
solution: Experience Platform
exl-id: e911a251-9f9f-484c-a2de-101b0fc2c417
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---


# Aggiungere attività e-mail

## Obiettivo

Nei passaggi successivi, sfrutterai la campagna per aggiungere due attività E-mail ai due rami dell’attività Fork. Configurerai le due attività E-mail per l’utilizzo dei canali E-mail, creati in precedenza. Infine, a ciascuna di queste attività e-mail verrà aggiunta anche la configurazione di base dell’e-mail (oggetto e corpo).

>[!CAUTION]
>
>Prima di continuare, è necessario assicurarsi che entrambe le configurazioni del canale e-mail siano attive nel loro stato.
>
>![Entrambe le configurazioni del canale e-mail mostrano lo stato attivo](assets/add-email-activities-email-channel-configs-active.png "Configurazioni del canale e-mail")



## Aggiungi attività e-mail del ramo principale

1. Fai clic su **+** del flusso principale e seleziona **E-mail** dalle **attività canale**

![Aggiungi attività e-mail](assets/add-email-activities-select-email-activity.png)

Viene aperto il riquadro dei dettagli **E-mail**

![Riquadro dettagli e-mail](assets/add-email-activities-email-details-pane.png)

&#x200B;2. Rinomina l&#39;etichetta in **E-mail utilizzando l&#39;attributo di profilo** per l&#39;attività **E-mail** e fai clic su **Modifica e-mail**. La creazione del corpo dell’e-mail è solo a scopo di test

![Rinomina etichetta attività e-mail e fai clic su Modifica e-mail](assets/add-email-activities-rename-and-edit-email.png)

&#x200B;3. Seleziona la scheda **Azioni** e dal menu a discesa seleziona **Configurazione del canale profilo-e-mail**

![Selezionare la configurazione del canale e-mail del profilo nella scheda Azioni](assets/add-email-activities-select-profile-email-channel.png)

&#x200B;4. Quindi, fai clic su **Modifica contenuto** per aggiungere del contenuto di prova

![Fare clic su Modifica contenuto per aggiungere il contenuto del test](assets/add-email-activities-edit-content.png)

&#x200B;5. Fornisci una **riga oggetto** (&quot;Aggiorna offerta per i membri del piano di base&quot;) e fai clic sul pulsante **Modifica corpo dell&#39;e-mail**

![Aggiungi l&#39;oggetto e modifica il corpo dell&#39;e-mail](assets/add-email-activities-subject-line-edit-body.png)

&#x200B;6. Ci sono molte opzioni, per questo test, scegli **Crea il codice tuo** opzione HTML

![Scegli un codice per la tua opzione HTML](assets/add-email-activities-code-your-own-html.png)

&#x200B;7. In **E-mail Designer**, inserisci una riga di test &quot;Offerta di aggiornamento disponibile!&quot; subito prima dei tag `</body></html>` come mostrato e fai clic su **Salva**

![Inserire la riga di test in E-mail Designer e fare clic su Salva](assets/add-email-activities-email-designer-save.png)

&#x200B;8. Attendi che il messaggio di conferma venga visualizzato nell’angolo in basso a destra

![Messaggio di conferma visualizzato](assets/add-email-activities-confirmation-message.png)

&#x200B;9. Fai clic sulla **freccia a sinistra** accanto a **Invia e-mail a Designer** per uscire

![Fare clic sulla freccia sinistra per uscire da E-mail Designer](assets/add-email-activities-exit-email-designer.png)

&#x200B;10. Viene visualizzata una finestra di dialogo di conferma, fai clic sul pulsante **Salva e chiudi**

![Finestra di dialogo di conferma con il pulsante Salva e chiudi](assets/add-email-activities-save-and-close-dialog.png)

&#x200B;11. Controlla le proprietà e le azioni Email, incluso il testo aggiunto al corpo dell’Email. Fai clic sulla **freccia a sinistra** per tornare all&#39;area di lavoro della campagna

![Torna all&#39;area di lavoro della campagna](assets/add-email-activities-back-to-campaign-canvas.png)

## Aggiungi attività e-mail ramo inferiore

Torna nell&#39;area di lavoro della campagna, fai clic su **+** del flusso inferiore e seleziona **E-mail** dalle **Attività canale**. Seguire gli stessi passaggi indicati sopra (passaggi da 2 a 11) ad eccezione dei seguenti:

- Rinomina l&#39;etichetta in **E-mail utilizzando Target Dimension** per l&#39;attività **E-mail**
- Nelle impostazioni Email, scegli la configurazione del canale Email **Relational-Email**

![Seconda attività e-mail configurata con il canale e-mail relazionale](assets/add-email-activities-bottom-branch-relational-email.png "Aggiungi la seconda attività e-mail")

## Riassunto

Ora hai visto come configurare le attività e-mail con i canali e-mail. Ogni attività è stata quindi configurata con un oggetto e un corpo di E-mail di base. L&#39;intera campagna verrà testata successivamente.
