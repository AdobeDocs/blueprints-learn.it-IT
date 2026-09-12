---
title: Ottieni classe profilo
description: Chiama l’API del registro dello schema globale per recuperare e salvare il $id della classe XDM Individual Profile da utilizzare in uno schema personalizzato.
doc-type: article
solution: Experience Platform
exl-id: d87c21a2-dad4-4666-b917-cdf8e16058d4
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# Ottieni classe profilo

## Esegui il passaggio 3: ottieni classe profilo

1. Fai clic sulla richiesta `Step 3 - Get Profile Class` nella cartella `XDM API Lab -> Create Schema`
1. Eseguire facendo clic sul pulsante `Send`

![Passaggio 3 - Ottieni richiesta API classe profilo](assets/get-profile-class-step-3-api-request.jpeg "Passaggio 3 - Ottieni richiesta API classe profilo")

>[!NOTE]
>
>Si noti che nella richiesta GET il percorso `global`: .../schemaregistry/**global**/classes. Ricorda che l&#39;utilizzo di `global` comunica al Registro di sistema dello schema che si desidera restituire solo gli oggetti XDM standard di Adobe


## Individuare e salvare la classe $id

Dopo aver eseguito la richiesta API, effettuare le seguenti operazioni per individuare e salvare `$id` per la classe XDM Individual Profile.

1. Cerca la classe `XDM Individual Profile` nella risposta
1. Copiare `$id` per la classe `XDM Individual Profile` e salvarlo in un percorso a cui fare riferimento in seguito.

![Classe profilo individuale XDM nella risposta API](assets/get-profile-class-xdm-individual-profile-class.png "Classe profilo individuale XDM")

>[!WARNING]
>
>Non continuare finché non hai salvato `$id` da qualche parte.  Sarà necessario in seguito per creare lo schema Account cliente
