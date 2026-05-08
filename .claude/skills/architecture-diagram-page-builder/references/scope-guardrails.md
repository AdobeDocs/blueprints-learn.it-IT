---
source-git-commit: 83e85d946e455cde46001af0a2112637b7fe24cc
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---
# Pagina guardrail di ambito: architettura e pagina pattern del caso di utilizzo

Il sito blueprint separa **pagine di diagramma dell&#39;architettura** dalle **pagine di modelli di casi d&#39;uso** perché rispondono a esigenze di lettura diverse. Questo documento definisce cosa appartiene a dove e come gestire il contenuto che va oltre il limite.

## La distinzione principale

- **Le pagine del diagramma dell&#39;architettura** sono riferimenti visivi di primo livello. Rispondono: *&quot;Come si adattano questi sistemi? Dove sono i punti di integrazione? Qual è la forma del flusso di dati?&quot;* I lettori vengono qui per orientarsi.
- **Le pagine del caso d&#39;uso** sono guide all&#39;implementazione. Rispondono: *&quot;Come si crea questa funzionalità? Quali funzioni sono coinvolte? Quali KPI misurano il successo? Quali sono le opzioni di implementazione?&quot;* I lettori vengono qui quando hanno un caso d&#39;uso e devono spedirlo.

## Appartiene a una pagina dell’architettura

| Categoria | Esempi |
| --- | --- |
| Architettura di primo livello | Diagrammi di panoramica di AEP e applicazioni, marketecture di Experience Cloud, topologia hub e edge |
| Flusso dei dati di sistema | Percorsi di acquisizione in tempo reale e in batch, sincronizzazione dei profili tra hub e edge, flussi di ricerca e attivazione |
| Punti di integrazione | Dove AEP si integra con AJO, CJA, Target, Campaign, Marketo, Workfront; limiti SDK; superfici API |
| Topologia di distribuzione | Distribuzione di Web SDK e Mobile SDK, inoltro lato server, posizionamento di nodi edge |
| Architettura dell&#39;applicazione | Struttura interna di una singola applicazione (AJO, CJA, RTCDP) a livello di sistema |
| Puntatori per i modelli di casi d’uso | &quot;Questa architettura supporta i modelli X, Y, Z&quot; con collegamenti. La pagina dell&#39;architettura **non** duplica tale contenuto |

## NON appartiene a una pagina dell&#39;architettura

Se scrivi uno dei seguenti elementi, reindirizza a una pagina di pattern del caso d&#39;uso (utilizza l&#39;abilità `use-case-pattern-builder`):

| Categoria | Perché appartiene altrove |
| --- | --- |
| KPI e formule di misurazione | I modelli di casi d’uso misurano i risultati; le pagine dell’architettura non |
| Obiettivi aziendali, impatto aziendale | Il contenuto KBO si trova in `/help/blueprints/business-objectives/`; i modelli vi fanno riferimento |
| Esempi di casi d’uso tattici | &quot;Promemoria di abbandono carrello&quot;, &quot;eroe homepage personalizzato&quot;, ecc. — questi sono contenuti pattern |
| Catene di funzioni (`A > B > C > D`) | Il costrutto a catena di funzioni fa parte del modello di pattern Use Case |
| Narrative personali | &quot;Maria l&#39;addetta al marketing vuole...&quot; gli scenari di stile appartengono ai modelli, non ai riferimenti all’architettura |
| Opzioni di implementazione | Le linee guida per l’implementazione con più opzioni (consigliate per, come funziona, vantaggi, limitazioni) sono un costrutto per pattern |
| Tabelle delle funzioni fondamentali/di supporto | Queste sono sezioni di pagina pattern |
| Elenchi di controllo dei prerequisiti per caso d’uso | I pattern tengono traccia di questi; le pagine dell’architettura si collegano invece ai pattern |

## Espressioni di attivazione da controllare

Se l’utente fornisce una di queste frasi durante la descrizione della nuova pagina, sospendi e ricontrolla l’ambito:

- &quot;KPI&quot;
- &quot;impatto aziendale&quot; / &quot;risultati aziendali&quot;
- &quot;casi d’uso tattici&quot;/&quot;scenari d’esempio&quot;
- &quot;catena di funzioni&quot;
- &quot;opzioni di implementazione&quot;
- &quot;ideale per&quot;
- &quot;vantaggi e limitazioni&quot;
- &quot;prerequisiti&quot;
- &quot;utenti tipo&quot; / &quot;stakeholder&quot;
- &quot;misurazione&quot;

Questi non squalificano automaticamente la pagina, ma segnalano che l’utente potrebbe voler usare una pagina con pattern di utilizzo, non una pagina con architettura. Conferma l’intento prima di generare.

## Cosa fare in caso di spostamento del contenuto

1. **Identificare la deriva.** Posizionare il puntatore del mouse sulla sezione o sul punto elenco specifico che ha attraversato il limite.
2. **Offrire due opzioni all&#39;utente:**
   - Ritaglia la sezione dalla pagina dell’architettura (il più comune, ovvero mantiene la pagina dell’architettura concentrata).
   - Interrompi e passa a `use-case-pattern-builder` per quel contenuto (quando l&#39;utente desidera effettivamente una pagina con pattern).
3. **Attendi conferma.** Non riscrivere o eliminare il contenuto in modo silenzioso.
4. **Se conservi contenuti solo per l&#39;architettura**, sostituisci i contenuti profondi con un singolo punto elenco in `## Use case patterns supported` che si collega al pattern rilevante (esistente o da creare).

## Casi Edge

- **La pagina è a metà architettura, a metà pattern.** Dividi in due pagine: una pagina architettura (questa abilità) e una pagina pattern caso d’uso (l’abilità `use-case-pattern-builder`). Collegale tra loro.
- **La pagina Architettura descrive un singolo caso d&#39;uso end-to-end.** Si tratta di un modello di caso d’uso, non di una pagina di architettura. Reindirizza a `use-case-pattern-builder`.
- **La pagina Architettura deve mostrare flussi di dati di esempio per uno scenario specifico.** Accettabile se lo scenario è solo illustrativo e la maggior parte della pagina rimane a livello di architettura di sistema. Mantenere l&#39;esempio su un paragrafo e collegarlo al modello appropriato per ottenere informazioni complete.

## Test rapido

Prima di generare, chiedere: *&quot;Se un lettore arriva a questa pagina in attesa di un riferimento all&#39;architettura di livello superiore, ne otterrà uno o riceverà una descrizione dettagliata del caso d&#39;uso?&quot;* In quest&#39;ultimo caso, la pagina appartiene a `use-case-pattern-builder`.
