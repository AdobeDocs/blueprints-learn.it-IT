---
hold: true
title: File di ambiente
description: Importa il file di ambiente Postman e popola le variabili di progetto sviluppatore e sandbox necessarie per le chiamate API di bootcamp.
doc-type: article
solution: Experience Platform
exl-id: 1461fac5-0714-44d4-b5c8-949df6bcff83
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---


# File di ambiente

## File di ambiente Postman

Scarica il file — [AEP Bootcamp.postman_environment.json](assets/aep-bootcamp.postman_environment.json)



## Importa file di ambiente

1. Apri `Environment File` dall&#39;alto nel browser facendo clic sul file
1. Copia l’URL del file negli Appunti
1. Avvia Postman nel computer locale e fai clic sul pulsante `Import` nell&#39;area di lavoro
1. Incollare l&#39;URL di `Environment File` nella casella di testo modale di importazione sulla sovrapposizione.  Questo dovrebbe attivare un’importazione automatica

![Fare clic sul pulsante Importa nell&#39;area di lavoro di Postman per importare il file di ambiente](assets/environment-file-click-import-button.png "Pulsante Importa")



![Incollare l&#39;URL del file di ambiente nella casella di testo modale di importazione di Postman](assets/environment-file-import-modal-paste-url.png "Sovrapposizione pulsante importazione")



Una volta importato, è possibile convalidare il file di ambiente esistente facendo clic sulla scheda `Environments` nella barra laterale a sinistra.  Dovresti vedere qualcosa di simile al seguente.

![Ambiente Bootcamp AEP elencato nella scheda Ambienti Postman dopo l&#39;importazione](assets/environment-file-aep-bootcamp-environment-listed.png "Ambiente Bootcamp AEP")



## Variabili di ambiente

Prima di poter effettuare chiamate API è necessario aggiornare alcune delle variabili nel file di ambiente appena importato.  Queste variabili fanno riferimento alle chiamate API, quindi assicurati che siano compilate correttamente.  Le variabili sono suddivise in due gruppi:

- **Valori progetto sviluppatore** -> queste sono le variabili predefinite generate dal progetto sviluppatore che sono state create in Adobe Developer Console
- **Altri valori** -> si tratta di variabili personalizzate create in genere da un utente per funzionare con le varie API di Experience Platform

>[!NOTE]
>
>Questi valori provengono dalle credenziali server-to-server OAuth create in [Installazione di Developer Console](../sandbox-setup/developer-console-setup.md#collect-your-values)



### Aggiorna valori progetto sviluppatore

1. Fai clic sulla scheda `Environments` nella barra laterale a sinistra di Postman
1. Fare clic sul file di ambiente `AEP Bootcamp`
1. Aggiorna `current values` per le seguenti variabili elencate:
   - CLIENT\_SECRET
   - CLIENT\_ID (chiamato anche CHIAVE API)
   - TECHNICAL\_ACCOUNT\_ID
   - IMS\_ORG

Al termine, il file di ambiente dovrebbe avere un aspetto simile al seguente:

![File ambiente dopo l&#39;aggiornamento dei valori CLIENT_SECRET, CLIENT_ID, TECHNICAL_ACCOUNT_ID e IMS_ORG](assets/environment-file-with-developer-project-values.png "File ambiente con valori di progetto sviluppatore")

### Aggiorna altri valori

Gli unici altri valori da aggiornare sono la variabile `SANDBOX_NAME` e la variabile `TENANT_NAME`.

- `SANDBOX_NAME` - indica a Adobe Experience Platform su quale sandbox eseguire
- `TENANT_NAME`: utilizzato per prepopolare il nome tenant in chiamate XDM specifiche

>[!NOTE]
>
>Se stai lavorando attraverso questi laboratori secondo il tuo ritmo (anziché con un evento di formazione live con sandbox-assignment.pdf), puoi trovare entrambi i valori mentre sei connesso alla sandbox dall’URL dell’interfaccia utente di Adobe Experience Platform, ad esempio:
>
>`https://experience.adobe.com/#/@dep/sname:prod/platform/home`
>
>- `SANDBOX_NAME` è il valore dopo `sname:` — in questo esempio, `prod`
>- `TENANT_NAME` è il valore dopo il simbolo `@`, con il prefisso trattino basso — in questo esempio, `_dep`

1. Aggiorna `current values` per le seguenti variabili elencate:
   - SANDBOX\_NAME
   - TENANT\_NAME
1. Salvare gli aggiornamenti facendo clic sul pulsante `Save` in alto a destra nell&#39;area di lavoro dell&#39;ambiente

Al termine, il file di ambiente dovrebbe avere un aspetto simile al seguente:

![File ambiente dopo l&#39;aggiornamento dei valori SANDBOX_NAME e TENANT_NAME](assets/environment-file-with-sandbox-name-and-tenant-name.png "File ambiente con SANDBOX_NAME")

>[!TIP]
>
>Congratulazioni! Hai completato la configurazione dell’ambiente Postman
