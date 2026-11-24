---
title: Creazione di frammenti di contenuto
description: Scopri come suddividere una progettazione e-mail in frammenti riutilizzabili, come un blocco di intestazione, che rimangano coerenti tra i modelli in Adobe Journey Optimizer.
doc-type: article
solution: Experience Platform
exl-id: 253a9332-dc08-420d-ac11-2bf342f0dc38
source-git-commit: d935e9a5179579e35c6aa5fe9e495f5bba1a1b03
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 0%
---

# Creazione di frammenti di contenuto

## Creazione di contenuti con modelli e frammenti

**Scopo:** scopri come creare frammenti riutilizzabili in Adobe Journey Optimizer, quindi applicarli all&#39;interno di un&#39;e-mail reale all&#39;interno di un percorso.

## Obiettivi di apprendimento

Al termine di questo modulo, sarai in grado di:

1. Suddividi una progettazione e-mail in frammenti riutilizzabili.
1. Crea frammenti di intestazione, piè di pagina, banner, corpo e CTA.

## Perché i frammenti contano

I frammenti consentono di creare contenuti coerenti e allineati al brand che possono essere riutilizzati in e-mail, campagne e percorsi.

### Frammenti

Blocchi predefiniti riutilizzabili come:

- Intestazioni
- Piè di pagina
- CTA
- Banner
- Esclusione di responsabilità legale

Ogni volta che un frammento viene aggiornato, tutte le e-mail che lo utilizzano vengono aggiornate automaticamente.

## Come si inserisce nella creazione di e-mail

- **Crea frammenti** per elementi che raramente cambiano.
- **Crea un modello** che utilizza tali frammenti.
- **Utilizza il modello** nell&#39;e-mail della campagna e personalizzane il contenuto.

Di seguito è riportato l’e-mail finale che creerai da questo laboratorio.

![Progettazione finale delle e-mail creata in questo laboratorio](assets/building-content-fragments-final-email-preview.png)

Tuttavia, il team di progettazione in genere fornisce modelli come questo:

![Modello di progettazione generico fornito dal team di progettazione](assets/building-content-fragments-generic-design-template.png)


## Passaggio 1: creare frammenti di contenuto

Il modello seguente è un modello di progettazione generico e il nostro obiettivo è quello di suddividerlo in blocchi di contenuto ripetibili. In Adobe percorsi Optimizer è denominato **Frammenti**.

Il primo passaggio consiste nell’identificare quanti frammenti è necessario creare. In questo modello ha senso utilizzare 5 frammenti come mostrato di seguito.



![Modello suddiviso in cinque frammenti identificati](assets/building-content-fragments-five-fragments-identified.png)

Abbiamo identificato che i modelli richiedono 5 frammenti come segue.

- Intestazione
- Banner
- CTA
- Corpo
- Piè di pagina

>[!NOTE]
>
>Per questo esercizio creerai un solo frammento di intestazione per risparmiare tempo.



Crea un frammento di intestazione con cui iniziare. Tuttavia, prima di creare il frammento, imposta una cartella di risorse poiché l’ambiente delle risorse è condiviso. A questo scopo, crea innanzitutto una cartella personalizzata.

1. Dalla navigazione a sinistra, individua la sezione **Gestione contenuto** e fai clic su **Assets**.

   ![Sezione Content Management con opzione Assets nel menu di navigazione a sinistra](assets/building-content-fragments-content-management-assets-nav.png)

2. Fai clic su **Assets** nella sezione Gestione Assets.

   ![Opzione Assets nella sezione Gestione di Assets](assets/building-content-fragments-assets-under-assets-management.png)

