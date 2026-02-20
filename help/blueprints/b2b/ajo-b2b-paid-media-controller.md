---
title: AJO B2B - controller per supporti a pagamento
description: Priorità delle campagne e attivazione degli account per le destinazioni dei file multimediali a pagamento
solution: Journey Optimizer B2B Edition
exl-id: a4f4982f-2b56-4ce2-9c16-abdf627f97de
source-git-commit: 388beb1609384f266f0d80a7dd5a14b03ced3110
workflow-type: tm+mt
source-wordcount: '1428'
ht-degree: 0%

---

# AJO B2B - Account Journey Orchestration - Controller per contenuti multimediali a pagamento

## Panoramica

I team di marketing che eseguono supporti B2B a pagamento su larga scala devono affrontare un problema ricorrente: **gli account finiscono in più campagne alla volta** (persona, consapevolezza delle categorie, soluzioni guidate, ricerca), che diluisce la messaggistica, causa affaticamento del pubblico e forza il lavoro manuale degli elenchi (caricamenti, esclusioni e soppressione) in LinkedIn Account Match (destinazione account). Senza **assegnazione delle priorità delle cascate** e **assegnazione automatica delle campagne**, non esiste un&#39;unica posizione per decidere quale account ottiene quale messaggio e le operazioni non vengono scalate.

**Paid Media Controller** è la soluzione ideale per risolvere questo problema. Utilizza **Adobe Journey Optimizer B2B edition (AJO B2B)** e **Adobe Experience Platform (AEP)** insieme: un **percorso di account** legge un pubblico di account qualificato da Real-Time CDP, applica la **logica split-path (waterfall)** per assegnare ogni account esattamente a un livello di campagna e **attiva ogni percorso direttamente** alle destinazioni di media a pagamento (**ad esempio, LinkedIn Matched Audiences**), senza handoff manuali dell&#39;elenco. Il risultato è un controllo di precisione, meno sovrapposizioni e un pattern ripetibile per l’orchestrazione di contenuti multimediali a pagamento B2B multicanale.

## Caso d’uso: storia di un addetto marketing: perché un controllore è importante

*Maya è leader nei media a pagamento per un marchio B2B globale. Il suo team gestisce decine di campagne: awareness di base, intento di categoria (Percorso, Dati, Contenuto), programmi guidati da soluzioni, campagne personali e campagne da vincere. Ha un problema.*

**Problema:** gli stessi account vengono visualizzati in più campagne. Un account di Percorso ad alto intento è anche in un ampio elenco di consapevolezza; un account di inseguimento ottiene ancora annunci personali. I caricamenti e le esclusioni degli elenchi sono manuali. Ogni volta che aggiorna un elenco &quot;must-win&quot; o il lancio di una nuova campagna persona, il suo team riesporta i tipi di pubblico, riconcilia le sovrapposizioni nei fogli di calcolo e ricarica LinkedIn e altre piattaforme. È lenta, soggetta ad errori, e non si adatta.

**Cosa vuole:** un posto in cui ogni account qualificato viene valutato una volta, assegnato alla campagna *più rilevante* utilizzando regole di priorità chiare (cascata) e inviato automaticamente alla destinazione media a pagamento corretta. Nessun handoff manuale dell’elenco. Quando i dati o la strategia cambiano, il sistema rivaluta e sposta gli account tra le campagne senza che il suo team modifichi gli elenchi.

**Risposta di Adobe:** Con **AJO B2B e AEP che lavorano insieme**, Maya può eseguire un singolo percorso **Paid Media Controller**: AEP e Real-Time CDP detengono i dati e un pubblico principale di &quot;account qualificati&quot;; AJO B2B esegue un percorso di account che utilizza la **logica del percorso diviso** (cascata) per indirizzare ogni account al livello giusto, ad esempio Inseguimenti mirati → Persona → Led da Soluzione → Categoria Consapevolezza → Consapevolezza Fondamentale, e **Attiva a Destinazione** invia ogni percorso a destra Campagna LinkedIn (o di altro tipo). Un percorso, una fonte di verità, nessuna esportazione manuale di elenchi. Questo è il modello di controller per supporti a pagamento ed è il modo in cui Adobe consente precisione e scalabilità per i supporti a pagamento B2B.

## Perché è importante per le imprese B2B:

