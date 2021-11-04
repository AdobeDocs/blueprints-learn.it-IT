---
title: Attivazione B2B
description: Offri tipi di pubblico basati su account ed esperienze cliente incentrate sul profilo con Real-time Customer Data Platform ​.
solution: Experience Platform, Real-time Customer Data Platform
kt: 9311
exl-id: null
source-git-commit: d811d82418d477372caa9e5b0b67af197275d459
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 5%

---

# Pubblico B2B e attivazione del profilo

Utilizza account, opportunità e informazioni principali collegate a un singolo cliente per creare profili b2b utilizzabili per migliorare la personalizzazione e il targeting tra i canali.

## Casi di utilizzo

* Crea tipi di pubblico di persone per il targeting e la personalizzazione tra canali diversi rispetto ai dati B2B, inclusi account, opportunità e lead.
* Attiva i tipi di pubblico in qualsiasi destinazione di Experience Platform per il targeting e la personalizzazione.

## Applicazioni

* Real-time Customer Data Platform Edizione B2B

## Pattern di integrazione

* Origini dati B2B (Marketo, Salesforce, ecc.) -> Real-time Customer Data Platform B2B Edition -> Destinazioni È possibile utilizzare diverse origini dati B2B per mappare i dati su account, lead, opportunità e persone all’edizione B2B di Real-time Customer Data Platform.

## Architettura

<img src="assets/b2b-activation.svg" alt="Architettura di riferimento per il Blueprint di attivazione B2B" style="border:1px solid #4a4a4a" />
<br>

## Guardrail

Tieni presente che le protezioni e le fasi di implementazione relative al Marketo Engage sono rilevanti solo quando il Marketo Engage è utilizzato come origine e/o destinazione.

### Supporto di più istanze e organizzazioni IMS:

Di seguito sono descritti i pattern supportati per la mappatura delle istanze di Experience Platform e Marketo Engage.

#### Marketo come origine dati per Experience Platform:

* Sono supportate più istanze di Marketi Engage a un&#39;istanza di Experience Platform.
* Non sono supportate più istanze di Marketi Engage a più istanze di Experience Platform.
* Un&#39;istanza di Marketo Engage a più istanze di Experience Platform non è supportata.
* È supportata un’istanza di Marketo Engage a un’istanza di Experience Platform e più sandbox.

#### Marketo come destinazione per Experience Platform:

* È supportato l’Experience Platform a più istanze di Marketo Engage
* Sono supportate molte istanze di Experience Platform a un&#39;istanza di Marketo Engage

#### Experience Platform di protezioni per profili e segmentazione:

* Vedi le protezioni di profilo e segmentazione per Experience Platform - [Linee guida per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)
* I segmenti B2B che includono account, lead, opportunità utilizzano relazioni con più entità che fanno sì che la valutazione dei segmenti diventi batch. La segmentazione in streaming è supportata per i segmenti che sono limitati a persone ed eventi.

#### Experience Platform - Connettore sorgente Marketo Engage:

* Il recupero storico può richiedere fino a 7 giorni per essere completato, a seconda del volume di dati.
* Gli aggiornamenti e le modifiche dei dati in corso da Marketo vengono inviati ad Experience Platform tramite l’API streaming che può essere latente fino a circa 5 minuti al profilo e circa 15 minuti al data lake a seconda del volume.

#### Experience Platform - Connettore di destinazione Marketo:

* La condivisione in streaming dei segmenti da Real-time Customer Data Platform al Marketo Engage può richiedere fino a 5 minuti.
* La segmentazione in batch viene condivisa una volta al giorno in base al programma di segmentazione Experience Platform. I segmenti B2B che includono account, lead, opportunità utilizzano relazioni con più entità che fanno sì che il segmento diventi batch.

#### Guardrail di Marketo Engage:

* I contatti e i lead devono essere acquisiti e definiti direttamente in Marketo Engage affinché il pubblico Real-time Customer Data Platform possa essere associato a un contatto e a un lead di Marketo Engage.

#### Guardrail di destinazione

* Per informazioni specifiche sulle destinazioni, consulta la documentazione di destinazione . [Linee guida sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=en)


## Fasi di implementazione

Per informazioni su come implementare e configurare l’edizione B2B di Real-time Customer Data Platform, consulta l’edizione B2B della documentazione Real-time Customer Data Platform. [Edizione B2B di Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)

Esistono due possibili pattern di implementazione. Sia la capacità di acquisire dati e profili B2B dal Marketo Engage che la capacità di acquisire dati B2B da altre fonti di dati CRM.

## Considerazioni sull’implementazione

Indicazioni su considerazioni e configurazioni chiave del modello.

* Integrazione CRM con e senza Marketo: Se l&#39;implementazione utilizzerà il Marketo Engage come origine e il Marketo Engage è connesso al sistema di gestione delle relazioni con i clienti, utilizza il connettore di origine Marketo in Experience Platform per acquisire i dati CRM in Experience Platform. Utilizza il connettore di origine Experience Platform se è necessario acquisire ulteriori tabelle. Se l&#39;implementazione non utilizza il Marketo Engage come origine, connetti l&#39;origine CRM direttamente ad AEP utilizzando il connettore di Experience Platform sorgente CRM.
* Si sconsiglia l’avvio e l’aggiornamento al lead della sola edizione B2B di Real-time Customer Data Platform. Per questo caso d’uso si consiglia l’utilizzo di uno strumento di sviluppo del lead (ad esempio Marketo Engage).
* Il connettore di destinazione Marketo Engage per AEP che invia i tipi di pubblico al Marketo Engage per l’attivazione, invia solo indirizzi e-mail ed ECID. Se il contatto non esiste già, non crea un nuovo lead, pertanto è necessario inserire i dati del profilo e del lead nel Marketo Engage.

## Documentazione correlata

* [Edizione B2B di Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)
* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [Marketo Engage](https://experienceleague.adobe.com/docs/marketo/using/home.html?lang=en)
* [Adobe Experience Platform - Connettore sorgente Marketo](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=it)
* [Adobe Experience Platform - Connettore di destinazione Marketo](https://experienceleague.adobe.com/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-cloud-segment-to-a-marketo-static-list.html?lang=en)