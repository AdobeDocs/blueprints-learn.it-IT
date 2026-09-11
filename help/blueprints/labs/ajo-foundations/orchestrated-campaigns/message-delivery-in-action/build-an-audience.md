---
hold: true
title: Creare un pubblico
description: Scopri come utilizzare l’attività Genera pubblico per eseguire il targeting dei membri del piano Basic da uno schema relazionale e verificare i conteggi delle righe risultanti.
doc-type: article
solution: Experience Platform
exl-id: 7576e64b-d99a-4864-b877-f4ae77e1d7bd
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---


# Creare un pubblico

## Obiettivo

Nel prossimo set di passaggi creerai un pubblico dallo schema relazionale selezionando la dimensione di targeting giusta e impostando le condizioni appropriate. Puoi anche utilizzare l’opzione di aggiornamento per controllare il numero previsto di conteggi di righe.

## Creazione del pubblico

1. Una volta eseguito il rendering della campagna, fai clic su **+** nell&#39;area di lavoro per aprire il menu delle opzioni, quindi seleziona **Genera pubblico** dalle **Attività di targeting**

![Seleziona Genera pubblico dalle attività di targeting](assets/build-an-audience-select-build-audience-activity.png)

&#x200B;2. L&#39;attività **Genera pubblico** apre il riquadro dei dettagli a destra, quindi fai clic sull&#39;icona di ricerca per selezionare la **dimensione di targeting**.

![Seleziona dimensione di targeting](assets/build-an-audience-select-targeting-dimension.png)

&#x200B;3. Seleziona `dep-rel: Customer Account` dall&#39;elenco e fai clic su **Conferma**

![Seleziona dep-rel: schema account cliente](assets/build-an-audience-select-customer-account-schema.png)

&#x200B;4. Una volta configurata la **dimensione di targeting**, fai clic su Crea pubblico per avviare il processo di creazione del pubblico dallo schema relazionale

![Fai clic sul pulsante Crea pubblico](assets/build-an-audience-create-audience-button.png)

&#x200B;5. Viene visualizzato il riquadro Crea dettagli pubblico. Fai clic su **Aggiungi condizione**

![Fai clic su Aggiungi condizione in Crea riquadro pubblico](assets/build-an-audience-add-condition.png)

&#x200B;6. Scorri verso il basso ed espandi `dep-rel: Plan Lookup` facendo clic su **>** accanto

![Espandi dep-rel: ricerca piano](assets/build-an-audience-expand-plan-lookup.png)

&#x200B;7. Seleziona `dep-rel: Plan Name` e fai clic su **Conferma**

![Selezionare dep-rel: nome piano](assets/build-an-audience-select-plan-name.png)

&#x200B;8. Nel pannello Condizione personalizzata, lascia l’operatore &quot;uguale a&quot; e per Valore, seleziona Base dal menu a discesa.

![Condizione personalizzata con nome piano uguale a Base](assets/build-an-audience-plan-name-equals-basic.png)

>[!NOTE]
>
>Tieni presente che tutti i valori distinti disponibili per la colonna selezionata vengono visualizzati nel menu a discesa, facilitando la creazione delle condizioni personalizzate.



&#x200B;9. Con la condizione Personalizzata configurata, fai clic sull’icona Aggiorna per calcolare e visualizzare il conteggio. Esistono due posizioni per il calcolo dei risultati

![Fare clic sull&#39;icona Aggiorna per calcolare il numero di righe previsto](assets/build-an-audience-refresh-row-counts.png)

>[!NOTE]
>
>L&#39;operazione di aggiornamento valuta la condizione rispetto ai dati relazionali e visualizza i risultati previsti. Questa operazione richiede in genere solo pochi secondi ed è estremamente utile per mettere a punto i criteri e garantire che soddisfino le aspettative.



&#x200B;10. I conteggi (**38**) indicano il numero di righe nell&#39;archivio relazionale che corrispondono alla condizione specificata. Fai clic su **Conferma** per uscire dal riquadro **Crea pubblico**

![Conferma conteggio righe ed esci da Crea riquadro pubblico](assets/build-an-audience-confirm-row-count.png)

>[!NOTE]
>
>Nella sezione Proprietà delle regole sono disponibili opzioni per ottenere ulteriori dettagli. Fai clic su **Visualizza risultati** per visualizzare i risultati effettivi restituiti. Utilizza l&#39;opzione **Vista codice** per visualizzare la query in esecuzione.

## Riassunto

Ora hai visto quanto è facile utilizzare l’attività Genera pubblico nella campagna scegliendo la dimensione di targeting giusta dallo schema relazionale. Quindi hai aggiunto una condizione per perfezionare i criteri di creazione del pubblico e hai utilizzato l’opzione di aggiornamento per verificare il numero previsto di righe.

Puoi trovare ulteriori [qui](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/design-campaigns/build-audience) se sei interessato.
