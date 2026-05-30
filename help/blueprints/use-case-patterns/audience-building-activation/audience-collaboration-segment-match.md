---
title: Audience Collaboration
description: Scopri come condividere e abbinare i segmenti di pubblico tra sandbox o organizzazioni utilizzando Segment Match.
solution: Real-Time Customer Data Platform, Experience Platform
exl-id: 7014849c-5e32-4ec3-a531-c0e8ce896f44
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1351'
ht-degree: 3%

---

# Audience Collaboration

Questa guida descrive il modello di casi di utilizzo di collaborazione tra tipi di pubblico, che utilizza [!DNL Segment Match] in [!DNL Real-Time CDP] e [!DNL Adobe Experience Platform] per condividere e abbinare segmenti di pubblico tra sandbox o organizzazioni in modo sicuro per la privacy. È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono comprendere il funzionamento di questo modello, gli obiettivi aziendali supportati, i casi di utilizzo tattici che consente e le applicazioni Adobe coinvolte.

[!DNL Segment Match] consente a due o più organizzazioni di [!DNL Experience Platform] (o sandbox all&#39;interno di un&#39;organizzazione) di collaborare ai dati del pubblico condividendo le informazioni sull&#39;appartenenza ai segmenti senza esporre i dati PII sottostanti. I partecipanti possono stimare la sovrapposizione, condividere i tipi di pubblico e attivare i profili corrispondenti nelle destinazioni a valle.

## Schema del caso d’uso

Questo caso d’uso segue il pattern di Audience Collaboration.

Condividi e abbina segmenti di pubblico tra sandbox o organizzazioni utilizzando [!DNL Segment Match].

**Piano di esecuzione:** Selezione segmenti > Configurazione corrispondenza > Stima sovrapposizione > Condivisione pubblico > Attivazione

## Panoramica del caso d’uso

Le organizzazioni devono collaborare sempre più spesso ai dati sul pubblico con partner, filiali o tra unità aziendali, mantenendo al contempo rigidi controlli sulla privacy. La collaborazione con il pubblico soddisfa questa esigenza abilitando la condivisione sicura dei segmenti tramite [!DNL Segment Match], una funzionalità all&#39;interno di [!DNL Real-Time CDP] che consente a due o più organizzazioni [!DNL Experience Platform] (o sandbox) di scambiare informazioni sull&#39;appartenenza al pubblico utilizzando identificatori hash e sicuri per la privacy.

In genere, lo scenario aziendale coinvolge un’organizzazione (il mittente) che ha creato un segmento di pubblico prezioso e desidera condividerlo con un’organizzazione partner (il destinatario) per il targeting, la soppressione o l’arricchimento congiunti. Prima della condivisione, entrambe le parti possono stimare la sovrapposizione del pubblico per valutarne il valore. Una volta condiviso, l’organizzazione ricevente può attivare il pubblico corrispondente tramite le proprie destinazioni.

Questo modello è distinto dall’attivazione standard del pubblico perché funziona tra organizzazioni o sandbox anziché verso destinazioni esterne di pubblicità o marketing. Si distingue inoltre dalle clean room di dati o dalle piattaforme di collaborazione di terze parti perché opera in modalità nativa nell&#39;ecosistema Adobe utilizzando l&#39;infrastruttura di identità [!DNL Experience Platform].

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### Acquisire nuovi clienti

Espandi la base di clienti tramite campagne di acquisizione mirate, tipi di pubblico simili e ottimizzazione di contenuti multimediali a pagamento. La collaborazione tra i tipi di pubblico consente alle organizzazioni di individuare nuovi pool di potenziali clienti confrontando i segmenti con quelli dei partner, identificando sovrapposizioni di alto valore e raggiungendo nuovi clienti attraverso l’attivazione congiunta.

- **KPI:** nuovi clienti, costo acquisizione cliente, conversione potenziali clienti/lead
- [Acquisire nuovi clienti](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Riduzione dei costi di acquisizione dei clienti

Migliora l’efficienza del targeting, elimina i clienti esistenti dalle campagne di acquisizione e ottimizza la spesa per i contenuti multimediali. Condividendo segmenti di soppressione tra organizzazioni o unità aziendali, i team possono evitare sprechi di spesa sui clienti già convertiti e concentrare il budget su nuovi potenziali clienti.

- **KPI:** Costo Acquisizione Cliente, Costo Per Lead, Efficienza
- [Riduzione dei costi di acquisizione dei clienti](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### Ottimizzazione della spesa di marketing e del ROI

Migliora il ritorno sull’investimento marketing migliorando il targeting, l’attribuzione, l’eliminazione del pubblico e l’allocazione del budget. [!DNL Segment Match] consente l&#39;eliminazione del pubblico tra organizzazioni e il targeting congiunto che riduce la duplicazione e migliora la precisione.

- **KPI:** Risparmio sui costi, Costo di acquisizione cliente, Ricavi incrementali
- [Ottimizzazione della spesa di marketing e del ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Esempi di casi d’uso tattici

- **Corrispondenza pubblico editore-inserzionista**: un brand condivide il proprio segmento di clienti di alto valore con un editore di contenuti multimediali per stimare la sovrapposizione e indirizzare gli utenti con annunci personalizzati, migliorando la rilevanza della campagna senza esporre i dati PII.
- **Eliminazione cross-brand all&#39;interno di una holding**: più marchi di un&#39;organizzazione principale condividono segmenti di clienti per eliminare i clienti esistenti dei marchi secondari dalle campagne di acquisizione, riducendo gli sprechi pubblicitari.
- **Arricchimento dell&#39;audience di Retail Media Network**: un retailer condivide segmenti basati sull&#39;acquisto con i partner del marchio CPG, consentendo ai brand di rivolgersi ad acquirenti comprovati sulla rete multimediale retailer con tassi di conversione più elevati.
- **Individuazione del pubblico di partner di co-marketing**: due marchi non concorrenti valutano la sovrapposizione del pubblico per valutare il potenziale di partnership prima di lanciare una campagna congiunta, utilizzando la stima di sovrapposizione per convalidare l&#39;allineamento del pubblico.
- **Condivisione dei segmenti di collaborazione dati**: le organizzazioni di una cooperativa dati condividono segmenti di pubblico con hash per espandere la portata del targeting mantenendo al contempo la conformità alla privacy e i controlli di governance dei dati.
- **Federazione di pubblico con più sandbox**: un&#39;azienda globale condivide segmenti di pubblico con sandbox regionali per consentire un targeting coerente dei clienti nei diversi mercati nel rispetto dei requisiti di residenza dei dati regionali.
- **Attivazione tra partner del programma fedeltà**: una coalizione di fidelizzazione condivide segmenti di livello fedeltà con i commercianti partecipanti, in modo che ogni partner possa offrire promozioni appropriate alla base clienti condivisa.
- **Collaborazione per la misurazione e l&#39;attribuzione**: un inserzionista condivide un segmento di conversione con un partner multimediale in modo che il partner possa misurare l&#39;efficacia della campagna confrontando gli utenti esposti con i convertitori.

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare il successo delle implementazioni di collaborazione tra tipi di pubblico.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Percentuale di sovrapposizione pubblico | Percentuale di profili nel segmento condiviso che corrispondono tra mittente e destinatario | [!DNL Segment Match] rapporto di stima sovrapposizione |
| Dimensione del pubblico corrispondente | Numero di profili con corrispondenza riuscita e disponibili per l’attivazione | Stato di condivisione e conteggio della popolazione di [!DNL Segment Match] |
| Nuova acquisizione di clienti da tipi di pubblico corrispondenti | Nuovi clienti acquisiti tramite campagne indirizzate a segmenti corrispondenti | Tracciamento delle conversioni nelle campagne che utilizzano tipi di pubblico corrispondenti |
| Riduzione dei costi di acquisizione dei clienti | Diminuzione del costo per acquisizione quando si utilizza un pubblico corrispondente rispetto al targeting ampio | Analisi dei costi della campagna confrontando le prestazioni del pubblico corrispondenti e non corrispondenti |
| Risparmi di eliminazione | Risparmio sui costi dei contenuti multimediali grazie alla rimozione dei clienti noti dalle campagne di acquisizione | Confronto delle spese dei supporti di pre/post-soppressione |
| Incremento delle prestazioni della campagna | Miglioramento del tasso di conversione, del tasso di click-through o del coinvolgimento per le campagne che utilizzano tipi di pubblico corrispondenti | Test A/B di confronto tra campagne per il pubblico e il controllo |
| Time to Collaboration | Tempo trascorso dall’avvio della condivisione dei segmenti alla preparazione all’attivazione | [!DNL Segment Match] timestamp del flusso di lavoro |

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Real-Time CDP]** - Fornisce la funzionalità [!DNL Segment Match] per la condivisione del pubblico sicura per la privacy, la valutazione del pubblico per la creazione di segmenti e l&#39;attivazione della destinazione per l&#39;utilizzo a valle dei tipi di pubblico corrispondenti.
- **[!DNL Adobe Experience Platform]**: fornisce l&#39;infrastruttura di dati di base, tra cui la risoluzione delle identità, l&#39;unificazione dei profili, la governance dei dati e l&#39;applicazione del consenso da cui dipende [!DNL Segment Match].

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sulle funzionalità utilizzate in questo modello di caso d’uso.

### [!DNL Segment Match]

- [Panoramica di Segment Match](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Risoluzione dei problemi di Segment Match](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Segmentazione e tipi di pubblico

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder)
- [Panoramica sulla composizione del pubblico](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/audience-composition)
- [Riferimento Profile Query Language](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/pql/overview)
- [Segmentazione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentazione Edge](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/edge-segmentation)

### Identità e profilo

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home)
- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview)
- [Panoramica del profilo cliente in tempo reale](https://experienceleague.adobe.com/it/docs/experience-platform/profile/home)

### Governance dei dati e consenso

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home)
- [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview)
- [Applicazione dei criteri](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/enforcement/overview)
- [Consenso e preferenze](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Gruppo di campi Consenso e preferenze](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/field-groups/profile/consents)

### Destinazioni e attivazione

- [Panoramica sulle destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/home)
- [Catalogo delle destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/overview)
- [Monitorare i flussi di dati per le destinazioni](https://experienceleague.adobe.com/it/docs/experience-platform/dataflows/ui/monitor-destinations)

### Modellazione dati e schema

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home)
- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/schema/composition)

### Amministrazione e controllo degli accessi

- [Panoramica sul controllo degli accessi](https://experienceleague.adobe.com/it/docs/experience-platform/access-control/home)
- [Panoramica sulle sandbox](https://experienceleague.adobe.com/it/docs/experience-platform/sandbox/home)

### Monitoraggio e osservabilità

- [Panoramica degli avvisi](https://experienceleague.adobe.com/it/docs/experience-platform/observability/alerts/overview)
- [Panoramica di Observability Insights](https://experienceleague.adobe.com/it/docs/experience-platform/observability/home)

### Guardrail

- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)
- [Guardrail di segmentazione](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [Guardrail di attivazione](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/guardrails)

### Tutorial

- [Creare uno schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [Abilitare un set di dati per il profilo](https://experienceleague.adobe.com/it/docs/experience-platform/catalog/datasets/enable-for-profile)
