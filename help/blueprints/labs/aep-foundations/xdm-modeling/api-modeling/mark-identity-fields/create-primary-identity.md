---
title: Creare un’identità primaria
description: Utilizza l’API del registro dello schema per creare un descrittore di identità customerID primario per lo schema dell’account cliente.
doc-type: article
solution: Experience Platform
exl-id: db690081-e857-4875-8bb9-7ac197d73cab
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---


# Creare un’identità primaria

1. Fai clic sulla richiesta API `Step 1 - Create Primary Identity for Customer Account Schema` nella cartella `XDM Schema Lab -> Create Identity Descriptors`

   ![Passaggio 1 - Crea identità primaria per la richiesta Postman dello schema dell&#39;account cliente](assets/create-primary-identity-step-1-postman-request.jpeg "Passaggio 1 - Crea identità primaria per lo schema dell&#39;account cliente")

   >[!CAUTION]
   >
   >Non eseguire ancora la richiesta



1. Aggiorna il valore `xdm:sourceSchema` nel corpo della richiesta utilizzando `$id` salvato dal passaggio lab [Crea schema](../build-schema/create-schema.md)

1. Aggiorna il valore `xdm:isPrimary` nel corpo della richiesta a `true`

   SOLO ESEMPIO

   ```json
   {
     "@type": "xdm:descriptorIdentity",
     "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
     "xdm:sourceVersion": 1,
     "xdm:sourceProperty": "/_devbc/customerID",
     "xdm:namespace": "customerID",
     "xdm:property": "xdm:code",
     "xdm:isPrimary": true
   }
   ```

   >[!NOTE]
   >
   >Ricorda di aggiornare il nome tenant precedente (\_devbc) con il tuo



1. Salva la richiesta prima di continuare a utilizzare il pulsante `Save`

1. Eseguire l&#39;API facendo clic sul pulsante `Send`. Dovresti ora visualizzare una risposta `201 Created` come segue

![201 Risposta creata dopo la creazione del descrittore di identità primaria](assets/create-primary-identity-201-created-response.png "Il descrittore di identità primaria è stato creato")

>[!TIP]
>
>Congratulazioni!  Hai appena creato un descrittore di identità primaria nello schema
