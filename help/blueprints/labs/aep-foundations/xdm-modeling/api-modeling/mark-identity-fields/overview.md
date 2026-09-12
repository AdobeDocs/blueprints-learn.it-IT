---
title: Contrassegna campi di identità
description: Scopri come i descrittori di identità contrassegnano i campi dello schema come identità primarie o non primarie utilizzando l’API del registro di schema XDM.
doc-type: overview-page
solution: Experience Platform
exl-id: f6498584-0f4d-4baf-86b5-b00cc78e2ba7
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# Contrassegna campi di identità

## Descrittori identità

Per contrassegnare un campo come identità è necessario creare un descrittore di identità nel registro dello schema. Di seguito è riportato un esempio di corpo del descrittore dello schema:

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

- **@type** -> sempre impostato su `xdm:descriptorIdentity`
- **xdm\:sourceSchema** -> `$id` dello schema in cui esiste il campo
- **xdm\:sourceVersion** -> sempre 1
- **xdm\:sourceProperty** -> percorso del campo nello schema
- **xdm\:namespace** -> il codice dello spazio dei nomi dell&#39;identità in cui deve essere archiviato il campo
- **xdm\:proprietà** -> sempre `xdm:code`
- **xdm\:isPrimary** -> se un&#39;identità primaria allora `true` altrimenti è `false`


## Il tuo obiettivo

Creare identità primarie e non primarie per lo schema dell&#39;account cliente. Dopo aver eseguito i passaggi della sezione successiva, lo schema dovrebbe presentarsi come segue.

![Schema dell&#39;account del cliente dopo la creazione di descrittori di identità primari e non primari](assets/overview-schema-with-primary-and-non-primary-identities.png)
