---
hold: true
title: Mappature iniziali
description: Mappa manualmente i campi _id e timestamp richiesti per un set di dati Experience Event utilizzando espressioni di campo calcolato.
doc-type: article
solution: Experience Platform
exl-id: 4052d104-bf0c-4b2d-a298-8075279aeaf8
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# Mappature iniziali

Come nell’esercizio precedente, dovrai verificare la mappatura e, in alcuni casi, modificarla.

## Verifica consigli ML

1. Nel passaggio di mappatura, ML Recommendations mappano automaticamente la maggior parte degli attributi. Tuttavia, si verificano anche diversi errori. La schermata iniziale potrebbe essere simile alla seguente.

![Schermata di mappatura che mostra _id e timestamp come campi non mappati non consigliati da ML](assets/initial-mappings-id-timestamp-unmapped-fields.png "_id; timestamp sono due campi per i quali ML Recommender non genererà la mappatura per")

>[!NOTE]
>
>Poiché è in corso la mappatura di un set di dati di Experience Event per la prima volta, tieni presente che **\_id** e **timestamp** non sono mai consigliati o mappati per impostazione predefinita per gli eventi di Experience. Devi accertarti manualmente che siano mappate correttamente.

## Mappa i campi \_id, timestamp e order.\_devbc.acqSource

1. Per mappare **\_id,** scrivi la seguente espressione di campo calcolato e fai clic su anteprima

```none
concat(orderID, "-", lastOrderStatusUpdate)
```

![Il campo calcolato per la mappatura _id, pronto per il salvataggio](assets/initial-mappings-calculated-field-for-id-mapping.png "Il campo calcolato per la mappatura _id avrà un aspetto simile a questo. Fare clic su Salva per salvare il campo calcolato")

![Mappatura del campo calcolato con l&#39;attributo _id](assets/initial-mappings-map-calculated-field-to-id.png "Mappatura del campo calcolato con _id")

1. Assicurati che il campo **timestamp** nello schema di destinazione sia mappato al seguente campo calcolato:

```none
lastOrderStatusUpdate
```

![Anteprima espressione campo calcolato per la mappatura timestamp](assets/initial-mappings-expression-preview.png "Scrivere l&#39;espressione seguente e fare clic su Anteprima. NOTA che questo valore distingue tra maiuscole e minuscole e deve essere scritto esattamente in questo modo")

![Mappatura dell&#39;espressione del campo calcolato &quot;inStore&quot; su order._devbc.acqSource](assets/initial-mappings-map-instore-expression-to-acqsource.png)

1. Mappa l&#39;espressione del campo calcolato **&quot;inStore&quot;** su **order.\_devbc.acqSource**

![Scrittura dell&#39;espressione del campo calcolato &quot;inStore&quot; e clic su Anteprima](assets/initial-mappings-write-instore-expression-preview.png "Scrivere l&#39;espressione seguente e fare clic su Anteprima. NOTA che questo valore distingue tra maiuscole e minuscole e deve essere scritto esattamente in questo modo")

## Gestione delle mappature duplicate

Se la schermata di mappatura ora lamenta la presenza di una mappatura duplicata come **orderStatus** mappata a **order.\_devbc.acqSource,** fai clic sull&#39;icona &quot;-&quot; per rimuovere la mappatura.

&#x200B;> [!NOTE]
>
>Tieni presente che più campi di input non possono essere mappati sullo stesso campo di output, in quanto questo rende ambigua la mappatura. Tuttavia, un singolo campo di input può essere mappato su più campi di output nello schema XDM.

![Avviso di mapping duplicato per orderStatus mappato su order._devbc.acqSource](assets/initial-mappings-duplicate-mapping-warning.png "Mapping duplicato per orderStatus mappato su order._devbc.acqSource")



![Avviso di mappatura duplicata per order._devbc.acqSource dopo la creazione del campo calcolato](assets/initial-mappings-duplicate-mapping-for-acqsource.png "Mappatura duplicata per order._devbc.acqSource dopo la creazione di un campo calcolato e il relativo mapping è già stato eseguito. ")
