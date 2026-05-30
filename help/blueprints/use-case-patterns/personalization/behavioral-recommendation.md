---
title: Consigli comportamentali
description: Scopri come generare consigli su elementi e contenuti utilizzando strategie di selezione e modelli di classificazione.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: db16e773-e0da-46c4-9fa5-d16f04feb46b
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 5%

---

# Raccomandazioni comportamentali

Questa guida descrive il modello di caso d’uso per i consigli comportamentali, che utilizza [!DNL Adobe Journey Optimizer] (AJO) Decisioning, [!DNL Real-Time Customer Data Platform] (RT-CDP) e [!DNL Adobe Experience Platform] (AEP) per fornire esperienze di consigli personalizzate tra canali web, app mobili ed e-mail. È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono comprendere il funzionamento di questo modello, gli obiettivi aziendali supportati, i casi di utilizzo tattici che consente e le applicazioni Adobe coinvolte.

La funzione Consigli comportamentali genera consigli a livello di elemento o di contenuto utilizzando segnali comportamentali (visualizzazioni di prodotto, acquisti, interazioni di contenuto, query di ricerca) combinati con strategie di selezione e modelli di classificazione di AJO Decisioning. A differenza di offer decisioning, che governa un set limitato di offerte, promozioni o incentivi utilizzando regole di idoneità e vincoli di business, questo modello opera su cataloghi di articoli di grandi dimensioni in continua evoluzione (prodotti, articoli, video) in cui la selezione è guidata da segnali di affinità comportamentale piuttosto che da idoneità regolamentata.

## Schema del caso d’uso

**Consigli comportamentali**

Genera consigli a livello di elemento o di contenuto in base ai segnali comportamentali, utilizzando le strategie di selezione di AJO Decisioning e i modelli di classificazione per distribuire i contenuti contestuali.

**Piano di esecuzione:** acquisizione segnale comportamentale > Valutazione strategia di decisione > Consegna consigli > Reporting

## Panoramica del caso d’uso

Le organizzazioni con cataloghi di prodotti, librerie di contenuti o librerie multimediali devono rendere visibili a ogni visitatore gli elementi più rilevanti in base alla cronologia comportamentale e all’attività durante la sessione. Che si tratti di un carosello &quot;consigliato per te&quot; su una pagina home, di un widget di cross-selling su una pagina di dettagli del prodotto o di consigli di prodotto incorporati in una campagna e-mail, la sfida di fondo è la stessa: abbinare il profilo comportamentale di ogni visitatore agli elementi più rilevanti di un catalogo, quindi fornire tali consigli nel canale giusto al momento giusto.

Questo modello affronta tale sfida acquisendo segnali comportamentali in tempo reale tramite [!DNL Web SDK] o [!DNL Mobile SDK], elaborandoli tramite strategie di selezione di AJO Decisioning che combinano gli attributi degli elementi con il contesto comportamentale e distribuendo gli elementi consigliati tramite canali web, in-app o e-mail. I modelli di classificazione possono essere basati su formule (ad esempio, in base al punteggio di affinità tra categorie) o classificati in base all’intelligenza artificiale (ad esempio, modello di consigli personalizzato). Il modello gestisce anche scenari di avvio a freddo per nuovi visitatori senza cronologia comportamentale configurando consigli di fallback.

Il pubblico di destinazione di questo modello include i team di merchandising di e-commerce, i team di personalizzazione dei contenuti e i team di esperienza digitale che desiderano migliorare il coinvolgimento, la conversione e il valore medio dell’ordine attraverso consigli personalizzati basati sul comportamento effettivo degli utenti.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### [Incrementa le vendite incrociate e incrementa i ricavi](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)

Promuovere prodotti o servizi complementari e di alta qualità ai clienti esistenti in base al comportamento e alla cronologia degli acquisti.

**KPI:** % vendite incrociate/upselling, ricavi incrementali, valore ciclo di vita cliente

