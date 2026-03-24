---
title: Attivazione del pubblico nelle destinazioni
description: Scopri come valutare e pubblicare segmenti di pubblico in destinazioni esterne per il targeting o l’eliminazione tramite Adobe Real-Time CDP.
solution: Real-Time Customer Data Platform, Experience Platform
exl-id: b0b9d937-45d2-48f9-ac4c-3611c6e35f58
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7043'
ht-degree: 1%

---

# Attivazione del pubblico nelle destinazioni

Questa guida fornisce un riferimento completo all&#39;implementazione per attivare i tipi di pubblico da Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP) a destinazioni esterne. È progettato per architetti di soluzioni, tecnici di marketing e ingegneri di implementazione che devono valutare i segmenti di pubblico e pubblicarli su piattaforme di annunci, archiviazione cloud, sistemi CRM o partner di dati per il targeting, l’eliminazione, la modellazione lookalike o l’arricchimento di analisi.

Presenta tutte le opzioni di implementazione disponibili con analisi di compromesso, indicazioni sulla decisione, percorsi di navigazione dell’interfaccia utente e riferimenti alla documentazione di Experience League.

La guida descrive l’intero ciclo di vita dell’attivazione del pubblico, dalla definizione e valutazione dei segmenti di pubblico fino alla configurazione delle connessioni di destinazione e alla pubblicazione dei tipi di pubblico, al monitoraggio dello stato di attivazione e all’applicazione della conformità alle normative.

## Panoramica del caso d’uso

Le organizzazioni devono fornire dati sul pubblico a sistemi esterni per alimentare campagne multimediali a pagamento, arricchire record CRM, condividere dati con i partner o alimentare analisi a valle. Audience Activation to Destinations è il modello di attivazione di base in RT-CDP: valuta quali profili sono idonei per un pubblico di destinazione, si connette a una o più destinazioni esterne, mappa gli attributi del profilo su campi specifici della destinazione e pubblica il pubblico per il consumo a valle.

Questo modello si applica ogni volta che l’obiettivo è quello di ottenere i dati di un pubblico a un sistema esterno nel formato giusto al momento giusto. Non implica la consegna di messaggi, la personalizzazione nel sito o l’analisi. È il punto di partenza più comune per le implementazioni RT-CDP e funge da blocco predefinito su cui si compongono altri modelli.

Le parti interessate tipiche includono i team di marketing digitale che gestiscono media a pagamento, i team di dati che arricchiscono i magazzini, i team di gestione delle relazioni con i clienti che preparano elenchi di contatti per le campagne e i team di privacy che garantiscono la conformità in materia di governance dei flussi di dati in uscita.

>[!NOTE]
>Se la tua organizzazione utilizza [!DNL Real-Time CDP] B2B edition e si attiva su destinazioni basate su account, consulta [Attivazione del pubblico B2B](b2b-audience-activation.md). Questo modello condivide la stessa meccanica di attivazione ma utilizza un modello di dati account-and-person B2B e richiede la licenza B2B edition.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### Acquisire nuovi clienti

Espandi la base di clienti tramite campagne di acquisizione mirate, tipi di pubblico simili e ottimizzazione di contenuti multimediali a pagamento.

**KPI:** nuovi clienti, costo acquisizione cliente, conversione potenziali clienti/lead

