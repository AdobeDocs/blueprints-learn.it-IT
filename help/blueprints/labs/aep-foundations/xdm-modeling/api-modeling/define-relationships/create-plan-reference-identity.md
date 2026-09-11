---
hold: true
title: Crea identità riferimento piano
description: Utilizza l’API del registro dello schema per creare un descrittore di identità di riferimento nello schema di ricerca in modo che possa essere utilizzato nella segmentazione batch.
doc-type: article
solution: Experience Platform
exl-id: b3b8f480-af3b-4bf8-b74e-3842f59691b6
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---


# Crea identità riferimento piano

1. Fai clic sulla richiesta API `Step 3 - Reference Descriptor for Plan` nella cartella `XDM Schema Lab -> Create Relationship Descriptors`

>[!CAUTION]
>
>Non eseguire ancora la richiesta

![Passaggio 3 - Descrittore di riferimento per la richiesta API dello schema del piano](assets/create-plan-reference-identity-step-3-descriptor-request.jpeg "Passaggio 3 - Descrittore di riferimento per lo schema del piano")



&#x200B;2. Aggiorna le seguenti proprietà nel corpo della chiamata API.

- Aggiorna il valore della proprietà `xdm:sourceSchema` in `$id` dello schema `Customer Account` salvato dal passaggio [Crea schema](../build-schema/create-schema.md)
- Aggiorna il valore di `xdm:sourceProperty` nel percorso del campo `planID` dallo schema `Customer Account`

>[!NOTE]
>
>Utilizza il valore di notazione del punto del campo `planId` dallo schema `dep: Lookup Plan` e sostituisci `.` con `/`
>
>Non dimenticare `/` iniziale 😄

SOLO ESEMPIO

```json
{
  "@type": "xdm:descriptorReferenceIdentity",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:identityNamespace": "planID"
}
```

>[!NOTE]
>
>Ricordati di aggiornare il nome tenant precedente (\_devbc) con il tuo



&#x200B;3. Salva la richiesta prima di continuare a utilizzare il pulsante `Save`

&#x200B;4. Eseguire l&#39;API facendo clic sul pulsante `Send`

Dovresti ora visualizzare una risposta `201 Created` come segue

![201 Risposta creata dopo la creazione del descrittore identità di riferimento Dep: Plan Lookup](assets/create-plan-reference-identity-dep-plan-descriptor-result.png "dep: descrittore identità di riferimento Plan Lookup")

>[!NOTE]
>
>Un descrittore di identità di riferimento viene sempre definito nello schema di ricerca (ad esempio sourceSchema)

>[!NOTE]
>
>I descrittori di identità di riferimento vengono creati automaticamente nel backend quando crei relazioni dall’interfaccia utente dello schema. **È necessario crearli in modo esplicito solo quando si utilizzano le API per creare schemi**

>[!TIP]
>
>Fantastico! Hai appena creato tutti i descrittori richiesti per correlare lo schema `dep: Lookup Plan` allo schema `Customer Account` e hai abilitato il riferimento a esso durante la segmentazione batch
