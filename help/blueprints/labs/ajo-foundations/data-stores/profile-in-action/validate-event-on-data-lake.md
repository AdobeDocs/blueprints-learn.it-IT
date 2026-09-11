---
hold: true
title: Convalida evento su Data Lake
description: Scopri come eseguire una query sul Data Lake per verificare che un evento web in streaming sia stato scritto nel set di dati corretto.
doc-type: article
solution: Experience Platform
exl-id: 14445089-aa3c-4cce-9d33-80032b6f9868
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---


# Convalida evento su Data Lake

## Finalità di apprendimento

Verifica che l’evento web sia stato scritto nel Data Lake di Experience Platform.

## Convalida evento

> [!NOTE]
>
>Alla fine i dati verranno visualizzati nel Data Lake.  **L&#39;operazione potrebbe richiedere fino a 60 minuti**.  Sappiamo che il set di dati è abilitato per il profilo e quindi l’evento creerà un frammento di profilo.
>
>Puoi trovare ed eseguire query sul set di dati web.

1. Vai a **Query** e **Crea query**

![Crea schermata Query nella sezione Query](assets/validate-event-on-data-lake-create-query.png)

2. Copia il file SQL e incollalo nella query

```sql
SELECT identityMap['email'][0].id, * FROM dep_web
where identityMap['email'][0].id = 'henry.creel@emailsim.io'
```

3. **Esegui** query

> [!NOTE]
>
>**Ricorda**: i dati verranno infine visualizzati nel Data Lake.  **L&#39;operazione potrebbe richiedere fino a 60 minuti**.
>
>Non è necessario attenderne la visualizzazione. Puoi tornare a questo passaggio e controllare più tardi.



![Risultati della query che mostrano l&#39;evento web in streaming nel data lake](assets/validate-event-on-data-lake-query-results.png)

## Riassunto

Il record dell’evento viene visualizzato nel set di dati appropriato.
