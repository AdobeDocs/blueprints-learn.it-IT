---
title: Oggetti standard del modello
description: Crea uno schema Profilo individuale nell’interfaccia utente di e aggiungi e taglia gruppi di campi standard come Dettagli demografici e Consenso e preferenze.
doc-type: article
solution: Experience Platform
exl-id: ea516c0b-3644-483c-a167-0264cc795449
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 0%

---


# Oggetti standard del modello

## Passare agli schemi

1. Fai clic sulla scheda **Schemi** nella barra a sinistra

   ![Scheda Schemi nella barra di navigazione a sinistra](assets/model-standard-objects-schemas-tab-left-rail.png "Passa agli schemi utilizzando la barra a sinistra")



1. Nella navigazione in alto sono disponibili opzioni per sfogliare gli schemi esistenti e visualizzare i gruppi di campi e i tipi di dati attualmente presenti nel registro XDM.

![Opzioni di navigazione principali per sfogliare schemi, gruppi di campi e tipi di dati](assets/model-standard-objects-browse-schemas-top-nav.png "Navigazione principale schemi")

>[!NOTE]
>
>Nella sandbox sono già presenti schemi precreati. Questi includono schemi precreati come parte di questo campo di avvio (con prefisso `dep`), nonché schemi generati dal sistema per Adobe Real-Time CDP e Adobe Journey Optimizer.


## Creare uno schema di profilo individuale

1. Per iniziare, fai clic su **Crea schema**

   ![Pulsante Crea schema](assets/model-standard-objects-create-schema-button.png "Crea schema")



1. Seleziona **Manuale**

   ![Seleziona opzione di creazione schema manuale](assets/model-standard-objects-select-manual-option.png "Seleziona manuale")



1. Seleziona **Profilo individuale**

![Selezionare la singola classe di profilo](assets/model-standard-objects-select-individual-profile-class.png "Selezionare la singola classe di profilo")


## Denomina lo schema

Gli schemi basati su classi di profili individuali XDM consentono di raccogliere gli attributi di un individuo che verrà unito al profilo. La classe stessa contiene campi non modificabili, ad esempio *modifiedByBatchID*, *PersonID* e così via.

1. Assegna un nome e una descrizione allo schema.
   - **Nome visualizzato schema** —> *Account cliente - \[Iniziali]*
   - **Descrizione** —> Questo schema raccoglie le identità, le informazioni sul piano, i dettagli demografici e i dettagli di contatto di un individuo.
1. Salva lo schema con il pulsante **Fine** in alto a destra.

![Denomina lo schema, aggiungi una descrizione e salva](assets/model-standard-objects-name-schema-and-save.png "Denomina lo schema, aggiungi una descrizione e salva")

## Aggiungi gruppo di campi Dettagli demografici

In Adobe Experience Platform esistono molti gruppi di campi XDM standard da aggiungere allo schema e personalizzare.

1. Fai clic su **+ (aggiungi)** nella barra a sinistra nella sezione del gruppo di campi.

   ![Pulsante Aggiungi gruppo di campi nella barra a sinistra](assets/model-standard-objects-add-field-group-button.png "Aggiungi un gruppo di campi")



1. Cercare **Dettagli demografici** o trovarli sfogliando l&#39;elenco.

   - Quando si trova il gruppo di campi, fare clic sulla lente di ingrandimento a destra del gruppo di campi per visualizzarne la struttura.  Si tratta di un modo utile per visualizzare in anteprima ciò che stai per aggiungere allo schema senza aggiungerlo effettivamente.
   - Al termine della revisione, chiudi l’anteprima



   ![Fare clic sulla lente di ingrandimento per visualizzare in anteprima la struttura del gruppo di campi](assets/model-standard-objects-click-magnify-glass-to-preview-field-group-structure.png "Fare clic sulla lente di ingrandimento per visualizzare in anteprima la struttura del gruppo di campi")

   ![Anteprima della struttura del gruppo di campi Dettagli demografici](assets/model-standard-objects-demographic-details-structure-preview.png)



&#x200B;3. **Selezionare** la casella di controllo accanto al gruppo di campi, quindi fare clic sul pulsante **Aggiungi gruppi di campi**

![Selezionare il gruppo di campi Dettagli demografici per aggiungerlo allo schema](assets/model-standard-objects-select-demographic-details-field-group.png "Selezionare il gruppo di campi Dettagli demografici per aggiungerlo allo schema")


## Aggiungi altri gruppi di campi standard

È necessario aggiungere ulteriori gruppi di campi standard allo schema. Ripeti i passaggi precedenti per aggiungere i due gruppi di campi aggiuntivi allo schema:

