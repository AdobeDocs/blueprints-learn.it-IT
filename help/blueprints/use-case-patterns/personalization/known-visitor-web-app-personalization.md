---
title: Personalization Web/app visitatore noto
description: Scopri come distribuire contenuti, offerte o promozioni personalizzati a visitatori identificati in base al profilo in tempo reale e all’iscrizione ai segmenti.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7957'
ht-degree: 2%

---


# Personalizzazione web/app per visitatore noto

Questo piano di riferimento fornisce una guida completa all&#39;implementazione per la distribuzione di contenuti personalizzati a visitatori identificati su superfici digitali tramite [!DNL Adobe Journey Optimizer] (AJO) e [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP). È progettato per architetti di soluzioni, tecnici di marketing e ingegneri dell’implementazione che devono comprendere tutti gli approcci all’implementazione praticabili, le decisioni che devono essere prese in ogni fase e la documentazione Experience League che supporta la configurazione.

La personalizzazione web/app per visitatore noto è il modello di personalizzazione principale per le esperienze digitali autenticate. A differenza della personalizzazione anonima dei visitatori, che si basa esclusivamente su segnali comportamentali durante la sessione, questo modello sfrutta l’intero profilo unificato: dati comportamentali storici, appartenenza ai segmenti, livello di fedeltà, cronologia degli acquisti, fase del ciclo di vita, attributi calcolati e punteggi di tendenza. Supporta la personalizzazione tra le pagine web (tramite il canale web AJO), i messaggi in-app mobili e le schede di contenuto.

Questa guida presenta tutte le opzioni di implementazione valide, basate su segmenti, decisioni e multi-superficie, con compromessi, indicazioni decisionali e riferimenti alla documentazione di [!DNL Adobe Experience League].

## Panoramica del caso d’uso

Le organizzazioni con proprietà digitali autenticate (siti di e-commerce, portali bancari, servizi di abbonamento, programmi fedeltà, app mobili) devono fornire esperienze personalizzate che riflettano il rapporto di ciascun cliente con il marchio. Quando un visitatore effettua l’accesso o viene riconosciuto tramite la risoluzione di identità, la piattaforma può accedere al proprio profilo unificato completo e fornire contenuti personalizzati per attributi, comportamenti e preferenze specifici.

Questo modello riguarda lo scenario in cui un visitatore identificato arriva su una proprietà web o apre un’app mobile e il sistema deve determinare il contenuto, l’offerta o la promozione ottimale da visualizzare in base ai dati di profilo in tempo reale e all’iscrizione al pubblico. La decisione di personalizzazione avviene al limite in millisecondi, consentendo la distribuzione di contenuti al secondo secondario senza latenza percepibile.

Il modello supporta sia la personalizzazione deterministica (in cui il contenuto specifico è mappato su segmenti di pubblico specifici) che le decisioni dinamiche (in cui AJO Decisioning valuta le regole di idoneità e le strategie di classificazione per selezionare il contenuto ottimale per profilo). Si estende su più superfici digitali: pagine web, messaggi in-app per dispositivi mobili e schede di contenuto, consentendo una personalizzazione coerente nel percorso digitale del cliente.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono affrontati da questo modello di casi d’uso.

### Fornire esperienze cliente personalizzate

Personalizza contenuti, offerte e messaggi in base a preferenze, comportamenti e fasi del ciclo di vita individuali. Per ulteriori informazioni, consulta [Distribuire esperienze cliente personalizzate](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md).

| KPI | Descrizione |
| --- | --- |
| Coinvolgimento | Frequenza e profondità di interazione con contenuti personalizzati su superfici digitali |
| Tassi di conversione | Percentuale di visitatori che hanno completato le azioni desiderate dopo aver ricevuto il contenuto personalizzato |
| Soddisfazione del cliente (CSAT) | Miglioramento della soddisfazione generale basato su esperienze digitali pertinenti e personalizzate |

### Aumentare il coinvolgimento con il sito Web

Migliora il tempo sul sito, le pagine per sessione e l’interazione con i contenuti web tramite esperienze rilevanti. Per ulteriori informazioni, vedere [Aumentare il coinvolgimento del sito Web](../../business-objectives/acquisition-growth/increase-website-engagement.md).

| KPI | Descrizione |
| --- | --- |
| Tempo sulla pagina (web) | Aumento del tempo di permanenza nelle aree di contenuto personalizzato |
| Coinvolgimento | Tassi di interazione con elementi personalizzati (clic, scorrimento, interazioni) |
| Tassi di conversione | Conversione migliorata dal contenuto personalizzato rispetto al contenuto predefinito |

### Aumentare il coinvolgimento con le app mobili

Promuovi l’utilizzo attivo giornaliero, l’adozione di funzioni e le conversioni in-app tramite esperienze in-app personalizzate.

| KPI | Descrizione |
| --- | --- |
| Coinvolgimento | Tassi di interazione in-app con messaggi personalizzati e schede di contenuto |
| Conservazione | Miglioramento della conservazione delle app grazie a esperienze personalizzate |
| Tassi di conversione | Miglioramenti della conversione in-app da offerte e consigli personalizzati |

## Esempi di casi d’uso tattici

Di seguito sono riportate le implementazioni tattiche comuni di questo modello:

- Personalizzazione eroe della homepage per livello di fedeltà o fase del ciclo di vita: visualizza diversi banner hero in base al fatto che il cliente sia nuovo, attivo, a rischio o VIP
- Carosello di consigli sui prodotti in base alla cronologia degli acquisti: vengono presentati suggerimenti di prodotti rilevanti utilizzando i dati di acquisto passati e i punteggi di affinità per i prodotti
- Banner promozionale personalizzato per segmento di clienti: mostra diverse promozioni per segmenti di clienti di alto valore, a rischio e nuovi
- Messaggio in-app per gli utenti di dispositivi mobili basato sull’adozione di funzioni: guida gli utenti alle funzioni sottoutilizzate in base ai loro pattern di utilizzo
- Scheda di contenuti con offerta personalizzata sulla dashboard dell’account: offerte persistenti e non consentite personalizzate in base al profilo del cliente
- Visualizzazione personalizzata dei prezzi o degli sconti in base al livello del cliente: mostra prezzi specifici per livello o sconti esclusivi per i membri del programma fedeltà
- Widget di consigli per le vendite incrociate basati su prodotti di proprietà: suggerisci prodotti o servizi complementari basati sul portfolio corrente
- Navigazione personalizzata o ordinamento dei contenuti in base agli interessi: riordina i moduli di contenuto o gli elementi di navigazione in base alle preferenze dimostrate

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare l’efficacia di questo modello di caso d’uso.

