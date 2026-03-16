---
title: Attivazione messaggi in uscita in batch
description: Scopri come valutare un pubblico e consegnare un messaggio in uscita pianificato in un’esecuzione batch singola.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '8246'
ht-degree: 1%

---


# Attivazione di messaggi in batch in uscita

Questa guida fornisce un riferimento completo all&#39;implementazione per la distribuzione di messaggi pianificati in uscita ai segmenti di pubblico definiti tramite [!DNL Adobe Journey Optimizer] (AJO) e [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP). È progettato per architetti di soluzioni, tecnici di marketing e ingegneri di implementazione che devono comprendere tutti gli approcci di implementazione validi, le considerazioni decisionali che guidano ogni scelta e dove trovare la documentazione dettagliata su [!DNL Adobe Experience League].

L’attivazione batch dei messaggi in uscita è il pattern di campagna fondamentale per la messaggistica in uscita uno-a-molti. Copre l’intero ciclo di vita, dalla definizione del pubblico alla consegna dei messaggi e all’analisi delle prestazioni. Questa guida presenta tre opzioni di implementazione: Scheduled Campaign, Audience-Triggered Percorsi e API-Triggered Campaign e fornisce indicazioni decisionali strutturate per selezionare l’approccio corretto per ogni caso d’uso.

Fornisce opzioni di implementazione, analisi di compromesso, percorsi di navigazione dell&#39;interfaccia utente e riferimenti alla documentazione [!DNL Experience League].

## Panoramica del caso d’uso

Le organizzazioni spesso devono inviare un singolo messaggio a un segmento di pubblico noto in un momento specifico o in risposta a un evento di sistema. Questo modello soddisfa tale requisito combinando la valutazione del pubblico in [!DNL RT-CDP] con la creazione dei messaggi e l&#39;esecuzione della campagna in [!DNL Journey Optimizer].

Lo scenario aziendale è semplice: definisci chi deve ricevere il messaggio, creane il contenuto con la personalizzazione, associa il pubblico e il messaggio in una campagna o in un percorso ed esegui l’invio secondo una pianificazione, tramite la qualificazione del pubblico o un attivatore di sistema. Il risultato è un messaggio consegnato con reporting completo sulle metriche di consegna, coinvolgimento e conversione.

Questo modello si applica ogni volta che un obiettivo di business può essere avanzato distribuendo un singolo messaggio a un pubblico noto in un’unica esecuzione. Si differenzia dalla messaggistica attivata dagli eventi, che risponde agli eventi comportamentali in tempo reale, e dai percorsi orchestrati in più passaggi, che guidano i profili attraverso più punti di contatto nel tempo. L’attivazione in batch è il modello di campagna più semplice e il punto di partenza più comune per i casi di utilizzo dei messaggi in uscita.

## Obiettivi aziendali chiave

Questa sezione identifica gli obiettivi aziendali principali supportati dall&#39;attivazione in batch dei messaggi in uscita.

### Aumentare il coinvolgimento nelle e-mail e nelle campagne

**Descrizione:** migliora i tassi di apertura, i tassi di click-through e la risposta complessiva alla campagna tramite contenuto ottimizzato e targeting.

**KPI:** tassi aperti, coinvolgimento, tassi di conversione

### Aumento dei ricavi e delle vendite

**Descrizione:** incrementa i ricavi principali tramite canali digitali ottimizzati, campagne e percorsi di clienti.

**KPI:** Tassi di conversione, Ricavi incrementali, Valore medio ordine

