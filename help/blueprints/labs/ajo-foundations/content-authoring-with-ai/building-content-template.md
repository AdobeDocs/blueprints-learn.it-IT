---
hold: true
title: Creazione di un modello di contenuto
description: Scopri come creare un modello di e-mail riutilizzabile in Adobe Journey Optimizer importando HTML e inserendo un frammento di intestazione creato in precedenza.
doc-type: article
solution: Experience Platform
exl-id: e73f06b1-be8a-4096-949c-900db13db9f8
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 0%

---


# Creazione di un modello di contenuto

## Creazione di contenuti con modelli e frammenti

**Scopo:** Scopri come creare modelli riutilizzabili in Adobe Journey Optimizer

## Obiettivi di apprendimento

Al termine di questo modulo, sarai in grado di:

1. Crea un modello e-mail completo utilizzando HTML e frammenti importati.

## Perché i modelli sono importanti

I modelli ti consentono di creare contenuti coerenti e allineati al brand che possono essere riutilizzati in e-mail, campagne e percorsi.

### Modelli

Blueprint con struttura:

- Posizionamento intestazione
- Area contenuto corpo
- Area piè di pagina
- Stile layout standard

I modelli garantiscono la coerenza del brand tra i team e consentono di risparmiare tempo prezioso per la creazione.


## Creare un nuovo modello utilizzando i frammenti

I modelli consentono agli utenti di riutilizzare i layout completi in più campagne. I modelli di contenuto in Adobe Journey Optimizer sono strumenti potenti progettati per semplificare e semplificare la creazione di contenuti riutilizzabili per campagne e percorsi. Per creare e-mail, SMS o notifiche push, i modelli ti aiutano a risparmiare tempo fornendo strutture preconfigurate che possono essere facilmente personalizzate e condivise tra i progetti.

Per accelerare e migliorare il processo di progettazione, crea modelli autonomi per riutilizzare facilmente i contenuti personalizzati nelle campagne e nei percorsi Journey Optimizer.

Questa funzionalità consente agli utenti orientati ai contenuti di lavorare su modelli al di fuori di campagne o percorsi. Gli utenti marketing possono quindi riutilizzare e adattare questi modelli di contenuto autonomo all’interno dei propri percorsi o campagne.

## Crea modello

1. Vai a **Gestione contenuto → Modelli di contenuto**.

![Accesso a Gestione contenuto e quindi a Modelli di contenuto](assets/building-content-template-navigate-content-templates.png)

&#x200B;2. Fai clic su **Crea modello** e quindi compila quanto segue:
   - **Nome:** `Promotional Template`
   - **Descrizione:** `Promotional Template for phone products`
   - **Canale:** `Email`

![Crea modulo modello con nome, descrizione e canale e-mail](assets/building-content-template-create-template-form-fields.png)

&#x200B;3. Fai clic su **Crea**.

![Crea pulsante per completare la creazione del modello promozionale](assets/building-content-template-click-create-button.png)


## Aggiungi oggetto e apri e-mail designer

1. Aggiungi oggetto: `Promotional Template` e fai clic su **nel corpo dell&#39;e-mail** per aprirla e modificarla

