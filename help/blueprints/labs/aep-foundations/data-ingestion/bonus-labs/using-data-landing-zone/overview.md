---
title: Utilizzo della Data Landing Zone
description: Installa e configura Azure Storage Explorer con un URL SAS per la connessione alla Adobe Experience Platform Data Landing Zone.
doc-type: overview-page
solution: Experience Platform
exl-id: d61bef25-7039-450d-a8e7-01bb12e8df7c
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---


# Utilizzo della Data Landing Zone

## Prerequisiti

Se non hai scaricato Azure Storage Explorer, fallo adesso, in quanto è un requisito per questo laboratorio.  Il download è disponibile al seguente link:

[Scarica Azure Storage Explorer](https://azure.microsoft.com/en-us/blog/microsoft-azure-data-lake-storage-adls-in-storage-explorer-public-preview/)

1. Installare l’applicazione
1. Al primo avvio accettare il contratto di licenza con l&#39;utente finale

![Schermata del contratto di licenza con l&#39;utente finale in Azure Storage Explorer](assets/overview-end-user-license-agreement-screen.png "Schermata del contratto di licenza con l&#39;utente finale")


## Configurare Azure Storage Explorer con Experience Platform

1. Apri Azure Storage Explorer e fai clic sull&#39;icona **Seleziona risorsa**, quindi seleziona **ADLS Gen 2 Container o directory**

   ![Selezione del contenitore o della directory ADLS Gen2 come risorsa in Azure Storage Explorer](assets/overview-choose-the-resource-as-shown-above.png)



1. Seleziona **URL firma di accesso condiviso (SAS)** e fai clic su **Avanti**

   ![Scegliere l&#39;opzione URL SAS come modalità di connessione](assets/overview-choose-the-sas-url-option-as-the-mode-of-connection.png "Scegliere l&#39;opzione URL SAS come modalità di connessione")



1. Immetti il nome visualizzato come **Area di destinazione dati**

   >[!NOTE]
   >
   >Non è possibile continuare in questo passaggio finché non si specifica l&#39;URL SAS.  Ottieni questo da Experience Platform, che vedi nel passaggio successivo.

   ![Denominazione della zona di destinazione dati della connessione](assets/overview-name-the-connection.png "Denominazione della connessione")



1. Vai a Adobe Experience Platform ed esegui il passaggio alla Data Landing zone effettuando le seguenti operazioni:

   - Passa a **Origini -> Catalogo**
   - Seleziona **Archiviazione cloud** nelle origini
   - Individua la scheda **Data Landing Zone**
   - Fai clic sulla scheda Data Landing Zone, quindi fai clic su **Visualizza credenziali** nella barra a destra

   ![Scheda di origine della zona di destinazione dati con opzione Visualizza credenziali in Adobe Experience Platform](assets/overview-data-landing-zone-view-credentials.png "Scheda Source della zona di destinazione dati di accesso in Adobe Experience Platform")



1. Copia **SASUri** dal modale visualizzato.

   Torna a Azure Storage Explorer e incolla il **valore SASUri** nell&#39;**contenitore Blob o URL SAS di directory** lasciato vuoto dal passaggio precedente

   ![Copia del valore SASUri da Experience Platform in Azure Storage Explorer](assets/overview-copy-sas-uri-into-azure-storage-explorer.png "Copia le credenziali dell&#39;URL SAS da Adobe Experience Platform e copiale in Azure Storage Explorer")



1. Fai clic su **Avanti** per continuare

   ![Copia delle credenziali dell&#39;URL SAS nella sezione dell&#39;URL SAS delle informazioni di connessione](assets/overview-copy-sas-url-into-connection-info.png "Copia delle credenziali dell&#39;URL SAS nella sezione dell&#39;URL SAS nelle informazioni di connessione")



1. Nella schermata Riepilogo fare clic su **Connetti**

![Schermata di riepilogo con pulsante Connetti](assets/overview-connect-screen.png "Schermata di connessione")



Ora dovresti vedere una schermata simile a quella riportata di seguito

![Azure Storage Explorer mostra l&#39;account della zona di destinazione dati connesso correttamente](assets/overview-successfully-connected-account.png)

>[!TIP]
>
>Congratulazioni!  Configurazione di Azure Storage Explorer completata
