---
hold: true
title: Creare un pubblico
description: Scopri come utilizzare l’attività Genera pubblico in una campagna orchestrata per eseguire il targeting delle linee attive dei clienti con una telefonata specifica utilizzando le condizioni dello schema relazionale.
doc-type: article
solution: Experience Platform
exl-id: 697d3edb-2b63-4038-a934-3587495e17f7
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 0%

---


# Creare un pubblico

## Obiettivo

Nei passaggi successivi creerai il pubblico di destinazione per la campagna, ovvero tutti i titolari di linea attivi con una marca che corrisponde al telefono di punta che viene avviato.  L’obiettivo è il gruppo di destinazione con un messaggio SMS che spinge i clienti ad aggiornare il telefono.



## Aggiungi attività Genera pubblico

1. Nell&#39;area di lavoro fare clic sul simbolo **+** e quindi selezionare l&#39;attività **Genera pubblico** per aggiungerla al flusso di lavoro

![Aggiungi attività Genera pubblico all&#39;area di lavoro del flusso di lavoro](assets/build-an-audience-add-activity.png)



2. Nella barra a destra trovi le proprietà Genera pubblico. Aggiornare l&#39;etichetta per indicare quanto segue: `Active Lines with Apple`

![Genera etichetta pubblico impostata su Linee attive con Apple](assets/build-an-audience-set-label.png)


## Seleziona dimensione di targeting

Il passaggio successivo consiste nel selezionare la **dimensione di targeting** (ovvero la tabella su cui si desidera eseguire la query). Effettua le seguenti operazioni:

1. Fai clic sull&#39;**icona di ricerca** nella casella Dimensione targeting

![Icona Ricerca nella casella della dimensione Targeting](assets/build-an-audience-search-targeting-dimension.png)

2. Nella finestra a comparsa, cercare e selezionare la tabella denominata **dep-rel: Customer Line**, quindi fare clic sul pulsante **Confirm**.

![Selezionare la tabella Dep-rel: Customer Line e fare clic su Conferma](assets/build-an-audience-select-customer-line-table.png)

>[!NOTE]
>
>Ricorda sempre la **dimensione di targeting** di ogni pubblico creato. Scoprirai il suo significato nei passaggi successivi.

>[!NOTE]
>
>se selezioni uno schema creato da Adobe, noti che lo schema inizia con -> *(caas)*. Questo è solo uno spazio dei nomi applicato alle tabelle all’interno dell’archivio relazionale e sta per Campaign as a Service :)



## Creare un pubblico

Ora che hai selezionato la dimensione di targeting (lo schema relazionale su cui stai eseguendo la query) puoi iniziare a creare la definizione.

1. Nella barra a destra, fai clic sul pulsante **Crea pubblico**

![Pulsante Crea pubblico nella barra a destra](assets/build-an-audience-click-create-audience.png)

2. Fai clic sul pulsante **Aggiungi condizione**

![Pulsante Aggiungi condizione per la definizione del pubblico](assets/build-an-audience-click-add-condition.png)



## Crea condizioni

Ora è il momento di scrivere la logica del pubblico utilizzando gli attributi presenti nello schema. L’obiettivo è quello di trovare tutte le linee di clienti attive e che utilizzano una marca di Apple.

### Crea #1 condizione

1. Impostare la condizione utilizzando le seguenti informazioni:
   - **Attributo**: `Active Line`
   - **Valore**: `true`

![Condizione 1 impostata su Linea attiva uguale a true](assets/build-an-audience-condition-active-line-true.png)

2. Fai clic sull&#39;icona **Aggiorna** per visualizzare i conteggi validi per la condizione.

![Icona di aggiornamento che mostra il conteggio qualificato di 241 per la condizione 1](assets/build-an-audience-condition-1-refresh-count.png)

>[!TIP]
>
>Se la condizione è stata generata correttamente, viene visualizzato il risultato di 241



### Crea #2 condizione

