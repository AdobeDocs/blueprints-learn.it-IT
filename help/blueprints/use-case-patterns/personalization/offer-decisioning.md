---
title: Offer Decisioning
description: Scopri come utilizzare la logica decisionale centralizzata per selezionare l’offerta o il contenuto migliore per un profilo tra canali diversi.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '7889'
ht-degree: 2%

---


# Offer Decisioning

Questa guida fornisce un riferimento completo all&#39;implementazione per offer decisioning utilizzando [!DNL Adobe Journey Optimizer] (AJO) Decisioning e [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP). È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono implementare una logica di selezione dell’offerta centralizzata che determini l’offerta migliore per ogni profilo cliente su tutti i canali.

Utilizza questa guida per capire cosa deve essere configurato, dove esistono opzioni e quali compromessi si applicano a ciascuna decisione.

Il modello separa la decisione &quot;cosa mostrare&quot; dalla logica del canale &quot;dove mostrarlo&quot;, consentendo una selezione dell’offerta coerente e ottimizzata su e-mail, web, app mobile e qualsiasi altro punto di contatto. AJO Decisioning gestisce l’intero ciclo di vita delle offerte: creazione di offerte e gestione del catalogo, regole di idoneità (chi può vedere ogni offerta), strategie di classificazione (come selezionare tra le offerte idonee), posizionamenti (dove vengono visualizzate le offerte) e criteri decisionali (che associano tutto).

## Panoramica del caso d’uso

Le organizzazioni devono spesso presentare a ciascun cliente l’offerta, la promozione o l’incentivo più pertinente al momento dell’interazione. Che l’interazione si verifichi in una campagna e-mail, su una home page del sito web, all’interno di un’app mobile o in un punto decisionale all’interno di un percorso in più passaggi, la sfida è la stessa: seleziona l’offerta ottimale da un catalogo di opzioni disponibili in base a chi sia il cliente, a cosa si qualifica e a quale offerta è più probabile che generi il risultato desiderato.

Offer Decisioning affronta questo problema centralizzando tutta la logica di selezione delle offerte nel motore di gestione delle decisioni di AJO. Invece di suddividere le assegnazioni delle offerte in singole campagne o canali, il motore decisionale valuta gli attributi di ciascun profilo, l’appartenenza al pubblico e i segnali contestuali per determinare l’offerta migliore in tempo reale. Questa centralizzazione assicura che lo stesso cliente riceva offerte coerenti e ottimizzate indipendentemente dal canale attraverso cui interagisce.

Questo modello si differenzia dalla personalizzazione web/app per visitatore noto per quanto riguarda l’ambito: le decisioni sull’offerta sono indipendenti dal canale e centralizzate, mentre la personalizzazione dei visitatori noti si concentra sulla personalizzazione della superficie digitale. Differisce dalla raccomandazione comportamentale in approccio: Offer Decisioning utilizza regole di idoneità esplicite e strategie di classificazione, mentre la raccomandazione comportamentale enfatizza le raccomandazioni basate sul segnale comportamentale utilizzando strategie di selezione e modelli di apprendimento automatico.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

