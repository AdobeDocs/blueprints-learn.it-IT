---
hold: true
title: Monitoraggio e debug degli errori
description: Utilizza il dashboard di monitoraggio end-to-end di Streaming per identificare e interpretare gli errori INGEST, DCVS e MAPPER in un flusso di dati in streaming.
doc-type: article
solution: Experience Platform
exl-id: 268abf15-14ac-45e3-8cd7-8d180ee5b1e3
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---


# Monitoraggio e debug degli errori

>[!NOTE]
>
>Il monitoraggio dell’acquisizione in streaming avviene a livello di flusso di dati, il che significa che quando la visualizzi nell’interfaccia utente stai visualizzando il data lake.  Questo significa che i batch vengono visualizzati (l’elaborazione dei microbatch dalla pipeline di streaming) all’incirca ogni 60 minuti.  Pertanto, se non visualizzi i dati nel profilo cliente in tempo reale, devi attendere fino a 60 minuti per diagnosticare il problema.



## Visualizza dashboard di monitoraggio

1. Passa a **Monitoraggio->Streaming end-to-end** e individua il **flusso di dati**:

![Individuazione del flusso di dati in streaming nella sezione Monitoraggio](assets/monitoring-and-debugging-errors-locate-your-dataflow-in-monitoring.png "Individuazione del flusso di dati nel monitoraggio")



1. Puoi visualizzare in anteprima la scheda **dashboard** per visualizzare le metriche della pipeline relative ai flussi di lavoro di acquisizione batch.

![Scheda Dashboard che mostra le metriche in tutti i flussi di lavoro di acquisizione batch](assets/monitoring-and-debugging-errors-dashboard-tab-metrics.png "La scheda Dashboard mostra le metriche in tutti i flussi di lavoro di acquisizione batch")

>[!NOTE]
>
>Questa schermata di monitoraggio consente di visualizzare lo stato delle varie esecuzioni del flusso di dati.  Osserva le varie metriche disponibili nel pannello superiore.  Queste metriche possono essere estremamente utili per comprendere lo stato della pipeline di dati all’interno di Experience Platform



## Errori di debug

1. Se il flusso di dati presentava errori perché non hai seguito le istruzioni, viene visualizzato quanto segue.

![Errori segnalati per un flusso di dati in streaming con errori di mappatura](assets/monitoring-and-debugging-errors-failures-reported.png "Errori segnalati")



1. Se fai clic su Errori, ottieni la seguente schermata:

![Schermata di diagnostica degli errori che mostra i dettagli degli errori INGEST, DCVS e MAPPER](assets/monitoring-and-debugging-errors-preview-error-diagnostics.png "Anteprima diagnostica degli errori")

>[!NOTE]
>
>Un microbatch di successo potrebbe richiedere più di 15 minuti, in quanto potrebbe richiedere tempo per scrivere i record nel data lake.



1. Analizza il messaggio di errore, identifica i **campi di origine/destinazione,** e cerca il codice:

- **ACQUISISCI XXXX** - Si tratta di un errore grave a causa di danneggiamento dei dati o problemi di formattazione, ad esempio non seguendo un formato regex.
- **DCVS XXXX** - Questo errore viene visualizzato con `required` campi. Se i valori non esistono o non sono mappati correttamente (non all&#39;interno dell&#39;elenco enum), queste righe vengono ignorate.
- **MAPPER XXXX** - Si tratta di avvisi e non vengono ignorate righe. I valori, tuttavia, potrebbero essere stati &quot;annullati&quot;; pertanto è necessario verificare che non influiscano sulle attività a valle.

1. Per correggere gli errori, passa a **Origini->Flussi dati->Nome flusso dati->Aggiorna flusso dati** e correggi i mapping.

> [!NOTE]
>
>Per ricaricare il file di esempio JSON, devi prima eliminarlo e aggiungerlo nuovamente in modo che ora il mapper venga aggiornato con una nuova copia per la convalida.

![Navigazione a Origini > Flussi dati > Nome flusso di dati > Aggiorna flusso di dati per correggere le mappature](assets/monitoring-and-debugging-errors-update-dataflow-navigation.png "Fai clic su Aggiorna flusso di dati")