1. Fai clic sul pulsante **Aggiungi condizione** e seleziona lo schema **dep-rel:** **Prodotto \[Ricerca]** facendo clic sull&#39;icona **>**

![Selezionare lo schema dep-rel: prodotto [Ricerca] facendo clic sull&#39;icona >](assets/build-an-audience-select-product-lookup-schema.png)


2. Cerca il campo denominato **Make**, fai clic sui tre punti e seleziona **Distribuzione dei valori**

![Opzione Distribuzione di valori per il campo Make](assets/build-an-audience-make-distribution-of-values.png)



3. Prendi nota dei vari valori. Vuoi solo `Apple` e per fortuna non ha 100 ortografie diverse. Fai clic sul **campo Apple** per selezionarlo, quindi fai clic sul **pulsante Seleziona attributo e valore** in alto a destra.

![Valore Apple selezionato con il pulsante Seleziona attributo e valore](assets/build-an-audience-select-apple-attribute-value.png)

>[!NOTE]
>
>Questo è un esempio emblematico di dove l’architetto dei dati avrebbe dovuto progettare lo schema con le enumerazioni.  In questo modo, un addetto marketing non deve selezionare/digitare manualmente il valore.  Vergogna all&#39;architetto dei dati!



4. Il campo `Make` viene aggiunto automaticamente insieme alle condizioni mostrate di seguito.
   - **Operatore:** `Equal to`
   - **Valore:** `Apple`
   - **Distinzione maiuscole/minuscole:** `Enabled`

5. Fai clic sull&#39;icona **calcola** e visualizzerai 85 come risultato.

![Condizione 2 conteggio calcolato di 85](assets/build-an-audience-condition-2-final-count.png)

>[!NOTE]
>
>Si noti l&#39;utilizzo dell&#39;operatore AND nel gruppo. Sia che lo si crei in un singolo gruppo come mostrato, sia che lo si crei in più gruppi, l’operatore AND è importante perché indica a Orchestrated Campaigns che entrambe le condizioni devono essere vere.



## Verifica i conteggi

1. Fai clic sull&#39;icona **Calcola** trovata nella barra a destra sotto l&#39;intestazione Profili interessati per ottenere una stima esatta della dimensione del pubblico. **65** come **conteggio finale**.

![Icona Calcola che mostra la dimensione finale del pubblico di 65](assets/build-an-audience-calculate-final-audience-size.png)

>[!NOTE]
>
>Nota come ogni singola condizione ha restituito un numero diverso (condizione #1 —> 241 e condizione #2 —> 85), ma la dimensione finale del pubblico era la minore tra le due condizioni.  Ciò è dovuto a tale operatore AND.



2. Se visualizzi il conteggio finale di **65**, fai clic sul pulsante **Conferma** in alto a destra dello schermo, quindi fai clic sul pulsante **Salva** in alto a destra per salvare i tuoi dati.



## Sfida

Si supponga per un momento di aver digitato nell&#39;ultima condizione in modo che `Make` fosse uguale a `apple` (in minuscolo) e di aver lasciato l&#39;opzione di configurazione per `Case sensitive` attivata `on`.  In questo modo il conteggio dei record delle condizioni diventerebbe uguale a 0.  Avreste 241 linee attive e 0 dove la marca è mela.



**Quale sarebbe la dimensione finale del pubblico in questo caso?**

![Ultima condizione che mostra un conteggio record di 0 &quot;L&#39;ultima condizione è 0&quot;](assets/build-an-audience-challenge-zero-count-condition.png "L&#39;ultima condizione è 0")

## Risposta

È zero. Sapete il perché?

![Spiegazione del motivo per cui il conteggio finale è zero](assets/build-an-audience-answer-zero-count-explanation.png)



## Riassunto

Hai creato correttamente il primo pubblico e ora dovresti vedere quanto è facile sviluppare e convalidare i conteggi nell’attività Genera pubblico.

![Compilazione dell&#39;attività del pubblico completata dopo il riassunto](assets/build-an-audience-recap-completed-audience.png)
