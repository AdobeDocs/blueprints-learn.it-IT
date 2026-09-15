---
title: Automatizzare con API
description: Esegui una raccolta Postman che automatizza la creazione di schemi, gruppi di campi, descrittori di identità e relazioni e set di dati in una singola esecuzione.
doc-type: article
solution: Experience Platform
exl-id: a490f93f-19da-4de3-81c8-4569c49c5354
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%
---

# Automatizzare con API

## Introduzione

Per scoprire come automatizzare le distribuzioni utilizzando le API, esegui una cartella di API che crea i seguenti oggetti:

- Account cliente e piano \[Lookup] schema/i
- Gruppi di campi che compongono gli schemi precedenti
- Descrittori di identità richiesti per il profilo
- Descrittori di relazioni e riferimenti necessari per creare le relazioni tra l&#39;account cliente e il piano \[Lookup]
- Due set di dati corrispondenti a ogni schema creato



## Esegui la cartella

1. In Postman passa alla cartella **Automazione con API** all&#39;interno della cartella **XDM Schema Lab**

   ![Cartella Automazione con API all&#39;interno della cartella XDM Schema Lab in Postman](assets/automate-with-apis-postman-automation-folder.png)



1. Fai clic sulla cartella **Automazione con API** e nell&#39;area di lavoro fai clic sul pulsante **Esegui**

   >[!NOTE]
   >
   >Il pulsante Esegui si trova in alto a destra nell’area di lavoro di Postman

   ![Pulsante Esegui in alto a destra nell&#39;area di lavoro di Postman per la cartella Automazione con API](assets/automate-with-apis-click-folder-run-button.png "Fare clic sulla cartella Esegui")



1. Viene visualizzata una nuova finestra che mostra tutte le chiamate API nella cartella. Imposta **Delay** su **500ms**, quindi fai clic sul pulsante **Esegui**.

   ![Esegui la finestra di dialogo di automazione con ritardo impostato su 500 ms prima di fare clic su Esegui](assets/automate-with-apis-execute-automation-dialog.png "Esegui automazione")



1. Vedrai che le chiamate API iniziano a essere eseguite in ordine e, una volta completate, vedrai 32 test superati.

   ![Automazione riuscita con 32 test superati](assets/automate-with-apis-successful-automation-32-passed-tests.png "Automazione riuscita")



1. Passa all&#39;interfaccia utente di Experience Platform per visualizzare due schemi e due set di dati creati e abilitati per il profilo con il prefisso **postman:**

![Due schemi creati e abilitati per il profilo con il postman: prefix](assets/automate-with-apis-schemas-created-in-ui.png "Schemi di automazione")



![Due set di dati creati con Postman: prefisso corrispondente agli schemi automatizzati](assets/automate-with-apis-datasets-created-in-ui.png "Set di dati di automazione")

>[!SUCCESS]
>
>Congratulazioni!  Hai automatizzato la distribuzione di spazi dei nomi di identità, gruppi di campi, schemi, descrittori di identità/relazione, hai abilitato uno schema per il profilo e generato un set di dati utilizzando lo schema
