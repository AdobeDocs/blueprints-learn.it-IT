---
title: Visualizza schema
description: Visualizza la relazione di ricerca dello schema dell’account cliente con lo schema del piano tramite l’interfaccia utente dello schema e l’API Get Schema.
doc-type: article
solution: Experience Platform
exl-id: dae48ef4-f762-4173-8564-c1ad40c0109b
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# Visualizza schema

## Visualizza tramite l’interfaccia utente

1. Apri il browser e torna alla sezione `Schema -> Browse`.
1. Cerca lo schema `Sample Customer Schema - <your sandbox number>`
1. La relazione con `dep: Plan [Lookup]` è definita

![Schema cliente di esempio nell&#39;interfaccia utente di Experience Platform che mostra la relazione Dep: Plan Lookup](assets/view-schema-relationship-to-plan-lookup-schema.png)


## Visualizza tramite API

1. Selezionare l&#39;API `Step 4 - Get Customer Account Schema and its descriptors` facendo clic su di essa

   ![Passaggio 4 - Ottieni lo schema account cliente e la chiamata API ai relativi descrittori](assets/view-schema-step-4-get-schema-and-descriptors.png "Passaggio 4 - Ottieni lo schema account cliente e i relativi descrittori")



2. Nell&#39;URL della richiesta sostituire `<replace me>` con `$meta:altId` salvato dalla sezione precedente [Crea schema](../build-schema/create-schema.md) come mostrato di seguito

   ![Richiesta passaggio 4 con meta:altId aggiunta all&#39;URL](assets/view-schema-final-step-4-request.png "Richiesta passaggio 4 finale")



3. Salva la richiesta utilizzando il pulsante `Save`

4. Eseguire la richiesta facendo clic sul pulsante `Send`

A questo punto dovrebbe essere visualizzata una risposta `200 OK` e dovrebbe essere possibile passare alla fine dello schema creato per visualizzare l&#39;identità attraverso l&#39;obiettivo della struttura JSON XDM



![Descrittore di relazione visibile nello schema dell&#39;account cliente JSON](assets/view-schema-relationship-descriptor.png "Descrittore di relazione")



![Descrittore identità di riferimento visibile nel JSON dello schema dell&#39;account cliente](assets/view-schema-reference-identity-descriptor.png "Descrittore identità di riferimento")
