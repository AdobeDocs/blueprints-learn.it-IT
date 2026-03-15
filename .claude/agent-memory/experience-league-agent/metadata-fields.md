---
source-git-commit: a632042b3a7434dd88f52804e15e30fa06057e3b
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 1%

---
# Adobe Experience League — Riferimento campi metadati approvati

*Originato dalla Guida all&#39;authoring di Adobe ExL (scansionata febbraio 2026) + analisi dell&#39;archivio dei blueprint-learn.en*

&#x200B;---

## Gerarchia metadati

I metadati vengono inseriti in cascata in questo ordine (l’articolo sostituisce il sommario, il sommario sostituisce l’archivio):
1. Articolo (priorità massima)
2. TOC.md nella guida utente
3. metadata.md nella directory principale dell’archivio (priorità più bassa)

&#x200B;---

## Campi a livello di articolo

### OBBLIGATORIO

| Campo | Descrizione | Formato/Vincoli |
|-------|-------------|----------------------|
| `title` | Titolo pagina SEO. Viene visualizzato nei risultati di ricerca. | Massimo ~60 caratteri; maiuscole/minuscole; utilizzare `[!DNL Product]` per i nomi dei prodotti; NON duplicare H1 esattamente se non previsto |
| `description` | Descrizione di Meta per motori di ricerca e consigli ExL. | 150-160 caratteri; idealmente inizia &quot;Scopri come...&quot; o &quot;Ulteriori informazioni su...&quot;; la convalida non riesce se mancante/null |
| `exl-id` | Identificatore univoco assegnato dal sistema. Utilizzato per il tracciamento dei contenuti. | Formato UUID (ad esempio `70573eb9-cd69-4fe6-b2ae-dae81665a308`); **elimina durante la copia di un file** — verrà assegnato automaticamente; non duplicare mai tra i file |

### FORTEMENTE CONSIGLIATO

| Campo | Descrizione | Valori validi |
|-------|-------------|--------------|
| `solution` | Prodotti Adobe coperti dall&#39;articolo. Utilizzato per ricerche/filtri ExL e consigli sui contenuti. | Separato da virgole; con distinzione tra maiuscole e minuscole; deve corrispondere all&#39;enum approvato (vedi Valori validi delle soluzioni di seguito) |

### FACOLTATIVO — COMUNE

| Campo | Descrizione | Valori/Note validi |
|-------|-------------|----------------------|
| `kt` | Numero JIRA legacy dell’articolo della conoscenza. Utilizzato per il tracciamento di Analytics. | Intero (ad esempio `7207`); vuoto accettabile; `null` accettabile |
| `thumbnail` | Immagine di riferimento per Recommendations/Analytics (Consigli/Analisi). | Stringa nome file o `null` o vuota |
| `version` | Filtro versione prodotto. Utilizzato principalmente per i blueprint di AEM e Campaign. | E.g. `Campaign v8`, `Campaign v8 Client Console`; deve corrispondere a version.yml |
| `doc-type` | Classificazione del contenuto utilizzata in repo/analytics. | `blueprint`, `overview-page`, `Video`, `Tutorial`, `Troubleshooting` (preferito in minuscolo) |
| `feature` | Tag di argomenti visualizzati come &quot;Argomenti&quot; nelle pagine ExL. | 1-2 per articolo; maiuscole/minuscole nei titoli; deve corrispondere a feature.yml; separato da virgole |
| `feature-set` | Applicazione padre per la convalida della funzionalità. | Deve corrispondere ai valori feature.yml |
| `role` | Ruolo del pubblico di destinazione. Visualizzato come &quot;Creato per&quot; su ExL. | `Admin`, `Architect`, `Data Architect`, `Data Engineer`, `Developer`, `Leader`, `User` |
| `level` | Livello di esperienza utente. Visualizzato come &quot;Creato per&quot; su ExL. | `Beginner`, `Intermediate`, `Experienced` (iniziali maiuscole) |
| `topic` | Argomenti tra prodotti diversi per ricerca/filtro. | Maiuscole/minuscole nei titoli; deve corrispondere a topic.yml; separato da virgole |
| `type` | Classificazione della guida. | `Documentation` (predefinito), `Tutorial`, `Troubleshooting` |
| `last-substantial-update` | Consente di visualizzare il contenuto nei widget &quot;Novità&quot;. | Formato: `YYYY-MM-DD` |
| `hide` | Esclude la pagina da tutte le ricerche e i consigli; imposta inoltre l’indice su no. | `yes` o `no` |
| `hidefromtoc` | Rimuove dal sommario di navigazione ma la pagina è ancora accessibile tramite collegamento diretto. | `yes` o `no` |
| `index` | Controlla se la pagina viene visualizzata nella ricerca/mappa del sito esterna. | `yes`/`no` o `y`/`n`; impostazione predefinita: `no` (indicizzato) |
| `recommendations` | Controlla il comportamento del widget &quot;Ulteriori informazioni su questa funzione&quot;. | `noDisplay` (impedisce la visualizzazione dei widget), `noCatalog` (esclude dal pool di consigli) |
| `internal` | Contrassegna la pagina come Solo interna di Adobe. Impedisce la segnalazione di collegamenti interni. | `yes` |
| `short-description` | Descrizione ridotta per le pagine di destinazione ExL. Usa `description` se omesso. | Una frase; massimo ~20 parole |
| `activity` | Classificazione dell’utilizzo della pagina. | `understand`, `implement`, `troubleshoot` (minuscolo) |
| `sub-product` | Sottocomponente del prodotto. Lavora con i team della soluzione per ottenere enum valide. | Minuscolo; esempio: `search`, `assets`, `sites` |
| `team` | Assegnazione del team per Analytics. | E.g. `TM` |
| `landing-page-name` | Collegamenti alla pagina di destinazione per il breadcrumb. | E.g. `experience-manager` |
| `landing-page-breadcrumb-title` | Testo della breadcrumb per il collegamento della pagina di destinazione. | E.g. `AEM` |
| `auto-video-transcripts` | Abilita le trascrizioni video per impostazione predefinita. | `true` |
| `badgeType` | Badge per lo stato del contenuto. | Varia; esempio: `informative`, `positive` |
| `badgePremium` | Indicatore di badge Premium. | Specifica del badge per Adobe |
| `badgeLabel` | Testo etichetta badge. | Stringa breve |
| `source-git-url` | URL archivio Source. | URL GitHub completo |
| `cloud` | Sostituzione categoria cloud a livello di articolo. | Tutte iniziali maiuscole; devono corrispondere a cloud.yml |

