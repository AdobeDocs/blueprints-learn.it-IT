---
hold: true
title: Errori di debug
description: Utilizza la diagnostica degli errori di anteprima per analizzare un’esecuzione non riuscita del flusso di dati e distinguere gli errori di formato INGEST dagli avvisi di conversione MAPPER.
doc-type: article
solution: Experience Platform
exl-id: beee191b-a860-494c-873f-ab2e407ffbf5
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---


# Errori di debug

## Anteprima diagnostica errori

Dopo alcuni minuti, dovresti notare che lo **Stato** mostra un errore. Eseguire un drill-through nei dettagli dell&#39;errore per vedere la causa dell&#39;errore.

1. Fai clic sulla data **Inizio esecuzione flusso di dati**
1. Fai clic su **Anteprima diagnostica errori** per visualizzare i dettagli specifici di ogni riga che non riesce

![Stato esecuzione flusso di dati che mostra un errore](assets/debugging-errors-dataflow-run-failure.png "Errore esecuzione flusso di dati")

![Collegamento per l&#39;anteprima della diagnostica degli errori nella schermata dei dettagli di esecuzione del flusso di dati](assets/debugging-errors-preview-error-diagnostics-link.png "Anteprima della diagnosi degli errori")



La schermata visualizzata mostra una serie di dettagli sul significato dei codici di errore con il messaggio di errore completo e la riga che ha avuto esito negativo.

![Schermata dei dettagli della diagnostica degli errori che mostra i codici di errore, i messaggi e la riga non riuscita](assets/debugging-errors-error-diagnostics-detail-screen.png "Anteprima della diagnostica degli errori")

>[!NOTE]
>
>Scorri verso destra per visualizzare i dati di origine associati a questo codice di errore



## Informazioni sui tipi di errore

### Errore INGEST-XXXX-XXX

Questo errore si verifica perché **person.bornDayAndMonth** è previsto nel formato di un mese di due cifre più un giorno di due cifre (ad esempio, il 27 aprile deve essere formattato come 04-27)

```none
The value (9-27) does not conform to the specified
regex pattern: [0-1][0-9]-[0-9][0-9] in field: 
person.birthDayAndMonth of type: String
```

>[!CAUTION]
>
>Nota che person.bornDayAndMonth non è un campo obbligatorio ma la non conformità alle espressioni regolari viene trattata dal sistema come un &quot;problema di corruzione dei dati&quot; e rappresenta un errore grave.



### Errore MAPPER-XXXX-XXX

Questo errore si verifica perché il campo di origine di **createDate** contiene valori stringa di `Created on 2022-04-22T19:34:17Z`. Impossibile convertire automaticamente questo valore in una data a causa del testo all&#39;inizio: `Created on`. Per pulire i dati è necessario utilizzare un campo calcolato.

```none
Error transforming data for destination path 
_dep.account.createDate. Details: Unable to convert 
Created on 2023-09-24T10:19:58Z to schema type DATE_TIME
```

> [!NOTE]
>
>Questo errore non è grave, in quanto genera solo avvisi durante la mappatura. L’esecuzione del flusso di dati non ha esito negativo per questo motivo, pertanto questa esercitazione non corregge questo errore.
