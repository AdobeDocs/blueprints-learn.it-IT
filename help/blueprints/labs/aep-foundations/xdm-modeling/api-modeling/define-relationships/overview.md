---
title: Definire le relazioni
description: Scopri come i descrittori di relazione collegano uno schema cliente a uno schema di ricerca nel registro dello schema XDM tramite l’API.
doc-type: overview-page
solution: Experience Platform
exl-id: be672c84-09ac-4941-b40e-da7bd3fd6704
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# Definire le relazioni

## Descrittori di relazione

Per creare una relazione da uno schema a un altro, è necessario creare un descrittore di relazione nel registro dello schema. Di seguito è riportato un esempio di corpo del descrittore dello schema:

Descrittore uno-a-uno

```json
{
  "@type": "xdm:descriptorOneToOne",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:destinationSchema": "https://ns.adobe.com/devbc/schemas/6470f71181cf87aa39c2c2c43824eaa15f523652f7f88ff7",
  "xdm:destinationVersion": 1
}
```

Descrittore dell’identità di riferimento

```json
{
  "@type": "xdm:descriptorReferenceIdentity",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/6470f71181cf87aa39c2c2c43824eaa15f523652f7f88ff7",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:identityNamespace": "planID"
}
```

## Il tuo obiettivo

Creare identità di relazione per lo schema dell’account cliente. Dopo aver eseguito i passaggi della sezione successiva, lo schema dovrebbe presentarsi come segue.

![Schema dell&#39;account del cliente che mostra i descrittori di relazione e identità di riferimento](assets/overview-schema-with-relationship-identities.png)
