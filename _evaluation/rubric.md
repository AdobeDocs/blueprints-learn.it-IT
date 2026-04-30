---
source-git-commit: 7511cc0e5c099d5d3ee1275a374cd9ffdc972335
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---
# Valutazione blueprint

Questa rubrica viene applicata a ogni documento nella sezione &quot;Diagrammi architettura e blueprint&quot;
di [TOC.md](../help/blueprints/TOC.md) (righe 76-133) per consigliare se ogni blueprint deve diventare un
**Caso d&#39;uso**, **Diagramma architettura**, entrambi (**Dividi**), o essere contrassegnati come
**Duplicato** di un modello esistente.

L&#39;output dell&#39;applicazione di questa rubrica è [blueprint-audit.md](blueprint-audit.md).

## Definizioni

- **Caso d&#39;uso**: documento che descrive un obiettivo tecnico o aziendale specifico e
delineare possibili approcci e considerazioni in materia di attuazione per raggiungere tale obiettivo.
Forma canonica: `.claude/skills/use-case-pattern-builder/references/pattern-template.md`.
- **Diagramma architettura**: un diagramma visivo che rappresenta la funzionalità di un sistema, ovvero
e flussi di dati. Minima narrazione; il diagramma è l&#39;artefatto.
Esempio canonico: [platform-data-flow.md](../help/blueprints/experience-platform/platform-data-flow.md).

## Punteggio

Ogni blueprint viene letto end-to-end e valutato rispetto a otto segnali binari. Ogni segnale contribuisce
+1 per il punteggio pattern o il punteggio diagramma.

### Segnali della serie (ciascuno = +1 serie)

1. **Framing obiettivi aziendali**: ricavi frame, conservazione, acquisizione, generazione di lead, costo
riduzione, customer experience o risultati di business simili.
2. **KPI o metriche di successo**: nomi espliciti di metriche, tassi di conversione, percentuali di corrispondenza, ROI o
misure di esito simili.
3. **Più opzioni di implementazione o livelli di maturità**: presenta l&#39;opzione A / l&#39;opzione B, opzioni di base e
alternative avanzate o paragonabili scelte dal lettore.
4. **Prerequisiti o elenco di controllo per la preparazione** — elenca gli elementi che devono essere implementati prima dell&#39;implementazione.
5. **Passaggi per l&#39;implementazione narrativa > ~30 righe** — istruzioni sostanziali per l&#39;implementazione, non
solo una breve panoramica.

### Segnali del diagramma (ciascuno = +1 diagramma)

&#x200B;6. **Architettura/immagine del flusso di dati presente** - `.svg`, `.png` o `.jpg` con topologia di sistema,
flusso di dati o frecce di integrazione.
&#x200B;7. **Topologia di integrazione tra sistemi, forma di distribuzione o guardrail**: descrive come
i componenti si connettono, dove risiedono i dati, i modelli di distribuzione (edge vs. hub) o i limiti di capacità.
&#x200B;8. **Il pubblico è un architetto della soluzione**. Il frame utilizza distribuzione, SDK, Edge, hub o simili
una terminologia orientata agli architetti piuttosto che orientata agli addetti al marketing (campagne, percorsi,
pubblico).

## Logica consigli

Applica prima le regole di sostituzione. Se non viene attivata alcuna sostituzione, deriva il consiglio dai punteggi.

### Sostituisci regole (priorità più alta)

1. **File denominato`overview.md`** → consiglio = `Navigation`. Escluso dalla migrazione; il
è una pagina di destinazione in stile sommario che verrà rivista dopo l’impostazione dei file secondari.
2. **Esiste già un pattern equivalente in`help/blueprints/use-case-patterns/`** →
consiglio = `Duplicate`. L’azione di migrazione consiste nel semplificare il blueprint per ottenere un
diagramma dell’architettura e aggiungere un collegamento incrociato &quot;See use case pattern&quot; al modello esistente.
Registra il percorso del pattern esistente nella colonna `duplicate_of`.
3. **Il file si trova in `experience-platform/` e non ha alcun segnale di obiettivo di business (#1)** → impostazione predefinita
   `Diagram` indipendentemente dagli altri punteggi. Questa cartella è il livello di panoramica dell’architettura.

### Consigli basati su punteggio (quando non viene attivata alcuna sostituzione)

| Punteggio pattern | Punteggio diagramma | Consiglio | Ragionamento |
| --- | --- | --- | --- |
| ≥ 3 | ≤ 1 | `Pattern` | Segnali di serie forti, segnali di diagramma debole → migrare a una serie. |
| ≤ 1 | ≥ 2 | `Diagram` | Segnali di pattern deboli, focus dominante visivo/topologico → mantenere come diagramma. |
| ≥ 3 | ≥ 2 | `Split` | Sia il contenuto ricco del pattern che un diagramma significativo → estrarre il pattern, riduci l’originale a diagramma, cross-link. |
| 2 | 2 | `Split` | Legare a forza moderata → dividersi. |
| 2 | ≤ 1 | `Pattern` | Schema inclinato, nessun valore di diagramma significativo. |
| ≤ 1 | ≤ 1 | `Diagram` | Complessivamente sottile: è probabile che esista una pagina di architettura minima. |

## Come applicare la rubrica

Per ogni file markdown blueprint nell’ambito:

1. Leggi il file completo end-to-end.
2. Contrassegna ciascuno degli otto segnali presenti/assenti.
3. Applica le regole di sostituzione in ordine. Se uno si attiva, questo è il consiglio.
4. In caso contrario, calcola il punteggio pattern e il punteggio diagramma e cerca il consiglio.
5. Per `Pattern` e `Split` consigli, proporre:
   - `proposed_pattern_category` — uno dei seguenti:
     `audience-building-activation`, `personalization`, `campaign-management-orchestration`,
     `analysis`, `conversational-experience` o una nuova categoria con etichetta `(new) <name>`.
   - `proposed_pattern_title`: titolo breve e orientato alle azioni, secondo il modello esistente
stile di denominazione.
6. Per `Diagram` e `Split` consigli, proporre:
   - `proposed_diagram_title` — in genere il titolo esistente troncato del frame aziendale.
7. Acquisisci eventuali duplicati trovati confrontando l’ambito della blueprint con il catalogo di modelli esistente
tra `duplicate_of`.
8. Registra le domande aperte, i contenuti tecnici univoci da conservare o i rischi di migrazione in `notes`.

## Catalogo pattern dei casi d’uso esistente (per il rilevamento di duplicati)

| Categoria | Pattern |
| --- | --- |
| audience-building-activation | audience-activation-to-destinations, audience-collaborative-segment-match, b2b-audience-activation, event-forwarding |
| personalizzazione | anonymous-visitor-web-personalization, known-visitor-web-app-personalization, offer-decisioning, behavioral-recommendations |
| campaign-management-orchestration | attivazione di messaggi in uscita batch, messaggistica attivata da eventi, percorso orchestrato con più passaggi, percorso con decisioni e marketing basato su gruppi di acquisto |
| analisi | customer-analytics-insight-generation, analisi B2B |
| esperienza di conversazione | brand-concierge-conversational-experience |
