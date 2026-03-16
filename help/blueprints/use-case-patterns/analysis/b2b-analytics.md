---
title: Analisi B2B
description: Scopri come includere le informazioni a livello di account B2B nell’analisi del percorso clienti cross-channel.
solution: Customer Journey Analytics, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7528'
ht-degree: 1%

---


# Analisi B2B

Questa guida fornisce un riferimento completo all&#39;implementazione per l&#39;analisi a livello di account B2B utilizzando [!DNL Customer Journey Analytics] ([!DNL CJA]) B2B edition e [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition. È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono incorporare informazioni a livello di account B2B nell’analisi del percorso cliente cross-channel.

Copre tutti gli approcci praticabili per l’analisi incentrata sull’account, dalle strutture di account flat a gerarchie di account globali complesse, con indicazioni su quando scegliere ogni opzione. Il piano riguarda le connessioni dati B2B, la configurazione della visualizzazione dati dell’account, l’analisi dell’area di lavoro e la pubblicazione dei dashboard.

Analytics B2B estende le funzionalità standard di [!DNL CJA] con connessioni basate su account, contenitori specifici di B2B (account, account globale, opportunità, gruppo di acquisto) e reporting a livello di account. Questa funzionalità consente alle organizzazioni di analizzare il coinvolgimento di marketing e vendite a livello di account, monitorare la progressione delle opportunità, misurare la completezza dei gruppi di acquisto e attribuire i ricavi ai punti di contatto di marketing attraverso cicli di vendita B2B estesi.

## Panoramica del caso d’uso

Le organizzazioni B2B devono affrontare una sfida di analisi fondamentale: i loro clienti non sono persone singole, ma account composti da più parti interessate, gruppi di acquisto e opportunità. Le analisi standard basate su persone non possono rispondere a domande come &quot;Quali account sono più coinvolti?&quot;, &quot;Quanto sono completi i nostri gruppi di acquisto?&quot; o &quot;Quali punti di contatto di marketing determinano la progressione dell’opportunità?&quot;

Analytics B2B affronta questo problema sfruttando [!DNL CJA] B2B edition per creare visualizzazioni analitiche incentrate sull&#39;account che combinano dati comportamentali a livello di persona con dimensioni di account, opportunità e gruppo di acquisto. [!DNL RT-CDP] B2B edition fornisce l’unificazione del profilo dell’account sottostante e la risoluzione delle identità B2B che alimenta il livello di analisi. Insieme, queste soluzioni consentono alle organizzazioni di creare analisi di percorso cross-channel a livello di account, correlare il coinvolgimento di marketing con la progressione della pipeline e fornire informazioni fruibili ai team di marketing e di vendita.

Il pubblico di destinazione include i team operativi di marketing B2B, i leader della generazione della domanda, gli analisti delle operazioni di ricavo e i responsabili delle vendite che necessitano di visibilità sul coinvolgimento a livello di account e sullo stato della pipeline.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### Migliorare analisi e reporting

Migliora le funzionalità di reporting per informazioni di marketing più veloci e fruibili tramite dashboard unificate e strumenti self-service. L’analisi B2B consente alle organizzazioni di consolidare i dati di coinvolgimento a livello di account da più origini in un unico ambiente analitico, fornendo visibilità cross-channel sul modo in cui i programmi di marketing influenzano la pipeline e i ricavi.

**KPI:** efficienza, produttività

[Ulteriori informazioni sul miglioramento di analisi e reporting](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)

### Abilitare il processo decisionale basato sui dati

Fornisci ai team analisi self-service, informazioni sui clienti in tempo reale e previsioni basate sull’intelligenza artificiale come guida per la strategia. L’analisi a livello di account fornisce ai team di marketing e vendite i dati necessari per assegnare le priorità agli account, ottimizzare le strategie di coinvolgimento e allineare le opportunità della pipeline.

**KPI:** efficienza, produttività

[Ulteriori informazioni sull’abilitazione del processo decisionale basato sui dati](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)

### Migliorare la qualificazione e la conversione dei lead

Aumenta la qualità dei lead e accelera la progressione della pipeline tramite valutazione, nutrimento e follow-up personalizzato. CJA B2B edition fornisce intervalli di lookback di account estesi per 13 mesi appositamente progettati per i cicli di vendita B2B, consentendo un’attribuzione multi-touch accurata in tutto il percorso di account.

**KPI:** efficienza, ricavi incrementali

