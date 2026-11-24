---
title: Personalizzazione dei contenuti assistiti da IA
description: Utilizza l’intelligenza artificiale di Adobe Journey Optimizer per generare l’oggetto del brand, perfezionare la copia e il tono delle e-mail e creare immagini generate da Firefly all’interno dell’e-mail designer.
doc-type: article
solution: Experience Platform
exl-id: 1f30c920-7b2b-4343-b663-ebbed1ae4709
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: ea468b0eddaacdb7beaa1227c9c335371d089f34
workflow-type: tm+mt
source-wordcount: '1311'
ht-degree: 5%
---

# Personalizzazione dei contenuti assistiti da IA

**Scopo:** scopri come utilizzare l&#39;intelligenza artificiale di Adobe Journey Optimizer per generare gli oggetti, perfezionare il testo delle e-mail, regolare il tono e creare immagini Firefly direttamente all&#39;interno della finestra di progettazione e-mail.

## Obiettivi di apprendimento

Al termine di questo modulo, sarai in grado di:

1. Utilizza l’intelligenza artificiale per generare gli oggetti e le intestazioni preliminari.
1. Perfeziona testo, descrizioni, tono e messaggi dell’eroe.
1. Applicare riformulazioni, riepiloghi e regolazioni dei toni basate sull’intelligenza artificiale.
1. Genera immagini utilizzando Adobe Firefly con stile di riferimento e impostazioni del brand.
1. Sostituisci i segnaposto con le immagini generate all’interno della progettazione delle e-mail.

## Introduzione

L’assistenza basata sull’intelligenza artificiale in AJO consente di creare contenuti più intelligenti e all’interno del brand.
Può:

- Genera righe oggetto
- Migliorare il testo esistente
- Regolare tono e chiarezza
- Creazione di immagini con marchio tramite Firefly
- Assicurati che tutto sia allineato alle linee guida per la connessione 5G

Per questo esercizio, puoi migliorare l’e-mail creata utilizzando l’intelligenza artificiale.

>[!NOTE]
>
>L&#39;IA è **non deterministica**, ovvero può generare contenuto leggermente diverso ogni volta che viene utilizzato. Le informazioni visualizzate durante l&#39;esercitazione potrebbero non corrispondere esattamente alle schermate o agli esempi contenuti in questa guida. Va bene, concentrati sull’apprendimento del processo e dei concetti anziché aspettarti risultati identici.

## Creare la riga dell’oggetto e-mail tramite IA

1. Torna alla campagna facendo clic sul pulsante Indietro o modifica l’e-mail creata nel modulo precedente. Dal passaggio precedente, puoi fare clic sulla scheda **Impostazioni** a destra.
2. Fai clic sul Contenitore e-mail > sul pulsante Modifica e-mail.
3. Fai clic sulla scheda del contenuto e quindi sul corpo dell’e-mail
4. Selezionare il campo **Oggetto**.
5. Fai clic sull&#39;icona **IA**. (vedi sotto)

   ![Icona IA nella barra degli strumenti del campo Oggetto](assets/ai-assistant-and-content-personalization-ai-assistant-icon.png)

6. Per impostazione predefinita, è selezionata l’opzione Linee guida per i marchi.
7. Immetti il prompt:

   >Stiamo lanciando iPhone 17 e vogliamo che l’oggetto sia accattivante

8. Premere **Genera**.
9. Esamina le quattro varianti generate.
10. Scegli la variante con il miglior punteggio di allineamento e fai clic su **Seleziona**.

