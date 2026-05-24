---
source-git-commit: e79d9d6490e4f50c4611dd879b53f0e63a90cd65
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 81%

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

This guide provides a comprehensive implementation blueprint for {{pattern name}} using {{solutions with [!DNL ...] formatting}}. It is designed for solution architects, marketing technologists, and implementation engineers who need to {{primary capability description}}.

Use this guide to understand what to configure, where implementation choices exist, and what trade-offs drive each decision.

{{Optional: 1-2 additional introductory sentences about what the guide covers.}}

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

## Use case pattern

**{{Pattern Name}}**

{{One-sentence description of what the pattern does.}}

**Execution Plan:** {{Step 1}} > {{Step 2}} > {{Step 3}} > {{Step 4}} > {{Step 5}}

## Applications

The following Adobe applications are used in this use case pattern.

- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}
- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}
- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}

## Foundational capabilities

The following foundational capabilities must be configured before implementing this pattern. Each capability represents a prerequisite or assumed platform capability.

| Foundational Capability | Status | What Must Be in Place | Experience League Reference |
| --- | --- | --- | --- |
| {{Capability name}} | {{Required / Assumed in Place / Not Applicable}} | {{Description of what must be configured or available}} | [{{Link text}}]({{URL}}) |
| {{Capability name}} | {{Required / Assumed in Place / Not Applicable}} | {{Description}} | [{{Link text}}]({{URL}}) |
| {{Capability name}} | {{Required / Assumed in Place / Not Applicable}} | {{Description}} | [{{Link text}}]({{URL}}) |
| {{Capability name}} | {{Required / Assumed in Place / Not Applicable}} | {{Description}} | [{{Link text}}]({{URL}}) |

## Supporting capabilities

The following supporting capabilities enhance or extend the pattern but are not strictly required for a basic implementation.

| Supporting Capability | Status | Why It Matters | Experience League Reference |
| --- | --- | --- | --- |
| {{Capability name}} | {{Recommended / Included / Not Applicable}} | {{Description of why this capability matters for this pattern}} | [{{Link text}}]({{URL}}) |
| {{Capability name}} | {{Recommended / Included / Not Applicable}} | {{Description}} | [{{Link text}}]({{URL}}) |
| {{Capability name}} | {{Recommended / Included / Not Applicable}} | {{Description}} | [{{Link text}}]({{URL}}) |

## Application capabilities

### [!DNL {{Application Name}}] ({{Abbreviation}})

| Capability | Implementation Phase | Description |
| --- | --- | --- |
| {{Capability name}} | {{Phase name (e.g., Setup, Configuration, Activation, Optimization)}} | {{Description of what this capability does in context}} |
| {{Capability name}} | {{Phase name}} | {{Description}} |
| {{Capability name}} | {{Phase name}} | {{Description}} |

### [!DNL {{Application Name}}] ({{Abbreviation}})

| Capability | Implementation Phase | Description |
| --- | --- | --- |
| {{Capability name}} | {{Phase name}} | {{Description}} |
| {{Capability name}} | {{Phase name}} | {{Description}} |
| {{Capability name}} | {{Phase name}} | {{Description}} |

{{Repeat for each application listed in the Applications section.}}

## Prerequisites

Complete the following before beginning the implementation.

- [ ] {{Prerequisite item -- e.g., "XDM schemas for behavioral and profile data are defined and deployed"}}
- [ ] {{Prerequisite item -- e.g., "Datastreams are configured for web and/or mobile properties"}}
- [ ] {{Prerequisite item -- e.g., "Identity namespaces are defined and identity resolution rules are configured"}}
- [ ] {{Prerequisite item -- e.g., "Merge policies are configured for the target profile dataset"}}
- [ ] {{Prerequisite item -- e.g., "Required Adobe product licenses are provisioned and sandbox access is granted"}}
- [ ] {{Prerequisite item}}

## Implementation options

