---
hold: true
title: Convalida istantanea profilo
description: Scopri come eseguire query sul set di dati di istantanea profilo e perché un nuovo aggiornamento del profilo in streaming non viene visualizzato fino al successivo processo batch giornaliero.
doc-type: article
solution: Experience Platform
exl-id: 1e7befcf-d952-47a2-86d9-33ef71eec57a
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# Convalida istantanea profilo

## Finalità di apprendimento

Conferma che il profilo non sia ancora visualizzato nel set di dati Snapshot profilo.

## Utilizzare il set di dati Snapshot profilo

1. Nella barra di navigazione a sinistra, nella sezione Gestione dati, fai clic su **Set di dati**, quindi fai clic sulla **scheda Sfoglia** nella barra superiore

![Scheda Sfoglia set di dati nella sezione Gestione dati](assets/validate-profile-snapshot-datasets-browse-tab.png)

&#x200B;2. Nella **casella di ricerca** digitare `profile`, quindi **fare clic sulla riga** con il titolo &quot;Profile-Snapshot...&quot;.   e nella barra a destra **copia il nome della tabella** e incollalo da qualche parte a cui puoi fare riferimento nel passaggio successivo.

&#x200B;> [!NOTE]
>
>Potrebbe essere necessario cancellare tutti i filtri se non viene visualizzato &quot;Profile-Snapshot...&quot; set di dati.



![Risultati della ricerca per il set di dati Profilo-Snapshot](assets/validate-profile-snapshot-dataset-search.png)

&#x200B;3. Torna all’editor delle query, copia e incolla l’istruzione SQL seguente nell’editor

```sql
select
  identityMap,
  segmentID,
  segmentMembershipUps[segmentID] ['lastQualificationTime'],
  segmentMembershipUps[segmentID] ['status'],
  current_timestamp
from
  (
    select
      identityMap,
      explode (map_keys (segmentMembership['ups'])) as segmentID,
      segmentMembership['ups'] as segmentMembershipUps
    from
   
    where
      map_keys (segmentMembership['ups']) is not null
    limit 100
  )
  --where identityMap['email'][0].id = 'henry.creel@emailsim.io'
  limit 50
```

&#x200B;4. Aggiorna il nome della tabella e l’indirizzo e-mail come descritto di seguito:
   - **Nome tabella:** alla riga 14 copia e incolla il nome della tabella disponibile per la tabella snapshot del profilo tra `from` e `where`
   - **Indirizzo e-mail:** per il momento, digitare alla riga 19 nello stesso indirizzo e-mail utilizzato per inviare l&#39;evento Web (abbiamo utilizzato henry.creel\@emailsim.io, a meno che non sia stato modificato).
     - Al momento, abbiamo commentato questo (lascialo così). Quando la query viene eseguita e cerchi Henry, non lo trovi.

![Editor query con il nome della tabella snapshot del profilo e l&#39;indirizzo di posta elettronica da aggiornare](assets/validate-profile-snapshot-update-query-table-name.png)

&#x200B;5. **Esegui** la query facendo clic sulla freccia in alto a sinistra
&#x200B;6. I risultati sono i seguenti (ma se cerchi henry, non lo trovi)

![I risultati della query non mostrano alcuna corrispondenza per il profilo in streaming nello snapshot](assets/validate-profile-snapshot-query-results-no-match.png)

>[!NOTE]
>
>**Perché nessun risultato per Henry?**
>
>**Promemoria**: lo snapshot del profilo è un **reflection** o uno snapshot di ciò che esisteva nel profilo in un **momento specifico**. Il processo viene eseguito **ogni giorno** e viene utilizzato per scopi downstream come AJO. Poiché hai appena eseguito lo streaming di questi dati, lo snapshot del profilo non ne è ancora disponibile.  Lo farà domani.

## Riassunto

I set di dati snapshot vengono aggiornati in un processo batch pianificato anziché immediatamente.
