---
hold: true
title: Lancio di punta del telefono
description: Ottieni una panoramica della creazione di una campagna orchestrata che esegue il targeting dei titolari di account e delle singole linee con un’offerta di aggiornamento SMS dopo un lancio di punta tramite telefono.
doc-type: overview-page
solution: Experience Platform
exl-id: 04c509f1-aa10-4d29-aa59-5e627b79e498
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---


# Lancio di punta del telefono

## Prerequisiti

>[!WARNING]
>
>Prima di avviare questo laboratorio, è necessario aver completato i seguenti laboratori

- **Archivi dati - Archivio relazionale in azione** **—>** [Dimension di destinazione profilo](../../data-stores/relational-store-in-action/profile-target-dimension.md)
- **Archivi dati — Configura canali e-mail —>** [Configura per relazionale](../../data-stores/configure-email-channels/configure-for-relational.md)
  *(il completamento di questo passaggio di installazione richiede fino a 3 ore)*

Se non hai completato queste esercitazioni, fallo adesso prima di continuare.

## Panoramica di Lab

Questo video illustra come il caso d’uso del lancio del telefono di punta corrisponde alle campagne orchestrate, riassumendo le domande e l’architettura di pensiero critiche prima di creare la campagna indirizzando i titolari di account e le singole linee.

>[!VIDEO](https://video.tv.adobe.com/v/3486217/)

## Obiettivi di apprendimento

- Creare una campagna orchestrata utilizzando diverse attività del flusso di lavoro
- Creare un pubblico utilizzando un’attività Creare pubblico
- Come impostare un canale SMS
- Salvare un pubblico nel portale del pubblico
- Eseguire il targeting dell’account del cliente e delle singole righe con e-mail e messaggi sms



## Descrizione del caso d’uso

Immediatamente dopo il lancio di un dispositivo di punta del produttore, invia un messaggio mirato agli account holder e agli utenti di linea con modelli meno recenti, invitandoli ad aggiornare e sperimentare il futuro del mobile.

**Callout chiave:**

- Salva il pubblico di tutte le righe cliente in Audience Portal
- Esegui il targeting di singole righe e titolari di account con un messaggio (utilizzerai SMS)

>[!NOTE]
>
>Questo scenario simula una **campagna di aggiornamento del contratto di telecomunicazione**, in cui le linee secondarie (dipendenti) ricevono messaggi di aggiornamento mirati.
