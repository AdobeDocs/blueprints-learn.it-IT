---
title: Accesso alla sandbox
description: Verifica che l’ambiente Postman possa recuperare correttamente la sandbox di Experience Platform assegnata prima di avviare i laboratori.
doc-type: article
solution: Experience Platform
exl-id: c841e497-a695-4d3f-85e6-d653478cad1e
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%
---

# Accesso alla sandbox

Prima di continuare, verificare che l&#39;accesso sia valido. Effettua le seguenti operazioni:

1. Apri la cartella con titolo `Check Sandbox Access` e fai clic sulla chiamata con titolo `Retrieve Your Sandbox`
1. Nell’angolo in alto a destra di Postman viene visualizzata una casella a discesa Ambiente.  Assicurarsi di selezionare l&#39;ambiente `AEP Bootcamp`
1. Eseguire la chiamata facendo clic sul pulsante `Send`

![Riquadro richieste Postman per la chiamata Retrieve Your Sandbox prima dell&#39;invio](assets/sandbox-access-check-sandbox-request.png "Retrieve your sandbox API call")



Una risposta corretta è simile alla seguente:

![200 Risposta OK che conferma il recupero della sandbox assegnata](assets/sandbox-access-successful-response.png "200 OK Richiesta sandbox riuscita")

>[!NOTE]
>
>Il valore **name** deve corrispondere alla variabile sandbox\_name nell&#39;ambiente postman

>[!SUCCESS]
>
>Congratulazioni!  Sei pronto per iniziare a utilizzare le API di Experience Platform
