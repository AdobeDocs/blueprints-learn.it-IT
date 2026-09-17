---
title: Attivazione di tipi di pubblico e profili B2B
description: Distribuisci tipi di pubblico basati su account e persone con Real-Time Customer Data Platform B2B edition per l’attivazione tra canali e destinazioni.
solution: Real-Time Customer Data Platform
source-git-commit: 7f0b624616480cf563142c08eb0598d1dd55d551
workflow-type: tm+mt
source-wordcount: '1264'
ht-degree: 5%
---

# Attivazione di tipi di pubblico e profili B2B

Utilizza **Real-Time Customer Data Platform B2B edition** per riunire i dati di account, opportunità e persone in profili B2B unificati, quindi attiva sia i tipi di pubblico delle persone che quelli degli account tra le destinazioni, ad esempio LinkedIn, Marketo Engage e l&#39;archiviazione cloud. Questo blueprint descrive come progettare schemi B2B, creare tipi di pubblico con più entità ed esportarli per l&#39;attivazione su più canali e destinazioni, nonché per l&#39;orchestrazione e l&#39;analisi in applicazioni come **Journey Optimizer B2B edition** e **Customer Journey Analytics B2B edition**.

## Casi di utilizzo

- Crea tipi di pubblico di persone per il targeting e la personalizzazione tra canali basati su dati B2B che includono account, opportunità e lead.
- Crea tipi di pubblico con più entità che combinano gli attributi a livello di account e opportunità con il comportamento a livello di persona utilizzando un approccio **segmento di segmenti** (ad esempio, &quot;Persone che hanno visitato la pagina dei prezzi negli ultimi 3 giorni e sono responsabili decisionali nelle opportunità nella fase X per i conti nel settore Y&quot;).
- Attiva le persone e i tipi di pubblico dell’account nelle destinazioni di archiviazione cloud e Experience Platform, come Marketo Engage, LinkedIn Matched Audiences, Google Customer Match, DV360, The Trade Desk, Amazon Ads, Bombora e Demandbase, per il targeting, la personalizzazione, la distribuzione delle vendite e l’analisi.

## Applicazioni

- Real-Time Customer Data Platform B2B edition
- (Facoltativo) **Customer Journey Analytics B2B edition**
- (Facoltativo) **Journey Optimizer B2B edition**

## Modelli di integrazione

I modelli di integrazione B2B tipici per questo blueprint includono:

- **Destinazioni → B2B del coinvolgimento B2B e origini CRM → RTCDP**

  Il coinvolgimento B2B e i sistemi CRM come Marketo Engage, Salesforce e Microsoft Dynamics inviano lead/contatti, account e opportunità in **Real-Time CDP B2B edition** utilizzando gli schemi B2B standard. Da lì, il pubblico di persone e account viene attivato nelle destinazioni, tra cui:

  - Marketo Engage
  - LinkedIn / LinkedIn Tipi di pubblico corrispondenti
  - Google Customer Match e DV360
  - Il Trade Desk
  - Amazon Ads
  - Trade Desk CRM, Criteo, Bing e altre piattaforme pubblicitarie
  - Destinazioni di archiviazione cloud come Amazon S3, ADLS e Snowflake per l’utilizzo a valle

- **Intento B2B e origini eventi → tipi di pubblico → B2B di RTCDP → destinazioni**

  Le origini degli intenti B2B e degli eventi, come Bombora Intent, Demandbase Intent, PathFactory e RainFocus, inviano eventi di intento e coinvolgimento in RTCDP B2B. Questi eventi sono mappati su schemi B2B standard e utilizzati per creare persone e tipi di pubblico di account che possono essere attivati nelle destinazioni pubblicitarie e di marketing.

È possibile utilizzare diverse origini dati B2B per mappare i dati di account, lead, opportunità e persona su B2B edition di Real-Time Customer Data Platform utilizzando gli schemi e le relazioni **B2B standard**.

## Architettura

<img src="assets/b2b-audience-profile-activation.png" alt="Architettura di riferimento per il blueprint di Audience B2B e Attivazione profilo" style="border:1px solid #4a4a4a"  width="100%" />

## Guardrail

Durante la progettazione di tipi di pubblico e profili B2B, consulta le seguenti protezioni e documentazione di idoneità:

- [Guardrail per Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails?lang=en)
- [Casi di utilizzo della segmentazione per Real-Time CDP B2B edition](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/segmentation/b2b)
- [Guardrail di profilo e segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)
- [Aggiornamento dei criteri di idoneità alla segmentazione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/eligibility-criteria-update)

### Supporto di più istanze e organizzazioni IMS

Di seguito sono descritti i pattern supportati per la mappatura delle istanze di Experience Platform e Marketo Engage.

