---
hold: true
title: Configurare l’origine
description: Carica un file dell’account cliente di esempio nella Data Landing Zone e configura un nuovo flusso di dati di origine dell’archiviazione cloud.
doc-type: article
solution: Experience Platform
exl-id: 1c80e71b-19a7-45e9-9961-d72b3f03ecae
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 0%

---


# Configurare l’origine

## Carica file di esempio

È necessario caricare un file di dati di esempio nell’area di destinazione dati tramite Azure Storage Explorer, per poterlo utilizzare in laboratorio.  A tale scopo, eseguire le operazioni seguenti:

1. Scarica i [file di esempio](../../sample-files.md)
1. Trascina e/o carica il file **Lab\_Customer\_Account.csv** nella Data Landing Zone salvata dal passaggio precedente.

Una volta caricato, lo schermo dovrebbe essere simile a quello riportato di seguito.

>[!WARNING]
>
>Assicurati di non caricare il file nella cartella *project*. Contiene dati precaricati che non utilizzi nei nostri laboratori.

![Browser file zona di destinazione dati che mostra il file Lab_Customer_Account.csv caricato, non la cartella del progetto](assets/setup-source-make-sure-you-do-not-upload-the-file.png)

## Passa a Origini

1. Vai a Adobe Experience Platform e passa a: **Origini** -> **Catalogo** -> **Archiviazione cloud**
1. Fai clic su **Configurazione** / **Aggiungi dati** per la Data Landing Zone

![Imposta o aggiungi azione dati per l&#39;origine di archiviazione cloud Data Landing Zone](assets/setup-source-add-data-landing-zone-source.png "Accedi a Data Landing Zone")

>[!NOTE]
>
>Se esiste almeno una connessione per l&#39;origine, verrà visualizzata l&#39;azione predefinita **Aggiungi dati**. Se non esistono connessioni per l&#39;origine, verrà visualizzato **Setup** come azione predefinita

## Anteprima del file

1. Seleziona **Lab\_Customer\_Account.csv**

![Selezione del file Lab_Customer_Account.csv da visualizzare in anteprima in Azure Storage Explorer](assets/setup-source-select-lab-customer-account-csv.png "Accesso ai file di Azure Storage Explorer in Adobe Experience Platform")

1. Nel riquadro di anteprima, esaminare i seguenti attributi e osservare quanto segue:

- **sms\_optIn** è un campo di consenso con diversi valori mancanti (mostrati in anteprima come - )
- **account\_create\_date** non ha il formato di data corretto. Contiene valori stringa insieme a valori di data e ora in una stringa.
- **account\_end\_date** ha il formato data corretto.



![campo sms_optIn con diversi valori mancanti visualizzati nell&#39;anteprima del file](assets/setup-source-sms-optin-missing-values.png "sms_optin")



I campi ![account_create_date e account_end_date sono visualizzati nell&#39;anteprima del file](assets/setup-source-account-create-date-account-end-date.png "account_create_date e account_end_date")

>[!NOTE]
>
>Dovrai occuparti dei valori mancanti, delle date e dei campi formattati in modo errato nei passaggi di mappatura successivi in questa esercitazione

1. Fai clic su **Avanti** nell&#39;angolo superiore destro della schermata per continuare con il passaggio successivo



## Impostare il flusso di dati

1. Nella schermata dei dettagli del flusso di dati, scegli **Nuovo set di dati**.
1. Denomina il set di dati di output come **Account cliente - \&lt;Iniziali>**
1. Selezionare lo schema **dep: Account cliente** dall&#39;elenco a discesa.
1. Attiva l&#39;interruttore **Set di dati profilo**.
Se non lo attivi, l’archivio profili non è in grado di monitorare i nuovi dati che entrano in questo set di dati e quindi non acquisisce questi dati nel profilo.
1. Attiva **Abilita acquisizione parziale**.
Se non lo attivi, l’acquisizione potrebbe non riuscire se uno dei record presenta errori.
1. Imposta il nome del flusso di dati come **Acquisizione batch account cliente - \&lt;Iniziali>**
1. Attiva tutti gli avvisi **Avvio/completamento/errore flusso di dati origini**

![Schermata dei dettagli del flusso di dati con nuovo set di dati, attivazione/disattivazione profilo e impostazioni di acquisizione parziali configurate](assets/setup-source-dataflow-detail-screen-settings.png "Dettagli flusso di dati")

>[!CAUTION]
>
> Assicurati di avere **abilitato il set di dati** sia per il profilo che per l&#39;acquisizione parziale.

Fai clic su **Avanti** nell&#39;angolo superiore destro della schermata per continuare con il passaggio successivo.

>[!NOTE]
>
>**Abilita acquisizione parziale** specifica il numero di errori (**INGEST** e **DCVS**) come percentuale del numero totale di record che possono avere esito negativo prima che l&#39;intero flusso di dati venga dichiarato un errore.
