---
title: Casi di utilizzo della tecnologia
description: Scopri in che modo le organizzazioni tecnologiche utilizzano Adobe Experience Platform per unificare la raccolta dati, inoltrare gli eventi in tempo reale e potenziare l’analisi e l’attivazione tra i prodotti digitali.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: a1b2c3d4-e5f6-7890-abcd-ef1234567890
source-git-commit: 77908fd8a9f4309cbe66063cd33f065424697e55
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Casi di utilizzo della tecnologia

Le organizzazioni tecnologiche utilizzano Adobe Experience Platform per centralizzare la raccolta dei dati da web, dispositivi mobili e superfici di prodotto e distribuire eventi in tempo reale ad analisi, data warehouse e destinazioni di attivazione che alimentano i loro prodotti e programmi di marketing. Consolidando la raccolta degli eventi a livello perimetrale, i team tecnologici riducono la complessità lato client, migliorano la qualità dei dati e garantiscono che tutti i sistemi a valle ricevano dati comportamentali coerenti da un&#39;unica origine autorevole.

## Inoltro eventi in tempo reale

Inoltra gli eventi comportamentali in tempo reale raccolti tramite Edge Network ad analisi di terze parti, data warehouse e piattaforme partner per l’arricchimento e l’attivazione. La centralizzazione della raccolta degli eventi ai confini e dell’inoltro a più destinazioni riduce il sovraccarico dei tag lato client, migliora la qualità dei dati e garantisce che tutti i sistemi a valle ricevano dati coerenti degli eventi da un’unica origine autorevole.

### Impatto aziendale

Le organizzazioni tecnologiche che implementano l’inoltro degli eventi in tempo reale riducono il carico di tag lato client e il relativo sovraccarico di prestazioni, migliorando al contempo la coerenza dei dati dell’evento tra le destinazioni di analisi, data warehouse e attivazione. L’inoltro lato server riduce inoltre il peso delle pagine e migliora le prestazioni di carico, a diretto vantaggio delle metriche di esperienza utente.

### Come implementare

Utilizza il pattern [Inoltro eventi](/help/blueprints/use-case-patterns/audience-building-activation/event-forwarding.md) per instradare gli eventi raccolti da Adobe Experience Platform Web SDK tramite Edge Network alle destinazioni lato server configurate. Questo è il modello corretto quando l’obiettivo è la distribuzione degli eventi da server a server da un singolo punto di raccolta, anziché gestire tag separati per ogni destinazione sul lato client, il che aumenta il peso della pagina e crea incoerenza dei dati tra i sistemi.

### Considerazioni tecniche

- L’inoltro degli eventi di Edge Network richiede la migrazione della raccolta di eventi a Adobe Experience Platform Web SDK o Mobile SDK; le implementazioni esistenti basate su tag devono essere valutate per la compatibilità prima di configurare le destinazioni di inoltro.
- Le regole di inoltro devono essere configurate in modo da inviare solo i campi richiesti da ciascuna destinazione; evita di inoltrare payload XDM completi a destinazioni che necessitano solo di un piccolo sottoinsieme di campi, in quanto ciò aumenta i costi di trasferimento dei dati e crea un’esposizione alla conformità.
- I connettori di destinazione devono gestire correttamente gli errori; le pipeline di inoltro eventi devono implementare una logica di nuovi tentativi e un avviso per le destinazioni che non sono più disponibili, al fine di evitare la perdita di dati durante le interruzioni.
- I criteri di governance dei dati devono essere rivisti per ogni destinazione di inoltro per garantire che le preferenze di consenso degli utenti acquisite al limite siano rispettate nella configurazione di inoltro.
