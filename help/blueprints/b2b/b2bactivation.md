---
title: Blueprint per l’attivazione di profili e pubblico B2B
description: Offri a un pubblico basato su account esperienze personalizzate secondo i profili con Real-time Customer Data Platform.
solution: Real-Time Customer Data Platform
kt: 9311
exl-id: 5215d077-b0a9-4417-ae9b-f4961d4a73fa
source-git-commit: 70816df06ec2dff5c3a4a94a8be701cb25e6f783
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 52%

---

# Blueprint per l’attivazione di profili e pubblico B2B

Associa a un singolo cliente le informazioni relative all’account, alle opportunità e ai lead, per creare profili B2B con cui migliorare la personalizzazione e il targeting su tutti i canali.

## Casi di utilizzo

* Crea un pubblico basato su persone e utilizzalo per il targeting e la personalizzazione su canali diversi, grazie a dati B2B quali account, opportunità e lead.
* Attiva uno specifico pubblico in qualsiasi destinazione di Experience Platform per attività di targeting e personalizzazione.
* Crea tipi di pubblico di account (ad esempio, elenchi di aziende) ed esegui il targeting di tali aziende tramite destinazioni come LinkedIn che accettano elenchi di aziende come input o esportazione in destinazioni di archiviazione cloud per il targeting e la divulgazione delle vendite.

## Applicazioni

* Real-time Customer Data Platform B2B Edition

## Modelli di integrazione

* Origini dati B2B (Marketo, Salesforce, ecc.) -> Real-time Customer Data Platform B2B edition -> Destinazioni
* È possibile utilizzare diverse origini dati B2B per mappare i dati di account, lead, opportunità e persone su B2B edition di Real-time Customer Data Platform.

## Architettura

![Architettura di riferimento per il blueprint di attivazione B2B](assets/b2b-activation.png)

## Guardrail

* I guardrail e le fasi di implementazione relative a Marketo Engage sono applicabili solo quando si usa Marketo Engage come origine e/o destinazione.

* Per ulteriori dettagli e guardrail per modello dati, dimensioni e segmentazione, consulta il [documento guardrail di distribuzione](../experience-platform/deployment/guardrails.md)


### Supporto di più istanze e organizzazioni IMS:

Di seguito sono descritti i pattern supportati per la mappatura delle istanze di Experience Platform e Marketo Engage.

#### Marketo come origine dati per Experience Platform:

* Sono supportate più istanze di Marketo Engage per una istanza di Experience Platform.
* Non è supportata una istanza di Marketo Engage per più istanze di Experience Platform.
* È supportata una istanza di Marketo Engage per una istanza di Experience Platform e più sandbox.

#### Marketo come destinazione per Experience Platform:

* È supportato Experience Platform per più istanze di Marketo Engage
* Sono supportate più istanze di Experience Platform per una istanza di Marketo Engage

#### Guardrail per segmentazione e profili Experience Platform:

* Vedi i guardrail relativi a profili e segmentazione per Experience Platform: [Guardrail per profili e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)
* I segmenti B2B che includono account, lead e opportunità utilizzano relazioni con più entità e pertanto la valutazione dei segmenti viene eseguita in batch. La segmentazione in streaming è supportata per i segmenti limitati a persone ed eventi.
* Includi un segmento b2b batch come input per un segmento in streaming o Edge per supportare casi di utilizzo di segmenti b2b in streaming. L’iscrizione al segmento batch si basa sul risultato più recente della valutazione della segmentazione batch giornaliera.

#### Connettore tra Experience Platform e origine Marketo Engage:

* Il recupero di dati storici può richiedere fino a 7 giorni, a seconda del volume di dati.
* Gli aggiornamenti e le modifiche continui dei dati da Marketo vengono inviati ad Experience Platform tramite API di streaming che possono essere latenti fino a circa 10 minuti nel profilo e possono richiedere fino a 60 minuti nel data lake, a seconda del volume.

#### Connettore tra Experience Platform e destinazione Marketo:

* La condivisione dei segmenti in streaming da Real-time Customer Data Platform a Marketo Engage può richiedere fino a 15 minuti dopo la valutazione dei segmenti. Il backfill di profili già esistenti nel segmento prima dell’attivazione per la prima volta può richiedere fino a 24 ore.
* La segmentazione in batch viene condivisa una volta al giorno in base al programma di segmentazione di Experience Platform. I segmenti B2B che utilizzano relazioni tra più entità, ad esempio i segmenti che utilizzano dati negli oggetti account e opportunità, vengono sempre eseguiti in modalità batch.

#### Guardrail per Marketo Engage:

* I contatti e i lead devono essere acquisiti e definiti direttamente in Marketo Engage affinché il pubblico Real-time Customer Data Platform possa essere associato a un contatto e un lead di Marketo Engage.
* La destinazione RTCDP Marketo può facoltativamente creare nuovi lead in Marketo per i clienti che si trovano in un segmento ma non esistono in Marketo.

#### Guardrail per destinazione

* Per informazioni specifiche sulle destinazioni, consulta la relativa documentazione. [Guardrail per destinazione](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=it)


## Fasi di implementazione

Per informazioni su come implementare e configurare Real-time Customer Data Platform B2B Edition, consulta la relativa documentazione. [Real-time Customer Data Platform B2B Edition](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=it)

Sono disponibili due modelli di implementazione: per acquisire dati e profili B2B da Marketo Engage, o per acquisire dati B2B da altri origini di dati CRM.

## Considerazioni sull’implementazione

Considerazioni chiavi e configurazioni del blueprint.

* Integrazione CRM con e senza Marketo:
Se l’implementazione utilizza Marketo Engage come origine e Marketo Engage è connesso al sistema di gestione delle relazioni con i clienti, i dati del sistema di gestione delle relazioni con i clienti passeranno automaticamente attraverso la stessa connessione, eliminando la necessità di collegare il sistema di gestione delle relazioni con i clienti direttamente a Platform, a meno che non vi siano oggetti di dati di gestione delle relazioni con i clienti aggiuntivi che non vengono passati tramite Marketo. Se dovranno essere acquisite altre tabelle di dati, utilizza il connettore di origine Experience Platform. Se l’implementazione non utilizza Marketo Engage come origine, connetti l’origine del sistema di gestione delle relazioni con i clienti direttamente a Platform utilizzando il connettore Experience Platform di origine del sistema di gestione delle relazioni con i clienti.
* Il connettore di destinazione Marketo Engage per Platform, che invia i tipi di pubblico a Marketo Engage per l’attivazione, condivide i membri del pubblico in base agli indirizzi e-mail e agli ECID corrispondenti. Se il contatto non esiste già, è possibile creare un nuovo lead. Durante la creazione di un nuovo lead, è possibile mappare fino a 50 attributi di profilo (non array o attributi di mappa) in Real-time Customer Data Platform sui campi Persona in Marketo.

## Documentazione correlata

* [Real-time Customer Data Platform B2B Edition](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=it)
* [Guida introduttiva di Real-time Customer Data Platform B2B edition](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial)
* [Guardrail per Real-time Customer Data Platform B2B edition](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails)
* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=it)
* [Marketo Engage](https://experienceleague.adobe.com/docs/marketo/using/home.html?lang=it)
* [Connettore tra Adobe Experience Platform e origine Marketo](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=it)
* [Connettore tra Adobe Experience Platform e destinazione Marketo](https://experienceleague.adobe.com/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-cloud-segment-to-a-marketo-static-list.html?lang=it)
