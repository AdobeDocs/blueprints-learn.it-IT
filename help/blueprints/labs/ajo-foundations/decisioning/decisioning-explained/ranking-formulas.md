---
hold: true
title: Classificazione delle formule
description: Scopri come la classificazione delle formule regola dinamicamente il punteggio di priorità di un elemento decisionale per profilo utilizzando le espressioni matematiche condizionali.
doc-type: article
solution: Experience Platform
exl-id: 08183f1a-8db6-43c5-8b2e-05fa3d9c0f8d
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# Classificazione delle formule

## Finalità di apprendimento

Al termine di questa lezione, sarai in grado di:

- Definire una formula di classificazione e spiegarne le modifiche
- Spiegare la struttura if/then di una regola formula di classificazione
- Spiega perché ogni impostazione della formula di classificazione richiede una formula predefinita
- Determinare il risultato quando due elementi di decisione arrivano sullo stesso punteggio di priorità adeguato

## Materiali necessari

- 12 carte da gioco (Jack, Queen, King da ogni seme)
- 12 note di Sticky Notes, compilate con il nome attributo e i valori delle lezioni precedenti

## Lezione

Questa lezione prevede diversi cicli di riordinamento manuale delle schede, prima in base alla priorità originale e poi in base a due diverse formule di classificazione applicate a profili di esempio diversi, in modo da poter vedere come lo stesso set di elementi viene rimpastato a seconda di chi glielo chiede.

>[!VIDEO](https://video.tv.adobe.com/v/3502209/)

## Punti chiave da eliminare

- Una formula di classificazione regola dinamicamente il punteggio di priorità di un elemento decisione in base al profilo, in base agli attributi di profilo o all’evento esperienza che attiva
- Le formule supportano la matematica di base (aggiungere, sottrarre, moltiplicare, dividere) e possono fare riferimento al punteggio di priorità originale dell’elemento decisionale come variabile
- Logica della regola: se una condizione relativa al profilo o all’hit è vera, regola la priorità per gli elementi di decisione che soddisfano determinati criteri per gli elementi
- Per ogni impostazione della formula di classificazione è necessaria una formula predefinita per gli elementi decisionali che non vengono toccati dalla regola di adeguamento
- Quando due elementi di decisione arrivano sullo stesso punteggio di priorità adeguato, il processo decisionale li ordina in modo casuale
