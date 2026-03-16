---
title: Personalization Web visitatore anonimo
description: Scopri come distribuire contenuti web personalizzati a visitatori non identificati in base a segnali comportamentali durante la sessione.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '8076'
ht-degree: 1%

---


# Personalizzazione web visitatore anonimo

Questo piano di riferimento fornisce indicazioni sull’implementazione per la distribuzione di contenuti web personalizzati a visitatori anonimi (non identificati) sulla base di segnali comportamentali durante la sessione. Copre l&#39;intero ciclo di vita dell&#39;implementazione, dalla configurazione di [!DNL Web SDK] alla definizione del pubblico perimetrale fino alla distribuzione dei contenuti e al reporting delle prestazioni, ed è progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che lavorano con [!DNL Adobe Journey Optimizer] (AJO), [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) e [!DNL Adobe Experience Platform] (AEP).

Utilizza questo piano per comprendere l’architettura, valutare le opzioni di implementazione, prendere decisioni di configurazione informate e individuare la documentazione Experience League pertinente per ogni fase di implementazione.

Il modello funziona con dati limitati, solo ciò che può essere osservato nella sessione corrente e qualsiasi profilo edge anonimo accumulato da visite precedenti con lo stesso dispositivo o cookie. Questo lo rende adatto per la personalizzazione top-of-funnel in cui il visitatore non ha un account o non è stato autenticato.

## Panoramica del caso d’uso

Visitatore anonimo Web Personalization risponde all&#39;esigenza aziendale di fornire contenuti pertinenti e personalizzati ai visitatori del sito Web che non sono ancora stati identificati: non hanno effettuato l&#39;accesso, non hanno un&#39;identità nota e non possono essere risolti in un profilo cliente unificato. Nonostante questo limite, è possibile ottenere una personalizzazione significativa utilizzando segnali comportamentali durante la sessione: pagine visualizzate, tempo sul sito, profondità di scorrimento, origine di riferimento, posizione geografica, tipo di dispositivo e parametri della campagna UTM.

Questo modello utilizza le superfici dei canali web di AJO e le esperienze basate su codice per modificare il contenuto della pagina in tempo reale. La segmentazione di Edge è il metodo di valutazione principale, in quanto le decisioni devono essere prese con latenza di secondo secondario mentre il visitatore naviga nel sito. [!DNL Web SDK] raccoglie i segnali comportamentali e li invia a [!DNL AEP Edge Network], dove le regole del pubblico valutate Edge determinano la variante di contenuto da distribuire.

A differenza della personalizzazione web/app per visitatore noto, che sfrutta l&#39;appartenenza completa unificata a profilo e segmento, questo modello è vincolato ai dati osservabili nella sessione corrente e a qualsiasi profilo Edge anonimo associato all&#39;ECID del visitatore ([!DNL Experience Cloud ID]). Questa distinzione è fondamentale per la pianificazione dell&#39;implementazione: i segnali comportamentali disponibili per la personalizzazione sono limitati a ciò che [!DNL Web SDK] acquisisce e a ciò che persiste nell&#39;archivio dei profili edge nelle sessioni tramite l&#39;ECID basato su cookie.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

**[Aumenta coinvolgimento sito Web](../../business-objectives/acquisition-growth/increase-website-engagement.md)**

Migliora il tempo sul sito, le pagine per sessione e l’interazione con i contenuti web attraverso esperienze rilevanti personalizzate in base ai segnali dei visitatori anonimi.

| KPI |
| --- |
| Tempo sulla pagina (web) |
| Coinvolgimento |
| Tassi di conversione |

