---
title: Token di accesso
description: Genera un token di accesso server-to-server OAuth in Postman e comprendi le intestazioni necessarie per l’autenticazione delle chiamate API di AEP.
doc-type: article
solution: Experience Platform
exl-id: e38a1bd4-5a09-40c6-8303-c3770801c864
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---


# Token di accesso

## Panoramica sulla sicurezza API



Per stabilire una connessione API sicura a un prodotto Adobe, Adobe fornisce la creazione di una credenziale server-to-server OAuth. A questo scopo, devi innanzitutto creare un progetto per sviluppatori all’interno di Adobe Developer Console. Per poter accedere a Developer Console è necessario disporre dei diritti di sviluppatore assegnati all’interno di Adobe Admin Console. Una volta ottenuti questi diritti, puoi creare progetti per sviluppatori utilizzando le varie API relative ai prodotti Adobe. Qui entra in gioco le credenziali server-to-server OAuth. Per generare un token di accesso è necessario trasmettere un determinato set di attestazioni al servizio Identity Management (IMS) di Adobe. Per le credenziali da server a server OAuth, una chiamata di esempio sarà simile alla seguente:

```curl
curl -X POST 'https://ims-na1.adobelogin.com/ims/token/v3?client_id={CLIENT_ID}' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'client_secret={CLIENT_SECRET}&grant_type=client_credentials&scope={SCOPE}'
```

>[!NOTE]
>
>Ulteriori informazioni sul processo e2e per la creazione del progetto per sviluppatori tramite le credenziali server-to-server OAuth [qui](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens). Per il bootcamp verrà eseguito un &quot;handwave&quot; di questo passaggio del processo 😄



## Adobe Experience Platform + Adobe IMS

Ogni richiesta a qualsiasi servizio Adobe deve includere il token di accesso nell’intestazione Autorizzazione insieme al segreto client generato durante la creazione del progetto per sviluppatori. Inoltre, Experience Platform e le applicazioni a essa associate richiedono la presenza di altri due parametri di intestazione per ogni richiesta.

- `x-gw-ims-org-id` - questo parametro specifica `IMS Org` a cui appartiene la richiesta e garantisce che l&#39;elaborazione delle richieste venga risolta nell&#39;ambiente SaaS appropriato
- `x-sandbox-name` - questo parametro specifica quale sandbox elaborare la richiesta in Experience Platform

Ora che hai capito qualcosa su come Adobe protegge le API e su cosa è necessario lavorare con esse, puoi utilizzarle ora.

>[!CAUTION]
>
>Se non si specifica il parametro `x-sandbox-name`, la richiesta non avrà esito negativo come previsto. Al contrario, per impostazione predefinita la richiesta viene elaborata nella sandbox `default` che viene fornita automaticamente con qualsiasi ambiente Experience Platform

>[!NOTE]
>
>Come parte di questo bootcamp abbiamo creato un progetto per sviluppatori e fornito un file di ambiente Postman con tutti i valori necessari per richiedere un `access_token`. Questo è ciò che hai caricato nei passaggi precedenti del laboratorio

## Autenticazione con Postman

1. Avviare Postman, passare alla directory con titolo `IMS Authenticate` e aprire la richiesta facendo clic su di essa
1. Nell’angolo in alto a destra di Postman viene visualizzato un elenco a discesa dell’ambiente. Seleziona l&#39;ambiente `AEP Bootcamp` dal menu a discesa
1. A questo punto eseguire la chiamata facendo clic sul pulsante &quot;Send&quot;

![Richiesta Postman dopo l&#39;invio della chiamata di autenticazione IMS per generare un token di accesso](assets/access-token-execute-ims-authenticate-request.png)

Una risposta corretta dovrebbe essere simile alla seguente:

```none
200 OK Successful Authentication
```

Risposta corretta

```json
{
    "token_type": "bearer",
    "access_token": "<value>",
    "expires_in": 86399979
}
```

`token_type` - sarà sempre di tipo bearer

`access_token`: verifica l&#39;autorizzazione e viene richiesta nell&#39;intestazione di autorizzazione di tutte le chiamate API

`expires_in` - millisecondi fino alla scadenza del token di accesso (oggi periodo di scadenza di 24 ore)

>[!TIP]
>
>Congratulazioni! Hai autenticato correttamente e il tuo access\_token è ora salvato nel file di ambiente



## Errori comuni

### Token non valido

Ciò si verifica quando `private_key` nel file di ambiente non è formattato correttamente o non è più valido. In questo caso, assicurati di aver copiato l’intera chiave, comprese le interruzioni di riga

Esempio:

```none
-----BEGIN PRIVATE KEY----- 
some uber long varchar set is here
-----END PRIVATE KEY----- 
```

```none
400 invalid_token
```

>[!NOTE]
>
>Applicabile solo quando si utilizza l’autenticazione basata su JWT

### IMS\_ORG non valido

Questo errore si verifica quando si dimentica di impostare l&#39;ambiente postman dal menu a discesa

![Errore IMS_ORG non trovato nell&#39;ambiente attivo quando non è selezionato alcun ambiente Postman](assets/access-token-forgot-to-select-postman-environment.png)

>[!NOTE]
>
>Non dimenticare di impostare l’ambiente postman durante l’esecuzione di chiamate API
>
>![Selezione dell&#39;ambiente di bootcamp AEP dal menu a discesa dell&#39;ambiente Postman](assets/access-token-set-postman-environment.png)
