---
name: use-case-icon-generator
description: Genera le specifiche delle icone e i prompt di generazione delle immagini per le icone dei casi d’uso nell’archivio dei blueprint di Adobe Experience Platform. Utilizza questa abilità per creare icone per nuovi casi d’uso di settore, quando l’abilità del generatore di casi d’uso di settore richiede un’icona o quando l’utente chiede di creare o aggiornare le icone dei casi d’uso. Genera un prompt di generazione dell'immagine dettagliato che l'utente può utilizzare con Midjourney, DALL-E, Adobe Firefly o strumenti simili, insieme alla denominazione e al posizionamento corretti dei file.
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '875'
ht-degree: 0%

---


# Generatore di icone del caso d’uso

Genera specifiche dettagliate sulle icone e prompt per la generazione di immagini AI per le icone dei casi d’uso nell’archivio blueprint.

## Quando utilizzare questa abilità

- Creazione di un nuovo caso d’uso che richiede un’icona
- Chiamata eseguita dall&#39;abilità generatore di casi d&#39;uso del settore per generare una specifica di icona
- L’utente chiede informazioni sulla creazione, l’aggiornamento o la sostituzione di un’icona del caso d’uso
- L’utente desidera generare un batch di icone per un nuovo settore verticale

## Passaggio 1: raccolta degli input

Raccogli le seguenti informazioni dall’utente o dall’abilità chiamante:

**Richiesto:**
- **Nome caso d&#39;uso**: nome leggibile del caso d&#39;uso (ad esempio &quot;Carrello abbandonato&quot;, &quot;Punteggio lead&quot;)
- **Settore verticale** — uno dei seguenti: automobilistico, b2b, servizi finanziari, sanitario, assicurativo, media-intrattenimento, retail, telecomunicazioni, viaggi-ospitalità
- **Breve descrizione** — 1-2 frasi che descrivono il caso d&#39;uso

**Facoltativo:**
- **Metafora visiva preferita o oggetto** - Se l&#39;utente ha un&#39;idea specifica su ciò che l&#39;icona dovrebbe rappresentare

Se manca un input necessario, chiedi all’utente prima di procedere.

## Passaggio 2: leggere la Guida allo stile

Leggere il file `references/icon-style-guide.md` (relativo alla directory di questa abilità) per caricare la guida di stile completa, che include:

- Specifiche tecniche
- Linee guida per lo stile visivo
- Esempi di metafore visive per settore
- Il modello di richiesta
- Inventario delle icone esistenti

Utilizza la guida di stile per garantire la coerenza con le icone esistenti.

## Passaggio 3: generare la specifica dell&#39;icona

Produrre tutte e tre le parti della specifica dell&#39;icona:

### A. Specifiche dei file

Deriva il nome file e il percorso dal nome del caso d’uso e dal settore:

- **Nome file:** `icon-{kebab-case-name}.png`
   - Converti il nome del caso d’uso in kebab (lettere minuscole, trattini per gli spazi)
   - Esempi: &quot;Carrello abbandonato&quot; diventa `icon-abandoned-cart.png`, &quot;Vendita incrociata&quot; diventa `icon-cross-sell-upsell.png`
- **Percorso:** `/help/blueprints/industry-use-cases/assets/use-case-icons/{industry}/`
- **Dimensioni:** 1024 x 1024 pixel
- **Formato:** PNG, RGB a 8 bit o RGBA
- **Dimensione file di destinazione:** 900KB - 1,4MB

### B. Prompt di generazione immagine

Crea un prompt dettagliato e pronto per la copia per gli strumenti di generazione di immagini AI. Il prompt deve:

1. **Descrivi una chiara metafora visiva**: scegli una singola metafora visiva forte che comunichi immediatamente il concetto di caso d&#39;uso. Se l’utente ha fornito una metafora preferita, utilizzala. In caso contrario, selezionane uno in base agli esempi della guida di stile e alla descrizione del caso d’uso.

2. **Specificare lo stile artistico**. Includere le seguenti direttive di stile:
   - Stile di illustrazione dell&#39;icona pulito e moderno
   - Design aziendale professionale
   - Forme grassetto e linee pulite
   - Finitura lucida e di rendering (non fotorealistica)
   - Coerente con un sistema di progettazione unificato

