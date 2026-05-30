---
title: Personalization Web visitatore anonimo
description: Scopri come distribuire contenuti web personalizzati a visitatori non identificati in base a segnali comportamentali durante la sessione.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: e2446801-ffce-40e6-bfe9-abec623c9201
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1739'
ht-degree: 4%

---

# Personalizzazione web visitatore anonimo

Questa guida descrive il modello di caso d’uso per la personalizzazione web del visitatore anonimo, che utilizza [!DNL Adobe Journey Optimizer] (AJO), [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) e [!DNL Adobe Experience Platform] (AEP) per fornire contenuti web personalizzati a visitatori anonimi (non identificati) in base a segnali comportamentali durante la sessione. È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono comprendere il funzionamento di questo modello, gli obiettivi aziendali supportati, i casi di utilizzo tattici che consente e le applicazioni Adobe coinvolte.

Il modello funziona con dati limitati, solo ciò che può essere osservato nella sessione corrente e qualsiasi profilo edge anonimo accumulato da visite precedenti con lo stesso dispositivo o cookie. Questo lo rende adatto per la personalizzazione top-of-funnel in cui il visitatore non ha un account o non è stato autenticato.

## Schema del caso d’uso

Di seguito sono descritti il modello di base e il piano di esecuzione per questo caso d’uso.

**Visitatore anonimo Web Personalization**

Distribuisci contenuti personalizzati in base a segnali comportamentali durante la sessione per visitatori non identificati tramite il canale web AJO.

**Piano di esecuzione:** Configurazione superficie web > Valutazione regole comportamentali > Consegna contenuto > Tracciamento impression > Reporting

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

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Adobe Journey Optimizer](AJO)**: configurazione della superficie del canale web, authoring dei contenuti (esperienze web e basate su codice), esecuzione di campagne, sperimentazione dei contenuti (test A/B), decisioning (selezione dinamica dei contenuti) e reporting
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — Segmentazione di Edge per la valutazione del pubblico in tempo reale basata su segnali comportamentali durante la sessione; gestione anonima dei profili edge
- **[!DNL Adobe Experience Platform](AEP)** — [!DNL Web SDK] per la raccolta di segnali comportamentali, [!DNL Edge Network] per il routing dei dati in tempo reale e la consegna della personalizzazione, configurazione dello stream di dati

## Architettura

La seguente architettura di riferimento illustra come i segnali dei visitatori anonimi vengono raccolti al limite, valutati in base alle regole di pubblico e utilizzati per fornire contenuti personalizzati.

![Architettura di riferimento per l&#39;attivazione e la personalizzazione del pubblico anonimo](/help/blueprints/audience-activation/assets/anonymous_activation.png)

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
