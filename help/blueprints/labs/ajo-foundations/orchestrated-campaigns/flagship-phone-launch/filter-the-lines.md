---
title: Filtra le righe
description: Scopri come filtrare le linee cliente che hanno rinunciato all’accesso con un’attività Split e utilizzare Modifica dimensione per allineare la dimensione di destinazione di un flusso di lavoro alla configurazione del canale SMS.
doc-type: article
solution: Experience Platform
exl-id: fb556a27-5c73-4457-ae98-dba43d445c7f
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: f189618dc8bfa198b25d646faa3ca0e0f5af5916
workflow-type: tm+mt
source-wordcount: '443'
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



2. Nella barra a destra, modifica innanzitutto la scelta di Target in **Un messaggio per dimensione secondaria**, quindi fai clic sul pulsante **Modifica messaggio mobile** per avviare la configurazione del messaggio SMS

   ![Pulsante Destinazione e modifica messaggio mobile nella barra a destra](assets/filter-the-lines-edit-sms-button.png)



3. Nella barra di navigazione in alto, fai clic sulla voce di menu Azioni, quindi seleziona il canale creato in precedenza dal menu a discesa Configurazione messaggio mobile.

![La configurazione SMS ha mostrato correttamente il canale selezionato](assets/filter-the-lines-sms-configuration-selected.png)




## Riassunto

Hai filtrato tutte le righe a cui non era consentito eseguire il targeting con un messaggio SMS a causa della rinuncia, modificato la dimensione da riga a account e hai aggiunto un’attività SMS per coloro a cui era consentito eseguire il targeting.