Le organizzazioni che adottano questo modello possono eliminare completamente la logica di eliminazione manuale e di esclusione (ad esempio, il 100% della risoluzione di sovrapposizione gestita nel percorso), scalare a **decine di migliaia di account** tramite un singolo controller e mantenere una **singola origine di verità** per cui l&#39;account viene indirizzato a quale campagna. Il sistema **si adatta automaticamente** in base al focus della campagna, al pubblico di destinazione e agli obiettivi di vendita, senza dover riesportare gli elenchi o ricaricare su ogni piattaforma. Per qualsiasi azienda B2B che esegue più campagne paid media, il modello Paid Media Controller offre la chiarezza, il controllo e l’automazione che i flussi di lavoro manuali di elenco non possono ottenere.

I seguenti KPI si allineano bene con la misurazione del successo:

- **Consapevolezza:** gli account di destinazione visualizzano gli annunci giusti e passano alle campagne giuste a una velocità maggiore?
- **Coinvolgimento:** coinvolgimento e conversione migliorano quando si rimuove la sovrapposizione?
- **Efficienza:** quanto è diminuito il lavoro dell&#39;elenco manuale (caricamenti, esclusioni, soppressione)?
- **Costo:** Come cambiano i costi per account o opportunità acquisiti con l&#39;orchestrazione automatizzata?

## Orchestrazione Percorso media a pagamento

Un caso d&#39;uso comune e su cui si concentra questo blueprint è l&#39;**orchestrazione di Percorsi multimediali a pagamento B2B**: verificare che ogni account qualificato sia assegnato esattamente a un livello di campagna e attivato nella destinazione corretta di media a pagamento, senza sovrapposizioni o handoff manuali.

Il percorso di controller **legge** un pubblico di account qualificati (integrato in Real-Time CDP dai dati di AEP), **valuta** ogni account attraverso condizioni di percorso suddiviso (cascata), ad esempio, → ricerca di tipi di pubblico → persona → categoria guidati dalla soluzione → di base, e **attiva** ogni percorso alla destinazione corrispondente (ad esempio, tipi di pubblico abbinati a LinkedIn per ogni campagna).

**Soluzione incentrata sull&#39;account:** L&#39;elemento attivo di Paid Media Controller è **account** e la relativa **assegnazione campagna**. La configurazione tecnica supporta i dati e i tipi di pubblico che rappresentano account qualificati e i relativi attributi (ad esempio intento, segmento, persona), necessari per la corretta segmentazione a livello di account e l’orchestrazione basata su percorso.

## Requisiti

La soluzione incentrata sull&#39;account richiede le applicazioni e i servizi seguenti:

- **Adobe Journey Optimizer B2B edition** — percorsi di account, logica split-path (cascata), Attiva su destinazione.
- **Adobe Real-time Customer Data Platform (RTCDP) B2B edition** — Profili account, pubblico account (ad esempio, account qualificati per supporti a pagamento).

## Architettura

Flusso ad alto livello:

1. **Dati e tipi di pubblico**: AEP contiene profili ed eventi; Real-Time CDP B2B crea tipi di pubblico per account (ad esempio, &quot;Account idonei per contenuti multimediali a pagamento&quot;) utilizzati come pubblico di ingresso al percorso.
2. **Orchestrazione** — percorso di account AJO B2B: **Read audience** (account qualificati) → **Split path** (cascata: ad esempio, Pursuit → Solution-Led → Persona → Category → Foundation) → **Activate to Destination** (per percorso a LinkedIn o altri supporti a pagamento).
3. **Destinazioni** — I canali multimediali a pagamento (ad esempio, LinkedIn Matched Audiences) ricevono l&#39;attivazione a livello di account da ogni percorso di percorso; nessun caricamento manuale dell&#39;elenco.

## Diagramma architettura

<img src="assets/ajo-b2b-paid-media-activation-architecture.svg" alt="Architettura di AJO B2B Paid Media Controller" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## Modellazione dei dati in AEP B2B

Con qualsiasi orchestrazione basata sui dati, la progettazione dello schema è importante. I profili account e persona in AEP/RTCDP devono includere gli attributi utilizzati in **condizioni del percorso diviso** (ad esempio, flag di ricerca, interesse della soluzione, persona, categoria intento, punteggio di coinvolgimento). Gli schemi B2B (XDM Business Account, XDM Individual Profile, relazionale) devono rappresentare la gerarchia e le origini dati. Per informazioni dettagliate, consulta [Schemi B2B di RTCDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) e [Documentazione B2B di AJO](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/home).

**Nota:** la logica dei percorsi suddivisi nel percorso utilizza i dati di profilo e, se supportati, i dati relazionali; assicurati che i campi necessari per la logica delle cascate siano disponibili nel percorso.

### Guardrail

- **Journey Optimizer B2B edition** — Per informazioni sui limiti di percorso, sui limiti dei nodi e sul supporto della destinazione, vedere la [descrizione del prodotto](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer-b2b.html).
- **Real-Time CDP** — Consulta [Guardrail di RTCDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/guardrails/overview) per i limiti di segmentazione e attivazione.

