---
name: industry-use-case-builder
description: 'Guida alla creazione di nuovi casi d’uso di settore per l’archivio dei blueprint di Adobe Experience Platform. Utilizza questa abilità quando aggiungi un nuovo caso d’uso a un settore verticale (retail, automotive, sanità, servizi finanziari, assicurazioni, media e intrattenimento, telecomunicazioni, viaggi e ospitalità, B2B), quando l’utente desidera aggiungere scenari commerciali alle pagine del settore o quando aggiorna il catalogo dei casi d’uso. Gestisce l’intero flusso di lavoro: raccoglie i dettagli dei casi d’uso, valuta il livello di maturità, genera contenuti, aggiorna la pagina di panoramica del settore e il catalogo dei casi d’uso e richiama l’abilità del generatore di icone per la creazione di icone.'
source-git-commit: ed8928687806b619e95d8d320478d27c13722a80
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 1%

---


# Generatore di casi d’uso di settore

Questa abilità guida la creazione di nuovi casi d’uso del settore per l’archivio dei blueprint di Adobe Experience Platform. Seguire ciascuna fase in sequenza. Leggete i file di riferimento prima di iniziare:

- `references/use-case-template.md` — modello esatto per le sezioni dei casi d&#39;uso
- `references/catalog-row-template.md` — formato esatto per le righe della tabella del catalogo
- `references/maturity-criteria.md` - valutazione dettagliata della scadenza

## Fase 1: Raccolta delle informazioni

Intervista l’utente per raccogliere tutti i dettagli richiesti prima di generare qualsiasi contenuto.

### Campi obbligatori

1. **Settore verticale**: deve essere uno dei seguenti:
   - settore automobilistico
   - b2b
   - servizi finanziari
   - assistenza sanitaria
   - assicurazione
   - media-entertainment
   - retail
   - telecomunicazioni
   - viaggi-ospitalità

2. **Nome caso d&#39;uso**: titolo descrittivo e chiaro (ad esempio, &quot;Abandoned Cart Email Recovery&quot;, &quot;Medication Adherence Campaigns&quot;).

3. **Descrizione** — 1-2 frasi che descrivono lo scenario aziendale e il motivo della sua importanza.

4. **Impatto aziendale** — Risultati quantificati con metriche specifiche (ad esempio, &quot;aumento del 20-30% dei tassi di click-through&quot;, &quot;miglioramento del 15-25% dei tassi di ricarica&quot;).

5. **Caso d&#39;uso**: deve essere mappato esattamente a uno dei seguenti modelli esistenti:
   - Audience Activation alle destinazioni
   - Audience Collaboration con corrispondenza segmento
   - Inoltro degli eventi
   - Audience Activation B2B
   - Personalization Web visitatore anonimo
   - Personalization Web/app visitatore noto
   - Offer Decisioning
   - Consigli comportamentali
   - Attivazione messaggi in uscita in batch
   - Messaggi attivati da eventi
   - Percorso orchestrato con più passaggi
   - Percorso cross-channel con decisioning
   - Acquisto di soluzioni di marketing e gestione dei Percorsi basate su gruppi
   - Customer Analytics e Insight Generation
   - Analisi B2B
   - Esperienza conversazionale Brand Concierge

6. **Considerazioni tecniche**: 4-8 punti elenco relativi a requisiti di dati, integrazioni, requisiti normativi/di conformità, considerazioni sulle prestazioni e note architetturali.

Richiedi eventuali campi mancanti prima di procedere. Non presumere o fabbricare dettagli.

## Fase 2: Valutazione della maturità

Leggi `references/maturity-criteria.md` per la rubrica completa. Assegna uno dei tre livelli di maturità:

- **Fondamentale** `[!BADGE Foundational]{type=Neutral}`: pattern attivati da un singolo passaggio o da un evento (messaggistica attivata da eventi, batch in uscita), requisiti di dati semplici, IA/ML minima, integrazioni standard.
- **Emergente** `[!BADGE Emerging]{type=Informative}`: percorsi con più passaggi, dati comportamentali, modelli di consigli, personalizzazione con visitatori noti, complessità di integrazione moderata.
- **Avanzate** `[!BADGE Advanced]{type=Caution}`: decisioning cross-channel, previsione basata su IA, offer decisioning, orchestrazione complessa, integrazioni di più sistemi.

### Flusso di lavoro valutazione

1. Identifica il pattern del caso d’uso associato al caso d’uso.
2. Controlla i &quot;Pattern tipici&quot; nell’elenco dei criteri di maturità per una corrispondenza rapida.
3. Se il modello non indica chiaramente la maturità, valuta la complessità dei dati, i requisiti di IA/ML e l’ambito di integrazione.
4. Presentare la valutazione all&#39;utente con una motivazione: &quot;In base alla mappatura pattern ({pattern}) e {key factors}, classificherei come {level} perché {reasoning}.&quot;
5. Attendi che l’utente confermi o esegua l’override prima di procedere alla generazione del contenuto.

