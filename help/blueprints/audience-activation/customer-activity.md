---
title: Blueprint per hub delle attività dei clienti
description: '[!UICONTROL Le ricerche in Real-time Customer Profile forniscono informazioni sul contesto utili per fornire assistenza tecnica e commerciale mediante un operatore.]'
solution: Experience Platform,Data Collection
kt: 7195
exl-id: 3616cbf1-2e59-4e68-a1ff-1d2e3b344a1c,4f15aa5d-9ee3-4d92-8012-3e2f0c0d615f
translation-type: tm+mt
source-git-commit: da21d1796eb9a2c9c0f087d82606874ca55bd4ea
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 90%

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
1. Utilizzare l’API Entity per cercare un attributo di profilo, dall’entità record o dall’entità dell’evento dell’esperienza.

## Documentazione correlata

* [Descrizione del prodotto Adobe Experience Platform Activation](https://helpx.adobe.com/it/legal/product-descriptions/adobe-experience-platform0.html)
* [Documentazione di Real-time Customer Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=it)
* [Guardrail per il profilo](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
* [API di ricerca profilo](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
