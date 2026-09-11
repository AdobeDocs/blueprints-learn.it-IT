---
title: Crea relazione schema
description: Utilizza l’API del registro dello schema per creare un descrittore di relazione uno-a-uno che colleghi lo schema Account cliente a uno schema di piano di ricerca.
doc-type: article
solution: Experience Platform
exl-id: c9079585-fff1-4ee1-8992-93825fcde759
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# Crea relazione schema

1. Fai clic sulla richiesta API `Step 2 - Relationship Descriptor Customer Account To Plan` nella cartella `XDM Schema Lab -> Create Relationship Descriptors`

   >[!CAUTION]
   >
   >Non eseguire ancora la richiesta

   ![Passaggio 2 - Richiesta dell&#39;account cliente del descrittore di relazione al piano API](assets/create-schema-relationship-step-2-descriptor-request.png "Passaggio 2 - Account cliente del descrittore di relazione al piano")



2. Aggiorna le seguenti proprietà nel corpo della chiamata API.

- Imposta il valore della proprietà `xdm:sourceSchema` su `$id` dello schema dell&#39;account cliente salvato dal passaggio lab [Crea schema](../build-schema/create-schema.md)
- Impostare il valore di `xdm:sourceProperty` sul percorso del campo `planID` dallo schema account cliente.
- Imposta il valore della proprietà `xdm:destinationSchema` su `$id` dello schema `dep: Lookup Plan` salvato nel primo passaggio

>[!NOTE]
>
>Utilizza il valore di notazione del punto del campo planId dallo schema account cliente e sostituisci `.` con `/`
>
>
>Non dimenticare `/` iniziale 😄

SOLO ESEMPIO

```json
{
  "@type": "xdm:descriptorOneToOne",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:destinationSchema": "https://ns.adobe.com/devbc/schemas/6470f71181cf87aa39c2c2c43824eaa15f523652f7f88ff7"
,
  "xdm:destinationVersion": 1
}
```

>[!NOTE]
>
>Ricordati di aggiornare il nome tenant precedente (\_devbc) con il tuo



3. Salva la richiesta prima di continuare a utilizzare il pulsante `Save`

4. Eseguire l&#39;API facendo clic sul pulsante `Send`

Dovresti ora visualizzare una risposta `201 Created` come segue

![201 Risposta creata dopo la creazione del descrittore di relazione tra account cliente e pianificazione](assets/create-schema-relationship-customer-account-plan-descriptor.png "Account cliente - Descrittore di relazione piano")

>[!NOTE]
>
>Ricorda che Real-Time Customer Profile (e tutto Experience Platform) supporta solo ciò che chiamiamo **un (1) hop join** dagli schemi XDM Individual Profile o XDM Experience Event (ovvero puoi creare solo una (1) relazione di ricerca a livello)

>[!NOTE]
>
>Si è notato che il descrittore di relazione `@type` è impostato su un valore di `OneToOne`? La relazione tra il conto cliente e la tabella Piano nell&#39;ERD XDM su carta non è 1\:N?  Cosa sta succedendo?
>
>
>Il profilo cliente in tempo reale è progettato per descrivere le caratteristiche e i comportamenti di una singola persona.  Pertanto, da un singolo obiettivo persona una tabella di ricerca è **only** **ever** definita come una relazione 1:1 durante la segmentazione.
>
>Va bene se ti fa male il cervello...