### Option A: {{Option name}}

**Best for:** {{One-sentence description of when to use this option}}

**How it works:**

{{Paragraph 1: Describe the overall approach and architecture of this option.}}

{{Paragraph 2: Describe the key configuration steps or workflow.}}

{{Paragraph 3 (optional): Describe any runtime behavior or execution model.}}

{{Paragraph 4 (optional): Describe monitoring, reporting, or optimization considerations.}}

**Key considerations:**

- {{Consideration about timing, latency, or throughput}}
- {{Consideration about data requirements or dependencies}}
- {{Consideration about channel support or limitations}}
- {{Consideration about governance or compliance}}

**Advantages:**

- {{Advantage of this approach}}
- {{Advantage of this approach}}
- {{Advantage of this approach}}

**Limitations:**

- {{Limitation or trade-off}}
- {{Limitation or trade-off}}
- {{Limitation or trade-off}}

**Experience League:**

- [{{Link text}}]({{URL}})
- [{{Link text}}]({{URL}})

### Option B: {{Option name}}

**Best for:** {{One-sentence description of when to use this option}}

**How it works:**

{{Paragraph 1: Describe the overall approach and architecture of this option.}}

{{Paragraph 2: Describe the key configuration steps or workflow.}}

**Key considerations:**

- {{Consideration}}
- {{Consideration}}

**Advantages:**

- {{Advantage}}
- {{Advantage}}

**Limitations:**

- {{Limitation}}
- {{Limitation}}

**Experience League:**

- [{{Link text}}]({{URL}})

{{Repeat for Options C, D as needed. Include 2-4 options total.}}

### Option comparison

| Criteria | Option A | Option B | Option C |
| --- | --- | --- | --- |
| Best for | {{description}} | {{description}} | {{description}} |
| Complexity | {{Low / Medium / High}} | {{Low / Medium / High}} | {{Low / Medium / High}} |
| Time to value | {{Fast / Moderate / Slow}} | {{Fast / Moderate / Slow}} | {{Fast / Moderate / Slow}} |
| Channel support | {{description}} | {{description}} | {{description}} |
| Personalization depth | {{description}} | {{description}} | {{description}} |
| Scalability | {{description}} | {{description}} | {{description}} |
````

---

## Note sull&#39;utilizzo di questo modello

- **Questione anteriore YAML:** `exl-id` deve essere un UUID segnaposto (ad esempio, `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`). La pipeline di pubblicazione assegna il valore reale.
- **Nomi prodotti Adobe:** Utilizza sempre la sintassi `[!DNL ...]` per i nomi prodotti Adobe nel corpo del testo e nelle tabelle (ad esempio, `[!DNL Journey Optimizer]`). Si tratta di una convenzione Experience League che impedisce la traduzione dei nomi dei prodotti.
- **Collegamenti obiettivi aziendali:** Utilizzare percorsi relativi dal file di pattern alla directory obiettivi aziendali: `../../business-objectives/{{category}}/{{filename}}.md`.
- **Nomi di file con maiuscole/minuscole:** Il nome del file del modello deve essere con maiuscole/minuscole derivato dal titolo del modello. Esempio: &quot;Messaggi attivati da eventi&quot; diventa `event-triggered-messaging.md`.
- **Piano di esecuzione:** Utilizzare ` > ` (spazio, maggiore di, spazio) come separatore tra i passaggi.
- **Valori di stato:** Le funzionalità fondamentali utilizzano: Obbligatorio, Presunto nella posizione, Non applicabile. Utilizzo delle funzionalità di supporto: Consigliato, Incluso, Non applicabile.
- **Fasi di implementazione:** I nomi comuni delle fasi includono: Configurazione, Configurazione, Attivazione, Ottimizzazione, Monitoraggio.
- **Prerequisiti:** Utilizzare la sintassi della casella di controllo `- [ ]` per ogni elemento.
