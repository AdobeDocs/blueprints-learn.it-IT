---
title: Creare gli attributi dell’offerta
description: Aggiungi attributi di dispositivo personalizzati come make, model e tier allo schema XDM standard per l’offerta da utilizzare nelle regole di classificazione e idoneità.
doc-type: article
solution: Experience Platform
exl-id: 00326a7c-8139-46f5-85bd-5ea1f63f29cf
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 0%

---


# Creare gli attributi dell’offerta

## Obiettivo

In questa sezione aggiungerai campi XDM personalizzati allo schema XDM standard per l’offerta. Questi campi personalizzati possono essere utilizzati per la classificazione, l’ordinamento e i criteri di idoneità. Possono anche essere dati restituiti al dispositivo richiedente.

## Crea oggetto principale dispositivo personalizzato

1. Espandi la voce di menu **Decisioning** nella barra a sinistra, se necessario, e fai clic su **Cataloghi.**
2. Per impostazione predefinita, viene visualizzata la pagina &quot;Offerte&quot;. Fare clic sul pulsante **Modifica schema** nell&#39;angolo superiore destro.

   ![Pulsante Modifica schema nella pagina del catalogo delle offerte](assets/create-offer-attributes-edit-schema-button.png)

   >[!TIP]
   >
   >La pagina risultante è l’editor di schema XDM standard. Proprio come XDM viene utilizzato per definire la struttura dati dei set di dati, XDM viene utilizzato qui per definire gli attributi di un’offerta.

   >[!NOTE]
   >
   >Lo schema &quot;Elementi di offerta personalizzati - Experience Decisioning&quot; è uno schema standard generato dal sistema e applicabile a tutte le offerte. Tuttavia, è possibile aggiungere elementi a questo schema per soddisfare esigenze aziendali specifiche, come illustrato in questa sezione.
   >
   >Inoltre, passare attraverso la pagina delle offerte è un collegamento per accedere a questo schema. Puoi anche accedervi tramite il menu Schema nella barra a sinistra.

3. Fai clic sull&#39;icona **+** a destra del livello principale dello schema e, utilizzando il menu &#39;Proprietà campo&#39; ora visibile nella barra a destra, compila i campi seguenti con i valori forniti:
   - Nome campo: **dispositivo**
   - Nome visualizzato: **Dispositivo**
   - Menu a discesa del tipo: **Oggetto**
   - Assegna a gruppo di campi (digita questo valore in): **Dettagli offerta**

   >[!NOTE]
   >
   >Il gruppo di campi Assegna a sembra essere un elenco a discesa, ma accetta anche l’immissione diretta di testo; pertanto, inserisci il testo &quot;Dettagli offerta&quot;. Quando lo digiti in, viene visualizzato anche un elemento &quot;Dettagli offerta (nuovo)&quot;. Qualsiasi nuovo attributo deve essere assegnato a un gruppo di campi, pertanto in questo passaggio stai effettivamente creando un nuovo gruppo di campi denominato Dettagli offerta.

4. Assicurati che tutte le proprietà siano state compilate come nella schermata seguente:

   ![Le proprietà del campo per il nuovo oggetto Device sono state compilate](assets/create-offer-attributes-device-object-field-properties.png)

5. Dopo aver verificato che tutti i campi sono corretti, fai clic sul pulsante blu **Applica** nella parte inferiore del menu &#39;Proprietà campo&#39; (barra a destra) per visualizzare le modifiche applicate allo schema:

![Gruppo di campi dispositivo applicato allo schema dell&#39;offerta](assets/create-offer-attributes-device-object-applied.png)

>[!TIP]
>
>Proprio come il normale XDM, gli attributi personalizzati sono raggruppati in uno spazio dei nomi specifico per l’organizzazione IMS, in questo caso l’ID tenant imsorg o &quot;dep&quot;. Inoltre, il nuovo gruppo di campi &quot;Dettagli offerta&quot; è ora elencato nel riquadro &quot;Composizione&quot;, a sinistra dello schema.

>[!WARNING]
>
>Tieni presente che queste modifiche NON vengono salvate. Sono solo &quot;Applicati&quot;. Se dovessi uscire dalla pagina senza salvare, perderesti il tuo lavoro. Completa i passaggi descritti in questa sezione prima di allontanarti.

## Creare attributi dispositivo personalizzati

Dopo aver creato l’oggetto XDM per dispositivo, puoi passare alla creazione di campi specifici per il dispositivo.

1. Fai clic sull&#39;icona **+** a destra del nuovo oggetto **device** appena creato e, utilizzando il menu &#39;Proprietà campo&#39; nella barra a destra, compila i campi seguenti con i valori specificati:
   - Nome campo: **make**
   - Nome visualizzato: **Make**
   - Menu a discesa Tipo: **Stringa**
   - Assegna a gruppo di campi: **Dettagli offerta** (dovrebbe essere già selezionato)
   - Dopo aver verificato la correttezza di tutti i campi, fai clic sul pulsante blu **Applica** per visualizzare le modifiche applicate allo schema
2. Ripeti i passaggi precedenti per aggiungere due attributi aggiuntivi per **Modello** e **Livello**. Utilizzare lo stesso pattern di denominazione, lo stesso tipo e lo stesso gruppo di campi. Al termine, lo schema dovrebbe essere simile al seguente:

   ![Schema dell&#39;offerta che mostra i campi Make, Model e Tier completati](assets/create-offer-attributes-make-model-tier-fields.png)

3. Dopo aver creato tutti i nuovi campi/attributi XDM, fai clic su **Salva** nell&#39;angolo superiore destro e nella parte inferiore dello schermo riceverai un messaggio verde di tipo &quot;Schema correttamente salvato&quot;. Hai completato i passaggi descritti in questa sezione.

>[!WARNING]
>
>Lo schema appena aggiornato si applica a TUTTE le offerte, comprese quelle future. Presta molta attenzione quando aggiungi attributi a questo schema. Nel nostro esempio di utilizzo di una società di telecomunicazioni che vende telefoni cellulari, la marca del dispositivo, il modello e gli attributi di livello saranno probabilmente ampiamente utilizzati per molte offerte e per gli anni a venire, quindi ha senso aggiungerli. Quando pensi a quali attributi sono necessari per un’offerta, evita di aggiungere attributi univoci a una campagna specifica. Nel corso di mesi o anni, questo schema può gonfiarsi e causare problemi durante la creazione delle offerte. Nella sezione in cui verranno create le offerte, vedrai come si applica questo criterio.

## Riassunto

Lo schema delle offerte standard è stato aggiornato con campi personalizzati riutilizzabili che verranno utilizzati in parti successive del laboratorio durante la creazione e la valutazione delle offerte.
