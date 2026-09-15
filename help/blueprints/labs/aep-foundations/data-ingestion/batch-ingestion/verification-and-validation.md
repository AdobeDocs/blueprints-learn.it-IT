---
title: Verifica e convalida
description: Visualizza l’anteprima di un set di dati acquisito nell’interfaccia utente ed esegui query SQL per verificare i record acquisiti in batch e i campi schema nidificati.
doc-type: article
solution: Experience Platform
exl-id: 7e7cd43d-cc24-4a40-a175-2c651436ab79
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%
---

# Verifica e convalida

## Visualizzare l’anteprima del set di dati

1. Fai clic su **Set di dati**
1. **Individua** e **fai clic** sul nome del set di dati creato.

   ![Individuazione e clic sul nome del set di dati nel riquadro Set di dati](assets/verification-and-validation-access-dataset-in-datasets-pane.png "Accesso al set di dati nel riquadro Set di dati")



1. Fai clic su **Anteprima set di dati** nell&#39;angolo superiore destro

   ![Posizione pulsante Anteprima set di dati nell&#39;angolo superiore destro della schermata del set di dati](assets/verification-and-validation-preview-dataset-button-location.png "Il set di dati di anteprima si trova nell&#39;angolo superiore destro")



1. **Verifica** e **convalida** gli stessi record acquisiti facendo clic sul riquadro a sinistra che mostra la gerarchia dello schema.

![Anteprima set di dati con riquadro gerarchia schema che mostra i record acquisiti](assets/verification-and-validation-verify-and-validate-the-dataset.png)

>[!NOTE]
>
>**Anteprima set di dati** visualizza il batch riuscito più recente in questo set di dati. Impossibile visualizzare i batch precedenti. Inoltre, dati complessi come array e mappe non sono attualmente visualizzabili e vengono visualizzati come colonne vuote. Per ottenere una visualizzazione più completa, è necessario utilizzare SQL per esplorare il set di dati come spiegato di seguito.



## Query set di dati

1. **Chiudi** l&#39;anteprima
1. Nella schermata Set di dati fare clic sull&#39;icona Copia in **Nome tabella**. Nella schermata di esempio seguente, il nome della tabella è `customer_account_sm`

   ![Icona Copia accanto al nome della tabella nella schermata Set di dati](assets/verification-and-validation-copy-table-name.png "Copia il nome della tabella")



1. Passa alla sezione **Query**

1. Fai clic su **Crea query**

   ![Crea pulsante query nella sezione Query](assets/verification-and-validation-access-the-query-editor.png)



1. Copiare e incollare la seguente query SQL nell&#39;**Editor**. Ricordarsi di sostituire `<table_name>` con il valore ottenuto al punto 6.

   ```sql
   SELECT * FROM <table_name>
   ```



1. Premere il pulsante **Riproduci**.

   ![Interfaccia dell&#39;editor delle query con query SQL e pulsante Play](assets/verification-and-validation-query-editor-interface.png "Interfaccia dell&#39;editor delle query")



1. **Anteprima** dei risultati

1. Per recuperare lo schema XDM insieme ai dati, esegui anche la seguente query SQL:

```sql
SELECT to_json(shippingAddress) FROM <table_name>
```

Per accedere ai dati nel `postalCode` **nodo**, digitare:

```sql
SELECT shippingAddress.postalCode FROM <table_name>
```

>[!SUCCESS]
>
>Congratulazioni!  Hai acquisito e creato correttamente un set di esempio di profili cliente in tempo reale