[Ulteriori informazioni sul miglioramento della qualificazione e conversione dei lead](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

## Esempi di casi d’uso tattici

Gli scenari seguenti illustrano come questo modello può essere applicato nella pratica.

- **Analisi del punteggio di coinvolgimento dell&#39;account**: misura e classifica gli account in base al loro coinvolgimento aggregato su web, e-mail, eventi e interazioni di contenuto per identificare gli account con intenti elevati per il follow-up delle vendite
- **Monitoraggio della completezza del gruppo di acquisto**: analizza la composizione del gruppo di acquisto tra gli account per identificare le lacune nella copertura dei ruoli e assegnare la priorità all&#39;acquisizione dei lead per i gruppi di acquisto incompleti
- **Correlazione della pipeline dell&#39;opportunità** — Correlazione dei dati dell&#39;impegno di marketing con la progressione della fase dell&#39;opportunità per capire quali campagne e punti di contatto guidano l&#39;avanzamento della pipeline
- **Attribuzione B2B multi-touch**: applica modelli di attribuzione con intervalli di lookback di 13 mesi ai punti di contatto di marketing del credito nell&#39;intero percorso di acquisto B2B dal primo contatto al vincitore chiuso
- **Mappatura percorso di account**: visualizza il percorso di account cross-channel dalla conoscenza iniziale fino alla creazione e alla chiusura delle opportunità, identificando percorsi comuni e punti di attrito
- **Influenza delle campagne sulla pipeline**: misura in che modo campagne specifiche influenzano la creazione di pipeline dell&#39;account, l&#39;avanzamento delle opportunità e la generazione di ricavi
- **Progressione dell&#39;engagement dei gruppi di acquisto**: verifica l&#39;evoluzione dei punteggi di engagement dei gruppi di acquisto nel tempo e correlazione delle soglie di engagement con i risultati delle opportunità
- **Prestazioni dei contenuti basati sull&#39;account**: analisi delle risorse e degli argomenti di contenuto che risuonano con segmenti di account, settori o ruoli di gruppi di acquisto specifici
- **Dashboard di allineamento vendite e marketing** — Crea dashboard condivise che forniscano sia ai team di marketing che a quelli di vendita una visione unificata del coinvolgimento dell&#39;account, dell&#39;integrità della pipeline e dell&#39;attribuzione dei ricavi
- **Segmentazione account per l&#39;attivazione**: crea segmenti B2B in base all&#39;analisi a livello di account (ad esempio, &quot;account altamente coinvolti senza opportunità aperte&quot;) e pubblicali per l&#39;attivazione a valle

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare il successo di questo modello di caso d’uso.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Punteggio di coinvolgimento dell’account | Aggregare metriche di coinvolgimento in tutti i contatti all’interno di un account | Metrica calcolata che combina visite web, interazioni e-mail, partecipazione a eventi e download di contenuti a livello di account |
| Completezza gruppo acquisti | Percentuale di ruoli richiesti completati all’interno di un gruppo di acquisto | Rapporto tra i ruoli completati e il totale dei ruoli richiesti per gruppo di acquisto, tracciato nel tempo |
| Pipeline influenzata dal marketing | Ricavi in pipeline toccati dalle attività di marketing | Valore dell’opportunità in cui i contatti dell’account associati hanno punti di contatto di marketing nella finestra di attribuzione |
| Tasso di conversione da account a opportunità | Percentuale di account coinvolti che generano opportunità qualificate | Conti con opportunità divisi per il totale dei conti impegnati in un periodo definito |
| Lunghezza media ciclo di offerta | Tempo dal primo contatto marketing al vincitore chiuso | Durata media dal primo punto di contatto attribuito alla data di chiusura dell’opportunità |
| Ricavi da attribuzione marketing | Ricavi attribuiti ai punti di contatto di marketing | Ricavi da opportunità realizzate chiuse con tocchi di marketing, distribuiti per modello di attribuzione |
| Raggiungimento e penetrazione dell’account | Numero di contatti coinvolti per account di destinazione | Contatti univoci con interazioni di marketing per account, rispetto al totale dei contatti noti |
| Coinvolgimento contenuti per ruolo di acquisto | Metriche di coinvolgimento segmentate per ruolo di gruppo di acquisto | Visualizzazioni di pagina, download e tempo trascorso suddivisi per persona/ruolo all’interno dei gruppi di acquisto |

## Schema del caso d’uso

**Analisi B2B**

Includere informazioni a livello di account B2B nell’analisi del percorso clienti cross-channel.

**Catena di funzioni:** Connessione dati B2B > Configurazione visualizzazione dati account > Analisi Workspace > Pubblicazione dashboard

## Applicazioni

Per implementare questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Customer Journey Analytics]B2B edition**: fornisce connessioni basate su account, contenitori di visualizzazione dati specifici di B2B, analisi dell&#39;area di lavoro a livello di account, analisi del gruppo di acquisto, analisi delle opportunità, segmentazione B2B e attribuzione B2B con intervalli di lookback estesi
- **[!DNL Real-Time CDP]B2B edition** — Fornisce le basi dati B2B tra cui l&#39;unificazione del profilo account, la risoluzione dell&#39;identità B2B, le classi di schema B2B (account, opportunità, gruppo acquisti) e l&#39;integrazione [!DNL Marketo Engage] per l&#39;acquisizione dei dati del coinvolgimento B2B

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve essere al suo posto | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Obbligatorio | Sandbox configurata con [!DNL CJA] adesioni B2B edition e [!DNL RT-CDP] B2B edition. Ruoli assegnati a data engineer, analisti e utenti delle operazioni di marketing con accesso a [!DNL CJA] e al modello dati B2B. | [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home) |
| Modellazione e preparazione dei dati | Obbligatorio | Schemi XDM B2B configurati utilizzando le classi B2B: account aziendale XDM, opportunità aziendale XDM, relazione persona account aziendale XDM, relazione persona opportunità aziendale XDM e membri elenco di marketing aziendale XDM. È necessario definire i gruppi di campi per gli attributi di conto, le fasi di opportunità e i ruoli dei gruppi di acquisto. Set di dati creati e abilitati per il profilo. | [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Schemi B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b) |
| Origini dati e raccolta | Obbligatorio | Origini dati B2B connesse, in genere tramite il connettore di origine [!DNL Marketo Engage] o il connettore di origine CRM [!DNL Salesforce]. I record account, i record opportunità, le relazioni persona-account e gli eventi di coinvolgimento comportamentale devono fluire nei set di dati di AEP. [!DNL Web SDK] L&#39;integrazione di o [!DNL Marketo] deve acquisire eventi comportamentali con associazione account. | [Panoramica origini](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home), [Connettore Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| Configurazione identità e profilo | Obbligatorio | Risoluzione identità B2B configurata per risolvere le relazioni persona-account. L&#39;ID account, l&#39;ID persona ([!DNL Marketo] ID lead o ID contatto CRM) e le identità multi-dispositivo (ECID, e-mail) devono essere collegati. Il grafo delle identità deve supportare la mappatura molti-a-molti persona-account inerente ai modelli di dati B2B. | [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Risoluzione identità B2B](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b) |
| Definizione e segmentazione del pubblico | Presunto sul posto | Le definizioni del pubblico a livello di account dovrebbero essere disponibili se i segmenti B2B verranno pubblicati da [!DNL CJA] ad AEP per l&#39;attivazione. Per i casi di utilizzo solo di Analytics, questo non è un prerequisito rigoroso ma è consigliato per l’analisi basata su segmenti. | [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Consigliato | Gli attributi calcolati nei profili di account (ad esempio, punteggio di coinvolgimento totale, giorni dall&#39;ultima attività, conteggio opportunità) arricchiscono le dimensioni analitiche disponibili in [!DNL CJA] per l&#39;analisi a livello di account. | [Panoramica attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Consigliato | I set di dati B2B, in particolare i dati degli eventi comportamentali di [!DNL Marketo Engage], possono crescere rapidamente. Le regole di scadenza dei dataset consentono di gestire lo storage e garantire la conformità ai requisiti di conservazione dei dati. | [Gestione avanzata del ciclo di vita dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Etichettatura e applicazione dell’utilizzo dati | Consigliato | I dati B2B spesso contengono informazioni aziendali sensibili (valori contrattuali, dati sulla concorrenza). Le etichette di utilizzo dei dati e i criteri di governance garantiscono che i dati vengano utilizzati in modo appropriato in tutti i flussi di lavoro di analisi e attivazione. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Monitoraggio e osservabilità | Consigliato | I connettori di origine B2B ([!DNL Marketo], [!DNL Salesforce]) richiedono il monitoraggio per l&#39;integrità dell&#39;acquisizione. Il monitoraggio dello stato della connessione in [!DNL CJA] garantisce l&#39;aggiornamento dei dati per l&#39;analisi. Le regole di avviso per gli errori di acquisizione impediscono l’utilizzo di dashboard non aggiornati. | [Panoramica di Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting e analisi | Incluso | Questo modello è esso stesso un modello di analisi. Questa funzione è intrinsecamente inclusa in quanto la catena di funzioni di base fornisce funzionalità di reporting e analisi. | [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Customer Journey Analytics] B2B edition

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Connessione basata su account | Fase 1: Connessione dati B2B | Configurare le connessioni utilizzando Account o Account globale come identificatore principale per l’analisi a livello di organizzazione |
| Configurazione visualizzazione dati B2B | Fase 2: configurazione della visualizzazione dati dell’account | Definisci le visualizzazioni dati con contenitori specifici di B2B (Account, Account globale, Opportunità, Gruppo acquisti) insieme ai contenitori standard Persona, Sessione ed Evento |
| Analisi Workspace a livello di account | Fase 3: Analisi Workspace | Creare analisi a forma libera utilizzando dimensioni a livello di account, metriche e contenitori B2B per approfondimenti sul percorso a livello di organizzazione |
| Analisi gruppo acquisti | Fase 3: Analisi Workspace | Analizza la composizione, il coinvolgimento e la progressione del gruppo di acquisto durante il processo di decisione di acquisto |
| Analisi dell’opportunità | Fase 3: Analisi Workspace | Monitorare la progressione delle opportunità attraverso le fasi dei funnel di vendita e correlare con i dati del coinvolgimento di marketing |
| Segmentazione B2B | Fase 3: Analisi Workspace | Creare segmenti utilizzando contenitori B2B per l’analisi filtrata a livello di account |
| Attribuzione B2B | Fase 3: Analisi Workspace | Applicare modelli di attribuzione con intervalli di lookback di account estesi a 13 mesi per l’analisi del ciclo di vendita B2B |
| Creazione di metriche calcolate | Fase 3: Analisi Workspace | Definire le metriche calcolate per i KPI B2B come il tasso di coinvolgimento dell’account, la completezza del gruppo di acquisto e l’influenza della pipeline |
| Pubblicazione di dashboard e scorecard | Fase 4: pubblicazione del dashboard | Creare e condividere dashboard e scorecard per dispositivi mobili per la leadership di marketing e vendita |
| Pubblicazione dei tipi di pubblico | Fase 4: pubblicazione del dashboard | Pubblica di nuovo in AEP i tipi di pubblico basati sull&#39;account definiti da [!DNL CJA] per l&#39;attivazione a valle |

