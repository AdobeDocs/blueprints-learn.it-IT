---
source-git-commit: 7511cc0e5c099d5d3ee1275a374cd9ffdc972335
workflow-type: tm+mt
source-wordcount: '3505'
ht-degree: 7%

---
# Audit e consigli blueprint

Questo controllo di audit applica la [valutazione](rubric.md) a ogni documento in
sezione &quot;Architecture Diagrams and Blueprints&quot; di [TOC.md](../help/blueprints/TOC.md) (righe 76-133) e
consiglia se ogni blueprint deve diventare un caso d&#39;uso **Pattern**, un&#39;architettura
**Diagramma**, entrambi (**Dividi**) o contrassegnati come **Duplicati** di un modello esistente.

Questo è solo un controllo di audit: nessun contenuto è stato spostato. Il backlog di migrazione (azioni Batch A-D)
sarà redatto come piano di follow-on separato una volta rivedute le raccomandazioni.

## Riepilogo

**Totale documenti controllati:** 43

| Consiglio | Conteggio | Azione |
| --- | --- | --- |
| Pattern | 8 | Creare un nuovo pattern di use case; rifilare l&#39;originale in un diagramma. |
| Duplica | 9 | Il modello esistente copre l’ambito; semplifica la blueprint a un diagramma e il collegamento incrociato. |
| Suddividi | 2 | Estrai il contenuto del pattern; riduci l’originale in un diagramma; collega entrambi. |
| Diagramma | 16 | Mantieni come diagramma dell’architettura; rifila la narrazione se necessario. |
| Navigazione | 8 | Pagina di destinazione della sezione (overview.md o links-only); visita di nuovo dopo l’arrivo delle migrazioni. |

### Taratura del gruppo di controllo

Tutti i 6 file `experience-platform/` hanno ottenuto un punteggio Pattern=0, Diagramma=3 → all&#39;unanimità **Diagramma**.
La rubrica è calibrata; i risultati delle altre sottoaree possono essere considerati attendibili come valutati.

### Nuova categoria di pattern del caso d’uso: attivazione e marketing B2B

Una nuova categoria `use-case-patterns/b2b/` (etichetta di visualizzazione **Attivazione e marketing B2B**, ancoraggio sommario
proposto `{#b2b-patterns}`) ospiterà tutti i modelli specifici di B2B. L’etichetta rispecchia la
Sottosezione &quot;Attivazione e marketing B2B&quot; nell&#39;area architettura-diagrammi di [TOC.md](../help/blueprints/TOC.md),
offrendo ai lettori una simmetria visiva tra le due sezioni.

Una volta completata, la categoria conterrà **7 pattern**:

| Origine | Azione | Percorso di destinazione |
| --- | --- | --- |
| `use-case-patterns/audience-building-activation/b2b-audience-activation.md` | **Riposiziona** modello esistente | `use-case-patterns/b2b/account-audience-activation.md` |
| `use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md` | **Riposiziona** modello esistente | `use-case-patterns/b2b/buying-group-marketing.md` |
| `use-case-patterns/analysis/b2b-analytics.md` | **Riposiziona** modello esistente | `use-case-patterns/b2b/account-analytics.md` |
| `b2b/b2b-journeys-with-marketo.md` | **Crea nuovo** (riga del modello di controllo) | `use-case-patterns/b2b/marketo-data-journeys.md` |
| `b2b/ajo-b2b-paid-media-controller.md` | **Crea nuovo** (riga del modello di controllo) | `use-case-patterns/b2b/paid-media-orchestration.md` |
| `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | **Crea nuovo** | `use-case-patterns/b2b/campaign-intake-and-creation.md` |
| `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | **Crea nuovo** | `use-case-patterns/b2b/campaign-review-and-approval.md` |

> **Stato di transizione iniziale - gate di coordinamento writer.** L&#39;attuale strategia di &quot;attivazione e marketing B2B&quot;> la sottosezione nell&#39;area dei diagrammi dell&#39;architettura di [TOC.md](../help/blueprints/TOC.md) (righe 95-106) **rimane intatta> durante la transizione**. Ogni conversione blueprint e rilocazione di pattern esistente richiede> disconnessione dal writer proprietario prima della migrazione del contenuto. Il nuovo pattern del caso d&#39;uso `b2b/`> coesiste con la sezione blueprint esistente durante le migrazioni pagina per pagina, con> collegamenti incrociati tra loro.

Quando le delocalizzazioni e i nuovi modelli sono tutti atterrati:

- La sezione [TOC.md](../help/blueprints/TOC.md) `Use Case Patterns` acquisirà un `B2B Activation & Marketing{#b2b-patterns}`
sottosezione (posizionamento da definire con l’autore).
- [use-case-patterns/overview.md](../help/blueprints/use-case-patterns/overview.md) otterrà una tabella delle categorie B2B.
- I modelli trasferiti verranno rimossi da `audience-building-activation`,
  `campaign-management-orchestration` e `analysis` tabelle di panoramica; i loro URL precedenti vengono mantenuti
