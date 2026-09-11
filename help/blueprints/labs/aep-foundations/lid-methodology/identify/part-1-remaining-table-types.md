---
hold: true
title: Parte 1 - Tipi di tabella rimanenti
description: Identifica ed etichetta le tabelle e le tabelle bridge che richiedono la denormalizzazione nei singoli ERD di profilo, evento esperienza e ricerca.
doc-type: article
solution: Experience Platform
exl-id: 742b58fa-3feb-4275-ab45-eb8d3aade22c
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---


# Parte 1 - Tipi di tabella rimanenti

## Lezione

Questo video illustra come etichettare le restanti tabelle senza etichetta con un tipo di denormalizzazione D o B, incluso il modo in cui Bridge Table Rule #1 trasforma il lato molti-a-uno di una tabella bridge in una ricerca.

>[!VIDEO](https://video.tv.adobe.com/v/3459082/?quality=12&learn=on)



## Dettagli laboratorio

Identificare ed etichettare le tabelle nel data warehouse di Connection 5G e le ERD streaming che rientrano in una delle categorie seguenti

- Tabella Bridge (etichettata come &quot;**B**&quot;)
- Nuove tabelle di ricerca esistenti a causa di tabelle bridge
- Tabelle che richiederanno la denormalizzazione (etichettate come &quot;**D**&quot;)

>[!CAUTION]
>
>L&#39;ordine è molto importante qui! Assicurati di seguire i passaggi in ordine in quanto ogni passaggio dipende dal precedente



## Passaggio 1: identificazione ed etichettatura delle singole tabelle di profilo XDM

1. Identifica tutte le tabelle direttamente correlate (un hop di distanza) alle tabelle Profilo individuale XDM che non dispongono ancora di un’etichetta. Contrassegnale con una stella &quot;**\***&quot;.
1. Osservando solo gli schemi appena etichettati con una stella, effettuare le seguenti operazioni:
   1. **Aggiungere un&#39;etichetta &quot;B&quot; per la tabella del bridge**. Una tabella viene considerata una tabella del bridge quando due o più tabelle sono correlate ad essa con il lato molti della relazione da entrambe le tabelle che puntano alla tabella del bridge
   2. **Aggiungere un&#39;etichetta &quot;D&quot; per le tabelle da denormalizzare** - qualsiasi entità con cardinalità 1\:M o M:1 con la tabella con etichetta Profilo individuale XDM e non già contrassegnata

>[!NOTE]
>
>Memorizza #1. regole tabella Bridge
>
>Quando si incontra una tabella bridge direttamente correlata a una &quot;P&quot; o a una &quot;E&quot;, la relazione M:1 agisce come una ricerca. In caso contrario, segui le regole di denormalizzazione standard.



## Passaggio 2: identificare ed etichettare le tabelle XDM Experience Event

1. Identifica tutte le tabelle direttamente correlate (un hop di distanza) alle tabelle etichettate Experience Event che non dispongono ancora di un’etichetta. Contrassegnale con una stella.
1. Osservando solo le tabelle a cui è stata applicata una stella, eseguire le operazioni seguenti:
   1. **Aggiungere un&#39;etichetta &quot;B&quot; per le tabelle del bridge**. Una tabella viene considerata una tabella del bridge quando due o più tabelle sono correlate ad essa con il lato molti della relazione che punta alla tabella del bridge
   2. **Aggiungi un&#39;etichetta &quot;D&quot; per le tabelle da denormalizzare** - qualsiasi tabella con cardinalità 1\:M o M:1 con la tabella etichettata XDM Experience Event e non già contrassegnata

>[!NOTE]
>
>Memorizza #1. regole tabella Bridge
>
>Quando si incontra una tabella bridge direttamente correlata a una &quot;P&quot; o a una &quot;E&quot;, la relazione M:1 agisce come una ricerca. In caso contrario, segui le regole di denormalizzazione standard.



## Passaggio 3: identificare ed etichettare le tabelle di ricerca

1. Identifica tutte le tabelle correlate a (non importa quanti passaggi si effettuano) una qualsiasi delle tabelle con etichetta di ricerca che non hanno ancora un’etichetta. Contrassegnale con una stella &quot;**\***&quot;.
1. Osservando solo le tabelle a cui è stata applicata una stella, eseguire le operazioni seguenti:
   1. Aggiungere un&#39;etichetta &quot;**B**&quot; per le tabelle bridge. Una tabella viene considerata una tabella bridge quando due o più tabelle sono correlate ad essa con il lato molti della relazione che punta alla tabella bridge
   2. Aggiungere un&#39;etichetta &quot;**D**&quot; per le tabelle da denormalizzare - qualsiasi tabella con cardinalità 1\:M o M:1 con una tabella di ricerca o una tabella di ponte correlata a una ricerca

>[!NOTE]
>
>Memorizza #1. regole tabella Bridge
>
>Quando si incontra una tabella bridge direttamente correlata a una &quot;P&quot; o a una &quot;E&quot;, la relazione M:1 agisce come una ricerca. Altrimenti seguire le regole di denormalizzazione standard **(hint, hint)**



## Revisione

Il video seguente analizza le etichette D e B corrette per il data warehouse di Connection 5G e le ERD in streaming, tra cui il motivo per cui il tipo di prodotto è una tabella denormalizzata anziché una ricerca.

>[!VIDEO](https://video.tv.adobe.com/v/3459064/?quality=12&learn=on)
