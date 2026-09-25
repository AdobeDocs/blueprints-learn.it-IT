---
source-git-commit: c766cd3153efce4635089d008daf3eb426eb7a24
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%
---
# Riferimento di posizionamento TOC.md

Quando l&#39;abilità genera una nuova pagina di diagramma architettura, deve aggiungere una voce a `/help/blueprints/TOC.md` in modo che la pagina sia individuabile nella navigazione del sito. Questo documento definisce esattamente dove e come va la voce.

## Sezione padre

Tutte le pagine del diagramma dell&#39;architettura si trovano nella sezione `+ Architecture Diagrams and Blueprints{#architecture-diagrams}` di primo livello in TOC.md. All’interno di tale sezione, diverse sottosezioni raggruppano le pagine per argomento.

I nomi delle cartelle, gli ancoraggi del sommario e le etichette del sommario per queste sottosezioni devono seguire la regola di denominazione in `../../architecture-diagram-category-builder/references/naming-conventions.md`. Vedere il file se è necessaria una nuova categoria (utilizzare l&#39;abilità `architecture-diagram-category-builder` per tale categoria, non questa).

## Mappatura sottosezione

Selezionare la sottosezione corrispondente alla cartella degli argomenti della nuova pagina:

| Cartella argomenti | Titolo sottosezione sommario |
| --- | --- |
| `architecture-diagrams/architecture-overviews/` | `+ Architecture overviews{#architecture-overviews}` |
| `architecture-diagrams/audience-profile-activation/` | `+ Audience & Profile Activation{#audience-profile-activation}` |
| `architecture-diagrams/b2b-activation-marketing/` | `+ B2B activation & marketing{#b2b-activation-marketing}` |
| `architecture-diagrams/customer-insights/` | `+ Customer Insights{#customer-insights}` |
| `architecture-diagrams/customer-journeys/` | `+ Customer journeys{#customer-journeys}` |

Se l&#39;utente propone una cartella di argomenti che non si trova in questa tabella, considerarla come una nuova sottosezione di livello superiore e sospendere l&#39;operazione. Chiedere all&#39;utente di confermare se crearla. Non inventare silenziosamente una nuova sottosezione.

## Formato di ingresso

```
    + [{Page title}](/help/blueprints/{topic-folder}/{filename}.md)
```

Regole:

- **Rientro:** esattamente quattro spazi, quindi `+ `. Il parser del sommario dipende da questo; tabulazioni o spaziatura diversa interrompono la navigazione.
- **Testo collegamento:** il titolo della pagina, corrispondente esattamente a `title`. Utilizzare `[!DNL ...]` solo se gli elementi di pari livello esistenti nella stessa sottosezione lo utilizzano, ovvero se corrispondono alla convenzione locale.
- **Destinazione collegamento:** percorso assoluto che inizia con `/help/blueprints/`. Includi sempre l&#39;estensione `.md`.
- **Posizione:** aggiungere come ultima voce nella sottosezione corrispondente a meno che l&#39;utente non specifichi una posizione diversa. Mantenere l&#39;ordine esistente di tutte le voci di pari livello.

## Sottosezioni nidificate

`+ Architecture overviews{#architecture-overviews}` non ha raggruppamenti nidificati. Tutte le pagine in `architecture-diagrams/architecture-overviews/` (incluse le pagine di distribuzione di SDK, ad esempio `websdk.md`, `appsdk.md`) si trovano allo stesso livello di rientro a quattro spazi. Altre sottosezioni (`Audience & Profile Activation`, `B2B activation & marketing`, ecc.) può contenere ancora raggruppamenti nidificati — ispezionate la sezione prima di inserire la voce. Se è presente un raggruppamento nidificato e la nuova pagina vi appartiene, applica un rientro a due spazi aggiuntivi; in caso contrario, posiziona la voce al livello superiore della sottosezione.

## Esempi di lavoro

### Esempio 1: pagina AEP di primo livello

- Cartella argomenti: `architecture-diagrams/architecture-overviews/`
- Nome file: `mix-modeler-integration.md`
- Titolo pagina: `Adobe Mix Modeler integration with Experience Platform`

Voce:

```
    + [Adobe Mix Modeler integration with Experience Platform](/help/blueprints/architecture-diagrams/architecture-overviews/mix-modeler-integration.md)
```

Inserito in `+ Architecture overviews{#architecture-overviews}`.

### Esempio 2 — Architettura di percorso AJO

- Cartella argomenti: `architecture-diagrams/customer-journeys/`
- Nome file: `cross-channel-journey-architecture.md`
- Titolo pagina: `Cross-channel journey architecture`

Voce:

```
    + [Cross-channel journey architecture](/help/blueprints/architecture-diagrams/customer-journeys/cross-channel-journey-architecture.md)
```

Inserito in `+ Customer journeys{#customer-journeys}`.

### Esempio 3: pagina Distribuzione di SDK

- Cartella argomenti: `architecture-diagrams/architecture-overviews/`
- Nome file: `mobile-sdk-architecture.md`
- Titolo pagina: `Mobile SDK deployment architecture`

Immissione (stesso rientro di quattro spazi delle altre pagine di panoramica dell’architettura):

```
    + [Mobile SDK deployment architecture](/help/blueprints/architecture-diagrams/architecture-overviews/mobile-sdk-architecture.md)
```

Inserito in `+ Architecture overviews{#architecture-overviews}`.

## Verifica

Dopo aver modificato TOC.md, rileggi la sottosezione interessata e conferma:

1. La nuova voce utilizza esattamente quattro spazi di rientro (o sei se nidificata sotto un raggruppamento specifico della sottosezione, ad esempio il raggruppamento RTCDP di `Audience & Profile Activation`).
2. La destinazione del collegamento corrisponde al percorso del file sul disco, inclusa l&#39;estensione `.md`.
3. La voce è raggruppata all&#39;interno della sottosezione corretta, non fluttuando tra le sottosezioni.
4. Nessuna voce esistente è stata riordinata o modificata.
