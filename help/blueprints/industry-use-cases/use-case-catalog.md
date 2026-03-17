---
title: Catalogo dei casi d’uso
description: Sfoglia i casi d’uso del settore in base a criteri verticali, al livello di maturità o al modello di implementazione per trovare il punto di partenza giusto per il tuo percorso Adobe Experience Platform.
doc-type: overview-page
exl-id: 7a3c2f1e-9b4d-4e6a-8f5c-2d1b3a4e7c9f
source-git-commit: 8ad59ff130dae13553f10049eb685cf557a73ead
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 6%

---

# Catalogo dei casi d’uso

Esplora i casi d&#39;uso del settore per [!DNL Adobe Experience Platform] e le applicazioni. Sfoglia per settore per visualizzare i casi d’uso per verticale, per livello di maturità per trovare il punto di partenza giusto per la tua organizzazione o per modello di implementazione per capire quale approccio tecnico si adatta alle tue esigenze.

Ogni caso d’uso è collegato a linee guida dettagliate sull’implementazione tramite un modello di caso d’uso che descrive la catena delle funzioni, i punti decisionali e i passaggi di configurazione necessari per dare vita al caso d’uso.

## Sfoglia per settore

>[!BEGINTABS]

>[!TAB Vendita al dettaglio]

Le organizzazioni di vendita al dettaglio utilizzano [!DNL Adobe Experience Platform] per unificare i dati dei clienti provenienti da negozi online, luoghi fisici e programmi fedeltà in un&#39;unica vista di ogni acquirente.