- Dettagli di contatto personali
- Dettagli su consenso e preferenze

Al termine, lo schema dovrebbe essere simile a quello riportato di seguito. Fai clic sul pulsante **Salva** e salva il tuo lavoro.

![Schema dopo l&#39;aggiunta di dettagli demografici, dettagli contatto personale e gruppi di campi Dettagli consenso e preferenze](assets/model-standard-objects-final-schema-after-adding-field-groups.png "Schema finale dopo il salvataggio di ")

>[!NOTE]
>
>I gruppi di campi selezionati e aggiunti ora vengono visualizzati nello schema e nella barra a sinistra. Non tutti i campi in ciascun gruppo di campi aggiunto sono necessariamente necessari.  Il passaggio successivo rimuove i campi estranei.

>[!WARNING]
>
>Prima di continuare, assicurati di salvare lo schema.


## Personalizza gruppi di campi standard

### Gruppo di campi Dettagli demografici

Il gruppo di campi Dettagli demografici ha incluso molti campi, ma in base alla progettazione dello schema dalla metodologia LID, sono necessari solo i campi seguenti:

- person.name.firstName
- person.name.lastName
- person.bornDayAndMonth
- person.bornYear

Per rimuovere campi da qualsiasi gruppo di campi standard di Adobe puoi utilizzare l&#39;opzione **Gestisci campi correlati**. Gestisci campi correlati consente di rimuovere i campi standard dallo schema, in modo da disporre solo dei campi necessari.

1. Seleziona l&#39;oggetto **person** nello schema
1. Fai clic su **Gestisci campi correlati** nella barra a destra

   ![Opzione Gestisci campi correlati per l&#39;oggetto persona nel gruppo di campi Dettagli demografici](assets/model-standard-objects-manage-related-fields-person-object.png "Gestisci campi correlati per l&#39;oggetto persona come parte del gruppo di campi Dettagli demografici")



1. Espandere l&#39;oggetto person facendo clic sulla freccia a sinistra dell&#39;oggetto person ed espandere l&#39;oggetto full name facendo clic sulla freccia a sinistra dell&#39;oggetto name. Mantieni solo i campi seguenti:

   - person.name.firstName
   - person.name.lastName
   - person.bornDayAndMonth
   - person.bornYear

   Al termine, fai clic sul pulsante **Conferma** nell&#39;angolo superiore destro.

   ![Finestra di dialogo Gestisci campi correlati che mostra i campi persona di Dettagli demografici selezionati](assets/model-standard-objects-demographic-details-person-fields-dialog.png "Gestisci i campi correlati dell&#39;oggetto persona di Dettagli demografici")

   >[!NOTE]
   >
   >È possibile selezionare la casella di controllo superiore per **Dettagli demografici** per deselezionare automaticamente tutti gli oggetti figlio e quindi riselezionare solo quelli necessari.



1. Al termine, dovresti visualizzare l’oggetto persona nello schema, come illustrato di seguito. Se tutto si presenta correttamente, fai clic sul pulsante **Salva** per salvare lo schema.

![Oggetto persona Dettagli demografici finali con solo i campi necessari](assets/model-standard-objects-final-demographic-details-person-object.png "Gruppo di campi Dettagli demografici finali con solo i campi necessari")

### Gruppo di campi Consenso e preferenze

Effettua la stessa serie di passaggi eseguita in precedenza ma questa volta per il gruppo di campi Consenso e preferenze.

1. Fai clic sul nome del gruppo di campi **Consenso e preferenze** nella barra a sinistra per evidenziarne i campi nello schema.
1. Seleziona l&#39;oggetto **consents**, quindi utilizza il processo **Manage related fields** per rimuovere i campi non necessari dall&#39;oggetto di consenso. Mantieni solo i campi seguenti:

- consents.marketing.email.val
- consents.marketing.sms.val

>[!NOTE]
>
>Verifica che l&#39;interruttore sia disattivato per **Mostra nomi visualizzati per i campi** nell&#39;angolo superiore destro dell&#39;area di lavoro dello schema
>
>![Mostra nomi visualizzati per i campi disattivati](assets/model-standard-objects-show-display-names-toggle-off.png)



Al termine, lo schema finale dovrebbe essere simile a questo.  Assicurarsi di fare clic su **Salva** prima di continuare.

![Schema dopo la gestione dei campi correlati per il gruppo di campi Consenso e preferenze](assets/model-standard-objects-final-consent-and-preferences-fields.png "Campi correlati gestiti per il gruppo di campi Consenso e preferenze")

>[!TIP]
>
>Ora hai completato l’aggiunta di componenti standard allo schema. Ottimo lavoro! Passa alla creazione di alcuni attributi personalizzati per lo schema.
