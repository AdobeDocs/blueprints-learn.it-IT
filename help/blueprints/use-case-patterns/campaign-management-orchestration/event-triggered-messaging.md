---
title: Messaggi attivati da eventi
description: Scopri come inviare messaggi contestuali in tempo reale in risposta a eventi comportamentali o di sistema.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 75137990-9848-40c0-abf3-adbd21d2de52
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '9040'
ht-degree: 1%

---

# Messaggistica attivata da eventi

Questa guida fornisce un blueprint di implementazione completo per la messaggistica attivata da eventi utilizzando [!DNL Adobe Journey Optimizer] (AJO), [!DNL Real-Time Customer Data Platform] (RT-CDP) e [!DNL Adobe Experience Platform] (AEP). È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono inviare messaggi contestuali in tempo reale in risposta a eventi comportamentali o di sistema.

Utilizza questa guida per capire cosa configurare, dove esistono opzioni di implementazione e quali compromessi sono alla base di ogni decisione.

La guida descrive l’intero ciclo di vita, dall’acquisizione degli eventi alla creazione del percorso, fino alla distribuzione dei messaggi e al reporting sulle prestazioni, con indicazioni decisionali dettagliate per tre diverse opzioni di implementazione.

## Panoramica del caso d’uso

La messaggistica attivata da eventi fornisce un messaggio contestuale in risposta a un evento comportamentale o di sistema in tempo reale. A differenza dell’attivazione batch dei messaggi in uscita, che invia a un pubblico pre-valutato secondo una pianificazione, questo modello ascolta un evento idoneo (ad esempio l’abbandono del carrello, una sessione di navigazione, l’invio di un modulo o una modifica dello stato del sistema) e inserisce immediatamente il profilo di attivazione in un percorso che valuta le condizioni e consegna un messaggio.

Il modello si basa sullo streaming di eventi in tempo reale in AEP (tramite Web SDK, Mobile SDK o API lato server), un percorso con una voce evento unitaria in AJO e una logica di valutazione delle condizioni che determina se e cosa inviare. Il messaggio viene generalmente inviato entro pochi minuti dall’evento di attivazione, rendendo questo modello ideale per comunicazioni pertinenti dal punto di vista temporale.

Le organizzazioni utilizzano questo modello per rispondere alle azioni dei clienti in tempo reale, aumentando la rilevanza e aumentando i tassi di coinvolgimento e conversione rispetto alle comunicazioni batch pianificate. Gli scenari comuni includono il recupero del carrello abbandonato, il follow-up post-acquisto, i messaggi di benvenuto dopo la registrazione e le notifiche sensibili al tempo come errori di pagamento o avvisi di calo dei prezzi.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

**[Ripristina percorsi e carrelli abbandonati](../../business-objectives/customer-experience/recover-abandoned-carts-journeys.md)**

Coinvolgi nuovamente gli utenti che abbandonano durante i flussi di acquisto, applicazione o iscrizione con follow-up personalizzati e tempestivi.

| KPI |
| --- |
| Tassi di conversione, ricavi incrementali, coinvolgimento |

