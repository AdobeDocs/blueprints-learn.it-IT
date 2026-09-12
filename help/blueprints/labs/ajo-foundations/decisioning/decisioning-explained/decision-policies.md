---
title: Criteri di decisione
description: Scopri in che modo i criteri di decisione applicano le strategie di selezione a un canale di consegna e come i metodi di combinazione individuali rispetto a quelli raggruppati modificano l’ordine delle offerte.
doc-type: article
solution: Experience Platform
exl-id: 21dc67fd-76ac-4b82-ae78-be024c7bfc55
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Criteri di decisione

## Finalità di apprendimento

Al termine di questa lezione, sarai in grado di:

- Spiegare cosa configura un criterio di decisione e dove viene applicato
- Definire un pacchetto decisionale e cosa comprende
- Differenziare i metodi individuali e quelli raggruppati per combinare più strategie di selezione
- Spiegare in che modo il limite di frequenza interagisce con il numero di elementi decisionali restituiti da un criterio

## Materiali necessari

- 12 carte da gioco (Jack, Queen, King da ogni seme)
- 13 note adesive
  - 12 compilato con il nome attributo e i valori delle lezioni precedenti
  - Una nuova nota per tenere traccia delle richieste

## Lezione

Questa è la simulazione più lunga e coinvolgente del corso. Puoi simulare il comportamento delle politiche decisionali in tempo reale, effettuando ripetute &quot;richieste&quot;, tracciando le impression rispetto ai limiti di frequenza e guardando i biglietti ritirati e sostituiti, quindi applicare tutto a uno scenario di business reale confrontando la combinazione di strategie di selezione individuale e raggruppata.

>[!VIDEO](https://video.tv.adobe.com/v/3502211/)

## Punti chiave da eliminare

- Un criterio di decisione applica strategie di selezione a un canale di consegna AJO effettivo, configurato su un nodo di canale in un percorso o in una sezione di canale di una campagna
- Un criterio può utilizzare nessuna, una o più strategie di selezione; senza nessuna, restituisce gli elementi in base al punteggio di priorità originale, filtrato per idoneità a livello di elemento
- Una policy decisionale e il relativo canale di distribuzione sono denominati insieme pacchetti decisionali, ossia la configurazione che risiede nell’hub o al limite
- Con la combinazione singola, ogni raccolta di strategie viene ordinata separatamente, quindi gli elenchi vengono impilati; con raggruppati, tutti gli elementi vengono ordinati insieme in un unico elenco e i duplicati utilizzano il più alto dei loro due punteggi
- Gli stessi input possono produrre ordini finali notevolmente diversi a seconda dei singoli utenti e dei gruppi
- Il limite di frequenza limita direttamente il numero di articoli disponibili da restituire, pertanto pianifica un numero sufficiente di articoli di fallback non limitati per riempire ogni slot
