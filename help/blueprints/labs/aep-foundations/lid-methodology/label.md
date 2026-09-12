---
title: Etichetta
description: Etichettare le tabelle data warehouse relazionali come classi XDM Individual Profile, Experience Event o Lookup come parte della metodologia LID.
doc-type: article
solution: Experience Platform
exl-id: 332ead7a-ca6e-4e30-bb35-8419c060c596
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# Etichetta

## Lezione

Questo video illustra come etichettare le tabelle relazionali come tabelle XDM di profilo individuale (P), Experience Event (E) o Lookup (L), utilizzando Connection 5G ERD come esempio.

>[!VIDEO](https://video.tv.adobe.com/v/3459087/?quality=12&learn=on)



## Dettagli laboratorio

Etichettare le tabelle di Connection 5G Data Warehouse ERD e Streaming ERD con l&#39;etichetta di classe XDM appropriata per le tabelle Profilo individuale, Evento esperienza e Ricerca.

Durante l&#39;esecuzione del laboratorio, tenete presente quanto segue:

- **Profilo individuale (caratteristiche) -** descrive in modo univoco le caratteristiche di una persona (ad esempio nome, e-mail, indirizzo, preferenze e così via)
- **Evento esperienza (comportamenti) -** descrive le interazioni e i punti di contatto di una persona con un marchio/un&#39;azienda (ad esempio visita di una pagina web, acquisto, interazioni con un call center, invio di un&#39;applicazione, ecc.)
- **Ricerche (supporto) -** forniscono informazioni contestuali aggiuntive a supporto del singolo profilo o evento esperienza



## Passaggio 1: Etichettare le singole tabelle del profilo XDM

1. Identificare tutte le tabelle di origine che rappresentano una singola persona sia nell&#39;ERD del data warehouse cliente che nell&#39;ERD dello streaming cliente.
1. Contrassegna ogni tabella con &quot;**P**&quot; a indicare che fa parte della classe Profilo individuale XDM

>[!NOTE]
>
>Contrassegna solo le tabelle che rappresentano in modo univoco le caratteristiche di una singola persona



## Passaggio 2: Etichettare le tabelle Experience Event di XDM

1. Identificare tutte le tabelle di origine che rappresentano il comportamento di una singola persona sia nell&#39;ERD del data warehouse Connection 5G che nell&#39;ERD Streaming.
1. Contrassegna ogni tabella con un &quot;**E**&quot; a indicare che fa parte della classe XDM Experience Event.

>[!NOTE]
>
>Contrassegna solo le tabelle che rappresentano in modo univoco il comportamento di una singola persona



## Passaggio 3: Tabelle di supporto XDM per etichette

1. Identificare tutte le tabelle di origine che rappresentano i dati di ricerca e sono direttamente correlate a una tabella **&quot;P&quot;** o **&quot;E&quot;** contrassegnata nell&#39;ERD del data warehouse Connection 5G e nell&#39;ERD Streaming.
1. Contrassegna ogni tabella con una **&quot;L&quot;** che indica che fa parte di una classe XDM personalizzata non personalizzata.

>[!NOTE]
>
>Le tabelle di ricerca possono trovarsi a 1 livello di join o a una distanza di &quot;hop&quot; da una tabella con etichetta &quot;P&quot; o &quot;E&quot;



## Revisione

Il video seguente esamina le etichette corrette per il magazzino Connection 5G e le ERD streaming, spiegando perché le tabelle di account cliente, ordini e rendiconti di fatturazione sono stati etichettati come erano.

>[!VIDEO](https://video.tv.adobe.com/v/3459081/?quality=12&learn=on)
