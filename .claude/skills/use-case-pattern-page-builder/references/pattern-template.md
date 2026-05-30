---
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 48%

---
# Modello di pattern del caso d’uso

Questo file contiene il modello markdown completo per una pagina con pattern di use case. Sostituisci tutti i valori `{{placeholder}}` con il contenuto effettivo durante la generazione di un nuovo modello.

---

## Modello

````markdown
---
title: {{Pattern Title}}
description: {{One-sentence description of what this pattern teaches}}
solution: {{Comma-separated Adobe solutions}}
exl-id: {{generate-uuid-placeholder}}
---
# {{Pattern title}}

This guide provides an overview of {{pattern name}} using {{solutions with [!DNL ...] formatting}}. It is designed for solution architects, marketing technologists, and implementation engineers who need to {{primary capability description}}.

## Use case pattern

**{{Pattern Name}}**

{{One-two sentence description of what the pattern does and enables.}}

**Execution plan:** {{Step 1}} > {{Step 2}} > {{Step 3}} > {{Step 4}} > {{Step 5}}

## Use case overview

{{Paragraph 1: Define the pattern. What does it do? How does it differ from related patterns? Provide a clear, specific definition.}}

{{Paragraph 2: Describe the typical trigger or starting condition. When does this pattern apply? What event, schedule, or condition initiates it?}}

{{Paragraph 3: Describe what the pattern delivers. What is the end result for the customer or business? What channels or touchpoints does it affect?}}

{{Paragraph 4: Clarify scope boundaries. What does this pattern NOT cover? What adjacent patterns handle those needs? Reference other patterns by name if relevant.}}

{{Paragraph 5 (optional): Identify typical stakeholders and teams involved in implementation. Who owns what?}}

## Key business objectives

The following business objectives are supported by this use case pattern.

**[{{Objective Name}}](../../business-objectives/{{category}}/{{objective-file}}.md)**

{{Brief description of how this pattern supports the objective -- 1-2 sentences.}}

| KPIs |
| --- |
| {{KPI1}}, {{KPI2}}, {{KPI3}} |

{{Repeat the above block for each supported business objective.}}

## Example tactical use cases

The following scenarios illustrate how {{pattern name}} can be applied across different business contexts.

- **{{Scenario name}}** -- {{Description of the scenario and how it uses this pattern}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
{{Include 6-10 scenarios total}}

## Key performance indicators

| KPI | Description | Measurement |
| --- | --- | --- |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |

## Applications

The following Adobe applications are used in this use case pattern.

- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}
- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}
- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}

## Related documentation

The following resources provide additional detail on the capabilities used in this pattern. Group the reference links to primary Experience League documents under descriptive subheadings.

### {{Topic group}}

- [{{Link text}}]({{URL}})
- [{{Link text}}]({{URL}})

### {{Topic group}}

- [{{Link text}}]({{URL}})
- [{{Link text}}]({{URL}})
````

---

## Note sull&#39;utilizzo di questo modello

- **Questione anteriore YAML:** `exl-id` deve essere un UUID segnaposto (ad esempio, `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`). La pipeline di pubblicazione assegna il valore reale.
- **Ordine sezioni:** La sezione `Use case pattern` viene immediatamente dopo l&#39;introduzione di apertura, prima di `Use case overview`. Offre ai lettori una definizione chiara e univoca e un piano di esecuzione di alto livello.
- **Nomi prodotti Adobe:** Utilizza sempre la sintassi `[!DNL ...]` per i nomi prodotti Adobe nel corpo del testo e nelle tabelle (ad esempio, `[!DNL Journey Optimizer]`). Si tratta di una convenzione Experience League che impedisce la traduzione dei nomi dei prodotti.
- **Collegamenti obiettivi aziendali:** Utilizzare percorsi relativi dal file di pattern alla directory obiettivi aziendali: `../../business-objectives/{{category}}/{{filename}}.md`.
- **Nomi di file con maiuscole/minuscole:** Il nome del file del modello deve essere con maiuscole/minuscole derivato dal titolo del modello. Esempio: &quot;Messaggi attivati da eventi&quot; diventa `event-triggered-messaging.md`.
- **Piano di esecuzione:** Utilizzare ` > ` (spazio, maggiore di, spazio) come separatore tra i passaggi. Mantieni l&#39;etichetta esattamente `**Execution plan:**`.
- **Documentazione correlata:** collegamenti di riferimento al gruppo nei sottotitoli descrittivi `###` (ad esempio, per applicazione o area funzionalità). Questi sono i riferimenti di Experience League per le applicazioni e le funzionalità utilizzate nel modello.
- **Architettura (facoltativa):** Se un modello beneficia di un diagramma di architettura di riferimento, è possibile inserire una sezione `## Architecture` facoltativa tra `Applications` e `Related documentation`.
- **Ambito:** Questo modello esclude intenzionalmente sezioni di implementazione dettagliate (funzionalità di base/supporto/applicazione, prerequisiti, opzioni di implementazione e passaggi di implementazione graduali). Questi dettagli sono presenti nella documentazione di Experience League collegata da `Related documentation`.