| KPI | Approccio di misurazione | Linee guida per benchmark |
| --- | --- | --- |
| Tasso di coinvolgimento Personalization | Clic e interazioni con elementi di contenuto personalizzato divisi per impression | Il contenuto personalizzato deve superare del 20-50% le prestazioni predefinite |
| Incremento tasso di conversione | Tasso di conversione per esperienze personalizzate rispetto a controllo/esperienze predefinite | Incremento del 10-30% rispetto alle esperienze non personalizzate |
| Percentuale di click-through (CTR) | Clic su CTA, offerte e consigli personalizzati divisi per impression | Monitoraggio per superficie (web, in-app, scheda di contenuti) e per segmento |
| Ricavo per visita | Ricavi attribuiti a sessioni con esperienze personalizzate | Confrontare le coorti di visitatori personalizzati e non personalizzati |
| Tasso di interazione scheda contenuto | Clic e licenziamenti sulla scheda contenuto relativi alle impression | Tracciamento per tipo di carta e segmento di pubblico |
| Coinvolgimento messaggi in-app | Interazioni dei messaggi in-app (clic su CTA, chiusure) relative alle impression | Confrontare segmenti di pubblico e tipi di messaggi diversi |
| Tempo sulla pagina | Tempo medio trascorso su pagine con contenuti personalizzati rispetto a quello predefinito | Le pagine personalizzate devono mostrare un tempo di permanenza maggiore |
| Tasso di accettazione offerta | Percentuale di offerte selezionate con decisioni che risultano in un evento di conversione | Tracciamento per offerta, posizionamento e strategia di classificazione |

## Schema del caso d’uso

Questa sezione descrive il pattern di base e la relativa catena di funzioni.

**Personalizzazione web/app visitatore noto**

Distribuisci contenuti, offerte o promozioni personalizzati a un visitatore identificato in base al profilo in tempo reale e all’iscrizione ai segmenti su più superfici Web, in-app mobile e schede di contenuto.

