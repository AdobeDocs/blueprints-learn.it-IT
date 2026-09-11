---
title: Opzione
description: Crea un pubblico completamente in streaming utilizzando gli attributi di utilizzo preaggregati calcolati a monte invece di aggregare gli eventi all’interno della regola di pubblico.
doc-type: article
solution: Experience Platform
exl-id: fe6ee041-814f-41c1-91cf-c3473cbca0c2
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# Opzione #2: utilizzare preaggregati

La sfida con Aggregates nel nostro pubblico è che il nostro pubblico (in streaming), è basato su aggregazioni effettuate all&#39;interno di tipi di pubblico che sono tipi di pubblico in batch. Poiché il reparto marketing ha stabilito che è necessario un approccio più in tempo reale, abbiamo adottato tre misure per ottimizzare questo processo:

- Calcola gli aggregati prima di inviare i dati in streaming

>[!NOTE]
>
>Ciò è abbastanza raro, in quanto la maggior parte dei dati in streaming è progettata intorno a un singolo evento rispetto a un aggregato

- Utilizza il nome del piano denormalizzato
- Trasmetti i dati in

## Creare il pubblico

Crea un pubblico di tutti i profili con un utilizzo elevato dei dati di fatturazione, ma che al momento non dispongono di un piano telefonico definitivo.

1. Crea un nuovo pubblico
1. Cerca &quot;Agg&quot; nella scheda Attributi non evento e trascina i due aggregati sull’area di lavoro. Impostare gli operatori e i valori appropriati per ciascuno di essi.

   ![Impostare gli operatori e i valori appropriati per ogni aggregato](assets/option-2-use-pre-aggregates-set-operators-and-values.png)



3. Cercare il nome del piano nel profilo e aggiungerlo (Profilo individuale XDM > Dispositivo > Dettagli piano > Nome piano). Seleziona Does not Equal &quot;Ultimate&quot;

   ![Il nome del piano selezionato non è uguale a Ultimate](assets/option-2-use-pre-aggregates-select-does-not-equal-ultimate.png)



4. Fornisci una descrizione.  Il metodo di valutazione della convalida è Streaming.

5. Salva il pubblico come &quot;*Utilizzo dati fatturazione elevato ma nessun piano Ultimate (Agg)*&quot;

>[!NOTE]
>
>Ricordate, abbiamo spostato la logica aggregata nel livello ETL di streaming a monte.
>
>Questa scelta rappresenta un compromesso tra avere un pubblico batch in cui l’addetto al marketing controlla la logica e un pubblico in streaming, ma invia la definizione e il controllo al livello ETL in cui Engineering deve essere coinvolto.

>[!TIP]
>
>**Laboratorio di verifica facoltativo**
>
>Finito presto?
>
>Vorremmo contattare i nostri VIP in tempo reale con un messaggio speciale al momento dell’acquisto.  Crea un pubblico di &quot;VIP&quot;.  Un VIP è qualcuno che ha acquistato più di 1.000 dollari nell&#39;ultimo mese.