attivo tramite reindirizzamenti in [migration-redirects.csv](migration-redirects.csv).

### Duplicati identificati (9)

L’ambito blueprint è già coperto da un pattern di casi d’uso esistente. L’azione di migrazione è
**semplifica in diagramma architettura + collegamento incrociato**.

| Blueprint | Pattern esistente |
| --- | --- |
| `audience-activation/advertising-activation.md` | `use-case-patterns/audience-building-activation/audience-activation-to-destinations.md` |
| `audience-activation/segment-match.md` | `use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md` |
| `b2b/b2bactivation.md` | `use-case-patterns/audience-building-activation/b2b-audience-activation.md` |
| `b2b/b2b-buying-group-journeys.md` | `use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md` |
| `customer-journey-analytics/b2b-cja.md` | `use-case-patterns/analysis/b2b-analytics.md` |
| `customer-journeys/journey-optimizer/journey-optimizer-journeys.md` | `use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md` |
| `customer-journeys/journey-optimizer/journey-optimizer-campaigns.md` | `use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md` |
| `customer-journeys/decision-management/decision-management-edge.md` | `use-case-patterns/personalization/offer-decisioning.md` |
| `customer-journeys/decision-management/decision-management-hub.md` | `use-case-patterns/personalization/offer-decisioning.md` |

> Nota: `decision-management-edge.md` e `decision-management-hub.md` sono mappati entrambi allo stesso> pattern `offer-decisioning.md` esistente. È consigliabile consolidare entrambi i progetti in un unico> diagramma delle opzioni di implementazione o miglioramento del modello esistente con l&#39;implementazione edge-vs-hub> varianti. Contrassegno per la revisione dello scrittore.

### Pattern per l’authoring (8 nuovi + 2 da frazioni = 10 totali)

| blueprint Source | Categoria proposta | Titolo pattern proposto |
| --- | --- | --- |
| `audience-activation/customer-activity.md` | audience-building-activation | Ricerca profilo in tempo reale per supporto e vendite |
| `audience-activation/data-science.md` | audience-building-activation | Acquisizione del modello di scienza dei dati per l’arricchimento del profilo |
| `audience-activation/real-time-lookup.md` | personalizzazione | Accesso profilo Edge per Personalization Web/Mobile |
| `b2b/b2b-journeys-with-marketo.md` | **b2b** (nuovo) | Percorsi di account B2B con integrazione dei dati di Marketo |
| `b2b/ajo-b2b-paid-media-controller.md` | **b2b** (nuovo) | Orchestrazione di contenuti multimediali a pagamento B2B tramite logica di tipo Waterfall Split-Path |
| `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | **b2b** (nuovo) | Acquisizione della richiesta di campagna e creazione automatica del programma |
| `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | **b2b** (nuovo) | Flusso di lavoro di revisione e approvazione risorse campagna |
| `customer-journeys/campaign-v8/campaign-v8-overview.md` | campaign-management-orchestration | Orchestrazione in batch e messaggistica transazionale di Campaign v8 |
| `audience-activation/rtcdp-target.md` *(Divisione)* | personalizzazione | Condivisione del pubblico in tempo reale con Adobe Target |
| `customer-journeys/journey-optimizer/3rd-party-messaging.md` *(Divisione)* | campaign-management-orchestration | Integrazione della messaggistica di terze parti con Journey Optimizer |

### Nuova categoria di pattern proposta

- **`b2b/`** (etichetta di visualizzazione **Attivazione e marketing B2B**) — consulta la sezione dedicata di cui sopra. Il
I modelli Marketo + Workfront (`intake-and-create`, `review-and-approve-blueprint`) sono instradati
anziché a una categoria `marketing-resource-management` separata, poiché rappresentano
Le operazioni di marketing B2B nella pratica. La nuova categoria aggrega 7 modelli totali: 3 ricollocati
da categorie esistenti e 4 nuove versioni create da blueprint.

### Reindirizzamenti di migrazione

Ogni modifica agli URL introdotta da questa migrazione aggiunge una riga al canonico
[`redirects.csv`](../redirects.csv) nella directory principale dell&#39;archivio (formato: `source,dest`). Confermato
i reindirizzamenti sono posizionati nell&#39;area intermedia in [migration-redirects.csv](migration-redirects.csv) e uniti in
file canonico, in quanto ogni spostamento corrispondente si verifica effettivamente.

**Confermato (3 voci, in staging):** rilocazioni pattern esistenti in `b2b/`. Consulta
[migration-redirects.csv](migration-redirects.csv).

**In sospeso — aggiunto quando un blueprint è *eliminato* (non quando ridotto al diagramma attivo):** se
La blueprint della riga Pattern, Split o Duplicate viene successivamente rimossa completamente, aggiungendo un reindirizzamento dalla
URL blueprint per l’URL del modello canonico. Approccio di migrazione predefinito (semplificazione per i diagrammi)
mantiene attivo l&#39;URL blueprint e **non richiede** questi reindirizzamenti. Elencato di seguito per
completezza se un progetto è completamente ritirato:

