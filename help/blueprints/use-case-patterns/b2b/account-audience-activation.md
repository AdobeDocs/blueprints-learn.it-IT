---
title: Audience Activation B2B
description: Scopri come attivare tipi di pubblico B2B basati sull’account tra canali web, e-mail e pubblicitari.
solution: Real-Time Customer Data Platform
exl-id: 2b979159-37aa-41d4-a6b4-1105538f6546
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1540'
ht-degree: 2%

---

# Attivazione del pubblico B2B

Questa guida descrive il modello di caso d&#39;uso dell&#39;attivazione del pubblico B2B, che utilizza [!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition per generare, valutare e attivare tipi di pubblico a livello di account tra canali Web, e-mail, pubblicitari e CRM. È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono comprendere il funzionamento di questo modello, gli obiettivi aziendali supportati, i casi di utilizzo tattici che consente e le applicazioni Adobe coinvolte.

Questo modello copre l&#39;intero ciclo di vita dall&#39;unificazione del profilo dell&#39;account attraverso la valutazione del pubblico e l&#39;attivazione a destinazioni specifiche di B2B come [!DNL Marketo Engage], [!DNL LinkedIn] e i sistemi CRM.

## Schema del caso d’uso

**Attivazione pubblico B2B**

Attiva tipi di pubblico B2B basati sull’account tra canali web, e-mail e pubblicitari.

**Piano di esecuzione:** Arricchimento profilo account > Valutazione pubblico account > Configurazione destinazione > Audience Activation > Monitoraggio

## Panoramica del caso d’uso

I team di marketing B2B devono eseguire il targeting e attivare i tipi di pubblico a livello di account anziché a livello di singola persona. A differenza dell’attivazione del pubblico B2C, in cui l’unità di targeting è un singolo profilo di consumatore, l’attivazione del pubblico B2B richiede la comprensione della relazione tra le persone e gli account a cui appartengono, la valutazione dell’iscrizione al pubblico in base agli attributi a livello di account combinati con i segnali di coinvolgimento a livello di persona e la distribuzione di tali tipi di pubblico a destinazioni che supportano il targeting basato sull’account.

[!DNL RT-CDP] B2B edition estende lo standard [!DNL Real-Time Customer Data Platform] con classi XDM specializzate per account, opportunità e campagne, insieme alla risoluzione delle identità B2B che mappa le relazioni persona-account. Questo consente agli esperti di marketing di creare tipi di pubblico per gli account che combinano dati firmografici (settore, ricavi, conteggio dei dipendenti), dati tecnologici (stack di tecnologia, utilizzo del prodotto) e dati comportamentali (visite web, coinvolgimento e-mail, partecipazione a eventi) dalle persone associate a tali account.

I casi d&#39;uso dei tipi di pubblico attivati per l&#39;account nella generazione della domanda di funnel: campagne di sensibilizzazione top-of-funnel su [!DNL LinkedIn] e visualizzazione di annunci pubblicitari, programmi di sviluppo mid-funnel in [!DNL Marketo Engage] e abilitazione delle vendite bottom-funnel tramite l&#39;integrazione CRM. I tipi di pubblico per la soppressione dell’account impediscono lo spreco di risorse escludendo i clienti esistenti, gli account persi chiusi o gli account già in cicli di vendita attivi.

>[!NOTE]
>Se il tuo caso d&#39;uso prevede l&#39;attivazione dei tipi di pubblico a livello di persona (B2C) anziché a livello di account, consulta [Attivazione del pubblico nelle destinazioni](../audience-building-activation/audience-activation-to-destinations.md). Questo modello utilizza il modello dati standard RT-CDP e non richiede B2B edition.

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

## Applicazioni

Per implementare questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Real-Time CDP]B2B edition**: piattaforma di base per l&#39;unificazione del profilo account, la risoluzione dell&#39;identità B2B, la valutazione del pubblico dell&#39;account, la configurazione della destinazione specifica B2B e l&#39;attivazione del pubblico dell&#39;account
- **[!DNL Adobe Experience Platform] (AEP)** — Infrastruttura fondamentale per la modellazione di dati XDM B2B, l&#39;acquisizione di dati da origini di automazione del marketing e del CRM, il servizio Identity e la governance
- **[!DNL Marketo Engage]** — Destinazione primaria di automazione del marketing B2B per i programmi di sviluppo dei lead, il punteggio e l&#39;esecuzione della campagna forniti dal pubblico dell&#39;account attivato

## Documentazione correlata

Le risorse seguenti forniscono ulteriore contesto e indicazioni dettagliate per le funzionalità utilizzate in questo modello di caso d’uso.

**[!DNL RT-CDP]B2B edition**

- [Panoramica di Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [Schemi B2B in Real-Time CDP](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/schemas/b2b)
- [Pubblico dell’account](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/types/account-audiences)
- [Descrizione del prodotto B2B edition RT-CDP](https://helpx.adobe.com/it/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

**Valutazione del pubblico e segmentazione**

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder)
- [Composizione del pubblico](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/audience-composition)
- [Segmentazione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Guardrail di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)

**Destinazioni e attivazione**

- [Panoramica sulle destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/home)
- [Catalogo delle destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/overview)
- [Destinazione Marketo Engage](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [LinkedIn - Destinazione tipi di pubblico corrispondenti](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/social/linkedin)
- [Destinazione Salesforce CRM](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Destinazione Microsoft Dynamics 365](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)
- [Destinazione Amazon S3](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [Attivare i tipi di pubblico nelle destinazioni di streaming](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Attivare i tipi di pubblico nelle destinazioni batch](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Guardrail di attivazione](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/guardrails)

**Origini dati e connettori**

- [Panoramica sulle origini](https://experienceleague.adobe.com/it/docs/experience-platform/sources/home)
- [Connettore Marketo Engage](https://experienceleague.adobe.com/it/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Connettore Salesforce](https://experienceleague.adobe.com/it/docs/experience-platform/sources/connectors/crm/salesforce)

**Modellazione dati e identità**

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home)
- [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home)
- [Panoramica del profilo](https://experienceleague.adobe.com/it/docs/experience-platform/profile/home)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview)

**Governance dei dati e privacy**

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home)
- [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview)
- [Consenso e preferenze](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Monitoraggio e osservabilità**

- [Panoramica degli avvisi](https://experienceleague.adobe.com/it/docs/experience-platform/observability/alerts/overview)
- [Monitorare i flussi di dati di destinazione](https://experienceleague.adobe.com/it/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Monitorare i flussi di dati di origine](https://experienceleague.adobe.com/it/docs/experience-platform/sources/api-tutorials/monitor)
- [Dashboard utilizzo licenze](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Reporting e analisi**

- [Panoramica di CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-overview/cja-overview)
- [Panoramica delle connessioni](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-connections/overview)
- [Panoramica delle visualizzazioni dati](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-dataviews/data-views)

**Tutorial e guide**

- [Guida introduttiva a Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro)
- [Creare uno schema per le origini B2B](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/schemas/b2b)
- [Strumenti sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/sandbox-tooling-api/overview)
