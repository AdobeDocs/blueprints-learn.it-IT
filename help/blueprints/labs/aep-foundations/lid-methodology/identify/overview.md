---
title: Identificare
description: 'Scopri il passaggio Identify in due parti della metodologia LID: etichettatura dei tipi di tabella rimanenti e identificazione dei campi di identità chiave.'
doc-type: article
solution: Experience Platform
exl-id: 83657cf0-db35-4d4d-8cfb-1934ff40baca
source-git-commit: 8fba6e953de0e588af5398b21554ebad085899fd
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---


# Identificare

## Obiettivi di apprendimento

Il passaggio **Identificare** nella metodologia LID è suddiviso in due parti distinte:

1. Parte 1 - Tipi di tabella rimanenti -> identificano le tabelle senza etichetta rimanenti ed etichettano il tipo di denormalizzazione
1. Parte 2 - Campi chiave -> identificare i campi chiave delle entità principali e di supporto



Ti insegnerà a identificare i seguenti elementi all’interno di un modello relazionale di cui avrai bisogno per progettare il Profilo cliente in tempo reale:

- Tabelle di Bridge (tabelle che gestiscono relazioni molti-a-molti)
- Tabelle che richiederanno la denormalizzazione
- Identità principali nel profilo cliente in tempo reale
- Identità basate su persona all’interno delle classi di entità primarie che possono essere utilizzate per identificare in modo univoco una persona
- Identificatori di relazione tra singole tabelle Profilo/Evento esperienza e tabelle di ricerca associate
- Campi richiesti necessari per gli schemi Experience Event
- Campi consigliati per profili individuali e schemi di ricerca
