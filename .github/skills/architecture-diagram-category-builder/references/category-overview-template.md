---
source-git-commit: e0ecfa4d74b8fcc0bbaf35d44c33c725a1b1a539
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%
---
# Modello overview.md categoria

Ogni cartella delle categorie in `help/blueprints/architecture-diagrams/` ha bisogno di un `overview.md` simile agli altri cinque. Utilizza questa struttura esatta.

## Frontmatter

```yaml
---
title: {Category Label}
description: {One-sentence summary of what this category covers.}
solution: {Primary Adobe solution(s), comma-separated}
doc-type: overview-page
---
```

Non includere `exl-id`, `product_v2`, `feature_v2`, `role_v2`, `topic_v2`, `TQID`, `kt` o `thumbnail` in una nuova pagina. La pipeline di pubblicazione compila automaticamente questi elementi.

## Corpo

```markdown
# {Category Label}

{1-3 paragraph intro describing what this category of diagrams covers and why it matters.}

| Diagram | Description |
| --- | --- |
| [{Page title}]({filename}.md) | {One-sentence description of the page} |
| [{Page title}]({filename}.md) | {One-sentence description of the page} |
```

Regole:

- Elencare tutte le pagine della categoria nello stesso ordine in cui vengono visualizzate nel sommario.
- Le destinazioni di collegamento sono nomi di file relativi (nessun prefisso `/help/blueprints/...`), poiché la panoramica si trova accanto alle relative pagine di pari livello.
- Le descrizioni sono una frase, non è necessario un periodo finale se si legge come un&#39;etichetta.
- Se una categoria ha un raggruppamento secondario naturale (ad esempio, &quot;Diagrammi obsoleti&quot; in percorsi di clienti), aggiungi un’intestazione `## {Sub-group name}` seguita dalla tabella a due colonne nello stesso formato. Non combinare miniature di diagrammi o colonne aggiuntive nella tabella.
- Non incorporare le miniature del diagramma `<img>` in questa tabella. Mantenerlo su due colonne: `Diagram` (collegamento) e `Description` (testo). Le miniature appartengono alle singole pagine di contenuto, non alla panoramica della categoria.
- Non utilizzare HTML `<ul><li>` nidificato all&#39;interno di celle di tabella. Solo testo normale.

## Esempio (Customer Insights)

```markdown
---
title: Customer Insights
description: Unify and analyze data and customer behaviors from across the customer journey
solution: Customer Journey Analytics
doc-type: overview-page
---
# Customer Insights

Customer Journey Analytics shows how brands can unify customer data and behavior from various interaction channels and sources to create a journey-based view of all customer interactions.

| Diagram | Description |
| --- | --- |
| [Adobe Customer Journey Analytics](cja.md) | Core Customer Journey Analytics architecture, including B2B and audience-sharing derivations |
| [Adobe Customer Journey Analytics & Adobe Journey Optimizer integration](cja-ajo-integration.md) | Campaign and journey insights integration between Customer Journey Analytics and Journey Optimizer |
```
