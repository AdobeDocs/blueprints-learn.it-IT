---
title: Consegna dei messaggi in azione
description: Ottieni una panoramica della creazione di una campagna orchestrata che esegue il targeting dei membri del piano di base e confronta il comportamento di consegna tra i canali e-mail del profilo di AEP e dello schema relazionale.
doc-type: overview-page
solution: Experience Platform
exl-id: 84b16fff-f733-439a-9a93-726811e543ce
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%
---

# Consegna dei messaggi in azione

## Prerequisiti

>[!WARNING]
>
>Prima di avviare questo laboratorio, è necessario che i laboratori seguenti siano stati completati

- **Archivi dati - Archivio relazionale in azione** **—>** [Dimension di destinazione profilo](../../data-stores/relational-store-in-action/profile-target-dimension.md)
- **Archivi dati —>** [Configura canali e-mail](../../data-stores/configure-email-channels/overview.md) *(il completamento di questo passaggio di installazione richiede entro 3 ore)*

Se non hai completato questi laboratori, fallo ora prima di continuare.

>[!CAUTION]
>
>Questo laboratorio richiede un sottodominio delegato ad Adobe nella sandbox. Consulta [Configurazione](../../setup.md) se sei al passo con i tuoi impegni e non ne hai ancora uno.

## Panoramica di Lab

Questo video spiega come creare la campagna orchestrata per questo laboratorio, inclusa la creazione e il forking di un pubblico di membri del piano Base e il confronto dei risultati di consegna tra i canali e-mail Profilo e Relazionale.

>[!VIDEO](https://video.tv.adobe.com/v/3486541/)

## Obiettivi di apprendimento

- Creare una campagna orchestrata utilizzando diverse attività del flusso di lavoro
- Creare un pubblico utilizzando l’attività Creare pubblico
- Effettua il forking del pubblico per creare due rami e utilizza i canali e-mail, creati nel laboratorio precedente, per inviare messaggi
- Test della campagna e comprensione della differenza di comportamento tra i canali e-mail

Per eseguire il targeting dei membri del piano &quot;Basic&quot;, crea una campagna in questa esercitazione ed esplora in che modo le diverse impostazioni della campagna orchestrata influiscono sulle configurazioni del canale e-mail.
