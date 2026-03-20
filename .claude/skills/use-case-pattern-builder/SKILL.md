---
name: use-case-pattern-builder
description: 'Guida alla creazione di nuovi contenuti del modello di caso d’uso per l’archivio Adobe Experience Platform blueprint. Utilizza questa abilità quando aggiungi un nuovo pattern di casi d’uso, crei contenuti di guida all’implementazione o quando l’utente menziona l’aggiunta di pattern al sito blueprint. Gestisce l’intero flusso di lavoro: raccoglie informazioni sul modello, genera il file markdown con la struttura corretta del modello e aggiorna tutte le pagine di riferimenti incrociati (TOC.md, overview.md).'
source-git-commit: ed8928687806b619e95d8d320478d27c13722a80
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 0%

---


# Generatore di modelli di casi d’uso

Questa abilità guida la creazione di un nuovo pattern di casi d’uso per l’archivio dei blueprint di Adobe Experience Platform. Gestisce l’intero flusso di lavoro: raccoglie le informazioni sul modello dall’utente, genera il file di contenuto Markdown con la struttura corretta del modello e aggiorna tutte le pagine di riferimento incrociato in modo che il nuovo modello sia individuabile.

Prima di iniziare, leggi i seguenti file di riferimento per la struttura completa dei modelli e l’elenco di controllo delle pagine da aggiornare:

- `references/pattern-template.md` — modello markdown completo con valori segnaposto
- `references/pages-to-update.md` — elenco di controllo delle pagine che devono essere aggiornate quando si aggiunge un pattern

## Fase 1: Raccolta delle informazioni

Intervistare l&#39;utente per raccogliere tutte le informazioni necessarie prima di generare qualsiasi file. Chiedi quanto segue e non procedere alla generazione del contenuto finché ogni elemento non viene fornito o esplicitamente differito.

### Informazioni richieste

1. **Nome pattern**: titolo leggibile (ad esempio, &quot;Messaggistica attivata da eventi&quot;).

2. **Categoria** — Esattamente una delle seguenti:
   - `audience-building-activation`
   - `personalization`
   - `campaign-management-orchestration`
   - `analysis`
   - `conversational-experience`

