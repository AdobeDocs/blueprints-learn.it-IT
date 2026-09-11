---
hold: true
title: Creare gruppi di campi personalizzati
description: Utilizza l’API del registro dello schema per creare un gruppo di campi Dettagli account cliente personalizzato e salvarne il valore $id da utilizzare in uno schema successivo.
doc-type: article
solution: Experience Platform
exl-id: d3262db9-7c0b-476a-843f-1a2c224ee792
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Creare gruppi di campi personalizzati

## Struttura del gruppo di campi

Un gruppo di campi è sempre composto dai campi seguenti. Questo aspetto sarà visibile nella richiesta nel passaggio successivo.

| Valori obbligatori | Descrizione |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| titolo | Nome del gruppo di campi che si desidera creare nel registro dello schema. Il nome DEVE ESSERE UNIVOCO. |
| descrizione | Breve descrizione dello scopo del gruppo di campi |
| tipo | Sempre un oggetto |
| meta\:intendedToExtend | Definisce con quali classi può essere utilizzato il gruppo di campi. Il valore `$id` fa sempre riferimento alle classi |
| allOf | Descrive le risorse che possono essere incluse nel gruppo di campi. Per i campi definiti personalizzati il percorso è sempre `#/definitions/customFields` |
| definitions.customFields... | Si tratta della struttura di schema JSON predefinita necessaria per creare gruppi di campi personalizzati. Deve corrispondere a `allOf` dall&#39;alto |
| \&lt;TENANT\_NAME> | Il nome tenant (ovvero il nome univoco) viene creato durante il processo di provisioning. In questo modo, eventuali personalizzazioni effettuate non entreranno in conflitto con le modifiche del registro di sistema dello schema di Adobe esistenti o future |



## Crea gruppo di campi Dettagli account cliente

1. Fai clic sulla chiamata API per la richiesta `Step 2 - Create Customer Account Details Field Group` nella cartella `XDM Schema Lab -> Create Schema`



![Passaggio 2 - Crea richiesta API gruppo di campi Dettagli account cliente](assets/create-custom-field-groups-step-2-field-group-request.png "Passaggio 2 - Crea gruppo di campi Dettagli account cliente")



Rivedi il corpo della richiesta prima di eseguire. Si noti che i campi obbligatori indicati nella sezione Struttura del gruppo di campi sono visualizzati come segue:

![Campi obbligatori di un gruppo di campi personalizzato come mostrato nel corpo della richiesta](assets/create-custom-field-groups-field-group-structure.png "Struttura del gruppo di campi")



![La proprietà allOf che fa riferimento al percorso delle definizioni dei campi personalizzati](assets/create-custom-field-groups-field-group-structure-allof.png "Struttura del gruppo di campi allOf")

>[!NOTE]
>
>Osserva come nell&#39;immagine a destra sopra `allOf` si fa riferimento al percorso di &quot;/definitions/customFields&quot;.  Deve corrispondere alla struttura definita nello schema (immagine a sinistra), in quanto indica al sistema XDM dove individuare gli oggetti creati personalizzati.
>
>![Confronto che evidenzia come il percorso allOf deve corrispondere al percorso delle definizioni dei campi personalizzati](assets/create-custom-field-groups-allof-path-highlighted.png)



Inoltre, osserva come ogni campo specifico del foglio di mappatura viene convalidato all’interno della struttura JSON XDM.



![Notazione del punto del piano del foglio di mapping convertita in struttura JSON XDM](assets/create-custom-field-groups-plan-dot-notation-to-xdm-json.png "Notazione dei punti del piano in JSON XDM")



![Mappatura dell&#39;account del foglio e della notazione del punto ID cliente convertiti in XDM](assets/create-custom-field-groups-account-customer-id-dot-notation-to-xdm.png "Notazione del punto dell&#39;account e dell&#39;ID cliente in XDM")



2. Aggiorna `title` e `description` per il gruppo di campi utilizzando il seguente formato: `Customer Account Details - Sandbox <your number here>`



![Titolo di esempio e descrizione compilati per il gruppo di campi personalizzato](assets/create-custom-field-groups-field-group-title-description-example.png "Titolo gruppo di campi e descrizione")



3. Eseguire facendo clic sul pulsante `Send`.  Dovresti trovare una risposta simile alla schermata seguente.

4. Copia il valore `$id` del gruppo di campi Dettagli account cliente appena creato.

![Risposta API riuscita dopo la creazione del gruppo di campi personalizzato](assets/create-custom-field-groups-step-2-create-custom-field-group-success.png "Passaggio 2 - Creazione del gruppo di campi personalizzato completata")

>[!WARNING]
>
>Non continuare finché non hai salvato `$id` da qualche parte.  Sarà necessario in seguito per creare lo schema Account cliente
>
>
