---
title: Messaggistica batch e blueprint Adobe Experience Platform
description: Esegui campagne di messaggistica pianificate e batch utilizzando Adobe Experience Platform come hub centrale per i profili dei clienti e la segmentazione.
solution: Experience Platform, Campaign
kt: 7196
exl-id: 4e55218c-c158-4f78-9f0b-c03528d992fa
translation-type: tm+mt
source-git-commit: ee1d97af9bf58076fbce24fbc8a3f0d50a4b52a0
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Messaggistica batch e blueprint Adobe Experience Platform

Esegui campagne di messaggistica pianificate e batch utilizzando Adobe Experience Platform come hub centrale per i profili dei clienti e la segmentazione.

## Casi d&#39;uso

* Campagne e-mail pianificate
* Campagne di onboarding e remarketing

## Applicazioni

* Adobe Experience Platform
* Adobe Campaign Classic o Standard

## Modelli di integrazione

* Adobe Experience Platform → Adobe Campaign Classic
* Adobe Experience Platform → Adobe Campaign Standard

## Architettura

<img src="assets/aepbatch.svg" alt="Architettura di riferimento per lo scenario Messaggistica in batch e Adobe Experience Platform" style="border:1px solid #4a4a4a" />

## Guardrail

* Supporta solo le distribuzioni di unità organizzative singole di Campaign
* Campaign è l’origine della verità per tutti i profili attivi, il che significa che i profili devono esistere in Campaign e che i nuovi profili non devono essere creati in base ai segmenti di Experience Platform.
* La realizzazione dell’appartenenza al segmento da Experience Platform è latente sia per il batch (1 al giorno) che per lo streaming (5 minuti)

**[!UICONTROL Condivisione dei segmenti di Customer Data ] Platform in tempo reale per la campagna:**

* Raccomandazione di un limite di 20 segmenti
* L&#39;attivazione è limitata a ogni 24 ore
* Sono disponibili solo gli attributi dello schema dell’unione per l’attivazione (nessun supporto per eventi array/map/experience).
* Raccomandazione di non più di 20 attributi per segmento
* Un file per segmento di tutti i profili con appartenenza al segmento &quot;realizzata&quot; O se l’appartenenza al segmento viene aggiunta come attributo nel file dei profili &quot;realizzata&quot; e &quot;uscita&quot;
* Sono supportate le esportazioni incrementali o complete di segmenti
* La crittografia del file non è supportata
* Flussi di lavoro di esportazione di Campaign da eseguire al massimo ogni 4 ore
* Consulta le protezioni per l’inserimento di profili e dati [per Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

## Passaggi di implementazione

### Adobe Experience Platform

#### Schema/Set di dati

1. Configura ad Experience Platform schemi di profilo individuale, evento esperienza e più entità in base ai dati forniti dal cliente.
1. Crea schemi di Campaign per wideLog, trackingLog, indirizzi non recapitati e preferenze di profilo (facoltativo).
1. Aggiungi le etichette di utilizzo dei dati al set di dati per la governance.
1. Crea criteri che applicano la governance sulle destinazioni.

#### Profilo/identità

1. Crea qualsiasi namespace specifico per il cliente.
1. Aggiungi identità agli schemi.
1. Abilita schemi e set di dati per il profilo.
1. Imposta le regole di unione per le diverse visualizzazioni di Profilo cliente in tempo reale (facoltativo).
1. Crea segmenti per l’utilizzo della campagna.

#### Origini / Destinazioni

1. Acquisisci dati in Experience Platform utilizzando API di streaming e connettori sorgente.
1. Configura la destinazione di archiviazione BLOB [!DNL Azure] da utilizzare con Campaign.

#### Implementazione di app mobili

1. Implementa Campaign SDK per Campaign Classic o Experience Platform SDK per Campaign Standard. Se è presente Experience Platform Launch, si consiglia di utilizzare l&#39;estensione Campaign Classic/Standard con Experience Platform SDK.

#### Campaign

1. Configura gli schemi per i dati di profilo, ricerca e consegna pertinenti.

>[!IMPORTANT]
>
>A questo punto è fondamentale comprendere cosa è il modello dati all’interno dell’Experience Platform per i dati di profilo ed evento in modo da sapere quali dati saranno necessari in Campaign.

#### Importare flussi di lavoro

1. Carica e trasferisci dati di profilo semplificati su Campaign sFTP.
1. Carica e acquisisci i dati di orchestrazione e personalizzazione della messaggistica su Campaign sFTP.
1. Acquisisci segmenti di Experience Platform dal BLOB [!DNL Azure] tramite flussi di lavoro.

#### Esportare flussi di lavoro

1. Invia nuovamente i registri di Campaign all’Experience Platform tramite flussi di lavoro ogni quattro ore (wideLog, trackingLog, indirizzi non recapitati).
1. Invia le preferenze del profilo all&#39;Experience Platform tramite flussi di lavoro basati sulla consulenza ogni quattro ore (facoltativo).


## Documentazione correlata

* [Documentazione di Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Documentazione di Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [Documentazione di Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [Documentazione del Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [Documentazione Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
