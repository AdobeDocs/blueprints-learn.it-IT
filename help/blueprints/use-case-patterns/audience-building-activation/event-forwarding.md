---
title: Inoltro degli eventi
description: Scopri come inoltrare i dati evento in tempo reale raccolti tramite Edge Network a destinazioni non Adobe per scopi di analisi, archiviazione o pubblicità.
solution: Experience Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '6342'
ht-degree: 0%

---


# Inoltro eventi

Questa guida descrive l&#39;implementazione dell&#39;inoltro degli eventi lato server tramite [!DNL Adobe Experience Platform] Edge Network. È progettato per architetti di soluzioni, tecnici di marketing e ingegneri dell’implementazione che devono distribuire i dati degli eventi in tempo reale raccolti tramite Edge Network a destinazioni non Adobe, ad esempio piattaforme di analisi di terze parti, endpoint di archiviazione cloud, reti pubblicitarie o webhook personalizzati.

Presenta tutti gli approcci possibili per la configurazione dell&#39;inoltro degli eventi, spiega i compromessi tra di essi e fornisce collegamenti alla documentazione di [!DNL Adobe Experience League] per istruzioni procedurali dettagliate.

## Panoramica del caso d’uso

Le organizzazioni che raccolgono dati comportamentali tramite l&#39;API di [!DNL Adobe Experience Platform] Web SDK, Mobile SDK o Server spesso devono condividere lo stesso flusso di eventi con sistemi non Adobe: piattaforme di analisi come [!DNL Google Analytics] o [!DNL Snowflake], reti pubblicitarie per il monitoraggio delle conversioni, data warehouse per l&#39;archiviazione a lungo termine o servizi interni personalizzati. In genere, questo richiedeva la proliferazione di tag lato client, che aumenta il peso delle pagine, introduce latenza e crea rischi per la privacy e la governance.

L’inoltro degli eventi risolve questo problema operando lato server su Edge Network. Quando un’interazione con un visitatore attiva un evento tramite Web SDK o l’API server, tale evento viene instradato attraverso un flusso di dati a Edge Network. Le regole di inoltro degli eventi, configurate in una proprietà di inoltro degli eventi dedicata, valutano i dati degli eventi in arrivo e li inoltrano selettivamente a una o più destinazioni configurate. Questo approccio lato server riduce l’ingrossamento dei tag lato client, migliora le prestazioni delle pagine, centralizza la governance dei dati e offre all’organizzazione il controllo esatto sui dati che lasciano l’ecosistema Adobe.

Il pubblico di destinazione per questo modello include organizzazioni che hanno già distribuito (o intendono distribuire) l&#39;API server o Web SDK [!DNL Adobe Experience Platform] per la raccolta dei dati e desiderano estendere tale investimento distribuendo i dati evento agli endpoint non Adobe senza aggiungere tag JavaScript lato client.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### Migliorare la qualità e la governance dei dati

Garantire dati puliti, completi e conformi per un targeting accurato, una riduzione degli sprechi e analisi affidabili. L&#39;inoltro degli eventi centralizza la distribuzione dei dati sul lato server, offrendo all&#39;organizzazione un unico punto di controllo per i dati condivisi con i sistemi esterni, riducendo il rischio di perdita di dati e garantendo l&#39;applicazione dei criteri di governance prima che i dati lascino l&#39;Edge Network [!DNL Adobe].

**KPI:** efficienza, risparmi sui costi

Per ulteriori informazioni, consulta [Migliorare la qualità e la governance dei dati](../../business-objectives/cost-efficiency/improve-data-quality-governance.md).

### Consolidamento e modernizzazione delle tecnologie di marketing

Ridurre la frammentazione degli strumenti e il debito tecnico con la migrazione a piattaforme unificate e scalabili. L’inoltro degli eventi consente alle organizzazioni di sostituire più tag dei fornitori lato client con un unico meccanismo di distribuzione dei dati lato server, riducendo il sovraccarico di caricamento delle pagine e semplificando lo stack di tecnologia.

**KPI:** Risparmio sui costi, efficienza, rapidità di commercializzazione

Per ulteriori informazioni, vedere [Consolidare e modernizzare la tecnologia di marketing](../../business-objectives/cost-efficiency/consolidate-modernize-marketing-technology.md).

## Esempi di casi d’uso tattici

Di seguito sono riportati gli scenari tattici comuni in cui si applica questo modello di caso d’uso.

- **Arricchimento di analisi di terze parti** - Inoltra in tempo reale eventi di visualizzazione pagina, clic e conversione a [!DNL Google Analytics], [!DNL Snowflake] o altre piattaforme di analisi senza aggiungere tag lato client
- **Tracciamento conversione Advertising** - Invia eventi di acquisto e generazione lead a [!DNL Meta] API di conversione, [!DNL Google Ads], [!DNL TikTok] o [!DNL Snap] per la misurazione e l&#39;ottimizzazione della conversione lato server
- **Streaming data warehouse**: instrada i dati evento non elaborati a un data warehouse cloud ([!DNL Google BigQuery], [!DNL Amazon S3], [!DNL Azure Event Hubs]) per l&#39;archiviazione a lungo termine e l&#39;analisi offline
- **Integrazione webhook personalizzata**: inoltro di dati evento filtrati o trasformati a microservizi interni, sistemi CRM o piattaforme partner tramite endpoint HTTP
- **Riduzione dei tag e miglioramento delle prestazioni delle pagine**: sostituzione di più tag JavaScript del fornitore lato client con un&#39;unica implementazione di Web SDK e regole di inoltro degli eventi lato server, riducendo il peso delle pagine e migliorando Core Web Vitals
- **Condivisione dei dati conforme alla privacy**: applica il filtro dei dati e le regole di redazione a livello di campo lato server prima di condividere i dati dell&#39;evento con terze parti, assicurandosi che i dati PII vengano eliminati o sottoposti ad hashing prima di raggiungere i sistemi esterni
- **Distribuzione di eventi multi-cloud**: inoltra simultaneamente lo stesso flusso di eventi a più destinazioni (ad esempio, analytics, advertising e data warehouse) da un singolo set di regole lato server
- **Inoltro del segnale di frode in tempo reale**: inoltra eventi di transazione di valore elevato ai sistemi di rilevamento delle frodi per il punteggio del rischio in tempo reale e gli avvisi

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare il successo di questo modello di caso d’uso.