**Catena di funzioni:** Valutazione del pubblico > Personalization Decisioning > Configurazione superficie/canale > Consegna contenuto > Tracciamento impression > Reporting

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Adobe Journey Optimizer] (AJO)**: configurazione del canale web, configurazione del canale in-app, configurazione del canale della scheda di contenuto, decisioning (selezione e classificazione dell&#39;offerta), authoring dei messaggi (creazione di contenuti personalizzati), esecuzione della campagna, sperimentazione dei contenuti e reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Valutazione del pubblico (edge, streaming e batch), ricerca dei profili in tempo reale tramite Edge Network, arricchimento dei profili con attributi calcolati e punteggi di propensione
- **[!DNL Adobe Experience Platform] (AEP)** — Archivio profili, servizio Identity, Web SDK, Mobile SDK, configurazione dello stream di dati, consegna rete Edge

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve esistere | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Presunto sul posto | Sandbox AJO con canale web, canale in-app e autorizzazioni di decisione configurate. Per gli utenti sono stati assegnati ruoli di addetto marketing e autore di contenuti. | [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home), [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/it/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Obbligatorio | Lo schema di profilo deve includere attributi utilizzati per la personalizzazione e la segmentazione (ad esempio, livello fedeltà, cronologia acquisti, interessi prodotto, fase del ciclo di vita). Schema Experience Event per il tracciamento delle interazioni web/app e gli eventi di conversione. Set di dati abilitati per [!DNL Real-Time Customer Profile]. | [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home), [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/schema/composition) |
| Origini dati e raccolta | Obbligatorio | Web SDK implementato nelle proprietà web per la distribuzione delle esperienze e il tracciamento delle impression. Mobile SDK implementato nelle app mobili per la distribuzione in-app e con scheda di contenuti. Stream di dati configurato con il servizio AJO abilitato per la personalizzazione Edge. Dati di profilo in tempo reale disponibili al limite per la personalizzazione di secondi secondari. | [Panoramica di Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/home), [Panoramica di Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview), [Configura flussi di dati](https://experienceleague.adobe.com/it/docs/experience-platform/datastreams/configure) |
| Configurazione identità e profilo | Obbligatorio | Spazi dei nomi di identità noti (ID CRM, e-mail, ID utente autenticato) configurati. L’unione delle identità tra sessioni anonime e autenticate è operativa per una transizione fluida dalla personalizzazione anonima a quella dei visitatori noti. Criterio di unione di Edge configurato con `isActiveOnEdge: true` per risolvere il profilo autenticato nel server Edge di. | [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home), [Panoramica dei criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview) |
| Definizione e segmentazione del pubblico | Obbligatorio | Tipi di pubblico definiti utilizzando gli attributi di profilo, i dati comportamentali e gli attributi calcolati. Valutazione Edge o streaming abilitata per la qualificazione della personalizzazione in tempo reale. I tipi di pubblico utilizzati per la personalizzazione basata su segmenti devono essere idonei per la valutazione Edge. | [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home), [Segmentazione di Edge](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/edge-segmentation) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Consigliato | Gli attributi calcolati (ad esempio, [!DNL Customer AI] punteggi di propensione, valore del ciclo di vita, punteggio di coinvolgimento, affinità di prodotto, giorni dall’ultimo acquisto) migliorano in modo significativo la qualità della personalizzazione fornendo segnali più ricchi per la definizione del pubblico e la selezione dei contenuti. | [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview), [Panoramica di IA per l&#39;analisi dei clienti](https://experienceleague.adobe.com/it/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Data Lifecycle Management | Consigliato | I criteri di conservazione dei dati di profilo ed eventi garantiscono che le decisioni sulla personalizzazione siano nuove e pertinenti. L’applicazione del consenso assicura che la personalizzazione rispetti le preferenze dell’utente. | [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/it/docs/experience-platform/data-lifecycle/home), [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted) |
| Etichettatura e applicazione dell’utilizzo dati | Consigliato | Le etichette di governance sugli attributi di profilo utilizzati per la personalizzazione (in particolare gli attributi adiacenti ai dati PII come cronologia acquisti, posizione, dati finanziari) garantiscono la conformità con i criteri di utilizzo dei dati. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home), [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview) |
| Monitoraggio e osservabilità | Consigliato | Il monitoraggio delle prestazioni di consegna e personalizzazione di Edge consente di rilevare problemi di latenza, errori di consegna o problemi di aggiornamento dei dati che peggiorano l’esperienza personalizzata. | [Panoramica di Observability Insights](https://experienceleague.adobe.com/it/docs/experience-platform/observability/home), [Panoramica degli avvisi](https://experienceleague.adobe.com/it/docs/experience-platform/observability/alerts/overview) |
| Reporting e analisi | Incluso | Il reporting sulle prestazioni di Personalization fa parte del passaggio 6 della catena di funzioni. [!DNL Customer Journey Analytics] L’analisi consente un’analisi approfondita dell’impatto della personalizzazione su conversione, coinvolgimento e ricavi nei segmenti di visitatori. | [Panoramica di CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-overview/cja-overview), [Guida all&#39;integrazione di AJO + CJA](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Journey Optimizer] (AJO)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Configurazione canali | Configurazione di superficie e canale | Configurare superfici di canale web, in-app e schede di contenuto per la distribuzione di personalizzazione |
| Authoring dei messaggi | Authoring dei contenuti | Crea varianti di contenuto personalizzato con contenuto dinamico, espressioni di personalizzazione e blocchi condizionali per ogni superficie |
| Esecuzione della campagna | Configurazione e attivazione di Campaign | Creare e attivare campagne web (pianificate o attivate da API) che associano tipi di pubblico, superfici e contenuti |
| Decisioni | Impostazione delle decisioni (opzione B/C) | Configurare i criteri di decisione con regole di idoneità, strategie di classificazione ed elementi di offerta/contenuto per la personalizzazione dinamica |
| Sperimentazione sui contenuti | Ottimizzazione (opzionale) | Eseguire test A/B sulle varianti di contenuto personalizzato per ottimizzare le prestazioni |
| Frequenza e regole business | Configurazione e attivazione di Campaign | Applica i limiti di frequenza per le impression per evitare un eccesso di personalizzazione |
| Reporting e analisi delle prestazioni | Reporting e ottimizzazione | Monitorare la consegna della personalizzazione, il coinvolgimento e le metriche di conversione per superficie e segmento |

### [!DNL Real-Time CDP] (RT-CDP)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Valutazione del pubblico | Definizione e valutazione del pubblico | Definire e valutare i tipi di pubblico utilizzando gli attributi di profilo, i dati comportamentali e gli attributi calcolati con la valutazione Edge o in streaming |
| Ricerca profilo in tempo reale | Consegna dei contenuti (runtime) | Accedere agli attributi di profilo in tempo reale e alle iscrizioni ai segmenti tramite Edge Network per prendere decisioni sulla personalizzazione di un secondo secondario |
| Arricchimento del profilo | Pre-implementazione (supporto) | Arricchisci i profili con attributi calcolati, punteggi [!DNL Customer AI] e segnali comportamentali aggregati che migliorano la qualità della personalizzazione |

## Prerequisiti

Prima di implementare questo pattern di casi d’uso, assicurati di aver implementato quanto segue:

- [ ] Web SDK implementato nelle proprietà Web di destinazione con `alloy("sendEvent")` configurato per le visualizzazioni di pagina e il tracciamento delle interazioni
- [ ] Mobile SDK implementato nelle app mobili di destinazione (se vengono utilizzate superfici in-app o schede di contenuto)
- [ ] Datastream configurato con il servizio [!DNL Adobe Journey Optimizer] abilitato
- [ Lo schema del profilo ] include gli attributi utilizzati per la personalizzazione (livello fedeltà, cronologia acquisti, interessi prodotto, fase del ciclo di vita)
- [ Schema ] Experience Event configurato per il tracciamento di impression e conversione
- [ ] Spazi dei nomi di identità noti creati e unione di identità operativa tra identità anonime (ECID) e autenticate
- [ ] criterio di unione Edge configurato con `isActiveOnEdge: true`
- [ ] tipi di pubblico definiti con valutazione idonea per Edge per la personalizzazione in tempo reale
- [ ] risorse di contenuto (immagini, copia, CTA) preparate per ogni variante di personalizzazione
- [ Documentazione della strategia di Personalization ]: quali attributi determinano quale contenuto, per quali superfici

## Opzioni di implementazione

Questa sezione descrive gli approcci di implementazione disponibili per questo modello di caso d’uso.

### Opzione A: personalizzazione web basata su segmenti

**Ideale per:** personalizzazione deterministica in cui varianti di contenuto specifiche vengono mappate direttamente sui segmenti di pubblico: banner principali specifici per il livello di fedeltà, messaggi della fase del ciclo di vita, contenuti promozionali per i segmenti di cliente. Ideale quando la mappatura contenuto-segmento è ben definita e non richiede classificazione dinamica o ottimizzazione.

**Funzionamento:**

La personalizzazione basata su segmenti mappa le varianti di contenuto direttamente sui segmenti di pubblico. Quando il profilo di un visitatore noto viene valutato in base ai tipi di pubblico idonei per Edge di al caricamento della pagina, il sistema determina a quali segmenti appartiene il visitatore e visualizza la variante di contenuto corrispondente. La selezione si basa sulla priorità di iscrizione al segmento: se un visitatore è idoneo per più segmenti, viene visualizzato il contenuto del segmento con priorità più elevata.

Questo approccio utilizza le campagne del canale web di AJO (o campagne in-app/scheda di contenuto) con regole di contenuto condizionale o configurazioni di targeting per più trattamenti. Ogni segmento di pubblico è associato a un’esperienza di contenuto specifica. Non è coinvolto alcun motore decisionale: la logica di selezione dei contenuti è interamente basata su segmenti.

Il contenuto viene creato utilizzando l’interfaccia di authoring dei messaggi di AJO con blocchi di contenuto dinamici che eseguono il rendering di contenuti diversi in base all’appartenenza al pubblico o agli attributi del profilo. Il SDK web o il SDK mobile offre l’esperienza personalizzata in tempo reale tramite Edge Network.

**Considerazioni chiave:**

- Le varianti di contenuto devono essere precreate per ciascun segmento
- Le definizioni dei segmenti devono essere idonee per l’edge per la qualifica in tempo reale
- Per aggiungere nuovi segmenti o varianti di contenuto è necessario aggiornare la configurazione della campagna
- La selezione del contenuto è deterministica: lo stesso segmento vede sempre lo stesso contenuto

**Vantaggi:**

- Semplicità di implementazione e manutenzione grazie a una chiara mappatura contenuto-segmento
- Facile da capire e spiegare alle parti interessate la logica di personalizzazione
- Nessun sovraccarico decisionale: risoluzione più rapida dei contenuti
- Controllo completo sul contenuto ricevuto da ogni segmento

**Limitazioni:**

- Flessibilità limitata con l’aumento del numero di segmenti e varianti di contenuto
- Impossibile ottimizzare in modo dinamico la selezione del contenuto in base a segnali a livello di profilo oltre l’iscrizione al segmento
- L’aggiunta di nuove varianti di contenuto richiede aggiornamenti manuali della campagna
- Non supporta gli scenari di offerta migliore successiva in cui più offerte competono per lo stesso posizionamento

**Experience League:**

- [Introduzione al canale web](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/web/get-started-web)
- [Creare esperienze web](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/web/create-web)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### Opzione B: Personalizzazione basata su decisioni

**Ideale per:** Personalizzazione dinamica in cui il contenuto o l&#39;offerta ottimale devono essere selezionati per profilo utilizzando le regole di idoneità e le strategie di classificazione: offerta migliore nella home page, consigli di prodotti personalizzati, selezione dinamica del banner promozionale. Ideale quando più offerte o elementi di contenuto competono per lo stesso posizionamento e il sistema deve scegliere quello migliore.

**Funzionamento:**

La personalizzazione basata sulle decisioni utilizza AJO Decisioning per valutare il profilo di ogni visitatore in base a un catalogo di articoli di contenuto o offerte, applicando le regole di idoneità per determinare quali articoli sono idonei e applicando quindi una strategia di classificazione (basata sulla priorità, basata su formule o con classificazione basata sull’intelligenza artificiale) per selezionare l’articolo ottimale per ogni posizionamento.

L’implementazione prevede la creazione di posizionamenti (dove viene visualizzato il contenuto), la definizione di offerte con regole di idoneità e rappresentazioni di contenuto, l’organizzazione di offerte in raccolte e la creazione di criteri decisionali che associano posizionamenti a raccolte con strategie di classificazione. In fase di runtime, quando un visitatore carica una pagina, Edge Network valuta il criterio di decisione in base al profilo del visitatore e restituisce il contenuto dell’offerta selezionata.

Questo approccio supporta scenari di personalizzazione sofisticati, tra cui offerte successive, promozioni personalizzate con limite e selezione di contenuti ottimizzati per l’intelligenza artificiale. Le offerte possono avere limiti di limite per profilo e globale, intervalli di date di validità e criteri di idoneità complessi che combinano attributi di profilo e appartenenza a un pubblico.

**Considerazioni chiave:**

- Richiede una configurazione più iniziale (posizionamenti, offerte, regole di idoneità, raccolte, decisioni)
- Le strategie di classificazione possono essere basate sulla priorità (manuale), basate su formule (espressione personalizzata) o basate sull’intelligenza artificiale (ottimizzazione automatica)
- La classificazione basata su IA richiede almeno 1.000 eventi di conversione per l’apprendimento dei modelli
- I contatori dei limiti di offerta possono presentare un lieve ritardo in scenari ad alto throughput
- Un’offerta di fallback deve essere configurata per i casi in cui nessuna offerta personalizzata è idonea

**Vantaggi:**

- Selezione dinamica dei contenuti per profilo senza mappatura hardcoded da segmento a contenuto
- Supporta criteri di idoneità e logica di classificazione complessi
- L’opzione con classificazione AI consente l’ottimizzazione automatica senza intervento manuale
- Il limite dell’offerta impedisce la sovraesposizione di contenuti specifici
- Gestione centralizzata delle offerte: le offerte possono essere riutilizzate su più campagne e canali

**Limitazioni:**

- Maggiore complessità di implementazione rispetto alla personalizzazione basata su segmenti
- La classificazione basata su IA richiede un volume di eventi di conversione sufficiente per l’apprendimento
- La valutazione delle decisioni aggiunge una latenza marginale rispetto alla distribuzione diretta dei contenuti basata su segmenti
- La classificazione basata su formula richiede una progettazione attenta per evitare la definizione di priorità non intenzionale

**Experience League:**

- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Opzione C: personalizzazione su più superfici (web + in-app + scheda di contenuti)

**Ideale per:** personalizzazione coerente su più superfici digitali: distribuzione di esperienze personalizzate coordinate su pagine web, messaggi in-app per dispositivi mobili e schede di contenuto. Ideale quando l’organizzazione dispone di proprietà sia per il web che per le app mobili e desidera una logica di personalizzazione unificata in tutti i punti di contatto digitali.

**Funzionamento:**

La personalizzazione su più superfici estende l’opzione A (basata su segmenti) o l’opzione B (basata su decisioni) per fornire contenuti personalizzati su più tipi di superfici di AJO. Ogni tipo di superficie, web, in-app, scheda di contenuto, può avere formati di contenuto e meccanismi di distribuzione diversi, ma la logica di personalizzazione sottostante (appartenenza al pubblico o decisioni) è condivisa.

L’implementazione prevede la configurazione di superfici di canale per ogni tipo di superficie, l’authoring di contenuti specifici per ogni superficie (web HTML/CSS per le superfici web, messaggi strutturati per le in-app, layout di schede per le schede di contenuto) e la creazione di campagne mirate per la superficie appropriata. Il Web SDK gestisce la consegna della superficie web, mentre il Mobile SDK gestisce la consegna in-app e delle schede di contenuto.

Le schede di contenuto sono particolarmente utili per i messaggi personalizzati persistenti e non consentiti sulle dashboard dell’account o nelle schermate home dell’app. I messaggi in-app sono ideali per le comunicazioni contestuali specifiche per sessione. La personalizzazione web gestisce banner hero, widget di consigli e contenuti promozionali.

**Considerazioni chiave:**

- Ogni tipo di superficie richiede la propria configurazione della superficie di canale e l’authoring dei contenuti
- È necessario implementare e configurare sia Web SDK che Mobile SDK
- Il contenuto deve essere progettato per ogni formato di superficie (dimensioni, layout, pattern di interazione diversi)
- I tipi di pubblico condivisi e la logica decisionale garantiscono la coerenza tra le superfici
- I test devono coprire tutti i tipi di superficie tra i dispositivi

**Vantaggi:**

- Esperienza di personalizzazione coerente in tutti i punti di contatto digitali
- Il pubblico condiviso e la logica decisionale riducono la duplicazione
- Le schede di contenuto forniscono una superficie di personalizzazione persistente e non intrusiva
- I messaggi in-app consentono la personalizzazione contestuale e specifica della sessione su dispositivi mobili

**Limitazioni:**

- Maggiore complessità di implementazione: richiede la configurazione per ogni tipo di superficie
- Richiede l’implementazione sia di Web SDK che di Mobile SDK
- Il contenuto deve essere progettato e mantenuto per ciascun formato di superficie
- L&#39;ambito del test aumenta con ogni tipo di superficie aggiuntiva

**Experience League:**

- [Panoramica del canale in-app](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [Canale scheda contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Introduzione al canale web](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/web/get-started-web)

### Confronto delle opzioni

La tabella seguente confronta le tre opzioni di implementazione.

| Criteri | Opzione A: Basata Su Segmenti | Opzione B: Basata Su Decisioni | Opzione C: superfici multiple |
| --- | --- | --- | --- |
| Ideale per | Mappatura segmento-contenuto nota | Selezione dinamica dei contenuti per profilo | Personalizzazione coerente su web + dispositivi mobili |
| Complessi | Bassa | Medium - Alta | Alta (si basa su A o B) |
| Latenza | Più veloce (risoluzione diretta dei segmenti) | Leggermente superiore (valutazione del processo decisionale) | Dipende dall’opzione sottostante (A o B) |
| Flessibilità | Limitato a coppie segmento-contenuto predefinite | Elevato: classificazione dinamica e idoneità | Massima: più superfici con logica condivisa |
| Gestione dei contenuti | Mappatura manuale segmento-contenuto | Libreria di offerte centralizzata con regole di idoneità | Contenuto per superficie con logica di personalizzazione condivisa |
| Ottimizzazione | Test A/B manuale | Ottimizzazione automatica con classificazione AI disponibile | Ottimizzazione per superficie |
| Richiede | Pubblico idoneo per Edge, Web SDK | Posizionamenti, offerte, regole di idoneità, decisioni | Web SDK + Mobile SDK, configurazioni a più superfici |
| Superfici supportate | Web (principale) | Web (principale) | Web + in-app + scheda contenuto |

### Scegli l’opzione giusta

Inizia con queste domande per selezionare l’approccio di implementazione corretto:

1. **Quante superfici?** Se hai bisogno di personalizzazione sia su app web che su app mobili, scegli l’opzione C (che si basa su A o B per la logica sottostante). Se disponibile solo per il Web, scegliere tra A e B.

2. **La selezione dei contenuti è dinamica?** Se disponi di una mappatura ben definita dei segmenti alle varianti di contenuto (ad esempio, 3-5 livelli di fedeltà, ciascuno con un banner principale specifico), scegli l’opzione A. Se devi effettuare una selezione da un catalogo di offerte con idoneità e classificazione complesse, scegli l’opzione B.

3. **È necessaria una selezione ottimizzata per l&#39;intelligenza artificiale?** Se desideri che il sistema impari e ottimizzi automaticamente quale contenuto funziona meglio per ciascun profilo, scegli l’opzione B con decisioning basato sull’intelligenza artificiale.

4. **Quante varianti di contenuto?** Se disponi di meno di 10 varianti di contenuto con mappature di segmenti chiare, l’opzione A è più semplice. Se decine di offerte necessitano di filtri e classificazione di idoneità, l’opzione B viene scalata meglio.

5. **Intendi estendere ad altri canali?** Se la logica decisionale dovesse infine distribuire offerte tra e-mail, web e altri canali, l’opzione B fornisce le basi decisionali centralizzate che il Offer Decisioning cross-channel estende.

## Fasi di implementazione

Questa sezione descrive in dettaglio ogni fase dell’implementazione.

### Fase 1: definire i tipi di pubblico e configurare la valutazione

**Funzione applicazione:** RT-CDP: Audience Evaluation

**Configurazione:** definire i tipi di pubblico che determinano la selezione dei contenuti di personalizzazione. Questi tipi di pubblico rappresentano i segmenti di visitatori che riceveranno esperienze personalizzate: livelli di fedeltà, fasi del ciclo di vita, coorti comportamentali o gruppi di affinità per i prodotti.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: metodo di valutazione del pubblico**
>
>Quanto rapidamente deve essere risolta l’iscrizione al pubblico per la personalizzazione? Questo influisce direttamente sul fatto che la personalizzazione possa avvenire al caricamento della pagina o richieda un ritardo.
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Valutazione Edge | Personalizzazione web/app in tempo reale che richiede una qualificazione al secondo secondario | Limitato a semplici controlli degli attributi di profilo e appartenenza ai segmenti. Nessuna query di serie temporali o aggregazione complessa. Obbligatorio per la personalizzazione dei visitatori noti. |
>| Valutazione in streaming | Qualificazione in tempo quasi reale quando i profili entrano/escono da tipi di pubblico in base a eventi comportamentali | Supporta query a singolo evento e finestre temporali limitate. Le modifiche del pubblico si riflettono in pochi minuti. Adatto per superfici in-app e schede di contenuto in cui è accettabile un leggero ritardo. |
>| Valutazione in batch | Il pubblico giornaliero si aggiorna per i segmenti basati su aggregazioni complesse o pattern storici | Supporto completo della funzione di regola del segmento. Non adatto alla personalizzazione in tempo reale, ma può integrare i tipi di pubblico edge con segmenti precalcolati complessi. |

>[!NOTE]
>**Decisione: attributi Personalization**
>
>Quali attributi di profilo devono guidare la definizione del pubblico e la selezione del contenuto?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Attributi del profilo (livello fedeltà, fase ciclo di vita) | Personalizzazione deterministica basata sulle proprietà note del cliente | Attributi stabili e ben definiti. Facile da mappare alle varianti di contenuto. Disponibile al perimetro se il profilo è configurato correttamente. |
>| Segnali comportamentali (cronologia acquisti, modelli di navigazione) | Personalization basato su comportamenti e modelli di coinvolgimento recenti | Richiede attributi calcolati o segmenti di streaming. Più dinamico, ma più complesso da mantenere. |
>| Punteggi tendenza ([!DNL Customer AI]) | Personalizzazione predittiva in base alla probabilità di conversione, abbandono o acquisto | Richiede attributi calcolati. Abilita una personalizzazione sofisticata ma richiede dati di apprendimento del modello ML. |
>| Approccio combinato | La maggior parte delle implementazioni di produzione | Utilizza gli attributi del profilo per la segmentazione primaria con segnali comportamentali e punteggi di tendenza per il perfezionamento. |

**Navigazione interfaccia utente:** Cliente > Tipi di pubblico > Crea pubblico > Genera regola

**Dettagli configurazione chiave:**

- Definire i tipi di pubblico utilizzando il Generatore di segmenti con espressioni della regola di segmento che fanno riferimento agli attributi del profilo
- Assicurarsi che le espressioni delle regole del segmento siano idonee per la valutazione Edge (controlli degli attributi semplici, appartenenza al segmento)
- Configurare tipi di pubblico idonei per Edge per casi di utilizzo di personalizzazione in tempo reale
- Considera l’eliminazione dei tipi di pubblico per escludere i visitatori convertiti o esclusi di recente

**Documentazione di Experience League:**

- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione Edge](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Segmentazione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/pql/overview)

### Fase 2: configurare le decisioni (solo opzioni B e C)

**Funzione applicazione:** AJO: Decisioning

**Configurazione:** configurare l&#39;infrastruttura decisionale che seleziona in modo dinamico il contenuto o l&#39;offerta ottimale per ogni visitatore. Ciò include posizionamenti (dove vengono visualizzate le offerte), offerte (quale contenuto è disponibile), regole di idoneità (chi si qualifica), strategie di classificazione (come scegliere il migliore) e criteri decisionali (come tutto si connette).

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: strategia di classificazione**
>
>Come dovrebbero essere classificate le offerte idonee per selezionare quella migliore per ogni visitatore?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Basato su priorità (manuale) | Casi d’uso semplici con gerarchia di offerte chiara | Ogni offerta ha un valore di priorità manuale. Vince l’offerta idonea con priorità più alta. Facile da capire e controllare. |
>| Basato su formula (espressione personalizzata) | Quando la classificazione deve considerare gli attributi del profilo | Le formule di classificazione personalizzate fanno riferimento ai dati del profilo (ad esempio, punteggio per livello fedeltà + aggiornamento). Flessibile ma richiede progettazione e test delle formule. |
>| Classificato in base all’intelligenza artificiale (ottimizzazione automatica) | Quando si desidera che il sistema ottimizzi automaticamente la selezione delle offerte | Il modello ML apprende quali offerte offrono le migliori prestazioni per quali profili. Richiede almeno 1.000 eventi di conversione per la formazione. Consigliato per posizionamenti a traffico elevato. |

>[!NOTE]
>**Decisione: limite offerte**
>
>Dovrebbero esserci limiti sul numero di volte in cui un’offerta viene mostrata a un visitatore o a tutti i visitatori?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Limite per profilo | Impedisci a fatica di visualizzare ripetutamente la stessa offerta | Limita le impression per visitatore in un determinato periodo di tempo. Garantisce varietà nell’esperienza personalizzata. |
>| Limite globale | Limitare il numero totale di impression per un&#39;offerta promozionale o a disponibilità limitata | Limita le impression totali a tutti i visitatori. Utile per promozioni in quantità limitata. |
>| Nessun limite | Contenuti sempreverdi o offerte sempre pertinenti | Nessun limite di impression. Adatto a contenuti persistenti come i banner del livello fedeltà. |

**Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Componenti > Gestione decisioni

**Dettagli configurazione chiave:**

- Crea posizionamenti per ogni superficie in cui verranno visualizzate le offerte (banner web, area messaggi in-app, slot per schede di contenuto)
- Definire le regole di idoneità utilizzando le espressioni della regola di segmento che fanno riferimento agli attributi di profilo e all’iscrizione al pubblico
- Creare offerte personalizzate con rappresentazioni di contenuto per ogni posizionamento
- Creare un’offerta di fallback che copra tutti i posizionamenti (visualizzati quando nessuna offerta personalizzata è idonea)
- Organizzare le offerte con i qualificatori di raccolta (tag) e raggrupparle in raccolte
- Creare un criterio di decisione che associa i posizionamenti alle raccolte con la strategia di classificazione selezionata

**Documentazione di Experience League:**

- [Creare i posizionamenti](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Creare regole di decisione](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Creare offerte di fallback](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Creare le raccolte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Fase 3: configurazione di superfici e canali

**Funzione applicazione:** AJO: Configurazione canale

**Configurazione:** configurare le superfici di canale che definiscono dove verranno consegnati i contenuti personalizzati. Ogni tipo di superficie (web, in-app, scheda di contenuto) richiede la propria configurazione che specifica l’URI della superficie, il formato del contenuto e i parametri di consegna.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: superfici di destinazione**
>
>Quali superfici digitali riceveranno il contenuto personalizzato?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Solo canale web | Personalization si concentra sulle proprietà web | Richiede Web SDK. Implementazione più semplice. Copre banner hero, aree promozionali, widget di consigli. |
>| Solo canale in-app | Personalization si concentra sulle esperienze delle app mobili | Richiede Mobile SDK. Include messaggi contestuali e specifici della sessione all’interno dell’app. |
>| Solo canale scheda di contenuto | Messaggi personalizzati persistenti e inammissibili | Richiede Mobile SDK o Web SDK. Le schede persistono fino a quando non vengono ignorate. Ideale per dashboard e schermi home. |
>| Superfici multiple (opzione C) | Personalizzazione coerente su web e dispositivi mobili | Richiede sia Web SDK che Mobile SDK. Ogni superficie necessita di configurazione e contenuto separati. |

>[!NOTE]
>**Decisione: approccio alla configurazione della superficie web**
>
>Come deve essere configurata la superficie web per la distribuzione dei contenuti?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Applicazione a pagina singola | App web moderne con routing lato client | Usa `renderDecisions: true` nelle chiamate di Web SDK `sendEvent`. Contenuto sottoposto a rendering automaticamente da SDK. |
>| Applicazione multipagina (MPA) | Pagine web tradizionali sottoposte a rendering del server | Contenuti consegnati al caricamento della pagina tramite risposta Edge Network. Potrebbe essere necessaria una configurazione URI di superficie a livello di pagina. |

**Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Amministrazione > Canali > Superfici di canale

**Dettagli configurazione chiave:**

- Per le superfici web: configura l’URI della superficie web che corrisponde alle pagine di destinazione
- Per le superfici in-app: configura la superficie dell’app mobile con l’ID app e il tipo di superficie
- Per le superfici delle schede di contenuto: configura la superficie della scheda di contenuto con l’ID app o il contesto web
- Assicurati che lo stream di dati abbia il servizio AJO abilitato per la consegna di personalizzazione Edge

**Documentazione di Experience League:**

- [Introduzione al canale web](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/web/get-started-web)
- [Configurazione del canale web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)
- [Prerequisiti per il canale in-app](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [Configurazione scheda contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)

### Fase 4: Creazione dei contenuti

**Funzione dell&#39;applicazione:** AJO: authoring dei messaggi

**Configurazione:** creazione di varianti di contenuto personalizzate per ogni superficie e segmento o offerta. Ciò include la progettazione del layout visivo, l’aggiunta di espressioni di personalizzazione che fanno riferimento agli attributi del profilo, la configurazione di blocchi di contenuto condizionali e la creazione di frammenti di contenuto riutilizzabili.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: approccio contenuto**
>
>Come dovrebbero essere strutturati i contenuti personalizzati per questo caso d’uso?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Blocchi di contenuto condizionali | Sezioni di contenuto diverse all’interno dello stesso layout variano a seconda del pubblico | Una singola risorsa di contenuto con regole condizionali. Efficiente per varianti minori (titolo, testo CTA, scambio immagini). |
>| Varianti di contenuto separate per trattamento | Layout o design fondamentalmente diversi per pubblico | Risorse di contenuto complete multiple. Più flessibile, ma più facile da mantenere. Richiesto per la sperimentazione dei contenuti. |
>| Contenuti basati sulle decisioni | Contenuto selezionato dinamicamente da un catalogo di offerta | Le rappresentazioni di offerta definiscono il contenuto. La gestione dei contenuti è centralizzata nella libreria delle offerte. |

>[!NOTE]
>**Decisione: profondità Personalization**
>
>Quanto contenuto deve essere personalizzato?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Personalizzazione a livello di superficie | Solo elementi specifici sono personalizzati (immagine protagonista, CTA, banner offerta) | Riduzione della complessità. Personalizzazione incentrata su aree di alto impatto. Punto di partenza più comune. |
>| Personalizzazione a pagina intera | L’intero layout di pagina o l’ordinamento dei contenuti è personalizzato | Maggiore complessità. Richiede la creazione di contenuti estesi. Offre l’esperienza più personalizzata. |
>| Personalizzazione a livello di token | Token di personalizzazione in linea (nome, livello, saldo punti) | Forma più semplice. Inserisce i valori degli attributi di profilo nel contenuto altrimenti statico. |

**Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Campagne > Crea campagna > Modifica contenuto

**Opzioni divergenti:**

**Per l&#39;opzione A (basata su segmenti):**

- Puoi creare varianti di contenuto per ogni segmento di pubblico utilizzando il web designer o l’editor di codice
- Utilizzare blocchi di contenuto dinamici con condizioni basate sull’iscrizione al pubblico
- Configurare le espressioni di personalizzazione che fanno riferimento agli attributi del profilo (ad esempio, `{{profile.person.name.firstName}}`, `{{profile.loyalty.tier}}`)
- Imposta le regole condizionali per visualizzare contenuti diversi in base all’iscrizione al segmento

**Per l&#39;opzione B (basata su decisioni):**

- Creare rappresentazioni del contenuto delle offerte per ogni posizionamento definito nella fase 2
- Ogni offerta ha una o più rappresentazioni (HTML, image, JSON) corrispondenti ai posizionamenti
- Integrare l’output decisionale nella pagina web o nell’app incorporando i posizionamenti di decisione
- Il contenuto viene selezionato dinamicamente in fase di runtime; l’authoring si concentra sui singoli elementi dell’offerta

**Per l&#39;opzione C (multi-superficie):**

- Creare contenuti specifici per ogni superficie di destinazione (HTML web/CSS, messaggi strutturati in-app, layout della scheda dei contenuti)
- Mantenere una logica di personalizzazione coerente tra le superfici adattandosi ai vincoli di formato di ciascuna superficie
- Test del rendering del contenuto su ciascun tipo di superficie

**Documentazione di Experience League:**

- [Creare esperienze web](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/web/create-web)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Funzioni di supporto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Creare messaggi in-app](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [Creare schede di contenuto](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/content-card/create-content-card)

### Fase 5: configurare e attivare le campagne

**Funzione dell&#39;applicazione:** AJO: Esecuzione della campagna

**Configurazione:** Crea e attiva la campagna AJO che associa il pubblico, la superficie e il contenuto per la consegna. Per la personalizzazione web, le campagne sono generalmente configurate per l’attivazione immediata o continua, anziché per invii pianificati una tantum.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: tipo di campagna**
>
>Come deve essere attivata la campagna di personalizzazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Campagna pianificata (sempre attiva) | Personalizzazione continua che viene eseguita in modo continuo per tutti i visitatori idonei | Impostare la data di inizio su immediata e nessuna data di fine. La campagna rimane attiva finché non viene arrestata manualmente. Più comune per la personalizzazione web. |
>| Campagna pianificata (con limiti di tempo) | Personalization associato a uno specifico periodo di promozione | Impostare le date di inizio e di fine. Campaign si interrompe automaticamente dopo la data di fine. Adatto per promozioni stagionali o offerte a tempo limitato. |
>| Campagna attivata da API | Personalization attivato da un evento applicazione specifico | Attivazione a livello di programmazione. Utile quando la personalizzazione dovrebbe apparire solo in risposta a specifici eventi di sistema. |

>[!NOTE]
>**Decisione: limite di frequenza**
>
>La frequenza delle impression deve essere limitata per questa personalizzazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Applicare le regole di frequenza | Personalizzazione promozionale o basata su offerte che potrebbero affaticare i visitatori | Impedisce che la stessa personalizzazione venga visualizzata troppe volte. Configurato tramite le regole aziendali di AJO. |
>| Nessun limite di frequenza | Personalizzazione dei contenuti Evergreen (banner livello fedeltà, contenuto dashboard) | Contenuti sempre rilevanti che non causano affaticamento. Non è necessario alcun limite di impression. |

**Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Campagne > Crea campagna

**Dettagli configurazione chiave:**

- Seleziona il canale web, in-app o della scheda di contenuto e la superficie configurata nella fase 3
- Associa il pubblico di destinazione definito nella fase 1
- Collegare i contenuti creati nella fase 4
- Configurare la pianificazione della campagna (immediata, intervallo di date o attivata da API)
- Rivedere e attivare la campagna
- Per la sperimentazione dei contenuti: abilita l’interruttore dell’esperimento, definisci i trattamenti, imposta l’allocazione del traffico e le metriche di successo prima dell’attivazione

**Documentazione di Experience League:**

- [Creare una campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Introduzione alle campagne](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Regole di frequenza](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Introduzione all’esperimento sui contenuti](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Creare un esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### Fase 6: tenere traccia delle impression e raccogliere i dati

**Funzione dell&#39;applicazione:** AEP: Origini dati e raccolta

**Configurazione:** assicurati che le impression, le interazioni e le conversioni da esperienze personalizzate vengano tracciate nella piattaforma per il reporting, la rivalutazione del pubblico e l&#39;ottimizzazione del decisioning.

**Dettagli configurazione chiave:**

- Verifica che Web SDK invii `decisioning.propositionDisplay` eventi quando viene eseguito il rendering del contenuto personalizzato
- Verifica che Web SDK invii `decisioning.propositionInteract` eventi quando i visitatori interagiscono con contenuti personalizzati (clic, chiusure)
- Per Mobile SDK: verifica che vengano acquisiti gli eventi di interazione dei messaggi in-app e delle schede di contenuto
- Configurare il tracciamento degli eventi di conversione per le metriche di successo a valle (acquisti, iscrizioni, adozione di funzioni)
- Assicurati che gli eventi includano l’ID proposta per l’attribuzione a specifiche decisioni di personalizzazione

**Documentazione di Experience League:**

- [Panoramica di Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/home)
- [Tracciare gli eventi con Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/commands/sendevent/overview)
- [Panoramica di Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)

### Fase 7: generare rapporti e ottimizzare

**Funzione dell&#39;applicazione:** AJO: Reporting &amp; Performance Analysis, Reporting &amp; Analysis

**Configurazione:** Imposta il monitoraggio e l&#39;analisi delle prestazioni per misurare l&#39;efficacia della personalizzazione tra superfici, segmenti e varianti di contenuto. Utilizza i rapporti nativi di AJO per le metriche operative e [!DNL Customer Journey Analytics] per l&#39;analisi dell&#39;impatto aziendale cross-channel.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: ambito di reporting**
>
>Quale livello di analisi è necessario per questo caso d’uso di personalizzazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Solo rapporti nativi di AJO | Monitoraggio operativo delle metriche di consegna e coinvolgimento | Rapporti incorporati sulle campagne con dati su impression, clic e conversione. Configurazione più rapida. |
>| Analisi cross-channel di CJA | Analisi approfondita dell’impatto della personalizzazione sui risultati aziendali | Richiede connessione CJA e visualizzazione dati. Consente l’analisi funnel, il confronto tra coorti e la modellazione di attribuzione tra canali diversi. |
>| Sia AJO che CJA | Visibilità operativa e analitica completa | Utilizza AJO per il monitoraggio quotidiano e CJA per l’analisi strategica. Consigliato per le implementazioni di produzione. |

**Navigazione interfaccia utente:**

- Rapporti di AJO: Campagne > Seleziona campagna > Visualizza rapporto
- CJA: Progetti > Crea nuovo progetto

**Dettagli configurazione chiave:**

- Accedere ai rapporti live delle campagne durante la consegna della personalizzazione attiva
- Esaminare i rapporti cronologici per le campagne completate o l’analisi periodica
- Per CJA: configura una connessione che includa i set di dati dell’evento esperienza AJO e crea una visualizzazione dati con metriche di personalizzazione
- Creare dashboard tenendo traccia del tasso di coinvolgimento nella personalizzazione, dell’incremento della conversione, del tasso di accettazione dell’offerta e dei ricavi per visita
- Per la personalizzazione basata sulle decisioni (opzione B): monitora le prestazioni dell’offerta in base al posizionamento e all’efficacia della strategia di classificazione

**Documentazione di Experience League:**

- [Rapporto live delle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapporto sull’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/home)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Considerazioni sull’implementazione

Questa sezione descrive guardrail, insidie comuni, best practice e decisioni di compromesso pertinenti a questo caso d’uso.

### Guardrail e limiti

- Le ricerche Edge Network hanno un tempo di risposta SLA inferiore a 200 ms per i segmenti valutati edge: [guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)
- Massimo 4.000 definizioni di segmenti per sandbox: [Guardrail di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)
- I segmenti Edge sono limitati a semplici controlli degli attributi e query di appartenenza ai segmenti, ovvero nessuna query di serie temporali. [Segmentazione Edge](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/edge-segmentation)
- In Edge può essere attivo un solo criterio di unione per sandbox: [Criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview)
- Massimo 10.000 offerte personalizzate approvate per sandbox — [Guardrail di gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/get-started/guardrails)
- Massimo 30 posizionamenti per decisione: [guardrail Journey Optimizer](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/get-started/guardrails)
- I modelli di classificazione IA richiedono almeno 1.000 eventi di conversione per la formazione
- Il tempo di risposta per la consegna delle offerte SLA è inferiore a 500 ms a P95 per le richieste con ambito singolo
- Massimo 500 campagne live attive per sandbox: [guardrail Journey Optimizer](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/get-started/guardrails)
- Massimo 25 attributi calcolati attivi per sandbox: [Guardrail attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview)

### Insidie comuni

- **Criterio di unione di Edge non configurato:** senza un criterio di unione attivo per Edge, Edge Network non è in grado di risolvere il profilo autenticato, causando errori di personalizzazione o il fallback a un comportamento anonimo. Verifica che nella sandbox sia presente esattamente un criterio di unione con `isActiveOnEdge: true`.
- **Pubblico non idoneo per Edge:** Se le espressioni della regola del segmento di pubblico utilizzano query di serie temporali, aggregazioni complesse o `inSegment()` riferimenti a segmenti solo batch, non saranno idonee per la valutazione Edge e non possono alimentare la personalizzazione in tempo reale. Convalida l’idoneità Edge durante la definizione del pubblico.
- **Intervallo di unione delle identità durante l&#39;autenticazione:** Quando un visitatore passa da anonimo a autenticato, potrebbe verificarsi un breve momento in cui il profilo non è ancora stato risolto. Verificare che l&#39;unione delle identità sia configurata correttamente e che Web SDK invii immediatamente l&#39;identità autenticata tramite `identityMap` al momento dell&#39;accesso.
- **Offerta di fallback mancante nel decisioning:** Se non è configurata alcuna offerta di fallback e nessuna offerta personalizzata è idonea per un visitatore, la decisione restituisce un contenuto vuoto, creando un&#39;esperienza non funzionante. Configura sempre un’offerta di fallback che copra tutti i posizionamenti.
- **Web SDK non invia eventi di visualizzazione della proposta:** Se `renderDecisions` è impostato su `true` ma gli eventi di visualizzazione non vengono inviati, il reporting non rifletterà le impression effettive. Verifica il tracciamento degli eventi esaminando le richieste di rete negli strumenti di sviluppo del browser.
- **Sfarfallio del contenuto al caricamento della pagina:** Se il contenuto personalizzato non è pre-nascosto durante la chiamata decisionale, i visitatori potrebbero visualizzare brevemente il contenuto predefinito prima che venga sostituito. Utilizza il frammento pre-hiding o il pre-hiding basato su CSS per eliminare lo sfarfallio.

### Best practice

- Inizia con la personalizzazione basata sui segmenti (opzione A) per l’implementazione iniziale, quindi passa all’opzione basata sulle decisioni (opzione B) man mano che il catalogo delle offerte cresce e le esigenze di ottimizzazione aumentano
- Utilizza i tipi di pubblico valutati Edge ogni volta che è possibile per la personalizzazione in tempo reale; riserva i tipi di pubblico in streaming e in batch per casi d’uso complementari
- Implementa la sperimentazione dei contenuti su esperienze personalizzate per verificare che la personalizzazione determini un incremento misurabile rispetto al contenuto predefinito
- Progettare la personalizzazione con una strategia di degradazione graduale: se il profilo non può essere risolto al limite, visualizza un contenuto predefinito ben progettato anziché un’esperienza interrotta
- Utilizza attributi calcolati per creare segnali di personalizzazione di alto valore come il punteggio di coinvolgimento, l’affinità di prodotto e i giorni dall’ultimo acquisto, che migliorano la qualità della personalizzazione basata su segmenti e decisioning
- Mantenere un processo di governance dei contenuti per garantire che i contenuti personalizzati rimangano aggiornati, nel brand e conformi su tutte le superfici
- Monitora le prestazioni di personalizzazione per segmento per identificare quali tipi di pubblico traggono maggior beneficio dalla personalizzazione e dove l’incremento è più forte

### Decisioni di compromesso

>[!NOTE]
>**Compensazione: granularità di Personalization rispetto alla complessità della gestione dei contenuti**
>
>Una personalizzazione più granulare (più segmenti, più varianti di contenuto, più superfici) offre esperienze sempre più personalizzate, ma richiede proporzionalmente più lavoro di creazione, manutenzione e governance dei contenuti.
>
>- **Maggiore granularità favorisce:** migliore esperienza del cliente, maggiore coinvolgimento, maggiore incremento di conversione
>- **Minore granularità a favore:** implementazione più rapida, minore onere di manutenzione dei contenuti, governance più semplice
>- **Consiglio:** inizia con 3-5 segmenti ad alto impatto (ad esempio, livelli di fedeltà o fasi del ciclo di vita) con una chiara differenziazione dei contenuti. Espandi la granularità in base all’incremento delle prestazioni misurato. Utilizza il decisioning (opzione B) per scalare la granularità senza una crescita proporzionale della gestione dei contenuti.

>[!NOTE]
>**Compensazione: decisioni in tempo reale rispetto al controllo deterministico dei contenuti**
>
>La personalizzazione basata sulle decisioni (opzione B) fornisce un’ottimizzazione dinamica, ma riduce il controllo diretto sul contenuto visualizzato da ogni visitatore. La personalizzazione basata su segmenti (opzione A) fornisce un controllo deterministico completo, ma limita l’ottimizzazione dinamica.
>
>- **Preferenze di Decisioning:** Scalabilità, ottimizzazione automatica, scenari di idoneità complessi
>- **Preferenze basate su segmenti:** Predittività, controllo di conformità, trasparenza delle parti interessate
>- **Consiglio:** utilizza la personalizzazione basata sui segmenti per i contenuti sensibili alla conformità (messaggi normativi, prezzi specifici per livello) in cui è richiesto un controllo esatto. Utilizza il decisioning per contenuti promozionali, offerte e consigli laddove l’ottimizzazione dinamica aggiunge valore.

>[!NOTE]
>**Compensazione: disponibilità dei dati di Edge e ricchezza della personalizzazione**
>
>La personalizzazione valutata da Edge è limitata agli attributi disponibili nell’archivio dei profili edge. Segnali di personalizzazione più completi (cronologia comportamentale completa, attributi computati complessi) possono richiedere una ricerca lato server o una precomputazione.
>
>- **Solo Edge favorisce:** Latenza al secondo, architettura più semplice
>- **L&#39;arricchimento precalcolato favorisce:** segnali di personalizzazione più ricchi, definizioni di pubblico più sofisticate
>- **Consiglio:** utilizza attributi calcolati per preaggregare segnali comportamentali avanzati in attributi di profilo disponibili per Edge. Questo fornisce la ricchezza dei dati comportamentali con la velocità della valutazione Edge.

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sulle tecnologie e le configurazioni a cui si fa riferimento in questa guida.

### Personalizzazione del canale web

- [Introduzione al canale web](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/web/get-started-web)
- [Creare esperienze web](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/web/create-web)
- [Configurazione del canale web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)

### Canali in-app e schede di contenuto

- [Panoramica del canale in-app](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [Prerequisiti per il canale in-app](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [Creare messaggi in-app](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [Canale scheda contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Configurazione scheda contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)
- [Creare schede di contenuto](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/content-card/create-content-card)

### Gestione delle decisioni

- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Creare i posizionamenti](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Creare regole di decisione](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Creare offerte di fallback](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Creare le raccolte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Personalization e contenuti

- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Funzioni di supporto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilizzare i frammenti di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

### Tipi di pubblico e segmentazione

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione Edge](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Segmentazione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/pql/overview)

### Identità e profilo

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home)
- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Regole di collegamento del grafo identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/identity-linking-logic)
- [Panoramica del profilo](https://experienceleague.adobe.com/it/docs/experience-platform/profile/home)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview)

### Raccolta dati e SDK

- [Panoramica di Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/home)
- [Installare Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/install/overview)
- [Panoramica di Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/it/docs/experience-platform/datastreams/configure)
- [Panoramica dell’API del server Edge Network](https://experienceleague.adobe.com/it/docs/experience-platform/edge-network-server-api/overview)

### Campagne e sperimentazione

- [Introduzione alle campagne](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Creare una campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Introduzione all’esperimento sui contenuti](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Creare un esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapporto sull’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### Attributi calcolati e arricchimento

- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview)
- [Guida dell’interfaccia utente attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/ui)
- [Panoramica di Customer AI](https://experienceleague.adobe.com/it/docs/experience-platform/intelligent-services/customer-ai/overview)

### Reporting e analisi

- [Rapporto live delle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Panoramica di CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-overview/cja-overview)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/home)

### Governance e privacy

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home)
- [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/it/docs/experience-platform/data-lifecycle/home)

### Guardrail

- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/get-started/guardrails)
- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)
- [Guardrail del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/guardrails)
