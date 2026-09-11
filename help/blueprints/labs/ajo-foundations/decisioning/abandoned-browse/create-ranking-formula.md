---
hold: true
title: Crea formula di classificazione
description: Crea una formula di classificazione che aumenti dinamicamente i punteggi di priorità delle offerte in base agli attributi del profilo, ad esempio l’età.
doc-type: article
solution: Experience Platform
exl-id: 67aaca7f-366c-4db4-a5d5-017f52fbd15b
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '1761'
ht-degree: 0%

---


# Crea formula di classificazione

## Obiettivo

Ora che tutti gli elementi dell’offerta sono stati creati, classificati in ordine di priorità, applicati all’idoneità e organizzati in una raccolta, possiamo rivolgere la nostra attenzione a determinare come verranno classificati per un determinato profilo. A tale scopo, crea una formula di classificazione.

Una formula di classificazione incrementa dinamicamente le priorità di offerta specifiche in modo che &quot;salgano in cima&quot;, in base ai criteri del profilo che interagisce con la proprietà Web/Mobile o con l’evento esperienza stesso.

In questo scenario di laboratorio, faremo finta che il team di marketing di ricerca per Connection 5G abbia mostrato che i minori di 39 anni sarebbero stati attratti dai livelli Ultra o Pro e che quelli 40-59 sarebbero stati attratti dai livelli base e pro. E siccome Connection 5G preferirebbe vendere telefoni di livello superiore, a parità di condizioni, il modello ultra sarebbe presentato prima per i minori di 39 anni, con il modello pro presentato prima per quelli 40-59. In questa sezione verrà illustrato come creare una formula di classificazione per soddisfare tali requisiti aziendali.

## Creare una formula di classificazione e un’espressione predefinita

1. Se necessario, espandi **Decisioning** nella barra a sinistra e fai clic su **Configurazione strategia**. Arrivi alla pagina &quot;Regole di decisione&quot; e vedi la regola di decisione &quot;Piani di livello superiore&quot; creata in precedenza e utilizzata come requisiti di idoneità per gli articoli dell’offerta telefonica di livello superiore.
2. Fare clic su **Formule di classificazione** nel menu &#39;Metodi di classificazione&#39;. Viene aperta una pagina vuota poiché non si dispone ancora di formule di classificazione.

![Pagina delle formule di classificazione vuota prima della creazione di una formula](assets/create-ranking-formula-empty-ranking-formulas-page.png)

&#x200B;3. Fai clic sul pulsante blu **Crea formula** per iniziare a creare una nuova formula di classificazione
&#x200B;4. Denomina la formula di classificazione **iPhone 17 Formula di classificazione**

>[!NOTE]
>
>Quando un evento esperienza viene inviato ad Edge Data Collection con i parametri richiesti per richiedere un’offerta da un pacchetto Decisioning attivo, tutte le offerte in tale pacchetto vengono valutate utilizzando la formula di classificazione. Ogni offerta manterrà la priorità originale o la sua priorità verrà regolata dinamicamente in base al profilo che ha attivato l’evento esperienza.

&#x200B;5. Scorri fino alla parte inferiore della sezione &quot;Criteri&quot; e fai clic sull&#39;icona **\&lt;/>** della casella di testo più in basso e seleziona la variabile **Punteggio di priorità dell&#39;offerta**.