## Implementazione

I passaggi seguenti forniscono indicazioni per l’implementazione di Paid Media Controller con AJO B2B e AEP.

### Passaggi preliminari

1. **Definire il pubblico dell&#39;account e il modello dati in Real-Time CDP B2B.**

   Creare il **pubblico con account qualificati** (ad esempio, &quot;Account idonei per contenuti multimediali a pagamento&quot;) che entrerà nel percorso di controller. Utilizza Segment Builder (Generatore di segmenti) e gli attributi account/persona che definiscono l’idoneità (ad esempio, area geografica, segmento, stato MQA). Questo pubblico è il singolo punto di ingresso per il percorso.

2. **Definire la gerarchia della campagna e la logica di suddivisione.**

   Documenta l’ordine delle cascate (ad esempio, Perseguimento → Persona → Categoria → Fondamentale → Soluzione) e le condizioni per ciascun percorso (quali attributi o tipi di pubblico qualificano un account). Assicurati che le condizioni siano **reciprocamente esclusive nell&#39;ordine** (dall&#39;alto verso il basso): un account deve corrispondere al massimo a un percorso, il primo che valuta true.

3. **Configurare le destinazioni.**

   Imposta le destinazioni di media a pagamento (ad esempio, tipi di pubblico abbinati a LinkedIn) in AEP/RTCDP e assicurati che siano disponibili per l’attivazione da AJO B2B. Mappa gli identificatori dei conti ed eventuali attributi richiesti per ciascuna destinazione.

### Configurazione controller di supporti a pagamento

1. **Creare il percorso di controller in AJO B2B.**

   - **Read audience:** Seleziona il pubblico dell&#39;account qualificato da Real-Time CDP.
   - **Dividi percorso:** Crea un percorso per ogni pubblico di media a pagamento, partendo dal percorso 1 come priorità principale e procedendo in ordine di priorità. Per ogni percorso, aggiungi gli attributi per impostare i criteri di qualifica (ad esempio, &quot;in Pursuit audience&quot;, &quot;solution interest = X&quot;, &quot;persona = Y&quot;, &quot;intent category = Z&quot;). Gli account valutano attraverso il nodo del percorso di divisione come in cascata, qualificandosi per il primo percorso per il quale soddisfano i criteri.
   - **Attiva nella destinazione:** Per ogni percorso, aggiungere un nodo Attiva nella destinazione alla campagna/destinazione LinkedIn (o di altro tipo) corretta.

2. **Convalidare l&#39;esclusività reciproca.**

   - Conferma che ogni account immette un solo percorso (la prima condizione corrispondente).
   - Verifica attivazione: gli account vengono visualizzati nella destinazione corretta e sono esclusi dalle campagne a priorità inferiore come previsto.

## Diagramma di implementazione

<img src="assets/ajo-b2b-paid-media-controller-canvas.svg" alt="Area di lavoro di AJO B2B Paid Media Controller" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

### Attivazione del pubblico

1. **Attiva in LinkedIn (e altre destinazioni).**

   Utilizza &quot;Activate to Destination&quot; (Attiva a destinazione) nel percorso per inviare ogni percorso al pubblico di file multimediali a pagamento giusto. Non viene eseguita alcuna esportazione o caricamento manuale degli elenchi; il percorso attiva l&#39;attivazione mentre gli account passano attraverso i percorsi.

2. **Monitora e ottimizza.**

   Utilizzare la generazione di rapporti di percorso per monitorare i volumi per percorso.

## Riepilogo

Il blueprint **Paid Media Controller** mostra come **AJO B2B e AEP** collaborino per offrire agli addetti al marketing B2B un unico modo automatico per assegnare account alle campagne e attivarli su supporti a pagamento: un pubblico principale, un percorso, logica di suddivisione delle cascate e attivazione diretta alle destinazioni, senza handoff manuali dell&#39;elenco. Stabilisce un pattern ripetibile per l’orchestrazione di contenuti multimediali B2B multicanale a pagamento e contribuisce a ridurre la sovrapposizione, migliorare la rilevanza e scalare le operazioni.

## Documentazione correlata

- [Blueprint per il marketing e la gestione dei Percorsi basato su gruppi di acquisto](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/b2b-activation/b2b-buying-group-journeys): percorsi di account e gruppi di acquisto in AJO B2B.
- [Adobe Journey Optimizer B2B edition](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b) — Documentazione del prodotto.
- [Real-time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) — Pubblico dell&#39;account e attivazione.
