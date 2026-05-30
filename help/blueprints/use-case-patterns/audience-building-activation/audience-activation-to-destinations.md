---
title: Attivazione del pubblico nelle destinazioni
description: Scopri come valutare e pubblicare segmenti di pubblico in destinazioni esterne per il targeting o l’eliminazione tramite Adobe Real-Time CDP.
solution: Real-Time Customer Data Platform, Experience Platform
exl-id: b0b9d937-45d2-48f9-ac4c-3611c6e35f58
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1365'
ht-degree: 4%

---

# Attivazione del pubblico nelle destinazioni

Questa guida descrive il caso di utilizzo dell&#39;attivazione del pubblico alle destinazioni, che valuta i segmenti di pubblico in Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP) e li pubblica su piattaforme di annunci, archiviazione cloud, sistemi CRM o partner di dati per il targeting, l&#39;eliminazione, la modellazione lookalike o l&#39;arricchimento di analisi. È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono comprendere il funzionamento di questo modello, gli obiettivi aziendali supportati, i casi di utilizzo tattici che consente e le applicazioni Adobe coinvolte.

Questo modello copre l’intero ciclo di vita dell’attivazione del pubblico, dalla definizione e valutazione dei segmenti di pubblico alla configurazione delle connessioni di destinazione e alla pubblicazione dei tipi di pubblico, fino al monitoraggio dello stato di attivazione e all’applicazione della conformità alle normative.

## Schema del caso d’uso

**Audience Activation in destinazioni**: valuta e pubblica un segmento di pubblico in destinazioni esterne per il targeting o l&#39;eliminazione.

**Piano di esecuzione:** Valutazione del pubblico > Configurazione di destinazione > Audience Activation > Monitoraggio

## Panoramica del caso d’uso

Le organizzazioni devono fornire dati sul pubblico a sistemi esterni per alimentare campagne multimediali a pagamento, arricchire record CRM, condividere dati con i partner o alimentare analisi a valle. Audience Activation to Destinations è il modello di attivazione di base in RT-CDP: valuta quali profili sono idonei per un pubblico di destinazione, si connette a una o più destinazioni esterne, mappa gli attributi del profilo su campi specifici della destinazione e pubblica il pubblico per il consumo a valle.

Questo modello si applica ogni volta che l’obiettivo è quello di ottenere i dati di un pubblico a un sistema esterno nel formato giusto al momento giusto. Non implica la consegna di messaggi, la personalizzazione nel sito o l’analisi. È il punto di partenza più comune per le implementazioni RT-CDP e funge da blocco predefinito su cui si compongono altri modelli.

Le parti interessate tipiche includono i team di marketing digitale che gestiscono media a pagamento, i team di dati che arricchiscono i magazzini, i team di gestione delle relazioni con i clienti che preparano elenchi di contatti per le campagne e i team di privacy che garantiscono la conformità in materia di governance dei flussi di dati in uscita.

>[!NOTE]
>Se la tua organizzazione utilizza [!DNL Real-Time CDP] B2B edition e si attiva su destinazioni basate su account, consulta [Attivazione del pubblico B2B](../b2b/account-audience-activation.md). Questo modello condivide la stessa meccanica di attivazione ma utilizza un modello di dati account-and-person B2B e richiede la licenza B2B edition.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### Acquisire nuovi clienti

Espandi la base di clienti tramite campagne di acquisizione mirate, tipi di pubblico simili e ottimizzazione di contenuti multimediali a pagamento.

**KPI:** nuovi clienti, costo acquisizione cliente, conversione potenziali clienti/lead

