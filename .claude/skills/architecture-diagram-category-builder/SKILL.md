---
name: architecture-diagram-category-builder
description: 'Guida alla creazione di una nuova categoria di livello principale (sottosezione) in Diagrammi architettura e blueprint nell’archivio dei blueprint di Adobe Experience Platform. Utilizza questa abilità quando un diagramma dell’architettura proposto non rientra in nessuna delle categorie esistenti (panoramiche dell’architettura, attivazione di tipi di pubblico e profili, attivazione e marketing B2B, approfondimenti sul cliente, percorsi di clienti) ed è necessario crearne una nuova. Gestisce l’intero flusso di lavoro: conferma che una nuova categoria sia effettivamente giustificata, applicazione delle convenzioni di denominazione di cartelle/ancoraggi, creazione della struttura delle cartelle e della pagina di destinazione overview.md, aggiunta della sottosezione TOC.md e aggiornamento della griglia della scheda della pagina di destinazione dei diagrammi dell’architettura. Per aggiungere una pagina a una categoria *esistente*, utilizza invece architecture-diagram-page-builder.'
source-git-commit: c766cd3153efce4635089d008daf3eb426eb7a24
workflow-type: tm+mt
source-wordcount: '1062'
ht-degree: 0%
---

# Generatore categorie diagramma architettura

Questa abilità guida la creazione di una nuova categoria di primo livello in `+ Architecture Diagrams and Blueprints{#architecture-diagrams}` in `/help/blueprints/TOC.md`. Una categoria è una cartella come `customer-insights/` o `b2b-activation-marketing/`, ovvero un gruppo di pagine di diagramma dell&#39;architettura correlate con la propria pagina di destinazione `overview.md` e la propria sottosezione del sommario.

**Operazione rara.** Ci sono cinque categorie oggi. L&#39;aggiunta di un sesto dominio dovrebbe avvenire solo quando un dominio veramente nuovo di contenuto dell&#39;architettura non si adatta a quello esistente, non come scorciatoia per evitare di organizzare una pagina sotto una categoria esistente.

## Lettura richiesta prima dell&#39;avvio

- `./references/naming-conventions.md`: la regola di denominazione della cartella, dell&#39;ancoraggio o dell&#39;etichetta e il motivo per cui è importante. Leggi tutto questo; è l&#39;unica fonte di verità per come le categorie devono essere denominate.
- `./references/category-overview-template.md`: la struttura esatta richiesta per il `overview.md` della nuova categoria.
- Se non lo hai già fatto, esegui anche lo skim di `../architecture-diagram-page-builder/SKILL.md`: una volta che la categoria esiste, le singole pagine al suo interno vengono aggiunte utilizzando tale abilità, non questa.

## Fase 1: conferma della necessità di una nuova categoria

Prima di procedere, elenca all’utente le cinque categorie esistenti e il relativo ambito:

| Categoria | Cartella | Ambito |
| --- | --- | --- |
| Panoramiche dell’architettura | `architecture-overviews/` | Architettura Experience Cloud / Experience Platform di livello superiore, guardrail, SDK di implementazione |
| Attivazione in base a pubblico e profili | `audience-profile-activation/` | Creazione e attivazione di tipi di pubblico/profili tramite Real-Time CDP e Audience Manager |
| Attivazione e marketing B2B | `b2b-activation-marketing/` | Attivazione basata su account, percorsi di acquisto, Marketo/Workfront |
| Informazioni sul cliente | `customer-insights/` | Customer Journey Analytics e le sue integrazioni |
| Percorsi di clienti | `customer-journeys/` | Journey Optimizer, Gestione delle decisioni, Campaign v7/v8 |

Chiedi all’utente di confermare che il contenuto proposto non rientri in nessuno di questi. Se si tratta di un&#39;operazione simile (ad esempio, un nuovo diagramma B2B o un nuovo diagramma di personalizzazione), eseguire il reindirizzamento a `architecture-diagram-page-builder` per la categoria esistente anziché crearne una nuova. Procedi alla fase 2 solo se l’utente conferma che è giustificata una categoria veramente nuova.

## Fase 2: raccogliere le informazioni sulla categoria

Utilizza un modulo di domanda per raccogliere in un unico passaggio:

1. **Etichetta categoria**: l&#39;etichetta TOC completa e leggibile (ad esempio &quot;Architettura di Commerce&quot;, non un&#39;abbreviazione). Presenti 2-3 frasi suggerite più &quot;Altro&quot;.
2. **Descrizione in una sola frase**: ciò che riguarda questa categoria, per la scheda della pagina di destinazione e del frontmatter di `overview.md`.
3. **Soluzioni Adobe primarie** per il campo `solution` di frontmatter.
4. **Pagine iniziali** — l&#39;utente dispone già di più di 1 pagina da inserire in questa categoria o la categoria è appena stata scaffolding per le pagine da seguire in un secondo momento?

Derivare il nome della cartella e l&#39;ancoraggio dall&#39;etichetta della categoria utilizzando la regola del margine in `./references/naming-conventions.md` (minuscolo, rilascio di `&`, sillabazione, nessuna abbreviazione). Mostrare all&#39;utente la cartella/ancoraggio derivata e confermare prima di procedere: questo è il dettaglio che è costoso da correggere in un secondo momento.

## Fase 3: creare la struttura delle cartelle

```
help/blueprints/architecture-diagrams/{new-folder}/
help/blueprints/architecture-diagrams/{new-folder}/assets/
help/blueprints/architecture-diagrams/{new-folder}/overview.md
```

