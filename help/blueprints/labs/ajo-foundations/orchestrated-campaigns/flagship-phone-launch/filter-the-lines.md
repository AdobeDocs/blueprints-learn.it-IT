---
title: Filtra le righe
description: Scopri come filtrare le linee cliente che hanno rinunciato all’accesso con un’attività Split e utilizzare Modifica dimensione per allineare la dimensione di destinazione di un flusso di lavoro alla configurazione del canale SMS.
doc-type: article
solution: Experience Platform
exl-id: fb556a27-5c73-4457-ae98-dba43d445c7f
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 8d5a87f094e2fba7abd7f5a9acf8e9e775d9b534
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 0%
---

# Filtra le righe

## Obiettivo

Nei passaggi successivi escluderai tutte le righe di cui non è consentito il targeting con un messaggio SMS a causa della rinuncia a livello di riga.  In questo caso non puoi fare affidamento sul consenso al profilo, perché si tratta di un target a livello di linea.



## Configurare l’attività di suddivisione

1. Fai clic sull&#39;icona **+** nella transizione inferiore dell&#39;attività Fork e seleziona l&#39;attività **Dividi** nel popup.

   ![Aggiungi un&#39;attività Split al ramo del fork inferiore](assets/filter-the-lines-add-split-activity.png)



2. Nella barra a destra, aggiorna l&#39;etichetta in modo che indichi quanto segue: `Filter out opt'd out lines`

   ![Dividi etichetta attività impostata su Escludi righe rinuncia](assets/filter-the-lines-set-split-label.png)



3. Nella barra a destra espandi la sezione **Sottoinsieme** del segmento predefinito e fai clic sul pulsante **Crea filtro**

   ![Crea pulsante filtro nella sezione Sottoinsieme](assets/filter-the-lines-create-filter-button.png)



4. Aggiungi una condizione per assicurarti di rimuovere tutte le righe cliente che hanno rinunciato alla messaggistica SMS, quindi fai clic su **Conferma**.

   ![Condizione che rimuove le linee cliente rifiutate da SMS](assets/filter-the-lines-sms-optin-condition.png)

   >[!NOTE]
   >
   >Devi capire come creare la condizione, ma il risultato finale corrisponde alla schermata precedente.  Ce l&#39;hai!



5. Fare clic sul pulsante Salva in alto a destra per salvare i dati.  L&#39;area di lavoro è simile ora\...

![Area di lavoro del flusso di lavoro dopo il salvataggio dell&#39;attività divisa](assets/filter-the-lines-canvas-after-split-save.png)



## Aggiungi dimensione di modifica

1. Nell&#39;area di lavoro del flusso di lavoro fare clic sull&#39;icona **+** dopo la condizione di suddivisione aggiunta e selezionare l&#39;attività **Modifica dimensione**

   ![Aggiungi l&#39;attività Modifica dimensione dopo la condizione di suddivisione](assets/filter-the-lines-add-change-dimension-activity.png)

2. Aggiorna le proprietà della dimensione di modifica come descritto di seguito e fai clic su **Conferma**:
Etichetta: `Convert Line to Account`
Nuova dimensione di destinazione: `dep-rel: Customer Account`

   ![Modifica dimensione di destinazione](assets/filter-the-lines-add-edit-target-dimension.png)

   ![Modifica dimensione di destinazione](assets/filter-the-lines-add-select-target-dimension.png)



## Aggiungere l’attività SMS

1. Fai clic sull&#39;icona **+** dopo la dimensione di modifica aggiunta e seleziona l&#39;**Attività messaggio mobile**

   ![Aggiungi l&#39;attività Mobile Message dopo la condizione di suddivisione](assets/filter-the-lines-add-sms-activity.png)

   ![Attività SMS aggiunta all&#39;area di lavoro del flusso di lavoro](assets/filter-the-lines-sms-activity-on-canvas.png)



2. Nella barra a destra, fai clic sul pulsante **Modifica messaggio mobile** per avviare la configurazione del messaggio SMS

   ![Pulsante Modifica messaggio mobile nella barra a destra](assets/filter-the-lines-edit-sms-button-only.png)



3. Nella barra di navigazione in alto, fai clic sulla voce di menu Azioni, quindi seleziona il canale creato in precedenza dal menu a discesa Configurazione messaggio mobile.

![Errore di configurazione SMS senza risultati](assets/filter-the-lines-sms-configuration-no-results.png)

>[!CAUTION]
>
>Oh no 🫨!  Perché non ottieni alcun risultato?  Non hai già configurato il tuo canale SMS?  Il prodotto è rotto?
>
>VAFFANCULO!!!!!!!!!



## Momento di abbandono

La configurazione del canale per SMS era già stata configurata in precedenza e al momento è così...

![Configurazione dei dettagli di esecuzione configurata durante il laboratorio del canale SMS](assets/configure-sms-channel-final-execution-details.png)

**Di seguito è riportato il testo:**

- Consegna un messaggio per dimensione di destinazione (ad esempio Conto cliente) sul numero di record correlati trovati nella dimensione secondaria (ad esempio Linea cliente)
- Esegui ogni consegna SMS utilizzando il numero di telefono cellulare presente nella dimensione secondaria (ad esempio, Linea cliente)

Questa capacità unica di inviare molti messaggi a un profilo è una delle caratteristiche principali delle Campagne orchestrate, che lo rende diverso dai Percorsi. Tuttavia, la transizione che porta all’attività Mobile Message è impostata su Account cliente. Questo ti consente di unirlo nuovamente al Real-Time Customer Profile al momento dell’invio, in modo che le informazioni di consegna e tracciamento dei messaggi vengano attribuite a un profilo.


Come si fa a far funzionare tutto questo? Modificare la destinazione per l&#39;esecuzione del messaggio in modo che corrisponda alla configurazione del canale 😀



## Modificare Target e completare la configurazione dei messaggi SMS

1. Fai clic sul pulsante Indietro nella schermata di modifica SMS

   ![Pulsante Indietro per uscire dalla schermata di modifica SMS](assets/filter-the-lines-exit-sms-editor.png)



2. Con l&#39;attività di messaggistica mobile selezionata, nella barra a destra modifica prima l&#39;opzione di destinazione predefinita di un messaggio per profilo in **Un messaggio per dimensione secondaria** e quindi fai clic di nuovo in **Modifica messaggio mobile**

   ![Cambia la destinazione, quindi modifica il pulsante del messaggio mobile nella barra a destra](assets/filter-the-lines-edit-sms-button.png)



3. Nella barra di navigazione in alto, fai clic sulla voce di menu **Azioni**, quindi seleziona il canale creato in precedenza dal menu a discesa Configurazione messaggio mobile.

   ![La configurazione SMS ha mostrato correttamente il canale selezionato](assets/filter-the-lines-sms-configuration-selected.png)



## Riassunto

Hai filtrato tutte le righe di cui non era consentito il targeting con un messaggio SMS a causa della rinuncia, modificato la dimensione da riga a account e alla fine hai configurato correttamente l’attività SMS per coloro a cui era consentito il targeting.
Speriamo che tu abbia anche imparato una cosa molto importante: **la destinazione deve corrispondere alla configurazione del canale che desideri utilizzare**