![Variabile del punteggio di priorità dell&#39;offerta selezionata nei criteri della formula di classificazione](assets/create-ranking-formula-select-offer-priority-score.png)

L’espressione predefinita è ora impostata come segue:

![Espressione predefinita impostata sulla variabile del punteggio di priorità dell&#39;offerta](assets/create-ranking-formula-default-expression-set.png)

>[!NOTE]
>
>Questa casella di testo inferiore è l&#39;espressione predefinita applicata a qualsiasi elemento dell&#39;offerta che non soddisfa i criteri di regolazione della priorità. In questo caso, si tratta semplicemente della priorità assegnata all’offerta al momento della sua creazione. Se non viene assegnato alcun punteggio di priorità predefinito alla raccolta su cui verrà eseguita questa formula di classificazione, è necessario assegnare un punteggio predefinito

## Creare regole di regolazione della priorità

Ora che è presente un’espressione predefinita, puoi iniziare ad aggiungere regole che modificano dinamicamente la priorità in base all’età dell’utente.

Un modo per considerare le regole di adeguamento delle priorità è trattarle come istruzioni standard if/then che si applicano solo a determinate offerte. Se il test risulta vero, regola la priorità per le offerte che soddisfano un dato criterio. L’interfaccia utente li organizza in un ordine leggermente diverso, come indicato in questa schermata.

![Ordine dell&#39;interfaccia utente di if, then e where in una regola di adeguamento della priorità](assets/create-ranking-formula-if-then-where-rule-order.png "Ordine dell&#39;interfaccia utente di if, then e where in una regola di adeguamento della priorità")

>[!NOTE]
>
>Il &quot;se&quot; è facoltativo perché si potrebbe applicare una regola di adeguamento della priorità quando un’offerta soddisfa un criterio specifico senza prima un’istruzione condizionale. Espandendo il nostro esempio in questa guida, immagina di avere diverse offerte con un attributo di sistema operativo per telefono (Android vs. iOS). Si potrebbe aumentare la priorità di tutte le offerte di iPhone in cui il sistema operativo preferito del profilo è iOS. Non c&#39;è nessun &quot;se&quot;. È sufficiente &quot;regolare il punteggio in cui attributo offerta = attributo profilo&quot;. Di seguito è riportata un&#39;immagine simile a quella precedente che delinea questa idea senza una dichiarazione condizionale.
>
>![Regola di adeguamento priorità applicata senza un&#39;istruzione condizionale if](assets/create-ranking-formula-rule-without-conditional.png "Regola di adeguamento priorità applicata senza un&#39;istruzione condizionale if")

## Crea criterio 1: regola di adeguamento per i minori di 39 anni

1. Per iniziare, crea la regola di classificazione per l’elemento di offerta Ultra tier. Fare clic sulla prima casella di testo nella sezione **Criterio 1**, quindi fare clic sul pulsante **Seleziona attributo** quando viene visualizzato.

![Opzione Seleziona attributo visualizzata per il criterio 1](assets/create-ranking-formula-criterion-one-select-attribute.png)

&#x200B;2. Quando viene visualizzata la finestra di dialogo &#39;Seleziona un attributo&#39;, fare clic su **Nome offerta**. Una volta selezionata, fai clic su **Salva.**

>[!NOTE]
>
>L’attributo &quot;Decision&quot; si riferisce agli elementi dell’articolo dell’offerta. Poiché è qui che si delineano gli articoli di offerta a cui si applicano i criteri, le uniche opzioni disponibili sono gli attributi dell&#39;articolo di offerta.
>

&#x200B;3. Lascia l&#39;operatore impostato su &quot;È uguale a&quot; e nella casella di testo rimanente immetti il nome dell&#39;elemento di offerta ultra-tier, che è **iphone:17\:ultra**. Dopo aver inserito il testo, l’interfaccia utente si aggiorna e indica che la condizione corrispondente è stata accettata.
&#x200B;4. Fai clic su **+Aggiungi condizione**, quindi fai clic sulla **nuova casella di testo visualizzata** (contiene il testo &#39;*Fai clic per creare un elemento di decisione...*&#39;
&#x200B;5. Fare clic sull&#39;opzione **Seleziona attributo** disponibile&#x200B;**.**
&#x200B;6. Quando si apre la finestra di dialogo &#39;Seleziona un attributo&#39;, fare clic su **Attributi profilo > Persona** (probabilmente sarà necessario scorrere verso il basso) **> Anno di nascita**. Una volta selezionata, fai clic su **Salva.**

>[!NOTE]
>
> &quot;Attributi del profilo&quot; si riferisce all’utente o al profilo che ha inviato l’evento esperienza, mentre &quot;Dati contestuali&quot; si riferisce agli elementi nell’evento esperienza stesso, come URL, nome pagina o altri attributi del payload dell’evento esperienza.

&#x200B;7. Cambia l&#39;operatore in **Maggiore di** e immetti l&#39;anno di nascita **1986** (l&#39;interfaccia utente inserisce una virgola nell&#39;anno, come previsto). Dopo l’immissione, l’interfaccia utente si aggiorna per indicare che la condizione è stata accettata. Dal momento che il caso d&#39;uso aziendale è quello di offrire il livello Ultra a chiunque abbia meno di 40 anni, la priorità viene regolata per chiunque nasca dopo il 1986.

>[!NOTE]
>
>Come indicato in precedenza, l’interfaccia utente indica che queste condizioni aggiuntive sono &quot;facoltative&quot;. Questo è vero perché potrebbe essere utile regolare dinamicamente la priorità di un set di articoli di offerta senza alcun criterio aggiuntivo. È possibile che gli stessi elementi di offerta possano essere utilizzati in una raccolta diversa e classificati con un set diverso di regole di classificazione. Poiché questo laboratorio utilizza un solo insieme di articoli di offerta, vengono utilizzate condizioni aggiuntive per regolare la priorità.

&#x200B;8. La priorità originale per l&#39;articolo di offerta Ultra tier è 4. Per aumentare la priorità, moltiplicalo per 100. A tale scopo, fai clic sull&#39;icona **\&lt;/>** accanto all&#39;ultima casella di testo e seleziona la variabile **Punteggio di priorità dell&#39;offerta**. Aggiungi **\*100** dopo il testo immesso automaticamente. Questa espressione moltiplica la priorità originale (4) per 100 e le assegna una nuova priorità di 400.

   La regola ora dovrebbe essere simile alla seguente:

![Regola criterio 1 che aumenta il punteggio di priorità dell&#39;offerta Ultra tier di 100](assets/create-ranking-formula-criterion-one-ultra-boost.png)

>[!NOTE]
>
>Perché moltiplicare per 100? L&#39;idea è che se volete assicurarvi che le vostre priorità siano aggiustate ben al di sopra delle altre, e 100 è solo un modo di fare semplice matematica per far sì che ciò accada. Le formule di classificazione possono essere complicate, come vedrai nella sezione successiva, quindi è utile mantenere la matematica semplice.
>
>Inoltre, mentre abbiamo utilizzato la moltiplicazione per aumentare il punteggio di priorità, altre espressioni matematiche avrebbero potuto essere utilizzate per diminuire il punteggio di priorità. In generale, tuttavia, è più facile fare le offerte desiderate &#39;fluttuare verso l&#39;alto&#39; che fare offerte che non si vogliono &#39;affondare verso il basso&#39;.



## Crea criterio 2: regola di adeguamento per i 40-59

1. Subito sotto la regola di regolazione appena creata, fare clic sul pulsante **+ Aggiungi criterio**.
2. Crea una condizione corrispondente per il caso in cui **Il nome dell&#39;offerta** NON è uguale a **iphone:17\:ultra**.

>[!WARNING]
>
>Questa regola si applica a tutti gli altri elementi dell’offerta. Maggiori dettagli sul perché sono più avanti in questa pagina, ma dovresti prestare molta attenzione all’utilizzo di questo tipo di logica nella pratica, in quanto si applicherebbe a ogni offerta della raccolta che non ha questo valore. Nel nostro caso, va bene, ma potrebbe non esserlo in altri casi d’uso.

3. Aggiungi la condizione che questa regola deve essere applicata a chiunque abbia un anno di nascita maggiore di **1966** (chiunque abbia meno di 60 anni).
4. Come per la regola precedente, moltiplica il punteggio di priorità predefinito dell’elemento dell’offerta per 100. Al termine, la regola &quot;Criterio 2&quot; si presenta così:

![Regola criterio 2 che regola la priorità per i profili nati dopo il 1966](assets/create-ranking-formula-criterion-two-rule.png)

>[!NOTE]
>
>L’utilizzo congiunto di formule di classificazione e regole di idoneità può risultare complesso, ma ecco l’idea di base:
>
>- **Le formule di classificazione** regolano dinamicamente i punteggi di priorità e, di conseguenza, l&#39;ordine delle offerte.
>- **Le regole di idoneità** (come le regole di decisione e i limiti di frequenza) rimuovono le offerte dall&#39;elenco ordinato se l&#39;utente non è autorizzato a visualizzarle.
>
>Di seguito viene illustrato l’ordine delle offerte, sulla base di questi esempi e della formula di classificazione appena creata:
>
>**Anno di nascita = 1990**
>
>- Ultra Priority diventa **400**
>- Pro = **3**, Base = **2**, Generico = **1**
>  Risultato: Ultra viene visualizzato prima (fino a 3 volte), quindi Pro, Base e infine Generic.
>
>**Anno di nascita = 1970**
>
>- La priorità Ultra rimane a **4**
>- Pro diventa **300**, Base = **200** e Generico = **100**
>  Risultato: Pro viene visualizzato per primo (3 volte), quindi Base, quindi Generico. Ultra viene ordinato per ultimo perché la sua priorità (4) è inferiore a Generico (100).
>
>Quando l’idoneità viene applicata tramite le regole di decisione e il limite di frequenza,
>
>- Gli utenti nati nel 1990 con un ID **piano = 1** avranno offerte Ultra e Pro rimosse, anche se si sono classificati ai primi posti. L&#39;utente vede le offerte Base e Generic solo perché i livelli Ultra e Pro hanno una condizione aggiuntiva: solo gli utenti con **ID piano 2 o 3** possono vederle.
>- Poiché l&#39;offerta generica non ha regole per il limite di frequenza, l&#39;utente dell&#39;anno di nascita **1970** non vedrà mai l&#39;offerta Ultra, in quanto il suo punteggio di priorità è inferiore al punteggio incrementato del generico.

&#x200B;5. Con tutte le regole e il punteggio di priorità predefinito attivo, scorri verso l&#39;alto e fai clic sul pulsante blu **Crea** nell&#39;angolo superiore destro.

>[!TIP]
>
>Ora viene visualizzata la pagina &quot;Impostazione strategia&quot; con la formula di classificazione singola appena creata.
> [!NOTE]
>
>Cosa succede se due offerte danno la stessa priorità? Le offerte con lo stesso punteggio di priorità vengono scelte a caso per tornare al sistema richiedente.

## Riassunto

In questa pagina è stata creata una formula di classificazione che determina il modo in cui gli articoli dell’offerta vengono ordinati dinamicamente per ciascun profilo. Hai anche definito un’espressione predefinita (il punteggio di priorità originale), quindi hai aggiunto regole di adeguamento della priorità che incrementano le priorità delle offerte in base ai criteri del profilo (ad esempio l’età). Questa logica di classificazione assicura che le offerte rilevanti (come i livelli Ultra o Pro per intervalli di età specifici) raggiungano il livello più alto quando vengono valutate.