| | Caso d’uso | Descrizione | Maturità | Pattern |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="Consigli di prodotto personalizzati" width="40"> | [Consigli di prodotto personalizzati](retail/retail-overview.md#personalized-product-recommendations) | Mostra prodotti personalizzati in base alla cronologia di navigazione e acquisto | [!BADGE Emergente]{type=Informative} | [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="Carrello abbandonato" width="40"> | [Ripristino e-mail carrello abbandonato](retail/retail-overview.md#abandoned-cart-email-recovery) | Invia promemoria personalizzati per i carrelli abbandonati | [!BADGE Fondamentale]{type=Neutral} | [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="Urgenza inventario" width="40"> | [Campagne Di Urgenza Basate Sull&#39;Inventario](retail/retail-overview.md#inventory-based-urgency-campaigns) | Attiva avvisi in tempo reale quando l’inventario dei prodotti è basso | [!BADGE Fondamentale]{type=Neutral} | [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="Vendita incrociata" width="40"> | [Consigli per vendite incrociate e upselling](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | Visualizzare i prodotti di cross-selling e upselling pertinenti al momento del pagamento e tramite e-mail | [!BADGE Avanzate]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="Serie di benvenuto" width="40"> | [Nuova serie di benvenuto per il cliente](retail/retail-overview.md#new-customer-welcome-series) | Automatizzare una serie di benvenuto con più e-mail con consigli personalizzati | [!BADGE Emergente]{type=Informative} | [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="Riduzione prezzo" width="40"> | [Avvisi di riduzione prezzo](retail/retail-overview.md#price-drop-alerts) | Notifica ai clienti il calo del prezzo per la lista dei desideri o gli articoli visualizzati | [!BADGE Fondamentale]{type=Neutral} | [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="Rifornimento" width="40"> | [Promemoria rifornimento](retail/retail-overview.md#replenishment-reminders) | Inviare promemoria automatici per i prodotti di consumo regolarmente acquistati | [!BADGE Emergente]{type=Informative} | [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="Pagine categoria" width="40"> | [Pagine di categorie personalizzate](retail/retail-overview.md#personalized-category-pages) | Riordina dinamicamente le pagine delle categorie in base alle preferenze di ciascun cliente | [!BADGE Emergente]{type=Informative} | [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="Post-acquisto" width="40"> | [Campagne Di Follow-Up Post-Acquisto](retail/retail-overview.md#post-purchase-follow-up-campaigns) | Invia suggerimenti per le cure, rivedi le richieste e i relativi suggerimenti di prodotto | [!BADGE Emergente]{type=Informative} | [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [Offerte esclusive per i clienti VIP](retail/retail-overview.md#vip-customer-exclusive-offers) | Offrire offerte esclusive e accesso anticipato a clienti di alto valore | [!BADGE Avanzate]{type=Caution} | [Percorso cross-channel con decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [Notifiche esaurite](retail/retail-overview.md#out-of-stock-notifications) | Avvisa i clienti quando i prodotti esauriti diventano disponibili | [!BADGE Fondamentale]{type=Neutral} | [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [Personalization di prova social](retail/retail-overview.md#social-proof-personalization) | Visualizzare recensioni e valutazioni personalizzate in base al profilo del cliente | [!BADGE Emergente]{type=Informative} | [Web visitatore conosciuto/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

>[!TAB Servizi finanziari]

I casi di utilizzo dei servizi finanziari saranno presto disponibili. [Visualizza i casi d&#39;uso correnti di Financial Services](financial-services/financial-services-overview.md).

>[!TAB Sanità]

I casi di utilizzo del sistema sanitario saranno presto disponibili. [Visualizza i casi d&#39;uso attuali del settore sanitario](healthcare/healthcare-overview.md).

>[!TAB Automotive]

I casi d’uso relativi al settore automobilistico saranno presto disponibili. [Visualizza casi d&#39;uso automobilistici correnti](automotive/automotive-overview.md).

>[!TAB Viaggi e ospitalità]

I casi di utilizzo relativi a viaggi e ospitalità saranno presto disponibili. [Visualizza i casi d&#39;uso correnti relativi a viaggi e ospitalità](travel-hospitality/travel-hospitality-overview.md).

>[!TAB Telecomunicazioni]

I casi di utilizzo delle telecomunicazioni saranno presto disponibili. [Visualizza i casi d&#39;uso delle telecomunicazioni correnti](telecommunications/telecommunications-overview.md).

>[!TAB Media e intrattenimento]

I casi d’uso per contenuti multimediali e intrattenimento saranno presto disponibili. [Visualizza casi di utilizzo correnti per contenuti multimediali e intrattenimento](media-entertainment/media-entertainment-overview.md).

>[!TAB Assicurazione]

I casi di utilizzo assicurativi saranno presto disponibili. [Visualizza casi di utilizzo assicurativi correnti](insurance/insurance-overview.md).

>[!TAB B2B]

I casi di utilizzo B2B saranno presto disponibili. [Visualizza casi d&#39;uso B2B correnti](b2b/b2b-overview.md).

>[!ENDTABS]

## Sfoglia per livello di maturità

>[!BEGINTABS]

>[!TAB Fondamentale]

Modelli di base e collaudati con consegna su un singolo canale. Punti di partenza ideali per le organizzazioni che iniziano il percorso [!DNL Experience Platform].

| | Caso d’uso | Settore | Impatto aziendale | Pattern |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="Carrello abbandonato" width="40"> | [Ripristino e-mail carrello abbandonato](retail/retail-overview.md#abandoned-cart-email-recovery) | Retail | 25-35% tasso di recupero del carrello | [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="Urgenza inventario" width="40"> | [Campagne Di Urgenza Basate Sull&#39;Inventario](retail/retail-overview.md#inventory-based-urgency-campaigns) | Retail | Aumento del 30-40% nella conversione | [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="Riduzione prezzo" width="40"> | [Avvisi di riduzione prezzo](retail/retail-overview.md#price-drop-alerts) | Retail | Tasso di conversione del 20-30% | [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [Notifiche esaurite](retail/retail-overview.md#out-of-stock-notifications) | Retail | Tasso di conversione 40-50% | [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |

>[!TAB Emergente]

Modelli multicanale e in più passaggi che si basano su funzionalità fondamentali con personalizzazione basata sull’intelligenza artificiale e percorsi orchestrati.

| | Caso d’uso | Settore | Impatto aziendale | Pattern |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="Consigli di prodotto" width="40"> | [Consigli di prodotto personalizzati](retail/retail-overview.md#personalized-product-recommendations) | Retail | Aumento del 20-30% del CTR, aumento della conversione del 15-25% | [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="Pagine categoria" width="40"> | [Pagine di categorie personalizzate](retail/retail-overview.md#personalized-category-pages) | Retail | Aumento del 25-35% del coinvolgimento | [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="Serie di benvenuto" width="40"> | [Nuova serie di benvenuto per il cliente](retail/retail-overview.md#new-customer-welcome-series) | Retail | Tasso di coinvolgimento del 40-50% | [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="Rifornimento" width="40"> | [Promemoria rifornimento](retail/retail-overview.md#replenishment-reminders) | Retail | 30-40% di acquisti ripetuti | [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="Post-acquisto" width="40"> | [Campagne Di Follow-Up Post-Acquisto](retail/retail-overview.md#post-purchase-follow-up-campaigns) | Retail | 15-20% tasso di revisione, 10-15% acquisto ripetuto | [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [Personalization di prova social](retail/retail-overview.md#social-proof-personalization) | Retail | Aumento del tasso di conversione del 10-15% | [Web visitatore conosciuto/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

>[!TAB Avanzate]

Orchestrazione cross-channel con decisioni in tempo reale e selezione di offerte basate sull’intelligenza artificiale per esperienze cliente più sofisticate.

| | Caso d’uso | Settore | Impatto aziendale | Pattern |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="Vendita incrociata" width="40"> | [Consigli per vendite incrociate e upselling](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | Retail | Aumento di $25-$75 in AOV, incremento del 10-15% dei ricavi | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| | [Offerte esclusive per i clienti VIP](retail/retail-overview.md#vip-customer-exclusive-offers) | Retail | Percentuale di coinvolgimento del 50-70% da VIP | [Percorso cross-channel con decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!ENDTABS]

## Sfoglia per modello di implementazione

>[!BEGINTABS]

>[!TAB Gestione e orchestrazione campagna]

### Messaggi attivati da eventi

Rispondi agli eventi comportamentali in tempo reale con messaggi tempestivi su un singolo canale.

| | Caso d’uso | Settore | Maturità | Impatto aziendale |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="Carrello abbandonato" width="40"> | [Ripristino e-mail carrello abbandonato](retail/retail-overview.md#abandoned-cart-email-recovery) | Retail | [!BADGE Fondamentale]{type=Neutral} | 25-35% tasso di recupero del carrello |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="Urgenza inventario" width="40"> | [Campagne Di Urgenza Basate Sull&#39;Inventario](retail/retail-overview.md#inventory-based-urgency-campaigns) | Retail | [!BADGE Fondamentale]{type=Neutral} | Aumento del 30-40% nella conversione |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="Riduzione prezzo" width="40"> | [Avvisi di riduzione prezzo](retail/retail-overview.md#price-drop-alerts) | Retail | [!BADGE Fondamentale]{type=Neutral} | Tasso di conversione del 20-30% |
| | [Notifiche esaurite](retail/retail-overview.md#out-of-stock-notifications) | Retail | [!BADGE Fondamentale]{type=Neutral} | Tasso di conversione 40-50% |

### Percorso orchestrato con più passaggi

Guida i clienti attraverso sequenze multi-touch che si adattano in base al coinvolgimento e al comportamento.

| | Caso d’uso | Settore | Maturità | Impatto aziendale |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="Serie di benvenuto" width="40"> | [Nuova serie di benvenuto per il cliente](retail/retail-overview.md#new-customer-welcome-series) | Retail | [!BADGE Emergente]{type=Informative} | Tasso di coinvolgimento del 40-50% |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="Rifornimento" width="40"> | [Promemoria rifornimento](retail/retail-overview.md#replenishment-reminders) | Retail | [!BADGE Emergente]{type=Informative} | 30-40% di acquisti ripetuti |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="Post-acquisto" width="40"> | [Campagne Di Follow-Up Post-Acquisto](retail/retail-overview.md#post-purchase-follow-up-campaigns) | Retail | [!BADGE Emergente]{type=Informative} | 15-20% tasso di revisione, 10-15% acquisto ripetuto |

### Percorso cross-channel con decisioning

Orchestrazione di esperienze cross-channel con decisioni sulle offerte in tempo reale in ogni punto di contatto.

| | Caso d’uso | Settore | Maturità | Impatto aziendale |
| --- | --- | --- | --- | --- |
| | [Offerte esclusive per i clienti VIP](retail/retail-overview.md#vip-customer-exclusive-offers) | Retail | [!BADGE Avanzate]{type=Caution} | Percentuale di coinvolgimento del 50-70% da VIP |

>[!TAB Personalization]

### Consigli comportamentali

Utilizza modelli basati sull’intelligenza artificiale per creare contenuti e prodotti personalizzati in base a segnali comportamentali.

| | Caso d’uso | Settore | Maturità | Impatto aziendale |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="Consigli di prodotto" width="40"> | [Consigli di prodotto personalizzati](retail/retail-overview.md#personalized-product-recommendations) | Retail | [!BADGE Emergente]{type=Informative} | Aumento del 20-30% del CTR, aumento della conversione del 15-25% |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="Pagine categoria" width="40"> | [Pagine di categorie personalizzate](retail/retail-overview.md#personalized-category-pages) | Retail | [!BADGE Emergente]{type=Informative} | Aumento del 25-35% del coinvolgimento |

### Offer Decisioning

Utilizza la logica decisionale centralizzata per valutare e selezionare l’offerta migliore per ogni cliente e contesto.

| | Caso d’uso | Settore | Maturità | Impatto aziendale |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="Vendita incrociata" width="40"> | [Consigli per vendite incrociate e upselling](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | Retail | [!BADGE Avanzate]{type=Caution} | Aumento di $25-$75 in AOV, incremento del 10-15% dei ricavi |

### Personalization Web/app visitatore noto

Personalizza i contenuti web e app per i visitatori identificati in base a profilo, preferenze e contesto di navigazione.

| | Caso d’uso | Settore | Maturità | Impatto aziendale |
| --- | --- | --- | --- | --- |
| | [Personalization di prova social](retail/retail-overview.md#social-proof-personalization) | Retail | [!BADGE Emergente]{type=Informative} | Aumento del tasso di conversione del 10-15% |

>[!ENDTABS]
