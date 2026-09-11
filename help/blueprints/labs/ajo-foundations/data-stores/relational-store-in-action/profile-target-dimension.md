---
hold: true
title: Dimension di destinazione profilo
description: Scopri come etichettare un campo di schema relazionale come identità e creare un Dimension di destinazione del profilo per unirsi al profilo cliente in tempo reale con l’archivio relazionale.
doc-type: article
solution: Experience Platform
exl-id: bfc71051-e471-4d5c-a9a7-bb6805a5acb1
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# Dimension di destinazione profilo

## Obiettivo

Nei passaggi successivi, scorri l’interfaccia utente per visualizzare lo schema e impostare l’identità. Successivamente, configurerai Profile Target Dimension (Target profilo), che è il tipo di entità di targeting e riconciliazione della campagna con il profilo di AEP per la consegna.

## Perché questo è importante

Il profilo Target Dimension viene utilizzato per indicare a Adobe Journey Optimizer come è possibile unire i dati tra Real-Time Customer Profile e Relational Store. Gli ingredienti di questa configurazione sono i seguenti:

- Uno schema relazionale
- Un singolo campo dallo schema relazionale
- Uno spazio dei nomi delle identità associato a quel campo

>[!CAUTION]
>
>Senza questa configurazione attiva, non è possibile leggere o condividere tipi di pubblico né inviare messaggi da Campagne orchestrate

## Etichettare l’identità

1. Fai clic sull&#39;icona **App** e seleziona **Journey Optimizer**

![Menu icona app con Journey Optimizer selezionato](assets/profile-target-dimension-navigate-to-journey-optimizer.png)

2. Fai clic su **Schemi** nel menu Gestione dati e accertati di aver selezionato la scheda **Sfoglia**.
3. Cerca lo schema denominato `dep-rel: Customer Account`

![Ricerca schema per dep-rel: account cliente](assets/profile-target-dimension-search-schema.png)

4. Apri lo schema facendo clic sul nome e quindi fai clic sul campo **customer\_id**

![Elenco campi schema con customer_id selezionato](assets/profile-target-dimension-select-customer-id-field.png)

5. Nella barra a destra individua la casella di controllo denominata **Identità**, **seleziona la casella** e scegli lo spazio dei nomi Identità denominato **customerID**

![Casella di controllo dell&#39;identità con lo spazio dei nomi customerID selezionato](assets/profile-target-dimension-choose-identity-namespace.png)

6. Fai clic sul pulsante **Salva** per salvare lo schema. Viene visualizzato un messaggio di conferma
7. Fai clic sul pulsante **Annulla** o sugli **Schemi** nella barra a sinistra per uscire dall&#39;interfaccia utente dello schema

>[!CAUTION]
>
>Se non salvi lo schema dopo l’aggiunta dell’etichetta di identità, il set successivo di passaggi di configurazione non funziona

>[!NOTE]
>
>Dopo il salvataggio, sono necessari alcuni minuti (meno di 5 minuti), prima che venga visualizzato nel menu a discesa Profile Target Dimension nel passaggio successivo.

## Creare il Dimension di destinazione del profilo

1. Fai clic su **Configurazioni** in **Amministrazione**

![Menu Amministrazione con configurazioni selezionate](assets/profile-target-dimension-configurations-menu.png)

2. Seleziona **Dimension di destinazione profilo** e fai clic su **Gestisci**

![Configurazione del profilo di Target Dimension con l&#39;opzione Gestisci](assets/profile-target-dimension-manage-configuration.png)

3. Viene aperto il riquadro Dimension di destinazione del profilo. Fare clic su **Crea**

![Riquadro Dimension di destinazione del profilo con il pulsante Crea](assets/profile-target-dimension-create-button.png)

4. Selezionare lo schema `dep-rel: Customer Account` dal menu a discesa.

>[!NOTE]
>
>Potrebbero essere necessari alcuni minuti perché lo schema venga visualizzato in questa schermata dopo aver contrassegnato l’identità. Aggiorna la pagina e ripeti i due passaggi precedenti fino a visualizzare lo schema.

![Crea modulo Dimension di destinazione profilo con il menu a discesa dello schema](assets/profile-target-dimension-select-schema-dropdown.png)

5. Per il **valore identità** selezionare `/customer_id`

![Elenco a discesa del valore dell&#39;identità con /customer_id selezionato](assets/profile-target-dimension-select-identity-value.png)

>[!NOTE]
>
>Uno schema relazionale può avere molti campi etichettati con identità, quindi questa è una casella di riepilogo.



6. Fai clic sul pulsante **Salva** per creare il Dimension di destinazione del profilo. Viene quindi visualizzato il record.

![Record Dimension di destinazione profilo salvato nell&#39;elenco](assets/profile-target-dimension-saved-record.png)

>[!NOTE]
>
>Il nome del record creato è una concatenazione del nome dello schema *(dep-rel: Customer Account)* e del campo con etichetta identità *(customer\_id)*

>[!TIP]
>
>Congratulazioni! Questo conclude il passaggio di creazione del Dimension di Target profilo nel laboratorio.

## Riassunto

Ora hai visto quanto è facile navigare nello schema, contrassegnare un attributo come identità e creare il Dimension di destinazione del profilo.

Puoi trovare ulteriori [qui](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/data-configuration/target-dimension) se sei interessato.