3. **Includi specifiche tecniche:**
   - Formato quadrato, 1024x1024 pixel
   - Singolo soggetto centrato
   - Sfondo sfumato o solido
   - Elevato contrasto tra soggetto e sfondo

4. **Applica leggibilità di piccole dimensioni:**
   - Nessun testo o lettering di alcun tipo
   - Nessun dettaglio preciso o pattern complessi
   - Nessuno sfondo complesso o scene con più elementi
   - Siluetta in grassetto con una nitidezza di lettura di 40 px
   - Forte riconoscimento delle forme anche senza colore

5. **Guida la tavolozza dei colori:**
   - Colori professionali, adatti alle aziende
   - Vibrante ma raffinato (non neon o eccessivamente saturo)
   - Elevato contrasto per l&#39;accessibilità
   - Coerente con altre icone nello stesso settore verticale

Struttura il prompt come un singolo paragrafo, pronto per essere incollato in qualsiasi strumento di generazione di immagini.

### C. Frammento di riferimento catalogo

Genera lo snippet HTML da utilizzare nella tabella del catalogo:

```
<img src="assets/use-case-icons/{industry}/icon-{name}.png" alt="{Alt Text}" width="40">
```

Dove `{Alt Text}` è il nome del caso d&#39;uso leggibile.

## Passaggio 4: Elencare le icone esistenti nello stesso settore

Consultate la sezione inventario delle icone esistenti nella guida di stile ed elencate tutte le icone attuali per lo stesso settore. In questo modo l’utente può:
- Assicurati della coerenza visiva durante la generazione della nuova icona
- Evita di duplicare un’icona già esistente
- Fare riferimento alle icone esistenti come esempi di stile

## Passaggio 5: presentare l’output

Formattare chiaramente l&#39;output con queste sezioni:

&#x200B;---

### Specifica icona: &lbrace;Use Case Name&rbrace;

**Settore:** {Industry}

**Dettagli file:**
- Nome file: `icon-{kebab-case-name}.png`
- Percorso: `/help/blueprints/industry-use-cases/assets/use-case-icons/{industry}/`
- Dimensioni: 1024 x 1024 pixel
- Formato: PNG (RGB/RGBA a 8 bit)

**Prompt generazione immagine:**

> {Il prompt completo e dettagliato, formattato come blockquote in modo che sia facile da copiare}

**HTML catalogo:**

```html
<img src="assets/use-case-icons/{industry}/icon-{name}.png" alt="{Use Case Name}" width="40">
```

**Icone esistenti in {Industry}:**
- {list of existing icon names}

**Passaggi successivi:**
1. Copia il prompt di generazione dell&#39;immagine qui sopra.
2. Incollalo nello strumento di generazione delle immagini preferito (Adobe Firefly, Midjourney, DALL-E o simile).
3. Genera l’immagine e seleziona il risultato migliore.
4. Se necessario, ridimensiona/esporta esattamente 1024x1024 pixel.
5. Salva come `{filename}` nel percorso indicato sopra.
6. Verifica che l’icona sia chiara e riconoscibile, con una dimensione di visualizzazione di 40 px.
7. Utilizza lo snippet HTML per il catalogo quando aggiungi questo caso d’uso alla tabella del catalogo.

&#x200B;---

## Linee guida

- **Non generare mai l&#39;immagine effettiva**. Questa abilità genera solo le specifiche e la richiesta. L’utente deve utilizzare uno strumento esterno per la generazione delle immagini.
- **Un&#39;icona per ogni caso d&#39;uso** — Ogni caso d&#39;uso ottiene esattamente un&#39;icona.
- **Verifica la presenza di duplicati**. Se nell&#39;inventario esiste già un&#39;icona con lo stesso nome o con un nome molto simile, avvisare l&#39;utente.
- **Assegna priorità alla leggibilità**: in caso di dubbi tra una metafora dettagliata e una semplice, scegli sempre l&#39;opzione più semplice che legge bene a 40 px.
- **Specificare nei prompt**. I prompt vaghi producono risultati incoerenti. Includi dettagli visivi concreti (ad esempio, &quot;un carrello con due scatole colorate all’interno&quot; anziché &quot;un concetto di shopping&quot;).
- **Se possibile, evitare i cliché**. Cercare metafore visive nuove ma immediatamente riconoscibili. Una lampadina per ogni caso d’uso &quot;intelligente&quot; diventa ripetitiva.
