---
user-guide-title: 'Customer Experience Orchestration: obiettivi aziendali, casi di utilizzo, diagrammi architettura e blueprint'
breadcrumb-title: Casi d'uso e blueprint
user-guide-description: Esplora gli obiettivi aziendali chiave, i modelli di casi d’uso e i casi d’uso del settore per Adobe Experience Platform e le applicazioni. I diagrammi e i progetti dell'architettura visiva forniscono riferimenti tecnici per l'integrazione del sistema, i flussi di dati e la progettazione delle soluzioni, collegando il valore aziendale all'implementazione.
product: adobe experience platform
mini-toc-levels: 3
role: Developer, User
nudge: orange
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 15%

---


# Blueprint per l’orchestrazione della customer experience {#architecture}

+ [Blueprint per l’orchestrazione della customer experience](/help/blueprints/overview.md)
+ Obiettivi aziendali chiave per AEP e app{#business-objectives}
  + [Panoramica](/help/blueprints/business-objectives/overview.md)
  + Acquisizione e crescita{#acquisition-growth}
    + [Acquisire nuovi clienti](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)
    + [Aumenta generazione lead](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)
    + [Aumenta il coinvolgimento del sito web](/help/blueprints/business-objectives/acquisition-growth/increase-website-engagement.md)
  + Ricavi e monetizzazione{#revenue-monetization}
    + [Aumentare i tassi di conversione](/help/blueprints/business-objectives/revenue-monetization/increase-conversion-rates.md)
    + [Aumento ricavi e vendite](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)
    + [Incrementa le attività di cross-selling e upselling](/help/blueprints/business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)
    + [Aumentare la fedeltà dei clienti e il valore del ciclo di vita](/help/blueprints/business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)
  + Costi ed efficienza{#cost-efficiency}
    + [Riduzione dei costi di acquisizione dei clienti](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)
    + [Ottimizzazione della spesa di marketing e del ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)
    + [Migliorare la qualità e la governance dei dati](/help/blueprints/business-objectives/cost-efficiency/improve-data-quality-governance.md)
    + [Consolidamento e modernizzazione della tecnologia di marketing](/help/blueprints/business-objectives/cost-efficiency/consolidate-modernize-marketing-technology.md)
  + Customer Experience{#customer-experience-objectives}
    + [Fornire esperienze cliente personalizzate](/help/blueprints/business-objectives/customer-experience/deliver-personalized-customer-experiences.md)
    + [Migliorare la fidelizzazione dei clienti](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)
    + [Migliorare l’onboarding dei clienti](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)
    + [Ripristino di carrelli e Percorsi abbandonati](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)
  + Analytics e approfondimenti{#analytics-insights}
    + [Migliorare analisi e reporting](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)
    + [Abilitare il processo decisionale basato sui dati](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)
    + [Migliorare l’attribuzione marketing](/help/blueprints/business-objectives/analytics-insights/improve-marketing-attribution.md)
  + Qualificazione e vendite (B2B){#qualification-sales-b2b}
    + [Migliorare la qualifica e la conversione dei lead](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)
    + [Migliorare il coinvolgimento dei clienti](/help/blueprints/business-objectives/qualification-sales-b2b/improve-customer-engagement.md)
+ Modelli di casi d’uso{#use-case-patterns}
  + [Panoramica](/help/blueprints/use-case-patterns/overview.md)
  + Creazione e attivazione di tipi di pubblico{#audience-building-activation}
    + [Audience Activation alle destinazioni](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md)
    + [Audience Collaboration con corrispondenza segmento](/help/blueprints/use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md)
    + [Inoltro degli eventi](/help/blueprints/use-case-patterns/audience-building-activation/event-forwarding.md)
    + [Ricerca profilo in tempo reale per supporto e vendite](/help/blueprints/use-case-patterns/audience-building-activation/real-time-profile-lookup.md)
    + [Data science personalizzata per l’arricchimento dei profili](/help/blueprints/use-case-patterns/audience-building-activation/data-science-profile-enrichment.md)
  + Personalizzazione{#personalization-patterns}
    + [Personalization Web visitatore anonimo](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md)
    + [Personalization Web/app visitatore noto](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md)
    + [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)
    + [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)
    + [Accesso profilo Edge per Personalization Web/Mobile](/help/blueprints/use-case-patterns/personalization/edge-profile-access.md)
    + [Condivisione di tipi di pubblico con Adobe Target](/help/blueprints/use-case-patterns/personalization/audience-sharing-with-target.md)
  + Gestione e orchestrazione delle campagne{#campaign-orchestration-patterns}
    + [Attivazione messaggi in uscita in batch](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md)
    + [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)
    + [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)
    + [Percorso cross-channel con decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)
    + [Orchestrazione in batch e messaggistica transazionale di Campaign v8](/help/blueprints/use-case-patterns/campaign-management-orchestration/campaign-v8-orchestration.md)
    + [Integrazione della messaggistica di terze parti con Journey Optimizer](/help/blueprints/use-case-patterns/campaign-management-orchestration/third-party-messaging.md)
  + Analisi{#analysis-patterns}
    + [Customer Analytics e Insight Generation](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md)
  + Attivazione e marketing B2B{#b2b-patterns}
    + [Audience Activation B2B](/help/blueprints/use-case-patterns/b2b/account-audience-activation.md)
    + [Acquisto di soluzioni di marketing e gestione dei Percorsi basate su gruppi](/help/blueprints/use-case-patterns/b2b/buying-group-marketing.md)
    + [Analisi B2B](/help/blueprints/use-case-patterns/b2b/account-analytics.md)
    + [Percorsi B2B con dati Marketo](/help/blueprints/use-case-patterns/b2b/marketo-data-journeys.md)
    + [AJO B2B - controller per supporti a pagamento](/help/blueprints/use-case-patterns/b2b/paid-media-orchestration.md)
    + [Acquisizione e creazione di Marketo e Workfront](/help/blueprints/use-case-patterns/b2b/campaign-intake-and-creation.md)
    + [Revisione e approvazione di Marketo e Workfront](/help/blueprints/use-case-patterns/b2b/campaign-review-and-approval.md)
  + Esperienza conversazionale{#conversational-experience-patterns}
    + [Esperienza conversazionale Brand Concierge](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md)
+ Esempi di casi d’uso di settore{#industry-use-cases}
  + [Catalogo dei casi d’uso](/help/blueprints/industry-use-cases/use-case-catalog.md)
  + [Settore automobilistico](/help/blueprints/industry-use-cases/automotive/automotive-overview.md)
  + [B2B](/help/blueprints/industry-use-cases/b2b/b2b-overview.md)
  + [Servizi finanziari](/help/blueprints/industry-use-cases/financial-services/financial-services-overview.md)
  + [Assistenza sanitaria](/help/blueprints/industry-use-cases/healthcare/healthcare-overview.md)
  + [Assicurazioni](/help/blueprints/industry-use-cases/insurance/insurance-overview.md)
  + [Media e intrattenimento](/help/blueprints/industry-use-cases/media-entertainment/media-entertainment-overview.md)
  + [Retail](/help/blueprints/industry-use-cases/retail/retail-overview.md)
  + [Telecomunicazioni](/help/blueprints/industry-use-cases/telecommunications/telecommunications-overview.md)
  + [Tecnologia](/help/blueprints/industry-use-cases/technology/technology-overview.md)
  + [Viaggi e ospitalità](/help/blueprints/industry-use-cases/travel-hospitality/travel-hospitality-overview.md)
+ Architettura - Diagrammi e blueprint{#architecture-diagrams}
  + Panoramiche dell’architettura{#architecture-overview}
    + [Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
    + [Experience Platform e applicazioni](/help/blueprints/experience-platform/platform-applications.md)
    + [Flusso di dati di Experience Platform](/help/blueprints/experience-platform/platform-data-flow.md)
    + [Guardrail di Experience Platform](/help/blueprints/experience-platform/guardrails.md)
    + Distribuzione{#deployment}
      + [Experience Platform Web SDK &amp; [!DNL Edge Network]](/help/blueprints/experience-platform/deployment/websdk.md)
      + [SDK delle applicazioni](/help/blueprints/experience-platform/deployment/appsdk.md)
  + Attivazione in base a pubblico e profili{#audience-activation}
    + [Basato su dispositivo: targeting del pubblico anonimo con Audience Manager](/help/blueprints/audience-activation/audience-manager.md)
    + Real-Time Customer Data Platform (RTCDP) {#known-customer-audience-activation}
      + [Attivazione del pubblico su destinazioni social e pubblicitarie](/help/blueprints/audience-activation/advertising-activation.md)
      + [Blueprint per l’attivazione di tipi di pubblico e profili nelle destinazioni Enterprise](/help/blueprints/audience-activation/enterprise-destinations.md)
      + [Accesso al profilo in tempo reale per scenari di supporto e vendita](/help/blueprints/audience-activation/customer-activity.md)
      + [Accesso in tempo reale al profilo edge per la personalizzazione web e mobile](/help/blueprints/audience-activation/real-time-lookup.md)
      + [Collaborazione del pubblico con Segment Match](/help/blueprints/audience-activation/segment-match.md)
      + [Personalizzazione del cliente nota con Target](/help/blueprints/audience-activation/rtcdp-target.md)
      + [Data science personalizzata per l’arricchimento dei profili](/help/blueprints/audience-activation/data-science.md)
  + Attivazione e marketing B2B{#b2b-activation}
    + [Panoramica](/help/blueprints/b2b/overview.md)
    + [Attivazione B2B](/help/blueprints/b2b/b2bactivation.md)
    + [Attivazione account B2B](/help/blueprints/b2b/b2b-account-activation.md)
    + [Acquisto di soluzioni di marketing e gestione dei percorsi basate su gruppi](/help/blueprints/b2b/b2b-buying-group-journeys.md)
    + [Percorsi B2B con dati Marketo](/help/blueprints/b2b/b2b-journeys-with-marketo.md)
    + [Controller supporti a pagamento B2B](/help/blueprints/b2b/ajo-b2b-paid-media-controller.md)
    + Blueprint per l’integrazione di Marketo Engage e Workfront{#marketo-engage-and-workfront-integration-blueprint}
      + [Panoramica](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md)
      + [Acquisizione e creazione](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md)
      + [Rivedi e approva](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md)
      + [Storie di successo dei clienti](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md)
  + Blueprint per{#customer-journey-analytics}
    + [Panoramica](/help/blueprints/customer-journey-analytics/overview.md)
    + [Customer Journey Analytics B2B](/help/blueprints/customer-journey-analytics/b2b-cja.md)
    + [Condivisione dei tipi di pubblico di CJA in RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
    + [CJA e Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
    + [Analisi dei dati e intelligence](/help/blueprints/customer-journey-analytics/analysis.md)
  + Percorsi di clienti{#customer-journeys}
    + [Panoramica](/help/blueprints/customer-journeys/overview.md)
    + Blueprint per{#journey-optimizer}
      + [Blueprint per](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md)
      + [percorsi AJO](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-journeys.md)
      + [Campagne AJO](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-campaigns.md)
      + [Messaggistica di terze parti](/help/blueprints/customer-journeys/journey-optimizer/3rd-party-messaging.md)
    + Gestione delle decisioni{#decision-management}
      + [Panoramica](/help/blueprints/customer-journeys/decision-management/decision-management-overview.md)
      + [Gestione delle decisioni su Edge](/help/blueprints/customer-journeys/decision-management/decision-management-edge.md)
      + [Gestione delle decisioni nel centro](/help/blueprints/customer-journeys/decision-management/decision-management-hub.md)
    + Campaign v8{#campaign-v8}
      + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8/campaign-v8-overview.md)
      + [Real-Time CDP con Adobe [!DNL Campaign] v8](/help/blueprints/customer-journeys/campaign-v8/rtcdp-and-campaign-v8.md)
      + [Journey Optimizer con Adobe Campaign v8](/help/blueprints/customer-journeys/campaign-v8/ajo-and-campaign-v8.md)
    + Blueprint obsoleti{#deprecated-blueprints}
      + Campaign Standard{#campaign-standard}
        + [[!DNL Campaign Standard]](https://experienceleague.adobe.com/it/docs/campaign-standard){target="_blank"}
        + [Real-Time CDP con Adobe [!DNL Campaign Standard]](https://experienceleague.adobe.com/it/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/get-started-sources-destinations)
      + Campaign v7{#campaign-v7}
        + [Campaign v7](/help/blueprints/customer-journeys/campaign-v7/campaign-v7-overview.md)

+ {hide-from-toc}Laboratori pratici{#labs}
  + [Panoramica pratica di Laboratori](/help/blueprints/labs/overview.md)
  + Workshop pratici{#workshops}
    + Nozioni di base di AEP{#aep-foundations}
      + [Panoramica](/help/blueprints/labs/aep-foundations/overview.md)
      + [Configurazione](/help/blueprints/labs/aep-foundations/setup.md)
      + Configurazione sandbox{#aep-sandbox}
        + [Installazione di Developer Console](/help/blueprints/labs/aep-foundations/sandbox-setup/developer-console-setup.md)
        + [Istruzioni di implementazione](/help/blueprints/labs/aep-foundations/sandbox-setup/deployment-instructions.md)
      + Installazione di Postman{#aep-postman}
        + [Installazione di Postman](/help/blueprints/labs/aep-foundations/postman-setup/postman-installation.md)
        + [File di ambiente](/help/blueprints/labs/aep-foundations/postman-setup/environment-file.md)
        + [Raccolta API](/help/blueprints/labs/aep-foundations/postman-setup/api-collection.md)
        + [Accesso alla sandbox](/help/blueprints/labs/aep-foundations/postman-setup/sandbox-access.md)
        + [Token di accesso](/help/blueprints/labs/aep-foundations/postman-setup/access-token.md)
      + Profilo cliente in tempo reale{#aep-rtcp}
        + [Lezioni](/help/blueprints/labs/aep-foundations/real-time-customer-profile/lectures.md)
        + Controllo del profilo{#aep-rtcp-inspect}
          + [Panoramica](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/overview.md)
          + [Nozioni di base sul profilo](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/profile-basics.md)
          + [Criteri di unione](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/merge-policies.md)
          + [API di profilo e identità](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/profile-and-identity-apis.md)
      + Metodologia LID{#aep-lid}
        + [Prerequisiti](/help/blueprints/labs/aep-foundations/lid-methodology/prerequisites.md)
        + [Etichetta](/help/blueprints/labs/aep-foundations/lid-methodology/label.md)
        + Identificare{#aep-lid-identify}
          + [Panoramica](/help/blueprints/labs/aep-foundations/lid-methodology/identify/overview.md)
          + [Parte 1 - Tipi di tabella rimanenti](/help/blueprints/labs/aep-foundations/lid-methodology/identify/part-1-remaining-table-types.md)
          + [Parte 2 - Campi Chiave](/help/blueprints/labs/aep-foundations/lid-methodology/identify/part-2-key-fields.md)
        + [Denormalizza](/help/blueprints/labs/aep-foundations/lid-methodology/denormalize.md)
      + Modello XDM{#aep-xdm}
        + [Lezioni](/help/blueprints/labs/aep-foundations/xdm-modeling/lectures.md)
        + Modellazione interfaccia utente{#aep-xdm-ui}
          + [Panoramica](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/overview.md)
          + [Accedi e sfoglia](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/login-and-browse.md)
          + [Oggetti modello standard](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/model-standard-objects.md)
          + [Oggetti personalizzati modello](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/model-custom-objects.md)
          + [Configura per profilo](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/configure-for-profile.md)
        + Modellazione API{#aep-xdm-api}
          + [Panoramica](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/overview.md)
          + Genera schema{#aep-xdm-api-build}
            + [Panoramica](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/overview.md)
            + [Recupera gruppi di campi standard](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/get-standard-field-groups.md)
            + [Creare gruppi di campi personalizzati](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/create-custom-field-groups.md)
            + [Ottieni classe profilo](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/get-profile-class.md)
            + [Crea schema](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/create-schema.md)
            + [Visualizza schema](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/view-schema.md)
            + [Modifica schema - Patch JSON](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/modify-schema-json-patch.md)
          + Contrassegna campi identità{#aep-xdm-api-identity}
            + [Panoramica](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/overview.md)
            + [Crea identità primaria](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/create-primary-identity.md)
            + [Crea altre identità](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/create-other-identities.md)
            + [Visualizza schema](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/view-schema.md)
          + Definire le relazioni{#aep-xdm-api-relationships}
            + [Panoramica](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/overview.md)
            + [Ottieni ID schema piano](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/get-plan-schema-id.md)
            + [Crea relazione schema](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/create-schema-relationship.md)
            + [Crea identità riferimento piano](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/create-plan-reference-identity.md)
            + [Visualizza schema](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/view-schema.md)
          + [Riassunto](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/recap.md)
        + Labs bonus{#aep-xdm-bonus}
          + [Panoramica](/help/blueprints/labs/aep-foundations/xdm-modeling/bonus-labs/overview.md)
          + [Automatizzare con API](/help/blueprints/labs/aep-foundations/xdm-modeling/bonus-labs/automate-with-apis.md)
      + Acquisizione di dati{#aep-ingestion}
        + [Lezioni](/help/blueprints/labs/aep-foundations/data-ingestion/lectures.md)
        + [Panoramica di Lab](/help/blueprints/labs/aep-foundations/data-ingestion/lab-overview.md)
        + [File di esempio](/help/blueprints/labs/aep-foundations/data-ingestion/sample-files.md)
        + Acquisizione in batch{#aep-ingestion-batch}
          + [Panoramica](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/overview.md)
          + [Crea flusso di dati](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/create-dataflow.md)
          + Mappatura dei dati{#aep-ingestion-batch-mapping}
            + [Panoramica](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/overview.md)
            + [Correggere le mappature passthrough](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/fix-passthrough-mappings.md)
            + [Campi calcolati](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/calculated-fields.md)
            + [Verifica set di mappatura finale](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/check-final-mapping-set.md)
          + [Esegui flusso di dati](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/run-dataflow.md)
          + [Errori di debug](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/debugging-errors.md)
          + [Creare un nuovo flusso di dati](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/create-a-new-dataflow.md)
          + [Correzione di errori](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/fixing-errors.md)
          + [Verifica e convalida](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/verification-and-validation.md)
        + Acquisizione flusso{#aep-ingestion-stream}
          + [Panoramica](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/overview.md)
          + [Configura Source](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/setup-source.md)
          + [Configura mappatura](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/configure-mapping.md)
          + [Verifica set di mappatura finale](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/check-final-mapping-set.md)
          + [Trasmetti un profilo](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/stream-a-profile.md)
          + [Verifica profilo acquisito](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/verify-ingested-profile.md)
          + [Monitoraggio e debug degli errori](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/monitoring-and-debugging-errors.md)
          + [Verifica e convalida](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/verification-and-validation.md)
        + Labs bonus{#aep-ingestion-bonus}
          + [Panoramica](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/overview.md)
          + [Correzione degli errori MAPPER per CreateDate](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/fix-mapper-errors-for-createdate.md)
          + [Trasmetti un evento ordine](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/stream-an-order-event.md)
          + Utilizzo della Data Landing Zone{#aep-ingestion-dlz}
            + [Panoramica](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/overview.md)
            + [Configura Source](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/setup-source.md)
            + [Crea mappature](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/create-mappings.md)
            + [Pianifica flusso di dati](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/schedule-dataflow.md)
            + [Ritentare un flusso di dati non riuscito](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/retry-a-failed-dataflow.md)
            + Carica ordini{#aep-ingestion-dlz-orders}
              + [Panoramica](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/overview.md)
              + [Configura Source](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/setup-source.md)
              + [Mappature iniziali](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/initial-mappings.md)
              + [Mappature copia oggetto](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/object-copy-mappings.md)
              + [Verifica e pianificazione del flusso di dati](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/verify-and-schedule-dataflow.md)
      + Segmentazione e attivazione{#aep-segmentation}
        + [Lezione](/help/blueprints/labs/aep-foundations/segmentation-and-activation/lecture.md)
        + Attivazione di Edge{#aep-segmentation-edge}
          + [Panoramica](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/overview.md)
          + [Creare un pubblico Edge](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/create-edge-audience.md)
          + [Inviare un evento Edge](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/send-an-edge-event.md)
          + Imposta inoltro eventi{#aep-segmentation-edge-ef}
            + [Panoramica](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/setup-event-forwarding/overview.md)
            + [Crea proprietà](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/setup-event-forwarding/create-property.md)
            + [Crea stream di dati](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/setup-event-forwarding/create-datastream.md)
      + Generazione di tipi di pubblico{#aep-audiences}
        + Caso d’uso 1: acquisizione{#aep-uc1}
          + [Panoramica](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/overview.md)
          + Configurare le destinazioni{#aep-uc1-destinations}
            + [Imposta destinazione Personalization personalizzata](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/configure-destinations/setup-custom-personalization-destination.md)
            + [Imposta destinazione di streaming](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/configure-destinations/setup-streaming-destination.md)
          + [Crea pubblico 1](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/build-audience-1.md)
          + [Genera pubblico 2](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/build-audience-2.md)
          + [Crea pubblico 3](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/build-audience-3.md)
          + [Inviare un evento Edge](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/send-an-edge-event.md)
          + [Revisione pensiero critico](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/critical-thinking-review.md)
        + Caso d&#39;uso 2: upselling{#aep-uc2}
          + [Panoramica](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/overview.md)
          + [Pre-lavoro](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/pre-work.md)
          + [Opzione 1 - Utilizzo dei tipi di pubblico per l’aggregazione](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/option-1-using-audiences-to-aggregate.md)
          + [Opzione 2 - Utilizzare gli aggregati preliminari](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/option-2-use-pre-aggregates.md)
          + [Revisione pensiero critico](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/critical-thinking-review.md)
        + Caso d’uso 3: sensibilizzazione{#aep-uc3}
          + [Panoramica](/help/blueprints/labs/aep-foundations/audience-building/use-case-3-outreach/overview.md)
          + [Caso di utilizzo 3 della build](/help/blueprints/labs/aep-foundations/audience-building/use-case-3-outreach/build-use-case-3.md)
          + [Revisione pensiero critico](/help/blueprints/labs/aep-foundations/audience-building/use-case-3-outreach/critical-thinking-review.md)
        + Labs bonus{#aep-audiences-bonus}
          + [Panoramica](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/overview.md)
          + [Invia evento ordine all&#39;hub](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/send-order-event-to-hub.md)
          + [Invia evento web all&#39;hub](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/send-web-event-to-hub.md)
          + [Monitorare l’evento](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/monitor-your-event.md)
    + Nozioni di base di AJO{#ajo-foundations}
      + [Panoramica](/help/blueprints/labs/ajo-foundations/overview.md)
      + [Configurazione](/help/blueprints/labs/ajo-foundations/setup.md)
      + Configurazione sandbox{#ajo-sandbox}
        + [Installazione di Developer Console](/help/blueprints/labs/ajo-foundations/sandbox-setup/developer-console-setup.md)
        + [Istruzioni di implementazione](/help/blueprints/labs/ajo-foundations/sandbox-setup/deployment-instructions.md)
      + Installazione di Postman{#ajo-postman}
        + [Installazione di Postman](/help/blueprints/labs/ajo-foundations/postman-setup/postman-installation.md)
        + [Importa file di ambiente](/help/blueprints/labs/ajo-foundations/postman-setup/import-environment-file.md)
        + [Importa raccolta API](/help/blueprints/labs/ajo-foundations/postman-setup/import-api-collection.md)
      + Elementi di base dell&#39;architettura{#ajo-architecture}
        + [Lezione](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/lecture.md)
        + Mappatura dei casi d’uso all’architettura{#ajo-architecture-mapping}
          + [Panoramica](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/overview.md)
          + [Introduzione al laboratorio](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/lab-introduction.md)
          + [Esercizio di laboratorio](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/lab-exercise.md)
          + [Recensione Lab](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/lab-review.md)
      + Archivi dati{#ajo-data-stores}
        + [Lezioni sul profilo cliente in tempo reale](/help/blueprints/labs/ajo-foundations/data-stores/real-time-customer-profile-lecture.md)
        + Profilo in azione{#ajo-profile}
          + [Panoramica](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/overview.md)
          + [Accedi e sfoglia](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/login-and-browse.md)
          + [Crea stream di dati](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/create-datastream.md)
          + [Inviare un evento web di Edge](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/send-an-edge-web-event.md)
          + [Convalida profilo su hub](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-profile-on-hub.md)
          + [Convalida profilo su Edge](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-profile-on-edge.md)
          + [Convalida evento su Data Lake](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-event-on-data-lake.md)
          + [Convalida istantanea profilo](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-profile-snapshot.md)
          + [Riepilogo](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/summary.md)
        + [Conferenza Relazionale Sullo Store](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-lecture.md)
        + Archivio relazionale in azione{#ajo-relational}
          + [Panoramica](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/overview.md)
          + [Sfoglia schemi](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/browse-schemas.md)
          + [Dimension di destinazione profilo](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/profile-target-dimension.md)
          + [Leggere un pubblico](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/read-an-audience.md)
          + [Riepilogo](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/summary.md)
        + Configurare I Canali E-Mail{#ajo-email}
          + [Panoramica](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/overview.md)
          + [Configura per profilo](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/configure-for-profile.md)
          + [Configura per relazionale](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/configure-for-relational.md)
          + [In attesa dello stato attivo](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/waiting-for-active-status.md)
      + Campagne orchestrate{#ajo-campaigns}
        + [Lezione sulla consegna dei messaggi](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-lecture.md)
        + Consegna dei messaggi in azione{#ajo-campaigns-delivery}
          + [Panoramica](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/overview.md)
          + [Creare una campagna](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/create-a-campaign.md)
          + [Creare un pubblico](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/build-an-audience.md)
          + [Aggiungi attività Fork](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/add-fork-activity.md)
          + [Aggiungi attività e-mail](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/add-email-activities.md)
          + [Testare la campagna](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/test-the-campaign.md)
          + [Riepilogo](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/summary.md)
        + [Lezione sui blocchi predefiniti del flusso di lavoro](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/workflow-building-blocks-lecture.md)
        + Lancio telefono di punta{#ajo-campaigns-flagship}
          + [Panoramica](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/overview.md)
          + [Configurare il canale SMS](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/configure-sms-channel.md)
          + [Creare una campagna orchestrata](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/create-an-orchestrated-campaign.md)
          + [Creare un pubblico](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/build-an-audience.md)
          + [Effettuare il forking del risultato](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/fork-the-result.md)
          + [Salvare il pubblico](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/save-the-audience.md)
          + [Filtrare le linee](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/filter-the-lines.md)
          + [Componi l’SMS](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/compose-the-sms.md)
          + [Eseguire il flusso di lavoro](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/run-the-workflow.md)
          + [Riepilogo](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/summary.md)
      + Percorsi{#ajo-journeys}
        + [Lezione](/help/blueprints/labs/ajo-foundations/journeys/lecture.md)
        + Eccitazione post-acquisto{#ajo-journeys-post-purchase}
          + [Panoramica](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/overview.md)
          + [Configura evento](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/configure-event.md)
          + [Configura azione personalizzata](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/configure-custom-action.md)
          + [Genera Percorso](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/build-journey.md)
          + [Percorso di prova](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/test-journey.md)
          + [Inviare un evento](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/send-an-event.md)
          + [Convalida evento acquisito](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/validate-event-ingested.md)
          + [Convalida Percorso](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/validate-journey.md)
          + [Riepilogo](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/summary.md)
      + Decisioni{#ajo-decisioning}
        + [Experience Edge](/help/blueprints/labs/ajo-foundations/decisioning/experience-edge.md)
        + Spiegazione delle decisioni{#ajo-decisioning-explained}
          + [Panoramica](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/overview.md)
          + [Introduzione](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/introduction.md)
          + [XDM elemento decisione](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/decision-item-xdm.md)
          + [Creazione elemento decisione](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/decision-item-creation.md)
          + [Raccolte](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/collections.md)
          + [Classificazione delle formule](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/ranking-formulas.md)
          + [Strategie di selezione](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/selection-strategies.md)
          + [Criteri di decisione](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/decision-policies.md)
          + [Guardrail, modelli AI Decisioning Futuro](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/guardrails-ai-models-decisioning-future.md)
        + Sfoglia abbandonata{#ajo-decisioning-abandoned}
          + [Panoramica](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/overview.md)
          + [Crea regola di decisione](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-decision-rule.md)
          + [Crea attributi offerta](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-offer-attributes.md)
          + [Crea elementi offerta](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-offer-items.md)
          + [Crea raccolta di offerte](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-offer-collection.md)
          + [Crea formula di classificazione](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-ranking-formula.md)
          + [Crea strategia di selezione](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-selection-strategy.md)
          + [Creare un canale di esperienza basato su codice](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-code-based-experience-channel.md)
          + [Creazione del Percorso](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-the-journey.md)
          + [Decisioning e CBE in azione](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/decisioning-and-cbes-in-action.md)
          + [Riepilogo](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/summary.md)
      + Authoring dei contenuti con IA{#ajo-content-ai}
        + [Lezione](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/lecture.md)
        + [Panoramica](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/overview.md)
        + [Gestione del marchio](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/brand-management.md)
        + [Creazione di frammenti di contenuto](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/building-content-fragments.md)
        + [Creazione di un modello di contenuto](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/building-content-template.md)
        + [Creazione dell’e-mail](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/creating-the-email.md)
        + [Assistente AI e Content Personalization](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/ai-assistant-and-content-personalization.md)
        + [Personalization e sperimentazione dei contenuti](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/personalization-and-content-experimentation.md)
        + [Simulazione dei contenuti](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/content-simulation.md)
        + [Allineamento marchio](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/brand-alignment.md)
        + [Verifica l’e-mail](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/test-the-email.md)
        + [Riepilogo](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/summary.md)
