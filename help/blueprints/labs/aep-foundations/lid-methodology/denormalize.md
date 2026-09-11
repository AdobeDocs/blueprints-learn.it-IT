---
hold: true
title: Denormalizza
description: Applicare le regole di denormalizzazione della metodologia LID per ripiegare il bridge e le tabelle dipendenti da un ERD nelle tabelle di profilo, evento e ricerca padre.
doc-type: article
solution: Experience Platform
exl-id: c98c9f58-03bc-4b28-becb-f84f3de04300
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---


# Denormalizza

## Lezione

In questo video scoprirai le tre regole di denormalizzazione per ripiegare le tabelle di ricerca e bridge nelle tabelle padre, oltre a come i requisiti di personalizzazione e segmentazione in streaming influiscono su tali decisioni.

>[!VIDEO](https://video.tv.adobe.com/v/3459083/?quality=12&learn=on)



## Dettagli laboratorio

>[!NOTE]
>
>Questo laboratorio si concentra solo sull&#39;ERD del magazzino Connection 5G

## Regole di denormalizzazione:

1. Qualsiasi tabella nel modello relazionale etichettata come &quot;**D**&quot; con cardinalità 1\:M o &quot;**B**&quot; sarà definita come matrice o mappa di oggetti nella tabella padre
1. Attivato dalla regola #1, prima di denormalizzare le tabelle &quot;**D**&quot; o &quot;**B**&quot; che fungono da matrici o mappe, interrogarle per determinare il modo migliore per denormalizzarle nuovamente nella tabella padre
1. Qualsiasi tabella nel modello relazionale etichettata come &quot;**D**&quot; con cardinalità M:1 agirà come oggetto o come elenco di campi nella relativa tabella padre

## Denormalizzazione per le regole di personalizzazione:

Ricorda sempre di esaminare i casi di utilizzo dei clienti durante la creazione del modello dati.  Considera quanto segue:

- La segmentazione in streaming non ha accesso alle tabelle di ricerca al momento della valutazione
- Solo le caratteristiche e le appartenenze a segmenti di un profilo sono accessibili per la personalizzazione dei contenuti

![Casi d&#39;uso per la connessione 5G considerati durante l&#39;applicazione della denormalizzazione per la personalizzazione](assets/denormalize-connection-5g-use-cases.png "Casi d&#39;uso per la connessione 5G")

>[!NOTE]
>
>Ricorda di fare riferimento al Connection 5G Training Scenario.pdf durante questo laboratorio!



## Passaggio 1: compilare la tabella Profilo individuale

1. Scrivere i campi da denormalizzare nella tabella Account cliente da qualsiasi schema &quot;**B**&quot; o &quot;**D**&quot; correlato
1. Rivedere i casi d’uso al di sopra di quali campi aggiuntivi sono necessari per supportare la segmentazione in streaming e/o la personalizzazione? Aggiungi questi campi alla tabella



## Passaggio 2: compilare le tabelle degli eventi di esperienza

1. Scrivere i campi che devono essere denormalizzati nelle tabelle Fatturazione e Ordini da qualsiasi tabella &quot;**B**&quot; o &quot;**D**&quot; correlata
1. Rivedere i casi d’uso al di sopra di quali campi aggiuntivi sono necessari per supportare la segmentazione in streaming e/o la personalizzazione? Aggiungi questi campi alla tabella



## Passaggio 3: compilare le tabelle di ricerca

1. Scrivere i campi che devono essere denormalizzati nella tabella di ricerca dei prodotti da qualsiasi tabella &quot;**B**&quot; o &quot;**D**&quot; correlata
1. Rivedere i casi d’uso al di sopra di quali campi aggiuntivi sono necessari per supportare la segmentazione in streaming e/o la personalizzazione? Aggiungi questi campi alla tabella




## Revisione

Il video seguente illustra come le tabelle Connection 5G sono state denormalizzate in array e oggetti, e come i casi di utilizzo di acquisizione e upselling hanno richiesto di riportare campi aggiuntivi sul profilo principale e sulle tabelle degli eventi.

>[!VIDEO](https://video.tv.adobe.com/v/3459086/?quality=12&learn=on)
