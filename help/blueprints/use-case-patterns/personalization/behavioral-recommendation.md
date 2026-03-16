---
title: Consigli comportamentali
description: Scopri come generare consigli su elementi e contenuti utilizzando strategie di selezione e modelli di classificazione.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '7626'
ht-degree: 2%

---


# Raccomandazioni comportamentali

Questa guida illustra come implementare i consigli sui contenuti e i prodotti comportamentali utilizzando [!DNL Adobe Journey Optimizer] (AJO) Decisioning, [!DNL Real-Time Customer Data Platform] (RT-CDP) e [!DNL Adobe Experience Platform] (AEP). È progettato per architetti di soluzioni, tecnici di marketing e ingegneri dell’implementazione che devono fornire esperienze di consigli personalizzate su canali web, app mobili ed e-mail.

Presenta tutte le opzioni di implementazione valide, considerazioni sulle decisioni in ogni fase e collegamenti alla documentazione di [!DNL Adobe Experience League]. La funzione Consigli comportamentali genera consigli a livello di elemento o di contenuto utilizzando segnali comportamentali (visualizzazioni di prodotto, acquisti, interazioni di contenuto, query di ricerca) combinati con strategie di selezione e modelli di classificazione di AJO Decisioning. A differenza di offer decisioning, che seleziona da un set curato di offerte di marketing utilizzando regole di idoneità esplicite, questo modello opera su cataloghi di articoli di grandi dimensioni (prodotti, articoli, video) e utilizza segnali di affinità comportamentale e classificazione basata su apprendimento automatico per far emergere gli elementi più rilevanti per ogni visitatore.

## Panoramica del caso d’uso

Le organizzazioni con cataloghi di prodotti, librerie di contenuti o librerie multimediali devono rendere visibili a ogni visitatore gli elementi più rilevanti in base alla cronologia comportamentale e all’attività durante la sessione. Che si tratti di un carosello &quot;consigliato per te&quot; su una pagina home, di un widget di cross-selling su una pagina di dettagli del prodotto o di consigli di prodotto incorporati in una campagna e-mail, la sfida di fondo è la stessa: abbinare il profilo comportamentale di ogni visitatore agli elementi più rilevanti di un catalogo, quindi fornire tali consigli nel canale giusto al momento giusto.

Questo modello affronta tale sfida acquisendo segnali comportamentali in tempo reale tramite [!DNL Web SDK] o [!DNL Mobile SDK], elaborandoli tramite strategie di selezione di AJO Decisioning che combinano gli attributi degli elementi con il contesto comportamentale e distribuendo gli elementi consigliati tramite canali web, in-app o e-mail. I modelli di classificazione possono essere basati su formule (ad esempio, in base al punteggio di affinità tra categorie) o classificati in base all’intelligenza artificiale (ad esempio, modello di consigli personalizzato). Il modello gestisce anche scenari di avvio a freddo per nuovi visitatori senza cronologia comportamentale configurando consigli di fallback.

Il pubblico di destinazione di questo modello include i team di merchandising di e-commerce, i team di personalizzazione dei contenuti e i team di esperienza digitale che desiderano migliorare il coinvolgimento, la conversione e il valore medio dell’ordine attraverso consigli personalizzati basati sul comportamento effettivo degli utenti.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### [Incrementa le vendite incrociate e incrementa i ricavi](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)

Promuovere prodotti o servizi complementari e di alta qualità ai clienti esistenti in base al comportamento e alla cronologia degli acquisti.

| KPI | Descrizione |
| --- | --- |
| % vendite in upselling/cross-selling | Percentuale di clienti che acquistano articoli complementari o premium consigliati |
| Reddito Incrementale | Ricavi aggiuntivi attribuibili ad acquisti basati su consigli |
| Valore ciclo di vita cliente | Aumento del valore a lungo termine derivante da un coinvolgimento più approfondito nei prodotti |

### [Aumentare i tassi di conversione](../../business-objectives/revenue-monetization/increase-conversion-rates.md)

Migliora la percentuale di visitatori e potenziali clienti che completano le azioni desiderate, ad esempio acquisti, iscrizioni o invii di moduli.

| KPI | Descrizione |
| --- | --- |
| Tassi di conversione | Percentuale di visitatori che convertono dopo il coinvolgimento con i consigli |
| Conversione lead | Percentuale di clienti dei visitatori coinvolti nei consigli |
| Costo per lead | Riduzione dei costi di acquisizione grazie al coinvolgimento nella raccomandazione organica |

### [Distribuisci esperienze cliente personalizzate](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

Personalizza contenuti, offerte e messaggi in base a preferenze, comportamenti e fasi del ciclo di vita individuali.

| KPI | Descrizione |
| --- | --- |
| Coinvolgimento | Frequenza di interazione con le superfici di consigli (clic, viste, componente aggiuntivo al carrello) |
| Tassi di conversione | Incremento dei tassi di conversione per i visitatori coinvolti nei consigli rispetto al controllo |
| Soddisfazione del cliente (CSAT) | Miglioramento della soddisfazione del cliente da esperienze pertinenti e personalizzate |

## Esempi di casi d’uso tattici

Di seguito sono riportate le implementazioni tattiche comuni di questo modello:

- Widget di cross-selling del prodotto sulla pagina dei dettagli del prodotto (&quot;anche i clienti hanno acquistato&quot;)
- Carosello &quot;Consigliato per te&quot; sulla home page in base alla cronologia dei browser
- Consigli sui contenuti sul sito multimediale in base al comportamento di lettura
- Widget &quot;Visualizzato di recente&quot; combinato con elementi simili
- Consigli sui prodotti complementari post-acquisto
- Invia raccomandazioni di prodotti e-mail in base all’affinità comportamentale
- Raccomandazioni specifiche per categoria in base al comportamento di navigazione nella sessione
- Nuova classificazione dei risultati di ricerca in base ai segnali comportamentali

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare l’efficacia delle implementazioni di consigli comportamentali.

| KPI | Approccio di misurazione |
| --- | --- |
| Frequenza di click-through dei consigli (CTR) | Clic sugli articoli consigliati divisi per impression di consigli |
| Tasso di conversione consigli | Acquisti o azioni desiderate dai clic sui consigli divisi per il totale dei clic sui consigli |
| Ricavi influenzati dalla funzione Consigli | Ricavi totali da ordini che includevano almeno un prodotto basato su consigli |
| Incremento valore medio ordine (AOV) | Aumento del valore medio dell’ordine per le sessioni che richiedono consigli rispetto a quelle senza |
| Articoli per ordine | Numero di elementi per ordine per le sessioni di consigli |
| Copertura consigli | Percentuale di visualizzazioni di pagina o sessioni idonee che hanno ricevuto consigli personalizzati (non di fallback) |
| Percentuale di fallback con avviamento a freddo | Percentuale di richieste di consigli servite dalla logica di fallback a causa di una cronologia comportamentale insufficiente |

## Schema del caso d’uso

**Consigli comportamentali**

