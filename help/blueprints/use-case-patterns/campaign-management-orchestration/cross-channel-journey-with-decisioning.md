---
title: Percorso cross-channel con decisioning
description: Scopri come orchestrare un percorso con più passaggi che incorporano decisioni in tempo reale per selezionare canali, contenuti o offerte ottimali.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: eabdd91f-bb7d-4de3-adb5-5940d3ca4a78
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '9029'
ht-degree: 2%

---

# Percorso cross-channel con decisioni

Questa guida fornisce un riferimento di implementazione completo per il percorso cross-channel con funzioni decisionali. È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono orchestrare percorsi multicanale con più passaggi che incorporano decisioni in tempo reale in uno o più nodi di percorso.

Utilizza questa guida per comprendere l’intero panorama delle scelte di implementazione, valutare i compromessi e passare alla documentazione pertinente di Experience League per istruzioni di configurazione dettagliate.

Il percorso cross-channel con decisioning è il modello di orchestrazione delle campagne più sofisticato nell&#39;ecosistema [!DNL Adobe Experience Platform]. Estende percorsi orchestrati in più passaggi incorporando decisioni in tempo reale, utilizzando [!DNL AJO] Decisioning per valutare il contesto corrente di un profilo e selezionare in modo dinamico il canale, il contenuto o l&#39;offerta ottimale in uno o più punti decisionali all&#39;interno dell&#39;area di lavoro del percorso.

## Panoramica del caso d’uso

Le organizzazioni devono sempre più spesso fornire percorsi di clienti adattativi e personalizzati che rispondano in modo dinamico al contesto in tempo reale di ogni individuo, anziché seguire una sequenza fissa e predeterminata. Il canale preferito dai clienti, la cronologia del coinvolgimento, il livello di fedeltà, il valore previsto per il ciclo di vita e gli interessi attuali dei prodotti contribuiscono a determinare quale sia l’azione migliore da intraprendere in ogni punto di contatto.

Il percorso cross-channel con il decisioning soddisfa questa esigenza combinando due potenti funzionalità di [!DNL AJO]: l&#39;orchestrazione del percorso (che gestisce il flusso in più passaggi, la tempistica, le condizioni e la distribuzione del canale) e il decisioning (che valuta le regole di idoneità, applica le strategie di classificazione e seleziona l&#39;offerta ottimale o la variante di contenuto a ogni punto decisionale).

Questo modello è appropriato quando:

- Il percorso deve adattarsi in modo dinamico allo stato in tempo reale di ciascun profilo, anziché seguire un canale fisso o una sequenza di contenuti
- Offerte multiple, varianti di contenuto o canali sono candidati in uno o più nodi di percorso e l’opzione migliore deve essere selezionata in base al contesto del profilo
- Per ottimizzare la selezione delle offerte in tutto il percorso è necessaria una classificazione basata su IA o su formula
- L’organizzazione desidera consolidare la logica di selezione dei canali e la gestione delle offerte in un framework decisionale centralizzato anziché mantenere una logica di ramificazione complessa

Il pubblico di destinazione include gli addetti al marketing che gestiscono programmi del ciclo di vita, percorsi di fidelizzazione, sequenze di riconquista e flussi di onboarding in cui la personalizzazione su larga scala richiede un processo decisionale automatizzato in ogni punto di contatto.

>[!NOTE]
>Se il percorso non richiede decisioni dinamiche sui singoli nodi, ad esempio un programma di sviluppo o onboarding a sequenza fissa, vedere [percorso orchestrato in più passaggi](multi-step-orchestrated-journey.md). Tale modello è più semplice da configurare e non richiede AJO Decisioning.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

