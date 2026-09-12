---
title: Creare altre identità
description: Utilizza l’API del registro dello schema per creare un descrittore di identità dell’indirizzo e-mail non primario per lo schema Account cliente.
doc-type: article
solution: Experience Platform
exl-id: 22c40299-fb93-4d41-a23b-f8629df3e7b9
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Creare altre identità

1. Fai clic sulla chiamata API `Step 2 - Create Email Address Identity for Customer Account Schema` nella cartella `XDM Schema Lab -> Create Identity Descriptors`

   >[!CAUTION]
   >
   >Non eseguire ancora la richiesta

   ![Passaggio 2 - Crea identità indirizzo e-mail per richiesta Postman schema account cliente](assets/create-other-identities-step-2-postman-request.jpeg "Passaggio 2 - Crea descrittore identità indirizzo e-mail")



1. Aggiorna il valore `xdm:sourceSchema` nel corpo della richiesta utilizzando `$id` salvato dal passaggio lab [Crea schema](../build-schema/create-schema.md)

1. Aggiorna il valore `xdm:isPrimary` nel corpo della richiesta a `false`

   SOLO ESEMPIO

   ```json
   {
     "@type": "xdm:descriptorIdentity",
     "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
     "xdm:sourceVersion": 1,
     "xdm:sourceProperty": "/personalEmail/address",
     "xdm:namespace": "Email",
     "xdm:property": "xdm:code",
     "xdm:isPrimary": false
   }
   ```

   >[!NOTE]
   >
   >Ricorda di aggiornare il nome tenant precedente (\_devbc) con il tuo



1. Salva la richiesta prima di continuare a utilizzare il pulsante `Save`

1. Eseguire l&#39;API facendo clic sul pulsante `Send`. Dovresti ora visualizzare una risposta `201 Created` come segue

![201 Risposta creata dopo la creazione del descrittore di identità dell&#39;indirizzo e-mail](assets/create-other-identities-201-created-response.png "Descrittore di identità riuscito per l&#39;indirizzo e-mail")
