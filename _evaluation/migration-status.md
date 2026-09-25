---
source-git-commit: 2ed15399073fce5ebd1c2ba07b1cf70ec706452c
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 2%
---
# Stato di migrazione â€&quot; Blueprint per modelli di casi d’uso

Questo documento acquisisce lo stato dell’impegno di riorganizzazione blueprint in modo che possa essere ripreso correttamente tra le sessioni.

**Ultimo aggiornamento:** 24/09/2026

## Dove siamo adesso

La sezione B2B non viene più sospesa. L’ambito dell’architettura pubblicata è ora limitato alle pagine di attivazione di tipi di pubblico/profili e account, con pagine ritirate reindirizzate alla panoramica della categoria.

**Stato corrente:** La pulizia dell&#39;architettura B2B è stata completata. Le pagine di attivazione di pubblico/profilo e account rimangono nella categoria dei diagrammi architettura; le altre pagine dell’architettura B2B sono state ritirate e reindirizzate alla panoramica della categoria.

## Metodo di lavoro

> L’approccio di lavoro riportato di seguito è storico; la sezione B2B è stata da allora disposta come registrato in precedenza.

L&#39;attuale modello di lavoro, concordato in questa sessione, è:

1. **Mantieni i blueprint attivi** â€&quot; senza elementi obsoleti. Ogni blueprint rimane nella posizione giusta come pagina incentrata sull’architettura.
2. **Aggiungi un suggerimento cross-link** a ogni blueprint con un caso d&#39;uso correlato/sovrapposto, immediatamente dopo H1:

   ```
   >[!TIP]
   >This blueprint is also available as a [use case pattern](<absolute path>) under <Category>.
   ```

3. **Esegui migrazione diagrammi** â€&quot; se un blueprint ha un diagramma di architettura mancante del relativo modello, aggiungi una sezione `## Architecture` al modello che fa riferimento allo stesso SVG tramite il percorso assoluto. La risorsa rimane nella posizione originale (nessuna copia del file).
4. **Taglia i passaggi di implementazione** dalla blueprint se coperti dal modello. Le sezioni da rimuovere in genere includono: `## Implementation steps`, `## Implementation patterns`, `## Implementation considerations`, a volte `## Prerequisites`. Utilizza il giudizio per blueprint.
5. **Sfoglia una per una** â€&quot; propone modifiche per blueprint, ottieni l&#39;approvazione dell&#39;utente, quindi applica.

### Regole universali

