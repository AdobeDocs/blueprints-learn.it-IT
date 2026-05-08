---
source-git-commit: 83e85d946e455cde46001af0a2112637b7fe24cc
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---
# Modello pagina diagramma architettura

Questo è il modello markdown completo per una pagina di diagramma dell’architettura. Sostituisci ogni `{placeholder}` con il valore raccolto durante la Fase 1 del flusso di lavoro abilità. Rimuovere eventuali sezioni facoltative non applicabili (ad esempio il blocco `>[!MORELIKETHIS]`). Non lasciare segnaposto vuoti nel file generato.

&#x200B;---

```markdown
---
title: {Page title}
description: {1-2 sentence page purpose, used for search snippets and previews}
solution: {Comma-separated Adobe solutions, e.g. Experience Platform, Journey Optimizer, Customer Journey Analytics}
---
# {Page title}

{Opening paragraph -- 1-2 sentences describing what the diagrams collectively illustrate. Frame the page as a top-level architecture reference, not a use case walkthrough.}

>[!MORELIKETHIS]
>
>[{Related-content link text}]({Related-content URL}).

## {Diagram 1 section title}

{1-2 sentence explanation of what the diagram shows and why it matters.}

<img src="assets/{filename-1}" alt="{Alt text for diagram 1}" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## {Diagram 2 section title}

{1-2 sentence explanation.}

<img src="assets/{filename-2}" alt="{Alt text for diagram 2}" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Primary data flows and integration points

- {Flow or integration 1 -- e.g., "Real-time event ingestion from [!DNL Web SDK] to [!DNL Edge Network]"}
- {Flow or integration 2 -- e.g., "Profile sync between [!DNL Experience Platform] Hub and Edge"}
- {Flow or integration 3}
- {Flow or integration 4}
- {Flow or integration 5}

## Use case patterns supported

The architecture above supports the following use case patterns:

- [{Pattern 1 name}](/help/blueprints/use-case-patterns/{category}/{pattern-1-file}.md) -- {1-line note on why this architecture enables the pattern}
- [{Pattern 2 name}](/help/blueprints/use-case-patterns/{category}/{pattern-2-file}.md) -- {1-line note}
- [{Pattern 3 name}](/help/blueprints/use-case-patterns/{category}/{pattern-3-file}.md) -- {1-line note}

## Further reading

- [{Article 1 title}]({Experience League URL 1})
- [{Article 2 title}]({Experience League URL 2})
- [{Article 3 title}]({Experience League URL 3})
```

&#x200B;---

## Regole sui contenuti

- **Campi obbligatori:** `title`, `description`, `solution`.
- **Campi non consentiti** (assegnati automaticamente all&#39;ora di pubblicazione): `exl-id`, `product_v2`, `feature_v2`, `role_v2`, `topic_v2`, `TQID`, `kt`, `thumbnail`. Non includerli nei file appena creati.

## Convenzioni corpo

- **Un H1** — titolo della pagina. Corrispondenza esatta con il frontmatter `title`.
- **Un H2 per diagramma.** Nessuna H3 all&#39;interno delle sezioni del diagramma; tienili ad un&#39;introduzione di 1-2 frasi più l&#39;immagine.
- **`<img>`incorporamento** — sono necessari lo stile in linea e `class="modal-image"`. Guidano l’interazione modale-zoom di Experience League.
- **Percorso immagine** - sempre `assets/{filename}` (relativo alla cartella argomenti della pagina). Non utilizzare percorsi assoluti.
- **Nomi di prodotti Adobe**: racchiudi `[!DNL ...]` nel corpo del testo e nei punti elenco. Esempio: `[!DNL Real-Time CDP]`, `[!DNL Journey Optimizer]`, `[!DNL Experience Platform]`.
- **Collegamenti ai pattern dei casi d&#39;uso**: utilizza sempre il modulo assoluto `/help/blueprints/use-case-patterns/{category}/{file}.md` in modo che il collegamento venga risolto da qualsiasi pagina che possa trascendere questo contenuto.
- **Collegamenti Experience League** — URL assoluti che iniziano con `https://experienceleague.adobe.com/`. Preferisci l’URL del documento canonico a una variante localizzata.

## Ordinamento sezioni

Mantieni l’ordine coerente in tutte le pagine dell’architettura in modo che i lettori possano eseguire la scansione in modo prevedibile:

1. Frontmatter
2. H1 + apertura paragrafo
3. (Facoltativo) `>[!MORELIKETHIS]` callout
4. Un H2 per diagramma (nell&#39;ordine specificato dall&#39;utente)
5. `## Use case patterns supported`
6. `## Primary data flows and integration points`
7. `## Further reading`

## Aspettative di lunghezza

40-100 righe di markdown sono tipiche. Se la pagina supera le 150 righe, è probabile che il contenuto si sia spostato nel territorio del modello del caso d&#39;uso. Ricontrollare `scope-guardrails.md` e considerare la suddivisione.