Genera consigli a livello di elemento o di contenuto in base ai segnali comportamentali, utilizzando le strategie di selezione di AJO Decisioning e i modelli di classificazione per distribuire i contenuti contestuali.

**Catena di funzioni:** acquisizione segnale comportamentale > Valutazione strategia di decisione > Consegna consigli > Reporting

Consulta la sezione Composizione pattern in Considerazioni sull’implementazione per indicazioni sulla combinazione dei pattern.

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Adobe Journey Optimizer] (AJO) Decisioning** — Strategie di selezione, modelli di classificazione, cataloghi di elementi e criteri decisionali che valutano i segnali comportamentali e restituiscono gli elementi più rilevanti per ogni visitatore
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Accumulo dei dati del profilo comportamentale, valutazione del pubblico per l&#39;ambito dei consigli e attributi calcolati per il punteggio di affinità comportamentale
- **[!DNL Adobe Experience Platform] (AEP)** — Acquisizione di eventi comportamentali tramite [!DNL Web SDK] e [!DNL Mobile SDK], elaborazione di [!DNL Edge Network], gestione dello schema XDM per i dati evento e catalogo

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve esistere | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Presunto sul posto | Sandbox di AJO con autorizzazioni Decisioning abilitate. I ruoli utente dispongono dell&#39;accesso alla gestione del catalogo articoli, alla configurazione della strategia di selezione e all&#39;amministrazione della superficie di canale. | [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home), [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Obbligatorio | Lo schema Experience Event acquisisce segnali comportamentali (visualizzazioni di prodotti, componenti aggiuntivi per il carrello, acquisti, interazioni di contenuti) con identificatori di elementi/prodotti. Schema del catalogo degli articoli (attributi di prodotto, categorie, immagini, prezzi) per il set di articoli da consigliare. Schema di profilo con campi di identità. Tutti gli schemi abilitati per [!DNL Real-Time Customer Profile]. | [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition), [Crea un set di dati](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/create) |
| Origini dati e raccolta | Obbligatorio | Lo streaming degli eventi comportamentali in tempo reale tramite [!DNL Web SDK] o [!DNL Mobile SDK] è fondamentale. La qualità dei consigli dipende da nuovi segnali comportamentali. I dati del catalogo degli articoli devono essere acquisiti (in batch o in streaming). Gli stream di dati configurati con il servizio AJO abilitato per le decisioni di Edge. | [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Panoramica di Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview), [Configura flussi di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Configurazione identità e profilo | Obbligatorio | I segnali comportamentali devono essere associati a un’identità (nota o anonima tramite ECID) per creare profili comportamentali. Per i consigli dei visitatori noti, è necessario configurare l’identità autenticata (ID del sistema di gestione delle relazioni con i clienti, e-mail). Criterio di unione attivo su Edge per la distribuzione di consigli in tempo reale. | [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Panoramica dei criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Definizione e segmentazione del pubblico | Consigliato | I tipi di pubblico possono essere utilizzati per formulare raccomandazioni (ad esempio, per consigliare solo prodotti premium ai membri premium) o per filtrarli. Non strettamente necessario se le raccomandazioni sono puramente comportamentali. Obbligatorio per i consigli basati su e-mail (opzione C) per definire il pubblico target. | [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Guida dell&#39;interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Consigliato | Attributi calcolati come i punteggi di affinità tra categorie, la frequenza di interazione con il prodotto, l’attualità degli acquisti e la spesa totale migliorano la qualità della classificazione dei consigli. [!DNL Customer AI] i punteggi di tendenza possono migliorare ulteriormente la rilevanza prevedendo la probabilità di acquisto. | [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview), [Panoramica di IA per l&#39;analisi dei clienti](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Data Lifecycle Management | Consigliato | I dati relativi agli eventi comportamentali devono prevedere politiche di scadenza appropriate; la rilevanza delle raccomandazioni si riduce con dati obsoleti. L’impostazione di criteri di scadenza dei set di dati sui set di dati degli eventi comportamentali garantisce l’aggiornamento e gestisce l’archiviazione. L’applicazione del consenso garantisce l’utilizzo conforme dei dati comportamentali. | [Scadenze set di dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration), [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Etichettatura e applicazione dell’utilizzo dati | Consigliato | Le etichette di governance sui dati comportamentali garantiscono l’utilizzo conforme della cronologia delle interazioni per i consigli. Particolarmente importante quando i dati comportamentali includono modelli di navigazione, cronologia degli acquisti o segnali di interesse sui prodotti finanziari o sanitari. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview) |
| Monitoraggio e osservabilità | Consigliato | È necessario monitorare la latenza di consegna dei consigli, i tassi di fallback e lo stato di acquisizione del catalogo articoli. Gli avvisi sugli errori di acquisizione degli eventi comportamentali e sugli errori di decisione contribuiscono a mantenere la qualità dei consigli. | [Panoramica di Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home), [Panoramica degli avvisi](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| Reporting e analisi | Incluso | Il reporting sulle prestazioni dei consigli fa parte del passaggio 4 della catena di funzioni. [!DNL Customer Journey Analytics] l’analisi dell’efficacia dei consigli, dell’impatto sui ricavi e delle prestazioni a livello di elemento tra superfici e segmenti fornisce informazioni approfondite sull’ottimizzazione. | [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Journey Optimizer] (AJO)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Decisioni | Impostazione catalogo articoli e strategia di selezione | Configurare cataloghi di elementi (elementi decisionali), strategie di selezione con modelli di classificazione comportamentale, regole di filtro e consigli di fallback |
| Configurazione canali | Configurazione canale e superficie | Configurare superfici di consegna per canali web (esperienze basate su codice), in-app, schede di contenuto o e-mail in cui verrà eseguito il rendering dei consigli |
| Authoring dei messaggi | Configurazione di contenuto e consegna | Progettare modelli di rendering dei consigli, layout di visualizzazione degli elementi ed espressioni di personalizzazione per gli elementi consigliati |
| Reporting e analisi delle prestazioni | Reporting e ottimizzazione | Monitorare le metriche di click-through, conversione e ricavi per i consigli tramite i rapporti nativi di AJO e l&#39;integrazione di [!DNL Customer Journey Analytics] |

### [!DNL Real-Time CDP] (RT-CDP)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Valutazione del pubblico | Ambito pubblico (opzione C) | Valuta i segmenti di pubblico utilizzati per definire i consigli o la popolazione target per le campagne e-mail di consigli |
| Arricchimento del profilo | Arricchimento del segnale comportamentale | Arricchisci i profili con attributi calcolati (punteggi di affinità tra categorie, frequenza di interazione) per migliorare la classificazione dei consigli |

## Prerequisiti

Completa quanto segue prima di iniziare l’implementazione:

- AJO Decisioning viene fornito e abilitato nella sandbox di destinazione
- [!DNL Web SDK] o [!DNL Mobile SDK] è distribuito e sta raccogliendo eventi comportamentali con identificatori di prodotto/contenuto
- I dati del catalogo di prodotti o contenuti sono disponibili per l’acquisizione (nome del prodotto, categoria, prezzo, URL immagine, disponibilità)
- Gli schemi di eventi comportamentali includono identificatori di articolo/prodotto collegati agli elementi del catalogo
- Lo stream di dati è configurato con il servizio [!DNL Adobe Journey Optimizer] abilitato (necessario per le decisioni di Edge)
- Il criterio di unione con `isActiveOnEdge: true` è configurato (obbligatorio per i consigli Web/app in tempo reale)
- Per i consigli sulle e-mail (opzione C): la superficie del canale e-mail è configurata e convalidata
- Per i consigli sulle e-mail (opzione C): il pubblico target è definito e in fase di valutazione

## Opzioni di implementazione

Le opzioni seguenti descrivono diversi approcci per l’implementazione delle raccomandazioni comportamentali. Scegli l’opzione che meglio si adatta ai requisiti dei canali e ai vincoli tecnici.

### Opzione A: consigli web in tempo reale

**Consigliato per:** Consigli per prodotti e contenuti su pagine Web: widget per la cross-selling di pagine di dettagli prodotto, caroselli di consigli per home page, inserzioni personalizzate di pagine categorie e personalizzazione dei risultati di ricerca.

**Funzionamento:**

I segnali comportamentali vengono raccolti in tempo reale tramite [!DNL Web SDK] mentre i visitatori navigano sul sito. Ogni visualizzazione di pagina, interazione del prodotto o query di ricerca viene trasmessa in streaming ad AEP e associata al profilo del visitatore (tramite ECID per i visitatori anonimi o identità autenticata per i visitatori noti). Quando viene caricata una pagina contenente una superficie di consigli, [!DNL Web SDK] richiede una valutazione del decisioning da AJO tramite [!DNL Edge Network]. Il motore delle decisioni valuta il profilo comportamentale del visitatore in base alla strategia di selezione, applica la logica di classificazione, esclude gli articoli non idonei (già acquistati, esauriti) e restituisce gli articoli consigliati.

I consigli vengono sottoposti a rendering sulla pagina tramite esperienze basate su codice o superfici di canali web. Il rendering può essere un carosello, una griglia, un widget a elemento singolo o qualsiasi layout personalizzato definito nel modello di consigli. Gli eventi di impression e clic vengono tracciati automaticamente in AEP per la generazione di rapporti sulle prestazioni.

**Considerazioni chiave:**

- Edge Decisioning richiede che il criterio di unione sia attivo su Edge
- La latenza dei consigli dipende dal tempo di risposta [!DNL Edge Network] (SLA inferiore a 500 ms per richieste con ambito singolo)
- I visitatori anonimi ricevono consigli in base al comportamento durante la sessione; i visitatori noti beneficiano della cronologia comportamentale tra sessioni diverse
- I visitatori con avvio a freddo senza cronologia comportamentale ricevono consigli di fallback

**Vantaggi:**

- Personalizzazione in tempo reale basata sul comportamento durante la sessione
- Consegna dei consigli al secondo secondario tramite [!DNL Edge Network]
- Funziona sia per i visitatori anonimi che per quelli noti
- Impression e tracciamento dei clic automatici
- Non è necessario ricaricare la pagina per aggiornare i consigli

**Limitazioni:**

- L’archivio profili di Edge contiene un sottoinsieme di attributi di profilo completi
- Modelli di classificazione complessi con molti attributi di profilo possono richiedere una valutazione lato hub
- Richiede l&#39;implementazione di [!DNL Web SDK] con il tracciamento degli eventi comportamentali

**Experience League:**

- [Distribuire le offerte tramite l’API Edge Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)

### Opzione B: consigli per le app mobili

**Consigliato per:** consigli di prodotti in-app, feed di contenuti personalizzati, consigli basati su notifiche ed esperienze di e-commerce mobile.

**Funzionamento:**

I segnali comportamentali vengono raccolti tramite [!DNL Mobile SDK] mentre gli utenti interagiscono con l&#39;app. Le visualizzazioni dei prodotti, le interazioni con i contenuti, le ricerche e gli acquisti vengono inviati in streaming ad AEP. Quando viene caricata una schermata contenente una superficie di consigli, [!DNL Mobile SDK] richiede una valutazione del decisioning. I consigli vengono trasmessi tramite messaggi in-app, schede di contenuto o esperienze basate su codice all’interno dell’app mobile.

Le schede di contenuto sono particolarmente indicate per i casi di utilizzo consigliati nelle app mobili, in quanto persistono in un’esperienza simile ai feed, che gli utenti possono consultare quando lo desiderano. I messaggi in-app possono essere utilizzati per consigli contestuali attivati da comportamenti specifici (ad esempio, mostrare prodotti complementari dopo aver aggiunto un elemento al carrello).

**Considerazioni chiave:**

- [!DNL Mobile SDK] deve essere configurato con il tracciamento degli eventi comportamentali per le interazioni rilevanti
- Le schede di contenuto forniscono una superficie di consigli persistente; i messaggi in-app sono temporanei
- Il tracciamento del comportamento offline richiede la gestione delle code SDK per l’invio differito degli eventi
- I cicli di aggiornamento dell’app store determinano la rapidità con cui è possibile distribuire le modifiche al rendering dei consigli

**Vantaggi:**

- Esperienza mobile nativa con rendering dei consigli fluido e integrato nell’app
- Le schede di contenuto forniscono un feed di consigli persistente e navigabile
- I messaggi in-app consentono consigli contestuali attivati dal comportamento
- Sfrutta i segnali a livello di dispositivo (posizione, pattern di utilizzo dell’app) per aumentarne la rilevanza

**Limitazioni:**

- Richiede l&#39;integrazione di [!DNL Mobile SDK] e risorse di sviluppo app
- Le modifiche del rendering richiedono aggiornamenti dell’app (a meno che non si utilizzino esperienze basate su codice con layout basati su server)
- I periodi offline creano lacune nella raccolta dei segnali comportamentali

**Experience League:**

- [Panoramica di Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Opzione C: consigli comportamentali per le e-mail

**Consigliato per:** Consigli di prodotto nelle campagne e-mail: e-mail di navigazione abbandonate con consigli di prodotto visualizzati, e-mail di cross-selling post-acquisto, digest periodici di &quot;selezioni per te&quot; e e-mail di ricoinvolgimento con suggerimenti di prodotto personalizzati.

**Funzionamento:**

I dati del profilo comportamentale accumulati dalle sessioni precedenti informano la selezione dei consigli al momento dell’invio dell’e-mail o del rendering. Viene definito un pubblico per il targeting dei destinatari appropriati (ad esempio, visitatori che hanno navigato ma non hanno acquistato, clienti che hanno effettuato un acquisto recente). Una campagna o un percorso è configurato per inviare un messaggio e-mail che include posizionamenti di consigli. Al momento dell’invio, AJO Decisioning valuta il profilo comportamentale di ciascun destinatario in base alla strategia di selezione e inserisce gli elementi consigliati nel contenuto dell’e-mail.

Questa opzione si basa sulla cronologia comportamentale accumulata anziché sui segnali in-session. Gli attributi calcolati (punteggi di affinità tra categorie, visualizzazioni recenti dei prodotti, frequenza di acquisto) migliorano in modo significativo la qualità dei consigli per le e-mail perché distillano la cronologia comportamentale in segnali a livello di profilo che la strategia di selezione può valutare in modo efficiente.

**Considerazioni chiave:**

- I consigli e-mail vengono valutati al momento dell’invio, non in fase di apertura: lo stato del profilo comportamentale al momento dell’invio determina i consigli
- Gli attributi calcolati sono fortemente consigliati per migliorare la qualità della classificazione
- Le limitazioni del rendering di e-mail (nessun JavaScript, CSS limitato) limitano i formati di visualizzazione dei consigli
- Richiede una superficie di canale e-mail configurata e convalidata

**Vantaggi:**

- Sfrutta la cronologia comportamentale completa tra le sessioni per una personalizzazione più approfondita
- Si integra con i flussi di lavoro esistenti di campagne e percorsi
- Valido per gli scenari di ricoinvolgimento e riconquista in cui i punti di contatto web/app non sono disponibili
- Può includere più posizionamenti di consigli in un’unica e-mail

**Limitazioni:**

- I consigli sono statici al momento dell’invio e non vengono aggiornati all’apertura dell’e-mail
- I vincoli di rendering di e-mail limitano i formati di visualizzazione dei consigli
- Richiede valutazione del pubblico e infrastruttura di orchestrazione di campagne/percorsi
- Maggiore complessità di implementazione a causa di dipendenze aggiuntive (configurazione del canale, definizione del pubblico, esecuzione della campagna)

**Experience League:**

- [Creare un messaggio e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Confronto delle opzioni

La tabella seguente riepiloga le differenze principali tra le opzioni di implementazione.

| Criteri | Opzione A: Web in tempo reale | Opzione B: app mobile | Opzione C: comportamento delle e-mail |
| --- | --- | --- | --- |
| Ideale per | Consigli per pagine web (PDP, home page, categoria) | Consigli in-app e feed di contenuti | Campagne e-mail con consigli sui prodotti |
| Sorgente del segnale comportamentale | In sessione + tra sessioni ([!DNL Web SDK]) | Interazioni in-app ([!DNL Mobile SDK]) | Cronologia comportamentale accumulata (profilo) |
| Latenza consigli | Secondi secondari ([!DNL Edge Network]) | Secondi secondari ([!DNL Edge Network]) | Al momento dell’invio (valutazione lato hub) |
| Tipo di visitatore | Anonimo e noto | Noto (utenti dell’app) | Noto (destinatari e-mail) |
| Complessi | Medio | Medium - Alta | Alta |
| Dipendenza canale | [!DNL Web SDK], superficie esperienza basata su codice | [!DNL Mobile SDK], superficie scheda in-app/contenuto | Superficie del canale e-mail, pubblico, campagna/percorso |
| Richiede | Distribuzione [!DNL Web SDK], criterio di unione Edge | Distribuzione [!DNL Mobile SDK], criterio di unione Edge | Superficie e-mail, definizione del pubblico, configurazione della campagna |

### Scegli l’opzione giusta

Utilizza le seguenti indicazioni per selezionare l’opzione migliore per la tua situazione:

- **Inizia con l&#39;opzione A** se il tuo obiettivo principale sono i consigli sui prodotti in tempo reale sul tuo sito Web. Si tratta del punto di partenza più comune e fornisce valore immediato con la minore complessità di implementazione.
- **Scegli l&#39;opzione B** se la tua app mobile è un canale di coinvolgimento primario e i consigli in-app genererebbero un incremento significativo della conversione. L&#39;opzione B può essere eseguita in parallelo con l&#39;opzione A utilizzando le stesse strategie di selezione e gli stessi cataloghi di articoli.
- **Aggiungi l&#39;opzione C** quando desideri estendere i consigli comportamentali nelle campagne e-mail. Questo viene generalmente sovrapposto all’opzione A o B, utilizzando gli stessi cataloghi di elementi e le stesse strategie di selezione, ma con modelli di rendering specifici per e-mail e targeting basato sul pubblico.
- **Combina le opzioni A + C** per un pattern comune: consigli Web in tempo reale per i visitatori attivi, più consigli per e-mail abbandonate durante la navigazione o dopo l&#39;acquisto per i visitatori che se ne vanno senza convertirsi.

## Fasi di implementazione

Le seguenti fasi ti guidano attraverso l’implementazione end-to-end delle raccomandazioni comportamentali.

### Fase 1: configurare lo schema di eventi comportamentali e la raccolta dati

**Funzione applicazione:** AEP: Modellazione e preparazione dati (F2), AEP: Origini dati e raccolta (F3)

Questa fase stabilisce gli schemi XDM, i set di dati e i meccanismi di raccolta dei dati che acquisiscono segnali comportamentali e dati del catalogo degli elementi. Questa base dati è ciò da cui dipende tutta la logica dei consigli.

#### Decisione: progettazione schema evento comportamentale

Quali segnali comportamentali dovrebbero guidare i consigli?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo visualizzazioni prodotto | Semplici consigli per la vendita incrociata/upselling | Minore sforzo di implementazione; profondità di segnale limitata |
| Visualizzazioni prodotto + acquisti | Consigli con logica di esclusione degli acquisti e di cross-selling | Sforzo moderato; abilita il filtro &quot;escludi già acquistato&quot; |
| Suite comportamentale completa (visualizzazioni, acquisti, componenti aggiuntivi al carrello, ricerche, interazioni con i contenuti) | Consigli sofisticati con classificazione a più segnali | Massima qualità del segnale; richiede strumentazione [!DNL Web SDK]/[!DNL Mobile SDK] completa |

#### Decisione: metodo di acquisizione catalogo articoli

Come verrà acquisito il catalogo di prodotti o contenuti in AEP?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Acquisizione in batch tramite connettore di origine | Gli aggiornamenti del catalogo sono periodici (giornalieri/settimanali) | Configurazione semplificata; le modifiche al catalogo non si riflettono in tempo reale |
| Acquisizione in streaming | Il catalogo richiede aggiornamenti quasi in tempo reale (variazioni di prezzo, disponibilità) | Più complesso; assicura che i consigli riflettano l’inventario corrente |
| Caricamento manuale/API | Catalogo di piccole dimensioni con modifiche non frequenti | Configurazione più semplice; non scalabile per cataloghi grandi o dinamici |

**Navigazione interfaccia utente:** Gestione dati > Schemi > Crea schema; Raccolta dati > Flussi di dati > Nuovo flusso di dati

**Dettagli configurazione chiave:**

- Lo schema Evento esperienza deve includere identificatori di prodotto/elemento (SKU, ID prodotto, ID contenuto) nel payload dell’evento
- Lo schema del catalogo articoli deve includere gli attributi utilizzati per filtrare e classificare: categoria, prezzo, URL immagine, stato disponibilità, tag
- Il servizio [!DNL Adobe Journey Optimizer] dello stream di dati deve essere abilitato per le decisioni di Edge
- Le chiamate [!DNL Web SDK] `sendEvent` devono includere dati di interazione prodotto mappati ai campi di e-commerce XDM

**Documentazione di Experience League:**

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Definire una relazione tra due schemi](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-api)

### Fase 2: configurare identità e profilo

**Funzione applicazione:** AEP: configurazione identità e profilo (F4)

Questa fase imposta gli spazi dei nomi delle identità, le designazioni delle identità primarie e i criteri di unione che garantiscono che i segnali comportamentali siano correttamente associati ai profili dei visitatori e disponibili per la distribuzione di consigli in tempo reale.

#### Decisione: criterio di unione per Edge Decisioning

Il caso di utilizzo della funzione Consigli richiede una valutazione Edge in tempo reale?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Attivo sui criteri di unione di Edge | Opzioni A e B (consigli web e mobile in tempo reale) | Obbligatorio per la consegna di consigli in un secondo secondario; un solo criterio di unione Edge per sandbox |
| Criterio di unione standard (non su Edge) | Solo opzione C (consigli e-mail valutati al momento dell’invio) | Sufficiente per la valutazione lato hub; non utilizza lo slot per criteri di unione di Edge |

#### Decisione: identità visitatore anonimo vs. identità visitatore nota

Come devono essere gestiti i segnali comportamentali provenienti da visitatori anonimi?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo ECID (anonimo) | Consigli principalmente per i visitatori anonimi in base al comportamento durante la sessione | Configurazione più semplice; nessuna continuità tra sessioni a meno che il visitatore non si autentichi |
| ECID + identità autenticata (ID CRM, e-mail) | Raccomandazioni tra sessioni per i visitatori noti con unione di identità | Profili comportamentali più completi; richiede un flusso di autenticazione |
| Entrambi con collegamento del grafico delle identità | Percorso completo da anonimo a noto con unione identità | Più completo; richiede la configurazione delle regole di collegamento delle identità |

**Navigazione interfaccia utente:** Identità > Spazi dei nomi identità; Profili > Criteri di unione

**Dettagli configurazione chiave:**

- Lo spazio dei nomi ECID è preconfigurato e utilizzato automaticamente da [!DNL Web SDK] e [!DNL Mobile SDK]
- È necessario creare spazi dei nomi di identità personalizzati (ID CRM, ID fedeltà) per l’identità autenticata
- L’identità primaria nello schema Experience Event deve essere ECID per eventi comportamentali web/mobili
- I criteri di unione devono utilizzare Private Device Graph per l’unione delle identità tra dispositivi diversi

**Documentazione di Experience League:**

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Regole di collegamento del grafo identità](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)

### Fase 3: Impostare il catalogo articoli e la strategia di selezione

**Funzione applicazione:** AJO: Decisioning

Questa fase configura il catalogo degli elementi (elementi decisionali), le strategie di selezione che combinano segnali comportamentali con attributi degli elementi per la classificazione, regole di filtro per escludere gli elementi non idonei e consigli di fallback per i profili con avvio a freddo.

#### Decisione: ambito catalogo articoli

Quali articoli sono disponibili per i consigli?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Catalogo dei prodotti (e-commerce) | Consigliare prodotti fisici o digitali per l&#39;acquisto | Gli attributi degli articoli includono prezzo, categoria, disponibilità, immagini |
| Catalogo dei contenuti (media/pubblicazione) | Articoli consigliati, video o contenuti educativi | Gli attributi degli elementi includono argomento, autore, data di pubblicazione e tipo di contenuto |
| Catalogo ibrido | Raccomandazione di prodotti e contenuti | Richiede uno schema di elementi unificato che soddisfi entrambi i tipi |

#### Decisione: approccio di classificazione

Come devono essere classificati gli articoli idonei per determinare i consigli migliori?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Classificazione basata su formule | Cancella la logica di business per la classificazione (ad esempio, ordina per punteggio di affinità tra categorie moltiplicato per la popolarità dell’elemento) | Classificazione trasparente e verificabile; richiede una formula di classificazione definita |
| Classificato in base all’intelligenza artificiale (ottimizzazione automatica) | L’apprendimento automatico dovrebbe determinare una classificazione ottimale in base ai dati di conversione | Richiede almeno 1.000 eventi di conversione per l&#39;apprendimento dei modelli; meno trasparente |
| Basato su priorità (manuale) | Ordinamento dei consigli semplice e curato manualmente | Più facile da configurare; non si adatta al comportamento individuale |

#### Decisione: regole di filtro

Quali elementi devono essere esclusi dai consigli?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Escludi articoli già acquistati | Consigli per il cross-selling e l&#39;individuazione | Richiede cronologia acquisti nel profilo comportamentale |
| Escludi articoli esauriti | E-commerce con inventario dinamico | Richiede aggiornamenti del catalogo in tempo reale o quasi reale |
| Escludi elementi precedentemente ignorati | Consigli sui contenuti in cui gli utenti possono ignorare i suggerimenti | Richiede il tracciamento dei licenziamenti negli eventi comportamentali |
| Filtro con ambito di categoria | Raccomandazioni limitate a categorie specifiche | Utilizza gli attributi dell&#39;elemento per il filtro |

#### Decisione: strategia di avviamento a freddo

Cosa deve essere mostrato per i nuovi visitatori senza cronologia comportamentale?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Articoli più richiesti (bestseller globali) | Fallback generico | Semplice da gestire; non personalizzato |
| Articoli popolari specifici per categoria | Il visitatore è arrivato su una pagina di categoria | Fallback contestualmente rilevante; richiede il contesto della pagina |
| Selezioni editoriali curate | Il marchio vuole un controllo editoriale sull’esperienza con avviamento a freddo | Richiede cura e aggiornamenti manuali |
| Elementi di tendenza (popolarità ponderata in base al tempo) | Fallback dinamico che riflette le tendenze correnti | Richiede il calcolo del segnale di tendenza |

**Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Componenti > Gestione decisioni > Decisioni; [!DNL Journey Optimizer] > Componenti > Gestione decisioni > Offerte; [!DNL Journey Optimizer] > Componenti > Gestione decisioni > Posizionamenti

**Dettagli configurazione chiave:**

- Crea elementi decisionali che rappresentano ciascun prodotto o contenuto del catalogo, con attributi (categoria, prezzo, URL immagine, tag)
- Definire strategie di selezione che combinano il filtro del catalogo degli articoli con la logica di classificazione comportamentale
- Configurare modelli di classificazione: le espressioni basate su formule possono fare riferimento agli attributi di profilo (ad esempio, punteggi di affinità tra categorie di attributi calcolati)
- Creare offerte/elementi di fallback che fungono da consigli predefiniti per i profili con avviamento a freddo
- Organizzare gli elementi in raccolte utilizzando i qualificatori di raccolta (tag) per il raggruppamento logico
- Imposta le regole di filtro nelle strategie di selezione per applicare le regole business (escludi solo articoli acquistati e in magazzino)

**Documentazione di Experience League:**

- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Creare i posizionamenti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Creare regole di decisione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Creare offerte di fallback](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Creare le raccolte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Fase 4: configurare canale e superficie

**Funzione applicazione:** AJO: Configurazione canale

Questa fase configura le superfici di consegna in cui verrà eseguito il rendering dei consigli. La configurazione varia in modo significativo in base all’opzione di implementazione.

#### Decisione: tipo di superficie di consegna

Dove verranno visualizzati i consigli?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Esperienza basata su codice (web) | Widget di consigli su pagine web con rendering personalizzato | Massima flessibilità per il rendering; richiede sviluppo front-end |
| Superficie del canale web | Superficie di personalizzazione web standard | Utilizza AJO Web Designer; meno flessibile rispetto a quello basato su codice |
| Messaggio in-app | Consigli contestuali attivati dal comportamento dell’app | Effimero; scompare dopo l&#39;interazione o il licenziamento |
| Scheda contenuto (mobile) | Feed di consigli persistenti nell’app mobile | Persiste finché l’utente non agisce; esperienza di feed navigabile |
| E-mail | Consigli di prodotto incorporati nelle campagne e-mail | Statico al momento dell’invio; soggetto ai vincoli di rendering di e-mail |

**Opzioni divergenti:**

**Per L&#39;Opzione A (Consigli Web In Tempo Reale):**
Configura una superficie di esperienza basata su codice o una superficie di canale web. Le esperienze basate su codice offrono la massima flessibilità per il rendering personalizzato dei consigli (caroselli, griglie, schede articolo). L’URI della superficie identifica la posizione in cui vengono visualizzati i consigli nella pagina.

**Per L&#39;Opzione B (Consigli Per App Mobile):**
Configurare le superfici dei messaggi o delle schede di contenuto in-app. Le schede di contenuto sono consigliate per i feed di consigli persistenti. I messaggi in-app funzionano bene per i consigli contestuali attivati dal comportamento.

**Per L&#39;Opzione C (Email Behavioral Recommendations):**
Configura una superficie di canale e-mail con delega del sottodominio, assegnazione del pool IP e impostazioni del mittente. Assicurati che la superficie sia convalidata per il recapito.

**Navigazione interfaccia utente:** Amministrazione > Canali > Superfici di canale > Crea superficie

**Documentazione di Experience League:**

- [Impostare le superfici di canale](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configurare il canale SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Fase 5: Configurare il contenuto e la consegna

**Funzione applicazione:** AJO: authoring dei messaggi

Questa fase definisce i modelli di rendering dei consigli che controllano la modalità di visualizzazione degli elementi consigliati al visitatore. Ciò include la progettazione del layout dell’articolo, espressioni di personalizzazione che richiamano gli attributi dell’articolo (nome, immagine, prezzo, collegamento) e la progettazione complessiva dell’esperienza di consigli.

#### Decisione: formato di visualizzazione dei consigli

Come devono essere renderizzati gli articoli consigliati?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Carosello (scorrimento orizzontale) | Pagina principale o pagina categoria con spazio verticale limitato | Modello UX familiare; mostra più elementi in uno spazio compatto |
| Griglia (su più righe) | Sezione dedicata ai consigli con ampio spazio | Mostra più elementi contemporaneamente; funziona bene per le sezioni &quot;consigliato per te&quot; |
| Widget per singolo elemento | Consigli contestuali in una posizione di pagina specifica (ad esempio, barra laterale) | Ingombro minimo; posizionamento ad alto impatto |
| Blocco e-mail in linea | Consigli incorporati nel corpo dell’e-mail | Soggetto ai vincoli HTML/CSS dell’e-mail; in genere 2-4 elementi |

#### Decisione: numero di consigli da visualizzare

Quanti elementi deve restituire la decisione per posizionamento?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| 3-4 elementi | Widget consigli standard | Bilancia la rilevanza con la densità visiva |
| 6-8 elementi | Carosello con layout a scorrimento o griglia | Più opzioni per il visitatore; richiede una profondità di catalogo sufficiente |
| 1 elemento | Consigli contestuali per un singolo prodotto | Massima rilevanza, rendering più semplice |
| Oltre 10 elementi | Esperienza di consigli in stile feed | Casi d’uso relativi ai contenuti (contenuti multimediali, pubblicazioni) |

**Opzioni divergenti:**

**Per L&#39;Opzione A (Consigli Web In Tempo Reale):**
Progetta il rendering dei consigli utilizzando modelli di esperienza basati su codice. Utilizza HTML/CSS/JavaScript per creare il layout carosello, griglia o widget. Le espressioni Personalization fanno riferimento agli attributi di risposta della decisione (nome articolo, URL immagine, prezzo, URL prodotto). Il rilevamento delle impression e dei clic viene gestito automaticamente da [!DNL Web SDK].

**Per L&#39;Opzione B (Consigli Per App Mobile):**
Configura i modelli per schede di contenuto o messaggi in-app con la logica di visualizzazione degli elementi. Utilizza strutture di contenuto basate su JSON riprodotte dall’app mobile in modalità nativa. Includi collegamenti profondi per ogni elemento consigliato.

**Per L&#39;Opzione C (Email Behavioral Recommendations):**
Progetta i contenuti delle e-mail utilizzando E-mail Designer. Inserisci posizionamenti di consigli utilizzando blocchi di contenuto basati sulle decisioni. Configura espressioni di personalizzazione per gli attributi di elemento nel modello e-mail. La personalizzazione della riga dell’oggetto può fare riferimento ai principali elementi consigliati.

**Navigazione interfaccia utente:** Gestione contenuto > Modelli di contenuto; Campagna/Percorso > Modifica contenuto > E-mail Designer

**Dettagli configurazione chiave:**

- Ogni posizionamento di consigli deve fare riferimento alla decisione creata nella Fase 3
- Le espressioni Personalization utilizzano la sintassi Handlebars per eseguire il rendering degli attributi degli elementi
- Per il web: configura l’esperienza basata su codice per chiamare la decisione ed eseguire il rendering della risposta
- Per e-mail: incorpora la decisione nell’azione e-mail nella campagna o nel percorso
- Visualizzare in anteprima i consigli utilizzando profili di test con cronologia comportamentale nota

**Documentazione di Experience League:**

- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Anteprima e test del contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### Fase 6: configurare l’ambito del pubblico e la campagna/il percorso (solo opzione C)

**Funzione applicazione:** RT-CDP: Audience Evaluation, AJO: Campaign Execution o Journey Orchestration

Per i consigli basati su e-mail (opzione C), questa fase definisce il pubblico target e configura la campagna o il percorso che distribuisce l’e-mail di consigli. Le opzioni A e B saltano questa fase perché i consigli vengono consegnati in tempo reale al caricamento della pagina o dello schermo.

#### Decisione: metodo di valutazione del pubblico

Come deve essere valutato il pubblico di destinazione delle e-mail di consigli?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Valutazione in batch | Campagne e-mail di consigli pianificate (giornaliero, riepilogo settimanale) | Tempistica di invio prevedibile; pubblico valutato prima dell’invio |
| Valutazione in streaming | E-mail di consigli attivate da eventi (navigazione abbandonata, post-acquisto) | Qualificazione del pubblico in tempo quasi reale; coppie con orchestrazione del percorso |

#### Decisione: meccanismo di consegna

L’e-mail deve essere consegnata tramite una campagna o un percorso?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Campagna pianificata | Esplosioni di e-mail per consigli una tantum o ricorrenti a un pubblico definito | Configurazione più semplice; valutazione e invio in batch del pubblico |
| Percorso con voce di pubblico | E-mail di consigli in corso attivate dalla qualificazione del pubblico | Abilita flussi in più passaggi (ad esempio e-mail di consigli seguita da promemoria) |
| Percorso attivato da eventi | E-mail di consiglio attivata da un evento specifico (abbandono navigazione, acquisto) | Attivazione in tempo reale; richiede l&#39;immissione di un percorso basato su eventi |

**Navigazione interfaccia utente:** Cliente > Tipi di pubblico > Crea pubblico > Genera regola; Campagne > Crea campagna; Percorsi > Crea percorso

**Dettagli configurazione chiave:**

- Definisci il pubblico di destinazione utilizzando le espressioni della regola del segmento che fanno riferimento alla cronologia dei comportamenti (ad esempio, &quot;prodotti visualizzati negli ultimi 7 giorni ma non acquistati&quot;)
- Configurare la campagna o il percorso con l’azione e-mail che fa riferimento alla superficie di canale della fase 4
- Incorporare la decisione della Fase 3 nel contenuto dell’e-mail
- Imposta le regole di pianificazione e frequenza per evitare messaggi eccessivi

**Documentazione di Experience League:**

- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Rapporto live delle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)

### Fase 7: configurare reporting e ottimizzazione

**Funzione applicazione:** AJO: Reporting &amp; Performance Analysis, S5: Reporting &amp; Analysis

Questa fase stabilisce il monitoraggio delle prestazioni per le metriche di click-through, conversione e ricavi per i consigli. Crea l’infrastruttura di reporting per misurare l’efficacia dei consigli e identificare le opportunità di ottimizzazione.

#### Decisione: profondità di reporting

Quale livello di analisi dei rapporti è necessario?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo rapporti nativi di AJO | Monitoraggio delle prestazioni dei consigli di base | Configurazione rapida; limitata alle metriche tracciate da AJO |
| Integrazione AJO + [!DNL Customer Journey Analytics] | Analisi dell’impatto dei consigli e attribuzione dei ricavi cross-channel | Richiede connessione [!DNL Customer Journey Analytics] e visualizzazione dati; fornisce informazioni più approfondite |
| Area di lavoro [!DNL Customer Journey Analytics] completa con dashboard personalizzati | Programma di ottimizzazione continuo con analisi a livello di elemento, segmento e superficie | Più completo; richiede [!DNL Customer Journey Analytics] esperienza e configurazione |

**Navigazione interfaccia utente:** Campagne > Seleziona campagna > Report tempo totale; Percorsi > Seleziona percorso > Report tempo totale; [!DNL Customer Journey Analytics] > Progetti > Crea nuovo progetto

**Dettagli configurazione chiave:**

- Rivedi i rapporti sulle campagne e sul percorso AJO per le metriche di consegna e coinvolgimento
- Per l&#39;integrazione con [!DNL Customer Journey Analytics], crea una connessione che includa i set di dati dell&#39;evento esperienza di AJO (feedback messaggi, tracciamento e-mail, decisioni)
- Crea una visualizzazione dati [!DNL Customer Journey Analytics] con dimensioni specifiche per i consigli (nome elemento, categoria elemento, superficie consiglio) e metriche (impression, clic, conversioni, ricavi)
- Creare metriche calcolate per CTR consigli, tasso di conversione e ricavi per impression
- Crea [!DNL Customer Journey Analytics] pannelli dell&#39;area di lavoro confrontando le prestazioni dei consigli tra superfici, segmenti e periodi di tempo

**Documentazione di Experience League:**

- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Creare o modificare una connessione](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Creare o modificare una visualizzazione dati](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Panoramica delle metriche calcolate](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

## Considerazioni sull’implementazione

Rivedi i seguenti guardrail, insidie, best practice e compromessi prima e durante l’implementazione.

### Guardrail e limiti

- Massimo 10.000 offerte personalizzate approvate (elementi di decisione) per sandbox — [Guardrail di gestione delle decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Massimo 30 posizionamenti per decisione
- Massimo 30 ambiti di raccolta per richiesta di decisione
- Tempi di risposta per la consegna delle offerte SLA: meno di 500 ms a P95 per richieste Edge a ambito singolo
- I modelli di classificazione IA richiedono almeno 1.000 eventi di conversione per la formazione
- I contatori di limite delle offerte possono presentare un ritardo di alcuni secondi in scenari ad alto throughput
- Le decisioni di Edge sono limitate agli attributi di profilo disponibili nell’archivio profili edge
- In Edge può essere attivo un solo criterio di unione per sandbox — [Guardrail di profilo](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Massimo 25 attributi calcolati attivi per sandbox: [Guardrail attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- Massimo 4.000 definizioni di segmenti per sandbox: [Guardrail di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Acquisizione in streaming: massimo 20.000 record al secondo per connessione HTTP — [Guardrail di acquisizione](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Insidie comuni

- **La decisione restituisce solo elementi di fallback:** verifica che gli elementi di decisione personalizzati siano approvati, entro il loro intervallo di date di validità, e che le regole di idoneità corrispondano agli attributi di profilo del visitatore. Verificare che i limiti di limitazione non siano stati raggiunti.
- **La consegna di Edge restituisce una personalizzazione vuota:** Verificare che lo stream di dati sia configurato con il servizio [!DNL Adobe Journey Optimizer] abilitato e che l&#39;ambito della decisione sia formattato correttamente nella richiesta [!DNL Web SDK].
- **Formula di classificazione non applicata:** Verificare che la formula sia sintatticamente valida e faccia riferimento ad attributi di profilo accessibili. Gli errori di formula tornano automaticamente alla classificazione basata sulla priorità.
- **Consigli non aggiornati:** se i dati dell&#39;evento comportamentale non scorrono in tempo reale, i consigli saranno basati su profili comportamentali obsoleti. Verificare che [!DNL Web SDK] o [!DNL Mobile SDK] stia eseguendo lo streaming attivo degli eventi.
- **Il tasso di fallback a freddo è troppo alto:** Se un&#39;ampia percentuale di visitatori riceve consigli di fallback, è consigliabile arricchire la strategia di avvio a freddo con segnali contestuali (categoria di pagina corrente, origine di riferimento) anziché affidarsi esclusivamente alla cronologia comportamentale.
- **Recommendations non esegue il rendering sulla pagina:** Verifica che l&#39;URI della superficie di esperienza basato su codice corrisponda al pattern dell&#39;URL della pagina e che [!DNL Web SDK] richieda correttamente ed esegua il rendering della risposta di decisione.
- **Elementi del catalogo mancanti nei consigli:** Assicurarsi che tutti gli elementi del catalogo siano stati acquisiti come elementi decisionali, taggati con i qualificatori di raccolta corretti e inclusi nelle raccolte appropriate a cui fa riferimento la strategia di selezione.

### Best practice

- Inizia con un modello di classificazione basato su formule utilizzando attributi calcolati (affinità tra categorie, recency di interazione) prima di investire in modelli con classificazione basata su IA. I modelli basati su formule sono trasparenti, verificabili e forniscono una base solida per il confronto.
- Implementa il tracciamento delle impression e dei clic dal primo giorno. Senza i dati di interazione, i modelli di classificazione di IA non possono essere addestrati e non è possibile misurare l’efficacia dei consigli.
- Crea strategie di selezione separate per diverse superfici di consigli (homepage, PDP, e-mail) anziché riutilizzare una singola strategia ovunque. Superfici diverse rispondono alle esigenze degli utenti.
- Utilizza attributi calcolati per distillare la cronologia comportamentale in segnali di classificazione. I dati dell’evento non elaborati sono troppo granulari per una classificazione efficace basata su formule; segnali aggregati come &quot;punteggio di affinità tra categorie&quot; e &quot;giorni dall’ultimo acquisto&quot; sono più efficaci.
- Testa i consigli di fallback separatamente dai consigli personalizzati. Assicurati che gli elementi di fallback siano valori predefiniti di alta qualità e appropriati per il brand che forniscano una buona esperienza ai nuovi visitatori.
- Monitora il tasso di fallback a freddo come metrica di integrità chiave. Un tasso di fallback decrescente nel tempo indica una crescente copertura comportamentale.
- Per i consigli e-mail, la pianificazione invia negli orari in cui il profilo comportamentale è più completo (ad esempio, dopo le ore di picco di navigazione, non durante le attività).

### Decisioni di compromesso

I seguenti compromessi devono essere valutati in base alle tue esigenze specifiche.

#### Segnali in tempo reale e cronologia accumulata

I segnali comportamentali durante la sessione forniscono rilevanza immediata ma profondità limitata. L’anamnesi comportamentale accumulata fornisce profondità, ma può essere obsoleta. L’equilibrio tra queste fonti incide sulla qualità dei consigli.

- **L&#39;opzione A favorisce:** Segnali in tempo reale per rilevanza immediata, integrati dalla cronologia accumulata per i visitatori noti
- **L&#39;opzione C favorisce:** Cronologia accumulata esclusivamente, poiché le e-mail vengono inviate in modo asincrono
- **Consiglio:** per web e dispositivi mobili (opzioni A e B), combina i segnali in-session con attributi calcolati derivati dal comportamento storico. Per l’e-mail (opzione C), investi massicciamente in attributi calcolati che riassumono la cronologia comportamentale in segnali a livello di profilo utilizzabili.

#### Modelli basati su formule e modelli basati su IA

La classificazione basata su formule è trasparente e immediata. I modelli con classificazione AI si adattano automaticamente, ma richiedono dati di formazione e offrono meno visibilità nelle decisioni di classificazione.

- **Preferenze basate su formule:** Trasparenza, verificabilità, distribuzione immediata e controllo aziendale dettagliato sulla logica di classificazione
- **Preferenze basate sull&#39;intelligenza artificiale:** ottimizzazione automatizzata, individuazione di pattern non evidenti e riduzione dello sforzo di ottimizzazione manuale
- **Consiglio:** inizia con una classificazione basata su formule per stabilire una linea di base delle prestazioni e accumulare i dati di conversione. Passare ai modelli classificati in base all’intelligenza artificiale una volta che si dispone di dati di formazione sufficienti (oltre 1.000 eventi di conversione) e si desidera ottimizzare oltre ciò che è possibile ottenere con il tuning manuale delle formule.

#### Copertura dei consigli e rilevanza

L’allargamento del catalogo degli articoli e l’attenuazione delle regole di filtro aumentano la percentuale di richieste che ricevono consigli personalizzati, ma possono ridurre la rilevanza per ogni consiglio.

- **Elevata copertura a favore:** massimizzare il numero di visitatori che visualizzano consigli personalizzati; utile quando l&#39;obiettivo principale è il coinvolgimento
- **Preferenze di rilevanza elevata:** solo elementi altamente rilevanti, anche se per un numero maggiore di visitatori vengono visualizzati consigli di fallback; utile quando l&#39;obiettivo principale è la conversione
- **Consiglio:** inizia con un filtro moderato (escludi articoli acquistati ed esauriti) e monitora sia il tasso di fallback che il tasso di conversione. Restringi le regole di filtro solo se i dati di conversione lo supportano.

#### Profondità di Personalization e complessità dell&#39;implementazione

Segnali comportamentali più ricchi e modelli di classificazione più sofisticati migliorano la qualità dei consigli, ma aumentano la complessità dell’implementazione e il carico di manutenzione.

- **Un&#39;implementazione più semplice favorisce:** un time-to-value più rapido, una manutenzione inferiore, un debug e un&#39;iterazione più semplici
- **Personalizzazione più approfondita a favore di:** Incremento della conversione, migliore esperienza del cliente, differenziazione della concorrenza
- **Consiglio:** Implementare in fasi. Inizia con i segnali di visualizzazione del prodotto e la classificazione basata su formule (fase 1). Aggiungere attributi calcolati per l’arricchimento comportamentale (fase 2). Valuta i modelli classificati in base all’intelligenza artificiale una volta che la base è matura e sono disponibili dati di formazione sufficienti (fase 3).

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sulle tecnologie e le funzionalità utilizzate in questo modello.

### Gestione delle decisioni

- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Creare i posizionamenti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Creare regole di decisione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Creare offerte di fallback](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Creare le raccolte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Creare qualificatori di raccolta](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Distribuire le offerte tramite l’API Edge Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)

### Raccolta dati e Web/Mobile SDK

- [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Installare Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Panoramica di Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Panoramica dell’API del server Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### XDM e modellazione dati

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Creare un set di dati](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/create)
- [Definire una relazione tra due schemi](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-api)

### Identità e profilo

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Panoramica del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Tipi di pubblico e segmentazione

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Attributi calcolati e arricchimento dei profili

- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Guida dell’interfaccia utente attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Panoramica di Customer AI](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Configurazione dei canali

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Impostare le superfici di canale](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delega sottodomini](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)

### Authoring e personalizzazione dei messaggi

- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### Reporting e analisi

- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Panoramica delle metriche calcolate](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

### Governance dei dati e ciclo di vita

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview)
- [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Scadenze set di dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration)

### Monitoraggio e osservabilità

- [Panoramica di Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
- [Panoramica degli avvisi](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

### Guardrail

- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Guardrail di acquisizione](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Guardrail del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)

### Tutorial e guide

- [Panoramica sulle origini](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Panoramica sui tag](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
- [Gruppo di campi Consenso e preferenze](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
