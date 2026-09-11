---
hold: true
title: Riprovare un flusso di dati non riuscito
description: Riprovare l'esecuzione di un flusso di dati non riuscito in modo che i dati di origine vengano rielaborati in base a regole di mappatura aggiornate in un nuovo flusso di dati.
doc-type: article
solution: Experience Platform
exl-id: 83ecf037-e524-4887-b833-5ed96af40419
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---


# Riprovare un flusso di dati non riuscito

Per ritentare un flusso di lavoro, eseguire le operazioni seguenti:

1. Passa a **Origini -> Flussi dati -> \[Nome flusso dati] -> \[Esecuzione non riuscita]**
1. Evidenzia l’esecuzione del flusso di dati che non è riuscito a visualizzare la barra corretta.
1. Fai clic su **Riprova**. Il nuovo tentativo acquisirà la copia dei dati associati all’esecuzione non riuscita e ad essa verranno applicate le nuove regole di mappatura

![Nuovo tentativo di esecuzione di un flusso di dati non riuscito dalla barra corretta](assets/retry-a-failed-dataflow.png)

>[!NOTE]
>
>Tieni presente che quando tenti di nuovo un flusso di dati non riuscito, viene creato ed eseguito un nuovo flusso di dati. Verrà visualizzato nella parte superiore dell’elenco dei flussi di dati
