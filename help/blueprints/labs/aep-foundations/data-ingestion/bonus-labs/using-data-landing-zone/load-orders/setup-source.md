---
title: Configurare l’origine
description: Carica un file JSON degli ordini storici nella Data Landing Zone e configura un nuovo flusso di dati che esegue il targeting dello schema Ordini.
doc-type: article
solution: Experience Platform
exl-id: 046d50ad-687e-4cdb-a8b1-3c55ab39b68e
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# Configurare l’origine

## Carica file di esempio

È necessario caricare un file di dati di esempio nell’area di destinazione dati tramite Azure Storage Explorer, per poterlo utilizzare in laboratorio.  A tale scopo, eseguire le operazioni seguenti:

1. Scarica i [file di esempio](../../../sample-files.md)
1. Trascina e/o carica il file **Lab\_Historical\_Orders.json** nella Data Landing Zone da cui hai salvato i dati.



Una volta caricato, lo schermo dovrebbe essere simile a quello riportato di seguito.

![File Lab_Historical_Orders.json caricato in Data Landing Zone](assets/setup-source-lab-historical-orders-json-uploaded-to-dlz.png "Lab_Historical_Orders.json caricato in DLZ")

## Passa a Origini

1. Vai a Adobe Experience Platform e passa a: **Origini** -> **Catalogo** -> **Archiviazione cloud**
1. Fai clic su **Configurazione** / **Aggiungi dati** per la Data Landing Zone

![Accesso a Origini > Catalogo > Archiviazione cloud per impostare la Data Landing Zone](assets/setup-source-navigate-to-data-landing-zone-source.png "Origini - Data Landing Zone")

>[!NOTE]
>
>**Aggiungi dati** come azione predefinita se hai già configurato una connessione dalla precedente esercitazione di acquisizione batch



## Anteprima del file

1. Seleziona il file **Lab\_Historical\_Orders.json** e visualizzane l&#39;anteprima
1. Fai clic su **Avanti** nell&#39;angolo superiore destro della schermata per continuare con il passaggio successivo

![Selezione e anteprima del contenuto del file Lab_Historical_Orders.json](assets/setup-source-select-and-preview-lab-historical-orders.png "Selezione e anteprima del file Lab_Historical_Orders.json")

## Impostare il flusso di dati

1. Nella schermata dei dettagli del flusso di dati, scegli **Nuovo set di dati**
1. Denomina il set di dati di output come **Ordini - NomeQui**
1. Seleziona il nome schema **dep: Orders**
1. Attiva l&#39;interruttore **Set di dati profilo**
Se non lo attivi, l’archivio profili non è in grado di monitorare i nuovi dati che entrano in questo set di dati e quindi non acquisisce questi dati nel profilo.
1. Attiva **Abilita acquisizione parziale**
Se non lo attivi, l’acquisizione potrebbe non riuscire se uno dei record presenta errori.
1. Imposta il nome del flusso di dati come **Ordini - Recupero - NomeQui**
1. Attiva tutti gli avvisi **Avvio/completamento/errore flusso di dati origini**

![Schermata dei dettagli del flusso di dati configurata per il set di dati Ordini](assets/setup-source-dataflow-details-for-orders.png "Dettagli del flusso di dati per Ordini")

>[!CAUTION]
>
>Assicurati di avere **abilitato** il set di dati sia per il profilo che per l&#39;acquisizione parziale.

Fai clic su **Avanti** nell&#39;angolo superiore destro della schermata per continuare con il passaggio successivo
