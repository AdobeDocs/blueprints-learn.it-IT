---
title: Leggere un pubblico
description: Scopri come utilizzare l’attività Read Audience con un Profile Target Dimension in una campagna orchestrata e come verificare come vengono eliminati i profili senza corrispondenza durante la riconciliazione dei dati relazionali.
doc-type: article
solution: Experience Platform
exl-id: f825efe9-4349-4195-a017-c956c15df946
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '1268'
ht-degree: 0%

---


# Leggere un pubblico

## Obiettivo

Nei passaggi successivi creerai una campagna per leggere un pubblico da AEP e utilizzarlo insieme al profilo di Target Dimension creato in precedenza. Utilizza l’attività Dividi per dividere i dati in base a una condizione. Infine, testa la campagna per comprendere come funzionano questi tipi di pubblico quando vengono utilizzati con lo schema relazionale.

## Leggi pubblico

Questo laboratorio illustra come utilizzare l’attività Read audience in combinazione con lo schema relazionale per l’arricchimento.

Orchestrated Campaign utilizza lo schema relazionale per tutte le attività. Quando si utilizza l’attività Read audience, che legge il pubblico da AEP, è necessario configurare un’entità corrispondente (Target Dimension) per riconciliare il pubblico con Campaign Target Dimension.

## Creare una campagna

1. Nella barra laterale a sinistra, fai clic su **Campagne**

   ![Navigazione nella barra a sinistra per Campagne](assets/read-an-audience-navigate-to-campaigns.png)

2. Fai clic su **Crea campagna**

   ![Crea pulsante campagna](assets/read-an-audience-create-campaign-button.png)

3. Seleziona **Orchestrazione - Marketing** e fai clic su **Conferma**

   ![Orchestrazione - Selezione del tipo di campagna di marketing](assets/read-an-audience-select-orchestration-marketing.png)

4. Fornisci i dettagli della campagna come segue, quindi fai clic sul pulsante **Salva**
   - Nome: **OC-RSL-ReadAudience-Test**
   - Descrizione: **Test pubblico lettura RSL**

   ![Modulo impostazioni campagna con campi nome e descrizione](assets/read-an-audience-campaign-settings-form.png)

5. Attendi il messaggio di conferma

![Messaggio di conferma dopo il salvataggio delle impostazioni della campagna](assets/read-an-audience-campaign-settings-confirmation.png)



## Aggiungi attività Read audience

1. Fai clic su **+** nell&#39;area di lavoro per aprire il menu delle opzioni, quindi seleziona **Read audience** dalle **attività di targeting**

   ![Menu delle attività di targeting con Read audience selezionato](assets/read-an-audience-add-read-audience-activity.png)

