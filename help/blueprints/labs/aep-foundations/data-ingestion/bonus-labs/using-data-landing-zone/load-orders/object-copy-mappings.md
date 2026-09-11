---
hold: true
title: Mappature copia oggetto
description: Configura i mapping di copia degli oggetti per un array di prodotti, quindi aggiungi e rimuovi le sostituzioni a livello di campo sopra la copia predefinita.
doc-type: article
solution: Experience Platform
exl-id: 762d0e19-ed1c-4f4d-91ec-a962bd6277a7
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---


# Mappature copia oggetto

In questa sezione aggiungerai le mappature della copia oggetto e creerai alcune sostituzioni.

## Mappature pass-through

Aggiungere le seguenti mappature passthrough con **products\[\*]** e **products\[\*].productID** facendo clic su Nuovo tipo di campo e aggiungere qui un nuovo campo per ogni riga. Alcuni potrebbero essere già presenti a causa di ML Recommendations.

| Colonna Source | Colonna XDM |
| ----------------------- | ------------------------- |
| orderStatus | eventType |
| lastOrderStatusUpdate | timestamp |
| products\[\*] | productListItems\[\*] |
| products\[\*].productID | productListItems\[\*].SKU |

>[!NOTE]
>
>**products\[\*]** sta eseguendo un mapping di campi 1-1 tra i campi oggetto e il mapping di campi esplicito **products\[\*].productID** sta sovrascrivendo la copia predefinita.

>[!NOTE]
>
>Anche **products\[\*].productID** è mappato a **productListItems\[\*].SKU** oltre a **productListItems\[\*].\_id**. Questo è un esempio di un singolo campo di input mappato su più campi di output nello schema XDM. Mantieni la mappatura così com’è.

1. Mantieni il mapping di **prodotti\[\*].prezzo** a **productListItems\[\*].prezzoTotale**

## Aggiungere sostituzioni in alcuni campi

1. Sostituisci i mapping della copia oggetto con
   1. Mappatura di **prodotti\[\*].make** a **productListItems\[\*].\_devbc.make**
   2. Mapping di **prodotti\[\*].model** a **productListItems\[\*].\_devbc.model**

## Eliminare le sostituzioni in alcuni campi

1. Tieni presente che **productListItems.currencyCode** e **productListItems.quantity** sono compilati automaticamente.
1. Rimuovi i mapping **productListItems\[\*].quantity** e **productListItems\[\*].currencyCode**.
1. Le sostituzioni non si verificano e la copia dell&#39;oggetto viene eseguita con i campi passthrough.


## Riepilogo delle mappature, delle sostituzioni e delle eliminazioni della copia dell&#39;oggetto

| Colonna Source | Colonna XDM | Azione |
| -------------------------- | ----------------------------------- | -------------------------------------- |
| products\[\*] | productListItems\[\*] | `Add` |
| products\[\*].productID | productListItems\[\*].SKU | `Add` |
| products\[\*].productID | productListItems\[\*].\_id | `No change` |
| products\[\*].make | productListItems\[\*].\_devbc.make | `Change` |
| products\[\*].model | productListItems\[\*].\_devbc.model | `Change` |
| products\[\*].price | productListItems\[\*].priceTotal | `No change` |
| products\[\*].quantity | productListItems\[\*].quantity | `Remove` |
| products\[\*].currencyCode | productListItems\[\*].currencyCode | `Remove` |

## Verificare le mappature

Sono disponibili 2 set di mappature da verificare. In totale, dovresti disporre di 6 mappature dopo la rimozione di 2.



![Mappature risultanti per productListItems dopo l&#39;aggiunta delle sostituzioni della copia dell&#39;oggetto](assets/object-copy-mappings-resultant-mappings-for-productlistitems.png "Le mappature risultanti per ProductListItems\[*] dovrebbero essere simili al seguente")

![Seconda visualizzazione dei mapping risultanti per productListItems dopo le sostituzioni della copia dell&#39;oggetto](assets/object-copy-mappings-resultant-mappings-for-productlistitems--2.png)
