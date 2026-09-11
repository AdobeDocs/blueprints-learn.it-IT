---
title: Verifica e convalida
description: Visualizza l’anteprima di un set di dati in streaming nell’interfaccia utente ed esegui query SQL per verificare i record acquisiti e i campi schema nidificati.
doc-type: article
solution: Experience Platform
exl-id: fbdb0b6b-08b6-49b8-b6ab-d59d5941c678
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---


# Verifica e convalida

## Visualizzare l’anteprima del set di dati

1. Fai clic su **Set di dati**
1. **Individua** e **fai clic** sul nome del set di dati creato.

   ![Accesso al set di dati creato nel riquadro Set di dati](assets/verification-and-validation-access-the-dataset-in-the-datasets-pane.png "Accesso al set di dati nel riquadro Set di dati")



1. Fai clic su **Anteprima set di dati** nell&#39;angolo superiore destro

   ![Pulsante Anteprima set di dati nell&#39;angolo superiore destro della schermata del set di dati](assets/verification-and-validation-preview-dataset-button.png "Il set di dati di anteprima si trova nell&#39;angolo superiore destro ")



1. **Verifica** e **convalida** gli stessi record acquisiti facendo clic sul riquadro a sinistra che mostra la gerarchia dello schema.

![Verifica e convalida dei record acquisiti tramite il riquadro della gerarchia dello schema](assets/verification-and-validation-verify-and-validate-the-dataset.png "Verifica e convalida il set di dati")

>[!NOTE]
>
>**Il set di dati di anteprima** mostrerà solo le prime righe del set di dati. Gli oggetti array non sono visualizzabili.



## Query set di dati

1. **Chiudi** l&#39;anteprima
1. Nella schermata Set di dati fare clic sull&#39;icona Copia in **Nome tabella**. Nella schermata di esempio seguente, il nome della tabella è `customer_account_sm`

   ![Copia del nome della tabella dalla schermata Set di dati per l&#39;utilizzo in una query](assets/verification-and-validation-copy-the-table-name.png "Copia del nome della tabella")



1. Passa alla sezione **Query**

1. Fai clic su **Crea query**

   ![Accesso all&#39;editor query dalla sezione Query](assets/verification-and-validation-access-the-query-editor.png "Accesso all&#39;editor query")



1. Attiva/disattiva **Editor query avanzato**

   ![Interfaccia dell&#39;editor delle query con l&#39;opzione Editor query avanzato abilitata](assets/verification-and-validation-enhanced-query-editor-toggle.png "Interfaccia dell&#39;editor delle query")



1. Copia e incolla la seguente query SQL nell&#39;**Editor**. Ricordarsi di sostituire `<table_name>` con il valore ottenuto nel passaggio 2.

   ```sql
   SELECT * FROM <table_name>
   ```



1. Premere il pulsante **Riproduci**.

1. **Anteprima** dei risultati.

1. Inoltre, esegui la seguente query SQL per recuperare lo schema XDM insieme ai dati:

   ```sql
   SELECT to_json(shippingAddress) FROM <table_name>
   ```



1. Per accedere ai dati nel `postalCode` **nodo**, digitare:

```sql
SELECT shippingAddress.postalCode FROM <table_name>
```

>[!TIP]
>
>Congratulazioni!  Hai acquisito e creato correttamente un set di esempio di profili cliente in tempo reale
