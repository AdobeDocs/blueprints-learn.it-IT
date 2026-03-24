---
title: Audience Collaboration
description: Scopri come condividere e abbinare i segmenti di pubblico tra sandbox o organizzazioni utilizzando Segment Match.
solution: Real-Time Customer Data Platform, Experience Platform
exl-id: 7014849c-5e32-4ec3-a531-c0e8ce896f44
source-git-commit: 27f7e230982807ec70ca96af7f737944a6588f27
workflow-type: tm+mt
source-wordcount: '6232'
ht-degree: 1%

---

# Audience Collaboration

Questa guida fornisce un riferimento completo all&#39;implementazione per la collaborazione tra i tipi di pubblico utilizzando [!DNL Segment Match] in [!DNL Real-Time CDP] e [!DNL Adobe Experience Platform]. È progettato per architetti di soluzioni, tecnici di marketing e ingegneri di implementazione che devono condividere e abbinare segmenti di pubblico tra sandbox o organizzazioni in modo sicuro per la privacy.

Utilizzare questo piano per comprendere gli approcci disponibili, valutare i compromessi e navigare in [!DNL Adobe Experience League] per istruzioni di configurazione dettagliate.

[!DNL Segment Match] consente a due o più organizzazioni di [!DNL Experience Platform] (o sandbox all&#39;interno di un&#39;organizzazione) di collaborare ai dati del pubblico condividendo le informazioni sull&#39;appartenenza ai segmenti senza esporre i dati PII sottostanti. I partecipanti possono stimare la sovrapposizione, condividere i tipi di pubblico e attivare i profili corrispondenti nelle destinazioni a valle.

## Panoramica del caso d’uso

Le organizzazioni devono collaborare sempre più spesso ai dati sul pubblico con partner, filiali o tra unità aziendali, mantenendo al contempo rigidi controlli sulla privacy. La collaborazione con il pubblico soddisfa questa esigenza abilitando la condivisione sicura dei segmenti tramite [!DNL Segment Match], una funzionalità all&#39;interno di [!DNL Real-Time CDP] che consente a due o più organizzazioni [!DNL Experience Platform] (o sandbox) di scambiare informazioni sull&#39;appartenenza al pubblico utilizzando identificatori hash e sicuri per la privacy.

In genere, lo scenario aziendale coinvolge un’organizzazione (il mittente) che ha creato un segmento di pubblico prezioso e desidera condividerlo con un’organizzazione partner (il destinatario) per il targeting, la soppressione o l’arricchimento congiunti. Prima della condivisione, entrambe le parti possono stimare la sovrapposizione del pubblico per valutarne il valore. Una volta condiviso, l’organizzazione ricevente può attivare il pubblico corrispondente tramite le proprie destinazioni.

Questo modello è distinto dall’attivazione standard del pubblico perché funziona tra organizzazioni o sandbox anziché verso destinazioni esterne di pubblicità o marketing. Si distingue inoltre dalle clean room di dati o dalle piattaforme di collaborazione di terze parti perché opera in modalità nativa nell&#39;ecosistema Adobe utilizzando l&#39;infrastruttura di identità [!DNL Experience Platform].

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### Acquisire nuovi clienti

Espandi la base di clienti tramite campagne di acquisizione mirate, tipi di pubblico simili e ottimizzazione di contenuti multimediali a pagamento. La collaborazione tra i tipi di pubblico consente alle organizzazioni di individuare nuovi pool di potenziali clienti confrontando i segmenti con quelli dei partner, identificando sovrapposizioni di alto valore e raggiungendo nuovi clienti attraverso l’attivazione congiunta.

- **KPI:** nuovi clienti, costo acquisizione cliente, conversione potenziali clienti/lead
- [Acquisire nuovi clienti](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Riduzione dei costi di acquisizione dei clienti

Migliora l’efficienza del targeting, elimina i clienti esistenti dalle campagne di acquisizione e ottimizza la spesa per i contenuti multimediali. Condividendo segmenti di soppressione tra organizzazioni o unità aziendali, i team possono evitare sprechi di spesa sui clienti già convertiti e concentrare il budget su nuovi potenziali clienti.

- **KPI:** Costo Acquisizione Cliente, Costo Per Lead, Efficienza
- [Riduzione dei costi di acquisizione dei clienti](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### Ottimizzazione della spesa di marketing e del ROI

Migliora il ritorno sull’investimento marketing migliorando il targeting, l’attribuzione, l’eliminazione del pubblico e l’allocazione del budget. [!DNL Segment Match] consente l’eliminazione dei tipi di pubblico tra organizzazioni e il targeting congiunto che riduce la duplicazione e migliora la precisione.

- **KPI:** Risparmio sui costi, Costo di acquisizione cliente, Ricavi incrementali
- [Ottimizzazione della spesa di marketing e del ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Esempi di casi d’uso tattici

- **Corrispondenza pubblico editore-inserzionista**: un brand condivide il proprio segmento di clienti di alto valore con un editore di contenuti multimediali per stimare la sovrapposizione e indirizzare gli utenti con annunci personalizzati, migliorando la rilevanza della campagna senza esporre i dati PII.
- **Eliminazione cross-brand all&#39;interno di una holding**: più marchi di un&#39;organizzazione principale condividono segmenti di clienti per eliminare i clienti esistenti dei marchi secondari dalle campagne di acquisizione, riducendo gli sprechi pubblicitari.
- **Arricchimento dell&#39;audience di Retail Media Network**: un retailer condivide segmenti basati sull&#39;acquisto con i partner del marchio CPG, consentendo ai brand di rivolgersi ad acquirenti comprovati sulla rete multimediale retailer con tassi di conversione più elevati.
- **Individuazione del pubblico di partner di co-marketing**: due marchi non concorrenti valutano la sovrapposizione del pubblico per valutare il potenziale di partnership prima di lanciare una campagna congiunta, utilizzando la stima di sovrapposizione per convalidare l&#39;allineamento del pubblico.
- **Condivisione dei segmenti di collaborazione dati**: le organizzazioni di una cooperativa dati condividono segmenti di pubblico con hash per espandere la portata del targeting mantenendo al contempo la conformità alla privacy e i controlli di governance dei dati.
- **Federazione di pubblico con più sandbox**: un&#39;azienda globale condivide segmenti di pubblico con sandbox regionali per consentire un targeting coerente dei clienti nei diversi mercati nel rispetto dei requisiti di residenza dei dati regionali.
- **Attivazione tra partner del programma fedeltà**: una coalizione di fidelizzazione condivide segmenti di livello fedeltà con i commercianti partecipanti, in modo che ogni partner possa offrire promozioni appropriate alla base clienti condivisa.
- **Collaborazione per la misurazione e l&#39;attribuzione**: un inserzionista condivide un segmento di conversione con un partner multimediale in modo che il partner possa misurare l&#39;efficacia della campagna confrontando gli utenti esposti con i convertitori.

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare il successo delle implementazioni di collaborazione tra tipi di pubblico.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Percentuale di sovrapposizione pubblico | Percentuale di profili nel segmento condiviso che corrispondono tra mittente e destinatario | [!DNL Segment Match] rapporto di stima sovrapposizione |
| Dimensione del pubblico corrispondente | Numero di profili con corrispondenza riuscita e disponibili per l’attivazione | Stato di condivisione e conteggio della popolazione di [!DNL Segment Match] |
| Nuova acquisizione di clienti da tipi di pubblico corrispondenti | Nuovi clienti acquisiti tramite campagne indirizzate a segmenti corrispondenti | Tracciamento delle conversioni nelle campagne che utilizzano tipi di pubblico corrispondenti |
| Riduzione dei costi di acquisizione dei clienti | Diminuzione del costo per acquisizione quando si utilizza un pubblico corrispondente rispetto al targeting ampio | Analisi dei costi della campagna confrontando le prestazioni del pubblico corrispondenti e non corrispondenti |
| Risparmi di eliminazione | Risparmio sui costi dei contenuti multimediali grazie alla rimozione dei clienti noti dalle campagne di acquisizione | Confronto delle spese dei supporti di pre/post-soppressione |
| Incremento delle prestazioni della campagna | Miglioramento del tasso di conversione, del tasso di click-through o del coinvolgimento per le campagne che utilizzano tipi di pubblico corrispondenti | Test A/B di confronto tra campagne per il pubblico e il controllo |
| Time to Collaboration | Tempo trascorso dall’avvio della condivisione dei segmenti alla preparazione all’attivazione | [!DNL Segment Match] timestamp del flusso di lavoro |

## Schema del caso d’uso

Questo caso d’uso segue il pattern di Audience Collaboration.

Condividi e abbina segmenti di pubblico tra sandbox o organizzazioni utilizzando [!DNL Segment Match].

**Catena di funzioni:** Selezione segmenti > Configurazione corrispondenza > Stima sovrapposizione > Condivisione pubblico > Attivazione

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Real-Time CDP]** - Fornisce la funzionalità [!DNL Segment Match] per la condivisione del pubblico sicura per la privacy, la valutazione del pubblico per la creazione di segmenti e l&#39;attivazione della destinazione per l&#39;utilizzo a valle dei tipi di pubblico corrispondenti.
- **[!DNL Adobe Experience Platform]**: fornisce l&#39;infrastruttura di dati di base, tra cui la risoluzione delle identità, l&#39;unificazione dei profili, la governance dei dati e l&#39;applicazione del consenso da cui dipende [!DNL Segment Match].

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve essere al suo posto | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Obbligatorio | Sia l’organizzazione del mittente che quella del destinatario devono disporre di sandbox con ruoli e autorizzazioni appropriati. Gli utenti che gestiscono [!DNL Segment Match] devono disporre delle autorizzazioni per visualizzare e condividere segmenti, configurare connessioni e gestire feed dei partner. I criteri ABAC devono essere configurati per controllare quali utenti possono avviare e accettare condivisioni di segmenti. | [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/it/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Presunto sul posto | Devono esistere schemi XDM per profili ed eventi con i gruppi di campi richiesti. I set di dati profilo ed evento devono essere creati e abilitati per [!DNL Real-Time Customer Profile]. Il modello dati deve supportare gli spazi dei nomi di identità utilizzati per la corrispondenza dei segmenti (in genere e-mail con hash o telefono con hash). | [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Origini dati e raccolta | Presunto sul posto | I dati del cliente devono fluire attivamente in [!DNL Experience Platform] tramite origini dati configurate (SDK, connettori di origine, acquisizione batch). I profili devono essere compilati con i tipi di identità utilizzati per [!DNL Segment Match] (ad esempio, e-mail con hash). | [Panoramica origini](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Configurazione identità e profilo | Obbligatorio | Gli spazi dei nomi delle identità devono essere configurati per gli identificatori utilizzati nella corrispondenza dei segmenti. Sia il mittente che il destinatario devono utilizzare spazi dei nomi di identità compatibili. I criteri di unione devono essere configurati in modo da unificare correttamente i profili. È opportuno stabilire regole di collegamento delle identità per garantire una risoluzione accurata del profilo. | [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home) |
| Definizione e segmentazione del pubblico | Obbligatorio | I tipi di pubblico di Source devono essere definiti e valutati prima di poter essere condivisi tramite [!DNL Segment Match]. I tipi di pubblico devono essere generati utilizzando [!DNL Segment Builder] o [!DNL Audience Composition] con la valutazione batch completata. Solo i tipi di pubblico valutati in batch sono idonei per la condivisione [!DNL Segment Match]. | [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Consigliato | Attributi calcolati come il valore di acquisto del ciclo di vita, il punteggio di coinvolgimento o l’affinità di prodotto possono creare segmenti più precisi da condividere. Segmenti di input di qualità superiore portano a una collaborazione più preziosa tra il pubblico. | [Panoramica attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Consigliato | Le policy di conservazione dei dati e del consenso garantiscono che i segmenti condivisi siano conformi alle normative sulla privacy. I criteri di scadenza dei set di dati consentono di gestire il ciclo di vita dei dati sul pubblico ricevuti. L’applicazione del consenso impedisce la condivisione di profili che hanno rinunciato. | [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Etichettatura e applicazione dell’utilizzo dati | Incluso | I criteri di governance dei dati devono essere valutati prima di condividere i segmenti per garantire la conformità. Le etichette sui campi di identità e gli attributi del profilo determinano cosa può essere condiviso. L’applicazione della governance impedisce l’inclusione di dati non autorizzati nelle condivisioni di segmenti. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home) |
| Monitoraggio e osservabilità | Consigliato | Il monitoraggio del processo di condivisione [!DNL Segment Match], dei processi di stima della sovrapposizione e dei flussi di dati di attivazione consente di rilevare gli errori in anticipo. Gli avvisi possono essere configurati per errori di condivisione o percentuali di corrispondenza inaspettatamente basse. | [Panoramica di Observability Insights](https://experienceleague.adobe.com/it/docs/experience-platform/observability/home) |
| Reporting e analisi | Consigliato | La misurazione delle prestazioni delle campagne che utilizzano tipi di pubblico corrispondenti convalida il valore della collaborazione. [!DNL Customer Journey Analytics] l’analisi può confrontare le prestazioni della campagna pubblico corrispondenti con quelle dei gruppi di controllo. | [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Real-Time CDP]

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Valutazione del pubblico | Fase 1: Selezione e preparazione dei segmenti | Valuta l&#39;appartenenza al segmento utilizzando la valutazione in batch per produrre i tipi di pubblico che verranno condivisi tramite [!DNL Segment Match] |
| Composizione del pubblico | Fase 1: Selezione e preparazione dei segmenti | Facoltativamente, comporre tipi di pubblico derivati (classificazione, suddivisione, esclusione, arricchimento) per creare segmenti più mirati per la condivisione |
| Applicazione del consenso e della governance | Fase 2: configurazione e governance corrispondenti | Applica i criteri di utilizzo dei dati e le preferenze di consenso prima di condividere i segmenti per garantire la conformità |
| Audience Activation | Fase 5: Audience Activation corrispondente | Pubblica i tipi di pubblico corrispondenti ricevuti tramite [!DNL Segment Match] su destinazioni esterne per l&#39;impostazione come destinazione o l&#39;eliminazione |
| Configurazione di destinazione | Fase 5: Audience Activation corrispondente | Configurare connessioni a destinazioni esterne in cui verranno attivati i tipi di pubblico corrispondenti |

## Prerequisiti

- Sia l&#39;organizzazione mittente che quella ricevente dispongono di [!DNL Real-Time CDP] con provisioning con [!DNL Segment Match] diritto
- [!DNL Segment Match] è abilitato per le organizzazioni o le sandbox che partecipano alla collaborazione
- Connessione partner stabilita tra le organizzazioni mittente e ricevente nell&#39;interfaccia utente [!DNL Segment Match]
- Entrambe le organizzazioni utilizzano spazi dei nomi di identità compatibili (ad esempio, entrambe hanno configurato un hash e-mail)
- I tipi di pubblico di Source sono stati definiti e valutati con popolazioni diverse da zero
- I criteri di governance dei dati sono configurati e le etichette di utilizzo dei dati sono applicate ai set di dati e ai campi pertinenti
- Gli utenti di entrambi i lati dispongono delle autorizzazioni necessarie per gestire connessioni, condivisioni e feed [!DNL Segment Match]
- I campi di consenso sono compilati sui profili per abilitare il filtro basato sul consenso prima della condivisione

## Opzioni di implementazione

Le opzioni seguenti descrivono diversi approcci per l&#39;implementazione della collaborazione del pubblico con [!DNL Segment Match]. Seleziona l’opzione che meglio si adatta alla tua struttura organizzativa e ai requisiti di collaborazione.

### Opzione A: condivisione diretta dei segmenti (uno a uno)

Questa opzione è ideale per le partnership bilaterali tra due organizzazioni specifiche, come un inserzionista e un editore, o due marchi in un accordo di co-marketing.

**Funzionamento:**

In una condivisione di segmenti uno-a-uno diretta, l’organizzazione mittente seleziona uno o più tipi di pubblico valutati, avvia una condivisione con un’organizzazione partner specifica e il destinatario accetta la condivisione. La stima di sovrapposizione viene eseguita automaticamente per mostrare a entrambe le parti la percentuale e il volume di profili corrispondenti prima che la condivisione venga finalizzata.

Il mittente definisce gli spazi dei nomi di identità da utilizzare per la corrispondenza e seleziona i segmenti da condividere. Il ricevente rivede la condivisione in ingresso, la accetta e il pubblico corrispondente diventa disponibile nel suo elenco di pubblico per l’attivazione a valle. Viene scambiata solo la sovrapposizione di identità con hash; nessun PII sottostante o dati di attributi di profilo oltrepassa i confini dell’organizzazione.

Si tratta di un approccio semplice che assicura il pieno controllo di entrambe le parti. Il mittente sceglie esattamente cosa condividere e con chi e il destinatario ha la possibilità di accettare o rifiutare ogni condivisione.

**Considerazioni chiave:**

- Richiede una connessione partner esplicita tra le due organizzazioni
- Entrambe le organizzazioni devono concordare spazi dei nomi di identità per la corrispondenza
- La stima di sovrapposizione garantisce trasparenza prima dell&#39;impegno
- Ogni azione deve essere gestita e monitorata singolarmente

**Vantaggi:**

- Flusso di lavoro bilaterale semplice e chiaro
- Piena trasparenza mediante la stima di sovrapposizione prima della condivisione
- Controllo granulare: il mittente sceglie esattamente quali segmenti condividere
- Sicuro per la privacy: per la corrispondenza vengono utilizzati solo identificatori con hash
- Il ricevente può accettare o rifiutare selettivamente le azioni

**Limitazioni:**

- Scalabilità non efficiente quando si collabora con più partner contemporaneamente
- Ogni partnership richiede una configurazione e una gestione separate delle connessioni
- La configurazione di condivisione deve essere ripetuta per ogni nuovo segmento

**Experience League:**

- [Panoramica di Segment Match](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Risoluzione dei problemi di Segment Match](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Opzione B: distribuzione di segmenti con più partner (uno-a-molti)

Questa opzione è ideale per le organizzazioni che devono condividere segmenti con più partner simultaneamente, ad esempio una rete di media al dettaglio che condivide segmenti basati su acquisti con più inserzionisti di marchi o una holding che distribuisce segmenti a marchi di consociate.

**Funzionamento:**

In un modello di distribuzione uno-a-molti, l&#39;organizzazione mittente stabilisce [!DNL Segment Match] connessioni con più organizzazioni partner e condivide lo stesso segmento o segmenti diversi con ognuna di esse. Il mittente gestisce un portfolio di connessioni con i partner e può condividere selettivamente diversi segmenti di pubblico con partner diversi in base alla relazione e al caso d’uso.

Ogni connessione partner opera in modo indipendente: la stima della sovrapposizione, l&#39;accettazione della condivisione e l&#39;attivazione vengono gestite in base al partner. Il mittente può controllare i segmenti ricevuti da ogni partner, consentendo strategie di collaborazione differenziate (ad esempio, i partner premium ricevono segmenti più granulari, i partner standard ne ricevono di più ampi).

Questo approccio utilizza lo stesso meccanismo [!DNL Segment Match] sottostante dell&#39;opzione A, ma lo applica su larga scala con un framework operativo per la gestione di più partnership simultanee.

**Considerazioni chiave:**

- Richiede solidi processi operativi per la gestione di più partnership
- I criteri di governance devono tenere conto della condivisione degli stessi segmenti con più parti esterne
- Ogni partner può utilizzare spazi dei nomi di identità diversi, che richiedono una configurazione flessibile
- I tassi di sovrapposizione variano a seconda del partner e richiedono una valutazione per partner

**Vantaggi:**

- Scalabilità della collaborazione tra i tipi di pubblico in un ecosistema di partner
- Strategie di condivisione differenziate per partner
- Gestione centralizzata di tutte le condivisioni di segmenti in uscita da un&#39;unica organizzazione
- Ogni partnership mantiene una governance indipendente e controlli sul consenso

**Limitazioni:**

- La complessità operativa aumenta con ogni partner aggiuntivo
- Il monitoraggio e la risoluzione dei problemi devono essere eseguiti per partner
- È necessaria una revisione della governance per ogni nuova connessione partner
- I partner non visualizzano i dati o lo stato di condivisione dell&#39;altro

**Experience League:**

- [Panoramica di Segment Match](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-match/overview)

### Opzione C: federazione di pubblico tra sandbox

Questa opzione è indicata per le grandi aziende con più sandbox di [!DNL Experience Platform] (ad esempio sandbox regionali, sandbox specifiche per il brand o sandbox specifiche per l’ambiente) che devono condividere segmenti di pubblico oltre i confini interni senza spostare dati non elaborati.

**Funzionamento:**

Anziché condividere tra organizzazioni diverse, la federazione di tipi di pubblico tra sandbox utilizza [!DNL Segment Match] per condividere segmenti di pubblico tra sandbox all&#39;interno della stessa organizzazione. Questo consente a un team di marketing globale di creare un segmento in una sandbox centrale e condividerlo con sandbox regionali o consente a sandbox specifiche per il brand di condividere tra loro gli elenchi di soppressione.

Il flusso di lavoro rispecchia la condivisione diretta dei segmenti (opzione A), ma funziona all’interno del limite organizzativo. Le connessioni sandbox-sandbox vengono stabilite tramite [!DNL Segment Match] e i segmenti vengono condivisi utilizzando lo stesso processo di corrispondenza sicuro per la privacy. La sandbox ricevente ottiene il pubblico corrispondente come nuovo pubblico che può essere attivato tramite le proprie destinazioni configurate localmente.

Questo approccio è particolarmente utile quando i requisiti di residenza dei dati impediscono lo spostamento di dati grezzi dei clienti tra aree geografiche, ma è consentita la collaborazione a livello di pubblico.

**Considerazioni chiave:**

- Richiede l&#39;adesione [!DNL Segment Match] che supporta la condivisione tra sandbox
- Gli spazi dei nomi delle identità devono essere coerenti tra le sandbox
- I criteri di unione in ciascuna sandbox possono risolvere i profili in modo diverso, influendo potenzialmente sulle percentuali di corrispondenza
- I criteri di governance si applicano in modo indipendente per sandbox

**Vantaggi:**

- Consente la collaborazione tra i tipi di pubblico senza spostare i dati non elaborati tra i limiti della sandbox
- Supporto dei requisiti di residenza dei dati e conformità regionale
- Sfruttamento dell&#39;infrastruttura di identità esistente
- Revisione della governance più semplice, poiché la condivisione avviene all’interno della stessa organizzazione

**Limitazioni:**

- Richiede una configurazione coerente dello spazio dei nomi delle identità nelle sandbox
- Le percentuali di corrispondenza dipendono dalla coerenza dei criteri di unione tra sandbox
- Non soddisfa le esigenze di collaborazione tra organizzazioni diverse
- Per sincronizzare schema e configurazione potrebbe essere necessario disporre di strumenti sandbox

**Experience League:**

- [Panoramica di Segment Match](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home)

### Confronto delle opzioni

La tabella seguente confronta le tre opzioni di implementazione tra i diversi criteri chiave.

| Criteri | Opzione A: Condivisione diretta dei segmenti | Opzione B: Distribuzione multi-partner | Opzione C: federazione tra sandbox |
| --- | --- | --- | --- |
| Ideale per | Partenariati bilaterali | Collaborazione su scala ecosistemica | Condivisione interna tra sandbox |
| Complessi | Bassa | Alta | Medio |
| Numero di partner | 1 | Molti | Sandbox interne |
| Spese generali di governance | Bassa | Alta (valutazione per partner) | Medium (all’interno dell’organizzazione) |
| Gestione operativa | Semplice | Richiede il framework di gestione dei partner | Modera |
| Supporto per la residenza dei dati | N/D | Dipende dalla posizione del partner | Forte |
| Richiede | Configurazione della connessione partner | Più connessioni partner | Sandbox incrociata [!DNL Segment Match] |

### Scegli l’opzione giusta

Per selezionare l’approccio di implementazione appropriato, utilizza le seguenti linee guida decisionali:

1. **Stai collaborando con un&#39;organizzazione esterna o con la tua?**
   - Organizzazione esterna: passare alla domanda 2.
   - Nella tua organizzazione (tra sandbox): scegli **Opzione C** (federazione tra sandbox).

2. **Con quanti partner esterni collaborerai?**
   - Un partner: scegli **Opzione A** (Condivisione segmenti diretta).
   - Più partner: scegliere **Opzione B** (distribuzione con più partner).

3. **Esistono vincoli di residenza dei dati che impediscono lo spostamento di dati non elaborati tra aree geografiche?**
   - Sì: scegli **l&#39;opzione C** indipendentemente dal fatto che i partner siano interni o esterni. Utilizza la condivisione tra sandbox per mantenere la posizione dei dati.

## Fasi di implementazione

Le fasi seguenti descrivono il processo di implementazione end-to-end per la collaborazione del pubblico con [!DNL Segment Match].

### Fase 1: Selezionare e preparare i segmenti

**Funzione dell&#39;applicazione:** [!DNL Real-Time CDP]: valutazione del pubblico, [!DNL Real-Time CDP]: composizione del pubblico

Questa fase prevede la definizione e la valutazione dei segmenti di pubblico che verranno condivisi tramite [!DNL Segment Match]. Prima di poter essere selezionati per la condivisione, i segmenti di origine devono essere valutati completamente con popolazioni diverse da zero. Questa fase tratta anche la composizione facoltativa del pubblico per perfezionare i segmenti prima della condivisione.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: approccio per la definizione del pubblico**
>
>Come creare i tipi di pubblico sorgente per la condivisione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Generatore di segmenti (regole dei segmenti) | Definizioni di pubblico standard basate su attributi di profilo, eventi o appartenenza a un segmento | Supporta la valutazione in batch, in streaming e Edge; più flessibile per la definizione dei criteri |
>| Composizione del pubblico | Tipi di pubblico derivati che richiedono operazioni di classificazione, suddivisione, esclusione o arricchimento sui segmenti esistenti | Supporta solo la valutazione batch; limitato a 10 aree di lavoro di composizione per sandbox |
>| Federated Audience Composition | Tipi di pubblico generati da query di data warehouse esterne senza acquisire dati in [!DNL Experience Platform] | Richiede l&#39;adesione [!DNL Federated Audience Composition]; i dati rimangono nel magazzino |

>[!NOTE]
>
>**Decisione: metodo di valutazione del pubblico**
>
>[!DNL Segment Match] richiede tipi di pubblico valutati in batch. Come deve essere programmata la valutazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Batch programmato (giornaliero) | Casi d’uso standard in cui è sufficiente l’aggiornamento giornaliero del pubblico | Pianificazione di valutazione predefinita; più semplice da gestire |
>| Batch su richiesta | Esigenze di condivisione ad hoc in cui desideri condividere immediatamente il pubblico più attuale | Richiede attivazione manuale; utile per le collaborazioni soggette a scadenza |
>| Pianificazione personalizzata | Requisiti di tempistica specifici allineati con le finestre di attivazione partner | Configurare una pianificazione cron personalizzata; più complessa ma precisa |

**Navigazione interfaccia utente:** Cliente > Tipi di pubblico > Crea pubblico > Genera regola (per [!DNL Segment Builder]) o Componi pubblico (per [!DNL Audience Composition])

**Dettagli configurazione chiave:**

- Definire i criteri di pubblico utilizzando gli attributi di profilo, gli eventi comportamentali e/o l’iscrizione al segmento
- Assicurarsi che il pubblico utilizzi un criterio di unione compatibile con gli spazi dei nomi di identità utilizzati per [!DNL Segment Match]
- Verifica che la popolazione del pubblico sia diversa da zero dopo la valutazione
- Applica regole di soppressione per escludere i profili da non condividere (ad esempio, profili che hanno rinunciato alla condivisione dei dati)

**Opzioni divergenti:**

**Per L&#39;Opzione A (Direct Segment Share):**
Prepara i segmenti specifici che intendi condividere con un singolo partner. Concentrati sulla qualità rispetto alla quantità: cura segmenti che forniscono un chiaro valore alla partnership.

**Per L&#39;Opzione B (Distribuzione Multipartner):**
Prepara un portfolio di segmenti che possono essere condivisi con partner diversi. Prendi in considerazione la creazione di segmenti specifici per i partner se diversi partner necessitano di definizioni di pubblico diverse. Utilizza convenzioni di denominazione coerenti per gestire segmenti tra partnership.

**Per L&#39;Opzione C (Cross-Sandbox Federation):**
Assicurati che i tipi di pubblico sorgente nella sandbox di invio utilizzino gli spazi dei nomi di identità esistenti nella sandbox di ricezione. Verifica che i criteri di unione siano allineati tra sandbox diverse.

**Documentazione di Experience League:**

- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder)
- [Panoramica sulla composizione del pubblico](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/audience-composition)
- [Metodi di valutazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home#evaluation-methods)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/pql/overview)

### Fase 2: configurare corrispondenza e governance

**Funzione dell&#39;applicazione:** [!DNL Real-Time CDP]: applicazione del consenso e della governance

Questa fase stabilisce la connessione [!DNL Segment Match] tra organizzazioni o sandbox, configura gli spazi dei nomi di identità utilizzati per la corrispondenza e garantisce che i criteri di governance dei dati consentano la condivisione. L’applicazione della governance funge da gate dei criteri che devono essere cancellati prima che i dati di qualsiasi segmento vengano condivisi.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: spazio dei nomi identità per corrispondenza**
>
>Quale spazio dei nomi delle identità verrà utilizzato per far corrispondere i profili tra mittente e destinatario?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| E-mail con hash (SHA-256) | Entrambe le organizzazioni raccolgono gli indirizzi e-mail e possono utilizzarli come hash in modo coerente | Chiave di corrispondenza più comune; percentuali di corrispondenza elevate per i casi di utilizzo da parte del consumatore; entrambi i lati devono utilizzare lo stesso algoritmo di hashing |
>| Numero di telefono con hash | L’e-mail non è disponibile in modo coerente, ma i numeri di telefono sono | Copertura inferiore rispetto alle e-mail in molti mercati; utile per il pubblico mobile-first |
>| Spazio dei nomi personalizzato (ad esempio, ID fedeltà con hash) | Le organizzazioni condividono un ID di programma fedeltà o iscrizione comune | Percentuali di corrispondenza più elevate per le basi clienti condivise note; richiede un’infrastruttura ID condivisa preesistente |
>| Più spazi dei nomi | Massimizzare il tasso di corrispondenza è fondamentale ed entrambe le organizzazioni dispongono di più identificatori coerenti | Aumenta le percentuali di corrispondenza ma aggiunge complessità; ogni spazio dei nomi deve essere configurato in modo indipendente |

>[!NOTE]
>
>**Decisione: revisione della governance dei dati**
>
>Quali controlli di governance devono essere completati prima della condivisione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Valutazione della governance standard | Caso d’uso tipico con etichette e criteri di utilizzo dei dati standard | Valuta l’azione di marketing &quot;Export to Third Party&quot; (Esporta a terze parti) rispetto alle etichette dei set di dati; risolvi eventuali violazioni prima di condividerli |
>| Governance migliorata con filtro del consenso | Condivisione con partner esterni in cui il consenso deve essere esplicitamente verificato | Aggiungi un filtro basato sul consenso per escludere i profili che non condividono il consenso (ad esempio, consents.share.val = &#39;n&#39;); più rigido ma sicuro |
>| Revisione della governance interna | Condivisione tra sandbox diverse all’interno della stessa organizzazione | Requisiti di governance più leggeri, poiché i dati rimangono entro i limiti dell’organizzazione; verifica comunque le etichette di utilizzo dei dati |

**Navigazione interfaccia utente:** Cliente > Tipi di pubblico > Corrispondenza segmento > Connessioni partner

**Dettagli configurazione chiave:**

- Stabilire una connessione partner scambiando gli identificativi di connessione tra le organizzazioni mittente e ricevente
- Configura gli spazi dei nomi di identità che verranno utilizzati per la corrispondenza su entrambi i lati
- Eseguire la valutazione dei criteri di governance dei dati rispetto all’azione di marketing associata alla condivisione dei segmenti
- Verifica che i campi di consenso siano compilati sui profili e che i profili senza condividere il consenso siano esclusi
- Esamina le etichette di utilizzo dei dati nei set di dati e nei campi dello schema inclusi nella condivisione

**Opzioni divergenti:**

**Per L&#39;Opzione A (Direct Segment Share):**
Stabilisci una connessione con un singolo partner. Configura gli spazi dei nomi di identità con il tuo partner specifico. Il riesame della governance si concentra sulle relazioni bilaterali.

**Per L&#39;Opzione B (Distribuzione Multipartner):**
Stabilire e gestire più connessioni partner. Ciascun partner può richiedere una revisione separata della governance. Documenta l’approvazione della governance per ogni partnership. Prendi in considerazione la creazione di un elenco di controllo per la governance al fine di semplificare l’onboarding dei partner.

**Per L&#39;Opzione C (Cross-Sandbox Federation):**
Stabilisci connessioni sandbox-sandbox all’interno dell’organizzazione. La governance è in genere più semplice, poiché la condivisione avviene internamente. Assicurati che gli spazi dei nomi delle identità siano coerenti tra le sandbox.

**Documentazione di Experience League:**

- [Panoramica di Segment Match](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home)
- [Applicazione dei criteri](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/enforcement/overview)
- [Consenso e preferenze](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

### Fase 3: Stima della sovrapposizione

**Funzione dell&#39;applicazione:** [!DNL Real-Time CDP]: Valutazione del pubblico (per la stima della sovrapposizione)

Questa fase esegue la stima della sovrapposizione tra i segmenti del mittente e la base del profilo del ricevente. La stima della sovrapposizione fornisce a entrambe le parti il volume e la percentuale di corrispondenza previsti prima di impegnarsi nella condivisione completa dei segmenti, consentendo decisioni informate sul valore della collaborazione.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: soglia di sovrapposizione per continuare**
>
>Quale tasso minimo di sovrapposizione giustifica la procedura con l’intera quota di segmento?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Nessuna soglia minima | Partnership esplorative o quando una sovrapposizione fornisce valore | Idoneo per le collaborazioni iniziali in cui si sta testando la relazione |
>| Soglia bassa (1-5%) | Collaborazione tra tipi di pubblico su larga scala, in cui anche una piccola sovrapposizione rappresenta un volume significativo | Comune per le relazioni editore-inserzionista con basi di pubblico di grandi dimensioni |
>| Soglia Medium (5-20%) | Partenariati standard in cui si prevede una significativa sovrapposizione | Tipico per co-marketing o collaborazioni con lo stesso settore |
>| Soglia alta (20%+) | Partnership in cui un forte allineamento del pubblico è un prerequisito | Comune per coalizioni di fidelizzazione o partnership di marchio strettamente integrate |

**Navigazione interfaccia utente:** Cliente > Tipi di pubblico > Corrispondenza segmento > Azioni > Sovrapposizione stima

**Dettagli configurazione chiave:**

- Seleziona i segmenti da includere nella stima di sovrapposizione
- Esamina il rapporto di sovrapposizione che mostra il conteggio e la percentuale dei profili corrispondenti
- Condividere i risultati della stima di sovrapposizione con le parti interessate di entrambe le parti per l’approvazione
- Documentare le metriche di sovrapposizione come base per la misurazione dell&#39;efficacia della collaborazione
- Se la sovrapposizione è inferiore alla soglia accettabile, è consigliabile modificare le definizioni dei segmenti o la configurazione di corrispondenza delle identità prima di procedere

**Documentazione di Experience League:**

- [Panoramica di Segment Match](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-match/overview)

### Fase 4: Condividere i tipi di pubblico

**Funzione dell&#39;applicazione:** [!DNL Real-Time CDP]: valutazione del pubblico (per l&#39;esecuzione della condivisione)

Questa fase esegue la condivisione del segmento effettivo dal mittente al ricevente. Il mittente avvia la condivisione per i segmenti selezionati e il destinatario accetta la condivisione in ingresso. Una volta accettato, il pubblico corrispondente viene visualizzato nell’elenco del pubblico del ricevente come nuovo pubblico disponibile per l’attivazione a valle.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: direzione condivisione**
>
>Qual è il modello di condivisione per questa collaborazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Condivisione unidirezionale (da mittente a destinatario) | Partnership asimmetrica in cui solo una parte fornisce dati sul pubblico | Modello più semplice; condivisione mittente, attivazione ricevitore; comune nelle relazioni inserzionista-editore |
>| Condivisione bidirezionale | Entrambe le parti traggono vantaggio dalla condivisione di tipi di pubblico tra di loro | Entrambe le organizzazioni agiscono contemporaneamente come mittente e ricevente; richiede due configurazioni di condivisione; comune nelle partnership di co-marketing |

>[!NOTE]
>
>**Decisione: frequenza di aggiornamento condivisione**
>
>Con quale frequenza il pubblico condiviso deve essere aggiornato con l’iscrizione al segmento aggiornata?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Condivisione una tantum | Verifica della collaborazione o di una campagna specifica con un pubblico fisso | Più semplice; nessuna manutenzione continua; il pubblico diventa obsoleto nel tempo |
>| Condivisione ricorrente (allineata con la valutazione batch) | Partnership continue in cui l’iscrizione al pubblico cambia e deve essere mantenuta aggiornata | Richiede il monitoraggio dello stato di aggiornamento; più comune per le collaborazioni di produzione |

**Navigazione interfaccia utente:** Cliente > Tipi di pubblico > Corrispondenza segmento > Condivisioni > Crea condivisione (mittente) o Accetta condivisione (destinatario)

**Dettagli configurazione chiave:**

- Il mittente seleziona i segmenti da condividere e avvia la condivisione con il partner configurato
- Il ricevente rivede i dettagli della condivisione in ingresso (nomi dei segmenti, dimensioni stimate, spazi dei nomi delle identità utilizzati)
- Il ricevente accetta la condivisione per creare il pubblico corrispondente nella propria sandbox
- Verifica che il pubblico corrispondente venga visualizzato nell’elenco del pubblico del ricevente con la popolazione prevista
- Conferma che il pubblico corrispondente sia etichettato in modo appropriato per il tracciamento della governance

**Opzioni divergenti:**

**Per L&#39;Opzione A (Direct Segment Share):**
Esegui una singola condivisione con il tuo partner. Monitora lo stato di condivisione e verifica il pubblico corrispondente sul lato ricevente.

**Per L&#39;Opzione B (Distribuzione Multipartner):**
Eseguire azioni per ciascun partner in modo indipendente. Monitora lo stato di condivisione in tutte le partnership. Prendi in considerazione l’avvio sfalsato della condivisione per gestire il carico di elaborazione.

**Per L&#39;Opzione C (Cross-Sandbox Federation):**
Esegui la condivisione tra sandbox. Il pubblico corrispondente viene visualizzato nell’elenco del pubblico della sandbox ricevente. Verifica che la sandbox ricevente disponga delle configurazioni di destinazione necessarie per l’attivazione a valle.

**Documentazione di Experience League:**

- [Panoramica di Segment Match](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Risoluzione dei problemi di Segment Match](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Fase 5: attivare i tipi di pubblico corrispondenti

**Funzione applicazione:** [!DNL Real-Time CDP]: configurazione di destinazione, [!DNL Real-Time CDP]: Audience Activation

Questa fase attiva il pubblico corrispondente (sul lato ricevente) a destinazioni esterne per il targeting, la soppressione o l’utilizzo a valle. Il pubblico corrispondente viene trattato come qualsiasi altro pubblico nella sandbox del destinatario e può essere attivato tramite il flusso di lavoro standard di attivazione della destinazione.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: tipo di destinazione per il pubblico corrispondente**
>
>Dove deve essere attivato il pubblico corrispondente?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Destinazioni Advertising (Google, Meta, Trade Desk) | Utilizzo di tipi di pubblico corrispondenti per il targeting o l’eliminazione di annunci | Richiede la connessione e l&#39;autenticazione della destinazione; soggetti ai limiti di tariffa e ai requisiti di formato specifici per la destinazione |
>| Destinazioni di archiviazione cloud (S3, Azure, GCS) | Esportazione di tipi di pubblico corrispondenti come file da utilizzare in sistemi esterni | Supporta la personalizzazione del formato dei file; è richiesta una pianificazione di esportazione batch; è flessibile per l&#39;elaborazione a valle |
>| Destinazioni di automazione CRM/marketing | Arricchimento dei record CRM o attivazione di flussi di lavoro di marketing automatizzato con dati di pubblico corrispondenti | Richiede il mapping dei campi allo schema CRM; utile per l&#39;allineamento vendite-marketing |
>| Destinazioni Personalization (web, app) | Utilizzo dell’iscrizione al pubblico corrispondente per la personalizzazione nel sito | Richiede la valutazione Edge del pubblico corrispondente o l’attivazione in streaming; la latenza varia in base alla destinazione |

>[!NOTE]
>
>**Decisione: pianificazione attivazione**
>
>Con quale frequenza il pubblico deve essere esportato nella destinazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Esportazione incrementale giornaliera | Attivazione standard con aggiornamenti regolari del pubblico | Esporta solo i profili modificati; volume di dati inferiore; più comune per le campagne in corso |
>| Esportazione completa giornaliera | Destinazioni che richiedono ogni volta un file del pubblico completo | Volume di dati più elevato; assicura che la destinazione abbia uno stato di pubblico completo; alcune destinazioni richiedono esportazioni complete |
>| Attivazione su richiesta | Avvii di campagne ad hoc o attivazioni sensibili al tempo | Attivazione manuale; ignora la cadenza pianificata; disponibile solo per destinazioni batch |

**Navigazione interfaccia utente:** Connessioni > Destinazioni > Catalogo (per l&#39;impostazione della destinazione) o Sfoglia > Seleziona destinazione > Attiva tipi di pubblico (per l&#39;attivazione)

**Dettagli configurazione chiave:**

- Configurare la connessione di destinazione con le credenziali di autenticazione appropriate
- Mappa gli attributi del profilo dal pubblico corrispondente ai campi di destinazione (campi di identità, attributi di profilo, appartenenza a segmenti)
- Configurare la pianificazione dell’esportazione (incrementale rispetto a completa, giornaliera rispetto a personalizzata)
- Monitora il flusso di dati di attivazione per confermare che i profili di pubblico corrispondenti siano stati esportati correttamente
- Verificare le metriche di attivazione (profili esportati, record non riusciti) nella vista di monitoraggio della destinazione

**Opzioni divergenti:**

**Per L&#39;Opzione A (Direct Segment Share):**
Il destinatario attiva il pubblico corrispondente tramite il flusso di lavoro di destinazione standard. Non è necessaria alcuna configurazione speciale oltre la normale attivazione della destinazione.

**Per L&#39;Opzione B (Distribuzione Multipartner):**
Ogni organizzazione ricevente attiva i tipi di pubblico corrispondenti in modo indipendente attraverso le proprie destinazioni. Il mittente non ha visibilità sull&#39;attivazione lato ricevente.

**Per L&#39;Opzione C (Cross-Sandbox Federation):**
La sandbox ricevente deve avere le proprie configurazioni di destinazione. Le destinazioni non possono essere condivise tra sandbox diverse. Assicurati che la sandbox ricevente disponga delle connessioni di destinazione necessarie.

**Documentazione di Experience League:**

- [Panoramica sulle destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/home)
- [Catalogo delle destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/overview)
- [Monitorare i flussi di dati per le destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Guardrail di attivazione](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/guardrails)

## Considerazioni sull’implementazione

Rivedi le seguenti considerazioni prima e durante l’implementazione per evitare problemi comuni e ottimizzare la collaborazione tra i tipi di pubblico.

### Guardrail e limiti

- [!DNL Segment Match] utilizza identificatori con hash per la corrispondenza. Nessun PII supera i limiti dell&#39;organizzazione. Vedi [Panoramica sulla corrispondenza dei segmenti](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-match/overview).
- Solo i tipi di pubblico valutati in batch possono essere condivisi tramite [!DNL Segment Match]. I segmenti in streaming e quelli valutati edge devono essere convertiti in valutazione batch prima della condivisione.
- Un massimo di 4.000 definizioni di segmenti per sandbox si applica sia ai segmenti sorgente che a quelli ricevuti. Consulta [Guardrail di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails).
- La precisione della stima di sovrapposizione dipende dal volume di identificatori corrispondenti. I tipi di pubblico di piccole dimensioni possono mostrare stime meno precise.
- I guardrail di attivazione si applicano ai tipi di pubblico corrispondenti come a qualsiasi altro pubblico, fino a un massimo di 100 flussi di dati per destinazione. Consulta [Guardrail di attivazione](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/guardrails).
- I tipi di pubblico composti vengono valutati in base a una pianificazione batch e sono limitati a 10 aree di lavoro per composizione per sandbox. Consulta [Guardrail di composizione del pubblico](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails).

### Insidie comuni

- **Hash di identità non coerente tra il mittente e il destinatario:** Se entrambe le organizzazioni eseguono l&#39;hashing degli indirizzi e-mail ma utilizzano diversi algoritmi di hashing, regole di normalizzazione o valori salt, le percentuali di corrispondenza saranno vicine allo zero. Prima di stabilire la connessione, entrambe le parti devono concordare le specifiche di hashing esatte (ad esempio, SHA-256 in minuscolo, e-mail ritagliate).
- **La condivisione di tipi di pubblico senza revisione della governance:** L&#39;avvio di una condivisione di segmenti senza la valutazione dei criteri di utilizzo dei dati può causare violazioni della conformità. Esegui sempre la valutazione dei criteri di governance rispetto all’azione di marketing &quot;Esporta a terze parti&quot; prima di condividere segmenti con organizzazioni esterne.
- **Basse percentuali di corrispondenza a causa di gap di copertura delle identità:** Se il pubblico del mittente è identificato principalmente da ECID (cookie anonimo) ma lo spazio dei nomi corrispondente è un&#39;e-mail con hash, la percentuale di corrispondenza sarà molto bassa perché i profili anonimi non hanno indirizzi e-mail. Verifica che i tipi di pubblico di origine abbiano una copertura sufficiente dello spazio dei nomi dell’identità corrispondente configurato.
- **Dimenticarsi di accettare la condivisione dal lato ricevente:** Il pubblico condiviso non viene visualizzato nell&#39;elenco del pubblico del ricevente finché la condivisione non viene accettata in modo esplicito. Coordina con il ricevitore per assicurarti un&#39;accettazione tempestiva, soprattutto per le campagne che richiedono molto tempo.
- **Tipi di pubblico con corrispondenza non aggiornati a causa di un disallineamento della pianificazione di valutazione:** Se il pubblico di origine del mittente viene valutato ogni giorno ma l&#39;aggiornamento di [!DNL Segment Match] viene eseguito settimanalmente, il pubblico corrispondente sul lato ricevente potrebbe non riflettere l&#39;appartenenza più recente. Allinea la valutazione e condividi le cadenze di aggiornamento.

### Best practice

- Stabilire un accordo formale per la condivisione dei dati tra le organizzazioni prima di configurare [!DNL Segment Match]. Ciò dovrebbe coprire i casi d’uso consentiti, i requisiti di governance dei dati, gli obblighi di consenso e le procedure di cessazione.
- Utilizza la stima di sovrapposizione come strumento di convalida prima di ogni campagna principale: esegui la stima prima di confermare, in modo che il pubblico corrispondente raggiunga le dimensioni minime e le soglie di qualità.
- Applica convenzioni di denominazione descrittive ai segmenti condivisi che includono il nome del partner, il caso d’uso e la data (ad esempio, &quot;PartnerX_HighValue_Suppression_2026Q1&quot;) per mantenere la chiarezza tra le organizzazioni.
- Monitora le percentuali di corrispondenza nel tempo. Il calo delle percentuali di corrispondenza può indicare un degrado della copertura delle identità, problemi di qualità dei dati o modifiche nella base clienti del partner.
- Segmenta i tipi di pubblico di origine per escludere i profili privi dello spazio dei nomi dell’identità corrispondente popolato. Ciò migliora le percentuali del tasso di corrispondenza e fornisce stime di sovrapposizione più precise.
- Per le partnership di condivisione bidirezionale, specifica una chiara proprietà della manutenzione dei segmenti e dei programmi di aggiornamento per evitare confusione su quale organizzazione è responsabile degli aggiornamenti.

### Decisioni di compromesso

>[!NOTE]
>
>**Compensazione: tasso di corrispondenza rispetto al controllo della privacy**
>
>L’utilizzo di più spazi dei nomi di identità (e-mail con hash, telefono con hash, ID dispositivo) per la corrispondenza aumenta le percentuali di corrispondenza, ma amplia la superficie per una potenziale reidentificazione. L’utilizzo di un numero inferiore di spazi dei nomi (solo e-mail con hash) offre una maggiore protezione della privacy, ma può ridurre la dimensione del pubblico corrispondente.
>
>- **Preferenza per più spazi dei nomi:** percentuali di corrispondenza più elevate, pubblico con corrispondenza più ampia, più prezioso per il targeting delle campagne
>- **Un solo namespace favorisce:** una maggiore privacy, una più semplice revisione della governance, minori rischi di conformità
>- **Consiglio:** inizia con un singolo spazio dei nomi (il più comune è l&#39;e-mail con hash) e aggiungi spazi dei nomi aggiuntivi solo se le percentuali di corrispondenza non sono sufficienti per il caso d&#39;uso. Documenta la valutazione dell’impatto sulla privacy per ogni spazio dei nomi aggiunto.

>[!NOTE]
>
>**Compensazione: granularità del segmento rispetto alla semplicità operativa**
>
>La condivisione di molti segmenti granulari e altamente mirati con un partner offre maggiore flessibilità per il targeting delle campagne, ma aumenta la complessità operativa sia per il mittente che per il destinatario. La condivisione di un numero inferiore di segmenti più ampi semplifica la gestione ma riduce la precisione di targeting.
>
>- **Segmenti granulari a favore:** Targeting preciso, campagne differenziate, rilevanza maggiore
>- **Segmenti ampi a favore:** gestione più semplice, meno condivisioni da monitorare, minor sovraccarico operativo
>- **Consiglio:** inizia con un numero limitato di segmenti di valore elevato (2-5) per una nuova partnership. Aumentare la granularità con la maturazione del partenariato e la definizione dei processi operativi. Utilizza le convenzioni di denominazione e la documentazione per gestire la complessità man mano che il conteggio dei segmenti aumenta.

>[!NOTE]
>
>**Compensazione: frequenza di aggiornamento rispetto al costo di elaborazione**
>
>L’aggiornamento più frequente dei tipi di pubblico condivisi mantiene aggiornato il pubblico corrispondente, ma aumenta il carico di elaborazione e può richiedere una maggiore capacità di licenza. Aggiornamenti meno frequenti riducono i costi, ma consentono al pubblico interessato di diventare obsoleto.
>
>- **Preferenze per l&#39;aggiornamento frequente:** Iscrizione corrente al pubblico, maggiore rilevanza della campagna, migliore precisione dell&#39;eliminazione
>- **Aggiornamenti poco frequenti favoriscono:** costi di elaborazione inferiori, monitoraggio più semplice, consumo ridotto delle licenze
>- **Consiglio:** L&#39;aggiornamento giornaliero è appropriato per la maggior parte delle collaborazioni di produzione. Per i casi d’uso sensibili al tempo (ad esempio, vendite flash, campagne basate su eventi), considera la rivalutazione e la condivisione su richiesta immediatamente prima del lancio della campagna.

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sulle funzionalità utilizzate in questo modello di caso d’uso.

### [!DNL Segment Match]

- [Panoramica di Segment Match](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Risoluzione dei problemi di Segment Match](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Segmentazione e tipi di pubblico

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder)
- [Panoramica sulla composizione del pubblico](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/audience-composition)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/pql/overview)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Identità e profilo

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home)
- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Panoramica del profilo cliente in tempo reale](https://experienceleague.adobe.com/it/docs/experience-platform/profile/home)

### Governance dei dati e consenso

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home)
- [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview)
- [Applicazione dei criteri](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/enforcement/overview)
- [Consenso e preferenze](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Gruppo di campi Consenso e preferenze](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/field-groups/profile/consents)

### Destinazioni e attivazione

- [Panoramica sulle destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/home)
- [Catalogo delle destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/overview)
- [Monitorare i flussi di dati per le destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/dataflows/ui/monitor-destinations)

### Modellazione dati e schema

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/schema/composition)

### Amministrazione e controllo degli accessi

- [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/it/docs/experience-platform/access-control/home)
- [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home)

### Monitoraggio e osservabilità

- [Panoramica degli avvisi](https://experienceleague.adobe.com/it/docs/experience-platform/observability/alerts/overview)
- [Panoramica di Observability Insights](https://experienceleague.adobe.com/it/docs/experience-platform/observability/home)

### Guardrail

- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Guardrail di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [Guardrail di attivazione](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/guardrails)

### Tutorial

- [Creare uno schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [Abilitare un set di dati per il profilo](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/enable-for-profile)
