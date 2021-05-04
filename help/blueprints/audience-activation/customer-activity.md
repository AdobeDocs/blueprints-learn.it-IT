---
title: Blueprint per hub delle attività dei clienti
description: '[!UICONTROL Le ricerche in Real-time Customer Profile forniscono informazioni sul contesto utili per fornire assistenza tecnica e commerciale mediante un operatore.]'
solution: Experience Platform,Data Collection
kt: 7195
exl-id: 3616cbf1-2e59-4e68-a1ff-1d2e3b344a1c,4f15aa5d-9ee3-4d92-8012-3e2f0c0d615f
translation-type: tm+mt
source-git-commit: 762836aba236ed78f4f396e8521a99c775dd52fc
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 72%

---

# Blueprint per hub delle attività dei clienti

Il blueprint per hub delle attività dei clienti mostra come le applicazioni esterne possono accedere a [!UICONTROL Real-time Customer Profile] di Adobe Experience Platform.

Le applicazioni esterne possono accedere ai profili con una richiesta di GET API. Gli attributi, gli eventi, le appartenenze ai segmenti e le funzioni basate sul modello memorizzati nel profilo possono quindi essere utilizzati anche in tali applicazioni esterne non Adobe.

Grazie a questa funzionalità, quando un cliente chiama il call center è possibile far emergere un contesto articolato. Gli operatori del supporto potrebbero, ad esempio, avere visibilità sul valore del ciclo di vita del cliente, sulla sua propensione all’abbandono o sulle campagne di marketing a cui è stato esposto. Gli agenti di vendita possono inoltre trarre vantaggio da un maggior contesto o da una migliore comprensione del cliente.

>[!NOTE]
>
>La latenza corrente supportata dall’API di ricerca profilo è di circa 500 millisecondi, che rende questo approccio inadatto per l’integrazione del profilo con motori di decisione in tempo reale, ad esempio per la personalizzazione web o mobile della pagina corrente.

## Casi di utilizzo

* Contesto del consumatore più approfondito, per le interazioni tramite operatore, come le esperienze di assistenza tecnica o commerciale. Utilizzando la ricerca del profilo in Experience Platform, gli agenti possono ricevere maggiori informazioni di contesto sul cliente, come acquisti recenti, interazioni con le campagne, tendenze, pubblico di appartenenza e altri attributi e informazioni che vengono memorizzati nel profilo del cliente in tempo reale.

## Architettura

<img src="assets/customer_activity_hub.svg" alt="Architettura di riferimento per il blueprint per hub delle attività dei clienti" style="border:1px solid #4a4a4a" />


## Guardrail

* [Guardrail per i dati di Real-time Customer Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)

## Fasi di implementazione

1. Configurare i set di dati e gli schemi.
1. Configura [!UICONTROL Profilo cliente in tempo reale]: configura lo schema e il set di dati per [!UICONTROL Profilo cliente in tempo reale] e configura un criterio di unione e le identità.
1. Inserire i dati in Platform ed elaborarli per [!UICONTROL Real-time Customer Profile].


1. [Creare ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html) schemi per l’acquisizione dei dati.
1. [Crea ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) set di dati per i dati da acquisire.
1. [Configurare correttamente le identità e i relativi namespace nello schema, affinché i dati acquisiti possano essere uniti in un profilo unificato.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)
1. [Attivare lo schema e i set di dati per il profilo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Acquisire i dati in Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion).
1. [Imposta criteri di unione](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html)
1. Utilizza l’ [API Entità per cercare un attributo di profilo](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html), dall’entità record o dall’entità evento esperienza.

## Documentazione correlata

* [Descrizione del prodotto Adobe Experience Platform Activation](https://helpx.adobe.com/it/legal/product-descriptions/adobe-experience-platform0.html)
* [Documentazione di Real-time Customer Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=it)
* [Guardrail per il profilo](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
* [API di ricerca profilo](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
