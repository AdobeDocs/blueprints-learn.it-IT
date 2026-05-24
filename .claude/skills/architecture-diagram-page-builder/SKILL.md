---
name: architecture-diagram-page-builder
description: 'Guida alla creazione di nuove pagine di diagramma dell’architettura per l’archivio dei blueprint di Adobe Experience Platform. Utilizza questa abilità per aggiungere un nuovo diagramma dell’architettura di livello superiore, una pagina dell’architettura di integrazione o una panoramica dell’architettura delle applicazioni. Le pagine dell’architettura descrivono architetture AEP di primo livello, architetture di applicazioni e punti di integrazione primari, non casi d’uso approfonditi (che appartengono a use-case-pattern-builder). Gestisce l’intero flusso di lavoro: raccolta delle informazioni di pagina, generazione del file Markdown, inserimento nella cartella degli argomenti corretta e aggiornamento di TOC.md.'
source-git-commit: e79d9d6490e4f50c4611dd879b53f0e63a90cd65
workflow-type: tm+mt
source-wordcount: '1393'
ht-degree: 2%

---


# Generatore pagina diagramma architettura

Questa abilità guida la creazione di nuove pagine di diagramma dell’architettura per l’archivio dei blueprint di Adobe Experience Platform. Le pagine dei diagrammi dell’architettura forniscono riferimenti visivi di primo livello sul modo in cui le applicazioni AEP e Adobe si integrano, sui flussi di dati primari che le uniscono e sui punti di integrazione di cui gli autori devono essere consapevoli durante la progettazione delle soluzioni.

## Ambito

Le pagine del diagramma dell&#39;architettura sono **pagine concentrate e in stile di riferimento**, in genere 40-100 righe di markdown, che contengono:

- Uno o più diagrammi di architettura con brevi spiegazioni sullo scopo di ogni diagramma
- Collegamenti ai pattern di casi d’uso supportati dall’architettura (la pagina dell’architettura non duplica tale contenuto)
- È illustrato un breve elenco dei flussi di dati primari e dei punti di integrazione
- Collegamenti Experience League per ulteriori informazioni sul dominio dell’applicazione

Sono **non** il luogo in cui inserire il contenuto del caso d&#39;uso approfondito. I KPI, gli obiettivi aziendali, gli esempi di casi d&#39;uso tattici, le funzionalità e le narrazioni personalizzate appartengono invece alle pagine dei modelli di casi d&#39;uso, generate tramite l&#39;abilità `use-case-pattern-builder`. Vedere `references/scope-guardrails.md` per i guardrail completi.

## Lettura richiesta prima dell&#39;avvio

Leggi i seguenti file di riferimento per modelli e regole:

- `references/diagram-template.md` — modello markdown completo con valori segnaposto
- `references/toc-placement.md` — Tabella di mappatura sottosezione e formato di voce per TOC.md
- `references/scope-guardrails.md`: regole per ciò che appartiene a una pagina dell&#39;architettura rispetto a una pagina del modello del caso d&#39;uso

## Fase 1: Raccolta delle informazioni

Intervistare l&#39;utente per raccogliere tutte le informazioni necessarie prima di generare qualsiasi file. Non procedere alla generazione del contenuto finché non viene fornito o differito esplicitamente ogni elemento richiesto.

### Informazioni richieste

1. **Titolo pagina**: titolo leggibile (ad esempio, `Adobe Journey Optimizer architecture diagrams`).

2. **Cartella argomenti** - Posizione della pagina. Sceglierne esattamente uno in base al dominio principale del diagramma:
   - `experience-platform/` — diagrammi di livello superiore di AEP, multi-app o piattaforma
   - `customer-journeys/` — AJO, Campaign, orchestrazione percorso
   - `customer-journey-analytics/`: architetture CJA
   - `audience-activation/` — Attivazione di RTCDP, pubblico e profilo
   - `b2b/`: architetture specifiche di B2B

3. **Nome file** — Kebab-case, derivato dal titolo della pagina (ad esempio, `Journey Optimizer architecture` -> `journey-optimizer-architecture.md`). Conferma con l’utente.

4. **Scopo della pagina** — 1-2 frasi che descrivono ciò che i diagrammi illustrano collettivamente. Utilizzato per il campo frontmatter `description` e il paragrafo di apertura.

5. **Soluzioni Adobe**: elenco separato da virgole dei prodotti Adobe al centro della pagina. Utilizzato per il campo frontmatter `solution`. Esempi: `Experience Platform, Journey Optimizer, Customer Journey Analytics`.

6. **Diagrammi**: uno o più diagrammi. Per ogni diagramma, raccogliere:
   - **Nome file immagine** (ad esempio, `aep_data_flow.svg`). Preferito SVG; PNG accettabile.
   - **Titolo sezione** — diventa l&#39;intestazione H2 per il diagramma (ad esempio, `Data flow diagram`, `Detailed architecture diagram`).
   - **Spiegazione scopo** — 1-2 frasi che descrivono ciò che viene visualizzato nel diagramma.
   - **Testo alternativo** — breve descrizione accessibile.