&#x200B;---

## Campi TOC.md

| Campo | Descrizione | Note |
|-------|-------------|-------|
| `user-guide-title` | Nome della guida visualizzato nelle breadcrumb ExL e nelle pagine di destinazione. | Obbligatorio per i file TOC |
| `breadcrumb-title` | Nome guida più breve per le breadcrumb quando user-guide-title è troppo lungo. | Facoltativo |
| `user-guide-description` | Riepilogo della guida per la pagina di destinazione ExL. | Una frase; consigliato un massimo di ~20 parole |
| `product` | Tracciamento di Analytics per la guida. Solo valore singolo. | Deve corrispondere a product.yml (vedi Valori di prodotto validi) |
| `mini-toc-levels` | Numero di livelli di intestazione visualizzati nel mini-TOC di navigazione a destra. | Intero 1-6; predefinito 2 |
| `role` | Ruolo di pubblico predefinito per la guida. | Stessi valori dell&#39;articolo `role`; separati da virgola |
| `index` | Indica se la guida è indicizzata. | `yes`/`no` |

&#x200B;---

## Campi metadata.md a livello di repository

| Campo | Note |
|-------|-------|
| `cloud` | Categoria cloud predefinita per tutti gli articoli nel repository |
| `solution` | Soluzione predefinita per tutti gli articoli |
| `product` | Prodotto predefinito per il tracciamento di Analytics |
| `type` | Tipo di guida predefinito |
| `doc-type` | Tipo documento predefinito |
| `mini-toc-levels` | Livelli mini-TOC predefiniti |
| `git-repo` | URL archivio GitHub; abilita i pulsanti &quot;Modifica questa pagina&quot; e &quot;Registra problema&quot; |
| `index` | Impostazione di indice predefinita |

&#x200B;---

## Valori Soluzione Validi (Distinzione Maiuscole/Minuscole)

Valori comuni utilizzati in questo archivio:
- `Experience Platform`
- `Real-Time Customer Data Platform`
- `Journey Optimizer`
- `Journey Optimizer B2B Edition`
- `Customer Journey Analytics`
- `Campaign`
- `Campaign v8`
- `Campaign Classic v7`
- `Campaign Standard`
- `Audience Manager`
- `Target`
- `Analytics`
- `Data Collection`
- `Commerce`
- `Marketo Engage`
- `Experience Cloud`
- `Journey Orchestration`

Più valori: separati da virgola, ad esempio `Real-Time Customer Data Platform, Campaign`

&#x200B;---

## Valori di prodotto validi (per il campo `product` - tracciamento di Analytics)

Per l&#39;elenco completo, vedere il prompt del sistema. Valori chiave:
- `adobe experience platform` / `experience platform` / `aem`
- `adobe analytics` / `analytics` / `aa`
- `adobe journey optimizer` / `journey optimizer` / `jo`
- `adobe customer journey analytics` / `customer journey analytics` / `cja`
- `adobe real time customer data platform` / `real time cdp` / `rtcdp`
- `adobe marketo` / `marketo` / `amk`
- `adobe campaign` / `campaign` / `ac`
- `adobe target` / `target` / `at`

&#x200B;---

## Valori Ruolo Validi

- `Admin`
- `Architect`
- `Data Architect`
- `Data Engineer`
- `Developer`
- `Leader`
- `User`

&#x200B;---

## Regole di convalida chiave

1. Non lasciare mai `exl-id` con lo stesso UUID in un file copiato. Eliminarlo e lasciare che il sistema ne assegni uno nuovo.
2. Sono accettabili `thumbnail` e `kt` vuoti/nulli; si tratta di campi legacy.
3. I valori `solution` devono corrispondere esattamente all&#39;enum approvato, con distinzione tra maiuscole e minuscole.
4. La convalida di `description` non riesce se manca o è null. Specificare sempre un valore significativo.
5. Racchiudi i valori `title` tra virgolette se contengono due punti, parentesi o caratteri speciali iniziali.
6. Più valori `solution` sono separati da virgole all&#39;interno di un singolo valore stringa.
7. `product` è solo un valore singolo (per il tracciamento di Analytics); non utilizzare valori separati da virgola.
8. Per richiedere nuovi valori enum, crea un ticket JIRA UGP con il componente &quot;Tag contenuto&quot;.
