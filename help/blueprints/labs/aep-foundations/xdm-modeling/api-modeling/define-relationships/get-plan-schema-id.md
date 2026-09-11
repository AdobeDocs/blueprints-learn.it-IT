---
title: Ottieni ID schema piano
description: Eseguire una query sull'API del Registro di sistema dello schema tenant per trovare e salvare il valore $id dello schema di ricerca del piano da utilizzare in un descrittore di relazione.
doc-type: article
solution: Experience Platform
exl-id: f66e0483-b5b3-4493-b752-c4e00211a8bd
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---


# Ottieni ID schema piano

## Elenca tutti gli schemi tenant

1. Fai clic sulla richiesta API `Step 1 - Get Lookup Schemas` nella cartella `XDM Schema Lab -> Create Relationship Descriptors`
1. Eseguire l&#39;API facendo clic sul pulsante `Send`

![Passaggio 1 - Ottieni richiesta API per schemi di ricerca](assets/get-plan-schema-id-step-1-get-lookup-schemas.jpeg "Passaggio 1 - Ottieni schemi di ricerca")

>[!NOTE]
>
>Questa chiamata GET recupera tutti gli schemi esistenti nella parte &quot;tenant&quot; del registro degli schemi (ad esempio gli schemi creati personalizzati). È sufficiente cercare lo schema **Piano** per poterlo correlare allo schema dell&#39;account cliente.



## Identificare lo schema del piano

1. Cerca lo schema `dep: Plan [Lookup] ` nella risposta delle chiamate
1. Copia `$id` dello schema e salvalo in un punto qualsiasi per riferimento futuro

![Dep: Schema $id ricerca piano nella risposta API](assets/get-plan-schema-id-dep-lookup-plan-schema-sid.png "dep: Schema piano ricerca $id")

>[!NOTE]
>
>Questo schema deve essere già pre-distribuito nella sandbox

>[!WARNING]
>
>Non continuare finché non hai salvato `$id` dello schema da qualche parte.  Sarà necessario in seguito per creare il descrittore di relazione
