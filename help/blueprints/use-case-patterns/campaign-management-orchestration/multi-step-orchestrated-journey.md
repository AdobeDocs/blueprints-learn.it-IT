---
title: Percorso orchestrato con più passaggi
description: Scopri come guidare un profilo attraverso un percorso multi-touch diramato con attese, condizioni e più azioni messaggio nel tempo.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: b2e496eb521fc3dd3290fccdd9a8203384934b88
workflow-type: tm+mt
source-wordcount: '8173'
ht-degree: 1%

---


# Percorso orchestrato in più passaggi

Questa guida fornisce un blueprint di implementazione completo per la creazione di percorsi orchestrati in più passaggi tramite [!DNL Adobe Journey Optimizer] (AJO) e [!DNL Real-Time Customer Data Platform] (RT-CDP). È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono orchestrare percorsi di clienti multi-touch diramati in grado di inviare più messaggi nel tempo.

Presenta tutte le opzioni di implementazione valide, considerazioni sulle decisioni in ogni punto di configurazione e collegamenti alla documentazione di [!DNL Adobe Experience League]. Utilizza questa guida per pianificare, configurare e convalidare l’implementazione del percorso in più passaggi.

## Panoramica del caso d’uso

I percorsi orchestrati in più passaggi sono destinati a scenari aziendali in cui un singolo messaggio non è sufficiente per ottenere il risultato desiderato per il cliente. Invece di un invio una tantum, il percorso guida ogni profilo attraverso una sequenza di punti di contatto, e-mail, messaggi SMS, notifiche push o messaggi in-app, suddivisi su giorni o settimane, con una logica di diramazione che adatta il percorso in base agli attributi del profilo, ai segnali comportamentali o ai dati dell’evento.

Questi percorsi sono il modello di campagna più complesso disponibile in AJO. Combinano una voce basata su pubblico o evento con un’area di lavoro costituita da nodi di azione (messaggi), nodi di condizione (logica di diramazione), nodi di attesa (ritardi) e criteri di uscita (eventi di conversione o timeout). Ogni profilo procede nel percorso in modo indipendente, al proprio ritmo, ricevendo contenuti contestualmente rilevanti in ogni fase.

Questo modello riassume i modelli più semplici: attivazione batch dei messaggi in uscita per campagne a invio singolo e messaggistica attivata da eventi per risposte a evento singolo. Utilizza questo modello quando il caso d’uso richiede di coltivare un profilo attraverso più interazioni nel tempo.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### Miglioramento della conservazione dei clienti

Coinvolgi e rinnova i clienti esistenti tramite esperienze basate sul valore aggiunto e lo sviluppo di relazioni continuative.

**KPI:** mantenimento, valore del ciclo di vita del cliente, coinvolgimento

