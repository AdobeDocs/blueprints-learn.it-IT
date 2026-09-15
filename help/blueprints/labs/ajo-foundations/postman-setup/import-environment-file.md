---
title: Importa file di ambiente
description: Importa il file di ambiente Postman e imposta le variabili globali come EDGE_REGION necessarie per le chiamate API in tutto il bootcamp.
doc-type: article
solution: Experience Platform
exl-id: a5d45656-e3f5-4207-823c-ad33d4ef26a4
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%
---

# Importa file di ambiente

## Obiettivo

In questa pagina viene importato il file di ambiente di Postman.  Questo file contiene diverse variabili globali utilizzate all’interno di varie chiamate API effettuate durante altri laboratori nel bootcamp.

## Importa file di ambiente

1. Scarica il file **AJO Bootcamp.postman\_environment.json**:

   Scarica il file — [AJO Bootcamp.postman_environment.json](assets/ajo-bootcamp.postman_environment.json)

2. Avvia Postman sul computer locale.
3. Se necessario, passare al Workspace utilizzato per questi laboratori e fare clic sul pulsante **Importa**.

   ![Inizio importazione Postman](assets/import-environment-file-click-import-button.png)

4. Incolla l&#39;URL locale del file **AJO Bootcamp.postman\_environment.json** nella casella di testo modale di importazione oppure rilascialo nella finestra di dialogo di importazione.  Questa azione attiva un’importazione automatica

   ![Finestra di dialogo di importazione Postman con l&#39;opzione di incollare un URL di file](assets/import-environment-file-import-button-overlay.png "Importazione Postman tramite URL")

   ![Finestra di dialogo di importazione di Postman che accetta un file rilasciato tramite trascinamento](assets/import-environment-file-drag-and-drop-import.png "Importazione di Postman tramite trascinamento")

5. Una volta importato, verifica l&#39;esistenza dell&#39;ambiente facendo clic sulla scheda **Ambienti** nella barra laterale a sinistra. L’ambiente Bootcamp AJO è ora disponibile.

![Convalida importazione ambiente](assets/import-environment-file-validate-environment-imported.png)

## Impostare le variabili di ambiente

Postman è stato progettato per testare e interagire con le API. Tuttavia, questa esercitazione lo utilizza per simulare gli hit di AEP Web SDK da un browser o per chiamate di raccolta dati in tempo reale lato server. Queste richieste sono tecnicamente chiamate API, ma non sono tipiche chiamate API che richiedono elementi come i token di autorizzazione nell’intestazione. Le variabili di ambiente in questi laboratori vengono utilizzate principalmente per le variabili nei percorsi URL (con una utilizzata in un’intestazione).

1. Se necessario, fai clic sulla scheda **Ambienti** nella barra laterale a sinistra di Postman
2. Fai clic sul file dell&#39;ambiente **AJO Bootcamp**. Vedrai alcuni valori che devi compilare

   ![Variabili di ambiente Postman con valori vuoti che devono essere compilati](assets/import-environment-file-values-need-filling-in.png "Verificare le variabili postman negli ambienti")

3. Per il momento ignora il valore DATASTREAM\_CONFIG. Puoi creare una configurazione dello stream di dati in un laboratorio successivo.
4. Aggiorna il campo **EDGE\_REGION** con il codice di regione più vicino alla posizione fisica del campo di avvio, utilizzando la tabella seguente come ricerca.

   | **Area** | **Codice area** |
   | ---------- | --------------- |
   | Stati Uniti occidentali | o2 |
   | Stati Uniti orientali | va6 |
   | Europa | irl1 |
   | Australia | aus3 |
   | Giappone | jpn3 |
   | Asia | spg3 |

   Al termine, il file di ambiente sarà simile al seguente:



   ![Verifica variabile di area geografica Postman](assets/import-environment-file-region-variable-set.png)

5. Ora è necessario salvare le variabili di ambiente; tuttavia, non è presente alcun pulsante Salva nell’interfaccia utente di Postman. Utilizzare i tasti di scelta rapida di Windows o Mac per il salvataggio (ad esempio, Ctrl+S su Windows). Le modifiche sono state salvate quando viene visualizzato il messaggio **Modifiche salvate** nell&#39;angolo inferiore destro dell&#39;interfaccia utente di Postman:

![Verifica modifiche salvate](assets/import-environment-file-changes-saved-confirmation.png)

>[!SUCCESS]
>
>Congratulazioni! Hai completato il file dell’ambiente Postman
