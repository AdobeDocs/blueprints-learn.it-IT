---
title: Offer Decisioning
description: Scopri come utilizzare la logica decisionale centralizzata per selezionare l’offerta o il contenuto migliore per un profilo tra canali diversi.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 8fd511b3-0200-41bf-aff1-e3f2a00a578e
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1640'
ht-degree: 5%

---

# Offer Decisioning

Questa guida descrive il modello di casi di utilizzo di Offer Decisioning, che utilizza [!DNL Adobe Journey Optimizer] (AJO) Decisioning e [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) per implementare una logica di selezione dell’offerta centralizzata che determina l’offerta migliore successiva per ogni profilo cliente su tutti i canali. È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono comprendere il funzionamento di questo modello, gli obiettivi aziendali supportati, i casi di utilizzo tattici che consente e le applicazioni Adobe coinvolte.

Il modello separa la decisione &quot;cosa mostrare&quot; dalla logica del canale &quot;dove mostrarlo&quot;, consentendo una selezione dell’offerta coerente e ottimizzata su e-mail, web, app mobile e qualsiasi altro punto di contatto. AJO Decisioning gestisce l’intero ciclo di vita delle offerte: creazione di offerte e gestione del catalogo, regole di idoneità (chi può vedere ogni offerta), strategie di classificazione (come selezionare tra le offerte idonee), posizionamenti (dove vengono visualizzate le offerte) e criteri decisionali (che associano tutto).

## Schema del caso d’uso

Questa sezione descrive il piano di esecuzione e la definizione del modello per offer decisioning.

**Offer Decisioning**

Utilizza la logica decisionale centralizzata per selezionare l’offerta o il contenuto migliore per un profilo tra canali diversi.

**Piano di esecuzione:** Valutazione del pubblico > Idoneità dell&#39;offerta > Strategia di classificazione > Esecuzione delle decisioni > Consegna > Generazione rapporti

## Panoramica del caso d’uso

Le organizzazioni devono spesso presentare a ciascun cliente l’offerta, la promozione o l’incentivo più pertinente al momento dell’interazione. Che l’interazione si verifichi in una campagna e-mail, su una home page del sito web, all’interno di un’app mobile o in un punto decisionale all’interno di un percorso in più passaggi, la sfida è la stessa: seleziona l’offerta ottimale da un catalogo di opzioni disponibili in base a chi sia il cliente, a cosa si qualifica e a quale offerta è più probabile che generi il risultato desiderato.

Offer Decisioning affronta questo problema centralizzando tutta la logica di selezione delle offerte nel motore di gestione delle decisioni di AJO. Invece di suddividere le assegnazioni delle offerte in singole campagne o canali, il motore decisionale valuta gli attributi di ciascun profilo, l’appartenenza al pubblico e i segnali contestuali per determinare l’offerta migliore in tempo reale. Questa centralizzazione assicura che lo stesso cliente riceva offerte coerenti e ottimizzate indipendentemente dal canale attraverso cui interagisce.

Questo modello si differenzia dalla personalizzazione web/app per visitatore noto per quanto riguarda l’ambito: le decisioni sull’offerta sono indipendenti dal canale e centralizzate, mentre la personalizzazione dei visitatori noti si concentra sulla personalizzazione della superficie digitale. Differisce dalle raccomandazioni comportamentali nel modello di catalogo: utilizza Offer Decisioning quando l’insieme di articoli idonei è disciplinato da regole aziendali, vincoli di idoneità o requisiti normativi (promozioni, prodotti finanziari, incentivi). Utilizza i consigli comportamentali quando il set di elementi è grande, in continua modifica e la selezione è guidata da segnali di affinità o similarità comportamentali (cataloghi di prodotti, librerie di contenuti).

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

**[Distribuisci esperienze cliente personalizzate](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
Personalizza contenuti, offerte e messaggi in base a preferenze, comportamenti e fasi del ciclo di vita individuali.
**KPI:** coinvolgimento, tassi di conversione, soddisfazione del cliente (CSAT)

**[Incrementa le vendite incrociate e incrementa i ricavi](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
Promuovere prodotti o servizi complementari e di alta qualità ai clienti esistenti in base al comportamento e alla cronologia degli acquisti.
**KPI:** % vendite incrociate/upselling, ricavi incrementali, valore ciclo di vita cliente

**[Aumenta la fedeltà dei clienti e il valore del ciclo di vita](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
Approfondisci le relazioni con i clienti e massimizza il valore a lungo termine tramite programmi di fidelizzazione, premi e coinvolgimento personalizzato.
**KPI:** Valore ciclo di vita cliente, mantenimento, upselling/cross-selling %

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

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni Adobe.

- **[!DNL Adobe Journey Optimizer] (AJO)** — Motore di gestione delle decisioni per la creazione di offerte, regole di idoneità, strategie di classificazione, posizionamenti e criteri di decisione; configurazione dei canali e authoring dei messaggi per la consegna delle offerte; esecuzione di campagne e percorsi
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Valutazione del pubblico per i segmenti di idoneità delle offerte; dati di profilo e attributi calcolati utilizzati nell&#39;idoneità e nella classificazione
- **[!DNL Adobe Experience Platform] (AEP)**: archivio profili unificato, risoluzione identità e base dati che supportano sia AJO che RT-CDP

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sui componenti utilizzati in questo modello di caso d’uso.

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

### Consegna delle offerte

- [Consegnare offerte nei messaggi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Distribuire le offerte tramite l’API Edge Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Distribuire le offerte tramite l’API Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/decisioning-api)

### Configurazione dei canali

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Impostazioni superficie e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delega sottodomini](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Configurare il canale SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### Authoring e personalizzazione dei messaggi

- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Anteprima e test del contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Campagne e percorsi

- [Introduzione alle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Creare una campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Introduzione ai percorsi](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)

### Sperimentazione sui contenuti

- [Introduzione all’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Creare un esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### Tipi di pubblico e segmentazione

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Profilo e identità

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Panoramica di Customer AI](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Modellazione e raccolta dati

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)

### Reporting e analisi

- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Governance dei dati e ciclo di vita

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview)
- [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Guardrail

- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### Tutorial

- [Guida introduttiva all’API di gestione delle decisioni](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/getting-started)
