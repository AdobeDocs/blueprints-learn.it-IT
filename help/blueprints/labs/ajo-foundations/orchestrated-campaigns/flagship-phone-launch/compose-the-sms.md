---
title: Componi l’SMS
description: Scopri come comporre e personalizzare un messaggio SMS nelle campagne orchestrate utilizzando gli attributi del telefono e del modello dall’archivio relazionale.
doc-type: article
solution: Experience Platform
exl-id: 3deb822b-8374-4537-a260-f4f6f4d67569
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# Componi l’SMS

## Obiettivo

Nei prossimi passaggi si sta per comporre un messaggio SMS MOLTO semplice.  Vedrai come aggiungere facilmente alcuni contenuti a un livello di base ESTREMO e personalizzare il messaggio in base ai dati nell’archivio relazionale.



## Passa al contenuto

Fai clic sul pulsante **Modifica contenuto** oppure passa direttamente alla scheda **Contenuto**

![Pulsante Modifica contenuto e navigazione nella scheda Contenuto &quot;Modifica contenuto&quot;](assets/compose-the-sms-navigate-to-content-tab.png "Modifica contenuto")



## Creare il messaggio

1. Fai clic sul pulsante **Personalization** per creare il messaggio.

   ![Pulsante Personalization per creare il messaggio SMS](assets/compose-the-sms-click-personalization-button.png)

   >[!NOTE]
   >
   >L’opzione &quot;bacchetta magica&quot; utilizza l’intelligenza artificiale per aiutarti a scrivere un messaggio. Controllalo se vuoi, ma non lo copriremo in questo laboratorio.



2. Copia e incolla il testo seguente nel corpo del messaggio SMS.

   ```none
   Hi from Connection 5G! Your phone_make phone_model is eligible for a free upgrade to one of the new iPhone 17 models. Shop online or come into a store today to take advantage of this offer.
   ```

   >[!NOTE]
   >
   >Assicurarsi di impostare il ritorno a capo automatico su **Attivato** nell&#39;editor messaggi.  È possibile trovare nel riquadro in basso a destra della finestra.



3. Aggiorna i due campi nel messaggio denominato **phone\_make** e **phone\_model** di seguito utilizzando l&#39;opzione **Target attributes** nella barra a sinistra.  Al termine il messaggio dovrebbe corrispondere alla schermata.

   ![Messaggio SMS finale con marca del telefono e modello personalizzati](assets/compose-the-sms-final-message-text.png)

   >[!NOTE]
   >
   >Perché sta facendo questo?  Beh, vuoi personalizzare il messaggio con il produttore e il modello del telefono dei clienti e queste informazioni risiedono nella tabella Linee cliente nello store relazionale.  Questo illustra come utilizzare i dati di Campagne orchestrate per personalizzare i messaggi.



4. Fai clic su **Convalida** nell&#39;editor e accertati che non vi siano errori di convalida; in caso affermativo, fai clic sul pulsante **Salva**

   ![Pulsanti di convalida e salvataggio nell&#39;editor messaggi](assets/compose-the-sms-validate-and-save.png)



5. Fai clic sulla freccia indietro **(\&lt;-)** quando hai finito di tornare all&#39;area di lavoro del flusso di lavoro

![Freccia indietro per tornare all&#39;area di lavoro del flusso di lavoro](assets/compose-the-sms-return-to-canvas.png)



## Riassunto

Hai appena creato un messaggio e, si spera, ora conosci meglio il funzionamento dell’editor di messaggi.  Ricorda che puoi personalizzare utilizzando i dati provenienti dallo Store relazionale, ma puoi anche personalizzare utilizzando i dati del Profilo cliente in tempo reale!

>[!NOTE]
>
>Se utilizzi gli attributi Profilo cliente in tempo reale per personalizzare i messaggi nelle campagne orchestrate, ricorda che vengono estratti dal set di dati Istantanea profilo nel data lake, in modo che gli attributi possano risalire a un massimo di 24 ore. Lo snapshot del profilo viene aggiornato solo una volta al giorno dopo il processo di segmentazione batch giornaliero.