2. Nel riquadro dei dettagli **Read audience**, fai clic sull&#39;icona Cerca per **Audience**

   ![Leggi il riquadro dei dettagli del pubblico con l&#39;icona di ricerca del pubblico](assets/read-an-audience-search-audience-icon.png)

3. Seleziona il pubblico **dep: Membri del piano di base** con conteggio profili di **9** e fai clic su **Aggiungi pubblico**

   ![dep: pubblico di membri del piano di base selezionato con conteggio profili di 9](assets/read-an-audience-select-basic-plan-members-audience.png)

4. Fai clic sul menu a discesa per **Entità** e seleziona il Dimension di destinazione della campagna `dep-rel: Customer Account - customer_id`

![Elenco a discesa Entità con Dimension di destinazione dell&#39;account cliente selezionato](assets/read-an-audience-select-entity-target-dimension.png)

>[!NOTE]
>
>È inoltre possibile estrarre altri attributi dal profilo AEP per utilizzarli nell&#39;area di lavoro utilizzando il pulsante **Aggiungi attributo**. Ma per questo laboratorio, non sono necessari attributi aggiuntivi, quindi il passaggio viene saltato.



## Testare la campagna

1. Sono state inserite le impostazioni per l&#39;attività **Read Audience**. Fai clic su **Avvia** per eseguire la campagna in **Modalità test**

   ![Pulsante Avvia per eseguire la campagna in modalità di test](assets/read-an-audience-start-test-mode.png)

   >[!NOTE]
   >
   >L&#39;esecuzione di questa operazione richiede alcuni minuti.
   >
   >La modalità di test consente l’esecuzione della campagna per verificarne e monitorarne il comportamento insieme ai risultati di ogni attività. Le attività vengono eseguite in sequenza fino alla fine dell’area di lavoro.



2. L’esecuzione del test viene avviata e i risultati vengono visualizzati al termine. Fai clic sul nodo **Risultato** e quindi su Anteprima risultati per visualizzare i risultati dell&#39;esecuzione

   ![Nodo di risultati con opzione Anteprima risultati](assets/read-an-audience-preview-test-results.png)

3. Tieni presente che **2** (su 9) profili di **Read audience** non hanno una dimensione **Target** corrispondente dallo schema relazionale (ovvero esistono nell&#39;archivio dei profili ma non nell&#39;archivio relazionale). E poiché Orchestrated Campaign non funziona secondo lo schema relazionale, i `customer_id` (**2**) senza corrispondenza del **Read audience** vengono eliminati e solo i *corrispondenti*, **7** in questo caso, sono utilizzabili nelle attività successive che sfruttano **dati relazionali** nella campagna

   ![Anteprima dei risultati che mostrano i profili senza un Dimension di destinazione corrispondente](assets/read-an-audience-missing-target-dimension.png)

   >[!NOTE]
   >
   >Nei passaggi seguenti vengono utilizzati i dati relazionali per confermare l&#39;istruzione precedente che indica l&#39;eliminazione di `customer_id` senza corrispondenza.

4. Fai clic su **Interrompi** per interrompere la **modalità di test** della campagna

   ![Pulsante Interrompi per terminare la modalità di test della campagna](assets/read-an-audience-stop-test-mode.png)

5. Fai clic su **+** alla fine del flusso e aggiungi **Dividi** dalle **attività di targeting**

   ![Menu attività di targeting con Divisione selezionata](assets/read-an-audience-add-split-activity.png)

6. Nel riquadro dei dettagli dell&#39;attività **Split**, espandere la prima suddivisione denominata **Subset**

   ![Dividi il riquadro dei dettagli attività con il segmento del sottoinsieme espanso](assets/read-an-audience-expand-subset-split.png)

7. Rinominalo in &quot;**Archivio**&quot; e fai clic su **Crea filtro** per impostare la condizione del filtro

   ![Segmento rinominato in In Store con l&#39;opzione Crea filtro](assets/read-an-audience-rename-in-store-segment.png)

8. Nel riquadro **Crea filtro** r fare clic su **Aggiungi condizione**

   ![Creare il riquadro del filtro con il pulsante Aggiungi condizione](assets/read-an-audience-add-condition-button.png)

9. Poiché non sono stati estratti altri attributi dal profilo AEP, l&#39;unico attributo del profilo AEP disponibile qui è `Customer ID`. Tuttavia, per impostare la condizione del filtro sono disponibili le colonne dell’archivio relazionale corrispondenti alla dimensione di Target corrispondente. Espandere la **dimensione di targeting** facendo clic su **>**

   ![Dimensione targeting espansa per mostrare le colonne dell&#39;archivio relazionale](assets/read-an-audience-expand-targeting-dimension.png)

10. Seleziona `Source` dall&#39;elenco e fai clic su **Conferma**

![Attributo Source selezionato dalle colonne della dimensione Targeting](assets/read-an-audience-select-source-attribute.png)

&#x200B;11. I valori distinti per la colonna Source sono disponibili nel menu a discesa. Per la **condizione personalizzata**, seleziona **&quot;In Store&quot;** dal menu a discesa e fai clic su **Conferma** per uscire

![Condizione personalizzata impostata su In Store](assets/read-an-audience-set-in-store-condition.png)

&#x200B;12. Nel riquadro dei dettagli dell&#39;attività **Divisione**, le impostazioni per la prima Divisione sono state completate. Fai clic su **Aggiungi segmento** alla seconda suddivisione

![Pulsante Aggiungi segmento nel riquadro dei dettagli attività di suddivisione](assets/read-an-audience-add-segment-button.png)

È stato creato un nuovo segmento denominato **Risultato**

![Nuovo segmento denominato Risultato](assets/read-an-audience-new-result-segment.png)

&#x200B;13. Rinomina &quot;**Risultato**&quot; in &quot;**Non nell&#39;archivio**&quot; e fai clic su **Crea filtro** per impostare la condizione del filtro

![Segmento rinominato in Non in archivio con l&#39;opzione filtro](assets/read-an-audience-rename-not-in-store-segment.png)

&#x200B;14. Nel riquadro **Crea filtro**, fare clic su **Aggiungi condizione**. Segui lo stesso approccio di cui sopra, espandi la **dimensione di targeting** facendo clic su **>**, quindi seleziona `Source` dall&#39;elenco e fai clic su **Conferma**

![Dimensione targeting espansa per mostrare le colonne dell&#39;archivio relazionale](assets/read-an-audience-expand-targeting-dimension.png)

![Attributo Source selezionato dalle colonne della dimensione Targeting](assets/read-an-audience-select-source-attribute.png)

&#x200B;15. Per la **condizione personalizzata**, selezionare **&quot;In store&quot;** dal menu a discesa e per l&#39;operatore selezionare &quot;**diverso da**&quot;. Fai clic su **Conferma** per uscire

![Condizione personalizzata impostata su non uguale a In Store](assets/read-an-audience-set-not-in-store-condition.png)

&#x200B;16. Nel riquadro dei dettagli dell&#39;attività **Divisione**, le impostazioni per le due divisioni sono state completate. Fai clic su **Avvia** per eseguire la campagna in **Modalità test**

![Pulsante Avvia per eseguire la campagna in modalità di test dopo la configurazione della suddivisione](assets/read-an-audience-start-test-mode-second-run.png)

&#x200B;17. L’esecuzione del test inizia e i risultati vengono visualizzati al termine. Poiché nello schema relazionale sono state trovate solo **7** dimensioni di destinazione corrispondenti, lo stesso conteggio viene osservato anche dopo le operazioni di suddivisione (**7** e **0**)

![Dividi risultati attività con conteggi di 7 e 0](assets/read-an-audience-verify-split-counts.png)

&#x200B;18. Fai clic su ogni casella dei risultati e **Anteprima risultati** per visualizzare i risultati

![Opzione Anteprima risultati per ogni casella risultati divisa](assets/read-an-audience-preview-split-results.png)

&#x200B;19. Fai clic su **Interrompi** per interrompere la **modalità di test** della campagna

![Pulsante Interrompi per terminare l&#39;esecuzione finale della modalità di test](assets/read-an-audience-stop-test-mode-final.png)

>[!NOTE]
>
>Mentre il pubblico Read mostrava **9** profili. Poiché abbiamo creato un filtro su Source e il campo Source esiste nello store relazionale, abbiamo dovuto unirci dallo store dei profili allo store relazionale per controllarlo. Quando è stato aggiunto allo schema relazionale tramite il Dimension di destinazione di Campaign, solo un totale di **7** profili ha restituito una corrispondenza. Questi **7** ID cliente corrispondenti sono disponibili per l&#39;utilizzo nelle seguenti attività che tentano di utilizzare dati relazionali. Tutti gli ID cliente **7** avevano `Source` impostati su **&quot;In Store&quot;**, come evidenziato dai flussi di suddivisione.
>
>Pertanto, mantenere la coerenza dei dati è fondamentale quando si utilizzano i profili AEP insieme alle relative controparti relazionali per l’arricchimento.

>[!TIP]
>
>Congratulazioni, questo completa il laboratorio sull’utilizzo dell’attività Read Audience con lo schema relazionale.

## Riassunto

Ora hai visto quanto è facile creare una campagna, eseguire un’attività Read Audience insieme al Dimension di destinazione del profilo per sfruttare lo schema relazionale. Hai utilizzato l’attività Dividi per dividere il pubblico in base a una condizione. Infine, la modalità di test ha aiutato a capire che è importante disporre della coerenza dei dati tra il profilo e lo schema relazionale.

Puoi trovare ulteriori [qui](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/design-campaigns/read-audience) se sei interessato.
