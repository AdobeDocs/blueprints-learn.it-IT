---
title: Automotive Use Cases
description: Discover how automotive organizations use Adobe Experience Platform to personalize the vehicle purchase journey, improve service retention, and build owner loyalty.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: ee83c739-0907-481d-ba3f-358af4e03c67
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '1941'
ht-degree: 4%

---

# Automotive use cases

Automotive organizations use Adobe Experience Platform to unify customer data from dealership interactions, online vehicle research, service records, and connected car systems into a single view of each owner. This foundation enables personalized experiences throughout the entire ownership lifecycle, from initial vehicle research through purchase, service, and loyalty.

## Use case summary

| Caso d’uso | Descrizione | Impatto aziendale | Implementation Pattern |
| --- | --- | --- | --- |
| [Percorso di acquisto veicolo Personalization](#vehicle-purchase-journey-personalization) | Personalizza il percorso di acquisto del veicolo dalla ricerca all’acquisto con le relative raccomandazioni per il veicolo, le opzioni di finanziamento e le informazioni sui dealer. When potential buyers receive tailored guidance at each stage, they move through the sales funnel more quickly and with greater confidence. | Improved lead-to-purchase conversion rates and stronger sales pipeline | [Percorso cross-channel con decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| [Promemoria appuntamenti di servizio](#service-appointment-reminders) | Send personalized service reminders based on vehicle mileage, service history, and customer preferences. Proactive outreach keeps vehicles maintained and ensures customers return to the dealership rather than seeking third-party providers. | Improved service appointment show rates and increased service revenue | [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [Campagne Di Valore Di permuta](#trade-in-value-campaigns) | Proactively offer trade-in value assessments to customers who may be ready to upgrade. Reaching owners at the right point in their ownership cycle accelerates the path to a new vehicle purchase. | Improved trade-in engagement and increased new vehicle sales | [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [Consigli su parti e accessori](#parts-and-accessories-recommendations) | Consigliare parti, accessori e aggiornamenti pertinenti in base al modello del veicolo, alla durata di proprietà e alle preferenze del cliente. Personalized aftermarket recommendations drive incremental revenue while helping owners get more from their vehicle. | Improved parts and accessories purchase rates and increased aftermarket revenue | [Consigli comportamentali](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| [Notifiche di richiamo veicolo](#vehicle-recall-notifications) | Send personalized recall notifications with service scheduling options and safety information. Timely, clear recall communications protect customer safety and demonstrate the brand&#39;s commitment to responsible ownership support. | Improved recall response rates and stronger safety compliance | [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [Nuove Campagne Di Lancio Modelli](#new-model-launch-campaigns) | Puoi indirizzare l’attività ai clienti che potrebbero essere interessati ai nuovi lanci di modelli in base al veicolo, alle preferenze e alla cronologia degli acquisti correnti. Focused audience targeting maximizes launch impact and builds early order momentum. | Improved launch campaign engagement and increased new model interest | [Attivazione messaggi in uscita in batch](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| [Offerte di finanziamento e assicurazione](#financing-and-insurance-offers) | Presenta offerte di finanziamento e assicurazione personalizzate in base al profilo di credito, alla selezione dei veicoli e alla tempistica di acquisto. Prodotti finanziari su misura eliminano le barriere all&#39;acquisto e aiutano i clienti a sentirsi sicuri delle loro condizioni. | Miglioramento dei tassi di accettazione dei finanziamenti e aumento dei ricavi per vendita | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| [Pianificazione unità di prova](#test-drive-scheduling) | Pianificazione personalizzata delle unità di test con consigli dei dealer e disponibilità del veicolo. Rendendo più semplice per gli acquirenti interessati mettersi al volante si accelera il percorso di acquisto. | Miglioramento dei tassi di completamento dei test e maggiore conversione delle vendite | [Messaggi attivati da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [Programmi fedeltà del proprietario](#owner-loyalty-programs) | Coordina le comunicazioni fidelizzate tra rivenditori, OEM digitali e canali di auto connesse, applicando regole di idoneità basate su livelli per determinare quali proprietari ricevono offerte esclusive, accesso anticipato al veicolo e premi per i partner. L&#39;arbitrato dell&#39;offerta impedisce le promozioni in conflitto da parte dei canali rivenditore e OEM che raggiungono lo stesso proprietario contemporaneamente. | Migliore coinvolgimento nel programma fedeltà e maggiori acquisti ripetuti | [Percorso cross-channel con decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| [Garanzia e piani di assistenza estesi](#warranty-and-extended-service-plans) | Consigliare la garanzia e piani di assistenza estesi in tempi ottimali in base all&#39;età del veicolo, al chilometraggio e ai modelli di acquisto. Un&#39;attività di outreach ben programmata acquisisce i ricavi prima della scadenza delle garanzie di fabbrica. | Tassi di adozione della garanzia estesi e maggiori ricavi dal servizio migliorati | [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [Attivazione funzionalità per auto collegate](#connected-car-feature-activation) | Personalizza le raccomandazioni sulle funzioni dell’auto collegata in base alle funzionalità del veicolo e alle preferenze tecnologiche. Aiutare i proprietari a scoprire le funzionalità inutilizzate aumenta la soddisfazione e rafforza la relazione digitale. | Tassi di attivazione delle funzioni migliorati e migliore esperienza del cliente | [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [Coordinazione rete rivenditori](#dealer-network-coordination) | Abilita i consigli personalizzati dei dealer in base alla posizione del cliente, alle preferenze e all’inventario dei dealer. Mettere in contatto i clienti con i rivenditori giusti migliora l&#39;esperienza di acquisto e di servizio. | Miglioramento delle percentuali di coinvolgimento dei dealer e potenziamento del coordinamento delle vendite | [Web visitatore conosciuto/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

## Considerazioni tecniche per caso d’uso

### Personalizzazione percorso di acquisto veicolo

- I dati di inventario dei veicoli provenienti dai sistemi di gestione dei concessionari devono essere integrati e aggiornati frequentemente in modo che le raccomandazioni riflettano l’effettiva disponibilità presso i concessionari nelle vicinanze.
- Per identificare con precisione i segnali di intento di acquisto, è necessario acquisire il comportamento di ricerca dei clienti nel sito web, incluse le attività di configurazione del veicolo, l’utilizzo degli strumenti di confronto e i download delle brochure.
- I modelli di valutazione dei lead devono tenere conto sia del coinvolgimento online che dei segnali offline, come le visite dei dealer e le richieste telefoniche, per dare priorità ai potenziali clienti con le migliori intenzioni.
- I profili [!DNL Real-Time Customer Data Platform] devono unire le sessioni di ricerca Web anonime con le identità note dei clienti una volta che un potenziale cliente si registra o visita un rivenditore.

### Promemoria appuntamenti assistenza

- Vehicle mileage and telematics data from connected car systems or dealer service records must flow into customer profiles to trigger reminders at the correct service intervals.
- Reminder messages should include one-click scheduling links that pre-populate the customer&#39;s vehicle information and recommended service items to minimize booking friction.
- Service history records must be integrated to avoid recommending services that were recently completed and to personalize the reminder with the specific maintenance items due.
- [!DNL Journey Optimizer] message timing should account for dealer service capacity and hours of operation to ensure customers can book appointments when they receive the reminder.

### Trade-in value campaigns

- Vehicle valuation data from third-party providers must be integrated and refreshed regularly to ensure trade-in estimates shared with customers are accurate and competitive.
- Ownership lifecycle models should consider factors such as lease expiration dates, loan payoff timelines, and average ownership duration by vehicle segment to identify the optimal outreach window.
- Campaign messaging should dynamically reference the customer&#39;s current vehicle and suggest specific upgrade options that align with their preferences and budget.
- [!DNL Experience Platform] segments should exclude customers who recently purchased a vehicle or are currently in an active service dispute to avoid poorly timed outreach.

### Parts and accessories recommendations

- Product catalog data must include vehicle compatibility information so that recommendations only show parts and accessories that fit the customer&#39;s specific vehicle year, make, and model.
- Seasonal and regional factors should influence recommendations; winter accessories should be promoted in colder climates, while performance upgrades may resonate more in regions with active enthusiast communities.
- Browsing behavior on parts and accessories pages must be captured and associated with customer profiles to refine recommendations based on expressed interest.
- [!DNL Experience Platform] Web SDK implementation should capture vehicle identification number data from authenticated sessions to ensure compatibility filtering is accurate.

### Vehicle recall notifications

- Vehicle identification number records must be accurately maintained in customer profiles so that recall notifications reach every affected owner and do not go to unaffected customers.
- Recall messaging must comply with regulatory requirements for safety notification content, timing, and delivery confirmation in each applicable market.
- Multi-channel delivery (email, text message, push notification, and physical mail) should be used to maximize reach, as safety-critical communications require higher delivery assurance than marketing messages.
- [!DNL Journey Optimizer] should track recall response status at the individual level and escalate follow-up communications for owners who have not scheduled service within a defined timeframe.

### New model launch campaigns

- Audience segments for launch campaigns should consider current vehicle model, ownership duration, past model interest signals, and demographic fit to identify the highest-propensity prospects.
- Launch content should be personalized to reference the customer&#39;s current vehicle and highlight specific improvements or features that address their likely priorities.
- Campaign timing must coordinate with embargo dates and regional launch schedules to ensure customers receive information at the appropriate time for their market.
- [!DNL Real-Time Customer Data Platform] audience activation should synchronize launch segments to advertising platforms for coordinated paid media support alongside owned-channel outreach.

### Financing and insurance offers

- Financial offer eligibility rules must be carefully configured to comply with lending regulations, ensuring that offers presented to customers are ones they can actually qualify for.
- Credit profile data integration requires secure handling and strict access controls, as financial information is subject to heightened privacy and regulatory requirements.
- Offer presentation must clearly disclose terms, rates, and conditions in compliance with consumer finance regulations in each applicable market.
- [!DNL Journey Optimizer] decisioning rules should factor in vehicle price, down payment, and loan term preferences to rank offers by relevance rather than simply by rate.

### Test drive scheduling

- Dealer inventory systems must be integrated to confirm that the specific vehicle model and trim the customer is interested in is available for test drive at the recommended dealership.
- Location-based dealer recommendations should factor in customer address, dealer ratings, and current appointment availability to suggest the most convenient option.
- Test drive confirmation and reminder messages should include directions, dealer contact information, and what to expect, reducing no-show rates.
- [!DNL Experience Platform] behavioral data should identify the optimal moment to suggest a test drive, avoiding premature outreach to early-stage researchers who are not yet ready.

### Owner loyalty programs

- Loyalty tier calculations must incorporate multiple dimensions of engagement including service visits, parts purchases, referrals, and event attendance, not just vehicle purchase history.
- Tier-based eligibility rules must be configured in [!DNL Journey Optimizer] decisioning to govern which owners qualify for exclusive offers, early access to new vehicle reveals, and partner reward redemptions, ensuring only eligible members receive each category of benefit.
- Offer arbitration logic must evaluate pending communications from both dealer and OEM channels before any message is sent, suppressing lower-priority or conflicting promotions to prevent the same owner from receiving contradictory offers simultaneously.
- Cross-channel coordination must span dealer CRM systems, OEM digital properties, connected car notification channels, and service touchpoints so that loyalty interactions are consistent regardless of where the owner engages.
- Reward fulfillment systems at dealerships and service centers must be integrated so that loyalty benefits can be redeemed seamlessly at the point of service.
- Communications should adapt based on ownership lifecycle stage, delivering different value propositions to new owners in their first year versus long-term owners approaching a potential upgrade.
- [!DNL Journey Optimizer] journey logic should detect tier changes in real time and trigger congratulatory or re-engagement messages when customers move between loyalty levels.

### Warranty and extended service plans

- Warranty expiration dates and coverage details must be accurately tracked in customer profiles to trigger outreach at the right time, typically 60-90 days before expiration.
- Vehicle mileage and usage patterns from connected car data or service records should inform plan recommendations, as high-mileage drivers benefit from different coverage than low-mileage owners.
- Plan comparison content should be clear and jargon-free, helping customers understand exactly what is covered and the value relative to potential out-of-pocket repair costs.
- [!DNL Real-Time Customer Data Platform] segments should distinguish between customers with expiring factory warranties, those with existing extended plans approaching renewal, and those with no current coverage.

### Connected car feature activation

- Connected car platform data must be integrated to identify which features are available on each vehicle and which ones the owner has already activated or used.
- Feature adoption tracking should capture activation events, usage frequency, and engagement depth to personalize the sequence and pacing of feature recommendations.
- In-vehicle notification channels should be coordinated with email and app notifications to deliver feature prompts at the most contextually relevant moment, such as suggesting navigation features when a road trip is detected.
- [!DNL Experience Platform] profiles should store vehicle technology configuration data including installed packages and software versions to ensure feature recommendations are compatible with the owner&#39;s specific vehicle.

### Dealer network coordination

- Dealer inventory feeds must be integrated and refreshed frequently to ensure that vehicle availability shown to customers accurately reflects what is on each dealer&#39;s lot.
- Customer-to-dealer assignment logic should consider proximity, dealer specialization, language preferences, and any existing dealer relationship to provide the best match.
- Lead routing rules must ensure that when a customer expresses purchase interest online, the inquiry reaches the appropriate dealer quickly with full context about the customer&#39;s research activity.
- [!DNL Experience Platform] identity resolution must handle scenarios where a customer interacts with multiple dealerships, maintaining a unified profile while respecting each dealer&#39;s view of their own customer relationships.