![Aggiunta dell&#39;oggetto e apertura del corpo dell&#39;e-mail da modificare](assets/building-content-template-add-subject-line-open-editor.png)

&#x200B;2. Sono disponibili tre opzioni:
   1. Progettare da zero
   2. Crea il codice
   3. Importa HTML

Seleziona la terza opzione. Fai clic su **Importa HTML**



![Selezione dell&#39;opzione Importa HTML tra le tre opzioni di progettazione](assets/building-content-template-select-import-html-option.png)

## Importa modello HTML fornito



1. Caricare il file HTML del modello dalla cartella toolkit `promotional-template-final.html`

![Caricamento di promotional-template-final.html dalla cartella toolkit](assets/building-content-template-upload-html-template-file.png)

&#x200B;2. Fai clic sul pulsante Importa per **importare** il modello.

![Pulsante Importa per importare il modello di HTML caricato](assets/building-content-template-click-import-button.png)

&#x200B;3. Attendere il rendering del layout. Noterai problemi come l’interruzione dei collegamenti immagine e la mancanza di branding. (comportamento previsto, in quanto sono presenti risorse segnaposto)

![Modello con rendering che mostra collegamenti immagine interrotti e segnaposto di branding mancanti](assets/building-content-template-rendered-template-broken-images.png)


## Esplora la struttura del modello

### Pannello sinistro

I componenti &quot;**Strutture**&quot; e &quot;**Contenuti**&quot; in Adobe Journey Optimizer (AJO) sono elementi essenziali utilizzati per la progettazione di e-mail, pagine di destinazione e frammenti di contenuto. Le strutture definiscono il framework di layout, mentre il contenuto fornisce i blocchi predefiniti effettivi posizionati all’interno di tali layout.

La sezione body in Adobe Journey Optimizer è il contenitore principale per l’e-mail o il contenuto della pagina. Funge da radice dello spazio di progettazione visiva, dove tutti i componenti struttura (colonne, layout) e contenuto (testo, immagini, pulsanti, ecc.) sono nidificati.

### Pannello a destra

Le opzioni &quot;**Settings**&quot; e &quot;**Style**&quot; nella sezione body di Adobe Journey Optimizer ti consentono di definire l&#39;aspetto e il layout fondamentali dell&#39;e-mail o della pagina. Questi controlli influiscono sull&#39;intero progetto poiché il corpo è l&#39;elemento padre di tutti i componenti.

![Impostazioni e opzioni di stile nel pannello di destra per la sezione corpo](assets/building-content-template-body-settings-style-panel.png)


Sulla barra della barra a sinistra sono presenti le sezioni relative a:

- Frammenti
- File
- Struttura del corpo
- URL tracciati

Il frammento di intestazione creato nell’esercizio precedente viene visualizzato qui come illustrato di seguito. Assicurati che il frammento di intestazione sia visualizzato in tempo reale con un punto blu e non in modalità bozza. Passate del tempo a controllare il resto delle sezioni.

![Frammento di intestazione visualizzato con un punto blu nella barra laterale sinistra](assets/building-content-template-header-fragment-live-sidebar.png)

&#x200B;> [!NOTE]
>
>Se il frammento non viene visualizzato qui, significa che non è stato salvato correttamente e deve essere ricaricato.



## Inserire frammenti di intestazione

Ora migliora il modello. Intestazione e piè di pagina già creati.

1. Trascina una **colonna 1:1** sopra il contenuto esistente.

![Trascinamento di una colonna 1:1 sopra il contenuto del modello esistente](assets/building-content-template-drag-1-1-column-above-content.png)

Vedete qualcosa come questo.

![Layout del modello dopo l&#39;aggiunta della nuova colonna sopra il contenuto](assets/building-content-template-column-added-above-content.png)

&#x200B;2. Lo sfondo utilizza il colore di sfondo del modello, attualmente nero. Imposta il colore di sfondo **su bianco. Fare clic su** nella scheda Stile nella barra a destra e utilizzare il colore bianco nel selettore dei colori.

![Impostazione del colore di sfondo della colonna su bianco mediante il selettore colore](assets/building-content-template-set-background-color-white.png)

&#x200B;3. Apri **Frammenti** e trascina il frammento **Intestazione**.

![Trascinamento del frammento di intestazione nel modello dal pannello Frammenti](assets/building-content-template-drag-header-fragment-into-template.png)

&#x200B;4. Il frammento di intestazione è allineato correttamente al modello, come illustrato di seguito.

![Frammento di intestazione allineato correttamente nel modello](assets/building-content-template-header-fragment-aligned-template.png)

&#x200B;5. Fai clic sul pulsante **Salva** per salvare il modello, quindi fai clic su **Indietro**.

![Salva pulsante per salvare il modello prima di fare clic su Indietro](assets/building-content-template-click-save-button-template.png)

>[!NOTE]
>
>Potresti vedere alcune immagini rotte. Lo ripareremo più tardi.


## Riassunto

In questo modulo, esegui correttamente le seguenti operazioni:

- HTML importato per creare un modello promozionale completo

Ora puoi passare al modulo successivo - **Creazione dell&#39;e-mail**
