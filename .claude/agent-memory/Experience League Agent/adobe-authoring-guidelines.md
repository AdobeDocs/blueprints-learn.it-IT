---
name: Adobe Experience League Authoring Guidelines
description: Riferimento completo per le regole di authoring di Markdown di Adobe Experience League, scansionato dalla guida ufficiale all’authoring di marzo 2026.
type: reference
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '1664'
ht-degree: 0%

---


# Linee guida per l’authoring di Adobe Experience League

Source: https://experienceleague.adobe.com/en/docs/authoring-guide/using/home
Scansionato: 15/03/2026

&#x200B;---

## &#x200B;1. METADATI/FRONT MATTER

### Campi obbligatori
| Campo | Requisito | Regole |
|---|---|---|
| `title` | Obbligatorio | Massimo 60 caratteri (inglese). Tutte iniziali maiuscole. Nessun nome di prodotto a meno che non sia necessario per chiarezza. Il sistema aggiunge &quot; | ProductName&quot; automaticamente. Racchiudi tra virgolette se contiene due punti o parentesi. |
| `description` | Obbligatorio | 150-160 caratteri max. Non può essere vuoto/nullo. I concetti iniziano con &quot;Scopri di...&quot; Le attività iniziano con &quot;Scopri come&quot;. o verbo imperativo. |

### Campi facoltativi ma di uso frequente
| Campo | Valori validi | Note |
|---|---|---|
| `feature` | Deve corrispondere ai valori YAML della funzione; tutte le iniziali maiuscole devono essere spazi (esempio: &quot;Frammento di contenuto&quot;) | 1-2 per articolo; viene visualizzato in Argomenti |
| `feature-set` | È necessario eseguire la convalida rispetto alla funzione YAML | Applicazione padre della feature |
| `role` | Utente, Sviluppatore, Leader, Amministratore, Architetto, Architetto dati, Ingegnere dati | Maiuscole/minuscole; viene visualizzato come &quot;Creato per&quot; |
| `level` | Principiante, Intermedio, Esperto | Predefinito come Principiante se non specificato |
| `solution` | Deve corrispondere alla soluzione YAML (ad esempio, &quot;Campaign, Campaign Standard v7&quot;) | Sono consentiti più valori; utilizzato per il filtro di ricerca |
| `topic` | Deve corrispondere all&#39;argomento YAML; la combinazione di maiuscole e minuscole nei titoli deve corrispondere agli spazi | Per il filtraggio tra prodotti (ad esempio, &quot;Integrazioni&quot;) |
| `type` | Documentazione, tutorial, risoluzione dei problemi | A livello di archivio; viene utilizzata per impostazione predefinita la documentazione |
| `short-description` | Una frase, massimo 20 parole | Per le pagine di destinazione ExL quando la descrizione è troppo lunga |
| `badgePremium` | `label="Premium" type="Positive" url="..."` | Badge a livello di pagina |
| `mini-toc-levels` | 1-6 (impostazione predefinita 2) | Controlla la profondità di visualizzazione dell&#39;intestazione del menu di navigazione a destra |
| `hidefromtoc` | true/false | Esclude dalla navigazione a sinistra ma mantiene l’URL accessibile |

### Posizionamento metadati
- Livello articolo: inizio del file markdown come argomento principale YAML
- Livello sommario: nel file TOC.md
- Livello archivio: nel file metadata.md

### Regole di formattazione chiave
- Racchiudi i valori contenenti virgole o parentesi tra virgolette
- Più valori separati da virgole
- Corrispondenza con distinzione tra maiuscole e minuscole rispetto alle definizioni YAML
- Valori di tag vuoti/vuoti causano errori di convalida

