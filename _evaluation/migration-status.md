---
source-git-commit: 7511cc0e5c099d5d3ee1275a374cd9ffdc972335
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 2%

---
# Stato della migrazione: blueprint per modelli di casi d’uso

Questo documento acquisisce lo stato dell’impegno di riorganizzazione blueprint in modo che possa essere ripreso correttamente tra le sessioni.

**Ultimo aggiornamento:** 29/04/2026

## Dove siamo adesso

**Attualmente in pausa il:** `b2b/overview.md` (sezione B2B blueprint #1 di 10) — in attesa di decisione se uscire così com’è, aggiungere un riferimento incrociato alla nuova sezione Modelli di attivazione e marketing B2B o aggiornare la tabella per elencare tutti i blueprint + aggiungere un riferimento incrociato.

**Per riprendere:** rispondi con **A** (lascia invariato, consigliato), **B** (aggiungi rimando) o **C** (aggiorna tabella + aggiungi rimando). Quindi continuare con la #2 blueprint (`b2b/b2bactivation.md`).

## Metodo di lavoro

L&#39;attuale modello di lavoro, concordato in questa sessione, è:

1. **Mantieni i blueprint attivi**. Nessuna rimozione. Ogni blueprint rimane nella posizione giusta come pagina incentrata sull’architettura.
2. **Aggiungi un suggerimento cross-link** a ogni blueprint con un caso d&#39;uso correlato/sovrapposto, immediatamente dopo H1:

   ```
   >[!TIP]
   >This blueprint is also available as a [use case pattern](<absolute path>) under <Category>.
   ```

3. **Esegui migrazione diagrammi**: se un blueprint dispone di un diagramma di architettura privo del modello correlato, aggiungi una sezione `## Architecture` al modello che fa riferimento allo stesso SVG tramite il percorso assoluto. La risorsa rimane nella posizione originale (nessuna copia del file).
4. **Taglia i passaggi di implementazione** dalla blueprint se coperti dal modello. Le sezioni da rimuovere in genere includono: `## Implementation steps`, `## Implementation patterns`, `## Implementation considerations`, a volte `## Prerequisites`. Utilizza il giudizio per blueprint.
5. **Scorri uno per uno**: propone le modifiche per blueprint, ottieni l&#39;approvazione dell&#39;utente, quindi applica.

### Regole universali

- Il testo del suggerimento per il collegamento incrociato è coerente: `>This blueprint is also available as a [use case pattern](...) under <Category>.`
- I nuovi file (modelli di casi d&#39;uso creati durante la migrazione) **non includono`exl-id`**. Tali file vengono assegnati dalla pubblicazione Adobe.
- I riferimenti alle immagini nei file appena creati utilizzano percorsi assoluti (`/help/blueprints/...`), non relativi.
- I valori `exl-id` esistenti nelle pagine esistenti vengono mantenuti.
- I reindirizzamenti in `redirects.csv` seguono il formato `source,dest` con `/en/docs/...` percorsi (nessun `.html`).

## Fasi A-E (lavori strutturali iniziali) — COMPLETO

| Fase | Risultato |
| --- | --- |
| A | Creazione della categoria pattern del caso d&#39;uso `B2B Activation & Marketing` completata. Sono stati riposizionati 3 modelli esistenti (`b2b-audience-activation` → `b2b/account-audience-activation`, `buying-group-based-marketing` → `b2b/buying-group-marketing`, `b2b-analytics` → `b2b/account-analytics`). Sono stati aggiunti 3 reindirizzamenti. |
| B | Copiato 4 blueprint B2B in `use-case-patterns/b2b/` (`marketo-data-journeys`, `paid-media-orchestration`, `campaign-intake-and-creation`, `campaign-review-and-approval`). |
| C | Copiato 4 blueprint non B2B (`real-time-profile-lookup`, `data-science-profile-enrichment`, `edge-profile-access`, `campaign-v8-orchestration`). |
| D | Copiato 2 blueprint suddivisi (`audience-sharing-with-target`, `third-party-messaging`). |
| E | È stato aggiunto un SUGGERIMENTO per il collegamento incrociato a 9 blueprint classificati duplicati. |

Totale casi d&#39;uso dopo A-E: **26 pattern** in 6 categorie.

## Procedura dettagliata sezione per sezione (in corso)

La procedura dettagliata della sezione applica l’approccio cross-link/migrazione diagramma/impl-trim a ogni blueprint singolarmente sotto la revisione dell’utente.

### Attivazione di ✅ pubblico e profilo - 8/8 completata

| # | Blueprint | Azione intrapresa |
| --- | --- | --- |
| 1 | `audience-manager.md` | Suggerimento cross-link + diagramma migrato a pattern (`anonymous-visitor-web-personalization`) + passaggi impl RTCDP rimossi |
| 2 | `enterprise-destinations.md` | Suggerimento cross-link + diagramma migrato al modello (`audience-activation-to-destinations`) |
| 3 | `advertising-activation.md` | Incrementi impl rimossi (99 → 35 linee) |
| 4 | `customer-activity.md` | Incrementi impl rimossi (51 → 40 righe) |
| 5 | `data-science.md` | Considerazioni Impl rimosse (46 → 40 righe) |
| 6 | `real-time-lookup.md` | Prerequisiti + modelli/passaggi/considerazioni impl rimossi (156 → 73 righe) |
| 7 | `segment-match.md` | **Nessuna modifica** (l&#39;utente ha scelto di uscire così com&#39;è) |
| 8 | `rtcdp-target.md` | Motivi impl + considerazioni rimosse (99 → 74 linee) |

### 🟡 attivazione e marketing B2B — 1/10 in corso

| # | Blueprint | Stato |
| --- | --- | --- |
| 1 | `b2b/overview.md` | **IN PAUSA** — in attesa della decisione A/B/C (vedi sopra &quot;Dove siamo ora&quot;) |
| 2 | `b2b/b2bactivation.md` | In sospeso — Fase E duplicata; collegamento incrociato aggiunto; è necessaria una revisione per il diagramma + trim implicito |
| 3 | `b2b/b2b-account-activation.md` | In sospeso — classificato in base al diagramma; è necessario un collegamento incrociato a `b2b/account-audience-activation.md` + prendere in considerazione la migrazione del diagramma |
| 4 | `b2b/b2b-buying-group-journeys.md` | In sospeso — Fase E duplicata; collegamento incrociato aggiunto; è necessaria una revisione |
| 5 | `b2b/b2b-journeys-with-marketo.md` | In sospeso — copia di fase B; il pattern è una copia; richiede il trim a fasi impl |
| 6 | `b2b/ajo-b2b-paid-media-controller.md` | In sospeso — copia di fase B; richiede il ritaglio a fasi intermedie |
| 7 | `b2b/marketo-engage-and-workfront-integration-blueprint/overview.md` | In sospeso — Pagina di destinazione sezione |
| 8 | `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | In sospeso — copia di fase B; richiede il ritaglio a fasi intermedie |
| 9 | `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | In sospeso — copia di fase B; richiede il ritaglio a fasi intermedie |
| 10 | `b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md` | In sospeso — pagina Solo collegamenti (il controllo di audit è contrassegnato come Navigazione) |

### ⚪ Customer Journey Analytics — 0/5 non ancora avviato

File: `overview.md`, `b2b-cja.md` (fase E duplicata, collegamento incrociato aggiunto), `cja-rtcdp.md` (gruppo 2 — collegamento incrociato consigliato a `customer-analytics-insight-generation`), `cja-ajo.md` (gruppo 2 — stesso), `analysis.md` (gruppo 3, possibilmente trasferimento a experience-platform/).

### ⚪ Percorsi di clienti — 0/14 non ancora avviato

File: `overview.md`; `journey-optimizer/` (4 file: panoramica, percorsi [Fase E], campagne [Fase E], messaggistica di terze parti [Fase D]); `decision-management/` (3 file: panoramica, edge [Fase E], hub [Fase E]); `campaign-v8/` (3 file: panoramica [Fase C], rtcdp-and-v8, ajo-and-v8); `campaign-v7/` (3 obsoleto) file).

### ⚪ Experience Platform — 0/6 non ancora avviato

File: `experience-cloud.md`, `platform-applications.md`, `platform-data-flow.md`, `guardrails.md`, `deployment/websdk.md`, `deployment/appsdk.md`. Tutto valutato come solo diagramma con 0 segnali pattern nel controllo di audit. **Probabilmente tutti &quot;nessun cambiamento&quot;**. Si tratta di un&#39;architettura fondamentale con cui nessun caso d&#39;uso si sovrappone.

## File di riferimento

| File | Finalità |
| --- | --- |
| [blueprint-audit.md](blueprint-audit.md) | Tabella di controllo per blueprint (43 righe) con consigli |
| [rubric.md](rubric.md) | Valutazione utilizzata per classificare i progetti |
| [migration-redirects.csv](migration-redirects.csv) | Reindirizzamenti in staging dalla migrazione |
| [reindirizzamenti.csv](../redirects.csv) | File di reindirizzamenti canonici (3 righe aggiunte nella fase A) |

## Domande aperte ancora non risolte (da audit)

1. **Edge + hub di gestione delle decisioni** — entrambi attualmente cross-link a `offer-decisioning`. Prendere in considerazione il consolidamento in un unico diagramma delle opzioni di distribuzione?
2. **`journey-optimizer-journeys.md`** — contrassegnato come duplicato incerto di `event-triggered-messaging`; verificare l&#39;ambito prima del ritaglio.
3. **`customer-journey-analytics/analysis.md`** — il contenuto riguarda Experience Platform Query Service, non CJA. Provare a riposizionare in `experience-platform/`.
4. **Campaign v7 (3 file obsoleti)** — eseguire la migrazione, uscire o rimuovere dal sommario?
5. **`customer-success-stories.md`** — pagina solo collegamenti; confermare la classificazione di navigazione.
6. **L&#39;ancoraggio TOC** per la nuova sezione B2B è `{#b2b-patterns}`. Confermare prima di qualsiasi creazione di reindirizzamento di produzione.

## Come riprendere

Apri una nuova sessione Claude Code in questo archivio e dì:

> Riprendiamo la migrazione blueprint. Leggi `_evaluation/migration-status.md` per capire da dove abbiamo interrotto.

Il prossimo passo concreto: rispondere alla decisione `b2b/overview.md` (A/B/C). Quindi continuare con la #2 blueprint (`b2b/b2bactivation.md`) e procedere attraverso la sezione B2B, quindi Customer Journey Analytics, Percorsi di clienti e Experience Platform.
