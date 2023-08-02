---
title: Settore retail - Attivazione con applicazioni Experience Cloud
description: 'Esperienze clienti in tempo reale su diversi canali: digital media, e-mail, push e web.'
solution: Real-Time Customer Data Platform, Customer Journey Analytics, Journey Orchestration, Campaign, Analytics, Target
kt: 9474
exl-id: a675bc81-e76c-491a-8718-359867d63351
source-git-commit: ae7347be5095ca4a7f99f9371dd94d87097112b0
workflow-type: ht
source-wordcount: '630'
ht-degree: 100%

---

# Le sfide nel settore retail

Questa azienda con esperienze integrate voleva personalizzare l’intera customer journey per migliorare la fidelizzazione, l’upselling ai clienti esistenti e la spesa marketing per tutte le campagne. Per raggiungere questo obiettivo e stimolare la crescita, ha esteso la sue capacità digitali includendo dati offline sui clienti e dati sulle transazioni.

## L’approccio Adobe

* Generare un profilo cliente unificato con tutti i dati online e offline pertinenti e attivabili in tempo reale
* Orchestrare le interazioni dei clienti sui canali web, media e push per favorire i primi o i secondi acquisti

## Valore aziendale conseguito

| Obiettivi | Tattiche | Nuovo valore |
|---|---|---|
| **Orchestrare customer journey in tempo reale **<br></br>** Favorire acquisti ripetuti da nuovi clienti **<br></br>** Migliorare le efficienze nel marketing e ridurre i costi dei media**</ul> | <ul><li>Strategia solida per dati e identità con cui generare profili completi in tempo reale.</li><li>Streaming dei dati cliente e transazionali in tempo reale, con 90 giorni di dati storici</li><li>Segmentazione in streaming per reti pubblicitarie e Adobe Target per potenziare la spesa sui media e le attività di personalizzazione.</li><li>Customer journey in tempo reale tramite Adobe Campaign, con una strategia per la misurazione delle prestazioni</li></ul> | <ul><li><strong>Real-time Customer Data Platform:</strong> esperienze cliente in tempo reale su media, e-mail, push e web</li><li><strong>Origini dati:</strong> dati in streaming relativi all’archivio profili, al sistema degli ordini, al catalogo dei prodotti e ai punti vendita del retailer.</li><li><strong>Attivazione di contenuti in tempo reale:</strong> invio in streaming di segmenti a reti pubblicitarie per attribuzione e soppressione di annunci</li><li><strong>Personalizzazione web in tempo reale:</strong> invio di segmenti in streaming attivati ad Adobe Target per attivare l’esperienza web del retailer.</li><li><strong>Journey Orchestration su grande scala:</strong> attivazione di messaggistica in tempo reale arricchita con tutti i dati cliente disponibili, e attivata in tempo reale nei canali e-mail e push</li></ul> |


## Casi di utilizzo

| Categoria | Obiettivo | Caso di utilizzo | Descrizione |
|:----|:----|:----|:----|
| Customer journey | Acquisizione | Serie di benvenuto | Dare il benvenuto a chi si iscrive, con una presentazione dell’azienda e dei suoi prodotti o servizi |
| | | Programma per 1° acquisto | |
| | Migliorare le vendite | Navigazione o carrello abbandonato | Recuperare potenziali acquirenti e incentivare le vendite |
| | | Recensioni prodotto/Cross-selling | Incrementare il cross-selling mediante recensioni di prodotto. |
| | | Promozioni sui prodotti |  |
| | | È ora di ordinare di nuovo | Promemoria ricorrente per prodotti/servizi ciclici |
| | Fedeltà al marchio | Riconquistare | Recuperare l’acquirente dopo un periodo di inattività. |
| | | Promemoria di compleanno | Promuovere relazioni più personali augurando a ogni cliente un buon compleanno |
| Merchandising | Gestire l’inventario | Di nuovo a magazzino | Migliorare l’inventario informando l’acquirente che i prodotti di suo interesse sono di nuovo disponibili |
| | | Categoria migliore | Identificare le categorie migliori o i prodotti più venduti per gli utenti |
| | | Articoli più venduti | |
| | | Promemoria per riduzione prezzo | Informare l’utente quando articoli di suo interesse sono disponibili a un prezzo ridotto |
| | | Prodotti simili |  |
| Personalizzazione | Aumentare la conversione | Coupon/Offerte | Presentare alla clientela coupon/offerte migliori |
| | | Ricerca di prodotti personalizzata | Migliorare l’esperienza di ricerca |
| | | Prodotti consigliati | Migliorare l’esperienza di navigazione nei prodotti |
| | | Esperienza omnicanale | Raggiungere la clientela su tutti i canali |
| Misurare | Comprendere i percorsi dei clienti | Campagna cross-channel | Misurare le campagne cross-channel |
| | | Prestazioni dei segmenti | Comprendere le prestazioni e il contributo dei segmenti |
| | | Rapporti di fallout | Visualizzare le conversioni in ogni fase |
| | | Analisi per coorte | Misurare il coinvolgimento tra diversi gruppi di segmenti |
| | | Rapporti “dal clic al negozio” | Scoprire l’effetto delle conversioni sull’esperienza in-store |
| | | Attribuzione | Individuare il punto di contatto o l’esperienza di maggiore influenza sulla conversione all’acquisto |
| | | Insight predittivi | Scoprire di più sulle propensioni dei clienti |

## Architettura

<img src="../vertical-blueprints/assets/retail-architecture.png" alt="Architettura di riferimento per il settore retail" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />


## Blueprint correlati


| Casi di utilizzo/integrazione  | Collegamento |
|:----|:----|
| CJA + AEP | [Panoramica dei blueprint su Customer Journey Analytics](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journey-analytics/overview.html?lang=it) |
| | [Customer Journey Analytics - Casi di utilizzo](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cja-usecases.html?lang=it) |
| AJO + AEP | [Adobe Journey Optimizer - Casi di utilizzo](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/journey-optimizer.html?lang=it) |
| | [Gestione delle decisioni](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=it) |
| RTCDP + AEP | [Attivazione del pubblico con dati online/offline](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html?lang=it) |
| | [Attivazione Experience Platform + applicazioni](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=it) |
| Marketo + AEP | [Attivazione e marketing B2B](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/overview.html?lang=it) | |
| Target + AEP | [Caso di utilizzo di Adobe Target - Personalizzazione web e mobile basata sul comportamento](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/behavioral.html?lang=it) | [Personalizzazione web e mobile con dati sui clienti noti](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/known-personalization.html?lang=it) | |