### [Aumentare i tassi di conversione](../../business-objectives/revenue-monetization/increase-conversion-rates.md)

Migliora la percentuale di visitatori e potenziali clienti che completano le azioni desiderate, ad esempio acquisti, iscrizioni o invii di moduli.

**KPI:** Tassi di conversione, Conversione lead, Costo per lead

### [Distribuisci esperienze cliente personalizzate](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

Personalizza contenuti, offerte e messaggi in base a preferenze, comportamenti e fasi del ciclo di vita individuali.

**KPI:** coinvolgimento, tassi di conversione, soddisfazione del cliente (CSAT)

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

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Adobe Journey Optimizer] (AJO) Decisioning** — Strategie di selezione, modelli di classificazione, cataloghi di elementi e criteri decisionali che valutano i segnali comportamentali e restituiscono gli elementi più rilevanti per ogni visitatore
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Accumulo dei dati del profilo comportamentale, valutazione del pubblico per l&#39;ambito dei consigli e attributi calcolati per il punteggio di affinità comportamentale
- **[!DNL Adobe Experience Platform] (AEP)** — Acquisizione di eventi comportamentali tramite [!DNL Web SDK] e [!DNL Mobile SDK], elaborazione di [!DNL Edge Network], gestione dello schema XDM per i dati evento e catalogo

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sulle tecnologie e le funzionalità utilizzate in questo modello.

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
- [Distribuire le offerte tramite l’API Edge Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)

### Raccolta dati e Web/Mobile SDK

- [Panoramica di Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/home)
- [Installare Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/install/overview)
- [Panoramica di Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/it/docs/experience-platform/datastreams/configure)
- [Panoramica dell’API del server Edge Network](https://experienceleague.adobe.com/it/docs/experience-platform/edge-network-server-api/overview)

### XDM e modellazione dati

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home)
- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/schema/composition)
- [Creare un set di dati](https://experienceleague.adobe.com/it/docs/experience-platform/catalog/datasets/create)
- [Definire una relazione tra due schemi](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/tutorials/relationship-api)

### Identità e profilo

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home)
- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview)
- [Panoramica del profilo cliente in tempo reale](https://experienceleague.adobe.com/it/docs/experience-platform/profile/home)

### Tipi di pubblico e segmentazione

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/edge-segmentation)

### Attributi calcolati e arricchimento dei profili

- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview)
- [Guida dell’interfaccia utente attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/ui)
- [Panoramica di Customer AI](https://experienceleague.adobe.com/it/docs/experience-platform/intelligent-services/customer-ai/overview)

### Configurazione dei canali

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Impostare le superfici di canale](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delega sottodomini](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)

### Authoring e personalizzazione dei messaggi

- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### Reporting e analisi

- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilizzare Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Panoramica di CJA](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-overview/cja-overview)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-workspace/home)
- [Panoramica delle metriche calcolate](https://experienceleague.adobe.com/it/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

### Governance dei dati e ciclo di vita

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home)
- [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview)
- [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/it/docs/experience-platform/data-lifecycle/home)
- [Scadenze set di dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-lifecycle/ui/dataset-expiration)

### Monitoraggio e osservabilità

- [Panoramica di Observability Insights](https://experienceleague.adobe.com/it/docs/experience-platform/observability/home)
- [Panoramica degli avvisi](https://experienceleague.adobe.com/it/docs/experience-platform/observability/alerts/overview)

### Guardrail

- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/get-started/guardrails)
- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)
- [Guardrail di acquisizione](https://experienceleague.adobe.com/it/docs/experience-platform/ingestion/guardrails)
- [Guardrail del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/guardrails)

### Tutorial e guide

- [Panoramica sulle origini](https://experienceleague.adobe.com/it/docs/experience-platform/sources/home)
- [Panoramica sui tag](https://experienceleague.adobe.com/it/docs/experience-platform/tags/home)
- [Gruppo di campi Consenso e preferenze](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/field-groups/profile/consents)
