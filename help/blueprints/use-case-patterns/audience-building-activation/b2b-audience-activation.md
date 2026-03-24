---
title: Audience Activation B2B
description: Scopri come attivare tipi di pubblico B2B basati sull’account tra canali web, e-mail e pubblicitari.
solution: Real-Time Customer Data Platform
exl-id: 2b979159-37aa-41d4-a6b4-1105538f6546
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7611'
ht-degree: 0%

---

# Attivazione del pubblico B2B

Questa guida fornisce un riferimento completo all&#39;implementazione per l&#39;attivazione di tipi di pubblico B2B basati sull&#39;account utilizzando [!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition. È progettato per architetti di soluzioni, tecnici di marketing e ingegneri dell’implementazione che devono creare, valutare e attivare tipi di pubblico a livello di account tra canali web, e-mail, pubblicitari e di gestione delle relazioni con i clienti.

Copre l&#39;intero ciclo di vita dall&#39;unificazione del profilo dell&#39;account attraverso la valutazione del pubblico e l&#39;attivazione a destinazioni specifiche di B2B come [!DNL Marketo Engage], [!DNL LinkedIn] e i sistemi CRM. Tutti gli approcci di implementazione praticabili vengono presentati con compromessi e indicazioni decisionali per aiutarti a selezionare il percorso giusto per la tua organizzazione.

## Panoramica del caso d’uso

I team di marketing B2B devono eseguire il targeting e attivare i tipi di pubblico a livello di account anziché a livello di singola persona. A differenza dell’attivazione del pubblico B2C, in cui l’unità di targeting è un singolo profilo di consumatore, l’attivazione del pubblico B2B richiede la comprensione della relazione tra le persone e gli account a cui appartengono, la valutazione dell’iscrizione al pubblico in base agli attributi a livello di account combinati con i segnali di coinvolgimento a livello di persona e la distribuzione di tali tipi di pubblico a destinazioni che supportano il targeting basato sull’account.

[!DNL RT-CDP] B2B edition estende lo standard [!DNL Real-Time Customer Data Platform] con classi XDM specializzate per account, opportunità e campagne, insieme alla risoluzione delle identità B2B che mappa le relazioni persona-account. Questo consente agli esperti di marketing di creare tipi di pubblico per gli account che combinano dati firmografici (settore, ricavi, conteggio dei dipendenti), dati tecnologici (stack di tecnologia, utilizzo del prodotto) e dati comportamentali (visite web, coinvolgimento e-mail, partecipazione a eventi) dalle persone associate a tali account.

I casi d&#39;uso dei tipi di pubblico attivati per l&#39;account nella generazione della domanda di funnel: campagne di sensibilizzazione top-of-funnel su [!DNL LinkedIn] e visualizzazione di annunci pubblicitari, programmi di sviluppo mid-funnel in [!DNL Marketo Engage] e abilitazione delle vendite bottom-funnel tramite l&#39;integrazione CRM. I tipi di pubblico per la soppressione dell’account impediscono lo spreco di risorse escludendo i clienti esistenti, gli account persi chiusi o gli account già in cicli di vendita attivi.

>[!NOTE]
>Se il tuo caso d&#39;uso prevede l&#39;attivazione dei tipi di pubblico a livello di persona (B2C) anziché a livello di account, consulta [Attivazione del pubblico nelle destinazioni](audience-activation-to-destinations.md). Questo modello utilizza il modello dati standard RT-CDP e non richiede B2B edition.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### Aumentare la generazione di lead

Genera lead più qualificati per la pipeline di vendita tramite moduli, eventi, contenuti e coinvolgimento multicanale.

**KPI:** potenziali clienti, costo per lead, conversione lead

