---
title: Configurare l’origine
description: Crea un account di streaming API HTTP e configura un flusso di dati per inviare i dati JSON dell’account cliente in un set di dati abilitato per il profilo.
doc-type: article
solution: Experience Platform
exl-id: a5c02337-8af3-45dc-82a0-fa9731892fe4
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---


# Configurare l’origine

## Passa a origini di streaming

1. Passa all&#39;interfaccia utente di Adobe Experience Platform e passa a **Origini**
1. Fai clic su **Catalogo** nel menu di navigazione superiore
1. Seleziona **Streaming** dall&#39;elenco delle origini (assicurati che il pulsante di opzione Tutte le origini sia selezionato)
1. Fai clic su **Configurazione** / **Aggiungi dati** per API HTTP

![Sequenza di passaggi per creare un nuovo account di origine API HTTP](assets/setup-source-sequence-of-steps-to-create-a-http-api-account.png)



## Crea account API HTTP

Per prima cosa devi creare un nuovo account. Questo account contiene i dettagli relativi alla gestione dell’autenticazione e al fatto che i dati in streaming siano compatibili con XDM (ovvero già corrispondenti alla struttura dello schema XDM sottostante)

Esegui le seguenti attività:

1. Seleziona **Nuovo account** e aggiungi i seguenti dettagli:
   - Nome account -> `Streaming Ingestion - <Your Initials>`
1. Lascia l&#39;opzione per **Abilita autenticazione** disabilitata
1. Lascia deselezionata la casella di controllo per **XDM compatibile**
1. Fai clic sul pulsante **Connetti all&#39;origine** per continuare

>[!CAUTION]
>
>NON attivare **Abilita autenticazione** o selezionare la casella per **XDM compatibile**. Questo rompe il laboratorio

Lo schermo dovrebbe essere simile al seguente:

![Schermata dopo aver fatto clic su Connetti all&#39;origine per il nuovo account API HTTP](assets/setup-source-connect-to-source-screen.png)



A questo punto dovrebbe essere visualizzata una casella di controllo verde con il messaggio &quot;Connesso&quot;. Fai clic sul pulsante **Avanti** in alto a destra per continuare a configurare il flusso di dati:

![Casella di controllo verde con messaggio connesso dopo la configurazione dell&#39;account API HTTP](assets/setup-source-green-checkbox-with-connected-message.png "Dovrebbe essere visualizzata una casella di controllo verde con messaggio connesso")



## Carica dati di esempio

>[!NOTE]
>
>Se non lo hai già fatto, assicurati di scaricare i [file di esempio](../sample-files.md)



1. Nella sezione Schema dati di Source della schermata, carica il file JSON **Lab\_Single\_Customer\_sample.json** dal file system locale scaricato dal laboratorio precedente.
1. Una volta caricato il file, viene visualizzata un’anteprima come segue. Fai clic sul pulsante **Avanti** in alto a destra per continuare. Osserva come il campo data_nascita è in un formato diverso AAAA-MM-GG rispetto al formato MM/GG/AAAA visualizzato in precedenza nel laboratorio di acquisizione batch.

![Anteprima del record Lab_Single_Customer_sample.json caricato per la progettazione e la convalida della pipeline](assets/setup-source-sample-customer-record-for-pipeline-design-and-validation.png)

>[!NOTE]
>
>Il file di esempio JSON contiene un singolo record per la progettazione e la convalida della pipeline. Se desideri scorrere, devi fare clic sui nodi XDM per far scorrere i nodi.



## Configurare i dettagli del flusso di dati

In questa schermata, stai creando un flusso di dati specifico che sfrutta l’account API HTTP configurato.  Puoi avere molti flussi di dati per account.  In questo scenario, devi creare un flusso di dati per lo streaming dei dati dell’account cliente. Un flusso di dati richiede un’associazione tra un account di origine, un set di dati con schema associato e i dettagli di configurazione.

Effettua le seguenti operazioni:

1. Crea un nuovo set di dati con il nome -> `Customer Account Stream - <Your Initials>`
1. Scegli lo **schema** come ->`dep: Customer Account`
1. Verificare che il set di dati **profilo** sia **abilitato**.  In caso contrario, **abilitarlo**.
1. Aggiorna il **nome flusso di dati** come segue:
   - `Customer Account Stream - <Your Initials>`
1. Fai clic sul pulsante **Avanti** per continuare

![Configurazione dei dettagli del flusso di dati per il set di dati di streaming dell&#39;account cliente](assets/setup-source-configuring-a-dataflow.png)

>[!NOTE]
>
>Se non abiliti il set di dati per il profilo, i dati vengono trasmessi solo nel Data Lake. Gli eventi di streaming non vengono visualizzati nel profilo o nel grafico delle identità.