- **Riduzione del tempo di caricamento delle pagine**: è stato misurato un miglioramento della velocità di caricamento delle pagine e di Core Web Vitals dopo la migrazione dei tag lato client all&#39;inoltro eventi lato server
- **Tasso di successo della consegna dati** — Percentuale di eventi inoltrati correttamente agli endpoint di destinazione senza errori o timeout
- **Riduzione del numero di tag** — Numero di tag fornitore lato client rimossi dopo l&#39;implementazione di equivalenti lato server
- **Aggiornamento/latenza dati** — Tempo tra l&#39;occorrenza dell&#39;evento sul client e l&#39;arrivo dell&#39;evento all&#39;endpoint di destinazione (destinazione: da un secondo all&#39;altro)
- **Tasso di conformità alla governance**: percentuale di condivisioni di dati in uscita che passano attraverso le regole di filtro lato server, garantendo che nessun PII o dati con restrizioni raggiunga destinazioni non autorizzate
- **Efficienza operativa**: riduzione delle ore dedicate agli sviluppatori per la gestione delle distribuzioni di tag lato client e la risoluzione dei conflitti di tag

## Schema del caso d’uso

Questa sezione descrive il pattern e la catena di funzioni utilizzati per implementare l’inoltro degli eventi.

**Inoltro eventi**: inoltra i dati evento in tempo reale raccolti tramite Edge Network a destinazioni non Adobe per scopi di analisi, archiviazione o pubblicità.

