---
title: Blueprint di Customer Activity Hub
description: Ricerche Profilo cliente in tempo reale per fornire contesto per il supporto e le vendite assistito dagli agenti.
solution: Experience Platform,Data Collection
kt: 7195
exl-id: 3616cbf1-2e59-4e68-a1ff-1d2e3b344a1c,4f15aa5d-9ee3-4d92-8012-3e2f0c0d615f
translation-type: tm+mt
source-git-commit: 98d44067a1640dc8b695cb0d25f69ec26be647e1
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# Blueprint di Customer Activity Hub

La Blueprint dell’attività cliente mostra come le applicazioni esterne possono accedere al profilo cliente in tempo reale di Adobe Experience Platform.

Le applicazioni esterne possono accedere ai profili cliente in tempo reale con una richiesta di GET API. Gli attributi, gli eventi, le appartenenze ai segmenti e le funzionalità basate su modelli memorizzate nel profilo possono quindi essere utilizzati in queste applicazioni esterne non di Adobe.

Grazie a questa funzionalità, potresti visualizzare un contesto ricco quando un cliente chiama il tuo call center. Gli agenti di supporto possono avere visibilità del valore del ciclo di vita del cliente, della propensione a abbandono o dell’esposizione alle campagne di marketing, ad esempio. Gli agenti di vendita possono anche trarre vantaggio da un contesto più ampio o da informazioni approfondite sui loro clienti.

>[!NOTE]
>
>La latenza corrente supportata dall’API di ricerca del profilo è di circa 500 millisecondi, il che rende questo approccio inadatto all’integrazione del profilo con motori decisionali in tempo reale, come la personalizzazione web della stessa pagina o mobile.

## Casi d&#39;uso

* Fornire un contesto di consumo più profondo alle interazioni supportate dagli agenti, ad esempio le esperienze di supporto e di vendita. Utilizzando la ricerca di profilo nell’Experience Platform, gli agenti possono ricevere più contesto sul consumatore, ad esempio acquisti recenti, interazioni di campagna, proprietà, appartenenze al pubblico e altri attributi e informazioni memorizzati nel profilo del cliente in tempo reale.

## Architettura

<img src="assets/cah.svg" alt="Architettura di riferimento per la blueprint di Customer Activity Hub" style="border:1px solid #4a4a4a" />

## Guardrail

* [Guardrail per dati Profilo cliente in tempo reale](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

## Passaggi di implementazione

1. Configura set di dati e schemi.
1. Configura i [!UICONTROL profili cliente in tempo reale]: configura lo schema e il set di dati per [!UICONTROL Profilo cliente in tempo reale] e configura un criterio di unione e le identità.
1. Acquisisci i dati in Platform ed elaborali in [!UICONTROL Profilo cliente in tempo reale].
1. Utilizza l’API di entità per cercare un attributo di profilo, dall’entità record o dall’entità evento esperienza.

## Documentazione correlata

* [Descrizione del prodotto Adobe Experience Platform Activation](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform0.html)
* [Documentazione del profilo cliente in tempo reale](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=en)
* [Guardrail profilo](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
* [API di ricerca del profilo](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
