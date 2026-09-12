---
title: Imposta inoltro eventi
description: Scopri come l’inoltro degli eventi utilizza proprietà, elementi dati, regole e flussi di dati per inoltrare eventi edge a un endpoint di terze parti.
doc-type: overview-page
solution: Experience Platform
exl-id: da3d1c7f-3642-4de7-a297-fc36d09e7336
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# Imposta inoltro eventi

L’inoltro degli eventi si trova su Edge e consente di creare un set di regole e trasformazioni leggere per inviare eventi a qualsiasi endpoint.

A questo punto, inoltreremo a un webhook tutti gli eventi che invieremo all’Edge. Il webhook fungerà da proxy per una terza parte e ci consentirà di vedere cosa sta succedendo.

Per configurare questo, verrà impostato:

- Una proprietà che contiene tutte le estensioni, gli elementi dati e le regole necessari per decidere cosa inoltrare e dove
  - Un elemento dati per fare riferimento all’evento in ingresso o analizzarlo in più componenti singoli, se necessario
  - Una regola per aggiungere condizioni su cosa inoltrare, trasformare il payload e dove inviarlo
- Un flusso di dati che configura quali servizi lo utilizzeranno (ad esempio, Inoltro eventi e AEP)
  - I dati inviati a questi flussi di dati possono quindi intervenire in base al servizio configurato (ad esempio, inoltrare un evento e inviare dati a un set di dati)