**Catena funzioni:** Configurazione flusso di dati > Definizione regola evento > Mapping destinazione > Esecuzione inoltro > Monitoraggio

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Adobe Experience Platform](Edge Network)** — Riceve e instrada dati evento in tempo reale da Web SDK, Mobile SDK o Server API tramite flussi di dati configurati
- **[!DNL Adobe Experience Platform](Inoltro eventi)** - Fornisce il motore delle regole lato server per la valutazione, il filtraggio, la trasformazione e l&#39;inoltro dei dati evento a destinazioni esterne
- **[!DNL Adobe Experience Platform](Tag / Raccolta dati)** - Gestisce il ciclo di vita, le estensioni, le regole e il flusso di lavoro di pubblicazione della proprietà di inoltro degli eventi

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve esistere | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Obbligatorio | Una sandbox deve essere attiva con i ruoli utente e le autorizzazioni appropriati configurati. Gli utenti che gestiscono l&#39;inoltro degli eventi devono disporre di autorizzazioni di raccolta dati in [!DNL Adobe Admin Console], inclusi i diritti per la gestione delle proprietà, delle estensioni e delle regole di inoltro degli eventi. | [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Obbligatorio | È necessario definire schemi XDM per i dati dell’evento che fluiscono attraverso Edge Network. Lo stream di dati deve fare riferimento a uno schema ExperienceEvent XDM valido in modo che le regole di inoltro degli eventi possano accedere a campi strutturati per il filtraggio, la trasformazione e la mappatura. | [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Origini dati e raccolta | Obbligatorio | Un meccanismo di raccolta dei dati deve essere attivo, ossia Web SDK, Mobile SDK o Edge Network Server API, per l’invio di eventi tramite uno stream di dati configurato. Lo stream di dati è il livello di routing fondamentale che connette la raccolta lato client all’inoltro eventi lato server. | [Configurare gli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Configurazione identità e profilo | Non applicabile | L’inoltro degli eventi funziona sui dati degli eventi non elaborati a livello di Edge Network, prima che si verifichi la risoluzione delle identità o l’unificazione dei profili. Gli spazi dei nomi di identità e i criteri di unione non sono necessari, a meno che gli eventi inoltrati non debbano contribuire anche a Real-Time Customer Profile (che è una configurazione separata del servizio dello stream di dati, non un problema di inoltro degli eventi). | |
| Definizione e segmentazione del pubblico | Non applicabile | L’inoltro degli eventi elabora i singoli eventi in tempo reale e non valuta l’iscrizione del pubblico. Il filtro basato sul pubblico non fa parte della catena della funzione di inoltro degli eventi. Se è necessaria l’attivazione basata sul pubblico, consulta il piano di riferimento da Audience Activation alle destinazioni. | |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Non applicabile | L’inoltro degli eventi funziona sui dati degli eventi non elaborati, non sugli attributi calcolati a livello di profilo. Gli attributi calcolati non sono disponibili nel contesto di inoltro degli eventi. | |
| Data Lifecycle Management | Consigliato | Se i dati evento vengono acquisiti anche nei set di dati di AEP (tramite lo stesso flusso di dati), è necessario configurare le policy di conservazione dei dati (scadenza) per tali set di dati in modo da gestire i costi di archiviazione e la conformità alle normative. L’inoltro degli eventi di per sé non memorizza i dati, mentre il percorso di acquisizione parallelo di AEP sì. | [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Etichettatura e applicazione dell’utilizzo dati | Consigliato | Mentre le regole di inoltro degli eventi forniscono un filtro a livello di campo (che consente di escludere i dati sensibili dai payload inoltrati), l’applicazione di etichette di utilizzo dei dati agli schemi e ai set di dati sottostanti garantisce che vengano applicati i criteri di governance se gli stessi dati vengono utilizzati per l’attivazione o la personalizzazione del pubblico. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Monitoraggio e osservabilità | Incluso | Il monitoraggio è essenziale per l’inoltro degli eventi. Il dashboard Monitoraggio inoltro eventi fornisce visibilità sulle percentuali di successo e di errore di inoltro, nonché sui codici di risposta della destinazione. Gli avvisi devono essere configurati per gli errori di destinazione. | [Monitoraggio inoltro eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring) |
| Reporting e analisi | Consigliato | Se gli eventi inoltrati alimentano una piattaforma di analisi di terze parti, puoi collegare gli stessi set di dati evento di AEP a CJA per una visualizzazione cross-channel unificata. Questo consente il confronto tra analisi lato Adobe e analisi lato terze parti. | [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Adobe Experience Platform] (AEP)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Configurazione dello stream di dati | Fase 1: configurazione dello stream di dati | Configurare uno stream di dati per ricevere eventi di Edge Network e abilitare il servizio di inoltro degli eventi |
| Impostazione proprietà inoltro eventi | Fase 2: proprietà ed estensioni di inoltro degli eventi | Creare una proprietà di inoltro degli eventi e installare estensioni specifiche per la destinazione |
| Definizione regola evento | Fase 3: definizione della regola evento | Definisci le regole che valutano i dati dell’evento in arrivo e determinano cosa inoltrare e dove |
| Mappatura delle destinazioni | Fase 3: definizione della regola evento | Mappa gli elementi dati evento ai formati di payload specifici della destinazione all’interno delle regole di inoltro |
| Inoltro dell’esecuzione | Fase 4: pubblicazione e attivazione | Pubblica la configurazione di inoltro degli eventi in Edge Network per l’esecuzione live |
| Monitoraggio | Fase 5: Monitoraggio e convalida | Monitorare i tassi di successo, i codici di errore e lo stato della destinazione dell’inoltro |

## Prerequisiti

Prima di iniziare l’implementazione, assicurati che siano presenti i seguenti elementi.

- [ Licenza ] [!DNL Adobe Experience Platform] con Edge Network e diritto all&#39;inoltro eventi
- [ ] Autorizzazioni di raccolta dati configurate in [!DNL Adobe Admin Console] (gestione proprietà, estensioni, regole e pubblicazione per l&#39;inoltro degli eventi)
- [ ] Almeno un meccanismo di raccolta dati attivo (Web SDK, Mobile SDK o API server) che invia eventi tramite uno stream di dati
- [ ] schema XDM ExperienceEvent definito per i dati evento raccolti
- [ Lo stream di dati ] è stato creato e collegato al meccanismo di raccolta
- [ Sono disponibili le credenziali e la documentazione dell&#39;endpoint di destinazione ] (ad esempio, token di accesso API per [!DNL Meta] conversioni, ID misurazione [!DNL Google Analytics], URL webhook, credenziali archiviazione cloud)
- [ ] Informazioni sul modello dati dell&#39;evento e sui campi/eventi richiesti da ogni destinazione

## Opzioni di implementazione

Questa sezione descrive gli approcci disponibili per l’implementazione dell’inoltro degli eventi e fornisce indicazioni sulla scelta dell’opzione giusta.

### Opzione A: inoltro di eventi basato su estensione

**Ideale per:** team che utilizzano piattaforme di destinazione ben supportate ([!DNL Meta], [!DNL Google], [!DNL AWS], [!DNL Azure], [!DNL Snowflake], ecc.) che dispongono di estensioni predefinite per l’inoltro degli eventi disponibili nel catalogo di Data Collection.

**Funzionamento:**

L’inoltro di eventi basato su estensioni sfrutta integrazioni predefinite gestite da Adobe o da partner di terze parti. Ogni estensione è progettata appositamente per una destinazione specifica e gestisce l’autenticazione, la formattazione del payload e la comunicazione con gli endpoint. Il implementatore installa l’estensione nella proprietà di inoltro degli eventi, configura le credenziali di autenticazione e crea regole che mappano gli elementi dati XDM ai campi di azione dell’estensione.

Questo approccio riduce al minimo lo sviluppo personalizzato perché l’estensione astrae i requisiti API della destinazione. Ad esempio, l&#39;estensione API per le conversioni [!DNL Meta] traduce gli eventi di e-commerce XDM nel formato previsto da [!DNL Meta], gestendo l&#39;hashing dei campi PII, i parametri di deduplicazione e la gestione dei token di accesso. Analogamente, le estensioni [!DNL Google Cloud Platform] o [!DNL AWS] gestiscono l&#39;autenticazione e la formattazione del payload per i rispettivi servizi cloud.

Il compromesso è che la disponibilità dell’estensione determina quali destinazioni sono supportate. Se non esiste alcuna estensione per una destinazione, utilizza l’opzione B (webhook personalizzato).

**Considerazioni chiave:**

- La disponibilità dell&#39;estensione varia. Controllare il [catalogo estensioni raccolta dati](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview) prima di pianificare
- Le estensioni sono gestite da Adobe o dai partner; gli aggiornamenti possono introdurre modifiche che causano interruzioni e che richiedono regolazioni delle regole
- Alcune estensioni supportano solo tipi di evento specifici o richiedono mappature di campi XDM specifiche
- Le estensioni gestiscono l’autenticazione e la gestione delle credenziali nell’interfaccia utente di configurazione

**Vantaggi:**

- Implementazione più rapida per le destinazioni supportate
- La formattazione predefinita del payload riduce gli errori di mappatura
- Gestione dell’autenticazione e delle credenziali gestite dall’estensione
- Gestito e aggiornato da Adobe o da partner certificati
- Riduzione del codice personalizzato e del carico di manutenzione

**Limitazioni:**

- Limitato alle destinazioni con estensioni disponibili
- Meno flessibilità nella personalizzazione del payload rispetto ai webhook personalizzati
- Gli aggiornamenti delle estensioni possono richiedere la riconfigurazione delle regole
- Alcune estensioni potrebbero non supportare tutte le funzioni API di destinazione

**Experience League:**

- [Catalogo estensioni inoltro eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [Estensione API per conversioni Meta](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/meta/overview)
- [Estensione Piattaforma Google Cloud](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [Estensione AWS](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/aws/overview)
- [Estensione Snowflake](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/snowflake/overview)

### Opzione B: inoltro di eventi del webhook personalizzato (Fetch API)

**Ideale per:** team che devono inoltrare eventi a destinazioni senza un&#39;estensione predefinita o che richiedono il controllo completo del payload della richiesta HTTP, delle intestazioni e del meccanismo di autenticazione.

**Funzionamento:**

L&#39;inoltro di eventi personalizzato basato su webhook utilizza l&#39;estensione [!DNL Adobe Cloud Connector] (inclusa per impostazione predefinita) per effettuare richieste HTTP arbitrarie a qualsiasi endpoint. L’implementatore definisce gli elementi dati per estrarre e trasformare i valori dall’evento XDM in ingresso, quindi configura un’azione della regola utilizzando il tipo di azione &quot;Fai chiamata di recupero&quot; del connettore cloud. Questa azione consente il controllo completo del metodo HTTP, dell’URL, delle intestazioni e del corpo della richiesta.

Il corpo della richiesta viene generalmente costruito utilizzando elementi di dati e codice personalizzato per formattare il payload in base alle specifiche API della destinazione. Questo approccio supporta qualsiasi endpoint accessibile tramite HTTP, come API REST, webhook, funzioni cloud o servizi interni, rendendolo l’opzione più flessibile.

Il compromesso consiste in un maggiore impegno nell’implementazione e nella manutenzione continua. L’implementatore deve comprendere l’API di destinazione, gestire l’autenticazione manualmente (ad esempio, impostando le intestazioni di Autorizzazione, gestendo l’aggiornamento dei token) e mantenere il formato del payload se l’API di destinazione si evolve.

**Considerazioni chiave:**

- Richiede la comprensione delle specifiche API di destinazione (metodo HTTP, struttura URL, formato payload, autenticazione)
- Le credenziali di autenticazione devono essere gestite manualmente in elementi dati o segreti
- Il codice personalizzato può essere necessario per la trasformazione del payload (hashing, codifica, ristrutturazione)
- Nessun aggiornamento automatico quando l’API di destinazione cambia — è necessaria una manutenzione manuale
- La funzione Segreti in Raccolta dati può memorizzare in modo sicuro chiavi e token API

**Vantaggi:**

- Supporta qualsiasi endpoint accessibile tramite HTTP: nessuna dipendenza di estensione
- Controllo completo del payload della richiesta, delle intestazioni e dell’autenticazione
- Può inoltrare a servizi interni, API personalizzate o piattaforme di nicchia
- Abilita trasformazioni di payload complesse utilizzando un codice personalizzato
- Può implementare la logica dei nuovi tentativi e la gestione degli errori nel codice personalizzato

**Limitazioni:**

- Maggiore impegno nell’implementazione iniziale
- Responsabilità della manutenzione continua per il formato del payload e l’autenticazione
- Gestione degli errori o rotazione delle credenziali non predefinite. Implementare manualmente
- Richiede competenze di sviluppo in protocolli HTTP e specifiche API di destinazione

**Experience League:**

- [Estensione Adobe Cloud Connector](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [Segreti di inoltro eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)

### Opzione C: ibrido (estensioni + webhook personalizzati)

**Ideale per:** organizzazioni che inoltrano eventi a più destinazioni in cui alcune hanno estensioni predefinite e altre richiedono un&#39;integrazione personalizzata.

**Funzionamento:**

L’approccio ibrido combina l’inoltro basato su estensione per destinazioni ben supportate con azioni webhook personalizzate per destinazioni prive di estensioni. Una singola proprietà di inoltro degli eventi contiene più regole, alcune che utilizzano azioni di estensione (ad esempio, l’estensione API per le conversioni di [!DNL Meta] per il tracciamento delle conversioni pubblicitarie) e altre che utilizzano azioni di recupero del connettore Cloud (ad esempio, l’inoltro a un endpoint interno del data lake).

Questo approccio massimizza la copertura riducendo al minimo gli sviluppi personalizzati non necessari. Ogni regola funziona in modo indipendente, pertanto le regole basate su estensioni traggono vantaggio dalla formattazione del payload predefinita, mentre le regole personalizzate mantengono la massima flessibilità.

**Considerazioni chiave:**

- La complessità delle proprietà aumenta con il numero di regole e destinazioni
- I test e il debug possono richiedere approcci diversi per le regole basate su estensioni rispetto a quelle personalizzate
- Le modifiche apportate alla pubblicazione influiscono su tutte le regole della proprietà: utilizza le librerie e gli ambienti per posizionare le modifiche in un ambiente sicuro
- Prendi in considerazione l’organizzazione di regole con chiare convenzioni di denominazione per distinguere le azioni basate su estensioni da quelle personalizzate

**Vantaggi:**

- Migliore copertura per diversi tipi di destinazioni
- Sfrutta le estensioni predefinite, se disponibili, riducendo gli sforzi
- Mantiene la flessibilità per le destinazioni personalizzate
- Una singola proprietà di inoltro degli eventi gestisce tutta la logica di inoltro

**Limitazioni:**

- Maggiore complessità delle proprietà con più tipi di regole
- Modello di manutenzione mista: alcune regole vengono aggiornate automaticamente tramite estensioni, altre richiedono la manutenzione manuale
- Il debug richiede familiarità sia con le configurazioni delle estensioni che con i pattern di chiamata di recupero personalizzati

**Experience League:**

- [Panoramica sull’inoltro degli eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [Guida introduttiva all’inoltro degli eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)

### Confronto delle opzioni

La tabella seguente confronta le tre opzioni di implementazione.

| Criteri | Opzione A: basata sull&#39;estensione | Opzione B: webhook personalizzato | Opzione C: Ibrido |
| --- | --- | --- | --- |
| Ideale per | Destinazioni supportate ([!DNL Meta], [!DNL Google], [!DNL AWS], ecc.) | Endpoint personalizzati, piattaforme di nicchia, servizi interni | Più destinazioni con supporto misto |
| Complessi | Bassa | Medium - Alta | Medio |
| Tempo di implementazione | Giorni | Giorni-Settimane | Varia in base al mix di destinazioni |
| Flessibilità | Limitato alle funzionalità di estensione | Controllo completo | Controllo completo quando necessario |
| Manutenzione | Basso (gestito da un&#39;estensione) | Alta (manutenzione manuale) | Misto |
| Richiede | Estensione disponibile per la destinazione | Documentazione API di destinazione | Entrambi, a seconda della destinazione |
| Codice personalizzato necessario | Minimo | Moderato-Significativo | Varia |

### Scegli l’opzione giusta

Per iniziare, crea un inventario delle destinazioni di destinazione e controlla se per ciascuna di esse esistono estensioni predefinite per l’inoltro degli eventi.

1. **Se tutte le destinazioni hanno estensioni** — Scegliere l&#39;opzione A. Questo offre l’implementazione più rapida con il minore carico di manutenzione. Le estensioni gestiscono l’autenticazione, la formattazione del payload e la gestione delle versioni API.

2. **Se nessuna destinazione dispone di estensioni o se è necessario il controllo completo del payload** — Scegliere l&#39;opzione B. Utilizza l’estensione Cloud Connector per effettuare richieste HTTP personalizzate per qualsiasi endpoint. Questa è anche la scelta giusta quando devi applicare trasformazioni complesse, hashing personalizzato o inviare a servizi interni.

3. **Se si dispone di una combinazione di destinazioni supportate e non supportate** — Scegliere l&#39;opzione C. Utilizza le estensioni per piattaforme come [!DNL Meta], [!DNL Google] e [!DNL AWS] e webhook personalizzati per tutto il resto. Si tratta dello scenario di produzione più comune per le organizzazioni con diversi stack di analisi e annunci pubblicitari.

## Fasi di implementazione

Le fasi seguenti descrivono il processo di implementazione end-to-end per l’inoltro degli eventi.

### Fase 1: configurazione dello stream di dati

**Funzione applicazione:** AEP: configurazione Datastream

**Configurazione:** un flusso di dati che riceve eventi dall&#39;implementazione di Web SDK, Mobile SDK o Server API e li indirizza ad Edge Network, dove le regole di inoltro degli eventi possono elaborarli. Se si aggiunge l’inoltro di eventi a una distribuzione di raccolta dati esistente, verrà abilitato l’inoltro di eventi sullo stream di dati esistente.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: nuovo stream di dati rispetto allo stream di dati esistente**
>
>È necessario creare un nuovo flusso di dati per l’inoltro di eventi o abilitare l’inoltro di eventi su un flusso di dati esistente?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Usa flusso di dati esistente | Si dispone già di eventi di invio tramite un flusso di dati tramite Web SDK o API server | Scenario più comune: l’inoltro di eventi viene semplicemente abilitato come servizio aggiuntivo nel flusso di dati. Non sono necessarie modifiche lato client. |
>| Crea nuovo flusso di dati | Si tratta di un’implementazione greenfield senza alcuna raccolta di dati esistente, oppure è necessario un flusso di dati separato per tipi di evento specifici | Richiede la configurazione SDK lato client per puntare al nuovo ID dello stream di dati. Consente la configurazione isolata. |

>[!NOTE]
>
>**Decisione: quali servizi AEP abilitare insieme all&#39;inoltro degli eventi**
>
>Lo stream di dati può instradare gli eventi a più servizi AEP simultaneamente. L&#39;inoltro degli eventi è un servizio; altri (acquisizione dati di AEP, [!DNL Target], [!DNL Analytics]) possono essere eseguiti in parallelo.
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Solo inoltro eventi | Devi solo inoltrare gli eventi a destinazioni non Adobe e non hai bisogno dei dati nei set di dati di AEP | Riduce al minimo i costi di elaborazione dei dati. Gli eventi passano attraverso Edge Network alle regole di inoltro ma non vengono acquisiti nel data lake di AEP. |
>| Inoltro eventi + acquisizione AEP | È necessario disporre degli stessi eventi sia in AEP (per profili, pubblico, percorsi) che in sistemi esterni | Più comune per le organizzazioni che utilizzano [!DNL RT-CDP] o [!DNL AJO] insieme ad analisi di terze parti. Lo stream di dati invia eventi sia ai set di dati di AEP che alle regole di inoltro degli eventi. |
>| Inoltro eventi + più servizi Adobe | Sono necessari eventi instradati simultaneamente ad AEP, [!DNL Target], [!DNL Analytics] e destinazioni esterne | Abilita tutti i servizi richiesti nello stream di dati. Ogni servizio riceve l&#39;evento in modo indipendente. |

**Navigazione interfaccia utente:** [!DNL Experience Platform] > Raccolta dati > Flussi dati > Seleziona o crea flussi dati

**Dettagli configurazione chiave:**

- L’inoltro eventi dello stream di dati deve essere abilitato nella configurazione del servizio o nelle impostazioni avanzate
- Collegare la proprietà di inoltro degli eventi (creata nella fase 2) allo stream di dati
- Conferma che lo schema XDM assegnato allo stream di dati corrisponda alla struttura dell’evento inviata dal meccanismo di raccolta

**Documentazione di Experience League:**

- [Configurare gli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Panoramica sugli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview)
- [Panoramica sull’inoltro degli eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)

### Fase 2: proprietà ed estensioni di inoltro degli eventi

**Funzione applicazione:** AEP: Impostazione proprietà inoltro eventi

**Configurazione:** proprietà di inoltro degli eventi nell&#39;interfaccia utente di Data Collection, insieme alle estensioni necessarie per le destinazioni di destinazione. La proprietà di inoltro degli eventi è il contenitore per tutte le regole, gli elementi dati e le estensioni che definiscono la logica di inoltro lato server.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: proprietà singola rispetto a più proprietà**
>
>È necessario utilizzare una proprietà di inoltro degli eventi per tutte le destinazioni o proprietà separate?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Proprietà singola | La maggior parte delle implementazioni; tutte le regole di inoltro condividono lo stesso flusso di eventi | Più semplice da gestire, singolo flusso di lavoro di pubblicazione, tutte le regole valutano rispetto a ogni evento. Utilizza le condizioni della regola per filtrare gli eventi che vanno a determinate destinazioni. |
>| Più proprietà | Sono necessari team diversi per gestire in modo indipendente diverse integrazioni di destinazione, oppure si hanno requisiti di isolamento dell’ambiente rigidi | Ogni proprietà ha un proprio flusso di lavoro di pubblicazione e può essere collegata a diversi flussi di dati. Aumenta il sovraccarico di gestione ma migliora i limiti di controllo degli accessi. |

>[!NOTE]
>
>**Decisione: quali estensioni installare**
>
>Seleziona le estensioni in base alle destinazioni di destinazione e all’opzione di implementazione scelta (A, B o C dall’alto).
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Estensioni specifiche della destinazione ([!DNL Meta], [!DNL Google], [!DNL AWS], ecc.) | La destinazione ha un’estensione predefinita e desideri una configurazione personalizzata minima (opzione A o C) | Ogni estensione richiede credenziali specifiche per la destinazione (token API, ID di misurazione, ID account). Consulta la documentazione dell’estensione per i tipi di evento supportati e i campi obbligatori. |
>| Solo estensione Cloud Connector | Tutte le destinazioni utilizzeranno richieste HTTP personalizzate (opzione B) | L’estensione Cloud Connector viene installata per impostazione predefinita. Utilizza la funzione Segreti per memorizzare in modo sicuro le chiavi API e i token di autenticazione. |
>| Connettore cloud e specifico per la destinazione | Sono disponibili diverse destinazioni supportate e personalizzate (opzione C) | Installa estensioni specifiche per destinazioni ben supportate e utilizza Cloud Connector per il resto. |

**Navigazione interfaccia utente:** [!DNL Experience Platform] > Raccolta dati > Inoltro eventi > Crea proprietà (o seleziona esistente)

**Dettagli configurazione chiave:**

- Denomina la proprietà con una convenzione chiara (ad esempio, &quot;Inoltro eventi - Produzione&quot; o &quot;EF - Analytics &amp; Advertising&quot;).
- Installa l&#39;estensione [!DNL Adobe Cloud Connector] (inclusa per impostazione predefinita per le azioni del webhook personalizzato)
- Installare le estensioni specifiche per la destinazione e configurarne le credenziali
- Utilizza la funzione Segreti (Raccolta dati > Inoltro eventi > Segreti) per memorizzare in modo sicuro chiavi API, token e credenziali
- Configurare gli ambienti (Sviluppo, Staging, Produzione) per flussi di lavoro di pubblicazione sicuri

**Documentazione di Experience League:**

- [Guida introduttiva all’inoltro degli eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)
- [Catalogo estensioni inoltro eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [Segreti di inoltro eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)
- [Estensione Adobe Cloud Connector](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)

### Fase 3: definizione della regola dell’evento

**Funzione applicazione:** AEP: definizione regola evento, AEP: mappatura destinazione

**Configurazione:** regole che valutano i dati dell&#39;evento in arrivo, applicano condizioni per filtrare gli eventi da inoltrare e definiscono azioni per inviare i dati agli endpoint di destinazione. Ogni regola è costituita da condizioni (quando attivare) e azioni (cosa fare). Gli elementi dati estraggono e trasformano i valori dal payload dell’evento XDM per utilizzarli nelle condizioni della regola e nelle configurazioni delle azioni.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: strategia filtro eventi**
>
>Come determinare quali eventi vengono inoltrati a ciascuna destinazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Inoltra tutti gli eventi | La destinazione richiede un flusso di eventi completo (ad esempio, data warehouse per l’archiviazione di eventi non elaborati) | Configurazione più semplice: nessuna condizione necessaria. Volume di dati elevato nella destinazione. Considera i limiti di costo e tasso di destinazione. |
>| Filtra per tipo di evento | Destinazioni diverse richiedono tipi di evento diversi (ad esempio, acquisti per pubblicità, visualizzazioni di pagina per analisi) | Utilizza condizioni basate su `arc.event.xdm.eventType` o campi XDM simili. Riduce i dati non necessari nella destinazione. |
>| Filtra per attributi evento | Devono essere inoltrati solo gli eventi specifici che soddisfano determinati criteri (ad esempio, acquisti al di sopra di una soglia, eventi da percorsi di pagina specifici) | Utilizza i valori degli elementi dati nelle condizioni della regola. Più complesso, ma riduce il rumore a destinazione. |

>[!NOTE]
>
>**Decisione: approccio alla trasformazione dei dati**
>
>Come devono essere trasformati i dati dell’evento XDM per il payload di destinazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Mappatura diretta del campo XDM tramite elementi dati | I campi di destinazione vengono mappati in modo pulito sui campi XDM (comune con l’inoltro basato su estensione) | Creare elementi dati che fanno riferimento a percorsi XDM (ad esempio, `arc.event.xdm.commerce.order.priceTotal`). Le estensioni spesso forniscono un’interfaccia utente di mappatura. |
>| Trasformazione del codice personalizzato | La destinazione richiede un formato di payload significativamente diverso da XDM, oppure i campi devono essere hashati, concatenati o ristrutturati | Utilizza elementi dati di codice personalizzato o codice personalizzato a livello di azione per trasformare il payload. Più flessibile, ma più difficile da mantenere. |
>| Combinazione di elementi dati e codice personalizzato | Alcuni campi vengono mappati direttamente, mentre altri richiedono una trasformazione | Utilizza elementi dati per mappature semplici e blocchi di codice personalizzati per trasformazioni complesse. Equilibrio tra manutenibilità e flessibilità. |

>[!NOTE]
>
>**Decisione: gestione PII nei dati inoltrati**
>
>Come devono essere trattate le informazioni di identificazione personale prima dell’inoltro?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Escludi completamente i campi PII | La destinazione non richiede PII e i criteri di governance limitano la condivisione | Configura le regole per omettere i campi PII dal payload inoltrato. Approccio più semplice per la conformità in materia di privacy. |
>| Hash dei campi PII prima dell’inoltro | La destinazione richiede identificatori con hash (ad esempio, [!DNL Meta] richiede un&#39;e-mail con hash SHA-256 per l&#39;API di conversione) | Utilizza elementi dati di codice personalizzato per applicare l’hashing SHA-256. Alcune estensioni gestiscono automaticamente l’hashing. |
>| Inoltra PII con base contrattuale | La destinazione dispone di un accordo di elaborazione dei dati ed esiste la base giuridica per la condivisione di PII | Assicurati che le etichette di utilizzo dei dati e i criteri di governance (S3) consentano la condivisione. Documentare la base giuridica. |

**Navigazione interfaccia utente:** [!DNL Experience Platform] > Raccolta dati > Inoltro eventi > Seleziona proprietà > Elementi dati/Regole

**Dettagli configurazione chiave:**

- **Gli elementi dati** fanno riferimento all&#39;evento XDM in ingresso utilizzando il prefisso del percorso `arc.event.xdm.` (ad esempio, `arc.event.xdm.web.webPageDetails.URL` per l&#39;URL della pagina)
- **Condizioni regola** valutano i valori degli elementi dati per determinare se la regola deve essere attivata
- **Le azioni regola** utilizzano azioni specifiche per l&#39;estensione (per l&#39;opzione A) o azioni &quot;Effettua chiamata di recupero&quot; del connettore cloud (per l&#39;opzione B) per inviare dati alle destinazioni
- Ogni regola può avere più azioni, consentendo l’inoltro di un singolo evento a più destinazioni
- Utilizza l’ordinamento delle regole per controllare la sequenza di valutazione quando più regole possono essere attivate per lo stesso evento
- Eseguire il test completo delle regole nell’ambiente di sviluppo prima di pubblicarle in produzione

**Opzioni divergenti:**

**Per L&#39;Opzione A (Basata Su Estensione):**

Configura le azioni regola utilizzando i tipi di azione predefiniti dell&#39;estensione di destinazione. Ad esempio, l&#39;estensione API per le conversioni [!DNL Meta] fornisce un&#39;azione &quot;Invia evento&quot; in cui i campi XDM vengono mappati sui [!DNL Meta] parametri dell&#39;evento (event_name, event_time, user_data, custom_data). L&#39;estensione gestisce la formattazione del payload, l&#39;hashing e la comunicazione API.

**Per L&#39;Opzione B (Webhook Personalizzato):**

Configura le azioni delle regole utilizzando l’azione &quot;Fai chiamata di recupero&quot; dell’estensione Cloud Connector. Specifica l’URL di destinazione, il metodo HTTP (in genere POST), le intestazioni di richiesta (inclusa l’Autorizzazione) e crea il corpo della richiesta utilizzando elementi dati e/o codice personalizzato. Sei responsabile della corrispondenza esatta del formato del payload previsto dell’API di destinazione.

**Per L&#39;Opzione C (Ibrida):**

Crea regole separate per ogni destinazione. Le regole basate sull’estensione utilizzano i tipi di azione dell’estensione; le regole personalizzate utilizzano le chiamate di recupero Cloud Connector. Tutte le regole coesistono nella stessa proprietà e vengono valutate in modo indipendente rispetto a ogni evento in ingresso.

**Documentazione di Experience League:**

- [Regole di inoltro degli eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [Elementi dati nell’inoltro degli eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/ui/data-elements)
- [Regole nella raccolta dati](https://experienceleague.adobe.com/en/docs/experience-platform/tags/ui/rules)
- [Estensione Adobe Cloud Connector](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)

### Fase 4: pubblicazione e attivazione

**Funzione dell&#39;applicazione:** AEP: inoltro dell&#39;esecuzione

**Configurazione:** il flusso di lavoro di pubblicazione che promuove le regole di inoltro degli eventi dallo sviluppo all&#39;ambiente di produzione. L’inoltro degli eventi utilizza lo stesso modello di pubblicazione basato su libreria dei tag, con ambienti e artefatti di build che controllano la configurazione attiva in Edge Network.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: rigore del flusso di lavoro di pubblicazione**
>
>Quanto deve essere rigoroso il processo di pubblicazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Diretto alla produzione (Sviluppo > Produzione) | Team di piccole dimensioni, destinazioni a basso rischio o implementazioni proof-of-concept | Distribuzione più rapida ma rischio più elevato di problemi di produzione. Ideale per il test iniziale con destinazioni non critiche. |
>| Progressione completa dell’ambiente (Sviluppo > Staging > Produzione) | Implementazioni di produzione con destinazioni critiche (piattaforme pubblicitarie, data warehouse) | Consigliato per tutti i casi di utilizzo in produzione. La gestione temporanea consente la convalida con traffico reale prima della distribuzione nell’ambiente di produzione. |

**Navigazione interfaccia utente:** [!DNL Experience Platform] > Raccolta dati > Inoltro eventi > Seleziona proprietà > Flusso di pubblicazione

**Dettagli configurazione chiave:**

- Crea una libreria contenente tutte le regole, gli elementi dati e le configurazioni di estensione da pubblicare
- Genera e testa nell’ambiente di sviluppo utilizzando prima lo strumento di monitoraggio dell’inoltro degli eventi per verificare che gli eventi vengano inoltrati correttamente
- Promuovi in staging per la convalida di pre-produzione con traffico live
- Pubblica in produzione solo dopo aver confermato la corretta consegna dell’evento in Staging
- Utilizza il controllo delle versioni della libreria per tenere traccia delle modifiche e, se necessario, abilitare il rollback

**Documentazione di Experience League:**

- [Panoramica sulla pubblicazione](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/overview)
- [Librerie](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/libraries)
- [Ambienti](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/environments)
- [Build](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/builds)

### Fase 5: Monitoraggio e convalida

**Funzione applicazione:** AEP: monitoraggio

**Configurazione:** dashboard di monitoraggio e processi di convalida per confermare che gli eventi vengono inoltrati correttamente, diagnosticare gli errori e mantenere l&#39;integrità operativa della distribuzione di inoltro degli eventi.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: profondità di monitoraggio**
>
>Quanto a fondo deve essere monitorato l’inoltro degli eventi?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Solo dashboard monitoraggio inoltro eventi | Monitoraggio di base per destinazioni non critiche o implementazioni iniziali | Fornisce una panoramica delle percentuali di inoltro riuscito/non riuscito e dei codici di risposta della destinazione. Sufficiente per la maggior parte delle implementazioni. |
>| Monitoraggio dell’inoltro degli eventi + convalida lato destinazione | Destinazioni critiche in cui la completezza dei dati influisce direttamente sui risultati aziendali (tracciamento delle conversioni pubblicitarie, integrità del data warehouse) | Riferimento incrociato alle metriche di inoltro lato Adobe con conferma della ricezione lato destinazione. Rileva i casi edge in cui la destinazione accetta la richiesta ma non elabora i dati. |
>| Stack di osservabilità completo (monitoraggio inoltro eventi + convalida destinazione + avvisi AEP) | Distribuzioni su scala aziendale con requisiti SLA per la distribuzione dei dati | Combina il monitoraggio dell’inoltro degli eventi con gli avvisi della piattaforma AEP per una visualizzazione completa. Configurare le notifiche di avviso per l&#39;inoltro delle soglie di errore. |

**Navigazione interfaccia utente:** [!DNL Experience Platform] > Raccolta dati > Inoltro eventi > Seleziona proprietà > Monitoraggio

**Dettagli configurazione chiave:**

- Lo strumento di monitoraggio dell’inoltro degli eventi mostra il volume degli eventi, i tassi di successo e i dettagli degli errori per regola e per destinazione
- Monitora i codici di risposta HTTP dalle destinazioni: 2xx indica il successo, 4xx indica gli errori del client (probabili problemi di payload o autenticazione), 5xx indica gli errori lato destinazione
- Utilizza l&#39;estensione del browser [!DNL Adobe Experience Platform Debugger] per verificare gli eventi che fluiscono dal client alle regole di inoltro degli eventi tramite Edge Network
- Convalida end-to-end verificando che gli eventi inoltrati vengano visualizzati nel sistema di destinazione (ad esempio, controllare [!DNL Google Analytics] rapporti in tempo reale, [!DNL Meta] Gestione eventi o tabelle data warehouse)
- Imposta gli avvisi di AEP per gli errori di origine e flusso di dati per rilevare problemi a monte che impedirebbero agli eventi di raggiungere le regole di inoltro degli eventi

**Documentazione di Experience League:**

- [Monitoraggio inoltro eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring)
- [Adobe Experience Platform Debugger](https://experienceleague.adobe.com/en/docs/experience-platform/debugger/home)
- [Panoramica degli avvisi](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

## Considerazioni sull’implementazione

Questa sezione descrive i guardrail, le insidie comuni, le best practice e le decisioni di compromesso da tenere presenti durante l’implementazione.

### Guardrail e limiti

- L’inoltro degli eventi elabora gli eventi in tempo reale in Edge Network; per impostazione predefinita, non è disponibile una modalità batch o una coda di nuovi tentativi per le consegne non riuscite
- I limiti di velocità di Edge Network si applicano al volume totale di eventi elaborati per flusso di dati — [guardrail di Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/guardrails)
- Le regole di inoltro degli eventi vengono eseguite lato server e non possono accedere alle risorse lato client (DOM, cookie, localStorage)
- Il codice personalizzato nelle regole di inoltro degli eventi viene eseguito in un ambiente in modalità sandbox; non tutte le API JavaScript del browser sono disponibili
- La chiamata di recupero del connettore cloud ha limiti di timeout; le destinazioni che rispondono lentamente possono causare timeout
- L’inoltro degli eventi è soggetto al routing geografico Edge Network: gli eventi vengono elaborati nella posizione Edge più vicina
- La dimensione massima del payload per le richieste inoltrate è regolata dai limiti di Edge Network

### Insidie comuni

- **Inoltro di tutti i campi XDM senza filtro:** L&#39;invio dell&#39;intero payload dell&#39;evento XDM a una destinazione che richiede solo pochi campi comporta uno spreco della larghezza di banda, un aumento dei costi di destinazione e la condivisione involontaria di PII. Mappa sempre solo i campi obbligatori nelle regole di inoltro.

- **La mancata protezione delle credenziali con i segreti:** La codifica di chiavi o token API negli elementi dati o nelle azioni delle regole crea un rischio per la sicurezza. Utilizza sempre la funzione Segreti raccolta dati per memorizzare le credenziali in modo sicuro e farvi riferimento nelle regole.

- **Ignorare i limiti di velocità di destinazione:** Le destinazioni di terze parti spesso hanno limiti di velocità API. Se il volume di eventi supera la capacità di una destinazione, è possibile che gli eventi vengano eliminati o che l’accesso API sia limitato. Rivedi la documentazione di destinazione per i limiti di velocità e implementa il filtro per ridurre il volume degli eventi, se necessario.

- **Pubblicazione diretta in produzione senza gestione temporanea:** Se si ignora l&#39;ambiente di gestione temporanea, gli errori vengono rilevati solo in produzione, causando potenzialmente la perdita di dati nelle destinazioni critiche. Convalida sempre in Staging con prima il traffico live.

- **Nessun monitoraggio dei codici di risposta HTTP:** Una regola che viene attivata senza errori non garantisce che la destinazione abbia elaborato correttamente i dati. Monitora i codici di risposta della destinazione (disponibili nello strumento Monitoraggio inoltro eventi) ed esamina eventuali risposte non 2xx.

- **Riferimenti al percorso XDM non configurati correttamente:** Gli elementi dati utilizzano il prefisso `arc.event.xdm.` per fare riferimento ai campi evento in ingresso. Un percorso errato (ad esempio, se manca un livello di nidificazione) produce automaticamente valori Null anziché generare errori. Convalidare i valori degli elementi dati utilizzando il debugger.

### Best practice

- **Iniziare con una singola destinazione ed espanderla gradualmente**. Convalidare l&#39;inoltro di eventi end-to-end con una destinazione prima di aggiungere regole e destinazioni aggiuntive. Questo semplifica il debug e crea fiducia nell’infrastruttura.

- **Utilizzare convenzioni di denominazione coerenti**: denominare elementi dati, regole e librerie con una convenzione chiara che identifichi la destinazione, il tipo di evento e l&#39;ambiente (ad esempio, &quot;Regola: Meta - Eventi di acquisto&quot;, &quot;DE: Totale ordine&quot;).

- **Implementa il filtro a livello di campo per la privacy**: anche se la destinazione dichiara di gestire i dati PII in modo appropriato, applica il filtro lato server ai campi sensibili di tipo strip o hash prima che lascino Edge Network. Questo è il principale vantaggio in termini di governance dell’inoltro di eventi rispetto ai tag lato client.

- **Versione delle configurazioni**: utilizza il flusso di lavoro di pubblicazione della libreria per gestire gli snapshot con versione della configurazione di inoltro degli eventi. Documenta ciò che ogni versione della libreria contiene a scopo di controllo e rollback.

- **Test con Platform Debugger**: l&#39;estensione [!DNL Adobe Experience Platform Debugger] fornisce visibilità sul ciclo di vita dell&#39;evento da SDK lato client tramite l&#39;elaborazione Edge Network. Utilizzala durante lo sviluppo e la risoluzione dei problemi.

- **Allineare le regole di inoltro degli eventi alla struttura dello schema XDM**. Se l&#39;inoltro degli eventi è un requisito noto, progettare lo schema XDM e la tassonomia degli eventi in modo da includere i campi necessari per le destinazioni. L’adattamento delle modifiche allo schema dopo la distribuzione comporta un aumento delle interruzioni.

### Decisioni di compromesso

>[!NOTE]
>
>**Compensazione: semplicità dell&#39;estensione e flessibilità del webhook**
>
>Le estensioni predefinite riducono al minimo lo sforzo di implementazione e la manutenzione, ma si limitano alle funzioni e ai formati di payload supportati dall&#39;estensione. I webhook personalizzati forniscono un controllo completo ma richiedono un maggiore sviluppo e una manutenzione continua.
>
>- **L&#39;opzione A (basata sull&#39;estensione) favorisce:** rapidità di commercializzazione, riduzione della dipendenza degli sviluppatori, gestione automatica delle credenziali, riduzione della manutenzione
>- **Basato su webhook (opzione B) preferisce:** Controllo completo del payload, supporto per qualsiasi endpoint HTTP, logica di trasformazione personalizzata, indipendenza dai cicli di rilascio delle estensioni
>- **Consiglio:** Utilizzare le estensioni quando disponibili e sufficienti. Torna ai webhook personalizzati solo quando la destinazione non dispone di un’estensione o quando l’estensione non supporta le funzioni API specifiche necessarie. L’approccio ibrido (opzione C) è la scelta pragmatica per la maggior parte delle organizzazioni.

>[!NOTE]
>
>**Compensazione: inoltro di tutti gli eventi e filtro selettivo**
>
>L’inoltro di tutti gli eventi a una destinazione garantisce la completezza ma aumenta il volume dei dati, i costi della destinazione e l’esposizione alla privacy. Il filtro selettivo riduce il rumore ma rischia di perdere eventi che potrebbero essere preziosi.
>
>- **Inoltra tutti i favori degli eventi:** Completezza, semplicità, verifica futura dei dati (i dati sono disponibili se necessario in un secondo momento)
>- **Il filtro selettivo favorisce:** efficienza in termini di costi, riduzione del rischio di privacy, dati di destinazione più puliti, conformità ai principi di minimizzazione dei dati
>- **Consiglio:** Filtro selettivo predefinito in base al tipo di evento e alla rilevanza aziendale. Inoltra solo gli eventi e i campi di cui ogni destinazione ha effettivamente bisogno. Questo è in linea con i principi di minimizzazione dei dati (articolo 5 del RGPD) e riduce i costi operativi.

>[!NOTE]
>
>**Compensazione: proprietà singola rispetto a più proprietà**
>
>Una singola proprietà di inoltro degli eventi è più semplice da gestire, ma significa che tutte le regole condividono un unico flusso di lavoro di pubblicazione. Più proprietà forniscono isolamento, ma aumentano il sovraccarico di gestione.
>
>- **Proprietà singola a favore:** semplicità, pubblicazione unificata, elementi dati condivisi, debug più semplice
>- **Più proprietà favoriscono:** controllo dell&#39;accesso a livello di team, cadenze di pubblicazione indipendenti, isolamento degli errori di destinazione
>- **Consiglio:** inizia con una singola proprietà per la maggior parte delle implementazioni. Dividi in più proprietà solo se i diversi team possiedono integrazioni di destinazione diverse e necessitano di cicli di rilascio indipendenti, oppure se i requisiti normativi richiedono un rigido isolamento tra i flussi di dati.

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sugli argomenti trattati in questa guida.

**Inoltro eventi**

- [Panoramica sull’inoltro degli eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [Guida introduttiva all’inoltro degli eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)
- [Monitoraggio inoltro eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring)
- [Segreti di inoltro eventi](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)

**Estensioni di inoltro eventi**

- [Catalogo delle estensioni lato server](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [Estensione Adobe Cloud Connector](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [Estensione API per conversioni Meta](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/meta/overview)
- [Estensione Piattaforma Google Cloud](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [Estensione AWS](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/aws/overview)
- [Estensione Snowflake](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/snowflake/overview)
- [Estensione per conversioni avanzate di Google Ads](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-ads-enhanced-conversions/overview)
- [Estensione Mailchimp](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/mailchimp/overview)

**Raccolta dati e Edge Network**

- [Configurare gli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Panoramica sugli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview)
- [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Panoramica dell’API del server Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Panoramica sui tag](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
