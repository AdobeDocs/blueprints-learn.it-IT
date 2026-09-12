---
title: Consegna dei messaggi in azione
description: Ottieni una panoramica della creazione di una campagna orchestrata che esegue il targeting dei membri del piano di base e confronta il comportamento di consegna tra i canali e-mail del profilo di AEP e dello schema relazionale.
doc-type: overview-page
solution: Experience Platform
exl-id: 84b16fff-f733-439a-9a93-726811e543ce
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 1%

---


# Consegna dei messaggi in azione

## Prerequisiti

>[!WARNING]
>
>Prima di avviare questo laboratorio, è necessario aver completato i seguenti laboratori

- **Archivi dati - Archivio relazionale in azione** **—>** [Dimension di destinazione profilo](../../data-stores/relational-store-in-action/profile-target-dimension.md)
- **Archivi dati —>** [Configura canali e-mail](../../data-stores/configure-email-channels/overview.md) *(il completamento di questo passaggio di installazione richiede fino a 3 ore)*

Se non hai completato queste esercitazioni, fallo adesso prima di continuare.

## Panoramica di Lab

Questo video illustra come creare la campagna orchestrata per questo laboratorio, inclusi la creazione e il forking di un pubblico di membri del piano Base e il confronto dei risultati di consegna tra i canali e-mail Profilo e Relazionale.

>[!VIDEO](https://video.tv.adobe.com/v/3486541/)

## Obiettivi di apprendimento

- Creare una campagna orchestrata utilizzando diverse attività del flusso di lavoro
- Creare un pubblico utilizzando l’attività Creare pubblico
- Effettua il forking del pubblico per creare due rami e utilizza i canali e-mail, creati nel laboratorio precedente, per inviare messaggi
- Test della campagna e comprensione della differenza di comportamento tra i canali e-mail

In questa esercitazione, creerai una campagna per eseguire il targeting dei membri del piano &quot;Basic&quot; e capire la differenza quando utilizzi diverse impostazioni di Campagna orchestrata nelle configurazioni del canale e-mail.