### [!DNL Customer Journey Analytics] — funzioni standard

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Connessione dati | Fase 1: Connessione dati B2B | Associa i set di dati B2B di AEP a [!DNL CJA] connessioni per l’analisi cross-channel |
| Configurazione visualizzazione dati | Fase 2: configurazione della visualizzazione dati dell’account | Configurare dimensioni, metriche, attribuzione e impostazioni di persistenza standard nella visualizzazione dati B2B |
| Analisi Workspace | Fase 3: Analisi Workspace | Creare analisi a forma libera con tabelle, fallout, visualizzazioni di flusso, coorte e attribuzione |
| Analisi guidata | Fase 3: Analisi Workspace | Utilizzare flussi di lavoro guidati per funnel, analisi delle tendenze e conservazione a livello di account |

### [!DNL Real-Time CDP] B2B edition

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Unificazione profilo account | Prerequisito (F2/F4) | Consolidare i dati B2B tra origini diverse in profili di account unificati utilizzando classi di schema B2B XDM specializzate |
| Risoluzione identità B2B | Prerequisito (F4) | Risolvere le relazioni tra persone e account che supportano gerarchie di account a più livelli e mappature molti-a-molti |
| Integrazione di [!DNL Marketo Engage] | Prerequisito (F3) | Acquisire i dati di coinvolgimento comportamentale e i record account/lead da [!DNL Marketo Engage] tramite i connettori di origine B2B nativi |

## Prerequisiti

Gli elementi seguenti devono essere presenti prima dell’inizio dell’implementazione.

- [!DNL CJA] licenza B2B edition è attiva ed è stato eseguito il provisioning per l&#39;organizzazione
- [!DNL RT-CDP] licenza B2B edition è attiva con schemi B2B e profili account configurati
- Vengono definiti gli schemi XDM B2B (account, opportunità, relazione persona account, relazione persona opportunità, membri elenco di marketing)
- [!DNL Marketo Engage] e/o i connettori di origine CRM sono configurati e acquisiscono attivamente i dati
- I dati dell’evento comportamentale a livello di account (visite web, interazioni e-mail, invii di moduli) fluiscono in AEP con l’associazione dell’account
- Le relazioni tra persone e account sono stabilite nel grafico delle identità
- Almeno 30 giorni di dati storici sul coinvolgimento B2B sono disponibili per analisi significative
- Le parti interessate hanno concordato le definizioni dei ruoli dei gruppi di acquisto e le mappature degli interessi delle soluzioni
- [!DNL CJA] account utente dispongono dei profili di prodotto appropriati per le funzionalità di B2B edition
- I KPI target e i requisiti di reporting sono stati definiti dai responsabili marketing e vendite

## Opzioni di implementazione

Le sezioni seguenti descrivono diversi approcci per l’implementazione di questo modello di caso d’uso.

### Opzione A: analisi incentrata sull’account

**Ideale per:** organizzazioni che desiderano analizzare tutti i dati di coinvolgimento e pipeline attraverso l&#39;obiettivo dell&#39;account. Questo approccio utilizza il contenitore Account come unità analitica principale, fornendo una vista dall’alto verso il basso dell’avanzamento dei conti nel percorso di acquisto.

**Funzionamento:**

Configurare una connessione B2B [!DNL CJA] con Account come identificatore primario. Tutti gli eventi comportamentali, le opportunità e i dati dei gruppi di acquisto vengono aggregati a livello di account. La visualizzazione dati utilizza Account come contenitore di livello più alto, con Persona, Sessione ed Evento nidificati al suo interno. In questo modo è possibile eseguire analisi del tipo: &quot;Quanti account hanno visitato la pagina dei prezzi e quindi creato un&#39;opportunità entro 30 giorni?&quot;

L’analisi incentrata sull’account fornisce la visualizzazione più naturale per le organizzazioni B2B in cui l’account è l’unità di acquisto. Dimensioni quali settore, dimensioni dell’azienda, livello dell’account e proprietario dell’account possono essere utilizzate per suddividere i modelli di coinvolgimento e le metriche della pipeline. L’attribuzione viene applicata a livello di account con intervalli di lookback di 13 mesi adatti a lunghi cicli di vendita B2B.

**Considerazioni chiave:**

- Richiede la mappatura pulita da account a persona nel grafo delle identità
- Tutti gli eventi a livello di persona devono essere attribuibili a un account
- Il traffico web anonimo che non può essere associato a un account non verrà visualizzato nell’analisi a livello di account

**Vantaggi:**

- Visualizzazione a livello di account dell&#39;intero percorso di acquisto
- Abilita l’attribuzione basata sul conto che corrisponde alla modalità di generazione dei ricavi B2B
- Supporta l’analisi dei gruppi di acquisto e delle opportunità come contenitori nidificati all’interno dell’account
- Allinea le analisi alla strategia di marketing basato sull’account (ABM)

**Limitazioni:**

- Richiede una solida risoluzione dell&#39;identità da persona ad account
- I dati di coinvolgimento anonimi o senza corrispondenza sono esclusi dall’analisi
- Configurazione più complessa rispetto all’analisi incentrata sulla persona

**Experience League:**