**[Distribuisci esperienze cliente personalizzate](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

Personalizza contenuti, offerte e messaggi in base alle preferenze, ai comportamenti e alla fase del ciclo di vita dei singoli utenti, anche per i visitatori che non si sono ancora identificati.

| KPI |
| --- |
| Coinvolgimento |
| Tassi di conversione |
| Soddisfazione del cliente (CSAT) |

**[Aumentare i tassi di conversione](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

Migliora la percentuale di visitatori e potenziali clienti che completano le azioni desiderate, ad esempio acquisti, iscrizioni o invii di moduli, presentando i contenuti più rilevanti in base al contesto comportamentale.

| KPI |
| --- |
| Tassi di conversione |
| Conversione lead |
| Costo per lead |

## Esempi di casi d’uso tattici

Gli esempi seguenti illustrano scenari specifici in cui è possibile applicare questo modello.

- **Test A/B del titolo della pagina di destinazione basato sull&#39;origine di riferimento** — Test di titoli diversi per i visitatori provenienti da Google, social media o traffico diretto per ottimizzare il coinvolgimento tramite il canale di acquisizione
- **Consigli di affinità tra categorie in base al comportamento di navigazione**: visualizzazione di consigli su prodotti o contenuti in base alle pagine visualizzate nella sessione corrente per aumentare l&#39;individuazione e la conversione
- **Offerta con intento di uscita per i visitatori che stanno per uscire** — Presenta un&#39;offerta promozionale o un modulo di acquisizione lead quando i segnali comportamentali indicano che il visitatore sta per abbandonare il sito
- **Banner promozionale con targeting geografico**: mostra promozioni specifiche per la località, contenuto del localizzatore dello store o offerte regionali in base alla posizione geografica del visitatore
- **Ottimizzazione del layout del contenuto specifico per il dispositivo**: adatta il layout del contenuto, le dimensioni delle immagini e il posizionamento del CTA in base al fatto che il visitatore si trovi su desktop, tablet o dispositivi mobili
- **Messaggi di benvenuto nuovi rispetto a visitatori di ritorno**: differenzia l&#39;esperienza per i nuovi visitatori rispetto ai visitatori anonimi di ritorno utilizzando la persistenza ECID nelle sessioni
- **Consigli sui contenuti basati sulle pagine visualizzate nella sessione corrente**: superficie dinamica di articoli, prodotti o risorse correlati in base alle pagine già visualizzate dal visitatore
- **Banner hero dinamico basato sui parametri della campagna UTM** — Personalizza il banner hero in modo che corrisponda al messaggio o alla creatività della campagna di riferimento

## Indicatori chiave di prestazioni

Utilizza i seguenti KPI per misurare l’efficacia di questo modello di caso d’uso.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Tasso di impression Personalization | Percentuale di visualizzazioni di pagina idonee in cui è stato consegnato il contenuto personalizzato | Rapporto di AJO campaign: impression/visualizzazioni di pagina totali |
| Percentuale di click-through (CTR) | Percentuale di impression di contenuto personalizzato che danno luogo a un clic | Rapporto campagna AJO: clic/impression |
| Incremento di coinvolgimento | Aumento del tempo su pagina, pagine per sessione o profondità di scorrimento per contenuti personalizzati e predefiniti | confronto tra aree di lavoro di CJA: coorte personalizzate e controllo |
| Tasso di conversione | Percentuale di visitatori esposti a contenuti personalizzati che completano l’azione desiderata | CJA funnel analysis: impression > interazione > conversione |
| Riduzione frequenza di mancato recapito | Diminuzione delle sessioni a pagina singola per i visitatori che ricevono contenuti personalizzati | Analisi della sessione di CJA: delta del tasso di mancato recapito per valori personalizzati e predefiniti |
| Percentuale vittorie esperimento | Percentuale di test A/B che producono un vincitore statisticamente significativo | rapporto sull’esperimento AJO: esperimenti che raggiungono la soglia di affidabilità |

## Schema del caso d’uso

Di seguito sono descritti il pattern principale e la catena di funzioni per questo caso d’uso.

**Visitatore anonimo Web Personalization**

Distribuisci contenuti personalizzati in base a segnali comportamentali durante la sessione per visitatori non identificati tramite il canale web AJO.

**Catena di funzioni:** Configurazione superficie web > Valutazione regole comportamentali > Consegna contenuto > Tracciamento impression > Reporting

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Adobe Journey Optimizer] (AJO)**: configurazione della superficie del canale web, authoring dei contenuti (esperienze web e basate su codice), esecuzione di campagne, sperimentazione dei contenuti (test A/B), decisioning (selezione dinamica dei contenuti) e reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Segmentazione di Edge per la valutazione del pubblico in tempo reale basata su segnali comportamentali durante la sessione; gestione anonima dei profili edge
- **[!DNL Adobe Experience Platform] (AEP)** — [!DNL Web SDK] per la raccolta di segnali comportamentali, [!DNL Edge Network] per il routing dei dati in tempo reale e la consegna della personalizzazione, configurazione dello stream di dati

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve essere al suo posto | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Presunto sul posto | Sandbox di AJO con autorizzazioni per il canale web configurate. [!DNL Web SDK] autorizzazioni di implementazione e accesso allo stream di dati concessi al team di implementazione. Agli utenti sono stati assegnati ruoli che consentono la configurazione del canale web, la gestione dell’audience e l’esecuzione della campagna. | [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Obbligatorio | Lo schema Experience Event acquisisce segnali comportamentali web (visualizzazioni di pagina, clic, profondità di scorrimento, dati di riferimento, parametri UTM). Lo schema deve includere gruppi di campi di interazione web standard ed essere abilitato per il profilo Edge in modo da supportare la valutazione in tempo reale. È necessario creare un set di dati corrispondente e abilitarlo per il profilo. | [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Origini dati e raccolta | Obbligatorio | [!DNL Web SDK] deve essere implementato in tutte le proprietà web di destinazione con uno stream di dati configurato per instradare i dati a [!DNL AEP Edge Network]. Lo stream di dati deve avere i servizi [!DNL Adobe Experience Platform] e [!DNL Adobe Journey Optimizer] abilitati. Si tratta di una dipendenza critica. Senza [!DNL Web SDK], non è possibile alcuna raccolta di segnali comportamentali o distribuzione di esperienze. | [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home) |
| Configurazione identità e profilo | Obbligatorio | ECID ([!DNL Experience Cloud ID]) configurato come spazio dei nomi dell&#39;identità primaria per i visitatori anonimi. Il criterio di unione di Edge deve essere configurato con `isActiveOnEdge: true` per risolvere i dati di profilo anonimi nel server Edge di. Su Edge può essere attivo un solo criterio di unione per sandbox. | [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| Definizione e segmentazione del pubblico | Obbligatorio | Segmenti di pubblico valutati da Edge definiti in base ai segnali comportamentali durante la sessione. La segmentazione di Edge è obbligatoria per la latenza di valutazione dei secondi secondari. Le regole di segmento devono utilizzare solo espressioni di regole di segmento idonee per gli edge (controlli di attributi semplici e appartenenza ai segmenti, senza query di serie temporali o aggregazioni complesse). | [Segmentazione di Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Non applicabile | Valore limitato per i visitatori anonimi, in quanto i dati del profilo storico da aggregare sono minimi. Può diventare applicabile se il profilo Edge accumula dati comportamentali significativi da precedenti visite anonime in più sessioni. | [Panoramica attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Consigliato | La scadenza del profilo pseudonimo deve essere configurata per i profili edge anonimi in modo da gestire l’archiviazione e rispettare i requisiti di privacy. I profili solo ECID possono essere impostati per scadere tra 14 e 365 giorni. I criteri di consenso dei cookie devono essere applicati per la raccolta dei dati comportamentali. | [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Etichettatura e applicazione dell’utilizzo dati | Consigliato | Le etichette di governance sui dati comportamentali garantiscono la conformità, in particolare per il geotargeting (etichetta geografica sensibile a S2) e la personalizzazione basata su dispositivi. Le etichette impediscono l’utilizzo di dati comportamentali limitati in contesti di personalizzazione non autorizzati. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Monitoraggio e osservabilità | Consigliato | Il monitoraggio del flusso di dati di [!DNL Edge Network] e [!DNL Web SDK] consente di rilevare i problemi di consegna della personalizzazione. Configura gli avvisi per gli errori dello stream di dati, gli errori di acquisizione e le anomalie di consegna Edge. Critico per le distribuzioni di produzione in cui gli errori di personalizzazione degradano l’esperienza del visitatore. | [Panoramica di Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting e analisi | Incluso | Il reporting sulle prestazioni di Personalization fa parte della catena di funzioni (fase 5). L’analisi CJA dell’efficacia della personalizzazione dei visitatori anonimi consente un’analisi approfondita del funnel, un confronto tra coorti e una misurazione dell’impatto della conversione oltre a quelli forniti dai rapporti nativi di AJO. | [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Journey Optimizer] (AJO)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Configurazione canali | Fase 1: configurazione della superficie web | Configurare le superfici di canale web definendo dove verranno consegnati i contenuti personalizzati sulle proprietà web di target |
| Authoring dei messaggi | Fase 3: authoring dei contenuti e creazione di varianti | Puoi creare varianti di contenuto personalizzate per le superfici web utilizzando web designer, editor di esperienze basato su codice o modelli di contenuto |
| Esecuzione della campagna | Fase 4: configurazione di Campaign &amp; Delivery | Creare e attivare campagne web che associano tipi di pubblico, contenuti e configurazioni di consegna |
| Decisioni | Fase 3: authoring dei contenuti e creazione di varianti (opzione C) | Configurare criteri di decisione, regole di idoneità e strategie di classificazione per la selezione dinamica dei contenuti basata su segnali comportamentali |
| Sperimentazione sui contenuti | Fase 3: authoring dei contenuti e creazione di varianti (opzione B) | Configurare esperimenti A/B e multivariati sui contenuti con allocazione del traffico, metriche di successo e soglie di affidabilità |
| Reporting e analisi delle prestazioni | Fase 5: Reporting e analisi delle prestazioni | Monitorare le metriche di consegna della personalizzazione, l’efficacia delle varianti, i risultati degli esperimenti e l’impatto sulla conversione |

### [!DNL Real-Time CDP] (RT-CDP)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Valutazione del pubblico | Fase 2: Definizione del pubblico comportamentale | Definire e valutare segmenti di pubblico basati su edge utilizzando segnali comportamentali durante le sessioni per il targeting di personalizzazione in tempo reale |

## Prerequisiti

Completa quanto segue prima di iniziare l’implementazione.

- [ ] [!DNL Web SDK] è implementato in tutte le proprietà web di destinazione con `sendEvent` chiamate che acquisiscono visualizzazioni di pagina, clic e interazioni comportamentali rilevanti
- [ Lo stream di dati ] è configurato nell&#39;interfaccia utente di Data Collection con i servizi [!DNL Adobe Experience Platform] e [!DNL Adobe Journey Optimizer] abilitati
- [ Lo schema ] Experience Event esiste con gruppi di campi di interazione web (visualizzazioni di pagina, dati di riferimento, parametri UTM, contesto del dispositivo) ed è abilitato per il profilo
- [ Lo spazio dei nomi dell&#39;identità ECID ] è configurato e designato come identità primaria nello schema dell&#39;evento comportamentale Web
- [ Il criterio di unione di ] Edge è configurato con `isActiveOnEdge: true` nella sandbox di destinazione
- [ Il provisioning e l&#39;accesso al canale web di AJO ] sono disponibili nella sandbox di destinazione
- [ ] Le varianti di contenuto (copia, immagini, CTA) sono progettate e approvate per ogni caso d&#39;uso di personalizzazione
- [ ] Le metriche di successo sono definite (che cosa costituisce un evento di conversione o di coinvolgimento per la misurazione)
- [ Il meccanismo di consenso dei cookie ] è implementato sul sito Web per rispettare le normative sulla privacy prima di raccogliere i dati comportamentali

## Opzioni di implementazione

Questa sezione descrive tre approcci di implementazione. Seleziona l’opzione che meglio si adatta ai tuoi requisiti di personalizzazione.

### Opzione A: personalizzazione web basata su regole

**Ideale per:** Personalizzazione semplice e deterministica: banner con targeting geografico, titoli specifici per l&#39;origine di riferimento, layout specifici per il dispositivo, messaggi nuovi e di ritorno per i visitatori. Scegli questa opzione quando la variante di contenuto può essere determinata da una logica condizionale diretta (se la condizione X mostra il contenuto Y).

**Funzionamento:**

La personalizzazione basata su regole utilizza segmenti di pubblico valutati Edge per determinare quale variante di contenuto visualizzare. Ogni segmento di pubblico viene mappato su una specifica variante di contenuto attraverso regole condizionali definite nella campagna. Quando un visitatore carica una pagina, [!DNL Web SDK] invia segnali comportamentali a [!DNL Edge Network], che valuta il profilo Edge del visitatore in base alle regole definite per il pubblico in millisecondi. La variante di contenuto corrispondente viene restituita nella risposta [!DNL Edge Network] ed è sottoposta a rendering sulla pagina.

Questo approccio richiede la definizione di segmenti di pubblico distinti in RT-CDP (ad esempio, &quot;visitatori da Google search&quot;, &quot;visitatori in California&quot;, &quot;visitatori da dispositivi mobili&quot;) e la creazione di varianti di contenuto corrispondenti in AJO. La campagna associa ogni pubblico alla rispettiva variante di contenuto utilizzando regole di contenuto condizionale o campagne separate per segmento. Non è coinvolta alcuna classificazione di IA o suddivisione del traffico; la relazione tra pubblico e contenuto è deterministica.

**Considerazioni chiave:**

- Richiede criteri di pubblico ben definiti che possono essere espressi come espressioni di regole di segmento idonee per Edge
- Le varianti di contenuto devono essere precreate per ciascun segmento di pubblico
- L’aggiunta di nuove regole di personalizzazione richiede la creazione di nuovi segmenti di pubblico e varianti di contenuto
- Non fornisce misurazioni statistiche sull’efficacia delle varianti di contenuto

**Vantaggi:**

- Semplice da implementare e comprendere: chiara relazione causa-effetto tra pubblico e contenuto
- Non è necessario alcun sovraccarico di sperimentazione o suddivisione del traffico
- Il comportamento deterministico rende semplici i test e il controllo qualità
- Latenza bassa perché la valutazione Edge è puramente basata su regole
- Funziona bene quando l’azienda sa già quale contenuto funziona meglio per ogni segmento

**Limitazioni:**

- Nessun meccanismo integrato per misurare se la personalizzazione migliora i risultati rispetto al contenuto predefinito
- Richiede un processo decisionale manuale per quanto riguarda il contenuto da visualizzare in ogni segmento
- Non si adatta o si ottimizza nel tempo — regole statiche fino a quando non vengono modificate manualmente
- La scalabilità a molti segmenti e varianti aumenta la complessità della configurazione

**Experience League:**

- [Introduzione al canale web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Segmentazione Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Opzione B: Personalizzazione web basata sulla sperimentazione

**Ideale per:** test A/B e multivariati — test delle varianti dei titoli, colori dei pulsanti CTA, alternative di layout, offerte promozionali — con misurazione della significatività statistica. Scegli questa opzione quando devi convalidare la variante di contenuto con le prestazioni migliori prima di confermare una regola di personalizzazione permanente.

**Funzionamento:**

La personalizzazione basata sulla sperimentazione utilizza la sperimentazione dei contenuti di AJO per allocare in modo casuale i visitatori ai gruppi di trattamento dei contenuti e misurare quale variante funziona meglio rispetto a una metrica di successo definita. Il traffico viene suddiviso tra le varianti (ad esempio, 50/50 per A/B, 33/33/34 per A/B/C) e le prestazioni vengono tracciate fino al raggiungimento della significatività statistica.

L’esperimento è incorporato in una campagna web AJO. Quando un visitatore carica una pagina, [!DNL Edge Network] le assegna a un gruppo di trattamento in base all&#39;allocazione del traffico configurata. Il visitatore vede costantemente lo stesso trattamento per la durata dell’esperimento (persistenza a livello di sessione o di visitatore a seconda della configurazione). Le metriche di successo (clic, conversioni, eventi di coinvolgimento) vengono tracciate tramite [!DNL Web SDK] e riportate nel rapporto dell&#39;esperimento di AJO.

Questa opzione non richiede segmenti di pubblico predefiniti per il targeting: tutti i visitatori (o un sottoinsieme di destinazione) partecipano all’esperimento. L’obiettivo è scoprire quale contenuto offre prestazioni migliori, non eseguire il targeting di segmenti noti con contenuti predeterminati.

**Considerazioni chiave:**

- Richiede un volume di traffico sufficiente per raggiungere la rilevanza statistica in un arco di tempo ragionevole
- Gli esperimenti utilizzano un modello statistico bayesiano con intervalli di affidabilità validi in qualsiasi momento
- Per misurare l’incremento incrementale, si consiglia un gruppo di attesa (che non riceve contenuti personalizzati)
- Può essere attivo un solo esperimento per campagna alla volta
- Le modifiche dell’esperimento richiedono l’arresto e il riavvio della campagna

**Vantaggi:**

- Misurazione statisticamente rigorosa dell’efficacia delle varianti di contenuto
- Rimuove le supposizioni dalle decisioni di personalizzazione: selezione di contenuti basati sui dati
- Supporta i gruppi di attesa per la misurazione incrementale effettiva dell&#39;incremento
- Generazione di rapporti sugli esperimenti incorporati con intervalli di affidabilità e dichiarazione dei vincitori
- I risultati possono informare la futura personalizzazione basata su regole (opzione A) identificando le varianti vincenti

**Limitazioni:**

- Richiede un volume di traffico significativo; per raggiungere la significatività le pagine a traffico ridotto possono richiedere settimane
- La suddivisione del traffico fa sì che alcuni visitatori visualizzino contenuti non ottimali durante il periodo di test
- Impossibile personalizzare per segmento durante l’esperimento (tutti i visitatori o un sottoinsieme partecipano allo stesso modo)
- Massimo 10 varianti di trattamento per esperimento
- Nessuna ottimizzazione continua: gli esperimenti sono discreti con un inizio e una fine

**Experience League:**

- [Introduzione all’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Creare un esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapporto sull’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### Opzione C: personalizzazione web basata su decisioni

**Ideale per:** Selezione dinamica dei contenuti: consigli di affinità tra categorie, offerte con intento di uscita, consigli comportamentali, in cui i criteri decisionali valutano i segnali di sessione e selezionano il contenuto ottimale da un catalogo di elementi idonei. Scegli questa opzione quando la logica di selezione del contenuto è troppo complessa per regole semplici, quando desideri un’ottimizzazione con classificazione AI o quando il set di elementi di contenuto idonei è ampio e dinamico.

**Funzionamento:**

La personalizzazione basata sulle decisioni utilizza AJO Decisioning per valutare i segnali comportamentali e selezionare la variante di contenuto migliore per ogni visitatore da un catalogo gestito di elementi di contenuto (offerte). Ogni elemento di contenuto dispone di regole di idoneità (chi è idoneo), rappresentazioni (come si presenta il contenuto in ogni posizionamento) e vincoli di limitazione facoltativi (con quale frequenza può essere visualizzato). Un criterio di decisione collega i posizionamenti (dove il contenuto viene visualizzato nella pagina) alle raccolte di elementi di contenuto e applica una strategia di classificazione per selezionare l’opzione migliore.

Quando un visitatore carica una pagina, [!DNL Web SDK] invia una richiesta [!DNL Edge Network] che include l&#39;ambito della decisione. Il motore delle decisioni valuta il profilo Edge del visitatore in base alle regole di idoneità per gli elementi di contenuto, applica la strategia di classificazione (basata su priorità, basata su formula o classificata in base all’intelligenza artificiale) e restituisce l’elemento di contenuto vincente. Ciò avviene al perimetro con latenza al secondo secondario.

La strategia di classificazione determina il modo in cui vengono ordinati gli elementi di contenuto idonei. La classificazione basata su priorità utilizza valori di priorità assegnati manualmente. La classificazione basata su formule utilizza un’espressione personalizzata (ad esempio, la ponderazione dell’attualità delle visualizzazioni di pagina). La classificazione con classificazione basata su IA utilizza un modello di apprendimento automatico che ottimizza nel tempo per la metrica di successo selezionata, ma richiede almeno 1.000 eventi di conversione per l’apprendimento.

**Considerazioni chiave:**

- Richiede la configurazione dei componenti Decisioning: posizionamenti, regole di idoneità, elementi di contenuto, elementi di fallback, raccolte e criteri di decisione
- Le strategie classificate in base all’intelligenza artificiale richiedono un volume di conversione sufficiente (oltre 1.000 eventi) per addestrare il modello
- Le decisioni di Edge sono limitate agli attributi di profilo disponibili nell’archivio profili edge
- Gli elementi di contenuto devono essere gestiti e mantenuti nella libreria Decisioning
- Il contenuto di fallback deve essere definito per i casi in cui nessun elemento personalizzato è idoneo

**Vantaggi:**

- Scalabilità a cataloghi di contenuti di grandi dimensioni senza richiedere la mappatura individuale tra pubblico e contenuto
- Le strategie classificate in base all’intelligenza artificiale ottimizzano continuamente la selezione dei contenuti in base alle prestazioni osservate
- Le regole di idoneità e i vincoli di limitazione forniscono un controllo dettagliato sulla distribuzione dei contenuti
- Supporta una logica di business complessa difficile da esprimere come segmenti di pubblico
- Riutilizzabile su più canali: lo stesso criterio decisionale può alimentare la personalizzazione web, e-mail e mobile

**Limitazioni:**

- Maggiore complessità di implementazione: richiede la configurazione dello stack di componenti Decisioning completo
- La classificazione basata su IA richiede un volume di conversione significativo e tempo di formazione efficace
- Le limitazioni relative ai dati di profilo di Edge limitano la complessità delle regole di idoneità per i visitatori anonimi
- Costi comuni di gestione degli elementi di contenuto: ogni elemento necessita di rappresentazioni, regole di idoneità e manutenzione
- La logica decisionale di debug è più complessa degli approcci basati su regole

**Experience League:**

- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Creare i posizionamenti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)

### Confronto delle opzioni

La tabella seguente confronta le tre opzioni di implementazione tra i diversi criteri chiave.

| Criteri | Opzione A: basata su regole | Opzione B: Sperimentazione | Opzione C: Decisioning |
| --- | --- | --- | --- |
| Ideale per | Mappature segmento-contenuto note | Individuazione dei contenuti più efficaci | Selezione dinamica dei contenuti da cataloghi di grandi dimensioni |
| Complessi | Bassa | Medio | Alta |
| Latenza | Secondi secondari (spigolo) | Secondi secondari (spigolo) | Secondi secondari (spigolo) |
| Precisione Personalization | A livello di segmento (regole del pubblico) | A livello di visitatore (assegnazione casuale) | Livello del visitatore (idoneità + classificazione) |
| Ottimizzazione dei contenuti | Manuale (nessuna misurazione) | Test statistico (A/B) | Continuo (classificazione IA) o manuale (priorità) |
| Richiede segmenti di pubblico | Sì (con valutazione spigolo) | No (suddivisione del traffico) | Facoltativo (per le regole di idoneità) |
| Capacità di misurazione | Nessuno incorporato (richiede CJA) | Rapporti incorporati sugli esperimenti | Rapporti decisioning incorporati |
| Dimensione catalogo contenuti | Piccolo (1:1 segmento-contenuto) | Piccola (2-10 varianti) | Grande (numero illimitato di elementi idonei) |
| Richiede | Tipi di pubblico di Edge, varianti di contenuto | Campagna con esperimento abilitato | Componenti decisionali (posizionamenti, offerte, criteri) |

### Scegli l’opzione giusta

Utilizza la seguente logica di decisione per selezionare l’opzione di implementazione appropriata:

1. **Sapete già quale contenuto mostrare a ogni segmento di visitatori?**
   - Sì: inizia con **Opzione A (basata su regole)**. Hai definito strategie di contenuto per segmento e hai bisogno di una distribuzione deterministica.
   - No: passare alla domanda 2.

2. **È necessario testare un numero limitato di varianti di contenuto per trovare l&#39;utente con le prestazioni migliori?**
   - Sì: Scegliere **Opzione B (Sperimentazione)**. Desideri la convalida statistica prima di adottare una strategia per i contenuti.
   - No: passare alla domanda 3.

3. **Disponi di un ampio catalogo di elementi di contenuto con requisiti di idoneità e classificazione complessi?**
   - Sì: Scegliere **Opzione C (Decisioning)**. È necessaria una selezione dinamica dei contenuti che vada oltre le semplici regole.
   - No: inizia con **l&#39;opzione A (basata su regole)** per semplicità, quindi passa all&#39;opzione B o C con l&#39;aumento dei requisiti.

**Opzioni di combinazione:** Queste opzioni non si escludono a vicenda. Una progressione comune consiste nell’iniziare con l’opzione B (sperimentazione) per individuare i contenuti vincenti, quindi distribuire i vincitori utilizzando l’opzione A (basata su regole) per la distribuzione continua. L’opzione C (Decisioning) può essere sovrapposta per i casi d’uso che richiedono una selezione dinamica basata sul catalogo, mentre l’opzione A gestisce regole deterministiche più semplici.

## Fasi di implementazione

Le fasi seguenti descrivono il flusso di lavoro di implementazione end-to-end.

### Fase 1: Configurare le superfici web

**Funzione applicazione:** AJO: Configurazione canale

Definisci le superfici dei canali web che specificano dove verrà distribuito il contenuto personalizzato sul sito web. Una superficie web identifica un URL specifico della pagina o un pattern di URL e la posizione sulla pagina (selettore CSS o superficie di esperienza basata su codice) in cui AJO può inserire o sostituire il contenuto.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: tipo di superficie** — Come distribuire il contenuto personalizzato alla pagina?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Canale web (editor visivo) | La personalizzazione comporta la modifica degli elementi visibili della pagina (banner, titoli, immagini, CTA) tramite un editor visivo con trascinamento della selezione | Richiede l’estensione del browser Web Designer. Consigliato per modifiche ai contenuti basate sul marketing. Limitato alle modifiche visive degli elementi di pagina esistenti. |
| Esperienza basata su codice | La personalizzazione richiede l’inserimento di dati strutturati (JSON) utilizzati e renderizzati dal codice dell’applicazione del sito web | Richiede l’implementazione da parte di sviluppatori per utilizzare il payload JSON. Massima flessibilità per una personalizzazione complessa. Consigliato per applicazioni a pagina singola, componenti dinamici e rendering programmatico. |
| Entrambi (ibridi) | Diverse personalizzazioni sullo stesso sito richiedono meccanismi di distribuzione diversi | Utilizza il canale web per semplici modifiche visive ed esperienze basate su codice per il rendering programmatico. Aumenta la complessità dell&#39;implementazione, ma ottimizza la copertura. |

>[!NOTE]
>**Decisione: ambito superficie** — Quale ambito URL deve coprire la superficie web?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Corrispondenza URL esatta | Personalization esegue il targeting per una pagina specifica (ad esempio, home page, pagina di destinazione) | Impostazione destinazione più precisa. Richiede superfici separate per ogni pagina. |
| Schema URL con caratteri jolly | Personalization si applica a una categoria di pagine (ad esempio, tutte le pagine di prodotto, tutti gli articoli di blog) | Riduce il sovraccarico di gestione della superficie. Le varianti di contenuto devono essere progettate per funzionare in tutte le pagine corrispondenti. |
| Superficie applicazione a pagina singola | Il sito web è un’applicazione a pagina singola in cui le modifiche URL non attivano i ricaricamenti dell’intera pagina | Richiede la configurazione di [!DNL Web SDK] compatibile con applicazioni a pagina singola con `sendEvent` chiamate per modifiche alla visualizzazione. Le definizioni delle superfici utilizzano il nome della vista SPA (applicazione a pagina singola) anziché l’URL. |

**Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Amministrazione > Canali > Configurazione Web

**Dettagli configurazione chiave:**

- Definire l’URL della pagina o il pattern URL per la superficie
- Specifica il selettore CSS o l’URI della superficie per il posizionamento del contenuto
- Per le esperienze basate su codice, definisci il nome della superficie a cui farà riferimento il codice dell’applicazione
- Associa la superficie alla sandbox di AJO in cui verranno create le campagne

**Documentazione di Experience League:**

- [Introduzione al canale web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Creare esperienze web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Canale di esperienza basato su codice](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Configurazione dell’esperienza basata su codice](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

### Fase 2: definire i tipi di pubblico comportamentali

**Funzione applicazione:** RT-CDP: Audience Evaluation

Definisci segmenti di pubblico valutati edge in base ai segnali comportamentali durante la sessione su cui si basa il targeting di personalizzazione. Questi tipi di pubblico determinano i visitatori idonei per ogni esperienza personalizzata. Per questo modello è obbligatoria la valutazione Edge, in quanto le decisioni di personalizzazione devono essere prese in intervalli di tempo di secondi secondari mentre il visitatore naviga nel sito.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: selezione del segnale comportamentale** — Quali segnali in-session devono guidare il targeting di personalizzazione?

| Segnale | Quando utilizzare | Idoneità ad Edge |
| --- | --- | --- |
| Parametri origine riferimento/UTM | Personalizzazione della pagina di destinazione specifica per la campagna | Idoneo: semplice controllo dell’attributo nell’evento corrente |
| Posizione geografica (paese, regione, città) | Promozioni regionali, contenuti specifici per la lingua, store locator | Idoneo: controllo degli attributi del profilo |
| Tipo di dispositivo (desktop, mobile, tablet) | Layout di contenuto e CTA ottimizzati per il dispositivo | Idoneo: controllo degli attributi del profilo |
| Pagine visualizzate nella sessione | Affinità tra categorie, contenuti consigliati | Idoneo con vincoli: solo controlli del conteggio degli eventi semplici |
| Visitatore nuovo o di ritorno | Messaggi di benvenuto, coinvolgimento progressivo | Idoneo: la persistenza ECID indica che il visitatore è di ritorno |
| Tempo sul sito/profondità di scorrimento | Offerte basate su coinvolgimento di uscita | Potrebbe essere necessaria un’implementazione personalizzata, non nativamente idonea per Edge |

>[!NOTE]
>**Decisione: metodo di valutazione del pubblico** — Tutti i tipi di pubblico per questo modello devono utilizzare la valutazione Edge. Conferma l’idoneità prima di definire i segmenti.

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Valutazione Edge | Obbligatorio per questo pattern | Le espressioni della regola del segmento devono essere idonee per Edge: confronti di attributi semplici, controlli di appartenenza ai segmenti, nessuna query di serie temporali o funzioni di aggregazione. Latenza di valutazione al secondo secondario. |
| Valutazione in streaming (fallback) | Quando l’espressione della regola di segmento non è idonea per Edge ma è accettabile quasi in tempo reale | Latenza da secondi a minuti. Supporta espressioni di regole di segmento più complesse. Può introdurre un ritardo notevole nella consegna della personalizzazione. |

**Navigazione interfaccia utente:** Cliente > Tipi di pubblico > Crea pubblico > Genera regola

**Dettagli configurazione chiave:**

- Utilizza Segment Builder (Generatore di segmenti) per definire le regole del pubblico utilizzando gli attributi comportamentali
- Verificare l’idoneità Edge confermando che l’espressione della regola del segmento utilizzi solo funzioni supportate (confronti di attributi semplici, appartenenza a segmenti)
- Imposta il criterio di unione sul criterio di unione attivo-bordo configurato in F4
- Anteprima della popolazione del pubblico per convalidare il segmento e restituire i risultati previsti
- Per i tipi di pubblico basati sulle visualizzazioni di pagina nella sessione, utilizza gli attributi a livello di evento della sessione corrente anziché le query della serie temporale

**Opzioni divergenti:**

**Per L&#39;Opzione A (Basata Su Regole):**
Crea segmenti di pubblico distinti per ogni variante di contenuto. Ogni segmento rappresenta una condizione comportamentale specifica (ad esempio, &quot;Referral = Google AND Geo = US&quot; corrisponde alla variante di contenuto A). Il numero di tipi di pubblico è uguale al numero di regole di personalizzazione.

**Per L&#39;Opzione B (Sperimentazione):**
La definizione del pubblico è facoltativa. Se l’esperimento ha come target tutti i visitatori, non è necessario alcun pubblico; la suddivisione del traffico gestisce l’assegnazione delle varianti. Se l’esperimento ha come target un sottoinsieme specifico (ad esempio, solo i visitatori mobili), definisci un singolo pubblico di targeting per l’idoneità all’esperimento.

**Per L&#39;Opzione C (Decisioning):**
Definisci i tipi di pubblico da utilizzare come regole di idoneità per gli elementi di contenuto. Questi tipi di pubblico determinano quali visitatori sono idonei per ciascun elemento di contenuto nel criterio decisionale. Il motore delle decisioni gestisce la selezione del contenuto tra gli elementi idonei.

**Documentazione di Experience League:**

- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

### Fase 3: Creare contenuti e varianti

**Funzione dell&#39;applicazione:** AJO: Message Authoring, AJO: Content Experimentation (opzione B), AJO: Decisioning (opzione C)

Crea le varianti di contenuto personalizzato che verranno consegnate ai visitatori in base all’iscrizione al pubblico (opzione A), all’assegnazione di esperimenti (opzione B) o alla logica decisionale (opzione C). Questa fase riguarda la creazione di contenuti tramite il web designer AJO o l’editor di esperienze basato su codice, nonché la configurazione dell’esperimento o del processo decisionale che determina come viene selezionato il contenuto.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: approccio per l&#39;authoring dei contenuti** — Come devono essere create le varianti di contenuti web?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Editor visivo web | Il team marketing può modificare gli elementi della pagina visivamente senza codice | Richiede l&#39;estensione del browser. Consigliato per modifiche a testo, immagini e CTA. Limitato alla modifica di elementi di pagina esistenti. |
| Editor esperienze basato su codice | Il contenuto richiede dati strutturati (JSON) per il rendering del codice dell’applicazione | Massima flessibilità. Richiede l’implementazione da parte degli sviluppatori per utilizzare il payload. Consigliato per componenti dinamici e applicazioni a pagina singola. |
| Editor di codice HTML/CSS | Le modifiche al contenuto richiedono HTML o CSS personalizzati | Controllo diretto del codice. Richiede competenze HTML/CSS. Consigliato per modifiche di layout complesse. |

>[!NOTE]
>**Decisione: token Personalization** — Il contenuto deve includere la personalizzazione dinamica tramite attributi di profilo o contestuali?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Varianti di contenuto statico | Ogni variante è un contenuto fisso senza token dinamici | Approccio più semplice. I contenuti sono prevedibili e facili da verificare. Nessun rischio di valori di attributo mancanti. |
| Contenuto dinamico con espressioni di personalizzazione | Il contenuto include token in stile Handlebars che si risolvono in attributi di profilo o evento (ad esempio, nome della città, origine riferimento) | Contenuti più rilevanti. Richiede valori di fallback per gli attributi che possono essere nulli nei profili anonimi. Utilizza la sintassi `{{profile.homeAddress.city}}` con gli helper. |
| Blocchi di contenuto condizionali | Blocchi di contenuto diversi eseguono il rendering in base alle condizioni di attributo all’interno di una singola variante | Riduce il numero di varianti distinte necessarie. Aumenta la complessità dei contenuti. Ideale per varianti minori all’interno di un layout condiviso. |

**Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Campagne > Seleziona campagna > Modifica contenuto

**Dettagli configurazione chiave:**

- Creare contenuti utilizzando il designer web (modifiche visive) o l’editor di esperienze basato su codice (payload JSON)
- Utilizza l’editor delle espressioni di personalizzazione per inserire token dinamici dagli attributi del profilo edge
- Configurare il contenuto di fallback per i token di personalizzazione che potrebbero essere vuoti nei profili anonimi
- Anteprima di contenuti con profili di test per verificare il rendering tra scenari

**Opzioni divergenti:**

**Per L&#39;Opzione A (Basata Su Regole):**
Crea una variante di contenuto distinta per ogni segmento di pubblico definito nella fase 2. Associa ogni variante al relativo pubblico di destinazione utilizzando le regole di contenuto condizionale nella configurazione della campagna. Assicurati che esista una variante di contenuto predefinita per i visitatori che non corrispondono ad alcuna regola di pubblico.

**Per L&#39;Opzione B (Sperimentazione):**
Creare varianti di trattamento (A, B, C, ecc.) per l’esperimento. Abilita la sperimentazione dei contenuti nella campagna, definisci le varianti di trattamento con il loro contenuto, imposta le percentuali di allocazione del traffico e configura la metrica di successo.

- Definire 2-10 varianti di trattamento con contenuto distinto
- Imposta l’allocazione del traffico (ad esempio, 50/50 per A/B o suddivisione ponderata per test a rischio ridotto)
- Facoltativamente, includi un gruppo di sospensione (ad esempio, il 10% riceve il contenuto predefinito) per misurare l’incremento incrementale
- Seleziona la metrica di successo: aperture univoche, clic univoci, conversioni o metrica personalizzata
- Imposta la soglia di affidabilità: 95% per i test standard, 99% per le decisioni ad alta posta, 90% per l’apprendimento direzionale
- **Navigazione interfaccia utente:** Campaign > Esperimento contenuti > Aggiungi trattamento > Allocazione traffico > Metrica di successo

**Per L&#39;Opzione C (Decisioning):**
Imposta lo stack di componenti Decisioning e integralo nella campagna.

1. **Crea posizionamenti** — Definisci dove verranno visualizzati gli elementi del contenuto della pagina (Web HTML, Web JSON, immagine Web)
   - **Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Componenti > Gestione decisioni > Posizionamenti
2. **Definire le regole di idoneità** — Creare regole basate sugli attributi del profilo Edge che determinano quali visitatori sono idonei per ciascun elemento di contenuto
   - **Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Componenti > Gestione decisioni > Regole
3. **Crea elementi di contenuto (offerte)**: crea elementi di contenuto personalizzati con rappresentazioni per ogni posizionamento, regole di idoneità, priorità e limite facoltativo
   - **Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Componenti > Gestione decisioni > Offerte > Crea offerta
4. **Crea contenuto di fallback** — Definisci un elemento di fallback restituito quando nessun elemento personalizzato è idoneo
   - **Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Componenti > Gestione decisioni > Offerte > Crea offerta di fallback
5. **Organizza in raccolte**: raggruppa gli elementi di contenuto utilizzando i qualificatori di raccolta (tag) e crea raccolte
   - **Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Componenti > Gestione decisioni > Qualificatori raccolta/Raccolte
6. **Crea criterio di decisione** — Collega i posizionamenti alle raccolte e seleziona la strategia di classificazione (basata su priorità, basata su formula o con classificazione basata su IA)
   - **Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Componenti > Gestione decisioni > Decisioni > Crea decisione

**Documentazione di Experience League:**

- [Creare esperienze web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Canale di esperienza basato su codice](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Creare un esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Fase 4: Configurare la campagna e la consegna

**Funzione dell&#39;applicazione:** AJO: Esecuzione della campagna

Crea e attiva la campagna web di AJO che associa la superficie web (fase 1), la configurazione dell’esperimento o del targeting di pubblico (fasi 2-3) e le varianti di contenuto (fase 3) in un’unità consegnabile. La campagna controlla quando e come il contenuto personalizzato viene distribuito ai visitatori.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: tipo di campagna** — Come attivare la campagna?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Campagna pianificata (sempre attiva) | Personalization deve essere eseguito continuamente per tutti i visitatori idonei | Imposta la data di inizio senza data di fine per la personalizzazione continua. La valutazione del pubblico avviene al limite in tempo reale. Più comune per la personalizzazione web. |
| Campagna pianificata (con limiti di tempo) | Personalization è legato a uno specifico periodo di promozione o evento stagionale | Impostare date di inizio e fine esplicite. Campaign si disattiva automaticamente alla data di fine. Ideale per campagne promozionali. |
| Campagna attivata da API | La consegna Personalization deve essere attivata da un evento di sistema esterno | Richiede l’integrazione API. Meno comune per la personalizzazione web anonima. Da utilizzare quando un sistema back-end deve controllare quando la personalizzazione è attiva. |

**Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Campagne > Crea campagna

**Dettagli configurazione chiave:**

- Seleziona il canale web e la superficie web configurati nella fase 1
- Associa il pubblico target (per l’opzione A) o configura le impostazioni dell’esperimento (per l’opzione B) o incorpora la decisione (per l’opzione C)
- Imposta la pianificazione della campagna (data di inizio, data di fine o sempre attiva)
- Configurare il limite di frequenza a livello di campagna, se applicabile
- Controlla tutte le configurazioni e attiva la campagna

**Opzioni divergenti:**

**Per L&#39;Opzione A (Basata Su Regole):**
Crea una campagna per regola di personalizzazione, ogni volta indirizzata a un pubblico Edge diverso con la corrispondente variante di contenuto. In alternativa, utilizza una singola campagna con regole di contenuto condizionale che mappano l’iscrizione al pubblico alle varianti di contenuto all’interno di una campagna.

**Per L&#39;Opzione B (Sperimentazione):**
Crea una singola campagna con la sperimentazione dei contenuti abilitata. La configurazione dell’esperimento (varianti, allocazione del traffico, metrica di successo) è stata definita nella Fase 3. Attiva la campagna per avviare l’esperimento.

**Per L&#39;Opzione C (Decisioning):**
Crea una campagna che incorpora il criterio di decisione configurato nella fase 3. L’azione di contenuto della campagna fa riferimento all’ambito della decisione, che attiva il motore Decisioning al limite. Attiva la campagna per iniziare la distribuzione dei contenuti basata su decisioni.

**Documentazione di Experience League:**

- [Creare una campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Introduzione alle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Fase 5: rapporto e analisi delle prestazioni

**Funzione applicazione:** AJO: Reporting e analisi delle prestazioni

Monitora le prestazioni di personalizzazione utilizzando i rapporti incorporati di AJO e, facoltativamente, estende l’analisi con CJA per ottenere informazioni più approfondite su più canali. Questa fase tratta argomenti quali l’accesso ai rapporti live e storici sulle campagne, la revisione dei risultati degli esperimenti e la creazione di aree di lavoro di analisi personalizzate.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: profondità del reporting** — Quanto deve essere profonda l&#39;analisi delle prestazioni?

| Opzione | Quando scegliere | Considerazioni |
| --- | --- | --- |
| Solo rapporti nativi di AJO | Sono sufficienti le metriche di base di consegna e coinvolgimento | Fornisce con facilità impression, clic, CTR e metriche di conversione. Disponibile immediatamente nell’interfaccia utente di Campaign. Personalizzazione limitata. |
| Rapporti di AJO + analisi di CJA | È necessaria un’analisi approfondita del funnel, un confronto tra coorti o una misurazione dell’impatto cross-channel | Richiede connessione CJA e visualizzazione dati collegata ai set di dati di AJO. Abilita l’analisi freeform, le metriche calcolate personalizzate, la modellazione di attribuzione e la pubblicazione di tipi di pubblico. |

**Navigazione interfaccia utente:** [!DNL Journey Optimizer] > Campagne > Seleziona campagna > Visualizza report

**Dettagli configurazione chiave:**

- Accedi al rapporto live durante le campagne attive per monitorare la consegna in tempo reale (si aggiorna ogni 60 secondi, mostra le ultime 24 ore).
- Accedi al rapporto cronologico (tutto il tempo) dopo il completamento della campagna per un’analisi completa (il completamento del popolamento potrebbe richiedere fino a 2 ore)
- Per l’opzione B (Sperimentazione): esaminare il rapporto dell’esperimento per il confronto delle prestazioni del trattamento, gli intervalli di affidabilità e la dichiarazione del vincitore
- Per l’analisi CJA: assicurati che una connessione CJA includa i set di dati dell’evento esperienza AJO e che una visualizzazione dati sia configurata con le metriche di personalizzazione web

**Opzioni divergenti:**

**Per L&#39;Opzione A (Basata Su Regole):**
Rivedi i rapporti sulle campagne per ogni segmento di pubblico per confrontare le metriche di consegna e coinvolgimento tra le varianti di contenuto personalizzato. Utilizza CJA per creare un’area di lavoro di confronto che misuri l’impatto della conversione di contenuti personalizzati rispetto a quelli predefiniti.

**Per L&#39;Opzione B (Sperimentazione):**
Esamina il rapporto dell’esperimento per verificare l’affidabilità statistica, l’incremento del trattamento e l’identificazione del vincitore. Attendi che venga raggiunta la soglia di affidabilità prima di dichiarare un vincitore. Applicare i contenuti vincenti come variante permanente (transizione all’opzione A per una distribuzione continua).

- **Navigazione interfaccia utente:** Campagna > Esperimento contenuti > Visualizza rapporto
- **Experience League:** [Rapporto sull&#39;esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

**Per L&#39;Opzione C (Decisioning):**
Rivedi le metriche delle prestazioni di decisioning, inclusi i tassi di impression delle offerte, la frequenza di selezione e l’attribuzione di conversione per elemento di contenuto. Analizza le prestazioni delle strategie di classificazione e se il contenuto di fallback viene trasmesso troppo spesso (indicando che le regole di idoneità sono troppo restrittive).

**Documentazione di Experience League:**

- [Rapporto live delle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Calcoli statistici nell’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

## Considerazioni sull’implementazione

Questa sezione descrive guardrail, insidie comuni, best practice e decisioni di compromesso per questo modello di casi d’uso.

### Guardrail e limiti

Rivedi i seguenti guardrail prima e durante l’implementazione.

- I segmenti Edge sono limitati a semplici controlli degli attributi e appartenenza ai segmenti, ovvero nessuna query di serie temporali o aggregazione complessa. [Idoneità alla segmentazione di Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- È possibile attivare un solo criterio di unione su Edge per sandbox: [Guardrail di profilo](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Massimo 4.000 definizioni di segmenti per sandbox: [Guardrail di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Massimo 500 campagne live attive per sandbox: [guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Massimo 10 varianti di trattamento per esperimento di contenuti — [Limiti per esperimento di contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Massimo 10.000 offerte personalizzate approvate per sandbox (opzione C) — [Guardrail di gestione delle decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Massimo 30 posizionamenti per decisione (opzione C): [guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- I modelli di classificazione IA richiedono almeno 1.000 eventi di conversione per l’apprendimento (opzione C)
- [!DNL Edge Network] tempo di risposta SLA: &lt; 200 ms per i segmenti valutati edge
- Scadenza profilo pseudonimo: configurabile da 14 a 365 giorni per profili solo ECID
- I rapporti live vengono aggiornati ogni 60 secondi e mostrano le ultime 24 ore di dati
- I rapporti cronologici possono richiedere fino a 2 ore per essere compilati completamente dopo il completamento della campagna

### Insidie comuni

Evita i seguenti errori di implementazione comuni.

- **[!DNL Web SDK]non invia segnali comportamentali ad AEP:** Verificare che lo stream di dati abbia il servizio [!DNL Adobe Experience Platform] abilitato e che il set di dati dell&#39;evento sia mappato correttamente. In caso contrario, i profili edge non vengono popolati e la valutazione del pubblico non riesce in modo silenzioso: il visitatore riceve il contenuto predefinito senza alcuna indicazione di errore.
- **Il pubblico di Edge che restituisce zero qualifiche:** La segmentazione di Edge ha dei requisiti di idoneità rigidi. Le query di serie temporali, le funzioni di aggregazione e le query con più entità non sono idonee per Edge. Riscrivi l’espressione della regola di segmento utilizzando confronti di attributi semplici o controlli di appartenenza ai segmenti.
- **Criterio di unione non attivo sul server Edge:** Se il criterio di unione utilizzato dal segmento di pubblico non contiene `isActiveOnEdge: true`, le ricerche dei profili Edge non riusciranno e la personalizzazione non verrà recapitata. Su Edge può essere attivo un solo criterio di unione per sandbox, verifica che non esista alcun conflitto.
- **Sfarfallio di Personalization al caricamento della pagina:** La chiamata [!DNL Web SDK] `sendEvent` che recupera le proposte di personalizzazione deve essere eseguita prima che la pagina esegua il rendering dell&#39;area del contenuto di destinazione. Implementa snippet per nascondere il contenuto o rendering asincrono per evitare che il contenuto predefinito lampeggi prima del caricamento del contenuto personalizzato.
- **Modifiche alla route SPA del contenuto non sottoposte a rendering:** Le applicazioni a pagina singola richiedono `sendEvent` chiamate esplicite con informazioni di visualizzazione aggiornate quando la route cambia. In caso contrario, [!DNL Edge Network] non rivaluta la personalizzazione per la nuova visualizzazione.
- **Esperimento che non raggiunge la significatività statistica:** Volume di traffico insufficiente o troppe varianti di trattamento diluiscono la dimensione del campione per variante. Riduci il numero di varianti o aumenta la durata dell’esperimento. Non interrompere gli esperimenti prematuramente — i risultati possono essere fuorvianti.
- **Decisioning restituisce solo contenuto di fallback:** Verifica che gli elementi di contenuto personalizzato siano approvati, entro il loro intervallo di date di validità e che le regole di idoneità corrispondano agli attributi di profilo edge del visitatore anonimo. Verificare inoltre che i limiti di limitazione non siano stati raggiunti.

### Best practice

Segui queste raccomandazioni per un’implementazione corretta.

- **Inizia semplice, quindi ripeti:** Inizia con l&#39;opzione A (basata su regole) per la personalizzazione iniziale, quindi utilizza l&#39;opzione B (sperimentazione) per convalidare le ipotesi e l&#39;opzione C (decisioning) per i casi d&#39;uso avanzati. Ogni opzione si basa sull’infrastruttura fondamentale.
- **Utilizza il pre-hiding per prevenire lo sfarfallio:** implementa il frammento pre-hiding di AEP nelle pagine in cui verrà distribuita la personalizzazione. In questo modo l’area del contenuto di destinazione viene nascosta fino a quando il contenuto personalizzato non è pronto per il rendering, impedendo la visualizzazione momentanea di altri contenuti.
- **Progetta deliberatamente il contenuto di fallback:** Il contenuto predefinito (non personalizzato) deve essere un&#39;esperienza di alta qualità. I visitatori che non si qualificano per la personalizzazione, o quando la risposta [!DNL Edge Network] viene ritardata, non devono ricevere un&#39;esperienza degradata.
- **Convalidare l&#39;idoneità Edge prima di creare i tipi di pubblico:** Prima di investire nello sviluppo di regole del pubblico, verificare che l&#39;espressione della regola del segmento sia idonea per Edge esaminando i criteri di idoneità in Experience League. Le espressioni non idonee torneranno automaticamente alla valutazione in batch o in streaming con latenza non accettabile per questo modello.
- **Monitoraggio delle prestazioni di recapito Edge:** Configurazione degli avvisi di monitoraggio per [!DNL Edge Network] tempi di risposta e errori di recapito della personalizzazione. I problemi di consegna in Edge sono invisibili al visitatore (visualizzano il contenuto predefinito) e possono non essere rilevati senza un monitoraggio proattivo.
- **Configura scadenza profilo pseudonimo:** Imposta i periodi di scadenza appropriati per i profili edge anonimi in modo da bilanciare la personalizzazione tra sessioni diverse (riconoscimento dei visitatori di ritorno) con la conformità in materia di privacy e la gestione dell&#39;archiviazione.
- **Test con profili rappresentativi:** Quando visualizzi l&#39;anteprima di contenuti personalizzati, utilizza profili di test che rappresentano gli scenari effettivi di visitatori anonimi (nessun dato CRM, cronologia comportamentale limitata, varie posizioni geografiche e dispositivi).

### Decisioni di compromesso

Quando pianifichi l’implementazione, considera i seguenti compromessi.

>[!NOTE]
>**Compensazione: ampiezza e complessità dell&#39;implementazione di Personalization**
>
>Una personalizzazione più granulare (molti tipi di pubblico, molte varianti di contenuto) produce esperienze più rilevanti, ma aumenta la complessità della configurazione e il sovraccarico di produzione dei contenuti.
>
>- **Ampia personalizzazione favorisce:** semplicità, tempi di commercializzazione più rapidi, costi di produzione inferiori dei contenuti. Un numero limitato di tipi di pubblico e varianti copre la maggior parte dei visitatori con una personalizzazione significativa.
>- **La personalizzazione granulare favorisce:** Massima rilevanza, incremento del coinvolgimento maggiore, tassi di conversione migliori. Molti tipi di pubblico e varianti trattano segnali comportamentali specifici con contenuti personalizzati.
>- **Consiglio:** inizia con 3-5 regole di personalizzazione ad alto impatto indirizzate ai segmenti di visitatori più comuni (ad esempio origine di riferimento, tipo di dispositivo, area geografica). Misura l’impatto, quindi espandi fino a regole più granulari in base alle prestazioni osservate e al valore aziendale.

>[!NOTE]
>**Compensazione: determinismo basato su regole e ottimizzazione basata sull&#39;intelligenza artificiale**
>
>Gli approcci basati sulle regole (opzione A) offrono all’azienda il pieno controllo sul contenuto visualizzato da ogni visitatore. Gli approcci basati sull’intelligenza artificiale (opzione C) ottimizzano la selezione dei contenuti nel tempo, ma riducono la visibilità sul motivo per cui è stato selezionato un contenuto specifico.
>
>- **Preferenze basate su regole:** Predittività, verificabilità, controllo aziendale. I team di marketing sanno esattamente quale contenuto riceve ogni segmento e possono spiegare la logica alle parti interessate.
>- **Preferenze basate sull&#39;intelligenza artificiale:** Ottimizzazione delle prestazioni, scalabilità, miglioramento continuo. Il modello di intelligenza artificiale rileva le affinità contenuto-visitatore che la scrittura di regole umane potrebbe perdere.
>- **Consiglio:** utilizza le decisioni basate su regole per i contenuti ad alto rischio in cui la coerenza del brand e la trasparenza delle parti interessate sono di importanza fondamentale. Utilizza la classificazione basata sull’intelligenza artificiale per i cataloghi di contenuti di grandi dimensioni in cui la gestione manuale delle regole diventa ingombrante e l’ottimizzazione continua offre un incremento misurabile.

>[!NOTE]
>**Compensazione: persistenza del profilo anonimo rispetto alla conformità alla privacy**
>
>Una scadenza più lunga del profilo pseudonimo consente una migliore personalizzazione tra sessioni (riconoscimento dei visitatori di ritorno, creazione di un contesto comportamentale nel tempo). Una scadenza più breve migliora la conformità alla privacy e riduce i costi di storage.
>
>- **Scadenza più lunga favorisce:** profili anonimi più ricchi, un migliore riconoscimento dei visitatori di ritorno, più dati per le decisioni di personalizzazione. Imposta scadenza su 90-365 giorni.
>- **Scadenza più breve a favore:** Conformità in materia di privacy (RGPD, CCPA), riduzione dei costi di archiviazione, riduzione del rischio di dati di profilo non aggiornati. Imposta la scadenza su 14-30 giorni.
>- **Consiglio:** Allinea la scadenza ai criteri di consenso dei cookie e ai requisiti di privacy della tua organizzazione. Per la maggior parte delle implementazioni, 30-90 giorni forniscono un ragionevole equilibrio tra il valore della personalizzazione e la conformità alla privacy.

## Documentazione correlata

Le seguenti risorse di Experience League forniscono ulteriori dettagli sulle funzionalità utilizzate in questo modello di caso d’uso.

**Canale web ed esperienze basate su codice**

- [Introduzione al canale web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Creare esperienze web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Canale di esperienza basato su codice](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Configurazione dell’esperienza basata su codice](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

**Tipi di pubblico e segmentazione**

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

**Personalization e contenuto**

- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilizzare i frammenti di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

**Sperimentazione dei contenuti**

- [Introduzione all’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Creare un esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapporto sull’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Calcoli statistici](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

**Gestione delle decisioni**

- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Creare i posizionamenti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Creare regole di decisione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Creazione di offerte personalizzate](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Creare offerte di fallback](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Creare le raccolte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Crea decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Strategie di classificazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

**Campagne**

- [Introduzione alle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Creare una campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

**[!DNL Web SDK]e raccolta dati**

- [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Installare Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Panoramica sui tag](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)

**Identità e profilo**

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Panoramica del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

**Modellazione dati**

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

**Reporting e analisi**

- [Rapporto live delle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

**Governance dei dati e privacy**

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Gruppo di campi Consenso e preferenze](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

**Guardrail**

- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Guardrail del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