7. **Modelli di casi d&#39;uso supportati**: da 2 a 5 modelli esistenti abilitati da questa architettura.

   **Consigliare prima i candidati.** Prima di richiedere all&#39;utente di fornire pattern, esegui la scansione di `/help/blueprints/use-case-patterns/` e propone 3-6 possibili corrispondenze in base al titolo della pagina, allo scopo della pagina e alle soluzioni Adobe raccolte in precedenza. Per ogni suggerimento, presenta:
   - Nome pattern (con il percorso collegato)
   - Una frase che spiega perché si adatta a questa architettura

   Presenta i suggerimenti come una rosa numerata e chiedi all’utente di (a) accettarne qualcuno, (b) rifiutarne qualcuno e (c) aggiungere pattern che non hai accettato. Genera solo suggerimenti che puntano a file reali: glob/read per confermare prima di suggerire. Non allucinare i nomi dei modelli.

   Per ogni modello accettato, acquisite la categoria e il nome del file. Convalidare ogni file esistente in `/help/blueprints/use-case-patterns/{category}/{pattern-file}.md` prima di generarlo.

8. **Flussi di dati primari/punti di integrazione** — 3-7 punti elenco che descrivono i flussi chiave e i limiti di integrazione visualizzati nei diagrammi (ad esempio, `Real-time event ingestion from Web SDK to Edge Network`, `Profile synchronization between Experience Platform Hub and Edge`).

9. **Collegamenti Experience League** — 3-6 collegamenti alla documentazione pertinente di Experience League per ulteriori informazioni. Ogni deve iniziare con `https://experienceleague.adobe.com/`.

   **Consigliare prima i candidati.** In base alle soluzioni Adobe e allo scopo della pagina, propone 4-8 articoli Experience League plausibili (ad esempio, le pagine di destinazione canoniche o di panoramica per ciascuna soluzione denominata, le guide all’integrazione chiave e i riferimenti alla distribuzione). Per ogni suggerimento, presenta:
   - Titolo articolo
   - URL
   - Motivazione in una sola riga del motivo per cui si adatta alla pagina

   Contrassegna i suggerimenti come **non verificati** a meno che non sia stato effettivamente recuperato l&#39;URL. L&#39;utente deve confermare o sostituire ogni suggerimento prima che venga inserito nel file generato. Chiedere all’utente di (a) accettare, (b) sostituire qualsiasi URL con uno verificato che già possiede, e (c) aggiungere il proprio. Non inventare mai URL che non hai visto; se non sei sicuro, suggerisci il titolo dell’articolo e lascia che l’utente fornisca l’URL.

### Facoltativo

- **Callout contenuto correlato**: un singolo collegamento visualizzato come blocco `>[!MORELIKETHIS]` nella parte superiore della pagina. Utile quando è presente una guida all’integrazione o alla configurazione di pari livello su Experience League di cui il lettore deve essere a conoscenza.

Se l’utente non fornisce tutti gli elementi richiesti, chiedi quelli mancanti prima di procedere. Non creare diagrammi, motivi o collegamenti.

## Fase 2: controllo del campo di applicazione

Prima di generare, rileggete le descrizioni dei diagrammi dell&#39;utente, i punti elenco del flusso di dati ed eventuali bozze di testo. Applica guardrail da `references/scope-guardrails.md`.

Se nel contenuto pianificato viene visualizzato uno dei seguenti elementi, avvisa l’utente e offre di reindirizzare tale sezione a una pagina con pattern di caso d’uso (o tagliarla dalla pagina dell’architettura):

- KPI o formule di misurazione
- Obiettivi aziendali o narrazioni sull’impatto aziendale
- Esempi di casi d’uso tattici (scenari di personalizzazione specifici, esempi di campagne, ecc.)
- Funzionalità (`A > B > C > D` style)
- Narrazione basata su persone

Se il contenuto pianificato rimane nell’ambito dell’architettura della pagina (architettura di livello superiore, flusso di dati del sistema, punti di integrazione, topologia di distribuzione, edge o hub), conferma con l’utente e procedi alla fase 3.

## Fase 3: Generazione dei contenuti

Genera la pagina in:

```
/help/blueprints/{topic-folder}/{kebab-filename}.md
```

Utilizza `references/diagram-template.md` come modello di origine. Compila tutti i valori dei segnaposto con le informazioni raccolte. Il file generato deve includere:

1. **Materiale di prima istanza YAML** — `title`, `description`, `solution` solo.
   - **NON includere`exl-id`**. La pipeline di pubblicazione lo assegna automaticamente.
   - **NON includere** `product_v2`, `feature_v2`, `role_v2`, `topic_v2`, `TQID`, `kt` o `thumbnail`. Anche questi elementi vengono compilati automaticamente.

2. **Intestazione H1**: il titolo della pagina.

3. **Apertura del paragrafo** — 1-2 frasi derivate dall&#39;input relativo allo scopo della pagina.

4. **Blocco `>[!MORELIKETHIS]` facoltativo**, solo se l&#39;utente ha fornito un collegamento di contenuto correlato.