[Ulteriori informazioni sull&#39;aumento della generazione di lead](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### Migliorare la qualificazione e la conversione dei lead

Aumenta la qualità dei lead e accelera la progressione della pipeline tramite valutazione, nutrimento e follow-up personalizzato.

**KPI:** conversione lead, conversione prospect/lead, efficienza

[Ulteriori informazioni sul miglioramento della qualificazione e conversione dei lead](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### Acquisire nuovi clienti

Espandi la base di clienti tramite campagne di acquisizione mirate, tipi di pubblico simili e ottimizzazione di contenuti multimediali a pagamento.

**KPI:** nuovi clienti, costo acquisizione cliente, conversione potenziali clienti/lead

[Ulteriori informazioni sull&#39;acquisizione di nuovi clienti](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Ottimizzazione delle spese di marketing e del ROI

Migliora il ritorno sull’investimento marketing migliorando il targeting, l’attribuzione, l’eliminazione del pubblico e l’allocazione del budget.

**KPI:** Risparmio sui costi, Costo di acquisizione cliente, Ricavi incrementali

[Ulteriori informazioni sull’ottimizzazione delle spese di marketing e del ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Esempi di casi d’uso tattici

Gli scenari seguenti illustrano come questo modello può essere applicato nella pratica.

- **Pubblicità basata sull&#39;account in[!DNL LinkedIn]**: gli account di destinazione che corrispondono al tuo profilo cliente ideale (ICP) con contenuti sponsorizzati e campagne InMail in [!DNL LinkedIn], utilizzando gli elenchi di account attivati da [!DNL RT-CDP] B2B edition
- **[!DNL Marketo Engage]programma di sviluppo di destinazione** — Attiva i tipi di pubblico dell&#39;account in [!DNL Marketo Engage] per iscrivere lead e contatti associati in flussi di sviluppo di destinazione in base ai criteri di qualificazione a livello di account
- **Sincronizzazione elenco account CRM**: invia elenchi di account qualificati a [!DNL Salesforce] o [!DNL Microsoft Dynamics] per la visibilità del team di vendita, l&#39;assegnazione del territorio e i flussi di lavoro di ricerca di potenziali clienti in uscita
- **Eliminazione account per supporti a pagamento**: eliminazione di clienti esistenti, account chiusi o account in cicli di vendita attivi da campagne di acquisizione a pagamento per ridurre gli sprechi di spesa
- **Targeting dell&#39;account basato su intento**: combina segnali di intento di terze parti con dati di coinvolgimento di prime parti a livello di account per identificare e attivare tipi di pubblico di account di mercato
- **Vendita incrociata di prodotti ad account esistenti** — Crea tipi di pubblico di account utilizzando una linea di prodotti ma non un&#39;altra, quindi attiva i canali di posta elettronica e pubblicitari per le campagne di vendita incrociata
- **Targeting di eventi e webinar** - Attiva i tipi di pubblico dell&#39;account sui canali pubblicitari e di posta elettronica per promuovere la registrazione di eventi dagli account di destinazione
- **Campagne di sostituzione competitive** — Eseguire il targeting degli account utilizzando prodotti della concorrenza con messaggi personalizzati attivati tramite canali pubblicitari e di posta elettronica
- **Coinvolgimento dell&#39;account su più livelli**: segmentare gli account in livelli di coinvolgimento (alto, medio, basso) in base all&#39;attività aggregata a livello di persona e attivare campagne differenziate per ogni livello
- **Pubblico di co-marketing partner**: condividi segmenti di pubblico di account con partner di canale o programmi di co-marketing tramite destinazioni di archiviazione cloud

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare il successo di questo modello di caso d’uso.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Raggiungimento dell’account | Numero di account target raggiunti tra i canali di attivazione | Tracciare account univoci attivati per destinazione |
| Tasso di coinvolgimento dell’account | Percentuale di account attivati che mostrano i segnali di coinvolgimento | Misura l&#39;impegno a livello di persona aggregato all&#39;account |
| Influenza pipeline | Pipeline dei ricavi attribuita alle campagne di attivazione basate sull’account | Tracciare le opportunità create dai tipi di pubblico attivati dell’account |
| Costo per account coinvolto | Spesa di marketing divisa per il numero di account che mostrano il coinvolgimento | Calcolare i costi dei canali pubblicitari ed e-mail |
| Tasso di conversione lead | Percentuale di lead da account attivati che convertono in opportunità | Tracciare la conversione lead-opportunità per il pubblico attivato |
| Risparmi di soppressione del pubblico | Costo evitato eliminando gli account non idonei dalle campagne a pagamento | Misura la riduzione della spesa dai tipi di pubblico di soppressione |
| Copertura account | Percentuale del totale del mercato indirizzabile (TAM) coperto dal pubblico attivato | Confronto degli account attivati con l&#39;universo ICP totale |

## Schema del caso d’uso

**Attivazione pubblico B2B**

Attiva tipi di pubblico B2B basati sull’account tra canali web, e-mail e pubblicitari.

**Catena di funzioni:** Arricchimento profilo account > Valutazione pubblico account > Configurazione destinazione > Audience Activation > Monitoraggio

## Applicazioni

Per implementare questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Real-Time CDP]B2B edition**: piattaforma di base per l&#39;unificazione del profilo account, la risoluzione dell&#39;identità B2B, la valutazione del pubblico dell&#39;account, la configurazione della destinazione specifica B2B e l&#39;attivazione del pubblico dell&#39;account
- **[!DNL Adobe Experience Platform] (AEP)** — Infrastruttura fondamentale per la modellazione di dati XDM B2B, l&#39;acquisizione di dati da origini di automazione del marketing e del CRM, il servizio Identity e la governance
- **[!DNL Marketo Engage]** — Destinazione primaria di automazione del marketing B2B per i programmi di sviluppo dei lead, il punteggio e l&#39;esecuzione della campagna forniti dal pubblico dell&#39;account attivato

## Funzioni fondamentali

Per questo modello di caso d’uso devono essere disponibili le seguenti funzionalità fondamentali. Per ogni funzione, lo stato indica se in genere è obbligatorio, se si presume che sia preconfigurato o meno applicabile.

| Funzione fondamentale | Stato | Cosa deve essere al suo posto | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Amministrazione e governance | Obbligatorio | Sandbox con provisioning di [!DNL RT-CDP] B2B edition abilitato. Ruoli configurati per la gestione dei dati B2B, la creazione di tipi di pubblico e l’attivazione della destinazione. Criteri ABAC in vigore se i dati dell&#39;account contengono campi con restrizioni. | [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home), [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modellazione e preparazione dei dati | Obbligatorio | Schemi XDM B2B configurati utilizzando le classi XDM Business Account, XDM Business Opportunity, XDM Business Campaign e XDM Individual Profile. Gruppi di campi B2B applicati per attributi di conto, relazioni persona-account e dati opportunità. Set di dati creati e abilitati per il profilo per ogni entità B2B. Relazioni di schema definite tra entità account, persona, opportunità ed entità campagna. | [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [schemi B2B in Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b) |
| Origini dati e raccolta | Obbligatorio | Connettori Source configurati per CRM ([!DNL Salesforce], [!DNL Microsoft Dynamics]) e automazione marketing ([!DNL Marketo Engage]) per acquisire dati di account, persona, opportunità e campagna. Pipeline di acquisizione in batch o in streaming attive. Mappature della preparazione dati configurate per trasformare i dati di origine in schemi XDM B2B. | [Panoramica origini](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home), [Connettore Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| Configurazione identità e profilo | Obbligatorio | Spazi dei nomi di identità B2B configurati per gli identificatori dell’account (ID account, ID account CRM) e gli identificatori della persona (E-mail, ID contatto CRM, ID lead Marketo). Le relazioni persona-account sono state risolte tramite la risoluzione dell’identità B2B. Criteri di unione configurati per l’unificazione del profilo account. | [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [B2B edition di Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b) |
| Definizione e segmentazione del pubblico | Obbligatorio | Definizioni del pubblico a livello di account create utilizzando gli attributi dell’account, gli attributi della persona e i dati dell’attività. Pianificazioni di valutazione configurate per il pubblico dell’account. Tipi di pubblico di eliminazione definiti per escludere account non idonei. | [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Pubblico dell&#39;account](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences) |

## Funzioni di supporto

Le seguenti funzionalità incrementano questo modello di caso d’uso, ma non sono necessarie per l’esecuzione di base.

| Funzione di supporto | Stato | Perché è importante | Guida di riferimento di Experience League |
| --- | --- | --- | --- |
| Creazione di attributi calcolati/derivati | Consigliato | I punteggi di coinvolgimento aggregati, il valore del ciclo di vita e le metriche delle attività a livello di account migliorano la precisione del pubblico. Gli attributi calcolati possono aggregare eventi a livello di persona (aperture di e-mail, visite web, download di contenuti) a livello di account per l’utilizzo nella segmentazione. | [Panoramica attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Consigliato | I criteri di conservazione dei dati B2B garantiscono la pulizia dei dati obsoleti di account e opportunità. La gestione del consenso per i contatti B2B garantisce la conformità alle normative di e-mail marketing. I criteri di scadenza del set di dati impediscono l’accumulo di dati di sincronizzazione CRM obsoleti. | [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Etichettatura e applicazione dell’utilizzo dati | Incluso | I dati dei conti B2B spesso contengono restrizioni contrattuali (cifre dei ricavi, conteggi dei dipendenti da fornitori terzi). Le etichette di utilizzo dei dati impediscono l’attivazione di attributi dell’account con restrizioni su destinazioni non autorizzate. I criteri di governance garantiscono che i campi PII dei record dei contatti vengano gestiti in modo appropriato durante l’attivazione. | [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Monitoraggio e osservabilità | Incluso | Il monitoraggio dei flussi di dati del CRM e del connettore di origine [!DNL Marketo Engage] assicura che i dati dell&#39;account rimangano correnti. Il monitoraggio dell&#39;attivazione della destinazione conferma che i tipi di pubblico sono stati recapitati correttamente alle destinazioni [!DNL LinkedIn], [!DNL Marketo] e CRM. Le regole di avviso rilevano gli errori di acquisizione che causerebbero dati dell’account non aggiornati. | [Panoramica avvisi](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [Monitora flussi dati di destinazione](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations) |
| Reporting e analisi | Consigliato | [!DNL CJA] B2B edition fornisce analisi a livello di account che includono la portata del pubblico, il coinvolgimento e l&#39;influenza sulla pipeline. L’attribuzione basata sull’account consente di misurare l’impatto delle campagne di attivazione sulla progressione delle opportunità e sui ricavi. | [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Funzioni dell’applicazione

Questo piano esegue le seguenti funzioni dal catalogo delle funzioni dell&#39;applicazione. Le funzioni sono mappate su fasi di implementazione anziché su passaggi numerati.

### [!DNL Real-Time CDP] B2B edition ([!DNL RT-CDP] B2B)

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Unificazione profilo account | Fase 1: Arricchimento del profilo dell’account | Consolidare i dati dei conti da CRM, automazione del marketing e origini di terze parti in profili di account unificati utilizzando classi di schema XDM B2B |
| Risoluzione identità B2B | Fase 1: Arricchimento del profilo dell’account | Risolvere le relazioni tra persone utilizzando gli identificatori primari, mappando i contatti e i lead ai relativi account associati |
| Valutazione del pubblico dell’account | Fase 2: Valutazione del pubblico dell’account | Valuta l’iscrizione al segmento a livello di conto combinando gli attributi del conto, gli attributi della persona e i dati dell’attività della persona |
| Configurazione destinazione account | Fase 3: configurazione della destinazione | Configurare connessioni a destinazioni specifiche di B2B ([!DNL Marketo Engage], [!DNL LinkedIn], CRM, archiviazione cloud) con mappatura campi a livello di account |
| Audience Activation dell’account | Fase 4: Audience Activation | Pubblicare tipi di pubblico basati sull’account su destinazioni configurate per la destinazione, l’eliminazione o la sincronizzazione del sistema CRM |
| Integrazione di [!DNL Marketo Engage] | Fase 3: configurazione della destinazione | Configurare il flusso di dati bidirezionale con [!DNL Marketo Engage] utilizzando i connettori di origine e destinazione B2B nativi |
| Governance dei dati B2B | Fase 5: Governance e monitoraggio | Applicazione dei criteri di utilizzo dei dati e del consenso nell’attivazione dei dati dell’account B2B per evitare l’esposizione non autorizzata dei dati |

### [!DNL Real-Time CDP] ([!DNL RT-CDP]) — funzioni standard

| Funzione | Fase di implementazione | Descrizione |
| --- | --- | --- |
| Valutazione del pubblico | Fase 2: Valutazione del pubblico dell’account | Motore di valutazione sottostante per i tipi di pubblico dei conti, che supporta la valutazione in batch delle definizioni dei segmenti a livello di conto |
| Configurazione di destinazione | Fase 3: configurazione della destinazione | Infrastruttura di connessione della destinazione di base utilizzata dalla configurazione di destinazione specifica per B2B |
| Audience Activation | Fase 4: Audience Activation | Infrastruttura del flusso di dati di attivazione di base utilizzata dall’attivazione del pubblico dell’account |
| Applicazione del consenso e della governance | Fase 5: Governance e monitoraggio | Imponi preferenze di consenso e criteri di utilizzo dei dati al momento dell’attivazione |

## Prerequisiti

Completa quanto segue prima di iniziare l’implementazione.

- [ ] [!DNL RT-CDP] Licenza B2B edition fornita e attivata nell&#39;organizzazione
- [ Accesso al sistema CRM ] ([!DNL Salesforce] o [!DNL Microsoft Dynamics]) con credenziali API per la configurazione del connettore di origine
- [ Provisioning dell&#39;istanza ] [!DNL Marketo Engage] eseguito con accesso API (ID Munchkin, ID client, segreto client) se si utilizza [!DNL Marketo] come destinazione
- [ Account ] [!DNL LinkedIn] di Campaign Manager con funzionalità di pubblico corrispondente se si utilizza [!DNL LinkedIn] come destinazione
- [ ] schemi XDM B2B creati con classi account, persona, opportunità e campagna (F2)
- [ ] connettori Source configurati e che acquisiscono attivamente dati di gestione delle relazioni con i clienti e di automazione del marketing (F3)
- [ ] relazioni di identità tra persone e account risolte e profili account unificati (F4)
- [ ] convenzioni di denominazione account e tassonomia concordate per le definizioni di pubblico
- [ ] criteri di governance dei dati definiti per le classificazioni di riservatezza dei dati a livello di account

## Opzioni di implementazione

Le opzioni seguenti descrivono diversi approcci per l’implementazione di questo modello di caso d’uso. Rivedi ogni opzione e seleziona quella che meglio si adatta alle tue esigenze.

### Opzione A: attivazione del pubblico in streaming a [!DNL Marketo Engage]

**Ideale per:** organizzazioni che utilizzano [!DNL Marketo Engage] come piattaforma di automazione del marketing B2B principale, che necessitano di aggiornamenti quasi in tempo reale per attivare programmi di sviluppo, aggiornare i punteggi dei lead o modificare l&#39;iscrizione alla campagna in base al fatto che gli account si qualificano o non si qualificano.

**Funzionamento:**

Questa opzione utilizza il connettore di destinazione nativo [!DNL Marketo Engage] in [!DNL RT-CDP] per inviare in streaming le modifiche di appartenenza al pubblico dell&#39;account direttamente a [!DNL Marketo Engage]. Quando un account si qualifica per un segmento di pubblico o ne esce, i lead e i contatti associati in [!DNL Marketo] vengono aggiornati con gli attributi di appartenenza al segmento. [!DNL Marketo] le campagne intelligenti possono quindi essere attivate in base a queste modifiche di appartenenza.

La destinazione [!DNL Marketo Engage] è una destinazione di streaming, il che significa che le modifiche di appartenenza al pubblico vengono inviate in modo incrementale quando si verificano anziché in batch pianificati. Questo offre un tempo di azione più rapido per le campagne che devono rispondere alle modifiche di qualificazione dell’account. Le mappature dei campi connettono gli attributi del profilo [!DNL RT-CDP] a [!DNL Marketo] campi lead/contatto, consentendo l&#39;arricchimento di [!DNL Marketo] record con dati a livello di account da [!DNL RT-CDP].

**Considerazioni chiave:**

- Richiede l&#39;abbonamento [!DNL Marketo Engage] attivo con accesso API
- L’attivazione in streaming invia aggiornamenti incrementali, non istantanee complete del pubblico
- I record a livello di persona in [!DNL Marketo] vengono aggiornati, non direttamente i record a livello di account
- [!DNL Marketo] campagne intelligenti devono essere configurate per agire sugli aggiornamenti del campo di iscrizione al segmento

**Vantaggi:**

- Aggiornamenti dell&#39;iscrizione al pubblico quasi in tempo reale in [!DNL Marketo]
- Il connettore bidirezionale nativo semplifica l&#39;integrazione
- Gli aggiornamenti incrementali riducono al minimo il volume di trasferimento dei dati
- [!DNL Marketo] può attivare immediatamente i programmi di sviluppo in base alle modifiche del pubblico

**Limitazioni:**

- Limitato a [!DNL Marketo Engage] come destinazione di attivazione
- I vincoli di idoneità alla valutazione in streaming si applicano alle definizioni del pubblico sottostanti
- Richiede la mappatura tra i tipi di pubblico dell&#39;account [!DNL RT-CDP] e i record dei lead/contatti [!DNL Marketo]
- Potrebbe essere necessaria una logica di programma [!DNL Marketo] complessa per tradurre gli aggiornamenti a livello di persona in azioni a livello di account

**Experience League:**

- [Destinazione Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [Attivare i tipi di pubblico nella destinazione Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage#activate)

### Opzione B: attivazione batch del pubblico su piattaforme pubblicitarie

**Ideale per:** campagne pubblicitarie basate su account su [!DNL LinkedIn], reti di visualizzazione o altre piattaforme pubblicitarie in cui gli aggiornamenti giornalieri del pubblico sono sufficienti e l&#39;obiettivo principale è la portata e la consapevolezza a livello di account anziché la risposta in tempo reale.

**Funzionamento:**

Questa opzione attiva i tipi di pubblico dell&#39;account alle destinazioni della piattaforma pubblicitaria ([!DNL LinkedIn] tipi di pubblico corrispondenti, [!DNL Google] tipi di pubblico corrispondenti, [!DNL Facebook] tipi di pubblico personalizzati o [!DNL The Trade Desk]) in una cadenza batch pianificata. Il flusso di dati di attivazione esporta i membri del pubblico dell’account con campi di identità mappati (in genere indirizzi e-mail con hash di contatti associati) che la piattaforma pubblicitaria utilizza per confrontare con la propria base di utenti.

Per [!DNL LinkedIn] in particolare, la destinazione Tipi di pubblico corrispondenti a [!DNL LinkedIn] accetta la corrispondenza basata su dominio e nome della società oltre alla corrispondenza basata su e-mail, abilitando il targeting effettivo a livello di account. Altre piattaforme pubblicitarie in genere richiedono identificatori a livello di persona (e-mail, telefono) dai contatti associati agli account idonei.

L’attivazione batch viene eseguita secondo una pianificazione configurabile (giornaliera, ogni 6 ore, ecc.) ed esporta snapshot complete del pubblico o modifiche incrementali a seconda del tipo di destinazione. Questo approccio è particolarmente adatto per campagne di sensibilizzazione prolungate in cui i requisiti di aggiornamento del pubblico vengono misurati in ore anziché in minuti.

**Considerazioni chiave:**

- La freschezza del pubblico dipende dalla pianificazione batch (in genere giornaliera)
- Le piattaforme Advertising presentano limitazioni specifiche per quanto riguarda la percentuale di corrispondenza
- [!DNL LinkedIn] supporta la corrispondenza a livello di account; altre piattaforme richiedono identificatori a livello di persona
- I formati dei file di esportazione e i requisiti di identità variano a seconda della destinazione

**Vantaggi:**

- Supporta più piattaforme pubblicitarie simultaneamente
- L’elaborazione in batch gestisce in modo efficiente grandi volumi di pubblico
- I tipi di pubblico di soppressione dell’account riducono lo spreco di annunci
- [!DNL LinkedIn] tipi di pubblico corrispondenti abilita il targeting nativo a livello di account

**Limitazioni:**

- Gli aggiornamenti del pubblico non sono in tempo reale; la latenza dipende dalla pianificazione batch
- Le percentuali di corrispondenza variano in base alla piattaforma e ai campi di identità disponibili
- Alcune piattaforme non supportano la corrispondenza effettiva a livello di account, solo a livello di persona
- Richiede una configurazione di destinazione separata per ogni piattaforma pubblicitaria

**Experience League:**

- [LinkedIn - Destinazione tipi di pubblico corrispondenti](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Destinazione Customer Match di Google](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/advertising/google-customer-match)
- [Catalogo delle destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)

### Opzione C: attivazione basata su file nell&#39;archiviazione cloud

**Ideale per:** organizzazioni che necessitano della massima flessibilità nel modo in cui i tipi di pubblico degli account vengono utilizzati a valle, incluse le importazioni CRM, l&#39;arricchimento dei data warehouse, la condivisione dei dati dei partner o le integrazioni personalizzate in cui si preferisce un handoff basato su file.

**Funzionamento:**

Questa opzione esporta i tipi di pubblico dell&#39;account come file CSV, JSON o Parquet nelle destinazioni di archiviazione cloud ([!DNL Amazon S3], [!DNL Azure Blob Storage], [!DNL Google Cloud Storage], SFTP) su una cadenza pianificata. L’esportazione include attributi dell’account, campi a livello di persona da contatti associati e metadati di iscrizione al pubblico. I sistemi a valle utilizzano questi file attraverso i propri processi di importazione.

L&#39;attivazione basata su file offre il maggiore controllo sul formato di esportazione, la selezione dei campi e la pianificazione. Supporta sia l’esportazione completa (snapshot del pubblico completo ogni esecuzione) che l’esportazione incrementale (solo le modifiche dall’ultima esecuzione). Questo approccio viene comunemente utilizzato quando il sistema di destinazione non ha un connettore di destinazione [!DNL RT-CDP] nativo o quando l&#39;organizzazione deve pre-elaborare o trasformare i dati prima di caricarli nel sistema di destinazione.

**Considerazioni chiave:**

- Richiede l&#39;infrastruttura di archiviazione cloud ([!DNL S3], [!DNL Azure Blob], [!DNL GCS] o SFTP)
- I processi di importazione a valle devono essere generati e mantenuti
- Il formato del file (CSV, JSON, Parquet) deve soddisfare i requisiti di sistema a valle
- La pianificazione dell’esportazione deve essere allineata alle finestre di elaborazione a valle

**Vantaggi:**

- Massima flessibilità nel modo in cui vengono utilizzati i dati sul pubblico
- Supporta qualsiasi sistema a valle in grado di leggere i file
- Pieno controllo su formato, campi e pianificazione delle esportazioni
- Può servire più consumatori a valle da una singola esportazione
- Supporta modalità di esportazione complete e incrementali

**Limitazioni:**

- Latenza massima di tutte le opzioni (solo batch)
- Richiede la creazione e la gestione di flussi di lavoro di importazione a valle
- Nessuna integrazione nativa: è necessario un ulteriore sforzo di sviluppo
- La gestione dei file (pulizia, archiviazione) deve essere gestita separatamente

**Experience League:**

- [Destinazione Amazon S3](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [Destinazione archiviazione BLOB di Azure](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/azure-blob)
- [Attivare i tipi di pubblico nelle destinazioni batch](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/api/connect-activate-batch-destinations)

### Opzione D: attivazione in streaming su sistemi CRM

**Ideale per:** casi di utilizzo di allineamento vendite-marketing in cui le modifiche alla qualifica dell&#39;account devono essere riportate nel CRM ([!DNL Salesforce] o [!DNL Dynamics]) quasi in tempo reale per la visibilità del team di vendita, gli aggiornamenti delle assegnazioni di territorio o i flussi di lavoro di vendita automatizzati.

**Funzionamento:**

Questa opzione utilizza i connettori di destinazione di streaming ([!DNL Salesforce] CRM, [!DNL Microsoft Dynamics]) per inviare le modifiche dell&#39;appartenenza al pubblico dell&#39;account direttamente ai record dell&#39;account o dei contatti del CRM. Quando un account si qualifica per un pubblico o ne esce, il record CRM viene aggiornato con un campo personalizzato che indica l’iscrizione al segmento. I team di vendita possono quindi creare report CRM, visualizzazioni e avvisi in base a questi campi.

Il connettore di streaming invia aggiornamenti incrementali quando si verificano modifiche di appartenenza al pubblico. Le mappature dei campi collegano gli attributi dell&#39;account [!DNL RT-CDP] e della persona ai campi del sistema di gestione delle relazioni con i clienti, consentendo l&#39;arricchimento dei record del sistema di gestione delle relazioni con i clienti con dati unificati provenienti da [!DNL RT-CDP]. Questo approccio chiude il loop tra marketing intelligence (qualificazione dell’account) ed esecuzione delle vendite (flussi di lavoro CRM).

**Considerazioni chiave:**

- Richiede l’accesso all’API di gestione delle relazioni con i clienti con le autorizzazioni di scrittura appropriate
- È necessario creare campi personalizzati del CRM per ricevere i dati di iscrizione del pubblico
- Il volume di streaming deve rientrare nei limiti di velocità delle API CRM
- L’automazione del flusso di lavoro CRM deve essere configurata per agire sugli aggiornamenti dei campi

**Vantaggi:**

- Aggiornamenti CRM quasi in tempo reale per la visibilità del team di vendita
- Abilita flussi di lavoro CRM automatizzati attivati da modifiche del pubblico
- Arricchisce i record CRM con i dati account unificati di [!DNL RT-CDP]
- Supporta gli aggiornamenti dei campi a livello di account e di contatto

**Limitazioni:**

- I limiti di frequenza delle API CRM possono limitare gli aggiornamenti con volumi elevati
- Richiede personalizzazione CRM (campi personalizzati, flussi di lavoro)
- Limitato a [!DNL Salesforce] e [!DNL Microsoft Dynamics] come connettori nativi
- I vincoli di valutazione in streaming si applicano ai tipi di pubblico sottostanti

**Experience League:**

- [Destinazione Salesforce CRM](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Destinazione Microsoft Dynamics 365](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)

### Confronto delle opzioni

La tabella seguente confronta le caratteristiche chiave di ciascuna opzione di implementazione.

| Criteri | Opzione A: [!DNL Marketo] streaming | Opzione B: batch Advertising | Opzione C: archiviazione cloud | Opzione D: streaming CRM |
| --- | --- | --- | --- | --- |
| Ideale per | Attivazione del programma di sviluppo | Pubblicità basata su account | Integrazione downstream flessibile | Allineamento vendite-marketing |
| Complessi | Bassa | Medio | Medium - Alta | Medio |
| Latenza | Quasi in tempo reale (minuti) | Batch (ore) | Batch (ore) | Quasi in tempo reale (minuti) |
| Flessibilità | Basso (solo [!DNL Marketo]) | Medium (piattaforme pubblicitarie) | Alta (qualsiasi sistema a valle) | Basso (solo CRM) |
| Richiede | Licenza [!DNL Marketo Engage] | Account della piattaforma Advertising | Infrastruttura di storage cloud | Accesso API CRM |
| Targeting a livello di account | Tramite record persona | Solo [!DNL LinkedIn] (altri a livello di persona) | Configurabile | Tramite record account/contatto |
| Manutenzione | Bassa | Low-Medium | Alta | Medio |

### Scegli l’opzione giusta

Utilizza le seguenti linee guida decisionali per selezionare l’approccio corretto per l’attivazione:

1. **Se l&#39;obiettivo principale è lo sviluppo di lead B2B e si utilizza[!DNL Marketo Engage]**, scegliere l&#39;opzione A. Il connettore di streaming nativo offre il tempo di azione più veloce per i flussi di lavoro di automazione del marketing.

2. **Se l&#39;obiettivo principale è la consapevolezza basata sull&#39;account e la generazione della domanda tramite la pubblicità**, scegliere l&#39;opzione B. [!DNL LinkedIn] Matched Audiences (Tipi di pubblico corrispondenti) fornisce il targeting più efficace a livello di account. Utilizza altre piattaforme pubblicitarie per una portata più ampia.

3. **Se è necessario inviare i tipi di pubblico dell&#39;account a sistemi senza connettori [!DNL RT-CDP] nativi** o se è necessario il massimo controllo sul formato dei dati e sull&#39;elaborazione a valle, scegliere l&#39;opzione C. Questa è anche la scelta migliore per la condivisione dei dati dei partner o l’arricchimento del data warehouse.

4. **Se l&#39;obiettivo principale è l&#39;abilitazione alle vendite e la visibilità CRM degli account qualificati per il marketing**, scegliere l&#39;opzione D. Questo chiude il ciclo di handoff marketing-vendita aggiornando i record CRM in tempo quasi reale.

La maggior parte delle organizzazioni B2B implementerà più opzioni contemporaneamente, ad esempio l&#39;opzione A per i programmi di crescita, l&#39;opzione B per la pubblicità [!DNL LinkedIn] e l&#39;opzione D per la sincronizzazione CRM. Queste opzioni non si escludono a vicenda; lo stesso pubblico dell’account può essere attivato simultaneamente su più destinazioni.

## Fasi di implementazione

Le fasi seguenti descrivono il processo dettagliato per l’implementazione di questo modello di caso d’uso.

### Fase 1: arricchimento del profilo dell’account

Questa fase stabilisce profili di account unificati consolidando i dati provenienti da CRM, automazione del marketing e origini di terze parti.

**Funzione applicazione:** [!DNL RT-CDP] B2B: unificazione profilo account, [!DNL RT-CDP] B2B: risoluzione identità B2B

**Configurazione in corso:** In questa fase vengono stabiliti i profili di account unificati tramite il consolidamento dei dati da CRM, automazione marketing e origini di terze parti. La risoluzione delle identità B2B mappa le relazioni persona-account in modo che i dati del coinvolgimento a livello di persona (aperture di e-mail, visite web, download di contenuti) possano essere aggregati e utilizzati nella valutazione del pubblico a livello di account. Questa fase si basa sulle funzioni fondamentali F2, F3 e F4 che devono già essere in atto.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: strategia dell&#39;identificatore account**
>
>Quale identificatore funge da chiave dell’account principale tra i sistemi?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| ID account CRM (ad esempio, ID account [!DNL Salesforce]) | CRM è il sistema di registrazione per gli account | Approccio più comune. Assicura l&#39;allineamento tra [!DNL RT-CDP] e CRM. Richiede che tutti i sistemi di origine facciano riferimento allo stesso ID account CRM. |
>| ID account personalizzato | Più istanze CRM o un account master proprietario | Richiede un livello di mappatura tra gli ID del sistema di origine e l’ID dell’account canonico. Maggiore flessibilità, ma maggiore complessità. |
>| Numero DUNS o dominio | L’arricchimento dei dati di terze parti è l’origine dell’account principale | Utile quando la sorgente principale è costituita dai provider di dati firmografici. Potrebbe essere necessaria una corrispondenza approssimativa per la risoluzione basata sul dominio. |

>[!NOTE]
>**Decisione: modello di relazione tra persona e account**
>
>In che modo le persone (lead, contatti) sono associate agli account?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Uno a uno (ogni persona appartiene a un account) | Modello B2B semplice con dati CRM puliti | Risoluzione semplice. Più comune per il B2B di fascia media. |
>| Molti-a-molti (le persone possono appartenere a più account) | Relazioni aziendali complesse, consulenti o reti di partner | [!DNL RT-CDP] B2B edition supporta questo elemento in modo nativo. Aumenta la complessità del pubblico, ma riflette in modo preciso le relazioni nel mondo reale. |

**Navigazione interfaccia utente:** Piattaforma > Profili > Sfoglia (per verificare i profili account unificati)

**Dettagli configurazione chiave:**

- Verifica che siano presenti schemi XDM B2B (account aziendale XDM, account persona aziendale XDM) da F2
- Conferma CRM e [!DNL Marketo] connettori di origine stanno attivamente acquisendo i dati account e persona da F3
- Verifica che le relazioni tra persone e account siano risolte nel grafico delle identità da F4
- Verifica la completezza del profilo account esplorando i profili account di esempio

**Documentazione di Experience League:**

- [Panoramica di Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [Schemi B2B in Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Connettore Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Connettore Salesforce](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/crm/salesforce)

### Fase 2: Valutazione del pubblico dell’account

Questa fase definisce e valuta i tipi di pubblico a livello di account utilizzando una combinazione di attributi di account, attributi di persona e dati di attività della persona.

**Funzione dell&#39;applicazione:** [!DNL RT-CDP] B2B: Valutazione del pubblico dell&#39;account, [!DNL RT-CDP]: Valutazione del pubblico

**Configurazione:** Questa fase definisce e valuta i tipi di pubblico a livello di account utilizzando una combinazione di attributi di account, attributi di persona e dati di attività della persona. I tipi di pubblico degli account in [!DNL RT-CDP] B2B edition consentono di segmentare gli account in base alle caratteristiche firmografiche (settore, ricavi, conteggio dipendenti) e al comportamento di coinvolgimento delle persone associate a tali account.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: metodo di valutazione del pubblico**
>
>Con quale rapidità deve essere aggiornata l’iscrizione al pubblico dell’account?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Valutazione batch (giornaliera) | Il pubblico delle campagne viene aggiornato su base giornaliera, le attivazioni basate su file e i tipi di pubblico delle piattaforme pubblicitarie | La maggior parte dei tipi di pubblico degli account utilizza la valutazione in batch. Gestisce query complesse con più entità che combinano attributi di account e di persona. Sufficiente per la maggior parte dei casi di utilizzo B2B in cui è accettabile l’aggiornamento giornaliero. |
>| Valutazione in streaming | Attivazione di [!DNL Marketo] o CRM in cui è necessaria la qualifica quasi in tempo reale | I tipi di pubblico dell’account hanno un’idoneità limitata allo streaming. Solo le condizioni dell’attributo dell’account semplice possono essere considerate per la valutazione in streaming. Le condizioni comportamentali a livello di persona richiedono in genere un batch. |

>[!NOTE]
>**Decisione: approccio di definizione del pubblico dell&#39;account**
>
>Come definirai i criteri di pubblico dell’account?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Solo attributi account | Targeting firmografico semplice (settore, ricavi, area geografica) | Implementazione più rapida. Limitato ai dati a livello di account. Utilizza per il targeting ampio. |
>| Account + attributi persona | Esecuzione del targeting di account in cui le persone associate corrispondono a criteri specifici (qualifica, reparto) | Un targeting più preciso. Combina dati firmografici e demografici. |
>| Account + attributi persona + attività persona | Esecuzione del targeting di account con contatti coinvolti (aperture di e-mail, visite web, download di contenuti) | Più potente, ma più complesso. Richiede dati evento comportamentale da F3. In genere richiede la valutazione batch. |
>| Composizione del pubblico | Logica di pubblico complessa che richiede operazioni di classificazione, suddivisione, esclusione o arricchimento | Utilizza l’area di lavoro di Composizione del pubblico visiva per i tipi di pubblico dell’account derivati. Limitato alla valutazione in batch. |

>[!NOTE]
>**Decisione: strategia di soppressione del pubblico**
>
>Quali account devono essere esclusi dall’attivazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Soppressione cliente esistente | Campagne di acquisizione con targeting per account nuovi | Escludi account con abbonamenti attivi o opportunità acquisite |
>| Soppressione ciclo di vendita attivo | Evita di interferire con gli account nel coinvolgimento attivo delle vendite | Escludi account con opportunità aperte al di sopra di una determinata fase |
>| Soppressione di coinvolgimento recente | Impedisci messaggistica eccessiva degli account contattati di recente | Escludi gli account coinvolti in un intervallo di lookback (ad esempio, 30 giorni) |
>| Nessuna soppressione | Campagne di brand awareness indirizzate a tutti gli account idonei | Da utilizzare con cautela; potrebbe comportare uno spreco di risorse per gli account non idonei |

**Navigazione interfaccia utente:** Cliente > Tipi di pubblico > Crea pubblico > Genera regola (seleziona Account come tipo di pubblico)

**Dettagli configurazione chiave:**

- Seleziona &quot;Account&quot; come tipo di pubblico durante la creazione di un nuovo pubblico in Segment Builder (Generatore di segmenti)
- Gli attributi dell’account vengono visualizzati nella sezione Account nel Generatore segmenti (settore, ricavi, stato dell’account)
- Gli attributi e le attività della persona possono essere aggiunti tramite la relazione &quot;Persone&quot; nel generatore di pubblico dell’account
- Configura la pianificazione di valutazione batch se non ne esiste già una per la sandbox
- Creare tipi di pubblico di targeting (account da includere) ed eliminare tipi di pubblico (account da escludere)

**Documentazione di Experience League:**

- [Pubblico dell’account](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Composizione del pubblico](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)

### Fase 3: configurazione della destinazione

Questa fase stabilisce connessioni autenticate alle destinazioni di destinazione in cui verranno recapitati i tipi di pubblico dell’account.

**Funzione dell&#39;applicazione:** [!DNL RT-CDP] B2B: configurazione di destinazione dell&#39;account, [!DNL RT-CDP] B2B: integrazione [!DNL Marketo Engage], [!DNL RT-CDP]: configurazione di destinazione

**Configurazione:** In questa fase vengono stabilite connessioni autenticate alle destinazioni di destinazione in cui verranno recapitati i tipi di pubblico dell&#39;account. La configurazione include la selezione della destinazione dal catalogo, l’immissione delle credenziali di autenticazione, la configurazione delle mappature dei campi a livello di account e di persona e l’impostazione della pianificazione dell’esportazione. Ogni tipo di destinazione ha requisiti e funzionalità univoci.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: selezione destinazione**
>
>Quale destinazione/i riceverà/riceverà/riceveranno il pubblico dell’account attivato?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| [!DNL Marketo Engage] | Sviluppo, punteggio ed esecuzione di campagne lead B2B | Connettore di streaming nativo. Aggiorna i record di contatti/lead. Richiede le credenziali API [!DNL Marketo] (ID Munchkin, ID client, Segreto client). |
>| [!DNL LinkedIn] tipi di pubblico corrispondenti | Pubblicità basata sull&#39;account su [!DNL LinkedIn] | Supporta la corrispondenza dei nomi delle società e dei domini per il targeting a livello di account. Attivazione batch. Richiede l&#39;accesso a [!DNL LinkedIn] Campaign Manager. |
>| CRM [!DNL Salesforce] | Sincronizzazione elenco account CRM e abilitazione vendite | Il connettore di streaming aggiorna i record di account o contatti. Richiede l&#39;accesso API [!DNL Salesforce] con autorizzazioni di scrittura. |
>| [!DNL Microsoft Dynamics 365] | Attivazione vendite per organizzazioni basate su [!DNL Dynamics] | Connettore di streaming. Richiede l&#39;accesso API [!DNL Dynamics 365]. |
>| Archiviazione cloud ([!DNL S3], [!DNL Azure Blob], [!DNL GCS], SFTP) | Integrazioni personalizzate, data warehouse, condivisione partner | Esportazione batch basata su file. Massima flessibilità, ma richiede un&#39;elaborazione a valle. |
>| Corrispondenza cliente [!DNL Google] | Ricerca e visualizzazione di targeting pubblicitario | Corrispondenza a livello di persona tramite e-mail con hash. Attivazione batch. |
>| [!DNL The Trade Desk] | Display programmatico e pubblicità video | Corrispondenza a livello di persona. Attivazione batch. |

>[!NOTE]
>**Decisione: strategia di mappatura dei campi**
>
>Quali campi account e persona devono essere mappati alla destinazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Solo campi di identità | Piattaforme Advertising che richiedono solo identificatori corrispondenti | Trasferimento di dati minimo. La destinazione corrisponde nel dominio e-mail o aziendale. |
>| Identità + attributi dell’account core | CRM o [!DNL Marketo] in cui il contesto dell&#39;account migliora il targeting | Include settore, ricavi, conteggio dipendenti, livello conto. Arricchire i record a valle. |
>| Set di attributi completo | Esportazioni di archiviazione cloud o data warehouse | Includi tutti gli attributi di account e persona rilevanti. Payload di esportazione più grande. |

**Navigazione interfaccia utente:** Connessioni > Destinazioni > Catalogo > Cerca destinazione > Configura

**Dettagli configurazione chiave:**

- Passa al catalogo Destinazioni e seleziona la destinazione
- Fornisci credenziali di autenticazione specifiche per il tipo di destinazione
- Configura le mappature dei campi che collegano i campi XDM [!DNL RT-CDP] ai campi di destinazione
- Per [!DNL Marketo Engage]: specificare ID Munchkin, ID client e Segreto client
- Per [!DNL LinkedIn]: autorizzare tramite OAuth e selezionare l&#39;account annuncio [!DNL LinkedIn]
- Per l’archiviazione cloud: fornisci nome bucket/contenitore, percorso, formato file e credenziali
- Per CRM: specifica l’URL dell’istanza, le credenziali API e il tipo di oggetto di destinazione (account o contatto)

**Opzioni divergenti:**

**Per L&#39;Opzione A ([!DNL Marketo Engage] Streaming):**

Passa a Destinazioni > Catalogo > Adobe > [!DNL Marketo Engage]. Configura l&#39;ID Munchkin e le credenziali API. Mappa i campi di identità (e-mail) di [!DNL RT-CDP] e gli attributi del profilo ai campi lead di [!DNL Marketo]. La destinazione gestisce automaticamente gli aggiornamenti di streaming incrementali.

**Per L&#39;Opzione B (Batch Piattaforma Advertising):**

Passa a Destinazioni > Catalogo > Advertising/Social > seleziona piattaforma. Autorizza tramite OAuth. Configura la pianificazione dell’esportazione (consigliata: giornaliera). Mappa gli identificatori e-mail con hash ed eventuali campi corrispondenti supportati. Per [!DNL LinkedIn], mappare inoltre i campi nome società e dominio per la corrispondenza a livello di account.

**Per L&#39;Opzione C (Basata Su File Di Archiviazione Cloud):**

Passa a Destinazioni > Catalogo > Archiviazione cloud > seleziona il provider. Configura bucket/contenitore, modello di percorso file e formato file (CSV, JSON o Parquet). Imposta la pianificazione dell’esportazione e scegli esportazione completa o incrementale. Mappa tutti i campi di attributi account e persona desiderati.

**Per l&#39;opzione D (flusso CRM):**

Passa a Destinazioni > Catalogo > CRM > seleziona [!DNL Salesforce] o [!DNL Dynamics]. Fornisci le credenziali API e l’URL dell’istanza. Mappa i campi [!DNL RT-CDP] ai campi Contatto o Account CRM. Assicurati che nel CRM siano presenti campi personalizzati per ricevere i dati di iscrizione del pubblico.

**Documentazione di Experience League:**

- [Panoramica sulle destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Catalogo delle destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Destinazione Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [LinkedIn - Destinazione tipi di pubblico corrispondenti](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Destinazione Salesforce CRM](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Destinazione Amazon S3](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)

### Fase 4: Attivazione del pubblico

Questa fase pubblica i tipi di pubblico dell’account valutati nelle destinazioni configurate.

**Funzione applicazione:** [!DNL RT-CDP] B2B: Audience Activation account, [!DNL RT-CDP]: Audience Activation

**Configurazione:** In questa fase i tipi di pubblico dell&#39;account valutati vengono pubblicati nelle destinazioni configurate. Activation crea il flusso di dati che collega il pubblico dell’account (sorgente) alla destinazione esterna (destinazione), applica i mapping degli attributi e avvia l’esportazione in base alla pianificazione configurata o al comportamento di streaming. Puoi anche configurare i tipi di pubblico per l’eliminazione in modo da escludere dall’attivazione gli account non idonei.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: tipo di esportazione**
>
>L’attivazione deve esportare snapshot del pubblico completo o solo modifiche incrementali?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Esportazione incrementale | Destinazioni di streaming ([!DNL Marketo], CRM) o destinazioni batch in cui i sistemi a valle gestiscono i delta | Volume di dati inferiore per esportazione. Elaborazione più rapida. Richiede sistemi a valle per gestire lo stato. Impostazione predefinita per le destinazioni di streaming. |
>| Esportazione completa | Destinazioni batch in cui il sistema a valle sostituisce il pubblico completo per ogni esecuzione | Volume di dati più grande ma logica downstream più semplice. Utile quando i sistemi a valle non mantengono lo stato. Disponibile per destinazioni basate su file. |

>[!NOTE]
>**Decisione: ambito di attivazione**
>
>Quanti tipi di pubblico devono essere attivati per destinazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Pubblico singolo per flusso di dati | Attivazione semplice con una chiara mappatura tra pubblico e destinazione | Monitoraggio e risoluzione dei problemi più semplici. Un errore del pubblico non influisce sugli altri. |
>| Più pubblici per flusso di dati | Più tipi di pubblico correlati che vanno alla stessa destinazione | Uso più efficiente delle connessioni di destinazione. Tutti i tipi di pubblico condividono la stessa mappatura dei campi e la stessa pianificazione. |

**Navigazione interfaccia utente:** Connessioni > Destinazioni > Sfoglia > Seleziona destinazione > Attiva tipi di pubblico

**Dettagli configurazione chiave:**

- Seleziona i tipi di pubblico target dall’elenco del pubblico
- Rivedi e conferma le mappature dei campi configurate nella Fase 3
- Per le destinazioni batch: configura la pianificazione dell’esportazione (ora, frequenza)
- Per le destinazioni di streaming: l’attivazione inizia immediatamente dopo la configurazione
- Facoltativamente, aggiungi tipi di pubblico di soppressione utilizzando la funzionalità di esclusione
- Attiva un’esecuzione iniziale dell’attivazione del test per convalidare il flusso di dati

**Opzioni divergenti:**

**Per L&#39;Opzione A ([!DNL Marketo Engage] Streaming):**

Seleziona il pubblico dell’account da attivare. L&#39;attivazione inizia immediatamente lo streaming. Verificare in [!DNL Marketo] che i record di lead/contatti vengano aggiornati con i campi di appartenenza ai segmenti. Configura [!DNL Marketo] campagne intelligenti da attivare in base a queste modifiche di campo.

**Per L&#39;Opzione B (Batch Piattaforma Advertising):**

Seleziona il pubblico dell’account e configura la pianificazione delle esportazioni giornaliere. Al termine della prima esportazione, verifica nella piattaforma pubblicitaria che il pubblico sia visualizzato e che abbia un numero di membri popolato. Consenti alla piattaforma di elaborare il file del pubblico iniziale per 24-48 ore.

**Per L&#39;Opzione C (Basata Su File Di Archiviazione Cloud):**

Seleziona i tipi di pubblico dell’account e configura la pianificazione dell’esportazione e il formato del file. Dopo la prima esportazione, verificare che i file vengano visualizzati nel percorso di archiviazione di destinazione con il formato e il contenuto previsti. Conferma dei processi di importazione a valle che utilizzano correttamente i file esportati.

**Per l&#39;opzione D (flusso CRM):**

Seleziona il pubblico dell’account da attivare. L&#39;attivazione inizia immediatamente lo streaming. Verifica nel CRM che i record di account o contatti vengano aggiornati con i campi mappati. Configura i rapporti CRM, le viste elenco o l’automazione del flusso di lavoro per agire sui campi aggiornati.

**Documentazione di Experience League:**

- [Attivare i tipi di pubblico nelle destinazioni di streaming](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Attivare i tipi di pubblico nelle destinazioni batch](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Guardrail di attivazione](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- [Panoramica sulle destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)

### Fase 5: Governance e monitoraggio

Questa fase assicura che l’attivazione del pubblico dell’account sia conforme ai criteri di governance dei dati e alle preferenze di consenso, e che i flussi di dati di attivazione in corso siano monitorati per verificarne l’integrità.

**Funzione dell&#39;applicazione:** [!DNL RT-CDP] B2B: governance dei dati B2B, [!DNL RT-CDP]: applicazione del consenso e della governance

**Configurazione:** questa fase garantisce che l&#39;attivazione del pubblico dell&#39;account sia conforme ai criteri di governance dei dati e alle preferenze di consenso e che i flussi di dati di attivazione in corso siano monitorati per verificarne l&#39;integrità. La governance dei dati B2B applica restrizioni agli attributi sensibili dell’account (ricavi, conteggio dei dipendenti da fornitori terzi), mentre l’applicazione del consenso assicura che le comunicazioni a livello di persona rispettino le preferenze di rinuncia. Il monitoraggio conferma che i flussi di dati di attivazione vengono completati correttamente.

**Punti decisionali in questa fase:**

>[!NOTE]
>**Decisione: livello di applicazione della governance**
>
>In che modo la governance dei dati deve essere applicata rigorosamente per le attivazioni B2B?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Applicazione completa (blocco in caso di violazione) | Attivazioni di produzione con dati sensibili | Impedisce qualsiasi attivazione che viola i criteri di governance. Per risolvere le violazioni, potrebbe essere necessario apportare delle modifiche alla mappatura iterativa dei campi. |
>| Avvisa e continua | Ambienti di sviluppo o test | Consente l&#39;attivazione ma registra gli avvisi. Utile durante la configurazione iniziale per identificare potenziali problemi. |

>[!NOTE]
>**Decisione: approccio di monitoraggio**
>
>Come deve essere monitorato lo stato di attivazione?
>
>| Opzione | Quando scegliere | Considerazioni |
>| --- | --- | --- |
>| Monitoraggio basato sugli avvisi | Ambienti di produzione in cui gli errori devono essere rilevati rapidamente | Configurare gli avvisi per gli errori di attivazione della destinazione, gli errori del flusso di origine e i ritardi del flusso di dati. Richiede la configurazione dell’abbonamento agli avvisi. |
>| Monitoraggio manuale | Sviluppo o attivazioni a basso volume | Il flusso di dati di revisione periodica viene eseguito nell’interfaccia utente delle destinazioni. Minore sovraccarico ma rischio di ritardo nel rilevamento dei guasti. |
>| Entrambi | Ambienti di produzione con attivazione complessa multi-destinazione | Avvisi per errori critici e revisione periodica del dashboard per le tendenze. Consigliato per la maggior parte delle implementazioni B2B. |

**Navigazione interfaccia utente:** Privacy > Criteri (per governance), Connessioni > Destinazioni > Sfoglia > Seleziona destinazione > Flussi di dati in esecuzione (per monitoraggio)

**Dettagli configurazione chiave:**

- Applicare etichette di utilizzo dei dati ai set di dati B2B contenenti attributi con restrizioni
- Verificare che i criteri di governance vengano applicati valutando l’attivazione in base all’azione di marketing di destinazione
- Configurare gli avvisi per gli errori di attivazione della destinazione e del connettore di origine
- Rivedere le metriche di esecuzione del flusso di dati (profili esportati, record non riusciti) dopo ogni ciclo di attivazione
- Imposta la revisione del dashboard utilizzo licenze per tenere traccia del volume del profilo account in base ai diritti

**Documentazione di Experience League:**

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Consenso e preferenze](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Monitorare i flussi di dati di destinazione](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Panoramica degli avvisi](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Guardrail di attivazione](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

## Considerazioni sull’implementazione

Le sezioni seguenti forniscono ulteriori indicazioni per un’implementazione corretta.

### Guardrail e limiti

Esamina i seguenti guardrail e limiti della piattaforma applicabili a questo pattern di casi d’uso.

- Massimo 4.000 definizioni di segmenti per sandbox, inclusi i tipi di pubblico dell&#39;account — [Guardrail di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- I tipi di pubblico dell’account vengono valutati principalmente utilizzando la valutazione in batch; l’idoneità allo streaming è limitata a condizioni di attributi dell’account semplici
- Massimo 100 flussi di dati per connessione di destinazione — [Guardrail di destinazione](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- Le destinazioni batch esportano fino a 5 milioni di profili per segmento di file
- Le destinazioni di streaming hanno limiti di velocità effettiva al secondo impostati dal partner di destinazione (ad esempio, limiti di velocità API [!DNL Marketo])
- I tipi di pubblico composti (da Composizione pubblico) sono limitati alla valutazione in batch e non possono utilizzare lo streaming
- Massimo 10 blocchi di composizione per area di lavoro di composizione del pubblico
- [!DNL LinkedIn] tipi di pubblico corrispondenti richiedono una dimensione minima del pubblico (in genere 300 membri) per l&#39;attivazione
- Le destinazioni di streaming CRM sono soggette ai limiti di velocità API del provider di gestione delle relazioni con i clienti (ad esempio, [!DNL Salesforce] limiti giornalieri API in blocco)
- [!DNL RT-CDP] la licenza B2B edition regola il numero totale di profili dell&#39;account aziendale - [Descrizione del prodotto RT-CDP](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

### Insidie comuni

Quando implementi questo modello di caso d’uso, tieni presente i seguenti problemi comuni.

- **Mappatura da persona a account incompleta:** Se i record di persona (lead, contatti) non sono collegati correttamente ai record di account tramite la risoluzione dell&#39;identità B2B, i tipi di pubblico dell&#39;account che dipendono da attributi o attività di persona sottovaluteranno gli account idonei. Convalida le relazioni tra persone e conti in F4 prima di creare i tipi di pubblico per i conti.

- **Dati CRM obsoleti che causano la deviazione del pubblico:** Se i connettori di origine CRM non sono in esecuzione su una pianificazione regolare o non riescono in modo invisibile all&#39;utente, gli attributi dell&#39;account (settore, ricavi, stato) diventano obsoleti. In questo modo i tipi di pubblico includono gli account che non soddisfano più o escludono gli account che dovrebbero essere idonei. Monitora lo stato del flusso di dati del connettore di origine.

- **Aspettative di percentuali di corrispondenza per la piattaforma Advertising:** Quando si attivano i tipi di pubblico dell&#39;account su piattaforme pubblicitarie diverse da [!DNL LinkedIn], la percentuale di corrispondenza dipende dall&#39;esistenza di identificatori a livello di persona validi (e-mail con hash) per i contatti associati ad account idonei. Gli account senza contatti associati con indirizzi e-mail non corrisponderanno. Monitora le percentuali di corrispondenza e prendi in considerazione l’arricchimento dei dati di contatto.

- Mapping del campo **[!DNL Marketo]non allineato:** Durante il flusso a [!DNL Marketo Engage], il mapping del campo [!DNL RT-CDP] deve eseguire il targeting dei campi lead o contatto [!DNL Marketo] esistenti. Se il campo [!DNL Marketo] mappato non esiste, l&#39;aggiornamento non riuscirà. Precreare tutti i campi di destinazione in [!DNL Marketo] prima di configurare la destinazione.

- **Attivazione di blocco dei criteri di governance:** Le etichette di utilizzo dei dati nei campi degli attributi dell&#39;account (in particolare i dati firmografici di terze parti) possono attivare violazioni di governance durante l&#39;attivazione nelle destinazioni pubblicitarie. Valuta la conformità in materia di governance prima di attivare e, se necessario, regola le mappature dei campi per escludere i campi con restrizioni.

- **Il pubblico dell&#39;account combina i dati dell&#39;account e della persona con la valutazione solo batch:** I tipi di pubblico dell&#39;account che fanno riferimento a eventi comportamentali a livello di persona (ad esempio, &quot;account in cui almeno un contatto ha aperto un&#39;e-mail negli ultimi 30 giorni&quot;) richiedono la valutazione batch. Se il caso d’uso prevede una qualificazione in tempo reale, questo vincolo può causare una latenza imprevista.

### Best practice

Segui queste raccomandazioni per risultati ottimali.

- Inizia con un piccolo numero di tipi di pubblico per account ben definiti (livello ICP, settore verticale, livello di coinvolgimento) prima di espanderli a definizioni complesse con più attributi
- Crea tipi di pubblico di eliminazione dedicati per clienti esistenti, opportunità attive e account recentemente coinvolti per evitare sprechi di spesa e conflitti di canale
- Utilizza la funzione Composizione pubblico per creare tipi di pubblico per account su più livelli (coinvolgimento alto/medio/basso) classificando gli account in base ai punteggi di coinvolgimento aggregati
- Attiva lo stesso pubblico account su più destinazioni contemporaneamente per campagne multicanale coordinate (ad esempio [!DNL LinkedIn] per la pubblicità, [!DNL Marketo] per l&#39;e-mail, CRM per la visibilità delle vendite)
- Implementa una convenzione di denominazione coerente per i tipi di pubblico dell’account che includa i criteri di targeting e il canale previsto (ad esempio, &quot;B2B_ICP_Enterprise_Tech_LinkedIn&quot; o &quot;B2B_Suppression_ActiveOpps&quot;)
- Pianifica l’attivazione batch nelle ore di minore utilizzo per ridurre al minimo l’impatto sui sistemi a valle e allinearla alle finestre di elaborazione delle piattaforme pubblicitarie
- Monitora i tassi di corrispondenza per destinazione dopo l’attivazione iniziale e ripeti le mappature dei campi di identità per migliorare la corrispondenza
- Gestisci flusso di dati bidirezionale con [!DNL Marketo Engage]: acquisisci i dati di coinvolgimento da [!DNL Marketo] in [!DNL RT-CDP] (connettore di origine) e attiva di nuovo i tipi di pubblico in [!DNL Marketo] (connettore di destinazione) per un sistema a loop chiuso

### Decisioni di compromesso

Quando prendi decisioni di implementazione, considera i seguenti compromessi.

>[!NOTE]
>**Compensazione: aggiornamento del pubblico rispetto alla complessità della valutazione**
>
>I tipi di pubblico dell’account che combinano attributi dell’account con dati comportamentali a livello di persona forniscono il targeting più preciso, ma sono limitati alla valutazione in batch (aggiornamento giornaliero). Un pubblico più semplice basato solo sugli attributi dell’account può qualificarsi per la valutazione in streaming con aggiornamenti in tempo quasi reale.
>
>- **Preferenze per il batch (criteri complessi):** precisione di targeting, combinazione di segnali firmografici e comportamentali, punteggio account completo
>- **Preferenza per lo streaming (criteri semplici):** velocità di aggiornamento del pubblico, risposta in tempo reale alle modifiche dell&#39;account, tempo di azione più rapido in [!DNL Marketo] e CRM
>- **Consiglio:** utilizza la valutazione in batch per i tipi di pubblico di targeting primari in cui è accettabile l&#39;aggiornamento giornaliero (per la maggior parte dei casi di utilizzo B2B). Riserva la valutazione in streaming per attivatori sensibili al tempo, come modifiche dello stato dell’account o avvisi di account di alto valore.

>[!NOTE]
>**Compensazione: attivazione centralizzata e pubblico specifico per la destinazione**
>
>Puoi attivare un singolo pubblico di account unificato per più destinazioni, oppure creare un pubblico specifico per la destinazione in base alle funzionalità e ai requisiti di ciascun canale.
>
>- **Il pubblico centralizzato favorisce:** coerenza tra i canali, gestione più semplice del pubblico, reporting unificato
>- **I tipi di pubblico specifici della destinazione sono i preferiti:** Il targeting ottimizzato per canale (ad esempio, [!DNL LinkedIn] beneficia degli attributi a livello di società mentre [!DNL Marketo] necessita di dettagli a livello di lead), regole di soppressione specifiche del canale
>- **Consiglio:** inizia con tipi di pubblico centralizzati per coerenza, quindi crea varianti specifiche per la destinazione solo quando i requisiti del canale divergono in modo significativo (ad esempio, diverse finestre di soppressione per la pubblicità rispetto all&#39;e-mail).

>[!NOTE]
>**Compensazione: sincronizzazione CRM in tempo reale e aggiornamenti CRM batch**
>
>Lo streaming verso il sistema CRM fornisce visibilità immediata sulle vendite, ma consuma quote API CRM. Le esportazioni di file batch sono più efficienti, ma introducono la latenza.
>
>- **Sincronizzazione CRM in streaming:** reattività alle vendite, avvisi immediati sugli account, visibilità della pipeline in tempo reale
>- **Aggiornamenti Batch CRM a favore di:** conservazione delle quote API, efficienza dell&#39;aggiornamento in blocco, allineamento con le finestre di caricamento dei dati CRM
>- **Consiglio:** utilizzare la sincronizzazione CRM in streaming per le modifiche di qualifica dell&#39;account ad alta priorità (ad esempio, spostamenti dell&#39;account al livello &quot;Pronto per le vendite&quot;). Utilizzare le esportazioni di file batch per aggiornamenti in blocco, ad esempio aggiornamenti mensili del punteggio dell&#39;account o elenchi di riassegnazione del territorio.

## Documentazione correlata

Le risorse seguenti forniscono ulteriore contesto e indicazioni dettagliate per le funzionalità utilizzate in questo modello di caso d’uso.

**[!DNL RT-CDP]B2B edition**

- [Panoramica di Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [Schemi B2B in Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Pubblico dell’account](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [Descrizione del prodotto B2B edition RT-CDP](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

**Valutazione del pubblico e segmentazione**

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Composizione del pubblico](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Guardrail di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

**Destinazioni e attivazione**

- [Panoramica sulle destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Catalogo delle destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Destinazione Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [LinkedIn - Destinazione tipi di pubblico corrispondenti](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Destinazione Salesforce CRM](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Destinazione Microsoft Dynamics 365](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)
- [Destinazione Amazon S3](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [Attivare i tipi di pubblico nelle destinazioni di streaming](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Attivare i tipi di pubblico nelle destinazioni batch](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Guardrail di attivazione](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

**Origini dati e connettori**

- [Panoramica sulle origini](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Connettore Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Connettore Salesforce](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/crm/salesforce)

**Modellazione dati e identità**

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica del profilo](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

**Governance dei dati e privacy**

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview)
- [Consenso e preferenze](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Monitoraggio e osservabilità**

- [Panoramica degli avvisi](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Monitorare i flussi di dati di destinazione](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Monitorare i flussi di dati di origine](https://experienceleague.adobe.com/en/docs/experience-platform/sources/api-tutorials/monitor)
- [Dashboard utilizzo licenze](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Reporting e analisi**

- [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Panoramica delle connessioni](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Panoramica delle visualizzazioni dati](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)

**Tutorial e guide**

- [Guida introduttiva a Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro)
- [Creare uno schema per le origini B2B](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Strumenti sandbox](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/sandbox-tooling-api/overview)
