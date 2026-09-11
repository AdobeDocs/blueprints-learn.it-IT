---
hold: true
title: Crea schema
description: Utilizza l’API del registro degli schemi per assemblare uno schema del cliente da una classe di profilo e da riferimenti a gruppi di campi standard e personalizzati.
doc-type: article
solution: Experience Platform
exl-id: 78ebc5b8-d088-48e9-857f-87085a87a280
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# Crea schema

## Modificare il corpo dell’API

>[!CAUTION]
>
>**Non eseguire la chiamata...eppure**

1. Fare clic sulla chiamata API `Step 4 - Create Customer Account Schema` nella cartella `XDM Schema Lab -> Create Schema`.

![Passaggio 4 - Creazione della chiamata API dello schema account cliente nella raccolta Postman](assets/create-schema-click-on-the-step-4-create-customer-account-schema.png)



&#x200B;2. Apri il corpo della chiamata e visualizza la struttura di come è definito uno schema. Ricorda che uno schema è sempre composto da una sola (1) classe e da uno o più gruppi di campi.

&#x200B;3. Compila i campi `title` e `description` nel corpo dello schema con quanto segue:

- Titolo -> `Sample Customer Schema - <your sandbox number>`
- Descrizione -> `Sample Customer Schema - <your sandbox number>`

&#x200B;4. Compilare i campi `$ref` con i `$ids` salvati dalle precedenti sezioni del laboratorio completate: [Creare gruppi di campi personalizzati](./create-custom-field-groups.md) e [Ottenere la classe del profilo](./get-profile-class.md). È necessario disporre di $id per ciascuno dei seguenti elementi:

- Classe -> Profilo individuale XDM
- Gruppo di campi -> Dettagli demografici
- Gruppo di campi -> Dettagli di contatto personali
- Gruppo di campi -> Dettagli su consenso e preferenze
- Gruppo di campi (personalizzato) -> Dettagli account cliente

![Corpo della richiesta schema vuoto prima di aggiungere riferimenti a classi e gruppi di campi](assets/create-schema-empty-schema-api-body.png "Corpo API schema vuoto")



&#x200B;5. Esamina il corpo finale e assicurati che sia simile a questo

![Corpo della richiesta dello schema completato con titolo, descrizione e tutti i valori $ref popolati](assets/create-schema-example-of-final-body-payload.png "Esempio di payload del corpo finale")

>[!NOTE]
>
>L&#39;ordine di `$refs` non ha importanza, né la posizione di `title` e `description` all&#39;interno del corpo.



## Eseguire l’API

1. Salva le modifiche apportate alla richiesta API prima di continuare.
1. Eseguire l&#39;API facendo clic sul pulsante `Send`

In caso di esito positivo, la risposta per la creazione dello schema dovrebbe ottenere lo stato `201 Created` e avere un aspetto simile all&#39;immagine seguente

>[!WARNING]
>
>Non eseguire nuovamente la richiesta in caso di esito positivo

![201 Risposta creata dopo la creazione dello schema tramite l&#39;API del passaggio 4](assets/create-schema-sample-response-from-executing-the-step-4-api.png "Risposta di esempio dall&#39;esecuzione dell&#39;API del passaggio 4")


## Individua e salva lo schema $id

1. Dopo aver eseguito la richiesta API, copia `$id` e `$meta:altId` dalla risposta
1. Salvare i valori in un punto qualsiasi per poterli riutilizzare in un secondo momento

>[!WARNING]
>
>Non continuare finché non avrai salvato `$id` e `$meta:altId` da qualche parte.  Saranno necessarie nelle prossime fasi del laboratorio

>[!TIP]
>
>**Congratulazioni! Hai appena creato uno schema utilizzando solo le API**