5. **Una sezione H2 per diagramma**, nell&#39;ordine in cui è stata fornita dall&#39;utente. Ogni sezione contiene:
   - Titolo della sezione come intestazione H2
   - 1-2 frasi che spiegano lo scopo del diagramma
   - L’immagine viene incorporata utilizzando la convenzione standard:

     ```html
     <img src="assets/{filename}" alt="{Alt Text}" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />
     ```

6. **`## Use case patterns supported`** — elenco puntato. Ogni punto elenco:

   ```
   - [{Pattern name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) -- {1-line note on why this architecture enables the pattern}
   ```

7. **`## Primary data flows and integration points`** — elenco puntato di 3-7 elementi di flusso/integrazione.

8. **`## Further reading`** — elenco puntato dei collegamenti Experience League:

   ```
   - [{Article title}]({Experience League URL})
   ```

Utilizza la sintassi `[!DNL ...]` per i nomi dei prodotti Adobe nel corpo del testo e nei punti elenco, in base alla convenzione delle pagine esistenti.

## Fase 4: aggiornamenti dei riferimenti incrociati

Aggiorna **`/help/blueprints/TOC.md`** per aggiungere la nuova pagina alla navigazione. Questa è l’unica pagina di riferimento incrociato da aggiornare.

Leggi `references/toc-placement.md` per la tabella e le regole di mappatura completa delle sottosezioni. Riepilogo:

| Cartella argomenti | Sottosezione sommario |
| --- | --- |
| `experience-platform/` | `+ Architecture overviews{#architecture-overview}` |
| `experience-platform/deployment/` | `+ Deployment{#deployment}` (sottosezione delle panoramiche dell&#39;architettura) |
| `audience-activation/` | `+ Audience & Profile Activation{#audience-activation}` |
| `b2b/` | `+ B2B activation & marketing{#b2b-activation}` |
| `customer-journey-analytics/` | `+ Customer Journey Analytics{#customer-journey-analytics}` |
| `customer-journeys/` | `+ Customer journeys{#customer-journeys}` |

Formato voce (rientro 4 spazi + `+`):

```
    + [{Page title}](/help/blueprints/{topic-folder}/{filename}.md)
```

Aggiungere la nuova voce come ultimo elemento nella sottosezione corrispondente, a meno che l&#39;utente non specifichi una posizione diversa. Mantenere il rientro esatto di 4 spazi: l&#39;analisi del sommario dipende da esso.

## Fase 5: Convalida

Dopo aver creato e aggiornato tutti i file, verifica quanto segue e segnala eventuali errori all’utente:

1. **Esistenza risorsa immagine**. Per ogni diagramma, verificare che `/help/blueprints/{topic-folder}/assets/{filename}` esista. **Avvisa** se manca; non bloccare (l&#39;utente potrebbe creare in parallelo con la progettazione del diagramma). Crea un elenco chiaro dei file mancanti in modo che l’utente sappia cosa aggiungere.

2. **Collegamenti per casi d&#39;uso**: ogni collegamento per motivi nel file punta a un file Markdown esistente in `/help/blueprints/use-case-patterns/`. Utilizza `Read` o glob per confermare l&#39;esistenza di ogni destinazione.

3. **Collegamenti Experience League** - Controllare che ogni URL nella sezione `## Further reading` inizi con `https://experienceleague.adobe.com/`.

4. **Posizionamento voce sommario**: la nuova voce si trova all&#39;interno della sottosezione corretta, utilizza il rientro a 4 spazi e il percorso corrisponde esattamente alla posizione del file generato.

5. **Denominazione file** - Il nome file della pagina è in caratteri kebab e corrisponde al percorso a cui si fa riferimento nel file TOC.md.

6. **Completezza elemento frontale** - La pagina include `title`, `description` e `solution`. Deve **non** includere `exl-id`, `product_v2`, `feature_v2`, `role_v2`, `topic_v2`, `TQID`, `kt` o `thumbnail`.

Correggi eventuali problemi di convalida prima di considerare il completamento dell’attività.

## Note

- Utilizza sempre la sintassi `[!DNL ...]` per i nomi dei prodotti Adobe nel corpo del testo e nei punti elenco, seguendo la convenzione delle pagine esistenti.
- I diagrammi di architettura sono tipicamente SVG (preferiti per la nitidezza e il ridimensionamento), ma PNG è accettabile per i disegni raster-source.
- Le stringhe di incorporamento in linea (`border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;`) e `class="modal-image"` di `<img>` sono obbligatorie e abilitano l&#39;interazione di zoom modale di Experience League.
- Se l&#39;utente sta creando una pagina per una nuova cartella di argomenti che non esiste ancora, avvisare che TOC.md richiede una nuova sottosezione di livello superiore in `+ Architecture Diagrams and Blueprints{#architecture-diagrams}`. Gestiscilo come passaggio separato con l’approvazione esplicita dell’utente.
- Se il diagramma dell&#39;architettura documenta ampiamente un *caso d&#39;uso singolo end-to-end* (con KPI, obiettivi aziendali, funzionalità), reindirizzare l&#39;utente a `use-case-pattern-builder`, che non è una pagina dell&#39;architettura.