**[Aumentare i tassi di conversione](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

Migliora la percentuale di visitatori e potenziali clienti che completano le azioni desiderate, ad esempio acquisti, iscrizioni o invii di moduli.

| KPI |
| --- |
| Tassi di conversione, conversione lead, costo per lead |

**[Distribuisci esperienze cliente personalizzate](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

Personalizza contenuti, offerte e messaggi in base a preferenze, comportamenti e fasi del ciclo di vita individuali.

| KPI |
| --- |
| Coinvolgimento, tassi di conversione, soddisfazione del cliente (CSAT) |

**[Miglioramento dell&#39;onboarding dei clienti](../../business-objectives/customer-experience/improve-customer-onboarding.md)**

Accelerare il time-to-value per i nuovi clienti con esperienze di benvenuto e percorsi di attivazione semplificati e personalizzati.

| KPI |
| --- |
| Coinvolgimento, fidelizzazione, tassi di conversione |

## Esempi di casi d’uso tattici

Gli scenari seguenti illustrano come la messaggistica attivata da eventi può essere applicata in contesti aziendali diversi.

- **E-mail di abbandono carrello o SMS**: invia un messaggio di promemoria quando un cliente aggiunge articoli al carrello ma non completa l&#39;acquisto entro un intervallo di tempo definito
- **Follow-up abbandono navigazione** — Coinvolgi nuovamente i visitatori che hanno visualizzato prodotti o contenuti ma non hanno eseguito un&#39;azione di conversione
- **Grazie dopo l&#39;acquisto o cross-selling**: invia una conferma e consigli di cross-selling subito dopo un evento di acquisto
- **Promemoria sulla scadenza della versione di prova** — Avvisa gli utenti che si stanno avvicinando alla fine di una versione di prova gratuita con messaggi di rinnovo o conversione
- **Messaggio di benvenuto dopo la registrazione** - Invia un messaggio di onboarding immediato quando un nuovo utente registra o crea un account
- **Conferma invio modulo** - Conferma invio modulo (richieste di contatto, applicazioni, iscrizioni) con una conferma contestuale
- **Notifica di errore pagamento** - Avvisa i clienti quando un pagamento ricorrente non riesce, richiedendo loro di aggiornare le informazioni di pagamento
- **Notifica push di riconversione dell&#39;app** — Attiva un messaggio di riconversione quando un utente disinstalla un&#39;app mobile
- **Conferma prenotazione o appuntamento** - Invia conferma immediata dopo la pianificazione di una prenotazione, una prenotazione o un appuntamento
- **Avviso di calo prezzo per gli elementi della lista dei desideri** — Notifica ai clienti quando un prodotto nella lista dei desideri scende di prezzo

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare l’efficacia delle implementazioni di messaggistica attivate da eventi.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Tasso di conversione | Percentuale di destinatari del messaggio attivato che hanno completato l’azione desiderata (acquisto, iscrizione, rinnovo) | Conversioni/Messaggi recapitati * 100 |
| Reddito Incrementale | Ricavi aggiuntivi attribuibili ai messaggi attivati da eventi rispetto ai gruppi di controllo senza invio | Ricavi da invii attivati - Linea di base gruppo di controllo |
| Percentuale aperture | Percentuale di messaggi recapitati aperti dai destinatari | Aperture / Consegnate * 100 |
| Percentuale di click-through (CTR) | Percentuale di messaggi consegnati che generano almeno un clic | Clic / Consegnato * 100 |
| Tempo di conversione | Tempo medio trascorso tra la consegna del messaggio e l’evento di conversione | Media(timestamp di conversione - timestamp di consegna) |
| Percentuale di completamento percorso | Percentuale di profili che entrano nel percorso e raggiungono il passaggio di consegna del messaggio (non eliminati da condizioni o uscite) | Profili che raggiungono la consegna / Profili che entrano nel percorso * 100 |
| Percentuale di soppressione dei messaggi | Percentuale di profili idonei soppressi a causa di limiti di frequenza, consenso o valutazione delle condizioni | Profili soppressi / Profili qualificati totali * 100 |
| Percentuale non recapitate | Percentuale di messaggi che non è stato possibile recapitare a causa di mancati recapiti permanenti o non permanenti | Rimbalzi / Inviati * 100 |

## Schema del caso d’uso

Questa sezione descrive il pattern di base e la catena di funzioni che gestisce la messaggistica attivata da eventi.

**Messaggi attivati da eventi**

Ascolta un evento comportamentale o di sistema in tempo reale, quindi distribuisci un messaggio contestuale al profilo che attiva.

**Catena di funzioni:** Acquisizione evento > Voce Percorso > Valutazione condizione > Consegna messaggio > Reporting

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni Adobe.

- **[!DNL Adobe Journey Optimizer](AJO)**: orchestrazione del Percorso con voce evento unitaria, valutazione delle condizioni, passaggi di attesa, authoring dei messaggi, configurazione dei canali, governance della frequenza e reporting sulla consegna
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — Valutazione del pubblico per filtraggio basato su condizioni all&#39;interno di percorsi, applicazione del consenso e della governance, arricchimento del profilo
- **[!DNL Adobe Experience Platform](AEP)** — Acquisizione di eventi in tempo reale tramite Web SDK, Mobile SDK o API lato server; modellazione dati; risoluzione identità; Edge Network

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve esistere | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Presunto sul posto | Sandbox AJO fornita con configurazione del canale attivo. Autorizzazioni di creazione e pubblicazione del percorso assegnate al team di implementazione. Ruoli utente configurati per la gestione del percorso, l’authoring dei contenuti e l’amministrazione dei canali. | [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home), [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Obbligatorio | Uno schema XDM ExperienceEvent deve acquisire l’evento di attivazione con tutti i campi contestuali necessari per la valutazione delle condizioni e la personalizzazione dei messaggi (ad esempio, `commerce.productListAdds` per eventi del carrello, dettagli del prodotto, valore del carrello). Lo schema deve essere abilitato per Real-Time Customer Profile. È necessario creare un set di dati corrispondente e abilitarlo per il profilo. | [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Origini dati e raccolta | Obbligatorio | È necessario configurare lo streaming di eventi in tempo reale: Web SDK per eventi web, Mobile SDK per eventi app o Edge Network Server API per eventi di sistema. Un flusso di dati deve essere configurato con AEP e i servizi AJO abilitati, instradando gli eventi al set di dati corretto. Si tratta di una dipendenza critica, in quanto il modello dipende dall’acquisizione di eventi in tempo reale. | [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Configurare gli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Configurazione identità e profilo | Obbligatorio | L’evento che scatena l’attivazione deve essere associato a un’identità nota (e-mail, ID CRM o sessione autenticata) in modo che il percorso possa risolvere il profilo e recapitare il messaggio. Gli spazi dei nomi delle identità devono esistere per gli identificatori utilizzati dall’evento che attiva. Gli eventi anonimi richiedono l’unione di identità tramite il grafo delle identità prima che sia possibile recapitare un messaggio. È necessario configurare un criterio di unione. | [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Panoramica dei criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Definizione e segmentazione del pubblico | Consigliato | Anche se non è strettamente necessario per i percorsi attivati da eventi (l’immissione è basata su eventi e non su pubblico), i segmenti di pubblico possono essere utilizzati per la valutazione delle condizioni all’interno del percorso (ad esempio, invia solo se il profilo si trova in un segmento di &quot;cliente di alto valore&quot; o sopprimi se il profilo si trova in un segmento &quot;contattato di recente&quot;). La valutazione in streaming è consigliata per i controlli di appartenenza ai segmenti in tempo reale all’interno di percorsi. | [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Consigliato | Attributi calcolati come il conteggio dell’abbandono del carrello, i giorni dall’ultimo acquisto, il valore medio dell’ordine e il totale degli acquisti nel corso della vita migliorano la valutazione delle condizioni e la personalizzazione entro percorsi attivati. Questi aggregati comportamentali consentono decisioni di targeting più precise (ad es., distinguere i soggetti che abbandonano per la prima volta da quelli che abbandonano ripetutamente). | [Panoramica attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Consigliato | La scadenza dei dati dell’evento deve essere configurata per eventi comportamentali transitori (visualizzazioni di pagina, ricerche, clic) per gestire i costi di archiviazione e la conformità. I campi dello schema di consenso devono essere presenti per l’applicazione di consenso/rinuncia specifica per il canale durante la consegna dei messaggi. | [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Scadenze set di dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| Etichettatura e applicazione dell’utilizzo dati | Consigliato | Le etichette di governance sui campi evento e profilo garantiscono la personalizzazione conforme. Se i messaggi attivati includono contenuto personalizzato che utilizza dati PII o comportamentali, è necessario rivedere le etichette di utilizzo dei dati e i criteri di governance per evitare l’utilizzo di dati non autorizzati nel contenuto dei messaggi. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview) |
| Monitoraggio e osservabilità | Incluso | Il monitoraggio dell’esecuzione del percorso fa parte della fase di reporting. Inoltre, configura gli avvisi per errori di acquisizione degli eventi o ritardi di elaborazione del percorso per rilevare problemi della pipeline che impedirebbero l’invio di messaggi attivati. | [Panoramica avvisi](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [Panoramica approfondimenti osservabilità](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting e analisi | Incluso | I rapporti sulle prestazioni del percorso sono trattati nella fase di reporting. Per un’analisi più approfondita dell’efficacia dei messaggi attivati tra i canali e nel tempo, configura le connessioni e le aree di lavoro di CJA per analizzare l’attribuzione della conversione, il tempo di conversione e le prestazioni dei canali. | [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Guida all&#39;integrazione di AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Journey Optimizer] (AJO)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Journey Orchestration | Creazione e configurazione percorso | Creazione di un percorso con voce evento unitaria, configurazione dell’evento qualificato, aggiunta di nodi condizione, passaggi di attesa, azioni messaggio, criteri di uscita e regole di reinserimento |
| Configurazione canali | Impostazione superficie di canale | Configurare o convalidare le superfici di canale (e-mail, SMS, push), inclusa la delega di sottodomini, pool IP, impostazioni del mittente e gestione degli elenchi di soppressione |
| Authoring dei messaggi | Creazione contenuto messaggio | Creare contenuti contestuali per messaggi con personalizzazione basata su eventi, blocchi di contenuto condizionali e frammenti riutilizzabili |
| Frequenza e regole business | Creazione e configurazione del percorso (opzione C) | Configurare i limiti di frequenza e le regole di deduplicazione per evitare messaggi eccessivi da origini eventi ad alta frequenza |
| Gestione dei conflitti e delle priorità | Creazione e configurazione percorso | Assegnare punteggi di priorità e configurare il rilevamento dei conflitti per percorsi in concorrenza per gli stessi profili |
| Reporting e analisi delle prestazioni | Reporting e monitoraggio | Monitorare le metriche di distribuzione del percorso tramite rapporti live e storici; accedere ai dati delle prestazioni programmatiche tramite CJA |

### [!DNL Real-Time CDP] (RT-CDP)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Valutazione del pubblico | Impostazione Fondamentale (F5) | Valuta i segmenti di pubblico utilizzati per filtrare in base a condizioni all’interno del percorso (ad esempio, segmenti di clienti di alto valore, segmenti di soppressione) |
| Applicazione del consenso e della governance | Configurazione di base (S2/S3) | Applica le preferenze di consenso e i criteri di governance per l’utilizzo dei dati durante la consegna dei messaggi per garantire comunicazioni conformi |

## Prerequisiti

Completa quanto segue prima di iniziare l’implementazione.

- [ Sandbox AJO ] fornita con autorizzazioni di creazione e pubblicazione del percorso (F1)
- [ ] schema XDM ExperienceEvent che acquisisce l&#39;evento di attivazione con campi contestuali, abilitato per Real-Time Customer Profile (F2)
- [ ] streaming di eventi in tempo reale configurato tramite Web SDK, Mobile SDK o Edge Network Server API con un flusso di dati che instradano gli eventi al set di dati AEP corretto (F3)
- [ ] spazi dei nomi di identità configurati per gli identificatori nell&#39;evento di attivazione; regole di collegamento identità attive (F4)
- [ Superficie di canale ] (e-mail, SMS o push) configurata e convalidata con invio di test riuscito
- [ ] Contenuto del messaggio creato, revisionato e testato con profili di esempio
- [ ] campi di consenso popolati nei profili per il canale di destinazione (ad esempio, `consents.marketing.email.val`)
- [ ] Se utilizzi il filtro del pubblico basato sulla condizione (Opzione B/C), vengono definiti segmenti di pubblico valutati in streaming e vengono valutati attivamente

## Opzioni di implementazione

Questa sezione descrive tre opzioni di implementazione per i messaggi attivati da eventi. Ogni opzione si basa sulla precedente, aggiungendo funzionalità aggiuntive.

### Opzione A: messaggio semplice attivato da un evento

**Consigliato per:** risposte immediate con messaggio singolo senza ritardi o logica condizionale: conferma dell&#39;ordine, e-mail di benvenuto, conferma dell&#39;invio del modulo, conferma della prenotazione.

**Funzionamento:**

Il percorso ascolta un evento qualificato tramite un nodo di immissione evento unitario. Quando l’evento viene ricevuto, il profilo entra nel percorso, passa attraverso la valutazione delle condizioni minime (controllo del consenso, verifica dell’esistenza del profilo) e riceve immediatamente un singolo messaggio tramite il nodo di azione del canale configurato.

Questa è la variante di implementazione più semplice. L’area di lavoro del percorso contiene un nodo di immissione eventi, un nodo condizione opzionale per i controlli di idoneità di base, un singolo nodo azione messaggio e un nodo finale. Non ci sono passaggi di attesa, ramificazioni complesse e controlli di conversione. Il messaggio viene generalmente consegnato entro pochi secondi o minuti dall’evento che scatena l’attivazione.

I dati evento dell’evento che scatena l’attivazione (nome del prodotto, totale dell’ordine, dettagli del modulo) possono essere utilizzati per la personalizzazione dei messaggi tramite attributi contestuali nell’editor di personalizzazione. Questo approccio ottimizza la velocità di consegna e riduce al minimo la complessità del percorso.

**Considerazioni chiave:**

- Il messaggio viene inviato indipendentemente dal fatto che il cliente si converta autonomamente dopo l’evento (nessun controllo di conversione)
- Ideale per eventi che richiedono intrinsecamente una risposta immediata (conferme, conferme)
- Le regole di reinserimento devono essere configurate con attenzione: per i messaggi di conferma, consenti il reinserimento in modo che ogni evento generi un messaggio; per i messaggi di benvenuto, impedisce il reinserimento

**Vantaggi:**

- Time-to-delivery più veloce (secondi-minuti dopo l’evento)
- Configurazione del percorso più semplice con un numero minimo di parti mobili
- Minor rischio di errori di percorso o profili bloccati
- Facilità di test e manutenzione

**Limitazioni:**

- Impossibile verificare se il cliente si è convertito autonomamente prima dell’invio
- Impossibile incorporare logica condizionale con ritardo
- Può generare messaggi non necessari se l’evento si verifica frequentemente senza governance della frequenza

**Experience League:**

- [Creazione di un percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Eventi generali](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)

### Opzione B: messaggio condizionale attivato da un evento con attesa

**Ideale per:** risposte condizionali ritardate, in cui il cliente deve avere il tempo di effettuare l&#39;autoconversione prima di ricevere il messaggio: abbandono del carrello (attendi 1-4 ore, quindi controlla se il carrello è ancora abbandonato), abbandono navigazione (attendi 24 ore, controlla se l&#39;acquisto è stato effettuato), scadenza della versione di prova (attendi l&#39;approssimarsi della data di scadenza).

**Funzionamento:**

Il percorso ascolta un evento idoneo, immette il profilo e introduce un periodo di attesa prima di valutare le condizioni. Dopo l’attesa, un nodo della condizione controlla se il cliente si è autoconvertito (ad esempio, ha completato l’acquisto, ha rinnovato l’abbonamento) o se il contesto originale è ancora valido. Solo se la condizione viene soddisfatta (ad esempio, carrello ancora abbandonato) il percorso procede alla consegna del messaggio.

L’area di lavoro del percorso contiene un nodo di ingresso evento, un nodo di attesa (durata configurabile o data/ora specifica), un nodo condizione che verifica la presenza di un evento di conversione o di una modifica dello stato del profilo, percorsi di diramazione (invio di messaggi e uscita senza invio), un nodo azione messaggio sul percorso qualificato e un nodo finale su ciascun ramo. I criteri di uscita possono essere configurati in modo da rimuovere automaticamente i profili dal percorso se l’evento di conversione si verifica durante il periodo di attesa, eliminando la necessità di controllare le condizioni esplicite.

Questo approccio riduce i messaggi superflui dando ai clienti il tempo di auto-conversione, migliorando l’esperienza del cliente e aumentando la percezione della rilevanza dei messaggi inviati.

**Considerazioni chiave:**

- La durata dell’attesa influisce in modo significativo sui tassi di conversione: attese più brevi (1-2 ore) producono un’urgenza maggiore ma invii più inutili; attese più lunghe (24-48 ore) riducono il volume ma possono perdere la finestra di rilevanza
- La valutazione delle condizioni richiede che l’evento di conversione venga acquisito in AEP e associato alla stessa identità di profilo
- I criteri di uscita forniscono un’alternativa più pulita ai nodi di condizione esplicita per il controllo della conversione
- Le regole di reinserimento devono tenere conto del periodo di attesa: un profilo non deve rientrare nel percorso mentre è già in attesa

**Vantaggi:**

- Riduce i messaggi superflui verificando l&#39;autoconversione
- Produce comunicazioni di qualità superiore e più pertinenti
- Supporta casi d’uso sensibili al tempo con finestre di ritardo configurabili
- I criteri di uscita consentono la rimozione automatica del percorso al momento della conversione

**Limitazioni:**

- Maggiore complessità del percorso con nodi di attesa e condizione
- I profili occupano gli slot del percorso durante i periodi di attesa (soggetti a un timeout di percorso di 91 giorni)
- Richiede che l’evento di conversione venga acquisito in AEP entro la finestra di attesa per una valutazione accurata delle condizioni
- Tempi di consegna più lunghi rispetto all&#39;opzione A

**Experience League:**

- [Attività Attendi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Attività Condizione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Criteri di uscita](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### Opzione C: evento attivato con governance della frequenza

**Ideale per:** origini eventi ad alta frequenza per le quali l&#39;affaticamento dei messaggi rappresenta un problema: visualizzazioni di pagina, visualizzazioni di prodotto, query di ricerca, aggiunte al carrello ripetute. Può essere applicata come sovrapposizione sull&#39;opzione A o sull&#39;opzione B.

**Funzionamento:**

Questa opzione aggiunge la governance della frequenza all’opzione A o all’opzione B per evitare messaggi eccessivi. Gli eventi comportamentali ad alta frequenza (come visualizzazioni di prodotti o aggiunte ripetute al carrello) possono attivare il percorso più volte in un breve periodo di tempo. Senza la governance della frequenza, un profilo potrebbe ricevere messaggi duplicati o eccessivi.

La governance della frequenza è implementata tramite due meccanismi complementari: le regole aziendali di AJO (limiti di frequenza) che limitano il numero di messaggi ricevuti da un profilo per canale per periodo di tempo e le regole di reinserimento a livello di percorso che definiscono un periodo di raffreddamento prima che un profilo possa rientrare nello stesso percorso. Le regole aziendali operano a livello di organizzazione e impongono limiti per tutte le campagne e i percorsi (ad esempio, un massimo di 3 e-mail a settimana), mentre il blocco del reinserimento opera a livello di singolo percorso (ad esempio, un profilo non può reinserire il percorso specifico entro 72 ore dall’ultima immissione).

Inoltre, la gestione dei conflitti e delle priorità può essere configurata in modo da assegnare punteggi di priorità al percorso attivato, assicurando che, quando più percorsi o campagne competono per lo stesso profilo, la comunicazione con la priorità più elevata vinca.

**Considerazioni chiave:**

- I limiti di frequenza devono bilanciare la prevenzione dell’affaticamento con la trasmissione di importanti messaggi attivati
- Si consigliano limiti specifici per il canale: e-mail, SMS e push hanno soglie di affaticamento diverse
- I limiti di frequenza a livello di organizzazione e di rientro del percorso funzionano insieme; entrambi devono essere configurati
- I punteggi di priorità determinano quale comunicazione vince quando vengono raggiunti i punteggi massimi: ai percorsi con priorità più elevata devono essere assegnati punteggi più elevati

**Vantaggi:**

- Impedisce l&#39;affaticamento dei messaggi provenienti da origini eventi ad alta frequenza
- Mantiene la reputazione del marchio e la soddisfazione degli abbonati
- I limiti a livello di organizzazione forniscono una rete di sicurezza per tutte le campagne e i percorsi
- Il punteggio di priorità assicura che i messaggi più importanti vengano inviati al raggiungimento del limite

**Limitazioni:**

- Alcuni profili idonei verranno eliminati, con la possibile mancanza di messaggi rilevanti
- La configurazione del limite di frequenza aggiunge complessità amministrativa
- Le maiuscole possono interagire in modo imprevisto con altre campagne e percorsi attivi che condividono lo stesso canale
- Richiede un monitoraggio e un adeguamento continui quando il portafoglio di messaggi cambia

**Experience League:**

- [Regole di frequenza](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Panoramica sulle regole business](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Punteggi di priorità](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Gestione voci percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)

### Confronto delle opzioni

La tabella seguente confronta le tre opzioni di implementazione tra i diversi criteri chiave.

| Criteri | Opzione A: evento semplice attivato | Opzione B: condizionale con attesa | Opzione C: Governance della frequenza |
| --- | --- | --- | --- |
| Ideale per | Conferme immediate, conferme | Ripristino dell’abbandono, risposte condizionali ritardate | Sorgenti di eventi ad alta frequenza, ambienti con più percorsi |
| Complessi | Bassa | Medio | Medium-High (aggiunge a A o B) |
| Latenza messaggio | Da secondi a minuti | Da minuti a ore/giorni (attesa configurabile) | Come opzione sottostante (A o B) |
| Controllo autoconversione | No | Sì (tramite condizione o criteri di uscita) | Dipende dall’opzione sottostante |
| Protezione della frequenza | Nessuno (a meno che non sia combinato con C) | Nessuno (a meno che non sia combinato con C) | Sì - Limiti di canale e raffreddamento del rientro |
| Nodi area di lavoro percorso | 3-4 (evento, condizione facoltativa, azione, fine) | 5-7 (evento, attesa, condizione, rami, azione, termina) | Come A o B, più la configurazione della regola business |
| Richiede | Schema dell’evento, superficie di canale, contenuto del messaggio | Tutte le opzioni A + acquisizione evento di conversione | Tutte le opzioni A o B + configurazione della regola di frequenza |

### Scegli l’opzione giusta

Utilizza la seguente guida decisionale per selezionare l’opzione di implementazione corretta.

1. **Il messaggio deve essere inviato immediatamente senza ritardi?** In caso affermativo, iniziare con **l&#39;opzione A**. I messaggi di conferma, le e-mail di benvenuto e le conferme in genere non richiedono un periodo di attesa.

2. **Il cliente deve avere il tempo di effettuare la conversione automatica prima di ricevere il messaggio?** In caso affermativo, scegliere **Opzione B**. I casi di utilizzo di abbandono del carrello, abbandono del browser e scadenza della versione di prova beneficiano di un periodo di attesa che consente ai clienti di completare l’azione da soli.

3. **L&#39;evento di attivazione è ad alta frequenza (si verifica più volte per sessione o al giorno per lo stesso profilo)?** In caso affermativo, aggiungere **l&#39;opzione C** come sovrapposizione all&#39;opzione A o B. Le visualizzazioni di prodotto, le visualizzazioni di pagina e gli eventi di ricerca possono generare elevati volumi di trigger che richiedono la protezione della frequenza.

4. **Nella sandbox sono attivi più percorsi e campagne attivati?** In caso affermativo, aggiungere **l&#39;opzione C** indipendentemente dalla frequenza degli eventi per gestire il carico di comunicazione tra percorsi e impedire l&#39;affaticamento dei canali.

In pratica, la maggior parte delle implementazioni di produzione utilizza le opzioni B + C per i casi di utilizzo in stile abbandono (attesa condizionale con governance della frequenza) e le opzioni A + C per i casi di utilizzo in stile conferma (invio immediato con governance della frequenza come rete di sicurezza).

## Fasi di implementazione

Le seguenti fasi descrivono l’implementazione end-to-end della messaggistica attivata da eventi.

### Fase 1: configurare lo schema evento e la raccolta dati

**Funzione applicazione:** AEP: Modellazione dati (F2), AEP: Origini dati e raccolta (F3)

**Configurazione:** lo schema XDM ExperienceEvent che acquisisce l&#39;evento di attivazione, il set di dati che memorizza tali eventi e la pipeline di raccolta dati in tempo reale (Web SDK, Mobile SDK o API server) che invia gli eventi ad AEP. Questa fase stabilisce le basi di dati che il percorso ascolterà.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: attivazione del tipo di evento**
>
>Quale evento attiva il messaggio? Il tipo di evento determina i campi dello schema richiesti e il metodo di raccolta.
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Evento Commerce (aggiunta al carrello, acquisto, pagamento) | Casi di utilizzo di e-commerce: abbandono del carrello, post-acquisto | Richiede un gruppo di campi Commerce con `productListItems`, `cart`, `order` campi |
>| Evento di interazione web (visualizzazione pagina, visualizzazione prodotto) | Abbandono della navigazione, trigger di coinvolgimento dei contenuti | Richiede il gruppo di campi Dettagli Web con `webPageDetails`, `webInteraction` campi |
>| Evento dell’applicazione (installazione, disinstallazione, azione in-app) | Trigger del coinvolgimento mobile | Richiede l&#39;implementazione di Mobile SDK e il gruppo di campi Applicazione |
>| Evento di sistema (errore di pagamento, modifica abbonamento, aggiornamento stato) | Notifiche operative | Richiede l’API lato server o il connettore di origine per acquisire gli eventi di sistema |
>| Evento di invio modulo | Generazione di lead, conferma di iscrizione | Richiede un gruppo di campi personalizzato per l&#39;acquisizione dei campi dati del modulo |

>[!NOTE]
>
>**Decisione: metodo di raccolta**
>
>In che modo l’evento che scatena l’attivazione verrà acquisito e trasmesso in streaming ad AEP?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Web SDK | Eventi comportamentali basati sul web (aggiunte al carrello, visualizzazioni di pagina, invio di moduli) | Richiede l’installazione di Web SDK sul sito web; gli eventi vengono trasmessi in streaming in tempo reale tramite Edge Network |
>| Mobile SDK | Eventi nell’app mobile (apertura dell’app, azioni in-app, registrazione del token push) | Richiede l’integrazione di Mobile SDK nell’app nativa o nel wrapper React Native |
>| API server di Edge Network | Eventi di sistema lato server (elaborazione dei pagamenti, gestione degli abbonamenti, trigger back-end) | Nessuna dipendenza lato client; eventi inviati dai sistemi back-end dell&#39;organizzazione |
>| Connettore Source | Eventi da sistemi esterni (CRM, automazione del marketing, piattaforme legacy) | In genere basato su batch; potrebbe non supportare l’attivazione in tempo reale a meno che non sia compatibile con lo streaming |

**Navigazione interfaccia utente:** Raccolta dati > Datastream > Nuovo datastream (per l&#39;impostazione dello stream di dati); Schemi > Crea schema (per lo schema evento); Set di dati > Crea set di dati dallo schema (per la creazione di set di dati)

**Dettagli configurazione chiave:**

- Lo schema evento deve includere tutti i campi necessari per la valutazione delle condizioni del percorso e la personalizzazione dei messaggi
- Lo stream di dati deve avere entrambi i servizi [!DNL Adobe Experience Platform] e [!DNL Adobe Journey Optimizer] abilitati
- Il set di dati deve essere abilitato per Real-Time Customer Profile in modo che gli eventi siano associati a profili unificati
- I dati evento devono includere un campo di identità (e-mail, ID CRM, ECID) che può essere risolto in un profilo noto

**Documentazione di Experience League:**

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Panoramica dell’API del server Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Panoramica sull’acquisizione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)

### Fase 2: configurare identità e profilo

**Funzione applicazione:** AEP: configurazione identità e profilo (F4)

**Configura:** spazi dei nomi di identità per gli identificatori nell&#39;evento di attivazione, designazione dell&#39;identità primaria nello schema dell&#39;evento, regole di collegamento dell&#39;identità per la risoluzione tra dispositivi e criteri di unione per l&#39;unificazione dei profili. In questo modo l’evento che scatena l’attivazione viene associato a un profilo cliente unificato, in modo che il percorso possa risolvere le informazioni di contatto e recapitare il messaggio.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: identità primaria per lo schema evento**
>
>Quale campo di identità nell’evento che scatena l’attivazione deve fungere da identità primaria per la risoluzione del profilo?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Indirizzo e-mail | Eventi da sessioni web autenticate o moduli in cui viene acquisita l’e-mail | Risoluzione diretta di un’identità contattabile; percorso più semplice per la consegna e-mail |
>| ID CRM | Eventi da sistemi autenticati in cui l’ID del sistema di gestione delle relazioni con i clienti è l’identificatore primario | Richiede la creazione dello spazio dei nomi dell’ID del sistema di gestione delle relazioni con i clienti; il profilo deve avere un indirizzo e-mail o un telefono collegato per la consegna dei messaggi |
>| ECID (Experience Cloud ID) | Eventi web o app anonimi in cui non è disponibile alcuna identità autenticata | Richiede l’unione di identità per collegare ECID a un’identità nota; i messaggi non possono essere inviati solo a ECID |
>| Numero di telefono | Eventi da interazioni con dispositivi mobili o con call center | Supporta la consegna SMS; richiede lo spazio dei nomi del telefono |

**Navigazione interfaccia utente:** identità > Crea spazio dei nomi identità; Schemi > Seleziona schema > Seleziona campo > Identità > Imposta come identità primaria; Profili > Criteri di unione

**Dettagli configurazione chiave:**

- Gli eventi anonimi (solo ECID) non possono attivare la consegna dei messaggi finché l’ECID non viene collegato a un’identità contattabile nota (e-mail, telefono) tramite il grafico delle identità
- Il criterio di unione utilizzato da AJO deve essere coerente con quello utilizzato per la valutazione del pubblico
- Per i messaggi attivati basati sul web, assicurati che il grafico delle identità colleghi l’ECID alle identità autenticate tramite eventi di accesso

**Documentazione di Experience League:**

- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Regole di collegamento del grafo identità](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Fase 3: impostazione delle superfici di canale

**Funzione applicazione:** AJO: Configurazione canale

**Configurazione:** la superficie di canale (predefinito) che definisce l&#39;infrastruttura di invio del messaggio attivato: delega del sottodominio, pool IP, identità del mittente, indirizzo di risposta, gestione degli annullamenti dell&#39;abbonamento e credenziali specifiche del canale (provider SMS, certificati push). Prima di poter creare il contenuto del messaggio o pubblicare i percorsi, è necessario che esista una superficie di canale valida.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: canale messaggi**
>
>Quale canale utilizzerà il messaggio attivato?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| E-mail | La maggior parte dei casi di utilizzo della messaggistica attivati: recupero dell’abbandono, conferme, onboarding | Richiede la delega dei sottodomini, il pool IP e la configurazione del mittente; supporta la personalizzazione e il contenuto avanzati di HTML |
>| SMS | Notifiche sensibili al tempo, avvisi concisi, tipi di pubblico con elevato coinvolgimento SMS | Richiede l’integrazione del provider SMS (Sinch, Twilio, Infobip); soggetto a limiti di caratteri e requisiti di consenso più severi |
>| Notifica push | Coinvolgimento con le app mobili, coinvolgimento degli utenti delle app | Richiede la configurazione delle credenziali push (APN per iOS, FCM per Android); l’utente deve avere l’app installata con il push abilitato |
>| Più canali | Strategia di coinvolgimento completa utilizzando la preferenza del canale o la logica di fallback | Richiede più superfici di canale; la selezione del canale può essere gestita tramite nodi condizione di percorso |

>[!NOTE]
>
>**Decisione: metodo di delega del sottodominio (e-mail)**
>
>Come deve essere delegato il sottodominio di invio dell’e-mail ad Adobe?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Delega completa | L’organizzazione desidera che Adobe gestisca tutti i record DNS per il sottodominio di invio | Configurazione più semplice: Adobe gestisce automaticamente i record SPF, DKIM e DMARC |
>| Delega CNAME | L’organizzazione vuole mantenere il controllo DNS puntando all’infrastruttura Adobe | Richiede la gestione manuale dei record DNS; fornisce un maggiore controllo organizzativo sul DNS |

**Navigazione interfaccia utente:** Amministrazione > Canali > Sottodomini (per la configurazione del sottodominio); Amministrazione > Canali > Pool IP (per la configurazione del pool IP); Amministrazione > Canali > Superfici canale > Crea superficie (per la creazione di superfici)

**Dettagli configurazione chiave:**

- La verifica dei sottodomini e la propagazione DNS possono richiedere fino a 48 ore
- I nuovi pool IP richiedono un piano di riscaldamento (2-4 settimane di aumento graduale del volume)
- Configurare le intestazioni con un solo clic per annullare l’iscrizione per la conformità e-mail
- Per gli SMS, configura le credenziali del provider prima di creare la superficie di canale SMS
- Per il push, configura le credenziali APN e FCM prima di creare la superficie del canale push

**Documentazione di Experience League:**

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delega sottodomini](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Creare pool IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Impostare le superfici di canale](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configurare il canale SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Fase 4: Creare il contenuto del messaggio

**Funzione applicazione:** AJO: authoring dei messaggi

**Configurazione:** il contenuto del messaggio che verrà consegnato dal percorso, inclusi la progettazione del layout, i token di personalizzazione mediante attributi di profilo ed eventi, i blocchi di contenuto condizionali, i frammenti riutilizzabili (intestazioni, piè di pagina, dichiarazioni di non responsabilità), l&#39;anteprima e il test del contenuto.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: approccio contenuto**
>
>Come creare il contenuto del messaggio?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Inizia da un modello esistente | Esistono modelli organizzativi ed è richiesta la coerenza del brand | Percorso più rapido per la creazione di contenuti; garanzia di conformità al brand; le modifiche al modello si propagano ai nuovi messaggi |
>| Progettare da zero in E-mail Designer | Layout personalizzato necessario per questo messaggio attivato specifico | Controllo creativo completo; editor visivo con trascinamento; più lento ma flessibile |
>| Importa HTML | Il contenuto è progettato da un team o da un’agenzia esterna e fornito come HTML | Richiede competenze di codifica HTML; potrebbe non supportare completamente tutte le funzioni di E-mail Designer |

>[!NOTE]
>
>**Decisione: personalizzazione evento**
>
>Quali dati evento devono essere utilizzati nel contenuto del messaggio?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Attributi contestuali dell’evento | Il messaggio deve includere i dettagli dell’evento che scatena l’attivazione (nome del prodotto, valore del carrello, campi del modulo) | Utilizza gli attributi dell’evento contestuale nell’editor di personalizzazione; i dati provengono dal payload dell’evento che attiva |
>| Attributi del profilo | Il messaggio deve includere dati a livello di profilo (nome, livello fedeltà, posizione) | Utilizza gli attributi del profilo tramite percorsi XDM (ad esempio, `profile.person.name.firstName`); i dati provengono dal profilo unificato |
>| Attributi evento e profilo | Il messaggio deve combinare il contesto dell’evento con la personalizzazione del profilo | Approccio più comune per i messaggi attivati; garantisce rilevanza (evento) e personalizzazione (profilo) |

**Navigazione interfaccia utente:** Gestione contenuto > Modelli di contenuto > Sfoglia (per la selezione di modelli); Azione campagna o Percorso > Modifica contenuto > Designer e-mail (per la progettazione di contenuti); Seleziona componente testo > icona Personalization (per l&#39;aggiunta della personalizzazione)

**Dettagli configurazione chiave:**

- Utilizza attributi contestuali da personalizzare con i dati dell’evento che scatena l’attivazione (ad esempio, nome del prodotto, valore del carrello)
- Utilizza gli attributi del profilo per i dati di nome, preferenze e fedeltà
- Configura i blocchi di contenuto condizionale per variare il contenuto in base al segmento o all’attributo del profilo (ad esempio, CTA diverso per i membri fedeltà)
- Crea frammenti riutilizzabili per intestazioni, piè di pagina e disclaimer legali condivisi tra i messaggi attivati
- Anteprima con più profili di test per verificare che i rendering di personalizzazione siano corretti
- Inviare bozze alle parti interessate interne prima di pubblicare il percorso

**Documentazione di Experience League:**

- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilizzare i frammenti di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anteprima e test del contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Phase 5: Create and configure the journey

**Application Function:** AJO: Journey Orchestration, AJO: Frequency &amp; Business Rules (Option C), AJO: Conflict &amp; Priority Management

**What you will configure:** The journey that listens for the triggering event and orchestrates message delivery. This is the core implementation phase where the journey canvas is designed with the event entry node, condition nodes, wait steps (for Option B), message action nodes, and exit criteria. This phase also covers frequency governance (Option C) and conflict/priority configuration.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decision: Re-entry rules**
>
>Can a profile re-enter this journey if the triggering event occurs again?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Allow re-entry (with cooldown) | The event can legitimately recur and each occurrence warrants a message (e.g., each cart abandonment should trigger a recovery message) | Set a cooldown period (minimum 5 minutes) to prevent rapid re-entry from duplicate events; typical cooldown ranges from 1 hour to 72 hours |
>| No re-entry | The message should only be sent once per profile regardless of event recurrence (e.g., welcome message after first registration) | Profile is permanently excluded after first journey completion; appropriate for one-time lifecycle messages |

>[!NOTE]
>
>**Decision: Wait duration (Option B only)**
>
>How long should the journey wait before evaluating conditions and sending the message?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Attesa breve (1-4 ore) | Casi d’uso altamente urgenti, come l’abbandono del carrello, in cui è efficace un follow-up immediato | Volume di messaggi più elevato; può rilevare alcuni auto-convertitori; ideale per il recupero del carrello ad alto valore |
>| Attesa Medium (12-24 ore) | Casi di utilizzo di moderata urgenza come abbandono della navigazione o coinvolgimento di contenuti | Approccio equilibrato; riduce gli invii inutili mantenendo al tempo stesso la rilevanza |
>| Attesa lunga (2-7 giorni) | Casi d’uso di bassa urgenza come promemoria di scadenza della sperimentazione o check-in periodici | Riduzione del volume dei messaggi; rischio maggiore di perdita di rilevanza contestuale |
>| Data/ora personalizzata | Casi d’uso associati a una data specifica (ad esempio, invio 3 giorni prima della data di scadenza della sperimentazione) | Attendi fino a una data/ora calcolata; utilizza l’editor di espressioni personalizzate |

>[!NOTE]
>
>**Decisione: criteri di uscita**
>
>In quali condizioni un profilo deve essere rimosso dal percorso prima di raggiungere l’azione del messaggio?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Evento di conversione (ad esempio, acquisto completato) | Abbandono del carrello o della navigazione dove l’obiettivo è la conversione | Il profilo viene chiuso automaticamente quando viene rilevato l’evento di conversione; approccio più pulito per l’opzione B |
>| Modifica dell’iscrizione al pubblico | Il profilo deve uscire se lascia un segmento idoneo | Richiede un pubblico valutato in streaming che si aggiorna quasi in tempo reale |
>| Timeout percorso (massimo 91 giorni) | Comportamento predefinito: il profilo viene chiuso dopo la durata massima del percorso | Rete di sicurezza; non deve essere il principale meccanismo di uscita per percorsi attivati di breve durata |
>| Nessun criterio di uscita esplicito | Conferme semplici (opzione A) in cui ogni profilo idoneo deve ricevere il messaggio | Il profilo viene chiuso naturalmente dopo l’azione del messaggio e il nodo finale |

>[!NOTE]
>
>**Decisione: governance della frequenza (opzione C)**
>
>Quanti messaggi attivati deve ricevere un profilo per periodo di tempo?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Limiti specifici per il canale (ad esempio, 3 e-mail/settimana, 1 SMS/giorno) | Canali diversi hanno soglie di affaticamento diverse | Approccio consigliato; rispetta il livello di intrusività di ciascun canale |
>| Limite globale (ad esempio, 5 messaggi/settimana su tutti i canali) | Governance semplificata per tutti i tipi di comunicazione | Più semplice da gestire, ma con meno sfumature; può limitare eccessivamente i canali meno invasivi |
>| Solo raffreddamento del rientro a livello di percorso | Governance della frequenza necessaria per questo percorso specifico ma non a livello di organizzazione | Implementazione più semplice; non protegge dall’affaticamento tra percorsi |

**Navigazione interfaccia utente:** Percorsi > Crea Percorso (per la creazione di percorsi); Area di lavoro Percorso > Trascina attività evento (per l&#39;immissione di eventi); Area di lavoro Percorso > Trascina attività &quot;Attesa&quot; (per la configurazione di attesa); Area di lavoro Percorso > Trascina attività &quot;Condizione&quot; (per il diramazione delle condizioni); Proprietà Percorso > Criteri di uscita (per la configurazione di uscita); Amministrazione > Regole business > Crea regola (per i limiti di frequenza)

**Dettagli configurazione chiave:**

- Configurare l’evento di percorso selezionando lo schema dell’evento e definendo le condizioni di idoneità
- Per l’opzione B, aggiungi il nodo di attesa immediatamente dopo l’immissione dell’evento e prima di qualsiasi valutazione della condizione
- Configurare i nodi delle condizioni utilizzando gli attributi di profilo, i dati evento o i controlli di appartenenza al pubblico
- Collega il nodo dell’azione del messaggio alla superficie di canale e al contenuto creato dalle fasi 3 e 4
- Imposta il timeout percorso su una durata appropriata (inferiore a 91 giorni per i percorsi attivati)
- Per l’opzione C, crea regole di frequenza tramite Amministrazione > Regole aziendali prima di pubblicare il percorso
- Assegna un punteggio di priorità al percorso se altre campagne o altri percorsi sono rivolti a tipi di pubblico sovrapposti

**Opzioni divergenti:**

**Per L&#39;Opzione A (Attivata Da Un Semplice Evento):**
L’area di lavoro del percorso è minima: voce evento > consenso facoltativo/condizione di idoneità > azione messaggio > fine. Nessun passaggio di attesa o controllo della conversione. Impostare le regole di reinserimento in base all&#39;eventualità che l&#39;evento generi un messaggio ogni volta che si verifica.

**Opzione B (condizionale con attesa):**
Aggiungi un nodo di attesa dopo l’immissione dell’evento. Dopo l’attesa, aggiungi un nodo condizione per verificare la conversione (ad esempio, verifica se l’evento `commerce.purchases` si è verificato dopo l’ingresso nel percorso) oppure utilizza i criteri di uscita per rimuovere automaticamente i profili convertiti. Diramare all&#39;azione del messaggio nel percorso &quot;non convertito&quot; e a un nodo finale nel percorso &quot;convertito&quot;.

**Per L&#39;Opzione C (Governance Della Frequenza):**
Configurare i limiti di frequenza a livello di organizzazione tramite Amministrazione > Regole aziendali prima della pubblicazione. Impostare il raffreddamento del rientro a livello di percorso nelle proprietà del percorso. Facoltativamente, assegna un punteggio di priorità tramite le proprietà del percorso per controllare quale comunicazione vince quando vengono raggiunte le maiuscole. Questa opzione può essere applicata sopra l’opzione A o l’opzione B.

**Documentazione di Experience League:**

- [Creazione di un percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Proprietà del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Eventi generali](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Attività Condizione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Attività Attendi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Aggiungere un messaggio in un percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Criteri di uscita](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Gestione voci percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Regole di frequenza](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Punteggi di priorità](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identificare potenziali conflitti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Fase 6: Test e implementazione del percorso

**Funzione applicazione:** AJO: Journey Orchestration

**Configurazione:** convalida della modalità di test per verificare che il percorso si comporti come previsto con i profili di test, seguita dalla pubblicazione del percorso per renderlo attivo.

**Navigazione interfaccia utente:** area di lavoro Percorsi > Attiva/Disattiva modalità test (per test); area di lavoro Percorsi > Pubblica (per distribuzione)

**Dettagli configurazione chiave:**

- Abilita la modalità di test nell’area di lavoro del percorso per simulare trigger di evento con i profili di test
- Seleziona i profili di test con informazioni di contatto del canale valide (indirizzo e-mail, numero di telefono)
- Attiva l&#39;evento di test e verifica che il profilo di test attraversi il percorso previsto
- Per l’opzione B, verifica che il passaggio di attesa si comporti correttamente e che la valutazione della condizione produca la diramazione prevista
- Verifica che il rendering dei token di personalizzazione sia corretto nel messaggio di test
- Dopo aver superato il test, pubblica il percorso per renderlo live
- Monitorare lo stato del percorso e le metriche iniziali di immissione profilo dopo la pubblicazione

**Documentazione di Experience League:**

- [Test del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Pubblicare il percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### Fase 7: monitoraggio e creazione di report sulle prestazioni

**Funzione Applicazione:** AJO: Reporting &amp; Performance Analysis, S4: Monitoring &amp; Observability, S5: Reporting &amp; Analysis

**Configura:** rapporti live e cronologici sul percorso per il monitoraggio della consegna e del coinvolgimento, avvisi sulla piattaforma per l&#39;inserimento di eventi e errori di elaborazione del percorso e, facoltativamente, aree di lavoro CJA per un&#39;analisi cross-channel più approfondita dell&#39;efficacia dei messaggi attivati.

**Punti decisionali in questa fase:**

>[!NOTE]
>
>**Decisione: profondità di reporting**
>
>Quanta analisi di reporting è necessaria per questo caso d’uso?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Solo rapporti nativi di AJO | È sufficiente il monitoraggio operativo delle metriche di consegna | Disponibile immediatamente; copertine inviate, consegnate, non consegnate, aperte, cliccate; nessuna configurazione aggiuntiva necessaria |
>| Integrazione nativa e CJA di AJO | Sono necessarie analisi cross-channel, attribuzione di conversione e analisi delle tendenze | Richiede connessione CJA e visualizzazione dati collegata ai set di dati di AJO; fornisce funzionalità di analisi più approfondite |

**Navigazione interfaccia utente:** Percorsi > Seleziona percorso > Live Report (per il monitoraggio in tempo reale); Percorsi > Seleziona percorso > All time report (per l&#39;analisi cronologica); Avvisi > Regole avviso > Abbonati (per la configurazione degli avvisi)

**Dettagli configurazione chiave:**

- Durante l’esecuzione attiva, accedi al rapporto live del percorso per monitorare le voci, le uscite e le metriche di consegna del profilo
- Rivedi il rapporto cronologico dopo che il percorso è stato attivo per un tempo sufficiente ad accumulare dati significativi
- Configurare gli avvisi per gli errori di esecuzione del flusso di origine (inserimento degli eventi) e i ritardi di elaborazione del percorso
- Per l’integrazione con CJA, assicurati che la connessione CJA includa i set di dati dell’evento esperienza di AJO (set di dati dell’evento di feedback del messaggio, set di dati dell’evento di tracciamento e-mail)

**Documentazione di Experience League:**

- [Rapporto live del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Panoramica degli avvisi](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Considerazioni sull’implementazione

Questa sezione descrive guardrail, insidie comuni, best practice e decisioni di compromesso per le implementazioni di messaggistica attivate da eventi.

### Guardrail e limiti

I seguenti guardrail e limiti della piattaforma si applicano alle implementazioni di messaggistica attivate da eventi.

- **Velocità effettiva evento unitaria:** massimo 5.000 eventi al secondo per sandbox per percorsi di eventi unitari — [Guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- **Limite percorso live:** Massimo 500 percorsi live per sandbox — [Guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- **Limite area di lavoro Percorsi:** Massimo 50 attività per area di lavoro percorso
- **Timeout Percorso:** La durata massima del percorso è di 91 giorni (timeout globale)
- **Ripristino del valore di ripristino:** Il valore minimo di ripristino del valore di ripristino è di 5 minuti
- **Configurazioni del limite di frequenza:** Massimo 10 configurazioni di limite per sandbox
- **Superfici di canale:** massimo 10 superfici di canale per tipo di canale per sandbox
- **Acquisizione in streaming:** massimo 20.000 record al secondo per connessione HTTP - [Guardrail di acquisizione](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- **Attributi calcolati:** massimo di 25 attributi calcolati per sandbox — [Guardrail attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview#guardrails)
- **Frammenti di contenuto:** massimo 30 frammenti di contenuto per messaggio
- **Aggiornamento dei rapporti live:** I rapporti live vengono aggiornati ogni 60 secondi e mostrano le ultime 24 ore di dati
- **Latenza report cronologico:** I report cronologici (tutti i tempi) possono richiedere fino a 2 ore per essere compilati completamente al termine dell&#39;esecuzione

### Insidie comuni

Tieni presente i seguenti problemi comuni durante l’implementazione della messaggistica attivata da eventi.

- **Eventi anonimi senza risoluzione identità:** Gli eventi che attivano solo un ECID (ID cookie anonimo) non possono essere risolti in un profilo contattabile per la consegna dei messaggi. Assicurati che l’evento che attiva includa un’identità autenticata o che il grafo delle identità colleghi l’ECID a un contatto noto. Senza la risoluzione dell’identità, i profili entrano nel percorso ma non riescono nel passaggio di consegna del messaggio.

- **Evento di conversione mancante per i controlli delle condizioni dell&#39;opzione B:** Se l&#39;evento di conversione (ad esempio, l&#39;acquisto) non viene acquisito in AEP o non è associato alla stessa identità di profilo dell&#39;evento di attivazione, il controllo delle condizioni non verrà valutato correttamente come &quot;non convertito&quot; e invierà messaggi non necessari. Verifica che gli eventi di conversione fluiscano in AEP in tempo reale e condividi un’identità con l’evento che scatena l’attivazione.

- **Regole di reinserimento eccessivamente permissive:** Consentendo il reinserimento senza un periodo di arresto sulle origini eventi ad alta frequenza, lo stesso profilo può ricevere più messaggi in pochi minuti. Imposta sempre un raffreddamento di rientro corrispondente al contesto aziendale (ad esempio, un raffreddamento di 4 ore per l’abbandono del carrello e un raffreddamento di 24 ore per l’abbandono della navigazione).

- **Disallineamento fuso orario passaggio di attesa:** Processo passaggi di attesa in UTC per impostazione predefinita. Se il percorso esegue il targeting dei profili su più fusi orari e l’attesa deve essere allineata all’ora locale del destinatario, configura di conseguenza le impostazioni del fuso orario sul percorso.

- **Limiti di frequenza in conflitto con altre campagne:** I limiti di frequenza a livello di organizzazione si applicano a tutte le campagne e ai percorsi. Un nuovo percorso attivato può essere eliminato se i profili hanno già raggiunto il limite da altre campagne attive. Monitora il tasso di soppressione e regola i punteggi di priorità per garantire che i messaggi attivati importanti abbiano la priorità.

- **Errore di pubblicazione Percorso a causa di dipendenze mancanti:** Ogni ramo nell&#39;area di lavoro del percorso deve terminare con un&#39;attività finale. Tutti i nodi di azione devono fare riferimento a superfici di canale valide con contenuto del messaggio attivo. Verifica tutte le dipendenze prima di pubblicarle.

### Best practice

Segui queste raccomandazioni per implementazioni di messaggistica attivate da eventi di successo.

- **Inizia semplice, quindi ripeti:** Inizia con l&#39;opzione A per i nuovi casi d&#39;uso dei messaggi attivati. Aggiungi logica di attesa e condizione (opzione B) solo dopo la convalida della pipeline dell’evento e della consegna del messaggio. Aggiungere la governance della frequenza (opzione C) quando sono attivi più percorsi attivati.

- **Utilizzare i criteri di uscita invece dei nodi condizione per i controlli di conversione:** I criteri di uscita rimuovono automaticamente i profili dal percorso quando si verifica un evento qualificante (ad esempio, l&#39;acquisto), eliminando la necessità di un nodo condizione esplicito dopo il passaggio di attesa. Questo produce un’area di lavoro del percorso più pulita e un rilevamento della conversione più reattivo.

- **Verifica con i dati evento reali in una sandbox di sviluppo:** Utilizza la modalità di test con i payload degli eventi effettivi (non solo i profili di test) per verificare che i campi dello schema dell&#39;evento, i token di personalizzazione e le espressioni di condizione funzionino correttamente con i dati di tipo produzione.

- **Impostare i limiti di rientro specifici per l&#39;evento:** Impostare il periodo di blocco sul contesto aziendale dell&#39;evento che attiva. I percorsi di abbandono del carrello utilizzano in genere un raffreddamento di 4-24 ore; i percorsi di conferma possono consentire un rientro immediato; i percorsi di onboarding devono impedire completamente il rientro.

- **Monitora il tasso di soppressione come metrica di integrità:** Se il tasso di eliminazione (profili qualificati ma che non ricevono messaggi a causa di limiti o condizioni di frequenza) supera il 30-40%, verifica se i limiti sono troppo restrittivi o se l&#39;evento che attiva è definito in modo troppo ampio.

- **percorsi versione invece di modificare quelli live:** Non è possibile modificare direttamente un percorso live. Crea una nuova versione duplicando il percorso, apportando modifiche, quindi interrompendo la versione precedente e pubblicando quella nuova. In questo modo si evitano interruzioni dei profili attualmente nel percorso.

- **Includi un percorso di fallback/predefinito nei nodi condizione:** Configura sempre un percorso predefinito (else) nei nodi condizione per gestire gli stati di profilo imprevisti. I profili che non corrispondono a nessun ramo della condizione devono uscire correttamente anziché rimanere bloccati.

### Decisioni di compromesso

Considera i seguenti compromessi durante la progettazione dell’implementazione della messaggistica attivata da eventi.

>[!NOTE]
>
>**Compensazione: velocità del messaggio rispetto alla rilevanza del messaggio**
>
>La consegna immediata dei messaggi (opzione A) massimizza la velocità, ma può inviare messaggi ai clienti che si sarebbero autoconvertiti. La consegna condizionale ritardata (opzione B) migliora la rilevanza filtrando gli autoconvertitori, ma introduce una latenza che può ridurre l’urgenza.
>
>- **L&#39;opzione A favorisce:** Casi d&#39;uso rapidi, semplici e di tipo di conferma in cui ogni evento giustifica un messaggio
>- **L&#39;opzione B favorisce:** pertinenza, minore affaticamento dei messaggi, casi di utilizzo in stile abbandono in cui l&#39;autoconversione è comune
>- **Consiglio:** utilizzare l&#39;opzione A per i messaggi transazionali e di conferma in cui la velocità è il valore principale. Utilizzare l&#39;opzione B per i messaggi di ripristino e reinserimento quando la rilevanza supera la velocità. Sperimenta le durate di attesa per trovare il saldo ottimale per ogni caso d’uso.

>[!NOTE]
>
>**Compensazione: protezione della frequenza rispetto alla copertura dei messaggi**
>
>Limiti di frequenza rigidi (opzione C) impediscono l’affaticamento, ma possono sopprimere importanti messaggi attivati quando i profili sono vicini al limite. I limiti permissivi o nulli massimizzano la copertura, ma rischiano di sovraccaricare la messaggistica e l’affaticamento del canale.
>
>- **Limiti rigorosi favore:** Esperienza del cliente, reputazione del brand, recapito messaggi (meno reclami di spam)
>- **Limiti permissivi favore:** Copertura dei messaggi, opportunità di conversione, evitare trigger mancanti
>- **Consiglio:** inizia con i limiti standard del settore (3-5 e-mail/settimana, 1-2 SMS/settimana, 2-3 push/giorno) e regola in base alle metriche di coinvolgimento e alle percentuali di annullamento dell&#39;abbonamento. Assegna punteggi di priorità più elevati ai messaggi attivati in modo che prevalgano sulle campagne batch quando vengono raggiunti i limiti.

>[!NOTE]
>
>**Compensazione: semplicità del Percorso e sofisticazione del percorso**
>
>I percorsi semplici (pochi nodi, nessuna diramazione) sono più facili da creare, testare e mantenere, ma offrono un adattamento contestuale limitato. I percorsi sofisticati (condizioni multiple, percorsi di diramazione, controlli dei segmenti) consentono risposte più sfumate, ma aumentano la complessità e il rischio di errori.
>
>- **percorsi semplici favoriscono:** implementazione più rapida, debug più semplice, minore onere di manutenzione
>- **percorsi sofisticati favoriscono:** Impostazione destinazione più precisa, personalizzazione migliore, riduzione degli invii non necessari
>- **Consiglio:** inizia con il percorso più semplice che soddisfa i requisiti aziendali. Aggiungere complessità in modo incrementale in base ai dati sulle prestazioni. Un percorso semplice che funziona in modo affidabile è più utile di un percorso complesso con errori non rilevati.

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sulle funzionalità utilizzate in questa implementazione.

### Orchestrazione percorso

- [Introduzione ai percorsi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Creazione di un percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Proprietà del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Eventi generali](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Eventi di qualificazione del pubblico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Attività Condizione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Attività Attendi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Aggiungere un messaggio in un percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Criteri di uscita](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Gestione voci percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Test del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Pubblicare il percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

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
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Funzioni di supporto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilizzare i frammenti di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anteprima e test del contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Creare un messaggio SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Progettare una notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### Frequenza e regole aziendali

- [Regole di frequenza](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Panoramica sulle regole business](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Limitazione di utilizzo API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/channel-surfaces/capping)

### Gestione dei conflitti e delle priorità

- [Introduzione alla gestione dei conflitti e delle priorità](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Identificare potenziali conflitti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Punteggi di priorità](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Limitazione di percorso e arbitrato](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### Reporting e prestazioni

- [Rapporto live del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### Raccolta e acquisizione dei dati

- [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Panoramica di Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Panoramica dell’API del server Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Panoramica sull’acquisizione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)

### Modellazione dati e schemi

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### Identità e profilo

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Regole di collegamento del grafo identità](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Panoramica del profilo](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Segmentazione e tipi di pubblico

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

### Governance dei dati e consenso

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview)
- [Gruppo di campi Consenso e preferenze](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Attributi calcolati

- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Guida dell’interfaccia utente attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)

### Monitoraggio e osservabilità

- [Panoramica degli avvisi](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Panoramica di Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### Guardrail

- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Guardrail di acquisizione](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Tutorial e guide

- [Tutorial sulla creazione di un percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Installare Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
