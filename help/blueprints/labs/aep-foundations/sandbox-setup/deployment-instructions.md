---
title: Istruzioni di distribuzione
description: Utilizza DEP CLI per distribuire nella sandbox gli schemi, i set di dati, i flussi di dati e i dati di profilo di esempio di AEP Foundations lab Pack.
doc-type: article
solution: Experience Platform
exl-id: 9f2b6d4a-8e1c-4b7a-a3d5-6c9f0e2a4b8d
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 1%

---


# Istruzioni di distribuzione

>[!NOTE]
>
>Questa opzione è necessaria solo se si lavora nei laboratori al proprio ritmo. Se ti trovi in un corso o evento di formazione live, la sandbox è già stata distribuita per te.

Il lab pack AEP Foundations viene distribuito nella sandbox utilizzando DEP CLI, uno strumento da riga di comando che crea schemi, set di dati, flussi di dati e dati di esempio da utilizzare in tutti i laboratori.

## Cosa viene distribuito

- 4 spazi dei nomi di identità
- 1 classe di schema, 13 gruppi di campi, 10 schemi
- 12 descrittori di identità, 6 descrittori di relazione/riferimento, 3 descrittori di nomi descrittivi
- 10 set di dati catalogo
- 1 connessione sorgente API HTTP e 10 flussi di dati
- Dati profilo: un singolo profilo in modalità Depeche (3 set di dati sulle caratteristiche, 7 set di dati sugli eventi) più 3 set di dati di ricerca
- 2 criteri di unione profili e 1 pubblico (qualsiasi streaming di eventi, entro un’ora)

>[!NOTE]
>
>L’implementazione end-to-end richiede circa 2 ore e 24 minuti, la maggior parte dei quali è costituita da un tempo di attesa incustodito tra un passaggio e l’altro. La CLI applica queste attese automaticamente, in modo che non sia necessario temporizzare nulla.

## Prerequisiti

- **Diritti licenza.** Privilegi amministrativi per un’organizzazione IMS con Real-Time CDP (con segmentazione streaming)
- **Diritti di accesso.** Un ruolo Adobe Experience Platform con tutte le autorizzazioni sulla sandbox di destinazione, incluse le credenziali API create da [Installazione di Developer Console](developer-console-setup.md).
- **Credenziali Developer Console.** Progetto che include le API di Adobe Experience Platform. Se non disponi ancora di questi elementi, segui prima [Installazione di Developer Console](developer-console-setup.md)
- **Sandbox.** Vuoto, di tipo `dev` e in stato &quot;Pronto&quot; per almeno 60 minuti prima dell&#39;avvio della distribuzione
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
1. Apri il file e compila i campi seguenti utilizzando i valori di [Installazione di Developer Console](developer-console-setup.md):

   | **Campo** | **Valore** |
   | --------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
   | `API_KEY` | ID client |
   | `CLIENT_SECRET` | Segreto client |
   | `IMS_ORG` | ID organizzazione |
   | `SCOPES` | Deve includere ambiti API di Experience Platform (openid, session, AdobeID, read_organization, additional_info.projectedProductContext) |
   | `SANDBOX_NAME` | La sandbox di destinazione deve essere vuota e di tipo `dev` |

1. Salva e chiudi il file

>[!NOTE]
>
>Ogni volta che si esegue un comando CLI, viene richiesto di specificare il nome del file, in modo da poterlo riutilizzare in tutti i passaggi seguenti.

## &#x200B;3. Eseguire il menu AEP Foundation

Dal menu principale, seleziona **AEP Foundation**. Ci sono tre passaggi, che devono essere eseguiti in ordine.

>[!WARNING]
>
>La sandbox deve essere stata in stato &quot;Pronta&quot; per almeno 60 minuti prima di eseguire il passaggio 1.

| **Passaggio** | **Funzionamento** | **Prima di eseguirlo** |
| ----------------------- | ------------------------------------------------------------------------------------------ | ------------------------------- |
| &#x200B;1. Crea base di profilo | Distribuisce spazi dei nomi di identità, schemi, set di dati, criteri di unione e tipi di pubblico | Sandbox &quot;Pronta&quot; per più di 60 minuti |
| &#x200B;2. Carica dati profilo | Crea flussi di dati, profili e dati di ricerca | Attendere più di 60 minuti dopo il punto 1 |
| &#x200B;3. Verifica stato del profilo | Verifica che tutti i dati siano stati caricati correttamente | Attendere più di 15 minuti dopo la Fase 2 |

Il passaggio 1 richiede circa 2 minuti, il passaggio 2 circa 6 minuti e il passaggio 3 è una convalida rapida senza attese proprie. Gli intervalli di 60 e 15 minuti tra i passaggi consentono ad AEP di completare la propagazione dei dati dietro le quinte, che rappresentano la maggior parte della sequenza temporale di 2 ore.

>[!NOTE]
>
>La CLI controlla automaticamente questi tempi di attesa. Se si esegue un passaggio troppo presto, questo blocca e indica quanti minuti rimangono, non è necessario tenere traccia dell&#39;orologio da soli.

>[!NOTE]
>
>Il passaggio 2 può essere rieseguito in caso di problemi. Sovrascrive i record di caratteristiche esistenti e ignora gli eventi duplicati.

## Risoluzione dei problemi

>[!WARNING]
>
>**Verifica stato non riuscita con eventi mancanti**. Alcuni dati del profilo non hanno ancora completato la propagazione. Attendi altri 15 minuti ed esegui nuovamente Verifica stato del profilo. Se il problema persiste, esegui nuovamente Carica dati profilo, attendi 15 minuti e riprova.

**Si è verificato un altro errore.** Come ultima risorsa, puoi reimpostare la sandbox dal menu di gestione Sandbox di CLI e ridistribuirla dal passaggio 1.

>[!CAUTION]
>
>Il ripristino di una sandbox è distruttivo. CLI richiede di digitare il nome della sandbox da confermare prima di procedere.
