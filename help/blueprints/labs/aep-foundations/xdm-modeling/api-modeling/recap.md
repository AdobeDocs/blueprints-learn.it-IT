---
title: Riassunto
description: Esamina i passaggi del laboratorio di modellazione API, dalla creazione dello schema dell’account cliente fino all’applicazione di patch JSON, al contrassegno delle identità e alla creazione della relazione di ricerca.
doc-type: article
solution: Experience Platform
exl-id: 0279cd68-af7b-43b4-8c6c-d8f8f96f0c0e
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%
---

# Riassunto

Il video seguente riassume il modo in cui hai creato lo schema, le identità e i descrittori di relazione tramite chiamate API e dimostra come la patch JSON viene utilizzata per modificare uno schema.

>[!VIDEO](https://video.tv.adobe.com/v/3459564/?quality=12&learn=on)

>[!SUCCESS]
>
>Congratulazioni! Comprendere come funziona ti aiuta a capire il sistema nel suo complesso.



## Creato schema account cliente

Hai creato lo schema da `$ref` sia per i gruppi di campi creati da Adobe che per il tuo gruppo di campi personalizzato (ovvero tenant). Hai anche `$ref` la classe che lo schema deve rappresentare (ovvero Profilo individuale XDM)

![Schema dell&#39;account cliente che fa riferimento a gruppi di campi e classi tramite $ref](assets/recap-customer-account-schema.png "Schema dell&#39;account cliente")


## Applicazione della patch JSON allo schema dell’account cliente

È stato utilizzato il metodo JSON Patch per modificare lo schema dell’account cliente per aggiungere un nuovo campo all’oggetto del piano. A tale scopo, è necessario applicare la patch al gruppo di campi personalizzato `$ref` denominato `Customer Account Details` definito in [Crea gruppi di campi personalizzati](build-schema/create-custom-field-groups.md), anziché applicare la patch allo schema stesso.

![Richiesta patch JSON aggiunta di un campo planDescription al gruppo di campi Dettagli account cliente](assets/recap-json-patch-plan-description-field.png "Patch JSON del campo planDescription")


## Campi di identità contrassegnati

Per creare `Identity Descriptors` per i campi `_devbc.customerID` e `personalEmail.address` nello schema dell&#39;account cliente, sono state eseguite due delle stesse `POST` chiamate.

1. Il campo `_devbc.customerID` è stato impostato come identità **primaria**
1. Il campo `personalEmail.address` è **non impostato** come primario

![Schema dell&#39;account cliente che mostra i descrittori di identità primari e non primari](assets/recap-marked-identity-fields.png "Campi di identità dello schema dell&#39;account cliente")

## Relazione di ricerca creata

L’ultimo passaggio è stato creare la relazione tra gli schemi Account cliente e Piano dal laboratorio XDM ERD on Paper. Questo richiedeva di creare sia un descrittore di relazione (ovvero come correlare lo schema `Customer Account` allo schema `dep: Plan [Lookup]`) che un descrittore di identità di riferimento nello schema dell&#39;account cliente.

![Descrittore di relazione e descrittore di identità di riferimento che collegano l&#39;account del cliente allo schema di ricerca del piano](assets/recap-relationship-reference-identity-descriptors.png "Descrittori di identità di relazione e di riferimento")

>[!NOTE]
>
>Il descrittore `referenceIdentity` indica al profilo cliente in tempo reale quale campo nello schema `Customer Account` corrisponde allo spazio dei nomi dell&#39;identità. Quando si definisce uno schema di ricerca, è necessario contrassegnare un campo come identità primaria e assegnargli uno spazio dei nomi con un tipo di `non-person`.