3. **Descrizione della funzionalità primaria**: una singola frase che descrive le funzioni del modello (utilizzata nella tabella di panoramica e nella descrizione dell&#39;argomento).

4. **Soluzioni core di Adobe**: i prodotti Adobe centrali per questo modello. Scegli tra: Journey Optimizer, Real-Time Customer Data Platform, Experience Platform, Customer Journey Analytics, Brand Concierge, Journey Optimizer B2B edition, Real-Time CDP B2B edition o altri, a seconda delle necessità.

5. **Passaggi della catena di funzioni**: 3-6 fasi sequenziali che descrivono il flusso di esecuzione del modello, separate da `>`. Esempio: &quot;Acquisizione evento > Inserimento Percorso > Valutazione condizione > Consegna messaggio > Reporting&quot;.

6. **Obiettivi aziendali supportati**: uno o più obiettivi aziendali del set esistente in `/help/blueprints/business-objectives/`. Ciascuno deve includere il nome dell&#39;obiettivo, la sottocartella della categoria e il nome del file. Verifica che i file a cui si fa riferimento esistano prima di generare il contenuto.

7. **Casi d&#39;uso tattici di esempio** — 6-10 scenari puntati che descrivono come questo modello può essere applicato in contesti aziendali diversi. Ogni scenario deve avere un nome in grassetto seguito da una descrizione.

8. **KPI** — Tabella con tre colonne: KPI (nome), Descrizione (cosa viene misurato), Misurazione (formula o approccio).

9. **Opzioni di implementazione** — 2-4 opzioni di implementazione. Per ogni opzione, raccogli:
   - Nome opzione
   - Consigliato per (quando utilizzare questa opzione)
   - Come funziona (2-4 paragrafi)
   - Considerazioni chiave (elenco puntato)
   - Vantaggi (elenco puntato)
   - Limitazioni (elenco puntato)
   - Collegamenti Experience League (URL della documentazione pertinente)

### Facoltativo ma consigliato

- Paragrafi di panoramica del caso d’uso (3-5 paragrafi; se non forniti, estrapolali dalle altre informazioni)
- Elenco delle applicazioni con la descrizione del ruolo di ogni app Adobe
- Tabella delle funzioni fondamentali (Funzione, Stato, Requisiti, Riferimento Experience League)
- Tabella delle funzioni di supporto (Funzione, Stato, Perché è importante, Riferimento Experience League)
- Tabelle delle funzioni dell’applicazione (una per applicazione, con funzione, fase di implementazione, descrizione)
- Elenco di controllo dei prerequisiti

Se l&#39;utente non fornisce gli elementi facoltativi, generare valori predefiniti ragionevoli in base alla categoria di pattern, alle soluzioni e alla catena di funzioni.

## Fase 2: Generazione dei contenuti

Generate il file markdown pattern nel percorso seguente:

```
/help/blueprints/use-case-patterns/{category}/{kebab-case-pattern-name}.md
```

Il nome del file deve utilizzare kebab-case derivato dal nome del pattern. Ad esempio, &quot;Messaggi attivati da eventi&quot; diventa `event-triggered-messaging.md`.

Utilizzare il modello da `references/pattern-template.md` e inserire tutti i valori segnaposto con le informazioni raccolte. Il file generato deve includere ogni sezione del modello:

1. **Materiale di prima istanza YAML** — titolo, descrizione, soluzione (separato da virgole), exl-id (genera un segnaposto UUID come `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx` — il team di pubblicazione assegnerà quello reale).

2. **Apertura dell&#39;intestazione** - `# {Pattern name}` seguita da un paragrafo introduttivo e dal messaggio &quot;Utilizzare questa guida per comprendere...&quot; frase.

3. **Panoramica sul caso d&#39;uso** — 3-5 paragrafi che descrivono l&#39;ambito del pattern, quando viene applicato, quali operazioni vengono eseguite e quali no e quali sono le parti interessate tipiche.

4. **Obiettivi aziendali chiave**: ogni obiettivo come intestazione collegata con una breve descrizione e una riga di riepilogo dei KPI.

5. **Casi d&#39;uso tattici di esempio** — Elenco puntato di 6-10 scenari.

6. **Indicatori prestazioni chiave** — Tabella con colonne KPI, Descrizione e Misurazione.

7. **Caso d&#39;uso** - Paragrafo di descrizione e catena di funzioni.

8. **Applicazioni** — Elenco di applicazioni Adobe con formattazione e descrizioni `[!DNL ...]`.

9. **Funzioni fondamentali** — Tabella con colonne: Funzione fondamentale, Stato, Contenuto necessario, Riferimento Experience League. Valori di stato: Obbligatorio, Presupposto attivo, Non applicabile.

10. **Funzioni di supporto** — Tabella con colonne: Funzione di supporto, Stato, Perché è importante, Riferimento Experience League. Valori di stato: consigliato, incluso, non applicabile.

11. **Funzioni dell&#39;applicazione** — Una tabella per applicazione con colonne: Funzione, Fase di implementazione, Descrizione.

12. **Prerequisiti** — Elenco di controllo con sintassi `- [ ]`.

13. **Opzioni di implementazione**: 2-4 opzioni dettagliate, ciascuna con Best for, Come funziona, Considerazioni chiave, Vantaggi, Limitazioni e collegamenti Experience League.

14. **Confronto opzioni**: tabella di confronto di riepilogo alla fine.

## Fase 3: Aggiornamenti dei riferimenti incrociati

Dopo aver generato il file di pattern, aggiornate i seguenti file. Leggi `references/pages-to-update.md` per l&#39;elenco di controllo dettagliato.

### Sommario.md

**File:** `/help/blueprints/TOC.md`

Aggiungi una nuova voce nella sezione categoria corretta. Le categorie sono associate alle seguenti sezioni del sommario:

| Margine categoria | Intestazione sezione sommario |
| --- | --- |
| `audience-building-activation` | `+ Audience Building & Activation{#audience-building-activation}` |
| `personalization` | `+ Personalization{#personalization-patterns}` |
| `campaign-management-orchestration` | `+ Campaign Management & Orchestration{#campaign-orchestration-patterns}` |
| `analysis` | `+ Analysis{#analysis-patterns}` |
| `conversational-experience` | `+ Conversational Experience{#conversational-experience-patterns}` |

Il formato di ingresso è:

```
    + [{{Pattern Title}}](/help/blueprints/use-case-patterns/{{category}}/{{filename}}.md)
```

Aggiungi la nuova voce dopo l’ultima voce esistente nella sezione corrispondente. Mantenere il rientro esatto (quattro spazi prima di `+`).

### Pagina Panoramica

**File:** `/help/blueprints/use-case-patterns/overview.md`

Aggiungere una nuova riga alla tabella delle categorie corretta. Il formato è:

```
| [{{Pattern Title}}]({{category}}/{{filename}}.md) | {{Primary capability description}} | [!DNL {{Solution1}}], [!DNL {{Solution2}}] |
```

Aggiungi la nuova riga dopo l’ultima riga esistente nella tabella delle categorie corrispondente.

## Fase 4: Convalida

Dopo aver creato e aggiornato tutti i file, verifica quanto segue:

1. **Collegamenti obiettivo aziendale**: ogni collegamento obiettivo aziendale nel file di modello punta a un file esistente in `/help/blueprints/business-objectives/`. Utilizza glob o read per confermare l’esistenza di ogni file di destinazione.

2. **Posizionamento voce sommario**: la nuova voce sommario si trova all&#39;interno della sezione categoria corretta e utilizza il formato di rientro e percorso corretto.

3. **Riga tabella panoramica**: la nuova riga panoramica si trova nella tabella delle categorie corretta e segue lo stesso formato di colonna delle righe esistenti.

4. **Denominazione file** - Il nome file del modello utilizza maiuscole/minuscole e corrisponde al percorso a cui si fa riferimento sia in TOC.md che in overview.md.

5. **Completezza frontmatter**: il file di pattern include titolo, descrizione, soluzione ed exl-id nel frontmatter YAML.

6. **Collegamenti Experience League** — Verifica che gli URL Experience League siano plausibili (inizia con `https://experienceleague.adobe.com/it`).

Segnala eventuali errori di convalida all’utente e correggili prima di considerare completata l’attività.

## Note

- Utilizza sempre la sintassi `[!DNL ...]` per i nomi dei prodotti Adobe nelle tabelle e nel corpo del testo, seguendo la convenzione dei file di pattern esistenti.
- `exl-id` in frontmatter deve essere un UUID segnaposto. La pipeline di pubblicazione assegna il valore reale.
- Se l&#39;utente desidera creare più modelli contemporaneamente, ripetere le fasi 2-4 per ogni modello, ma raccogliere tutte le informazioni nella fase 1.
- Se è necessaria una nuova categoria che non esiste nell’elenco precedente, avvisa l’utente che TOC.md e overview.md richiederanno la creazione di nuove sezioni e gestirle come un passaggio separato.
