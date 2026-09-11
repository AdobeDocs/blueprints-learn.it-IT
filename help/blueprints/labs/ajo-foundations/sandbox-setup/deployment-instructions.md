---
hold: true
title: Istruzioni di distribuzione
description: Utilizza DEP CLI per distribuire nella sandbox gli schemi, i set di dati, i flussi di dati e i dati di esempio di AJO Architectural Foundations lab Pack.
doc-type: article
solution: Experience Platform
exl-id: 3d6e9a1c-7b2f-4e8a-9d0c-1f5a8b6c2e3d
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '942'
ht-degree: 1%

---


# Istruzioni di distribuzione

>[!WARNING]
>
>Questa opzione è necessaria solo se si lavora nei laboratori al proprio ritmo. Se ti trovi in un corso o evento di formazione live, la sandbox è già stata distribuita per te.

Il lab pack AJO Architectural Foundations viene distribuito nella sandbox utilizzando DEP CLI, uno strumento da riga di comando per la creazione di schemi, set di dati, flussi di dati e dati di esempio da utilizzare in tutti i laboratori, sia nell’archivio dei profili che nell’archivio relazionale di AJO utilizzato per le campagne orchestrate.

## Cosa viene distribuito

**Traccia profilo**

- Spazi dei nomi di identità (customerID, planID, productID)
- Gruppi di campi XDM standard, descrittori e schemi abilitati per il profilo
- Set di dati catalogo abilitati per il profilo
- Criteri di unione e tipi di pubblico
- Dati profilo per tre set di dati di esempio: modalità Depeche (caratteristiche + eventi), elementi estranei (caratteristiche) e decisioning (caratteristiche)

**Traccia relazionale**

- Spazio dei nomi dell’identità customerID
- 11 schemi XDM relazionali con descrittori di chiave primaria, chiave esterna e versione
- 11 set di dati abilitati per le campagne orchestrate di AJO
- 11 flussi di dati che caricano dati dalla Data Landing Zone

>[!NOTE]
>
>L’implementazione end-to-end richiede circa 2 ore e 23 minuti. Le tracce di profilo e relazionali vengono eseguite in parallelo e la maggior parte del tempo è il tempo di attesa automatico applicato automaticamente dalla CLI.

## Prerequisiti

- **Diritti licenza.** Privilegi amministrativi per un’organizzazione IMS con Real-Time CDP (con segmentazione streaming) e Adobe Journey Optimizer (con campagne orchestrate)
- **Diritti di accesso.** Un ruolo Experience Platform con tutte le autorizzazioni sulla sandbox di destinazione, incluse le credenziali API create da [Configurazione di Developer Console](developer-console-setup.md).
- **Credenziali Developer Console.** Progetto che include sia API Adobe Experience Platform che API Adobe Journey Optimizer. Se non disponi ancora di questi elementi, segui prima [Configurazione di Developer Console](developer-console-setup.md)
- **Sandbox.** Vuoto, di tipo `dev` e in stato &quot;Pronto&quot; per almeno 120 minuti prima dell&#39;avvio della distribuzione
- **Node.js.** Qualsiasi versione LTS recente, su Windows o Mac

## &#x200B;1. Installare CLI

1. Clona o scarica l&#39;archivio [dep-cli](https://github.com/adobe/dep-cli)
1. Dalla directory `dep-cli`, eseguire `npm install`
1. Avvia CLI con `npm start`