- [Panoramica di CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [Schemi B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)

### Opzione B: analisi globale incentrata sull&#39;account

**Ideale per:** organizzazioni aziendali con gerarchie di conti complesse in cui una società madre ha più account affiliata. Questo approccio utilizza il conto globale come identificatore principale, aggregando tutte le attività del conto dell&#39;affiliata al livello dell&#39;organizzazione padre.

**Funzionamento:**

Configurare la connessione B2B [!DNL CJA] con Account globale come identificatore primario anziché Account. In questo modo vengono aggregati i dati del coinvolgimento da tutti i conti affiliata nell&#39;organizzazione padre. Ad esempio, se &quot;Acme Corp&quot; ha controllate regionali &quot;Acme EMEA&quot; e &quot;Acme APAC&quot;, una connessione account globale consolida tutto il coinvolgimento di tutte e tre le entità in un’unica vista analitica.

La visualizzazione dati include Account globale come contenitore principale, con Account, Persona, Sessione ed Evento come contenitori nidificati. Ciò consente l’analisi a livello di account globale e secondario all’interno dello stesso progetto Workspace. Gli intervalli di lookback dell’attribuzione si applicano a livello di account globale, acquisendo tutti i punti di contatto nell’intera gerarchia aziendale.

**Considerazioni chiave:**

- Richiede dati della gerarchia dei conti con relazioni padre-figlio definite nel modello di dati B2B
- L&#39;ID account globale deve essere compilato e accurato in tutti i record account
- I conti delle affiliate devono essere mappati correttamente al relativo padre

**Vantaggi:**

- Offre visibilità consolidata su strutture di account aziendali complesse
- Impedisce l&#39;analisi frammentata quando un singolo cliente aziendale ha più record di account
- Consente il confronto tra le consociate regionali all&#39;interno di un unico account globale
- Supporta la generazione di rapporti sui ricavi e sulla pipeline a livello aziendale

**Limitazioni:**

- Richiede dati accurati della gerarchia degli account, che molte organizzazioni faticano a mantenere
- Può oscurare i pattern a livello di consociata se visualizzati solo a livello globale
- Ulteriore lavoro di modellazione dei dati per stabilire e mantenere relazioni gerarchiche

**Experience League:**

- [Panoramica di CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### Opzione C: Analisi delle persone e degli account ibridi

**Ideale per:** organizzazioni che passano da analisi basate su persone ad analisi basate su account o che richiedono sia visualizzazioni a livello di persona che di account. Questo approccio crea due visualizzazioni dati dalla stessa connessione, una incentrata sulla persona e l’altra incentrata sull’account.

**Funzionamento:**

Configurare una singola connessione B2B [!DNL CJA] che includa tutti i set di dati B2B (evento, account, opportunità, gruppo di acquisto, relazioni persona-account). Creare quindi due visualizzazioni dati: una che utilizza Persona come contenitore principale (simile allo standard [!DNL CJA]) e una che utilizza Account come contenitore principale. Gli analisti possono passare da una visualizzazione dati all’altra a seconda della domanda da porsi.

La visualizzazione dati incentrata sulla persona fornisce un’analisi di percorso tradizionale a livello individuale (ad esempio, &quot;Qual è il percorso di conversione per i lead che diventano opportunità?&quot;), mentre la visualizzazione dati incentrata sull’account fornisce un’analisi a livello di organizzazione (ad esempio, &quot;Quali account hanno il tasso di conversione più elevato da coinvolgimento a pipeline?&quot;). Entrambe le viste utilizzano gli stessi dati sottostanti, garantendo la coerenza.

**Considerazioni chiave:**

- Richiede due visualizzazioni dati con configurazioni di dimensioni e metriche potenzialmente diverse
- Gli analisti devono sapere quando utilizzare ciascuna visualizzazione
- Potrebbe essere necessario creare separatamente le metriche calcolate per ogni visualizzazione dati

**Vantaggi:**

- Offre flessibilità per analizzare i dati a livello sia di persona che di account
- Percorso di adozione più semplice per i team abituati alle analisi a livello di persona
- Consente il confronto tra metriche a livello di persona e di account
- Supporto di strategie di marketing basate su lead e account

**Limitazioni:**

- Due visualizzazioni dati da mantenere e mantenere sincronizzate
- Potenziale confusione per gli analisti sulla visualizzazione da utilizzare
- Le metriche calcolate e i filtri possono richiedere la duplicazione tra le viste

**Experience League:**

- [Creare o modificare una visualizzazione dati](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Panoramica delle visualizzazioni dati](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)

### Confronto delle opzioni

| Criteri | Opzione A: incentrato sull&#39;account | Opzione B: approccio globale incentrato sull&#39;account | Opzione C: persona ibrida + account |
| --- | --- | --- | --- |
| Ideale per | B2B standard con struttura di conti flat | Organizzazione con gerarchie padre-figlio | Organizzazioni in transizione o necessità doppie |
| Complessi | Medio | Alta | Medium - Alta |
| Requisiti dei dati | Mappatura account-persona | Gerarchia dei conti + mappatura | Mappatura account-persona |
| Ambito di attribuzione | Livello account (lookback di 13 mesi) | Livello account globale (lookback di 13 mesi) | A livello sia di persona che di account |
| Dati anonimi | Escluso dalla visualizzazione account | Escluso dalla visualizzazione globale | Incluso nella vista Persona, escluso dalla vista account |
| Richiede | [!DNL RT-CDP] B2B edition, [!DNL CJA] B2B edition | [!DNL RT-CDP] B2B edition, [!DNL CJA] B2B edition, dati gerarchia | [!DNL RT-CDP] B2B edition, [!DNL CJA] B2B edition |
| Manutenzione | Visualizzazione dati singola | Visualizzazione dati singola | Due visualizzazioni dati |

### Scegli l’opzione giusta

- **Scegliere l&#39;opzione A** se l&#39;organizzazione dispone di una struttura di conti piatta (senza gerarchie padre-figlio), la strategia ABM funziona a livello di singolo account e si desidera il percorso più semplice per le analisi a livello di account.
- **Scegliere l&#39;opzione B** se i conti di destinazione sono aziende di grandi dimensioni con conti affiliate in aree geografiche o divisioni e sono necessari rapporti consolidati a livello di padre aziendale. Questa opzione richiede dati di gerarchia di account di alta qualità.
- **Scegliere l&#39;opzione C** se l&#39;organizzazione sta passando dal marketing basato su lead a quello basato su account, gli analisti necessitano sia di analisi funnel a livello di persona che di analisi del coinvolgimento a livello di account, oppure si dispone di una combinazione di linee di business B2B e B2C.

## Fasi di implementazione

Le seguenti fasi delineano la sequenza di implementazione consigliata.

### Fase 1: connessione dati B2B

**Funzione applicazione:** [!DNL CJA] B2B: connessione basata su account, [!DNL CJA]: connessione dati

Configura la connessione [!DNL CJA] che associa i set di dati B2B di AEP a [!DNL CJA] per l&#39;analisi. Questa connessione definisce quali set di dati fluiscono in [!DNL CJA], il tipo di identificatore primario (Account o Account globale) e il modo in cui vengono acquisiti i dati storici e in streaming. La connessione è la base di tutte le analisi successive.

#### Decisione: tipo di identificatore primario

Determina se la connessione deve utilizzare l’ID account o l’ID account globale come identificatore primario.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| ID account | Struttura dei conti semplice, senza gerarchie padre-figlio | Configurazione più semplice; ogni account è stato analizzato in modo indipendente. La scelta più comune per il B2B incentrato sulle PMI. |
| ID account globale | Conti aziendali con gerarchie di affiliate | Richiede dati gerarchici; aggrega tutte le affiliate sotto la padre. Ideale per i programmi ABM aziendali. |

#### Decisione: Selezione del set di dati e designazione del tipo

Determina quali set di dati B2B devono essere inclusi e come devono essere digitati.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Set di dati evento (comportamentali) | Includi sempre | Interazioni web, eventi e-mail, invii di moduli, download di contenuti. Deve avere un campo timestamp. Questi sono i segnali di coinvolgimento. |
| Set di dati record account (profilo) | Includi sempre | Attributi dell’account come industria, dimensione, livello, proprietario. Fornisce il contesto dimensionale per l&#39;analisi dell&#39;account. |
| Set di dati di opportunità (ricerca/profilo) | Includi per analisi pipeline | Fase dell’opportunità, valore, data di chiusura. Obbligatorio per l’analisi dell’attribuzione di pipeline e ricavi. |
| Acquisto di set di dati di gruppo (ricerca/profilo) | Includi per analisi gruppo di acquisto | Ruoli di gruppo di acquisto, punteggi di coinvolgimento, completezza. Obbligatorio per l&#39;analisi della composizione del gruppo di acquisto. |
| Set di dati di relazione persona-account (ricerca) | Includi sempre | Associa le persone agli account. Critico per l’associazione di eventi a livello di persona all’analisi a livello di account. |
| Set di dati di campagne/programmi (ricerca) | Includi per attribuzione | Metadati della campagna, tipi di programmi, canali. Abilita l’analisi dell’influenza della campagna. |

#### Decisione: intervallo di retrocompilazione

Determina la quantità di dati storici da importare nella connessione.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Tutti i dati esistenti | I cicli di vendita B2B sono lunghi (6-18 mesi) e hai bisogno di una storia completa | Consigliato per B2B. La retrocompilazione può richiedere giorni per set di dati di grandi dimensioni, ma fornisce dati di attribuzione completi. |
| Intervallo date personalizzato (ultimi 2-3 anni) | La qualità dei dati si deteriora oltre un certo punto | Bilancia completezza e qualità dei dati. Comune quando i dati CRM presentano incongruenze storiche. |
| Nessuna retrocompilazione | Solo test o sviluppo | Solo i nuovi dati fluiscono in. Non adatto per analisi B2B di produzione. |

#### Configurare la connessione dati B2B

**Navigazione interfaccia utente:** [!DNL Customer Journey Analytics] > Connessioni > Crea nuova connessione

Dettagli configurazione chiave:

- Seleziona la sandbox di AEP contenente i set di dati B2B
- Imposta il numero medio di eventi giornalieri per la pianificazione della capacità
- Aggiungi ogni set di dati e designane il tipo (evento, ricerca o profilo)
- Configurare il campo ID persona per utilizzare l’ID account o l’ID account globale per le connessioni B2B
- Abilita lo streaming per i set di dati che richiedono aggiornamenti quasi in tempo reale
- Abilita &quot;Importa tutti i dati esistenti&quot; per la retrocompilazione cronologica

**Opzioni divergenti:**

**Per L&#39;Opzione A (Incentrata Sull&#39;Account):**
Imposta l’identificatore principale su ID account. Aggiungi i set di dati record account, opportunità, gruppo di acquisto e relazione persona-account. Configura i set di dati evento a livello di persona con il campo ID account per l’unione di più set di dati.

**Per L&#39;Opzione B (Global Account-Centric):**
Imposta l’identificatore principale su ID account globale. Assicurarsi che i dati della gerarchia di account includano il campo ID account globale. Tutti i set di dati devono includere o poter essere collegati all’ID account globale per una corretta aggregazione.

**Per L&#39;Opzione C (Ibrida):**
Crea una singola connessione con tutti i set di dati B2B. Utilizza l’ID account come identificatore principale. La vista incentrata sulla persona verrà creata nella fase 2 utilizzando una configurazione diversa della vista dati sulla stessa connessione.

**Documentazione di Experience League:**

- [Panoramica delle connessioni](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Creare o modificare una connessione](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Gestire le connessioni](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)
- [Panoramica di CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### Fase 2: configurazione della visualizzazione dati dell’account

**Funzione applicazione:** [!DNL CJA] B2B: configurazione visualizzazione dati B2B, [!DNL CJA]: configurazione visualizzazione dati

Configura la visualizzazione dati che definisce la modalità di visualizzazione dei dati di connessione nell’analisi. Per l’analisi B2B, ciò include la configurazione di contenitori specifici per B2B (account, opportunità, gruppo di acquisto), la mappatura dei campi dello schema B2B su dimensioni e metriche, l’impostazione di modelli di attribuzione con intervalli di lookback appropriati per B2B e la creazione di campi derivati per la logica di business B2B.

#### Decisione: configurazione del contenitore

Determina quali contenitori B2B devono essere abilitati e come devono essere denominati.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Account + persona + sessione + evento | B2B standard senza analisi del gruppo di acquisto o dell’opportunità | Gerarchia dei contenitori B2B più semplice. Account è il contenitore principale. |
| Account + opportunità + persona + sessione + evento | È richiesta l’analisi della pipeline e dei ricavi | Aggiunge opportunità come livello contenitore, consentendo l&#39;analisi basata sull&#39;ambito opportunità. |
| Account + Gruppo di acquisto + Opportunità + Persona + Sessione + Evento | Analisi B2B completa, inclusa la composizione del gruppo di acquisto | Più completo. Consente l’analisi a ogni livello del modello dati B2B. |
| Account globale + account + persona + sessione + evento | Analisi della gerarchia di conti globale | Aggiunge Account globale come contenitore di livello più alto al di sopra di Account. |

#### Decisione: modello di attribuzione per le metriche B2B

Determina quale modello di attribuzione deve essere il predefinito per le metriche di conversione.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Attribuzione lineare (lookback di 13 mesi) | Credito uguale a tutti i punti di contatto nel percorso B2B | Ideale per comprendere l’intera gamma di attività di marketing. Punto di partenza consigliato per il B2B. |
| Attribuzione a forma di U (lookback di 13 mesi) | Enfasi sul primo e ultimo contatto con il credito ai contatti intermedi | Evidenzia i momenti di creazione di lead e conversione di opportunità. Comune nell’analisi della generazione della domanda. |
| Decadimento nel tempo (lookback di 13 mesi) | I punti di contatto più recenti dovrebbero ricevere più credito | Consigliato quando l&#39;attualità del coinvolgimento è un segnale importante per la fattibilità. |
| Ultimo contatto | Reporting semplice del punto di contatto finale prima della conversione | Facile da capire, ma sottovaluta il marketing nelle fasi iniziali. Utilizzare solo per la creazione rapida di report operativi. |

#### Decisione: definizione della sessione per B2B

Determina come definire le sessioni per il coinvolgimento B2B.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Timeout di 30 minuti (impostazione predefinita) | Comportamento della sessione di analisi web standard | Standard per l’analisi del coinvolgimento web. Possono frammentare le sessioni di utilizzo dei contenuti lunghe. |
| Timeout esteso (60-120 minuti) | Gli utenti B2B partecipano a sessioni di ricerca più lunghe | Gli acquirenti B2B spesso dedicano molto tempo alla revisione di contenuti tecnici, prezzi e documentazione. |
| Nuova sessione basata su eventi | Eventi specifici devono sempre avviare una nuova sessione | Da utilizzare quando i click-through di campagne o le richieste demo devono sempre iniziare una nuova sessione di analisi. |

#### Configurare la visualizzazione dati dell’account

**Navigazione interfaccia utente:** [!DNL Customer Journey Analytics] > Visualizzazioni dati > Crea nuova visualizzazione dati

Dettagli configurazione chiave:

- Selezionare la connessione creata nella fase 1
- Configura il fuso orario e il tipo di calendario appropriati per l’organizzazione
- Rinominare i contenitori in terminologia rilevante per B2B (ad esempio Account/Coinvolgimento/Punto di contatto)
- Mappa i campi dello schema B2B alle dimensioni: nome account, ID account, settore, dimensioni società, livello account, proprietario account, fase opportunità, valore opportunità, ruolo gruppo di acquisto, interesse soluzione
- Mappare le metriche di coinvolgimento: eventi (occorrenze), persone, sessioni, visualizzazioni di pagina, invii di moduli, aperture di e-mail, clic su e-mail
- Configurare la persistenza per le dimensioni chiave (ad esempio, il settore dell’account persiste a livello di account)
- Imposta l’attribuzione su lineare con un lookback di 13 mesi come predefinito per le metriche di conversione
- Creare campi derivati per la classificazione del canale di marketing, i livelli di punteggio del coinvolgimento e il raggruppamento delle fasi dell’opportunità

**Opzioni divergenti:**

**Per L&#39;Opzione A (Incentrata Sull&#39;Account):**
Configura una singola visualizzazione dati con Account come contenitore principale. Includi i contenitori Opportunità e Gruppo di acquisto se sono necessarie l’analisi della pipeline e del gruppo di acquisto.

**Per L&#39;Opzione B (Global Account-Centric):**
Configura Account globale come contenitore principale. Includi conto come contenitore secondario per abilitare l&#39;analisi globale e secondaria.

**Per L&#39;Opzione C (Ibrida):**
Crea due visualizzazioni dati dalla stessa connessione. La visualizzazione dati 1 utilizza Persona come contenitore primario (comportamento standard [!DNL CJA]). Nella visualizzazione dati 2, Account è utilizzato come contenitore principale con contenitori B2B. Mappa metriche identiche a entrambe le viste, se applicabile.

**Documentazione di Experience League:**

- [Panoramica delle visualizzazioni dati](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Creare o modificare una visualizzazione dati](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Panoramica delle impostazioni dei componenti](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Impostazioni persistenza](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Impostazioni di attribuzione](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Campi derivati](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [Impostazioni di sessione](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)

### Fase 3: analisi Workspace

**Funzione dell&#39;applicazione:** [!DNL CJA] B2B: Analisi Workspace a livello di account, Analisi del gruppo di acquisto, Analisi dell&#39;opportunità, Segmentazione B2B, Attribuzione B2B, [!DNL CJA]: Analisi Workspace, Creazione di metriche calcolate, Analisi guidata

Crea progetti Workspace che forniscano le informazioni analitiche definite negli indicatori KPI. Questa fase include la creazione di tabelle a forma libera con dimensioni e metriche B2B, la creazione di metriche calcolate per i KPI B2B, la configurazione di visualizzazioni specifiche per B2B (flusso a livello di account, funnel delle opportunità, coinvolgimento dei gruppi di acquisto), la creazione di filtri/segmenti utilizzando contenitori B2B e l’applicazione di modelli di attribuzione B2B.

#### Decisione: struttura di Analysis Workspace

Determina come deve essere organizzato il progetto Workspace.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Singolo progetto completo con più pannelli | Piccolo team, tutte le parti interessate visualizzano gli stessi rapporti | Manutenzione più semplice. Utilizza i pannelli per separare gli argomenti (coinvolgimento, pipeline, attribuzione). Fino a 40 pannelli per progetto. |
| Progetti mirati multipli per pubblico | Le diverse parti interessate hanno bisogno di punti di vista diversi | Il marketing ottiene coinvolgimento/attribuzione. Vendite ottiene lo stato della pipeline/account. Le operazioni ottengono la qualità dei dati. Maggiore manutenzione, ma più mirato. |
| Progetti basati su modelli con analisi guidata | Analisi self-service per utenti non esperti | Utilizza l’analisi guidata per le viste funnel e tendenze. Salva come modelli per analisi ripetibili. Ideale per una vasta adozione. |

#### Decisione: metriche calcolate B2B

Determina quali metriche calcolate sono necessarie per i KPI B2B.

| Metrica | Formula | Quando creare |
| --- | --- | --- |
| Tasso di coinvolgimento dell’account | (Eventi conto totali / Account totali) | Sempre: metrica B2B di base |
| % completezza gruppo acquisti | (Ruoli occupati / Ruoli richiesti) * 100 | Quando si acquista un&#39;analisi di gruppo nell&#39;ambito |
| Conversione da account a opportunità | Account con opportunità / Account coinvolti | Quando è necessaria l’analisi della pipeline |
| Influenza pipeline % | Valore pipeline influenzato/Valore pipeline totale | Quando è richiesta l’attribuzione marketing |
| Coinvolgimento medio per contatto | Eventi / Persone univoche per account | Quando è necessaria l’analisi della penetrazione dell’account |
| Coinvolgimento contenuti per ruolo | Eventi filtrati per Ruolo gruppo di acquisto | Quando è necessaria l’ottimizzazione dei contenuti per B2B |

#### Decisione: ambito filtro/segmento B2B

Determina a quale livello di contenitore devono essere creati i filtri.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Filtri a livello di account | Analisi definita in base ai criteri di corrispondenza dei conti (ad esempio, conti aziendali, settori specifici) | Include tutti gli eventi dagli account idonei. Più comune per il B2B. |
| Filtri a livello di opportunità | Analisi con ambito a tipi o fasi di opportunità specifici | Include tutti gli eventi associati alle opportunità di qualificazione. |
| Acquisto di filtri a livello di gruppo | Analisi con ambito a specifici stati dei gruppi di acquisto | Include eventi da persone nei gruppi di acquisto idonei. |
| Filtri a livello di persona | Analisi definita in base ai singoli criteri di corrispondenza (ad esempio, ruoli specifici, titoli) | Comportamento del filtro standard. Utilizzare per analizzare il coinvolgimento individuale all’interno del contesto B2B. |

#### Generare l’analisi dell’area di lavoro

**Navigazione interfaccia utente:** [!DNL Customer Journey Analytics] > Workspace > Progetti > Crea progetto

Dettagli configurazione chiave:

- Seleziona la visualizzazione dati B2B creata nella fase 2
- Creare tabelle a forma libera con dimensioni a livello di account (nome account, settore, livello) suddivise per metriche di coinvolgimento
- Creare visualizzazioni funnel delle opportunità che mostrano la progressione delle opportunità attraverso le fasi
- Creare tabelle di composizione del gruppo di acquisto che mostrano i tassi di riempimento dei ruoli e il coinvolgimento per ruolo
- Configurare i pannelli di attribuzione B2B confrontando i modelli di attribuzione (lineare, a forma di U, con decadimento temporale) con un lookback di 13 mesi
- Creare visualizzazioni del flusso di account che mostrino i percorsi comuni attraverso il percorso di acquisto
- Creare tabelle coorte per analizzare la conservazione e il coinvolgimento degli account nel tempo
- Applicare filtri B2B all’analisi dei segmenti per livello di account, settore o livello di coinvolgimento
- Creare annotazioni per eventi significativi (lanci di campagne, rilasci di prodotti, modifiche dei prezzi)

**Documentazione di Experience League:**

- [Panoramica di Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Creare un progetto](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Tabella a forma libera](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Pannello Attribuzione](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Visualizzazione del flusso](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Visualizzazione Abbandono](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Tabella coorte](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Panoramica sui filtri](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Panoramica delle metriche calcolate](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Creare metriche calcolate](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Panoramica delle annotazioni](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Panoramica dell’analisi guidata](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Dimensioni di raggruppamento](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

### Fase 4: pubblicazione del dashboard

**Funzione applicazione:** [!DNL CJA]: pubblicazione dashboard e scorecard, [!DNL CJA]: pubblicazione pubblico

Crea dashboard condivisibili e scorecard per dispositivi mobili che forniscano informazioni analitiche B2B alle parti interessate. Questa fase copre anche la pubblicazione in AEP di tipi di pubblico B2B definiti da [!DNL CJA] per l&#39;attivazione in casi di utilizzo a valle, come l&#39;attivazione di un pubblico B2B.

#### Decisione: metodo di consegna del dashboard

Determina in che modo gli approfondimenti di analisi B2B devono essere forniti alle parti interessate.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Progetto Workspace (desktop) | Analisti e operazioni di marketing che necessitano di esplorazione interattiva | Interattività completa, drill-down, attivazione/disattivazione dei filtri. Richiede l&#39;accesso [!DNL CJA]. |
| Scorecard per dispositivi mobili | Dirigenti e responsabili vendite che necessitano di KPI immediati | Numeri di riepilogo con linee di tendenza. Accessibile tramite l&#39;app delle dashboard [!DNL Adobe Analytics]. Interattività limitata. |
| Esportazione PDF/CSV pianificata | Le parti interessate senza accesso [!DNL CJA] che necessitano di aggiornamenti regolari | Consegna automatizzata secondo una pianificazione. Nessuna interattività. Consigliato per i riepiloghi settimanali/mensili. |
| Tutti i precedenti | Grandi organizzazioni con diverse esigenze delle parti interessate | Portata massima. Manutenzione più efficiente. Consigliato per programmi di analisi B2B maturi. |

#### Decisione: pubblicazione del pubblico da [!DNL CJA]

Determina se i segmenti B2B devono essere pubblicati in AEP per l’attivazione.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Pubblicare tipi di pubblico basati sull’account | Le informazioni di Analytics devono informare il targeting e l’eliminazione | Abilita l&#39;attivazione dei segmenti definiti da [!DNL CJA] (ad esempio, &quot;account altamente coinvolti senza opportunità aperte&quot;) tramite [!DNL RT-CDP]. Frequenza di aggiornamento: da 4 ore a una settimana. |
| Non pubblicare | Analytics è solo per il reporting, non per l&#39;attivazione | Configurazione più semplice. Attivazione gestita separatamente in [!DNL RT-CDP]. |

#### Pubblicare dashboard e tipi di pubblico

**Navigazione interfaccia utente:** [!DNL Customer Journey Analytics] > Progetti > Condividi (per Workspace), Progetti > Crea > Scorecard per dispositivi mobili (per le scorecard), Componenti > Tipi di pubblico > Pubblica (per la pubblicazione di tipi di pubblico)

Dettagli configurazione chiave:

- Creare dashboard esecutivi con numeri di riepilogo per i KPI B2B chiave (account coinvolti totali, valore della pipeline, completezza del gruppo di acquisto)
- Configurare i periodi di confronto (mese su mese, trimestre su trimestre) per gli indicatori di tendenza
- Creare scorecard per dispositivi mobili con riquadri per il coinvolgimento dell’account, l’integrità della pipeline e le metriche di attribuzione
- Aggiungere filtri per consentire ai dirigenti di attivare o disattivare le visualizzazioni per area geografica, settore o livello account
- Configurare la consegna pianificata del progetto per i report esecutivi settimanali
- Per la pubblicazione di tipi di pubblico: seleziona il filtro B2B, configura lo spazio dei nomi delle identità (ID account) e imposta la frequenza di aggiornamento

**Documentazione di Experience League:**

- [Crea una scorecard per dispositivi mobili](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Condividi progetti](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Programmare progetti](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Configurare e curare le scorecard](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Dashboard di Adobe Analytics: guida esecutiva](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Panoramica di Audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Creare e pubblicare tipi di pubblico](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)

## Considerazioni sull’implementazione

Le sezioni seguenti descrivono i guardrail, le insidie comuni, le best practice e le decisioni di compromesso da tenere presenti durante l’implementazione.

### Guardrail e limiti

- [!DNL CJA] connessioni possono includere set di dati da una sola sandbox AEP — [guardrail CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)
- Massimo 5.000 dimensioni e 5.000 metriche per visualizzazione dati
- Massimo 100 campi derivati per visualizzazione dati
- L’attribuzione B2B supporta intervalli di lookback fino a 13 mesi per l’analisi a livello di account
- Massimo di 75 tipi di pubblico pubblicati per cliente [!DNL CJA] in tutte le sandbox
- La frequenza minima di aggiornamento della pubblicazione del pubblico è ogni 4 ore
- La latenza di streaming da AEP a [!DNL CJA] è in genere inferiore a 90 minuti
- Le tabelle a forma libera supportano fino a 10 analisi approfondite delle dimensioni
- Le scorecard per dispositivi mobili supportano fino a 16 sezioni per scorecard
- I progetti Workspace supportano fino a 40 pannelli per progetto
- Il completamento della retrocompilazione per set di dati B2B di grandi dimensioni (miliardi di record) può richiedere giorni

### Insidie comuni

- **Mappatura persona-account incompleta:** Se gli eventi a livello di persona non possono essere associati a un account, non verranno visualizzati nell&#39;analisi a livello di account. Assicurati che tutti i set di dati evento includano un campo che possa essere unito all’ID account, direttamente o tramite un set di dati di ricerca di relazioni persona-account. Prima di creare l’analisi, controlla la percentuale di eventi con associazione account mancante.
- **Designazione tipo set di dati errata:** i set di dati di ricerca B2B (opportunità, gruppo di acquisto, relazioni persona-account) devono essere correttamente designati come tipo di ricerca o profilo nella connessione [!DNL CJA]. La digitazione errata di un set di dati di ricerca come set di dati evento produrrà risultati non corretti perché [!DNL CJA] tenterà di trattare ogni record come un evento con marca temporale.
- **Finestra di attribuzione troppo breve per B2B:** Se si utilizzano finestre di attribuzione predefinite di 30 giorni, nei percorsi B2B i punti di contatto in fase iniziale non verranno raggiunti dopo 6-18 mesi. Configura sempre intervalli di lookback di 13 mesi per le metriche di attribuzione B2B.
- **La combinazione errata delle metriche a livello di account e di persona:** Contare le &quot;persone&quot; in un&#39;analisi a livello di account può essere fuorviante. Assicurati che le metriche calcolate siano definite al livello del contenitore appropriato. Un &quot;tasso di coinvolgimento dell’account&quot; deve utilizzare gli eventi a livello di account divisi per account, non per persone.
- **Dati del gruppo di acquisto non aggiornati:** La composizione del gruppo di acquisto e le assegnazioni di ruolo cambiano nel tempo. Se i set di dati di gruppo di acquisto non vengono aggiornati regolarmente, le metriche di completezza non saranno accurate. Verificare che il sistema di origine ([!DNL Marketo Engage] o [!DNL AJO] B2B edition) sincronizzi attivamente i dati del gruppo di acquisto.
- **Il sovraccarico di un singolo progetto area di lavoro:** l&#39;analisi B2B si estende su gruppi di coinvolgimento, pipeline, attribuzione e acquisto. Il tentativo di inserire tutto in un progetto causa un caricamento lento e confonde la navigazione. Utilizza più progetti mirati o pannelli chiaramente etichettati.

### Best practice

- Iniziare con l&#39;opzione A (incentrata sull&#39;account) anche se si prevede di utilizzare l&#39;opzione B (account globale) in un secondo momento. L’analisi incentrata sull’account è più semplice e convalida il modello dati prima di aggiungere complessità alla gerarchia.
- Crea un progetto Workspace dedicato alla &quot;Qualità dei dati B2B&quot; che tenga traccia della percentuale di eventi con associazione dell’account, del numero di account orfani e delle metriche di completezza del gruppo di acquisto. Esegui questa settimana per rilevare in anticipo i problemi relativi ai dati.
- Utilizza i campi derivati per creare livelli di punteggio di coinvolgimento (High/Medium/Low) in base ai conteggi degli eventi a livello di account. Questo semplifica l’analisi e rende le dashboard più fruibili per gli interessati non tecnici.
- Quando configuri l’attribuzione B2B, inizia con l’attribuzione lineare come base, quindi confronta con modelli a forma di U e a decadimento temporale. Le differenze tra i modelli spesso rivelano se il mix di marketing è ponderato verso le attività di consapevolezza o conversione.
- Pubblica una scorecard mobile &quot;B2B Executive Summary&quot; con non più di 8 sezioni che coprono i KPI più importanti per la leadership. Mantieni l&#39;attenzione: le scorecard manageriali dovrebbero rispondere a &quot;Come va?&quot; non &quot;Perché?&quot;
- Annota eventi chiave (lanci di prodotti, lanci di campagne principali, modifiche dei prezzi, modifiche dei processi di vendita) per fornire contesto per le tendenze dei dati. I dati B2B mostrano spesso picchi e ribassi che sono inspiegabili senza il contesto degli eventi.
- Quando si pubblicano tipi di pubblico B2B da [!DNL CJA], utilizzare l&#39;aggiornamento giornaliero per i segmenti di attivazione standard e l&#39;aggiornamento di 4 ore solo per i segmenti sensibili al tempo. Gli aggiornamenti frequenti utilizzano risorse di elaborazione.

### Decisioni di compromesso

>[!NOTE]
>Le seguenti decisioni di compromesso devono essere valutate in base ai requisiti e ai vincoli specifici dell’organizzazione.

**Completezza dei dati rispetto alla precisione analitica**

L’inclusione di tutti gli eventi a livello di persona nell’analisi dell’account (anche quelli con un’associazione dell’account debole) migliora la completezza dei dati, ma può ridurre l’accuratezza dell’analisi se la mappatura dell’account non è affidabile.

- **Inclusi tutti i favori degli eventi:** Misurazione del coinvolgimento completa, punteggi di coinvolgimento dell&#39;account più elevati, visibilità più ampia
- **Esclusione di eventi senza corrispondenza favorisce:** metriche precise a livello di account, attribuzione affidabile, correlazione affidabile della pipeline
- **Consiglio:** escludere eventi senza corrispondenza dall&#39;analisi a livello di account, ma includerli in una visualizzazione dati a livello di persona separata (opzione C) per comprendere l&#39;immagine completa. Assegna le priorità al miglioramento della qualità dei dati di associazione dell’account come flusso di lavoro parallelo.

**Lunghezza intervallo di lookback dell&#39;attribuzione B2B**

Intervalli di lookback più lunghi (13 mesi) acquisiscono più punti di contatto, ma possono includere attività di marketing che non sono più rilevanti per la decisione di acquisto corrente.

- **Un lookback più lungo (13 mesi) favorisce:** l&#39;acquisizione dell&#39;intero percorso B2B, l&#39;accreditamento delle attività di fase di consapevolezza, l&#39;adattamento a lunghi cicli di vendita
- **Un lookback più breve (6 mesi) favorisce:** Concentrarsi sul coinvolgimento recente, riducendo il rumore dai vecchi punti di contatto, riflettendo meglio l&#39;attuale intento di acquisto
- **Consiglio:** utilizzare un lookback di 13 mesi per gli account aziendali con cicli di vendita lunghi (oltre 12 mesi). Utilizza un lookback di 6 mesi per gli account di fascia media con cicli più brevi. Crea metriche calcolate separate per ogni finestra da confrontare.

**Visualizzazione dati completa singola rispetto a più visualizzazioni dati mirate**

Una visualizzazione dati con tutti i contenitori e le dimensioni B2B è più semplice da gestire, ma può sopraffare gli analisti con complessità. Le visualizzazioni dati incentrate su più elementi (coinvolgimento, pipeline, attribuzione) sono più facili da utilizzare ma più difficili da mantenere.

- **La visualizzazione singola favorisce:** coerenza, manutenzione semplificata, analisi tra domini diversi all&#39;interno di un singolo progetto
- **Viste multiple a favore:** Semplicità per gli analisti, tempi di caricamento più rapidi, elenchi di componenti personalizzati per caso d&#39;uso
- **Consiglio:** inizia con un&#39;unica visualizzazione dati completa. Se gli analisti segnalano difficoltà nel trovare le dimensioni e le metriche corrette, crea gruppi di componenti curati all’interno della stessa vista prima di suddividerli in più viste. Utilizza i modelli di Workspace per guidare gli analisti verso i componenti giusti.

## Documentazione correlata

Le risorse seguenti forniscono informazioni aggiuntive per l’implementazione di questo modello di caso d’uso.

**[!DNL CJA]B2B edition**

- [Panoramica di CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Guardrail CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

**Connessioni**

- [Panoramica delle connessioni](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Creare o modificare una connessione](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Gestire le connessioni](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)

**Visualizzazioni dati**

- [Panoramica delle visualizzazioni dati](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Creare o modificare una visualizzazione dati](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Panoramica delle impostazioni dei componenti](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Impostazioni persistenza](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Impostazioni di attribuzione](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Impostazioni formato](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Campi derivati](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [Impostazioni di sessione](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)

**Workspace e analisi**

- [Panoramica di Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Creare un progetto](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Tabella a forma libera](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Visualizzazione del flusso](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Visualizzazione Abbandono](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Tabella coorte](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Pannello Attribuzione](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Condividi progetti](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Programmare progetti](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Dimensioni di raggruppamento](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

**Componenti**

- [Panoramica sui filtri](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Creare filtri](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Panoramica delle metriche calcolate](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Creare metriche calcolate](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Panoramica delle annotazioni](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Intervalli di date](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

**Tipi di pubblico**

- [Panoramica di Audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Creare e pubblicare tipi di pubblico](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [Gestire i tipi di pubblico](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)

**Dashboard e scorecard**

- [Crea una scorecard per dispositivi mobili](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Configurare e curare le scorecard](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Dashboard di Adobe Analytics: guida esecutiva](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)

**Analisi guidata**

- [Panoramica dell’analisi guidata](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Vista funnel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Visualizzazione tendenze](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Vista Mantenimento](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

**[!DNL RT-CDP]B2B edition**

- [Panoramica di RT-CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#702702)
- [Schemi B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Panoramica sulle origini B2B](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/sources/b2b)

**AEP data foundation**

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Panoramica sulle origini](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Connettore Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home)

**Governance dei dati e ciclo di vita**

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

**Tutorial e guide**

- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Panoramica di Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
