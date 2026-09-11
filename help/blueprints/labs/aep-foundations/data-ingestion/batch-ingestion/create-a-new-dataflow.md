---
title: Crea un nuovo flusso di dati
description: Crea un flusso di dati di origine batch a fronte di un set di dati esistente e importa mappature da un flusso di dati precedente per velocizzare l’impostazione.
doc-type: article
solution: Experience Platform
exl-id: 6f26f742-27e8-445a-8005-21d4e59dc3d0
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---


# Crea un nuovo flusso di dati

## Passa a Origini

1. Nell’interfaccia utente di Adobe Experience Platform, passa alla seguente posizione:\
   **Origini** -> **Catalogo** -> **Sistema locale**
1. Fai clic sul pulsante **Aggiungi dati** per la scheda **Caricamento file locale**

![Pulsante Aggiungi dati per la scheda Caricamento file locali nel catalogo origini](assets/create-a-new-dataflow-local-file-upload-add-data.png "Accedi alla Data Landing Zone")



## Impostare il flusso di dati

1. Nella schermata dei dettagli del flusso di dati, scegli **Set di dati esistente**.
1. Utilizza il set di dati creato in precedenza con il nome **Account cliente - \&lt;Iniziali>**
1. Verifica che il set di dati **Profilo** sia attivato.
Se non lo attivi, l’archivio profili non sarà in grado di monitorare i nuovi dati che entrano in questo set di dati e quindi non acquisirà questi dati nel profilo.
1. Verifica che l&#39;opzione **Abilita acquisizione parziale** sia attivata
Se non lo attivi, l’intera acquisizione potrebbe non riuscire se solo uno dei record presenta un errore.
1. Imposta il nome del flusso di dati come **Batch account cliente v2 - \&lt;Iniziali>**
1. Attiva tutti gli avvisi **Avvio/completamento/errore flusso di dati origini**
1. Se tutto sembra a posto, fai clic sul pulsante **Successivo** nell&#39;angolo superiore destro dello schermo per continuare con il passaggio successivo.

![Schermata dei dettagli del flusso di dati configurata con il set di dati esistente per il secondo flusso di dati](assets/create-a-new-dataflow-existing-dataset-flow-details.png "Dettagli flusso di dati")



## Carica file di esempio

1. Trascina e/o carica il file **Lab\_Customer\_Account.csv** nell&#39;interfaccia utente.  Al termine, lo schermo dovrebbe essere simile al seguente.

![Anteprima del file CSV dell&#39;account cliente caricato per il secondo flusso di dati](assets/create-a-new-dataflow-uploaded-csv-preview.png "Accesso ai file di Azure Storage Explorer in Adobe Experience Platform")



## Importa mappature

Nella schermata di mappatura, invece di impostare nuovamente tutte le mappature, puoi importare quelle create in precedenza.

1. Fai clic sul pulsante **Importa mapping**
1. Seleziona il flusso di dati con la mappatura creata in precedenza



![Pulsante Importa mapping nella schermata di mapping](assets/create-a-new-dataflow-import-mapping-button.png "Pulsante Importa mapping")



![Finestra di dialogo per selezionare il flusso di dati da cui importare il mapping](assets/create-a-new-dataflow-select-dataflow-to-import-mapping-from.png "Seleziona il flusso di dati da cui importare il mapping")

>[!NOTE]
>
>L’importazione delle mappature è un modo utile per riutilizzare le mappature da altri flussi di dati e ridurre la quantità di lavoro di mappatura da eseguire
