---
user-guide-title: Blueprint per esperienze digitali
breadcrumb-title: Blueprint
user-guide-description: I blueprint sono implementazioni ripetibili che permettono di risolvere problemi di business noti e contengono diagrammi di architettura, considerazioni tecniche e collegamenti alla documentazione pertinente.
product: adobe experience platform
mini-toc-levels: 3
role: Architect, Developer, User
source-git-commit: 0dfe87cbffa265ee47873a91259a73dbc6c9dc76
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 97%

---


# Blueprint per esperienze digitali {#architecture}

+ [Panoramica](/help/blueprints/overview.md)
+ Blueprint per settori verticali {#vertical-blueprints}
   + [Panoramica](/help/blueprints/vertical-blueprints/overview.md)
   + [Abbigliamento](/help/blueprints/vertical-blueprints/apparel.md)
   + [Retail](/help/blueprints/vertical-blueprints/retail.md)
   + [Telecomunicazioni](/help/blueprints/vertical-blueprints/telecommunications.md)
   + [Viaggi e hospitality](/help/blueprints/vertical-blueprints/travel-hospitality.md)
+ Panoramica dell’architettura {#architecture-overview}
   + [Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
   + [Experience Platform e applicazioni](/help/blueprints/experience-platform/platform-applications.md)
   + [Flusso di dati in Experience Platform](/help/blueprints/experience-platform/platform-data-flow.md)
   + Implementazione {#deployment}
      + [Experience Platform Web SDK e rete Edge](/help/blueprints/data-ingestion/websdk.md)
      + [SDK delle applicazioni](/help/blueprints/data-ingestion/appsdk.md)
      + [Guardrail](/help/blueprints/experience-platform/deployment/guardrails.md)
+ Attivazione in base a pubblico e profili {#audience-activation}
   + [Panoramica](/help/blueprints/audience-activation/overview.md)
   + [Attivazione del pubblico con dati anonimi   (AAM)](/help/blueprints/audience-activation/anonymous.md)
   + Attivazione dei clienti noti (RTCDP) {#known-customer-audience-activation}
      + [Panoramica](/help/blueprints/audience-activation/known.md)
      + Attivazione per canali social e pubblicitari {#audience-activation}
         + [Attivazione in Facebook Custom Audiences](/help/blueprints/audience-activation/destinations/facebook.md)
         + [Attivazione per Google Customer Match](/help/blueprints/audience-activation/destinations/gcm.md)
      + [Attivazione per destinazioni basate su file e streaming verso soluzioni aziendali](/help/blueprints/audience-activation/enterprise-destinations.md)
      + [Hub delle attività dei clienti](/help/blueprints/audience-activation/customer-activity.md)
      + [Servizio Segment Match](/help/blueprints/audience-activation/segment-match.md)
   + [Attivazione con applicazioni Experience Cloud](/help/blueprints/audience-activation/platform-and-applications.md)
+ Attivazione e marketing B2B {#b2b-activation}
   + [Panoramica](/help/blueprints/b2b/overview.md)
   + [Attivazione B2B](/help/blueprints/b2b/b2bactivation.md)
+ Customer Journey Analytics {#customer-journey-analytics}
   + [Panoramica](/help/blueprints/customer-journey-analytics/overview.md)
   + [Condivisione di tipi di pubblico CJA in RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
   + [CJA e Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
+ Customer journey {#customer-journeys}
   + [Panoramica](/help/blueprints/customer-journeys/overview.md)
   + Journey Optimizer {#journey-optimizer}
      + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer.md)
      + Gestione delle decisioni {#decision-management}
         + [Panoramica](/help/blueprints/customer-journeys/decision_management/decision-management-overview.md)
         + [Gestione delle decisioni tramite rete Edge](/help/blueprints/customer-journeys/decision_management/decision-management-edge.md)
         + [Gestione delle decisioni tramite hub](/help/blueprints/customer-journeys/decision_management/decision-management-hub.md)
      + [Journey Optimizer con Adobe Campaign](/help/blueprints/customer-journeys/ajo-and-campaign.md)
      + [Messaggistica di terze parti](/help/blueprints/customer-journeys/3rd-party-messaging.md)
   + Campaign Standard {#campaign-standard}
      + [Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=it)
      + [Real-Time CDP con Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html?lang=it)
   + Campaign v8 {#campaign-v8}
      + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8.md)
      + [Real-Time CDP con Adobe Campaign v8](/help/blueprints/customer-journeys/rtcdp-and-campaign-v8.md)
      + [Journey Optimizer con Adobe Campaign v8](/help/blueprints/customer-journeys/ajo-and-campaign-v8.md)
   + Campaign v7 {#campaign-v7}
      + [Campaign v7](/help/blueprints/customer-journeys/campaign-v7.md)
      + [Real-Time CDP con Adobe Campaign   v7](/help/blueprints/customer-journeys/rtcdp-and-campaign.md)
      + [Journey Optimizer con Adobe Campaign v7](/help/blueprints/customer-journeys/ajo-and-campaign-v7.md)
+ Raccolta, accesso ed esportazione di dati{#data-ingestion}
   + [Panoramica](/help/blueprints/data-ingestion/overview.md)
   + [Preparazione e acquisizione dei dati](/help/blueprints/data-ingestion/ingestion.md)
   + [Accesso ed esportazione dei dati](/help/blueprints/data-ingestion/egress.md)
   + [Inoltro eventi](/help/blueprints/data-ingestion/server-side-collection.md)
   + [Raccolta dati per più sandbox](/help/blueprints/data-ingestion/multi-sandbox-data-collection.md)
+ Analisi dei dati, intelligence e AI/ML {#data-exploration}
   + [Panoramica](/help/blueprints/data-insights/overview.md)
   + [Analisi e intelligence dei dati](/help/blueprints/data-insights/analysis.md)
   + [Personalizzazione Data Science per l’arricchimento del profilo](/help/blueprints/data-insights/data-science.md)
+ Personalizzazione web e mobile {#web-personalization}
   + [Panoramica](/help/blueprints/web-personalization/overview.md)
   + [Personalizzazione basata sul comportamento   - Target](/help/blueprints/web-personalization/behavioral.md)
   + [Personalizzazione per clienti noti - Target e RTCDP](/help/blueprints/web-personalization/known-personalization.md)
   + [Gestione delle decisioni](/help/blueprints/web-personalization/decision-management-edge.md)