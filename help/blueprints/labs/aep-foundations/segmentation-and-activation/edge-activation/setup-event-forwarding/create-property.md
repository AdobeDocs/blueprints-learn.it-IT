---
hold: true
title: Crea proprietà
description: Crea una proprietà di Inoltro eventi con un elemento dati e una regola che inoltra gli eventi di esperienza in arrivo a un endpoint del webhook.
doc-type: article
solution: Experience Platform
exl-id: eabd5f75-7706-4c96-982e-2512509bdc55
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 0%

---


# Crea proprietà

In genere si desidera inoltrare un evento esperienza a una terza parte (anche se non deve esserlo). Questa opzione viene in genere utilizzata quando è necessaria una copia di un evento in tempo reale per notificare a una terza parte in circostanze specifiche (ad esempio, per notificare a Google, Meta o TikTok un acquisto).

>[!NOTE]
>
>Promemoria: una proprietà contiene tutte le estensioni, gli elementi di dati e le regole necessari per decidere cosa inoltrare e dove

1. Nella barra a sinistra, fai clic su Inoltro eventi
2. Quindi fai clic su Nuova proprietà

![Sezione Inoltro eventi con il pulsante Nuova proprietà evidenziato](assets/create-property-new-property-button.png "Crea una nuova proprietà di inoltro eventi")

3. Aggiornare il nome della proprietà utilizzando la formula seguente: `Event Forward Property SB + [sandbox number]`. Il nome finale sarà simile al seguente: **Proprietà inoltro eventi SB01**

4. Al termine, fai clic su **Salva**

![Campo nome proprietà inoltro eventi compilato con il pulsante Salva evidenziato](assets/create-property-name-property-form.png)

## Installa estensione

1. Fai clic sulla proprietà di inoltro eventi appena creata

![Elenco delle proprietà di Inoltro eventi con la proprietà appena creata evidenziata](assets/create-property-open-new-property.png "Apri la proprietà evento")



2. Dovresti vedere una schermata come quella di seguito.  Fai clic su **Estensioni**.

![Schermata di panoramica della proprietà Inoltro eventi con la scheda Estensioni evidenziata](assets/create-property-click-extensions-tab.png)



3. Installa l’estensione Adobe Cloud Connector effettuando le seguenti operazioni:

4. Fai clic su **Catalogo** nel menu di navigazione superiore
5. Fai clic sulla scheda **Adobe Cloud Connector**
6. Nella barra a destra, fai clic sul pulsante **Installa**

![Catalogo estensioni con scheda Adobe Cloud Connector ed il pulsante Installa evidenziati](assets/create-property-install-cloud-connector-extension.png)



Dopo aver fatto clic su Installa, l’estensione viene visualizzata in Estensioni installate per la proprietà, come illustrato di seguito.

