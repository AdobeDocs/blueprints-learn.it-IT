---
title: Personalization Web/app visitatore noto
description: Scopri come distribuire contenuti, offerte o promozioni personalizzati a visitatori identificati in base al profilo in tempo reale e all’iscrizione ai segmenti.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 585adc0e-f528-4a09-b931-ef6b45fa8ec8
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1819'
ht-degree: 4%

---

# Personalizzazione web/app per visitatore noto

Questa guida descrive il caso d’uso di personalizzazione web/app per visitatore noto, che utilizza [!DNL Adobe Journey Optimizer] (AJO) e [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) per fornire contenuti personalizzati ai visitatori identificati su superfici digitali. È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono comprendere il funzionamento di questo modello, gli obiettivi aziendali supportati, i casi di utilizzo tattici che consente e le applicazioni Adobe coinvolte.

La personalizzazione web/app per visitatore noto è il modello di personalizzazione principale per le esperienze digitali autenticate. A differenza della personalizzazione anonima dei visitatori, che si basa esclusivamente su segnali comportamentali durante la sessione, questo modello sfrutta l’intero profilo unificato: dati comportamentali storici, appartenenza ai segmenti, livello di fedeltà, cronologia degli acquisti, fase del ciclo di vita, attributi calcolati e punteggi di tendenza. Supporta la personalizzazione tra le pagine web (tramite il canale web AJO), i messaggi in-app mobili e le schede di contenuto.

## Schema del caso d’uso

Questa sezione descrive il modello di base e il relativo piano di esecuzione.

**Personalizzazione web/app visitatore noto**

Distribuisci contenuti, offerte o promozioni personalizzati a un visitatore identificato in base al profilo in tempo reale e all’iscrizione ai segmenti su più superfici Web, in-app mobile e schede di contenuto.

**Piano di esecuzione:** Valutazione del pubblico > Personalization Decisioning > Configurazione superficie/canale > Consegna contenuto > Tracciamento impression > Reporting

## Panoramica del caso d’uso

Le organizzazioni con proprietà digitali autenticate (siti di e-commerce, portali bancari, servizi di abbonamento, programmi fedeltà, app mobili) devono fornire esperienze personalizzate che riflettano il rapporto di ciascun cliente con il marchio. Quando un visitatore effettua l’accesso o viene riconosciuto tramite la risoluzione di identità, la piattaforma può accedere al proprio profilo unificato completo e fornire contenuti personalizzati per attributi, comportamenti e preferenze specifici.

Questo modello riguarda lo scenario in cui un visitatore identificato arriva su una proprietà web o apre un’app mobile e il sistema deve determinare il contenuto, l’offerta o la promozione ottimale da visualizzare in base ai dati di profilo in tempo reale e all’iscrizione al pubblico. La decisione di personalizzazione avviene al limite in millisecondi, consentendo la distribuzione di contenuti al secondo secondario senza latenza percepibile.

Il modello supporta sia la personalizzazione deterministica (in cui il contenuto specifico è mappato su segmenti di pubblico specifici) che le decisioni dinamiche (in cui AJO Decisioning valuta le regole di idoneità e le strategie di classificazione per selezionare il contenuto ottimale per profilo). Si estende su più superfici digitali: pagine web, messaggi in-app per dispositivi mobili e schede di contenuto, consentendo una personalizzazione coerente nel percorso digitale del cliente.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### Fornire esperienze cliente personalizzate

Personalizza contenuti, offerte e messaggi in base a preferenze, comportamenti e fasi del ciclo di vita individuali. Per ulteriori informazioni, consulta [Distribuire esperienze cliente personalizzate](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md).

**KPI:** coinvolgimento, tassi di conversione, soddisfazione del cliente (CSAT)

### Aumentare il coinvolgimento con il sito Web

Migliora il tempo sul sito, le pagine per sessione e l’interazione con i contenuti web tramite esperienze rilevanti. Per ulteriori informazioni, vedere [Aumentare il coinvolgimento del sito Web](../../business-objectives/acquisition-growth/increase-website-engagement.md).

**KPI:** tempo su pagina (Web), coinvolgimento, tassi di conversione

### Aumentare il coinvolgimento con le app mobili

Promuovi l’utilizzo attivo giornaliero, l’adozione di funzioni e le conversioni in-app tramite esperienze in-app personalizzate.

**KPI:** coinvolgimento, mantenimento, tassi di conversione

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

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Adobe Journey Optimizer](AJO)**: configurazione del canale web, configurazione del canale in-app, configurazione del canale della scheda di contenuto, decisioning (selezione e classificazione dell&#39;offerta), authoring dei messaggi (creazione di contenuti personalizzati), esecuzione della campagna, sperimentazione dei contenuti e reporting
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — Valutazione del pubblico (edge, streaming e batch), ricerca dei profili in tempo reale tramite Edge Network, arricchimento dei profili con attributi calcolati e punteggi di propensione
- **[!DNL Adobe Experience Platform](AEP)** — Archivio profili, servizio Identity, Web SDK, Mobile SDK, configurazione dello stream di dati, consegna rete Edge

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sulle tecnologie e le configurazioni a cui si fa riferimento in questa guida.

### Personalizzazione del canale web

- [Introduzione al canale web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Creare esperienze web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Configurazione del canale web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)

### Canali in-app e schede di contenuto

- [Panoramica del canale in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [Prerequisiti per il canale in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [Creare messaggi in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [Canale scheda contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Configurazione scheda contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)
- [Creare schede di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/create-content-card)

### Gestione delle decisioni

- [Panoramica sulla gestione delle decisioni](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Creare i posizionamenti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Creare regole di decisione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
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
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilizzare i frammenti di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

### Tipi di pubblico e segmentazione

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Identità e profilo

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Regole di collegamento del grafo identità](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Panoramica del profilo](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Raccolta dati e SDK

- [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Installare Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Panoramica di Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Panoramica dell’API del server Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### Campagne e sperimentazione

- [Introduzione alle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Creare una campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Introduzione all’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Creare un esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapporto sull’esperimento sui contenuti](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### Attributi calcolati e arricchimento

- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Guida dell’interfaccia utente attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Panoramica di Customer AI](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Reporting e analisi

- [Rapporto live delle campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapporto globale della campagna](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Panoramica di CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Panoramica di Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Governance e privacy

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Panoramica di Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### Guardrail

- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Guardrail del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
