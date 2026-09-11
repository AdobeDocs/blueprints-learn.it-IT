---
hold: true
title: Verifica profilo acquisito
description: Cerca un profilo in streaming nel browser Profili utilizzando il relativo spazio dei nomi dell’identità primaria per confermare la corretta acquisizione.
doc-type: article
solution: Experience Platform
exl-id: d45d6baf-9597-4419-b838-03156ce8cc83
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# Verifica profilo acquisito

## Convalida streaming

La convalida dei dati in streaming in Adobe Experience Platform richiede alcuni passaggi diversi.  Ricorda che i dati in streaming possono scrivere su più database a seconda della configurazione del set di dati.

| Archiviazione | Latenza | Descrizione |
| -------------- | -------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Data Lake | \~fino a 60 minuti | Luogo di riposo finale per tutti i dati in streaming |
| Archivio profili | \~1 minuto in media ma fino a \~15min | Elabora i dati solo quando il set di dati sottostante è abilitato per il profilo |
| Archivio identità | \~1 min medio \~10 min micro-batch per nuove relazioni di identità | Elabora i dati solo quando il set di dati sottostante è abilitato per il profilo |

A seconda di ciò che stai tentando di convalidare, potrebbe essere necessario recarsi in alcuni luoghi diversi, come puoi vedere dall’alto.  In questo scenario, hai scritto i dati nel profilo (poiché hai abilitato il set di dati per il profilo), quindi controlla l’archivio profili per verificare se il profilo è presente.



## Cercare il profilo

1. Nell&#39;interfaccia utente passa a **Profili -> Sfoglia**
1. Immetti i seguenti valori nelle caselle di input Spazio dei nomi identità e Valore identità:
   - **Spazio dei nomi identità** -> `customerID`
   - **Valore identità** -> `202208240125`
1. Fai clic sul pulsante **Visualizza** per cercare il tuo profilo
1. Fai clic sul collegamento **ID profilo** nella riga restituita per visualizzare il profilo

![Sfoglia la schermata del profilo che mostra la riga del profilo restituita dopo la ricerca per customerID](assets/verify-ingested-profile-browse-profile-screen.png "Sfoglia la schermata del profilo")

Dai un&#39;occhiata al tuo profilo e verifica che corrisponda a quello trasmesso in streaming. Fantastico, eh!

![Visualizzazione dettagli profilo corrispondente al record Account cliente in streaming](assets/verify-ingested-profile-profile-detail-view.png)

>[!NOTE]
>
>Data la latenza di \~10min sull’unione di nuove relazioni di identità, se avessi cercato di cercare il tuo profilo utilizzando lo spazio dei nomi e-mail non avresti visto una risposta.
>
>L’utilizzo dello spazio dei nomi customerID (che è l’identità principale) ti ha consentito di cercare il profilo immediatamente.
>
>Ricorda che il profilo conosce solo le identità primarie 😄