#### Marketo come origine dati per Experience Platform

- Sono supportate più istanze di Marketo Engage in una sola istanza di Experience Platform.
- Non è supportata una istanza di Marketo Engage per più istanze di Experience Platform.
- È supportata una istanza di Marketo Engage per una istanza di Experience Platform e più sandbox.

#### Marketo come destinazione di Experience Platform

- Experience Platform in molte istanze Marketo Engage è supportato.
- Sono supportate molte istanze di Experience Platform in un’istanza di Marketo Engage.

#### Guardrail di segmentazione e profilo di Experience Platform

Consulta il profilo Experience Platform e i guardrail di segmentazione qui: [Guardrail di profilo e segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails).

I segmenti che includono entità B2B come conti, lead o opportunità si basano su relazioni tra più entità e vengono valutati in **batch**. Al contrario, **la segmentazione in streaming** è supportata per tipi di pubblico limitati a persone ed eventi che non incorporano entità B2B. Per scenari di attivazione B2B quasi in tempo reale, considera l’utilizzo di tipi di pubblico B2B valutati in batch come input per tipi di pubblico in streaming o edge, se supportato.

#### Experience Platform - Connettore Marketo Engage Source

- Fai riferimento alla documentazione [qui](https://experienceleague.adobe.com/it/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo).

#### Experience Platform - Connettore di destinazione Marketo

- Fai riferimento alla documentazione [qui](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/adobe/marketo-engage-connection).

#### Guardrail per destinazione

- Per istruzioni specifiche su ciascuna destinazione, consulta la documentazione di destinazione: [Guardrail di destinazione](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/guardrails).
- Per destinazioni pubblicitarie come Facebook, Google Customer Match e DV360, Microsoft Bing, The Trade Desk, Amazon Ads, Bombora, Demandbase e altri, assicurati che gli identificatori scelti nello schema e nella strategia di identità (e-mail, ID mobile advertising, campi indirizzo, ID account) siano allineati con le funzionalità di mappatura e le identità supportate per tali destinazioni.

## Fasi di implementazione

Per informazioni su come implementare e configurare B2B edition di Real-Time Customer Data Platform, vedere la documentazione di Real-Time CDP B2B edition: [B2B edition di Real-Time Customer Data Platform](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview).

Sono comuni due modelli di implementazione:

- Acquisire dati e profili B2B da Marketo Engage (e dal CRM connesso) in RTCDP B2B edition.
- Acquisire dati B2B direttamente dal sistema CRM o da altri sistemi B2B in RTCDP B2B edition utilizzando i connettori di origine pertinenti.

Come parte degli aggiornamenti dell’architettura B2B di RTCDP, alcuni modelli utilizzati in precedenza sono ora obsoleti per le entità B2B. Per ulteriori dettagli, consulta la documentazione dettagliata [qui](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-architecture-upgrade).

## Considerazioni sull’implementazione

Considerazioni chiavi e configurazioni del blueprint.

- Integrazione di **CRM con e senza Marketo**

  - Se l’implementazione utilizza Marketo Engage come origine e Marketo Engage è connesso al sistema di gestione delle relazioni con i clienti, i dati del sistema di gestione delle relazioni con i clienti sincronizzati in Marketo (ad esempio, lead/contatti, account, opportunità) confluiranno in RTCDP B2B edition tramite il connettore di origine di Marketo.
  - Se esistono tabelle o attributi CRM aggiuntivi che non vengono passati tramite Marketo (ad esempio, oggetti personalizzati o campi aggiuntivi), connetti l’origine CRM direttamente ad Experience Platform utilizzando i connettori di origine CRM e mappa tali tabelle agli schemi e alle relazioni B2B standard.
  - Progetta l’acquisizione di CRM e Marketo insieme per evitare rappresentazioni duplicate o in conflitto di entità B2B in RTCDP B2B e garantire che tutte le entità B2B siano conformi agli schemi standard.

## Documentazione correlata

- [B2B edition di Real-Time Customer Data Platform](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
- [Guida introduttiva di Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial?lang=en)
- [Guardrail per Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails?lang=en)
- [Schemi in Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/schemas/b2b)
- [Aggiornamento dell&#39;architettura a Real-Time CDP B2B edition](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-architecture-upgrade)
- [Adobe Experience Platform](https://experienceleague.adobe.com/it/docs/experience-platform)
- [Marketo Engage](https://experienceleague.adobe.com/it/docs/marketo/using/home)
- [Adobe Experience Platform - Connettore Marketo Source](https://experienceleague.adobe.com/it/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Adobe Experience Platform - Connettore di destinazione Marketo](https://experienceleague.adobe.com/it/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-platform-segment-to-a-marketo-static-list)
- [Guardrail per destinazione](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/guardrails)
