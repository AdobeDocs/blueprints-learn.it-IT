---
hold: true
title: Lezione
description: Esplora il modello anatomico dei contenuti a quattro livelli, i modelli di integrazione dei contenuti AJO e AEM e la governance dei contenuti assistiti da AI per la personalizzazione su larga scala.
doc-type: article
solution: Experience Platform
exl-id: 1ac39a70-51f8-426e-97cf-1ff08450d326
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---


# Lezione

## Obiettivi di apprendimento

- Spiegare perché il contenuto, non dati o percorsi, è il vincolo principale nei programmi di personalizzazione su larga scala
- Descrizione del modello anatomico dei contenuti a quattro livelli: risorse, frammenti, modelli e messaggi
- Differenziare tra frammenti di AJO e frammenti di contenuto di AEM, incluso il modo in cui ciascuno di essi gestisce la propagazione
- Mappare le fasi del ciclo di vita dei contenuti: creazione, archiviazione, gestione, gestione, attivazione e misurazione
- Confronta i tre modelli di integrazione dei contenuti: AJO Standalone, AJO + AEM Assets e AJO + GenStudio for Performance Marketing
- Identificare i segnali architettonici che indicano quando passare da un modello all&#39;altro
- Descrivi i tre livelli di funzionalità IA nello stack di Adobe: Assistente contenuti, Modelli personalizzati Firefly e Unified Brand Service
- Spiegare il principio della supervisione human-in-the-loop nei flussi di lavoro di contenuti basati sull’intelligenza artificiale
- Distinguere la vera personalizzazione dall’inserimento del nome o dalla moltiplicazione delle risorse

## Video

Questo video illustra il modello anatomico dei contenuti a quattro livelli, i tre modelli di integrazione dei contenuti di AJO e il modo in cui le funzionalità di intelligenza artificiale si adattano a un sistema di contenuti gestito.

>[!VIDEO](https://video.tv.adobe.com/v/3491063/?quality=12&learn=on)

## Punti chiave da eliminare

La scalabilità di Personalization dipende da tre pilastri: contenuto, dati e percorsi. La maggior parte delle aziende investe molto nei dati e nell’orchestrazione dei percorsi, ma considera i contenuti come un pensiero successivo. Questo è esattamente il motivo per cui i contenuti vengono prima interrotti dai programmi di personalizzazione. Per un architetto di AJO, capire come strutturare il contenuto come sistema gestito, anziché come una pila di risorse una tantum, è ciò che separa un’implementazione scalabile da una che collassa sotto la relativa espansione dei modelli.

**In questa lezione hai trattato:**

- La tesi: la personalizzazione non ha esito negativo a causa dei dati, ha esito negativo perché il contenuto non è progettato come sistema
- L’anatomia dei contenuti a quattro livelli: Assets (elemento multimediale atomico nel DAM), Frammenti (blocchi visivi o di espressione riutilizzabili), Modelli (zone bloccate o modificabili) e Messaggi (output finale assemblato, pronto per il canale)
- Il ciclo di vita dei contenuti: creare, archiviare, gestire, gestire, attivare, misurare e come gli errori si propagano da sinistra a destra quando viene saltata una fase
- Pattern 1, AJO standalone: ideale per il mercato singolo, a canale singolo, con meno di 50 varianti, quando la velocità è il vincolo principale; utilizza AEM Assets Essentials come DAM in bundle di base
- I frammenti di AJO vengono memorizzati in AJO e copiati in modelli come duplicati, senza aggiornamenti automatici e con un limite di 30 frammenti/1 livello di nidificazione
- Pattern 2, AJO + AEM: il migliore per le varianti multi-mercato, 50+, quando la governance è il vincolo principale; AEM diventa il sistema di registrazione, AJO il sistema di attivazione
- AJO fa riferimento (non copia) ai frammenti di contenuto di AEM, pertanto gli aggiornamenti si propagano istantaneamente su ogni modello, percorso e campagna di riferimento
- Tre scenari che interrompono automaticamente la propagazione dei frammenti: ereditarietà interrotta (frammento sbloccato), nuovi attributi di personalizzazione aggiunti a un frammento pubblicato e restrizioni delle etichette OLAC (Object Level Access Control)
- Pattern 3, AJO + GenStudio for Performance Marketing: ideale per la generazione di varianti su scala di produzione e per volumi elevati; richiede la governance Pattern 2 come prerequisito fondamentale
- I quattro pilastri che mantengono la generazione di intelligenza artificiale sul marchio: Unified Brand Service, Content Credentials, la cura umana nel ciclo e l’integrazione di AJO
- Architectural Decision Matrix e Content Supply chain Maturity Model (livelli da 1 ad hoc a 5 autonomi) per la diagnosi della posizione attuale di un cliente
- La vera personalizzazione è una variante intelligente all’interno di un singolo modello gestito, non campi unione di nome o campagne separate per segmento
