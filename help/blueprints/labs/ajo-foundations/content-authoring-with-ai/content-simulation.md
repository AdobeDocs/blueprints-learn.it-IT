---
title: Simulazione dei contenuti
description: Scopri come utilizzare lo strumento di simulazione di Adobe Journey Optimizer con dati di profilo di esempio per convalidare campi personalizzati, varianti di contenuto e comportamenti di fallback.
doc-type: article
solution: Experience Platform
exl-id: 3e2b064f-5680-461c-a49e-2a61514e146f
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: c0adb1eab9b0a1315e2041c1f2cb89a4bfdae4b2
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%
---

# Simulazione dei contenuti

**Scopo:** convalidare le varianti di personalizzazione, logica condizionale e contenuto utilizzando gli strumenti di simulazione e bozza di Adobe Journey Optimizer.

## Obiettivi di apprendimento

Al termine di questo modulo, sarai in grado di:

1. Carica e utilizza i dati del profilo di test per la simulazione.
1. Convalida campi personalizzati e logica delle varianti.
1. Verifica il comportamento di fallback per dati mancanti o senza corrispondenza.

## Introduzione

In questo modulo, eseguirai il test dell&#39;e-mail con **due varianti condizionali** utilizzando lo strumento di simulazione in Adobe Journey Optimizer.
Questo consente di visualizzare in anteprima come diversi clienti percepiranno il tuo messaggio personalizzato, garantendo precisione prima di lanciare la campagna.

Verrà utilizzato il file del profilo di test di esempio **sample.csv** dal toolkit.

![Esempio di file del profilo di test sample.csv dal toolkit](assets/content-simulation-sample-csv-toolkit-file.png)

## Aprire lo strumento di simulazione

1. Apri l’e-mail completata.
2. Nell&#39;e-mail, fai clic su **Simula contenuto**.

![Fare clic su Simula contenuto e selezionare Simula variante contenuto](assets/content-simulation-click-simulate-content-variation.png)

Dopo alcuni secondi viene visualizzato un pannello di simulazione.

## Caricare i dati del profilo di test

1. Fai clic su **Carica** in basso per caricare i dati di input.

   ![Pulsante Carica per i dati di input nel pannello di simulazione](assets/content-simulation-click-upload-input-data.png)

&#x200B;3. Scegli **sample.csv** e fai clic su **Continua**.

   ![Scegliere sample.csv e fare clic su Apri](assets/content-simulation-choose-sample-csv-continue.png)

AJO elabora il file e nel tempo prepara le anteprime.
![Anteprime varianti](assets/content-simulation-variation-previews.png)


## Rivedi rendering variante

Quando fai clic su Simula contenuto nell’e-mail, AJO mostra le varianti una accanto all’altra in base ai profili caricati.

**Risultati previsti:**

- **Alex** → vede **Variante 1** (età superiore a 40)
Fai clic sull&#39;icona della matita sopra la prima variante per **Mostra dettagli variante**

![Fai clic sull&#39;icona della matita per visualizzare i dettagli della variante](assets/content-simulation-click-pencil-icon.png)

La scheda si capovolge per mostrare i dettagli su cui si basa la personalizzazione
![Rendering del profilo Alex variante 1 per età superiore a 40](assets/content-simulation-variant-1-age-above-40.png)

- **Jason** → Visualizza **Variante 2** (Età Inferiore A 40)
Fai clic sull&#39;icona della matita sopra la seconda variante di **Mostra dettagli variante**

![Fai clic sull&#39;icona della matita per visualizzare i dettagli della variante](assets/content-simulation-click-pencil-icon-for-second-variant.png)

Sostituisci la visualizzazione affiancata con **Sovrapposizione verticale** per esaminare affiancati i dettagli e la personalizzazione di Jason

![Rendering profilo Jason variante 2 per età inferiore a 40](assets/content-simulation-swap-view-to-vertically-stacked.png)

Quando scorriamo il contenuto dell’e-mail possiamo vedere il nome completo di Jason e l’immagine del contenuto condizionale scelta. Che figata!

![Campo personalizzato con nome completo visualizzato per Jason nella variante 2](assets/content-simulation-personalized-name-field-variant-2.png)



## Convalida comportamento di fallback

**Fallback e impostazioni predefinite:** verifica che l&#39;e-mail gestisca correttamente eventuali dati mancanti o scenari di mancata corrispondenza. Ad esempio, simula un profilo con un campo dell’anno di nascita vuoto o che non sia idoneo per alcuna offerta mirata. L’anteprima deve mostrare un blocco di contenuto predefinito o un segnaposto sensibile invece di contenuto interrotto o vuoto. Se la simulazione mostra una sezione vuota in cui dovrebbe essere presente il contenuto, potrebbe essere necessario configurare un’offerta di fallback o un testo predefinito nella progettazione.


## Riassunto

In questo modulo, esegui correttamente le seguenti operazioni:

- Contenuto personalizzato simulato utilizzando profili di esempio
- Logica di cambio variante convalidata
- I campi personalizzati confermati vengono compilati correttamente

Ora sei pronto per il modulo successivo - **Allineamento marchio**,
dove valuterai l’e-mail in base alle linee guida del brand Connection 5G utilizzando l’intelligenza artificiale.