[Ulteriori informazioni sull&#39;acquisizione di nuovi clienti](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Riduzione dei costi di acquisizione dei clienti

Migliora l’efficienza del targeting, elimina i clienti esistenti dalle campagne di acquisizione e ottimizza la spesa per i contenuti multimediali.

**KPI:** Costo Acquisizione Cliente, Costo Per Lead, Efficienza

[Ulteriori informazioni sulla riduzione dei costi di acquisizione dei clienti](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### Ottimizzazione della spesa di marketing e del ROI

Migliora il ritorno sull’investimento marketing migliorando il targeting, l’attribuzione, l’eliminazione del pubblico e l’allocazione del budget.

**KPI:** Risparmio sui costi, Costo di acquisizione cliente, Ricavi incrementali

[Ulteriori informazioni sull’ottimizzazione della spesa di marketing e del ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Esempi di casi d’uso tattici

- **Pubblico della piattaforma di annunci targeting**: invia segmenti qualificati alle piattaforme di media a pagamento per il targeting della campagna
- **Eliminazione dei supporti a pagamento dei clienti esistenti** — Escludi i clienti noti dalle campagne di acquisizione sulle piattaforme di annunci per eliminare gli sprechi
- **Pubblico di seed lookalike**: invia segmenti di clienti di alto valore a Facebook, Google Ads o The Trade Desk come pubblico di seed per l’espansione lookalike
- **Sincronizzazione CRM per l&#39;abilitazione alle vendite**: attiva tipi di pubblico ad alto intento o di valore elevato in modo che i team di vendita possano dare priorità all&#39;impegno
- **Condivisione del pubblico tra partner dati**: condividi segmenti di pubblico qualificati con partner dati per il targeting o la misurazione cooperativi
- **Esportazione archiviazione cloud per arricchimento data warehouse** — Esporta appartenenza pubblico e attributi di profilo in Amazon S3, Azure Blob, Google Cloud Storage o SFTP per analisi a valle
- **Attivazione pubblico per retargeting** - Attiva i visitatori del sito che non sono stati convertiti in piattaforme di retargeting
- **Sincronizzazione elenco contatti con provider di servizi di posta elettronica**: invia iscrizione pubblico a piattaforme di posta elettronica di terze parti per una distribuzione coordinata

## Indicatori chiave di prestazioni

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Costo di acquisizione cliente (CAC) | Costo per acquisire un nuovo cliente tramite tipi di pubblico attivati | Spesa totale per contenuti multimediali/nuovi clienti attribuiti al pubblico attivato |
| Percentuale di corrispondenza pubblico | Percentuale di profili attivati con corrispondenza riuscita nella destinazione | Profili associati alla destinazione / profili esportati da RT-CDP |
| Risparmi di eliminazione | Si evitano spese di supporto eliminando i clienti esistenti dalle campagne di acquisizione | Dimensione stimata del pubblico per CPM x soppresso |
| Tasso di consegna attivazione | Percentuale di profili consegnati correttamente alla destinazione | Profili consegnati/profili nel pubblico sorgente |
| Tempo di attivazione | Tempo trascorso dalla definizione del pubblico alla prima consegna nella destinazione | Misura dalla creazione del segmento alla prima esecuzione confermata del flusso di dati |
| Precisione popolazione pubblico | Allineamento tra le dimensioni del pubblico previste e quelle effettive nella destinazione | Conteggio del pubblico di destinazione/conteggio del pubblico RT-CDP |

## Applicazioni

- **Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP)** — Valutazione del pubblico, gestione della destinazione, attivazione del pubblico, applicazione del consenso e della governance
- **Adobe [!DNL Experience Platform] (AEP)** — Archivio profili, servizio identità, motore di segmentazione, governance dei dati

## Architettura

La seguente architettura di riferimento illustra il flusso di dati di pubblico e profilo da Real-Time CDP a destinazioni aziendali, tra cui archiviazione cloud, endpoint di streaming e applicazioni SaaS.

![Architettura di riferimento per l&#39;attivazione di tipi di pubblico e profili per le destinazioni enterprise](/help/blueprints/audience-activation/assets/known_activation.png)

## Documentazione correlata

**Destinazioni**

- [Panoramica sulle destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Catalogo delle destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Attivare i tipi di pubblico nelle destinazioni di streaming](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Attivare i tipi di pubblico per le destinazioni di esportazione dei profili in batch](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Attivare i tipi di pubblico on-demand per le destinazioni batch](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [Guardrail delle destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- [Panoramica di Destination SDK](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/destination-sdk/overview)

**Tipi di pubblico e segmentazione**

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Segmentazione in streaming](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Panoramica sulla composizione del pubblico](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Guardrail di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

**Identità e profilo**

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Regole di collegamento del grafo identità](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Panoramica del profilo](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

**Modellazione dati e schemi**

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

**Governance dei dati**

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview)
- [Criteri di governance dei dati](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/policies/overview)
- [Applicazione dei criteri](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [Consenso e preferenze](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Monitoraggio e osservabilità**

- [Monitorare i flussi di dati per le destinazioni](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Panoramica degli avvisi](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Panoramica di Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
- [Dashboard utilizzo licenze](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Attributi calcolati**

- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Guida dell’interfaccia utente attributi calcolati](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)

**Raccolta dati e origini**

- [Panoramica sulle origini](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Panoramica di Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)

**Amministrazione**

- [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home)
- [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home)
- [Controllo degli accessi basato su attributi](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/abac/overview)

**Guardrail**

- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Guardrail del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
- [Guardrail di attivazione](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- [Guardrail di acquisizione](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
