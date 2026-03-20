---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---
# Pagine da aggiornare quando si aggiunge un modello di caso d’uso

Quando viene creato un nuovo pattern di casi d’uso, è necessario aggiornare le pagine seguenti per garantire che sia individuabile e collegato correttamente.

## Aggiornamenti richiesti

### &#x200B;1. Sommario.md
- **File:** `/help/blueprints/TOC.md`
- **Azione:** Aggiungere una nuova voce nella sezione categoria corretta
- **Formato:** `    + [{{Pattern Title}}](/help/blueprints/use-case-patterns/{{category}}/{{filename}}.md)`
- **Posizione per categoria:**
   - Creazione e attivazione di tipi di pubblico: dopo la riga ~47 (dopo le voci esistenti in tale sezione)
   - Personalization: dopo la riga ~52
   - Gestione e orchestrazione delle campagne: dopo la riga ~58
   - Analisi: dopo la riga ~61
   - Esperienza conversazionale: dopo la riga ~63

#### Mappatura categoria-sommario

| Margine categoria | Intestazione sezione sommario | Ancoraggio |
| --- | --- | --- |
| `audience-building-activation` | `+ Audience Building & Activation` | `{#audience-building-activation}` |
| `personalization` | `+ Personalization` | `{#personalization-patterns}` |
| `campaign-management-orchestration` | `+ Campaign Management & Orchestration` | `{#campaign-orchestration-patterns}` |
| `analysis` | `+ Analysis` | `{#analysis-patterns}` |
| `conversational-experience` | `+ Conversational Experience` | `{#conversational-experience-patterns}` |

#### Regole di rientro

- Le intestazioni di categoria utilizzano due spazi + `+` (esempio: `  + Personalization{#personalization-patterns}`)
- Le voci del pattern utilizzano quattro spazi + `+` (ad esempio, `    + [Pattern Title](path)`)

### &#x200B;2. Panoramica dei modelli di casi d’uso
- **File:** `/help/blueprints/use-case-patterns/overview.md`
- **Azione:** Aggiungere una nuova riga alla tabella delle categorie corretta
- **Formato:** `| [{{Pattern Title}}]({{category}}/{{filename}}.md) | {{Primary capability description}} | [!DNL {{Solution1}}], [!DNL {{Solution2}}] |`
- **Categorie nella panoramica:**
   - Creazione e attivazione di tipi di pubblico (linea ~18)
   - Personalization (linea ~29)
   - Gestione e orchestrazione delle campagne (linea ~40)
   - Analisi (riga ~52)
   - Esperienza conversazionale (riga ~61)

#### Esempio di formato riga

```
| [Event-Triggered Messaging](campaign-management-orchestration/event-triggered-messaging.md) | Listen for a real-time behavioral or system event, then deliver a contextual message to the triggering profile | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
```

## Elenco di controllo convalida

- [ ] file markdown pattern creato nella directory categoria corretta
- [ ] Frontmatter include titolo, descrizione, soluzione ed exl-id
- [ ] voce TOC.md aggiunta nella categoria corretta
- [ ] riga di tabella Overview.md aggiunta nella categoria corretta
- [ ] Tutti i collegamenti agli obiettivi di business puntano a file esistenti
- [ Il file ] utilizza la convenzione di denominazione con maiuscole/minuscole
- [ ] Tutti i collegamenti Experience League sono URL validi
- [ I nomi di prodotto di Adobe ] utilizzano la sintassi `[!DNL ...]`
- [ La catena di funzioni ] utilizza il formato separatore ` > `
- [ Il file del modello ] include tutte le sezioni richieste (vedere pattern-template.md)
