---
hold: true
title: Sfoglia abbandonata
description: Scopri come creare un flusso di lavoro decisionale completo e abbandonato per la navigazione che offra offerte telefoniche personalizzate e basate sull’idoneità tra i canali.
doc-type: overview-page
solution: Experience Platform
exl-id: 37b8a0b3-2820-4303-81d2-19890a3c5782
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---


# Sfoglia abbandonata

## Prerequisiti

>[!WARNING]
>
>Prima di avviare questo laboratorio, è necessario aver completato i seguenti laboratori

- **Archivi dati — Profilo in azione** **—>** [Crea flusso di dati](../../data-stores/profile-in-action/create-datastream.md)

Se non hai completato queste esercitazioni, fallo adesso prima di continuare.

## Panoramica di Lab

Questo video illustra come la descrizione del caso d’uso abbandonato per i browser riveli gli elementi decisionali e cosa verrà realizzato in questo laboratorio per offrire in tempo reale un’offerta telefonica personalizzata e basata su criteri di idoneità.

>[!VIDEO](https://video.tv.adobe.com/v/3491316/)

## Obiettivi aziendali

Il caso d’uso aziendale di questo laboratorio è che Connection 5G vuole aumentare le vendite del nuovo telefono di punta di Apple, iPhone 17, rivolgendosi ai clienti che hanno navigato nella pagina della panoramica di iPhone 17 ma non hanno acquistato. Gli obiettivi principali della campagna sono i seguenti:

- **Identifica i clienti ad alto intento** rilevando quando un utente visualizza più volte una pagina di telefono di punta senza completare un acquisto.
- **Attiva un&#39;esperienza personalizzata in tempo reale** su tutte le superfici digitali di proprietà di Connection 5G quando si verifica questo comportamento.
- **Distribuisci offerte contestuali** in base agli attributi chiave del cliente, ad esempio **età del titolare dell&#39;account** e il relativo **piano mobile corrente**.
- **Assicurati che l&#39;idoneità per le offerte sia applicata** in modo che i clienti vedano solo le offerte telefoniche compatibili con il proprio piano.
- **Regola dinamicamente il livello telefonico offerto** (ad es. base, pro, ultra) in base al coinvolgimento del cliente o alla risposta alle offerte precedenti.
- **Fornisci una personalizzazione coerente tra i canali** utilizzando la logica decisionale centralizzata per determinare l&#39;offerta migliore in tempo reale.
- **Aumenta la probabilità di conversione** presentando l&#39;offerta telefonica di punta più pertinente a ciascun cliente al momento giusto.

## Obiettivi di apprendimento del laboratorio

Per soddisfare i suddetti obiettivi di business in questo laboratorio, imparerai a:

- **Estendi il modello dati dell&#39;offerta** aggiungendo attributi personalizzati allo schema dell&#39;offerta in modo che possano essere utilizzati nella logica decisionale.
- **Crea regole di idoneità** che determinano quali profili sono idonei per offerte specifiche in base agli attributi del profilo.
- **Crea e configura gli elementi dell&#39;offerta**, incluse l&#39;impostazione delle priorità, la definizione delle condizioni di idoneità e l&#39;applicazione di limiti di frequenza.
- **Organizza le offerte in una raccolta** in modo che possano essere facilmente referenziate e valutate durante l&#39;attività Decisioning.
- **Crea una formula di classificazione** che regola dinamicamente la priorità dell&#39;offerta in base alle caratteristiche del profilo.
- **Configura una strategia di selezione** che combina raccolte di offerte, regole di idoneità e logica di classificazione per determinare quali offerte vengono considerate e come vengono ordinate.
- **Configura un canale di esperienza basata su codice** per consentire ai sistemi esterni di richiedere risultati decisionali e ricevere offerte in formato JSON.
- **Verifica il flusso di lavoro decisionale end-to-end** inviando eventi di esperienza e richieste di decisione per convalidare la logica di idoneità, il comportamento di classificazione e i limiti di frequenza.

Completando questa esercitazione, acquisirai un&#39;esperienza pratica nella progettazione e nella convalida di un **flusso di lavoro completo di offer decisioning in Adobe Journey Optimizer** per soddisfare il caso d&#39;uso aziendale.