Genera `overview.md` utilizzando `./references/category-overview-template.md`. Se l&#39;utente dispone di pagine iniziali pronte, elencarle nella tabella (utilizzando `architecture-diagram-page-builder` per generare direttamente i file di pagina. Questa abilità crea solo lo scaffold delle categorie e la relativa pagina di panoramica, non le singole pagine di diagramma). Se non esiste ancora alcuna pagina, la tabella potrebbe essere vuota o omessa fino all&#39;aggiunta della prima pagina. Tenere presente questo aspetto per l&#39;utente anziché inventare righe segnaposto.

La cartella `assets/` può essere vuota al momento della creazione; esiste in modo che la prima pagina di diagramma aggiunta alla categoria disponga di un punto in cui inserire le immagini.

## Fase 4: Aggiungere la sottosezione TOC.md

Inserire la nuova categoria come voce di primo livello in `+ Architecture Diagrams and Blueprints{#architecture-diagrams}`, posizionata dopo l&#39;ultima categoria esistente, a meno che l&#39;utente non specifichi diversamente:

```
  + {Category Label}{#{folder-slug}}
    + [Overview](/help/blueprints/architecture-diagrams/{new-folder}/overview.md)
    + [{Page title}](/help/blueprints/architecture-diagrams/{new-folder}/{filename}.md)
```

Regole:

- Rientro a 2 spazi per l’intestazione della categoria, corrispondente agli altri cinque.
- L&#39;ancoraggio `{#{folder-slug}}` deve essere esattamente uguale al nome della cartella (vedere naming-convention.md).
- `+ [Overview]` è sempre la prima voce, con un rientro di 4 spazi, prima di qualsiasi pagina di contenuto.
- Mantenere l&#39;ordine e il contenuto esistenti di tutte le altre voci di TOC.md: consente di inserire, non riordinare e non riscrivere sezioni non correlate.

## Fase 5: aggiornare la pagina di destinazione dei diagrammi dell’architettura e delle blueprint

Aggiungere una nuova scheda a `help/blueprints/architecture-diagrams/overview.md`, nella stessa griglia `<table style="table-layout:fixed; width:100%;">` utilizzata dalle altre cinque schede. La nuova scheda:

- Collegamenti a `{new-folder}/overview.md`.
- Utilizza una miniatura di diagramma rappresentativa da `{new-folder}/assets/` (o una nota segnaposto neutra se non esiste ancora alcun diagramma; segnalalo all&#39;utente anziché inventare un percorso immagine).
- Utilizza lo stesso blocco di stile in linea delle schede esistenti (`width:100%; height:160px; object-fit:contain; background-color:#ffffff; border:1px solid #d3d3d3; padding:10px; box-sizing:border-box;` sull&#39;immagine, `min-height:100px;` sul div di testo).

**Ricalcola il layout della griglia.** Le cinque schede esistenti riempiono una griglia a 3 colonne (due righe, una cella vuota finale). L&#39;aggiunta di una sesta scheda riempie esattamente la cella vuota, senza alcuna modifica del layout. Se si tratta della settima, ottava e così via categoria, aggiungi un nuovo `<tr>` con le nuove schede e tampona le celle vuote rimanenti nella riga con `<td style="width:33%; ...;"></td>` elementi vuoti in modo che la riga non venga frammentata.

## Fase 6: Convalida

Conferma e segnala all’utente:

1. **Coerenza dei nomi** - Il nome della cartella, l&#39;ancoraggio del sommario e il margine dell&#39;etichetta della categoria sono identici (per naming-convention.md).
2. **struttura overview.md** — corrisponde a `category-overview-template.md` (intro + tabella `Diagram | Description` a due colonne, nessuna immagine incorporata o elenco nidificato nella tabella).
3. **Posizionamento TOC.md**: la nuova sottosezione si trova in Architettura, Diagrammi e blueprint, `+ [Overview]` è il primo, il rientro è corretto, nessun&#39;altra voce è stata modificata.
4. **Scheda della pagina di destinazione** — aggiunta nella posizione corretta della griglia, utilizza lo stile di scheda standard e i collegamenti al nuovo `overview.md`.
5. **Reindirizzamenti**: se questa categoria consolida o rinomina contenuti che in precedenza risiedevano altrove (raro per una categoria nuova di zecca, ma verifica), aggiungere voci a `redirects.csv` seguendo il formato `source,dest` esistente utilizzato per le precedenti ridenominazioni dei diagrammi architettura.

Correggi eventuali problemi di convalida prima di considerare il completamento dell’attività.

## Note

- Se l’utente rinomina in un secondo momento una categoria (etichetta, cartella o ancoraggio), si tratta di un’operazione di ridenominazione e non di una nuova categoria: segui la regola naming-convention.md per il nuovo nome, aggiorna ogni collegamento interno (TOC.md, entrambe le pagine di panoramica, i collegamenti relativi di pari livello, i documenti di abilità) e aggiungi le voci di reindirizzamento. Considerala allo stesso modo in cui le ridenominazioni delle categorie sono state gestite in precedenza in questo archivio: `git mv` la cartella, quindi una ricerca a livello di repository e la sostituzione dei vecchi moduli di percorso, mai una sostituzione di stringa globale cieca che potrebbe entrare in conflitto con URL esterni non correlati (ad esempio `experienceleague.adobe.com/docs/experience-platform/...` collegamenti alla documentazione del prodotto).
- Mantieni sincronizzate questa abilità e `architecture-diagram-page-builder`: se la tabella di mappatura della sottosezione in `references/toc-placement.md` di `architecture-diagram-page-builder` non elenca ancora la nuova categoria, aggiungila anche in questo caso.
