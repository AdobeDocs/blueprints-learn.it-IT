---
title: Creazione elemento decisione
description: Scopri le differenze tra gli attributi degli elementi di decisione e le impostazioni di idoneità, oltre al guardrail a livello di organizzazione sugli elementi di decisione e sulle impression rispetto agli eventi di decisione.
doc-type: article
solution: Experience Platform
exl-id: 28752ac1-118c-41d9-af6a-9907f854df1e
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# Creazione elemento decisione

## Finalità di apprendimento

Al termine di questa lezione, sarai in grado di:

- Differenziare gli attributi di un elemento di decisione dalle relative impostazioni di idoneità
- Indica il guardrail sugli elementi decisionali per organizzazione IMS e perché è a livello di organizzazione, non di sandbox
- Distinguere un’impression da un evento decisionale
- Differenziare le regole di decisione dai tipi di pubblico per ambito, tempistica e dati a cui ciascuno può accedere

## Materiali necessari

- 12 carte da gioco (Jack, Queen, King da ogni seme)
- 12 note, con nomi di attributi già scritti nella lezione precedente

## Lezione

Questa è la lezione più pratica che abbiamo visto finora: allegherai una nota a ogni scheda, poi dovrai metterla in pausa più volte per scrivere i valori di livello, capacità, visualizzazione, fotocamera, priorità e idoneità man mano che ogni concetto viene introdotto.

>[!VIDEO](https://video.tv.adobe.com/v/3502207/)

## Punti chiave da eliminare

- Un elemento decisionale si compone di due metà: attributi (nome, descrizione, attributi personalizzati, tag, priorità) e idoneità (date, inclusione della regola di decisione, inclusione del pubblico, limiti).
- Un cliente può avere fino a 10.000 elementi di decisione; tale limite si riferisce all’organizzazione IMS e non alla sandbox
- I punteggi di priorità più alti vengono restituiti per primi
- Una regola di decisione è un if/true con ambito condizionale per una singola campagna o percorso, valutato al momento della decisione e in grado di utilizzare gli attributi degli elementi di decisione; un pubblico è un gruppo più ampio di profili, valutato alla velocità batch/streaming/edge e non può accedere agli attributi degli elementi di decisione
- Utilizza una regola di decisione invece di un pubblico quando l’idoneità dipende dagli attributi propri dell’elemento di decisione
- Un elemento decisionale può contenere più di un trigger di limite (impression, clic, eventi di decisione, eventi personalizzati) alla volta
- Un’impression conta quando l’elemento viene effettivamente visualizzato al limite; un evento decisionale conta ogni volta che il processo decisionale valuta e restituisce una risposta, visualizzata o meno
- La limitazione viene ripristinata ogni giorno, ogni settimana o ogni mese a mezzanotte GMT (ora locale)