## Fase 3: Generazione dei contenuti

Genera o aggiorna il contenuto in due file.

### A. File di panoramica del settore

**Percorso file:** `/help/blueprints/industry-use-cases/{industry}/{industry}-overview.md`

Leggi prima il file esistente per comprendere la struttura e il contenuto correnti. Quindi aggiungere una nuova sezione seguendo il modello esatto da `references/use-case-template.md`:

```markdown
## {Use Case Title}

{1-2 sentence description of the business scenario and why it matters}

### Business impact

{Quantified business outcomes, e.g., "Retailers typically see a 20-30% increase in click-through rates..."}

### How to implement

Use the [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) pattern. {1-2 sentence explanation of why this pattern applies}

### Technical considerations

- {4-8 bullet points covering data integration, regulatory, performance, or architectural considerations}
```

Posiziona la nuova sezione dopo le sezioni esistenti del caso d’uso, mantenendo una formattazione coerente.

### B. Catalogo dei casi d’uso

**Percorso file:** `/help/blueprints/industry-use-cases/use-case-catalog.md`

Leggi prima il file di catalogo esistente. Aggiungi una nuova riga alla scheda corretta del settore. Il catalogo utilizza una struttura a schede con `>[!TAB {Industry}]` marcatori. Ogni scheda contiene una tabella con le colonne seguenti:

| Colonna | Contenuto |
| --- | --- |
| Icona | `<img src="assets/use-case-icons/{industry}/icon-{kebab-name}.png" alt="{Alt Text}" width="40">` (lasciare vuoto se non è ancora presente alcuna icona) |
| Caso d’uso | `[{Use Case Title}]({industry}/{industry}-overview.md#{anchor})` dove ancoraggio è l&#39;intestazione in kebab-case |
| Descrizione | Riepilogo di una frase |
| Maturità | Sintassi del badge per il livello assegnato |
| Pattern | `[{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md)` |

**Regola di posizionamento:** All&#39;interno di ogni scheda del settore, le righe sono raggruppate per scadenza in questo ordine: Fondamentale prima, Emergente poi Avanzato. Posizionare la nuova riga alla fine del gruppo di scadenza corretto.

I percorsi dei file di pattern sono:
- `audience-building-activation/audience-activation-to-destinations.md`
- `audience-building-activation/audience-collaboration-segment-match.md`
- `audience-building-activation/event-forwarding.md`
- `audience-building-activation/b2b-audience-activation.md`
- `personalization/anonymous-visitor-web-personalization.md`
- `personalization/known-visitor-web-app-personalization.md`
- `personalization/offer-decisioning.md`
- `personalization/behavioral-recommendation.md`
- `campaign-management-orchestration/batch-outbound-message-activation.md`
- `campaign-management-orchestration/event-triggered-messaging.md`
- `campaign-management-orchestration/multi-step-orchestrated-journey.md`
- `campaign-management-orchestration/cross-channel-journey-with-decisioning.md`
- `campaign-management-orchestration/buying-group-based-marketing.md`
- `analysis/customer-analytics-insight-generation.md`
- `analysis/b2b-analytics.md`
- `conversational-experience/brand-concierge-conversational-experience.md`

## Fase 4: generazione di icone

Dopo la creazione del contenuto, richiamare l&#39;abilità `use-case-icon-generator` per generare una specifica di icona per il nuovo caso d&#39;uso. Fornisci l’abilità con:
- Nome del caso d’uso
- Settore verticale
- Breve descrizione del caso d’uso

Una volta che l’utente dispone del file di icona generato, aggiorna la riga del catalogo per includere il riferimento all’icona:

```
<img src="assets/use-case-icons/{industry}/icon-{kebab-name}.png" alt="{Alt Text}" width="40">
```

## Fase 5: Convalida

Prima di terminare, verificare quanto segue:

1. **Conformità modello**: la sezione panoramica del settore segue esattamente il modello (## intestazione, descrizione, ### Impatto aziendale, ### Come implementare, ### Considerazioni tecniche).
2. **Posizione catalogo** - La riga del catalogo si trova nella scheda del settore corretta e nel gruppo di maturità corretto (Fondamentale, Emergente, quindi Avanzato).
3. **Validità collegamento pattern**: il collegamento pattern nella panoramica e nel catalogo utilizza un percorso di file pattern valido dall&#39;elenco precedente.
4. **Coerenza ancoraggio**: l&#39;ancoraggio nel collegamento al catalogo (ad esempio, `#abandoned-cart-email-recovery`) corrisponde all&#39;intestazione `##` nel file di panoramica convertito in maiuscolo/minuscolo.
5. **Convenzioni percorso icona**. Il percorso icona segue `assets/use-case-icons/{industry}/icon-{kebab-name}.png`.

Segnala eventuali problemi rilevati durante la convalida e risolvili prima del completamento.
