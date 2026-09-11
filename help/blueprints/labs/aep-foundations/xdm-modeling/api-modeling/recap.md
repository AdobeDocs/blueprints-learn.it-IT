---
hold: true
title: Riassunto
description: Esamina i passaggi del laboratorio di modellazione API, dalla creazione dello schema dell’account cliente fino all’applicazione di patch JSON, al contrassegno delle identità e alla creazione della relazione di ricerca.
doc-type: article
solution: Experience Platform
exl-id: 0279cd68-af7b-43b4-8c6c-d8f8f96f0c0e
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Riassunto

Il video seguente riassume il modo in cui hai creato lo schema, le identità e i descrittori di relazione tramite chiamate API e dimostra come la patch JSON viene utilizzata per modificare uno schema.

>[!VIDEO](https://video.tv.adobe.com/v/3459564/?quality=12&learn=on)

&#x200B;> [!TIP]
>
>Prima di tutto congratulazioni! Costruire cose tramite API non è facile, ma comprendere come funziona ti aiuterà a comprendere il sistema nel suo complesso. Kudos!



## Creato schema account cliente

Hai creato lo schema da `$ref` sia con i gruppi di campi creati da Adobe che con il tuo gruppo di campi creato personalizzato (ad esempio tenant).  Hai anche `$ref` per la classe che lo schema deve rappresentare (esempio: Profilo individuale XDM)

![Schema dell&#39;account cliente che fa riferimento a gruppi di campi e classi tramite $ref](assets/recap-customer-account-schema.png "Schema dell&#39;account cliente")


## La patch JSON applica lo schema dell’account cliente

È stato utilizzato il metodo JSON Patch per modificare lo schema dell’account cliente per aggiungere un nuovo campo all’oggetto del piano. A tale scopo, è necessario applicare la patch al gruppo di campi personalizzato `$ref` denominato `Customer Account Details` definito in [Crea gruppi di campi personalizzati](build-schema/create-custom-field-groups.md), anziché applicare la patch allo schema stesso.

![Richiesta patch JSON aggiunta di un campo planDescription al gruppo di campi Dettagli account cliente](assets/recap-json-patch-plan-description-field.png "Patch JSON del campo planDescription")


## Campi di identità contrassegnati

In questo passaggio sono state eseguite due delle stesse chiamate `POST` per creare `Identity Descriptors` per i campi `_devbc.customerID` e `personalEmail.address` nello schema dell&#39;account cliente.

1. Il campo `_devbc.customerID` è stato impostato come identità **primaria**
1. Il campo `personalEmail.address` è **non impostato** come primario

![Schema dell&#39;account cliente che mostra i descrittori di identità primari e non primari](assets/recap-marked-identity-fields.png "Campi di identità dello schema dell&#39;account cliente")

## Relazione di ricerca creata

L’ultimo passaggio è stato creare la relazione tra gli schemi Account cliente e Piano dal laboratorio XDM ERD on Paper.  È necessario creare sia un descrittore di relazione (ad esempio, come correlare lo schema `Customer Account` allo schema `dep: Plan [Lookup]`) sia un descrittore di identità di riferimento nello schema dell&#39;account cliente.

![Descrittore di relazione e descrittore di identità di riferimento che collegano l&#39;account del cliente allo schema di ricerca del piano](assets/recap-relationship-reference-identity-descriptors.png "Descrittori di identità di relazione e di riferimento")

>[!NOTE]
>
>Il descrittore `referenceIdentity` indica al profilo cliente in tempo reale quale campo nello schema `Customer Account` corrisponde allo spazio dei nomi dell&#39;identità. Quando si definisce uno schema di ricerca, è necessario contrassegnare un campo come identità primaria e assegnargli uno spazio dei nomi con un tipo di `non-person`.
