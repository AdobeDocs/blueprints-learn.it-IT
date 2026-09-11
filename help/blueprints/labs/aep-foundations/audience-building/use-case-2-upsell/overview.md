---
hold: true
title: Caso d’uso
description: Definisci un caso di utilizzo di upselling indirizzato ai clienti con elevato utilizzo di dati senza un piano telefonico finale, confrontando gli approcci di aggregazione del pubblico per l’attivazione.
doc-type: overview-page
solution: Experience Platform
exl-id: d0268de8-87eb-4dd9-b699-99d42716f20c
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Caso d’uso #2: upselling

## Panoramica

Questo video illustra come affrontare il caso di utilizzo dell’upselling, che ha come target i clienti con elevato utilizzo di dati per l’attivazione tramite canali di direct mailing e a pagamento.

>[!VIDEO](https://video.tv.adobe.com/v/3459487/?quality=12&learn=on)



**Definizione del caso d&#39;uso**

Trova tutti i clienti che hanno avuto un utilizzo totale dei dati di fatturazione negli ultimi 6 mesi > 140 GB, una media continua di 6 mesi. utilizzo mensile dei dati di >=20 GB e che non hanno un piano telefonico definitivo.

Attiva nei canali Facebook/Google e Direct Mail.

Campi di personalizzazione direct mailing:

- Nome → utilizzato per il saluto
- Indirizzo postale → per l&#39;invio
- Nome del piano → utilizzato per il rendiconto postale (ad esempio &quot;Eric, effettua subito l’aggiornamento a un piano finale&quot;)



## Attività di analisi

Analizzare quanto sopra e annotare:

1. Quali campi sono necessari per risolvere questo caso d’uso?
1. Il metodo di valutazione deve essere Streaming?
1. Cosa dobbiamo tenere a mente con i dati di fatturazione?
1. Quali altre informazioni vorresti conoscere?

Ricorda: quando riceviamo i requisiti dagli stakeholder aziendali, questi tendono ad essere incompleti, ad usare un&#39;altra terminologia, e a fare supposizioni senza saperlo. È tuo compito far emergere tutto questo e guidarli verso qualcosa che possa essere fatto.



## Approccio

Per questo caso d’uso verranno valutate due opzioni:

- #1 opzione (utilizza pubblico per aggregare)
  - Il pubblico eseguirà l’aggregazione
    - Utilizzo dati fatturazione Somma > 140 GB (ultimi 6 mesi)
    - Utilizzo dati fatturazione Media > 20 GB (ultimi 6 mesi)
    - Utilizzo dati fatturazione elevato ma nessun piano Ultimate
- Opzione #2 (Usa Preaggregati)
  - Questa operazione utilizza l’aggregazione eseguita prima di inserire i dati nel profilo
    - Utilizzo dati fatturazione elevato ma nessun piano Ultimate (Agg)