>[!NOTE]
>
>Node.js è necessario prima di eseguire i comandi riportati sopra. Se non hai ancora installato Node.js, consulta prima la [pagina di configurazione di Node.js](https://github.com/adobe/dep-cli/wiki/Nodejs-Setup) del wiki. Per informazioni complete sull&#39;installazione, incluse le schermate e le modalità di aggiornamento di un&#39;installazione esistente, vedere la pagina wiki [Installazione](https://github.com/adobe/dep-cli/wiki/Installation)

## &#x200B;2. Configurare il file di ambiente

La CLI viene distribuita in qualsiasi sandbox in cui punti il file di ambiente, pertanto deve essere impostata correttamente prima di eseguire qualsiasi operazione.

1. Copia `envFiles/sample-env.json` e assegnagli un nuovo nome, ad esempio `my-env.json`
2. Apri il file e compila i campi seguenti utilizzando i valori di [Configurazione di Developer Console](developer-console-setup.md):

| **Campo** | **Valore** |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `API_KEY` | ID client |
| `CLIENT_SECRET` | Segreto client |
| `IMS_ORG` | ID organizzazione |
| `SCOPES` | Deve includere entrambi gli ambiti API di Experience Platform e API di Adobe Journey Optimizer <br />*(ad esempio cjm.suppression\_service.client.delete, cjm.suppression\_service.client.all, openid, session, AdobeID, read\_organization, additional\_info.projectedProductContext)* |
| `SANDBOX_NAME` | La sandbox di destinazione deve essere vuota e di tipo `dev` |

3. Salva e chiudi il file

>[!NOTE]
>
>Ogni volta che si esegue un comando CLI, viene richiesto di specificare il nome del file, in modo da poterlo riutilizzare in tutti i passaggi seguenti.

## &#x200B;3. Eseguire il menu AJO Architectural Foundations

Dal menu principale, seleziona **Fondamenti AJO arch**. Ci sono sei passaggi suddivisi in due tracce.

### Traccia del profilo (esegui in ordine)

>[!WARNING]
>
>La sandbox deve essere stata in stato &quot;Pronta&quot; per almeno 60 minuti prima di eseguire il passaggio 1.

| **Passaggio** | **Funzionamento** | **Prima di eseguirlo** |
| ------------------------ | ------------------------------------------------------------------------------------------- | ---------------------------------- |
| &#x200B;1. Crea base di profilo | Distribuisce spazi dei nomi di identità, schemi, set di dati, criteri di unione e tipi di pubblico | Sandbox &quot;Pronta&quot; per più di 60 minuti |
| &#x200B;2. Carica dati profilo | Crea flussi di dati e trasmette dati di profilo in modalità Depeche, Cose strane e Decisioning | Attendere più di 60 minuti dopo il punto 1 |
| &#x200B;3. Verifica stato del profilo | Verifica che tutti i dati del profilo siano stati caricati correttamente | Attendere più di 15 minuti dopo la Fase 2 |

Il passaggio 1 dura circa 2 minuti, il passaggio 2 circa 6 minuti.

>[!NOTE]
>
>Il passaggio 2 può essere rieseguito in caso di errore, poiché sovrascrive le caratteristiche esistenti e salta gli eventi duplicati.

### Traccia relazionale

>[!WARNING]
>
>La sandbox deve essere stata in stato &quot;Pronta&quot; per almeno 120 minuti prima di eseguire il passaggio 4 o 6.

| **Passaggio** | **Funzionamento** | **Prima di eseguirlo** |
| ----------------------------------- | -------------------------------------------------------------------------------- | ---------------------------------------------------- |
| &#x200B;4. Crea base relazionale | Crea lo spazio dei nomi customerID e schemi/descrittori/set di dati relazionali | Sandbox &quot;Pronta&quot; per oltre 120 minuti |
| &#x200B;5. Carica dati relazionali | Carica 11 file CSV e crea i flussi di dati che li caricano | Viene eseguito subito dopo il passaggio 4, senza attesa manuale |
| &#x200B;6. Distribuire dati e base relazionale | Combina i passaggi 4 e 5 in un&#39;unica esecuzione di circa 5 minuti | Sandbox &quot;Pronta&quot; per oltre 120 minuti |

>[!NOTE]
>
>Utilizzare il passaggio 6 invece di eseguire separatamente i passaggi 4 e 5: esegue la stessa operazione in un passaggio con l&#39;attesa di propagazione gestita automaticamente.

> [!NOTE]
>
>Tutti i tempi di attesa indicati sopra vengono controllati automaticamente da CLI. Se esegui un passaggio troppo presto, questo blocca e ti dice quanto tempo aspettare.

## Risoluzione dei problemi

>[!WARNING]
>
>**Il controllo dello stato di integrità del profilo non riesce e gli eventi mancano.** Alcuni dati del profilo non hanno ancora completato la propagazione. Attendi altri 15 minuti ed esegui nuovamente Verifica stato del profilo. Se il problema persiste, esegui nuovamente Carica dati profilo, attendi 15 minuti e riprova.

>[!WARNING]
>
>**Il caricamento dei dati relazionali non riesce da parte a parte.** Ogni chiamata API esegue un nuovo tentativo fino a 3 volte. Se il problema persiste, la funzione di pulizia rimuove le connessioni di origine, le connessioni di destinazione e i flussi di dati creati in modo da poter eseguire nuovamente il passaggio 5 (o il passaggio 6) in modo ordinato. I set di mappatura non possono essere eliminati tramite l’API e possono essere lasciati indietro; questo non influisce sulla ridistribuzione.

**Si è verificato un altro errore.** Come ultima risorsa, puoi reimpostare la sandbox dal menu di gestione Sandbox di CLI e ridistribuirla dal passaggio 1.

>[!CAUTION]
>
>Il ripristino di una sandbox è distruttivo. CLI richiede di digitare il nome della sandbox da confermare prima di procedere.