**Obiettivo aziendale correlato:** [Aumento ricavi e vendite](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

### Semplificare l’esecuzione della campagna

**Descrizione:** riduci il tempo di creazione delle campagne e semplifica la distribuzione di campagne multicanale tramite modelli, automazione e processi standardizzati.

**KPI:** Velocità al mercato, efficienza, completamento puntuale %

## Esempi di casi d’uso tattici

Gli scenari seguenti illustrano le applicazioni comuni dell’attivazione batch dei messaggi in uscita.

- **Annuncio di vendita o messaggio e-mail promozionale** — Trasmetti un&#39;offerta promozionale a un segmento di clienti idonei in una data pianificata
- **Notifica push di lancio del prodotto** — Notifica ai clienti interessati la disponibilità di un nuovo prodotto tramite push
- **Newsletter o e-mail di riepilogo** - Distribuisci periodicamente aggiornamenti dei contenuti ai tipi di pubblico degli abbonati
- **Invito alla registrazione dell&#39;evento** - Invita potenziali clienti qualificati a webinar, conferenze o eventi di persona
- **E-mail di promemoria per il rinnovo dell&#39;abbonamento** — Ricorda ai clienti che si avvicinano alle date di rinnovo di intervenire
- **Notifica milestone programma fedeltà** — Congratularsi con i membri che hanno raggiunto livelli fedeltà o soglie di punti
- **E-mail call-to-action specifica** — Consente di eseguire un&#39;azione mirata come il completamento di un acquisto, l&#39;aggiornamento delle preferenze o la registrazione a un programma
- **Campagna SMS per vendita flash o offerta limitata nel tempo**: invia promozioni urgenti e limitate nel tempo tramite SMS al pubblico che ha acconsentito

## Indicatori chiave di prestazioni

La tabella seguente definisce i KPI utilizzati per misurare l’efficacia della campagna.

| KPI | Descrizione | Metodo di misurazione |
| --- | --- | --- |
| Percentuale di consegna | Percentuale di messaggi consegnati correttamente ai destinatari | Consegnato / Inviato x 100 |
| Percentuale aperture | Percentuale di messaggi recapitati aperti dai destinatari | Aperture univoche/consegnate x 100 |
| Percentuale di click-through (CTR) | Percentuale di messaggi consegnati in cui è stato fatto clic su un collegamento | Clic univoci / 100 consegnati |
| Percentuale di clic per apertura (CTOR) | Percentuale di messaggi aperti in cui è stato fatto clic su un collegamento | Clic/Aperture univoche x 100 |
| Tasso di conversione | Percentuale di destinatari che hanno completato l’azione desiderata | Conversioni / Consegnate x 100 |
| Percentuale annullamenti iscrizione | Percentuale di destinatari che hanno annullato l’abbonamento dopo la ricezione del messaggio | Annullamenti iscrizione/Consegne x 100 |
| Percentuale non recapitate | Percentuale di messaggi non recapitati | Mancato recapito / Inviato x 100 |
| Ricavo per e-mail inviata | Ricavi attribuiti alla campagna divisi per messaggi inviati | Ricavi / Inviati - Totale |

## Schema del caso d’uso

**Attivazione messaggi in uscita in batch**

Valuta un pubblico, quindi distribuisci un messaggio in uscita pianificato (e-mail, SMS, push) a tutti i profili idonei in un’unica esecuzione batch.

**Catena di funzioni:** Valutazione del pubblico > Authoring dei messaggi > Esecuzione della campagna > Generazione rapporti

## Applicazioni

Per implementare questo modello vengono utilizzate le seguenti applicazioni.

- **[!DNL Adobe Journey Optimizer] (AJO)** — Authoring dei messaggi, configurazione del canale, esecuzione della campagna, orchestrazione del percorso, sperimentazione dei contenuti, regole di frequenza e reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Valutazione del pubblico, consenso e applicazione della governance
- **[!DNL Adobe Experience Platform] (AEP)** — Archivio profili, servizio identità, schemi, set di dati, raccolta dati

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve esistere | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Presunto sul posto | Sandbox di AJO fornita con una configurazione di canale attiva. Invio del sottodominio delegato, del pool IP assegnato e dell’aggiornamento dell’IP completato. Ruoli utente a cui sono assegnate le autorizzazioni per la creazione di campagne/percorsi. | [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home), [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Obbligatorio | Schema del profilo individuale XDM con attributi utilizzati per la segmentazione e la personalizzazione (ad esempio nome, e-mail, preferenze, livello). Lo schema XDM ExperienceEvent acquisisce l&#39;azione di conversione di destinazione (ad esempio, `commerce.purchases`, `web.webInteraction`) per il tracciamento della conversione post-campagna. Set di dati abilitati per il profilo per entrambi gli schemi. | [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Origini dati e raccolta | Presunto sul posto | Per acquisire eventi di conversione, l’assegnazione tag di Web SDK o Analytics sulla destinazione CTA deve essere attiva. Le pipeline di acquisizione in streaming o batch per gli attributi del profilo devono essere operative. | [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Panoramica delle origini](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Configurazione identità e profilo | Presunto sul posto | Spazi dei nomi delle identità per l’e-mail (ed eventuali identificatori per più dispositivi) configurati. Attributi di profilo richiesti per la personalizzazione mappati, acquisiti e risolvibili al momento dell’invio. Criterio di unione configurato. | [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Panoramica dei criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Definizione e segmentazione del pubblico | Obbligatorio | Pubblico di destinazione definito in RT-CDP utilizzando Segment Builder (Generatore di segmenti) o Audience Composition (Composizione pubblico). Pubblico pubblicato e in valutazione con una popolazione diversa da zero. Coperto nella fase di implementazione 1 tramite RT-CDP Audience Evaluation. | [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Guida dell&#39;interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Consigliato | Attributi calcolati come giorni dall’ultimo acquisto, conteggio degli ordini per tutta la durata o punteggio di coinvolgimento migliorano la precisione del pubblico e abilitano una personalizzazione più ricca dei messaggi. | [Panoramica attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Consigliato | I criteri di conservazione dei dati (scadenza) devono essere applicati per i set di dati evento che determinano il tracciamento delle conversioni. I campi dello schema di consenso devono essere configurati per l’applicazione di consenso/rinuncia a livello di canale. | [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Gruppo di campi Consenso e preferenze](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents) |
| Etichettatura e applicazione dell’utilizzo dati | Consigliato | Le etichette di governance sui campi PII utilizzati nella personalizzazione garantiscono la conformità durante l’attivazione. Impedisce l’uso non autorizzato dei dati sensibili del profilo nel contenuto dei messaggi o nelle esportazioni di pubblico. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview) |
| Monitoraggio e osservabilità | Incluso | Il monitoraggio dell’invio in tempo reale fa parte della fase di reporting. Gli avvisi a livello di piattaforma sugli errori di acquisizione o sull’utilizzo delle licenze forniscono visibilità operativa oltre le metriche a livello di campagna. | [Panoramica di Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home), [Panoramica degli avvisi](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| Reporting e analisi | Incluso | I rapporti sulle campagne e sul percorso sono trattati nella fase di reporting. Per un’analisi cross-channel più approfondita, l’integrazione di CJA fornisce analisi funnel, modellazione di attribuzione e analisi di coorte oltre i rapporti incorporati di AJO. | [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Guida all&#39;integrazione di AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Journey Optimizer] (AJO)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Configurazione canali | Fase 2: configurazione del canale | Configurare o convalidare la superficie di canale (e-mail, SMS o push) inclusi sottodominio, pool IP, impostazioni del mittente e elenco di soppressione |
| Authoring dei messaggi | Fase 3: authoring dei messaggi | Creare contenuti di messaggi utilizzando modelli, E-mail Designer, espressioni di personalizzazione, blocchi di contenuto condizionali e frammenti di contenuto |
| Esecuzione della campagna | Fase 4: Creazione di una campagna o di un Percorso | Crea, configura e attiva una campagna pianificata o attivata da API che associa il pubblico, il messaggio e la pianificazione di esecuzione |
| Sperimentazione sui contenuti | Fase 4: Creazione di una campagna o di un Percorso | Facoltativamente, configura esperimenti di contenuto A/B o multivariato per ottimizzare le prestazioni dei messaggi |
| Frequenza e regole business | Fase 4: Creazione di una campagna o di un Percorso | Facoltativamente, applica le regole di quota limite per evitare messaggi eccessivi tra campagne simultanee |
| Gestione dei conflitti e delle priorità | Fase 4: Creazione di una campagna o di un Percorso | Assegna punteggi di priorità e configura la risoluzione dei conflitti quando più campagne sono indirizzate a tipi di pubblico sovrapposti |
| Reporting e analisi delle prestazioni | Fase 5: Reporting e analisi delle prestazioni | Monitora le metriche di consegna tramite rapporti live durante l’esecuzione e analizza le prestazioni della campagna tramite rapporti cronologici dopo il completamento |

### [!DNL Real-Time CDP] (RT-CDP)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Valutazione del pubblico | Fase 1: Valutazione del pubblico | Definisci le regole del pubblico utilizzando Segment Builder (Generatore di segmenti) o Audience Composition (Composizione pubblico), seleziona il metodo di valutazione (batch, streaming o edge) e convalida la popolazione del pubblico |
| Applicazione del consenso e della governance | Fase 1: Valutazione del pubblico | Applica le preferenze di consenso e i criteri di utilizzo dei dati per garantire che solo i profili autorizzati ricevano il messaggio della campagna |

## Prerequisiti

Completa quanto segue prima di iniziare l’implementazione.

- La sandbox di AJO è attivata e attivata
- Il sottodominio di invio è delegato e verificato (SPF, DKIM, DMARC configurati)
- Il pool IP viene assegnato e riscaldato per il volume di invio della produzione
- Esiste almeno una superficie di canale attiva (e-mail, SMS o push)
- Gli account utente dispongono delle autorizzazioni per la creazione di campagne/percorsi e per l’authoring dei contenuti
- Lo schema di profilo XDM include gli attributi necessari per la segmentazione del pubblico e la personalizzazione dei messaggi
- Lo schema evento XDM acquisisce gli eventi di conversione per il tracciamento post-campagna
- I dati del profilo vengono acquisiti e unificati tramite Identity Service
- L’assegnazione tag di Web SDK o Analytics è attiva nella pagina di destinazione di CTA per acquisire eventi di conversione
- I campi di consenso sono compilati sui profili per il canale di messaggistica di destinazione
- Le risorse di contenuto (immagini, loghi, linee guida per il brand) sono disponibili per la progettazione dei messaggi

## Opzioni di implementazione

Questa sezione descrive tre opzioni di implementazione per l’attivazione batch dei messaggi in uscita, insieme a una guida di confronto e decisione.

### Opzione A: campagna pianificata (invio in batch una tantum)

**Ideale per:** invii ancorati alla data: annunci di vendita, avvii di prodotti, scadenze di registrazione di eventi, promemoria di rinnovo, blast di newsletter e qualsiasi invio in cui la data di esecuzione è nota in anticipo.

**Funzionamento:**

Una campagna pianificata è la variante più semplice della messaggistica in uscita in batch. L’addetto al marketing definisce il pubblico di destinazione, crea il contenuto del messaggio, imposta una data e un’ora di invio e attiva la campagna. Al momento dell’esecuzione pianificata, AJO valuta il pubblico per determinare la popolazione qualificata corrente, quindi consegna il messaggio a tutti i profili qualificati in un singolo batch.

L’intera configurazione avviene all’interno dell’interfaccia di AJO Campaigns, senza area di lavoro di percorso, logica di diramazione e passaggi di attesa. Questo rende le campagne pianificate le più veloci da configurare e le più facili da gestire. La campagna può essere impostata per l’esecuzione immediata, una data/ora futura specifica o una pianificazione ricorrente (giornaliera, settimanale, mensile).

**Considerazioni chiave:**

- Il pubblico viene valutato al momento dell’esecuzione, quindi vengono inclusi i profili idonei tra la pianificazione e l’esecuzione
- Non è disponibile alcuna logica di diramazione, attesa o condizione: il messaggio viene consegnato a tutti i profili idonei
- Supporta la sperimentazione dei contenuti (test A/B) direttamente nella configurazione della campagna
- Le proprietà della campagna includono un punteggio di priorità per la risoluzione dei conflitti con altre campagne

**Vantaggi:**

- Configurazione più semplice con il minor sovraccarico
- Tempi di avvio più rapidi per invii batch semplici
- Supporto integrato per pianificazioni ricorrenti
- Sperimentazione sui contenuti supportata in modo nativo
- Pubblico rivalutato al momento dell’esecuzione per verificarne l’attualità

**Limitazioni:**

- Nessun passaggio di attesa, condizioni o diramazione prima della consegna
- Impossibile reagire al comportamento del profilo tra la pianificazione e l’esecuzione
- Solo azione messaggio singolo: nessuna sequenza multi-touch
- Non può essere modificato una volta attivato (deve essere duplicato e modificato)

**Experience League:**

- [Introduzione alle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Creare una campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

### Opzione B: percorso attivato dal pubblico

**Ideale per:** invii basati sul comportamento: notifiche del carrello abbandonate, promemoria di scadenza delle sperimentazioni, celebrazioni milestone, attività di sensibilizzazione basate sulla qualifica e qualsiasi invio in cui il trigger è la qualifica del pubblico o un evento di business anziché una data di calendario.

**Funzionamento:**

Un percorso attivato dal pubblico utilizza l’area di lavoro del percorso per inviare un messaggio quando un profilo si qualifica per un pubblico definito o genera un evento qualificante. La voce percorso viene attivata dalle modifiche di appartenenza al pubblico (profili che entrano nel pubblico) anziché da una pianificazione fissa. L’area di lavoro di percorso consente passaggi di attesa facoltativi, rami di condizione e logica di eliminazione prima dell’azione del messaggio, fornendo maggiore flessibilità rispetto a una campagna pianificata.

Il percorso è configurato nell’interfaccia di AJO Percorsi utilizzando l’evento Read Audience entry. Quando i profili si qualificano per il pubblico, entrano nel percorso e procedono attraverso i nodi dell’area di lavoro. Una semplice implementazione può contenere un solo nodo di azione e-mail, rendendolo funzionalmente simile a una campagna pianificata ma con tempistiche di ingresso basate sulla qualifica del pubblico. Implementazioni più complesse possono aggiungere nodi di attesa (ad esempio, un’attesa di 24 ore dopo la qualifica), nodi di condizione (ad esempio, verifica se il profilo ha aperto un’e-mail precedente) o logica di eliminazione prima della consegna del messaggio.

**Considerazioni chiave:**

- La voce percorso viene attivata dalla qualifica del pubblico, non da una data di calendario
- L’area di lavoro del percorso supporta nodi di attesa, condizione e suddivisi per la logica di pre-consegna
- Le regole di reinserimento del percorso controllano se i profili possono entrare nel percorso più volte
- Le impostazioni di arbitrato di percorso determinano il comportamento quando un profilo si trova già in un percorso concorrente

**Vantaggi:**

- Tempi di ingresso flessibili in base alla qualifica del pubblico anziché alla pianificazione fissa
- I nodi di attesa e condizione consentono la logica di pre-consegna (ad esempio, ritardo, controllo, eliminazione)
- I controlli di reinserimento impediscono invii duplicati allo stesso profilo
- Può essere esteso in un percorso con più passaggi se il caso d’uso evolve
- Supporta la generazione di rapporti a livello di percorso con metriche a livello di ingresso, uscita e nodo

**Limitazioni:**

- Sovraccarico di configurazione maggiore rispetto a una campagna pianificata
- L’area di lavoro di percorso aggiunge complessità anche per i casi di utilizzo con messaggio singolo
- Il percorso deve essere pubblicato e non può essere modificato mentre è attivo (deve creare una nuova versione)
- Il limite di immissione può limitare il numero di profili inseriti in un intervallo di tempo

**Experience League:**

- [Introduzione ai percorsi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Leggi percorso di pubblico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### Opzione C: campagna attivata da API

**Ideale per:** invii avviati dal sistema: conferma dell&#39;ordine con contenuto di upselling, follow-up della risoluzione dei ticket di supporto, notifiche transazionali con contenuto di marketing e qualsiasi invio in cui l&#39;evento che attiva proviene da un sistema esterno in un momento specifico.

**Funzionamento:**

Una campagna attivata da API viene attivata tramite una chiamata API REST nel momento in cui si verifica un evento di sistema di attivazione. La campagna è preconfigurata in AJO con il contenuto del messaggio e le impostazioni del canale, ma invece di associare un pubblico predefinito, la chiamata API specifica i profili dei destinatari e può trasmettere dati contestuali che popolano i parametri dei messaggi dinamici.

Questa variante è ideale quando la tempistica di invio è determinata da un sistema esterno (ad esempio, un sistema di gestione degli ordini, un flusso di lavoro CRM o una piattaforma di supporto) anziché dalla valutazione del pubblico o da una pianificazione del calendario. I dati contestuali passati nel payload dell’attivatore API, ad esempio i dettagli dell’ordine, i numeri dei biglietti o i nomi dei prodotti, possono personalizzare il contenuto del messaggio utilizzando attributi contestuali non memorizzati nel profilo.

**Considerazioni chiave:**

- Non è richiesto alcun pubblico preassociato; i destinatari sono specificati nella richiesta di attivazione dell’API
- I dati contestuali nel payload del trigger consentono la personalizzazione dinamica oltre gli attributi del profilo
- La campagna deve essere di tipo &quot;Attivata da API&quot; e deve essere attivata prima di poter ricevere le richieste di attivazione
- Ogni richiesta di attivazione API supporta fino a 20 destinatari di profilo
- La valutazione del pubblico (fase 1) può essere ignorata poiché i destinatari provengono dalla chiamata API

**Vantaggi:**

- Attivazione in tempo reale da sistemi esterni al momento dell&#39;evento
- Personalizzazione contestuale con dati non memorizzati nel profilo (dettagli dell’ordine, informazioni sul biglietto)
- Nessun sovraccarico di valutazione del pubblico: i destinatari vengono specificati direttamente
- Supporta la messaggistica ibrida transazionale e di marketing

**Limitazioni:**

- Richiede l’integrazione con il sistema esterno per inviare l’attivatore API
- Massimo 20 destinatari per richiesta di attivazione API
- Nessuna valutazione del pubblico incorporata - il sistema chiamante deve determinare i destinatari
- Maggiore complessità tecnica dovuta ai requisiti di integrazione API
- La sperimentazione dei contenuti non è supportata per le campagne attivate da API

**Experience League:**

- [Campagne attivate da API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)
- [Attivare campagne tramite API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### Confronto delle opzioni

La tabella seguente confronta le tre opzioni di implementazione tra i diversi criteri chiave.

| Criteri | Opzione A: campagna pianificata | Opzione B: Percorso basato su pubblico | Opzione C: campagna attivata da API |
| --- | --- | --- | --- |
| Ideale per | Invii ancorati alla data (promozioni, lanci, newsletter) | Invii basati sul comportamento (eventi di qualifica, milestone) | Invii avviati dal sistema (conferme d’ordine, transazionali) |
| Complessi | Bassa | Medio | Medium - Alta |
| Tipo di trigger | Data/ora calendario o pianificazione ricorrente | Qualificazione del pubblico o evento di business | Chiamata API di sistema esterna |
| Logica di pre-consegna | Nessuno | Attesa, condizione, nodi suddivisi disponibili | Nessuno (logica nel sistema chiamante) |
| Associazione del pubblico | Pubblico predefinito per RT-CDP | Pubblico predefinito per RT-CDP | Destinatari specificati nel payload API |
| Dati contestuali | Solo attributi profilo | Solo attributi profilo | Attributi del profilo + dati del payload API |
| Sperimentazione sui contenuti | Supportato | Supportato (su azione messaggio) | Non supportato |
| Quota limite | Supportato | Supportato | Supportato |
| Controllo del rientro | N/D (esecuzione unica) | Regole di reinserimento configurabili | N/D (per richiesta) |
| Interfaccia di configurazione | Campagne AJO | Percorsi AJO | Campagne AJO + sistema esterno |
| Richiede | Pubblico, superficie di canale, messaggio | Pubblico, superficie di canale, messaggio, area di lavoro percorso | Superficie di canale, messaggio, integrazione API |

### Scegli l’opzione giusta

Utilizza il seguente flusso di decisione per selezionare l’opzione di implementazione appropriata:

1. **L&#39;invio è attivato da un evento di sistema esterno (ad esempio, ordine effettuato, ticket risolto)?** In caso affermativo, scegliere **Opzione C: campagna attivata da API**. Questa è l&#39;unica opzione che supporta i trigger avviati dal sistema con dati di payload contestuali.

2. **L&#39;invio è ancorato a una data di calendario specifica o a una pianificazione ricorrente?** In caso affermativo, scegliere **Opzione A: campagna pianificata**. Si tratta del metodo più semplice e veloce da configurare per gli invii basati su date.

3. **L&#39;invio deve reagire alla qualificazione del pubblico o richiedere una logica di pre-consegna (attesa, condizione, soppressione)?** In caso affermativo, scegliere **Opzione B: Percorso attivato dal pubblico**. L’area di lavoro del percorso offre la flessibilità necessaria per una logica decisionale basata sul comportamento e per la fase di pre-consegna.

4. **L&#39;invio è una trasmissione semplice a un pubblico noto senza requisiti logici o di tempistica speciali?** Scegliere **Opzione A: campagna pianificata** per il sovraccarico di configurazione più basso.

## Fasi di implementazione

Questa sezione descrive in dettaglio ogni fase dell’implementazione, compresi i punti decisionali e gli orientamenti specifici per ciascuna opzione.

### Fase 1: Valutare il pubblico

**Funzione applicazione:** RT-CDP: Audience Evaluation

Questa fase definisce e valuta il segmento di pubblico target che riceverà il messaggio della campagna. Determina i profili idonei per l’invio in base agli attributi del profilo, ai segnali comportamentali e alle regole di soppressione.

>[!NOTE]
>Per l’opzione C (Campagna attivata da API), questa fase può essere ignorata se i destinatari sono specificati completamente nel payload del trigger API. Tuttavia, anche le campagne attivate da API traggono vantaggio dall’avere un pubblico di soppressione per filtrare i profili che non devono ricevere messaggi.

#### Decisione: Criteri del pubblico

Quali condizioni definiscono il pubblico target? Quali regole di soppressione devono escludere i profili?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Pubblico basato su attributi di profilo | Il pubblico di destinazione è definito dagli attributi demografici, di preferenza o di stato | Più semplice da generare; supporta tutti i metodi di valutazione |
| Pubblico basato su eventi comportamentali | Il pubblico di destinazione è definito dalle azioni intraprese (o non intraprese) entro un intervallo di tempo | Richiede l’acquisizione dei dati dell’evento; le regole dell’intervallo di tempo possono limitare l’idoneità allo streaming |
| Composizione del pubblico (pubblico derivato) | Il pubblico di destinazione richiede operazioni di classificazione, suddivisione, esclusione o arricchimento tra più tipi di pubblico di origine | Valutazione più potente, ma solo batch; limitato a 10 composizioni per sandbox |

#### Decisione: metodo di valutazione

Quanto rapidamente il pubblico deve aggiornarsi per riflettere i nuovi profili che si qualificano o meno?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Valutazione in batch | Campagne pianificate in cui è accettabile l’aggiornamento del pubblico in una giornata; tipi di pubblico grandi e complessi | Predefinito per la maggior parte dei tipi di segmenti; elabora su base giornaliera o su richiesta; supporta tutte le funzioni delle regole di segmento |
| Valutazione in streaming | Percorsi attivati dal pubblico in cui i profili devono entrare quasi in tempo reale per qualificarsi | Automatico per le espressioni di regole di segmento idonee; non tutti i tipi di segmento sono idonei per lo streaming; latenza in tempo quasi reale (secondi o minuti) |
| Valutazione Edge | Non tipico per questo pattern (utilizzato per la personalizzazione della stessa pagina) | Supporto limitato per le regole di segmento; latenza di millisecondi; rilevante solo se combinata con modelli di personalizzazione web |

#### Decisione: criterio di unione

Quale criterio di unione deve utilizzare il pubblico per risolvere i frammenti di profilo?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Criterio di unione predefinito (timestamp ordinato) | Più comune per i casi di utilizzo di campagne batch | Il valore di attributo più recente vince; standard per messaggi in uscita |
| Criterio di unione personalizzato (precedenza set di dati) | Quando una specifica origine dati deve avere la priorità per gli attributi chiave | Utile quando i dati del sistema di gestione delle relazioni con i clienti devono sostituire i dati raccolti sul web per determinati campi |

#### Navigazione interfaccia utente

Cliente > Tipi di pubblico > Crea pubblico > Genera regola

#### Dettagli chiave della configurazione

- Definisci il pubblico utilizzando Segment Builder (Generatore di segmenti) con regole di segmento per gli attributi di profilo, gli eventi comportamentali e l’iscrizione al segmento
- Applica le regole di soppressione per escludere i profili che si sono già convertiti, hanno recentemente ricevuto un messaggio simile o hanno rinunciato
- Verifica che il pubblico abbia una popolazione diversa da zero prima di procedere
- Per le campagne batch, assicurati che sia attiva una pianificazione di valutazione del segmento o attiva la valutazione on-demand
- Conferma i campi di consenso (`consents.marketing.email.val`, `consents.marketing.sms.val`, ecc.) sono compilati e applicati

#### Dove le opzioni divergono

**Per L&#39;Opzione A (Campagna Pianificata):**

La valutazione in batch è tipica. Il pubblico viene rivalutato al momento dell’esecuzione della campagna, quindi viene eseguito il targeting della popolazione qualificata più recente. Definisci il pubblico e verificane la popolazione, quindi procedi alla creazione della campagna.

**Per L&#39;Opzione B (Percorso Attivato Dal Pubblico):**

È preferibile la valutazione in streaming, in modo che i profili entrino nel percorso quando sono idonei. Assicurati che l’espressione della regola del segmento sia idonea allo streaming (attivatori di eventi semplici, confronti di attributi, finestre temporali limitate). Configura il pubblico e verifica che la qualifica per lo streaming sia attiva.

**Per L&#39;Opzione C (Campagna Attivata Da API):**

La valutazione del pubblico può essere saltata completamente. Se utilizzato, crea un pubblico di soppressione per filtrare i profili che non devono ricevere il messaggio (ad esempio, abbonamento annullato di recente, già convertito). Il sistema chiamante determina i destinatari primari.

#### Documentazione di Experience League

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Composizione del pubblico](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Fase 2: configurare il canale

**Funzione applicazione:** AJO: Configurazione canale

Questa fase convalida o crea la superficie di canale (predefinito) che definisce l’infrastruttura di invio del messaggio: sottodominio, pool IP, identità del mittente, indirizzo di risposta e impostazioni di annullamento dell’abbonamento. Prima di poter creare il contenuto del messaggio o attivare le campagne, è necessario che esista una superficie di canale valida.

#### Decisione: canale di destinazione

Quale canale di messaggistica distribuirà il messaggio della campagna?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| E-mail | La maggior parte dei tipi di campagna: newsletter, promozioni, notifiche, rinnovi | Richiede la configurazione del sottodominio delegato, del pool IP riscaldato, dell’identità del mittente e dell’annullamento dell’iscrizione |
| SMS | Messaggi brevi o sensibili al tempo: vendite flash, promemoria di appuntamenti, codici OTP | Richiede le credenziali del provider SMS (Sinch, Twilio o Infobip); costo per messaggio più alto; requisiti di consenso più severi |
| Notifica push | Pubblico interessato da dispositivi mobili: aggiornamenti delle app, offerte basate sulla posizione, annunci in-app | Richiede credenziali APN (iOS) e/o FCM (Android); gli utenti devono avere l&#39;app installata con le autorizzazioni push concesse |

#### Decisione: selezione della superficie di canale

Nella sandbox esiste già una superficie di canale adatta o è necessario crearne una nuova?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Riutilizza superficie esistente | Una superficie attiva e verificata corrisponde al sottodominio, all’identità del mittente e al tipo di canale richiesti | Percorso più veloce; non è necessaria alcuna configurazione DNS o di riscaldamento |
| Crea nuova superficie | Non esiste alcuna superficie corrispondente ai requisiti oppure è necessaria una nuova identità di sottodominio/mittente | Richiede la delega dei sottodomini, la verifica DNS, l’assegnazione del pool IP e, potenzialmente, il riscaldamento dell’IP (2-4 settimane per i nuovi IP) |

#### Decisione: gestione dell’annullamento dell’abbonamento

Come deve essere gestita la rinuncia sulla superficie di canale?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Intestazione di annullamento iscrizione all’elenco con un solo clic | Standard per tutte le e-mail di marketing; richiesto dai principali ISP (Gmail, Yahoo) per il recapito dei messaggi | Aggiunge un’intestazione di annullamento dell’iscrizione basata su mailto: o URL che gli ISP presentano come pulsante &quot;Annulla iscrizione&quot; |
| Collegamento per annullare l’abbonamento nel corpo dell’e-mail | Richiesto come fallback per i client e-mail che non supportano le intestazioni per l’annullamento dell’iscrizione all’elenco | Includi un collegamento per annullare l’iscrizione nel piè di pagina dell’e-mail insieme all’intestazione per annullare l’iscrizione all’elenco |
| Entrambi (consigliato) | Best practice per tutte le e-mail di marketing | Massima copertura di conformità e miglior profilo di consegna |

#### Navigazione interfaccia utente

Administration > Channels > Channel surfaces > Create surface (Amministrazione > Canali > Superfici di canale > Crea superficie (o seleziona esistente))

#### Dettagli chiave della configurazione

- Per l’e-mail: associa il sottodominio di invio, il pool IP, il nome del mittente, l’e-mail del mittente, l’indirizzo di risposta e l’indirizzo Ccn (se è richiesta una copia di audit)
- Per SMS: configura le credenziali del provider SMS e le impostazioni per codice breve o codice lungo
- Per push: configura le credenziali APN e/o FCM con il certificato o la chiave server dell’app
- Verificare che la superficie di canale mostri lo stato &quot;Attivo&quot; prima di procedere
- Conferma che i record DNS (SPF, DKIM, DMARC) siano configurati correttamente per il sottodominio di invio
- Rivedi l’elenco di soppressione per le voci non aggiornate; effettua la pulizia prima dell’attivazione

#### Documentazione di Experience League

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delega sottodomini](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Creare pool IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Piani di riscaldamento IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Impostazioni superficie e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configurare il canale SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Gestire l’elenco di soppressione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Fase 3: Creazione del messaggio

**Funzione dell&#39;applicazione:** AJO: authoring dei messaggi

Questa fase crea il contenuto del messaggio che verrà consegnato al pubblico. Include la selezione o la creazione di un modello di contenuto, la progettazione del layout del messaggio, l’aggiunta di personalizzazione utilizzando gli attributi del profilo, la configurazione di blocchi di contenuto condizionale per varianti specifiche per il pubblico, la creazione di frammenti di contenuto riutilizzabili e la visualizzazione in anteprima/test del messaggio con profili di esempio.

#### Decisione: approccio basato sul contenuto

Come creare il contenuto del messaggio?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Inizia da modello esistente | Esistono modelli approvati dal marchio che corrispondono al tipo di messaggio (promozionale, transazionale, newsletter) | Percorso di authoring più veloce; garantisce la coerenza del brand; i modelli sono specifici per le sandbox |
| Progettare da zero | Non esiste alcun modello adatto o il messaggio richiede un layout univoco | Maggiore flessibilità, ma maggiore impegno; considera il salvataggio come modello da riutilizzare |
| Importa HTML | La progettazione del messaggio è stata creata esternamente (ad esempio, in uno strumento di progettazione) e HTML è pronto per l’importazione | Mantiene la progettazione esterna; potrebbe essere necessario apportare modifiche per i token di compatibilità e personalizzazione di AJO |

#### Decisione: profondità Personalization

Quali attributi di profilo devono personalizzare il messaggio e sono necessari blocchi di contenuto condizionali?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Personalizzazione di base (nome, saluto) | Campagne semplici in cui è sufficiente contenuto generico con una formula di apertura personalizzata | Impegno ridotto; rischio minimo di problemi di rendering; utilizza attributi di profilo standard |
| Personalizzazione basata su attributi | Il contenuto del messaggio varia in base agli attributi del profilo (livello, preferenza, posizione) | Richiede percorsi XDM verificati; prova con più profili per garantire il corretto rendering di tutte le varianti |
| Blocchi di contenuto condizionali | È necessario mostrare sezioni di contenuto diverse a segmenti di pubblico diversi all’interno dello stesso messaggio | Authoring più complesso; ogni condizione richiede un fallback predefinito; testare tutte le permutazioni |
| Personalizzazione contestuale (solo opzione C) | Le campagne attivate da API devono eseguire il rendering dei dati trasmessi nel payload del trigger (dettagli dell’ordine, informazioni sul ticket) | Gli attributi contestuali non sono memorizzati nel profilo; definisci i segnaposto nel messaggio e mappali sui campi del payload |

#### Decisione: strategia dei frammenti

Creare blocchi di contenuto condivisi come frammenti riutilizzabili?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Frammenti riutilizzabili | Intestazioni, piè di pagina, dichiarazioni di non responsabilità legali o blocchi di annullamento dell’abbonamento sono condivisi tra più campagne | Le modifiche a un frammento si propagano a tutti i messaggi che vi fanno riferimento (in tempo reale e bozza); un massimo di 30 frammenti per messaggio |
| Contenuto in linea | Messaggio una tantum senza elementi condivisi in altre campagne | Più semplice per contenuti monouso; nessun rischio di propagazione |

#### Navigazione interfaccia utente

Campagne > Seleziona campagna > Modifica contenuto > Designer e-mail (o editor SMS/push)

#### Dettagli chiave della configurazione

- Progetta il layout del messaggio trascinando i componenti di contenuto (testo, immagine, pulsante, divisore, colonne)
- Imposta le proprietà dell’intestazione dell’e-mail: oggetto, testo di preintestazione e superficie del mittente
- Inserire espressioni di personalizzazione utilizzando la sintassi Handlebars (ad esempio, `{{profile.person.name.firstName}}`)
- Configurare le funzioni di assistenza per la formattazione (data, numero, manipolazione delle stringhe)
- Aggiungi regole di contenuto condizionale per visualizzare contenuti diversi in base agli attributi del profilo o all’iscrizione al segmento
- Configura il contenuto di fallback predefinito quando non vengono soddisfatte condizioni
- Per gli SMS, componi il corpo del messaggio entro i limiti di caratteri considerati
- Per push, configura titolo, corpo, immagine e azione (collegamento profondo o URL)
- Visualizza l’anteprima del messaggio con profili di esempio per verificare il rendering della personalizzazione
- Invia e-mail di prova alle parti interessate interne per la revisione
- Test del rendering tra client e-mail tramite la funzione di rendering di e-mail

#### Documentazione di Experience League

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
- [Inviare bozze e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [Rendering di e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)
- [Creare un messaggio SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Progettare una notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### Fase 4: Creazione della campagna o del percorso

**Funzione applicazione:** AJO: Esecuzione campagna (opzioni A e C) o AJO: Journey Orchestration (opzione B)

Questa fase crea la campagna o il percorso che associa il pubblico, il messaggio e il meccanismo di esecuzione a un’unità consegnabile. È qui che le tre opzioni di implementazione divergono maggiormente.

#### Decisione: sperimentazione dei contenuti

La campagna deve includere un test A/B o un esperimento multivariato per ottimizzare le prestazioni dei messaggi?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Nessun esperimento | Variante di messaggio singolo con elevata affidabilità nell’efficacia dei contenuti | Configurazione più semplice; attivazione più rapida |
| Test A/B (2 varianti) | Verifica di righe dell’oggetto, CTA o layout di contenuto con un’ipotesi chiara | Suddividi il traffico 50/50 o con un’allocazione ponderata; richiede una dimensione di pubblico sufficiente per la rilevanza statistica |
| Test multivariato (3+ varianti) | Verifica di più elementi di contenuto simultaneamente | Richiede un pubblico più ampio; una durata più lunga per raggiungere la soglia di affidabilità; un massimo di 10 trattamenti per esperimento |

#### Decisione: Limitazione della frequenza

Questa campagna deve rispettare le regole globali di quota limite per evitare messaggi eccessivi?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Applicare le regole di frequenza | Campaign fa parte di un programma di messaggistica più ampio con più invii simultanei | Impedisce la stanchezza del cliente; i profili che superano il limite vengono eliminati dalla consegna |
| Esenzione dai limiti | La campagna è di importanza critica in termini di tempo o transazionale e deve raggiungere tutti i profili idonei indipendentemente dalla cronologia dei messaggi recenti | Utilizzare con moderazione; l’esenzione delle campagne dalle regole di frequenza rischia di causare un messaggistica eccessiva |

#### Decisione: punteggio di priorità

Quale livello di priorità deve avere questa campagna rispetto alle altre campagne attive?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Priorità alta (75-100) | Campagne critiche: lanci di prodotti principali, offerte a tempo limitato, notifiche normative | Ha la precedenza sulle campagne con priorità inferiore in caso di conflitti |
| Priorità Medium (25-74) | Campagne di marketing standard: newsletter, campagne di coinvolgimento, promozioni generali | Bilanciato rispetto ad altre campagne; può essere eliminato in caso di conflitti tra campagne con priorità più elevata |
| Priorità bassa (0-24) | Invii piacevoli: aggiornamenti informativi e promozioni secondarie | Sarà soppresso a favore di campagne con priorità più elevata |

#### Dove le opzioni divergono

**Per L&#39;Opzione A (Campagna Pianificata):**

**Navigazione interfaccia utente:** Campagne > Crea campagna > Pianificato > Marketing

1. Crea una nuova campagna di marketing pianificata
2. Selezionare il pubblico di destinazione dal selettore del pubblico
3. Seleziona la superficie di canale e collega il contenuto del messaggio creato
4. Configurare la pianificazione di esecuzione: immediata, data/ora specifica o ricorrente
5. Facoltativamente, abilita la sperimentazione dei contenuti e definisci le varianti di trattamento
6. Facoltativamente, configura il limite di frequenza e il punteggio di priorità
7. Rivedi la configurazione completa della campagna
8. Attivare la campagna

**Per L&#39;Opzione B (Percorso Attivato Dal Pubblico):**

**Navigazione interfaccia utente:** Percorsi > Crea Percorso

1. Creazione di un nuovo percorso con un evento di partecipazione &quot;Read Audience&quot;
2. Seleziona il pubblico di destinazione come origine della voce
3. Configurare le regole di reinserimento (consentire il reinserimento, l&#39;immissione una tantum o il reinserimento dopo il periodo di attesa)
4. Facoltativamente, aggiungi nodi di attesa (ad esempio, attendi 24 ore dopo la qualifica)
5. Facoltativamente, aggiungi nodi condizione (ad esempio, verifica se il profilo soddisfa criteri aggiuntivi)
6. Aggiungi il nodo azione del messaggio e seleziona la superficie di canale e il contenuto creato
7. Configurare i criteri di uscita (ad esempio, conversioni di profili, annullamenti di abbonamenti a profili)
8. Facoltativamente, abilita la sperimentazione del contenuto sull’azione del messaggio
9. Rivedere e pubblicare il percorso

**Per L&#39;Opzione C (Campagna Attivata Da API):**

**Navigazione interfaccia utente:** Campagne > Crea campagna > Attivato da API

1. Creare una nuova campagna attivata da API
2. Seleziona la superficie di canale e collega il contenuto del messaggio creato
3. Configurare i token di personalizzazione contestuali per i dati che verranno trasmessi nel payload dell’attivatore API
4. Rivedere e attivare la campagna
5. Nota l’ID della campagna da utilizzare nell’integrazione del trigger API del sistema esterno
6. Il sistema chiamante invia richieste di attivazione all’endpoint della campagna con profili dei destinatari e dati contestuali

#### Documentazione di Experience League

- [Creare una campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Introduzione alle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Campagne attivate da API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)
- [Introduzione ai percorsi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Leggi percorso di pubblico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Introduzione all’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Creare un esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Regole di frequenza](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Punteggi di priorità](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identificare potenziali conflitti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Fase 5: analisi di reporting e prestazioni

**Funzione applicazione:** AJO: Reporting e analisi delle prestazioni

Questa fase monitora le metriche di consegna durante l’esecuzione tramite rapporti live e analizza le prestazioni della campagna dopo il completamento tramite rapporti storici. Facoltativamente, configura l’integrazione di CJA per un’analisi cross-channel più approfondita.

#### Decisione: metodo di comunicazione

Quale livello di reporting è necessario per questa campagna?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo rapporti nativi di AJO | Le metriche di consegna e coinvolgimento standard sono sufficienti (invio, consegna, apertura, clic, mancati recapiti) | Nessuna configurazione aggiuntiva; i rapporti sono incorporati nell’interfaccia utente di Campaign/percorsi |
| Rapporti nativi di AJO + analisi CJA | Oltre alle metriche di consegna, è necessario eseguire analisi dell’impatto cross-channel, modellazione di attribuzione o analisi funnel | Richiede una connessione CJA e una visualizzazione dati collegata ai set di dati di AJO; fornisce funzionalità di analisi più approfondite |
| Reporting programmatico di CJA | Per le parti interessate è necessario disporre di dashboard automatizzati o di rapporti pianificati | Richiede l’integrazione con l’API di reporting di CJA; utile per dashboard esecutivi e riepiloghi ricorrenti sulle prestazioni |

#### Decisione: monitoraggio delle conversioni

Come verrà misurato il successo della campagna oltre le metriche di consegna e coinvolgimento?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Nessun tracciamento delle conversioni | L’obiettivo della campagna è la consapevolezza o il coinvolgimento (aperture, clic) senza alcuna azione a valle specifica | Più semplice; non è richiesto alcun tracciamento aggiuntivo degli eventi |
| Tracciamento conversione web | Campaign CTA rimanda a una pagina web in cui vengono tracciati gli eventi di conversione (acquisto, registrazione, invio di moduli) | Richiede l’assegnazione di tag Web SDK o Analytics sulla pagina di destinazione; gli eventi devono essere acquisiti nei set di dati di AEP |
| Evento di conversione personalizzato | Il successo della campagna si misura in base a un evento specifico per l’azienda non acquisito sul web (ad esempio, acquisto in-store, interazione con il call center) | Richiede che l’evento personalizzato venga acquisito in AEP e incluso nei set di dati di reporting |

#### Navigazione interfaccia utente

- Rapporti live: Campagne > Seleziona campagna > Rapporto live (o Percorsi > Seleziona percorso > Rapporto live)
- Rapporti cronologici: Campagne > Seleziona campagna > Rapporto tempo totale (o Percorsi > Seleziona percorso > Rapporto tempo totale)

#### Dettagli chiave della configurazione

- Accedi ai rapporti live durante l’esecuzione della campagna per monitorare la consegna e il coinvolgimento in tempo reale
- Rivedi le metriche chiave: Inviato, Consegnato, Mancato recapito, Aperture, Clic, Annullamenti iscrizione (e-mail); Inviato, Consegnato, Clic, Errori (SMS); Inviato, Consegnato, Aperture, Azioni (push)
- Dopo il completamento della campagna, accedi ai rapporti cronologici (sempre) per un’analisi completa
- Analizza la consegna funnel: Target > Inviato > Consegnato > Aperture > Clic
- Esamina i motivi di errore ed esclusione per identificare i problemi di consegna
- Se la sperimentazione dei contenuti è stata abilitata, rivedi i risultati dell’esperimento e attendi l’affidabilità statistica prima di dichiarare un vincitore
- Per l’integrazione con CJA, verifica che la visualizzazione dati di AJO includa i set di dati AJO rilevanti (Set di dati evento di feedback dei messaggi, Set di dati evento di tracciamento delle e-mail)

#### Documentazione di Experience League

- [Rapporto live delle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapporto live del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Rapporto sull’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Considerazioni sull’implementazione

Questa sezione descrive guardrail, insidie comuni, best practice e decisioni di compromesso.

### Guardrail e limiti

- Massimo 500 campagne live attive per sandbox: [guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Massimo 4.000 definizioni di segmenti per sandbox: [guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Massimo 10 superfici di canale per tipo di canale per sandbox
- Le campagne attivate da API supportano fino a 20 destinatari di profilo per richiesta di attivazione
- Una volta attivate, le campagne non possono essere modificate; duplicale e modificale
- I rapporti live vengono aggiornati ogni 60 secondi e mostrano le ultime 24 ore di dati
- I rapporti cronologici possono richiedere fino a 2 ore per essere compilati completamente dopo il completamento della campagna
- Massimo 10 trattamenti (varianti) per esperimento sul contenuto
- Massimo 10 configurazioni di limite per sandbox
- Massimo 30 frammenti di contenuto per messaggio
- Per una consegna dei messaggi ottimale, si consiglia una dimensione massima dell’e-mail di 100 KB
- I piani di riscaldamento dell’IP dovrebbero aumentare gradualmente il volume nell’arco di 2-4 settimane per i nuovi IP
- Le voci dell’elenco di soppressione vengono mantenute per un periodo configurabile (14 giorni predefiniti per mancati recapiti non permanenti)

### Insidie comuni

- **Invio prima del completamento del riscaldamento dell&#39;IP:** I nuovi indirizzi IP che inviano immediatamente volumi elevati verranno contrassegnati dagli ISP, causando uno scarso recapito messaggi e una potenziale blacklist. Completa sempre un piano di riscaldamento IP prima che la produzione invii nuovi IP.

- **Nessun test di personalizzazione tra più profili:** i token Personalization che funzionano per un profilo di test potrebbero non riuscire per altri se il percorso XDM di riferimento non esiste o è nullo in alcuni profili. Visualizza sempre in anteprima più profili di test che rappresentano diversi livelli di completezza dei dati.

- **Se si ignora la revisione dell&#39;elenco di soppressione:** le voci dell&#39;elenco di soppressione non aggiornate potrebbero bloccare la consegna a indirizzi validi, mentre le voci mancanti potrebbero causare la consegna a indirizzi non validi che generano mancati recapiti. Rivedi e pulisci l’elenco di soppressione prima delle campagne principali.

- **Ignorare il limite di frequenza per le campagne promozionali:** L&#39;invio di una campagna promozionale senza il limite di frequenza mentre sono attive anche altre campagne può causare la ricezione di più messaggi in un breve periodo, causando l&#39;annullamento degli abbonamenti e i reclami di spam.

- **Pianificazione di campagne senza verifica della popolazione del pubblico:** L&#39;attivazione di una campagna prima della conferma che il pubblico di destinazione abbia una popolazione valutata diversa da zero comporta la consegna di zero messaggi. Verifica sempre la dimensione del pubblico prima dell&#39;attivazione.

- **Utilizzo della valutazione batch per i percorsi attivati dal pubblico:** Se il percorso utilizza una voce Read Audience con la valutazione batch, i profili non verranno inseriti quasi in tempo reale. Utilizza la valutazione in streaming per il pubblico quando è richiesto l’accesso al percorso quasi in tempo reale.

- **Non configurare l&#39;applicazione del consenso:** L&#39;invio di messaggi ai profili senza un consenso marketing valido viola le normative e danneggia la reputazione del recapito messaggi. Assicurati che i campi di consenso siano compilati e applicati a livello di superficie di canale.

### Best practice

- Inizia con l’opzione A (campagna pianificata) per casi d’uso di trasmissione semplici e passa all’opzione B (Percorso basato sul pubblico) solo quando è necessaria una logica di pre-consegna o una tempistica basata sul comportamento
- Per garantire la massima conformità, includi sempre nel corpo dell’e-mail sia l’intestazione con un solo clic per annullare l’iscrizione che un collegamento per annullare l’iscrizione
- Crea frammenti di contenuto riutilizzabili per intestazioni, piè di pagina e note legali per garantire la coerenza tra le campagne
- Imposta le regole di quota limite prima di attivare le campagne per evitare messaggi eccessivi tra invii simultanei
- Utilizza la sperimentazione dei contenuti per ottimizzare gli oggetti e i CTA, iniziando con test A/B prima di passare agli esperimenti multivariati
- Assegna punteggi di priorità a tutte le campagne attive per garantire una risoluzione coerente dei conflitti
- Pianifica il completamento della valutazione batch del pubblico prima del tempo di esecuzione della campagna per garantire la disponibilità di nuovi dati sul pubblico
- Invia e-mail di prova e utilizza la funzione di rendering delle e-mail per verificare che il messaggio venga visualizzato correttamente tra i client e-mail prima dell’attivazione
- Monitora il rapporto live immediatamente dopo l’attivazione della campagna per rilevare tempestivamente i problemi di consegna
- Archivia configurazioni di campagne e risultati di esperimenti per riferimenti futuri e ottimizzazione continua

### Decisioni di compromesso

Nell’effettuare le scelte di attuazione, dovrebbero essere valutati i seguenti compromessi.

#### Semplicità e flessibilità

Le campagne pianificate (opzione A) offrono la configurazione più semplice, ma non dispongono di una logica di pre-consegna. I percorsi attivati dal pubblico (opzione B) forniscono una logica di pre-distribuzione, ma aggiungono complessità alla configurazione.

- **L&#39;opzione A favorisce:** velocità di avvio, semplicità operativa, self-service per gli addetti marketing
- **L&#39;opzione B favorisce:** il targeting comportamentale, la soppressione condizionale e l&#39;estensibilità a percorsi con più passaggi
- **Consiglio:** inizia con l&#39;opzione A per gli invii diretti. Passa all’opzione B solo quando il caso d’uso richiede effettivamente una logica di attesa, condizione o diramazione prima della consegna. Evita di utilizzare l’area di lavoro del percorso per semplici invii batch che non beneficiano delle funzionalità di orchestrazione.

#### Aggiornamento del pubblico rispetto ai costi di valutazione

La valutazione in streaming fornisce aggiornamenti del pubblico quasi in tempo reale, ma prevede restrizioni per le regole dei segmenti. La valutazione in batch supporta tutte le funzioni delle regole di segmento ma valuta su base giornaliera.

- **Preferenze streaming:** tempestività, precisione basata sul comportamento, voce di percorso attivata dal pubblico
- **Preferenze batch:** logica di pubblico complessa, popolazioni grandi, sovraccarico di valutazione inferiore
- **Consiglio:** Utilizzare la valutazione in batch per le campagne pianificate (opzione A) in cui è sufficiente la freschezza giornaliera. Utilizza la valutazione in streaming per percorsi attivati dal pubblico (opzione B) in cui i profili devono entrare quando sono idonei. Se l’espressione della regola del segmento di pubblico non è idonea allo streaming, ristruttura le regole o accetta la latenza a livello di batch.

#### Profondità di Personalization e complessità dell’authoring

Una personalizzazione più approfondita (blocchi di contenuto condizionali, sezioni dinamiche) migliora il coinvolgimento, ma aumenta le attività di authoring e test.

- **La personalizzazione approfondita favorisce:** tassi di coinvolgimento più elevati, esperienza del cliente più pertinente, migliore conversione
- **La personalizzazione semplice favorisce:** tempi di avvio più rapidi, minore onere dei test, rischio ridotto di errori di rendering
- **Consiglio:** inizia con la personalizzazione di base (nome, categoria di prodotto pertinente) e il livello nei blocchi di contenuto condizionale in base ai miglioramenti delle prestazioni misurati. Prima dell’attivazione, testa sempre tutte le varianti di contenuto in più profili di test.

#### Controllo della frequenza e portata del messaggio

Un limite di frequenza rigoroso impedisce i messaggi eccessivi, ma può sopprimere la consegna della campagna ai profili che hanno ricevuto di recente altri messaggi.

- **Limiti rigorosi per i favori:** qualità dell&#39;esperienza del cliente, tassi di annullamento degli abbonamenti più bassi, reputazione del marchio
- **Preferenze per limiti permissivi:** Massima portata dei messaggi, impression totali più elevate, copertura della campagna
- **Consiglio:** Abilita sempre il limite di frequenza per le campagne di marketing. Imposta i limiti specifici per il canale (ad esempio, 3-5 e-mail a settimana, 1-2 SMS a settimana). Esentare dalle regole relative ai limiti solo i messaggi realmente critici in termini di tempo o transazionali.

## Documentazione correlata

Questa sezione fornisce collegamenti completi alla documentazione di [!DNL Experience League] organizzati per argomento.

### Campagne

- [Introduzione alle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Creare una campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Campagne attivate da API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### Percorsi

- [Introduzione ai percorsi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Leggi percorso di pubblico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### Configurazione dei canali

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delega sottodomini](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Creare pool IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Piani di riscaldamento IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Impostazioni superficie e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configurare il canale SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Gestire l’elenco di soppressione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Authoring e personalizzazione dei messaggi

- [Creare un messaggio e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Utilizzare i componenti di contenuto Designer e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [Importare o codificare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/code-content)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Funzioni di supporto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### Gestione dei contenuti

- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilizzare i frammenti di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anteprima e test del contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Inviare bozze e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [Rendering di e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)

### Sperimentazione sui contenuti

- [Introduzione all’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Creare un esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapporto sull’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Calcoli statistici](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### Gestione della frequenza e dei conflitti

- [Regole di frequenza](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Panoramica sulle regole business](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Introduzione alla gestione dei conflitti e delle priorità](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Punteggi di priorità](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identificare potenziali conflitti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Limitazione di percorso e arbitrato](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### Tipi di pubblico e segmentazione

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Composizione del pubblico](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Generazione rapporti

- [Rapporto live delle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapporto live del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### Governance dei dati e consenso

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview)
- [Gruppo di campi Consenso e preferenze](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Modellazione dati e identità

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Guardrail

- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Guardrail di acquisizione](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Tutorial e guida introduttiva

- [Introduzione a Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/get-started)
- [Creare la prima campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Creare il primo percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