```
# Pattern blueprints — if deleted, redirect to the new pattern URL
# (slugs are placeholders; finalize when each pattern is authored)
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/customer-activity → use-case-patterns/audience-building-activation/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/data-science → use-case-patterns/audience-building-activation/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/real-time-lookup → use-case-patterns/personalization-patterns/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2b-journeys-with-marketo → use-case-patterns/b2b-patterns/marketo-data-journeys
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/ajo-b2b-paid-media-controller → use-case-patterns/b2b-patterns/paid-media-orchestration
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/marketo-engage-and-workfront-integration-blueprint/intake-and-create → use-case-patterns/b2b-patterns/campaign-intake-and-creation
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint → use-case-patterns/b2b-patterns/campaign-review-and-approval
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/campaign-v8/campaign-v8-overview → use-case-patterns/campaign-orchestration-patterns/<new-pattern-slug>

# Duplicate blueprints — if deleted, redirect to the existing pattern URL
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/advertising-activation → use-case-patterns/audience-building-activation/audience-activation-to-destinations
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/segment-match → use-case-patterns/audience-building-activation/audience-collaboration-segment-match
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2bactivation → use-case-patterns/b2b-patterns/account-audience-activation  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2b-buying-group-journeys → use-case-patterns/b2b-patterns/buying-group-marketing  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journey-analytics/b2b-cja → use-case-patterns/b2b-patterns/account-analytics  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/journey-optimizer/journey-optimizer-journeys → use-case-patterns/campaign-orchestration-patterns/event-triggered-messaging
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/journey-optimizer/journey-optimizer-campaigns → use-case-patterns/campaign-orchestration-patterns/batch-outbound-message-activation
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/decision-management/decision-management-edge → use-case-patterns/personalization-patterns/offer-decisioning
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/decision-management/decision-management-hub → use-case-patterns/personalization-patterns/offer-decisioning

# Optional one-off — if customer-journey-analytics/analysis.md is relocated to experience-platform/
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journey-analytics/analysis → architecture-diagrams/architecture-overview/analysis
```

Quando converti uno dei precedenti in righe di reindirizzamento attive, formatta come separato da virgole `source,dest`
con percorsi completi di `/en/docs/...` (nessun suffisso `.html`), corrispondenti al pattern esistente in
[`redirects.csv`](../redirects.csv).

### Criterio di creazione di reindirizzamento (regola durevole)

Per ogni passaggio di migrazione, segui queste regole:

1. **File spostato o rinominato** → aggiungere il reindirizzamento dal vecchio URL al nuovo URL.
2. **File eliminato** (blueprint sostituito; nessun diagramma mantenuto) → aggiungere il reindirizzamento dall&#39;URL eliminato a
URL di sostituzione canonico.
3. **File semplificato** (URL invariato) → reindirizzamento.
4. **Ancoraggio sommario rinominato** (ad esempio, modifica intestazione sezione) → aggiungere reindirizzamenti per ogni pagina in
l’ancoraggio, poiché l’URL cambia.

### Domande aperte per l&#39;autore

1. **Edge di gestione delle decisioni rispetto all&#39;hub**: entrambi corrispondono allo stesso elemento esistente `offer-decisioning.md`
pattern. Consolidamento in un singolo diagramma con varianti di distribuzione o trattamento separato
diagrammi che si intersecano con lo stesso pattern?
2. **percorsi Journey Optimizer e messaggistica attivata da eventi**: l&#39;agente ha contrassegnato questo duplicato
classificazione come incerta. Verifica l’allineamento dell’ambito prima di ridurre la blueprint.
3. **`customer-journey-analytics/analysis.md`** — il contenuto riguarda in realtà Experience Platform
Query Service, non CJA. Provare a spostare la cartella in `experience-platform/`. (Un reindirizzamento
verrebbe aggiunto in tal caso. Vedere [migration-redirects.csv](migration-redirects.csv).)
4. **Campaign v7 (obsoleto)** — tre file v7 obsoleti sono stati classificati come Diagramma /
Navigazione. Conferma se eseguire la migrazione, lasciare invariato o rimuovere completamente dal sommario.
5. **`customer-success-stories.md`** — pagina di riferimento solo collegamenti (non `overview.md`).
Classificato come Navigazione. Conferma o riclassifica.
6. **Ancoraggio sommario sezione B2B** — proposto `{#b2b-patterns}`. Altre sottosezioni di pattern utilizzano
   Suffisso `-patterns` (`{#personalization-patterns}`, `{#analysis-patterns}`,
   `{#campaign-orchestration-patterns}`). Conferma o scegli un altro ancoraggio prima di creare i reindirizzamenti.