[Ulteriori informazioni sull&#39;acquisizione di nuovi clienti](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Riduzione dei costi di acquisizione dei clienti

Migliora l’efficienza del targeting, elimina i clienti esistenti dalle campagne di acquisizione e ottimizza la spesa per i contenuti multimediali.

**KPI:** Costo Acquisizione Cliente, Costo Per Lead, Efficienza

[Ulteriori informazioni sulla riduzione dei costi di acquisizione dei clienti](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### Ottimizzazione della spesa di marketing e del ROI

Migliora il ritorno sull’investimento marketing migliorando il targeting, l’attribuzione, l’eliminazione del pubblico e l’allocazione del budget.

**KPI:** Risparmio sui costi, Costo di acquisizione cliente, Ricavi incrementali

[Ulteriori informazioni sull’ottimizzazione della spesa di marketing e del ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Esempi di casi d’uso tattici

- **Pubblico della piattaforma di annunci targeting**: invia segmenti qualificati alle piattaforme di media a pagamento per il targeting della campagna
- **Eliminazione dei supporti a pagamento dei clienti esistenti** — Escludi i clienti noti dalle campagne di acquisizione sulle piattaforme di annunci per eliminare gli sprechi
- **Pubblico di seed lookalike**: invia segmenti di clienti di alto valore a Facebook, Google Ads o The Trade Desk come pubblico di seed per l’espansione lookalike
- **Sincronizzazione CRM per l&#39;abilitazione alle vendite**: attiva tipi di pubblico ad alto intento o di valore elevato in modo che i team di vendita possano dare priorità all&#39;impegno
- **Condivisione del pubblico tra partner dati**: condividi segmenti di pubblico qualificati con partner dati per il targeting o la misurazione cooperativi
- **Esportazione archiviazione cloud per arricchimento data warehouse** — Esporta appartenenza pubblico e attributi di profilo in Amazon S3, Azure Blob, Google Cloud Storage o SFTP per analisi a valle
- **Attivazione pubblico per retargeting** - Attiva i visitatori del sito che non sono stati convertiti in piattaforme di retargeting
- **Sincronizzazione elenco contatti con provider di servizi di posta elettronica**: invia iscrizione pubblico a piattaforme di posta elettronica di terze parti per una distribuzione coordinata

## Indicatori chiave di prestazioni

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Costo di acquisizione cliente (CAC) | Costo per acquisire un nuovo cliente tramite tipi di pubblico attivati | Spesa totale per contenuti multimediali/nuovi clienti attribuiti al pubblico attivato |
| Percentuale di corrispondenza pubblico | Percentuale di profili attivati con corrispondenza riuscita nella destinazione | Profili associati alla destinazione / profili esportati da RT-CDP |
| Risparmi di eliminazione | Si evitano spese di supporto eliminando i clienti esistenti dalle campagne di acquisizione | Dimensione stimata del pubblico per CPM x soppresso |
| Tasso di consegna attivazione | Percentuale di profili consegnati correttamente alla destinazione | Profili consegnati/profili nel pubblico sorgente |
| Tempo di attivazione | Tempo trascorso dalla definizione del pubblico alla prima consegna nella destinazione | Misura dalla creazione del segmento alla prima esecuzione confermata del flusso di dati |
| Precisione popolazione pubblico | Allineamento tra le dimensioni del pubblico previste e quelle effettive nella destinazione | Conteggio del pubblico di destinazione/conteggio del pubblico RT-CDP |

## Schema del caso d’uso

**Audience Activation in destinazioni**: valuta e pubblica un segmento di pubblico in destinazioni esterne per il targeting o l&#39;eliminazione.

**Catena di funzioni:** Valutazione pubblico > Configurazione destinazione > Audience Activation > Monitoraggio

## Applicazioni

- **Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP)** — Valutazione del pubblico, gestione della destinazione, attivazione del pubblico, applicazione del consenso e della governance
- **Adobe [!DNL Experience Platform] (AEP)** — Archivio profili, servizio identità, motore di segmentazione, governance dei dati

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve essere al suo posto | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Presunto sul posto | Sandbox RT-CDP attivata e attiva. Autorizzazioni di attivazione e gestione delle destinazioni assegnate ai ruoli di implementazione. Credenziali dell’account di destinazione disponibili per le piattaforme di destinazione. | [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home), [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/it/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Obbligatorio | Lo schema del profilo deve includere attributi che verranno mappati sui campi di destinazione (ad esempio e-mail, telefono, identificatori con hash, attributi demografici). Lo schema deve essere abilitato per il profilo con set di dati che ricevono attivamente i dati. | [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home), [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/schema/composition) |
| Origini dati e raccolta | Presunto sul posto | I dati di profilo che alimentano la valutazione del pubblico devono essere acquisiti e aggiornati. Le pipeline di acquisizione in batch e/o in streaming sono operative. Web SDK, connettori di origine o acquisizione in batch che fornisce dati in set di dati abilitati per il profilo. | [Panoramica origini](https://experienceleague.adobe.com/it/docs/experience-platform/sources/home), [Panoramica Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/home) |
| Configurazione identità e profilo | Obbligatorio | È necessario configurare gli spazi dei nomi delle identità per la corrispondenza della destinazione (ad esempio, e-mail con hash per i tipi di pubblico personalizzati di Facebook, Customer Match di Google Ads). I criteri di unione devono produrre profili unificati con tutti gli attributi richiesti per l’attivazione. | [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home), [Panoramica dei criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview) |
| Definizione e segmentazione del pubblico | Obbligatorio | Il pubblico di destinazione è definito utilizzando Segment Builder (Generatore di segmenti), Audience Composition (Composizione del pubblico) o Federated Audience Composition (Composizione federata del pubblico). Metodo di valutazione (batch, streaming o edge) selezionato in base alle esigenze di latenza di attivazione. Questa funzione è esercitata nella fase 1 del presente piano. | [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home), [Guida dell&#39;interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Consigliato | Attributi calcolati come il valore del ciclo di vita, il punteggio di coinvolgimento o il punteggio di propensione migliorano la precisione del pubblico e forniscono attributi di arricchimento da mappare sulle destinazioni. Particolarmente utile quando le destinazioni traggono vantaggio dalla segmentazione del pubblico basata su valori o su punteggi. | [Panoramica attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Consigliato | Le policy di scadenza dei set di dati e dei profili garantiscono l’aggiornamento e la conformità dei dati. La configurazione dello schema di consenso assicura che siano attivati solo i profili consentiti. Critico per la conformità normativa durante l&#39;esportazione dei dati in sistemi esterni. | [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/it/docs/experience-platform/data-lifecycle/home) |
| Etichettatura e applicazione dell’utilizzo dati | Consigliato | Le etichette e i criteri di governance impediscono l’attivazione di dati limitati a destinazioni non autorizzate (ad esempio, PII per piattaforme di annunci, segmenti sensibili per partner di dati). Particolarmente importante per l’attivazione del pubblico su sistemi esterni di terze parti. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home), [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview) |
| Monitoraggio e osservabilità | Incluso | Il monitoraggio dell&#39;attivazione fa parte della catena di funzioni (fase 5). Include il monitoraggio dell’esecuzione dei flussi di dati, gli avvisi sullo stato della consegna, il tracciamento della popolazione del pubblico e la visibilità dell’utilizzo delle licenze. | [Monitorare i flussi di dati di destinazione](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations), [Panoramica avvisi](https://experienceleague.adobe.com/it/docs/experience-platform/observability/alerts/overview) |
| Reporting e analisi | Consigliato | L’analisi CJA dell’efficacia dell’attivazione del pubblico consente di misurare le prestazioni per i tipi di pubblico attivati (ad esempio, incremento della conversione da soppressione, ROAS da tipi di pubblico simili). | [Panoramica di CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-overview/cja-overview) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Real-Time CDP] (RT-CDP)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Valutazione del pubblico | Fase 1: Valutazione del pubblico | Definisci le regole del pubblico e valuta l’iscrizione al segmento utilizzando metodi di valutazione batch, in streaming o edge |
| Composizione del pubblico | Fase 1: Valutazione del pubblico | Facoltativamente, comporre tipi di pubblico derivati tramite operazioni di arricchimento, classificazione, suddivisione, esclusione e unione per logiche di pubblico complesse |
| Configurazione di destinazione | Fase 2: configurazione della destinazione | Configurare connessioni autenticate a destinazioni esterne con parametri di mappatura e pianificazione dei campi |
| Audience Activation | Fase 3: Audience Activation | Pubblicare i tipi di pubblico valutati su destinazioni configurate con mappatura degli attributi e pianificazione delle esportazioni |
| Applicazione del consenso e della governance | Fase 4: convalida della governance | Applicare le preferenze di consenso e i criteri di utilizzo dei dati prima e durante l’attivazione del pubblico su sistemi esterni |

## Prerequisiti

- [ ] la licenza RT-CDP è attiva con i diritti di attivazione del pubblico
- [ È stato eseguito il provisioning della sandbox di Target ] e questa è accessibile al team di implementazione
- [ I ruoli utente di ] includono le autorizzazioni di gestione della destinazione e di attivazione del pubblico
- [ ] Sono disponibili le credenziali di autenticazione per ogni destinazione (token OAuth, chiavi API, chiavi di accesso S3 o credenziali account del servizio)
- [ Lo schema del profilo ] include tutti gli attributi che devono essere mappati ai campi di destinazione
- [ ] Gli spazi dei nomi di identità necessari per la corrispondenza della destinazione sono configurati (ad esempio e-mail con hash, telefono, ID dispositivo)
- [ ] le pipeline di acquisizione dati sono operative e i profili stanno popolando l&#39;archivio profili
- [ ] Le etichette e i criteri di governance dei dati vengono esaminati per gli attributi attivati (in particolare per le destinazioni esterne)
- [ ] I campi di consenso sono compilati sui profili se è richiesto un filtro basato sul consenso

## Opzioni di implementazione

Per questo modello di caso d’uso sono disponibili le seguenti opzioni di implementazione. Esaminare ogni opzione e la tabella di confronto per determinare l&#39;approccio migliore per i requisiti.

### Opzione A: attivazione della destinazione di streaming

**Consigliato per:** aggiornamenti in tempo reale dell&#39;iscrizione al pubblico per piattaforme di annunci o sistemi partner: Facebook Custom Audiences, Google Ads Customer Match, LinkedIn Matched Audiences, The Trade Desk e destinazioni simili basate su API di streaming.

**Funzionamento:**

L’attivazione della destinazione di streaming offre alla destinazione le modifiche di iscrizione al pubblico quasi in tempo reale, in quanto i profili si qualificano o non si qualificano dal segmento. Quando un attributo di profilo cambia o si verifica un evento comportamentale che causa l’ingresso o l’uscita di un profilo da un pubblico, l’aggiornamento dell’appartenenza viene inviato in streaming alla destinazione in pochi minuti.

Questo approccio richiede un connettore di destinazione in streaming (supportato dalla maggior parte delle piattaforme di annunci principali) e un metodo di valutazione del pubblico in streaming o Edge. La valutazione del pubblico monitora continuamente le modifiche del profilo di qualificazione e il flusso di dati di attivazione invia gli aggiornamenti man mano che si verificano. La destinazione riceve modifiche incrementali dell’iscrizione anziché snapshot del pubblico completo.

L’attivazione in streaming è l’impostazione predefinita per la maggior parte delle destinazioni di piattaforme di annunci nel catalogo RT-CDP. Il connettore di destinazione gestisce automaticamente l’autenticazione API, la limitazione della frequenza e la logica dei nuovi tentativi.

**Considerazioni chiave:**

- La valutazione del pubblico deve utilizzare lo streaming o la valutazione Edge (i tipi di pubblico solo batch non possono fornire destinazioni di streaming in tempo reale)
- Non tutte le espressioni di segmento sono idonee per la valutazione dello streaming: aggregazioni complesse, query con più entità e alcune funzioni basate sul tempo richiedono l’esecuzione in batch
- I limiti di velocità delle API dei partner di destinazione possono influire sulla velocità effettiva durante eventi di qualificazione di pubblico di grandi dimensioni
- Gli aggiornamenti degli attributi del profilo vengono inviati insieme alle modifiche di appartenenza, mantenendo aggiornati i dati di destinazione

**Vantaggi:**

- Aggiornamento del pubblico quasi in tempo reale a destinazione (minuti, non ore)
- Gli aggiornamenti incrementali riducono il volume di trasferimento dei dati rispetto alle esportazioni complete
- Gestione automatica degli eventi di qualificazione e di squalifica
- La maggior parte delle destinazioni delle piattaforme di annunci supporta lo streaming in modalità nativa

**Limitazioni:**

- Richiede definizioni di segmenti idonei per lo streaming (set di funzioni di segmento limitate)
- Nessun controllo sul formato file o sulla struttura di esportazione — formato dati determinato dal connettore di destinazione
- Impossibile esportare in destinazioni di archiviazione basate su file (S3, Blob Azure, SFTP)
- I limiti di velocità delle API di destinazione possono limitare le modifiche a volumi elevati

**Experience League:**

- [Attivare i tipi di pubblico nelle destinazioni di streaming](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Catalogo delle destinazioni di streaming](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/overview)

### Opzione B: attivazione della destinazione batch (esportazione file)

**Ideale per:** esportazioni di tipi di pubblico pianificate in sistemi di archiviazione cloud, data warehouse o sistemi che utilizzano importazioni basate su file: Amazon S3, Azure Blob Storage, Google Cloud Storage, SFTP, Data Landing Zone.

**Funzionamento:**

L’attivazione della destinazione batch valuta i tipi di pubblico su una frequenza pianificata ed esporta i risultati come file (CSV, JSON o Parquet) nella destinazione di archiviazione configurata. L’esportazione può includere istantanee complete del pubblico o modifiche incrementali (nuove qualifiche e interruzioni dall’ultima esportazione).

L’implementazione comporta la configurazione di una connessione di destinazione basata su file con le credenziali di archiviazione, le preferenze del formato file (delimitatore, compressione, convenzione di denominazione) e una pianificazione di esportazione (ogni giorno, ogni 3 ore, ogni 6 ore, ecc.). Ogni esportazione genera file contenenti l’appartenenza al pubblico e tutti gli attributi di profilo mappati.

Questo approccio supporta la più ampia gamma di consumatori downstream perché lo scambio di dati basato su file è universalmente supportato. È anche l’unica opzione per i casi di utilizzo dell’archiviazione cloud e dell’arricchimento del data warehouse.

**Considerazioni chiave:**

- La valutazione del pubblico può utilizzare qualsiasi metodo (batch, streaming o perimetrale); l’esportazione stessa viene eseguita secondo una pianificazione, indipendentemente
- Le convenzioni di formato, compressione e denominazione dei file possono essere configurate in base alla destinazione
- Supporta sia le esportazioni incrementali (solo le modifiche) che le esportazioni complete (snapshot completo del pubblico)
- Esporta intervalli di granularità della pianificazione da ogni 3 ore a ogni giorno

**Vantaggi:**

- Controllo completo su formato file di esportazione (CSV, JSON, Parquet), compressione e denominazione
- Compatibile con qualsiasi sistema downstream in grado di utilizzare file
- Supporta sia la modalità di esportazione incrementale che quella completa
- È possibile esportare i tipi di pubblico con qualsiasi metodo di valutazione (inclusi i segmenti solo batch con logica di segmentazione complessa)
- Supporta l’esportazione ad hoc (su richiesta) eseguita al di fuori della pianificazione regolare

**Limitazioni:**

- La latenza è intrinsecamente più elevata: i dati del pubblico arrivano a destinazione secondo una pianificazione, non in tempo reale
- Le esportazioni basate su file richiedono che il sistema di destinazione elabori e acquisisca i file
- Costi di archiviazione a destinazione per i file esportati
- Volumi di dati più elevati per esportazione rispetto agli aggiornamenti di streaming incrementali

**Experience League:**

- [Attivare i tipi di pubblico per le destinazioni di esportazione dei profili in batch](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Catalogo delle destinazioni basate su file](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage)

### Opzione C: attivazione con più destinazioni

**Ideale per:** attivare lo stesso pubblico in più destinazioni simultaneamente, ad esempio inviando un elenco di soppressione a tutte le piattaforme di annunci, sincronizzando un segmento di alto valore sia alle piattaforme CRM che di annunci o coordinando la portata del pubblico tra più partner multimediali.

**Funzionamento:**

L’attivazione con più destinazioni non è un meccanismo tecnico separato, ma una composizione delle opzioni A e B applicate allo stesso pubblico su più connessioni di destinazione. Lo stesso pubblico viene attivato su due o più destinazioni, ciascuna con la propria configurazione di connessione, la mappatura dei campi e la pianificazione.

Ogni connessione di destinazione funziona in modo indipendente: un’attivazione in streaming su Facebook e un’esportazione batch in S3 possono essere eseguite contemporaneamente dallo stesso pubblico di origine. Le mappature dei campi sono configurate per destinazione, in modo da poter inviare attributi diversi a sistemi diversi in base alle esigenze di ogni destinazione e ai criteri di governance consentiti.

Si tratta di un modello di produzione comune per le organizzazioni che operano su più piattaforme di annunci, che gestiscono la sincronizzazione CRM insieme all’attivazione dei contenuti multimediali o che devono distribuire i dati sul pubblico sia ai sistemi operativi che a quelli analitici.

**Considerazioni chiave:**

- Ogni destinazione dispone di mappatura dei campi, pianificazione e valutazione della governance indipendenti
- I criteri di governance vengono applicati per destinazione — attributi diversi possono essere consentiti per tipi di destinazione diversi
- È possibile attivare un singolo pubblico contemporaneamente per una combinazione di destinazioni di streaming e batch
- L’aggiunta di una nuova destinazione non richiede modifiche alle attivazioni esistenti

**Vantaggi:**

- Distribuzione coordinata del pubblico in tutti i sistemi esterni da un’unica definizione di pubblico
- La configurazione indipendente per destinazione consente mappature e pianificazioni ottimizzate
- L’applicazione della governance per destinazione garantisce la conformità tra diversi tipi di destinazione
- Centralizza la gestione dell&#39;audience e supporta l&#39;attivazione distribuita

**Limitazioni:**

- Più connessioni di destinazione per configurare, autenticare e gestire
- La complessità del monitoraggio aumenta con ogni destinazione: è necessario tenere traccia degli errori di attivazione per ogni destinazione
- L’utilizzo delle licenze (profili attivati) può essere conteggiato per destinazione a seconda delle adesioni
- La manutenzione della mappatura dei campi su più destinazioni richiede coordinamento

**Experience League:**

- [Panoramica sulle destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/home)
- [Catalogo delle destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/overview)

### Confronto delle opzioni

| Criteri | Opzione A: streaming | Opzione B: Batch (esportazione file) | Opzione C: multi-destinazione |
| --- | --- | --- | --- |
| Ideale per | Targeting ed eliminazione di piattaforme di annunci in tempo reale | Arricchimento di data warehouse, integrazione di sistema basata su file | Distribuzione coordinata del pubblico su più piattaforme |
| Complessi | Bassa | Medio | Alta |
| Latenza | Minuti (quasi in tempo reale) | Ore (programmate) | Mix di minuti e ore per destinazione |
| Controllo formato file | Nessuno (la destinazione determina il formato) | Completo (CSV, JSON, Parquet, compressione, denominazione) | Per destinazione |
| Valutazione del pubblico | È necessario usare streaming o Edge | Qualsiasi metodo (batch, streaming, edge) | Requisiti per destinazione |
| Richiede | Connettore di destinazione di streaming, segmento idoneo allo streaming | Connettore di destinazione basato su file, credenziali di archiviazione | Più connettori di destinazione e credenziali |
| Governance | Valutazione di una singola destinazione | Valutazione di una singola destinazione | Valutazione per destinazione |

### Scegli l’opzione giusta

Utilizza la seguente logica decisionale per selezionare l’approccio di implementazione corretto:

1. **Di quante destinazioni hai bisogno?** Se devi attivare lo stesso pubblico su due o più destinazioni, stai implementando l’opzione C (che compone le opzioni A e B per destinazione). Procedere alle domande 2 e 3 per ciascuna destinazione.

2. **La destinazione supporta lo streaming?** Se la destinazione è una piattaforma di annunci (Facebook, Google Ads, LinkedIn, The Trade Desk) o un’integrazione di partner con un’API di streaming, utilizza l’opzione A per tale destinazione. Se la destinazione è l’archiviazione cloud (S3, Azure Blob, GCS, SFTP) o un sistema che consuma file, utilizza l’opzione B.

3. **Quanto rapidamente deve arrivare il pubblico alla destinazione?** Se l’appartenenza a un pubblico deve riflettersi nella destinazione in pochi minuti (ad esempio, soppressione in tempo reale durante le campagne attive), utilizza l’opzione A. Se è sufficiente la consegna giornaliera o su più ore (ad esempio, aggiornamento settimanale del data warehouse, sincronizzazione batch del sistema di gestione delle relazioni con i clienti), utilizza l’opzione B.

4. **Il pubblico utilizza una logica di segmentazione complessa?** Se la definizione del pubblico include aggregazioni di più eventi, finestre temporali di grandi dimensioni o funzioni che non sono idonee per la valutazione dello streaming, utilizza l’opzione B (destinazioni batch) o assicurati che anche le destinazioni dell’opzione A ricevano un pubblico valutato in batch secondo una pianificazione.

## Fasi di implementazione

L&#39;implementazione segue queste fasi. Ogni fase include dettagli di configurazione, punti decisionali e collegamenti alla documentazione di Experience League.

### Fase 1: Valutazione del pubblico

**Funzione dell&#39;applicazione:** RT-CDP: Audience Evaluation, RT-CDP: Audience Composition

**Configurazione:** Definire il pubblico di destinazione che verrà attivato nelle destinazioni. Ciò include la specifica dei criteri di pubblico (quali profili sono idonei), la selezione del metodo di valutazione (la rapidità con cui l’iscrizione si aggiorna) e la convalida della popolazione del pubblico. Questo è il punto di partenza per tutte le attivazioni: senza un pubblico definito e valutato, non c&#39;è nulla da attivare.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: metodo di creazione del pubblico**
>
>Come definire il pubblico di destinazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Generatore di segmenti (basato su regole) | Definizione del pubblico standard utilizzando gli attributi di profilo, gli eventi comportamentali e le condizioni di appartenenza ai segmenti | Definizione della regola più flessibile; supporta lo streaming e la valutazione Edge per espressioni idonee; ideale per tipi di pubblico a condizione singola o moderatamente complessi |
>| Composizione del pubblico | Il pubblico richiede la combinazione, la classificazione, la suddivisione o l’esclusione di pubblici esistenti | Area di lavoro visiva per operazioni sequenziali; i risultati vengono valutati solo in batch; massimo 10 blocchi di composizione per area di lavoro |
>| Federated Audience Composition | I criteri di pubblico devono essere valutati in base ai dati in data warehouse esterni senza acquisirli in AEP | Interroga direttamente i database esterni; evita la duplicazione dei dati; richiede la licenza Federated Audience Composition |

>[!NOTE]
>
>**Decisione: metodo di valutazione**
>
>Quanto rapidamente devono entrare e uscire dal pubblico i profili?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Batch | Campagne pianificate, aggiornamenti giornalieri del pubblico o logica di segmentazione complessa non idonea per lo streaming | Elabora fino a 24 milioni di profili per processo; supporta tutte le funzioni di segmentazione; viene eseguito secondo una pianificazione (pianificazione cron predefinita giornaliera o personalizzata) |
>| Streaming | Modifiche all’iscrizione al pubblico in tempo reale necessarie per l’attivazione della destinazione di streaming o per casi d’uso attivati da eventi | In tempo reale (secondi o minuti); set di funzioni di segmentazione limitato: eventi semplici, confronti di attributi e finestre temporali limitate; nessuna query con più entità |
>| Edge | Personalizzazione della stessa pagina o qualificazione immediata del pubblico necessaria ai margini | Latenza in millisecondi; set di regole più restrittivo — solo attributi di profilo e semplici controlli di appartenenza ai segmenti; utilizzato principalmente per la personalizzazione nel sito (meno comune per l’attivazione della destinazione) |

>[!NOTE]
>
>**Decisione: criterio di unione**
>
>Quale criterio di unione utilizzare per la valutazione del pubblico?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Timestamp ordinato (impostazione predefinita) | Casi d’uso più frequenti: i dati recenti dovrebbero avere priorità in caso di conflitto tra frammenti di profilo | Più comune; utilizza il valore dell’attributo aggiornato più di recente |
>| Precedenza set di dati | Le origini dati specifiche devono ignorare le altre a prescindere dalla marca temporale | Richiede la definizione di un ordine di priorità dei set di dati; utile quando un sistema di gestione delle relazioni con i clienti deve sempre ignorare i dati raccolti sul web |

**Navigazione interfaccia utente:** Cliente > Tipi di pubblico > Crea pubblico > Genera regola (per Generatore di segmenti) o Componi pubblico (per Composizione pubblico)

**Dettagli configurazione chiave:**

- Definisci i criteri di pubblico in base al caso d’uso: attributi di profilo, eventi comportamentali, appartenenza a un segmento o condizioni basate sul tempo
- Applica regole di soppressione per escludere i profili da non attivare (ad esempio, convertiti di recente, con annullamento dell’abbonamento globale)
- Convalida la dimensione della popolazione del pubblico prima di procedere all&#39;attivazione
- Confermare l&#39;allineamento del metodo di valutazione al tipo di destinazione selezionato nella fase 2

**Opzioni divergenti:**

**Per L&#39;Opzione A (Attivazione Destinazione Di Streaming):**
Il pubblico deve utilizzare lo streaming o la valutazione Edge per distribuire aggiornamenti di iscrizione in tempo reale. Verificare che l&#39;espressione della regola del segmento sia idonea per la valutazione in streaming, evitando funzioni di aggregazione basate sul tempo, query con più entità e riferimenti `inSegment()` a segmenti solo batch.

**Per L&#39;Opzione B (Attivazione Destinazione Batch):**
Qualsiasi metodo di valutazione funziona. La valutazione batch è la scelta più comune, poiché l’esportazione stessa viene eseguita secondo una pianificazione. Conferma l’esistenza di una pianificazione di valutazione batch nella sandbox o creane una.

**Per L&#39;Opzione C (Attivazione Con Più Destinazioni):**
Il metodo di valutazione dovrebbe tener conto della destinazione più impegnativa. Se una destinazione richiede lo streaming, il pubblico deve utilizzare la valutazione dello streaming. Se tutte le destinazioni sono batch, è sufficiente la valutazione batch.

**Documentazione di Experience League:**

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/pql/overview)
- [Segmentazione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Panoramica sulla composizione del pubblico](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/audience-composition)
- [Metodi di valutazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home#evaluation-methods)


### Fase 2: configurazione della destinazione

**Funzione applicazione:** RT-CDP: configurazione di destinazione

**Configurazione:** stabilire connessioni autenticate alle destinazioni esterne in cui verranno pubblicati i tipi di pubblico. Ciò include la selezione della destinazione dal catalogo, l’immissione delle credenziali di autenticazione e la configurazione di parametri specifici della destinazione, ad esempio il formato del file, la posizione di archiviazione e la pianificazione delle esportazioni. Ogni destinazione richiede la propria configurazione di connessione.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: tipo di destinazione**
>
>Dove vanno distribuiti i tipi di pubblico?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Destinazione Advertising (streaming) | Targeting o soppressione sulle piattaforme di annunci (Facebook, Google Ads, LinkedIn, The Trade Desk, ecc.) | Connettori in streaming; aggiornamenti dell’iscrizione quasi in tempo reale; corrispondenza delle identità tramite e-mail con hash, telefono o ID dispositivo |
>| Destinazione archiviazione cloud (batch) | Esportazione in S3, Azure Blob, GCS, SFTP o Data Landing Zone per l’arricchimento del data warehouse | Esportazione basata su file; formato configurabile (CSV, JSON, Parquet); cadenza pianificata |
>| Destinazione CRM | Sincronizza i tipi di pubblico con Salesforce, Microsoft Dynamics o HubSpot per agevolare le vendite | In genere streaming; richiede la mappatura di campi specifici per CRM; potrebbe richiedere le autorizzazioni di amministratore CRM |
>| Destinazione partner dati | Condividere dati sul pubblico con partner di misurazione o targeting | Varia in base al partner; rivedi le implicazioni di governance derivanti dalla condivisione esterna dei dati |
>| Destinazione personalizzata (Destination SDK) | Sistema di destinazione non disponibile nel catalogo | Richiede la creazione di una destinazione personalizzata utilizzando Destination SDK; maggiore sforzo di implementazione |

>[!NOTE]
>
>**Decisione: metodo di autenticazione**
>
>Quali credenziali richiede la destinazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| OAuth 2.0 | Piattaforme pubblicitarie e destinazioni SaaS (Facebook, Google, Salesforce) | Richiede il flusso di autorizzazione iniziale; i token vengono aggiornati automaticamente; più comune per le destinazioni di streaming |
>| Chiave di accesso / Chiave segreta | Archiviazione cloud (S3, BLOB Azure) | Credenziali statiche; la rotazione deve essere pianificata; adatta per destinazioni basate su file |
>| Account del servizio/chiave API | API dei partner e integrazioni personalizzate | Richiede il provisioning delle credenziali dal partner di destinazione |
>| Stringa di connessione | Destinazioni basate su Azure | Stringa singola contenente tutti i parametri di connessione |

>[!NOTE]
>
>**Decisione: tipo di esportazione (solo destinazioni batch)**
>
>Come creare il pacchetto dei dati sul pubblico da esportare?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Esportazione incrementale | Solo le nuove qualifiche e interdizioni o decadenze dall&#39;ultima esportazione | File di dimensioni ridotte; elaborazione più rapida a destinazione; richiede che il sistema di destinazione mantenga lo stato |
>| Esportazione completa | Snapshot completo del pubblico a ogni esecuzione | File più grandi; la destinazione ottiene un&#39;immagine completa ogni volta; più semplice per i sistemi che eseguono una sostituzione completa |

**Navigazione interfaccia utente:** Connessioni > Destinazioni > Catalogo > [Seleziona destinazione] > Configura

**Dettagli configurazione chiave:**

- Sfoglia il catalogo di destinazione e seleziona la destinazione
- Fornisci le credenziali di autenticazione e verifica la connessione
- Per le destinazioni batch: configura il formato file (CSV, JSON, Parquet), la compressione, il modello di denominazione file e la pianificazione di esportazione
- Per le destinazioni di streaming: la connessione viene in genere stabilita tramite il flusso di autorizzazione OAuth
- Verifica che lo stato della connessione di destinazione sia visualizzato come attivo prima di procedere all&#39;attivazione

**Opzioni divergenti:**

**Per L&#39;Opzione A (Attivazione Destinazione Di Streaming):**
Seleziona una destinazione di streaming dal catalogo (Advertising o categorie Social). Completa il flusso di autorizzazione OAuth. La connessione è pronta per l’attivazione dopo la conferma dell’autorizzazione.

**Per L&#39;Opzione B (Attivazione Destinazione Batch):**
Seleziona una destinazione basata su file dal catalogo (categoria Archiviazione cloud). Configurare il percorso di archiviazione, il formato del file, la compressione, la convenzione di denominazione e la pianificazione di esportazione. Verificare la connessione verificando l&#39;accesso in scrittura al percorso di archiviazione.

**Per L&#39;Opzione C (Attivazione Con Più Destinazioni):**
Ripeti questa fase per ogni destinazione. Ogni connessione è indipendente: è possibile che si disponga di una combinazione di destinazioni di streaming e batch. Documenta l’autenticazione e la configurazione di ogni connessione per riferimento operativo.

**Documentazione di Experience League:**

- [Catalogo delle destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/overview)
- [Panoramica sulle destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/home)
- [Attivare i tipi di pubblico per le destinazioni di esportazione dei profili in batch](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Attivare i tipi di pubblico nelle destinazioni di streaming](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Panoramica di Destination SDK](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/destination-sdk/overview)
- [Opzioni di configurazione di Destination SDK](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/destination-sdk/functionality/configuration-options)


### Fase 3: Attivazione del pubblico

**Funzione dell&#39;applicazione:** RT-CDP: Audience Activation

**Configurazione:** Pubblicare il pubblico valutato nella destinazione configurata creando il flusso di dati di attivazione. Ciò comporta la selezione dei tipi di pubblico da attivare, la mappatura degli attributi del profilo ai campi di destinazione e la configurazione della pianificazione di esportazione. Il flusso di dati di attivazione connette il pubblico di origine alla destinazione di destinazione e gestisce la distribuzione continua dei dati.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: mapping degli attributi**
>
>Quali attributi di profilo devono essere inclusi nell’attivazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Solo campi di identità | La destinazione deve corrispondere solo ai profili (ad esempio, iscrizione al pubblico nelle piattaforme di annunci) | Trasferimento dati minimo; più sicuro per la privacy; tipico per il targeting e l’eliminazione delle piattaforme di annunci |
>| Identità e attributi del profilo | La destinazione richiede attributi di arricchimento per la personalizzazione o la segmentazione (ad esempio, sincronizzazione CRM, condivisione partner) | Più dati trasferiti; richiede una revisione della governance per ogni attributo; controlla le etichette di utilizzo dei dati rispetto all’azione di marketing della destinazione |
>| Identità + attributi calcolati | La destinazione trae vantaggio da punteggi o aggregazioni derivati (ad esempio, livello del valore del ciclo di vita, punteggio di propensione per il targeting dei partner) | Richiede la configurazione di attributi calcolati; arricchimento di alto valore per i sistemi a valle |

>[!NOTE]
>
>**Decisione: pianificazione delle esportazioni (solo destinazioni batch)**
>
>Con quale frequenza devono essere esportati i dati sul pubblico?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Giornaliero | Frequenza di aggiornamento standard; la maggior parte dei casi di utilizzo batch | Bilancia la freschezza con il costo di elaborazione; impostazione predefinita più comune |
>| Ogni 3-6 ore | Casi d’uso con frequenza più elevata, ad esempio ottimizzazione di campagne infragiornaliere | Generazione di file più frequente; maggiore capacità di archiviazione ed elaborazione a destinazione |
>| On-demand (ad hoc) | Esportazione una tantum o attivazione urgente fuori ciclo | Pianificazione manuale dell’attivazione ignorata; utile per test o esigenze urgenti della campagna |

**Navigazione interfaccia utente:** Connessioni > Destinazioni > Sfoglia > [Seleziona la destinazione] > Attiva tipi di pubblico

**Dettagli configurazione chiave:**

- Seleziona uno o più tipi di pubblico da attivare nella destinazione
- Mappare gli attributi del profilo e i campi di identità ai campi specifici della destinazione
- Per le destinazioni di streaming: conferma la mappatura dello spazio dei nomi delle identità (ad esempio, e-mail con hash all’extern_id di Facebook)
- Per le destinazioni batch: configura la pianificazione di esportazione, seleziona la modalità di esportazione incrementale o completa e imposta la prima data di esportazione
- Rivedi il riepilogo dell’attivazione per confermare tutte le mappature e le pianificazioni prima di pubblicarle

**Opzioni divergenti:**

**Per L&#39;Opzione A (Attivazione Destinazione Di Streaming):**
Seleziona i tipi di pubblico e mappa gli spazi dei nomi delle identità sui campi di identità di destinazione. L’attivazione inizia immediatamente dopo la pubblicazione: l’iscrizione del pubblico cambia flusso per la destinazione quasi in tempo reale. Non è necessario alcun programma di esportazione; l’attivazione è continua.

**Per L&#39;Opzione B (Attivazione Destinazione Batch):**
Seleziona i tipi di pubblico, mappa gli attributi del profilo e configura la pianificazione dell’esportazione. Scegli tra le modalità di esportazione incrementale e completa. Facoltativamente, attiva un’esportazione ad hoc per la consegna immediata al di fuori della pianificazione regolare.

**Per L&#39;Opzione C (Attivazione Con Più Destinazioni):**
Ripeti il flusso di lavoro di attivazione per ogni destinazione. Lo stesso pubblico può essere attivato su più destinazioni con mappature di attributi diverse per destinazione. Ad esempio, invia solo e-mail con hash alle piattaforme di annunci ma includi gli attributi demografici al CRM.

**Documentazione di Experience League:**

- [Attivare i tipi di pubblico nelle destinazioni di streaming](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Attivare i tipi di pubblico per le destinazioni di esportazione dei profili in batch](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Attivare i tipi di pubblico on-demand per le destinazioni batch](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [Monitorare i flussi di dati per le destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)


### Fase 4: convalida della governance

**Funzione dell&#39;applicazione:** RT-CDP: applicazione del consenso e della governance

**Configurazione:** Verificare che i criteri di governance e le preferenze di consenso siano applicati correttamente prima e durante l&#39;attivazione. Questa fase garantisce che i dati con restrizioni (PII, attributi sensibili) non vengano inviati a destinazioni non autorizzate e che i profili senza consenso valido siano esclusi dall’attivazione. L’applicazione della governance avviene automaticamente al momento dell’attivazione, ma la convalida proattiva impedisce le attivazioni bloccate e le violazioni della conformità.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: approccio di applicazione della governance**
>
>Quando deve essere convalidata la conformità alla governance?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Proattivo (preattivazione) | Consigliato per tutte le implementazioni, soprattutto quando si attiva su sistemi esterni di terze parti | Esamina le etichette e i criteri di utilizzo dei dati prima di configurare le mappature dei campi; evita errori di attivazione e garantisce la conformità fin dall’inizio |
>| Reattivo (al momento dell’attivazione) | Quando i criteri di governance sono già consolidati e il team è sicuro della conformità | Platform applica automaticamente i criteri all’attivazione; le violazioni bloccano l’attivazione o escludono gli attributi con restrizioni; possono causare errori imprevisti se i criteri non sono ben compresi |

>[!NOTE]
>
>**Decisione: filtro del consenso**
>
>In che modo le preferenze di consenso influiscono sull’attivazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Applicazione del consenso abilitata | Obbligatorio per l’attivazione per pubblicità o destinazioni di marketing con consenso legalmente richiesto | I profili senza consenso valido (consents.marketing.{channel}.val = &#39;y&#39;) vengono automaticamente esclusi dall&#39;attivazione; richiede l&#39;acquisizione dei dati del consenso |
>| Nessun filtro di consenso | Destinazioni per uso interno o esportazioni Analytics per le quali il consenso non si applica al trasferimento di dati | Appropriato solo se l’utilizzo dei dati non costituisce un’azione di marketing che richiede il consenso; consulta il team legale/privacy |

**Navigazione interfaccia utente:** Privacy > Criteri > Criteri di consenso (per la revisione del consenso); Governance dei dati > Criteri (per la revisione dei criteri di utilizzo dei dati)

**Dettagli configurazione chiave:**

- Esamina le etichette di utilizzo dei dati applicate ai set di dati e ai campi dello schema che vengono attivati
- Verifica che i criteri di governance siano attivi per l’azione di marketing associata alla destinazione (ad esempio, &quot;Esporta a terze parti&quot; per le piattaforme di annunci)
- I campi di consenso di conferma sono compilati su profili e l’applicazione del consenso è abilitata per i canali pertinenti
- Se vengono rilevate violazioni dei criteri, risolvi il problema rimuovendo i campi con restrizioni dal mapping della destinazione o selezionando una destinazione alternativa

**Documentazione di Experience League:**

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home)
- [Applicazione dei criteri](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/enforcement/overview)
- [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview)
- [Consenso e preferenze](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Applicazione dei criteri di consenso](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/policies/user-guide)


### Fase 5: Monitoraggio e convalida

**Funzione applicazione:** Monitoraggio e osservabilità

**Configurazione:** configurare il monitoraggio continuo per i flussi di dati di attivazione, configurare gli avvisi per gli errori, convalidare la popolazione del pubblico nelle destinazioni e tenere traccia dell&#39;utilizzo delle licenze. Il monitoraggio è fondamentale per le attivazioni di produzione in cui gli errori di consegna influiscono direttamente sulle prestazioni della campagna e sulla spesa per i contenuti multimediali.

**Dettagli configurazione chiave:**

- Rivedi lo stato di esecuzione del flusso di dati per ogni destinazione attiva per confermare che i tipi di pubblico siano stati consegnati correttamente
- Configurare gli avvisi per gli errori di attivazione della destinazione, i ritardi del flusso di dati e le anomalie della popolazione del pubblico
- Tracciamento dei profili esportati e dei profili non riusciti per esecuzione del flusso di dati
- Monitorare i tassi di corrispondenza del pubblico alla destinazione (dove è disponibile il reporting sulla destinazione)
- Verifica l’utilizzo della licenza per tenere traccia del volume di profilo attivato rispetto ai diritti

**Navigazione interfaccia utente:** Connessioni > Destinazioni > Sfoglia > [Seleziona destinazione] > Flussi dati in esecuzione (per il monitoraggio dell&#39;attivazione); Avvisi > Regole avvisi > Sottoscrivi (per la configurazione degli avvisi); Amministrazione > Utilizzo licenze (per il monitoraggio delle licenze)

**Documentazione di Experience League:**

- [Monitorare i flussi di dati per le destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Panoramica degli avvisi](https://experienceleague.adobe.com/it/docs/experience-platform/observability/alerts/overview)
- [Panoramica di Observability Insights](https://experienceleague.adobe.com/it/docs/experience-platform/observability/home)
- [Dashboard utilizzo licenze](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

## Considerazioni sull’implementazione

Rivedi le seguenti considerazioni prima e durante l’implementazione.

### Guardrail e limiti

- **Limite definizione segmento:** Massimo 4.000 definizioni segmento per sandbox — [Guardrail di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)
- **Flussi dati per destinazione:** Massimo 100 flussi dati per connessione di destinazione: [Guardrail destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/guardrails)
- **Dimensione file esportazione in batch:** Le destinazioni basate su file hanno limiti massimi per le dimensioni dei file di esportazione; i tipi di pubblico di grandi dimensioni vengono automaticamente suddivisi in più file
- **Velocità effettiva di destinazione in streaming:** I limiti di velocità effettiva al secondo sono impostati da ciascun partner di destinazione; le modifiche di pubblico con volume elevato potrebbero essere limitate
- **Capacità di valutazione batch:** Fino a 24 milioni di profili per processo di valutazione segmento per impostazione predefinita
- **Composizione pubblico:** massimo di 10 blocchi di composizione per area di lavoro; i tipi di pubblico composti vengono valutati solo in batch
- **Grafo identità:** massimo di 50 identità per grafo - [Guardrail del servizio identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/guardrails)
- **Attributi calcolati:** massimo di 25 attributi calcolati per sandbox — [Guardrail attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview#guardrails)
- **Panoramica sui guardrail di attivazione:** [Guardrail di attivazione](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/guardrails)

### Insidie comuni

- **Segmento di streaming con logica di regola non idonea:** definizione di un pubblico con funzioni di aggregazione complesse o query con più entità e valutazione in streaming prevista. Questi segmenti tornano automaticamente alla valutazione batch, causando latenza imprevista. Prevenzione: rivedi i requisiti di idoneità allo streaming prima di definire il pubblico.

- **Nessun profilo esportato a causa del filtro del consenso:** tutti i profili nel pubblico non dispongono di valori di consenso validi, causando l&#39;esclusione dell&#39;intero pubblico al momento dell&#39;attivazione. Prevenzione: verifica che l’acquisizione dei dati sul consenso sia operativa e che i campi del consenso siano compilati prima dell’attivazione.

- **Attivazione blocco imprevisto dei criteri di governance:** Le etichette di utilizzo dei dati nei campi dello schema attivano violazioni dei criteri che impediscono l&#39;attivazione. Prevenzione: valuta proattivamente la conformità alle normative (fase 4) prima di configurare le mappature dei campi. Esamina quali etichette vengono ereditate dallo schema.

- **Scadenza credenziali di destinazione:** i token OAuth o le chiavi API scadono, causando errori di attivazione senza alcun avviso immediato. Prevenzione: configura gli avvisi per gli errori di attivazione della destinazione e stabilisce una pianificazione di rotazione delle credenziali.

- **Spazi dei nomi di identità non corrispondenti:** Lo spazio dei nomi di identità configurato nel mapping di attivazione non corrisponde a quello previsto dalla destinazione (ad esempio, l&#39;invio di un&#39;e-mail in formato testo normale quando la destinazione richiede un&#39;e-mail con hash SHA-256). Prevenzione: rivedi la documentazione di destinazione per i formati di identità richiesti prima di configurare la mappatura.

- **Errori di mapping campi che causano errori di esportazione:** mapping di un attributo di profilo a un campo di destinazione con tipo di dati o formato non compatibili. Prevenzione: testa l’attivazione prima con un pubblico ridotto e controlla i dettagli di esecuzione del flusso di dati per individuare eventuali errori di mappatura prima di adattarla ai tipi di pubblico di produzione.

- **Deriva della popolazione di pubblico tra RT-CDP e destinazione:** Il conteggio del pubblico in RT-CDP non corrisponde al conteggio nella destinazione a causa di differenze di corrispondenza delle identità, logica di deduplicazione della destinazione o tempistica. Questo è il comportamento atteso — prevenzione: documenta i benchmark di corrispondenza prevista per destinazione e monitora le deviazioni significative.

### Best practice

- **Inizia con un pubblico di prova:** Attiva un pubblico di prova piccolo e ben conosciuto in ogni nuova destinazione prima di attivare i tipi di pubblico di produzione. Convalida le mappature dei campi, la corrispondenza delle identità e le metriche di consegna con il pubblico di test.

- **Governance dei livelli anticipata:** Applica le etichette di utilizzo dei dati e configura i criteri di governance prima di configurare le attivazioni di destinazione. In questo modo si evitano le attivazioni bloccate e si garantisce la conformità fin dall&#39;inizio.

- **Utilizzare esportazioni incrementali per destinazioni batch:** Le esportazioni incrementali riducono le dimensioni dei file, velocizzano l&#39;elaborazione nella destinazione e riducono al minimo i costi di archiviazione. Utilizza esportazioni complete solo quando il sistema di destinazione richiede una sostituzione completa del pubblico.

- **Standardizzare le convenzioni di denominazione:** Stabilire una denominazione coerente per i tipi di pubblico, le connessioni di destinazione e i flussi di dati in tutta l&#39;organizzazione. Includi il caso d’uso, la destinazione e il metodo di valutazione nei nomi (ad esempio, &quot;Suppression_ExistingCustomers_Facebook_Streaming&quot;).

- **Monitorare le percentuali di corrispondenza:** Monitorare il rapporto tra i profili esportati da RT-CDP e i profili corrispondenti in ogni destinazione. Cali significativi nella percentuale di corrispondenza possono indicare problemi di risoluzione dell’identità, problemi delle credenziali o modifiche all’API di destinazione.

- **Coordinare la soppressione tra le destinazioni:** Quando si utilizzano i tipi di pubblico di soppressione (ad esempio, escludendo i clienti esistenti dalle campagne di acquisizione), attiva il pubblico di soppressione simultaneamente a tutte le piattaforme di annunci rilevanti per mantenere la coerenza.

- **Rivedi ed elimina le attivazioni inattive:** Rivedi periodicamente i flussi di dati di destinazione e disattiva i tipi di pubblico non più necessari. Le attivazioni inattive consumano capacità di licenza e aggiungono costi comuni di monitoraggio.

### Decisioni di compromesso

>[!NOTE]
>
>**Compensazione: aggiornamento del pubblico rispetto alla flessibilità di segmentazione**
>
>La valutazione in streaming fornisce aggiornamenti del pubblico in tempo reale, ma limita le funzioni della regola del segmento utilizzabili. La valutazione in batch supporta il set di funzioni completo per le regole di segmento, ma introduce una latenza (ore anziché minuti).
>
>- **Preferenze streaming:** casi d&#39;uso in tempo reale in cui l&#39;iscrizione al pubblico deve essere visualizzata a destinazione in pochi minuti (soppressione attiva della campagna, retargeting in tempo reale)
>- **Preferenze batch:** logica di pubblico complessa che richiede funzioni di aggregazione, query con più entità o condizioni di intervallo di tempo estese (livelli di valore del ciclo di vita, segmenti comportamentali multi-touch)
>- **Consiglio:** utilizza la valutazione in streaming per i tipi di pubblico attivati in destinazioni di streaming in cui la freschezza in tempo reale aumenta il valore aziendale. Utilizza la valutazione in batch per tipi di pubblico complessi attivati su destinazioni basate su file o quando è sufficiente l’aggiornamento giornaliero. Per i tipi di pubblico che necessitano di entrambe, puoi creare due versioni: un segmento di streaming semplificato per l’attivazione in tempo reale e un segmento batch completo per l’arricchimento periodico.

>[!NOTE]
>
>**Compensazione: esportazione minima di dati rispetto alla mappatura di attributi avanzati**
>
>L’esportazione dei soli campi di identità (e-mail con hash, ID dispositivo) riduce al minimo l’esposizione dei dati e semplifica la governance. L’esportazione di attributi di profilo aggiuntivi (dati demografici, livello di valore, punteggio di coinvolgimento) arricchisce la destinazione ma aumenta la complessità di governance e la responsabilità dei dati.
>
>- **Esportazione minima a favore di:** Approccio basato sulla privacy, minore rischio di governance, mappatura dei campi più semplice, sufficiente per la maggior parte dei casi di utilizzo di targeting e soppressione di piattaforme di annunci
>- **Esportazione avanzata in favore di:** Personalizzazione a valle nella destinazione; arricchimento CRM; condivisione dati partner che richiede dettagli a livello di attributo
>- **Consiglio:** esportazione minima per impostazione predefinita delle sole identità per le destinazioni pubblicitarie. Aggiungi gli attributi del profilo solo quando il caso di utilizzo della destinazione li richiede in modo specifico e la revisione della governance conferma la conformità. Utilizza gli attributi calcolati per fornire valori di arricchimento aggregati e meno sensibili invece dei dati PII non elaborati.

>[!NOTE]
>
>**Compensazione: pubblico singolo per destinazione rispetto ai flussi di dati consolidati per più tipi di pubblico**
>
>L’attivazione di ogni pubblico come flusso di dati separato fornisce isolamento e monitoraggio granulare. L’attivazione di più tipi di pubblico tramite un singolo flusso di dati a una destinazione semplifica la gestione ma riduce l’isolamento.
>
>- **Flussi di dati separati favoriscono:** Monitoraggio indipendente, risoluzione dei problemi semplificata, possibilità di mettere in pausa le singole attivazioni del pubblico senza influire sugli altri
>- **Flussi di dati consolidati favoriscono:** meno connessioni da mantenere, gestione semplificata delle credenziali, riduzione del sovraccarico operativo
>- **Consiglio:** utilizza flussi di dati consolidati quando attivi più tipi di pubblico correlati alla stessa destinazione (ad esempio, tutti i segmenti di soppressione in Facebook). Utilizza flussi di dati separati quando i tipi di pubblico hanno SLA diversi, mappature di attributi diverse o quando l’isolamento degli errori è critico.

## Documentazione correlata

**Destinazioni**

- [Panoramica sulle destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/home)
- [Catalogo delle destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/overview)
- [Attivare i tipi di pubblico nelle destinazioni di streaming](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Attivare i tipi di pubblico per le destinazioni di esportazione dei profili in batch](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Attivare i tipi di pubblico on-demand per le destinazioni batch](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [Guardrail delle destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/guardrails)
- [Panoramica di Destination SDK](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/destination-sdk/overview)

**Tipi di pubblico e segmentazione**

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/pql/overview)
- [Segmentazione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Panoramica sulla composizione del pubblico](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/audience-composition)
- [Guardrail di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)

**Identità e profilo**

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home)
- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Regole di collegamento del grafo identità](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Panoramica del profilo](https://experienceleague.adobe.com/it/docs/experience-platform/profile/home)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview)

**Modellazione dati e schemi**

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home)
- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/schema/composition)

**Governance dei dati**

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home)
- [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview)
- [Criteri di governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/policies/overview)
- [Applicazione dei criteri](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/enforcement/overview)
- [Consenso e preferenze](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Monitoraggio e osservabilità**

- [Monitorare i flussi di dati per le destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Panoramica degli avvisi](https://experienceleague.adobe.com/it/docs/experience-platform/observability/alerts/overview)
- [Panoramica di Observability Insights](https://experienceleague.adobe.com/it/docs/experience-platform/observability/home)
- [Dashboard utilizzo licenze](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Attributi calcolati**

- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview)
- [Guida dell’interfaccia utente attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)

**Raccolta dati e origini**

- [Panoramica sulle origini](https://experienceleague.adobe.com/it/docs/experience-platform/sources/home)
- [Panoramica di Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/home)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)

**Amministrazione**

- [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home)
- [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/it/docs/experience-platform/access-control/home)
- [Controllo degli accessi basato su attributi](https://experienceleague.adobe.com/it/docs/experience-platform/access-control/abac/overview)

**Guardrail**

- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)
- [Guardrail del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/guardrails)
- [Guardrail di attivazione](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/guardrails)
- [Guardrail di acquisizione](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