![Elenco delle estensioni installate che mostra l&#39;estensione Adobe Cloud Connector installata correttamente](assets/create-property-extension-installed-confirmation.png "Estensione completamente installata")

## Creare un elemento dati

>[!NOTE]
>
>Un elemento dati fa riferimento all’evento in ingresso e, se necessario, può analizzarlo in più componenti singoli

1. Nella barra a sinistra, fai clic su **Elementi dati**



![Navigazione nella barra a sinistra con il collegamento Elementi dati evidenziato](assets/create-property-navigate-to-data-elements.png "Passare agli elementi dati")



2. Fai clic sul pulsante **Crea nuovo elemento dati**

![Pagina Elementi dati con il pulsante Crea nuovo elemento dati evidenziato](assets/create-property-create-new-data-element-button.png "Crea nuovo elemento dati")



3. Configura il nuovo elemento dati con le seguenti informazioni:

| Tipo di elemento | Valore da configurare |
| ----------------- | ------------------ |
| Nome | Oggetto dati |
| Estensione | Core |
| Tipo di elemento dati | Codice personalizzato |

![Configurazione dell&#39;elemento dati con i campi Nome, Estensione e Tipo di elemento dati impostati](assets/create-property-data-element-config-step-1.png "Passaggio 1 della configurazione dell&#39;elemento dati")



4. Fai clic sul pulsante **Apri editor** per aggiungere il seguente codice personalizzato:

![Impostazioni degli elementi dati con il pulsante Apri editor evidenziato per il codice personalizzato](assets/create-property-open-custom-code-editor.png "Apri editor")



5. Aggiungi all’editor il codice personalizzato e salvalo

```none
var xdm = arc?.event || '';
return xdm;
```

![Editor di codice personalizzato che mostra lo script che restituisce l&#39;oggetto evento XDM in ingresso](assets/create-property-custom-code-added.png "Codice personalizzato")

>[!NOTE]
>
>Questo consiste nell’acquisire l’intero oggetto xdm senza eseguire alcuna traduzione nel payload.  Se necessario, è possibile analizzare ogni singolo elemento all’interno dell’oggetto XDM (ad esempio nome della pagina, importo dell’acquisto) in un unico elemento dati per campo.  Ciò potrebbe essere dovuto alla trasformazione della struttura in una struttura diversa





6. Fai clic sul pulsante **Salva** per salvare l&#39;elemento dati.

![Editor elementi dati con il pulsante Salva evidenziato](assets/create-property-save-data-element-button.png)



Al termine della procedura, dovresti vedere la seguente schermata che conferma l’aggiunta dell’elemento dati:

![Elenco di elementi dati che mostra l&#39;elemento dati appena salvato aggiunto alla proprietà](assets/create-property-data-element-saved-confirmation.png)


## Creare le regole

>[!NOTE]
>
>Una regola contiene:
>
>1. Condizioni su cosa inoltrare
>2. Azioni che possono trasformare il payload e definire dove inviarlo



1. Nella barra a sinistra fai clic su **Regole**

![Navigazione nella barra a sinistra con il collegamento Regole evidenziato](assets/create-property-navigate-to-rules.png)



2. Quindi fai clic su **Crea nuova regola**

![Pagina Regole con il pulsante Crea nuova regola evidenziato](assets/create-property-new-rule-button.png)



3. Aggiornare il nome della regola utilizzando la formula seguente: `"EF Rule SB" + [your sandbox number]` (ad esempio, regola EF SB01). Puoi trovare il numero della sandbox in alto a destra nella finestra del browser, come mostrato di seguito\...

![Angolo superiore destro della finestra del browser che mostra il numero di sandbox utilizzato nel nome della regola](assets/create-property-sandbox-number-location.png)

4. Al termine, fai clic su **Salva**

>[!NOTE]
>
>Assicurarsi che il nome della regola segua il pattern di formula di `"EF Rule SB" + [sandbox number]`

![Campo nome regola compilato con il pattern di denominazione sandbox della regola EF](assets/create-property-add-rule-name.png "Aggiungi un nome alla regola")



5. Aggiungi un&#39;azione alla regola facendo clic sul segno (+) per aggiungere una nuova azione

![Editor regole con l&#39;icona più evidenziata per aggiungere una nuova azione](assets/create-property-add-action-button.png "Aggiungi un&#39;azione")

## Ottieni URL webhook (da utilizzare in azione)

>[!NOTE]
>
>In questo laboratorio viene utilizzato un webhook per verificare se i dati sono arrivati alla destinazione a cui si sta inviando. In uno scenario reale, invece, accedi a quella destinazione e utilizza i suoi strumenti per vedere cosa è arrivato.



1. Apri il seguente collegamento in una nuova scheda nel browser -> [https://webhook.site](https://webhook.site/)
2. Copia l’URL univoco visualizzato e salvalo in un luogo sicuro

![Pagina WebHook.site con URL univoco evidenziato per la copia](assets/create-property-webhooksite-copy-url.png)



3. Configura l’azione con le seguenti informazioni:

| Impostazione | Valore |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Estensione | Connettore cloud Adobe |
| Tipo di azione | Effettua chiamata di recupero |
| Metodo | Pubblica |
| URL | Utilizza lo stesso URL del webhook utilizzato durante la configurazione della destinazione di streaming. Per trovarla, apri una nuova scheda nel browser e passa a Destinazioni -> Sfoglia |
| Corpo | Raw |
| Dati corpo | \{ &quot;data&quot;: \{ &quot;event&quot;: &quot;\{\{Data Object\}\}&quot; } } |

>[!NOTE]
>
>Il \{\{Data Object\}\} a cui si fa riferimento qui è l’elemento dati creato in precedenza. In questo caso, il requisito del sistema a valle era quello di racchiudere l’evento in un oggetto dati con un oggetto evento. Puoi inserire qui qualsiasi formattazione.
>
>Se avessimo diviso \{\{Data Object\}\} in più campi (ad esempio nome della pagina, acquisto, ecc.), potremmo trasformare la struttura JSON posizionando ogni campo nel punto desiderato, dandoci più controllo sulla corrispondenza con la destinazione.





Dopo aver verificato che la schermata sia simile a quella riportata di seguito, fai clic su **Mantieni modifiche**

![Azione di regola configurata con Adobe Cloud Connector Effettua chiamate di recupero e URL del webhook](assets/create-property-configure-action-settings.png "Configura l&#39;azione")



4. Al termine dell’operazione, dovresti vedere che l’azione è stata aggiunta alla regola. Fai clic su **Salva** per continuare.

![Editor regole che mostra l&#39;azione configurata con il pulsante Salva evidenziato](assets/create-property-save-rule-button.png "Salva la regola")

>[!WARNING]
>
>Quando invii un evento esperienza, stai inviando l’evento, non il profilo, né uno dei suoi attributi, comprese le qualifiche del pubblico (anche se è un pubblico di Edge).
>
>Questo avviene per motivi di velocità.



## Pubblicare le modifiche

1. Nella barra a sinistra, fai clic su **Flusso di pubblicazione**

![Navigazione nella barra a sinistra con il collegamento Flusso di pubblicazione evidenziato](assets/create-property-navigate-to-publishing-flow.png "Passare al flusso di pubblicazione")



2. Fai clic sul pulsante **Aggiungi libreria**

![Pagina Flusso di pubblicazione con il pulsante Aggiungi libreria evidenziato](assets/create-property-add-library-button.png "Aggiungi libreria")



3. Configura la libreria con le seguenti informazioni:

- Nome -> **Libreria EF**
- Ambiente -> **Sviluppo**
- Fai clic su **Aggiungi tutte le risorse modificate**


Al termine, lo schermo dovrebbe essere simile a quello riportato di seguito.  Se tutto sembra a posto, fai clic sul pulsante **Salva e genera in sviluppo**

![Configurazione della libreria con nome, ambiente di sviluppo e pulsante Salva e genera in sviluppo](assets/create-property-configure-library-save-and-build.png)



4. Dovresti vedere la build di sviluppo diventare verde e dichiarare che è pronta per l’uso

![Flusso di pubblicazione che mostra lo stato di sviluppo della build diventato verde e pronto all&#39;uso](assets/create-property-development-build-ready.png)