- Il testo del suggerimento per il collegamento incrociato è coerente: `>This blueprint is also available as a [use case pattern](...) under <Category>.`
- I nuovi file (modelli di casi d&#39;uso creati durante la migrazione) **non includono`exl-id`** â€&quot; assegnati dalla pubblicazione Adobe.
- I riferimenti alle immagini nei file appena creati utilizzano percorsi assoluti (`/help/blueprints/...`), non relativi.
- I valori `exl-id` esistenti nelle pagine esistenti vengono mantenuti.
- I reindirizzamenti in `redirects.csv` seguono il formato `source,dest` con `/en/docs/...` percorsi (nessun `.html`).

## Fasi Aâ€&quot;E (lavoro strutturale iniziale) â€&quot; COMPLETO

| Fase | Risultato |
| --- | --- |
| A | Creazione della categoria pattern del caso d&#39;uso `B2B Activation & Marketing` completata. Sono stati riposizionati 3 modelli esistenti (`b2b-audience-activation` â†’ `b2b/account-audience-activation`, `buying-group-based-marketing` â†’ `b2b/buying-group-marketing`, `b2b-analytics` â†’ `b2b/account-analytics`). Sono stati aggiunti 3 reindirizzamenti. |
| B | Copiato 4 blueprint B2B in `use-case-patterns/b2b/` (`marketo-data-journeys`, `paid-media-orchestration`, `campaign-intake-and-creation`, `campaign-review-and-approval`). |
| C | Copiato 4 blueprint non B2B (`real-time-profile-lookup`, `data-science-profile-enrichment`, `edge-profile-access`, `campaign-v8-orchestration`). |
| D | Copiato 2 blueprint suddivisi (`audience-sharing-with-target`, `third-party-messaging`). |
| E | È stato aggiunto un SUGGERIMENTO per il collegamento incrociato a 9 blueprint classificati duplicati. |

Totale casi d&#39;uso dopo Aâ€&quot;E: **26 modelli** in 6 categorie.

## Procedura dettagliata sezione per sezione (in corso)

La procedura dettagliata della sezione applica l’approccio cross-link/migrazione diagramma/impl-trim a ogni blueprint singolarmente sotto la revisione dell’utente.

### âoe... Attivazione del pubblico e del profilo â€&quot; 8/8 completo

| # | Blueprint | Azione intrapresa |
| --- | --- | --- |
| 1 | `audience-manager.md` | Suggerimento cross-link + diagramma migrato a pattern (`anonymous-visitor-web-personalization`) + passaggi impl RTCDP rimossi |
| 2 | `enterprise-destinations.md` | Suggerimento cross-link + diagramma migrato al modello (`audience-activation-to-destinations`) |
| 3 | `advertising-activation.md` | Incrementi impl rimossi (99 â†’ 35 linee) |
| 4 | `customer-activity.md` | Incrementi impl rimossi (51 â†’ 40 linee) |
| 5 | `data-science.md` | Considerazioni Impl eliminate (46 â†’ 40 linee) |
| 6 | `real-time-lookup.md` | Prerequisiti + modelli/passaggi/considerazioni impl rimossi (156 â†’ 73 linee) |
| 7 | `segment-match.md` | **Nessuna modifica** (l&#39;utente ha scelto di uscire così com&#39;è) |
| 8 | `rtcdp-target.md` | Motivi impl + considerazioni rimosse (99 â†’ 74 linee) |

### ðBEYŸ Attivazione e marketing B2B â€&quot; 1/10 in corso

| # | Blueprint | Stato |
| --- | --- | --- |
| 1 | `b2b/overview.md` | Completato - Panoramica categoria B2B aggiornata |
| 2 | `b2b/b2bactivation.md` | Ritirato: sostituito dalla pagina audience/profilo dei diagrammi dell’architettura |
| 3 | `b2b/b2b-account-activation.md` | Mantenuto: migrazione alla categoria B2B di diagrammi architettura |
| 4 | `b2b/b2b-buying-group-journeys.md` | Ritirato |
| 5 | `b2b/b2b-journeys-with-marketo.md` | Ritirato |
| 6 | `b2b/ajo-b2b-paid-media-controller.md` | Ritirato |
| 7 | `b2b/marketo-engage-and-workfront-integration-blueprint/overview.md` | Ritirato |
| 8 | `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | Ritirato |
| 9 | `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | Ritirato |
| 10 | `b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md` | Ritirato |

### âšª Customer Journey Analytics â€&quot; 0/5 non ancora iniziato

File: `overview.md`, `b2b-cja.md` (fase E duplicata, collegamento incrociato aggiunto), `cja-rtcdp.md` (gruppo 2 â€&quot; consiglia collegamento incrociato a `customer-analytics-insight-generation`), `cja-ajo.md` (gruppo 2 â€&quot; uguale), `analysis.md` (gruppo 3, eventualmente trasferimento in experience-platform/).

### âšª Pulizia Percorsi di clienti â€&quot; completata; in attesa di migrazione delle pagine mantenute

File: `overview.md`; `journey-optimizer/` (4 file: panoramica, percorsi [Fase E], campagne [Fase E], messaggistica di terze parti [Fase D]); `campaign-v8/` (3 file: panoramica [Fase C], rtcdp-and-v8, ajo-and-v8). `decision-management/` e `campaign-v7/` sono completamente ritirati; i loro dati storici rimangono nel controllo di audit e i loro URL vengono reindirizzati alle pagine di panoramica approvate.

### âšª Experience Platform â€&quot; 0/6 non ancora iniziato

File: `experience-cloud.md`, `platform-applications.md`, `platform-data-flow.md`, `guardrails.md`, `deployment/websdk.md`, `deployment/appsdk.md`. Tutto valutato come solo diagramma con 0 segnali pattern nel controllo di audit. **Probabilmente tutti &quot;nessun cambiamento&quot;** â€&quot; sono architetture fondamentali con cui nessun caso d&#39;uso si sovrappone.

Le decisioni relative alla gestione delle decisioni e al ritiro di Campaign v7 sono complete. Le relative domande aperte
sono solo storiche e non devono bloccare il lavoro di migrazione rimanente.

## File di riferimento

| File | Finalità |
| --- | --- |
| [blueprint-audit.md](blueprint-audit.md) | Tabella di controllo per blueprint (43 righe) con consigli |
| [rubric.md](rubric.md) | Valutazione utilizzata per classificare i progetti |
| [migration-redirects.csv](migration-redirects.csv) | Reindirizzamenti in staging dalla migrazione |
| [reindirizzamenti.csv](../redirects.csv) | File di reindirizzamenti canonici (3 righe aggiunte nella fase A) |

## Domande aperte ancora non risolte (da audit)

&#x200B;2. **`journey-optimizer-journeys.md`** â€&quot; contrassegnato come duplicato incerto di `event-triggered-messaging`; verifica l&#39;ambito prima del ritaglio.
&#x200B;3. Il contenuto di **`customer-journey-analytics/analysis.md`** â€&quot; riguarda Experience Platform Query Service, non CJA; puoi provare a trasferirti in `experience-platform/`.
&#x200B;4. Pagina di soli collegamenti **`customer-success-stories.md`** â€&quot;; conferma la classificazione di navigazione.
&#x200B;5. Domanda storica dell&#39;ancoraggio TOC sostituita dalla disposizione completa dell&#39;architettura B2B.

## Come riprendere

Apri una nuova sessione Claude Code in questo archivio e dì:

> Riprendiamo la migrazione blueprint. Leggi `_evaluation/migration-status.md` per capire da dove abbiamo interrotto.

Pulizia dell’architettura B2B completata. Continua con la categoria di architettura pianificata successiva dopo la convalida.