7. **Posizionamento di sezione B2B nel sommario** — proposto in `+ Use Case Patterns{#use-case-patterns}`.
Ordina tra fratelli e sorelle (Creazione e attivazione del pubblico, Personalization, Gestione campagne)
Orchestrazione, analisi, attivazione B2B e marketing, esperienza conversazionale)
la chiamata dello scrittore.
8. **Coordinamento autore** — ogni conversione blueprint e rilocazione pattern esistente
richiede l’approvazione dello scrittore prima dello spostamento del contenuto. La tabella di controllo è lo stato di destinazione, non uno
piano di sequenziamento; la sequenza avviene in un piano di migrazione successivo dopo il coordinamento.

## Tabella di controllo

| percorso | titolo | riepilogo | dominant_type | consiglio | posed_pattern_category | posed_pattern_title | posed_diagram_title | duplicate_of | pattern_score | chart_score | note |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| help/blueprints/experience-platform/experience-cloud.md | Diagrammi dell’architettura di Adobe Experience Cloud | Architettura aziendale che mostra come le applicazioni e i servizi Experience Cloud si integrano in AEP Foundation. | Diagramma | Diagramma |  |  | Panoramica dell’architettura di Experience Cloud |  | 0 | 3 | Sostituzione 3 (nessun obiettivo aziendale). Tre diagrammi complementari (marketing, integrazione, scenario aziendale). Gruppo di controllo: come previsto. |
| help/blueprints/experience-platform/platform-applications.md | Diagrammi di architettura di Adobe Experience Platform e applicazioni | Diagrammi di architettura che mostrano la relazione di Experience Platform con altre applicazioni Experience Cloud. | Diagramma | Diagramma |  |  | Architettura di AEP e applicazioni |  | 0 | 3 | Sostituisci 3. Due diagrammi panoramici/dettagliati; nessuna guida all’implementazione. Collegamenti incrociati alle integrazioni: scopri i documenti. Gruppo di controllo: come previsto. |
| help/blueprints/experience-platform/platform-data-flow.md | Diagrammi dell’architettura del flusso di dati in Adobe Experience Platform | Diagramma dell’architettura del flusso di dati che mostra i percorsi di acquisizione e di uscita da e verso Experience Platform. | Diagramma | Diagramma |  |  | Architettura del flusso di dati di AEP |  | 0 | 3 | Sostituisci 3. Diagramma di flusso dei dati singolo con riferimento ai documenti di raccolta dei dati. Artefatto di architettura pura. Gruppo di controllo: come previsto. |
| help/blueprints/experience-platform/guardrails.md | Guarderail per Experience Platform e applicazioni | Vincoli di sistema, aspettative di prestazioni e guardrail di latenza per AEP e le applicazioni. | Diagramma | Diagramma |  |  | Guardrail e latenze di AEP e Applications |  | 0 | 3 | Sostituisci 3. Diagramma di latenza più tabelle di riferimento. Architect-oriented (edge vs hub). Documentazione sui vincoli, non sulle procedure. Gruppo di controllo: come previsto. |
| help/blueprints/experience-platform/deployment/websdk.md | Diagramma dell’architettura di Experience Platform Web SDK e Edge Network | Architettura di distribuzione di Web SDK e Edge Network che mostra i flussi di raccolta dati. | Diagramma | Diagramma |  |  | Distribuzione di Web SDK e Edge Network |  | 0 | 3 | Sostituisci 3. Due diagrammi (flusso e sequenza). Fa riferimento ai tutorial ma non a procedure interne al documento. Orientata agli architetti. Gruppo di controllo: come previsto. |
| help/blueprints/experience-platform/deployment/appsdk.md | Diagramma dell’architettura per l’implementazione tramite SDK per specifiche applicazioni | Diagramma dell’architettura dei percorsi di integrazione SDK e di raccolta dati specifico per l’applicazione. | Diagramma | Diagramma |  |  | Distribuzione di SDK specifica per l’applicazione |  | 0 | 3 | Sostituisci 3. Diagramma di distribuzione singolo con narrazione minima. Artefatto di architettura pura. Gruppo di controllo: come previsto. |
| help/blueprints/audience-activation/advertising-activation.md | Destinazioni da Audience Activation a social network e Advertising | Attiva i tipi di pubblico su Facebook e Google tramite RTCDP con configurazione dell’identità e configurazione della destinazione. | Pattern | Duplica |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md | 4 | 1 | Il modello esistente copre questo ambito. Sostituzione duplicata. Azione: da semplificato a diagramma puro e collegamento incrociato. |
| help/blueprints/audience-activation/audience-manager.md | Basato su dispositivo: targeting del pubblico anonimo con Audience Manager | Attivazione anonima del pubblico tramite Audience Manager o RTCDP per il targeting basato su dispositivi tra canali diversi. | Diagramma | Diagramma |  |  | Targeting Anonimo Del Pubblico Basato Su Dispositivi |  | 1 | 2 | Minima narrazione. Diagramma dell’architettura presente, topologia di sistema illustrata. Nessun framework per obiettivi aziendali; implementazione di SDK e concetti hub/edge. |
| help/blueprints/audience-activation/customer-activity.md | Accesso al profilo in tempo reale per scenari di supporto e vendita | Abilita il contesto del cliente in tempo reale da parte del supporto e degli agenti di vendita tramite l’API di ricerca dei profili. | Pattern | Pattern | audience-building-activation | Ricerca profilo in tempo reale per supporto e vendite |  |  | 3 | 1 | Definisce il risultato di business (contesto dell’agente). Include un elenco di controllo dei prerequisiti; passaggi di implementazione > 30 righe. Caso d’uso univoco: accesso al profilo hub (non personalizzazione Edge). Distinto dai modelli di personalizzazione esistenti. |
| help/blueprints/audience-activation/data-science.md | Blueprint per personalizzazione Data Science per l’arricchimento del profilo | Acquisisci i punteggi del modello di apprendimento automatico in RTCDP per arricchire i profili per la personalizzazione e la segmentazione. | Pattern | Pattern | audience-building-activation | Acquisizione del modello di scienza dei dati per l’arricchimento del profilo |  |  | 3 | 1 | Frames business result (arricchimento per la personalizzazione). Ha casi d’uso e considerazioni; considerazioni sull’implementazione > 30 righe. Concentrati sui flussi di lavoro della scienza dei dati, non sulla messaggistica/attivazione. |
| help/blueprints/audience-activation/enterprise-destinations.md | Attivazione in base a pubblico e profili con destinazioni verso soluzioni aziendali | Trasmetti le modifiche al profilo batch o di streaming e le modifiche del pubblico all’archiviazione cloud e alle app aziendali per le vendite, il supporto e le analisi. | Diagramma | Diagramma |  |  | Attivazione di tipi di pubblico e profili Enterprise |  | 1 | 2 | Nessun inquadramento degli obiettivi aziendali. Linee guida sull’implementazione sparse. Diagramma dell’architettura + topologia di sistema per applicazioni di archiviazione cloud/aziendali. Visivo-dominante. |
| help/blueprints/audience-activation/real-time-lookup.md | Accesso in tempo reale al profilo Edge per Personalization web e mobile | Accedi al profilo unificato Edge in millisecondi per la personalizzazione web e mobile in tempo reale. | Pattern | Pattern | personalizzazione | Accesso profilo Edge per Personalization Web/Mobile |  |  | 5 | 2 | Frame aziendale avanzato (personalizzazione a bassa latenza). Due modelli di implementazione (SDK web e API Edge). Prerequisiti e passaggi completi (>30 righe). KPI impliciti (latenza, velocità effettiva). |
| help/blueprints/audience-activation/rtcdp-target.md | Customer Personalization noto con Target | Condividi i tipi di pubblico e i profili di RTCDP con Adobe Target per la personalizzazione web e mobile dei visitatori noti. | Misto | Suddividi | personalizzazione | Condivisione del pubblico in tempo reale con Adobe Target | Architettura di integrazione di Target | help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md | 3 | 2 | Si sovrappone al pattern visitatore noto esistente, ma con un ambito più ristretto (solo Target). Tre modelli di integrazione. Diagrammi dell’architettura + implementazione Edge considerata. Contenuto del modello + diagramma sostanziali → Divisione. |
| help/blueprints/audience-activation/segment-match.md | Audience Collaboration con corrispondenza segmento | Abilita la collaborazione sicura del pubblico dei partner tramite Segment Match con controlli della privacy. | Pattern | Duplica |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md | 4 | 1 | Il modello esistente copre esattamente questo aspetto. Sostituzione duplicata. Contenuto univoco da mantenere nel diagramma: configurazione dettagliata di RBAC/consenso/governance e flusso di lavoro degli annunci programmatici. |
| help/blueprints/b2b/overview.md | Progetti di analisi, attivazione e marketing B2B | Pagina di navigazione in cui sono elencati analisi B2B, attivazione del pubblico, gruppo di acquisto, Marketo e blueprint di Workfront. | Navigazione | Navigazione |  |  |  |  |  |  | Override 1: file denominato overview.md. Escluso dalla migrazione. |
| help/blueprints/b2b/b2bactivation.md | Blueprint per l’attivazione di profili e pubblico B2B | Attiva tipi di pubblico B2B basati sull’account tra canali web, e-mail e pubblicitari utilizzando i dati dell’account e del profilo. | Pattern | Duplica |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md | 3 | 1 | Override 2: esiste un pattern equivalente. La blueprint è un sottoinsieme più ristretto incentrato sull’architettura. |
| help/blueprints/b2b/b2b-account-activation.md | Attivazione di account B2B su destinazioni Advertising e file | Eseguire il targeting di account B2B tramite destinazioni di archiviazione LinkedIn e cloud utilizzando la creazione e l’attivazione del pubblico dell’account. | Diagramma | Diagramma |  |  | Audience Activation account B2B |  | 1 | 2 | Inquadratura aziendale minima, nessun KPI, narrazione minima. Diagramma dell’architettura presente; descrizione della topologia LinkedIn/cloud-storage. Mantieni come diagramma. |
| help/blueprints/b2b/b2b-buying-group-journeys.md | Blueprint per l’acquisto di attività di marketing e gestione dei Percorsi basate su gruppi | Progetta percorsi di account che qualifichino i lead in gruppi di acquisto con ruoli definiti e interessi nella soluzione. | Pattern | Duplica |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md | 5 | 2 | Override 2: esiste un pattern equivalente. La blueprint ha un contenuto ricco, ma il modello esistente è più completo. |
| help/blueprints/b2b/b2b-journeys-with-marketo.md | Percorsi B2B con blueprint dei dati Marketo | Distribuisci Journey Optimizer B2B edition con i dati di Marketo per orchestrare i percorsi di gruppi di acquisto e il coinvolgimento degli account. | Pattern | Pattern | b2b | Percorsi di account B2B con integrazione dei dati di Marketo |  |  | 4 | 1 | Solida struttura aziendale. KPI elencati; più opzioni di implementazione; considerazioni approfondite (>30 righe). Differenziato dal modello esistente in base alla profondità di integrazione dei dati di Marketo (configurazione XDM, unione delle identità, blocco dei campi). Consente di passare alla nuova categoria b2b/. |
| help/blueprints/b2b/ajo-b2b-paid-media-controller.md | AJO B2B - Account Journey Orchestration - Controller per contenuti multimediali a pagamento | Orchestrazione di campagne multimediali B2B a pagamento utilizzando la logica a cascata per assegnare account alle campagne e attivarle nelle destinazioni. | Pattern | Pattern | b2b | Orchestrazione di contenuti multimediali a pagamento B2B tramite logica di tipo Waterfall Split-Path |  |  | 4 | 2 | Solida struttura aziendale. KPI espliciti; opzioni di implementazione multiple; prerequisiti; narrazione di più di 30 righe. Distinto dal modello di gruppo acquirente esistente (si concentra sulla definizione delle priorità dei media a pagamento, non sullo sviluppo). Consente di passare alla nuova categoria b2b/. |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md | Panoramica del blueprint per l’integrazione di Marketo Engage e Workfront | Panoramica della pianificazione delle campagne per l’automazione dell’esecuzione tramite Marketo Engage e Workfront con Fusion. | Navigazione | Navigazione |  |  |  |  |  |  | Override 1: file denominato overview.md. Escluso dalla migrazione. |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md | Blueprint per l’acquisizione e la creazione | Automatizzare l’inserimento delle richieste di campagne di marketing B2B alla creazione utilizzando i modelli di programma di Workfront Forms e Marketo Engage. | Pattern | Pattern | b2b | Acquisizione della richiesta di campagna e creazione automatica del programma |  |  | 4 | 1 | Forte struttura aziendale sulla velocità della campagna. KPI impliciti (errori/riduzione della rilavorazione); passaggi del flusso di lavoro > 30 righe; elenco di controllo di preparazione. Percorsi verso la nuova categoria b2b/ (Marketo+Workfront ops sono prevalentemente B2B). |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md | Blueprint per la revisione e l’approvazione | Integra i flussi di lavoro di verifica e approvazione di Workfront con le risorse e-mail di Marketo Engage utilizzando l’automazione Fusion. | Pattern | Pattern | b2b | Flusso di lavoro di revisione e approvazione risorse campagna |  |  | 3 | 2 | Solida struttura aziendale basata su conformità e precisione; KPI impliciti (velocità di approvazione); descrizione > 30 righe; sezione pianificazione del flusso di lavoro. Consente di passare alla nuova categoria b2b/. |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md | Storie di successo dei clienti | Collegamenti a casi aziendali di clienti e webinar che illustrano i risultati dell’integrazione di Marketo e Workfront. | Navigazione | Navigazione |  |  |  |  |  |  | Contenuto minimo (6 collegamenti ipertestuali). Nessuna struttura aziendale, KPI, architettura o narrativa. Viene considerato come navigazione. Il processo di scrittura deve confermare. |
| help/blueprints/customer-journey-analytics/overview.md | Customer Journey Analytics blueprint | Unifica e analizza i dati e il comportamento dei clienti da vari canali per creare visualizzazioni basate sul percorso. | Navigazione | Navigazione |  |  |  |  |  |  | Override 1: overview.md. Pagina di destinazione in stile sommario. Escluso dalla migrazione. |
| help/blueprints/customer-journey-analytics/b2b-cja.md | Blueprint per Customer Journey Analytics B2B | Reporting e analisi CJA basati sull’account per le organizzazioni B2B che utilizzano l’account come modello di dati principale. | Pattern | Duplica |  |  |  | help/blueprints/use-case-patterns/analysis/b2b-analytics.md | 4 | 2 | Override 2: il modello equivalente riguarda l’analisi a livello di account B2B con CJA B2B edition. Azione: semplifica con diagramma, collegamento incrociato. |
| help/blueprints/customer-journey-analytics/cja-rtcdp.md | Customer Journey Analytics con blueprint di Real-time Customer Data Platform | Crea e pubblica tipi di pubblico da CJA a RTCDP per il targeting e la personalizzazione. | Diagramma | Diagramma |  |  | Integrazione di pubblicazione di tipi di pubblico da CJA a RTCDP |  | 1 | 3 | Forte attenzione all’architettura (integrazione sistema-sistema, forma di implementazione). Minima narrazione. Contenuto univoco: il pubblico di CJA pubblica i guardrail di latenza. |
| help/blueprints/customer-journey-analytics/cja-ajo.md | Customer Journey Analytics con blueprint Journey Optimizer | Analizza i dati di consegna e interazione di AJO in CJA; pubblica i tipi di pubblico di CJA in AJO. | Diagramma | Diagramma |  |  | Integrazione e analisi tra CJA e AJO |  | 1 | 3 | Forte attenzione all’architettura. Minima narrazione. Contenuto univoco: modello bidirezionale di condivisione dati CJA-AJO. |
| help/blueprints/customer-journey-analytics/analysis.md | Blueprint per analisi e intelligence dei dati | Utilizza Experience Platform Query Service per l’analisi esplorativa dei dati del data lake. | Diagramma | Diagramma |  |  | Integrazione di Experience Platform Query Service e BI Tool |  | 1 | 3 | Include Query Service, NON specifico per CJA. Potrebbe non essere posizionato correttamente nella cartella di CJA; valuta la possibilità di trasferire Experience-platform/. Pubblico architetto forte (PostgreSQL, strumenti BI). |
| help/blueprints/customer-journeys/overview.md | Blueprint per customer journey | Piattaforme di marketing moderne che supportano percorsi basati su eventi e campagne avviate dal brand su diversi canali. | Navigazione | Navigazione |  |  |  |  |  |  | Override 1: overview.md. Sommario per le sottocategorie di percorso; descrive il posizionamento di Journey Optimizer e Campaign. |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md | Blueprint Journey Optimizer | Orchestrazione del profilo 1:1 basata sugli eventi e comunicazioni del brand basate sul pubblico tra canali diversi. | Navigazione | Navigazione |  |  |  |  |  |  | Override 1: overview.md. Pagina di destinazione con schede dei casi d’uso e modelli di integrazione. |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-journeys.md | Journey Optimizer - Blueprint per messaggi attivati e Adobe Experience Platform | Flussi di lavoro basati su eventi in tempo reale che offrono esperienze personalizzate in più passaggi in base ai comportamenti dei clienti. | Pattern | Duplica |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md | 4 | 2 | Override 2 con attenzione: l’agente è contrassegnato come probabilmente duplicato ma incerto. Verificare l&#39;allineamento dell&#39;ambito prima della riduzione. Le considerazioni sull’architettura possono essere univoche (aggiornamento del profilo, tempistica di qualificazione dei segmenti) e meritano di essere mantenute nel diagramma. |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-campaigns.md | Journey Optimizer - Orchestrazione campagna | Comunicazioni pianificate in più passaggi basate sul pubblico tra canali in uscita: e-mail, SMS, push, direct mail. | Pattern | Duplica |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md | 3 | 2 | Override 2: pattern equivalente. Diagrammi a più architetture; mantieni come diagramma. Contenuto univoco: dettagli dell’architettura del profilo di database relazionale/portale del pubblico/skinny. |
| help/blueprints/customer-journeys/journey-optimizer/3rd-party-messaging.md | Journey Optimizer - Blueprint per messaggistica di terze parti | Dimostra l&#39;integrazione di Journey Optimizer con sistemi di messaggistica di terze parti per comunicazioni orchestrate. | Misto | Suddividi | campaign-management-orchestration | Integrazione della messaggistica di terze parti con Journey Optimizer | Architettura di messaggistica di terze parti |  | 2 | 2 | Punteggi → Dividi. Diagramma (topologia sistema-sistema) più contenuto pattern (passaggi di implementazione, vincoli di integrazione: autenticazione bearer, nessun IP statico, limiti di velocità). Vale la pena di preservarli entrambi. |
| help/blueprints/customer-journeys/decision-management/decision-management-overview.md | Blueprint per la gestione delle decisioni | Distribuisci offerte personalizzate tra i percorsi dei clienti tramite la libreria di offerte centralizzata e il motore decisionale. | Navigazione | Navigazione |  |  |  |  |  |  | Override 1: overview.md. Descrive i componenti di gestione delle decisioni e gli approcci di distribuzione edge vs hub. |
| help/blueprints/customer-journeys/decision-management/decision-management-edge.md | Blueprint per la gestione delle decisioni tramite rete Edge | Distribuisci offerte personalizzate in esperienze web e mobili in tempo reale con latenza di sotto-secondo sulla rete Edge di. | Misto | Duplica |  |  |  | help/blueprints/use-case-patterns/personalization/offer-decisioning.md | 2 | 3 | Override 2: è mappato su offer-decisioning. Variante di distribuzione di Edge: è consigliabile consolidare con la blueprint dell’hub in un unico diagramma di opzioni di distribuzione. |
| help/blueprints/customer-journeys/decision-management/decision-management-hub.md | Blueprint per la gestione delle decisioni tramite hub | Distribuisci offerte personalizzate tra i canali, inclusi chioschi, esperienze assistite da agenti e consegne in uscita. | Misto | Duplica |  |  |  | help/blueprints/use-case-patterns/personalization/offer-decisioning.md | 2 | 3 | Override 2: è mappato su offer-decisioning. Variante di distribuzione dell’hub: è consigliabile eseguire il consolidamento con una blueprint Edge in un singolo diagramma di opzioni di distribuzione. |
| help/blueprints/customer-journeys/campaign-v8/campaign-v8-overview.md | Blueprint, campagna e piattaforma di Campaign v8 | Piattaforma di gestione delle campagne batch di nuova generazione con funzionalità di ETL, segmentazione e messaggistica transazionale. | Pattern | Pattern | campaign-management-orchestration | Orchestrazione in batch e messaggistica transazionale di Campaign v8 | Modelli di implementazione dell’architettura di Campaign v8 |  | 4 | 3 | Approccio tecnico distinto (Campaign v8 nativo, non AJO). Diagrammi a più architetture; inquadratura aziendale; KPI impliciti nei guardrail (batch da 20 milioni di msg/h, tempo reale da 1 milione di ore). Nessun equivalente nel catalogo pattern esistente. Nota: anche i punteggi possono essere suddivisi, quindi proporre un motivo, ma l&#39;autore potrebbe voler conservare il diagramma. |
| help/blueprints/customer-journeys/campaign-v8/rtcdp-and-campaign-v8.md | Modello di integrazione per Real-Time CDP con Adobe Campaign v8 | Mostra l’integrazione di pubblico e profilo di RTCDP con Campaign v8 per conversazioni personalizzate. | Diagramma | Diagramma |  |  | RTCDP - Pubblico e scambio di profili di Campaign v8 |  | 1 | 2 | Blueprint del connettore di integrazione, non caso di utilizzo autonomo. Diagramma + brevi prerequisiti/guardrail. Architetto-orientato. |
| help/blueprints/customer-journeys/campaign-v8/ajo-and-campaign-v8.md | Blueprint per Journey Optimizer con Adobe Campaign v8 | Dimostra l’orchestrazione AJO con la messaggistica transazionale di Campaign v8 per 1:1 esperienze. | Diagramma | Diagramma |  |  | Journey Optimizer - Integrazione della messaggistica transazionale di Campaign v8 |  | 1 | 2 | Connettore di integrazione. Diagramma + passaggi di implementazione + vincoli tecnici (4.000 msg/5min, solo per eventi avviati). Collegamento incrociato ai modelli di AJO e Campaign v8. |
| help/blueprints/customer-journeys/campaign-v7/campaign-v7-overview.md | Blueprint per Campaign v7 | Obsoleto: messaggistica basata su batch, onboarding, remarketing, direct mailing, messaggistica transazionale semplice. | Navigazione | Navigazione |  |  |  |  |  |  | PRODOTTO OBSOLETO (frontmatter si collega a v8). Contenuto minimo (solo diagramma dell’architettura). Non eseguire la migrazione. |
| help/blueprints/customer-journeys/campaign-v7/rtcdp-and-campaign-v7.md | Real-Time CDP con Campaign v7 e modello di integrazione Campaign Standard | Presenta l’integrazione di RTCDP e Real-Time Customer Profile con Campaign v7/Standard per conversazioni personalizzate. | Diagramma | Diagramma |  |  | RTCDP - Pubblico e scambio di profili di Campaign v7/Standard |  | 1 | 2 | OBSOLETO. Connettore di integrazione. Diagramma + fasi di implementazione complete. Non eseguire la migrazione a un nuovo pattern; lascia invariato. |
| help/blueprints/customer-journeys/campaign-v7/ajo-and-campaign-v7.md | Blueprint per Journey Optimizer con Adobe Campaign v7 | Dimostra l’orchestrazione AJO con la messaggistica transazionale di Campaign v7 per 1:1 esperienze. | Diagramma | Diagramma |  |  | Journey Optimizer - Integrazione della messaggistica transazionale di Campaign v7 |  | 1 | 2 | OBSOLETO. Connettore di integrazione. Diagramma + passaggi di implementazione + vincoli. Non eseguire la migrazione; lascia così com’è. |
