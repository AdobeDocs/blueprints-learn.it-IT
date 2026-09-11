---
hold: true
title: Creazione dell’e-mail
description: Scopri come applicare un modello di contenuto con brand a un’e-mail di campagna in Adobe Journey Optimizer e sostituire le immagini principali e di prodotto.
doc-type: article
solution: Experience Platform
exl-id: bf823714-7298-48fc-a18b-9bf2462ae52e
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---


# Creazione dell’e-mail

## Creazione di contenuti con modelli

**Scopo:** scopri come creare modelli riutilizzabili in Adobe Journey Optimizer, quindi applicarli all&#39;interno di un&#39;e-mail reale all&#39;interno di una campagna.

## Obiettivi di apprendimento

Al termine di questo modulo, sarai in grado di:

1. Crea una nuova campagna e utilizza il nuovo modello di marchio.
1. Aggiornare le immagini principali, le immagini dei prodotti, i pulsanti e lo stile del layout.

## Creare e aggiornare l’e-mail in una campagna

### Obiettivo

In questo esercizio impareremo a applicare il modello creato a un’e-mail all’interno di un percorso. In uno scenario ideale, puoi utilizzare qualsiasi percorso o campagna esistente e sostituirne il contenuto e-mail con un modello standardizzato per garantire la coerenza del brand e un’esecuzione più rapida.

Questo passaggio illustra come riutilizzare i modelli nei diversi percorsi, consentendo ai team di aggiornare le progettazioni senza dover ricompilare le e-mail da zero.

## Creare una nuova campagna e-mail

1. Torna alla schermata principale e fai clic su **Gestione Percorsi → Campagne**.
2. Fai clic su **Crea campagna**

![Pulsante Crea campagna in Gestione Percorsi](assets/creating-the-email-click-create-campaign-button.png)

&#x200B;3. Seleziona &quot;**Orchestrazione - Marketing**&quot; e fai clic su **conferma**