3. Creare una cartella facendo clic sul pulsante **&quot;Crea cartella&quot;**.

   ![Pulsante Crea cartella nell&#39;area Assets](assets/building-content-fragments-click-create-folder-button.png)

4. Assegna un nome come nome e cognome. Esempio: Nish\_Pithia\_LabAssets (un ricordo)

   ![Assegnazione di nomi e cognomi alla nuova cartella di risorse](assets/building-content-fragments-name-asset-folder.png)

5. Fai doppio clic sulla cartella appena creata per **aprirla**. Quindi fai clic su **Aggiungi Assets** e sfoglia o rilascia tutte le immagini .png e .jpg dalla cartella toolkit. Quindi fare clic su **Carica**

   ![Fai clic su Aggiungi risorse e carica file di immagine](assets/building-content-fragments-add-assets-and-upload-image-files.png)

   ![Fai clic su Carica](assets/building-content-fragments-click-upload.png)

6. **Crea un nuovo frammento:** In Gestione contenuto, fai clic su **Frammenti** e crea un nuovo frammento.

   ![Opzione Frammenti in Gestione contenuto per creare un nuovo frammento](assets/building-content-fragments-click-fragments-create-new.png)

   Assegna un nome descrittivo come illustrato di seguito. Aggiungere tutti i dettagli come segue:

   **Nome:** Intestazione

   **Descrizione:** intestazione frammento per il modello

   **Tipo:** Seleziona frammento visivo

   ![Campi Nome frammento intestazione, descrizione e Tipo frammento visivo](assets/building-content-fragments-fragment-name-type-details.png)

7. Fai clic sul **pulsante Crea** in alto a destra.

   ![Pulsante Crea in alto a destra nella finestra di dialogo Nuovo frammento](assets/building-content-fragments-click-create-button-top-right.png)

   Viene visualizzata una schermata di creazione del frammento vuota.

8. Passa alla scheda **Componenti** nella colonna sinistra. Quindi fare clic su **1:1 Colonna** in Strutture e trascinare sull&#39;area di lavoro come mostrato di seguito. (Cliccate sull&#39;immagine qui sotto per vedere l&#39;immagine animata)

   ![Trascinamento di una struttura a colonne 1:1 nell&#39;area di lavoro del frammento](assets/building-content-fragments-drag-1-1-columns-structure.png)

9. Quindi, trascina &quot;**immagine**&quot; sulla riga 1:1 appena aggiunta

   ![Trascinamento di un componente immagine nella riga 1:1](assets/building-content-fragments-drag-image-onto-row.png)

10. Fai clic su **&quot;Sfoglia&quot;** per selezionare l&#39;immagine del logo che ti è stata fornita e che è già stata caricata in Assets.

![Fare clic sul pulsante Sfoglia per selezionare l&#39;immagine del logo](assets/building-content-fragments-click-browse-button.png)

11. Vai alla cartella, fai clic sull&#39;immagine del logo (*C5G-Logo.png*) e fai clic su **Seleziona**.

![Selezione di C5G-Logo.png dalla cartella Assets](assets/building-content-fragments-select-logo-from-assets.png)

12. Il logo è posizionato correttamente, ma è troppo grande e deve essere ridimensionato. Per ridimensionare il logo, aggiornarne le proprietà. Fai clic sulla scheda **Stili** nella colonna di destra e imposta la larghezza su 40% trascinando il dispositivo di scorrimento, come illustrato di seguito.

>[!NOTE]
>
>Quando il pulsante di attivazione è attivato, il numero 40 rappresenta % e non i pixel. Se desideri un valore assoluto di precisione pixel, imposta il pulsante su px.



![Dispositivo di scorrimento della larghezza della scheda di stile impostato su 40% per ridimensionare il logo](assets/building-content-fragments-resize-logo-width-slider.png)

13. Fare clic su **&quot;Salva&quot;** per salvare il frammento. Ricevi una notifica con barra verde alla conferma.

![Barra di conferma verde dopo il salvataggio del frammento](assets/building-content-fragments-save-fragment-confirmation.png)

14. Il frammento salvato è in modalità bozza. Prima di utilizzarlo, è necessario pubblicarlo. Fai clic sul pulsante **indietro**.

![Pulsante Indietro per lasciare il frammento bozza prima della pubblicazione](assets/building-content-fragments-click-back-button-draft.png)

15. Fare clic sul pulsante &quot;**Pubblica**&quot;. Viene visualizzato il messaggio &quot;Pubblicazione del frammento in corso. L’operazione potrebbe richiedere del tempo. Al termine riceverai una notifica.&quot; alla conferma. Il frammento è pronto per essere utilizzato per la creazione di modelli.

![Pulsante Pubblica e messaggio di conferma del frammento di pubblicazione](assets/building-content-fragments-click-publish-fragment-button.png)

Lo stato verrà modificato in **&quot;Live&quot;**. A questo punto, hai completato la creazione di un frammento di intestazione, che verrà utilizzato nel passaggio successivo.

![Lo stato del frammento di intestazione è cambiato in Live](assets/building-content-fragments-fragment-status-live.png)

>[!NOTE]
>
>Tieni presente che in questo esercizio hai creato un solo frammento. In pratica, gli architetti possono scegliere di creare più frammenti, ad esempio intestazioni, piè di pagina o altri componenti riutilizzabili.

## Riassunto

In questo modulo, esegui correttamente le seguenti operazioni:

- Suddivisione di un’e-mail in un frammento di intestazione riutilizzabile
- Creazione di blocchi di contenuto di intestazione

Ora puoi passare al modulo successivo - **Creazione del modello di contenuto**, in cui utilizzerai il frammento creato per generare il nuovo modello.
