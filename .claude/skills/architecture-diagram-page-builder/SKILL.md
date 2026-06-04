---
name: architecture-diagram-page-builder
description: 'Guida alla creazione di nuove pagine di diagramma dell’architettura per l’archivio dei blueprint di Adobe Experience Platform. Utilizza questa abilità per aggiungere un nuovo diagramma dell’architettura di livello superiore, una pagina dell’architettura di integrazione o una panoramica dell’architettura delle applicazioni. Le pagine dell’architettura descrivono architetture AEP di primo livello, architetture di applicazioni e punti di integrazione primari, non casi d’uso approfonditi (che appartengono a use-case-pattern-builder). Gestisce l’intero flusso di lavoro: raccolta delle informazioni di pagina, generazione del file Markdown, inserimento nella cartella degli argomenti corretta e aggiornamento di TOC.md.'
source-git-commit: 4d236750286c28a8b8eb53a5bdec0645cc0e3e91
workflow-type: tm+mt
source-wordcount: '1556'
ht-degree: 1%

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

**Utilizzare i moduli, non un&#39;intervista lineare.** Raccogliere tutte le informazioni richieste presentando `AskUserQuestion` moduli in batch logico anziché porre una domanda alla volta. In questo modo l’esperienza viene mantenuta veloce e analizzabile per l’utente.

### Vincoli AskUserQuestion

- Massimo **4 domande** per chiamata `AskUserQuestion`.
- Massimo **4 opzioni** per domanda.
- Se una domanda ha più di 4 opzioni plausibili, suddividila in due chiamate (ad esempio, chiedi le prime 4 opzioni, quindi segui con un sì/no sulla quinta).
- Utilizza `multiSelect: true` per domande a cui si applicano più risposte (soluzioni, modelli, flussi di dati).

### Turno 1 — Informazioni pagina core (una chiamata AskUserQuestion, fino a 4 domande)

Richiedi tutti gli elementi seguenti in un unico modulo:

1. **Titolo pagina** — presenta 2-3 varianti suggerite derivate da ciò che l&#39;utente ti ha già detto, più un tratteggio di escape &quot;Altro&quot;.
2. **Cartella argomento**: presenta le 5 cartelle valide come opzioni. Consiglia quella più probabile in base all&#39;input dell&#39;utente.
3. **Soluzioni Adobe** — a selezione multipla; suggerisci i candidati più probabili in base all&#39;argomento della pagina.
4. **Conteggio diagrammi** - quanti diagrammi includerà la pagina (1 / 2 / 3 / 4+).

### Turno 2 — Dettagli diagramma (una chiamata AskUserQuestion, fino a 4 domande)

Richiedere il nome del file immagine di ogni diagramma e lo scopo della pagina in un unico modulo:

- Per ogni diagramma (fino a 2 in un singolo round di moduli), chiedi il **nome file immagine** come domanda con 2-3 nomi file suggeriti (derivati dal titolo della pagina) più un&#39;opzione &quot;Altro&quot;.
- Chiedi lo **scopo pagina** (descrizione di 1-2 frasi) come domanda con 2-3 frasi suggerite più &quot;Altro&quot;.
- Chiedere se è necessario un callout **`>[!MORELIKETHIS]`** (Sì / No). Se Sì, raccogli l’URL e il testo di collegamento in un messaggio di follow-up.

> **Titoli di sezione e testo alternativo:** Se il nome del file dell&#39;immagine è descrittivo (ad esempio, `fac-architecture.svg`, `fac-dataflow.svg`), dedurre il titolo della sezione H2 e il testo alternativo da esso. Non è necessario chiedere all&#39;utente. Utilizzare lo stelo del nome file, con maiuscole e minuscole, come titolo della sezione (ad esempio, `Architecture diagram`, `Data flow diagram`). Chiedi solo se il nome del file è ambiguo.

### Turno 3 — Modelli di casi d&#39;uso (AskUserQuestion dopo la scansione)

Prima di presentare questo modulo, **glob`/help/blueprints/use-case-patterns/`** e identifica 3-5 probabili pattern corrispondenti in base al titolo della pagina, allo scopo e alle soluzioni. Conferma l’esistenza di ogni file prima di suggerirlo.

Presentare i primi 4 candidati come domanda `multiSelect`. Se esiste un quinto candidato forte, seguire con una domanda sì/no separata per quello. Invita inoltre l’utente a citare un nome per il pattern che non hai seguito.

Includi solo i pattern i cui file sono confermati come esistenti. Non allucinare i nomi dei modelli.

### Turno 4 — Flussi di dati e collegamenti Experience League (una chiamata AskUserQuestion)

**Flussi di dati:** proporre 3-5 punti elenco del flusso di dati prescritti come domanda `multiSelect` (derivata dall&#39;argomento della pagina). L’utente seleziona l’opzione applicabile. Mantieni ogni opzione su una frase concisa. Se l’utente necessita di flussi personalizzati non presenti nell’elenco, può fornirli in un follow-up.

**Collegamenti Experience League:** Dopo il modulo, presenta una tabella markdown di 4-6 collegamenti suggeriti con titolo dell&#39;articolo, URL e una motivazione di una riga. Contrassegna ogni URL come **non verificato**. Chiedi all’utente di (a) accettare, (b) sostituire con un URL verificato, o (c) aggiungere il proprio. Utilizzare un `AskUserQuestion` di completamento con un massimo di 4 opzioni se l&#39;elenco è lungo; in caso contrario, accettare la conferma in testo normale.

Non inventare mai URL che non sono stati recuperati. Se non è sicuro, suggerisci il titolo dell’articolo e lascia che l’utente fornisca l’URL.

### Quando tutti gli arrotondamenti sono completati

Prima di generare qualsiasi file, conferma il set di informazioni completo con l’utente. Se un elemento richiesto risulta ancora mancante o contrassegnato come &quot;Altro&quot; senza valore, richiederlo prima di procedere. Non creare diagrammi, motivi o collegamenti.

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

**Controllare i sottogruppi nidificati prima del posizionamento.** Alcune sottosezioni (in particolare `Audience & Profile Activation`) contengono raggruppamenti nidificati (ad esempio `Real-Time Customer Data Platform (RTCDP) {#known-customer-audience-activation}`). Leggi la sottosezione interessata di TOC.md prima di modificarla. Le nuove pagine dell&#39;architettura di primo livello appartengono al livello di rientro a 4 spazi della sottosezione, **not** all&#39;interno di un sottogruppo nidificato (che utilizza il rientro a 6 spazi). Posizionare la nuova voce dopo l&#39;ultima voce di sottogruppo nidificata e prima dell&#39;intestazione di sottosezione di livello superiore successiva.

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