![Selezione dell&#39;orchestrazione - Marketing e clic su confirm](assets/creating-the-email-select-orchestration-marketing.png)

&#x200B;4. Assegna un nome alla campagna `Flagship Phone Launch Branded`. Premere il pulsante **Salva**.

![Assegnazione del nome al lancio del telefono di punta della campagna con marchio e clic su Salva](assets/creating-the-email-name-campaign-save.png)

&#x200B;5. Fai clic sul segno **+** e seleziona l&#39;attività **Leggi pubblico**

![Segno più per selezionare l&#39;attività Read audience](assets/creating-the-email-click-plus-read-audience.png)

&#x200B;6. Il passaggio successivo consiste nel selezionare la casella **&quot;Read Audience&quot;** e fare clic sull&#39;icona della cartella **Audience**

![Icona Leggi casella pubblico e cartella Pubblico](assets/creating-the-email-read-audience-folder-icon.png)

&#x200B;7. Seleziona il **dep: interessato al pubblico di iPhone 17** e fai clic sul pulsante &quot;**Aggiungi pubblico**&quot;

![Selezione del pubblico interessato da iPhone 17 e clic su Aggiungi pubblico](assets/creating-the-email-select-audience-add-button.png)

&#x200B;8. Seleziona entità - **dep-rel: Account cliente - cliente\_id** (o qualsiasi altro dato non rilevante per questa parte)
&#x200B;9. Aggiungi l&#39;**attività E-mail** facendo clic sul segno **+** e quindi seleziona **E-mail** dalle attività del canale.

![Aggiunta dell&#39;attività e-mail dalle attività del canale](assets/creating-the-email-add-email-channel-activity.png)

&#x200B;10. Fai clic su **Modifica e-mail**.

![Modifica opzione e-mail per l&#39;attività e-mail della campagna](assets/creating-the-email-click-edit-email.png)

&#x200B;11. Fai clic sulla **scheda Azione** e seleziona **la tua** configurazione e-mail. Nella sandbox potrebbe essere visualizzato come E-mail relazionale. (Seleziona qualsiasi)

![Scheda Azione con la configurazione e-mail selezionata](assets/creating-the-email-action-tab-email-configuration.png)

&#x200B;12. Fai clic sulla **scheda Contenuto**

![Scheda Contenuto nell&#39;editor e-mail](assets/creating-the-email-click-content-tab.png)

&#x200B;13. Fai clic su **Applica modello di contenuto**

![Opzione Applica modello di contenuto nell&#39;editor e-mail](assets/creating-the-email-click-apply-content-template.png)

&#x200B;14. Seleziona il modello **&quot;Modello promozionale&quot;** creato e fai clic su **Conferma**

![Selezione del modello promozionale e clic su Conferma](assets/creating-the-email-select-promotional-template-confirm.png)

&#x200B;15. Fai clic su **Modifica corpo dell&#39;e-mail**

![Modifica il corpo dell&#39;e-mail dopo l&#39;applicazione del modello](assets/creating-the-email-click-edit-email-body.png)

&#x200B;16. Conferma che i nuovi blocchi di intestazione, protagonista, piè di pagina e contenuto vengano visualizzati correttamente.

![I blocchi di intestazione, protagonista, piè di pagina e contenuto vengono visualizzati correttamente nell&#39;e-mail](assets/creating-the-email-header-hero-footer-blocks-confirmed.png)


## Sostituisci immagine protagonista e immagini del prodotto

Cambia le immagini dell&#39;eroe e del telefono. È necessario caricare il contenuto nelle risorse dalla cartella toolkit. Attualmente l’immagine del banner principale del prodotto è un segnaposto.

1. Fai clic sull’immagine del banner eroe rotta.

![Fare clic sull&#39;immagine del banner principale segnaposto](assets/creating-the-email-click-broken-hero-banner-image.png)

&#x200B;2. Rimuovi l’URL di origine temporaneo.

![Rimozione dell&#39;URL di origine temporaneo dall&#39;immagine](assets/creating-the-email-remove-temporary-source-url.png)

&#x200B;3. Fai clic su **Importa file multimediali**

![Pulsante Importa file multimediali per l&#39;immagine protagonista](assets/creating-the-email-click-import-media.png)

&#x200B;4. Carica `hero.png` dal tuo toolkit. (puoi trascinare il file)

![Caricamento di hero.png dalla cartella toolkit](assets/creating-the-email-upload-hero-png-file.png)

&#x200B;5. Fai clic su **Avanti,** seleziona **la cartella per le risorse** e premi **importa**

![Selezione della cartella delle risorse e clic su Importa per l&#39;immagine protagonista](assets/creating-the-email-select-folder-import-hero.png)

&#x200B;6. Il modello di e-mail verrà visualizzato correttamente. Viene visualizzato come segue. Fai clic su **&quot;Salva&quot;** per salvare i tuoi dati.

![Modello di posta elettronica aggiornato con la nuova immagine protagonista prima del salvataggio](assets/creating-the-email-save-updated-email-template.png)


## Esercizio facoltativo

### Sostituisci immagini prodotto

Procedi con l’aggiornamento di tutte le immagini del prodotto (immagini fornite nella cartella toolkit) e aggiungi un bordo arrotondato a tuo piacimento. L’e-mail si presenta meglio senza collegamenti interrotti, come illustrato di seguito. Ripeti il processo per tutte le schede prodotto.

![Invia un&#39;e-mail con tutte le immagini del prodotto aggiornate e senza collegamenti interrotti](assets/creating-the-email-product-images-updated-no-broken-links.png)

## Riassunto

In questo modulo, esegui correttamente le seguenti operazioni:

- È stata creata una nuova campagna tramite e-mail utilizzando il modello di marchio
- Sono state aggiornate le immagini protagonista e prodotto
- Stili migliorati

Ora puoi passare al modulo successivo - **Assistente AI e personalizzazione contenuti**, in cui utilizzerai AI per perfezionare il testo e generare automaticamente le immagini.
