---
hold: true
title: Configurazione della Console per sviluppatori
description: Crea un progetto Adobe Developer Console con credenziali server-to-server OAuth per DEP CLI per l’autenticazione nella sandbox.
doc-type: article
solution: Experience Platform
exl-id: 4a7c9e2b-1d3f-4a6e-8b9c-2d5e7f1a3c6b
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---


# Configurazione della Console per sviluppatori

&#x200B;> [!NOTE]
>
>Questa opzione è necessaria solo se si lavora nei laboratori al proprio ritmo. Se ti trovi in un corso o evento di formazione live, la sandbox è già stata distribuita per te.

L’interfaccia della riga di comando DEP si autentica nella sandbox utilizzando le credenziali server-to-server OAuth di un progetto Adobe Developer Console. Questa pagina illustra come creare quel progetto. È necessario eseguire questa operazione solo una volta: le stesse credenziali funzionano sia nei brani AEP Foundations che in AJO Architectural Foundations, purché vengano aggiunte entrambe le API descritte di seguito.

>[!NOTE]
>
>Se disponi già di un progetto Developer Console con credenziali per Adobe Experience Platform (e, se necessario, Adobe Journey Optimizer), salta questa sezione e vai direttamente a [Istruzioni di distribuzione](deployment-instructions.md).

## Prerequisiti

- Un Adobe ID con accesso per sviluppatori all’organizzazione
- Sandbox Adobe Experience Platform vuota e di tipo `dev`
- Un ruolo Adobe Experience Platform con tutte le autorizzazioni concesse per quella sandbox (se non sei sicuro, rivolgiti al tuo amministratore di sistema)

## Creare il progetto

1. Vai a [Adobe Developer Console](https://developer.adobe.com/console) e accedi
1. Se hai accesso a più organizzazioni, utilizza il selettore organizzazione in alto a destra per selezionare quella corretta
1. Seleziona **Crea nuovo progetto**
1. Rinominare il progetto come qualcosa che riconoscerai in seguito (ad esempio, `DEP Sandbox`)

## Aggiungi API Experience Platform

1. Dalla panoramica del progetto, seleziona **Aggiungi API**
1. Scegli l&#39;icona del prodotto **Adobe Experience Platform**, quindi seleziona **API Adobe Experience Platform**
1. Seleziona **Avanti**
1. Scegli **OAuth Server-to-Server** come tipo di autenticazione e seleziona **Next**
1. Assegna un nome alle credenziali e seleziona **Avanti**
1. Seleziona il profilo prodotto che corrisponde alla sandbox che userai, quindi seleziona **Salva API configurata**

## Raccogliere i valori

Apri la pagina di panoramica **OAuth Server-to-Server** delle credenziali. Sono necessari quattro valori per il file di ambiente della CLI:

| **Valore console sviluppo** | **Campo file Env** |
| --------------------- | ------------------------------- |
| ID client | `API_KEY` |
| Segreto client | `CLIENT_SECRET` |
| ID organizzazione | `IMS_ORG` (termina in `@AdobeOrg`) |
| Ambiti | `SCOPES` |

>[!NOTE]
>
>Copiare gli ambiti predefiniti visualizzati nella pagina delle credenziali. Non è necessario aggiungere nulla manualmente. Se hai aggiunto entrambe le API qui sopra, l’elenco degli ambiti include entrambe automaticamente.

Tieni aperta questa pagina o copia questi quattro valori in un luogo sicuro. Tali file verranno incollati nel file di ambiente della CLI nel passaggio successivo della guida alla configurazione del brano.