[Ulteriori informazioni sul miglioramento della customer retention](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### Migliorare l’onboarding dei clienti

Accelerare il time-to-value per i nuovi clienti con esperienze di benvenuto e percorsi di attivazione semplificati e personalizzati.

**KPI:** coinvolgimento, mantenimento, tassi di conversione

[Ulteriori informazioni su come migliorare l’onboarding dei clienti](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)

### Rivolgersi nuovamente ai clienti inattivi

Recupera i clienti inattivi o inattivi con campagne di riattivazione mirate basate su segnali comportamentali.

**KPI:** coinvolgimento, mantenimento, tassi di conversione

### Recupera carrelli e percorsi abbandonati

Coinvolgi nuovamente gli utenti che abbandonano durante i flussi di acquisto, applicazione o iscrizione con follow-up personalizzati e tempestivi.

**KPI:** tassi di conversione, ricavi incrementali, coinvolgimento

[Ulteriori informazioni sul ripristino di carrelli e percorsi abbandonati](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)

## Esempi di casi d’uso tattici

Gli scenari seguenti illustrano le applicazioni comuni del pattern di percorso orchestrato in più passaggi.

- **Serie sull&#39;onboarding dei clienti**: e-mail di benvenuto, seguita da formazione sulle funzioni, quindi da una richiesta di attivazione nei primi 14 giorni dopo la registrazione
- **Campagna di ricoinvolgimento**: un promemoria e-mail, quindi un&#39;offerta di incentivo e un avviso finale per i clienti inattivi di oltre 3 settimane
- **percorso milestone fedeltà** — Notifica di aggiornamento livello, seguita da un&#39;offerta esclusiva, quindi da un promemoria di rinnovo in vista dell&#39;anniversario di iscrizione
- **Sequenza di riconquista** - E-mail con &quot;Ci manchi&quot;, poi offerta di sconto via e-mail, quindi un promemoria SMS finale per gli acquirenti inattivi
- **percorso di adozione del prodotto**: benvenuto di prova, suggerimenti di utilizzo, quindi richiesta di aggiornamento con l&#39;avanzare del periodo di prova
- **Sequenza di rinnovo dell&#39;abbonamento** - Notifica di 30 giorni, promemoria di 7 giorni, quindi messaggio di scadenza per i prossimi rinnovi dell&#39;abbonamento
- **Alimentazione post-acquisto**: e-mail di ringraziamento, guida all&#39;utilizzo, consigli sulla vendita incrociata, quindi una richiesta di revisione oltre 30 giorni dopo l&#39;acquisto

## Indicatori chiave di prestazioni

Utilizza i KPI seguenti per misurare l’efficacia dell’implementazione di un percorso orchestrato in più passaggi.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Percentuale di completamento percorso | Percentuale di profili che completano l’intero percorso senza uscire anticipatamente | Rapporto percorso: chiuso (completato) / inserito |
| Tasso di conversione passo | Percentuale di profili che avanzano da un passaggio all’altro | Metriche per nodo nel rapporto percorso |
| Tasso di coinvolgimento canale | Percentuali di apertura, percentuali di click-through e percentuali di risposta a ogni punto di contatto | Metriche di consegna e coinvolgimento per messaggio |
| Tasso di conversione criteri di uscita | Percentuale di profili che attivano l’evento di uscita (ad esempio, acquisto, iscrizione) prima del timeout del percorso | Conteggio hit criteri di uscita / Totale inserito |
| Tempo di conversione | Durata media dall’inserimento del percorso all’evento di criteri di uscita | Percorsi analytics: timestamp di ingresso per timestamp evento di conversione |
| Percentuale percorso di abbandono | Percentuale di profili che non coinvolgono più ogni passaggio (analisi di abbandono) | Visualizzazione dell’abbandono di CJA nei passaggi del percorso |
| Tasso di mantenimento/ricoinvolgimento | Percentuale di profili target che tornano allo stato attivo | Analisi comportamentale post-percorso in CJA |

## Schema del caso d’uso

**Percorso orchestrato con più passaggi**

Guida un profilo attraverso un percorso multi-touch diramato con attese, condizioni e azioni con più messaggi nel tempo.

**Catena di funzioni:** Valutazione del pubblico > Esecuzione del Percorso (più nodi) > Diramazione delle condizioni > Consegna dei messaggi (xN) > Criteri di uscita > Reporting

## Applicazioni

Per implementare questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Adobe Journey Optimizer] (AJO)**: motore di orchestrazione del Percorso, authoring dei messaggi, configurazione dei canali, sperimentazione dei contenuti, gestione dei conflitti e della frequenza e reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Valutazione e definizione del pubblico per tipi di pubblico di ingresso nel percorso, dati del profilo per la personalizzazione e diramazione delle condizioni
- **[!DNL Adobe Experience Platform] (AEP)** — Archivio profili, servizio Identity, acquisizione dati evento e infrastruttura dati di base

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve essere al suo posto | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Presunto sul posto | Sandbox AJO con autorizzazioni di creazione e pubblicazione del percorso. È necessario configurare le superfici di canale per tutti i canali utilizzati nel percorso. Gli utenti devono disporre dei ruoli appropriati (addetto marketing, responsabile Percorso) con autorizzazioni di percorso e campagna. | [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home), [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Obbligatorio | Schema di profilo XDM con attributi utilizzati per il diramazione delle condizioni e la personalizzazione tra più messaggi (ad esempio, livello di fedeltà, interesse del prodotto, punteggio di coinvolgimento). Schemi Experience Event per eventi di conversione che determinano i criteri di uscita e la valutazione delle condizioni (ad esempio, eventi di acquisto, invii di moduli). | [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Origini dati e raccolta | Presunto sul posto | Il flusso di eventi deve essere attivo se i criteri o le condizioni di uscita dipendono da eventi in tempo reale (ad esempio, un evento di acquisto per uscire dal percorso). Acquisizione in batch degli attributi del profilo utilizzati nelle diramazioni. Web SDK o API lato server per la raccolta di eventi comportamentali. | [Panoramica sull&#39;acquisizione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview), [Panoramica sulle origini](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Configurazione identità e profilo | Presunto sul posto | I profili devono essere risolvibili su tutti i canali utilizzati nel percorso (e-mail, SMS, push). L’identità tra dispositivi deve essere configurata se il percorso si estende su punti di contatto web e mobili. Il criterio di unione deve essere configurato per la sandbox. | [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Panoramica dei criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Definizione e segmentazione del pubblico | Obbligatorio | È necessario definire il pubblico di ingresso per i percorsi di lettura del pubblico. I segmenti possono essere utilizzati anche nei nodi condizione per la diramazione. Il metodo di valutazione (batch o streaming) deve corrispondere ai requisiti percorsi di immissione. | [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Guida dell&#39;interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Consigliato | Attributi calcolati come i punteggi di coinvolgimento, i giorni dall’ultima attività o il valore di acquisto del ciclo di vita migliorano la logica di ramificazione delle condizioni, consentendo decisioni più intelligenti sui percorsi di percorso. | [Panoramica attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Consigliato | La conservazione dei dati di eventi di percorso deve essere configurata con regole di scadenza dei set di dati per gestire lo storage e rispettare le normative sulla conservazione dei dati. L’applicazione del consenso assicura che solo i profili con consenso positivo ricevano messaggi a ogni punto di contatto del canale. | [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Scadenze set di dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| Etichettatura e applicazione dell’utilizzo dati | Consigliato | Le etichette di governance garantiscono una personalizzazione conforme in più punti di contatto dei messaggi, particolarmente importante quando i percorsi utilizzano dati PII o sensibili per la personalizzazione tra canali diversi. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview) |
| Monitoraggio e osservabilità | Incluso | Monitoraggio dell’esecuzione del percorso: avvisi su errori di elaborazione, colli di bottiglia nell’inserimento dei profili e problemi di consegna. Essenziale per i percorsi di produzione in cui ritardi o guasti influiscono sulla customer experience. | [Panoramica avvisi](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [Panoramica approfondimenti osservabilità](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting e analisi | Incluso | CJA funnel e l’analisi dell’abbandono nell’intero percorso forniscono dati più approfonditi su insight rispetto ai soli rapporti nativi di AJO. Abilita l&#39;analisi dettagliata delle conversioni, il confronto tra coorti e l&#39;ottimizzazione del percorso. | [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Journey Optimizer] (AJO)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Configurazione canali | Fase 1: configurazione del canale | Configurare le superfici di canale (e-mail, SMS, push) per ogni punto di contatto di messaggistica nel percorso |
| Authoring dei messaggi | Fase 2: Creazione di contenuti per i messaggi | Contenuto del messaggio dell’autore con personalizzazione, contenuto dinamico e modelli per ogni nodo di azione del percorso |
| Journey Orchestration | Fase 3: Progettazione e attivazione del Percorso | Progetta l’area di lavoro di percorso in più passaggi con nodi di entrata, azione, condizione, attesa ed uscita; testa e pubblica |
| Frequenza e regole business | Fase 4: Governance e ottimizzazione | Configura i limiti di frequenza per evitare messaggi eccessivi tra i punti di contatto del percorso e altre campagne simultanee |
| Gestione dei conflitti e delle priorità | Fase 4: Governance e ottimizzazione | Assegnare punteggi di priorità e configurare il rilevamento dei conflitti per i percorsi in concorrenza con altre comunicazioni attive |
| Sperimentazione sui contenuti | Fase 4: Governance e ottimizzazione | Eseguire test A/B sul contenuto dei messaggi all’interno dei nodi di azione del percorso per ottimizzare le prestazioni |
| Reporting e analisi delle prestazioni | Fase 5: Reporting e monitoraggio | Monitorare l’esecuzione del percorso, le metriche di consegna per passaggio e le prestazioni del coinvolgimento |

### [!DNL Real-Time CDP] (RT-CDP)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Valutazione del pubblico | Fase 1: configurazione del canale (prerequisito) | Definisci e valuta il pubblico di ingresso per i percorsi di lettura del pubblico; definisci i tipi di pubblico di condizione per la diramazione |
| Applicazione del consenso e della governance | Fase 4: Governance e ottimizzazione | Applicare le preferenze di consenso e i criteri di utilizzo dei dati nelle azioni dei messaggi del percorso |

## Prerequisiti

Completa i seguenti prerequisiti prima di iniziare l’implementazione.

- [ La sandbox di AJO ] dispone delle autorizzazioni di creazione e pubblicazione del percorso
- [ ] Almeno una superficie di canale (e-mail, SMS o push) è configurata e attiva
- [ Lo schema del profilo ] include gli attributi necessari per la diramazione delle condizioni e la personalizzazione
- [ Lo schema ] Experience Event è configurato per gli eventi di conversione utilizzati nei criteri di uscita
- [ ] Il flusso di eventi è attivo per gli eventi in tempo reale utilizzati nei criteri di uscita o nella voce attivata da eventi
- [ ] Gli spazi dei nomi delle identità e i criteri di unione sono configurati per la risoluzione dei profili cross-channel
- [ ] risorse di contenuto (immagini, copia, CTA) preparate per ogni punto di contatto del messaggio
- [ ] Il pubblico di ingresso è definito e valutato (per percorsi di lettura del pubblico)
- [ Lo schema dell&#39;evento di attivazione ] è configurato (per percorsi attivati da eventi)
- [ ] profili di test disponibili per la convalida della modalità di test percorso
- [ L&#39;elenco di soppressione di ] è rivisto e aggiornato per tutti i canali utilizzati

## Opzioni di implementazione

Rivedi le seguenti opzioni per determinare l’approccio migliore per il percorso orchestrato in più passaggi.

### Opzione A: percorso orchestrato per lettura di pubblico

**Ideale per:** sequenze di sviluppo basate sul tempo in cui un pubblico noto entra nel percorso e procede attraverso punti di contatto pianificati: serie di onboarding, sequenze di rinnovo, gocce di ricoinvolgimento, percorsi di milestone fedeltà.

**Funzionamento:**

Un pubblico viene letto all’ingresso del percorso, come lettura una tantum o secondo una pianificazione ricorrente. Tutti i profili idonei entrano nel percorso simultaneamente e quindi avanzano nell’area di lavoro al proprio ritmo, gestito da durate di attesa e valutazioni delle condizioni. Il percorso di ciascun profilo nel percorso è indipendente: alcuni possono seguire il ramo &quot;interessato&quot;, altri il ramo &quot;non coinvolto&quot; in base al loro comportamento o ai loro attributi.

Il pubblico viene valutato al momento dell’esecuzione dell’attività Read Audience. Per i percorsi ricorrenti, il pubblico viene rivalutato a ogni ricorrenza e i nuovi profili idonei entrano nel percorso mentre i profili già nel percorso continuano il loro percorso. Questo approccio fornisce tempi di ingresso prevedibili ed è adatto per i programmi di ciclo di vita pianificati.

**Considerazioni chiave:**

- Il pubblico deve essere definito e valutato prima dell&#39;attivazione del percorso
- Lettura ricorrente consente l&#39;immissione di nuovi qualificatori in ogni ciclo
- I profili nel percorso non vengono riletti; solo i nuovi qualificatori vengono immessi nelle letture successive
- I passaggi di attesa hanno una durata minima di 1 ora per i percorsi di lettura del pubblico

**Vantaggi:**

- Tempi di immissione prevedibili allineati ai programmi aziendali
- Supporta grandi volumi di pubblico (fino a 20.000 profili al secondo, velocità predefinita)
- Test e monitoraggio semplici con popolazioni di pubblico note
- Può essere programmato per l&#39;immissione ricorrente (giornaliera, settimanale, mensile)

**Limitazioni:**

- La voce è basata su batch, non su tempo reale: i profili vengono inseriti al momento della lettura programmata, non quando si qualificano
- Non adatto per sequenze iniziate da comportamenti che richiedono una risposta immediata
- Le modifiche del pubblico tra le letture non vengono applicate ai profili già presenti nel percorso

**Experience League:**

- [Attività Read audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Creazione di un percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)

### Opzione B: percorso orchestrato attivato da eventi

**Consigliato per:** sequenze avviate dal comportamento in cui un evento in tempo reale avvia il percorso: sequenze di attivazione di prova, percorso fedeltà attivato da milestone, escalation di abbandono del carrello, sviluppo post-acquisto.

**Funzionamento:**

Un evento unitario (ad esempio, un acquisto, l’abbandono del carrello, l’invio di moduli o l’installazione di un’app) attiva in tempo reale l’ingresso del percorso per i singoli profili. Quando l’evento viene ricevuto, il profilo entra nel percorso e procede attraverso la sequenza di punti di contatto con condizioni, attese e diramazioni. Questo approccio combina l’immediatezza dei messaggi attivati da eventi con l’orchestrazione in più passaggi di un percorso completo.

L’evento che scatena l’attivazione deve essere configurato come evento di percorso con il relativo schema e le relative condizioni definite. Il percorso ascolta l’evento in modo continuo e, all’arrivo degli eventi, immette i profili uno alla volta. I nodi di percorso successivi possono valutare la risposta del profilo per determinare quale ramo seguire.

**Considerazioni chiave:**

- Richiede che lo streaming degli eventi in tempo reale sia attivo
- Lo schema e le condizioni dell’evento devono essere configurati con precisione per evitare falsi attivatori
- Le regole di reinserimento sono fondamentali: determinare se un profilo può essere reinserito nel caso in cui l&#39;evento venga nuovamente attivato
- Supporta fino a 5.000 eventi al secondo per sandbox

**Vantaggi:**

- Ingresso in tempo reale basato sul comportamento del cliente, altamente contestuale
- Ogni profilo viene immesso in modo indipendente quando si verifica l’evento, non in una pianificazione
- Adattabilità naturale per le sequenze di risposta comportamentale (abbandono del carrello, post-acquisto)
- Può combinarsi con i dati del profilo per diramazioni personalizzate dopo l’immissione

**Limitazioni:**

- Richiede la presenza di un&#39;infrastruttura per eventi in streaming
- Maggiore complessità nella configurazione e nel test dello schema di eventi
- Ogni evento immette un profilo, non adatto per l’attivazione in blocco del pubblico
- Il debug richiede la traccia di singoli percorsi di profili

**Experience League:**

- [Eventi generali](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Eventi di qualificazione del pubblico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)

### Opzione C: percorso orchestrato multicanale

**Ideale per:** sequenze cross-channel che utilizzano canali diversi in ogni punto di contatto: e-mail, SMS e inoltro per livelli successivi di priorità, e-mail e messaggi complementari in-app. È possibile utilizzare una voce attivata da eventi o per la lettura del pubblico.

**Funzionamento:**

Questa opzione estende l&#39;opzione A o l&#39;opzione B incorporando più canali di messaggistica all&#39;interno dello stesso percorso. Ogni nodo di azione nel percorso può eseguire il targeting di un canale diverso (e-mail, SMS, push, in-app o web), che richiede una superficie di canale separata per ciascuno di essi. Il progettista del percorso seleziona il canale appropriato in ogni fase, abilitando i pattern di escalation (ad esempio, e-mail prima, SMS se non vi è coinvolgimento) o i pattern complementari (ad esempio, e-mail con rafforzamento in-app).

I percorsi cross-channel richiedono superfici di canale per ciascun canale utilizzato e devono tenere conto dei requisiti di personalizzazione specifici del canale, dei limiti dei caratteri e del consenso. I nodi delle condizioni possono verificare il coinvolgimento con i messaggi precedenti (ad esempio, &quot;e-mail aperta?&quot; come condizione di diramazione) per determinare il canale successivo.

**Considerazioni chiave:**

- Richiede superfici di canale attive per ogni canale utilizzato nel percorso
- Ogni canale ha diverse funzionalità di personalizzazione e diversi vincoli per i contenuti
- Il consenso deve essere verificato per canale: un profilo può essere prestato per e-mail ma non per SMS
- I limiti di frequenza specifici per canale devono essere configurati per evitare messaggi eccessivi tra canali diversi

**Vantaggi:**

- Massimizza la portata coinvolgendo i profili nei loro canali preferiti
- Abilita le strategie di escalation per i profili non reattivi
- Supporta messaggi complementari tra canali per il rafforzamento
- Esperienza cliente più sofisticata possibile

**Limitazioni:**

- Massima complessità di implementazione: richiede la configurazione per ogni canale
- Il contenuto deve essere creato per ogni canale in ogni punto di contatto
- La gestione del consenso e della frequenza diventa più complessa tra i canali
- Il test richiede la convalida su tutte le superfici di canale

**Experience League:**

- [Configurare il canale SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Confronto delle opzioni

La tabella seguente confronta le tre opzioni di implementazione tra i diversi criteri chiave.

| Criteri | Opzione A: lettura da parte del pubblico | Opzione B: attivazione di un evento | Opzione C: multicanale |
| --- | --- | --- | --- |
| Ideale per | Programmi di ciclo di vita programmati, serie di crescita | Sequenze di risposta comportamentale, abbandono del carrello | Escalation cross-channel, messaggistica complementare |
| Tempistica di ingresso | Pianificato (batch) | In tempo reale (basato su eventi) | Pianificato o in tempo reale |
| Complessi | Medio | Medium - Alta | Alta |
| Volume di ingresso | Fino a 20.000 profili al secondo | Fino a 5.000 eventi/sec | Uguale al metodo di immissione sottostante |
| Ambito canale | Uno o più canali | Uno o più canali | Sono necessari più canali |
| Richiede | Pubblico definito, pianificazione della valutazione | Infrastruttura di eventi in streaming | Superfici di canale per ciascun canale |
| Risposta in tempo reale | No - Inserimento batch | Sì - subito dopo l&#39;evento | Dipende dal metodo di immissione |

### Scegli l’opzione giusta

Utilizza il seguente flusso di decisione per selezionare l’approccio di implementazione corretto:

1. **Il percorso è avviato da un comportamento o un evento del cliente?** In caso affermativo, scegliere **Opzione B** (Attivata da evento). Se il percorso è avviato da una lettura pianificata del pubblico, scegli **Opzione A** (Lettura del pubblico).

2. **Il percorso utilizza più canali di messaggistica (ad esempio, e-mail E SMS)?** In caso affermativo, applicare **l&#39;opzione C** (multicanale) alla scelta del metodo di immissione (A o B). Se il percorso utilizza un singolo canale in tutto, è sufficiente l’opzione A o B da sola.

3. **Devi passare a un canale diverso in base al coinvolgimento?** In caso affermativo, scegliere **Opzione C** con nodi di condizione che controllano l&#39;interazione con i messaggi precedenti e si diramano su canali alternativi.

4. **Il pubblico è noto in anticipo ed elaborato in base a una pianificazione?** In caso affermativo, scegliere **Opzione A**. Se i profili devono entrare nel percorso nel momento in cui eseguono un&#39;azione, scegliere **Opzione B**.

## Fasi di implementazione

Le seguenti fasi descrivono l’implementazione end-to-end di un percorso orchestrato in più passaggi.

### Fase 1: Impostare i canali e preparare il pubblico

**Funzioni dell&#39;applicazione:** AJO: Configurazione canale, RT-CDP: Valutazione pubblico

Prima di progettare il percorso, tutte le superfici di canale devono essere attive e il pubblico di ingresso (per l&#39;opzione A) deve essere definito e valutato. Questa fase assicura che l’infrastruttura sia pronta per la consegna dei messaggi.

#### Decidi il tipo di canale per ogni punto di contatto

Quali canali di messaggistica utilizzerà il percorso in ogni punto di contatto?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo e-mail | Il percorso comunica esclusivamente via e-mail (onboarding, cultura) | Configurazione più semplice; richiede sottodominio e-mail e pool IP; soggetto al posizionamento della casella in entrata |
| Solo SMS | Avvisi sensibili al tempo, promemoria di appuntamenti | Richiede le credenziali del provider SMS (Sinch, Twilio, Infobip); costo più elevato per messaggio; regole di rinuncia più severe |
| Solo push | Sequenze di coinvolgimento in-app per gli utenti di dispositivi mobili | Richiede credenziali APN/FCM; gli utenti devono avere l’app installata |
| Multicanale | Escalation o messaggistica complementare su tutti i canali | Richiede una superficie di canale per canale; portata più complessa ma più alta |

#### Decidere il metodo di valutazione del pubblico (opzione A)

Con quale rapidità i profili devono qualificarsi per il pubblico di ingresso?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Valutazione in batch | Il pubblico viene letto secondo una pianificazione (giornaliera, settimanale); non è necessario inserire dati in tempo reale | Configurazione semplice; pubblico valutato prima della lettura del percorso; supporta regole di segmento complesse |
| Valutazione in streaming | I profili devono qualificarsi quasi in tempo reale man mano che gli attributi cambiano | L’espressione della regola del segmento deve essere idonea allo streaming; qualificazione quasi in tempo reale |

#### Decidere il metodo di delega del sottodominio (canale e-mail)

Come deve essere delegato il sottodominio di invio dell’e-mail ad Adobe?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Delega completa | Adobe gestisce i record DNS; configurazione più semplice | Configurazione più rapida; Adobe gestisce SPF, DKIM, DMARC |
| Delega CNAME | L&#39;organizzazione mantiene il controllo DNS | Richiede il coinvolgimento dell&#39;amministratore DNS; è necessario configurare i record CNAME |

#### Navigazione interfaccia utente

- Superfici di canale: Amministrazione > Canali > Superfici di canale > Crea superficie
- Sottodomini: Amministrazione > Canali > Sottodomini
- Configurazione SMS: Amministrazione > Canali > Configurazione SMS
- Configurazione push: Amministrazione > Canali > Impostazioni notifica push
- Tipi di pubblico: Cliente > Tipi di pubblico > Crea pubblico > Genera regola

#### Dettagli chiave della configurazione

- Verifica dello stato di riscaldamento del pool IP per le e-mail: i nuovi pool IP richiedono un piano di riscaldamento graduale in 2-4 settimane
- Per gli SMS, configura le credenziali del provider e verifica la registrazione del numero del mittente
- Per il push, carica certificati APN e chiavi del server FCM
- Definisci il pubblico di ingresso utilizzando Segment Builder (Generatore di segmenti) con regole di segmento che coprono la popolazione target
- Includi regole di soppressione nella definizione del pubblico (escludi quelli convertiti di recente, quelli non sottoscritti a livello globale)

#### Dove le opzioni divergono

**Per L&#39;Opzione A (Lettura Del Pubblico):**
Definisci e valuta il pubblico di ingresso. Conferma che il pubblico abbia una popolazione diversa da zero. Determina se il percorso utilizzerà una pianificazione delle letture una tantum o ricorrente.

**Per L&#39;Opzione B (Attivata Da Evento):**
Verifica che lo schema dell’evento che attiva sia configurato e che gli eventi siano in streaming nella piattaforma. Non è richiesto alcun pubblico predefinito: i profili vengono inseriti singolarmente alla ricezione dell’evento.

**Per L&#39;Opzione C (Multicanale):**
Configura le superfici di canale per OGNI canale utilizzato nel percorso (e-mail, SMS, push, in-app). Verifica lo stato del consenso per canale per la popolazione target.

#### Documentazione di Experience League

- [Impostare le superfici di canale](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configurare il canale SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Piani di riscaldamento IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)


### Fase 2: creare il contenuto del messaggio

**Funzione dell&#39;applicazione:** AJO: authoring dei messaggi

Crea il contenuto del messaggio per ogni punto di contatto nel percorso. Ogni messaggio può avere contenuti, profondità di personalizzazione e canale diversi. Questa fase crea tutti i contenuti consegnabili a cui faranno riferimento i nodi di azione del percorso.

#### Decidere l’approccio ai contenuti

Ogni messaggio deve iniziare da un modello, essere progettato da zero o importare HTML?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Modello di contenuto esistente | Messaggi coerenti con il marchio con layout consolidati | Più veloce; garantisce la conformità del brand; il modello deve esistere e corrispondere al tipo di canale |
| Progettare da zero | Layout univoci e personalizzati per ogni punto di contatto | Più flessibile; più tempo di creazione; utilizza il trascinamento della selezione di E-mail Designer |
| Importa HTML | HTML precompilato da strumenti di progettazione esterni | Richiede un HTML pulito; potrebbe essere necessario regolare la velocità di risposta |

#### Decidere il livello di personalizzazione

Quanta personalizzazione deve includere ogni messaggio?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Inserimento token di base | Nome, città, attributi di profilo semplici | Bassa complessità; utilizza la sintassi Handlebars con percorsi XDM |
| Blocchi di contenuto condizionali | Contenuto diverso mostrato in base a segmento o attributo | complessità di Medium; richiede regole di contenuto dinamico |
| Personalizzazione percorso-contestuale | Il contenuto varia in base al percorso del percorso e alle interazioni precedenti | Maggiore complessità; sfrutta le variabili di contesto del percorso e i dati evento |

#### Decidere la strategia per i frammenti

Creare blocchi di contenuto condivisi (intestazioni, piè di pagina, testo legale) come frammenti riutilizzabili?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Frammenti riutilizzabili | Messaggi multipli condividono gli elementi comuni; è necessaria la coerenza del brand | Le modifiche si propagano a tutti i messaggi che utilizzano il frammento; massimo 30 frammenti per messaggio |
| Contenuto in linea | Messaggi unici con layout univoci | Più veloce per contenuti monouso; nessun vantaggio di coerenza tra i messaggi |

#### Navigazione interfaccia utente

- Gestione contenuti > Modelli di contenuto > Sfoglia
- E-mail Designer (nell’azione della campagna o del percorso)
- Gestione contenuto > Frammenti > Crea frammento

#### Dettagli chiave della configurazione

- Contenuto dell&#39;autore per OGNI azione messaggio nel percorso: un percorso in 4 fasi può richiedere 4 progettazioni di messaggi separate
- Utilizza espressioni di personalizzazione che fanno riferimento a percorsi di profilo XDM (ad esempio, `{{profile.person.name.firstName}}`)
- Configurare blocchi di contenuto dinamici per varianti specifiche del segmento
- Anteprima di ogni messaggio con profili di test per verificare il rendering della personalizzazione
- Inviare bozze alle parti interessate interne per la revisione del contenuto
- Per gli SMS, rispetta i limiti di caratteri (160 caratteri per la codifica GSM standard)
- Per inviare un messaggio push, configura il titolo, il corpo, l’immagine e l’azione URL/collegamento profondo

#### Documentazione di Experience League

- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Creare un messaggio e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilizzare i frammenti di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Creare un messaggio SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Progettare una notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)
- [Anteprima e test del contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)


### Fase 3: Progettazione e attivazione del percorso

**Funzione applicazione:** AJO: Journey Orchestration

Progetta l’area di lavoro del percorso in più passaggi, inclusi il nodo di ingresso, i nodi di azione (messaggi), i nodi di condizione (diramazione), i nodi di attesa (ritardi) e i criteri di uscita. Quindi esegui il test con i profili di test e pubblica.

#### Decidi il tipo di voce

Come devono entrare nel percorso i profili?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Read Audience | Sequenze di sviluppo pianificate; pubblico noto elaborato in batch | Pubblico valutato in fase di lettura; supporta letture una tantum o ricorrenti; fino a 20.000 profili/sec |
| Evento unitario | Trigger comportamentali in tempo reale (acquisto, abbandono del carrello) | Immissione in tempo reale; richiede streaming di eventi; fino a 5.000 eventi/sec |
| Qualificazione del pubblico | Ingresso quando un profilo entra o esce da un pubblico in tempo quasi reale | Valutazione in streaming; attivata dalla modifica dell’iscrizione al segmento |
| Evento di business | Un evento a livello di organizzazione attiva il percorso per un pubblico | Utile per il lancio di prodotti, eventi meteo e avvisi di sistema |

#### Decidi la politica di rientro

Un profilo può rientrare nel percorso dopo aver completato o chiuso?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Consenti rientro (con raffreddamento) | I profili possono dover ripetere il percorso (acquisti ricorrenti, ricoinvolgimento stagionale) | Tempo minimo di raffreddamento di 5 minuti; impedisce la presenza di voci duplicate all&#39;interno della finestra di raffreddamento |
| Nessun rientro | Percorsi una tantum (onboarding, evento ciclo di vita singolo) | Il profilo completa o esce dal percorso e non può entrare di nuovo |

#### Decidere le durate di attesa tra i punti di contatto

Quanto tempo deve trascorrere il percorso tra un messaggio e l’altro?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Durata fissa (ad esempio 3 giorni) | Ritmo coerente indipendentemente dal comportamento del profilo | Semplice; tempistica prevedibile; minimo 1 ora per percorsi di lettura del pubblico |
| Data/ora specifica | Il messaggio deve pervenire in un momento preciso (ad esempio, data di rinnovo) | Utilizza l’attributo o l’espressione di profilo per determinare la data/ora esatta |
| Espressione personalizzata | Attesa dinamica basata su dati di profilo o contesto di percorso | Più flessibile; richiede l’authoring delle espressioni |

#### Decidere le condizioni di diramazione

Quali condizioni determinano il percorso seguito da un profilo?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Controllo degli attributi del profilo | Ramo basato su livello di fedeltà, interesse prodotto, area geografica | Utilizza i dati profilo disponibili al momento della valutazione |
| Verifica dell’iscrizione al segmento | Ramo in base al fatto che il profilo appartenga a un pubblico specifico | Richiede che il pubblico sia definito e valutato |
| Verifica dati evento | Ramo in base al fatto che il profilo abbia eseguito un’azione (e-mail aperta, collegamento su cui è stato fatto clic) | Valuta i dati dell’evento con ambito di percorso; utile per ramificazioni basate sul coinvolgimento |
| Suddivisione percentuale | Distribuisci in modo casuale i profili tra percorsi diversi (per test A/B o rollout controllati) | Non utilizza i dati del profilo; allocazione puramente casuale |

#### Decidi i criteri di uscita

Quale evento o condizione causa l’uscita anticipata di un profilo dal percorso?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Evento di conversione | Il profilo completa l’azione desiderata (acquisto, iscrizione, invio modulo) | Richiede streaming degli eventi; i criteri di uscita più comuni |
| Uscita dall’iscrizione al pubblico | Il profilo lascia il pubblico di ingresso o si unisce a un pubblico di esclusione | Valuta in tempo quasi reale per il pubblico in streaming |
| Timeout | Durata massima del percorso raggiunta (fino a 91 giorni) | Rete di sicurezza predefinita; configurabile nelle proprietà del percorso |
| Nessun criterio di uscita | Il profilo completa l&#39;intero percorso di percorso in modo naturale | Più semplice: tutti i profili attraversano l’intero percorso a meno che non vengano rimossi manualmente |

#### Decidi in caso di timeout del percorso

Qual è la durata massima che un profilo può rimanere nel percorso?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| 91 giorni (massimo) | Percorsi di lunga durata (rinnovo trimestrale, onboarding esteso) | Massimo consentito; i profili ancora presenti nel percorso al timeout vengono chiusi automaticamente |
| Durata più breve personalizzata | Il percorso deve essere completato entro un intervallo definito (7 giorni, 14 giorni, 30 giorni) | Impostato in base al ciclo di vita naturale del caso d’uso |

#### Navigazione interfaccia utente

- Crea percorso: Percorsi > Crea Percorso
- Proprietà percorso: area di lavoro Percorso > pannello Proprietà
- Nodo di ingresso: area di lavoro Percorso > Trascina &quot;Read Audience&quot; (Leggi pubblico) o attività evento
- Nodi azione: area di lavoro del Percorso > Trascina azione canale (e-mail, SMS, push)
- Nodi condizione: Area di lavoro Percorso > Trascina attività &quot;Condizione&quot;
- Nodi di attesa: area di lavoro Percorso > Attività Trascina attesa
- Criteri di uscita: proprietà Percorso > Criteri di uscita > Configura
- Modalità di test: Area di lavoro del Percorso > Attiva/Disattiva modalità di test
- Pubblica: area di lavoro Percorso > Pubblica

#### Dettagli chiave della configurazione

- Assegna al percorso un nome con una convenzione chiara e descrittiva (ad esempio, &quot;Onboarding_Series_Email_v1&quot;)
- Imposta il fuso orario del percorso per un&#39;elaborazione coerente dei passaggi di attesa
- Configura ogni nodo di azione con la superficie di canale appropriata e collega al contenuto del messaggio creato
- Ogni ramo deve terminare con un’attività Fine
- Configurare le regole di reinserimento appropriate per il caso d’uso
- Utilizza la modalità di test con i profili di test per simulare il percorso completo del percorso prima della pubblicazione
- Verifica che i profili di test attraversino i percorsi previsti e ricevano i messaggi corretti

#### Dove le opzioni divergono

**Per L&#39;Opzione A (Lettura Del Pubblico):**

- Trascina l’attività &quot;Read Audience&quot; come nodo di ingresso
- Selezionare il pubblico di destinazione definito nella fase 1
- Facoltativamente, configura una pianificazione di lettura ricorrente (giornaliera, settimanale)
- Configurare la velocità di lettura se il caricamento del sistema a valle rappresenta un problema

**Per L&#39;Opzione B (Attivata Da Evento):**

- Trascina l’evento che attiva come nodo di ingresso
- Configurare lo schema dell’evento e le condizioni di ingresso
- Imposta le regole di reinserimento con attenzione per evitare voci duplicate da eventi ripetuti

**Per L&#39;Opzione C (Multicanale):**

- Utilizzare il metodo di immissione dell&#39;opzione A o B
- In ciascun nodo di azione, seleziona la superficie di canale appropriata per quel punto di contatto
- Aggiungi nodi di condizione tra i canali per verificare il coinvolgimento (ad esempio, &quot;Il profilo ha aperto l’e-mail?&quot;) e indirizzare a canali alternativi

#### Documentazione di Experience League

- [Creazione di un percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Proprietà del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Attività Read audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Eventi generali](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Eventi di qualificazione del pubblico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Aggiungere un messaggio in un percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Attività Condizione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Attività Attendi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Criteri di uscita](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Attività Fine](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [Gestione voci percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Test del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Pubblicare il percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)


### Fase 4: configurare governance e ottimizzazione

**Funzioni dell&#39;applicazione:** AJO: Frequency &amp; Business Rules, AJO: Conflict &amp; Priority Management, AJO: Content Experimentation, RT-CDP: Applicazione del consenso e della governance

Applica i limiti di frequenza per evitare messaggi eccessivi, assegna punteggi di priorità per la risoluzione dei conflitti con altre comunicazioni attive, configura facoltativamente test A/B all’interno dei messaggi di percorso e verifica l’applicazione del consenso.

#### Decidere la configurazione del limite di frequenza

I messaggi di percorso devono rispettare i limiti di frequenza globali?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Applicare le regole di frequenza | Il percorso funziona insieme ad altre campagne e percorsi; i profili non devono essere sovrascritti | I messaggi possono essere eliminati se il profilo ha già raggiunto il limite da altre comunicazioni |
| Esenzione dai limiti | I messaggi di percorso sono fondamentali e devono sempre essere consegnati (transazionali, normativi) | Usare con moderazione; può contribuire all’affaticamento del messaggio se utilizzato in modo eccessivo |

#### Decidere l’assegnazione del punteggio di priorità

In che modo questo percorso deve essere classificato rispetto ad altre campagne e percorsi attivi?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Priorità alta (70-100) | I messaggi di percorso sono comunicazioni critiche del ciclo di vita (onboarding, rinnovo) | La priorità più alta si ottiene in caso di conflitti con altre comunicazioni |
| Priorità Medium (30-69) | I messaggi di percorso sono importanti ma non urgenti (educazione, educazione) | Può essere soppresso da comunicazioni con priorità più elevata |
| Priorità bassa (0-29) | I messaggi di percorso sono supplementari o promozionali | Verrà eliminato quando si è in concorrenza con messaggi di priorità superiore |

#### Decidere sulla sperimentazione dei contenuti

Un messaggio di percorso deve includere un test A/B o multivariato?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Sì — test A/B | Ottimizzare le linee dell’oggetto, i CTA o i layout di contenuto in un punto di contatto specifico | Richiede un volume sufficiente per variante per la significatività statistica; 2-10 trattamenti supportati |
| Nessuna sperimentazione | Il contenuto è finalizzato o il volume è troppo basso per test significativi | Configurazione più semplice; non è necessario alcun tracciamento delle varianti |

#### Navigazione interfaccia utente

- Regole di frequenza: Amministrazione > Regole aziendali > Crea regola
- Punteggi di priorità: proprietà Percorso > Punteggio priorità
- Rilevamento conflitti: Amministrazione > Regole business > Conflitti e priorità
- Esperimento sui contenuti: Area di lavoro del Percorso > Seleziona azione messaggio > Attiva/disattiva esperimento sui contenuti
- Criteri di consenso: Privacy > Criteri > Criteri di consenso

#### Dettagli chiave della configurazione

- Imposta i limiti di frequenza specifici per il canale (ad esempio, max 3 e-mail/settimana, max 1 SMS/giorno, max 2 push/giorno)
- Assegna al percorso un punteggio di priorità (0-100) che ne rifletta l’importanza commerciale rispetto ad altre comunicazioni attive
- Rivedi il pannello di rilevamento dei conflitti per identificare eventuali campagne o percorsi sovrapposti
- Se esegui un esperimento sui contenuti, definisci le varianti di trattamento, imposta l’allocazione del traffico, scegli la metrica di successo (aperture, clic o conversioni) e imposta la soglia di affidabilità (in genere il 95%)
- Verifica che l’applicazione del consenso sia attiva per ogni canale utilizzato nel percorso

#### Documentazione di Experience League

- [Regole di frequenza](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Panoramica sulle regole business](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Punteggi di priorità](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identificare potenziali conflitti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Limitazione di percorso e arbitrato](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Introduzione all’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Creare un esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)


### Fase 5: configurare reporting e monitoraggio

**Funzioni dell&#39;applicazione:** AJO: Reporting &amp; Performance Analysis, Monitoring &amp; Observability, Reporting &amp; Analysis

Monitora l’esecuzione del percorso durante e dopo l’attivazione, rivedi le metriche di coinvolgimento e consegna per passaggio, configura gli avvisi per gli errori di elaborazione del percorso e, facoltativamente, crea un’analisi dell’area di lavoro CJA per una visualizzazione approfondita di funnel e abbandono.

#### Decidere il metodo di reporting

Quali strumenti di reporting sono necessari per questo percorso?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo rapporti nativi di AJO | È sufficiente il monitoraggio di base della consegna e del coinvolgimento | Report live (durante l’esecuzione) e Report all time (post-esecuzione); aggiorna ogni 60 secondi per il report live |
| Analisi AJO + CJA | Sono necessarie un’analisi approfondita del funnel, tassi di conversione dei passaggi, visualizzazione dell’abbandono o confronto tra percorsi | Richiede connessione CJA e visualizzazione dati collegata ai set di dati di AJO; più completo |
| Solo CJA | L’organizzazione utilizza CJA come piattaforma di analisi principale | Richiede la configurazione di CJA; i rapporti nativi di AJO sono ancora disponibili come backup |

#### Decidi la configurazione dell’avviso

Quali errori di percorso devono attivare gli avvisi?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Avvisi elaborazione percorso | Sempre consigliato per percorsi di produzione | Avvisi su errori di immissione profilo, errori del nodo di azione e blocchi del percorso |
| Avvisi di errore di consegna | Critico per percorsi con comunicazioni di alto valore | Avvisi su tassi di mancato recapito superiori alle soglie, errori di consegna |

#### Navigazione interfaccia utente

- Rapporto live percorso: Percorsi > Seleziona percorso > Rapporto live
- Rapporto tempo totale percorso: Percorsi > Seleziona percorso > Rapporto tempo totale
- Avvisi: Avvisi > Regole di avviso > Abbonati
- Area di lavoro CJA: Progetti > Crea nuovo progetto

#### Dettagli chiave della configurazione

- Accedi al rapporto live durante l’esecuzione del percorso per monitorare in tempo reale le voci di profilo, le uscite e le metriche di consegna per passaggio
- Dopo il completamento del percorso (o dopo l&#39;accumulo di dati sufficienti), esaminare il rapporto Tutti i tempi per un&#39;analisi completa
- Configurazione degli avvisi della piattaforma per errori di elaborazione del percorso e problemi di consegna
- Per l’analisi CJA, assicurati che la connessione CJA includa i set di dati dell’evento esperienza AJO (feedback messaggi, tracciamento e-mail, eventi dei passaggi del Percorso)
- Crea un Workspace CJA con:
   - Visualizzazione funnel che mostra i conteggi dei profili in ogni passaggio del percorso
   - Visualizzazione Abbandono per identificare i punti di abbandono
   - Calcoli del tasso di conversione per fase
   - Analisi del tempo di conversione
   - Intervento a livello di canale (per percorsi multicanale)

#### Documentazione di Experience League

- [Rapporto live del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Panoramica degli avvisi](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Considerazioni sull’implementazione

Rivedi i seguenti guardrail, insidie, best practice e compromessi prima e durante l’implementazione.

### Guardrail e limiti

- Massimo di **500 percorsi live** per sandbox: [guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- La durata massima di **percorsi è di 91 giorni** (timeout globale). I profili ancora presenti nel percorso al momento del timeout vengono automaticamente chiusi
- Massimo di **50 attività** per area di lavoro percorso
- Leggi percorsi di pubblico elabora fino a **20.000 profili al secondo** (limitazione predefinita)
- I percorsi di eventi unitari supportano fino a **5.000 eventi al secondo** per sandbox
- I passaggi di attesa hanno una durata minima di **di 1 ora** per i percorsi di lettura del pubblico
- Il percorso **minimo di raffreddamento per rientro è di 5 minuti**
- Massimo di **10 superfici di canale per tipo di canale** per sandbox
- Dimensione massima dell&#39;e-mail di **100 KB** consigliata per una consegna dei messaggi ottimale
- Massimo **30 frammenti di contenuto** per messaggio
- Massimo di **10 trattamenti per esperimento sui contenuti** (varianti) per esperimento
- Massimo **10 configurazioni limite** per sandbox
- Massimo **4.000 definizioni di segmenti** per sandbox

### Insidie comuni

- **Pubblicazione senza test:** Prima di pubblicare, utilizza sempre la modalità di test con i profili di test per convalidare il percorso di percorso completo. Verifica che i profili attraversino i rami previsti, che i passaggi di attesa avanzino correttamente e che i messaggi vengano visualizzati correttamente.
- **Attività finali mancanti nei rami:** Ogni ramo del percorso deve terminare con un&#39;attività Fine. Se un ramo viene lasciato senza un nodo di terminazione, il percorso non verrà pubblicato.
- **Condizioni di ingresso eccessivamente ampie:** Un pubblico di ingresso o una condizione di evento liberamente definiti possono inondare il percorso con profili non desiderati. Affina i criteri di immissione con controlli di attributi e regole di soppressione specifici.
- **Le regole di reinserimento verranno ignorate:** Per i percorsi attivati da eventi, i profili potrebbero attivare più volte l&#39;evento di attivazione. Se non si esegue la configurazione di rientro corretta (nega il rientro o il periodo di arresto), i profili possono accumularsi nel percorso, generando messaggi duplicati.
- **Confusione del fuso orario del passaggio di attesa:** Le durate di attesa vengono elaborate in UTC. Impostare esplicitamente il fuso orario del percorso nelle proprietà del percorso per garantire che i passaggi di attesa avanzino all&#39;ora locale prevista.
- **Modifica di un percorso live:** Non è possibile modificare direttamente i percorsi live. Per apportare modifiche, duplicare il percorso, modificare la copia, interrompere l&#39;originale e pubblicare la nuova versione. Pianifica il controllo delle versioni di percorso prima della pubblicazione.
- **Nessun criterio di uscita definito:** Senza criteri di uscita, i profili che convertono il percorso intermedio continueranno a ricevere messaggi successivi, potenzialmente irrilevanti o contraddittori. Configura sempre i criteri di uscita per gli eventi di conversione.
- **Mancato allineamento del consenso del canale:** Un profilo può essere prestato per e-mail ma non per SMS. I percorsi multicanale devono rispettare il consenso per canale. Verifica che i campi di consenso siano compilati e applicati su ogni superficie di canale.

### Best practice

- **Inizia semplice, ripeti:** Inizia con un percorso lineare di 2-3 passaggi prima di aggiungere ramificazioni complesse. Convalidare il funzionamento del flusso principale prima di creare livelli in condizioni e canali.
- **Utilizza le convenzioni di denominazione descrittive:** I nodi, le condizioni e i passaggi di attesa del percorso dei nomi sono chiari (ad esempio, &quot;Wait_3_Days_After_Welcome&quot; anziché &quot;Wait 1&quot;). Questo semplifica notevolmente il debug in modalità di test e l’interpretazione dei rapporti.
- **Configurare anticipatamente i criteri di uscita:** Definire l&#39;evento di conversione come criterio di uscita prima di progettare i percorsi di percorso. In questo modo i profili che eseguono la conversione vengono rimossi dal percorso, indipendentemente dal passaggio in cui si trovano.
- **Imposta durate di attesa significative:** Basa le durate di attesa sui dati del comportamento del cliente: tempo tra le interazioni tipiche, intervalli di risposta previsti e cadenza appropriata per il canale (ad esempio, 2-3 giorni tra le e-mail, 1 settimana tra gli SMS).
- **Utilizzare i nodi delle condizioni per controllare il coinvolgimento:** Dopo un&#39;azione del messaggio, aggiungere una condizione per verificare se il profilo è attivato (aperto, su cui è stato fatto clic). Instradare i profili coinvolti a un percorso e i profili non coinvolti a un percorso di escalation o a un percorso di canale alternativo.
- **Sfruttare gli attributi calcolati per la diramazione:** Utilizzare attributi calcolati come i punteggi di coinvolgimento, la frequenza di acquisto o i giorni trascorsi dall&#39;ultima attività per prendere decisioni sulla diramazione basate sui dati anziché su dati arbitrari.
- **Monitorare e ottimizzare in modo iterativo:** Esaminare settimanalmente i report del percorso durante l&#39;esecuzione iniziale. Identifica i punti di riconsegna, regola la durata dell’attesa, perfeziona le condizioni e ottimizza il contenuto dei messaggi in base ai dati sulle prestazioni per passaggio.
- **Versione dei percorsi:** Quando si apportano modifiche, duplicare il percorso per creare una nuova versione. Gestisci un registro delle modifiche alla versione per il controllo e il tracciamento dell’ottimizzazione.

### Decisioni di compromesso

I seguenti compromessi devono essere valutati nel contesto dei requisiti aziendali specifici.

#### Voce di lettura del pubblico rispetto alla voce attivata da eventi

L’immissione in lettura da parte del pubblico fornisce un’elaborazione prevedibile basata su batch più semplice da gestire e testare. L&#39;ingresso attivato da eventi offre tempi di risposta in tempo reale più pertinenti dal punto di vista contestuale, ma richiede un&#39;infrastruttura di streaming e una gestione più attenta del rientro.

- **Preferenze di lettura del pubblico:** Predittività, elaborazione di grandi volumi, programmi di ciclo di vita pianificati, test più semplici
- **Preferenze attivate da eventi:** Rilevanza in tempo reale, contesto comportamentale, andamento dei singoli profili, risposta immediata alle azioni dei clienti
- **Consiglio:** utilizza audience-read per i programmi del ciclo di vita pianificati (onboarding, rinnovo) in cui la tempistica è orientata al business. Utilizza evento attivato per le sequenze di risposta comportamentale (abbandono del carrello, post-acquisto) in cui la tempistica è guidata dal cliente.

#### Percorso a canale singolo e multicanale

I percorsi a canale singolo sono più semplici da implementare, testare e gestire. I percorsi multicanale offrono una portata più ampia e funzionalità di escalation, ma aumentano la complessità nella creazione di contenuti, nella gestione del consenso e nella governance delle frequenze.

- **Un singolo canale favorisce:** implementazione più rapida, gestione del consenso più semplice, minore impegno nella produzione dei contenuti, debug più semplice
- **Preferenze multicanale:** maggiore potenziale di coinvolgimento, escalation del canale per profili non reattivi, esperienza del cliente più completa
- **Consiglio:** inizia con un percorso a canale singolo e convalida il flusso e l&#39;impatto aziendale prima di espanderlo a multicanale. Aggiungi i canali in modo incrementale dove i dati di coinvolgimento mostrano che il canale principale non raggiunge il pubblico in modo efficace.

#### Complessità del percorso e gestibilità

Un percorso altamente ramificato con molte condizioni e percorsi può affrontare più scenari, ma diventa più difficile da testare, eseguire il debug e ottimizzare. Un percorso più semplice con meno rami è più facile da gestire, ma può offrire un’esperienza meno personalizzata.

- **percorsi complessi favoriscono:** personalizzazione granulare, percorsi specifici del segmento, copertura completa dello scenario
- **percorsi più semplici favoriscono:** distribuzione più rapida, test più semplici, creazione di report più chiara, riduzione degli oneri di manutenzione
- **Consiglio:** Limita i percorsi a 3-5 rami principali e 15-25 attività. Se la logica richiede una maggiore complessità, è consigliabile suddividerla in più percorsi con coordinamento tra percorsi diversi anziché in un unico percorso monolitico.

#### Restringimento del limite di frequenza rispetto al completamento del percorso

Limiti di frequenza rigidi proteggono dai messaggi eccessivi, ma possono eliminare i messaggi di percorso, causando il salto dei passaggi da parte dei profili e riducendo la frequenza di completamento del percorso. I tappi indulgenti garantiscono la distribuzione dei messaggi di percorso, ma rischiano di causare affaticamento del canale.

- **Limiti rigorosi favore:** Protezione dell&#39;esperienza del cliente, riduzione delle percentuali di annullamento dell&#39;iscrizione, brand trust
- **Favore per limiti indulgenti:** tassi di completamento Percorsi, consegna sequenza messaggi completa, efficacia del programma di marketing
- **Consiglio:** assegna punteggi di priorità più elevati ai messaggi critici di percorso (onboarding, rinnovo) in modo che abbiano la precedenza sulle campagne promozionali quando vengono raggiunti i limiti. Riserva &quot;esente da limiti&quot; solo per le comunicazioni veramente essenziali.

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sulle funzionalità utilizzate in questa implementazione.

### Percorsi

- [Introduzione ai percorsi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Creazione di un percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Proprietà del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Pubblicare il percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [Test del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)

### Attività percorso

- [Attività Read audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Eventi generali](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Eventi di qualificazione del pubblico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Attività Condizione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Attività Attendi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Aggiungere un messaggio in un percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Attività Fine](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [Configurare un’azione personalizzata](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions)

### Gestione delle entrate e delle uscite

- [Gestione voci percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Criteri di uscita](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### Configurazione dei canali

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Impostare le superfici di canale](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delega sottodomini](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Creare pool IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Piani di riscaldamento IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Configurare il canale SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Authoring e personalizzazione dei messaggi

- [Creare un messaggio e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Utilizzare i componenti di contenuto Designer e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Funzioni di supporto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilizzare i frammenti di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anteprima e test del contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Sperimentazione sui contenuti

- [Introduzione all’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Creare un esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapporto sull’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Calcoli statistici](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### Frequenza, conflitti e priorità

- [Regole di frequenza](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Panoramica sulle regole business](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Introduzione alla gestione dei conflitti e delle priorità](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Punteggi di priorità](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Limitazione di percorso e arbitrato](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Identificare potenziali conflitti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Tipi di pubblico e segmentazione

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/edge-segmentation)

### Reporting e analisi

- [Rapporto live del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

### Consenso e governance

- [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Gestire l’elenco di soppressione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Data Foundation

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica del profilo](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