**[Distribuisci esperienze cliente personalizzate](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
Personalizza contenuti, offerte e messaggi in base a preferenze, comportamenti e fasi del ciclo di vita individuali.
**KPI:** coinvolgimento, tassi di conversione, soddisfazione cliente (CSAT)

**[Aumenta la fedeltà dei clienti e il valore del ciclo di vita](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
Approfondisci le relazioni con i clienti e massimizza il valore a lungo termine tramite programmi di fidelizzazione, premi e coinvolgimento personalizzato.
**KPI:** valore ciclo di vita cliente, conservazione, upselling/cross-selling %

**[Miglioramento della conservazione dei clienti](../../business-objectives/customer-experience/improve-customer-retention.md)**
Coinvolgi e rinnova i clienti esistenti tramite esperienze basate sul valore aggiunto e lo sviluppo di relazioni continuative.
**KPI:** mantenimento, valore del ciclo di vita del cliente, coinvolgimento

**[Incrementa le vendite incrociate e incrementa i ricavi](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
Promuovere prodotti o servizi complementari e di alta qualità ai clienti esistenti in base al comportamento e alla cronologia degli acquisti.
**KPI:** % vendite incrociate/upselling, ricavi incrementali, valore ciclo di vita cliente

## Esempi di casi d’uso tattici

Gli scenari seguenti illustrano come applicare nella pratica il percorso cross-channel con il decisioning.

- **percorso di recupero adattivo**: un percorso in più passaggi in cui il processo decisionale seleziona il canale (e-mail, push o SMS) in base alla cronologia di coinvolgimento di ciascun profilo e seleziona in modo dinamico la migliore offerta di incentivo in base al valore previsto del ciclo di vita
- **percorso del ciclo di vita con le migliori azioni successive**: le decisioni determinano cosa comunicare in ogni fase del ciclo di vita del cliente, scegliendo tra contenuti di onboarding, offerte di cross-selling, premi fedeltà o incentivi alla fidelizzazione
- **Onboarding personalizzato con selezione dinamica dei contenuti**: nuovo percorso di onboarding dei clienti in cui ogni punto di contatto utilizza il decisioning per selezionare i contenuti, i suggerimenti o le offerte di attivazione più rilevanti per la formazione sui prodotti
- **percorso di programmi fedeltà cross-channel con premi personalizzati** — I membri fedeltà progrediscono attraverso un percorso in cui il processo decisionale seleziona offerte di premi personalizzate in base a livello, cronologia acquisti e affinità tra categorie
- **Nuovo coinvolgimento dinamico con ottimizzazione di canali e incentivi** — Nuovo coinvolgimento inattivo del cliente in cui sia il canale di sensibilizzazione che l&#39;incentivo vengono selezionati in modo dinamico per massimizzare la probabilità di risposta
- **Consigli sul ciclo di vita del cliente con contenuti classificati in base all&#39;intelligenza artificiale**: percorso di sviluppo continuo in cui il decisioning basato sull&#39;intelligenza artificiale seleziona i contenuti o i prodotti più rilevanti in ogni punto di contatto

## Indicatori chiave di prestazioni

Utilizza i seguenti KPI per misurare l’efficacia di questo modello di caso d’uso.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Percentuale di completamento percorso | Percentuale di profili che completano l’intero percorso | Rapporto percorso: completato/inserito |
| Tasso di accettazione offerta | Percentuale di offerte selezionate con decisioni che sono coinvolte con (selezionate, riscattate) | Rapporto sulle decisioni: clic sulle offerte/impression delle offerte |
| Tasso di coinvolgimento canale | Percentuali di apertura e clic su ogni canale utilizzato nel percorso | Metriche di consegna per canale nel rapporto del percorso |
| Tasso di conversione | Percentuale di partecipanti al percorso che hanno completato l&#39;azione di conversione target | Tracciamento degli eventi di uscita dal percorso o analisi CJA funnel |
| Percentuale di offerte di fallback | Percentuale di richieste di decisione che restituiscono l’offerta di fallback anziché un’offerta personalizzata | Rapporto Decisioning: selezioni di fallback/selezioni totali |
| Impatto del valore del ciclo di vita del cliente | Variazione di CLV per i partecipanti al percorso rispetto al gruppo di controllo | Analisi per coorte CJA con confronto dei dati di sospensione |
| Ricavi da vendite incrociate/upselling | Ricavi incrementali attribuiti alle offerte selezionate nel processo decisionale | Analisi dell’attribuzione CJA sulle conversioni guidate dall’offerta |
| Decisioning dell’efficacia della classificazione | Differenza di prestazioni tra le offerte classificate in base all’intelligenza artificiale e la selezione casuale/basata sulla priorità | Esperimento A/B che confronta le strategie di classificazione |

## Schema del caso d’uso

**percorso cross-channel con decisioning**

Orchestrazione di un percorso multicanale in più passaggi che incorpora decisioni in tempo reale in uno o più nodi per selezionare il canale, il contenuto o l’offerta ottimale.

**Catena di funzioni:** Valutazione del pubblico > Esecuzione del Percorso > Nodo di decisione > Selezione canale > Consegna messaggi > Reporting

## Applicazioni

Per implementare questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Adobe Journey Optimizer] ([!DNL AJO])** — orchestrazione del Percorso (progettazione area di lavoro con più passaggi, condizioni di ingresso, attese, condizioni, criteri di uscita), authoring dei messaggi tra canali, configurazione della superficie di canale, gestione dei conflitti e delle priorità
- **[!DNL Adobe Journey Optimizer]Decisioning** — Gestione di offerte e contenuti, regole di idoneità, strategie di classificazione (priorità, formula, IA), criteri di decisione, posizionamenti, offerte di fallback
- **[!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP])** — Valutazione del pubblico per i segmenti di idoneità delle offerte e delle voci di percorso, arricchimento dei profili con attributi calcolati e punteggi di propensione, applicazione del consenso e della governance
- **[!DNL Adobe Experience Platform] ([!DNL AEP])** — Archivio Profilo cliente in tempo reale, servizio Identity per la risoluzione cross-channel, modellazione dati e infrastruttura di acquisizione

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve essere al suo posto | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Presunto sul posto | [!DNL AJO] sandbox with journey, campaign, and decisioning permissions configured. Channel surfaces for all possible delivery channels. User roles for journey designers, decisioning managers, and content authors. | [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home), [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/it/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Obbligatorio | Profile schema must include attributes used for decisioning (for example, loyalty tier, purchase history, channel preferences, engagement scores). Offer catalog and decision item schemas must be configured. ExperienceEvent schemas must capture behavioral signals used by eligibility rules and ranking formulas. | [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home), [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/schema/composition) |
| Origini dati e raccolta | Presunto sul posto | Profile attributes and behavioral signals used by decisioning must be current. Real-time event streaming is needed if the journey uses event-triggered entry or exit criteria. Web SDK, Mobile SDK, or server-side collection must be active for channels that feed decisioning context. | [Panoramica di Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/home), [Panoramica delle origini](https://experienceleague.adobe.com/it/docs/experience-platform/sources/home) |
| Configurazione identità e profilo | Obbligatorio | Cross-channel identity resolution is critical — the journey must resolve profiles across email, push, SMS, and web. Merge policies must produce a unified profile for decisioning. Identity namespaces for all customer identifiers (CRM ID, email, ECID, phone) must be configured. | [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home), [Panoramica dei criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview) |
| Definizione e segmentazione del pubblico | Obbligatorio | Definizione del pubblico di ingresso per il percorso. Segmenti aggiuntivi utilizzati per le regole di idoneità delle offerte e per la ramificazione delle condizioni all’interno del percorso. Il metodo di valutazione deve corrispondere ai requisiti di latenza (streaming per immissione in tempo reale, batch per pianificata). | [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home), [Guida dell&#39;interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Consigliato | Attributi calcolati come i punteggi di tendenza di Customer AI, i punteggi di coinvolgimento, i punteggi di preferenza dei canali e i calcoli del valore del ciclo di vita migliorano notevolmente la qualità del processo decisionale. Questi attributi di profilo arricchiti consentono regole di idoneità e formule di classificazione più sofisticate. | [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview), [Panoramica di IA per l&#39;analisi dei clienti](https://experienceleague.adobe.com/it/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Data Lifecycle Management | Consigliato | La cronologia delle offerte e i dati degli eventi decisionali si accumulano nel tempo e dovrebbero includere criteri di conservazione. L’applicazione del consenso su più canali è fondamentale: i profili senza consenso valido per un canale devono essere esclusi dal percorso di consegna di quel canale. | [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/it/docs/experience-platform/data-lifecycle/home), [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted) |
| Etichettatura e applicazione dell’utilizzo dati | Consigliato | L’applicazione della governance su più canali e tipi di offerta è importante quando il processo decisionale può indirizzare i profili a canali diversi con restrizioni di utilizzo dei dati diverse. Garantisce la consegna di offerte conformi su tutti i canali. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home), [Applicazione dei criteri](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/enforcement/overview) |
| Monitoraggio e osservabilità | Incluso | Il monitoraggio dei percorsi e delle decisioni è essenziale per le operazioni di produzione. Gli avvisi relativi a errori di inserimento nel percorso, picchi di fallback decisionali ed errori di consegna consentono una rapida risoluzione dei problemi. | [Panoramica avvisi](https://experienceleague.adobe.com/it/docs/experience-platform/observability/alerts/overview), [Panoramica approfondimenti osservabilità](https://experienceleague.adobe.com/it/docs/experience-platform/observability/home) |
| Reporting e analisi | Incluso | Le relazioni sul percorso e sulle decisioni sono trattate nella fase di rendicontazione. L’analisi CJA dell’efficacia del processo decisionale, dell’ottimizzazione del mix di canali, delle prestazioni dell’offerta e del ROI del percorso fornisce le informazioni necessarie per perfezionare le strategie di classificazione e ottimizzare il percorso nel tempo. | [Panoramica di CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-overview/cja-overview), [Guida all&#39;integrazione di AJO + CJA](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Journey Optimizer] ([!DNL AJO])

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Configurazione canali | Fase 2: configurazione del canale | Configurare le superfici di canale per tutti i canali che possono essere selezionati con le decisioni o utilizzati dal percorso (e-mail, SMS, push, in-app) |
| Authoring dei messaggi | Fase 4: authoring dei messaggi | Contenuto dei messaggi di authoring per ciascun canale e integrazione dell’output decisionale: posizionamenti di offerte, blocchi di contenuto dinamici, token di personalizzazione da offerte selezionate |
| Decisioni | Fase 3: Impostazione del processo decisionale | Configurare gli elementi dell’offerta, le regole di idoneità, le strategie di classificazione, i criteri di decisione e le offerte di fallback per ogni punto decisionale del percorso |
| Journey Orchestration | Fase 5: progettazione e attivazione del Percorso | Progettare l’area di lavoro del percorso con più passaggi con condizioni di ingresso, nodi decisionali, indirizzamento dei canali, passaggi di attesa, azioni messaggio e criteri di uscita |
| Gestione dei conflitti e delle priorità | Fase 5: progettazione e attivazione del Percorso | Configurare i punteggi di priorità e il rilevamento dei conflitti se più percorsi possono eseguire il targeting simultaneo degli stessi profili |
| Frequenza e regole business | Fase 5: progettazione e attivazione del Percorso | Applica i limiti di frequenza dei messaggi tra i canali per evitare messaggi eccessivi nel percorso multicanale |
| Reporting e analisi delle prestazioni | Fase 6: Reporting e monitoraggio | Monitorare le metriche di distribuzione del percorso e per nodo, le prestazioni di decisioning e il coinvolgimento dei canali |

### [!DNL Real-Time CDP] ([!DNL RT-CDP])

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Valutazione del pubblico | Fase 1: Valutazione del pubblico | Definire e valutare il pubblico di ingresso o l’evento di ingresso qualificato; creare segmenti di idoneità utilizzati dalle decisioni |
| Arricchimento del profilo | Prerequisito/supporto | Arricchisci i profili con attributi calcolati e punteggi di propensione che migliorano la qualità delle decisioni |
| Applicazione del consenso e della governance | Fase 2: configurazione del canale | Applica le preferenze di consenso su tutti i canali; assicurati che la consegna delle offerte sia conforme alle normative |

## Prerequisiti

Completa quanto segue prima di iniziare l’implementazione.

- [ È stato eseguito il provisioning della sandbox ] [!DNL AJO] con le funzionalità di orchestrazione del percorso e decisioning abilitate
- [ ] Tutti i canali di destinazione (e-mail, SMS, push) hanno superfici di canale attive e verificate
- [ Lo schema del profilo ] include gli attributi necessari per il processo decisionale (livello fedeltà, cronologia acquisti, preferenze canale, punteggi coinvolgimento)
- [ ] è configurata la risoluzione delle identità cross-channel: i profili possono essere risolti tramite e-mail, token push, numero di telefono e identificatori Web
- [ ] Il pubblico di ingresso è definito e sta valutando con una popolazione diversa da zero
- [ ] Il contenuto del catalogo delle offerte (risorse creative, copia, esclusioni di responsabilità legali) è approvato e pronto per la configurazione
- [ ] I dati di consenso vengono acquisiti e l&#39;applicazione del consenso è attiva per tutti i canali di destinazione
- [ ] I modelli di contenuto e i frammenti per ciascun canale sono progettati e approvati
- [ ] Le regole di quota limite vengono definite e distribuite se l&#39;organizzazione dispone di criteri di frequenza per più campagne
- [ ] Se utilizzi decisioni con classificazione AI, esistono almeno 1.000 eventi di conversione per l&#39;apprendimento dei modelli

## Opzioni di implementazione

Rivedi le opzioni seguenti e seleziona l’approccio che meglio si adatta alle tue esigenze.

### Opzione A: Percorso con Offer Decisioning (canale fisso, contenuto dinamico)

**Consigliato per:** Percorsi in cui la sequenza di canali è predeterminata ma il contenuto o l&#39;offerta in ogni punto di contatto deve essere selezionato in modo dinamico: percorsi fedeltà con premi personalizzati, nuovo coinvolgimento con incentivi dinamici, sviluppo del ciclo di vita con consigli sui contenuti classificati in base all&#39;intelligenza artificiale.

#### Come funziona

L’area di lavoro del percorso definisce la sequenza fissa di canali e tempi (ad esempio, Giorno 0: E-mail, Giorno 3: Push, Giorno 7: SMS). In ogni nodo di azione del messaggio, un criterio di decisione seleziona l’offerta o il contenuto migliore da includere nel messaggio da un catalogo configurato di elementi idonei. Le offerte vengono gestite nel catalogo [!DNL AJO] Decisioning con regole di idoneità che filtrano le offerte idonee per un profilo e strategie di classificazione che determinano quale offerta idonea è la più adatta.

Questo approccio separa il &quot;quando e dove&quot; (orchestrazione del percorso) dal &quot;cosa&quot; (decisioning). Il designer del percorso controlla il flusso del canale, mentre il responsabile delle decisioni controlla il catalogo delle offerte, le regole di idoneità e la logica di classificazione in modo indipendente. Questa separazione dei problemi rende l’implementazione più gestibile e consente al catalogo delle offerte di evolvere senza modificare l’area di lavoro del percorso.

I posizionamenti delle offerte sono incorporati direttamente nel contenuto del messaggio tramite E-mail Designer o altri editor di canali. Quando viene eseguito il rendering del messaggio al momento della consegna, il motore decisionale valuta l’idoneità e la classificazione del profilo per selezionare l’offerta ottimale per ogni posizionamento nel messaggio.

#### Considerazioni chiave

- La sequenza di canali è statica: tutti i profili seguono lo stesso percorso di canale, indipendentemente dalle preferenze
- La complessità delle decisioni è inferiore, poiché seleziona solo contenuti/offerte, non canali
- Il catalogo delle offerte può essere gestito indipendentemente dal percorso
- Le offerte di fallback devono essere configurate per ogni posizionamento per gestire profili senza offerte personalizzate idonee

#### Vantaggi

- Area di lavoro di percorso più semplice: nessuna logica di diramazione per la selezione dei canali
- Chiara separazione tra la progettazione del percorso e la gestione dell&#39;offerta
- Test e convalida più semplici: ogni percorso di canale è deterministico
- Riduzione della complessità dell&#39;implementazione e tempi di commercializzazione più rapidi
- Le modifiche al catalogo delle offerte hanno effetto immediato senza modifiche al percorso

#### Limitazioni

- Impossibile adattare il canale in base al comportamento o alle preferenze dei singoli profili
- I profili che preferiscono un canale rispetto a un altro ricevono comunque messaggi sui canali predeterminati
- Non ottimizza per le percentuali di coinvolgimento a livello di canale

#### Riferimenti ad Experience League

- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)

### Opzione B: Percorso con selezione dinamica dei canali (contenuto fisso, canale dinamico)

**Ideale per:** Percorsi in cui il contenuto di ogni punto di contatto è simile, ma il canale deve essere selezionato in modo dinamico in base al contesto del profilo: win-back adattivo (e-mail vs. push vs. SMS in base al coinvolgimento), programmi con le migliori azioni successive in cui l&#39;ottimizzazione del canale è l&#39;obiettivo principale.

#### Come funziona

Il percorso utilizza i nodi delle condizioni informati dagli attributi del profilo (come i punteggi delle preferenze del canale, l’ultimo canale di coinvolgimento o lo stato del consenso) o dall’output delle decisioni per indirizzare i profili a percorsi di canale diversi. Ogni percorso fornisce contenuti specifici per il canale attraverso il proprio nodo di azione del messaggio. La logica decisionale determina quale canale è più probabile che susciti il coinvolgimento in base alla cronologia comportamentale del profilo.

La selezione del canale può essere implementata utilizzando nodi di condizione del percorso con valutazioni degli attributi di profilo (ad esempio, se `channelPreference = "push"` viene indirizzato al percorso push), oppure utilizzando decisioni con elementi specifici del canale in cui ogni &quot;offerta&quot; rappresenta un canale e la strategia di classificazione determina il canale migliore.

Questo approccio ottimizza il canale di distribuzione mantenendo al tempo stesso la coerenza dei contenuti tra i canali. Richiede che il contenuto del messaggio sia creato per ogni canale possibile e che le superfici di canale siano configurate per tutti i canali candidati.

#### Considerazioni chiave

- Richiede varianti di contenuto del messaggio per ogni canale candidato
- Le superfici di canale devono essere attive per tutti i canali possibili
- La logica della condizione o la configurazione delle decisioni devono tenere conto del consenso — i profili senza consenso SMS non possono essere indirizzati al percorso SMS
- L’area di lavoro del percorso è più complessa con percorsi di diramazione per ogni canale

#### Vantaggi

- Ottimizza la selezione del canale per ogni singolo profilo
- Aumenta il coinvolgimento complessivo raggiungendo i profili sul canale preferito
- Rispetta automaticamente il consenso specifico del canale tramite l’indirizzamento in base al consenso
- Può incorporare la cronologia del coinvolgimento e i punteggi delle preferenze del canale nelle decisioni di indirizzamento

#### Limitazioni

- Area di lavoro di percorso più complessa con più rami di canale
- Il contenuto deve essere creato separatamente per ciascun canale (anche se l’intento del messaggio è lo stesso)
- Più difficile da testare: è necessario convalidare tutti i percorsi di canale possibili
- La personalizzazione dei contenuti all’interno di ciascun canale è statica (nessuna offerta decisionale)

#### Riferimenti ad Experience League

- [Attività Condizione](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Creazione di un percorso](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)

### Opzione C: percorso adattivo completo (canale dinamico + contenuto dinamico)

**Ottimo per:** Personalizzazione massima: sia il canale che il contenuto/offerta vengono selezionati in modo dinamico in ogni nodo. Appropriato per segmenti di clienti di alto valore, programmi fedeltà sofisticati e organizzazioni con procedure decisionali mature e dati di profilo avanzati.

#### Come funziona

Questa opzione combina le opzioni A e B. Il percorso utilizza il processo decisionale a due livelli: primo, per determinare quale canale utilizzare per ogni punto di contatto e, secondo, per determinare quale contenuto o offerta distribuire nel canale selezionato. Ogni punto decisionale nel percorso valuta il contesto corrente del profilo per effettuare sia la selezione del canale che quella del contenuto.

L’implementazione richiede una configurazione completa del processo decisionale con criteri decisionali sia per la selezione del canale che per la selezione di contenuti/offerte. La selezione del canale può utilizzare un criterio di decisione in cui ogni elemento rappresenta un canale con regole di idoneità basate sul consenso e sul coinvolgimento, mentre la selezione del contenuto utilizza un criterio di decisione separato con elementi di offerta classificati per rilevanza.

Questa è la variante più complessa e richiede la più profonda integrazione tra orchestrazione del percorso e decisioning. Offre il massimo grado di personalizzazione, ma richiede anche la massima configurazione, test e gestione continua.

#### Considerazioni chiave

- Richiede due livelli di decisione: selezione del canale e selezione del contenuto
- La complessità dell’area di lavoro di percorso è più elevata con diramazioni e decisioni nidificate in ogni nodo
- Sono necessari test approfonditi su tutte le possibili combinazioni canale-contenuto
- Richiede dati di profilo avanzati (cronologia del coinvolgimento, preferenze del canale, affinità di prodotto, punteggi di propensione) per un processo decisionale efficace
- Le decisioni con classificazione AI traggono notevoli vantaggi dagli attributi calcolati

#### Vantaggi

- Massima personalizzazione: ogni punto di contatto è ottimizzato per canale e contenuto
- Miglior potenziale di coinvolgimento e conversione per implementazioni ben configurate
- Centralizza tutta la logica di personalizzazione nel processo decisionale anziché nei rami di percorso statici
- Può migliorare continuamente tramite l’apprendimento del modello di classificazione AI

#### Limitazioni

- Massima complessità nell&#39;implementazione e tempi di commercializzazione più lunghi
- Richiede la preparazione più estesa del catalogo delle offerte e dei contenuti del canale
- Più difficile da risolvere in caso di problemi di consegna
- Richiede infrastrutture dati mature con attributi di profilo avanzati
- La classificazione basata su IA richiede un volume di eventi di conversione sufficiente per l’apprendimento dei modelli

#### Riferimenti ad Experience League

- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Confronto delle opzioni

Utilizza la tabella seguente per confrontare rapidamente le tre opzioni di implementazione.

| Criteri | Opzione A: Offer Decisioning | Opzione B: canale dinamico | Opzione C: Adattabilità completa |
| --- | --- | --- | --- |
| Ideale per | Sequenza a canale fisso, contenuto dinamico | Ottimizzazione dei canali, contenuti coerenti | Massima personalizzazione per entrambe le dimensioni |
| Complessi | Medio | Medium - Alta | Alta |
| Area di lavoro percorso | Semplice (lineare con decisioning nei nodi di azione) | Modera (diramazione per percorsi canale) | Complesso (ramificazioni nidificate con decisioning a più livelli) |
| Ambito decisionale | Solo selezione di contenuti/offerte | Solo selezione canale | Selezione di canali e contenuti |
| Requisiti del contenuto | Un set di contenuti per canale (con posizionamenti di offerte) | Contenuto per ciascun canale candidato | Contenuto con posizionamenti di offerte per ogni canale candidato |
| Dati profilo richiesti | Moderato (attributi di idoneità dell’offerta) | Modera (preferenza canale, coinvolgimento) | Alta (attributi di canale e di offerta) |
| Time-to-market | Più veloce | Modera | Più lungo |
| Gestione continua | Gestione catalogo offerte | Gestione logica di routing dei canali | Instradamento sia del catalogo delle offerte che del canale |
| Profondità Personalization | Il contenuto varia, il canale è fisso | Canale variabile, contenuto simile | Canale e contenuto variano |

### Scegli l’opzione giusta

Utilizza le indicazioni seguenti per determinare l’opzione migliore per la tua situazione.

- **Inizia con l&#39;opzione A** se la tua strategia di canale è già definita (ad esempio, &quot;inviamo sempre e-mail prima, quindi inviamo e-mail, poi SMS&quot;) e la necessità principale di personalizzazione consiste nel selezionare l&#39;offerta o il contenuto giusto a ogni punto di contatto. Questo è il punto di partenza più comune per le organizzazioni che non hanno familiarità con le decisioni.

- **Scegliere l&#39;opzione B** se l&#39;ottimizzazione del canale è l&#39;obiettivo principale: si desidera raggiungere ogni cliente sul canale con cui è più probabile che interagisca, ma il contenuto del messaggio è relativamente coerente tra i canali. Questo richiede dati sulle preferenze del canale sui profili.

- **Scegli l&#39;opzione C** solo quando disponi di un&#39;infrastruttura decisionale matura, di dati di profilo avanzati (inclusi attributi calcolati e punteggi di propensione), di un catalogo delle offerte ben popolato e della capacità organizzativa necessaria per gestire la complessità. Molte organizzazioni iniziano con l’opzione A o B e passano all’opzione C con l’aumentare della maturità decisionale.

- **Se non si è certi**, iniziare con l&#39;opzione A. Offre una personalizzazione significativa con la complessità più bassa e il catalogo delle offerte creato per l’opzione A è direttamente riutilizzabile se successivamente si passa all’opzione C.

## Fasi di implementazione

Le seguenti fasi descrivono l’implementazione end-to-end di questo modello di caso d’uso.

### Fase 1: Valutazione del pubblico

**Funzione dell&#39;applicazione:** [!DNL RT-CDP]: valutazione del pubblico

Questa fase configura il pubblico di ingresso che determina i profili che entrano nel percorso ed eventuali altri segmenti utilizzati per le regole di idoneità delle offerte o per la diramazione delle condizioni all’interno del percorso. La definizione del pubblico è la base per tutta la logica decisionale e di percorso a valle.

#### Decisione: tipo di voce

In che modo i profili devono entrare nel percorso, tramite una lettura pianificata del pubblico o un trigger di evento in tempo reale?

>[!NOTE]
>Seleziona un tipo di voce in base ai requisiti di tempistica e attivazione del percorso.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Read Audience (voce batch) | Programmi del ciclo di vita, percorsi fedeltà, campagne di ricoinvolgimento pianificate | I profili vengono immessi in batch agli orari pianificati; il pubblico viene valutato al momento della lettura; supporta dimensioni di pubblico elevate |
| Qualificazione del pubblico (streaming) | Percorsi attivati dal comportamento in cui l’ingresso dovrebbe avvenire quando un profilo entra in un segmento o ne esce | Immissione quasi in tempo reale; richiede la definizione di segmenti idonei per lo streaming; ideale per percorsi basati su milestone |
| Evento unitario (attivazione evento) | Un evento specifico deve attivare il percorso (ad esempio, acquisto, abbandono carrello, registrazione) | Immissione in tempo reale su evento; richiede la configurazione dello schema dell’evento; limitato a 5.000 eventi/secondo |

#### Decisione: metodo di valutazione del pubblico

Quanto rapidamente il pubblico deve qualificare i profili?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Batch | Sono sufficienti aggiornamenti giornalieri o periodici del pubblico; percorsi pianificati in stile campagna | Elabora fino a 24 milioni di profili per processo; in base alla pianificazione; è supportata la maggior parte delle espressioni delle regole di segmento |
| Streaming | L’iscrizione al pubblico in tempo reale è necessaria per l’ingresso attivato da un evento o basato su una qualifica | Quasi in tempo reale; set di funzioni regola segmento limitato; nessuna aggregazione basata sul tempo |
| Edge | Qualificazione per la stessa sessione richiesta | Latenza in millisecondi; solo controlli di attributi semplici; limitato agli attributi di profilo edge |

#### Dettagli chiave della configurazione

**Navigazione interfaccia utente:** Cliente > Tipi di pubblico > Crea pubblico > Genera regola

- Definisci il pubblico di ingresso utilizzando Segment Builder (Generatore di segmenti) con espressioni della regola di segmento che eseguono il targeting degli attributi di profilo e degli eventi comportamentali pertinenti
- Crea ulteriori segmenti di idoneità se le regole di idoneità per le offerte faranno riferimento all’iscrizione al segmento (ad esempio, &quot;Clienti di valore elevato&quot;, &quot;Livello Oro fedeltà&quot;)
- Verifica che il pubblico sia diverso da zero prima di procedere alla configurazione del percorso
- Seleziona il criterio di unione che produce la vista di profilo unificata necessaria per le decisioni

#### Documentazione di Experience League

- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/pql/overview)

### Fase 2: configurazione del canale

**Funzione applicazione:** [!DNL AJO]: Configurazione canale

Questa fase configura le superfici di canale per ogni canale che il percorso può utilizzare per la consegna dei messaggi. Prima di poter creare i messaggi o pubblicare il percorso, tutti i canali candidati devono avere superfici attive e verificate. Per questo pattern, in genere si configurano superfici per e-mail, SMS e push come minimo e, potenzialmente, in-app o web, se il processo decisionale può selezionare tali canali.

#### Decisione: quali canali configurare

Quali sono i canali candidati per il percorso, come fasi di percorso fisse (opzioni A/B) o come canali selezionabili mediante decisioni (opzioni B/C)?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo e-mail | Percorso a canale singolo con offer decisioning (opzione A, solo e-mail) | Configurazione più semplice; richiede la delega del sottodominio e il riscaldamento dell’IP |
| E-mail + push | Percorso a due canali; comune per percorsi incentrati sul coinvolgimento | Il push richiede credenziali APNs/FCM; l’app mobile deve avere SDK integrato |
| E-mail + SMS + push | Percorso completo cross-channel; più comune per le opzioni B e C | Per SMS sono necessarie le credenziali del provider (Sinch, Twilio, Infobip); ogni canale ha bisogno della propria superficie |
| E-mail + SMS + push + in-app | Copertura massima del canale, incluse le superfici in sessione | In-app richiede la configurazione della superficie dell’app e del SDK per dispositivi mobili |

#### Decisione: metodo di delega del sottodominio (e-mail)

Come deve essere delegato il sottodominio di invio ad Adobe?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Delega completa | L’organizzazione desidera che Adobe gestisca tutti i record DNS per il sottodominio di invio | Configurazione più semplice; Adobe gestisce SPF, DKIM, DMARC; meno controllo sul DNS |
| Delega CNAME | L&#39;organizzazione deve mantenere il controllo dei record DNS | Configurazione più complessa; gestione del DNS da parte del cliente; maggiore flessibilità |

#### Dettagli chiave della configurazione

**Navigazione interfaccia utente:** Amministrazione > Canali > Superfici di canale > Crea superficie

- Per le e-mail: configura sottodominio, pool IP, nome del mittente, indirizzo di risposta e gestione dell’annullamento dell’abbonamento
- For SMS: configure SMS provider credentials and sender number
- For push: configure APNs and FCM credentials for iOS and Android
- Verify each surface is in Active status before proceeding
- Confirm IP warmup is complete for email sending IPs

#### Documentazione di Experience League

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delega sottodomini](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Creare pool IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Configurare il canale SMS](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Phase 3: Decisioning setup

**Application function:** [!DNL AJO]: Decisioning

This phase configures the complete decisioning framework including placements, eligibility rules, personalized offers, fallback offers, collection qualifiers, collections, ranking strategies, and decision policies. This phase creates the decision logic that will be invoked at journey decision points.

#### Decision: Decisioning scope

What should decisioning select — offers/content (Option A), channels (Option B), or both (Option C)?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Offer/content selection only | Channel sequence is fixed; personalization is in the content | I criteri di decisione eseguono il targeting degli elementi di offerta con rappresentazioni di contenuto per posizionamento |
| Solo selezione canale | Il contenuto è coerente; l’ottimizzazione si trova sul canale di consegna | Gli elementi decisionali rappresentano i canali; l’idoneità include i controlli del consenso; la classificazione utilizza i dati del coinvolgimento |
| Canale e contenuto | Personalizzazione adattiva completa su canali e contenuti | Richiede due livelli di criteri decisionali; la personalizzazione più complessa ma più elevata |

#### Decisione: strategia di classificazione

Come dovrebbero essere classificate le offerte idonee per selezionare quella migliore?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Basato su priorità (manuale) | Classificazione semplice in cui le regole business determinano l’importanza dell’offerta | Ogni offerta ottiene un punteggio di priorità; vince la priorità più alta; deterministico e facile da capire |
| Basato su formula (espressione personalizzata) | La classificazione deve tenere conto degli attributi del profilo (ad esempio, CLV, livello, punteggio di affinità) | La formula di classificazione personalizzata valuta il contesto del profilo; più dinamico della priorità; non è richiesto alcun ML |
| Classificato in base all’intelligenza artificiale (ottimizzazione automatica) | La classificazione deve essere ottimizzata automaticamente in base ai dati di conversione storici | Il modello di intelligenza artificiale apprende dagli eventi di conversione; richiede almeno 1.000 eventi per la formazione; migliora continuamente |

#### Decisione: limite dell’offerta

Dovrebbero esserci limiti sul numero di volte in cui viene visualizzata un’offerta?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Limite per profilo | Impedisci che la stessa offerta venga mostrata ripetutamente allo stesso profilo | Protegge dall&#39;affaticamento dell&#39;offerta; contro lag possibile con throughput elevato |
| Limite globale | Limitare il numero totale di impression su tutti i profili (ad esempio, promozioni di inventario limitate) | Controlla l&#39;esposizione totale; utile per le offerte limitate |
| Nessun limite | Ogni impression idonea deve mostrare l’offerta | Più semplice; adatto a contenuti fissi o offerte illimitate |

#### Dettagli chiave della configurazione

**Navigazione interfaccia utente:** Componenti > Gestione decisioni > Posizionamenti / Offerte / Decisioni

- Crea posizionamenti per ogni combinazione di canale e tipo di contenuto (ad esempio, banner HTML e-mail, JSON push, testo SMS)
- Definire le regole di idoneità utilizzando espressioni della regola di segmento che fanno riferimento ad attributi di profilo o appartenenza a un pubblico
- Crea offerte personalizzate con rappresentazioni per ogni posizionamento, assegna le regole di idoneità e imposta la priorità
- Crea un’offerta di fallback che copre tutti i posizionamenti: questa viene restituita quando nessuna offerta personalizzata è idonea
- Organizzare le offerte in raccolte utilizzando i qualificatori di raccolta (tag)
- Configurare la strategia di classificazione: basata su priorità, basata su formule o classificata in base all’intelligenza artificiale
- Creare criteri di decisione che associano posizionamenti, raccolte, strategia di classificazione e offerte di fallback
- Approva tutte le offerte prima che possano essere selezionate con le decisioni

#### Dove le opzioni divergono

**Per L&#39;Opzione A (Offer Decisioning):**
Crea posizionamenti e offerte incentrati sulla personalizzazione dei contenuti all’interno di ciascun canale (ad esempio, offerta banner e-mail hero, offerta piè di pagina e-mail, offerta corpo della notifica push). I criteri di decisione selezionano il contenuto migliore per ogni posizionamento nel messaggio.

**Per L&#39;Opzione B (Selezione Canale Dinamico):**
Crea elementi decisionali che rappresentano ogni canale. Le regole di idoneità includono i controlli del consenso (ad esempio, un profilo deve disporre del consenso SMS per essere idoneo all’elemento SMS). La classificazione utilizza punteggi di coinvolgimento del canale o espressioni basate su formule.

**Per L&#39;Opzione C (Adattabile):**
Configura due livelli di decisioning: un set di criteri di decisione per la selezione del canale e un set separato per la selezione di contenuti/offerte all’interno del canale selezionato. Entrambi i livelli richiedono posizionamenti, offerte, regole di idoneità e strategie di classificazione.

#### Documentazione di Experience League

- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Creare i posizionamenti](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Creare regole di decisione](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Creare offerte di fallback](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Creare le raccolte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Fase 4: authoring dei messaggi

**Funzione dell&#39;applicazione:** [!DNL AJO]: authoring dei messaggi

Questa fase configura il contenuto del messaggio per ogni canale e punto di contatto nel percorso, integrando l’output del decisioning (contenuto dell’offerta selezionata) nei modelli di messaggio. Ogni nodo di azione del messaggio nel percorso richiede contenuti creati con la superficie di canale, i token di personalizzazione e le integrazioni di posizionamento delle offerte appropriate.

#### Decisione: approccio basato sul contenuto

Come creare il contenuto dei messaggi per ogni canale?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Basato su modello | L’organizzazione ha stabilito modelli di marchio; la coerenza è importante | Authoring più rapido; garantisce la coerenza del marchio; può limitare la flessibilità di progettazione |
| Progettare da zero | Creatività univoca per questo percorso; nessun modello esistente | Controllo completo della progettazione; tempi di authoring più lunghi; trascinamento della selezione tramite E-mail Designer |
| Importa HTML | Il team Creative produce HTML esternamente; importa in [!DNL AJO] | Mantiene il flusso di lavoro di progettazione esterno; richiede la compatibilità di HTML con E-mail Designer |

#### Decisione: ambito Personalization

Quale livello di personalizzazione deve includere i messaggi oltre all’output decisionale?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Personalizzazione di base (nome, saluto) | Esigenze minime di personalizzazione oltre la selezione dell’offerta | Espressioni Handlebars semplici; complessità ridotta |
| Blocchi di contenuto condizionali | Sezioni di contenuto diverse per segmenti o attributi diversi | Utilizza regole di contenuto dinamico; il contenuto varia in base all’attributo di profilo o all’iscrizione al segmento |
| Personalizzazione completa con integrazione del decisioning | Posizionamenti di offerta incorporati nel messaggio, combinati con la personalizzazione basata sul profilo | Combina l’output di Offer Decisioning con i token di personalizzazione Handlebars; esperienza più ricca |

#### Dettagli chiave della configurazione

**Navigazione interfaccia utente:** Seleziona azione campagna o percorso > Modifica contenuto > E-mail Designer/Editor canale

- Contenuto del messaggio dell’autore per ogni canale utilizzato nel percorso (e-mail, SMS, push, in-app)
- Incorpora i posizionamenti di decisione per le offerte nel contenuto del messaggio dove dovrebbero apparire le offerte selezionate con decisioni
- Aggiungere espressioni di personalizzazione utilizzando la sintassi Handlebars per gli attributi del profilo (ad esempio, `{{profile.person.name.firstName}}`)
- Configurare blocchi di contenuto condizionale per la messaggistica specifica per segmento
- Creare frammenti di contenuto riutilizzabili per gli elementi condivisi (intestazioni, piè di pagina, dichiarazioni di non responsabilità)
- Anteprima e test con profili di esempio per verificare che i rendering della personalizzazione siano corretti
- Inviare messaggi di prova per la revisione delle parti interessate

#### Dove le opzioni divergono

**Per L&#39;Opzione A (Offer Decisioning):**
Ogni messaggio include posizionamenti di offerta in cui viene visualizzato il contenuto selezionato in base alle decisioni. Il layout del messaggio è coerente, ma l’area offerta mostra in modo dinamico l’offerta migliore per ogni profilo.

**Per L&#39;Opzione B (Selezione Canale Dinamico):**
Ogni canale ha il proprio contenuto di messaggi creato separatamente. Il contenuto è simile per tutti i canali, ma adattato ai vincoli del canale (testo e-mail HTML vs SMS vs. formato di notifica push).

**Per L&#39;Opzione C (Adattabile):**
Ogni canale ha il proprio contenuto di messaggi con posizionamenti di offerte incorporati. Sia il canale che il contenuto dell’offerta all’interno di tale canale vengono selezionati in modo dinamico.

#### Documentazione di Experience League

- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilizzare i frammenti di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Creare un messaggio SMS](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/sms/create-sms)
- [Progettare una notifica push](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/push/design-push)

### Fase 5: progettazione e attivazione del Percorso

**Funzione dell&#39;applicazione:** [!DNL AJO]: Journey Orchestration, [!DNL AJO]: gestione dei conflitti e delle priorità, [!DNL AJO]: regole di frequenza e regole business

Questa fase configura l’area di lavoro completa del percorso, inclusi la configurazione dell’entrata, i nodi decisionali collegati ai criteri di decisione configurati, le suddivisioni delle condizioni per il routing dei canali (Opzioni B/C), i nodi di azione dei messaggi per ciascun percorso di canale, i nodi di attesa tra i punti di contatto, i criteri di uscita, le impostazioni per conflitti/priorità e le regole di quota limite. Questa fase assembla tutti i componenti configurati in precedenza nel flusso di percorso orchestrato e lo attiva.

#### Decisione: politica di rientro

I profili possono rientrare nel percorso dopo aver completato o chiuso?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Consenti rientro (con raffreddamento) | Percorsi ricorrenti in cui i profili possono qualificarsi nuovamente (ad esempio, rinnovo della fedeltà trimestrale) | Imposta un periodo di raffreddamento (minimo 5 minuti) per impedire il rientro immediato; il profilo viene riavviato dall’inizio |
| Nessun rientro | Percorsi una tantum in cui ogni profilo deve attraversare una sola volta (ad esempio, l’onboarding) | Il profilo non può rientrare dopo il completamento o l’uscita; comportamento più semplice |

#### Decisione: criteri di uscita

In quali condizioni un profilo deve essere rimosso dal percorso prima del completamento?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Modifica dell’iscrizione al pubblico | Il profilo deve uscire quando lascia il pubblico di ingresso o entra in un pubblico di soppressione | Uscita in tempo reale alla modifica del segmento, utile per le uscite &quot;convertite&quot; o &quot;con rinuncia&quot; |
| Occorrenza evento | Un evento specifico (ad esempio acquisto, annullamento dell’abbonamento) deve attivare l’uscita | Uscita in tempo reale da un evento; richiede la configurazione dello schema dell’evento |
| Timeout | La durata massima nel percorso è trascorsa | Il valore massimo predefinito è 91 giorni; impedisce ai profili di rimanere indefinitamente |

#### Decisione: timeout del Percorso

Qual è la durata massima che un profilo può rimanere nel percorso?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| 91 giorni (massimo) | Percorsi a ciclo di vita lungo con sequenze di sviluppo estese | Durata massima consentita; i profili terminano dopo 91 giorni indipendentemente |
| Durata più breve personalizzata | Campagne con limiti di tempo o percorsi stagionali | Impostato in base alla logica di business del percorso; un timeout più breve riduce i profili non aggiornati |

#### Decisione: impostazioni di conflitti e priorità

Questo percorso dovrebbe avere un punteggio di priorità per la risoluzione dei conflitti con altri percorsi/campagne?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Priorità alta (70-100) | Percorsi di clienti critici (fidelizzazione, fidelizzazione) che dovrebbero avere la precedenza | Una priorità più alta si ottiene quando più comunicazioni competono; utilizzare con moderazione |
| Priorità Medium (30-69) | Standard lifecycle journeys | Balanced priority; may be suppressed by higher-priority communications |
| Priorità bassa (0-29) | Supplemental or informational journeys | Will be suppressed when competing with more important communications |

#### Dettagli chiave della configurazione

**UI navigation:** Journeys > Create Journey

- Create the journey and configure properties (name, description, timezone, timeout)
- Configure entry: Read Audience (for batch) or event trigger (for real-time)
- Add decision nodes linked to configured decision policies from Phase 3
- Add condition splits for channel routing based on decision output or profile attributes (Options B/C)
- Add message action nodes for each channel path, linking to the authored content from Phase 4
- Add wait nodes between touchpoints (minimum 1 hour for audience-read journeys)
- Define exit criteria (audience change, event, timeout)
- Assign priority score for conflict resolution
- Configure frequency capping if cross-journey frequency limits apply
- Test the journey in test mode with test profiles before publishing
- Publish the journey to make it live

#### Dove le opzioni divergono

**Per L&#39;Opzione A (Offer Decisioning):**
The journey canvas is linear with decision policies embedded in each message action node. No branching for channel selection. The offer decision is made at message render time within the action node.

**Per L&#39;Opzione B (Selezione Canale Dinamico):**
After each wait step, add a condition node that evaluates channel selection criteria (profile attributes, decisioning output, or consent status). Each condition branch leads to a channel-specific message action node. Includi un percorso predefinito/else per i profili che non soddisfano alcuna condizione.

**Per L&#39;Opzione C (Adattabile):**
Combina i nodi della condizione di selezione del canale con i nodi dell’azione del messaggio incorporati nei criteri di decisione. A ogni punto di contatto: in primo luogo, una condizione o una decisione determina il canale; quindi, all’interno dell’azione del messaggio del canale selezionato, un criterio di decisione seleziona l’offerta o il contenuto ottimale.

#### Documentazione di Experience League

- [Creazione di un percorso](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Proprietà del percorso](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Attività Read audience](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Attività Condizione](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Attività Attendi](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Aggiungere un messaggio in un percorso](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Criteri di uscita](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Gestione voci percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Test del percorso](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Pubblicare il percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [Punteggi di priorità](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Panoramica sulla gestione dei conflitti e delle priorità](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Regole di frequenza](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### Fase 6: Reporting e monitoraggio

**Funzione applicazione:** [!DNL AJO]: Reporting e analisi delle prestazioni

Questa fase configura il monitoraggio delle prestazioni del percorso e del processo decisionale tramite rapporti live (durante l’esecuzione) e cronologici (dopo il completamento). Metriche specifiche per il processo decisionale, tra cui distribuzione della selezione delle offerte, tassi di fallback ed efficacia della classificazione. Facoltativamente, analisi dello spazio di lavoro CJA per un percorso cross-channel approfondito e analisi del ROI decisionale.

#### Decisione: profondità di reporting

Quale livello di analisi dei rapporti è necessario?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo [!DNL AJO] rapporti nativi | Monitoraggio operativo delle metriche di consegna e coinvolgimento | Rapporti live e cronologici incorporati; nessuna configurazione aggiuntiva; limitato a [!DNL AJO] metriche |
| [!DNL AJO] + analisi CJA | Analisi cross-channel approfondita, efficacia del processo decisionale, ROI del percorso, analisi per coorte | Richiede connessione CJA e visualizzazione dati; fornisce funzionalità di attribuzione, funnel e analisi per coorte |

#### Dettagli chiave della configurazione

**Navigazione interfaccia utente:** Percorsi > Seleziona percorso > Report live/Report all time

- Monitora il report live del percorso durante l’esecuzione iniziale per le metriche di entrata, uscita e per nodo
- Verifica delle prestazioni decisionali: distribuzione della selezione delle offerte, tasso di offerta di fallback, efficacia della classificazione
- Dopo il completamento del percorso, rivedi i rapporti cronologici per l’analisi completa di funnel
- Per l&#39;analisi CJA: verificare che la connessione CJA includa [!DNL AJO] set di dati (evento di feedback del messaggio, evento di tracciamento e-mail)
- Crea un’area di lavoro CJA con pannelli per l’analisi del mix di canali, il confronto delle prestazioni e funnel di conversione del percorso
- Creazione di annotazioni per le date di avvio del percorso e per modifiche significative alla configurazione

#### Documentazione di Experience League

- [Rapporto live del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/home)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Considerazioni sull’implementazione

Rivedi i seguenti guardrail, insidie comuni, best practice e decisioni di compromesso prima e durante l’implementazione.

### Guardrail e limiti

- Massimo 500 percorsi live per sandbox: [guardrail Journey Optimizer](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/get-started/guardrails)
- La durata massima del percorso è di 91 giorni (timeout globale)
- Massimo 50 attività per area di lavoro del percorso
- Read Audience percorsi può elaborare fino a 20.000 profili al secondo
- I percorsi di eventi unitari supportano fino a 5.000 eventi al secondo per sandbox
- Massimo 10.000 offerte personalizzate approvate per sandbox
- Massimo 30 posizionamenti per decisione
- Tempi di risposta per la consegna delle offerte SLA: meno di 500 ms a P95 per richieste con ambito singolo
- I modelli di classificazione IA richiedono almeno 1.000 eventi di conversione per la formazione
- Massimo 10 superfici di canale per tipo di canale per sandbox
- I passaggi di attesa hanno una durata minima di 1 ora per i percorsi di lettura del pubblico
- Il tempo percorso di rientro è di almeno 5 minuti
- Massimo 4.000 definizioni di segmenti per sandbox: [guardrail della piattaforma](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)

### Insidie comuni

**La decisione restituisce sempre l&#39;offerta di fallback:** verifica che le offerte personalizzate siano approvate (non in stato di bozza), entro il loro intervallo di date di validità e che le regole di idoneità corrispondano agli attributi dei profili di destinazione. Verifica che i limiti di limitazione delle offerte non siano stati raggiunti. Testa con un profilo che dovrebbe essere chiaramente idoneo per un’offerta personalizzata.

**Il Percorso pubblica ma i profili non entrano:** Per i percorsi di lettura del pubblico, confermare che il pubblico ha una popolazione valutata maggiore di zero. Per i percorsi attivati da eventi, verifica lo schema dell’evento, le condizioni di attivazione e che gli eventi vengano inviati. Verifica che il criterio di unione del pubblico di ingresso corrisponda al criterio di unione previsto dal percorso.

**Formula di classificazione non applicata correttamente:** Verificare che la sintassi della formula sia valida e faccia riferimento agli attributi di profilo accessibili. Gli errori di formula tornano automaticamente alla classificazione basata sulla priorità senza alcun avviso. La classificazione dei test con profili che hanno valori di attributo diversi per confermare che la formula produce l’ordine previsto.

**Il routing del canale ignora il consenso:** I nodi della condizione per la selezione del canale devono includere verifiche del consenso. Un profilo senza consenso SMS non deve essere indirizzato al percorso SMS. Converti il consenso nelle regole di idoneità quando utilizzi le decisioni per la selezione del canale (opzione B/C).

**I contatori di limite delle offerte sono in ritardo rispetto al throughput elevato:** I contatori di limite delle offerte possono subire un ritardo di alcuni secondi in scenari di throughput elevato. Se il limite esatto è fondamentale, utilizza i limiti globali con un buffer o combinali con le regole di frequenza.

**L&#39;area di lavoro Percorsi supera il limite di 50 attività:** I percorsi Opzione C complessi con molti rami di canale e nodi decisionali possono avvicinarsi al limite di 50 attività. Semplifica consolidando la logica della condizione, riducendo il numero di punti di contatto o suddividendola in più percorsi sequenziali.

**Le decisioni di Edge restituiscono una personalizzazione vuota:** Se utilizzi le decisioni edge per le decisioni in tempo reale, assicurati che lo stream di dati abbia il servizio [!DNL Adobe Journey Optimizer] abilitato e che l&#39;ambito decisionale sia formattato correttamente. Le decisioni di Edge sono limitate agli attributi di profilo disponibili nell’archivio profili edge.

### Best practice

**Inizia con semplicità ed evoluzione:** Inizia con l&#39;opzione A (canale fisso, offerte dinamiche) per convalidare il framework decisionale, quindi passa alle opzioni B o C con l&#39;aumentare della maturità dei dati e della capacità organizzativa.

**Investire nell&#39;arricchimento dei profili:** Gli attributi calcolati come i punteggi di coinvolgimento, gli indici di preferenza dei canali e i punteggi di propensione di IA per l&#39;analisi dei clienti migliorano notevolmente la qualità del processo decisionale. Crea questi attributi di arricchimento prima di configurare strategie di classificazione complesse.

**Configura sempre le offerte di fallback:** Ogni criterio decisionale deve avere un&#39;offerta di fallback. Progetta le offerte di fallback come contenuti di grande valore (non segnaposto vuoti), in quanto gestiscono profili che non sono idonei per alcuna offerta personalizzata.

**Test con profili diversi:** Utilizza la modalità di test con profili che rappresentano percorsi di idoneità diversi, preferenze di canale e combinazioni di attributi. Verifica che ogni possibile percorso di percorso e risultato del processo decisionale funzioni correttamente prima di pubblicarlo.

**Monitorare i tassi di fallback come metrica di integrità:** un elevato tasso di offerta di fallback indica che le regole di idoneità sono troppo restrittive oppure che il catalogo delle offerte non copre un numero sufficiente di segmenti di profilo. Esegui il targeting di un tasso di fallback inferiore al 20% per decisioni ben configurate.

**Utilizza frammenti di contenuto per coerenza cross-channel:** crea frammenti di contenuto condivisi (intestazioni, piè di pagina, dichiarazioni di non responsabilità, blocchi di annullamento abbonamento) per mantenere la coerenza del brand tra e-mail, SMS e messaggi push all&#39;interno del percorso.

**Configurare i criteri di uscita in modo proattivo:** Definire i criteri di uscita per gli eventi di conversione (ad esempio, acquisto, registrazione) in modo che i profili che completano l&#39;azione desiderata vengano rimossi immediatamente dal percorso anziché continuare a ricevere messaggi.

**Assegna punteggi di priorità significativi:** Quando esegui più percorsi e campagne, assegna punteggi di priorità in base all&#39;impatto aziendale. I percorsi di conservazione di elevato valore devono avere priorità maggiore rispetto alle comunicazioni informative.

### Decisioni di compromesso

Esamina i seguenti compromessi per orientare le scelte di implementazione.

#### Decisioning della complessità rispetto al time-to-market

Decisioning più sofisticato (opzione C con classificazione basata su IA) offre una personalizzazione più elevata, ma richiede una quantità significativamente maggiore di configurazione, preparazione dei dati e tempi di test.

- **L&#39;opzione A/B favorisce:** distribuzione più rapida, test più semplici, riduzione del sovraccarico di gestione continuo
- **L&#39;opzione C favorisce:** personalizzazione massima, ottimizzazione continua basata sull&#39;intelligenza artificiale, massimo potenziale di coinvolgimento
- **Consiglio:** Iniziare con l&#39;opzione A o B per l&#39;avvio iniziale. Raccogli i dati sulle prestazioni e genera in parallelo gli attributi di arricchimento del profilo. Passa all’opzione C quando disponi di almeno 1.000 eventi di conversione per l’apprendimento della classificazione AI e un catalogo di offerte ben popolato.

#### Branching statico e decisioning per la selezione del canale

La selezione dei canali può essere implementata attraverso semplici nodi di condizione del percorso (valutando direttamente gli attributi del profilo) o attraverso il framework decisionale (in cui i canali sono modellati come elementi decisionali con idoneità e classificazione).

- **I nodi con condizione statica favoriscono:** Semplicità, trasparenza, facile risoluzione dei problemi. Consigliato quando la logica di selezione del canale è semplice (ad esempio, &quot;se è presente un token push e l’ultima apertura push è avvenuta entro 30 giorni, usa push; in caso contrario invia un messaggio e-mail&quot;).
- **La selezione dei canali basata su decisioni favorisce:** gestione centralizzata, potenziale di ottimizzazione IA, possibilità di evolvere la logica di classificazione senza modificare l&#39;area di lavoro del percorso. Consigliato quando la selezione del canale è complessa e dovrebbe migliorare nel tempo.
- **Consiglio:** utilizzare nodi di condizione statici per l&#39;opzione B quando i criteri di selezione dei canali sono semplici e ben definiti. Utilizza la selezione dei canali basata su decisioni quando desideri che l’intelligenza artificiale ottimizzi la selezione dei canali nel tempo o quando la logica di selezione dei canali è sufficientemente complessa da beneficiare di una gestione centralizzata dell’idoneità e della classificazione.

#### Granularità dell’offerta e gestibilità del catalogo

Un ampio catalogo di offerte granulare con molte offerte mirate produce una personalizzazione più precisa, ma richiede un maggiore sforzo di gestione. Un catalogo più piccolo con idoneità più ampia è più facile da gestire, ma meno personalizzato.

- **Catalogo di grandi dimensioni (molte offerte specifiche) favorisce:** maggiore precisione di personalizzazione, selezioni più rilevanti per tipi di pubblico diversi, percentuali di fallback più basse
- **Piccolo catalogo (meno offerte generiche) favorisce:** Gestione più semplice, configurazione più rapida, test più semplici, minor rischio di offerte orfane
- **Consiglio:** inizia con 5-15 offerte personalizzate più un fallback per decisione. Aggiungi altre offerte man mano che noti quali segmenti ricevono le offerte di fallback più frequentemente. Utilizza i qualificatori di raccolta per organizzare le offerte per categoria, livello o linea di prodotti per una crescita gestibile.

#### Decisioning basato su priorità e basato sull’intelligenza artificiale

La classificazione basata sulle priorità è deterministica e trasparente. Le decisioni con classificazione AI vengono ottimizzate automaticamente, ma richiedono dati di formazione e sono meno trasparenti.

- **Preferenze di classificazione basata su priorità:** Prevedibilità, trasparenza, distribuzione immediata, nessun requisito di dati di formazione
- **Il decisioning basato sull&#39;intelligenza artificiale favorisce:** ottimizzazione continua, selezione basata sui dati, possibilità di individuare affinità non ovvie tra profili di offerta
- **Consiglio:** Utilizzare la classificazione basata su priorità o su formula per la distribuzione iniziale. Passaggio al decisioning basato sull’intelligenza artificiale una volta accumulati almeno 1.000 eventi di conversione e se desideri passare dall’ottimizzazione basata su regole a quella basata su modelli.

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sulle funzionalità utilizzate in questo modello di caso d’uso.

### Orchestrazione percorso

- [Introduzione ai percorsi](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Creazione di un percorso](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Proprietà del percorso](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Attività Read audience](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Eventi generali](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Eventi di qualificazione del pubblico](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Attività Condizione](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Attività Attendi](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Aggiungere un messaggio in un percorso](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Criteri di uscita](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Gestione voci percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Test del percorso](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Pubblicare il percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### Gestione delle decisioni

- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Creare i posizionamenti](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Creare regole di decisione](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Creare offerte di fallback](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Creare le raccolte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Creare qualificatori di raccolta](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Configurazione dei canali

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delega sottodomini](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Creare pool IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Piani di riscaldamento IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Impostazioni superficie e-mail](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configurare il canale SMS](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Authoring e personalizzazione dei messaggi

- [Creare un messaggio e-mail](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/create-email)
- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilizzare i frammenti di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anteprima e test del contenuto](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Gestione dei conflitti, delle priorità e delle frequenze

- [Panoramica sulla gestione dei conflitti e delle priorità](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Punteggi di priorità](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identificare potenziali conflitti](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Limitazione di percorso e arbitrato](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Regole di frequenza](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### Tipi di pubblico e segmentazione

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Composizione del pubblico](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/audience-composition)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/pql/overview)

### Reporting e analisi

- [Rapporto live del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Panoramica di CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-overview/cja-overview)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/home)

### Profilo e identità

- [Panoramica del profilo cliente in tempo reale](https://experienceleague.adobe.com/it/docs/experience-platform/profile/home)
- [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview)
- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview)
- [Panoramica di Customer AI](https://experienceleague.adobe.com/it/docs/experience-platform/intelligent-services/customer-ai/overview)

### Governance dei dati e consenso

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home)
- [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Gestire l’elenco di soppressione](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Guardrail

- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/get-started/guardrails)
- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)
- [Guardrail del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/guardrails)