![Selezione della variante dell&#39;oggetto meglio allineata da AI](assets/ai-assistant-and-content-personalization-select-subject-line-variant.png)

>[!NOTE]
>
>I risultati potrebbero essere completamente diversi dalla guida di laboratorio, quindi non è necessario preoccuparsi. Seleziona quello che pensi sia un titolo corretto e continua con il laboratorio.




## Migliora titolo e descrizione protagonista

1. Apri l’e-mail facendo clic sul pulsante &quot;Modifica corpo dell’e-mail&quot;.

   ![Pulsante Modifica corpo e-mail nell&#39;editor di Campaign](assets/ai-assistant-and-content-personalization-edit-email-body-button.png)

2. Fai clic sull&#39;intestazione **Product Catchy line**.
3. Avvia assistenza IA facendo clic su **Genera e seleziona un testo**

   ![Genera e seleziona un&#39;opzione di testo per aprire IA](assets/ai-assistant-and-content-personalization-generate-and-select-text.png)

4. Seleziona **Linee guida per il marchio Connection 5G** dal menu a discesa.

   ![Opzione Linee guida per il marchio Connection 5G selezionata nel menu a discesa IA](assets/ai-assistant-and-content-personalization-brand-guidelines-dropdown.png)

5. Prompt:

   >*Scrivi un titolo in grassetto per il lancio di iPhone 17. Mantieni il testo sotto le 10 parole*

6. Fare clic su Impostazioni testo per modificare il tono e la strategia di comunicazione. Cambia la strategia di comunicazione in **FOMO (Paura di perdere)**, Lingua in **Inglese** e Tonalità in **Eccitante**.

   ![Pannello impostazioni testo con strategia di comunicazione FOMO e tono eccitante selezionato](assets/ai-assistant-and-content-personalization-text-settings-fomo-tone.png)

7. Fai clic sul pulsante **Genera**
8. Rivedi e **Seleziona** la versione migliore

![Selezione del testo del titolo principale protagonista generato](assets/ai-assistant-and-content-personalization-select-generated-hero-text.png)

## Prompt descrizione

Questa volta, verifichi come l’intelligenza artificiale può aiutare a individuare i problemi.

1. Seleziona il testo sottostante che è testo con modelli e non ha alcun significato.

   ![Testo segnaposto con modello selezionato per la valutazione](assets/ai-assistant-and-content-personalization-select-templated-text.png)

2. Fai clic sul pulsante Valuta come mostrato di seguito.

   ![Pulsante Valuta nel pannello di testo IA](assets/ai-assistant-and-content-personalization-click-evaluate-button.png)

3. Il contenuto originale viene selezionato automaticamente con il marchio, come illustrato nei passaggi 1 e 2. Fare clic sul pulsante **Valuta** per continuare.

   ![Contenuto originale selezionato automaticamente con le linee guida del brand prima della valutazione](assets/ai-assistant-and-content-personalization-evaluate-brand-alignment.png)

4. Come previsto, puoi notare molti errori che violano le linee guida del brand. Anche se queste possono essere corrette utilizzando l’intelligenza artificiale, in questo caso non è necessario rivedere il testo del segnaposto. È invece possibile immettere tutto il nuovo contenuto per la descrizione.

   ![I risultati della valutazione IA mostrano violazioni delle linee guida del brand](assets/ai-assistant-and-content-personalization-brand-guideline-errors.png)

5. Puoi seguire gli stessi passaggi del titolo principale precedente, utilizzando il prompt seguente oppure... per risparmiare tempo puoi anche sostituire il testo segnaposto con un paragrafo pronto fornito di seguito.

Prompt:

>*Scrivi una descrizione convincente del prodotto per il nuovo iPhone 17. Evidenzia le sue caratteristiche più straordinarie, come la fotocamera avanzata, la durata della batteria e le prestazioni. Il tono dovrebbe essere premium, emozionante, e facile da capire per un pubblico ampio. Mantieni il contenuto in 3 frasi.*

Paragrafo pronto:

>Scopri iPhone 17™, con una fotocamera avanzata per foto straordinarie, durata della batteria per tutto il giorno e prestazioni incredibilmente veloci che ti mantengono in testa. Non perdere questa esperienza innovativa.



L’e-mail ha un aspetto simile all’esempio mostrato di seguito.

![Anteprima e-mail dopo l&#39;aggiunta del nuovo testo di descrizione generato dall&#39;intelligenza artificiale](assets/ai-assistant-and-content-personalization-email-with-description-text.png)


## Aggiungere un’immagine generata da Firefly

Finora, abbiamo testato l’intelligenza artificiale sull’oggetto e sul testo. E le immagini?

Prima di immergerti nella generazione di immagini AI, osserva quali tipi di esperienze puoi creare.

Sappiamo che abbiamo l&#39;anno di nascita del profilo. Una delle esperienze che possiamo fare è creare un blocco con diverse varianti. Con Adobe Journey Optimizer, questo è possibile e uno dei maggiori vantaggi di avere Adobe Experience Platform come base. La sperimentazione verrà illustrata nel modulo successivo, ma prima prepareremo il blocco seguente.

1. Trascina un componente **Immagine** nella colonna di sinistra sotto il blocco famiglia iphone 17.

   ![Trascinamento di un componente Immagine sotto il blocco della famiglia iPhone 17](assets/ai-assistant-and-content-personalization-drag-image-component.png)

2. Fai clic all’esterno, quindi seleziona il segnaposto dell’immagine. Assicurati di fare clic sull’immagine, altrimenti non visualizzerai l’opzione Firefly.

   ![Selezione del segnaposto immagine per accedere alle opzioni di Firefly](assets/ai-assistant-and-content-personalization-select-image-placeholder.png)

3. In **Firefly**, fare clic su **Genera e selezionare l&#39;immagine**.

![Genera e seleziona l&#39;opzione immagine in Firefly](assets/ai-assistant-and-content-personalization-firefly-generate-select-image.png)

## Carica immagine di riferimento

1. Attiva **Stile riferimento**.
2. Seleziona **Connection 5G Brand Guideline** per la selezione del brand

   ![Linee guida per il marchio Connection 5G selezionate per lo stile di riferimento immagine](assets/ai-assistant-and-content-personalization-select-brand-guideline-reference.png)

3. Fai clic su **Carica immagine**

   ![Pulsante Carica immagine nel pannello di stile riferimento di Firefly](assets/ai-assistant-and-content-personalization-click-upload-image.png)

4. Selezionate reference.jpg dalla cartella toolkit

   ![Selezione di reference.jpg dalla cartella toolkit](assets/ai-assistant-and-content-personalization-select-reference-jpg.png)

5. Prompt Aggiungi immagine
   `Portrait-oriented image of a confident man in his early to mid-40s, standing alone at night in a neon-lit urban street, focused on his smartphone. Cinematic cyberpunk-inspired city atmosphere with colorful LED signs, cool blue and warm orange lighting, shallow depth of field, soft bokeh lights in the background. Modern lifestyle, tech-savvy mood, realistic skin tones, high contrast, photorealistic, professional lighting, ultra-detailed`.

![Campo del prompt delle immagini di Firefly con descrizione verticale immesso](assets/ai-assistant-and-content-personalization-firefly-image-prompt.png)

## Scegli impostazioni immagine

Scorri verso il basso nella colonna sinistra e fai clic su **Altre impostazioni**

![Seleziona altre impostazioni](assets/ai-assistant-and-content-personalization-select-more-settings.png)

1. Scegliere le impostazioni seguenti:
   - **Rapporto:** Orizzontale (4:3)
   - **Tipo di contenuto:** foto
   - **Colore e tonalità:** Tono fresco
   - **Illuminazione:** Illuminazione Drammatica

2. Premi il pulsante **Genera**

![Impostazioni dell&#39;immagine di Firefly, inclusi rapporto, tipo di contenuto e illuminazione, prima della generazione](assets/ai-assistant-and-content-personalization-firefly-image-settings.png)

&#x200B;3. Seleziona le varianti a destra per visualizzarle e **Salva** alcuni dei tuoi preferiti nella cartella Assets per utilizzarli in un secondo momento. Puoi anche fare clic su Genera altre volte per ottenere altre varianti.

![Sfoglia le varianti e salva alcune](assets/ai-assistant-and-content-personalization-browse-image-variations.png)

![Salva nella cartella Assets](assets/ai-assistant-and-content-personalization-save-image-variations-into-assets.png)

&#x200B;4. Quindi per il momento è sufficiente **Annulla** dall&#39;interfaccia di generazione dell&#39;immagine.



## Finalizzare la progettazione dei blocchi

1. Nell&#39;interfaccia di e-mail designer, fare clic su **Sfoglia** nel blocco immagine.

![Fare clic su Sfoglia nel blocco immagine](assets/ai-assistant-and-content-personalization-click-browse-in-image-block.png)

&#x200B;2. Seleziona una delle varianti e fai clic su **Seleziona**

![Seleziona una delle varianti](assets/ai-assistant-and-content-personalization-select-one-of-your-variations.png)

&#x200B;3. Seleziona la scheda **Stili** nella colonna di destra e applica all&#39;immagine un raggio del bordo arrotondato di 10

![Progettazione del blocco e-mail finale con angoli immagine arrotondati](assets/ai-assistant-and-content-personalization-final-block-design.png)

Dopo alcune iterazioni e varianti, viene creata la progettazione finale. Il layout finale è simile all&#39;esempio precedente.

A questo punto, dovresti aver acquisito sicurezza nell’utilizzo dell’intelligenza artificiale per accelerare e migliorare la creazione dei contenuti.

## Riassunto

Hai utilizzato correttamente l’intelligenza artificiale per:

- Genera righe oggetto
- Ridefinisci testo principale
- Riformulare i paragrafi
- Cambia il tono dei messaggi
- Creazione di immagini Firefly con marchio utilizzando lo stile di riferimento
- Inserire le immagini generate nell’e-mail

Ora sei pronto per il modulo successivo - **Personalization e sperimentazione dei contenuti**, in cui verranno create varianti e test basati sul profilo.
