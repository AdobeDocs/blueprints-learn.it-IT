---
title: Guardrail, modelli AI e il futuro del Decisioning
description: Scopri i guardrail decisionali chiave, come i modelli di classificazione di IA differiscono dalle formule e come i blocchi decisionali si connettono end-to-end.
doc-type: article
solution: Experience Platform
exl-id: 90902f6e-ba3c-4852-ab82-ad852698b227
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Guardrail, modelli AI e il futuro del Decisioning

## Finalità di apprendimento

Al termine di questa lezione, sarai in grado di:

- Ricorda le due protezioni più comunemente incontrate nella pratica
- Differenziare l’ottimizzazione automatica dai modelli di ottimizzazione personalizzata basati su IA
- Spiegare in che modo il processo decisionale si estende oltre il prodotto ODE legacy
- Riepilogare il modo in cui gli otto blocchi predefiniti si adattano, end-to-end

## Lezione

Il video seguente illustra i due guardrail decisionali più comuni, il modo in cui i modelli di classificazione basati sull’intelligenza artificiale differiscono dalle formule di classificazione manuali, il modo in cui il processo decisionale si estende oltre il motore Offer Decisioning legacy e un riepilogo del modo in cui gli otto blocchi predefiniti si connettono end-to-end.

>[!VIDEO](https://video.tv.adobe.com/v/3502212/)

## Punti chiave da eliminare

- I due guardrail più comunemente visitati: 10.000 elementi decisionali per organizzazione IMS (non per sandbox) e 100 attributi personalizzati per schema; controlla la documentazione del prodotto per i numeri correnti, in quanto sono soggetti a modifiche
- I modelli di IA possono essere utilizzati all’interno di formule di classificazione; l’ottimizzazione automatica non è personalizzata e si ottimizza in base alle prestazioni globali, mentre l’ottimizzazione personalizzata fornisce elementi verso obiettivi aziendali specifici per profilo
- I punteggi del modello calcolati al di fuori di AEP possono essere inseriti come attributi di profilo e utilizzati nelle regole di idoneità o nelle formule di classificazione
- Il processo decisionale va oltre il precedente motore Offer Decisioning: utilizza XDM per la riutilizzabilità, distribuisce JSON alle applicazioni headless e separa l’elemento decisionale dal trattamento
- Il processo decisionale può condizionare il percorso del percorso e la priorità di immissione in una risposta decisionale
- End-to-end: l’elemento di decisione XDM definisce gli attributi → la creazione dell’elemento di decisione assegna valori e idoneità → raccolte elementi di gruppo → formule di classificazione regola la priorità per profilo → strategie di selezione classifica e filtra una raccolta → criteri di decisione applica strategie a un canale → i pacchetti di decisione sono live sull’hub o sul perimetro
