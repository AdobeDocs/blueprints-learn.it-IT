---
hold: true
title: Visualizza schema
description: Visualizza uno schema cliente appena creato sia nell’interfaccia utente di Experience Platform che tramite una chiamata Get Schema API.
doc-type: article
solution: Experience Platform
exl-id: 29302546-46dc-4c97-8fd8-deab6977635c
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---


# Visualizza schema

## Visualizza tramite l’interfaccia utente

1. Apri il browser e torna alla sezione `Schema -> Browse`.

>[!NOTE]
>
>Aggiorna l’interfaccia utente per visualizzarla, poiché è stata appena creata e devi eseguire nuovamente una query nel registro dello schema

2. Cerca lo schema `Sample Customer Schema - <your sandbox number>`

3. La classe richiesta e i gruppi di campi associati vengono aggiunti allo schema

![Schema cliente di esempio visualizzato nell&#39;interfaccia utente di Experience Platform con i relativi gruppi di campi e classi](assets/view-schema-ui-view-of-sample-customer-schema.png "Visualizzazione dell&#39;interfaccia utente dello schema cliente di esempio")


## Visualizza tramite API

1. Selezionare l&#39;API `Step 5 - Get Customer Account Schema` facendo clic su di essa.
1. Nell&#39;URL della richiesta sostituisci `<replace me>` con `$meta:altId` salvato dalla sezione precedente (Crea schema) alla fine della chiamata come mostrato di seguito
1. Salva le modifiche apportate alla richiesta
1. Eseguire la richiesta facendo clic sul pulsante `Send`

![Passaggio 5 - Ottieni chiamata API schema account cliente](assets/view-schema-step-5-get-customer-account-schema.jpeg "Passaggio 5 - Ottieni schema account cliente")



Esempio della richiesta finale dopo l&#39;aggiunta di `$meta:altId`

![Richiesta passaggio 5 con meta:altId aggiunta all&#39;URL](assets/view-schema-final-step-5-request.png "Richiesta passaggio 5 finale")



Se hai ricevuto una risposta `200 OK`, dovresti essere in grado di sfogliare lo schema creato appena attraverso l&#39;obiettivo nella struttura JSON XDM

![200 Risposta OK che mostra il codice JSON](assets/view-schema-sample-customer-account-schema.png "Sample Customer Account Schema") completo dell&#39;account cliente