### Campi obsoleti
seo-title, seo-description, pubblico, difficoltà, uuid (dall&#39;era della migrazione)

&#x200B;---

## &#x200B;2. SINTASSI MARKDOWN (AROMATIZZATO CON ADOBE)

### Formattazione testo
- Grassetto: `**text**`
- Corsivo: `*text*`
- Grassetto + Corsivo: `***text***`
- Esci dai caratteri speciali: usa la barra rovesciata `\` prima di `# { } [ ] * + - . !`
- Entità HTML: `&lt;` `&gt;` `&amp;` `&mdash;` `&ndash;`

### Intestazioni
- Usa stile ATX (solo sintassi `#`, mai sottolineatura/testo)
- Una H1 per documento (in genere il titolo della pagina corrisponde ai metadati `title`)
- Tutti i titoli successivi H2 (`##`) o inferiore
- Righe vuote necessarie prima e dopo le intestazioni (tranne la prima intestazione)
- Massimo 69 caratteri (inglese) / 120 caratteri (localizzati)
- Max ~5 parole preferite
- Maiuscole/minuscole per tutte le intestazioni (solo maiuscolo per la prima parola e i sostantivi propri)
- Solo maiuscole/minuscole per il campo di metadati `title`
- Nessuna punteggiatura finale (sono consentiti punti interrogativi per le intestazioni delle domande frequenti)
- ID di ancoraggio personalizzati: `## Title {#custom-id}`. Utilizzare i trattini e non i punti
- Nessun ID di ancoraggio titolo duplicato in un documento
- Evita nomi di ancoraggio riservati: ricerca, risultati, facet, impaginazione, ordinamento, query, casella di ricerca, contenuto, intestazione, piè di pagina, principale, navigazione, barra laterale, pagina, contenitore, wrapper
- Segui ogni titolo con almeno un paragrafo del corpo del testo (non inserire elenchi/tabelle direttamente dopo un titolo)
- Intestazioni del concetto: frasi sostantivo/sostantivo
- Intestazioni attività: verbi imperativi (NON gerundi — &quot;Creare un segmento&quot; non &quot;Creare un segmento&quot;)
- Struttura parallela tra i livelli di intestazione

### Elenchi
- Punto elenco (non ordinato): `*`, `-` o `+`. Utilizzo coerente all&#39;interno di un documento
- Ordinato: `1.` per ogni elemento (numeri automatici)
- Righe vuote prima e dopo gli elenchi
- Rientra elementi numerati nidificati 3 spazi; punti elenco nidificati 2 spazi
- Punteggiatura punto elenco: omettere punti e virgola/virgole/congiunzioni alla fine; aggiungere punti solo per le frasi complete
- Non aggiungere punti se tutti gli elementi sono ≤3 parole o sono etichette/intestazioni dell’interfaccia utente

### Collegamenti
- Esterno: `[text](https://url.com)`
- Relativo (stesso livello): `[text](file.md)`
- Relativo radice: `[text](/help/path/file.md)` — deve iniziare con `/`
- Collegamenti profondi (stessa pagina): `[text](#heading-anchor)`
- Collegamenti diretti tra documenti: `[text](file.md#heading-id)`
- Forza nuova scheda: `[text](url){target="_blank"}`
- URL vuoti: racchiudi tra parentesi angolari `<https://example.com>` per rendere selezionabile
- Collegamenti di riferimento: solo i collegamenti assoluti funzionano per i collegamenti di tipo riferimento
- Non includere lo stesso file in più posizioni del sommario tramite collegamenti relativi
- Utenti Windows: convertire le barre rovesciate in barre in avanti nei percorsi

### Immagini
- Base: `![alt text](image.png "hover tooltip")`
- Ridimensiona: `{width="300"}`
- Allinea: `{align="center"}` o `{align="right"}`
- Zoom consentito: `{zoomable="yes"}` o `{modal="regular"}`
- Dimensione massima del file: 100 MB (consigliati meno di 5 MB)
- Il testo alternativo è OBBLIGATORIO per tutte le immagini (per SEO e accessibilità)
- Nomi file immagine: lettere minuscole con trattini
- Memorizzare le immagini in una cartella risorse designata

### Blocchi di codice
- In linea: backticks `` `code` ``
- Usa per: nomi di file, URL, termini definiti dall&#39;utente, comandi
- Blocchi di codice delimitati: tre apici retroversi con identificatore della lingua

  ```
  ```javascript

  code here

  ```

  ```

  
  
- Opzioni: `{line-numbers="true"}`, `{start-line="7"}`, `{highlight="11-13, 16"}`
- Includi sempre un identificatore della lingua nei blocchi di codice delimitati

### Tabelle
- La riga del separatore richiede almeno 3 trattini per colonna: `|---|---|---|`
- Allineamento: `|---|` sinistra, `|:---:|` centro, `|---:|` destra
- Esci dai pipe letterali: `\|` o usa `&vert;`
- Tabelle HTML consentite; utilizzare `<table style="table-layout:auto">` o `table-layout:fixed`
- Allineamento tabella HTML: `<td align="left|center|right">`
- Evita la sintassi Markdown nelle tabelle di HTML (ad esempio, `[!NOTE]` non funziona nelle tabelle di HTML)
- Rimuovi bordi: `<tr style="border: 0;">`
- Opzione layout tabella Markdown: aggiungi `{style="table-layout:auto"}` dopo la tabella con righe vuote
- Evitare tabelle molto ampie/alte a causa di problemi di visibilità delle barre di scorrimento orizzontali

&#x200B;---

## &#x200B;3. ESTENSIONI SPECIALI DELLA SINTASSI ADOBE

### Callout/ammonizioni

```
>[!NOTE]
>
>Text here.

>[!TIP]
>
>Text here.

>[!IMPORTANT]
>
>Text here.

>[!WARNING]
>
>Text here.

>[!CAUTION]
>
>Text here.

>[!ADMIN]
>[!AVAILABILITY]
>[!PREREQUISITES]
>[!INFO]
>[!ERROR]
>[!SUCCESS]
```

- CRITICO: nessuno spazio tra `>` e `[ !`. Utilizzare `>[!NOTE]` NOT `> [!NOTE]`
- Aggiungi una riga vuota tra `>[!NOTE]` e la riga del corpo del testo

### Schede

```
>[!BEGINTABS]

>[!TAB iOS]
Content here

>[!TAB Android]
Content here

>[!ENDTABS]
```

### Sezioni comprimibili (Accordions)

```
+++Click to expand
Content inside
+++
```

Nota: le sezioni comprimibili nidificate NON sono supportate.

### Scatole ombreggiature

```
>[!BEGINSHADEBOX "Optional Title"]
Content here
>[!ENDSHADEBOX]
```

### Video

```
>[!VIDEO](https://video.tv.adobe.com/v/ID/?quality=12&learn=on)
```

Aggiungi `{transcript=true}` per le trascrizioni.

### Altri argomenti correlati

```
>[!MORELIKETHIS]
>* [Article 1](url)
>* [Article 2](url)
```

### Aiuto contestuale

```
>[!CONTEXTUALHELP]
>id="..."
>title="..."
>abstract="..."
>additional-url="..."
```

### Badge (in linea)

```
[!BADGE Label]{type=Informative url="https://example.com" tooltip="text"}
```

Tipi: `Informative` (blu), `Positive` (verde), `Negative` (rosso), `Neutral` (grigio), `Caution` (giallo)

### Evidenziazione testo (anteprima)

```html
<span class="preview">highlighted text</span>
```

### Inclusioni e snippet
- Includi intero file: `{{$include /help/_includes/legal-blurb.md}}`
- Snippet (senza intestazioni): `{{snippet-id}}`
- Archivia file riutilizzabili nella cartella `help > _includes/`
- Snippet archiviati in `help > _includes/snippets.md`
- Le inclusioni possono avere intestazioni; i frammenti NON POSSONO
- Funziona solo all’interno dello stesso archivio (non cross-repo)
- Esci da `{{` o `}}` caratteri nei file senza riferimenti

### Tag DNL (Do Not Localize)
- `[!DNL ProductName]` - esegue il wrapping dei nomi di prodotti/marchi che non devono essere tradotti
- Utilizzare la prima o la prominente menzione all&#39;interno di una pagina

### UICONTROL Tag
- `[!UICONTROL Button Label]` — applica il wrapping al testo dell&#39;elemento dell&#39;interfaccia utente (pulsanti, menu, nomi dei campi)
- Assicura che le stringhe dell’interfaccia utente vengano richiamate dai database dei prodotti anziché dalla traduzione automatica
- Nessun apostrofo, virgoletta o punteggiatura nei tag UICONTROL
- Utilizza il grassetto per gli elementi dell’interfaccia utente a cui si fa riferimento nei passaggi

### Funzioni non supportate
- Elenchi di task (caselle di controllo)
- Emoji
- Regole orizzontali
- Sezioni comprimibili nidificate

&#x200B;---

## &#x200B;4. DENOMINAZIONE DEI FILE E STRUTTURA DELLE CARTELLE

### Regole di denominazione dei file
- Nomi di file in minuscolo con solo trattini
- Nessun carattere maiuscolo, carattere di sottolineatura, punto o spazio
- Nomi descrittivi e descrittivi SEO (ad esempio, `calculated-metric-overview.md` non `cmo.md`)
- Evita i numeri nei nomi dei file; usa parole descrittive
- Evita nomi riservati/in conflitto: `metadata.md`, `search.md`
- La ridenominazione di file live richiede la gestione dei reindirizzamenti (modifiche URL)

### Struttura delle cartelle
- I nomi di directory/cartelle NON influiscono sugli URL (solo i nomi di repository e i nomi di file influiscono sugli URL)
- TOC.md controlla la gerarchia di navigazione e non la posizione della cartella Git
- Memorizzare immagini/risorse in una cartella risorse specifica
- Include riutilizzabili archiviati in `help/_includes/`
- Snippet archiviati in `help/_includes/snippets.md`

### Regole TOC.md
- Per eseguire il rendering su Experience League, ogni articolo deve essere elencato in TOC.md
- Formato H1: `# Guide Title {#anchor-id}` — l&#39;ancoraggio genera il percorso URL di base
- Le intestazioni di sezione devono avere ID di ancoraggio: `+ Section Name {#section-id}`
- Le intestazioni di sezione (elementi padre) non possono essere collegamenti
- Collegamenti articolo: `+ [Title](path/file.md)`
- La modifica degli ID di ancoraggio della sezione cambia tutti gli URL degli articoli nidificati (richiede reindirizzamenti)
- Usa stile punto elenco coerente in (`+`, `*` o `-`)
- Metadati sommario: `user-guide-description`, facoltativamente `breadcrumb-title`
- `mini-toc-levels`: controlla la visualizzazione dell&#39;intestazione del menu di navigazione a destra (1-6, impostazione predefinita 2)

&#x200B;---

## &#x200B;5. QUALITÀ DEI CONTENUTI E STANDARD EDITORIALI

### Voce e tono
- Voce attiva preferita rispetto a passiva
- Il presente nel futuro
- Seconda persona (&quot;tu&quot;) per contenuti istruttivi
- Frasi sotto 35 parole
- Verbi forti e precisi — evitare avverbi deboli (&quot;molto&quot;, &quot;estremamente&quot;)

### Passaggi/Procedure
- Ogni passaggio è UN comando singolo e conciso (una frase)
- Le informazioni supplementari vengono inserite nella riga successiva (rientrate sotto il passaggio)
- Inizia ogni passaggio con un verbo imperativo
- Limita le procedure a circa 7 passaggi (massimo ~10 prima di suddividerle in sottoattività)
- Posizionare le informazioni concettuali PRIMA dei passaggi
- Posiziona le schermate DOPO il passaggio pertinente
- Ripeti i nomi di pagina/scheda per l&#39;orientamento del lettore
- Formattazione grassetto UICONTROL per gli elementi dell’interfaccia utente nei passaggi

### Terminologia interfaccia
- **Apri/Chiudi**: applicazioni e programmi
- **Vai a**: menu, schede o posizioni dell&#39;interfaccia utente
- **Seleziona**: testo, celle o opzioni da elenchi
- **Clic**: azioni del mouse (evitare di specificare il tipo di controllo se non essenziale)
- **Menu a discesa** (non &quot;elenco a discesa&quot;)

### Nomi prodotti
- Non aggiungere il nome del prodotto a titoli o intestazioni a meno che non sia necessario per maggiore chiarezza
- Ometti &quot;il&quot; prima dei nomi dei prodotti
- Includi &quot;Adobe&quot; nella prima menzione a livello di guida (requisito del marchio)
- Elimina &quot;Adobe&quot; nelle menzioni secondarie a meno che non sia legalmente richiesto
- Utilizza i tag DNL per i nomi dei prodotti per evitare errori di traduzione

### Enfasi e formattazione
- Grassetto: elementi dell’interfaccia utente e azioni da tastiera
- Corsivo: messaggi di errore, parole straniere, enfasi
- Codice (contrassegni): nomi di file, URL e termini definiti dall’utente
- Nessuna virgoletta intorno agli elementi dell’interfaccia utente (utilizza il tag UICONTROL)

### Maiuscole
- Caso di frase per titoli, navigazione, sottotitoli
- Solo maiuscole/minuscole per il campo di metadati `title`
- I sostantivi appropriati sono sempre maiuscoli

&#x200B;---

## &#x200B;6. BEST PRACTICE SEO

- Una H1 per pagina: deve essere concisa, descrittiva, per comunicare agli utenti la pagina
- Gerarchia di intestazioni sequenziali (h1 → h2 → h3, senza saltare mai i livelli)
- Includi parole chiave in H1, corpo del testo e metadati (non nel metatag `keywords`, verrà ignorato da Google)
- Evita l&#39;inserimento di parole chiave (intento > frequenza)
- Titolo: max. 50-60 caratteri; il sistema aggiunge &quot;| Adobe ProductName&quot; automaticamente
- Descrizione: 150-160 caratteri; deve essere un call to action, non una ripetizione di contenuto
- Aggiungi testo alternativo descrittivo a tutte le immagini
- Includi trascrizioni video (i motori di ricerca possono solo leggere il testo)
- Collegamento strategico alle pagine correlate (evitare pagine orfane)
- Includi elementi strutturati: elenchi numerati, sottotitoli, blocchi di codice
- Utilizza strumenti come AnswerThePublic, Google Trends per cercare parole chiave
- Il contenuto deve dimostrare l&#39;E-A-T (esperienza, competenza, autorevolezza, affidabilità)

&#x200B;---

## &#x200B;7. LOCALIZZAZIONE

### Traduzione automatica
- Il contenuto sorgente in inglese genera automaticamente versioni localizzate
- Lingue supportate: tedesco, francese, giapponese, italiano, spagnolo, portoghese brasiliano, cinese semplificato, cinese tradizionale, coreano, olandese, svedese

### Scrittura per la localizzazione
- Coerenza terminologica nell&#39;intero
- Brevi frasi e voce attiva
- Ordine delle parole inglese standard (oggetto → verbo → oggetto)
- Usa pronomi relativi (&quot;che&quot;, &quot;che&quot;)
- Evita: umorismo, idiomi, gergo, frasi regionali, metafore, parole non necessarie

### Tag di localizzazione
- `[!UICONTROL Label]`: assicura il pull delle stringhe dell&#39;interfaccia utente dal database del prodotto, non la traduzione automatica
- `[!DNL ProductName]` — impedisce la traduzione di prodotti/marchi
- Le immagini in una cartella &quot;do-not-localize&quot; (non localizzare) sono escluse dalla localizzazione

&#x200B;---

## &#x200B;8. TIPI DI CONTENUTO

- **Guida**: raccolta online di pagine a cui si fa riferimento nel sommario; descrive le best practice ufficiali
- **Tutorial**: contenuto istruttivo (video o testo) per casi d&#39;uso specifici; pubblicato in learn repos
- **Guida di riferimento**: API/SDK per sviluppatori; in genere formato tabella; pubblicato in developer.adobe.com
- **Corso**: raccolta di lezioni curata da esperti che eseguono il targeting di ruoli utente specifici
- **Articoli della Knowledge Base**: breve, contenuto temporaneamente rilevante per la risoluzione dei problemi
- **Pagina di destinazione/Home page**: gestita separatamente (SCCM)

&#x200B;---

## &#x200B;9. ERRORI DI CONVALIDA COMUNI DA EVITARE

- Metadati `title` o `description` mancanti o vuoti
- `description` non inizia con &quot;Ulteriori informazioni su...&quot; o &quot;Scopri come...&quot;
- Spazio tra `>` e `[ !` nella sintassi del callout (`> [!NOTE]` anziché `>[!NOTE]`)
- Spazi in grassetto: `**text **` (lo spazio finale è in grassetto)
- Sintassi Markdown all’interno delle tabelle HTML (ad esempio, i callout non funzionano lì)
- ID di ancoraggio titolo duplicati in un documento
- Ancorare gli ID contenenti punti (utilizza i trattini)
- Utilizzo di nomi di ancoraggio riservati (ricerca, risultati, intestazione, piè di pagina, ecc.)
- Valori `role`, `level`, `feature`, `topic` che non corrispondono alle definizioni YAML
- Intestazioni sovrapposte senza corpo del testo tra di esse
- H1 utilizzato più di una volta per documento
- Livelli di rotta saltati (ad esempio, H1 → H3)
- Denominazione dei file con caratteri maiuscoli, trattini bassi o spazi
- Testo alternativo mancante nelle immagini
- Intestazioni attività Gerund (&quot;Creazione in corso...&quot;) invece di &quot;Crea...&quot;)