**[Distribuisci esperienze cliente personalizzate](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
Personalizza contenuti, offerte e messaggi in base a preferenze, comportamenti e fasi del ciclo di vita individuali.
**KPI:** coinvolgimento, tassi di conversione, soddisfazione cliente (CSAT)

**[Incrementa le vendite incrociate e incrementa i ricavi](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
Promuovere prodotti o servizi complementari e di alta qualità ai clienti esistenti in base al comportamento e alla cronologia degli acquisti.
**KPI:** % vendite incrociate/upselling, ricavi incrementali, valore ciclo di vita cliente

**[Aumenta la fedeltà dei clienti e il valore del ciclo di vita](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
Approfondisci le relazioni con i clienti e massimizza il valore a lungo termine tramite programmi di fidelizzazione, premi e coinvolgimento personalizzato.
**KPI:** valore ciclo di vita cliente, conservazione, upselling/cross-selling %

## Esempi di casi d’uso tattici

Gli scenari seguenti illustrano come è possibile applicare in pratica Offer Decisioning.

- Proposta di acquisto successiva nelle campagne e-mail: seleziona la promozione più pertinente per destinatario al momento dell’invio
- Banner promozionale in tempo reale sul sito web: il processo decisionale seleziona l’offerta al caricamento della pagina in base al profilo del visitatore
- Scheda in-app personalizzata con il miglior incentivo per la fase del ciclo di vita dell’utente
- Coerenza delle offerte cross-channel: la stessa logica decisionale viene utilizzata per e-mail, web e push, in modo che il cliente possa vedere un’esperienza di offerta unificata
- Selezione dinamica di coupon o sconti in base al livello di valore del cliente (ad esempio, i clienti di valore elevato ricevono un’offerta premium)
- Aggiornamento del prodotto o selezione di offerte di upselling in base al livello di abbonamento corrente
- Personalizzazione delle offerte di fidelizzazione e premio in base alla cronologia dei livelli e delle attività

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare l’efficacia di un’implementazione di Offer Decisioning.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Tasso di accettazione offerta | Percentuale di offerte consegnate che risultano in un clic, un rimborso o una conversione | Clic o rimborsi offerta / Totale offerte consegnate |
| Distribuzione selezione offerta | Percentuale di ogni offerta selezionata in tutte le decisioni | Conteggio per offerta / Totale decisioni sottoposte a rendering |
| Percentuale di fallback | Percentuale di decisioni in cui non è stata soddisfatta alcuna offerta personalizzata ed è stato distribuito il fallback | Impression di fallback / Decisioni totali |
| Tasso di conversione | Percentuale di destinatari dell’offerta che hanno completato l’azione desiderata (acquisto, iscrizione, rimborso) | Conversioni / Impression offerta |
| Reddito Incrementale | Ricavi attribuibili alle offerte selezionate dal decisioning rispetto a un gruppo di controllo o a un fallback | Ricavi da offerte personalizzate: ricavi da fallback/controllo |
| Punteggio di coerenza cross-channel | Percentuale di profili che ricevono la stessa offerta su più canali all’interno di una finestra definita | Offerte coerenti/impression multicanale totali |
| Percentuale di click-through offerta | Percentuale di impression dell’offerta che danno luogo a un clic | Clic sull’offerta/Impression dell’offerta |

## Schema del caso d’uso

Questa sezione descrive la catena di funzioni e la definizione del modello per offer decisioning.

**Offer Decisioning**

Utilizza la logica decisionale centralizzata per selezionare l’offerta o il contenuto migliore per un profilo tra canali diversi.

**Catena di funzioni:** Valutazione del pubblico > Idoneità offerta > Strategia di classificazione > Esecuzione delle decisioni > Consegna > Generazione rapporti

Consulta la sezione [Opzioni di implementazione](#implementation-options) per informazioni sulla modalità di visualizzazione di ciascuna composizione.

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni Adobe.

- **[!DNL Adobe Journey Optimizer] (AJO)** — Motore di gestione delle decisioni per la creazione di offerte, regole di idoneità, strategie di classificazione, posizionamenti e criteri di decisione; configurazione dei canali e authoring dei messaggi per la consegna delle offerte; esecuzione di campagne e percorsi
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Valutazione del pubblico per i segmenti di idoneità delle offerte; dati di profilo e attributi calcolati utilizzati nell&#39;idoneità e nella classificazione
- **[!DNL Adobe Experience Platform] (AEP)**: archivio profili unificato, risoluzione identità e base dati che supportano sia AJO che RT-CDP

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve essere al suo posto | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Presunto sul posto | Sandbox di AJO con autorizzazioni Decisioning abilitate. Ruoli di gestione delle offerte (Responsabile delle decisioni, Approvatore offerte) assegnati al team di implementazione. | [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home), [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/it/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Obbligatorio | Lo schema del profilo deve includere gli attributi utilizzati per le regole di idoneità delle offerte (ad esempio, livello fedeltà, cronologia acquisti, tipo di abbonamento). Deve essere presente uno schema di risposta/interazione dell’offerta per monitorare impression, clic e conversioni delle offerte. | [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home), [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/schema/composition) |
| Origini dati e raccolta | Presunto sul posto | Gli attributi di profilo utilizzati nelle regole di idoneità devono essere correnti. Per la distribuzione web (opzione B), il Web SDK deve essere implementato con il servizio AJO abilitato sullo stream di dati. Per la consegna e-mail, gli attributi del profilo devono essere risolvibili al momento dell’invio. | [Panoramica di Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/home), [Configurare gli stream di dati](https://experienceleague.adobe.com/it/docs/experience-platform/datastreams/configure) |
| Configurazione identità e profilo | Presunto sul posto | I profili devono essere risolvibili su tutti i canali in cui vengono distribuite le offerte. Per la coerenza delle offerte cross-channel, l’identità unificata è fondamentale: lo stesso profilo deve essere riconosciuto nei contesti e-mail, web e mobili. Per la distribuzione Web/app in tempo reale è necessario un criterio di unione attivo per Edge. | [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home), [Panoramica dei criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview) |
| Definizione e segmentazione del pubblico | Obbligatorio | I tipi di pubblico utilizzati come criteri di idoneità per le offerte devono essere definiti e valutati (ad esempio, &quot;clienti di alto valore&quot;, &quot;utenti di prova&quot;, &quot;livello oro fedeltà&quot;). Il metodo di valutazione deve corrispondere alla latenza di consegna — valutazione Edge per web/app in tempo reale, batch o streaming per campagne e-mail. | [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home), [Guida dell&#39;interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Consigliato | I punteggi di propensione di IA per l’analisi dei clienti, i calcoli del valore del ciclo di vita e le metriche di coinvolgimento migliorano in modo significativo l’efficacia della strategia di classificazione. Attributi calcolati come &quot;giorni dall’ultimo acquisto&quot; o &quot;spesa totale in 90 giorni&quot; consentono regole di idoneità più precise e una classificazione basata su formule. | [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview), [Panoramica di IA per l&#39;analisi dei clienti](https://experienceleague.adobe.com/it/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Data Lifecycle Management | Consigliato | La cronologia delle offerte e i dati dell’evento decisionale si accumulano nel tempo. I criteri di conservazione (scadenza) devono essere configurati in modo da offrire set di dati evento di interazione per gestire lo storage e rispettare i requisiti di conservazione dei dati. | [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/it/docs/experience-platform/data-lifecycle/home), [Scadenze set di dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| Etichettatura e applicazione dell’utilizzo dati | Consigliato | Le etichette di governance garantiscono che le offerte con criteri di targeting sensibili (ad esempio, stato finanziario, condizioni di salute) siano conformi ai criteri di utilizzo dei dati. Le etichette sui campi utilizzati nelle regole di idoneità impediscono il targeting delle offerte non conformi. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home), [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview) |
| Monitoraggio e osservabilità | Consigliato | Devono essere monitorate le prestazioni del motore decisionale, i tassi di fallback e lo stato di consegna dell’offerta. Gli avvisi per tassi di fallback elevati possono indicare errori di configurazione delle regole di idoneità o problemi di aggiornamento dei dati. | [Panoramica avvisi](https://experienceleague.adobe.com/it/docs/experience-platform/observability/alerts/overview), [Panoramica approfondimenti osservabilità](https://experienceleague.adobe.com/it/docs/experience-platform/observability/home) |
| Reporting e analisi | Incluso | Il reporting sulle prestazioni delle offerte fa parte della catena di funzioni (fase 7). L’analisi CJA consente la misurazione dell’efficacia delle offerte cross-channel, l’attribuzione dell’impatto sui ricavi e l’identificazione delle opportunità di ottimizzazione. | [Panoramica di CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-overview/cja-overview), [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/home) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Journey Optimizer] (AJO)

Nella tabella seguente sono elencate le funzioni di AJO e le fasi di implementazione in cui sono configurate.

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Decisioni | Fase 3: Impostazione del processo decisionale | Creare elementi di offerta, definire regole di idoneità, configurare strategie di classificazione, creare offerte di fallback, definire posizionamenti e creare criteri decisionali |
| Configurazione canali | Fase 4: configurazione di canali e superfici | Configurare superfici di canale basate su e-mail, web, in-app o codice per la consegna delle offerte |
| Authoring dei messaggi | Fase 5: configurazione di contenuto e consegna | Progetta modelli di messaggio con aree di posizionamento dell’offerta; configura esperienze basate su codice per la consegna web/app |
| Esecuzione della campagna | Fase 5: configurazione di contenuto e consegna | Eseguire campagne pianificate o attivate da API che richiamano i criteri di decisione (opzione A) |
| Sperimentazione sui contenuti | Fase 5: configurazione di contenuto e consegna | Facoltativamente, testa A/B diverse strategie di classificazione o offri varianti creative |
| Reporting e analisi delle prestazioni | Fase 7: reporting e monitoraggio delle prestazioni | Monitorare la distribuzione della selezione delle offerte, le percentuali di accettazione, le percentuali di fallback e le prestazioni a livello di canale |

### [!DNL Real-Time CDP] (RT-CDP)

Nella tabella seguente sono elencate le funzioni RT-CDP e le fasi di implementazione in cui sono configurate.

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Valutazione del pubblico | Fase 2: Valutazione del pubblico | Definisci e valuta i tipi di pubblico utilizzati per le regole di idoneità delle offerte; seleziona il metodo di valutazione appropriato (batch, streaming o edge) |
| Arricchimento del profilo | Fase 1 (supporto): Attributi calcolati | Arricchire i profili con attributi calcolati e punteggi di propensione che migliorano l’efficacia della strategia di classificazione |

## Prerequisiti

Completa i seguenti prerequisiti prima di iniziare l’implementazione.

- [ Sandbox AJO ] con funzionalità di gestione delle decisioni abilitate
- [ ] Ruoli utente con autorizzazioni di Gestione delle decisioni (crea/modifica offerte, posizionamenti, decisioni)
- [ Lo schema del profilo ] include gli attributi necessari per l&#39;idoneità dell&#39;offerta (ad esempio, livello fedeltà, segmento cliente, livello di abbonamento)
- [ I dati del profilo ] sono correnti e vengono acquisiti attivamente per l&#39;aggiornamento degli attributi di idoneità
- [ ] per l&#39;opzione A (e-mail): superficie del canale e-mail configurata con sottodominio verificato e pool IP riscaldato
- [ ] Per l&#39;opzione B (Web/App): Web SDK implementato con il servizio AJO abilitato nello stream di dati; criterio di unione edge-active configurato
- [ ] per l&#39;opzione C (Percorso): autorizzazioni dell&#39;area di lavoro del Percorso e configurazione di almeno un evento di ingresso del percorso o pubblico
- [ ] Risorse creative per offerte (immagini, copie, CTA) preparate per ogni combinazione di offerta e posizionamento
- [ ] contenuto offerta di fallback preparato per ogni posizionamento
- [ ] tipi di pubblico per le regole di idoneità delle offerte definiti e valutati in RT-CDP

## Opzioni di implementazione

Questa sezione descrive le opzioni di implementazione disponibili per offer decisioning. Ogni opzione offre un canale di consegna e un contesto del caso d’uso diversi.

### Opzione A: Decisioning delle offerte e-mail

Questa opzione è ideale per selezionare l’offerta migliore da includere nelle campagne e-mail in uscita: e-mail promozionali, personalizzazione newsletter, e-mail sul ciclo di vita con contenuto di offerta dinamico. La decisione viene presa al momento del rendering del messaggio per ogni destinatario.

#### Come funziona

I criteri di decisione vengono richiamati durante il rendering dei messaggi e-mail per selezionare l’offerta migliore per ogni destinatario. Il modello e-mail include un’area di posizionamento dell’offerta in cui il motore decisionale inserisce la rappresentazione del contenuto dell’offerta selezionata (immagine, HTML o testo). Al momento dell’invio, il motore di valuta il profilo di ciascun destinatario in base alle regole di idoneità per le offerte, applica la strategia di classificazione e incorpora il contenuto dell’offerta vincente nell’e-mail.

Questo approccio funziona sia con le campagne pianificate (valutate al momento dell’esecuzione della campagna) che con le e-mail incorporate nel percorso (valutate quando il profilo raggiunge il nodo dell’azione del messaggio). Il contenuto dell’offerta (immagine, titolo, copia del corpo e CTA) è personalizzato per destinatario in base al risultato della decisione.

#### Considerazioni chiave

- L’idoneità dell’offerta viene valutata al momento dell’invio utilizzando lo stato corrente del profilo
- La valutazione del pubblico in batch è sufficiente poiché le decisioni si verificano durante il rendering dei messaggi
- Ogni offerta richiede una rappresentazione del contenuto di HTML o immagini per il posizionamento dell’e-mail
- L’offerta di fallback deve contenere contenuti per ogni posizionamento e-mail utilizzato

#### Vantaggi

- Percorso di implementazione più semplice: utilizza la consegna e-mail standard per campagne o percorsi
- Nessun requisito SDK lato client
- Compatibile con l&#39;infrastruttura e-mail e le superfici di canale esistenti
- Supporta volumi di pubblico di grandi dimensioni tramite l’esecuzione di campagne in batch

#### Limitazioni

- La decisione viene presa al momento dell’invio; non può adattarsi al comportamento successivo all’invio
- Il contenuto dell’offerta è statico una volta consegnata l’e-mail (nessun aggiornamento in tempo reale)
- Limitato agli attributi di profilo disponibili nell’archivio profili hub (non edge)

#### Risorse di Experience League

- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Creare una campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

### Opzione B: Decisioning delle offerte in tempo reale per web/app

Questa opzione è ideale per la selezione delle offerte in tempo reale su pagine web o app mobili: banner promozionali per home page, widget di offerte sulla dashboard dell’account, schede di offerta in-app o qualsiasi superficie digitale in cui l’offerta deve essere selezionata al momento del caricamento della pagina o del rendering dello schermo.

#### Come funziona

I criteri di decisione vengono richiamati al caricamento della pagina o al rendering della schermata dell’app tramite la rete Edge Decisioning o esperienze basate su codice. Quando un visitatore carica una pagina, il Web SDK invia una richiesta ad Edge Network, che valuta il profilo Edge del visitatore in base alle regole di idoneità delle offerte e alle strategie di classificazione. L’offerta selezionata viene restituita nella risposta ed è sottoposta a rendering nel posizionamento configurato sulla superficie digitale.

Per esperienze basate su codice, l’applicazione recupera la risposta di decisione ed esegue il rendering del contenuto dell’offerta utilizzando una logica front-end personalizzata. Per le esperienze dei canali web, il canale web AJO può inserire il contenuto dell’offerta direttamente nella pagina utilizzando l’authoring visivo o basato su codice.

#### Considerazioni chiave

- Richiede l’implementazione di Web SDK o Mobile SDK con il servizio AJO abilitato per lo stream di dati
- Il criterio di unione attivo per Edge è richiesto per le ricerche di profilo in tempo reale
- I tipi di pubblico utilizzati per l’idoneità devono supportare la valutazione Edge (controlli degli attributi semplici e appartenenza ai segmenti)
- Le rappresentazioni di contenuto dell’offerta devono utilizzare formati JSON o URL immagine per il rendering lato client
- Per acquisire visualizzazioni e clic delle offerte, è necessario implementare il tracciamento delle impression

#### Vantaggi

- Selezione di offerte in tempo reale durante la sessione in base allo stato attuale del profilo del visitatore
- Latenza delle decisioni al secondo secondario tramite Edge Network
- Le offerte si adattano ai dati di profilo più recenti disponibili al perimetro
- Supporta il test A/B delle strategie di offerta tramite la sperimentazione dei contenuti

#### Limitazioni

- Richiede l’implementazione lato client di SDK (Web SDK o Mobile SDK)
- Il profilo Edge dispone di un sottoinsieme di attributi completi del profilo hub; regole di idoneità complesse potrebbero non essere valutate correttamente
- I segmenti di Edge hanno restrizioni di complessità delle regole di segmento (nessuna query di serie temporali)
- Richiede lo sviluppo front-end per il rendering personalizzato nelle esperienze basate su codice

#### Risorse di Experience League

- [Distribuire le offerte tramite l’API Edge Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Canale di esperienza basato su codice](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/code-based-experience/get-started-code-based)

### Opzione C: nodo di decisione del Percorso

Questa opzione è ideale per la selezione di offerte all’interno di un percorso con più passaggi: selezionare l’offerta migliore in un punto decisionale di un percorso di clienti, quindi distribuirla attraverso il nodo di azione successivo. Utilizzalo quando la decisione sull’offerta fa parte di un flusso di orchestrazione più ampio con attese, condizioni e più azioni messaggio.

#### Come funziona

I criteri di decisione vengono richiamati da un nodo di decisione all’interno di un’area di lavoro del percorso AJO. Quando un profilo raggiunge il nodo della decisione, il motore valuta l’idoneità e la classificazione delle offerte per selezionare l’offerta ottimale. L’offerta selezionata informa l’azione del messaggio successiva, che indica il contenuto dell’offerta da includere, il canale da utilizzare o il ramo di percorso da intraprendere in base al risultato dell’offerta.

Questo approccio consente percorsi adattivi in cui la decisione di offerta influenza le fasi successive del percorso. Ad esempio, un percorso potrebbe selezionare l’offerta migliore, consegnarla tramite e-mail, attendere il coinvolgimento e quindi inviare una notifica push se l’offerta non è stata aperta.

#### Considerazioni chiave

- Il percorso deve essere progettato con un nodo decisione seguito da uno o più nodi azione messaggio
- L’idoneità dell’offerta viene valutata utilizzando lo stato del profilo nel momento in cui questo raggiunge il nodo della decisione
- Passaggi di attesa percorsi tra la decisione e la consegna possono causare la modifica dello stato del profilo
- Può combinarsi con la diramazione del percorso per seguire percorsi diversi in base all’offerta selezionata

#### Vantaggi

- Integra la selezione delle offerte nei flussi di orchestrazione in più passaggi
- Abilita percorsi adattivi in cui la scelta dell’offerta influenza i passaggi successivi
- Supporta la consegna cross-channel all’interno dello stesso percorso (e-mail, push, SMS)
- Può combinarsi con condizioni di percorso per il tracciamento del coinvolgimento post-offerta

#### Limitazioni

- Configurazione più complessa rispetto alle decisioni sulle campagne autonome
- Si applicano limiti di velocità effettiva percorsi (velocità di ingresso di 5,000 profili al secondo)
- La decisione è associata al contesto del percorso. Le modifiche richiedono il controllo delle versioni del percorso
- È necessario ripubblicare il percorso per rendere effettivi gli aggiornamenti del catalogo delle offerte o dei criteri di decisione

#### Risorse di Experience League

- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Introduzione ai percorsi](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/journey)

### Confronto delle opzioni

La tabella seguente confronta le tre opzioni di implementazione tra i diversi criteri chiave.

| Criteri | Opzione A: decisioni e-mail | Opzione B: Web/app in tempo reale | Opzione C: nodo di decisione del Percorso |
| --- | --- | --- | --- |
| Ideale per | Campagne e-mail batch con selezione di offerte per destinatario | Banner di offerte in tempo reale su superfici Web/app | Selezione di offerte in percorsi orchestrati in più passaggi |
| Latenza di decisione | Al momento dell’invio (secondi per destinatario durante il rendering in batch) | Secondi secondari (Edge Network) | Esecuzione nodo di percorso (secondi) |
| Canale | E-mail | Superfici basate su codice, web app per dispositivi mobili | Qualsiasi canale (e-mail, push, SMS) all’interno del percorso |
| SDK richiesto | No | Sì (Web SDK o Mobile SDK) | No (per e-mail/push); Sì (se il canale web è un’azione di percorso) |
| Valutazione del pubblico | Batch o streaming | Edge | Batch, streaming o edge (a seconda della voce del percorso) |
| Ambito dati profilo | Profilo hub completo | Profilo Edge (sottoinsieme) | Profilo hub completo |
| Complessi | Bassa | Medium - Alta | Medio |
| Velocità effettiva | Elevato (volumi di campagne batch) | Alta (scala Edge Network) | Medium (si applicano limiti di velocità effettiva percorso) |

### Scegli l’opzione giusta

Utilizza le indicazioni seguenti per selezionare l’opzione di implementazione migliore per il tuo caso d’uso.

- **Scegli l&#39;opzione A** se il caso d&#39;uso principale è la selezione dell&#39;offerta migliore per destinatario nelle campagne e-mail in uscita e non è disponibile alcun SDK lato client. Si tratta del percorso di implementazione più semplice e funziona bene per e-mail promozionali, newsletter e campagne sul ciclo di vita.
- **Scegli l&#39;opzione B** se le offerte devono essere selezionate in tempo reale nel momento in cui un visitatore carica una pagina web o apre un&#39;app mobile. Questo richiede Web SDK o Mobile SDK e un criterio di unione attivo per Edge, ma offre la selezione dell’offerta più veloce e contestuale.
- **Scegliere l&#39;opzione C** se la decisione sull&#39;offerta fa parte di un percorso di clienti più ampio con più passaggi, attese e diramazioni condizionali. Questa è la scelta giusta quando l’offerta selezionata dovrebbe influenzare le azioni del percorso a valle o quando è necessario un follow-up multicanale basato sull’impegno dell’offerta.
- **Combina opzioni** quando le offerte devono essere consegnate in modo coerente tra i canali. Utilizza lo stesso criterio decisionale in tutte e tre le opzioni per garantire che un cliente veda la stessa offerta in un’e-mail (opzione A), sul sito web (opzione B) e nell’ambito di un follow-up percorso (opzione C).

## Fasi di implementazione

Le fasi seguenti descrivono la sequenza di implementazione end-to-end per Offer Decisioning.

### Fase 1: Convalida dei prerequisiti fondamentali

**Funzione applicazione:** AEP: modellazione e preparazione dati, AEP: configurazione identità e profilo

Questa fase verifica se il livello dati fondamentale supporta le decisioni sulle offerte. Gli schemi di profilo devono includere gli attributi utilizzati nelle regole di idoneità dell’offerta e la configurazione dell’identità deve abilitare la risoluzione del profilo cross-channel.

#### Decisione: Attributi del profilo per l’idoneità

Determina quali attributi di profilo verranno utilizzati nelle regole di idoneità delle offerte.

>[!NOTE]
>La scelta degli attributi di profilo influisce sia sulla progettazione delle regole di idoneità che sull’efficacia della strategia di classificazione. Considera gli attributi calcolati e i punteggi di tendenza per migliorare la qualità delle decisioni.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Attributi di profilo standard (livello fedeltà, cronologia acquisti) | Attributi già esistenti nello schema del profilo | Non sono necessarie modifiche allo schema; verifica l’aggiornamento dei dati |
| Attributi calcolati (valore del ciclo di vita, punteggio di coinvolgimento) | L’idoneità o la classificazione dipende dai dati comportamentali aggregati | Richiede la configurazione S1; aggiunge una dipendenza sulla frequenza di aggiornamento degli attributi calcolati |
| Punteggi di propensione di Customer AI | La classificazione deve sfruttare le previsioni basate sull’apprendimento automatico | Richiede dati di formazione sufficienti (oltre 10.000 profili con evento target); modellare i tempi di formazione |

#### Dettagli chiave della configurazione

- Verificare che lo schema del profilo includa i campi a cui si fa riferimento nelle regole di idoneità (ad esempio, `_tenantId.loyaltyTier`, `_tenantId.subscriptionType`)
- Conferma l’esistenza di uno schema di tracciamento dell’interazione dell’offerta per gli eventi di impression, clic e conversione
- Per l’opzione B: verifica che il criterio di unione edge-active sia configurato e che lo stream di dati Web SDK abbia il servizio AJO abilitato

#### Documentazione di Experience League

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home)
- [Abilitare uno schema per il profilo](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview)

### Fase 2: configurare la valutazione del pubblico

**Funzione applicazione:** RT-CDP: Audience Evaluation

Questa fase definisce e valuta i tipi di pubblico utilizzati come criteri di idoneità per le offerte. Questi tipi di pubblico determinano quali segmenti di clienti sono idonei per offerte specifiche (ad esempio, i &quot;clienti di alto valore&quot; si qualificano per le offerte premium, gli &quot;utenti di prova&quot; si qualificano per le offerte di conversione).

#### Decisione: metodo di valutazione del pubblico

Determina la rapidità con cui l’iscrizione al pubblico deve essere aggiornata per l’idoneità alle offerte.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Valutazione in batch | Opzione A (campagne e-mail) in cui l’idoneità viene valutata al momento dell’invio | Più semplice; sono supportate tutte le espressioni delle regole di segmento; aggiornamento giornaliero o su richiesta |
| Valutazione in streaming | Opzione A o C quando sono necessari aggiornamenti del pubblico in tempo quasi reale tra batch diversi | Automatico per i segmenti idonei; supporto limitato per le regole di segmento (eventi singoli, confronti di attributi) |
| Valutazione Edge | Opzione B (web/app in tempo reale) in cui l’idoneità deve essere valutata al caricamento della pagina | Sub-secondo; richiesto per le offerte web/app in tempo reale; limitato a semplici controlli degli attributi e appartenenza ai segmenti |

**Navigazione interfaccia utente:** Cliente > Tipi di pubblico > Crea pubblico > Genera regola

#### Dettagli chiave della configurazione

- Definisci i tipi di pubblico di targeting per l’idoneità delle offerte (ad esempio, &quot;Livello Gold fedeltà&quot;, &quot;Clienti di alto valore&quot;, &quot;Utenti di prova&quot;)
- Definisci i tipi di pubblico di eliminazione se necessario (ad esempio, &quot;Offerta X ricevuta di recente&quot;)
- Per l’opzione B: verificare che i tipi di pubblico di idoneità siano idonei per la valutazione Edge — evitare query di serie temporali e aggregazioni complesse nelle espressioni delle regole di segmento

#### Dove le opzioni divergono

**Per L&#39;Opzione A (Email Decisioning):**
È sufficiente la valutazione in batch o in streaming. I tipi di pubblico vengono valutati prima o durante l’esecuzione della campagna. Sono completamente supportate le espressioni di regole di segmento complesse, comprese le condizioni basate sul tempo e le aggregazioni di eventi.

**Per L&#39;Opzione B (Web/App In Tempo Reale):**
È necessaria la valutazione di Edge. I tipi di pubblico devono utilizzare semplici controlli degli attributi o condizioni di appartenenza ai segmenti. Verifica l’idoneità degli edge verificando che l’espressione della regola del segmento sia idonea alla segmentazione degli edge.

**Per L&#39;Opzione C (Nodo Di Decisione Percorso):**
Qualsiasi metodo di valutazione funziona in base ai criteri percorsi di immissione. Se il percorso utilizza una voce basata sul pubblico, il metodo di valutazione del pubblico corrisponde ai requisiti del percorso.

#### Documentazione di Experience League

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/edge-segmentation)

### Fase 3: Impostare il decisioning

**Funzione applicazione:** AJO: Decisioning

Questa è la fase principale in cui vengono generati il catalogo delle offerte, le regole di idoneità, le strategie di classificazione e i criteri decisionali. Questa fase crea la configurazione del motore decisionale che tutte le opzioni di consegna (A, B, C) condividono.

#### Decisione: canale di posizionamento e formato dei contenuti

Determina dove verranno visualizzate le offerte e in quale formato.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| E-mail (HTML) | Opzione A: contenuto dell’offerta sottoposto a rendering come HTML nel corpo dell’e-mail | Supporta la formattazione avanzata; deve essere compatibile con i client e-mail |
| E-mail (URL immagine) | Opzione A — Offerta sottoposta a rendering come immagine ospitata nelle e-mail | Più semplice; l’immagine deve essere ospitata e accessibile; nessun testo dinamico |
| Web (HTML) | Opzione B — offerta sottoposta a rendering come HTML su una pagina web | Controllo di layout completo; supporta gli elementi interattivi |
| Web/Mobile (JSON) | Opzione B — Dati dell’offerta restituiti come JSON per il rendering personalizzato | Massima flessibilità; richiede sviluppo front-end per il rendering |
| Basato su codice (JSON) | Opzione B — Dati dell&#39;offerta per superfici esperienza basate su codice | Rendering dei controlli dell&#39;applicazione; più flessibile |

#### Decisione: strategia di classificazione

Determina come deve essere selezionata l’offerta migliore dalle offerte idonee.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Basato su priorità (manuale) | Piccoli cataloghi di offerte; regole aziendali esplicite per l’ordinamento delle offerte | Configurazione più semplice; assegnazione manuale del valore di priorità per offerta; deterministico |
| Basato su formula (espressione personalizzata) | La classificazione deve considerare gli attributi del profilo (ad esempio, livello di fedeltà, aggiornamento) | Flessibile; utilizza i dati del profilo per calcolare un punteggio di classificazione; richiede la progettazione di espressioni della regola del segmento |
| Classificato in base all’intelligenza artificiale (ottimizzazione automatica) | Cataloghi di offerte di grandi dimensioni; vuoi che ML ottimizzi la selezione nel tempo | Richiede almeno 1.000 eventi di conversione per l’apprendimento dei modelli; apprende dai dati sulle prestazioni dell’offerta |

#### Decisione: limite dell’offerta

Determina se ci devono essere limiti sul numero di volte in cui viene visualizzata un’offerta.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Limite per profilo | Impedisci che la stessa offerta venga mostrata troppe volte a un cliente | Evita l&#39;affaticamento delle offerte; ritardo del contatore di alcuni secondi in scenari ad alta velocità |
| Limite globale | Limitare le impression totali per un’offerta su tutti i profili (ad esempio, inventario limitato) | Controlla la fornitura delle offerte; una volta raggiunto il limite, l’offerta viene esclusa dalle decisioni |
| Nessun limite | Disponibilità illimitata delle offerte | Più semplice; adatto per promozioni sempre attive |

**Navigazione interfaccia utente:** Componenti > Gestione decisioni > Posizionamenti / Regole / Offerte / Decisioni

#### Dettagli chiave della configurazione

1. **Crea posizionamenti** — consente di definire la posizione in cui vengono visualizzate le offerte specificando il tipo di canale e il formato di contenuto per ciascun posizionamento.
   - Interfaccia utente: Componenti > Gestione delle decisioni > Posizionamenti
   - Crea un posizionamento per ogni combinazione canale/formato (ad esempio, &quot;Email Hero Banner - HTML&quot;, &quot;Web Homepage - JSON&quot;, &quot;Mobile App Card - JSON&quot;)

2. **Definire le regole di idoneità** — Creare regole utilizzando espressioni della regola di segmento che fanno riferimento ad attributi di profilo o appartenenza a un pubblico.
   - Interfaccia utente: Componenti > Gestione delle decisioni > Regole
   - Le regole possono fare riferimento all’iscrizione al pubblico, agli attributi del profilo (livello di fedeltà, tipo di abbonamento), ai vincoli di data o ai dati contestuali

3. **Crea offerte personalizzate**: crea ogni offerta con rappresentazioni di contenuto per ogni posizionamento, assegna le regole di idoneità, imposta la priorità e configura il limite facoltativo.
   - Interfaccia utente: Componenti > Gestione delle decisioni > Offerte > Crea offerta
   - Ogni offerta richiede una rappresentazione del contenuto per posizionamento (ad esempio, HTML per e-mail, JSON per web)
   - Assegna regole di idoneità per controllare quali profili possono visualizzare ogni offerta
   - Impostare le date di validità dell’offerta (inizio/fine) e il limite di frequenza opzionale
   - Approva ogni offerta per renderla idonea alle decisioni

4. **Crea offerte di fallback**: crea un&#39;offerta predefinita per ogni posizionamento visualizzato quando non è idonea alcuna offerta personalizzata.
   - Interfaccia utente: Componenti > Gestione delle decisioni > Offerte > Crea offerta di fallback
   - Il fallback deve avere rappresentazioni per ogni posizionamento utilizzato nella decisione

5. **Creare qualificatori e raccolte della raccolta** — Organizzare le offerte in raccolte utilizzando tag qualificatori.
   - Interfaccia utente: Componenti > Gestione delle decisioni > Qualificatori di raccolta
   - Offerte relative al gruppo (ad esempio, &quot;Promozioni estive&quot;, &quot;Premi fedeltà&quot;) da utilizzare negli ambiti decisionali

6. **Creare criteri di decisione**: associa posizionamenti, raccolte, strategie di classificazione e offerte di fallback a decisioni eseguibili.
   - Interfaccia utente: Componenti > Gestione delle decisioni > Decisioni > Crea decisione
   - Ogni ambito decisionale collega un posizionamento a una raccolta e specifica il metodo di classificazione

#### Documentazione di Experience League

- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Creare i posizionamenti](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Creare regole di decisione](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Creare offerte di fallback](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Creare le raccolte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Creare qualificatori di raccolta](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Fase 4: configurare canale e superficie

**Funzione applicazione:** AJO: Configurazione canale

Questa fase configura le superfici di canale attraverso le quali verranno distribuite le offerte. La configurazione dipende dalle opzioni di implementazione utilizzate.

#### Decisione: tipo di canale

Determina quale canale di messaggistica richiede il caso d’uso.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| E-mail | Opzione A o Opzione C con consegna e-mail | Richiede la delega del sottodominio, il pool IP e le impostazioni del mittente |
| Web | Opzione B per la consegna della superficie web | Richiede la configurazione di Web SDK e dello stream di dati |
| In-app | Opzione B per la distribuzione di app per dispositivi mobili | Richiede Mobile SDK e credenziali push |
| Esperienza basata su codice | Opzione B per superfici di rendering personalizzate | Più flessibile; l&#39;applicazione gestisce il rendering |

#### Dove le opzioni divergono

**Per L&#39;Opzione A (Email Decisioning):**
- Interfaccia utente: Amministrazione > Canali > Superfici di canale > Crea superficie (e-mail)
- Configurare le impostazioni relative a sottodominio, pool IP, nome/e-mail del mittente, risposta e annullamento dell’abbonamento
- Verifica i record SPF, DKIM e DMARC per il sottodominio di invio

**Per L&#39;Opzione B (Web/App In Tempo Reale):**
- Interfaccia utente: Amministrazione > Canali > Superfici di canale > Crea superficie (web o in-app)
- Per il web: configura il pattern URL della superficie web
- Per esperienze basate su codice: definisci l’URI di superficie per l’applicazione
- Verifica che il servizio AJO sia abilitato per lo stream di dati

**Per L&#39;Opzione C (Nodo Di Decisione Percorso):**
- Configurare le superfici di canale per ciascun canale utilizzato nel percorso (e-mail, push, SMS o web)
- Ogni azione del messaggio di percorso richiede una superficie di canale attiva corrispondente

#### Documentazione di Experience League

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Impostazioni superficie e-mail](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delega sottodomini](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Fase 5: Configurare il contenuto e la consegna

**Funzione dell&#39;applicazione:** AJO: Message Authoring, AJO: Campaign Execution

Questa fase progetta i modelli di messaggio o le superfici di esperienza che visualizzano l’offerta selezionata, quindi configura il meccanismo di consegna (esperienza per campagna, percorso o basata su codice).

#### Decisione: approccio ai contenuti per il rendering delle offerte

Determina in che modo il contenuto dell’offerta deve essere integrato nel messaggio o nell’esperienza.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Componente decisione offerta in E-mail Designer | Opzione A - Inserimento del posizionamento dell’offerta nel modello e-mail | Trascinamento della selezione; il contenuto dell’offerta viene riprodotto automaticamente in base al risultato della decisione |
| Esperienza basata su codice con i criteri di decisione | Opzione B: l&#39;applicazione recupera ed esegue il rendering dei dati dell&#39;offerta | Massimo controllo sul rendering; richiede sviluppo front-end |
| Azione messaggio percorso con decisione incorporata | Opzione C: il contenuto dell’offerta viene trasmesso al messaggio del percorso tramite il nodo di decisione | La selezione e la consegna delle offerte sono orchestrate all’interno del flusso di percorso |

#### Decisione: tipo di campagna (solo opzione A)

Determina se si tratta di una campagna di marketing pianificata o di una campagna attivata da API.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Campagna pianificata | Invii in batch una tantum o ricorrenti a un pubblico definito | Pubblico valutato al momento dell’esecuzione; imposta data/ora o ricorrenza |
| Campagna attivata da API | Invii guidati da eventi o attivati dal sistema a profili specifici | Profili specificati nel payload del trigger; supporta fino a 20 destinatari per richiesta |

#### Dove le opzioni divergono

**Per L&#39;Opzione A (Email Decisioning):**

1. Creare il messaggio e-mail tramite E-mail Designer
   - Interfaccia utente: Campagne > Crea campagna > Seleziona e-mail > Modifica contenuto
   - Inserisci un componente decisione di offerta nel layout dell’e-mail per definire l’area di posizionamento
   - Aggiungere token di personalizzazione per il contenuto a livello di profilo (nome, livello fedeltà)
   - Configurare l’oggetto e il preintestazione con la personalizzazione facoltativa
2. Creare e configurare la campagna
   - Interfaccia utente: Campagne > Crea campagna > Pianificato o attivato da API
   - Associa il pubblico di destinazione e seleziona la superficie di canale
   - Impostare la pianificazione di esecuzione o la configurazione del trigger API
   - Rivedere e attivare la campagna

**Per L&#39;Opzione B (Web/App In Tempo Reale):**

1. Configurare l’esperienza basata su codice o il canale web
   - Interfaccia utente: Campagne > Crea campagna > Esperienza basata su codice (o Web)
   - Collegare il criterio di decisione alla superficie dell’esperienza
   - Definire il formato di rendering (risposta JSON per basato su codice; editor visivo per canale web)
2. Implementare il rendering lato client
   - Utilizza la risposta di Web SDK `sendEvent` per recuperare l&#39;offerta selezionata
   - Eseguire il rendering del contenuto dell’offerta nel posizionamento designato nella pagina
   - Implementare il tracciamento delle impression e dei clic

**Per L&#39;Opzione C (Nodo Di Decisione Percorso):**

1. Progettare il percorso con un nodo di decisione
   - Interfaccia utente: Percorsi > Crea Percorso > Aggiungi nodo di decisione
   - Configurare il nodo della decisione per richiamare il criterio di decisione dalla fase 3
2. Aggiungi nodi di azione del messaggio dopo la decisione
   - Configurare le azioni e-mail, push o SMS che fanno riferimento all’offerta selezionata
   - Aggiungi passaggi di attesa, condizioni o diramazioni in base al coinvolgimento dell’offerta
3. Pubblicare il percorso

#### Documentazione di Experience League

- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Creare una campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Introduzione ai percorsi](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Anteprima e test del contenuto](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Fase 6: Test e convalida

**Funzione dell&#39;applicazione:** AJO: Decisioning, AJO: Message Authoring

Questa fase verifica che il motore decisionale restituisca le offerte corrette per i profili di test e che il contenuto dell’offerta venga riprodotto correttamente in ogni canale di consegna.

#### Logica di test decisioning

Utilizza profili di test con attributi noti per verificare che le offerte corrette siano selezionate in base all’idoneità e alla classificazione.

- Crea profili di test che corrispondono a diversi criteri di idoneità (ad esempio, livello Gold, livello Silver, utente di prova)
- Verifica che ogni profilo di test riceva l’offerta prevista
- Verifica che i profili che non corrispondono a nessuna regola di idoneità ricevano l’offerta di fallback

#### Test del rendering del contenuto

Visualizza l’anteprima del contenuto dell’offerta in ogni canale di consegna.

- Per l’opzione A: utilizza l’anteprima e-mail con profili di test per verificare che il contenuto dell’offerta venga riprodotto correttamente
- Per l’opzione B: testare la risposta di Edge Decisioning in un ambiente di staging
- Per l’opzione C: utilizza la modalità di test percorso per verificare che il nodo decisionale selezioni correttamente

#### Convalidare il tracciamento delle impression

Verifica che vengano tracciate le impression, i clic e le conversioni delle offerte.

- Verificare che gli eventi di interazione dell’offerta vengano visualizzati nei set di dati di tracciamento
- Conferma l’attribuzione tra le impression dell’offerta e le conversioni a valle

#### Documentazione di Experience League

- [Anteprima e test del contenuto](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Inviare bozze e-mail](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/preview-test/proofs)

### Fase 7: configurare la generazione di rapporti e il monitoraggio delle prestazioni

**Funzione applicazione:** AJO: Reporting e analisi delle prestazioni

Questa fase imposta la generazione di rapporti per tenere traccia della distribuzione della selezione delle offerte, dei tassi di accettazione, dell’impatto sulla conversione e dei tassi di fallback. Questa fase tratta sia i rapporti nativi di AJO che l’analisi cross-channel basata su CJA.

#### Decisione: metodo di comunicazione

Determina quali strumenti di reporting sono necessari per l’analisi delle prestazioni delle offerte.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo rapporti nativi di AJO | Monitoraggio operativo di singole campagne o percorsi | Accesso rapido; metriche integrate di consegna e coinvolgimento; analisi limitata tra più entità |
| analisi dell’area di lavoro CJA | Efficacia delle offerte cross-channel, attribuzione dei ricavi, analisi funnel | Richiede connessione CJA e visualizzazione dati; funzionalità di analisi più approfondite |
| Sia AJO che CJA | Piena copertura operativa e analitica | Consigliato per implementazioni di produzione; AJO per monitoraggio in tempo reale, CJA per analisi strategiche |

#### Dettagli chiave della configurazione

1. **Rapporti nativi di AJO**: monitora le prestazioni della campagna o del percorso utilizzando i rapporti incorporati.
   - Interfaccia utente: Campagne > Seleziona campagna > Rapporto Tutti i tempi (o Rapporto live)
   - Rivedi metriche specifiche per l’offerta: impression per offerta, tasso di click-through per offerta, tasso di fallback
   - Monitora la consegna funnel: Target > Inviato > Consegnato > Aperture > Clic

2. **Analisi CJA (consigliata)**: creazione di dashboard delle prestazioni delle offerte cross-channel.
   - Configurare una connessione CJA con i set di dati di interazione dell’offerta AJO
   - Creare una visualizzazione dati con dimensioni specifiche per l’offerta (nome dell’offerta, posizionamento, decisione) e metriche (impression, clic, conversioni)
   - Crea un’analisi dell’area di lavoro per: distribuzione della selezione delle offerte, tasso di accettazione per segmento, impatto sui ricavi, coerenza delle offerte cross-channel

#### Documentazione di Experience League

- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/home)

## Considerazioni sull’implementazione

Questa sezione descrive guardrail, insidie comuni, best practice e decisioni di compromesso per le implementazioni di Offer Decisioning.

### Guardrail e limiti

Quando pianifichi l’implementazione, tieni presenti i seguenti guardrail e limiti della piattaforma.

- Massimo 10.000 offerte personalizzate approvate per sandbox — [Guardrail di gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/get-started/guardrails)
- Massimo 30 posizionamenti per decisione
- Massimo 30 ambiti di raccolta per richiesta di decisione
- I modelli di classificazione IA richiedono almeno 1.000 eventi di conversione per la formazione
- I contatori di limite delle offerte possono presentare un ritardo di alcuni secondi in scenari ad alto throughput
- Le decisioni di Edge sono limitate agli attributi di profilo disponibili nell’archivio profili edge
- Massimo 4.000 definizioni di segmenti per sandbox: [guardrail della piattaforma](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)
- In Edge può essere attivo un solo criterio di unione per sandbox
- Massimo 500 campagne live attive per sandbox
- Limite velocità di ingresso percorso: 5.000 profili al secondo
- Massimo 10 superfici di canale per tipo di canale per sandbox

### Insidie comuni

Evita questi problemi che si verificano di frequente durante l’implementazione.

- **La decisione restituisce sempre l&#39;offerta di fallback:** In genere significa che le offerte personalizzate non sono approvate, non rientrano nel loro intervallo di date di validità o che le regole di idoneità non corrispondono agli attributi del profilo di test. Verifica ciascuna condizione: stato di approvazione, intervallo di date e precisione delle espressioni della regola del segmento. Verifica inoltre che i limiti di limitazione non siano stati raggiunti.
- **Offerta non visualizzata nella raccolta:** Assicurarsi che all&#39;offerta sia stato applicato il tag con il qualificatore di raccolta corretto e che il filtro di raccolta corrisponda. Per poter essere visualizzate negli ambiti decisionali basati sulla raccolta, le offerte devono essere taggate e approvate.
- **Formula di classificazione non applicata:** Verificare che la formula sia sintatticamente valida e faccia riferimento ad attributi di profilo accessibili. Gli errori di formula tornano automaticamente alla classificazione basata sulla priorità senza errori visibili.
- **La consegna di Edge restituisce una personalizzazione vuota:** Verificare che lo stream di dati sia configurato con il servizio [!DNL Adobe Journey Optimizer] abilitato e che l&#39;ambito della decisione sia formattato correttamente. Verifica che esista il criterio di unione attivo per Edge.
- **Offerte non coerenti tra i canali:** Se vengono utilizzati criteri di decisione separati per canale, lo stesso profilo potrebbe ricevere offerte diverse. Utilizza un singolo criterio decisionale tra i canali per coerenza o accetta divergenze intenzionali in base a posizionamenti specifici per canale.
- **Impossibile eseguire il rendering del contenuto dell&#39;offerta nell&#39;e-mail:** Verificare che l&#39;offerta includa una rappresentazione del contenuto corrispondente al formato di posizionamento dell&#39;e-mail (HTML o URL immagine). Le rappresentazioni mancanti generano zone di posizionamento vuote.

### Best practice

Segui queste raccomandazioni per un’implementazione corretta di Offer Decisioning.

- **Inizia con un piccolo catalogo di offerte ed esegui iterazione**. Inizia con 5-10 offerte ed espandile man mano che il framework decisionale viene convalidato. Questo semplifica la risoluzione dei problemi e garantisce il corretto funzionamento delle regole di idoneità prima della scalabilità.
- **Utilizzare i qualificatori di raccolta in modo strategico**. Assegnare tag alle offerte per categoria (ad esempio, &quot;Acquisizione&quot;, &quot;Mantenimento&quot;, &quot;Upselling&quot;) per abilitare ambiti decisionali flessibili basati sulla raccolta che possono essere riutilizzati in campagne e percorsi.
- **Crea sempre offerte di fallback significative** — Le offerte di fallback non sono solo una rete di sicurezza; sono l&#39;esperienza predefinita per i profili che non corrispondono ad alcuna regola di idoneità. Investire in contenuti di fallback che offrano valore anche senza personalizzazione.
- **Progettare le regole di idoneità in modo che si escludano a vicenda, ove possibile**: quando più offerte hanno idoneità sovrapposte, la strategia di classificazione diventa critica. Se i requisiti aziendali impongono un’offerta specifica per un segmento specifico, fai in modo che le regole di idoneità si escludano a vicenda, anziché affidarsi esclusivamente alla classificazione.
- **Test con profili rappresentativi di Edge per l&#39;opzione B**. I profili Edge contengono un sottoinsieme di attributi di profilo hub. Esegui il test con profili con attributi Edge disponibili per garantire che l’idoneità venga valutata correttamente in produzione.
- **Monitorare le percentuali di fallback come metrica di integrità**. Una percentuale elevata di fallback (superiore al 20-30%) indica che il catalogo delle offerte non copre un numero sufficiente di segmenti di clienti. Espandi il catalogo delle offerte o amplia le regole di idoneità.
- **Versione dei criteri di decisione anziché modificare quelli attivi** — Creare una nuova versione dei criteri di decisione anziché modificarne una attiva. Questo impedisce l’interruzione delle campagne live e consente un confronto A/B delle strategie decisionali.

### Decisioni di compromesso

Quando prendi decisioni su architettura e configurazione, considera i seguenti compromessi.

#### Precisione dell’idoneità rispetto alla copertura dell’offerta

Regole di idoneità rigide garantiscono che ogni offerta raggiunga solo i profili più rilevanti, ma possono causare tassi di fallback elevati quando i profili non corrispondono a nessuna offerta. Le ampie regole di idoneità massimizzano la copertura delle offerte ma riducono la precisione della personalizzazione.

- **Privilegi limitati per l&#39;idoneità:** Tassi di accettazione più elevati, migliore personalizzazione, minore affaticamento delle offerte
- **Ampi favori di idoneità:** tassi di fallback inferiori, più profili ricevono offerte personalizzate, gestione più semplice delle regole
- **Consiglio:** inizia con regole di idoneità più ampie e le inasprisce in base ai dati sulle prestazioni. Monitora i tassi di fallback e i tassi di accettazione per trovare il giusto equilibrio. Utilizza le strategie di classificazione per differenziare le offerte ampiamente idonee.

#### Classificazione basata su priorità e classificazione basata su IA

La classificazione basata su priorità offre all’azienda il pieno controllo su quali offerte vengono visualizzate, mentre la classificazione basata su IA ottimizza la conversione ma riduce il controllo umano sulla selezione delle offerte.

- **Preferenze basate su priorità:** Controllo aziendale, prevedibilità, nessun requisito di dati di formazione, distribuzione immediata
- **Preferenze basate sull&#39;intelligenza artificiale:** Ottimizzazione della conversione, individuazione di pattern imprevisti, adattamento automatico al comportamento del cliente in continua evoluzione
- **Consiglio:** utilizza la classificazione basata sulla priorità per i lanci iniziali e le offerte soggette a normative in cui il controllo aziendale è fondamentale. Transizione verso una classificazione basata sull’intelligenza artificiale per casi d’uso di volume elevato e ottimizzati per le prestazioni, una volta disponibili dati di conversione sufficienti (oltre 1.000 eventi).

#### Criteri decisionali singoli e criteri decisionali per singolo canale

Un unico criterio decisionale garantisce la coerenza dell’offerta su tutti i canali, ma limita l’ottimizzazione per canale. I criteri per canale consentono la classificazione specifica per il canale e l’idoneità, ma rischiano di causare esperienze cliente incoerenti.

- **Un singolo criterio favorisce:** coerenza cross-channel, gestione semplificata, reporting unificato
- **I criteri per canale favoriscono:** classificazione ottimizzata per il canale, idoneità specifica per il canale (ad esempio, offerte solo web), iterazione indipendente
- **Consiglio:** inizia con un singolo criterio di decisione per coerenza tra canali diversi. Crea criteri per canale solo quando i requisiti aziendali richiedono strategie di offerta specifiche per canale (ad esempio, vendite flash esclusive per il web).

#### Decisioning hub (opzione A/C) e Edge Decisioning (opzione B)

Le decisioni dell’hub hanno accesso al profilo completo, ma funzionano al momento dell’invio. Edge Decisioning funziona in tempo reale con latenza al secondo secondario, ma è limitato agli attributi di profilo disponibili all’edge.

- **Il decisioning dell&#39;hub favorisce:** accesso ai dati del profilo completo, regole di idoneità complesse, volumi di campagne batch
- **Il decisioning di Edge favorisce:** Contesto in tempo reale, personalizzazione nella sessione, risposta al secondo secondario
- **Consiglio:** utilizza le decisioni hub per i canali in uscita (e-mail, push) in cui i dati di profilo completi migliorano la rilevanza dell&#39;offerta. Utilizza le decisioni edge per i canali in entrata (web, app) in cui la risposta in tempo reale è fondamentale. Assicurati che le regole di idoneità per Edge utilizzino solo attributi disponibili Edge.

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sui componenti utilizzati in questo modello di caso d’uso.

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

### Consegna delle offerte

- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Distribuire le offerte tramite l’API Edge Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Distribuire le offerte tramite l’API Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/decisioning-api)

### Configurazione dei canali

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Impostazioni superficie e-mail](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delega sottodomini](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Configurare il canale SMS](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### Authoring e personalizzazione dei messaggi

- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Anteprima e test del contenuto](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Campagne e percorsi

- [Introduzione alle campagne](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Creare una campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Introduzione ai percorsi](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/journey)

### Sperimentazione sui contenuti

- [Introduzione all’esperimento sui contenuti](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Creare un esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### Tipi di pubblico e segmentazione

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/edge-segmentation)

### Profilo e identità

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview)
- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview)
- [Panoramica di Customer AI](https://experienceleague.adobe.com/it/docs/experience-platform/intelligent-services/customer-ai/overview)

### Modellazione e raccolta dati

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home)
- [Panoramica di Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/home)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/it/docs/experience-platform/datastreams/configure)

### Reporting e analisi

- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Panoramica di CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-overview/cja-overview)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/home)

### Governance dei dati e ciclo di vita

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home)
- [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview)
- [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/it/docs/experience-platform/data-lifecycle/home)
- [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Guardrail

- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/get-started/guardrails)
- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)

### Tutorial

- [Guida introduttiva all’API di gestione delle decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/getting-started)
